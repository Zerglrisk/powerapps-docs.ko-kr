---
title: PowerApps 포털 수명 주기 정보 | MicrosoftDocs
description: PowerApps 포털 수명 주기에 대 한 정보를 읽고 평가판에서 프로덕션으로 변환 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c2ee82be5526cce41451c8a703971c0f97d32ea0
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977315"
---
# <a name="about-portal-lifecycle"></a>포털 수명 주기 정보

포털은 항상 시험로 생성 됩니다. 30 일 후에 만료 되는 평가판 포털은 무료로 기능을 사용해 보려는 경우 유용 합니다. 만료 후에는 포털이 일시 중단 되 고 종료 됩니다. 일시 중단 후 7 일이 지나면 평가판 포털이 삭제 됩니다. 일시 중단, 일시 중단 됨, 삭제 됨 및 평가판에서 프로덕션으로 전환 되는 것과 같이 포털 수명 주기 단계를 변경할 때마다 알림 및 전자 메일을 통해 알림을 받게 됩니다.

관리자는 평가판 또는 일시 중단 된 포털을 프로덕션 포털로 변환할 수 있습니다. 평가판 포털을 프로덕션 환경으로 변환 하는 동안 환경을 프로덕션 환경으로 변환 해야 합니다. 평가판 환경에서는 평가판 포털을 프로덕션 환경으로 변환할 수 없습니다. 평가판 포털이 생성 된 환경을 삭제 하면 포털도 삭제 됩니다.

첫 번째 포털은 테 넌 트의 환경에서 무료로 만들 수 있습니다. 둘 이상의 포털을 만들어야 하는 경우 테 넌 트에서 사용 하지 않는 저장소 공간이 1gb 있어야 합니다.

## <a name="stages-in-portal-lifecycle"></a>포털 수명 주기의 단계

### <a name="trial-portal"></a>평가판 포털

포털은 항상 평가판 포털로 생성 됩니다. 필요한 라이선스가 있는 경우 PowerApps 포털 관리 센터에서 프로덕션으로 변환할 수 있습니다. 평가판 포털을 프로덕션으로 변환 하는 방법에 대 한 자세한 내용은 [평가판 포털을 프로덕션으로 변환](#convert-a-trial-portal-to-production)을 참조 하세요.

평가판 포털을 프로덕션으로 변환 하려면 환경에 외부 사용자를 위한 추가 기능이 필요 하거나 내부 사용자에 대 한 라이선스가 있어야 합니다. 라이선스에 대 한 자세한 내용은 [powerapps 및 Microsoft Flow 라이선스 faq](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq) 및 [powerapps 포털 라이선스](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing)를 참조 하세요.

### <a name="suspended-portal"></a>일시 중단 된 포털

평가판 포털의 만료에 대해 PowerApps 포털 관리 센터에서 알림이 계속 표시 됩니다. 평가판 포털은 30 일 후에 만료 됩니다. 평가 기간 내에 포털을 프로덕션으로 변환 하지 않으면 포털이 종료 되 고 일시 중단 상태에 배치 됩니다. 만료 된 후에는 포털에 액세스할 수 없습니다.

그러나 일시 중단 된 포털은 일시 중단 후 7 일 이내에 프로덕션으로 변환 될 수 있습니다. 

### <a name="deleted-portal"></a>삭제 된 포털

7 일 일시 중단 기간 내에 포털을 프로덕션으로 변환 하지 않으면 포털이 삭제 됩니다. 포털 데이터는 환경에서 삭제 되지 않지만, 환경에서 포털에 사용 되는 공간이 출시 되며 새 포털을 만들 수 있습니다.

## <a name="convert-a-trial-portal-to-production"></a>평가판 포털을 프로덕션으로 변환

PowerApps 포털 관리 센터에 표시 된 알림에서 평가판 포털을 프로덕션으로 변환할 수 있습니다.

> [!NOTE]
> 평가판 포털을 프로덕션으로 변환 하려면 다음 역할 중 하나를 할당 해야 합니다.
> - 전역 관리자
> - 시스템 관리자

[PowerApps 포털 관리 센터](admin-overview.md) 를 열고 [포털 세부 정보](portal-details.md) 탭으로 이동 하면 **유형** 필드 아래에 평가판 만료에 대 한 알림이 표시 됩니다.

> [!div class=mx-imgBorder]
> 포털(../media/admin-center-convert-notif.png "세부 정보 탭") 의 평가판 알림 탭의 ![평가판]알림

관리 센터의 다른 페이지에서 알림은 페이지 맨 위에 표시 됩니다.

> [!div class=mx-imgBorder]
> 다른 탭(../media/admin-center-convert-notif-all.png "의") 평가판 알림 다른 탭에 ![대 한 평가판 알림]

평가판 포털을 프로덕션으로 변환 하려면 다음을 수행 합니다.

1.  알림에서 **변환**을 선택 합니다.

2.  **확인**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![평가판에서]프로덕션(../media/trial-to-prod-confirm.png "으로") 평가판 확인
