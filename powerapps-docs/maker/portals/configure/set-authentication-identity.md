---
title: 포털에 대 한 인증 id 설정 | MicrosoftDocs
description: 포털에 대 한 인증 id를 설정 하는 지침입니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542666"
---
# <a name="set-authentication-identity-for-a-portal"></a>포털에 대 한 인증 id 설정

포털은 [ASP.NET Identity](https://www.asp.net/identity) API에 구축 된 인증 기능을 제공 합니다. ASP.NET Identity는 인증 시스템의 중요 한 구성 요소인 [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) 프레임 워크를 기반으로 합니다. 제공 되는 서비스는 다음과 같습니다.

- 로컬 (사용자 이름/암호) 사용자 로그인
- 타사 id 공급자를 통한 외부 (소셜 공급자) 사용자 로그인
- 전자 메일을 사용 하는 2 단계 인증
- 전자 메일 주소 확인
- 암호 복구
- 사전 생성 된 contact 레코드를 등록 하기 위한 초대 코드 등록

> [!NOTE]
> 포털 연락처 엔터티의 포털 연락처 폼에 있는 **휴대폰 확인** 필드는 현재 용도 없이 사용 됩니다. 이 필드는 Adxstudio 포털에서 업그레이드 하는 경우에만 사용 해야 합니다.

## <a name="requirements"></a>사항이

포털에는 다음이 필요 합니다.

- 포털 기준
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Id
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Identity 워크플로 솔루션 패키지

## <a name="authentication-overview"></a>인증 개요

포털 방문자를 반환 하면 로컬 사용자 자격 증명 또는 외부 id 공급자 계정을 사용 하 여 인증할 수 있습니다. 새 방문자는 사용자 이름 및 암호를 제공 하거나 외부 공급자를 통해 로그인 하 여 새 사용자 계정을 등록할 수 있습니다. 포털 관리자가 초대 코드를 보낸 방문자는 새 사용자 계정에 등록 하는 과정에서 코드를 사용 하는 옵션을 사용할 수 있습니다.

**관련 사이트 설정:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>로컬 id 또는 외부 id를 사용 하 여 로그인

![로컬 계정을 사용 하 여 로그인](../media/sign-in-local-account.png "로컬 계정을 사용 하 여 로그인")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>로컬 id 또는 외부 id를 사용 하 여 등록

![새 로컬 계정 등록](../media/register-new-local-account.png "새 로컬 계정 등록")  

### <a name="redeem-an-invitation-code-manually"></a>수동으로 초대 코드 교환

![초대 코드를 사용 하 여 등록](../media/sign-up-invitation-code.png "초대 코드를 사용 하 여 등록")  

## <a name="forgot-password-or-password-reset"></a>암호 또는 암호 다시 설정 잊음 

암호 재설정을 필요로 하 고 이전에 사용자 프로필에 전자 메일 주소를 지정한 방문자를 반환 하면 암호 재설정 토큰이 전자 메일 계정으로 전송 되도록 요청할 수 있습니다. 다시 설정 토큰은 소유자가 새 암호를 선택할 수 있도록 합니다. 또는 토큰을 중단 하 고 사용자의 원래 암호를 수정 하지 않은 상태로 둘 수 있습니다.

**관련 사이트 설정:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**관련 프로세스:** 연락처로 암호 재설정 보내기

1.  필요에 따라 워크플로에서 전자 메일을 사용자 지정 합니다.
2.  프로세스를 호출 하는 전자 메일을 제출 합니다.
3.  방문자에 게 전자 메일을 확인 하 라는 메시지가 표시 됩니다.
4.  방문자는 지침이 포함 된 암호 재설정 전자 메일을 받습니다.
5.  방문자가 reset 폼으로 돌아갑니다.
6.  암호 재설정이 완료 되었습니다.

## <a name="redeem-an-invitation"></a>초대를 교환 합니다.

초대 코드를 교환 하면 등록 방문자가 해당 방문자에 대해 미리 준비 된 기존 연락처 레코드와 연결 될 수 있습니다. 일반적으로 초대 코드는 전자 메일로 전송 되지만 다른 채널을 통해 코드를 전송 하는 일반 코드 전송 양식을 사용할 수 있습니다. 유효한 초대 코드를 제출한 후에는 일반 사용자 등록 (등록) 프로세스가 새 사용자 계정을 설정 하는 데 사용 됩니다.

**관련 사이트 설정:**

`Authentication/Registration/InvitationEnabled`

**관련 프로세스:** 초대 보내기

포털의 사용 초대 페이지에 대 한 URL을 사용 하 여이 워크플로에서 보낸 전자 메일을 사용자 지정 해야 합니다. https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation 코드 (초대)}

