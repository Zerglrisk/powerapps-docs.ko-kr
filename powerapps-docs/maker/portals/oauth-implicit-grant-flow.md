---
title: 포털 내에서 OAuth 2.0 암시적 권한 부여 흐름 사용 | MicrosoftDocs
description: 외부 API에 대한 클라이언트 측 호출을 수행하고 Dynamics 365 포털의 OAuth 암시적 권한 부여 흐름을 사용하여 보안을 유지하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>포털 내에서 OAuth 2.0 암시적 권한 부여 흐름 사용 

이 기능을 사용하면 고객이 외부 API에 대한 클라이언트 쪽 호출을 수행하고 OAuth 암시적 권한 부여 흐름을 사용하여 보안을 유지할 수 있습니다. OAuth 2.0 암시적 권한 부여 흐름 이후에 권한 부여를 위해 외부 API에서 사용할 사용자 ID 정보를 포함하는 보안 액세스 토큰을 얻을 수 있는 끝점을 제공합니다. 로그인한 사용자의 ID 정보는 보안 방식으로 외부 AJAX 호출에 전달됩니다. 이는 개발자가 인증 컨텍스트를 전달하는 데 도움이 될 뿐만 아니라 사용자가 이 메커니즘을 사용하여 API를 보호하는 데도 도움이 됩니다.

