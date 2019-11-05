---
title: 포털에 대 한 WS-FEDERATION 공급자 설정 구성 | MicrosoftDocs
description: 포털에 대 한 WS-FEDERATION 공급자 설정을 추가 하 고 구성 하는 지침을 제공 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542697"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>포털에 대 한 WS-FEDERATION 공급자 설정 구성

단일 [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] 페더레이션 서비스 서버를 id 공급자로 추가 하거나 다른 [ws-federation](https://msdn.microsoft.com/library/bb498017.aspx)규격 보안 토큰 서비스를 추가할 수 있습니다. 또한 단일 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) 네임 스페이스를 개별 id 공급자 집합으로 구성할 수 있습니다. AD FS 및 ACS의 설정은 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) 클래스의 속성을 기반으로 합니다.

## <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 신뢰 당사자 트러스트 만들기

AD FS 관리 도구를 사용 하 여 신뢰 당사자 **트러스트**&gt; **신뢰 관계** 로 이동 합니다.

1.  **신뢰 당사자 트러스트 추가**를 선택 합니다.
2.  시작: **시작**을 선택 합니다.
3.  데이터 원본 선택: **신뢰 당사자에 대 한 데이터를 수동으로 입력**을 선택 하 고 **다음**을 선택 합니다.
4.  표시 이름 지정: **이름을**입력 하 고 **다음**을 선택 합니다.
    예: https://portal.contoso.com/
5.  프로필 선택: **AD FS 2.0 프로필**을 선택 하 고 **다음**을 선택 합니다.
6.  인증서 구성: **다음**을 선택 합니다.
7.  URL 구성: **Ws-federation 수동 프로토콜에 대 한 지원 사용** 확인란을 선택 합니다.

신뢰 당사자 WS-FEDERATION 수동 프로토콜 URL: https://portal.contoso.com/signin-federation 을 입력 합니다.

-   참고: AD FS 하려면 포털이 **HTTPS**에서 실행 되어야 합니다.

    > [!Note]
    > 결과 끝점의 설정은 다음과 같습니다. 끝점 유형: **ws-federation**
    > -   바인딩: **POST**
    > -   인덱스: 해당 없음 (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  Id 구성: https://portal.contoso.com/ 을 지정 하 고 **추가**를 선택한 후 **다음**을 선택 합니다.
    해당 하는 경우 추가 신뢰 당사자 포털에 더 많은 id를 추가할 수 있습니다. 사용자는 사용 가능한 id 중 일부 또는 모두에 대해 인증할 수 있습니다.
9.  발급 권한 부여 규칙 선택: **모든 사용자가이 신뢰 당사자에 액세스 하도록 허용**을 선택 하 고 **다음**을 선택 합니다.
10.  트러스트 추가 준비 완료: **다음**을 선택 합니다.
11.  **닫기**를 선택합니다.

신뢰 당사자 트러스트에 **이름 ID** 클레임을 추가 합니다.

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름을** **이름 ID** 클레임으로 변환 (들어오는 클레임 변환):
- 들어오는 클레임 유형: Windows 계정 이름
- 보내는 클레임 유형: 이름 ID
- 보내는 이름 ID 형식: 지정 되지 않음
- 모든 클레임 값 통과

### <a name="create-ad-fs-site-settings"></a>AD FS 사이트 설정 만들기

위의 AD FS 신뢰 당사자 트러스트를 참조 하는 포털 사이트 설정을 적용 합니다.

> [!Note]
> STS (표준 AD FS) 구성은 다음 설정 (예제 값)만 사용 합니다.
> - Authentication/WsFederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust
>   - 페더레이션 메타 데이터의 루트 요소에 있는 **entityID** 특성의 값을 사용 합니다 (위의 사이트 설정 값을 브라우저에서 **metadataaddress URL** 열기).
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-federation

AD FS 서버에서 다음 스크립트를 실행 하 여 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 에서 **ws-federation 메타 데이터** 를 검색할 수 있습니다.

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      사이트 설정 이름                      |                                                                                                                                                                                                                                                 설명                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      인증/등록/ExternalLoginEnabled       |                                                                                                                                                                                                                외부 계정 로그인 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 필수. STS (AD FS) 서버의 [ws-federation](https://msdn.microsoft.com/library/bb498017.aspx) 메타 데이터 URL입니다. 일반적으로:/Federationmetadata.xml/2007-06/Federationmetadata.xml 경로로 끝납니다. 예:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. 자세한 내용은 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)을 (를) 수행 하십시오. |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            필수. OWIN authentication 미들웨어 유형입니다. 페더레이션 메타 데이터 XML의 루트에 있는 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 특성의 값을 지정 합니다. 예: https://adfs.contoso.com/adfs/services/trust. 자세한 내용: [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              필수. AD FS 신뢰 당사자 식별자입니다. 예: `https://portal.contoso.com/`. 자세한 내용은 [WsFederationAuthenticationOptions. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)을 (를) 수행 하세요.                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     필수. AD FS WS-FEDERATION 수동 끝점입니다. 예: https://portal.contoso.com/signin-federation. 자세한 내용은 [WsFederationAuthenticationOptions. Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)을 (를) 수행 하세요.                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           바람직하지. 사용자가 로그인 사용자 인터페이스에 표시할 수 있는 텍스트입니다. 기본값: ADFS. 자세한 내용은 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)을 (를) 추가 하세요.                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             인증 콜백을 처리할 선택적 제한 된 경로입니다. 자세한 내용은 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)을 (를) 수행 하십시오.                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               로그 아웃 중에 사용 되는 ' wreply ' 값입니다. 자세한 내용은 [WsFederationAuthenticationOptions. SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)을 (를) 수행 하세요.                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         백 채널 통신에 대 한 시간 제한 값입니다. 예: 00:05:00 (5 분) 자세한 내용은 WsFederationAuthenticationOptions. [BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)를 추가 합니다.                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  SecurityTokenSignatureKeyNotFoundException 후 메타 데이터 새로 고침을 시도해 야 하는지 여부를 결정 합니다. 자세한 내용은 [WsFederationAuthenticationOptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)을 (를) 수행 하세요.                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   인증 세션 수명 (예: 쿠키)이 인증 토큰과 일치 해야 함을 나타냅니다. [WsFederationAuthenticationOptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN authentication 미들웨어 모드입니다. 자세한 내용은 [Authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)을 (를) 선택 합니다.                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            ClaimsIdentity를 만들 때 사용 되는 AuthenticationType입니다. 자세한 내용은 [WsFederationAuthenticationOptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)을 (를) 수행 하세요.                                                                                            |
|       Authentication/WsFederation/ADFS/유효한 대상       |                                                                                                                                         쉼표로 구분 된 대상 그룹 Url 목록입니다. 자세한 내용은 [Tokenvalidationparameters를 대상](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)으로 합니다.                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              쉼표로 구분 된 발급자 Url 목록입니다. 자세한 내용은 [Tokenvalidationparameters](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)을 (를) 수행 하십시오.                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               시간 유효성을 검사할 때 적용할 클록 오차입니다.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     ClaimsIdentity에서 이름 클레임을 저장 하는 데 사용 하는 클레임 유형입니다.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     ClaimsIdentity에서 역할 클레임을 저장 하는 데 사용 하는 클레임 유형입니다.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     토큰에 ' 만료 ' 값이 있어야 하는지 여부를 나타내는 값입니다.                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/Require) 토큰     |                                                                                                                                                                       서명 되지 않은 경우 System.identitymodel. xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5>를 사용할 수 있는지 여부를 나타내는 값입니다.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               세션이 만들어질 때 원본 토큰이 저장 되는지 여부를 제어 하는 부울입니다.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   System.identitymodel. JwtSecurityToken의 유효성을 검사 해야 하는지 여부를 나타내는 값입니다.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               토큰 유효성 검사를 수행 하는 동안 대상 그룹의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                토큰 유효성 검사 중 발급자의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               토큰 유효성 검사 중 수명의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         SecurityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 서명 된 System.identitymodel 키의 유효성 검사가 호출 되는지 여부를 제어 하는 부울입니다.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       Id 공급자 리디렉션 URL에 "whr" 매개 변수를 지정 합니다. 자세한 내용은 [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)을 (를) 수행 하세요.                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]에 대 한 WS-FEDERATION 설정

[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD는 표준 [ws-federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) 규격 보안 토큰 서비스 처럼 동작 하기 때문에 AD FS를 설명 하는 이전 섹션을 [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx))에도 적용할 수 있습니다. 시작 하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) 에 로그인 하 고 기존 디렉터리를 만들거나 선택 합니다. 디렉터리를 사용할 수 있는 경우 지침에 따라 디렉터리에 [응용 프로그램을 추가](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) 합니다.

