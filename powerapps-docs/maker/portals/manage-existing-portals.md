---
title: PowerApps에서 기존 포털 관리 | Microsoft 문서
description: PowerApps에서 포털을 관리하기 위한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="manage-existing-portals-in-powerapps"></a>PowerApps에서 기존 포털 관리

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

포털을 만들면 PowerApps 홈 페이지의 **최근 앱** 섹션 아래에 표시됩니다.

> [!div class=mx-imgBorder]
> ![최근 앱](media/recent-apps.png "최근 앱")  

앱을 관리하려면 **추가 명령**(**…**)을 클릭하고 상황에 맞는 메뉴에서 작업을 선택하십시오.

> [!div class=mx-imgBorder]
> ![포털 앱 옵션](media/portal-app-options.png "포털 앱 옵션")  

## <a name="edit"></a>편집

[포털 디자이너](portal-designer-anatomy.md)를 열어 포털의 콘텐츠 및 구성 요소를 편집합니다.  

> [!div class=mx-imgBorder]
> ![포털 제조업체](media/portal-maker.png "포털 제조업체")  

## <a name="browse"></a>찾아보기

포털을 열어 웹 사이트를 탐색하십시오. 이를 통해 고객에게 보이는 대로 포털을 볼 수 있습니다.

> [!div class=mx-imgBorder]
> ![포털 웹 사이트](media/portal-website.png "포털 웹 사이트")  

또는, 포털을 열고 [포털 디자이너](portal-designer-anatomy.md)에서 **웹 사이트 찾아보기**를 선택하여 웹 사이트로 이동하여 웹 사이트에 대한 변경 사항을 볼 수 있습니다. 웹 사이트가 웹 사이트의 URL이 포함된 새 탭에서 열립니다.

## <a name="share"></a>공유

내부 또는 외부 사용자와 포털을 공유하십시오. **이 포털 공유** 창에 언급된 단계를 따르십시오.

> [!div class=mx-imgBorder]
> ![포털 공유](media/share-portal.png "포털 공유")  

### <a name="share-with-internal-users"></a>내부 사용자와 공유

내부 사용자와 포털을 공유하려면 먼저 보안 역할을 만든 다음 보안 역할에 포털을 사용할 수 있는 사용자를 지정해야 합니다.

> [!NOTE]
> Common Data Service의 사용자로서 포털 엔터티에 대한 적절한 권한이 없는 경우 “이 환경에서 솔루션을 보는 데 필요한 액세스 권한이 없습니다.” 또는 “이 환경에서 웹 사이트를 보는 데 필요한 액세스 권한이 없습니다.”와 같은 오류가 표시될 수 있습니다. 이 미리 보기의 경우 해당 Common Data Service 데이터베이스에서 **시스템 관리자** 또는 최소한 **시스템 사용자 지정자** 보안 역할이 있는 것이 좋습니다.

#### <a name="step-1-create-a-security-role"></a>1단계: 보안 역할 만들기

1.  **이 포털 공유** 창의 **보안 역할 만들기**에서 **보안 역할**을 선택합니다. 구성된 모든 보안 역할 목록이 표시됩니다.

2.  작업 도구 모음에서 **새로 만들기**를 선택합니다.

3.  **새 보안 역할** 창에서 역할 이름을 입력하십시오.

4.  포털에서 사용되는 모든 엔터티에 대한 권한을 설정하십시오.

5.  보안 역할 구성을 마치면 도구 모음에서 **저장 후 닫기**를 선택합니다.

보안 역할 및 권한에 대한 자세한 내용은 [보안 역할 및 권한](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/security-roles-privileges)을 참조하십시오.  

#### <a name="step-2-assign-users-to-the-security-role"></a>2단계 : 보안 역할에 사용자 할당

1.  **이 포털 공유** 창의 **보안 역할에 사용자 할당**에서 **사용자**를 선택합니다. 모든 사용자의 목록이 표시됩니다.

2.  보안 역할을 할당할 사용자를 선택합니다.

3.  **역할 관리**를 선택합니다.

    > [!NOTE]
    > 명령 모음에서 **역할 관리** 버튼을 볼 수 없는 경우 URL에서 forceUCI를 0으로 설정하여 클라이언트를 변경해야 합니다. 예: https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  **사용자 역할 관리** 대화 상자에서 이전에 만든 보안 역할을 선택한 다음 **확인**을 선택합니다.

### <a name="share-with-external-users"></a>외부 사용자와 공유

포털은 익명으로 작동해야 하며 외부 사용자가 액세스할 수 있어야 합니다. 외부 사용자의 역할 및 권한 관리를 위한 고급 기능을 사용하려면 [포털에서 사용할 연락처 구성](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-contacts), [포털에 연락처 초대](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/invite-contacts), [포털의 웹 역할 만들기](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/create-web-roles), [엔터티 권한 할당](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/assign-entity-permissions)을 참조하십시오.  

## <a name="settings"></a>설정

포털 설정을 표시하고 포털 이름을 변경할 수 있습니다. 포털 관리 센터를 통한 포털 관리 및 사이트 설정 작업과 같은 고급 조치를 수행할 수도 있습니다. 설정은 PowerApps 포털 관리 센터 및 사이트 설정에 대한 링크를 제공합니다. 추가 정보: [포털 관리](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal) 및 [포털의 사이트 설정 구성](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-site-settings).  

> [!div class=mx-imgBorder]
> ![포털 설정](media/portal-settings.png "포털 설정")  

## <a name="delete"></a>삭제

포털 및 호스팅된 리소스를 삭제합니다. 포털을 삭제하면 해당 URL에 액세스할 수 없게 됩니다. 포털을 삭제해도 환경에 존재하는 포털 구성 또는 솔루션에는 영향을 미치지 않으며 그대로 유지됩니다.
환경에서 포털 구성을 완전히 제거하려면 포털 구성을 수동으로 삭제해야 합니다. 이를 수행하려면 포털 관리 앱을 사용하고 포털의 해당 웹 사이트 레코드를 삭제하십시오.

> [!NOTE]
> 포털을 삭제할 권한이 충분하지 않으면 오류가 표시됩니다. 포털을 삭제하려면 시스템 사용자 지정자 또는 시스템 관리자 역할이 있어야 합니다. 또한 Azure Active Directory에서 포털 애플리케이션의 담당자여야 합니다. 포털을 만드는 사용자는 기본적으로 담당자이며 포털을 삭제할 수 있습니다. 자신을 담당자로 추가하는 방법에 대한 자세한 내용은 [자신을 Azure AD 애플리케이션의 담당자로 추가](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application)를 참조하십시오.

## <a name="details"></a>자세히

포털 담당자, 포털을 만들고 마지막으로 수정한 날짜 및 시간, 포털의 URL과 같은 세부 사항을 표시합니다.

> [!div class=mx-imgBorder]
> ![포털 세부 정보](media/portal-details.png "포털 세부 정보")  

