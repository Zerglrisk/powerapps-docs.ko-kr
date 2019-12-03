---
title: 캔버스 앱 공유 | Microsoft Docs
description: 다른 사용자에게 캔버스 앱을 실행하거나 수정할 수 있는 권한을 부여하여 앱 공유
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/09/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b04c1d9ecc4c2955b68f1ffeae1a5a56e74ab710
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733111"
---
# <a name="share-a-canvas-app-in-power-apps"></a>Power Apps에서 캔버스 앱 공유

비즈니스 요구를 해결하는 캔버스 앱을 빌드한 후에 조직의 어떤 사용자가 앱을 실행하고 수정하며 심지어 다시 공유할 수 있는지 지정합니다. 이름으로 각 사용자를 지정하거나, Azure Active Directory의 보안 그룹을 지정합니다. 모든 사용자가 앱의 이점을 누리는 경우 조직 전체가 실행할 수 있도록 지정합니다.

> [!IMPORTANT]
> 공유 앱이 원하는 대로 작동 하려면 [Common Data Service](#common-data-service) 또는 [Excel](share-app-data.md)과 같이 앱의 기반이 되는 데이터 원본 또는 원본에 대 한 권한도 관리 해야 합니다. 또한, 앱이 종속된 [기타 리소스](share-app-resources.md)(예: 흐름, 게이트웨이 또는 연결)도 공유해야 합니다.

## <a name="prerequisites"></a>필수 조건

앱을 공유하려면 로컬이 아닌 클라우드에 저장한 다음, 앱을 게시해야 합니다.

- 사용자가 앱의 기능에 대해 알고 목록에서 쉽게 찾을 수 있도록 앱에 의미 있는 이름을 지정하고 명료한 설명을 제공합니다. Power Apps 스튜디오의 **파일** 메뉴에서 **앱 설정**을 선택 하 고 이름을 지정한 다음 설명을 입력 하거나 붙여 넣습니다.

- 변경 사항을 적용할 때마다 다른 사용자가 해당 변경 사항을 보길 원한다면 저장하고 앱을 다시 게시합니다.

## <a name="share-an-app"></a>앱 공유

1. 파워 앱에 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음, 왼쪽 가장자리 근처의 **앱** 을 선택 합니다.

    ![앱 목록 표시](./media/share-app/file-apps.png)

1. 해당 아이콘을 선택 하 여 공유 하려는 앱을 선택 합니다.

    ![앱 선택](./media/share-app/select-app.png)

1. 배너에서 **공유**를 선택 합니다.

    ![공유 화면 열기](./media/share-app/banner-share.png)

1. 앱을 공유 하려는 Azure Active Directory의 사용자 또는 보안 그룹을 이름 또는 별칭으로 지정 합니다.

    - 전체 조직에서 앱을 실행 (수정 하거나 공유 하지 않음) 할 수 있도록 하려면 공유 패널에 **Everyone** 을 입력 합니다.
    - 항목이 세미콜론으로 구분 되는 경우 별칭의 목록, 이름 또는 이러한 항목의 조합 (예: **Jane Doe &lt;jane.doe@contoso.com** )을 사용 하 여 앱을 공유할 수 있습니다. 두 명 이상의 사용자에 게 이름이 같지만 별칭이 다른 경우 처음 찾은 사용자가 목록에 추가 됩니다. 이름 또는 별칭에 이미 권한이 있거나 확인할 수 없는 경우 도구 설명이 나타납니다. 

    ![사용자 및 공동 소유자 지정](./media/share-app/share-everyone.png)

    > [!NOTE]
    > 조직의 메일 그룹이 나 조직 외부의 그룹에는 앱을 공유할 수 없습니다.

1. 앱을 공유 하는 앱을 공유 하는 사용자가 앱을 공유 하는 것을 허용 하려는 경우 **공동 소유자** 확인란을 선택 합니다.

    [솔루션 내에서 앱을 만든](add-app-solution.md)경우에는 보안 그룹에 대 한 **공동 소유자** 권한을 부여할 수 없습니다.

    > [!NOTE]
    > 사용 권한에 관계 없이 두 사람이 동시에 앱을 편집할 수 없습니다. 한 사람이 편집을 위해 앱을 여는 경우 다른 사용자가 앱을 실행할 수 있지만 편집할 수는 없습니다.

1. 앱이 사용자가 액세스 권한을 필요로 하는 데이터에 연결 하는 경우 해당 데이터를 지정 합니다.

    예를 들어 앱이 Common Data Service 데이터베이스의 엔터티에 연결할 수 있습니다. 이러한 앱을 공유 하는 경우 공유 패널에 해당 엔터티에 대 한 보안을 관리 하 라는 메시지가 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 보안 역할을 할당 ![](media/share-app/cds-assign-security-role.png)

    엔터티에 대 한 보안을 관리 하는 방법에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [엔터티 권한 관리](share-app.md#manage-entity-permissions) 를 참조 하세요.

1. 사용자가 앱을 찾는 데 도움이 되도록 하려면 **새 사용자에 게 전자 메일 초대 보내기** 확인란을 선택 합니다.

1. 공유 패널의 아래쪽에서 **공유**를 선택 합니다.

    앱을 공유 하는 모든 사용자는 모바일 장치의 Power Apps Mobile에서 또는 브라우저의 [Dynamics 365](https://home.dynamics.com) 에 대 한 appsource에서 앱을 실행할 수 있습니다. 공동 소유자는 [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 앱을 편집 하 고 공유할 수 있습니다.

    전자 메일 초대를 보낸 경우 앱을 공유한 모든 사람이 초대의 링크를 선택 하 여 실행할 수 있습니다.

    - 사용자가 모바일 장치에서 링크를 선택 하면 앱이 Power Apps Mobile에서 열립니다.
    - 사용자가 데스크톱 컴퓨터에서 링크를 선택 하면 앱이 브라우저에서 열립니다.

    초대를 받는 공동 소유자는 Power Apps 스튜디오에서 편집 하기 위해 앱을 여는 다른 링크를 받습니다.

사용자 또는 보안 그룹의 이름을 선택 하 고 다음 단계 중 하나를 수행 하 여 사용자 또는 보안 그룹에 대 한 권한을 변경할 수 있습니다.

- 공동 소유자가 앱을 실행할 수 있지만 더 이상 편집 하거나 공유 하지 않으려면 **공동 소유자** 확인란의 선택을 취소 합니다.
- 해당 사용자 또는 그룹과 앱 공유를 중지 하려면 제거 (x) 아이콘을 선택 합니다.

## <a name="security-group-considerations"></a>보안 그룹 고려 사항

- 보안 그룹과 앱을 공유한 경우 그룹의 기존 회원 및 가입하는 모든 회원이 해당 그룹에 지정된 사용 권한을 받습니다. 그룹을 떠난 사람은 액세스 권한이 있는 다른 그룹에 속하거나, 개인으로 사용 권한이 부여되지 않는 한 해당 사용 권한을 잃게 됩니다.

- 보안 그룹의 모든 구성원은 앱에 대해 전체 그룹과 동일한 권한을 갖습니다. 하지만 해당 그룹의 한 명 또는 그 이상의 회원에게 더 많은 사용 권한을 지정하여 더 많은 액세스를 허용할 수 있습니다. 예를 들어 보안 그룹에 앱을 실행할 수 있는 권한을 부여할 수 있지만, 해당 그룹에 속한 사용자 B, **공동 소유자** 권한을 제공할 수도 있습니다. 보안 그룹의 모든 구성원은 앱을 실행할 수 있지만 사용자 B만 편집할 수 있습니다. 앱을 실행할 수 있는 보안 그룹에 **공동 소유자** 권한 및 사용자 B 권한을 부여 하는 경우 해당 사용자는 여전히 앱을 편집할 수 있습니다.

## <a name="manage-entity-permissions"></a>엔터티 사용 권한 관리

### <a name="common-data-service"></a>Common Data Service

Common Data Service 기반으로 앱을 만드는 경우 앱을 공유 하는 사용자에 게 앱이 사용 하는 엔터티 또는 엔터티에 대 한 적절 한 권한이 있는지 확인 해야 합니다. 특히 해당 사용자는 관련 레코드 만들기, 읽기, 쓰기 및 삭제와 같은 태스크를 수행할 수 있는 보안 역할에 속해야 합니다. 대부분의 경우 사용자가 앱을 실행 하는 데 필요한 정확한 권한을 사용 하 여 사용자 지정 보안 역할을 하나 이상 만들 수 있습니다. 그러면 각 사용자에 게 적절 하 게 역할을 할당할 수 있습니다.

> [!NOTE]
> 이 문서를 작성할 당시에는 Azure Active Directory에서 개별 사용자와 보안 그룹에 보안 역할을 할당할 수 있지만 Office 그룹에는 할당할 수 없습니다.

#### <a name="prerequisite"></a>필수 조건

역할을 할당 하려면 Common Data Service 데이터베이스에 대 한 **시스템 관리자** 권한이 있어야 합니다.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Azure AD의 보안 그룹을 역할에 할당

1. 공유 패널의 **데이터 권한**에서 **보안 역할 할당** 을 선택 합니다.

1. 앱을 공유 하려는 Azure AD의 보안 그룹 또는 사용자에 게 할당할 Common Data Service에서 역할을 하나 이상 선택 합니다.
     > [!div class="mx-imgBorder"] 
     > ![보안 역할 목록](media/share-app/cds-assign-security-role-list.png "보안 역할 목록")

### <a name="common-data-service-previous-version"></a>Common Data Service(이전 버전)

이전 버전의 Common Data Service 기반으로 하는 앱을 공유 하는 경우 서비스에 대 한 런타임 권한을 별도로 공유 해야 합니다. 이 작업을 수행할 수 있는 권한이 없으면 환경 관리자에 게 문의 하세요.

## <a name="share-with-guests"></a>게스트와 공유
 
Power Apps canvas 앱은 Azure Active Directory 테 넌 트의 게스트 사용자와 공유할 수 있습니다. 이를 통해 외부 비즈니스 파트너, 계약자 및 제 3 자가 회사의 캔버스 앱을 실행할 수 있습니다. 

> [!NOTE]
> 게스트에는 공유 된 앱에 대 한 **공동 소유자** 역할이 아닌 **사용자** 역할만 할당 될 수 있습니다.

### <a name="prerequisites"></a>필수 조건
- Azure Active Directory (Azure AD)에서 테 넌 트에 대해 B2B 외부 공동 작업을 사용 하도록 설정 합니다. 추가 정보: [B2B 외부 공동 작업을 사용 하도록 설정 하 고 게스트를 초대할 수 있는 사람 관리](/azure/active-directory/b2b/delegate-invitations)
    - B2B 외부 공동 작업은 기본적으로 설정 되어 있습니다. 그러나 테 넌 트 관리자는 설정을 변경할 수 있습니다.  Azure AD B2B에 대 한 자세한 내용은 [AZURE AD b2b의 게스트 사용자 액세스 란?](/azure/active-directory/b2b/what-is-b2b) 을 참조 하세요.  
- Azure AD 테 넌 트에 게스트 사용자를 추가할 수 있는 계정에 대 한 액세스. 관리자 및 게스트 초대자 역할을 가진 사용자는 테 넌 트에 게스트를 추가할 수 있습니다.   
- 게스트 사용자에 게는 다음 테 넌 트 중 하나를 통해 할당 된 앱의 기능과 일치 하는 Power Apps 사용 권한이 있는 라이선스가 있어야 합니다.
    - 공유 되는 앱을 호스트 하는 테 넌 트입니다.
    - 게스트 사용자의 홈 테 넌 트입니다.

### <a name="steps-to-grant-guest-access"></a>게스트 액세스 권한을 부여 하는 단계
1. **새 게스트 사용자** 를 선택 하 여 Azure AD에서 게스트 사용자를 추가 합니다. 추가 정보: [빠른 시작: AZURE AD에 새 게스트 사용자 추가](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal)
    > [!div class="mx-imgBorder"] 
    > ![Azure AD에서 게스트 추가](media/share-app/guest_access_doc_1.png "Azure AD에서 게스트 추가")
2. 게스트 사용자의 홈 테 넌 트에 라이선스가 아직 없는 경우 게스트 사용자에 게 라이선스를 할당 합니다.
   - Admin.microsoft.com에서 게스트 사용자를 할당 하려면 [한 사용자에 게 라이선스 할당](/office365/admin/subscriptions-and-billing/assign-licenses-to-users)을 참조 하세요.
   - Portal.azure.com에서 게스트 사용자를 할당 하려면 [라이선스 할당 또는 제거](/azure/active-directory/fundamentals/license-users-groups)를 참조 하세요.
 
   > [!IMPORTANT]
   > 게스트에 라이선스를 할당 하려면 Microsoft 365 관리 센터 미리 보기를 사용 하지 않도록 설정 해야 할 수 있습니다. 

3. Canvas 앱을 공유 합니다. 
    1. https://make.powerapps.com 에 로그인  
    2. **앱**으로 이동 하 여 캔버스 앱을 선택한 다음 명령 모음에서 **공유**를 선택 합니다. 
    3. Azure AD 테 넌 트에서 게스트 사용자에 대 한 전자 메일 주소를 입력 합니다. 추가 정보: [AZURE AD B2B에서 게스트 사용자 액세스 란 무엇 인가요?](/azure/active-directory/b2b/what-is-b2b)
          > [!div class="mx-imgBorder"] 
          > ![게스트와 공유](media/share-app/guest_access_doc_2.png "게스트와 공유")
 
게스트 액세스를 위해 앱을 공유한 후 게스트가 공유의 일부로 전송 된 전자 메일에서 공유 하는 앱을 검색 하 고 액세스할 수 있습니다.

> [!div class="mx-imgBorder"]  
> ![게스트가 앱 공유 전자 메일을 받습니다.](media/share-app/guest_access_doc_4.png "게스트가 앱 공유 전자 메일을 받습니다.")

### <a name="frequently-asked-questions"></a>질문과 대답

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-power-apps-portals"></a>Canvas 앱 게스트 액세스와 Power Apps 포털의 차이점은 무엇 인가요? 
Canvas apps를 사용 하면와 C#같은 기존 프로그래밍 언어로 코드를 작성 하지 않고도 비즈니스 프로세스를 디지타이징에 맞게 구성 하 여 앱을 빌드할 수 있습니다. Canvas 앱에 대 한 게스트 액세스를 사용 하면 다양 한 Microsoft 및 타사 소스와 통합 될 수 있는 동일한 앱 리소스에 액세스 하는 공통 비즈니스 프로세스에 참여 하는 다양 한 조직으로 구성 된 개인 팀이 가능 합니다. 추가 정보: [Power Apps의 캔버스-앱 커넥터 개요](/powerapps/maker/canvas-apps/connections-list)

[Power Apps 포털](/powerapps/maker/portals/overview) 외부 사용자가 Common Data Service 저장 된 데이터와 상호 작용할 수 있도록 하는 낮은 코드의 응답성이 뛰어난 웹 사이트를 빌드하는 기능을 제공 합니다. 조직에서 조직 외부 사용자와 공유 하는 웹 사이트 (예: LinkedIn, Microsoft 계정 또는 기타 상업적 로그인 공급자)를 사용 하 여 익명으로 또는 선택한 로그인 공급자를 통해 공유할 수 있는 웹 사이트를 만들 수 있습니다. 

다음 표에서는 Power Apps 포털과 canvas 앱 간의 몇 가지 핵심 기능 차이점을 간략하게 설명 합니다.  

| | 인터페이스 | 인증은 | 액세스 가능한 데이터 원본 |
|------|--------|----------|-------------------|
| Power Apps 포털 | 브라우저 전용 환경 | 익명 및 인증 된 액세스 허용 | Common Data Service |
| 캔버스 앱 | 브라우저 및 모바일 앱 | Azure AD를 통한 인증 필요 | 모든 ~ 150 기본 커넥터 및 사용자 지정 커넥터  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>게스트가 SharePoint에서 사용자 지정 된 양식에 액세스할 수 있나요?
예로. 사용자 지정 된 양식으로 SharePoint 목록에 액세스할 수 있는 모든 사용자는 Power Apps 라이선스 없이 양식을 사용 하 여 목록에서 항목을 만들고 편집할 수 있습니다.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>게스트가 SharePoint에 포함 된 앱에 액세스할 수 있나요? 
예로. 그러나 캔버스 독립 실행형 앱에 대 한 액세스에는 포함 된 앱을 포함 하 여 앱의 기능과 일치 하는 Power Apps 사용 권한이 있는 라이선스가 필요 합니다. Microsoft Power Apps embed 컨트롤을 통해 SharePoint에 캔버스 앱을 포함 하는 경우 앱 id를 입력 합니다. 이렇게 하려면 **앱 웹 링크 또는 ID** 상자에 앱 id를 입력 합니다. 

> [!div class="mx-imgBorder"]  
> ![게스트에 대 한 SharePoint에 캔버스 앱 포함](media/share-app/guest_access_doc_5.PNG "게스트에 대 한 SharePoint에 캔버스 앱 포함")

IFrame HTML 태그를 통해 SharePoint에 캔버스 앱을 포함 하는 경우 전체 웹 URL을 사용 하 여 앱을 참조 합니다. URL을 찾으려면 https://make.powerapps.com 로 이동 하 고, 앱을 선택 하 고, **세부 정보** 탭을 선택 하 고, **웹 링크**아래에 url을 표시 합니다.

> [!div class="mx-imgBorder"]  
> ![Canvas 앱 세부 정보](media/share-app/guest_access_doc_6.PNG "Canvas 앱 세부 정보")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>게스트가 공유 된 앱을 시작할 수 있는 방법 및 연결을 만들지 못함
비 게스트와 마찬가지로, 앱에서 액세스 하는 기본 데이터 원본도 게스트에서 액세스할 수 있도록 설정 해야 합니다.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>사용자가 공유 하는 앱을 실행할 수 있도록 게스트에 할당 해야 하는 라이선스는 무엇입니까?
비 게스트에 앱을 실행 하는 데 필요한 것과 동일한 라이선스. 예를 들어 앱에서 premium connecters를 사용 하는 경우 앱 요금제 또는 사용자 당 Power Apps 요금제의 Power Apps를 게스트에 할당 해야 합니다.  

|                                 | SharePoint 사용자 지정 양식 | 비 프리미엄 커넥터를 사용 하는 독립 실행형 캔버스 앱 | 프리미엄 커넥터를 사용 하는 독립 실행형 캔버스 앱 | 모델 기반 앱 |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint 사용자 (PA 라이선스 없음) | x                          |                                                    |                                                |                  |
| 업무에 포함 된 Power Apps    | x                          | x                                                  |                                                |                  |
| 앱 요금제 당 Power Apps          | x                          | x                                                  | x                                              | x                |
| 사용자 요금제 당 Power Apps         | x                          | x                                                  | x                                              | x                |


#### <a name="in-power-apps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>Power Apps 모바일에서 게스트는 홈 테 넌 트에 대 한 앱을 어떻게 볼 까 요?
자신의 모바일 장치에서, 홈 테 넌 트가 아닌 Azure AD 테 넌 트에서 게시 된 캔버스 앱에 액세스 한 모든 사용자는 Power apps에서 로그 아웃 하 고 Power Apps Mobile에 다시 로그인 해야 합니다.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>게스트와 앱을 공유 하기 전에 게스트가 Azure AD 게스트 초대를 수락 해야 하나요?
아니요. 게스트가 게스트 초대를 수락 하기 전에 공유 앱을 시작 하면 앱을 시작 하는 동안 로그인 환경의 일부로 초대를 수락 하 라는 메시지가 표시 됩니다.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>에서 생성 된 게스트 사용자에 대 한 연결을 Azure AD 테 넌 트 란?
앱에 대 한 연결은 항상 앱이 연결 된 Azure AD 테 넌 트의 컨텍스트에서 만들어집니다. 예를 들어 Contoso 테 넌 트에서 앱을 만든 경우 contoso 내부 및 게스트 사용자에 대 한 연결은 Contoso 테 넌 트의 컨텍스트에서 수행 됩니다.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>게스트가 Microsoft Graph Api를 사용 하 여 Microsoft Security Graph 커넥터 또는 사용자 지정 커넥터를 통해 Microsoft Graph를 사용할 수 있나요?
아니요, Azure AD 게스트는 Microsoft Graph을 쿼리하여 해당 사용자가 게스트로 된 테 넌 트에 대 한 정보를 검색할 수 없습니다.

#### <a name="what-intune-policies-apply-to-guests-using-my-power-apps"></a>내 Power Apps를 사용 하 여 게스트에 적용 되는 InTune 정책은 무엇 인가요?
InTune은 사용자의 홈 테 넌 트에 대해서만 정책을 적용 합니다. 예를 들어 Alice@Contoso.com Vikram@Fabrikam.com와 앱을 공유 하는 경우 InTune은 실행 하는 전원 앱에 관계 없이 Virkam의 장치에 Fabrikam.com 정책을 계속 적용 합니다.

#### <a name="what-connectors-support-guest-access"></a>게스트 액세스를 지 원하는 커넥터는 무엇 인가요?
모든 종류의 Azure AD 인증을 수행 하지 않는 모든 커넥터는 게스트 액세스를 지원 합니다. 다음 표에서는 Azure AD 인증을 수행 하는 모든 커넥터 및 현재 게스트 액세스를 지 원하는 커넥터를 열거 합니다. 이러한 대부분은 일반 공급으로 업데이트 될 예정입니다.

| **커넥터**                                     | **게스트 액세스 지원**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 Appointment Scheduling                      | 아니요                                                                     |
| Adobe Creative Cloud                              | 아니요                                                                     |
| Adobe Sign                                        | 아니요                                                                     |
| Asana                                             | 아니요                                                                     |
| AtBot 관리자                                       | 아니요                                                                     |
| AtBot 논리                                       | 아니요                                                                     |
| Azure AD                                          | 예                                                                    |
| Azure Automation                                  | 예                                                                    |
| Azure 컨테이너 인스턴스                          | 예                                                                    |
| Azure Data Factory                                | 예                                                                    |
| Azure Data Lake                                   | 예                                                                    |
| Azure DevOps                                      | 아니요                                                                     |
| Azure Event Grid                                  | 아니요                                                                     |
| Azure IoT Central                                 | 예                                                                    |
| Azure Key Vault                                   | 아니요                                                                     |
| Azure Kusto                                       | 예                                                                    |
| Azure Log Analytics                               | 예                                                                    |
| Azure Resource Manager                            | 예                                                                    |
| Basecamp 2                                        | 아니요                                                                     |
| Bitbucket                                         | 아니요                                                                     |
| Bitly                                             | 아니요                                                                     |
| bttn                                              | 아니요                                                                     |
| Buffer                                            | 아니요                                                                     |
| 비즈니스 중부                                  | 아니요                                                                     |
| CandidateZip                                      | 아니요                                                                     |
| Capsule CRM                                       | 아니요                                                                     |
| 클라우드 PKI 관리                              | 아니요                                                                     |
| Cognito Forms                                     | 아니요                                                                     |
| Common Data Service                               | 아니요                                                                     |
| Common Data Service (레거시)                      | 아니요                                                                     |
| D & B 최적화 프로그램                                     | 아니요                                                                     |
| DerSIGNL4                                    | 아니요                                                                     |
| Disqus                                            | 아니요                                                                     |
| 문서 병합                                    | 아니요                                                                     |
| Dynamics 365                                      | 아니요                                                                     |
| 판매에 대 한 Dynamics 365 AI                         | 예                                                                    |
| Fin & Ops 용 Dynamics 365                        | 아니요                                                                     |
| Enadoc my workspace                                            | 아니요                                                                     |
| Eventbrite                                        | 아니요                                                                     |
| Excel Online (Business)                           | 아니요                                                                     |
| Excel Online (OneDrive)                           | 아니요                                                                     |
| 만료 알림                               | 아니요                                                                     |
| FreshBooks                                        | 아니요                                                                     |
| GoToMeeting                                       | 아니요                                                                     |
| GoToTraining                                      | 아니요                                                                     |
| GoToWebinar                                       | 아니요                                                                     |
| Harvest                                           | 아니요                                                                     |
| HTTP with Azure AD                                | 아니요                                                                     |
| Infusionsoft                                      | 아니요                                                                     |
| Inoreader                                         | 아니요                                                                     |
| Intercom                                          | 아니요                                                                     |
| JotForm                                           | 아니요                                                                     |
| kintone                                           | 아니요                                                                     |
| LinkedIn                                          | 아니요                                                                     |
| 마케팅 콘텐츠 허브                             | 아니요                                                                     |
| 중간                                            | 아니요                                                                     |
| Metatask                                          | 아니요                                                                     |
| Microsoft Forms                                   | 아니요                                                                     |
| Microsoft Forms Pro                               | 아니요                                                                     |
| Microsoft Graph 보안                          | 아니요                                                                     |
| Microsoft Kaizala                                 | 아니요                                                                     |
| Microsoft School 데이터 동기화                        | 아니요                                                                     |
| Microsoft StaffHub                                | 아니요                                                                     |
| Microsoft Teams                                   | 예                                                                    |
| Microsoft 할 일 (비즈니스)                        | 아니요                                                                     |
| Muhimbi PDF                                       | 아니요                                                                     |
| NetDocuments                                      | 아니요                                                                     |
| Office 365 그룹                                 | 예                                                                    |
| Office 365 Outlook                                | 아니요                                                                     |
| Office 365 사용자                                  | 예                                                                    |
| Office 365 비디오                                  | 아니요                                                                     |
| OneDrive                                          | 아니요                                                                     |
| 비즈니스용 OneDrive                             | 아니요                                                                     |
| OneNote(비즈니스)                                | 아니요                                                                     |
| Outlook Customer Manager                          | 아니요                                                                     |
| Outlook 작업                                     | 예                                                                    |
| Outlook.com                                       | 아니요                                                                     |
| Paylocity                                         | 아니요                                                                     |
| Planner                                           | 아니요                                                                     |
| Plumsail 양식                                    | 아니요                                                                     |
| Power BI                                          | 예                                                                    |
| Project Online                                    | 아니요                                                                     |
| ProjectWise 디자인 통합                    | 아니요                                                                     |
| Projectwise 공유                                 | 아니요                                                                     |
| SharePoint                                        | 예                                                                    |
| 지금 sign                                           | 아니요                                                                     |
| 비즈니스용 Skype Online                         | 아니요                                                                     |
| Soft1                                             | 아니요                                                                     |
| Stormboard                                        | 아니요                                                                     |
| Survey123                                         | 아니요                                                                     |
| SurveyMonkey                                      | 아니요                                                                     |
| Toodledo                                          | 아니요                                                                     |
| Typeform                                          | 아니요                                                                     |
| Vimeo                                             | 아니요                                                                     |
| Webex 팀                                       | 아니요                                                                     |
| Windows Defender ATP (Advanced Threat Protection) | 아니요                                                                     |
| 온라인 Word (비즈니스)                            | 아니요                                                                     |