1.  디렉터리의 **응용 프로그램** 메뉴에서 **추가**를 선택 합니다.
2.  **내 조직에서 개발 중인 응용 프로그램 추가를**선택 합니다.
3.  응용 프로그램에 대 한 사용자 지정 **이름을** 지정 하 고 **웹 응용 프로그램 및/또는 web API**유형을 선택 합니다.
4.  로그온 **URL** 및 **앱 ID URI**의 경우 https://portal.contoso.com/ 두 필드 모두에 대 한 포털의 URL을 지정 합니다.
    - **Wtrealm** 사이트 설정 값에 해당 합니다.
5.  이때 새 응용 프로그램이 만들어집니다. 메뉴의 **구성** 섹션으로 이동 합니다.
6.  **Single Sign-On** 섹션에서 첫 번째 **회신 url** 항목을 업데이트 하 여 url https://portal.contoso.com/signin-azure-ad 에 경로를 포함 합니다.
    - **Wreply** 사이트 설정 값에 해당 합니다.
7.  바닥글에서 **저장** 을 선택 합니다.
8.  바닥글 메뉴에서 **끝점 보기** 를 선택 하 고 **페더레이션 메타 데이터 문서** 필드를 확인 합니다.

    - 이는 **Metadataaddress** 사이트 설정 값에 해당 합니다.
    - 페더레이션 메타 데이터 XML을 볼 수 있도록이 URL을 브라우저 창에 붙여넣고 root 요소의 **entityID** 특성을 확인 합니다.
    - 이 값은 **AuthenticationType** 사이트 설정 값에 해당 합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성은 다음 설정 (예제 값)만 사용 합니다.
> - Authentication/WsFederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - 페더레이션 메타 데이터의 루트 요소에 있는 **entityID** 특성의 값을 사용 합니다 (위의 사이트 설정 값을 브라우저에서 **metadataaddress URL** 열기).
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>참고 항목

[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대 한 인증 id 설정](set-authentication-identity.md)  
[포털에 대 한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대 한 Open ID Connect 공급자 설정](configure-openid-settings.md)  
[포털에 대 한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  
