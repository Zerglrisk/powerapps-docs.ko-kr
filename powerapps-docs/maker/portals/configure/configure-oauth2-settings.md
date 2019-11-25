---
title: 포털에 대한 OAuth2 공급자 설정 구성 | MicrosoftDocs
description: 포털의 OAuth2 공급자 설정을 추가 및 구성하는 방법에 대해 설명합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: be576425067079549d3174e6d6306814a6ddb13a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755450"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>포털에 대한 OAuth2 공급자 설정값 구성

OAuth 2.0 기반의 외부 ID 공급자는 "클라이언트 ID" 및 "클라이언트 비밀" 쌍을 획득하기 위해 제3자 서비스로 "응용 프로그램"을 렌더링하는 것을 포함합니다. 이 응용 프로그램은 종종 ID 공급자가 사용자를 포털(신뢰측)로 도로 보낼 수 있는 리디렉션 URL의 지정을 요구합니다. 클라이언트 ID와 클라이언트 비밀은 신뢰측으로부터 ID 공급자에게 보안 연결을 확립하기 위해 포털 사이트 설정으로 구성됩니다. 설정은 [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx), 및 [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) 클래스의 속성에 근거합니다.  

지원되는 공급자:

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 계정
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>OAuth 응용 프로그램 생성

일반적으로, OAuth 제공자가 리디렉션 URI 값을 요구하는 앱 설정을 사용하는 경우, 제공자가 리디렉션 URI 유효성 검사를 어떻게 수행하느냐에 따라 <https://portal.contoso.com/or> https://portal.contoso.com/signin-\[제공자\]를 지정하십시오(일부 제공자는 전체 URL 경로를 도메인 이름과 함께 지정할 것을 요구합니다). 리디렉션 URI의 \[공급자\] 자리에 공급자 이름을 대체하십시오.

### <a name="google"></a>Google

