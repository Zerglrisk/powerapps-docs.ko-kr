---
title: 포털에 대 한 OAuth2 공급자 설정 구성 | MicrosoftDocs
description: 포털에 대 한 OAuth2 공급자 설정을 추가 하 고 구성 하는 지침을 제공 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 25a26e6298fa3257f3db6d04ffd2937e8e71d3a1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978534"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>포털에 대 한 OAuth2 공급자 설정 구성

OAuth 2.0 기반 외부 id 공급자는 "응용 프로그램"을 타사 서비스에 등록 하 여 "클라이언트 ID" 및 "클라이언트 암호" 쌍을 가져와야 합니다. 이 응용 프로그램에는 id 공급자가 사용자를 다시 포털 (신뢰 당사자)에 게 보낼 수 있는 리디렉션 URL을 지정 해야 하는 경우가 많습니다. 클라이언트 ID와 클라이언트 암호는 신뢰 당사자에서 id 공급자로 보안 연결을 설정 하기 위해 포털 사이트 설정으로 구성 됩니다. 설정은 [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [twitterauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)및 [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) 클래스의 속성을 기반으로 합니다.  

지원 되는 공급자는 다음과 같습니다.

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 계정
- Twitter
- Facebook
- 로그
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>OAuth 응용 프로그램 만들기

일반적으로 OAuth 공급자가 리디렉션 URI 값을 요구 하는 앱 설정을 사용 하는 경우 공급자가 리디렉션 URI 유효성 검사를 수행 하는 방법에 따라 [공급자\] http://portal.contoso.com/signin-\<http://portal.contoso.com/or> 지정 합니다. 일부 공급자는와 함께 전체 URL 경로를 지정 해야 합니다. 도메인 이름). 리디렉션 URI에서 \[공급자\] 대신 공급자 이름을 대체 합니다.

### <a name="google"></a>로그

[Google OAuth2 API 자격 증명 지침](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. [Google 개발자 콘솔](https://console.developers.google.com/) 열기  
2. API 프로젝트를 만들거나 기존 프로젝트를 엽니다.
3. Api **& auth** &gt;**api**로 이동 하 고 **소셜 API**아래에서**Google + api**를 선택한 다음**api 사용** 을 선택 합니다.
4. **Api & auth** &gt;**동의 화면**으로 이동 합니다.
    - **전자 메일 주소**를 지정 합니다.
    - 사용자 지정**제품 이름을**지정 합니다.
    - **저장**을 선택 합니다.
5. **Api & auth** &gt;**자격 증명** 으로 이동 하 여 새 클라이언트 ID를 만듭니다.
   - 응용 프로그램 유형:**웹 응용 프로그램**
   - 권한 있는 [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] 원본: http://portal.contoso.com
   - 권한 있는 리디렉션 Uri: http://portal.contoso.com/signin-google 
   - **클라이언트 ID 만들기**를 선택 합니다.

### <a name="facebook-app-settings"></a>Facebook 앱 설정

1. [Facebook 개발자 앱 대시보드](https://developers.facebook.com/apps) 열기  
2. **새 앱 추가를**선택 합니다.
3. **웹 사이트**를 선택 합니다.
4. **건너뛰기 및 앱 ID 만들기를**선택 합니다.
    - **표시 이름을**지정 합니다.
    - **범주**를 선택 합니다.
    - **앱 ID 만들기**를 선택 합니다.

5. 새 앱에 대 한 대시보드에서 **설정** &gt;**기본** (탭)으로 이동 하 고 다음 세부 정보를 추가 합니다.
    - 앱 도메인 (선택 사항): portal.contoso.com 
    - 담당자 전자 메일: *선택한&gt;전자 메일 주소&lt;* 
    - **플랫폼 추가**를 선택 하 고 **웹 사이트**를 선택 합니다. 
    - 사이트 URL: http://portal.contoso.com/ 또는 http://portal.contoso.com/signin-facebook

6. **변경 내용 저장**을 선택 합니다.
7. **상태 & 검토** &gt; **상태** 탭으로 이동 합니다.
8. 앱과 모든 기능을 일반 공용에서 사용할 수 있도록 설정 하 라는 메시지가 표시 되 면 **예** 를 선택 합니다. 이 설정을 사용 하도록 설정 하려면 위의 5 단계에서 유효한 데이터를 입력 해야 합니다.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>응용 프로그램 설정 [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 계정 개발자 센터](https://account.live.com/developers/applications/index) 열기  
2. **응용 프로그램 만들기** 를 선택 하 고 **응용 프로그램 이름을**지정 합니다.
3. **동의** 함을 선택 하 여 사용 약관에 동의 합니다.
4. **설정** &gt;**API 설정**으로 이동한 후 리디렉션 URL을으로 설정 http://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Twitter 앱 설정

1. [Twitter 응용 프로그램 관리](https://apps.twitter.com/)를 엽니다. 
2. **새 앱 만들기**를 선택 합니다.

    - 앱에 대 한 **이름** 및 **설명을** 지정 합니다.
    - 웹 사이트 URL을 http://portal.contoso.com 로 설정 합니다.
    - 콜백 URL을 http://portal.contoso.com 또는 http://portal.contoso.com/signin-twitter 로 설정 합니다.

3. **Twitter 응용 프로그램 만들기**를 선택 합니다.

### <a name="linkedin-app-settings"></a>LinkedIn 앱 설정

1. [LinkedIn Developer 네트워크](https://www.linkedin.com/secure/developer)를 엽니다.  
2. **새 응용 프로그램 추가**를 선택 합니다.

    - **응용 프로그램 이름**, **설명**등을 지정 합니다.
    - 웹 사이트 URL을 http://portal.contoso.com 로 설정 합니다.
    - OAuth 사용자 계약/기본 범위를 설정 합니다. r\_basicprofie 및 r\_emailaddress
    - OAuth 2.0 리디렉션 url 설정: http://portal.contoso.com/signin-linkedin.

3. **응용 프로그램 추가**를 선택 합니다.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN 앱 설정

1. [Yahoo! 개발자 네트워크](https://developer.yahoo.com/apps)를 엽니다.
2. **앱 만들기**를 선택 합니다.
    
    - **응용 프로그램 이름을**지정 합니다.
    - 응용 프로그램 유형: **웹 응용 프로그램**입니다.
    - 콜백 도메인: portal.contoso.com

3. **앱 만들기**를 선택 합니다.

## <a name="create-site-settings-by-using-oauth2"></a>OAuth2를 사용 하 여 사이트 설정 만들기

각 공급자의 응용 프로그램 대시보드는 각 응용 프로그램에 대 한 클라이언트 ID (앱 ID, 소비자 키) 및 클라이언트 암호 (앱 암호, 소비자 암호)를 표시 합니다. 이러한 두 값을 사용 하 여 포털 사이트 설정을 구성 합니다.

>[!Note]
> 표준 OAuth2 구성에는 다음 설정 (Facebook을 예로 사용)만 필요 합니다.
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

사이트 설정 이름의 `[provider]` 태그를 Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn 또는 Twitter의 특정 id 공급자 이름으로 대체 합니다.

|**사이트 설정 이름**                                           |**설명**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 인증/등록/ExternalLoginEnabled                | 외부 계정 로그인 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[공급자\]/ClientId                   | 필수. 공급자 응용 프로그램의 클라이언트 ID 값입니다. 앱 ID 또는 소비자 키 라고도 할 수 있습니다.  이전 버전과의 호환성을 위해 다음 설정 이름이 허용 됩니다. Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[공급자\]/ClientSecret               | 필수. 공급자 응용 프로그램의 클라이언트 암호 값입니다. 앱 암호 또는 소비자 암호 라고도 합니다.  이전 버전과의 호환성을 위해 다음 설정 이름이 허용 됩니다. Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[공급자\]/AuthenticationType         | OWIN authentication 미들웨어 유형입니다. 예: yahoo. [authenticationoptions. authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentication/OpenAuth/\[공급자\]/Scope                      | 요청에 대 한 쉼표로 구분 된 권한 목록입니다. [microsoftaccountauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentication/OpenAuth/\[공급자\]/캡션                    | 사용자가 로그인 사용자 인터페이스에 표시할 수 있는 텍스트입니다. [microsoftaccountauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[공급자\]/BackchannelTimeout         | 백 채널 통신의 시간 제한 값 (밀리초)입니다. [microsoftaccountauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentication/OpenAuth/\[provider\]/Shpath               | 응용 프로그램의 기본 경로 내에서 사용자 에이전트가 반환 될 요청 경로입니다. [microsoftaccountauthenticationoptions 경로](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx)입니다.                                                         |  
| Authentication/OpenAuth/\[공급자\]/SignInAsAuthenticationType | 실제로**userClaimsIdentity**를 발급 하는 다른 인증 미들웨어의 이름입니다. [microsoftaccountauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentication/OpenAuth/\[공급자\]/AuthenticationMode         | OWIN authentication 미들웨어 모드입니다. [authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>참고 항목

[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대 한 인증 id 설정](set-authentication-identity.md)  
[포털에 대 한 OPEN ID Connect 공급자 설정](configure-openid-settings.md)   
[포털에 대 한 WS-FEDERATION 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대 한 SAML 2.0 공급자 설정](configure-saml2-settings.md)
