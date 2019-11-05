---
title: PowerApps 포털 관리 센터 개요 | MicrosoftDocs
description: PowerApps 포털 관리 센터에 대 한 정보입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543090"
---
# <a name="powerapps-portals-admin-center"></a>PowerApps 포털 관리 센터

PowerApps 포털 관리 센터에서 포털에 대 한 고급 관리 작업을 수행할 수 있습니다. 관리 센터는 포털을 성공적으로 프로 비전 할 때 사용할 수 있습니다.

## <a name="open-powerapps-portals-admin-center"></a>PowerApps 포털 관리 센터 열기

1. PowerApps 홈 페이지에서 **최근 앱** 섹션으로 이동 하 여 포털을 찾습니다.

    > [!div class=mx-imgBorder]
    > ![최근 앱](../media/recent-apps.png "최근 앱")  

2. **추가 명령 (...)**  > **설정을**선택 합니다.

    > [!div class=mx-imgBorder]
    > ![포털 설정 옵션](../media/portal-settings-option.png "포털 설정 옵션")

3. **포털 설정** 창에서 **관리**를 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![포털 설정 창](../media/portal-settings-admin.png "포털 설정 창")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>사용자를 Azure AD 응용 프로그램의 소유자로 추가

전역 관리자가 아닌 사용자가 이미 프로 비전 된 포털을 관리 하려고 하거나 실패 한 경우 프로 비전을 다시 제출 하는 경우 포털에 연결 된 Azure Active Directory (Azure AD) 응용 프로그램의 소유자 여야 합니다.

1. PowerApps 포털 관리 센터로 이동 하 여 **포털 세부 정보** 탭을 엽니다.

2. **응용 프로그램 ID** 필드에서 값을 복사 합니다.

    > [!div class=mx-imgBorder]
    > ![포털 세부 정보 탭](../media/portal-details-admin.png "포털 세부 정보 탭")

3. 테 넌 트와 연결 된 Azure AD로 이동 합니다. [에서 관리 되지 않는 디렉터리를 관리자 권한으로 사용 [!include[](../../../includes/proc-more-information.md)] Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. Azure AD에서 복사한 응용 프로그램 ID를 사용 하 여 앱 등록을 검색 합니다. **내 앱** 에서 **모든 앱**으로 전환 해야 할 수도 있습니다.

5. 이 앱 등록의 소유자로 사용자 또는 그룹을 추가 합니다. [앱에 대 한 액세스를 관리](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps) [!include[](../../../includes/proc-more-information.md)]

    > [!Note]
    > 조직의 전역 관리자 또는이 응용 프로그램의 기존 소유자가이 작업을 수행할 수 있습니다.

6. 자신을 소유자로 추가 했으면 PowerApps 포털 관리 센터 페이지를 다시 엽니다.