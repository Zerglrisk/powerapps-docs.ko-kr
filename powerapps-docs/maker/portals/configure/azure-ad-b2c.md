---
title: 포털을 위한 Azure AD B2C 공급자 설정 | MicrosoftDocs
description: 포털을 위한 Azure AD B2C 공급자 설정을 가능하게 하는 지침.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5f902dd900e074c2e6b3f08f8848475dcd907ee4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755494"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>포털에 대한 Azure AD B2C 공급자 설정

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory(Azure AD)는 직원 또는 내부 인증을 위해 Office 365 및 Dynamics 365 서비스에 권한을 제공합니다. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C는 그 인증 모델의 확장으로서 로컬 자격 증명을 통해 외부 고객 로그인을 가능하게 하고 다양한 소셜 ID 공급자들과의 연대를 가능하게 합니다.

포털 담당자는 포털이 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C를 ID 공급자로 받아들이도록 구성할 수 있습니다. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C는 연대를 위한 오픈 ID 연결을 지원합니다.

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C를 포털을 위한 ID 공급자로 구성하는 과정에서 나중에 포털을 구성할 때 사용할 여러 값이 생성됩니다. 다음 표에서 이러한 값을 확인할 수 있습니다. 포털을 구성하는 동안 변수 이름을 여기에 기록해 둔 값으로 교체합니다.

| 변수 이름     | 값 | 설명                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| 응용 프로그램-이름  |       | 신뢰 당사자로서의 포털을 나타내는 응용 프로그램의 이름 |
| 응용 프로그램-ID    |       | Azure Active Directory B2C에서 생성된 응용 프로그램과 연계된 응용 프로그램 ID.  |
| 정책-로그인-URL |       | 메타데이터 종점에 정의된 발급자(iss) URL.                |
| 연대 이름   |       | ‘B2C’ 같은 연대 공급자의 타입을 나타내는 고유 이름. 이것은 이 특정 공급자의 구성 설정을 분류하는 사이트 설정 이름에 사용됩니다.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Azure AD B2C를 포털을 위한 ID 공급자로 사용

