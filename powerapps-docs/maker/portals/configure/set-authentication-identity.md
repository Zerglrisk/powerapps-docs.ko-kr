---
title: 포털의 인증 ID 설정 | MicrosoftDocs
description: 포털의 인증 ID 설정하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 44b45a019b786da01dc686ecb69f068ce1d7eef8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756439"
---
# <a name="set-authentication-identity-for-a-portal"></a>포털의 인증 ID 설정

포털은 [ASP.NET ID](https://www.asp.net/identity) API에 구축된 인증 기능을 제공합니다. ASP.NET ID는 역시 인증 시스템의 중요한 구성 요소인 [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) 프레임워크에 구축되어 있습니다. 제공되는 서비스:

- 로컬 (사용자 이름/암호) 사용자 로그인
- 제3자 ID 공급자를 통한 외부 (소셜 공급자) 사용자 로그인
- 전자 메일 주소를 통한 2단계 인증
- 전자 메일 주소 확인
- 암호 복구
- 사전 생성된 연락처 레코드를 등록하기 위한 초대 코드 등록

> [!NOTE]
> 현재 연락처 항목의 포털 문의 양식에 있는 **휴대폰 확인됨**필드는 아무 의미가 없습니다. 이 필드는 Adxstudio Portals에서 업그레이드할 때만 사용해야 합니다.

## <a name="requirements"></a>요구 사항

포털에는 다음이 필요합니다.

- 포털 기반
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ID
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] ID 워크플로 솔루션 패키지

## <a name="authentication-overview"></a>인증 개요

돌아온 포털 방문자는 로컬 사용자 자격 증명 또는 외부 ID 공급자 계정을 사용하여 인증할 수 있습니다. 새 방문자는 사용자 이름 및 암호를 제공함으로써 또는 외부 공급자를 통해 로그인함으로써 새 사용자 계정을 등록할 수 있습니다. (포털 관리자로부터) 초대 코드를 받은 방문자는 새 사용자 계정을 위한 가입 과정에서 코드를 등록할 수 있는 옵션을 갖습니다.

**관련된 사이트 설정값:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>로컬 ID 또는 외부 ID를 사용한 로그인

![로컬 계정을 사용하여 로그인](../media/sign-in-local-account.png "로컬 계정을 사용하여 로그인")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>로컬 ID 또는 외부 ID를 사용한 가입

![새 로컬 계정에 등록](../media/register-new-local-account.png "새 로컬 계정으로 등록")  

### <a name="redeem-an-invitation-code-manually"></a>초대 코드를 수동으로 등록

![초대 코드를 사용하여 로그인](../media/sign-up-invitation-code.png "초대 코드를 사용하여 로그인")  

## <a name="forgot-password-or-password-reset"></a>암호 찾기 또는 암호 재설정 

암호 재설정을 요구하고 (이전에 사용자 프로필에 전자 메일 주소를 명시한) 돌아온 방문자는 암호 재설정 토큰을 자신의 전자 메일 계정으로 발송하도록 요청할 수 있습니다. 재설정 토큰 담당자는 토큰을 사용하여 새 암호를 선택할 수 있습니다. 또는 토큰을 포기하면 사용자의 원래 암호가 수정되지 않고 유지될 수 있습니다.

**관련된 사이트 설정값:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**관련 프로세스:** 재설정된 암호를 연락처에 발송

1.  워크플로에서 전자 메일을 필요에 따라 사용자 지정합니다.
2.  전자 메일을 제출하여 프로세스를 호출합니다.
3.  방문자에게 전자 메일을 확인하라는 메시지를 표시합니다.
4.  방문자는 지침이 있는 암호 재설정 전자 메일을 받습니다.
5.  방문자가 재설정 양식으로 돌아옵니다.
6.  암호 재설정이 완료됩니다.

## <a name="redeem-an-invitation"></a>초대 회수

초대 코드를 사용하면 등록 방문자가 그 방문자를 위해 미리 특별히 준비된 기존 연락처 레코드에 연계될 수 있습니다. 일반적으로, 초대 코드는 전자 메일로 발송되지만 다른 채널을 통해 코드를 전송하기 위해 일반 코드 제출 양식을 사용할 수 있습니다. 유효한 초대 코드를 제출하면 새 사용자 계정을 설정하기 위한 정상적 사용자 등록(가입) 프로세스가 개시됩니다.

**관련된 사이트 설정값:**

`Authentication/Registration/InvitationEnabled`

**관련 프로세스:** 초대장 발송

