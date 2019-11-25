---
title: 포털에 대한 WS-Federation 공급자 설정 구성 | MicrosoftDocs
description: 포털의 WS-Federation 공급자 설정을 추가 및 구성하는 방법에 대해 설명합니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759607"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>포털을 위한 WS-연대 공급자 설정값 구성

단일 [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] 페더레이션 서비스 서버(또는 다른 [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) 호환 보안 토큰 서비스)를 ID 공급자로 추가할 수 있습니다. 또한 단일 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) 네임스페이스를 일련의 개별 ID 공급자로 구성할 수 있습니다. AD FS 및 ACS에 대한 설정 모두 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) 클래스의 속성에 기반합니다.

## <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 신뢰 당사자 신뢰 만들기

AD FS 관리 도구를 사용하여 **신뢰 관계** &gt; **신뢰 당사자 신뢰**로 이동합니다.

1.  **신뢰 당사자 신뢰 추가**를 선택합니다.
2.  시작: **시작**을 선택합니다.
3.  데이터 원본 선택: **수동으로 신뢰 당사자에 대한 데이터 입력**을 선택한 다음, **다음**을 선택합니다.
4.  표시 이름 지정: **이름**을 입력한 다음, **다음**을 선택합니다.
    예: https://portal.contoso.com/
5.  프로필 선택: **AD FS 2.0 프로필**을 선택한 다음 **다음**을 선택합니다.
6.  인증서 구성: **다음**을 선택합니다.
7.  URL 구성: **WS-Federation 패시브 프로토콜에 대한 지원 활성화** 확인란을 선택합니다.

신뢰 당사자 WS-Federation 패시브 프로토콜 URL: https://portal.contoso.com/signin-federation 입력

-   참고: AD FS에는 **HTTPS**에서 실행되는 포털이 필요합니다.

    > [!Note]
    > 결과 엔드 포인트에는 다음 설정이 있습니다. 엔드 포인트 유형: **WS-페더레이션**
    > -   바인딩: **POST**
    > -   색인: 해당 없음(0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  ID 구성: https://portal.contoso.com/을 지정하고 **추가**를 선택한 후 **다음**을 선택합니다.
    해당되는 경우, 각 추가 신뢰 당사자 포털에 대해 더 많은 ID를 추가할 수 있습니다. 사용자는 해당되는 ID라면 어떤 ID라도 인증할 수 있습니다.
9.  발급 인증 규칙 선택: **모든 사용자가 이 신뢰 당사자에 액세스하도록 허용**을 클릭한 다음 **다음**을 선택합니다.
10.  신뢰 추가 준비 완료: **다음**을 선택합니다.
11.  **닫기**를 선택합니다.

**이름 ID** 클레임을 신뢰 당사자 신뢰에 추가:

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름**을 **이름 ID** 클레임으로 변환(수신 클레임 변환):
- 수신 클레임 유형: Windows 계정 이름
- 발신 클레임 유형: 이름 ID
- 발신 이름 ID 형식: 지정되지 않음
- 모든 클레임 값 통과

### <a name="create-ad-fs-site-settings"></a>AD FS 사이트 설정 만들기

위의 AD FS 신뢰 당사자 신뢰를 참조하여 포털 사이트 설정을 적용합니다.

> [!Note]
> 표준 AD FS(STS) 구성은 다음의 설정만을 사용합니다(예시 값).
> - Authentication/WsFederation/ADFS/MetadataAddress - https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust
>   - 페더레이션 메타데이터의 루트 요소의 **엔터티 ID** 특성 값을 사용(브라우저에서 위 사이트의 설정 값인 **메타데이터 주소 URL**을 엽니다)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-federation

**WS-Federation 메타데이터**는 AD FS 서버에서 다음 스크립트를 실행하여 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 에서 검색할 수 있습니다.

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      사이트 설정 이름                      |                                                                                                                                                                                                                                                 설명                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                외부 계정 로그인 및 등록을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 필수 특성: AD FS(STS) 서버의 [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) 메타데이터 URL입니다. 일반적으로 path:/FederationMetadata/2007-06/FederationMetadata.xml로 끝납니다. 예:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml> 자세한 내용은 [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)를 참조하십시오. |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            필수 특성: OWIN 인증 미들웨어 타입. 페더레이션 메타데이터 XML의 루트에서의 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 특성 값을 지정합니다. 예: https://adfs.contoso.com/adfs/services/trust 자세한 내용은 [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)을 참조하십시오.             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              필수 특성: AD FS 신뢰 당사자 식별자입니다. 예: `https://portal.contoso.com/` 자세한 내용은 [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)을 참조하십시오.                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     필수 특성: AD FS WS-연합 피동 종점. 예: https://portal.contoso.com/signin-federation 자세한 내용은 [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)를 참조하십시오.                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           권장. 로그인 사용자 인터페이스에 사용자가 표시할 수 있는 텍스트. 기본값: ADFS 자세한 내용은 [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)을 참조하십시오.                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             인증 콜백을 처리할 제약 경로 옵션. 자세한 내용은 [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)를 참조하십시오.                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               로그아웃하는 동안 사용되는 'wreply' 값입니다. 자세한 내용은 [WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)를 참조하십시오.                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         백채널 통신을 위한 타임아웃 값. 예: 00:05:00(5분) 자세한 내용은 [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)을 참조하십시오.                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  SecurityTokenSignatureKeyNotFoundException 후에 메타데이터 새로 고침을 시도해야 하는지를 결정합니다. 자세한 내용은 [WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)를 참조하십시오.                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   인증 세션 수명(예: 쿠키)이 인증 토큰의 수명과 일치함을 나타냅니다. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN 인증 미들웨어 모드입니다. 자세한 내용은 [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)를 참조하십시오.                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            System.Security.Claims.ClaimsIdentity를 생성할 때 사용되는 인증 타입. 자세한 내용은 [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)을 참조하십시오.                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         쉼표로 구분된 대상 URL 목록. 자세한 내용은 [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)를 참조하십시오.                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              쉼표로 구분된 발행자 URL 목록. 자세한 내용은 [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)를 참조하십시오.                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               시간 유효성을 검사할 때 적용할 클록 스큐입니다.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     이름 클레임을 저장하기 위해 ClaimsIdentity가 사용하는 클레임 타입.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     역할 클레임을 저장하기 위해 ClaimsIdentity가 사용하는 클레임 타입.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     토큰이 '만료' 값을 가져야 할지 여부를 표시하는 값입니다.                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       서명되지 않은 경우 System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>이 유효할 수 있는지의 여부를 표시하는 값.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               세션 생성시 원래 토큰이 저장되는지를 통제하는 부울값.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   System.IdentityModel.Tokens.JwtSecurityToken.Actor를 검증해야 하는지의 여부를 표시하는 값.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               토큰의 유효성을 검사하는 동안 대상의 유효성을 검사할지 제어하는 부울입니다.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                토큰 검증시 발행자가 검증될지를 통제하는 부울값.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               토큰 검증시 수명 시간이 검증될지를 통제하는 부울값.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>을 서명한 System.IdentityModel.Tokens.SecurityKey의 검증이 호출되는지를 통제하는 부울값.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       ID 공급자 리디렉션 URL의 "whr" 매개 변수를 지정합니다. 자세한 내용은 [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)을 참조하십시오.                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]용 WS-Federation 설정

[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD가 표준 [WS-연대](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) 준수 보안 토큰 서비스처럼 작동하기 때문에 AD FS를 설명하는 이전 섹션의 내용은 [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx))에도 적용할 수 있습니다. 시작하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)에 로그인하여 디렉터리를 생성하거나 기존 디렉터리를 선택하십시오. 디렉터리를 사용할 수 있을 때 지시를 따라 디렉터리에 [응용 프로그램을 추가](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)하십시오.

