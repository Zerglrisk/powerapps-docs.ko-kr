---
title: 질문과 대답 | Microsoft Docs
description: PowerApps 포털에 대 한 질문과 대답입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: eb7228f669fe8c36e25a18f4db0c7e4c4964a42d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976694"
---
# <a name="powerapps-portals-faq"></a>PowerApps 포털 FAQ

자주 묻는 질문과 대답 목록을 컴파일하고 정보를 신속 하 게 가져오는 데 도움이 되는 간단한 대답을 제공 합니다.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>하나의 포털만 만들 수 있다는 오류가 발생 합니다.

현재는 언어별로 환경에서 각 유형의 포털을 하나만 만들 수 있습니다. 둘 이상의 포털을 만들려고 하면 다음과 같은 오류 메시지가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![최대 포털 생성 오류](media/portal-max-error.png "최대 포털 생성 오류")

더 많은 포털을 만들려면 오류 메시지에서 **새 환경 만들기** 링크를 사용 하 여 새 환경을 만들어야 합니다. 포털을 만드는 방법에 대 한 자세한 내용은 [포털 만들기](create-portal.md)를 참조 하세요.

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>포털을 삭제할 수 없다는 오류가 발생 합니다.

포털을 삭제할 수 있는 권한이 없는 경우 다음과 같은 오류가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![포털 삭제 오류](media/portal-delete-error.png "포털 삭제 오류")

포털 및 필요한 권한 삭제에 대 한 자세한 내용은 [포털 삭제](manage-existing-portals.md#delete)를 참조 하세요.

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>포털을 만들 수 없다는 오류가 발생 합니다.

환경에서 포털을 만들 수 있는 충분 한 권한이 없는 경우 다음과 같은 오류가 표시 됩니다.

> [!div class=mx-imgBorder]
> 포털 만들기 ![오류](media/portal-create-error.png "포털 만들기 오류")

포털 및 필요한 권한 만들기에 대 한 자세한 내용은 [포털 만들기](create-portal.md)를 참조 하세요.

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>"데이터가 아직 준비 되지 않았습니다." 라는 메시지를 받고 있습니다.

경우에 따라 데이터베이스를 만드는 데 시간이 걸리고 홈 페이지에 올바른 상태가 반영 되지 않을 수 있습니다. 이 경우 다음과 같은 메시지가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![데이터 준비]안 됨(media/data-not-ready.png "데이터가 준비 되지") 않음

데이터베이스 만들기 프롬프트를 계속 표시 하거나 데이터에 대 한 준비가 되지 않은 경우에는 **빈 타일에서 포털** 을 선택 하기 전에 PowerApps 홈 페이지를 새로 고쳐 볼 수 있습니다.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory 응용 프로그램을 만드는 데 필요한 권한이 없다는 오류가 발생 합니다.

포털을 만들 때 새 응용 프로그램은 테 넌 트와 연결 된 Azure Active Directory에 등록 됩니다. Azure Active Directory 테 넌 트에 응용 프로그램을 등록할 수 있는 권한이 없는 경우 다음과 같은 오류가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![Azure Active Directory 오류](media/azure-ad-error.png "Azure Active Directory 오류")

Azure Active Directory에서 응용 프로그램을 만들고 등록 하려면 테 넌 트 관리자에 게 문의 하 여 테 넌 트에 대 한 **앱 등록** 설정을 켜야 합니다. 자세한 내용은 [필요한 권한](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)을 참조 하세요.

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>전역 관리자가이 테 넌 트에서 포털 만들기가 차단 되었다는 오류가 발생 합니다.

전역 관리자가 테 넌 트에서 포털 만들기가 차단 된 경우 다음과 같은 오류가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![포털 만들기가 차단 됨 오류](media/portal-create-blocked-error.png "포털 만들기 차단 오류")

관리자가 아닌 사용자가 포털을 만들 수 있도록 하려면 전역 관리자에 게 문의 해야 합니다.

전역 관리자 인 경우 PowerShell을 통해 `disablePortalsCreationByNonAdminUsers` 테 넌 트 수준 설정을 사용 하지 않도록 설정 해야 합니다. PowerShell 창에서 다음 명령을 실행 합니다 (관리자 권한으로 PowerShell 실행).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

추가 정보: [테 넌 트에서 포털 만들기를 사용 하지 않도록 설정](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>이 웹 사이트에 액세스할 수 있는 적절 한 라이선스가 없다는 오류가 표시 됩니다.

포털을 사용 하 여 인증 된 페이지에 액세스 하는 조직의 내부 사용자에 게는 포털이 연결 된 환경에 라이선스를 할당 해야 합니다. 내부 사용자에 대 한 포털의 사용자 권한에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users)를 참조 하세요. 환경에 라이선스가 할당 되지 않은 경우 내부 사용자에 게 다음과 같은 오류가 발생 합니다.

> [!div class=mx-imgBorder]
> ![포털 로그인 오류](media/portal-login-error.png "포털 로그인 오류")

