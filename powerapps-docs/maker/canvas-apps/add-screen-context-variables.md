---
title: 캔버스 앱에 화면 추가 및 화면 간 이동 | Microsoft Docs
description: 캔버스 앱에 화면을 추가 하 고 다음 및 뒤로 화살표를 사용 하 여 Power Apps에서 화면 간을 이동 합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724573"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>캔버스 앱에 화면 추가 및 화면 간 이동

여러 화면이 있는 캔버스 앱을 만들고 사용자가 이들 사이를 이동할 수 있는 방법을 추가합니다.

## <a name="add-and-rename-a-screen"></a>화면 추가 및 이름 바꾸기

1. **홈** 탭에서 **새 화면**을 선택 하 고 추가 하려는 화면 유형을 선택 합니다.

    ![홈 탭에서 화면 옵션 추가](./media/add-screen-context-variables/add-screen.png)

2. 오른쪽 창에서 화면 이름 ( **속성** 탭 바로 위)을 선택한 다음 **원본**을 입력 합니다.

    ![기본 화면 이름 바꾸기](./media/add-screen-context-variables/name-source-screen.png)

3. 다른 화면을 추가하고 이름을 **Target**으로 지정합니다.

    ![왼쪽 탐색 표시줄에서 두 개의 화면](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>화면 다시 정렬

왼쪽 탐색 모음에서 위나 아래로 이동 하려는 화면을 마우스로 가리키고, 표시 되는 줄임표 단추를 선택한 다음 **위로 이동** 또는 **아래로 이동**을 선택 합니다.

![화면 다시 정렬](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> 앱을 열면 일반적으로 컨트롤의 계층 목록 맨 위에 있는 화면이 먼저 나타납니다. 그러나 **[OnStart](controls/control-screen.md)** 속성을 **[Navigate](functions/function-navigate.md)** 함수를 포함 하는 수식으로 설정 하 여 다른 화면을 지정할 수 있습니다.

## <a name="add-navigation"></a>탐색 추가

1. **원본** 화면이 선택 된 상태에서 **삽입** 탭을 열고 **아이콘**을 선택한 후 **다음 화살표**를 선택 합니다.  

    ![[삽입] 탭에 있는 [셰이프] 옵션](./media/add-screen-context-variables/add-next-arrow.png)

2. (선택 사항) 화면의 오른쪽 아래 모서리에 표시되도록 화살표를 이동합니다.

3. 화살표가 선택 된 상태에서 **작업** 탭을 선택 하 고 **탐색**을 선택 합니다.

    화살표에 대한 **[OnSelect](controls/properties-core.md)** 속성이 **Navigate** 함수로 자동으로 설정됩니다.

    ![Navigate 함수로 설정된 OnSelect 속성](./media/add-screen-context-variables/onselect-default.png)

    사용자가 화살표를 선택 하면 **대상** 화면이 페이드 인 됩니다.

4. **Target** 화면에서 **뒤로 화살표**를 추가하고 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    `Navigate(Source, ScreenTransition.Fade)`

5. Alt 키를 누른 채 각 화면에서 화살표를 선택 하 여 화면 사이를 전환 합니다.

## <a name="more-information"></a>자세한 정보

[화면 컨트롤 참조](controls/control-screen.md)