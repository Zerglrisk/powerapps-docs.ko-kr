---
title: 캔버스 앱 공유 | Microsoft Docs
description: 다른 사용자에게 캔버스 앱을 실행하거나 수정할 수 있는 권한을 부여하여 앱 공유
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/28/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b070dfad61f3e53e313d4e8891dc44507a910292
ms.sourcegitcommit: edf79033111b50aa3015b55929ce689474edba2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68917380"
---
# <a name="share-a-canvas-app-in-powerapps"></a>PowerApps에서 캔버스 앱 공유

비즈니스 요구를 해결하는 캔버스 앱을 빌드한 후에 조직의 어떤 사용자가 앱을 실행하고 수정하며 심지어 다시 공유할 수 있는지 지정합니다. 이름으로 각 사용자를 지정하거나, Azure Active Directory의 보안 그룹을 지정합니다. 모든 사용자가 앱의 이점을 누리는 경우 조직 전체가 실행할 수 있도록 지정합니다.

> [!IMPORTANT]
> 공유 앱이 예상대로 동작하게 하기 위해서는, 앱이 기준으로 하는 [Common Data Service](#common-data-service) 또는 [Excel](share-app-data.md)과 같은  데이터 원본 또는 원본에 대한 권한을 관리해야 합니다. 또한, 앱에 종속된 [기타 리소스](share-app-resources.md)(예: 흐름, 게이트웨이 또는 연결)도 공유해야 합니다.

## <a name="prerequisites"></a>필수 조건

앱을 공유하려면 로컬이 아닌 클라우드에 저장한 다음, 앱을 게시해야 합니다.

- 사용자가 앱의 기능에 대해 알고 목록에서 쉽게 찾을 수 있도록 앱에 의미 있는 이름을 지정하고 명료한 설명을 제공합니다. PowerApps Studio의 **파일** 메뉴에서 **앱 설정**을 선택하고 이름을 지정한 다음, 설명을 입력하거나 붙여넣습니다.

- 변경 사항을 적용할 때마다 다른 사용자가 해당 변경 사항을 보길 원한다면 저장하고 앱을 다시 게시합니다.

## <a name="share-an-app"></a>앱 공유

1. [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인한 다음, 왼쪽 가장자리 근처에서 **앱**을 선택합니다.

    ![앱 목록 표시](./media/share-app/file-apps.png)

1. 해당 아이콘을 선택하여 공유하려는 앱을 선택합니다.

    ![앱 선택](./media/share-app/select-app.png)

1. 배너에서 **공유**를 선택합니다.

    ![공유 화면 열기](./media/share-app/banner-share.png)

1. 앱을 공유하려는 Azure Active Directory의 사용자 또는 보안 그룹을 이름 또는 별칭으로 지정합니다.

    - 조직 전체에서 앱을 실행하는 것(하지만 수정이나 공유는 금지)을 허용하려면, 공유 패널에서 **Everyone**을 입력합니다.
    - 항목을 세미콜론으로 구분하는 경우 별칭, 친숙한 이름 또는 이들의 조합(예를 들어 **Jane Doe &lt;jane.doe@contoso.com>** )을 사용하여 앱을 공유할 수 있습니다. 둘 이상의 사람이 동일한 이름을 갖지만 별칭이 다른 경우, 처음 발견된 사용자가 목록에 추가됩니다. 해당 이름이나 별칭이 이미 권한이 있는나 확인할 수 없는 경우에는 도구 설명이 표시됩니다. 

    ![사용자 및 공동 소유자 지정](./media/share-app/share-everyone.png)

    > [!NOTE]
    > 조직 외부의 사용자 또는 그룹이나 조직의 배포 그룹과는 앱을 공유할 수 없습니다.

1. 앱을 편집하고 사용하고, 공유할 수 있는(실행 포함) 사용자를 허용하려는 경우,**공동 소유자** 확인란을 선택합니다.

    [솔루션 내에서 앱을 만든](add-app-solution.md) 경우 보안 그룹에 **공동 소유자** 권한을 부여할 수 없습니다 .

    > [!NOTE]
    > 권한에 관계 없이 두 사람이 동시에 앱을 편집할 수 없습니다. 한 사용자가 편집을 위해 앱을 열면, 다른 사용자는 실행할 수 있지만 편집할 수는 없습니다.

1. 앱이 사용자 액세스 권한을 필요로 하는 데이터에 연결하는 경우, 권한을 지정합니다.

    예를 들어 앱이 Common Data Service 데이터베이스의 엔터티에 연결할 수 있습니다. 이러한 앱을 공유하는 경우, 공유 패널은 해당 엔터티에 대한 보안을 관리하라는 메시지를 표시합니다.

    > [!div class="mx-imgBorder"]
    > ![보안 역할 할당](media/share-app/cds-assign-security-role.png)

    엔터티에 대한 보안을 관리하는 방법에 대한 자세한 내용은 뒷부분의 [엔터티 권한 관리](share-app.md#manage-entity-permissions)를 참조하세요.

1. 사람들이 앱을 찾을 수 있도록 하려는 경우는 **새 사용자에게 메일 초대 보내기** 확인란을 선택합니다.

1. 공유 패널의 맨 아래에서 **공유**를 선택합니다.

    앱을 공유받은 모든 사용자는 모바일 장치의 PowerApps Mobile 또는 브라우저의 [Dynamics 365](https://home.dynamics.com) AppSource에서 실행할수 있습니다. 공동 소유자는 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 앱을 편집하고 공유할 수 있습니다.

    초대 메일을 보낸 경우, 앱을 공유받은 모든 사용자는 초대에서 링크를 선택하여 앱을 실행할 수 있습니다.

    - 사용자가 모바일 장치에서 링크를 선택 하면 PowerApps Mobile에서 앱이 열립니다.
    - 사용자가 데스크톱 컴퓨터에서 링크를 선택 하면 앱이 브라우저에서 열립니다.

    초대 받은 공동 소유자는 PowerApps Studio 에서 편집을 위해 다른 링크로 앱을 엽니다.

해당 이름을 선택하고 다음 단계 중 하나를 수행하여 사용자 또는 보안 그룹에 대한 권한을 변경할 수 있습니다.

- 공동 소유자가 앱을 실행하지만 더 이상 편집하거나 공유하지 못하게 하려면, **공동 소유자** 확인란 선택을 취소합니다.
- 해당 사용자 또는 그룹에 앱 공유를 중지하려면 제거(x) 아이콘을 선택합니다.

## <a name="security-group-considerations"></a>보안 그룹 고려 사항

- 보안 그룹과 앱을 공유한 경우 그룹의 기존 회원 및 가입하는 모든 회원이 해당 그룹에 지정된 사용 권한을 받습니다. 그룹을 떠난 사람은 액세스 권한이 있는 다른 그룹에 속하거나, 개인으로 사용 권한이 부여되지 않는 한 해당 사용 권한을 잃게 됩니다.

- 보안 그룹의 모든 구성원은 앱에 대해 전체 그룹과 동일한 권한을 갖습니다. 하지만 해당 그룹의 한 명 또는 그 이상의 회원에게 더 많은 사용 권한을 지정하여 더 많은 액세스를 허용할 수 있습니다. 예를 들어, 보안 그룹 A에 앱을 실행하는 권한을 부여 하고, 그 그룹에 속하는 사용자 B에게 **공동 소유자** 권한을 제공할 수 있습니다. 보안 그룹의 모든 구성원은 앱을 실행할 수 있지만 사용자 B만 편집할 수 있습니다. **공동 소유자** 권한을 보안 그룹 A에 부여하고 사용자 B에게 앱 실행 권한을 부여해도, 해당 사용자는 여전히 앱을 편집할 수 있습니다.

## <a name="manage-entity-permissions"></a>엔터티 사용 권한 관리

### <a name="common-data-service"></a>Common Data Service

Common Data Service에 따라 앱을 만드는 경우 앱을 공유하는 사용자가 앱이 사용하는 엔터티에 대한 적절한 권한이 있는지 확인해야 합니다. 특히, 해당 사용자는 관련 레코드를 삭제하고 만들기, 읽기, 쓰기 등의 작업을 수행할 수 있는 보안 역할에 속해야 합니다. 많은 경우 사용자가 앱을 실행하는데 필요한 정확한 권한이 있는 하나 이상의 사용자 지정 보안 역할을 만들고자 할 것입니다. 그런 다음 적절하게 각 사용자에게 역할을 할당할 수 있습니다.

> [!NOTE]
> 이 문서를 작성할 당시에는 Azure Active Directory에서 개별 사용자와 보안 그룹에 보안 역할을 할당할 수 있지만 Office 그룹에는 할당할 수 없습니다.

#### <a name="prerequisite"></a>필수 조건

역할을 할당 하려면 Common Data Service 데이터베이스에 대 한 **시스템 관리자** 권한이 있어야 합니다.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Azure AD의 보안 그룹을 역할에 할당

1. 공유 패널의 **데이터 권한**에서 **보안 역할 할당** 을 선택 합니다.

1. 앱을 공유 하려는 Azure AD의 보안 그룹 또는 사용자에 게 할당할 Common Data Service에서 역할을 하나 이상 선택 합니다.

    ![보안 역할 목록](media/share-app/cds-assign-security-role-list.png)

### <a name="common-data-service-previous-version"></a>Common Data Service(이전 버전)

이전 버전의 Common Data Service를 기반으로 하는 앱을 공유 하는 경우 서비스에 대한 런타임 권한을 별도로 공유 해야 있습니다. 이 작업을 수행할 수 있는 권한이 없으면 환경 관리자에 게 문의 하세요.

## <a name="share-with-guests"></a>게스트와 공유

> [!IMPORTANT]
> - 미리 보기 기능은 프로덕션 용도로 사용되지 않으며 기능이 제한될 수 있습니다. 이러한 기능은 공식 릴리스 전에 사용할 수 있으므로 고객이 미리 액세스하고 피드백을 제공할 수 있습니다. 
> - 미리 보기 기능은 Microsoft 지원에 의해 제한적으로 지원 되며 선택한 지리적 영역 에서만 사용할 수 있습니다. 

PowerApps canvas 앱은 Azure Active Directory 테 넌 트의 게스트 사용자와 공유할 수 있습니다. 이를 통해 외부 비즈니스 파트너, 계약자 및 제 3 자가 회사의 캔버스 앱을 실행할 수 있습니다. 

게스트에는 공유 된 앱에 대 한 공동 소유자 역할이 아닌 사용자 역할만 할당 될 수 있습니다.

### <a name="prerequisites"></a>전제 조건
1. Azure Active Directory에서 테 넌 트에 대해 [B2B 외부 공동 작업을 사용 하도록 설정](https://docs.microsoft.com/en-us/azure/active-directory/b2b/delegate-invitations) 합니다.  
- 이는 기본적으로 설정 되어 있으므로 테 넌 트 관리자가 설정을 변경할 수 있습니다.  
- Azure AD B2B 체크 아웃에 대 한 자세한 내용은 다음을 참조 하세요. [Azure AD B2B에서 게스트 사용자 액세스 란 무엇 인가요?](https://docs.microsoft.com/en-us/azure/active-directory/b2b/what-is-b2b)  
2. AAD 테 넌 트에 게스트 사용자를 추가할 수 있는 계정에 액세스 합니다. "게스트 초대자" 역할이 있는 관리자와 사용자는 테 넌 트에 게스트를 추가할 수 있습니다.   
3. 공유 중인 앱이 연결 된 테 넌 트에서 게스트 사용자에 게 PowerApps 라이선스를 할당 해야 합니다. Canvas 앱 게스트 액세스를 일반적으로 사용 하기 전에, 해당 홈 테 넌 트에 PowerApps 라이선스가 있는 게스트는 해당 테 넌 트의 라이선스를 할당할 필요가 없습니다.

### <a name="steps"></a>단계
1. Azure Active Directory에서 게스트 사용자를 추가 합니다.  
- 이 내용은이 문서에 설명 되어 있습니다. [빠른 시작: Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal)에서 새 게스트 사용자를 추가 합니다.
![Azure AD에서 게스트 추가](media/share-app/guest_access_doc_1.png)
2. 게스트 사용자에 게 라이선스를 할당 합니다. 
- 이에 대해서는 다음 문서에서 설명 합니다. 한 [사용자에 게 라이선스를 할당](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide#assign-licenses-to-one-user) 하거나 및 https://portal.azure.com 에 대 한 https://admin.microsoft.com 사용자의 라이선스를 [할당 하거나 제거](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/license-users-groups) 합니다.  
- 게스트에 라이선스를 할당 하려면 Microsoft 365 관리 센터 미리 보기를 해제 해야 할 수도 있습니다. 
3. Canvas 앱을 공유 합니다. 
- 로그인 https://make.powerapps.com  
- 앱을 선택 하 고 공유를 클릭 합니다. 
![](media/share-app/guest_access_doc_2.png)
게스트![게스트와 공유 하는 사용자만 사용할 수 있습니다.](media/share-app/guest_access_doc_3.png)
4. 게스트는 공유의 일부로 전송 된 전자 메일에서 공유 된 앱을 검색 하 고 액세스할 수 있습니다.
![게스트가 앱 공유 전자 메일을 받습니다.](media/share-app/guest_access_doc_4.png)

### <a name="frequently-asked-questions"></a>질문과 대답

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-powerapps-portal"></a>Canvas 앱 게스트 액세스와 PowerApps 포털의 차이점은 무엇 인가요? 
Canvas apps를 사용 하면와 C#같은 기존 프로그래밍 언어로 코드를 작성 하지 않고도 비즈니스 프로세스를 디지타이징에 맞게 구성 하 여 앱을 빌드할 수 있습니다. Canvas 앱에 대 한 게스트 액세스를 사용 하면 다양 [한 Microsoft 및 타사 소스](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/connections-list)와 통합 될 수 있는 동일한 앱 리소스에 액세스 하는 공통 비즈니스 프로세스에 참여 하는 다양 한 조직으로 구성 된 개인 팀이 가능 합니다.

[PowerApps 포털](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview) 은 외부 사용자가 Common Data Service에 저장 된 데이터와 상호 작용할 수 있도록 하는 낮은 코드의 응답성이 뛰어난 웹 사이트를 빌드하는 기능을 제공 합니다. 조직에서 조직 외부 사용자와 공유 하거나 LinkedIn, Microsoft 계정, 기타 상업적 로그인 공급자와 같이 선택한 로그인 공급자를 통해 공유할 수 있는 웹 사이트를 만들 수 있습니다. 

다음 표에서는 PowerApps 포털 및 canvas 앱 간의 몇 가지 핵심 기능 차이점을 간략하게 설명 합니다.  

| | 인터페이스 | 인증 | 액세스 가능한 데이터 원본 |
|------|--------|----------|-------------------|
| PowerApps 포털 | 브라우저 전용 환경 | 익명 및 인증 된 액세스 허용 | Common Data Service |
| 캔버스 앱 | 브라우저 및 모바일 앱 | Azure AD를 통한 인증 필요 | 모든 ~ 150 기본 커넥터 및 사용자 지정 커넥터  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>게스트가 SharePoint에서 사용자 지정 된 양식에 액세스할 수 있나요?
예. 사용자 지정 된 양식을 사용 하 여 SharePoint 목록에 액세스할 수 있는 모든 사용자는 PowerApps 라이선스 없이 양식을 사용 하 여 목록에서 항목을 만들고 편집할 수 있습니다.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>게스트가 SharePoint에 포함 된 앱에 액세스할 수 있나요? 
예. 그러나 캔버스 독립 실행형 앱에 대 한 액세스에는 포함 된 앱을 포함 하는 PowerApps 라이선스가 필요 합니다. Microsoft PowerApps를 통해 SharePoint에 캔버스 앱을 포함 하는 경우 앱 id를 복사 하 여 붙여넣습니다. 

![게스트에 대 한 SharePoint에 캔버스 앱 포함](media/share-app/guest_access_doc_5.PNG)

IFrame HTML 태그를 통해 SharePoint에 캔버스 앱을 포함 하는 경우 >에서 http://make.powerapps.com 찾을 수 있는 전체 웹 링크를 사용 하 여 앱을 참조 하 고 웹 링크 > 앱 > 세부 정보를 선택 합니다.

![Canvas 앱 세부 정보](media/share-app/guest_access_doc_6.PNG)

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>게스트가 공유 된 앱을 시작할 수 있는 방법 및 연결을 만들지 못함
비 게스트와 마찬가지로, 앱에서 액세스 하는 기본 데이터 원본도 게스트에서 액세스할 수 있도록 설정 해야 합니다.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>사용자가 공유 하는 앱을 실행할 수 있도록 게스트에 할당 해야 하는 라이선스는 무엇입니까?
비 게스트에 앱을 실행 하는 데 필요한 것과 동일한 라이선스. 예를 들어 앱에서 premium connecters를 사용 하지 않는 경우 PowerApps P1 라이선스는 게스트에 할당할 수 있는 충분 합니다.  

Canvas 앱 게스트 액세스 일반 공급 이전에는 해당 홈 테 넌 트에 PowerApps 라이선스가 있는 게스트가 게스트로 할당 될 필요가 없습니다.

|                                 | SharePoint 사용자 지정 양식 | 비 프리미엄 커넥터를 사용 하는 독립 실행형 캔버스 앱 | 프리미엄 커넥터를 사용 하는 독립 실행형 캔버스 앱 | 모델 기반 앱 |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint 사용자 (PA 라이선스 없음) | x                          |                                                    |                                                |                  |
| W/Office가 포함 된 PowerApps    | x                          |                                                    |                                                |                  |
| PowerApps 요금제 1                | x                          | x                                                  |                                                |                  |
| PowerApps Plan2                 | x                          | x                                                  | x                                              | x                |

#### <a name="in-powerapps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>PowerApps Mobile에서 게스트는 홈 테 넌 트의 앱을 어떻게 볼 까 요?
자신의 모바일 장치에서, 홈 테 넌 트가 아닌 Azure AD 테 넌 트에서 게시 된 캔버스 앱에 액세스 한 모든 사용자는 PowerApps에서 로그 아웃 하 고 PowerApps Mobile에 다시 로그인 해야 합니다.  

Canvas 앱 게스트 액세스 일반 공급 이전에는 조직 선택기를 사용 하 여 사용자가 앱에서 명시적으로 로그 아웃 하지 않고도 로그인 한 Azure AD 테 넌 트를 변경할 수 있습니다.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>게스트와 앱을 공유 하기 전에 게스트가 Azure AD 게스트 초대를 수락 해야 하나요?
아니요. 게스트가 게스트 초대를 수락 하기 전에 공유 앱을 시작 하면 앱을 시작 하는 동안 로그인 환경의 일부로 초대를 수락 하 라는 메시지가 표시 됩니다.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>에서 생성 된 게스트 사용자에 대 한 연결을 Azure AD 테 넌 트 란?
앱에 대 한 연결은 항상 앱이 연결 된 Azure AD 테 넌 트의 컨텍스트에서 만들어집니다. 예를 들어 Contoso 테 넌 트에서 앱을 만든 경우 contoso 내부 및 게스트 사용자에 대 한 연결은 Contoso 테 넌 트의 컨텍스트에서 수행 됩니다.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connectorhttpsdocsmicrosoftcomen-usconnectorsmicrosoftgraphsecurity-or-a-custom-connector-using-microsoft-graph-apishttpsdevelopermicrosoftcomen-usgraph"></a>게스트가 [Microsoft Graph api](https://developer.microsoft.com/en-us/graph)를 사용 하 여 [Microsoft Security Graph 커넥터](https://docs.microsoft.com/en-us/connectors/microsoftgraphsecurity/) 또는 사용자 지정 커넥터를 통해 Microsoft Graph를 사용할 수 있나요?
아니요, Azure AD 게스트는 Microsoft Graph을 쿼리하여 해당 사용자가 게스트로 된 테 넌 트에 대 한 정보를 검색할 수 없습니다.

#### <a name="what-intune-policies-apply-to-guests-using-my-powerapps"></a>PowerApps를 사용 하 여 게스트에 적용 되는 InTune 정책은 무엇 인가요?
InTune은 사용자의 홈 테 넌 트에 대해서만 정책을 적용 합니다. 예를 들어가 Alice@Contoso.com 와 Vikram@Fabrikam.com앱을 공유 하는 경우 InTune은 실행 하는 PowerApps에 관계 없이 Fabrikam.com 정책을 계속 Virkam의 장치에 적용 합니다.

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
| 버퍼                                            | 아니요                                                                     |
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
| 보통                                            | 아니요                                                                     |
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
