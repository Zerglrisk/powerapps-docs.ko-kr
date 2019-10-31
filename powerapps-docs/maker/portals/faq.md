---
title: 질문과 대답 | Microsoft Docs
description: PowerApps 포털의 질문과 대답입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-portals-faq"></a>PowerApps 포털 FAQ

우리는 질문과 대답의 목록을 컴파일하고 귀하의 정보를 신속하게 얻을 수 있도록 간단한 답변을 제공했습니다.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>하나의 포털만 만들 수 있다는 오류가 발생합니다.

현재 언어별로 환경에서 각 유형의 포털을 하나만 작성할 수 있습니다. 둘 이상의 포털을 작성하려고 하면 다음과 같은 오류 메시지가 표시됩니다.

> [!div class=mx-imgBorder]
> ![최대 포털 생성 오류](media/portal-max-error.png "최대 포털 생성 오류")

더 많은 포털을 작성하려면 오류 메시지에 **새로운 환경 만들기** 링크를 사용하여 새 환경을 작성해야 합니다. 포털 만들기에 대한 자세한 내용은 [포털 만들기](create-portal.md)를 참조하십시오.

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>포털을 삭제할 수 없다는 오류가 발생합니다.

포털을 삭제할 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 삭제 오류](media/portal-delete-error.png "포털 삭제 오류")

포털 삭제 및 필요한 권한에 대한 정보는 [포털 삭제](manage-existing-portals.md#delete)를 참조하십시오.

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>포털을 만들 수 없다는 오류가 발생합니다.

환경에서 포털을 만들 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 만들기 오류](media/portal-create-error.png "포털 만들기 오류")

포털 만들기 및 필요한 권한에 대한 정보는 [포털 만들기](create-portal.md)를 참조하십시오.

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>"데이터가 준비되지 않았습니다"라는 메시지가 나타납니다.

때때로 데이터베이스 작성에 시간이 걸리고 올바른 상태가 홈 페이지에 반영되지 않을 수 있습니다. 이 경우 다음과 같은 메시지가 나타납니다.

> [!div class=mx-imgBorder]
> ![준비되지 않은 데이터](media/data-not-ready.png "준비되지 않은 데이터")

데이터베이스 작성 프롬프트 또는 데이터가 준비되지 않았다는 프롬프트가 계속 표시되는 경우 빈(미리 보기) 타일에서 포털을 선택하기 전에 PowerApps 홈 페이지를 새로 고쳐 봅니다.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory 애플리케이션을 만드는 데 필요한 권한이 없다는 오류가 표시됩니다.

포털을 만들면 포털이 테넌트와 연결된 Azure Active Directory에 새 애플리케이션으로 등록됩니다. Azure Active Directory 테넌트로 애플리케이션을 등록할 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![Azure Active Directory 오류](media/azure-ad-error.png "Azure Active Directory 오류")

Azure Active Directory에서 애플리케이션을 만들고 등록하려면 테넌트 관리자에게 문의하여 테넌트에 대한 **앱 등록** 설정을 켭니다. 자세한 내용은 [필요한 권한](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)을 참조하십시오.

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>이 테넌트에서 포털 작성이 전역 관리자에 의해 차단되었다는 오류가 발생합니다.

전역 관리자가 테넌트에서 포털 작성을 차단하면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 생성 차단 오류](media/portal-create-blocked-error.png "포털 생성 차단 오류")

관리자가 아닌 사람도 포털을 작성할 수 있도록 하려면 전역 관리자에게 문의해야 합니다.

전역 관리자인 경우 PowerShell을 통해 `disablePortalsCreationByNonAdminUsers` 테넌트 수준 설정을 해제해야 합니다. PowerShell 창에서 다음 명령을 실행합니다(관리자 권한으로 PowerShell 실행).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

추가 정보: [테넌트에서 포털 작성 사용 안 함](create-portal.md#disable-portal-creation-in-a-tenant)