포털에서 초대 페이지를 사용하려면 이 워크플로에 의해 발송된 이메일을 URL과 함께 맞춤화해야 합니다. https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code(Invitation)}

1. 새 연락처를 위한 초대장 만들기.

    ![새 연락처를 위한 초대장 만들기](../media/create-invitation.png "새 연락처를 위한 초대장 만들기")  

2. 새 초대장 사용자 지정 및 저장.

    ![새 초대장 사용자 지정](../media/customize-new-invitation.png "새 초대장 사용자 지정")  

3. 프로세스: 초대장 발송
4. 초대 전자 메일 사용자 지정.
5. 초대 전자 메일은 회수 페이지를 엽니다.
6. 사용자는 제출된 초대 코드를 사용하여 가입합니다.

    ![초대 코드로 가입](../media/sign-up-invitation-code.png "초대 코드를 사용하여 로그인")  

## <a name="manage-user-accounts-through-profile-pages"></a>프로필 페이지를 통한 사용자 계정 관리

인증된 사용자는 프로필 페이지의 **보안** 탐색 바를 통해 자신의 사용자 계정을 관리합니다. 사용자는 사용자 등록 시에 선택한 단일 로컬 계정 또는 단일 외부 계정으로 제한되지 않습니다. 외부 계정을 가진 사용자는 사용자 이름과 암호를 적용하여 로컬 계정을 생성하기로 선택할 수 있습니다. 로컬 계정으로 시작한 사용자는 여러 외부 ID를 자신의 계정에 연계하기로 선택할 수 있습니다. 또한 프로필 페이지는 사용자가 확인 전자 메일이 자신의 전자 메일 계정으로 발송되도록 요청함으로써 자신의 전자 메일 주소를 확인하도록 안내되는 곳입니다.

**관련된 사이트 설정값:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>암호 설정 또는 변경

기존 로컬 계정을 가진 사용자는 원래 암호를 제공함으로써 새 암호를 신청할 수 있습니다. 로컬 계정이 없는 사용자는 사용자 이름과 암호를 선택하여 새 로컬 계정을 설정할 수 있습니다. 설정된 후에는 사용자 이름을 변경할 수 없습니다.

**관련된 사이트 설정값:**

`Authentication/Registration/LocalLoginEnabled`

**관련 프로세스:**
- 사용자 이름과 암호 생성.
- 기존 암호 변경.

## <a name="confirm-an-email-address"></a>전자 메일 주소 확인

전자 메일 주소를 변경(또는 처음으로 설정)하면 미확정 상태로 들어갑니다. 사용자는 새 전자 메일 주소로 확인 전자 메일이 발송되도록 요청할 수 있으며 이 전자 메일에는 사용자에게 전자 메일 확인 프로세스를 완료하라는 지침이 포함됩니다.

**관련 프로세스:** 연락처에 전자 메일 확인 발송

1. 워크플로에서 전자 메일을 필요에 따라 사용자 지정합니다. 
2. 사용자는 미확인 상태에 있는 새 전자 메일을 제출합니다.
3. 사용자는 확인을 위해 전자 메일을 체크합니다.
4. 프로세스: 연락처에 전자 메일 확인 발송
5. 확인 전자 메일 사용자 지정.
6. 사용자가 확인 링크를 클릭하여 확인 프로세스를 완료합니다.

> [!NOTE]
> 확인 메일이 연락처의 기본 전자 메일(emailaddress1)로만 전송되기 때문에 연락처에 대해 기본 전자 메일이 지정되었는지 확인합니다. 확인 전자 메일은 보조 전자 메일(emailaddress2) 또는 연락처 레코드의 대체 전자 메일(emailaddress3)로 전송되지 않습니다.

## <a name="enable-two-factor-authentication"></a>2단계 인증 활성화

2단계 인증 기능은 표준 로컬 또는 외부 계정 로그인에 추가하여 확인된 전자 메일 주소의 소유권 증명을 요구함으로써 사용자 계정 보안을 증대합니다. 활성화된 2단계 인증으로 계정에 로그인을 시도하는 사용자에게는 본인의 계정에 연계되어 있는 확인된 전자 메일 주소로 보안 코드가 발송됩니다. 로그인 프로세스를 완료하려면 보안 코드를 제출해야 합니다. 사용자는 후속 로그인을 위해 같은 브라우저로부터 보안 코드가 요구되지 않도록 검증을 성공적으로 통과하는 브라우저를 기억하는 것을 선택할 수 있습니다. 각 사용자 계정은 이 기능을 개별적으로 활성화하여 확인된 전자 메일 주소를 요구합니다.

