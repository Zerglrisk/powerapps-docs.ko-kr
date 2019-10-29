---
title: 포털에 대 한 SAML 2.0 공급자 설정 구성 | MicrosoftDocs
description: 포털에 대 한 SAML 2.0 공급자 설정을 추가 하 고 구성 하는 지침을 제공 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a9e3f9398d8fdeadc9f5a6f7c57bbedbf972ef62
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978166"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>포털에 대 한 SAML 2.0 공급자 설정 구성

외부 인증을 제공 하려면 하나 이상의 [SAML 2.0](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)호환 id 공급자 (IdP)를 추가할 수 있습니다. 이 문서에서는 다양 한 id 공급자를 설정 하 여 서비스 공급자 역할을 하는 포털과 통합 하는 방법에 대해 설명 합니다.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

[!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)]와 같은 id 공급자에 대 한 설정입니다.

### <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 신뢰 당사자 트러스트 만들기

> [!Note]
> [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트에서 이러한 단계를 수행 하는 방법에 대 한 자세한 내용은 아래의 [PowerShell을 사용 하 여 AD FS 구성](#configure-ad-fs-by-using-powershell)을 참조 하세요.

[!include[](../../../includes/pn-adfs-short.md)] 관리 도구를 사용 하 여 **서비스** > **클레임 설명**으로 이동 합니다.

1.  **클레임 설명 추가**를 선택 합니다.
2.  클레임 지정:

    -  표시 이름: **영구 식별자**

    -  클레임 식별자: **urn: oasis: names: tc: SAML: 2.0: nameid-format: persistent**

    -  **사용** 확인란:이 클레임 설명을이 페더레이션 서비스에서 수락할 수 있는 클레임 유형으로 페더레이션 메타 데이터에 게시 합니다.

    -  **사용** 확인란:이 클레임 설명을이 페더레이션 서비스에서 보낼 수 있는 클레임 유형으로 페더레이션 메타 데이터에 게시 합니다.

3.  **확인**을 선택합니다.

[!include[](../../../includes/pn-adfs-short.md)] 관리 도구를 사용 하 여 신뢰 당사자 **트러스트** >**신뢰 관계** 를 선택 합니다.

1. **신뢰 당사자 트러스트 추가**를 선택 합니다.
2. 시작: **시작**을 선택 합니다.
3. 데이터 원본 선택: **신뢰 당사자에 대 한 데이터를 수동으로 입력**을 선택 하 고 **다음**을 선택 합니다.
4. 표시 이름 지정: 이름을 입력 하 고 **다음**을 선택 합니다.
   예: https://portal.contoso.com/
5. 프로필 선택: **AD FS 2.0 프로필**을 선택 하 고 **다음**을 선택 합니다.
6. 인증서 구성: **다음**을 선택 합니다.
7. URL 구성: **SAML 2.0 WebSSO 프로토콜에 대 한 지원 사용** 확인란을 선택 합니다.
   신뢰 당사자 SAML 2.0 SSO 서비스 URL: https://portal.contoso.com/signin-saml2 입력
   - 참고: [!include[](../../../includes/pn-adfs-short.md)] 하려면 포털이 HTTPS에서 실행 되어야 합니다.

   > [!Note] 
   > 결과 끝점의 설정은 다음과 같습니다. 
   > - 끝점 형식: **SAML 어설션이 끝점을 사용** 합니다.             
   > - 바인딩: **POST**                                            
   > - 인덱스: 해당 없음 (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Id 구성: https://portal.contoso.com/ 을 지정 하 고 **추가**를 선택한 후 **다음**을 선택 합니다.
   해당 하는 경우 각 추가 신뢰 당사자 포털에 대 한 id를 더 추가할 수 있습니다. 사용자는 사용 가능한 id 중 일부 또는 모두에 대해 인증할 수 있습니다.
9. 발급 권한 부여 규칙 선택: **모든 사용자가이 신뢰 당사자에 액세스 하도록 허용**을 선택 하 고 **다음**을 선택 합니다.
10. 트러스트 추가 준비 완료: **다음**을 선택 합니다.
11. **닫기**를 선택합니다.

신뢰 당사자 트러스트에 **이름 ID** 클레임을 추가 합니다.

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름을** **이름 ID** 클레임으로 변환 (들어오는 클레임 변환):

- 들어오는 클레임 유형: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 계정 이름**

- 보내는 클레임 유형: **이름 ID**

- 보내는 이름 ID 형식: **영구 식별자**

- 모든 클레임 값 통과

### <a name="create-site-settings"></a>사이트 설정 만들기

위의 [!include[](../../../includes/pn-adfs-short.md)] 신뢰 당사자 트러스트를 참조 하는 포털 사이트 설정을 적용 합니다.

> [!Note]
> 표준 [!include[](../../../includes/pn-adfs-short.md)] (IdP) 구성은 Authentication/SAML2/ADFS/MetadataAddress Address를 사용 하는 다음 설정 (예제 값)만 사용 합니다.  
> - Authentication/SAML2/ADFS/AuthenticationType- http://adfs.contoso.com/adfs/services/trust    
>   -   페더레이션 메타 데이터의 루트 요소에 있는 **entityID** 특성의 값을 사용 합니다 (위의 사이트 설정 값을 브라우저에서 **metadataaddress URL** 열기). 
> - Authentication/SAML2/ADFS/ServiceProviderRealm- https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2  
>   [!include[](../../../includes/pn-adfs-short.md)] 서버에서 다음 스크립트를 실행 하 여 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 에서 **페더레이션 메타 데이터** 를 검색할 수 있습니다. `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

[Provider] 태그의 레이블을 대체 하 여 여러 IdP 서비스를 구성할 수 있습니다. 각 고유 레이블은 IdP 관련 된 설정 그룹을 형성 합니다. 예: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| 사이트 설정 이름                                             | 설명                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 인증/등록/ExternalLoginEnabled              | 외부 계정 로그인 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | 필수. STS ([!include[](../../../includes/pn-adfs-short.md)]) 서버의 [ws-federation](https://msdn.microsoft.com/library/bb498017.aspx) 메타 데이터 URL입니다. 일반적으로/Federationmetadata.xml/2007-06/Federationmetadata.xml 경로로 끝납니다. 예: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions 주소](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | 필수. OWIN authentication 미들웨어 유형입니다. 페더레이션 메타 데이터 XML의 루트에 있는 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 특성의 값을 지정 합니다. 예: `http://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>또는 <br>Authentication/SAML2/[provider]/Wtrealm                      | 필수. [!include[](../../../includes/pn-adfs-short.md)] 신뢰 당사자 식별자입니다. 예: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>또는<br>Authentication/SAML2/[provider]/Wreply                       | 필수. [!include[](../../../includes/pn-adfs-short.md)] SAML 소비자 어설션 끝점입니다. 예: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/캡션                     | 바람직하지. 사용자가 로그인 사용자 인터페이스에 표시할 수 있는 텍스트입니다. 기본값: [provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | 인증 콜백을 처리할 선택적 제한 된 경로입니다. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions 경로](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | 백 채널 통신에 대 한 시간 제한 값입니다. 예: 00:05:00 (5 분) [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | 인증 세션 수명 (예: 쿠키)이 인증 토큰과 일치 해야 함을 나타냅니다. [WsFederationAuthenticationOptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | OWIN authentication 미들웨어 모드입니다. [!include[](../../../includes/proc-more-information.md)] [Authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | ClaimsIdentity를 만들 때 사용 되는 AuthenticationType입니다. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/유효한 대상 그룹              | 쉼표로 구분 된 대상 그룹 Url 목록입니다. [Tokenvalidationparameters를 [!include[](../../../includes/proc-more-information.md)] 합니다. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | 시간 유효성을 검사할 때 적용할 클록 오차입니다.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | 토큰에 만료 값이 있어야 하는지 여부를 나타내는 값입니다.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | 토큰 유효성 검사를 수행 하는 동안 대상 그룹의 유효성을 검사할지 여부를 제어 하는 부울입니다.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP-시작 된 로그인

[!include[](../../../includes/pn-adfs-short.md)]는 SAML 2.0 [사양의](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) [SSO (IdP Single Sign-On](https://technet.microsoft.com/library/jj127245.aspx) ) 프로필을 지원 합니다. 포털 (서비스 공급자)이 IdP에서 시작 된 SAML 요청에 적절히 응답 하려면 [RelayState](http://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) 매개 변수를 올바르게 인코딩해야 합니다.  

SAML RelayState 매개 변수로 인코딩될 기본 문자열 값은 **ReturnUrl =/content/sub-content/** 형식 이어야 합니다. 여기서 **/content/sub-content/** 는 포털 (서비스 공급자)에서 이동 하려는 웹 페이지의 경로입니다. 경로는 포털의 유효한 웹 페이지로 바꿀 수 있습니다. 문자열 값은 인코딩된 다음 **rpid =&lt;url로 인코딩된 rpid&gt;& RelayState =&lt;url 인코딩된 RelayState&gt;** 형식의 컨테이너 문자열에 배치 됩니다. 이 전체 문자열을 다시 인코딩한 후 **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> 인코딩된 RPID/RelayState&gt;** 형식의 다른 컨테이너에 추가 했습니다.

예를 들어 서비스 공급자 경로 **/content/sub-content/** 및 신뢰 당사자 ID **https://portal.contoso.com/** 지정 된 경우 다음 단계를 사용 하 여 URL을 구성 합니다.

ReturnUrl =/content/sub-content/값을 인코딩합니다.

-   ReturnUrl% 3D% 2Fcontent% 2Fsub-content% 2F

<!-- -->

-   값 https://portal.contoso.com/ 인코딩합니다.

<!-- -->

-   https %3을 (를) 가져오려면 %2 F %2 F portal. .com% 2F

<!-- -->

-   값 RPID = https %3 A %2 F %2 F portal. .com% 2F & RelayState = ReturnUrl% 3D% 2Fcontent% 2Fsub% 2F

<!-- -->

-   RPID %3 D https %2 5 3A %2 5 2F %2 5 2Fportal% 252F% 26RelayState% 3DReturnUrl% 252F% 252Fcontent% 252Fsub-content% 252F

<!-- -->

-   AD FS IdP 시작 된 SSO 경로 앞에 추가 하 여 최종 URL을 가져옵니다.

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트를 사용 하 여 URL을 생성할 수 있습니다 (Get-IdPInitiatedUrl 이라는 파일에 저장).

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

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]에 대 한 SAML 2.0 설정

[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD는 표준 [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;준수 IdP 처럼 동작 하기 때문에 [!include[](../../../includes/pn-adfs-short.md)]를 설명 하는 이전 섹션을 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx)에도 적용할 수 있습니다. 시작 하려면 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 관리 포털](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) 에 로그인 하 고 기존 디렉터리를 만들거나 선택 합니다. 디렉터리를 사용할 수 있는 경우 지침에 따라 디렉터리에 [응용 프로그램을 추가](https://msdn.microsoft.com/library/azure/dn132599.aspx) 합니다.  

1.  디렉터리의**응용 프로그램** 메뉴에서 **추가**를 선택 합니다.
2.  **내 조직에서 개발 중인 응용 프로그램 추가를**선택 합니다.
3.  응용 프로그램에 대 한 사용자 지정 이름을 지정 하 고 **웹 응용 프로그램 및/또는 WEB API**유형을 선택 합니다.
4.  로그온 **URL** 및**앱 ID URI**의 경우 https://portal.contoso.com/ 두 필드 모두에 대 한 포털의 URL을 지정 합니다.
    이는 **Serviceproviderrealm** (Wtrealm) 사이트 설정 값에 해당 합니다.
5. 이때 새 응용 프로그램이 만들어집니다. 메뉴의 **구성** 섹션으로 이동 합니다.

    **Single Sign-On** 섹션에서 첫 번째 **회신 url** 항목을 업데이트 하 여 url http://portal.contoso.com/signin-azure-ad 에 경로를 포함 합니다.

    이는 **AssertionConsumerServiceUrl** (Wreply) 사이트 설정 값에 해당 합니다.

6. 바닥글 메뉴에서 **끝점 보기** 를 선택 하 고 **페더레이션 메타 데이터 문서** 필드를 확인 합니다.

이는 **Metadataaddress** 사이트 설정 값에 해당 합니다.

-   페더레이션 메타 데이터 XML을 볼 수 있도록이 URL을 브라우저 창에 붙여넣고 root 요소의 **entityID** 특성을 확인 합니다.
-   이 값은**AuthenticationType** 사이트 설정 값에 해당 합니다.

> [!Note]
> 표준 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 구성에는 Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml>와 같은 설정 (예제 값)만 사용 됩니다. 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - 페더레이션 메타 데이터의 루트 요소에 있는**entityID** 특성의 값을 사용 합니다 (위의 사이트 설정 값을 브라우저에서**metadataaddress URL** 열기). 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm-<https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth Id 공급자 3

[Shibboleth Id 공급자](https://wiki.shibboleth.net/confluence/display/IDP30/Home) 를 IdP 서비스로 올바르게 구성 하려면 다음 지침을 따르십시오. 다음은 IdP가 도메인 https://idp.contoso.com 호스트 되는 것으로 가정 합니다.  

페더레이션 메타 데이터 URL은 https://idp.contoso.com/idp/shibboleth

-   영구 식별자를 생성 하거나 제공 하도록 IdP를 구성 해야 합니다. 지침에 따라 [영구 식별자 생성](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)을 사용 하도록 설정 합니다.  

-   IdP federation 메타 데이터 (&lt;IDPSSODescriptor&gt;)는 [SSO 리디렉션 바인딩을](https://shibboleth.net/about/advanced.html)포함 하도록 구성 되어야 합니다. [예:](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample)  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

[Metadata-providers](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)를 설정 하 여 서비스 공급자 (신뢰 당사자)를 구성 합니다.  

-   각 서비스 공급자 페더레이션 메타 데이터 (&lt;SPSSODescriptor&gt;)는 Assertion Consumer Service 게시 바인딩을 포함 해야 합니다. 한 가지 옵션은 [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) 를 사용 하 고 다음을 포함 하는 구성 파일을 참조 하는 것입니다.  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Location 특성은**AssertionConsumerServiceUrl** (Wreply) 설정에 해당 합니다.

-   서비스 공급자 페더레이션 메타 데이터는 **AuthenticationType** 설정에 해당 하는 EntityDescriptor에 대 한 **entityID** 특성을 지정 해야 합니다.

**&lt;EntityDescriptor entityID =<https://portal.local.contoso.com/&gt>; ...**

> [!Note] 
> 표준 Shibboleth 구성에는 다음 설정 (예제 값)만 사용 됩니다.   
> Authentication/SAML2/Shibboleth/MetadataAddress- https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   페더레이션 메타 데이터의 루트 요소에 있는 **entityID** 특성의 값을 사용 합니다 (위의 사이트 설정 값을 브라우저에서 **metadataaddress URL** 열기).  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm- https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP-시작 된 로그인

Shibboleth는 SAML 2.0 [사양의](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) [IdP 시작 SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) 프로필을 지원 합니다. 포털 (서비스 공급자)이 IdP에서 시작 된 SAML 요청에 적절히 응답 하려면 RelayState 매개 변수를 올바르게 인코딩해야 합니다.  

SAML RelayState 매개 변수로 인코딩될 기본 문자열 값은 **ReturnUrl =/content/sub-content/** 형식 이어야 합니다. 여기서 **/content/sub-content/** 는 포털 (서비스 공급자)에서 이동 하려는 웹 페이지의 경로입니다. 경로는 포털의 유효한 웹 페이지로 바꿀 수 있습니다. 전체 IdP 시작 된 SSO URL은 인코딩된 <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> 공급자 ID&gt;& target =&lt;URL 인코딩된 반환 경로&gt;형식 이어야 합니다.

예를 들어 서비스 공급자 경로 **/content/sub-content/** 및 신뢰 당사자 ID **https://portal.contoso.com/** 지정 된 경우 최종 URL은 https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트를 사용 하 여 URL을 생성할 수 있습니다 (Get-ShibbolethIdPInitiatedUrl 이라는 파일에 저장).

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

## <a name="configure-ad-fs-by-using-powershell"></a>PowerShell을 사용 하 여 AD FS 구성

[!include[](../../../includes/pn-adfs-short.md)]에서 신뢰 당사자 트러스트를 추가 하는 프로세스는 [!include[](../../../includes/pn-adfs-short.md)] 서버에서 다음 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 스크립트를 실행 하 여 수행할 수도 있습니다. 즉, 콘텐츠를 Add-AdxPortalRelyingPartyTrustForSaml 라는 파일에 저장 합니다. 스크립트를 실행 한 후 포털 사이트 설정 구성을 계속 합니다.

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

c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["http://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = http://schemas.microsoft.com/authorization/claims/permit, Value = true);

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

### <a name="see-also"></a>참고 항목

[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대 한 인증 id 설정](set-authentication-identity.md)  
[포털에 대 한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대 한 Open ID Connect 공급자 설정](configure-openid-settings.md)  
[포털에 대 한 WS-FEDERATION 공급자 설정](configure-ws-federation-settings.md)  
