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
ms.openlocfilehash: c1107fd96070e62ffc8df53ad756dea01da7c5f7
ms.sourcegitcommit: db2d38f0351fd41f74fa44f7a1d80703a6b38527
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66723989"
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

    ![사용자 및 공동 소유자를 지정 합니다.](./media/share-app/share-everyone.png)

    > [!NOTE]
    > 조직 외부의 사용자 또는 그룹이나 조직의 배포 그룹과는 앱을 공유할 수 없습니다.

1. 앱을 편집하고 사용하고, 공유할 수 있는(실행 포함) 사용자를 허용하려는 경우,**공동 소유자** 확인란을 선택합니다.

    [솔루션 내에서 앱을 만든](add-app-solution.md) 경우 보안 그룹에 **공동 소유자** 권한을 부여할 수 없습니다 .

    > [!NOTE]
    > 권한에 관계 없이 두 사람이 동시에 앱을 편집할 수 없습니다. 한 사용자가 편집을 위해 앱을 열면, 다른 사용자는 실행할 수 있지만 편집할 수는 없습니다.

1. 앱이 사용자 액세스 권한을 필요로 하는 데이터에 연결하는 경우, 권한을 지정합니다.

    예를 들어, 앱은 Common Data Service 데이터베이스의 엔터티에 연결할 수 있습니다. 이러한 앱을 공유하는 경우, 공유 패널은 해당 엔터티에 대한 보안을 관리하라는 메시지를 표시합니다.

    > [!div class="mx-imgBorder"]
    > ![보안 역할 할당](media/share-app/cds-assign-security-role.png)

    엔터티에 대한 보안을 관리하는 방법에 대한 자세한 내용은 뒷부분의 [엔터티 권한 관리](share-app.md#manage-entity-permissions)를 참조하세요.

1. 사람들이 앱을 찾을 수 있도록 하려는 경우는 **새 사용자에게 메일 초대 보내기** 확인란을 선택합니다.

1. 공유 패널의 맨 아래에서 **공유**를 선택합니다.

    앱을 공유받은 모든 사용자는 모바일 장치의 PowerApps Mobile 또는 브라우저의 [Dynamics 365](https://home.dynamics.com) AppSource에서 실행할수 있습니다. 공동 소유자는 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 앱을 편집하고 공유할 수 있습니다.

    초대 메일을 보낸 경우, 앱을 공유받은 모든 사용자는 초대에서 링크를 선택하여 앱을 실행할 수 있습니다.

    - 사용자가 모바일 장치에서 링크를 선택 하는 경우 앱이 PowerApps Mobile에서 열립니다.
    - 사용자가 데스크톱 컴퓨터에서 링크를 선택 하는 경우 앱이 브라우저에서 열립니다.

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
> 이 문서의 작성 시점 현재 Office 그룹 아니라 개별 사용자와 Azure Active Directory 보안 그룹에 보안 역할을 할당할 수 있습니다.

#### <a name="prerequisite"></a>필수 조건

역할에 할당 하려면 있어야 **시스템 관리자에 게** Common Data Service 데이터베이스에 대 한 권한.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>역할에 Azure AD에서 보안 그룹에 할당

1. 공유 패널에서 선택 **보안 역할 할당** 아래에서 **데이터 권한을**합니다.

1. 앱을 공유 하려는 Azure AD에서 사용자 또는 보안 그룹에 할당 하려는 Common Data Service에서 역할을 선택 합니다.

    ![보안 역할 목록](media/share-app/cds-assign-security-role-list.png)

### <a name="common-data-service-previous-version"></a>Common Data Service(이전 버전)

이전 버전의 Common Data Service를 기반으로 하는 앱을 공유 하는 경우 서비스에 대한 런타임 권한을 별도로 공유 해야 있습니다. 이 작업을 수행할 수 있는 권한이 없으면 환경 관리자를 참조 하세요.