1. 새 연락처에 대 한 초대를 만듭니다.

    ![새 연락처에 대 한 초대 만들기](../media/create-invitation.png "새 연락처에 대 한 초대 만들기")  

2. 새 초대를 사용자 지정 하 고 저장 합니다.

    ![새 초대 사용자 지정](../media/customize-new-invitation.png "새 초대 사용자 지정")  

3. 프로세스: 초대 보내기
4. 초대 전자 메일을 사용자 지정 합니다.
5. 초대 전자 메일에서 상환 페이지가 열립니다.
6. 사용자는 제출 된 초대 코드를 사용 하 여 등록 합니다.

    ![초대 코드를 사용 하 여 등록](../media/sign-up-invitation-code.png "초대 코드를 사용 하 여 등록")  

## <a name="manage-user-accounts-through-profile-pages"></a>프로필 페이지를 통해 사용자 계정 관리

인증 된 사용자는 프로필 페이지의 **보안** 탐색 모음을 통해 사용자 계정을 관리 합니다. 사용자는 단일 로컬 계정이 나 사용자 등록 시 선택한 단일 외부 계정으로 제한 되지 않습니다. 외부 계정이 있는 사용자는 사용자 이름 및 암호를 적용 하 여 로컬 계정을 만들도록 선택할 수 있습니다. 로컬 계정으로 시작한 사용자는 여러 외부 id를 계정에 연결 하도록 선택할 수 있습니다. 프로필 페이지에는 전자 메일 계정으로 전송 되는 확인 전자 메일을 요청 하 여 사용자에 게 전자 메일 주소를 확인 하는 메시지가 있습니다.

**관련 사이트 설정:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>암호 설정 또는 변경

기존 로컬 계정이 있는 사용자는 원래 암호를 제공 하 여 새 암호를 적용할 수 있습니다. 로컬 계정이 없는 사용자는 사용자 이름 및 암호를 선택 하 여 새 로컬 계정을 설정할 수 있습니다. 사용자 이름은 설정한 후에는 변경할 수 없습니다.

**관련 사이트 설정:**

`Authentication/Registration/LocalLoginEnabled`

**관련 프로세스:**
- 사용자 이름 및 암호를 만듭니다.
- 기존 암호를 변경 합니다.

## <a name="confirm-an-email-address"></a>전자 메일 주소 확인

전자 메일 주소를 변경 하거나 처음으로 설정 하면 확인 되지 않은 상태가 됩니다. 사용자는 새 전자 메일 주소로 보낼 확인 전자 메일을 요청할 수 있으며 전자 메일에는 전자 메일 확인 프로세스를 완료 하기 위한 지침이 포함 됩니다.

**관련 프로세스:** 연락처에 전자 메일 확인 보내기

1. 필요에 따라 워크플로에서 전자 메일을 사용자 지정 합니다. 
2. 사용자가 확인 되지 않은 상태에 있는 새 전자 메일을 제출 합니다.
3. 사용자가 전자 메일을 확인 하 여 확인 합니다.
4. 프로세스: 연락처에 전자 메일 확인 보내기
5. 확인 전자 메일을 사용자 지정 합니다.
6. 사용자가 확인 링크를 클릭 하 여 확인 프로세스를 완료 합니다.

> [!NOTE]
> 확인 전자 메일이 연락처의 기본 전자 메일 (emailaddress1)에만 전송 되므로 연락처에 대해 기본 전자 메일을 지정 해야 합니다. 확인 전자 메일은 연락처 레코드의 보조 전자 메일 (emailaddress2) 또는 대체 전자 메일 (emailaddress3)에 전송 되지 않습니다.