1.  디렉터리의 **응용 프로그램** 메뉴 아래의 **추가**를 선택합니다.
2.  **내 조직이 개발하는 응용 프로그램 추가**를 선택합니다.
3.  응용 프로그램에 대한 사용자 지정 **이름**을 지정한 다음, **웹 응용 프로그램 및/또는 웹 API** 유형을 선택합니다.
4.  **로그인 URL** 및 **앱 ID URI**을 위해 두 필드 https://portal.contoso.com/를 위한 포털의 URL을 지정합니다.
    - **Wtrealm** 사이트 설정 값과 일치합니다.
5.  이 시점에서 새 애플리케이션이 생성됩니다. 메뉴에서 **구성** 섹션으로 이동합니다.
6.  **단일 로그인** 섹션에서 URL https://portal.contoso.com/signin-azure-ad에 경로를 포함하기 위해 첫 번째 **회신 URL** 항목을 업데이트합니다.
    - **Wreply** 사이트 설정 값과 일치합니다.
7.  바닥글에서 **저장**을 선택합니다.
8.  바닥글 메뉴에서 **끝점 보기**를 선택한 다음 **페더레이션 메타데이터 문서** 필드를 참고합니다.

    - 이는 **MetadataAddress** 사이트 설정값에 해당됩니다.
    - 브라우저 창에 이 URL을 붙여 넣어 페더레이션 메타데이터 XML을 확인하고 루트 요소의 **entityID** 특성을 참고합니다.
    - **인증 유형** 사이트 설정 값과 일치합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성은 다음의 설정만을 사용합니다(예시 값).
> - Authentication/WsFederation/ADFS/MetadataAddress - https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - 페더레이션 메타데이터의 루트 요소의 **엔터티 ID** 특성 값을 사용(브라우저에서 위 사이트의 설정 값인 **메타데이터 주소 URL**을 엽니다)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>참조

[포털 인증 구성](configure-portal-authentication.md)  
[포털의 인증 ID 설정](set-authentication-identity.md)  
[포털에 대한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대한 ID 연결 공급자 열기](configure-openid-settings.md)  
[포털에 대한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  