> [!WARNING]
> **인증/등록/MobilePhoneEnabled** 사이트 설정을 만들어 사용 설정하여 기존 기능을 사용하도록 설정하면 오류가 발생합니다. 이 사이트 설정은 기본 제공되지 않으며 포털에서 지원되지 않습니다.

**관련된 사이트 설정값:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**관련 프로세스:** 연락처에 2단계 코드 전자 메일 발송

1. 2단계 인증 활성화.
2. 보안 코드를 전자 메일로 받기를 선택.
3. 보안 코드가 포함된 전자 메일을 기다립니다.
4. 프로세스: 연락처에 2단계 코드 전자 메일 발송.
5. 2단계 인증은 비활성화할 수 있습니다.

## <a name="manage-external-accounts"></a>외부 계정 관리

인증된 사용자는 여러 외부 ID를 구성한 각 ID 공급자 중 하나의 사용자 계정에 연결(등록)할 수 있습니다. 일단 ID가 연결되면 사용자는 연결된 ID들 중 하나를 사용하여 로그인할 수 있습니다. 또한 한 개의 외부 또는 로컬 ID가 유지되는 한 기존 ID들을 연결 해제할 수 있습니다.

**관련된 사이트 설정:**

- `Authentication/Registration/ExternalLoginEnabled`

**외부 ID 공급자 사이트 설정**

1.  사용자 계정에 연결할 공급자를 선택합니다.

    ![외부 계정 관리](../media/manage-external-accounts.png "외부 계정 관리")  

2.  연결하려는 공급자를 사용하여 로그인합니다.

이제 공급자가 연결됩니다. 공급자의 연결을 해제할 수도 있습니다.

## <a name="enable-aspnet-identity-authentication"></a>ASP.NET ID 인증 활성화

다음에서 다양한 인증 기능 및 동작을 활성화 및 비활성화하기 위한 설정에 대해 설명합니다.


