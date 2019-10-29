---
title: 포털 내에서 OAuth 2.0 암시적 권한 부여 흐름을 사용 합니다. | MicrosoftDocs
description: 포털에서 OAuth 암시적 권한 부여 흐름을 사용 하 여 외부 Api에 대 한 클라이언트 쪽 호출을 수행 하 고이를 보호 하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 06db149e5f86696ecffae38fe05e23198d72ecb5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974509"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>포털 내에서 OAuth 2.0 암시적 권한 부여 흐름을 사용 합니다. 

이 기능을 통해 고객은 외부 Api에 대 한 클라이언트 쪽 호출을 수행 하 고 OAuth 암시적 권한 부여 흐름을 사용 하 여 보안을 유지할 수 있습니다. OAuth 2.0 암시적 허용 흐름에 따라 권한 부여를 위해 외부 Api에서 사용할 사용자 id 정보를 포함 하는 보안 액세스 토큰을 가져오기 위한 끝점을 제공 합니다. 로그인 한 사용자의 id 정보는 외부 AJAX 호출에 보안 된 방식으로 전달 됩니다. 그러면 개발자가 인증 컨텍스트를 전달 하는 데 도움이 될 뿐만 아니라 사용자가이 메커니즘을 사용 하 여 Api를 보호 하는 데도 도움이 됩니다.

