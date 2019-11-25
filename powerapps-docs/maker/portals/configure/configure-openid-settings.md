---
title: 포털에 대한 OpenID 연결 공급자 설정 구성 | MicrosoftDocs
description: 포털의 OpenID Connect 공급자 설정을 추가 및 구성하는 방법에 대해 설명합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2b4d31165ccd12b2cb5c8c2a4c8ec6f9dd04a7c7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755362"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>포털에 대한 오픈 ID 연결 공급자 설정값 구성

[OpenID 연결](https://openid.net/connect/) 외부 ID 공급자는 오픈 ID 연결 [규격](https://openid.net/developers/specs/)을 준수하는 서비스입니다. 공급자 통합은 공급자와 연계되어 있는 권한(또는 발행자) URL을 찾습니다. 인증 워크플로 동안 요구되는 메타데이터를 공급하는 권한으로부터 구성 URL을 결정할 수 있습니다. 공급자 설정은 [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx) 클래스의 속성에 근거합니다.

권한 URL의 예:

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 응용 프로그램&gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

각 OpenID Connect 공급자는 OAuth 2.0 공급자의 응용 프로그램과 유사한 응용 프로그램의 등록 및 클라이언트 ID 확보도 요구합니다. 권한 URL과 생성된 애플리케이션 클라이언트 ID는 포털과 ID 공급자 사이의 외부 인증을 사용하기 위해 요구되는 설정입니다.

> [!Note]
> 주소 호환성 문제로 기저 라이브러리가 아직 릴리스 초기 단계에 있기 때문에 Google OpenID Connect 종점은 현재 지원되지 않습니다. [포털에 대한 OAuth2 공급자 설정](configure-oauth2-settings.md) 끝점을 대신 사용할 수 있습니다.

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]의 OpenID 설정을 지정합니다.

시작하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)에 로그인하여 디렉터리를 생성하거나 기존 디렉터리를 선택하십시오. 디렉터리를 사용할 수 있을 때 지시를 따라 디렉터리에 [응용 프로그램을 추가](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)하십시오.  

1. 디렉터리의 **응용 프로그램** 메뉴 아래의 **추가**를 선택합니다.
2. **내 조직이 개발하는 응용 프로그램 추가**를 선택합니다.
3. 응용 프로그램에 대한 사용자 지정 **이름**을 지정한 다음, **웹 응용 프로그램 및/또는 웹 API** 유형을 선택합니다.
4. **로그인 URL** 및 **앱 ID URI**을 위해 두 필드를 위한 포털의 URL을 지정합니다 https://portal.contoso.com/
5. 이 시점에서 새 애플리케이션이 생성됩니다. 메뉴에서 **구성** 섹션으로 이동합니다.

    **단일 로그인** 섹션에서 URL https://portal.contoso.com/signin-azure-ad에 경로를 포함하기 위해 첫 번째 **회신 URL** 항목을 업데이트합니다. 이는 **RedirectUri** 사이트 설정값에 해당됩니다

6. **속성** 섹션에서 **클라이언트 ID** 필드를 찾습니다. 이는 **ClientId** 사이트 설정값에 해당됩니다.
7. 바닥글 메뉴에서 **끝점 보기**를 선택한 다음 **페더레이션 메타데이터 문서** 필드를 참고합니다.

URL의 왼쪽 부분이 **권한** 값으로서 다음 형식 중 하나입니다.

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

서비스 구성 URL을 가져오려면 FederationMetadata/2007-06/FederationMetadata.xml 경로 꼬리를 .well-known/openid-configuration 경로로 바꿉니다. 인스턴스의 경우, <https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

이는 **MetadataAddress** 사이트 설정값에 해당됩니다.

### <a name="related-site-settings"></a>관련된 사이트 설정값

위의 응용 프로그램을 참조하는 포털 사이트 설정값을 적용합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성은 다음의 설정만을 사용합니다(예시 값).                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId - fedcba98-7654-3210-fedc-ba9876543210                                      
>   클라이언트 ID와 권한 URL은 같은 값을 포함하지 않기 때문에 별도로 가져와야 합니다.           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri - https://portal.contoso.com/signin-azure-ad
 
\[provider\] 태그의 레이블을 대체함으로써 여러 ID 공급자들을 구성할 수 있습니다. 각 고유 레이블은 ID 공급자에 관련된 설정값 그룹을 형성합니다. 예: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