[Google OAuth2 API 자격 증명 지침](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. [Google 개발자 콘솔](https://console.developers.google.com/) 열기  
2. API 프로젝트 만들기 또는 기존 프로젝트 열기
3. **API 및 인증** &gt;**API**로 이동하여 **소셜 API** 아래에서 **Google+ API**, **API 사용**을 차례로 선택합니다.
4. **API 및 인증** &gt;**동의 화면**으로 이동합니다.
    - **전자 메일 주소**를 지정합니다.
    - 사용자 지정 **제품 이름**을 지정합니다.
    - **저장**을 선택합니다.
5. **API및 인증** &gt;**자격 증명**으로 이동하여 새 클라이언트 ID를 만듭니다.
   - 응용 프로그램 유형: **웹 응용 프로그램**
   - 승인된 [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] 출처:https://portal.contoso.com
   - 승인된 리디렉션 URI: https://portal.contoso.com/signin-google 
   - **클라이언트 ID 만들기**를 선택합니다.

### <a name="facebook-app-settings"></a>Facebook 앱 설정

1. [Facebook 개발자 앱 대시보드](https://developers.facebook.com/apps)를 엽니다.  
2. **새 앱 추가**를 선택합니다.
3. **웹사이트**를 선택합니다.
4. **건너뛰기 및 앱 ID 만들기**를 선택합니다.
    - **표시 이름**을 지정합니다.
    - **범주**를 선택합니다.
    - **앱 ID 만들기**를 선택합니다.

5. 새 앱의 대시보드에서 **설정** &gt;**기본**(탭)으로 이동하여 다음 세부 정보를 추가합니다.
    - 앱 도메인(선택 사항): portal.contoso.com 
    - 연락처 이메일: *&lt;귀하가 원하는 이메일 주소&gt;* 
    - **플랫폼 추가**를 선택한 다음 **웹사이트**를 선택합니다. 
    - 사이트 URL: https://portal.contoso.com/ 또는 https://portal.contoso.com/signin-facebook

6. **변경 내용 저장**을 선택합니다.
7. **상태 및 검토** &gt; **상태** 탭으로 이동합니다.
8. 앱을 만들고 및 모든 기능을 일반 대중에게 제공하라는 메시지가 표시되면 **예**를 선택합니다. 이 설정을 사용하려면 위의 5단계에서 유효한 데이터를 채워야 합니다.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 응용 프로그램 설정

1. [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 계정 개발자 센터](https://account.live.com/developers/applications/index)를 엽니다.  
2. **응용 프로그램 만들기**를 선택하고 **응용 프로그램 이름**을 지정합니다.
3. **동의함**을 선택하여 이용 약관에 동의합니다.
4. **설정** &gt;**API 설정**으로 이동한 다음 리디렉션 URL을 https://portal.contoso.com/signin-microsoft로 설정합니다. 

### <a name="twitter-apps-settings"></a>Twitter 앱 설정

1. [Twitter 앱 관리](https://apps.twitter.com/)를 엽니다. 
2. **새 응용 프로그램 만들기**를 선택합니다.

    - 앱의 **이름** 및 **설명**을 지정합니다.
    - 웹 사이트 URL을 https://portal.contoso.com으로 설정합니다.
    - 콜백 URL을 https://portal.contoso.com 또는 https://portal.contoso.com/signin-twitter로 설정합니다.

3. **Twitter 앱 만들기**를 선택합니다.

### <a name="linkedin-app-settings"></a>LinkedIn 앱 설정

1. [LinkedIn 개발자 네트워크](https://www.linkedin.com/secure/developer)를 엽니다.  
2. **새 응용 프로그램 추가**를 선택합니다.

    - **응용 프로그램 이름**, **설명** 등을 지정합니다.
    - 웹 사이트 URL을 https://portal.contoso.com으로 설정합니다.
    - OAuth 사용자 계약/기본 범위 설정: r\_basicprofie and r\_emailaddress
    - OAuth 2.0 리디렉션 url을 https://portal.contoso.com/signin-linkedin으로 설정합니다.

3. **응용 프로그램 추가**를 선택합니다.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN 앱 설정

1. [Yahoo! 개발자 네트워크](https://developer.yahoo.com/apps)를 엽니다.
2. **앱 만들기**를 선택합니다.
    
    - **애플리케이션 이름**을 지정합니다.
    - 응용 프로그램 유형은 **웹 응용 프로그램**입니다.
    - 콜백 도메인: portal.contoso.com

3. **앱 만들기**를 선택합니다.

## <a name="create-site-settings-by-using-oauth2"></a>OAuth2를 사용하여 사이트 설정 만들기

각 공급자를 위한 응용 프로그램 대시보드가 각 응용 프로그램에 대한 클라이언트 ID(앱 ID, 소비자 키)와 클라이언트 비밀(앱 비밀, 소비자 비밀)을 표시할 것입니다. 이 두 값을 사용하여 포털 사이트 설정을 구성하십시오.

>[!Note]
> 표준 OAuth2 구성에는 다음 설정만 필요합니다(예: Facebook).
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

사이트 설정 이름의 `[provider]` 태그를 다음: Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Twitter와 같은 특정 ID 제공자 이름으로 대체하십시오.

|**사이트 설정 이름**                                           |**설명**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | 외부 계정 로그인 및 등록을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[공급자\]/ClientId                   | 필수 특성: 공급자 응용 프로그램의 클라이언트 ID 값. 앱 ID 또는 소비자 키로 지칭될 수도 있습니다.  구버전과의 호환성을 위해 다음 설정 이름이 허용됩니다. Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[공급자\]/ClientSecret               | 필수 특성: 공급자 응용 프로그램의 클라이언트 비밀 값. 앱 비밀 또는 소비자 비밀로 지칭될 수도 있습니다.  구버전과의 호환성을 위해 다음 설정 이름이 허용됩니다. Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[공급자\]/AuthenticationType         | OWIN 인증 미들웨어 타입. 예: yahoo [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentication/OpenAuth/\[공급자\]/Scope                      | 쉼표로 구분된 요청할 권한 목록. [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentication/OpenAuth/\[공급자\]/Caption                    | 로그인 사용자 인터페이스에 사용자가 표시할 수 있는 텍스트. [microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[공급자\]/BackchannelTimeout         | 백채널 통신을 위한 밀리초 단위의 타임아웃 값. [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentication/OpenAuth/\[공급자\]/CallbackPath               | 사용자-에이전트가 반환될 응용 프로그램의 기저 경로 내의 요청 경로. [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Authentication/OpenAuth/\[공급자\]/SignInAsAuthenticationType | **userClaimsIdentity**의 실제 발행을 담당할 다른 인증 미들웨어의 이름. [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentication/OpenAuth/\[공급자\]/AuthenticationMode         | OWIN 인증 미들웨어 모드입니다. [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>참조

[포털 인증 구성](configure-portal-authentication.md)  
[포털의 인증 ID 설정](set-authentication-identity.md)  
[포털에 대한 ID 연결 공급자 열기](configure-openid-settings.md)   
[포털에 대한 WS-Federation 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대한 SAML 2.0 공급자 설정](configure-saml2-settings.md)
