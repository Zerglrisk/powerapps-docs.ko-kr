---
title: Back 및 Navigate 함수 | Microsoft Docs
description: PowerApps에서 Back 및 Navigate 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8f63321b128214d14cd2f4e521d7cc1b85c7b98f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984494"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>PowerApps에서 Back 및 Navigate 함수

표시되는 화면을 변경합니다.

## <a name="overview"></a>개요

대부분의 앱에는 여러 화면 포함되어 있습니다.  **Back** 및 **Navigate** 함수를 사용하여 표시되는 화면을 변경합니다. 예를 들어 사용자가 해당 단추를 선택할 때 다른 화면을 표시하려는 경우 단추의 **[OnSelect](../controls/properties-core.md)** 속성 단추를 **Navigate** 함수를 포함하는 수식으로 설정합니다. 해당 수식에서 **페이드**와 같은 시각적 전환을 지정하여 한 화면을 다른 화면으로 변경하는 방법을 제어할 수 있습니다.  

**Back** 및 **Navigate**는 표시되는 화면만 변경합니다. 현재 표시되지 않은 화면은 백그라운드에서 작업을 계속합니다. 다른 화면에서 컨트롤의 속성을 참조 하는 수식을 작성할 수 있습니다. 예를 들어 사용자가 한 화면에서 슬라이더의 값을 변경 하 고, 수식에서 해당 값을 사용 하는 다른 화면으로 이동 하 고, 새 화면에서 발생 하는 작업에 미치는 영향을 확인할 수 있습니다. 그러면 사용자가 원래 화면으로 다시 이동 하 여 슬라이더가 해당 값을 유지 하는지 확인할 수 있습니다.

