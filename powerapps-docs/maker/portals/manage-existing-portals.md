---
title: PowerApps에서 기존 포털 관리 | Microsoft Docs
description: PowerApps에서 포털을 관리 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f21671368bfdaf9623a294c86b113b6b62f028e7
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976441"
---
# <a name="manage-existing-portals-in-powerapps"></a>PowerApps에서 기존 포털 관리

포털을 만든 후에는 PowerApps 홈 페이지의 **최근 앱** 섹션에 표시 됩니다.

> [!div class=mx-imgBorder]
> ![최근 앱](media/recent-apps.png "최근 앱")  

앱을 관리 하려면 포털에 대 한 **추가 명령** ( **...** )을 선택 하 고 상황에 맞는 메뉴에서 작업을 선택 합니다.

> [!div class=mx-imgBorder]
> ![포털 앱 옵션](media/portal-app-options.png "포털 앱 옵션")  

## <a name="edit"></a>편집할

[PowerApps 포털 Studio](portal-designer-anatomy.md) 를 열어 포털의 콘텐츠 및 구성 요소를 편집 합니다.  

> [!div class=mx-imgBorder]
> ![포털 작성자](media/portal-maker.png "포털 작성자")  

## <a name="browse"></a>찾아

포털을 열어 웹 사이트를 검색 합니다. 이를 통해 고객에 게 표시 되는 포털을 볼 수 있습니다.

> [!div class=mx-imgBorder]
> ![포털 웹 사이트](media/portal-website.png "포털 웹 사이트")  

또는 [PowerApps 포털 스튜디오](portal-designer-anatomy.md) 에서 웹 사이트 **찾아보기** 를 선택 하 여 웹 사이트에 대 한 변경 내용을 확인 하는 방식으로 포털을 열어 웹 사이트를 탐색할 수도 있습니다. 웹 사이트의 URL이 포함 된 새 탭에서 웹 사이트가 열립니다.

## <a name="share"></a>공유

내부 또는 외부 사용자와 포털을 공유 합니다. **이 포털 공유** 창에 설명 된 단계를 수행 합니다.

> [!div class=mx-imgBorder]
> ![포털](media/share-portal.png "공유 포털") 공유  

### <a name="share-with-internal-users"></a>내부 사용자와 공유

내부 사용자와 포털을 공유 하려면 먼저 보안 역할을 만든 다음 사용자가 포털을 사용할 수 있도록 보안 역할에 사용자를 할당 해야 합니다.

> [!NOTE]
> Common Data Service 사용자는 포털 엔터티에 대 한 적절 한 권한이 없는 경우 "이 환경에서 솔루션을 볼 수 있는 액세스 권한이 없습니다."와 같은 오류가 표시 될 수 있습니다. 또는 "이 환경에서 웹 사이트를 볼 수 있는 액세스 권한이 없습니다." 해당 Common Data Service 데이터베이스에서 시스템 관리자 보안 역할을 하는 것이 좋습니다.

#### <a name="step-1-create-a-security-role"></a>1 단계: 보안 역할 만들기

1.  **이 포털 공유** 창의 **보안 역할 만들기**에서 **보안 역할**을 선택 합니다. 구성 된 모든 보안 역할의 목록이 표시 됩니다.

2.  작업 도구 모음에서 **새로 만들기**를 선택 합니다.

3.  **새 보안 역할** 창에서 역할 이름을 입력 합니다.

4.  포털에서 사용 되는 모든 엔터티에 대 한 권한을 설정 합니다.

5.  보안 역할 구성이 완료 되 면 도구 모음에서 **저장 후 닫기**를 선택 합니다.

보안 역할 및 권한에 대 한 자세한 내용은 [보안 역할 및 권한](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges)을 참조 하세요.  

#### <a name="step-2-assign-users-to-the-security-role"></a>2 단계: 보안 역할에 사용자 할당

1.  **이 포털 공유** 창의 **보안 역할에 사용자 할당**에서 **사용자**를 선택 합니다. 모든 사용자의 목록이 표시 됩니다.

2.  보안 역할을 할당 하려는 사용자를 선택 합니다.

3.  **역할 관리**를 선택합니다.

    > [!NOTE]
    > 명령 모음에서 **역할 관리** 단추를 볼 수 없는 경우 URL에서 forceuci를 0으로 설정 하 여 클라이언트를 변경 해야 합니다. 예를 들어 https://&lt;org\_url&gt;/main.aspx? pagetype = entitylist & etn = systemuser & forceUCI = 0

4.  **사용자 역할 관리** 대화 상자에서 이전에 만든 보안 역할을 선택한 다음 **확인**을 선택 합니다.

### <a name="share-with-external-users"></a>외부 사용자와 공유

포털은 익명으로 작동 하며 외부 사용자가 액세스할 수 있어야 합니다. 외부 사용자에 대 한 역할 및 사용 권한을 관리 하는 고급 기능을 사용 하려는 경우 [포털에서 사용할 연락처 구성](https://docs.microsoft.com/dynamics365/customer-engagement/portals/configure-contacts), 포털에 [연락처 초대](https://docs.microsoft.com/dynamics365/customer-engagement/portals/invite-contacts), [포털에 대 한 웹 역할 만들기](https://docs.microsoft.com/dynamics365/customer-engagement/portals/create-web-roles), [엔터티 권한 할당을 참조 하세요. ](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions).  

## <a name="settings"></a>설정

포털 설정을 표시 하 고 포털의 이름을 변경할 수 있습니다. PowerApps 포털 관리 센터에서 포털 관리 및 사이트 설정 작업을 수행 하는 등의 고급 작업을 수행할 수도 있습니다. 설정은 PowerApps 포털 관리 센터 및 사이트 설정에 대 한 링크를 제공 합니다. 추가 정보: [고급 포털 관리](admin/admin-overview.md) 및 [사이트 설정 구성](configure/configure-site-settings.md)  

> [!div class=mx-imgBorder]
> ![포털 설정](media/portal-settings.png "포털 설정")  

## <a name="delete"></a>삭제

포털 및 호스트 된 리소스를 삭제 합니다. 포털을 삭제 하면 해당 URL에 액세스할 수 없게 됩니다. 포털을 삭제 해도 사용자 환경에 있는 포털 구성 또는 솔루션에는 영향을 주지 않으며 그대로 유지 됩니다.
사용자 환경에서 포털 구성을 완전히 제거 하려면 포털 구성을 수동으로 삭제 해야 합니다. 이렇게 하려면 포털 관리 앱을 사용 하 고 포털에 대 한 해당 웹 사이트 레코드를 삭제 합니다.

> [!NOTE]
> 포털을 삭제할 수 있는 권한이 없는 경우 오류가 표시 됩니다. 포털을 삭제 하려면 시스템 관리자 역할이 있어야 합니다. 또한 Azure Active Directory에서 포털 응용 프로그램의 소유자 여야 합니다. 포털을 만드는 사용자는 기본적으로 소유자 이며 포털을 삭제할 수 있습니다. 자신을 소유자로 추가 하는 방법에 대 한 자세한 내용은 [AZURE AD 응용 프로그램의 소유자로 자신 추가](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application)를 참조 하세요.

## <a name="details"></a>대해

포털의 소유자, 만들고 마지막으로 수정한 날짜 및 시간, 포털의 URL 등의 세부 정보를 표시 합니다.

> [!div class=mx-imgBorder]
> ![포털 정보](media/portal-details.png "포털 세부 정보")  

