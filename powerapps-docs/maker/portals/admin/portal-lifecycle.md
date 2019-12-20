---
title: Power Apps 포털 수명 주기 정보 | MicrosoftDocs
description: Power Apps 포털 수명 주기에 대한 정보 및 평가판에서 프로덕션으로 변환.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 60300176f0a39258bbb7030c9e30d9b2e7711990
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874657"
---
# <a name="about-portal-lifecycle"></a>포털 수명 주기 정보

포털은 항상 평가판으로 생성됩니다. 30일 후에 만료되는 평가판 포털은 무료로 기능을 시험해 볼 때 유용합니다. 만료 후 포털이 일시 중단되고 종료됩니다. 정지 후 7일이 지나면 평가판 포털이 삭제됩니다. 일시 중단 예정, 일시 중단, 삭제 및 시험판에서 프로덕션으로 전환 등 포털 수명 주기 스테이지가 변경될 때마다 알림 메시지를 토스트와 전자 메일로 받습니다.

관리자는 평가판 또는 일시 중단된 포털을 프로덕션 포털로 변환할 수 있습니다. 평가판 포털을 프로덕션으로 변환하는 동안 환경도 프로덕션 환경인지 확인하십시오. 평가판 환경에서는 평가판 포털을 프로덕션으로 변환할 수 없습니다. 평가판 포털이 생성된 환경을 삭제하면 포털도 삭제됩니다.

첫 번째 포털은 테넌트의 환경에서 자유롭게 작성할 수 있습니다. 둘 이상의 포털을 작성해야 하는 경우 테넌트에 1GB의 사용되지 않은 스토리지 공간이 있어야 합니다.

## <a name="stages-in-portal-lifecycle"></a>포털 수명 주기의 스테이지

### <a name="trial-portal"></a>평가판 포털

포털은 항상 평가판 포털로 생성됩니다. 필요한 라이선스가 있는 경우 Power Apps 포털 관리 센터에서 프로덕션으로 변환할 수 있습니다. 평가판 포털을 프로덕션으로 변환하는 방법에 대한 정보는 [시험판 포털을 프로덕션으로 변환](#convert-a-trial-portal-to-production)을 참조하십시오.

평가판 포털을 프로덕션으로 변환하려면 환경에 외부 사용자용 추가 기능 또는 내부 사용자용 라이선스가 있어야 합니다. 라이선싱에 대한 자세한 내용은 [Power Apps 및 Power Automate 라이선싱 FAQ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) 및 [Power Apps 포털 라이선싱](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing)을 참조하십시오.

### <a name="suspended-portal"></a>일시 중단된 포털

Power Apps 포털 관리 센터에 평가판 포털 만료에 대한 알림이 계속 표시됩니다. 평가판 포털은 30일 후에 만료됩니다. 평가판 기간 내에 포털을 프로덕션으로 변환하지 않으면 포털이 종료되고 일시 중단 상태가 됩니다. 만료 후에는 포털에 액세스할 수 없습니다.

그러나 일시 중단된 포털은 일시 중단 후 7일 이내에 프로덕션으로 변환할 수 있습니다. 

### <a name="deleted-portal"></a>삭제된 포털

7일 정지 기간 내에 포털을 프로덕션으로 변환하지 않으면 포털이 삭제됩니다. 포털 데이터는 환경에서 삭제되지 않지만 환경에서 포털이 사용하는 공간이 해제되고 새 포털을 작성할 수 있습니다.

## <a name="convert-a-trial-portal-to-production"></a>평가판 포털을 프로덕션으로 변환

Power Apps 포털 관리 센터에 표시된 알림에서 평가판 포털을 프로덕션으로 변환할 수 있습니다.

> [!NOTE]
> 평가판 포털을 프로덕션으로 변환하려면 다음 역할 중 하나가 지정되어야 합니다.
> - 전역 관리자
> - 시스템 관리자

[Power Apps 포털 관리 센터](admin-overview.md)를 열고 [포털 세부 정보](portal-details.md) 탭으로 이동하면 **유형** 필드 아래에 평가판 만료에 대한 알림이 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 세부 정보 탭의 평가판 알림](../media/admin-center-convert-notif.png "포털 세부 정보 탭의 평가판 알림")

관리 센터의 다른 페이지에서는 알림이 페이지 상단에 표시됩니다.

> [!div class=mx-imgBorder]
> ![다른 탭의 평가판 알림](../media/admin-center-convert-notif-all.png "다른 탭의 평가판 알림")

평가판 포털을 프로덕션으로 변환하려면:

1.  알림에서 **변환**을 선택합니다.

2.  **확인**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![평가판에서 프로덕션 확인](../media/trial-to-prod-confirm.png "평가판에서 프로덕션 확인")