## <a name="enable-two-factor-authentication"></a>2 단계 인증 사용

2 단계 인증 기능은 표준 로컬 또는 외부 계정 로그인 외에도 확인 된 전자 메일의 소유권 증명을 요구 하 여 사용자 계정 보안을 향상 시킵니다. 2 단계 인증을 사용 하도록 설정 된 계정에 로그인 하려는 사용자는 해당 계정과 연결 된 확인 된 전자 메일에 보안 코드를 보냅니다. 로그인 프로세스를 완료 하려면 보안 코드를 제출 해야 합니다. 사용자는 인증을 성공적으로 통과 한 브라우저를 기억할 수 있습니다. 그러면 동일한 브라우저에서 후속 로그인에 보안 코드가 필요 하지 않습니다. 각 사용자 계정은이 기능을 개별적으로 사용 하도록 설정 하 고 확인 된 전자 메일이 필요 합니다.

> [!WARNING]
> **인증/등록/MobilePhoneEnabled** 사이트 설정을 만들고 사용 하도록 설정 하 여 레거시 기능을 사용 하도록 설정 하면 오류가 발생 합니다. 이 사이트 설정은 포털에서 지원 하지 않는 기본 제공 되지 않습니다.

**관련 사이트 설정:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**관련 프로세스:** 연락처에 2 단계 코드 전자 메일 보내기

1. 2 단계 인증을 사용 하도록 설정 합니다.
2. 전자 메일을 통해 보안 코드를 받도록 선택 합니다.
3. 보안 코드가 포함 된 전자 메일을 기다립니다.
4. 프로세스: Contact에 전자 메일 2 단계 코드를 보냅니다.
5. 2 단계 인증을 사용 하지 않도록 설정할 수 있습니다.

## <a name="manage-external-accounts"></a>외부 계정 관리

인증 된 사용자는 각각의 구성 된 id 공급자에서 하나씩 여러 외부 id를 사용자 계정에 연결 (등록) 할 수 있습니다. Id가 연결 된 후 사용자는 연결 된 id를 사용 하 여 로그인 하도록 선택할 수 있습니다. 단일 외부 또는 로컬 id가 남아 있으면 기존 id의 연결을 끊을 수도 있습니다.

**관련 사이트 설정:**

- `Authentication/Registration/ExternalLoginEnabled`

**외부 Id 공급자 사이트 설정**

1.  사용자 계정에 연결할 공급자를 선택 합니다.

    ![외부 계정 관리](../media/manage-external-accounts.png "외부 계정 관리")  

2.  연결 하려는 공급자를 사용 하 여 로그인 합니다.

이제 공급자가 연결 되었습니다. 공급자의 연결을 끊을 수도 있습니다.

## <a name="enable-aspnet-identity-authentication"></a>ASP.NET identity authentication 사용

다음은 다양 한 인증 기능 및 동작을 사용 하거나 사용 하지 않도록 설정 하는 설정에 대 한 설명입니다.