OAuth 2.0 암시적 허용 흐름은 클라이언트가 ID 토큰을 가져오기 위해 호출할 수 있는 끝점을 지원 합니다. 이 목적에 사용 되는 두 개의 끝점은 [권한 부여](#authorize-endpoint-details) 및 [토큰](#token-endpoint-details)입니다.

## <a name="authorize-endpoint-details"></a>끝점 세부 정보 권한 부여 

권한 부여 끝점에 대 한 URL은 `<portal_url>/_services/auth/authorize`입니다. 권한 부여 끝점은 다음 매개 변수를 지원 합니다.

| 매개 변수   | 필수? | 설명                             |
|---------------|-----------|---------------------------------------|
| client_id      | 예       | 권한 부여 끝점에 대 한 호출을 만들 때 전달 되는 문자열입니다. 클라이언트 ID가 [포털에 등록](#register-client-id-for-implicit-grant-flow)되어 있는지 확인 해야 합니다. 그렇지 않으면 오류가 표시 됩니다. 클라이언트 ID는 토큰의 클레임에 `aud` 및 `appid` 매개 변수로 추가 되며, 클라이언트에서 반환 된 토큰이 앱에 대해 반환 되었는지 확인 하는 데 사용할 수 있습니다.<br>최대 길이는 36 자입니다. 영숫자 문자 및 하이픈만 지원 됩니다. |
| 수신      | 예       | 인증 응답을 보내고 받을 수 있는 포털의 URL입니다. 호출에 사용 되는 특정 `client_id`에 대해 등록 되어야 하며, 등록 된 것과 정확히 같은 값 이어야 합니다.            |
| 상태일       | 아니요        | 토큰 응답에도 반환 되는 요청에 포함 된 값입니다. 사용 하려는 모든 콘텐츠의 문자열일 수 있습니다. 일반적으로 임의로 생성 된 고유 값은 사이트 간 요청 위조 공격을 방지 하는 데 사용 됩니다.<br>최대 길이는 20 자입니다.              |
| 임시   | 아니요        | 클라이언트에서 보낸 결과 ID 토큰에 클레임으로 포함 되는 문자열 값입니다. 그러면 클라이언트는이 값을 확인 하 여 토큰 재생 공격을 완화할 수 있습니다. 최대 길이는 20 자입니다.      |
| response_type         | 아니요        | 이 매개 변수는 `token` 값 으로만 지원 합니다. 그러면 앱이 권한 부여 끝점에 대 한 두 번째 요청을 수행 하지 않고도 권한 부여 끝점에서 액세스 토큰을 즉시 받을 수 있습니다.                               |
|||

### <a name="successful-response"></a>성공적인 응답

권한 부여 끝점은 응답 URL에서 다음 값을 조각으로 반환 합니다.

- **token**: 토큰이 포털의 개인 키에 의해 디지털 서명 된 JSON WEB TOKEN (JWT)로 반환 됩니다.
- **상태**: 요청에 state 매개 변수가 포함 되어 있으면 동일한 값이 응답에 표시 되어야 합니다. 앱은 요청 및 응답의 상태 값이 동일한 지 확인 해야 합니다.
- **expires_in**: 액세스 토큰이 유효한 시간 (초)입니다.

예를 들어 성공적인 응답은 다음과 같습니다.

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>오류 응답

권한 부여 끝점의 오류는 다음 값을 포함 하는 JSON 문서로 반환 됩니다.

- **오류 ID**: 오류에 대 한 고유 식별자입니다.
- **오류 메시지**: 인증 오류의 근본 원인을 식별 하는 데 도움이 될 수 있는 특정 오류 메시지입니다.
- **상관 관계 ID**: 디버깅 목적으로 사용 되는 GUID입니다. 진단 로깅을 사용 하도록 설정한 경우 서버 오류 로그에 상관 관계 ID가 표시 됩니다.
- **Timestamp**: 오류가 생성 된 날짜 및 시간입니다.

오류 메시지는 로그인 한 사용자의 기본 언어로 표시 됩니다. 사용자가 로그인 하지 않은 경우 로그인 페이지가 표시 되어 사용자가 로그인 할 수 있습니다. 예를 들어 오류 응답은 다음과 같습니다.

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>토큰 끝점 세부 정보

`/token` 끝점에 대 한 요청을 만들어 토큰을 가져올 수도 있습니다. 권한 부여 끝점은 개별 페이지 (redirect_uri)에서 토큰 논리를 처리 하는 방식으로 권한 부여 끝점과 다르며, 토큰 끝점은 동일한 페이지에서 토큰 논리를 처리 합니다. 토큰 끝점의 URL은 `<portal_url>/_services/auth/token`입니다. 토큰 끝점은 다음 매개 변수를 지원 합니다.

| 매개 변수   | 필수? | 설명                             |
|---------------|-----------|---------------------------------------|
| client_id      | 아니요       | 권한 부여 끝점에 대 한 호출을 만들 때 전달 되는 문자열입니다. 클라이언트 ID가 [포털에 등록](#register-client-id-for-implicit-grant-flow)되어 있는지 확인 해야 합니다. 그렇지 않으면 오류가 표시 됩니다. 클라이언트 ID는 토큰의 클레임에 `aud` 및 `appid` 매개 변수로 추가 되며, 클라이언트에서 반환 된 토큰이 앱에 대해 반환 되었는지 확인 하는 데 사용할 수 있습니다.<br>최대 길이는 36 자입니다. 영숫자 문자 및 하이픈만 지원 됩니다. |
| 수신      | 아니요       | 인증 응답을 보내고 받을 수 있는 포털의 URL입니다. 호출에 사용 되는 특정 `client_id`에 대해 등록 되어야 하며, 등록 된 것과 정확히 같은 값 이어야 합니다.            |
| 상태일       | 아니요        | 토큰 응답에도 반환 되는 요청에 포함 된 값입니다. 사용 하려는 모든 콘텐츠의 문자열일 수 있습니다. 일반적으로 임의로 생성 된 고유 값은 사이트 간 요청 위조 공격을 방지 하는 데 사용 됩니다.<br>최대 길이는 20 자입니다.              |
| 임시   | 아니요        | 클라이언트에서 보낸 결과 ID 토큰에 클레임으로 포함 되는 문자열 값입니다. 그러면 클라이언트는이 값을 확인 하 여 토큰 재생 공격을 완화할 수 있습니다. 최대 길이는 20 자입니다.      |
| response_type         | 아니요        | 이 매개 변수는 `token` 값 으로만 지원 합니다. 그러면 앱이 권한 부여 끝점에 대 한 두 번째 요청을 수행 하지 않고도 권한 부여 끝점에서 액세스 토큰을 즉시 받을 수 있습니다.                               |
|||

> [!NOTE]
> `client_id`, `redirect_uri`, `state`및 `nonce` 매개 변수가 선택 사항인 경우에도 통합이 안전한 지 확인 하기 위해 사용 하는 것이 좋습니다.

### <a name="successful-response"></a>성공적인 응답

토큰 끝점은 상태 및 expires_in를 응답 헤더로, 토큰을 폼 본문에 반환 합니다.

### <a name="error-response"></a>오류 응답

토큰 끝점의 오류는 다음 값을 포함 하는 JSON 문서로 반환 됩니다.

- **오류 ID**: 오류에 대 한 고유 식별자입니다.
- **오류 메시지**: 인증 오류의 근본 원인을 식별 하는 데 도움이 될 수 있는 특정 오류 메시지입니다.
- **상관 관계 ID**: 디버깅 목적으로 사용 되는 GUID입니다. 진단 로깅을 사용 하도록 설정한 경우 서버 오류 로그에 상관 관계 ID가 표시 됩니다.
- **Timestamp**: 오류가 생성 된 날짜 및 시간입니다.

오류 메시지는 로그인 한 사용자의 기본 언어로 표시 됩니다. 사용자가 로그인 하지 않은 경우 사용자가 로그인 할 수 있도록 로그인 페이지가 표시 됩니다. 예를 들어 오류 응답은 다음과 같습니다.

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>ID 토큰 유효성 검사

ID 토큰을 가져오는 것 만으로는 사용자를 인증할 수 없습니다. 또한 토큰 서명의 유효성을 검사 하 고 앱의 요구 사항에 따라 토큰의 클레임을 확인 해야 합니다. 공용 토큰 끝점은 포털에서 제공 하는 토큰 서명의 유효성을 검사 하는 데 사용할 수 있는 포털의 공개 키를 제공 합니다. 공용 토큰 끝점의 URL은 `<portal_url>/_services/auth/publickey`입니다.

## <a name="turn-implicit-grant-flow-on-or-off"></a>암시적 권한 부여 흐름 설정 또는 해제

기본적으로 암시적 허용 흐름은 사용 하도록 설정 됩니다. 암시적 권한 부여 흐름을 해제 하려면 **커넥터/ImplicitGrantFlowEnabled** 사이트 설정의 값을 **False**로 설정 합니다.

포털에서이 사이트 설정을 사용할 수 없는 경우 적절 한 값을 사용 하 여 [새 사이트 설정을 만들어야](configure/configure-site-settings.md#manage-portal-site-settings) 합니다.

## <a name="configure-token-validity"></a>토큰 유효성 구성

기본적으로 토큰은 15 분 동안 유효 합니다. 토큰의 유효성을 변경 하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 필요한 값으로 설정 합니다. 값은 초 단위로 지정 해야 합니다. 최대값은 1 시간이 될 수 있으며 최소값은 1 분 이어야 합니다. 잘못 된 값을 지정 하는 경우 (예: 영숫자 문자) 15 분의 기본값을 사용 합니다. 최 댓 값 보다 크거나 최소값 보다 작은 값을 지정 하면 기본적으로 최대값과 최소값이 각각 사용 됩니다.

예를 들어 토큰 유효성을 30 분으로 설정 하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 **1800**로 설정 합니다. 토큰 유효성을 1 시간으로 설정 하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 **3600**로 설정 합니다.

## <a name="register-client-id-for-implicit-grant-flow"></a>암시적 권한 부여 흐름에 대 한 클라이언트 ID 등록

이 흐름이 허용 된 포털에서 클라이언트 ID를 등록 해야 합니다. 클라이언트 ID를 등록 하려면 다음 사이트 설정을 만들어야 합니다.

|사이트 설정|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|이 포털에 허용 되는 유효한 클라이언트 ID 값입니다. 값은 세미콜론으로 구분 해야 하며 영숫자 문자와 하이픈을 포함할 수 있습니다. 최대 길이는 36 자입니다.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|특정 클라이언트 ID에 허용 되는 유효한 리디렉션 Uri입니다. 값은 세미콜론으로 구분 해야 합니다. 제공 된 URL은 포털의 올바른 웹 페이지 여야 합니다.|
|||

## <a name="sample-code"></a>샘플 코드

다음 샘플 코드를 사용 하 여 PowerApps 포털 Api에서 OAuth 2.0 암시적 부여를 사용 하는 작업을 시작할 수 있습니다.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>외부 웹 API에서 포털 OAuth 토큰 사용

이 샘플은 ASP.NET 기반 프로젝트 이며 PowerApps 포털에서 발급 한 ID 토큰의 유효성을 검사 하는 데 사용 됩니다. 전체 샘플은 [외부 웹 API와 함께 포털 OAuth 토큰 사용](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample)에서 찾을 수 있습니다.

### <a name="authorize-endpoint-sample"></a>권한 부여 끝점 샘플

이 샘플에서는 권한 부여 끝점이 리디렉션된 URL에서 ID 토큰을 조각으로 반환 하는 방법을 보여 줍니다. 암시적 권한 부여에서 지원 되는 상태 유효성 검사에 대해서도 설명 합니다. 이 샘플은 [끝점 권한 부여 샘플](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js)에서 찾을 수 있습니다.

### <a name="token-endpoint-sample"></a>토큰 끝점 샘플

이 샘플에서는 getAuthenticationToken 함수를 사용 하 여 PowerApps 포털에서 토큰 끝점을 사용 하 여 ID 토큰을 가져오는 방법을 보여 줍니다. 이 샘플은 [토큰 끝점 샘플](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js)에서 찾을 수 있습니다.