1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.
2. [Azure AD B2C 테넌트를 만듭니다](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
3. 탐색 모음 가장 왼쪽의 **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C**를 선택합니다.
4. [Azure 응용 프로그램 생성](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > **묵시적 흐름 허용** 필드의 경우 **예**를 선택하고 **회신 URL** 필드에 포털 URL을 지정해야 합니다. **회신 URL** 필드의 값은 [포털 도메인]/signin-[페더레이션-이름] 형식이어야 합니다. `https://contosocommunity.microsoftcrmportals.com/signin-B2C`을 예로 들 수 있습니다.

5. 응용 프로그램 이름을 복사하여 앞의 표에서 응용 프로그램-이름의 값으로 입력합니다.
6. 응용 프로그램 ID를 복사하여 앞의 표에서 응용 프로그램-ID의 값으로 입력합니다.
7. [가입 또는 로그인 정책 생성](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy)
8. 정책을 선택한 다음, **편집**을 선택합니다.
9. **토큰, 세션 및 SSO 구성**을 선택합니다.
10. **발급자(iss) 클레임** 목록에서 해당 경로에 **/tfp**가 있는 URL을 선택합니다.
11. 정책을 저장합니다.
12. 이 정책 **필드의** 메타데이터 종점에서 URL을 선택합니다.
13. 발급자 필드의 값을 복사하여 앞의 표에서 정책-로그인-URL 값으로 입력합니다. 

## <a name="portal-configuration"></a>포털 구성

[!include[Azure](../../../includes/pn-azure-shortest.md)]에서 B2C 테넌트를 만들고 구성한 후에는 오픈 ID 연결 프로토콜을 사용하여 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C와 연대할 포털을 구성해야 합니다. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C에 연대하기 위한 고유 이름&mdash;예컨대, B2C&mdash;를 생성하여 위의 표에서 *페더레이션-이름* 변수의 값으로 저장해야 합니다.

### <a name="configure-your-portal"></a>포털 구성
1. 포털 관리 앱을 엽니다.
2. **포털** > **엡사이트**로 이동합니다.
3. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C를 활성화해야 하는 웹사이트 레코드를 선택합니다.
4. **사이트 설정**으로 이동합니다.
5. 다음 사이트 설정값을 만듭니다.
   -   **이름**: Authentication/OpenIdConnect/[페더레이션-이름]/Authority

       **값**: [정책-로그인-URL]
   -   **이름**: Authentication/OpenIdConnect/[페더레이션-이름]/ClientId

       **값**: [응용 프로그램-ID]
   -   **이름**: Authentication/OpenIdConnect/[페더레이션-이름]/RedirectUri

       **값**: [포털 도메인/]/signin-[페더레이션-이름]

       `https://mysite.com/signin-b2c`을 예로 들 수 있습니다. 
6. 연대된 로그아웃을 지원하려면 다음 사이트 설정을 만듭니다.
   - **이름**: Authentication/OpenIdConnect/[페더레이션-이름]/ExternalLogoutEnabled

     **값**: 참
7. 포털을 단일 ID 공급자로 하드코딩하려면 다음 사이트 설정을 만듭니다.
   - **이름**: 인증/등록/로그인 버튼 인증 타입

     **값**: [정책-로그인-URL]

8. 암호 재설정을 지원하려면 [여기에](#password-reset) 설명된 필수 사이트 설정을 만듭니다.
9. 클레임 매핑을 지원하려면 [여기에](#claims-mapping) 설명된 필수 사이트 설정을 만듭니다.

관련 사이트 설정의 전체 목록을 보려면 [여기를](#related-site-settings) 참조하십시오.

### <a name="password-reset"></a>암호 다시 설정

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 로컬 계정으로 암호 재설정을 지원하려는 경우 다음 사이트 설정이 요구됩니다.

| 사이트 설정                                                        | 설명                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[페더레이션-이름]/PasswordResetPolicyId | 암호 재설정 정책의 ID.                                                                                     |
| Authentication/OpenIdConnect/[페더레이션-이름]/ValidIssuers         | [정책-로그인-URL]과 암호 재설정 정책의 발급자를 포함하는 발급자들의 쉼표로 구분된 목록. |
|Authentication/OpenIdConnect/[페더레이션-이름]/DefaultPolicyId | 로그인 또는 가입 정책의 ID입니다.|
|||

### <a name="related-site-settings"></a>관련된 사이트 설정값

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C를 ID 공급자로 지원하기 위해 포털에서 다음 사이트 설정을 생성하거나 구성할 수 있습니다.


| 사이트 설정                                                         | 설명                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 인증/등록/프로필 리디렉션 활성화                   | 로그인에 성공한 후 포털이 사용자를 프로필 페이지로 리디렉션할 수 있는지의 여부를 지정합니다. 기본적으로는 참으로 설정됩니다.                                                                                                                                            |
| 인증/등록/이메일 확인 활성화                 | 이메일 유효성 검사가 요구되는지의 여부를 지정합니다. 기본적으로는 참으로 설정됩니다.                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | 로컬 로그인이 요구되는지의 여부를 지정합니다. 기본적으로는 참으로 설정됩니다.                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | 외부 인증을 활성화 또는 비활성화합니다.       |
| 인증/등록/Azure AD 로그인 활성화                      | [!include[Azure](../../../includes/pn-azure-shortest.md)] AD를 외부 ID 공급자로 활성화하거나 비활성화합니다. 기본적으로는 참으로 설정됩니다.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[페더레이션-이름]/ExternalLogoutEnabled | 페더레이션된 로그아웃을 활성화하거나 비활성화합니다. 참으로 설정하면 사용자가 포털에서 로그아웃할 때 연대 로그아웃 사용자 환경으로 리디렉션됩니다. 거짓으로 설정하면 사용자가 포털에서만 로그아웃됩니다. 기본적으로는 거짓으로 설정됩니다.               |
| 인증/로그인 추적 활성화                                  | 사용자의 마지막 로그인 추적을 활성화 또는 비활성화합니다. 참으로 설정하면 접촉 레코드의 **마지막 성공한 로그인** 필드에 날짜와 시간이 표시됩니다. 기본적으로 이것은 거짓으로 설정되어 있습니다.                                                            |
| Authentication/OpenIdConnect/[페더레이션-이름]/RegistrationEnabled   | 기존 ID 공급자에 대한 등록 요건을 활성화하거나 비활성화합니다. 참으로 설정하면 사이트 설정 인증/등록/활성화도 참으로 설정된 경우에만 기존 공급자의 등록이 활성화됩니다. 기본적으로는 참으로 설정됩니다. |
|Authentication/OpenIdConnect/[페더레이션-이름]/PostLogoutRedirectUri |사용자가 로그인한 후 리디렉션할 포털 내의 URL을 지정합니다. |
| | |

### <a name="related-content-snippet"></a>관련 콘텐츠 조각

사용자가 초대를 사용한 후에 사용자의 등록이 비활성화된 경우 다음 콘텐츠 조각을 사용하여 메시지를 표시합니다.

**이름**: 계정/등록/등록 비활성화 메시지

**값**: 등록이 비활성화됨.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 사용자 인터페이스 사용자 지정

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C는 사용자 인터페이스 사용자 지정을 지원합니다. 가입 및 로그인 시나리오에 대한 사용자 환경을 사용자 지정할 수 있습니다.

### <a name="step-1-create-a-web-template"></a>단계 1: 웹 템플릿 만들기
다음 값을 사용하여 웹 템플릿을 만듭니다.

**이름**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 맞춤 페이지

**소스**: 다음 샘플 웹 템플릿 소스 HTML을 사용합니다.

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>단계 2: 페이지 템플릿 만들기

다음 페이지 템플릿을 만듭니다.
- **이름**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 맞춤 페이지
- **타입**: 웹 템플릿
- **웹 템플릿**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 맞춤 페이지
- **웹사이트 머리글 및 바닥글 사용**: 이 확인란 선택을 취소합니다

### <a name="step-3-create-a-webpage"></a>단계 3: 웹페이지 만들기

다음 웹 페이지를 만듭니다.
- **이름**: 로그인
- **상위** 페이지: 홈
- **부분 URL**: azure-ad-b2c-sign-in
- **페이지 템플릿**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 맞춤 페이지
- **게시 상태**: 게시

### <a name="step-4-create-site-settings"></a>단계 4: 사이트 설정 만들기

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C가 맞춤 페이지를 요청하고 로그인 또는 가입 사용자 인터페이스를 주입할 수 있도록 교차 기원 리소스 공유(CORS)를 구성하기 위해서는 사이트 설정이 요구됩니다. 다음 사이트 설정을 만듭니다.

| 이름                              | 값                             |
|-----------------------------------|-----------------------------------|
| HTTP/액세스-제어-허용-방법 | 받기, 옵션                      |
| HTTP/액세스-제어-허용-기원  | `https://login.microsoftonline.com` |
| | |

기타 CORS 설정의 전체 목록은 [CORS 프로토콜 지원](../add-web-resource.md#cors-protocol-support)을 참조하십시오.

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>단계 5: [!include[Azure](../../../includes/pn-azure-shortest.md)] 구성

1. [!include[Azure portal](../../../includes/pn-azure-portal.md)]에 로그인합니다.
2. **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 테넌트 관리** 블레이드로 이동합니다.
3. **설정** > **가입 또는 로그인 정책**으로 이동합니다. 가용 정책의 목록이 표시됩니다.
4. 편집할 정책을 선택합니다.
5. **편집**을 선택합니다.
6. **정책 편집** > **페이지 UI 사용자 지정** > **통합 가입 또는 로그인 페이지**를 선택합니다
7. **맞춤 페이지 사용**을 **예**로 설정합니다.
8. **맞춤 페이지 URI**를 이 절차의 단계 3에서 생성한 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 맞춤 페이지 웹페이지의 URL로 설정합니다. `https://mydomain.com/azure-ad-b2c-sign-in`을 예로 들 수 있습니다.
9. **확인**을 선택합니다.

## <a name="claims-mapping"></a>클레임 매핑

사용자가 처음으로 또는 그 후에 로그인하면 사용자의 로그인에 관한 데이터베이스에 근거하여 연대된 ID 공급자가 클레임을 제공합니다. 이러한 클레임은 ID 공급자에서 구성할 수 있습니다.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 이메일 클레임

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C는 컬렉션으로서 전자 메일 클레임을 보냅니다. 포털은 컬렉션에 제공된 첫 번째 이메일을 연락처의 기본 이메일 주소로 받아들입니다.

### <a name="claims-to-support-sign-up-scenarios"></a>가입 시나리오를 지원하기 위한 클레임

Common Data Service에 존재하지 않는 새 고객이 프로비전된 경우 인바운드 클레임을 사용하여 포털이 만들 새 연락처 레코드를 시드할 수 있습니다. 일반 클레임은 이름과 성, 이메일 주소 및 전화번호를 포함할 수 있지만 그것들은 구성 가능합니다. 다음 사이트 설정이 요구됩니다.

**이름**: Authentication/OpenIdConnect/[페더레이션-이름]/RegistrationClaimsMapping

**설명**: 등록 중에 생성된 연락처 레코드의 속성에 클레임 값을 매핑하는 데 사용할 논리 이름/클레임 쌍의 목록.

**형식**: 속성1=클레임1,속성2=클레임2,속성3=클레임3

예: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> 이메일 주소를 연락처의 기본 이메일(emailaddress1)에 매핑하도록 합니다. 보조 이메일(emailaddress2) 또는 대체 이메일(emailaddress3)을 연락처 레코드에 추가하고 이메일에 매핑한 경우, ID 정보는 연락처에 추가되지 않으며 기본 이메일(emailaddress1)에 설정된 등록에 사용된 이메일 주소로 새 주소가 생성됩니다.

### <a name="claims-to-support-sign-in-scenarios"></a>로그인 시나리오를 지원하기 위한 클레임

Common Data Service 및 ID 공급자의 데이터는 직접 연결되어 있지 않으므로 데이터가 동기화되지 않을 수 있습니다. 포털에는 Common Data Service에서 업데이트할 로그인 이벤트에서 수락할 클레임의 목록이 있어야 합니다. 이러한 클레임은 로그인 시나리오에서 들어오는 클레임과 같거나 하위 집합일 수 있습니다. 일부 키 포털 속성을 덮어쓰지 않을 수 있으므로 이는 로그인 클레임 매핑과는 별도로 구성해야 합니다. 다음 사이트 설정이 요구됩니다.

**이름**: Authentication/OpenIdConnect/[페더레이션-이름]/LoginClaimsMapping

**설명**: 로그인 후에 생성된 연락처 레코드의 속성에 클레임 값을 매핑하는 데 사용할 논리 이름/클레임 쌍의 목록.

**형식**: 속성1=클레임1, 속성2=클레임2, 속성3=클레임3

예: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

클레임 이름은 로그인 정책 응용 프로그램 클레임의 속성 옆에 나열된 클레임 타입 필드입니다.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>이메일 주소에 근거한 연락처 레코드에 자동 연계 허용 

그러면 이메일 주소가 연계된 연락처 레코드가 있는 고객이 웹사이트를 출범시키면 외부 사용자들이 이메일 주소 유효성 검사 메커니즘을 통해 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C로 로그인할 것입니다. 중복 레코드를 만드는 대신 새 로그인을 기존 연락처 레코드와 연계해야 합니다. 이 기능은 활성 ID가 없는 연락처만 성공적으로 매핑하기 때문에 이메일 주소는 고유해야 합니다(복수의 연락처 레코드에 연계되지 않아야 함). 다음 사이트 설정이 요구됩니다.

**이름**: Authentication/[프로토콜]/[공급자]/AllowContactMappingWithEmail

**설명**: 연락처가 해당 이메일 주소에 매핑되는지의 여부를 지정합니다. 참으로 설정하면 이 설정은 고유한 연락처 레코드를 매칭되는 이메일 주소와 연계한 다음, 사용자가 성공적으로 로그인 한 후에 외부 ID 공급자를 연락처에 자동으로 할당합니다. 기본적으로는 거짓으로 설정됩니다.
