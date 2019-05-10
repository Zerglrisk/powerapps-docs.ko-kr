---
title: Back 및 Navigate 함수 | Microsoft Docs
description: PowerApps에서 Back 및 Navigate 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0033d0a2d7473e6aaeac1e8533f62873e0d2f49a
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670931"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>PowerApps에서 Back 및 Navigate 함수
표시되는 화면을 변경합니다.

## <a name="overview"></a>개요
대부분의 앱에는 여러 화면이 포함되어 있습니다.  **Back** 및 **Navigate** 함수를 사용하여 표시되는 화면을 변경합니다. 예를 들어 사용자가 해당 단추를 선택할 때 다른 화면을 표시하려는 경우 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 **Navigate** 함수를 포함하는 수식으로 설정합니다. 해당 수식에서 **Fade**와 같은 시각적 전환을 지정하여 한 화면을 다른 화면으로 변경하는 방법을 제어할 수 있습니다.  

**Back** 및 **Navigate**는 표시되는 화면만 변경합니다. 현재 표시되지 않은 화면은 백그라운드에서 작업을 계속합니다. 다른 화면에서 컨트롤의 속성을 참조하는 수식을 빌드할 수 있습니다. 예를 들어, 사용자가 한 화면에서 슬라이더의 값을 변경하고, 수식에서 해당 값을 사용하는 다른 화면으로 이동하여, 새 화면에서 어떻게 적용되는지를 확인할 수 있습니다.  그런 다음, 사용자가 원래 화면으로 다시 이동하면 슬라이더가 해당 값을 유지하고 있음을 확인할 수 있습니다.