|                        사이트 설정 이름                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          인증/등록/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     사용자 이름 (또는 전자 메일) 및 암호를 기반으로 로컬 계정 로그인을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          인증/등록/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               사용자 이름 필드 대신 전자 메일 주소 필드를 사용 하 여 로컬 계정 로그인을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        인증/등록/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  외부 계정 로그인 및 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          인증/등록/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          암호를 선택 하거나 선택 취소 합니다. 로컬 로그인의 확인란을 선택 하면 웹 브라우저가 닫힌 경우에도 인증 된 세션을 유지할 수 있습니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          인증/등록/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        사용자가 2 단계 인증을 사용 하도록 설정 하는 옵션을 사용 하거나 사용 하지 않도록 설정 합니다. 확인 된 전자 메일 주소를 가진 사용자는 2 단계 인증에 대 한 추가 보안을 선택할 수 있습니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                기억할 브라우저를 선택 하거나 선택 취소 합니다. 2 단계 유효성 검사 (전자 메일 코드)의 확인란을 선택 하 여 현재 브라우저에 대 한 두 번째 단계 유효성 검사를 유지 합니다. 사용자는 동일한 브라우저를 사용 하는 동안 후속 로그인에 대 한 두 번째 단계 유효성 검사를 통과 하지 않아도 됩니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         암호 재설정 기능을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 인증/등록/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               확인 전자 메일 주소에 대해서만 암호 재설정을 사용 하거나 사용 하지 않도록 설정 합니다. 사용 하도록 설정 하면 확인 되지 않은 전자 메일 주소를 사용 하 여 암호 재설정 지침을 보낼 수 없습니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   인증/등록/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          실패 한 암호 시도 기록을 사용 하거나 사용 하지 않도록 설정 합니다. 사용 하지 않도록 설정 된 경우 사용자 계정이 잠기지 않습니다. 기본값: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          개발 또는 시연 환경 에서만 사용 되는 데모 모드 플래그를 사용 하거나 사용 하지 않도록 설정 합니다. 프로덕션 환경에서는이 설정을 사용 하지 마십시오. 또한 데모 모드에서는 웹 브라우저가 웹 응용 프로그램 서버에서 로컬로 실행 되 고 있어야 합니다. 데모 모드를 사용 하는 경우 빠른 액세스를 위해 암호 재설정 코드와 두 번째 단계 코드가 사용자에 게 표시 됩니다. 기본값: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    인증/등록/LoginButtonAuthenticationType    | 포털에 모든 인증을 처리 하기 위한 단일 외부 id 공급자만 필요한 경우에는 헤더 탐색 모음의 **로그인** 단추를 사용 하 여 해당 외부 id 공급자의 로그인 페이지에 직접 연결할 수 있습니다 (대신 중간에 연결). 로컬 로그인 양식 및 id 공급자 선택 페이지). 이 작업에는 단일 id 공급자만 선택할 수 있습니다. 공급자의 [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) 값을 지정 합니다.<br>Azure Active Directory B2C 사용과 같이 OpenIdConnect를 사용 하는 Single Sign-On 구성의 경우 사용자는 권한을 제공 해야 합니다.<br>OAuth2 기반 공급자의 경우 허용 되는 값은 `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` 또는 `Twitter`입니다.<br>WS-FEDERATION 기반 공급자의 경우 `Authentication/WsFederation/ADFS/AuthenticationType` 및 `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` 사이트 설정에 지정 된 값을 사용 합니다. 예: https://adfs.contoso.com/adfs/services/trust , Facebook-0123456789, Google, Yahoo!, uri:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>사용자 등록 사용 또는 사용 안 함

다음은 사용자 등록 (등록) 옵션을 사용 하거나 사용 하지 않도록 설정 하는 설정에 대 한 설명입니다.

| 사이트 설정 이름                                   | 설명                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 인증/등록/사용                 | 모든 형태의 사용자 등록을 사용 하거나 사용 하지 않도록 설정 합니다. 이 섹션의 다른 설정이 적용 되려면 등록을 사용 하도록 설정 되어 있어야 합니다. 기본값: true                                   |
| 인증/등록/OpenRegistrationEnabled | 새 로컬 사용자를 만들기 위한 등록 등록 양식을 사용 하거나 사용 하지 않도록 설정 합니다. 등록 양식을 통해 모든 익명 방문자가 포털을 통해 새 사용자 계정을 만들 수 있습니다. 기본값: true |
| 인증/등록/InvitationEnabled       | 초대 코드를 소유 하는 사용자를 등록 하기 위한 초대 코드 상환 형식을 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: true                                                               |
|인증/등록/CaptchaEnabled|사용자 등록 페이지에서 captcha를 사용 하거나 사용 하지 않도록 설정 합니다. 기본값: false<br>**참고**:이 사이트 설정은 기본적으로 사용 하지 못할 수 있습니다. Captcha를 사용 하도록 설정 하려면 사이트 설정을 만들고 해당 값을 true로 설정 해야 합니다. |
||

