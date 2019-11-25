---
title: PowerApps 포털 관리 센터 개요 | MicrosoftDocs
description: PowerApps 포털 관리 센터에 대한 정보.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756175"
---
# <a name="powerapps-portals-admin-center"></a>PowerApps 포털 관리 센터

PowerApps 포털 관리 센터를 통해 포털에서 고급 관리 조치를 수행할 수 있습니다. 포털이 성공적으로 프로비저닝되면 관리 센터를 사용할 수 있습니다.

## <a name="open-powerapps-portals-admin-center"></a>PowerApps 포털 관리 센터 열기

1. PowerApps 홈 페이지에서 **최근 앱** 섹션으로 이동하여 포털을 찾으십시오.

    > [!div class=mx-imgBorder]
    > ![최근 앱](../media/recent-apps.png "최근 앱")  

2. **추가 명령(...)** > **설정**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![포털 설정 옵션](../media/portal-settings-option.png "포털 설정 옵션")

3. **포털 설정** 창에서 **관리**를 선택합니다.

    > [!div class=mx-imgBorder]
    > ![포털 설정 창](../media/portal-settings-admin.png "포털 설정 창")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>자신을 Azure AD 애플리케이션의 담당자로 추가

전역 관리자가 아니면서 이미 프로비된 포털을 관리하려고 하거나 이에 실패한 경우 프로비전을 다시 제출하려고 하면 포털에 연결된 Azure Active Directory(Azure AD 응용 프로그램의 담당자여야 합니다.

1. PowerApps 포털 관리 센터로 이동하여 **포털 세부 정보** 탭을 엽니다.

2. **응용 프로그램 ID** 필드에서 값을 복사합니다.

    > [!div class=mx-imgBorder]
    > ![포털 정보 탭](../media/portal-details-admin.png "포털 정보 탭")

3. 테넌트에 연결된 Azure AD로 이동합니다. [!include[](../../../includes/proc-more-information.md)] [Azure Active Directory에서 관리되지 않는 디렉터리를 관리자로 인계](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. Azure AD에서 복사한 응용 프로그램 ID를 사용하여 앱 등록을 검색합니다. **내 앱**에서 **모든 앱**으로 전환해야 할 수 있습니다.

5. 이 앱 등록의 담당자로 사용자 또는 그룹을 추가합니다. [!include[](../../../includes/proc-more-information.md)] [앱 액세스 관리](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > 이 작업은 조직의 전역 관리자 또는 이 응용 프로그램의 기존 담당자가 수행할 수 있습니다.

6. 자신을 담당자로 추가한 후 PowerApps 포털 관리 센터 페이지를 다시 엽니다.