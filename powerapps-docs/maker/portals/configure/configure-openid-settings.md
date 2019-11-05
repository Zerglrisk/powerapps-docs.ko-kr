---
title: 포털에 대 한 Openid connect Connect 공급자 설정 구성 | MicrosoftDocs
description: 포털에 대 한 Openid connect Connect 공급자 설정을 추가 하 고 구성 하는 지침을 제공 합니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542779"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>포털에 대 한 Open ID Connect 공급자 설정 구성

[Openid connect connect](https://openid.net/connect/) 외부 id 공급자는 Open ID connect [사양을](https://openid.net/developers/specs/)준수 하는 서비스입니다. 공급자를 통합 하려면 공급자와 연결 된 인증 기관 (또는 발급자) URL을 찾아야 합니다. 구성 URL은 인증 워크플로 중에 필요한 메타 데이터를 제공 하는 기관에서 확인할 수 있습니다. 공급자 설정은 [Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx) 클래스의 속성을 기반으로 합니다.

권한 Url의 예는 다음과 같습니다.

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt ; AD 응용 프로그램&gt;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] /](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

각 Openid connect Connect 공급자는 응용 프로그램 (OAuth 2.0 공급자와 유사)을 등록 하 고 클라이언트 Id를 가져오는 작업도 수행 합니다. 인증 기관 URL과 생성 된 응용 프로그램 클라이언트 Id는 포털 및 id 공급자 간에 외부 인증을 사용 하도록 설정 하는 데 필요한 설정입니다.

> [!Note]
> Google Openid connect Connect 끝점은 현재 지원 되지 않습니다. 기본 라이브러리는 여전히 호환성 문제가 해결 되는 릴리스 초기 단계에 있기 때문입니다. [포털 끝점에 대 한 OAuth2 공급자 설정을](configure-oauth2-settings.md) 대신 사용할 수 있습니다.

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]에 대 한 Openid connect 설정

시작 하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) 에 로그인 하 고 기존 디렉터리를 만들거나 선택 합니다. 디렉터리를 사용할 수 있는 경우 지침에 따라 디렉터리에 [응용 프로그램을 추가](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) 합니다.  

1. 디렉터리의 **응용 프로그램** 메뉴에서 **추가**를 선택 합니다.
2. **내 조직에서 개발 중인 응용 프로그램 추가를**선택 합니다.
3. 응용 프로그램에 대 한 사용자 지정 **이름을** 지정 하 고 **웹 응용 프로그램 및/또는 web API**유형을 선택 합니다.
4. 로그온 **URL** 및 **앱 ID URI**에 대해 두 필드 모두에 대 한 포털의 url을 지정 https://portal.contoso.com/
5. 이때 새 응용 프로그램이 만들어집니다. 메뉴의 **구성** 섹션으로 이동 합니다.

    **Single Sign-On** 섹션에서 첫 번째 **회신 url** 항목을 업데이트 하 여 url: https://portal.contoso.com/signin-azure-ad 에 경로를 포함 합니다. 이는 **Redirecturi** 사이트 설정 값에 해당 합니다.

6. **속성** 섹션에서 **클라이언트 ID** 필드를 찾습니다. 이 값은 **ClientId** 사이트 설정 값에 해당 합니다.
7. 바닥글 메뉴에서 **끝점 보기** 를 선택 하 고 **페더레이션 메타 데이터 문서** 필드를 확인 합니다.

URL의 왼쪽 부분은 **기관** 값 이며 다음 형식 중 하나입니다.

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

서비스 구성 URL을 가져오려면 Federationmetadata.xml/2007-06/Federationmetadata.xml 경로 tail을 경로 (잘 알려진/openid connect-구성)로 바꿉니다. 예를 들어 <https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

이는 **Metadataaddress** 사이트 설정 값에 해당 합니다.

### <a name="related-site-settings"></a>관련 사이트 설정