> [!NOTE]
> 사용자의 기본 전자 메일 (emailaddress1)을 사용 하 여 등록을 수행 하기 때문에 사용자에 대해 기본 전자 메일을 지정 했는지 확인 합니다. 사용자는 연락처 레코드의 보조 전자 메일 (emailaddress2) 또는 대체 전자 메일 (emailaddress3)을 사용 하 여 등록할 수 없습니다.

## <a name="user-credential-validation"></a>사용자 자격 증명 유효성 검사

다음은 사용자 이름 및 암호 유효성 검사 매개 변수를 조정 하는 설정에 대 한 설명입니다. 사용자가 새 로컬 계정을 등록 하거나 암호를 변경할 때 유효성 검사가 수행 됩니다.

| 사이트 설정 이름                                                       | 설명                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | 암호에 다음 범주의 세 가지 문자를 포함할지 여부를 지정 합니다.<br><ul><li>유럽 언어의 대문자 (A ~ Z, 분음 부호, 그리스어 및 키릴 자모 문자 포함)</li><li>유럽 언어 소문자 (a ~ z, 선명한 문자, 분음 부호, 그리스어 및 키릴 자모 문자 포함)</li><li>밑수 10 자리 (0-9)</li><li>영숫자가 아닌 문자 (특수 문자) (예:!, $, \#,%)</li></ul>기본값: true 자세한 내용은 [암호 정책](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx)을.                                                                                                           |  
| Authentication/UserManager/Usermanager/AllowOnlyAlphanumericUserNames | 사용자 이름에 영숫자 문자만 허용 하는지 여부입니다. 기본값: false 자세한 내용은 [Uservalidator < TUser, TKey >를 사용 합니다. AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx).                                                          |  
| Authentication/UserManager/Usermanager/RequireUniqueEmail             | 사용자의 유효성을 검사 하는 데 고유한 전자 메일 주소가 필요한 지 여부입니다. 기본값: true 자세한 내용은 [Uservalidator < TUser, TKey >를 사용 합니다. RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx).                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 필요한 최소 암호 길이입니다. 기본값: 8. 추가 정보: [Passwordvalidator. RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx)                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | 암호에 문자 또는 숫자가 아닌 문자를 사용 해야 하는지 여부를 나타냅니다. 기본값: false 추가 정보: [Passwordvalidator. RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | 암호에 숫자 (0-9)가 필요한 지 여부를 나타냅니다. 기본값: false 추가 정보: [Passwordvalidator.](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx)                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | 암호에 소문자 (a ~ z)가 필요한 지 여부입니다. 기본값: false 추가 정보: [Passwordvalidator](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | 암호에 대문자 (A ~ Z)가 필요한 지 여부를 나타냅니다. 기본값: false 추가 정보: [Passwordvalidator](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>사용자 계정 잠금 설정

다음은 인증에서 계정이 잠기는 방법과 시기를 정의 하는 설정에 대 한 설명입니다. 짧은 시간 동안 실패 한 암호 시도 횟수를 검색 하면 일정 시간 동안 사용자 계정이 잠깁니다. 잠금 기간이 경과 된 후에는 사용을 다시 시도할 수 있습니다.

| 사이트 설정 이름                                               | 설명                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | 사용자를 만들 때 사용자 잠금이 설정 되었는지 여부를 나타냅니다. 기본값: true 자세한 내용은 [Usermanager < TUser, TKey >를 사용 합니다. UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | 인증/u s e r/MaxFailedAccessAttemptsBeforeLockout에 도달한 후 사용자가 잠기는 기본 시간입니다. 기본값: 24:00:00 (1 일) 자세한 내용은 [Usermanager < TUser, TKey >를 사용 합니다. DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | 잠금이 설정 된 경우 사용자가 잠기기 전에 허용 되는 최대 액세스 시도 횟수입니다. 기본값은 5입니다. 자세한 내용은 [Usermanager < TUser, TKey >를 사용 합니다. MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | 의 기본 시간 쿠키 인증 세션은에 유효 합니다. 기본값: 24:00:00 (1 일) 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype. ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)을 (를) 수행 하세요. |
||  

## <a name="cookie-authentication-site-settings"></a>쿠키 인증 사이트 설정

기본 인증 쿠키 동작을 수정 하는 설정입니다. [은 cookieauthenticationoptions.authenticationtype](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) 클래스에 의해 정의 됩니다.

| 사이트 설정 이름   | 설명       |
|----------------------|------------------------------------------------|
| 인증/s s s/AuthenticationType                      | 응용 프로그램 인증 쿠키의 유형입니다. 기본값: ApplicationCookie. 추가 정보: [Authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)  |
| Authentication/ApplicationCookie/CookieName                              | Id를 유지 하는 데 사용 되는 쿠키 이름을 결정 합니다. 기본값은입니다. AspNet. 쿠키. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: CookieName](https://msdn.microsoft.com/library/dn385537.aspx)를 추가 합니다.  |
| Authentication/ApplicationCookie/CookieDomain                            | 쿠키를 만드는 데 사용 되는 도메인을 결정 합니다. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx)를 추가 합니다.  |
| Authentication/ApplicationCookie/CookiePath                              | 쿠키를 만드는 데 사용 되는 경로를 결정 합니다. 기본값은/입니다. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: CookiePath](https://msdn.microsoft.com/library/dn385539.aspx)를 추가 합니다. |
| Authentication/ApplicationCookie/CookieHttpOnly                          | 브라우저에서 클라이언트 쪽 javascript가 쿠키에 액세스할 수 있어야 하는지 여부를 결정 합니다. 기본값: true 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx)를 추가 합니다.                     |
| Authentication/ApplicationCookie/CookieSecure                            | 쿠키가 HTTPS 요청 에서만 전송 되어야 하는지 여부를 결정 합니다. 기본값: SameAsRequest. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx)를 추가 합니다.  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | 응용 프로그램 쿠키가 생성 된 시점부터 유효한 상태로 유지 되는 시간을 제어 합니다. 기본값: 14 일 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)를 추가 합니다.  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration는 만료 기간을 초과 하는 요청을 처리할 때마다 새 만료 시간을 사용 하 여 새 쿠키를 다시 발급 하도록 미들웨어에 지시 하기 위해 true로 설정 됩니다. 기본값: true 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx)를 추가 합니다. |
| Authentication/ApplicationCookie/LoginPath                               | LoginPath 속성은 보내는 401 권한 없음 상태 코드를 지정 된 로그인 경로에 대 한 302 리디렉션으로 변경 해야 함을 미들웨어에 게 알립니다. 기본값: ~/signin. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: LoginPath](https://msdn.microsoft.com/library/dn385541.aspx)를 추가 합니다.                                            |
| Authentication/ApplicationCookie/LogoutPath                              | LogoutPath가 미들웨어를 제공 하는 경우 해당 경로에 대 한 요청은 ReturnUrlParameter에 따라 리디렉션됩니다. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx)를 추가 합니다.               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter는 401 권한 없음 상태 코드가 로그인 경로에 대 한 302 리디렉션으로 변경 될 때 미들웨어에 의해 추가 되는 쿼리 문자열 매개 변수의 이름을 결정 합니다. 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx)를 추가 합니다.                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | 보안 스탬프 유효성 검사 간의 시간 간격입니다. 기본값: 30 분 자세한 내용은 [SecurityStampValidator:: OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx)를 추가 합니다.                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 2 단계 인증 쿠키의 유형입니다. 기본값: TwoFactorCookie. 추가 정보: [Authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 2 단계 쿠키가 생성 된 시점부터 유효한 상태로 유지 되는 시간을 제어 합니다. 기본값: 5 분 자세한 내용은 [은 cookieauthenticationoptions.authenticationtype:: ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx)를 추가 합니다.     |
|||

### <a name="see-also"></a>참고 항목

[포털 인증 구성](configure-portal-authentication.md)  
[포털에 대 한 OAuth2 공급자 설정](configure-oauth2-settings.md)  
[포털에 대 한 Open ID Connect 공급자 설정](configure-openid-settings.md)  
[포털에 대 한 WS-FEDERATION 공급자 설정](configure-ws-federation-settings.md)  
[포털에 대 한 SAML 2.0 공급자 설정](configure-saml2-settings.md)  