|                        사이트 설정 이름                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     사용자 이름(또는 전자 메일 주소) 및 암호에 기반한 로컬 계정 로그인을 활성화 또는 비활성화합니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               사용자 이름 필드 대신에 전자 메일 주소 필드를 사용한 로컬 계정 로그인을 활성화 또는 비활성화합니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  외부 계정 로그인 및 등록을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          웹 브라우저가 닫힌 경우에도 인증된 세션을 유지할 수 있도록 하려면 로컬 로그인에서 저장? 확인란을 선택하거나 선택 취소합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        사용자가 2단계 인증을 활성화할 수 있는 옵션을 활성화 또는 비활성화합니다. 확인된 전자 메일 주소를 가진 사용자는 2단계 인증의 추가된 보안을 선택할 수 있습니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                현재 브라우저에 대한 두 번째 요소 유효성 검사를 유지하려면 두 번째 요소 유효성 검사(전자 메일 코드)에서 브라우저 저장 확인란을 선택하거나 선택 취소합니다. 사용자가 같은 브라우저를 사용하는 한 후속 로그인을 위해 두 번째 요소 검증을 통과할 것이 요구되지 않을 것입니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         암호 재설정 기능을 활성화 또는 비활성화합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               확인된 전자 메일 주소를 위해서만 암호 재설정을 활성화 또는 비활성화합니다. 활성화된 경우, 미확인된 전자 메일 주소를 사용하여 암호 재설정 지시를 보낼 수 없습니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          암호 시도 실패의 기록을 활성화 또는 비활성화합니다. 비활성화된 경우 사용자 계정이 잠가지지 않을 것입니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          개발 또는 데모 환경에서만 사용될 데모 모드 플래그를 활성화 또는 비활성화합니다. 생산 환경에서 이 설정을 활성화하지 마십시오. 또한 데모 모드에서는 웹 브라우저가 웹 응용 프로그램 서버에 로컬로 실행되어야 합니다. 데모 모드가 활성화된 경우, 빠른 액세스를 위해 암호 재설정 코드 및 2단계 코드가 사용자에게 표시됩니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | 포털이 (모든 인증을 취급하기 위해) 단일 외부 ID 공급자만 요구하는 경우, 머리글 탐색 모음의 **로그인** 버튼에서 해당 외부 ID 공급자의 로그인 페이지로 연결할 수 있습니다(중간 로컬 로그인 양식 및 ID 공급자 선택 페이지에 링크하지 않고). 이 작업을 위해서는 단일 ID 공급자만 선택될 수 있습니다. 공급자의 [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) 값을 지정하십시오.<br>Azure Active Directory B2C 사용 같은 오픈 ID 연결을 사용하는 Single Sign-On 구성의 경우, 사용자는 그 권한을 제공해야 합니다.<br>OAuth2 기반 제공자의 경우 허용되는 값: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` 또는 `Twitter`<br>WS 연합 기반 제공자의 경우 `Authentication/WsFederation/ADFS/AuthenticationType` 및 `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` 사이트 설정을 위해 지정된 값을 사용하십시오. 예: https://adfs.contoso.com/adfs/services/trust, Facebook-0123456789, Google, Yahoo!, uri:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>사용자 등록 활성화 또는 비활성화

다음에서 사용자 등록(로그인) 옵션을 활성화 및 비활성화하기 위한 설정에 대해 설명합니다.

| 사이트 설정 이름                                   | 설명                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/Enabled                 | 모든 형식의 사용자 등록을 활성화 또는 비활성화합니다. 이 섹션에서 다른 설정이 발효되려면 등록이 활성화되어야 합니다. 기본값: true                                   |
| Authentication/Registration/OpenRegistrationEnabled | 새 로컬 사용자를 생성하기 위한 가입 등록 양식을 활성화 또는 비활성화합니다. 가입 양식을 사용하여 포털의 익명 방문자가 새 사용자 계정을 생성할 수 있습니다. 기본값: true |
| Authentication/Registration/InvitationEnabled       | 초대 코드를 보유한 사용자를 등록하기 위한 초대 코드 사용 양식을 활성화 또는 비활성화합니다. 기본값: true                                                               |
|Authentication/Registration/CaptchaEnabled|사용자 등록 페이지에서 이미지 문자를 활성화 또는 비활성화합니다. 기본값: false<br>**참고**: 이 사이트 설정은 기본적으로 사용하지 못할 수도 있습니다. 이미지 문자를 활성화하려면 사이트 설정을 만들어 그 값을 true로 설정해야 합니다. |
||

> [!NOTE]
> 사용자의 기본 전자 메일(emailaddress1)을 사용하여 등록이 수행되기 때문에 사용자에 대래 기본 전자 메일이 지정되었는지 확인합니다. 사용자는 보조 전자 메일(emailaddress2) 또는 연락처 레코드의 대체 전자 메일(emailaddress3)을 사용하여 등록할 수 없습니다.

## <a name="user-credential-validation"></a>사용자 자격 증명 검증

다음에서 사용자 이름 및 암호 유효성 검사 매개 변수를 조정하기 위한 설정에 대해 설명합니다. 검증은 새 로컬 계정을 등록하거나 암호를 변경할 때 발생합니다.

| 사이트 설정 이름                                                       | 설명                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | 암호가 다음 중 세 범주에 해당하는 문자를 포함하는지 여부.<br><ul><li>유럽 언어의 대문자(A ~ Z, 분음 기호 사용, 그리스 및 키릴 문자)</li><li>유럽 언어의 소문자(A ~ Z, 뾰족한 s, 분음 기호 사용, 그리스 및 키릴 문자)</li><li>기본 10자리(0~9)</li><li>영숫자가 아닌 문자(특수 문자)(예: !, $, \#, %)</li></ul>기본값: true 추가 정보: [암호 정책](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx).                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | 사용자 이름에 영숫자 문자만 허용 여부. 기본값: false 추가 정보: [UserValidator<TUser, TKey>.AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx).                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | 사용자를 검증하기 위해 고유한 전자 메일 주소가 필요한지의 여부. 기본값: true 추가 정보: [UserValidator<TUser, TKey>.RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx).                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 요구되는 최소 암호 길이. 기본: 8 추가 정보: [PasswordValidator.RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx).                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | 암호가 비문자 또는 숫자를 요구하는지의 여부. 기본값: false 추가 정보: [PasswordValidator.RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | 암호가 숫자(0~9)를 요구하는지의 여부. 기본값: false 추가 정보: [PasswordValidator.RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx).                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | 암호가 소문자(a~z)를 요구하는지의 여부. 기본값: false 추가 정보: [PasswordValidator.RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | 암호가 대문자(A~Z)를 요구하는지의 여부. 기본값: false 추가 정보: [PasswordValidator.RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>사용자 계정 잠금 설정

다음에서 언제 어떻게 계정을 인증하지 못하도록 잠글지를 규정하는 설정에 대해 설명합니다. 단기간에 특정 수의 암호 시도 실패가 감지되면 사용자 계정이 일정 시간 동안 잠가집니다. 사용자는 잠금 기간이 경과한 후에 다시 시도할 수 있습니다.

| 사이트 설정 이름                                               | 설명                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | 사용자가 생성될 때 사용자 잠금이 활성화되는지의 여부를 표시합니다. 기본값: true 추가 정보: [UserManager<TUser, TKey>.UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout이 도달한 후 사용자를 잠그는 시간의 기본값입니다. 기본값: 24:00:00(1일). 추가 정보: [UserManager<TUser, TKey>.DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | (잠금이 활성화된 경우) 사용자가 잠가지기 전 허용되는 액세스 시도의 최대 수. 기본: 5 추가 정보: [UserManager<TUser, TKey>.MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | 다음에 대한 쿠키 인증 세션의 기본 시간이 유효합니다. 기본값: 24:00:00(1일). 추가 정보: [CookieAuthenticationOptions.ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx). |
||  

## <a name="cookie-authentication-site-settings"></a>쿠키 인증 사이트 설정

기본 인증 쿠키 동작을 수정하기 위한 설정입니다. [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) 클래스에 의해 정의됩니다.

| 사이트 설정 이름   | 설명       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | 응용 프로그램 인증 쿠키 유형입니다. 기본값: 응용 프로그램 쿠키. 자세한 내용은 [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)을 참조하십시오.  |
| Authentication/ApplicationCookie/CookieName                              | id를 지속하는 데 사용되는 쿠키 이름을 결정합니다. 기본값: .AspNet.Cookies. 추가 정보: [CookieAuthenticationOptions::CookieName](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Authentication/ApplicationCookie/CookieDomain                            | 쿠키를 만드는 데 사용되는 도메인을 결정합니다. 추가 정보: [CookieAuthenticationOptions::CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/ApplicationCookie/CookiePath                              | 쿠키를 만드는 데 사용되는 경로를 결정합니다. 기본값: /. 추가 정보: [CookieAuthenticationOptions::CookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Authentication/ApplicationCookie/CookieHttpOnly                          | 브라우저에서 클라이언트 쪽 javascript가 쿠키에 액세스하도록 허용할지 여부를 결정합니다. 기본값: true 추가 정보: [CookieAuthenticationOptions::CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Authentication/ApplicationCookie/CookieSecure                            | 쿠키가 HTTPS 요청 시에만 전송되어야 하는지 여부를 결정합니다. 기본값: SameAsRequest. 추가 정보: [CookieAuthenticationOptions::CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | 응용 프로그램 쿠키가 만들어진 지점에서 유효한 상태로 유지되는 시간을 제어합니다. 기본값: 14일. 추가 정보: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration은 미들웨어가 만료 기간을 절반 이상 경과한 요청을 처리할 때마다 새 만료 시간으로 새 쿠키를 다시 발급하도록 하기 위해 true로 설정되었습니다. 기본값: true 추가 정보: [CookieAuthenticationOptions::SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Authentication/ApplicationCookie/LoginPath                               | LoginPath 속성은 302 리디렉션으로 나가는 401 승인되지 않음 상태 코드를 지정된 로그인 경로로 변경해야 한다고 미들웨어에 알려 줍니다. 기본값: ~/signin. 추가 정보: [CookieAuthenticationOptions::LoginPath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Authentication/ApplicationCookie/LogoutPath                              | LogoutPath가 미들웨어를 제공하는 경우 해당 경로에 대한 요청은 ReturnUrlParameter를 기반으로 리디렉션됩니다. 추가 정보: [CookieAuthenticationOptions::LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter는 로그인 경로에서 401 승인되지 않음 상태 코드가 302 리디렉션으로 변경될 때 미들웨어에 의해 추가되는 쿼리 문자열 매개 변수의 이름을 결정합니다. 추가 정보: [CookieAuthenticationOptions::ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | 보안 스탬프 유효성 검사 사이의 시간 간격입니다. 기본값: 30분. 추가 정보: [SecurityStampValidator::OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 두 요소 인증 쿠키 유형입니다. 기본값: TwoFactorCookie. 자세한 내용은 [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)을 참조하십시오.            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 두 요소 쿠키가 만들어진 지점에서 유효한 상태로 유지되는 시간을 제어합니다. 기본값: 5분. 추가 정보: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>참조

[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대한 ID 연결 공급자 열기](configure-openid-settings.md)  
[포털에 대한 WS-Federation 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  
