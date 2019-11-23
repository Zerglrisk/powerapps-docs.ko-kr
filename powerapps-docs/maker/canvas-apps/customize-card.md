---
title: Canvas 앱에서 카드 사용자 지정 | Microsoft Docs
description: 캔버스 앱의 세부 정보 또는 편집 양식에서 카드에 표시 되는 기본 컨트롤 변경
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985909"
---
# <a name="customize-a-card-in-a-canvas-app"></a>캔버스 앱에서 카드 사용자 지정

해당 컨트롤을 변경하는 등의 방법으로 (카드를 잠금 해제하지 않고) 기본 사용자 지정 을 수행합니다. 기본값으로 가능하지 않은 컨트롤을 추가하는 등의 방법으로 카드를 잠금 해제하여 고급 사용자 지정을 수행합니다.

개요를 보려면 [데이터 카드 이해](working-with-cards.md)를 참조하세요.

## <a name="prerequisites"></a>필수 조건

- [컨트롤을 추가하고 구성](add-configure-controls.md)하는 방법을 알아보세요.
- 이 항목은 일반적인 개념에 대해서만 검토할 수도 있고, 먼저 다음 항목의 절차를 완료 하는 경우이 항목을 단계별로 수행할 수도 있습니다.

    1. [앱 생성](data-platform-create-app.md)
    1. [해당 갤러리 사용자 지정](customize-layout-sharepoint.md)
    1. [해당 양식 사용자 지정](customize-forms-sharepoint.md)

## <a name="customize-a-locked-card"></a>잠긴 카드 사용자 지정

이 절차에서는 카드를 잠금 해제 하지 않고 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 **[Slider] (컨트롤/컨트롤-슬라이더나 컨트롤)** 로 바꿉니다.

1. 사용자가 생성 하 고 사용자 지정한 앱의 왼쪽 탐색 모음에서 **EditForm1** 을 선택한 다음 오른쪽 창의 **속성** 탭에서 **필드 편집** 을 선택 합니다.

1. 필드 목록에서 **직원 수**에 대 한 아래쪽 화살표를 선택 하 고 **컨트롤 유형**아래에서 목록을 엽니다.

    > [!div class="mx-imgBorder"]
    > 숫자 카드에 대 한 옵션 드롭다운 목록 ![](./media/customize-card/card-selector.png)

1. **편집 슬라이더**를 선택 합니다.

    화면은 변경 내용을 반영합니다.

    > [!div class="mx-imgBorder"]
    > 슬라이더 컨트롤을 사용 하 여 EditForm1 ![](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>카드 잠금 해제 및 사용자 지정

이 절차에서는 카드를 잠금 해제 하 고 방금 추가한 **슬라이더** 컨트롤의 **Max** 속성을 업데이트 합니다.

1. **EditForm1**에서 **직원 수** 카드의 **슬라이더** 컨트롤을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 슬라이더 ![선택](./media/customize-card/select-slider.png)

1. 오른쪽 창의 **고급** 탭에서 잠금 아이콘을 선택 하 여 카드의 잠금을 해제 합니다.

    > [!div class="mx-imgBorder"]
    > 카드 잠금 해제 ![](./media/customize-card/lock-icon.png)

1. **슬라이더** 컨트롤의 **Max** 속성을 1만로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 고급 탭에서 Max 속성 ![](./media/customize-card/max-property.png)

    **슬라이더** 컨트롤은 보다 정확한 값을 표시 합니다.

    > [!div class="mx-imgBorder"]
    > ![슬라이더 범위: 0 ~ 10000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>다음 단계

이제 앱을 생성하고 갤러리, 양식 및 카드를 사용자 지정하는 방법에 대한 기본적인 이해를 마쳤으므로 [처음부터 직접 앱을 빌드](data-platform-create-app-scratch.md)할 수 있습니다.