위의 응용 프로그램을 참조 하는 포털 사이트 설정을 적용 합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성은 다음 설정 (예제 값)만 사용 합니다.                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId-fedcba98-7654-3210-fedc-ba9876543210                                      
>   클라이언트 ID와 기관 URL은 동일한 값을 포함 하지 않으므로 별도로 검색 해야 합니다.           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri- https://portal.contoso.com/signin-azure-ad
 
\[공급자\] 태그의 레이블을 대체 하 여 여러 id 공급자를 구성할 수 있습니다. 각 고유 레이블은 id 공급자와 관련 된 설정 그룹을 형성 합니다. 예: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


|                          사이트 설정 이름                           |                                                                                                                                                                                                         설명                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           인증/등록/ExternalLoginEnabled           |                                                                                                                                                                         외부 계정 로그인 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                         |
|         인증/OpenIdConnect/\[공급자\]/Authority          |                                               필수. OpenIdConnect를 호출할 때 사용할 인증 기관입니다. 예: `https://login.microsoftonline.com/contoso.onmicrosoft.com/`. 자세한 내용은[Openidconnectauthenticationoptions. Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx).                                                |
|      Authentication/OpenIdConnect/\[공급자\]/MetadataAddress       | 메타 데이터를 가져오기 위한 검색 끝점입니다. 일반적으로:/. well-known/openid-configuration 경로로 끝납니다. 예: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`. 자세한 내용은[Openidconnectauthenticationoptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx)를 선택 합니다. |
|     Authentication/OpenIdConnect/\[공급자\]/AuthenticationType     |                                   OWIN authentication 미들웨어 유형입니다. 서비스 구성 메타 데이터의 발급자 값을 지정 합니다. 예: `https://sts.windows.net/contoso.onmicrosoft.com/`. 자세한 내용: [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                   |
|          Authentication/OpenIdConnect/\[공급자\]/ClientId          |                                                  필수. 공급자 응용 프로그램의 클라이언트 ID 값입니다. "응용 프로그램 ID" 또는 "소비자 키" 라고도 합니다. 자세한 내용은 [Openidconnectauthenticationoptions. ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx)를 선택 합니다.                                                   |
|        인증/OpenIdConnect/\[공급자\]/ClientSecret        |                                              공급자 응용 프로그램의 클라이언트 암호 값입니다. "앱 암호" 또는 "소비자 암호" 라고도 합니다. 자세한 내용은 [Openidconnectauthenticationoptions. ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx)을 (를) 선택 합니다.                                              |
|        인증/OpenIdConnect/\[공급자\]/RedirectUri         |                                                        바람직하지. AD FS WS-FEDERATION 수동 끝점입니다. 예: https://portal.contoso.com/signin-saml2. 자세한 내용은 [Openidconnectauthenticationoptions. RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx)를 선택 합니다.                                                        |
|          인증/OpenIdConnect/\[공급자\]/캡션           |                                                              바람직하지. 사용자가 로그인 사용자 인터페이스에 표시할 수 있는 텍스트입니다. 기본값: 공급자\]를 \[합니다. 자세한 내용은 [Openidconnectauthenticationoptions. 캡션](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx)을 선택 합니다.                                                               |
|          인증/OpenIdConnect/\[공급자\]/Resource          |                                                                                                       ' 리소스 '입니다. 자세한 내용은 [Openidconnectauthenticationoptions. 리소스](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx)를 선택 합니다.                                                                                                        |
|        Authentication/OpenIdConnect/\[공급자\]/ResponseType        |                                                                                                ' Response\_형식 '입니다. 자세한 내용은 [Openidconnectauthenticationoptions. ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx)을 (를) 입력 합니다.                                                                                                 |
|           인증/OpenIdConnect/\[공급자\]/Scope            |                                                                                요청할 사용 권한의 공백으로 구분 된 목록입니다. 기본값: openid connect. 자세한 내용은 [Openidconnectauthenticationoptions. 범위 ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx)를 선택 하십시오.                                                                                 |
|        Authentication/OpenIdConnect/\[공급자\]/CallbackPath        |                      인증 콜백을 처리할 선택적 제한 된 경로입니다. 제공 되지 않고 RedirectUri를 사용할 수 있는 경우이 값은 RedirectUri에서 생성 됩니다. 자세한 내용은 [Openidconnectauthenticationoptions. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx)를 선택 합니다.                      |
|     Authentication/OpenIdConnect/\[공급자\]/BackchannelTimeout     |                                                                백 채널 통신에 대 한 시간 제한 값입니다. 예: 00:05:00 (5 분) 자세한 내용은 [Openidconnectauthenticationoptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx)을 수행 하세요.                                                                |
| 인증/OpenIdConnect/\[공급자\]/RefreshOnIssuerKeyNotFound |                                      메타 데이터 새로 고침을 SecurityTokenSignatureKeyNotFoundException 후에 시도해 야 하는지 여부를 결정 합니다. 자세한 내용은 [Openidconnectauthenticationoptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx)을 (를) 선택 합니다.                                       |
|      인증/OpenIdConnect/\[공급자\]/UseTokenLifetime      |                                               인증 세션 수명 (예: 쿠키)이 인증 토큰과 일치 해야 함을 나타냅니다. 자세한 내용은 [Openidconnectauthenticationoptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx)을 (를) 선택 합니다.                                               |
|     인증/OpenIdConnect/\[공급자\]/AuthenticationMode     |                                                                                                     OWIN authentication 미들웨어 모드입니다. 자세한 내용은 [Authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)을 (를) 선택 합니다.                                                                                                     |
| 인증/OpenIdConnect/\[공급자\]/SignInAsAuthenticationType |                                                   ClaimsIdentity를 만들 때 사용 되는 AuthenticationType입니다. 자세한 내용은 [Openidconnectauthenticationoptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx)을 (를) 선택 합니다.                                                   |
|   Authentication/OpenIdConnect/\[공급자\]/PostLogoutRedirectUri    |                                                                                 ' Post\_로그 아웃\_리디렉션\_uri '입니다. 자세한 내용은 [Openidconnectauthenticationoptions. PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx)를 선택 합니다.                                                                                 |
|       인증/OpenIdConnect/\[공급자\]/유효한 대상 그룹       |                                                                                                  쉼표로 구분 된 대상 그룹 Url 목록입니다. 자세한 내용은 [Tokenvalidationparameters를 대상](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)으로 합니다.                                                                                                  |
|        인증/OpenIdConnect/\[공급자\]/ValidIssuers        |                                                                                                       쉼표로 구분 된 발급자 Url 목록입니다. 자세한 내용은 [Tokenvalidationparameters](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)을 (를) 수행 하십시오.                                                                                                       |
|         인증/OpenIdConnect/\[공급자\]/ClockSkew          |                                                                                                                                                                                        시간 유효성을 검사할 때 적용할 클록 오차입니다.                                                                                                                                                                                        |
|       인증/OpenIdConnect/\[공급자\]/NameClaimType        |                                                                                                                                                                              ClaimsIdentity에서 이름 클레임을 저장 하는 데 사용 하는 클레임 유형입니다.                                                                                                                                                                              |
|       인증/OpenIdConnect/\[공급자\]/RoleClaimType        |                                                                                                                                                                              ClaimsIdentity에서 역할 클레임을 저장 하는 데 사용 하는 클레임 유형입니다.                                                                                                                                                                              |
|   인증/OpenIdConnect/\[공급자\]/RequireExpirationTime    |                                                                                                                                                                              토큰에 ' 만료 ' 값이 있어야 하는지 여부를 나타내는 값입니다.                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[공급자\]/RequireSignedTokens     |                                                                                                                               서명 되지 않은 경우 System.identitymodel. xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5>를 사용할 수 있는지 여부를 나타내는 값입니다.                                                                                                                                |
|      인증/OpenIdConnect/\[공급자\]/SaveSigninToken       |                                                                                                                                                                        세션이 만들어질 때 원본 토큰이 저장 되는지 여부를 제어 하는 부울입니다.                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[공급자\]/ValidateActor        |                                                                                                                                                            System.identitymodel. JwtSecurityToken의 유효성을 검사 해야 하는지 여부를 나타내는 값입니다.                                                                                                                                                            |
|      인증/OpenIdConnect/\[공급자\]/ValidateAudience 대상      |                                                                                                                                                                       토큰 유효성 검사를 수행 하는 동안 대상 그룹의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                        |
|       인증/OpenIdConnect/\[공급자\]/ValidateIssuer       |                                                                                                                                                                        토큰 유효성 검사 중 발급자의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                         |
|      인증/OpenIdConnect/\[공급자\]/ValidateLifetime      |                                                                                                                                                                       토큰 유효성 검사 중 수명의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                        |
|  인증/OpenIdConnect/\[공급자\]/ValidateIssuerSigningKey  |                                                                                                                  SecurityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 서명 된 System.identitymodel 키의 유효성 검사가 호출 되는지 여부를 제어 하는 부울입니다.                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>다중 테 넌 트 Azure Active Directory 응용 프로그램을 사용 하 여 인증 활성화

[!include[](../../../includes/pn-azure-active-directory.md)]에 등록 된 다중 테 넌 트 응용 프로그램을 사용 하 여 특정 테 넌 트 뿐만 아니라 [!include[](../../../includes/pn-azure-shortest.md)]의 모든 테 넌 트에서 [!include[](../../../includes/pn-azure-active-directory.md)] 사용자를 허용 하도록 포털을 구성할 수 있습니다. 다중 테 넌 트를 사용 하도록 설정 하려면 [!include[](../../../includes/pn-azure-active-directory.md)] 응용 프로그램에서 **멀티 테 넌 트** 스위치를 **예** 로 설정 합니다.

![Azure Active Directory 응용 프로그램에서 다중 테 넌 트 사용](../media/enable-multi-tenancy.png "Azure Active Directory 응용 프로그램에서 다중 테 넌 트 사용")

### <a name="related-site-settings"></a>관련 사이트 설정

[Provider] 태그의 레이블을 대체 하 여 여러 id 공급자를 구성할 수 있습니다. 각 고유 레이블은 id 공급자와 관련 된 설정 그룹을 형성 합니다. 다중 테 넌 트 응용 프로그램을 사용 하 여 [!include[](../../../includes/pn-azure-active-directory.md)]에 대 한 인증을 지원 하도록 포털에서 다음 사이트 설정을 만들거나 구성할 수 있습니다.

|사이트 설정 이름    |설명   |
|---|---|
|Authentication/OpenIdConnect/[provider]/Authority   |OpenIdConnect를 호출할 때 사용할 인증 기관입니다. 예: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[provider]/ClientId   |공급자 응용 프로그램의 클라이언트 ID 값입니다. 앱 ID 또는 소비자 키 라고도 할 수 있습니다.   |
|Authentication/OpenIdConnect/[provider]/ExternalLogoutEnabled   |외부 계정 로그 아웃 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 이 값을 True로 설정 합니다.   |
|Authentication/OpenIdConnect/[provider]/IssuerFilter   |모든 테 넌 트의 모든 발급자와 일치 하는 와일드 카드 기반 필터입니다. 대부분의 경우 값을 사용 합니다. `https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[provider]/RedirectUri  |공급자가 인증 응답을 보내는 회신 URL 위치입니다. 예: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[provider]/ValidateIssuer   |토큰 유효성 검사 중 발급자의 유효성을 검사할지 여부를 제어 하는 부울입니다. 이 값을 False로 설정 합니다.   |
|||

### <a name="see-also"></a>참고 항목
[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대 한 인증 id 설정](set-authentication-identity.md)  
[포털에 대 한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대 한 WS-FEDERATION 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대 한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  