사용자가 화면 사이를 이동할 때 [컨텍스트 변수](../working-with-variables.md#use-a-context-variable)도 보존됩니다. **Navigate**를 사용하여 수식이 표시되는 화면에 대해 둘 이상의 컨텍스트 변수를 설정할 수 있습니다. 이는 화면 외부에서 컨텍스트 변수를 설정하는 유일한 방법입니다. 이 방법을 사용하여 화면에 매개 변수를 전달할 수 있습니다. 다른 프로그래밍 도구를 사용한 경험이 있는 경우, 이 방법은 프로시저에 매개 변수를 전달하는 것과 유사합니다.

## <a name="description"></a>설명
### <a name="back"></a>Back
**Back** 함수는 가장 최근에 표시된 화면을 표시합니다. 이 함수에 대해 인수를 지정하지 않았습니다.

### <a name="navigate"></a>Navigate
첫 번째 인수에서 표시할 화면의 이름을 지정합니다.  

 두 번째 인수에서 이전 화면을 새 화면으로 변경하는 방법을 지정합니다.

| 전환 인수 | 설명 | 데모 |
| --- | --- | --- |
| **ScreenTransition.Cover** |새 화면이 현재 화면에 맞게 오른쪽에서 왼쪽으로 이동 뷰로 슬라이드 합니다. | ![화면 전환 커버 애니메이션](media/function-navigate/cover.gif) |
| **ScreenTransition.CoverRight** |새 화면 슬라이드 뷰로 이동 왼쪽에서 오른쪽으로 현재 화면에 맞게 합니다. | ![화면 전환 커버 오른쪽 애니메이션](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |현재 화면이 서서히 서 새 화면을 표시 합니다. | ![화면 전환 페이드 애니메이션](media/function-navigate/fade.gif) |
| **ScreenTransition.None** (기본값) |새 화면이 현재 화면을 신속 하 게 바꿉니다. | ![none 화면 전환 애니메이션](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | 현재 화면 슬라이드에서 새로운 화면을 알아내는 데 오른쪽에서 왼쪽으로 이동 합니다. | ![화면 전환 애니메이션을 끌어 내도록](media/function-navigate/uncover.gif) |
| **ScreenTransition.UnCoverRight** | 현재 화면 슬라이드에서 이동 왼쪽에서 오른쪽, 새 화면을 발견할 수 있습니다. | ![화면 전환은 오른쪽 애니메이션 파악](media/function-navigate/uncoverright.gif) |

**Navigate**를 사용하여 새 화면의 컨텍스트 변수를 만들거나 업데이트할 수 있습니다. 선택 사항인 세 번째 인수처럼 컨텍스트 변수의 이름을 포함하는 [레코드](../working-with-tables.md#records)를 [열](../working-with-tables.md#columns) 이름 및 컨텍스트 변수의 새 값으로 전달합니다.  이 레코드는 **[UpdateContext](function-updatecontext.md)** 함수로 사용한 레코드와 동일합니다.

전환하는 동안 추가적인 변경을 수행하려면 이전 화면의 **[OnHidden](../controls/control-screen.md)** 속성 또는 새 화면의 **[OnVisible](../controls/control-screen.md)** 속성을 설정합니다. **App.ActiveScreen** 속성은 변경 내용을 반영하도록 업데이트됩니다.

**Back**은 일반적으로 **true**를 반환하지만, 해당 사용자가 표시된 첫 번째 화면에 있고 이전 화면이 없는 경우 **false**를 반환합니다.  **Navigate**는 일반적으로 **true**를 반환하지만, 인수 중 하나에 문제가 있으면 **false**를 반환합니다.

[동작 수식](../working-with-formulas-in-depth.md) 내에서만 이러한 함수를 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Back**()

**Navigate**( *Screen* [, *Transition* [, *UpdateContextRecord* ] ] )

* *Screen* - 필수 항목입니다. 표시할 화면입니다.
* *전환* -선택 사항입니다.  현재 화면과 다음 화면 간에 사용할 시각적 전환입니다. 이 토픽의 앞부분에 있는 이 인수에 대한 유효한 값 목록을 참조하세요. 기본값은 **None**합니다.
* *UpdateContextRecord* - 선택 사항입니다.  하나 이상의 열 이름 및 각 열에 대한 값을 포함하는 레코드입니다. 이 레코드는 **[UpdateContext](function-updatecontext.md)** 함수에 전달된 경우처럼 새 화면의 컨텍스트 변수를 업데이트합니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **(세부 정보)를 이동 합니다.** |컨텍스트 변수에 대한 값으로 전환 또는 변경되지 않은 **Details** 화면을 표시합니다. |**Details** 화면이 빠르게 나타납니다. |
| **Navigate( Details, ScreenTransition.Fade )** |**Fade** 전환을 사용하여 **Details** 화면이 표시됩니다.  컨텍스트 변수의 값이 변경되지 않습니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시됩니다. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |**Fade** 전환을 사용하여 **Details** 화면이 표시되고 **ID** 컨텍스트 변수의 값이 **12**로 업데이트됩니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시되고, 화면의 컨텍스트 변수 **ID**가 **12**로 설정됩니다. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |**Fade** 전환을 사용하여 **Details** 화면이 표시됩니다. **ID** 컨텍스트 변수의 값이 **12**로 업데이트되고, **Shade** 컨텍스트 변수의 값이 **Color.Red**로 업데이트됩니다. |현재 화면이 서서히 사라지면서 **Details** 화면이 표시됩니다. **Details** 화면의 컨텍스트 변수 **ID**가 **12**로 설정되고, 컨텍스트 변수 **Shade**가 **Color.Red**로 설정됩니다. **Details** 화면에서 컨트롤의 **Fill** 속성을 **Shade**로 설정하는 경우 해당 컨트롤이 빨간색으로 표시됩니다. |

### <a name="step-by-step"></a>단계별
1. 기본 화면의 이름을 **DefaultScreen**으로 지정하고, 레이블을 추가하고, 해당 레이블의 **[Text](../controls/properties-core.md)** 속성이 **Default**를 표시하도록 설정합니다.
2. 화면을 추가하고 이름을 **AddlScreen**으로 지정합니다.
3. 레이블을 **AddlScreen**에 추가하고, 레이블의 **[Text](../controls/properties-core.md)** 속성을 **Addl**을 표시하도록 설정합니다.
4. 단추를 **AddlScreen**에 추가하고, 해당 **[OnSelect](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.<br>**Navigate(DefaultScreen, ScreenTransition.Fade)**
5. **AddlScreen**에서 F5를 누른 다음, 단추를 선택합니다.<br>**DefaultScreen** 페이드 전환을 통해 표시 됩니다.

[또 다른 예](../add-screen-context-variables.md)

