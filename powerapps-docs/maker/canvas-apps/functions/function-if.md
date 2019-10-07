---
title: If 및 Switch 함수 | Microsoft Docs
description: PowerApps의 If 및 Switch 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff143e9d73de25b5ba2c0076fc4b02d5f101a85b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984755"
---
# <a name="if-and-switch-functions-in-powerapps"></a>PowerApps의 If 및 Switch 함수
집합의 조건이 참 인지(**If**) 또는 수식의 결과가 집합의 값과 일치하는지(**Switch**) 확인한 다음, 결과를 반환하거나 작업을 실행합니다.

## <a name="description"></a>설명
**If** 함수는 **true** 결과를 찾을 때까지 하나 이상의 조건을 테스트합니다. 그러한 결과를 찾으면 해당 값이 반환됩니다. 그러한 결과가 없으면 기본값이 반환됩니다. 두 경우 모두, 표시할 문자열, 평가할 수식 또는 다른 양식의 결과가 반환 값이 될 수 있습니다.

**Switch** 함수는 수식을 평가하고 그 결과가 사용자가 지정한 시퀀스의 값과 일치하는지 확인합니다. 일치하는 항목을 찾으면 해당 값이 반환됩니다. 일치하는 항목이 없으면 기본값이 반환됩니다. 두 경우 모두, 표시할 문자열, 평가할 수식 또는 다른 양식의 결과가 반환 값이 될 수 있습니다.

**If**와 **Switch**는 매우 유사하지만 상황에 가장 적합한 함수를 사용해야 합니다.

* 단일 조건을 평가하려면 **If**를 사용합니다. 이 함수의 가장 일반적인 구문은 **If**( *Condition*, *ThenResult*, *DefaultResult* )이며, 다른 프로그래밍 도구에서 볼 수 있는 일반적인 “if …  then … else …” 패턴을 제공합니다.
* 관련이 없는 여러 조건을 평가하려면 **If**를 사용합니다. Microsoft Excel과 달리 PowerApps에서는 **If** 수식을 중첩하지 않고 여러 조건을 지정할 수 있습니다.
* 다수의 가능한 일치 항목에 대해 단일 조건을 평가하려면 **Switch**를 사용합니다. 이 경우 **If**를 사용할 수도 있지만 가능한 일치 항목마다 수식을 반복해야 합니다.

두 가지 이상의 작업을 분기하기 위해 [동작 수식](../working-with-formulas-in-depth.md)에 이 두 가지 함수를 모두 사용할 수 있습니다. 하나의 분기만 작업을 트리거합니다. 조건과 일치는 순서대로 평가되고 조건이 **true**이거나 일치가 발견되면 중지됩니다.

**true**인 조건이 없고 일치하는 항목이 없고 기본 결과를 지정하지 않으면 *공백*이 반환됩니다.

## <a name="syntax"></a>구문
**If**( *Condition*, *ThenResult* [, *DefaultResult* ] )<br>**If**( *Condition1*, *ThenResult1* [, *Condition2*, *ThenResult2*, ... [ , *DefaultResult* ] ] )

* *Condition(s)* - 필수 항목입니다. **true**가 있는지 테스트할 수식입니다. 이러한 수식에는 일반적으로 비교 [연산자](operators.md)(예: **<** , **>** 및 **=** )와 **[IsBlank](function-isblank-isempty.md)** 및 **[IsEmpty](function-isblank-isempty.md)** 와 같은 테스트 함수가 포함됩니다.
* *ThenResult(s)* - 필수 항목입니다. **true**로 평가되는 조건에 대해 반환할 해당 값입니다.
* *DefaultResult* - 선택 항목입니다. **true**로 평가되는 조건이 없는 경우 반환할 값입니다.  이 인수를 지정하지 않으면 *공백*이 반환됩니다.

**Switch**( *Formula*, *Match1*, *Result1* [, *Match2*, *Result2*, ... [, *DefaultResult* ] ] )

* *Formula* - 필수 항목입니다. 일치 항목이 있는지 평가할 수식입니다.  이 수식은 한 번만 평가됩니다.
* *Match(s)* - 필수 항목입니다. *Formula*의 결과와 비교할 값입니다.  정확히 일치하는 항목이 발견되면 해당하는 *Result*가 반환됩니다.
* *Result(s)* - 필수 항목입니다. 정확히 일치하는 항목이 발견되면 반환할 해당 값입니다.
* *DefaultResult* - 선택 항목입니다. 정확히 일치하는 항목이 없으면 이 값이 반환됩니다. 이 인수를 지정하지 않으면 *공백*이 반환됩니다.