|                          사이트 설정 이름                           |                                                                                                                                                                                                         설명                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Authentication/Registration/ExternalLoginEnabled           |                                                                                                                                                                         외부 계정 로그인 및 등록을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                         |
|         Authentication/OpenIdConnect/\[공급자\]/Authority          |                                               필수 특성: OpenIdConnect 콜을 할 때 사용할 권한. 예: `https://login.microsoftonline.com/contoso.onmicrosoft.com/` 자세한 내용은 [OpenIdConnectAuthenticationOptions.Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx)를 참조하십시오.                                                |
|      Authentication/OpenIdConnect/\[공급자\]/MetadataAddress       | 메타데이터를 획득하기 위한 발견 종점. 일반적으로 path:/.well-known/openid-configuration으로 끝납니다. 예: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration` 자세한 내용은 [OpenIdConnectAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx)를 참조하십시오. |
|     Authentication/OpenIdConnect/\[공급자\]/AuthenticationType     |                                   OWIN 인증 미들웨어 타입. 서비스 구성 메타데이터에 발행자 값을 지정합니다. 예: `https://sts.windows.net/contoso.onmicrosoft.com/` 자세한 내용은 [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)을 참조하십시오.                                   |
|          Authentication/OpenIdConnect/\[공급자\]/ClientId          |                                                  필수 특성: 공급자 응용 프로그램의 클라이언트 ID 값. "앱 ID" 또는 "소비자 키"로 지칭될 수도 있습니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx)를 참조하십시오.                                                   |
|        Authentication/OpenIdConnect/\[공급자\]/ClientSecret        |                                              공급자 응용 프로그램의 클라이언트 비밀 값. "앱 비밀" 또는 "소비자 비밀"로 지칭될 수도 있습니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx)을 참조하십시오.                                              |
|        Authentication/OpenIdConnect/\[공급자\]/RedirectUri         |                                                        권장. AD FS WS-연합 피동 종점. 예: https://portal.contoso.com/signin-saml2 자세한 내용은 [OpenIdConnectAuthenticationOptions.RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx)를 참조하십시오.                                                        |
|          Authentication/OpenIdConnect/\[공급자\]/Caption           |                                                              권장. 로그인 사용자 인터페이스에 사용자가 표시할 수 있는 텍스트. 기본값: \[공급자\] 자세한 내용은 [OpenIdConnectAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx)을 참조하십시오.                                                               |
|          Authentication/OpenIdConnect/\[공급자\]/Resource          |                                                                                                       '리소스'. 자세한 내용은 [OpenIdConnectAuthenticationOptions.Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx)를 참조하십시오.                                                                                                        |
|        Authentication/OpenIdConnect/\[공급자\]/ResponseType        |                                                                                                'response\_type'입니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx)을 참조하십시오.                                                                                                 |
|           Authentication/OpenIdConnect/\[공급자\]/Scope            |                                                                                공백으로 구분된 요청할 권한 목록. 기본값: openid 자세한 내용은 [OpenIdConnectAuthenticationOptions.Scope](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx)을 참조하십시오.                                                                                 |
|        Authentication/OpenIdConnect/\[공급자\]/CallbackPath        |                      인증 콜백을 처리할 제약 경로 옵션. 제공되지 않고 RedirectUri를 사용할 수 있는 경우, 이 값은 RedirectUri에서 생성될 것입니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx)를 참조하십시오.                      |
|     Authentication/OpenIdConnect/\[공급자\]/BackchannelTimeout     |                                                                백채널 통신을 위한 타임아웃 값. 예: 00:05:00(5분) 자세한 내용은 [OpenIdConnectAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx)을 참조하십시오.                                                                |
| Authentication/OpenIdConnect/\[공급자\]/RefreshOnIssuerKeyNotFound |                                      SecurityTokenSignatureKeyNotFoundException 후에 메타데이터 새로 고침을 시도해야 하는지를 결정합니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx)를 참조하십시오.                                       |
|      Authentication/OpenIdConnect/\[공급자\]/UseTokenLifetime      |                                               인증 세션 수명(예: 쿠키)이 인증 토큰의 수명과 일치함을 나타냅니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx)을 참조하십시오.                                               |
|     Authentication/OpenIdConnect/\[공급자\]/AuthenticationMode     |                                                                                                     OWIN 인증 미들웨어 모드입니다. 자세한 내용은 [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)를 참조하십시오.                                                                                                     |
| Authentication/OpenIdConnect/\[공급자\]/SignInAsAuthenticationType |                                                   System.Security.Claims.ClaimsIdentity를 생성할 때 사용되는 인증 타입. 자세한 내용은 [OpenIdConnectAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx)을 참조하십시오.                                                   |
|   Authentication/OpenIdConnect/\[공급자\]/PostLogoutRedirectUri    |                                                                                 'post\_logout\_redirect\_uri'입니다. 자세한 내용은 [OpenIdConnectAuthenticationOptions.PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx)를 참조하십시오.                                                                                 |
|       Authentication/OpenIdConnect/\[공급자\]/ValidAudiences       |                                                                                                  쉼표로 구분된 대상 URL 목록. 자세한 내용은 [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)를 참조하십시오.                                                                                                  |
|        Authentication/OpenIdConnect/\[공급자\]/ValidIssuers        |                                                                                                       쉼표로 구분된 발행자 URL 목록. 자세한 내용은 [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)를 참조하십시오.                                                                                                       |
|         Authentication/OpenIdConnect/\[공급자\]/ClockSkew          |                                                                                                                                                                                        시간 유효성을 검사할 때 적용할 클록 스큐입니다.                                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[공급자\]/NameClaimType        |                                                                                                                                                                              이름 클레임을 저장하기 위해 ClaimsIdentity가 사용하는 클레임 타입.                                                                                                                                                                              |
|       Authentication/OpenIdConnect/\[공급자\]/RoleClaimType        |                                                                                                                                                                              역할 클레임을 저장하기 위해 ClaimsIdentity가 사용하는 클레임 타입.                                                                                                                                                                              |
|   Authentication/OpenIdConnect/\[공급자\]/RequireExpirationTime    |                                                                                                                                                                              토큰이 '만료' 값을 가져야 할지 여부를 표시하는 값입니다.                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[공급자\]/RequireSignedTokens     |                                                                                                                               서명되지 않은 경우 System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>이 유효할 수 있는지의 여부를 표시하는 값.                                                                                                                                |
|      Authentication/OpenIdConnect/\[공급자\]/SaveSigninToken       |                                                                                                                                                                        세션 생성시 원래 토큰이 저장되는지를 통제하는 부울값.                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[공급자\]/ValidateActor        |                                                                                                                                                            System.IdentityModel.Tokens.JwtSecurityToken.Actor를 검증해야 하는지의 여부를 표시하는 값.                                                                                                                                                            |
|      Authentication/OpenIdConnect/\[공급자\]/ValidateAudience      |                                                                                                                                                                       토큰의 유효성을 검사하는 동안 대상의 유효성을 검사할지 제어하는 부울입니다.                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[공급자\]/ValidateIssuer       |                                                                                                                                                                        토큰 검증시 발행자가 검증될지를 통제하는 부울값.                                                                                                                                                                         |
|      Authentication/OpenIdConnect/\[공급자\]/ValidateLifetime      |                                                                                                                                                                       토큰 검증시 수명 시간이 검증될지를 통제하는 부울값.                                                                                                                                                                        |
|  Authentication/OpenIdConnect/\[공급자\]/ValidateIssuerSigningKey  |                                                                                                                  securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>을 서명한 System.IdentityModel.Tokens.SecurityKey의 검증이 호출되는지를 통제하는 부울값.                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>다중 테넌트 Azure Active Directory 응용 프로그램을 사용하여 인증 활성화