OAuth 2.0 암시적 권한 부여 흐름은 클라이언트가 ID 토큰을 가져오기 위해 호출할 수 있는 끝점을 지원합니다. 이 목적을 위해 [승인](#authorize-endpoint-details)과 [토큰](#token-endpoint-details)의 두 개의 끝점이 사용됩니다.

## <a name="authorize-endpoint-details"></a>승인 끝점 세부 정보 

승인 끝점의 URL은 `<portal_url>/_services/auth/authorize`입니다. 승인 끝점은 다음 매개 변수를 지원합니다.

| 매개 변수   | 필수? | 설명                             |
|---------------|-----------|---------------------------------------|
| client_id      | 지원       | 승인 끝점에 대한 호출을 만들 때 전달되는 문자열입니다. 클라이언트 ID가 [포털에 등록되어 있는지](#register-client-id-for-implicit-grant-flow) 확인해야 합니다. 그렇지 않으면 오류가 표시됩니다. 클라이언트 ID는 `aud` 및 `appid` 매개 변수로 토큰의 클레임에 추가되며, 클라이언트가 해당 앱에 대해 반환된 토큰이 맞는지 확인하기 위해 클라이언트에서 사용할 수 있습니다.<br>최대 길이는 36자입니다. 영숫자 문자와 하이픈만 지원됩니다. |
| redirect_uri      | 지원       | 인증 응답이 송수신될 수 있는 포털의 URL입니다. 호출에 사용되는 특정 `client_id`에 대해 등록되어야 하며 등록된 것과 정확히 동일한 값이어야 합니다.            |
| state       | 아니오        | 또한 토큰 응답에 반환되는 요청에 포함된 값입니다. 사용하려는 콘텐츠의 문자열일 수 있습니다. 일반적으로 교차 사이트 요청 위조 공격을 방지하기 위해 임의로 생성된 고유한 값이 사용됩니다.<br>최대 길이는 20자입니다.              |
| nonce   | 아니오        | 클레임으로 결과 ID 토큰에 포함된 클라이언트에서 보낸 문자열 값입니다. 그러면 클라이언트는 이 값을 확인하여 토큰 재생 공격을 완화할 수 있습니다. 최대 길이는 20자입니다.      |
| response_type         | 아니오        | 이 매개 변수는 값으로 `token`만 지원합니다. 이렇게 하면 앱이 승인 끝점에 대한 두 번째 요청을 수행하지 않고 승인 끝점에서 액세스 토큰을 즉시 받을 수 있습니다.                               |
|||

### <a name="successful-response"></a>성공적인 응답

승인 끝점은 응답 URL의 다음 값을 조각으로 반환합니다.

- **token**: 토큰은 포털의 개인 키에 의해 디지털 서명된 JSON 웹 토큰(JWT)으로 반환됩니다.
- **state**: state 매개 변수가 요청에 포함된 경우 응답에 동일한 값이 나타나야 합니다. 앱은 요청과 응답의 상태 값이 동일한지 확인해야 합니다.
- **expires_in**: 액세스 토큰이 유효한 시간(초)입니다.

예를 들어 성공적인 응답은 다음과 같습니다.

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>오류 응답

승인 끝점의 오류는 다음 값을 포함하는 JSON 문서로 반환됩니다.

- **오류 ID**: 동기화 오류의 고유 식별자입니다.
- **오류 메시지**: 승인 오류의 근본 원인을 식별하는 데 도움이 될 수 있는 특정 오류 메시지입니다.
- **상관 관계 ID**: 디버깅 목적으로 사용되는 GUID입니다. 진단 로깅을 활성화한 경우 서버 오류 로그에 상관 관계 ID가 표시됩니다.
- **타임 스탬프**: 오류가 생성된 날짜와 시간입니다.

오류 메시지는 로그인한 사용자의 기본 언어로 표시됩니다. 사용자가 로그인하지 않은 경우 로그인 페이지가 표시되고 사용자가 로그인할 수 있습니다. 예를 들어 오류 응답은 다음과 같습니다.

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>토큰 끝점 세부 정보

`/token` 끝점에 대한 요청을 작성하여 토큰을 가져올 수도 있습니다. 승인 끝점이 별도의 페이지(redirect_uri)에서 토큰 논리를 처리하는 방식에서 승인 끝점과 다르며 토큰 끝점은 동일한 페이지에서 토큰 논리를 처리합니다. 토큰 끝점의 URL은 `<portal_url>/_services/auth/token`입니다. 토큰 끝점은 다음 매개 변수를 지원합니다.

| 매개 변수   | 필수? | 설명                             |
|---------------|-----------|---------------------------------------|
| client_id      | 아니오       | 승인 끝점에 대한 호출을 만들 때 전달되는 문자열입니다. 클라이언트 ID가 [포털에 등록되어 있는지](#register-client-id-for-implicit-grant-flow) 확인해야 합니다. 그렇지 않으면 오류가 표시됩니다. 클라이언트 ID는 `aud` 및 `appid` 매개 변수로 토큰의 클레임에 추가되며, 클라이언트가 해당 앱에 대해 반환된 토큰이 맞는지 확인하기 위해 클라이언트에서 사용할 수 있습니다.<br>최대 길이는 36자입니다. 영숫자 문자와 하이픈만 지원됩니다. |
| redirect_uri      | 아니오       | 인증 응답이 송수신될 수 있는 포털의 URL입니다. 호출에 사용되는 특정 `client_id`에 대해 등록되어야 하며 등록된 것과 정확히 동일한 값이어야 합니다.            |
| state       | 아니오        | 또한 토큰 응답에 반환되는 요청에 포함된 값입니다. 사용하려는 콘텐츠의 문자열일 수 있습니다. 일반적으로 교차 사이트 요청 위조 공격을 방지하기 위해 임의로 생성된 고유한 값이 사용됩니다.<br>최대 길이는 20자입니다.              |
| nonce   | 아니오        | 클레임으로 결과 ID 토큰에 포함된 클라이언트에서 보낸 문자열 값입니다. 그러면 클라이언트는 이 값을 확인하여 토큰 재생 공격을 완화할 수 있습니다. 최대 길이는 20자입니다.      |
| response_type         | 아니오        | 이 매개 변수는 값으로 `token`만 지원합니다. 이렇게 하면 앱이 승인 끝점에 대한 두 번째 요청을 수행하지 않고 승인 끝점에서 액세스 토큰을 즉시 받을 수 있습니다.                               |
|||

> [!NOTE]
> `client_id``redirect_uri``state` 및 `nonce` 매개 변수는 선택 사항이지만, 통합이 안전한지 확인하기 위해 이를 사용하는 것이 좋습니다.

### <a name="successful-response"></a>성공적인 응답

토큰 끝점은 state 및 expires_in을 응답 헤더 및 양식 본문의 토큰으로 반환합니다.

### <a name="error-response"></a>오류 응답

토큰 끝점의 오류는 다음 값을 포함하는 JSON 문서로 반환됩니다.

- **오류 ID**: 동기화 오류의 고유 식별자입니다.
- **오류 메시지**: 승인 오류의 근본 원인을 식별하는 데 도움이 될 수 있는 특정 오류 메시지입니다.
- **상관 관계 ID**: 디버깅 목적으로 사용되는 GUID입니다. 진단 로깅을 활성화한 경우 서버 오류 로그에 상관 관계 ID가 표시됩니다.
- **타임 스탬프**: 오류가 생성된 날짜와 시간입니다.

오류 메시지는 로그인한 사용자의 기본 언어로 표시됩니다. 사용자가 로그인하지 않은 경우 로그인 페이지가 표시되고 사용자가 로그인할 수 있습니다. 예를 들어 오류 응답은 다음과 같습니다.

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>ID 토큰 유효성 검사

ID 토큰을 얻는 것 만으로는 사용자를 인증할 수 없습니다. 또한 토큰 서명의 유효성을 검사하고 앱의 요구 사항에 따라 토큰의 클레임을 확인해야 합니다. 공개 토큰 끝점은 포털의 공개 키를 제공하며, 포털에서 제공하는 토큰 서명의 유효성을 검사하는 데 사용할 수 있습니다. 공개 토큰 끝점의 URL은 `<portal_url>/_services/auth/publickey`입니다.

## <a name="turn-implicit-grant-flow-on-or-off"></a>암시적 권한 부여 흐름 켜기 또는 끄기

기본적으로 암시적 권한 부여 흐름이 사용됩니다. 암시적 권한 부여 흐름을 끄려면 **Connector/ImplicitGrantFlowEnabled** 사이트 설정 값을 **False**로 설정합니다.

포털에서 이 사이트 설정을 사용할 수 없는 경우 적절한 값을 사용하여 [새 사이트 설정을 생성](configure-site-settings.md#manage-portal-site-settings)해야 합니다.

## <a name="configure-token-validity"></a>토큰 유효성 구성

기본적으로 토큰은 15분 동안 유효합니다. 토큰의 유효성을 변경하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 필수 값으로 설정합니다. 값은 초 단위로 지정해야 합니다. 최대값은 1시간 일 수 있으며 최소값은 1분 이어야 합니다. 잘못된 값이 지정된 경우(예: 영숫자) 기본값인 15분이 사용됩니다. 최대값보다 크거나 최소값보다 작은 값을 지정하는 경우 기본적으로 최대값 및 최소값이 각각 사용됩니다.

예를 들어 토큰 유효성을 30분으로 설정하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 **1800**으로 설정합니다. 토큰 유효성을 1시간으로 설정하려면 **ImplicitGrantFlow/TokenExpirationTime** 사이트 설정 값을 **3600**으로 설정합니다.

## <a name="register-client-id-for-implicit-grant-flow"></a>암시적 권한 부여 흐름에 대한 클라이언트 ID 등록

이 흐름이 허용되는 포털에 클라이언트 ID를 등록해야 합니다. 클라이언트 ID를 등록하려면 다음 사이트 설정을 만들어야 합니다.

|사이트 설정|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|이 포털에 허용되는 유효한 클라이언트 ID 값입니다. 값은 세미콜론으로 구분해야 하며 영숫자 문자와 하이픈을 포함할 수 있습니다. 최대 길이는 36자입니다.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|특정 클라이언트 ID에 대해 허용되는 유효한 리디렉션 URI입니다. 값은 세미콜론으로 구분해야 합니다. 제공된 URL은 포털의 유효한 웹 페이지여야 합니다.|
|||

## <a name="sample-code"></a>샘플 코드

다음 샘플 코드를 사용하여 Dynamics 365 포털 API와 함께 OAuth 2.0 암시적 부여 사용을 시작할 수 있습니다.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>외부 웹 API와 함께 포털 OAuth 토큰 사용

이 샘플은 ASP.NET 기반 프로젝트이며 Dynamics 365 포털에서 발급한 ID 토큰의 유효성을 검사하는 데 사용됩니다. 전체 샘플은 [외부 웹 API와 함께 포털 OAuth 토큰 사용](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample)에서 찾을 수 있습니다.

### <a name="authorize-endpoint-sample"></a>승인 끝점 샘플

이 샘플은 승인 끝점이 리디렉션된 URL에서 ID 토큰을 조각으로 반환하는 방법을 보여줍니다. 또한 암시적 부여에서 지원되는 상태 검증도 다룹니다. 샘플은 [승인 끝점 샘플](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js)에서 찾을 수 있습니다.

### <a name="token-endpoint-sample"></a>토큰 끝점 샘플

이 샘플은 getAuthenticationToken 함수를 사용하여 Dynamics 365 포털에서 토큰 끝점을 사용하여 ID 토큰을 가져오는 방법을 보여줍니다. 샘플은 [토큰 끝점 샘플](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js)에서 찾을 수 있습니다.