## <a name="examples"></a>예
### <a name="values-in-formulas"></a>수식의 값
다음 예제에서 **Slider1**이라는 **Slider** 컨트롤의 값은 **25**입니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1" )** |조건은 **true**이고 해당 결과가 반환됩니다. |"Result1" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", "Result2" )** |조건은 **true**이고 해당 결과가 반환됩니다. |"Result1" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1" )** |조건은 **false**이고 *DefaultResult*가 제공되지 않았습니다. |*공백* |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", "Result2" )** |조건은 **false**이고 *DefaultResult*가 제공되었고 반환됩니다. |"Result2" |
| **If( Slider1.Value&nbsp;=&nbsp;25, "Result1", Slider1.Value&nbsp;>&nbsp;0, "Result2" )** |첫 번째 조건은 **true**이고 해당 결과가 반환됩니다. 두 번째 조건도 **true**이지만, 인수 목록에서 **true**로 평가되는 조건보다 뒷부분에 표시되기 때문에 평가되지 않습니다. |"Result1" |
| **If( IsBlank(&nbsp;Slider1.Value&nbsp;), "Result1", IsNumeric(&nbsp;Slider1.Value&nbsp;), "Result2" )** |슬라이더가 *공백*이 아니어서 첫 번째 조건은 **false**입니다. 슬라이더의 값이 숫자이고 해당 결과가 반환되기 때문에 두 번째 조건은 **true**입니다. |"Result2" |
| **If( Slider1.Value&nbsp;>&nbsp;1000, "Result1", Slider1.Value&nbsp;>&nbsp;50, "Result2", "Result3")** |첫 번째와 두 번째 조건이 모두 **false**이며 *DefaultResult*가 제공되었고 반환됩니다. |"Result3" |
| **Switch( Slider1.Value, 25, "Result1" )** |슬라이더의 값이 검사할 첫 번째 값과 일치하며 해당 결과가 반환됩니다. |"Result1" |
| **Switch( Slider1.Value, 20, "Result1", 25, "Result2", 30, "Result3" )** |슬라이더의 값이 검사할 두 번째 값과 일치하며 해당 결과가 반환됩니다. |"Result2" |
| **Switch( Slider1.Value, 20, "Result1", 10, "Result2", 0, "Result3", "DefaultResult" )** |슬라이더의 값이 검사할 모든 값과 일치하지 않습니다.  *DefaultResult*가 제공되었으므로 반환됩니다. |"DefaultResult" |

### <a name="branching-in-behavior-formulas"></a>동작 수식에서 분기
이 예제는 **FirstName**이라는 **[Text input](../controls/control-text-input.md)** 컨트롤에 "John"이라는 값이 입력되어 있습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **If( ! IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ) )** |조건이 **true**이므로 **[Navigate](function-navigate.md)** 함수가 실행됩니다. **[IsBlank](function-isblank-isempty.md)** 함수를 사용하면 필수 양식 필드가 채워져 있는지 테스트할 수 있습니다.  **FirstName**이 [공백](function-isblank-isempty.md)인 경우 이 수식은 아무 효과가 없습니다. |**true**<br><br>화면이 **Screen1**으로 변경됩니다. |
| **If( IsBlank( FirstName.Text ), Navigate(&nbsp;Screen1, ScreenTransition.None ), Back() )** |**!** 연산자가 없으면 조건이 **false**이므로 **[Navigate](function-navigate.md)** 함수가 실행되지 않습니다. **[Back](function-navigate.md)** 함수가 *DefaultResult*로 제공되었으므로 실행됩니다. |**true**<br><br>화면이 이전에 표시된 화면으로 돌아갑니다. |
| **Switch( FirstName.Text, "Carlos", Navigate(&nbsp;Screen1, ScreenTransition.None ), "Kirstin", Navigate( Screen2, ScreenTransition.None ), "John", Navigate( Screen3, ScreenTransition.None ) )** |**FirstName.Text**의 값이 "Carlos", "Kirstin", "John" 순서로 비교됩니다. 'John'과 일치하는 항목이 있으므로 앱이 **Screen3**으로 이동합니다. |**true**<br><br>화면이 **Screen3**으로 변경됩니다. |

### <a name="step-by-step"></a>단계별 가이드
1. **[Text input](../controls/control-text-input.md)** 컨트롤을 추가하고 기본적으로 해당 이름이 없는 경우 이름을 **Text1**로 지정합니다.
2. **Text1**에 **30**을 입력합니다.
3. **Label** 컨트롤을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
   **If( Value(Text1.Text) < 20, "Order MANY more!", Value(Text1.Text) < 40, "Order more!", Text1.Text )**
   
    **레이블** 컨트롤에 **Order more!** 가 표시됩니다. **Text1**의 값이 20보다 크지만 40보다 작기 때문입니다.
4. **Text1**에 **15**를 입력합니다.
   
    **레이블** 컨트롤에 **Order MANY more!** 가 표시됩니다. **Text1**의 값이 20보다 작기 때문입니다.
5. **Text1**에 **50**을 입력합니다.
   
    입력한 값이 40 이상이기 때문에 **레이블** 컨트롤에 이 값이 표시됩니다.