또한 사용자가 화면 간 이동할 때 [컨텍스트 변수](../working-with-variables.md#use-a-context-variable)도 보존됩니다. **Navigate**를 사용하여 수식이 표시되는 화면에 대해 둘 이상의 컨텍스트 변수를 설정할 수 있습니다. 이는 화면 외부에서 컨텍스트 변수를 설정하는 유일한 방법입니다. 이 방법을 사용하여 화면에 매개 변수를 전달할 수 있습니다. 다른 프로그래밍 도구를 사용한 경우 이 방법은 프로시저에 매개 변수를 전달하는 것과 유사합니다.

[동작 수식](../working-with-formulas-in-depth.md)내 에서만 함수 중 하나를 사용할 수 있습니다.

## <a name="navigate"></a>Navigate

첫 번째 인수에서 표시할 화면의 이름을 지정합니다.  

 두 번째 인수에서 이전 화면을 새 화면으로 변경하는 방법을 지정합니다.

| 전환 인수 | 설명 | 데모 |
| --- | --- | --- |
| **ScreenTransition.Cover** |새 화면은 현재 화면을 포함 하도록 오른쪽에서 왼쪽으로 이동 하는 보기에 슬라이드를 표시 합니다. | ![화면 전환 커버 애니메이션](media/function-navigate/cover.gif) |
| **Screentransition.none. CoverRight** |새 화면은 현재 화면을 포함 하도록 왼쪽에서 오른쪽으로 이동 하는 보기에 슬라이드를 표시 합니다. | ![화면 전환 오른쪽 애니메이션](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |현재 화면이 사라지고 새 화면을 표시 합니다. | ![화면 전환 페이드 애니메이션](media/function-navigate/fade.gif) |
| **Screentransition.none** (기본값) |새 화면이 현재 화면을 신속 하 게 대체 합니다. | ![화면 전환 없음 애니메이션](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | 현재 화면에서 오른쪽에서 왼쪽으로 이동 하 여 새 화면을 표시 하는 뷰를 벗어났습니다. | ![화면 전환에서 애니메이션을 찾습니다.](media/function-navigate/uncover.gif) |
| **Screentransition.none. UnCoverRight** | 현재 화면에 표시 되는 슬라이드가 표시 되지 않으며 왼쪽에서 오른쪽으로 이동 하 여 새 화면을 찾습니다. | ![화면 전환 오른쪽으로 당기기 애니메이션](media/function-navigate/uncoverright.gif) |

**Navigate**를 사용하여 새 화면의 컨텍스트 변수를 만들거나 업데이트할 수 있습니다. 선택 사항인 세 번째 인수처럼 컨텍스트 변수의 이름을 포함하는 [레코드](../working-with-tables.md#records)를 [열](../working-with-tables.md#columns) 이름 및 컨텍스트 변수의 새 값으로 전달합니다.  이 레코드는 **[UpdateContext](function-updatecontext.md)** 함수로 사용한 레코드와 동일합니다.

전환하는 동안 추가적인 변경을 수행하려면 이전 화면의 **[OnHidden](../controls/control-screen.md)** 속성 또는 새 화면의 **[OnVisible](../controls/control-screen.md)** 속성을 설정합니다. **App.ActiveScreen** 속성은 변경 내용을 반영하도록 업데이트됩니다.

**탐색** 은 일반적으로 **true** 를 반환 하지만 오류가 발생 하면 **false** 를 반환 합니다.

## <a name="back"></a>Back

**뒤로** 함수는 가장 최근에 표시 된 화면으로 돌아갑니다.

각 **탐색** 호출에 대해 앱은 표시 된 화면과 전환을 추적 합니다. 연속 된 호출을 사용 하 여 사용자가 앱을 시작할 때 표시 되는 화면 **으로 돌아갈 수** 있습니다.

**Back** 함수가 실행 되 면 기본적으로 역 전환이 사용 됩니다. 예를 들어 화면이 **CoverRight** 전환을 통해 표시 되는 경우 **Back** 은 return (왼쪽)을 사용 **하 여를** 반환 합니다.  **페이드** 및 **없음** 은 자신의 반대입니다. 선택적 인수를 **뒤로** 전달 하 여 특정 전환을 강제로 적용 합니다.

**뒤로** 는 일반적으로 **true** 를 반환 하지만, 사용자가 앱을 시작한 후 다른 화면으로 이동 하지 않은 경우 **false** 를 반환 합니다.

## <a name="syntax"></a>구문

**Back**([ *전환* ])

* *Transition* -선택 사항입니다. 현재 화면과 이전 화면 사이에서 사용할 시각적 전환입니다. 이 항목의 앞부분에 나오는이 인수에 대 한 올바른 값 목록을 참조 하십시오. 기본적으로 화면에서 반환 하는 전환은 표시 되는 전환의 역함수입니다.

**Navigate**( *화면* [, *전환* [, *UpdateContextRecord* ]])

* *Screen* - 필수 항목입니다. 표시할 화면입니다.
* *Transition* -선택 사항입니다.  현재 화면과 다음 화면 간에 사용할 시각적 전환입니다. 이 토픽의 앞부분에 있는 이 인수에 대한 유효한 값 목록을 참조하세요. 기본값은 **None**입니다.
* *UpdateContextRecord* - 선택 사항입니다.  하나 이상의 열 이름 및 각 열에 대한 값을 포함하는 레코드입니다. 이 레코드는 **[UpdateContext](function-updatecontext.md)** 함수에 전달된 경우처럼 새 화면의 컨텍스트 변수를 업데이트합니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Navigate (세부 정보)** |컨텍스트 변수에 대한 값으로 전환 또는 변경되지 않은 **Details** 화면을 표시합니다. |**Details** 화면이 빠르게 나타납니다. |
| **Navigate( Details, ScreenTransition.Fade )** |**Fade** 전환을 사용하여 **Details** 화면이 표시됩니다.  컨텍스트 변수의 값이 변경되지 않습니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시됩니다. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |**Fade** 전환을 사용하여 **Details** 화면이 표시되고 **ID** 컨텍스트 변수의 값이 **12**로 업데이트됩니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시되고, 화면의 컨텍스트 변수 **ID**가 **12**로 설정됩니다. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |**Fade** 전환을 사용하여 **Details** 화면이 표시됩니다. **ID** 컨텍스트 변수의 값이 **12**로 업데이트되고, **Shade** 컨텍스트 변수의 값이 **Color.Red**로 업데이트됩니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시됩니다. **Details** 화면의 컨텍스트 변수 **ID**가 **12**로 설정되고, 컨텍스트 변수 **Shade**가 **Color.Red**로 설정됩니다. **Details** 화면에서 컨트롤의 **Fill** 속성을 **Shade**로 설정하는 경우 해당 컨트롤이 빨간색으로 표시됩니다. |
| **Back()** | 기본 반환 전환을 사용 하 여 이전 화면을 표시 합니다. | 현재 화면이 나타난 전환의 역 전환을 통해 이전 화면을 표시 합니다. |
| **Back (Screentransition.none)** |  **커버** 전환을 사용 하 여 이전 화면을 표시 합니다. | 현재 화면이 나타난 전환에 관계 없이 **덮개** 전환을 통해 이전 화면을 표시 합니다. |

### <a name="step-by-step"></a>단계별

1. 빈 앱을 만듭니다.

1. 여기에 두 번째 화면을 추가 합니다.

    앱에는 두 개의 빈 화면이 있습니다. **Screen1** 및 **Screen2**.

1. **Screen2** 의 **Fill** 속성을 값 `Gray`로 설정 합니다.

1. **Screen2**에서 단추를 추가 하 고 **[onselect](../controls/properties-core.md)** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. **Alt** 키를 누른 채 단추를 선택 합니다.

    **Screen1** 는 왼쪽에 있는 전환을 통해 흰색 배경으로 표시 됩니다.

1. **Screen1**에서 단추를 추가 하 고 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Back()
    ```

1. **Alt** 키를 누른 채 단추를 선택 합니다.

    두 번째 화면은 오른쪽 ( **덮개**의 역함수)을 나타내는 전환을 통해 회색 배경과 함께 표시 됩니다.

1. 각 화면에서 단추를 반복 해 서 선택 하 여 앞뒤로 바운스 합니다.

[또 다른 예](../add-screen-context-variables.md)