[!include[](../../../includes/pn-azure-active-directory.md)]에 등록된 다중 테넌트 응용 프로그램을 사용하여 특정 테넌트를 허용하지 않고 [!include[](../../../includes/pn-azure-shortest.md)]의 모든 테넌트의 [!include[](../../../includes/pn-azure-active-directory.md)] 사용자를 수락하도록 포털을 구성할 수 있습니다. 멀티 테넌시를 활성화하려면, [!include[](../../../includes/pn-azure-active-directory.md)] 응용 프로그램에서 **다중 테넌트** 스위치를 **예**로 설정합니다.

![Azure Active Directory 애플리케이션에서 멀티 테넌시 사용](../media/enable-multi-tenancy.png "Azure Active Directory 애플리케이션에서 멀티 테넌시 사용")

### <a name="related-site-settings"></a>관련된 사이트 설정값

[provider] 태그의 레이블을 대체함으로써 여러 ID 공급자들을 구성할 수 있습니다. 각 고유 레이블은 ID 공급자에 관련된 설정값 그룹을 형성합니다. 다중 테넌트 응용 프로그램을 사용하여 [!include[](../../../includes/pn-azure-active-directory.md)]에 대한 인증을 지원하기 위해 포털에서 다음 사이트 설정을 만들거나 구성할 수 있습니다.

|사이트 설정 이름    |설명   |
|---|---|
|Authentication/OpenIdConnect/[공급자]/Authority   |OpenIdConnect 콜을 할 때 사용할 권한. 예: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[공급자]/ClientId   |공급자 응용 프로그램의 클라이언트 ID 값. 앱 ID 또는 소비자 키로 지칭될 수도 있습니다.   |
|Authentication/OpenIdConnect/[공급자]/ExternalLogoutEnabled   |외부 계정 로그인 및 등록을 활성화 또는 불활성화합니다. 이 값을 true로 설정합니다.   |
|Authentication/OpenIdConnect/[공급자]/IssuerFilter   |모든 테넌트에 걸친 모든 발급자와 일치하는 와일드 카드 기반 필터입니다. 대부분의 경우 `https://sts.windows.net/*/` 값을 사용합니다.   |
|Authentication/OpenIdConnect/[공급자]/RedirectUri  |공급자가 인증 응답을 보내는 회신 URL 위치입니다. 예: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[공급자]/ValidateIssuer   |토큰 검증시 발행자가 검증될지를 통제하는 부울값. 이 값을 false로 설정합니다.   |
|||

### <a name="see-also"></a>참조
[포털 인증 구성](configure-portal-authentication.md)  
[포털의 인증 ID 설정](set-authentication-identity.md)  
[포털에 대한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대한 WS-Federation 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  

