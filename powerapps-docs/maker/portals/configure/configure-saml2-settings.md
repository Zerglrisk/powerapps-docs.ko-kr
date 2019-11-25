---
title: 포털에 대한 SAML 2.0 공급자 설정 구성 | MicrosoftDocs
description: 포털의 SAML 2.0 공급자 설정을 추가 및 구성하는 방법에 대해 설명합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759651"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>포털에 대한 SAML 2.0 공급자 설정값 구성

외부 인증을 제공하려면 하나 혹은 그 이상의 [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html) 호환 ID 공급자(IdP)를 추가할 수 있습니다. 이 문서는 서비스 공급자 역할을 하는 ID 공급자를 포털과 통합하기 위해 다양한 ID 공급자를 설치하는 방법을 설명합니다.  

## <a name="ad-fs-idp"></a>AD FS(IdP)

[!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)]와 같은 ID 공급자에 대한 설정입니다.

### <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 신뢰 당사자 신뢰 만들기

> [!Note]
> [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트에서 이러한 단계를 수행하는 방법에 대한 자세한 내용은 [PowerShell을 사용하여 AD FS 구성](#configure-ad-fs-by-using-powershell)을 참조하십시오.

[!include[](../../../includes/pn-adfs-short.md)] 관리 도구를 사용하여 **서비스** > **클레임 설명**으로 이동합니다.

1.  **클레임 설명 추가**를 선택합니다.
2.  클레임 지정:

    -  표시 이름: **영구 식별자**

    -  클레임 식별자: **urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  다음에 대한 확인란 **활성화**: 페더레이션 메타데이터에 페더레이션 서비스가 허용할 수 있는 클레임 형식으로 이 클레임 설명을 게시

    -  다음에 대한 확인란 **활성화**: 페더레이션 메타데이터에 페더레이션 서비스가 허용할 수 있는 클레임 형식으로 이 클레임 설명을 보내기

3.  **확인**을 선택합니다.

[!include[](../../../includes/pn-adfs-short.md)] 관리 도구를 사용하여 **신뢰 관계** >**신뢰 당사자 신뢰**를 순서대로 선택합니다.

1. **신뢰 당사자 신뢰 추가**를 선택합니다.
2. 시작: **시작**을 선택합니다.
3. 데이터 원본 선택: **수동으로 신뢰 당사자에 대한 데이터 입력**을 선택한 다음, **다음**을 선택합니다.
4. 표시 이름 지정: 이름을 입력한 다음, **다음**을 선택합니다.
   예: https://portal.contoso.com/
5. 프로필 선택: **AD FS 2.0 프로필**을 선택한 다음 **다음**을 선택합니다.
6. 인증서 구성: **다음**을 선택합니다.
7. URL 구성: **SAML 2.0 WebSSO 프로토콜에 대한 지원 활성화** 확인란을 선택합니다.
   신뢰 당사자 SAML 2.0 SSO 서비스 URL: https://portal.contoso.com/signin-saml2 입력
   - 참고: [!include[](../../../includes/pn-adfs-short.md)]에는 HTTPS에서 실행되는 포털이 필요합니다.

   > [!Note] 
   > 결과 끝점은 다음의 설정을 가집니다. 
   > - 끝점 형식: **SAML 어설션 소비 끝점**             
   > - 바인딩: **POST**                                            
   > - 색인: 해당 없음(0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. ID 구성: https://portal.contoso.com/을 지정하고 **추가**를 선택한 후 **다음**을 선택합니다.
   해당되는 경우, 각 추가 신뢰 당사자 포털에 대해 더 많은 ID를 추가할 수 있습니다. 사용자는 해당되는 ID라면 어떤 ID라도 인증할 수 있습니다.
9. 발급 인증 규칙 선택: **모든 사용자가 이 신뢰 당사자에 액세스하도록 허용**을 클릭한 다음 **다음**을 선택합니다.
10. 신뢰 추가 준비 완료: **다음**을 선택합니다.
11. **닫기**를 선택합니다.

**이름 ID** 클레임을 신뢰 당사자 신뢰에 추가:

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름**을 **이름 ID** 클레임으로 변환(수신 클레임 변환):

- 수신 클레임 유형: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름**

- 발신 클레임 유형: **이름 ID**

- 발신 이름 ID 형식: **영구 식별자**

- 모든 클레임 값 통과

### <a name="create-site-settings"></a>사이트 설정 만들기

위의 [!include[](../../../includes/pn-adfs-short.md)] 신뢰 당사자 신뢰를 참조하여 포털 사이트 설정을 적용합니다.

> [!Note]
> 표준 [!include[](../../../includes/pn-adfs-short.md)](IdP) 구성은 다음 설정만 사용합니다(예제 값 사용): Authentication/SAML2/ADFS/MetadataAddress - <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust    
>   -   페더레이션 메타데이터의 루트 요소의 **entityID** 특성 값을 사용(브라우저에서 위 사이트의 설정 값인 **MetadataAddress URL**을 엽니다) 
> - Authentication/SAML2/ADFS/ServiceProviderRealm - https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2  
>   **페더레이션 메타데이터**는 [!include[](../../../includes/pn-adfs-short.md)] 서버에서 다음 스크립트를 실행하여 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 에서 검색할 수 있습니다. `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

[공급자] 태그의 레이블을 대체하여 여러 IdP 서비스를 구성할 수 있습니다. 각 고유 레이블은 IdP와 관련된 설정 그룹을 형성합니다. 예: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| 사이트 설정 이름                                             | 설명                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | 외부 계정 로그인 및 등록을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[공급자]/MetadataAddress             | 필수 특성: [!include[](../../../includes/pn-adfs-short.md)](STS) 서버의 [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) 메타데이터 URL입니다. 일반적으로 path:/FederationMetadata/2007-06/FederationMetadata.xml로 끝납니다. 예: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml` [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[공급자]/AuthenticationType          | 필수 특성: OWIN 인증 미들웨어 타입. 페더레이션 메타데이터 XML의 루트에서의 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 특성 값을 지정합니다. 예: `https://adfs.contoso.com/adfs/services/trust` [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[공급자]/ServiceProviderRealm<br>또는 <br>Authentication/SAML2/[공급자]/Wtrealm                      | 필수 특성: [!include[](../../../includes/pn-adfs-short.md)] 신뢰 당사자 식별자입니다. 예: `https://portal.contoso.com/` [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[공급자]/AssertionConsumerServiceUrl<br>또는<br>Authentication/SAML2/[공급자]/Wreply                       | 필수 특성: [!include[](../../../includes/pn-adfs-short.md)] SAML 소비자 어설션 끝점입니다. 예: https://portal.contoso.com/signin-saml2 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[공급자]/Caption                     | 권장. 로그인 사용자 인터페이스에 사용자가 표시할 수 있는 텍스트. 기본값: [공급자]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[공급자]/CallbackPath                | 인증 콜백을 처리할 제약 경로 옵션. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[공급자]/BackchannelTimeout          | 백채널 통신을 위한 타임아웃 값. 예: 00:05:00(5분) [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[공급자]/UseTokenLifetime            | 인증 세션 수명(예: 쿠키)이 인증 토큰의 수명과 일치함을 나타냅니다. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[공급자]/AuthenticationMode          | OWIN 인증 미들웨어 모드입니다. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[공급자]/SignInAsAuthenticationType  | System.Security.Claims.ClaimsIdentity를 생성할 때 사용되는 인증 타입. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[공급자]/ValidAudiences              | 쉼표로 구분된 대상 URL 목록. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[공급자]/ClockSkew                   | 시간 유효성을 검사할 때 적용할 클록 스큐입니다.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[공급자]/RequireExpirationTime       | 토큰이 만료 값을 가져야 할지 여부를 표시하는 값입니다.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[공급자]/ValidateAudience            | 토큰의 유효성을 검사하는 동안 대상의 유효성을 검사할지 제어하는 부울입니다.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP가 시작한 로그인

[!include[](../../../includes/pn-adfs-short.md)]는 SAML 2.0 [사양](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)의 [IdP가 시작한 Single Sign-On(SSO)](https://technet.microsoft.com/library/jj127245.aspx) 프로필을 지원합니다. 포털(서비스 공급자)이 IdP 가 시작한 SAML 요청에 적절히 반응하기 위해서는 [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) 매개 변수가 바르게 인코딩되어야 합니다.  

포털(서비스 공급자)에서 원하는 웹 페이지로 이동할 경로가 **content/sub-content/** 일 때 SAML RelayState 매개 변수에 인코딩될 기본 문자열 값은 **ReturnUrl=/content/sub-content/** 와 같은 형식이어야 합니다. 경로는 포털의 어떠한 유효한 웹 페이지로든 대체할 수 있습니다. 문자열 값은 인코딩되고 다음 형식의 컨테이너 문자열에 배치됩니다 **RPID=&lt;URL encoded RPID&gt;&RelayState=&lt;URL encoded RelayState&gt;**. 전체 문자열은 **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> 인코딩된 RPID/RelayState&gt;** 형식의 다른 컨테이너에 한 번 더 인코딩되고 추가됩니다.

예를 들면 서비스 공급자 경로 **/content/sub-content/** 와 신뢰 당사자 ID **https://portal.contoso.com/** 는 여러 단계의 URL을 구성합니다.

ReturnUrl=/content/sub-content/ 값을 인코딩하여

-   ReturnUrl%3D%2Fcontent%2Fsub-content%2F를 얻습니다.

<!-- -->

-   https://portal.contoso.com/ 값 인코딩

<!-- -->

-   https%3A%2F%2Fportal.contoso.com%2F를 얻습니다.

<!-- -->

-   RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F 값을 인코딩하여

<!-- -->

-   RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F를 얻습니다.

<!-- -->

-   최종 URL을 얻기 위해 AD FS IdP가 시작한 SSO 경로를 앞에 추가

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

URL을 구성하기 위해 다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]을 사용할 수 있습니다(Get-IdPInitiatedUrl.ps1이라는 이름의 파일로 저장).

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]의 SAML 2.0 설정을 지정합니다.

[!include[](../../../includes/pn-adfs-short.md)]를 설명하는 이전 섹션은 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)에도 적용할 수 있습니다. [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD는 표준 [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx) 호환 IdP처럼 작동하기 때문입니다. 시작하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)에 로그인하여 디렉터리를 생성하거나 기존 디렉터리를 선택하십시오. 디렉터리를 사용할 수 있을 때 지시를 따라 디렉터리에 [응용 프로그램을 추가](https://msdn.microsoft.com/library/azure/dn132599.aspx)하십시오.  

1.  디렉터리의 **응용 프로그램** 메뉴 아래의 **추가**를 선택합니다.
2.  **내 조직이 개발하는 응용 프로그램 추가**를 선택합니다.
3.  응용 프로그램에 대한 사용자 지정 이름을 지정한 다음, **웹 응용 프로그램 및/또는 웹 API** 유형을 선택합니다.
4.  **로그인 URL** 및 **앱 ID URI**을 위해 두 필드를 위한 포털의 URL을 지정합니다 https://portal.contoso.com/.
    이는 **서비스 공급자 영역**(Wtrealm) 사이트 설정 값과 일치합니다.
5. 이 시점에서 새 응용 프로그램이 생성됩니다. 메뉴에서 **구성** 섹션으로 이동합니다.

    **단일 로그인** 섹션에서 URL https://portal.contoso.com/signin-azure-ad에 경로를 포함하기 위해 첫 번째 **회신 URL** 항목을 업데이트합니다.

    이는 **어설션 소비자 서비스 URL**(Wreply) 사이트 설정 값과 동일합니다.

6. 바닥글 메뉴에서 **끝점 보기**를 선택한 다음 **페더레이션 메타데이터 문서** 필드를 참고합니다.

이는 **MetadataAddress** 사이트 설정값에 해당됩니다.

-   브라우저 창에 이 URL을 붙여 넣어 페더레이션 메타데이터 XML을 확인하고 루트 요소의 **entityID** 특성을 참고합니다.
-   이는 **인증 유형** 사이트 설정 값과 일치합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성은 다음 설정만 사용합니다(예제 값 사용): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType - <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - 페더레이션 메타데이터의 루트 요소의 **entityID** 특성 값을 사용(브라우저에서 위 사이트의 설정 값인 **MetadataAddress URL**을 엽니다) 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm - <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth ID 공급자 3

다음 안내서를 사용하여 IdP 서비스로서 [Shibboleth ID 공급자](https://wiki.shibboleth.net/confluence/display/IDP30/Home)를 올바르게 구성할 수 있습니다. 다음은 IdP가 도메인에 호스팅된다고 가정함: https://idp.contoso.com  

페더레이션 메타데이터 URL: https://idp.contoso.com/idp/shibboleth

-   영구 식별자를 생성 또는 제공하기 위해 반드시 IdP가 구성되어야 합니다. 지시를 따라 [영구 식별자 생성](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)을 활성화하십시오.  

-   IdP 페더레이션 메타데이터(&lt;IDPSSODescriptor&gt;)는 [SSO 리디렉션 바인딩](https://shibboleth.net/about/advanced.html)을 포함하도록 구성되어야 합니다. [예](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

[metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)을 설정하여 서비스 공급자(신뢰 당사자)를 구성합니다.  

-   각 서비스 공급자 페더레이션 메타데이터(&lt;SPSSODescriptor&gt;)는 권리 어설션 소비자 서비스 게시물 바인딩을 포함해야 합니다. [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider)를 사용하고 다음을 포함하는 구성 파일을 참고하는 방법도 있습니다.  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

위치 특성이 **어설션 소비자 서비스 URL**(Wreply) 설정과 일치합니다.

-   서비스 공급자 페더레이션 메타데이터는 **AuthenticationType** 설정과 일치하는 EntityDescriptor에 대한 **entityID** 특성을 지정해야 합니다.

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> 표준 Shibboleth 구성만은 다음 설정만을 사용합니다(예시 값).   
> Authentication/SAML2/Shibboleth/MetadataAddress - https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType - https://idp.contoso.com/idp/shibboleth 
> -   페더레이션 메타데이터의 루트 요소의 **entityID** 특성 값을 사용(브라우저에서 위 사이트의 설정 값인 **MetadataAddress URL**을 엽니다)  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm - https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP가 시작한 로그인

Shibboleth는 SAML 2.0 [사양](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)의 [IdP가 시작한 SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) 프로필을 지원합니다. 포털(서비스 공급자)이 IdP 가 시작한 SAML 요청에 적절히 반응하기 위해서는 RelayState 매개 변수가 바르게 인코딩되어야 합니다.  

포털(서비스 공급자)에서 원하는 웹 페이지로 이동할 경로가 **content/sub-content/** 일 때 SAML RelayState 매개 변수에 인코딩될 기본 문자열 값은 **ReturnUrl=/content/sub-content/** 와 같은 형식이어야 합니다. 경로는 포털의 어떠한 유효한 웹 페이지로든 대체할 수 있습니다. IdP가 시작한 전체 SSO URL은 <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> 인코딩된 공급자 ID&gt;&target=&lt;URL 인코딩된 반환 경로&gt; 형식이어야 합니다.

예를 들면 서비스 공급자 경로 **/content/sub-content/** 와 신뢰 당사자 ID **https://portal.contoso.com/** 인 경우 최종 URL은 https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F입니다.

URL을 구성하기 위해 다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]을 사용할 수 있습니다(Get-ShibbolethIdPInitiatedUrl.ps1이라는 이름의 파일로 저장).

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>PowerShell을 사용하여 AD FS 구성

[!include[](../../../includes/pn-adfs-short.md)]에 신뢰 당사자 신뢰를 추가하는 프로세스는 [!include[](../../../includes/pn-adfs-short.md)] 서버에서 다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트를 실행하여 수행할 수도 있습니다(Add-AdxPortalRelyingPartyTrustForSaml.ps1이라는 이름의 파일로 내용 저장). 스크립트를 실행한 다음 포털 사이트 설정 구성을 계속하십시오.

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>참조

[포털 인증 구성](configure-portal-authentication.md)  
[포털의 인증 ID 설정](set-authentication-identity.md)  
[포털에 대한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대한 ID 연결 공급자 열기](configure-openid-settings.md)  
[포털에 대한 WS-Federation 공급자 설정](configure-ws-federation-settings.md)  
