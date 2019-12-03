---
title: 캔버스 앱의 변수 이해 | Microsoft Docs
description: 캔버스 앱의 상태, 컨텍스트 변수 및 컬렉션 작업에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ac00411c48cc97cb54c30ccefc3d8a6e1af5e48
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74673256"
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>PowerApps에서 캔버스 앱 변수 이해

Visual Basic 또는 JavaScript와 같은 다른 프로그래밍 도구를 사용한 경우 **변수가 어디에 있나요?** 라고 물어볼 수 있습니다. Power Apps는 약간 다르며 다른 방법이 필요 합니다. 캔버스 앱을 빌드할 때 변수에 도달하는 대신 자신에게 **Excel에서 무엇을 할 수 있나요?** 라고 물어보세요.

다른 도구에서는 명시적으로 계산을 수행하여 결과를 변수에 저장했습니다. 그러나 Power Apps와 Excel은 입력 데이터가 변경 될 때 수식을 자동으로 다시 계산 하므로 일반적으로 변수를 만들고 업데이트할 필요가 없습니다. 가능한 경우 언제든지 이 방법을 사용하면 앱을 더 쉽게 만들고, 이해하고, 유지 관리할 수 있습니다.

경우에 따라 [동작 수식을](working-with-formulas-in-depth.md)추가 하 여 Excel의 모델을 확장 하는 Power Apps에서 변수를 사용 해야 합니다. 예를 들어 사용자가 단추를 선택할 때 이러한 수식이 실행됩니다. 종종 동작 수식 내에서 다른 수식에 사용할 변수를 설정하는 것이 유용합니다.

일반적으로 변수를 사용하지 마세요. 그러나 때로는 변수만 사용하여 원하는 환경을 설정할 수 있습니다. 변수는 해당 값을 설정 하는 함수에 표시 될 때 암시적으로 만들어지고 형식화 됩니다. 

## <a name="translate-excel-into-powerapps"></a>Excel을 PowerApps로 변환

### <a name="excel"></a>Excel

Excel의 작동 원리를 검토해 보겠습니다. 셀에는 숫자 또는 문자열과 같은 값 또는 다른 셀의 값을 기반으로 하는 수식이 포함될 수 있습니다. 사용자가 셀에 다른 값을 입력하면 Excel에서는 새 값에 종속된 모든 수식을 자동으로 다시 계산합니다. 이 동작을 프로그래밍하여 사용하도록 설정할 필요가 없습니다.

다음 예에서는 **A3** 셀이 **A1 + A2**수식으로 설정 됩니다. **A1** 또는 **A2** 가 변경 되 면 **A3** 이 변경 내용을 반영 하도록 자동으로 다시 계산 됩니다. 이 동작을 수행 하려면 수식 자체 외부에서 코딩을 수행 하지 않아도 됩니다.

![Excel에서 두 숫자의 합계를 다시 계산 하는 애니메이션](media/working-with-variables/excel-recalc.gif)

Excel에서는 변수를 사용하지 않습니다. 수식이 포함된 셀의 값은 입력에 따라 변경되지만 수식의 결과를 기억하고 셀이나 다른 위치에 저장할 방법이 없습니다. 셀의 값을 변경하면 전체 스프레드시트가 변경되고 이전에 계산된 값이 손실될 수 있습니다. Excel 사용자는 셀을 복사하여 붙여넣을 수 있고 직접 제어할 수 있지만, 수식으로는 가능하지 않습니다.

### <a name="powerapps"></a>PowerApps

Power Apps에서 만든 앱은 Excel과 매우 비슷하게 작동 합니다. 셀을 업데이트하는 대신 화면에 원하는 위치에 컨트롤을 추가하고 수식에 사용할 컨트롤의 이름을 지정할 수 있습니다.

예를 들어 **Label1**이라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가 하 고 **TextInput1** 및 **TextInput2**라는 두 개의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가 하 여 앱에서 Excel 동작을 복제할 수 있습니다. 그런 다음 **Label1** 의 **[Text](controls/properties-core.md)** 속성을 **TextInput1 + TextInput2**로 설정 하면 **TextInput1** 및 **TextInput2** 에 있는 모든 숫자의 합계가 자동으로 표시 됩니다.

![PowerApps에서 두 숫자의 합계 계산](media/working-with-variables/recalc1.png)

**Label1** 컨트롤이 선택 되어 화면 위쪽의 수식 입력줄에 해당 **[텍스트](controls/properties-core.md)** 수식이 표시 됩니다. 여기서 **TextInput1 + TextInput2** 수식을 찾습니다. 이 수식은 Excel 통합 문서에서 셀 간에 종속성을 만든 것처럼 이러한 컨트롤 간에 종속성을 만듭니다.  **TextInput1**의 값을 변경 하겠습니다.

![PowerApps에서 두 숫자의 합계를 계산 하는 애니메이션](media/working-with-variables/recalc2.gif)

**Label1** 의 수식이 자동으로 다시 계산 되어 새 값을 표시 합니다.

Power Apps에서 수식을 사용 하 여 컨트롤의 기본 값 뿐만 아니라 서식 지정과 같은 속성을 확인할 수 있습니다. 다음 예제에서 레이블의 **[Color](controls/properties-color-border.md)** 속성에 대한 수식은 자동으로 음수 값을 빨간색으로 표시합니다. **[If](functions/function-if.md)** 함수는 Excel과 매우 친숙해야 합니다.

`If( Value(Label1.Text) < 0, Red, Black )`

![조건부 서식 지정 애니메이션](media/working-with-variables/recalc-color.gif)

다음과 같은 다양한 시나리오에 수식을 사용할 수 있습니다.

* 디바이스의 GPS를 사용하면 지도 컨트롤에서 **Location.Latitude** 및 **Location.Longitude**를 사용하는 수식으로 현재 위치를 표시할 수 있습니다.  이동하는 대로 지도에서 내 위치를 자동으로 추적합니다.
* 다른 사용자가 [데이터 원본](working-with-data-sources.md)을 업데이트할 수 있습니다.  예를 들어 팀의 다른 구성원이 SharePoint 목록의 항목을 업데이트할 수 있습니다.  데이터 원본을 새로 고치면 종속된 모든 수식이 업데이트된 데이터를 반영하도록 자동으로 다시 계산됩니다. 예를 들어 **Filter( SharePointList )** 수식에 갤러리의 **[Items](controls/properties-core.md)** 속성을 설정하여 새로 필터링된 [레코드](working-with-tables.md#records) 집합을 자동으로 표시할 수 있습니다.

### <a name="benefits"></a>아니라

수식을 사용하여 앱을 빌드하면 다음과 같은 많은 이점이 있습니다.

* Excel을 알고 있는 경우 Power Apps를 알고 있어야 합니다. 모델과 수식 언어가 동일하기 때문입니다.
* 다른 프로그래밍 도구를 사용했으면 이러한 예제를 수행하는 데 필요한 코드의 양을 생각하면 됩니다.  Visual Basic에서는 각 텍스트 입력 컨트롤에 변경 이벤트에 대한 이벤트 처리기를 작성해야 합니다.  이러한 컨트롤 각각에서 계산을 수행하는 코드가 중복되고 동기화되지 못하거나 일반적인 서브루틴을 작성해야 합니다.  Power Apps에서 한 줄로 된 단일 수식을 사용 하 여 모든 것을 수행 했습니다.
* **Label1**의 텍스트를 가져오는 위치를 이해 하기 위해 **[텍스트](controls/properties-core.md)** 속성의 수식을 정확히 찾을 수 있습니다.  이 컨트롤의 텍스트에 영향을 줄 수 있는 다른 방법은 없습니다.  기존의 프로그래밍 도구에서 모든 이벤트 처리기 또는 서브루틴은 프로그램의 모든 위치에서 레이블의 값을 변경할 수 있습니다.  이로 인해 변수가 언제 어디서 변경되었는지 추적하기가 어려워질 수 있습니다.
* 사용자가 슬라이더 컨트롤을 변경한 다음 생각을 바꾸면 슬라이더를 원래 값으로 다시 변경할 수 있습니다.  그러면 마치 아무 것도 변경되지 않은 것처럼 됩니다. 즉 앱에서 이전과 동일한 컨트롤 값을 표시합니다.  Excel에서 아무 효과가 없는 것처럼 "what if"를 실험하고 요청하는 것에 대해 아무 효과가 없습니다.  

일반적으로 수식을 사용하여 결과를 얻을 수 있는 경우가 더 효과적입니다. Power Apps에서 수식 엔진을 사용할 수 있습니다.  

## <a name="know-when-to-use-variables"></a>변수를 사용하는 경우 확인

구식의 계산기처럼 작동하도록 단순한 가산기를 누계로 변경해 보겠습니다. **추가** 단추를 선택하는 경우 누계에 숫자를 추가합니다. **지우기** 단추를 선택하는 경우 누계를 0으로 다시 설정합니다.

| 표시가 | 설명 |
|----|----|
| 텍스트 입력 컨트롤, 레이블 및 단추 2 개가 포함 된 <style>img {max-width: none}</style> ![앱](media/working-with-variables/button-changes-state-1.png) | 앱이 시작 되 면 누계는 0입니다.<br><br>빨간색 점은 사용자가 **77**를 입력 하는 텍스트 입력 상자에 사용자의 손가락을 나타냅니다. |
| ![텍스트 입력 컨트롤에 77이 포함 되어 있고 추가 단추가 눌러져 있습니다.](media/working-with-variables/button-changes-state-2.png) | 사용자가 **추가** 단추를 선택 합니다. |
| ![합계는 77이 고 다른 77는 추가 됩니다.](media/working-with-variables/button-changes-state-3.png) | 77는 누계에 추가 됩니다.<br><br>사용자가 **추가** 단추를 다시 선택 합니다. |
| ![합계는 지워지는 154입니다.](media/working-with-variables/button-changes-state-4.png) | 77이 실행 중인 합계에 다시 추가 되어 154가 발생 합니다.<br><br>사용자가 **지우기** 단추를 선택 합니다. |
| ![합계가 지워집니다.](media/working-with-variables/button-changes-state-5.png) | 누계는 0으로 다시 설정 됩니다. |

계산기는 Excel에 존재하지 않는 단추를 사용합니다. 이 앱에서는 사용자가 수행하는 일련의 작업에 따라 값이 달라지므로 수식만으로는 누계를 계산할 수 없습니다. 대신 누계를 수동으로 기록하고 업데이트해야 합니다. 대부분의 프로그래밍 도구에서는 이 정보를 *변수*에 저장합니다.

앱이 원하는 방식으로 작동하도록 변수가 필요할 수도 있습니다.  그러나 이 방법에는 다음과 같은 주의 사항이 있습니다.

* 누계를 수동으로 업데이트해야 합니다. 자동 다시 계산을 수행하지 않습니다.
* 누계는 더 이상 다른 컨트롤의 값을 기준으로 계산되지 않습니다. 사용자가 **추가** 단추를 선택한 횟수와 매번 텍스트 입력 컨트롤에 있던 값에 따라 누계가 달라집니다. 사용자가 77을 입력하고 **추가**를 두 번 추가했나요? 아니면 각 추가에 대해 24와 130을 지정했나요? 합계가 154에 도달한 후에는 그 차이를 알 수 없습니다.
* 합계에 대한 변경은 다른 경로에서 제공될 수 있습니다. 이 예제에서는 **추가** 및 **지우기** 단추 모두에서 합계를 업데이트할 수 있습니다. 앱이 예상대로 작동하지 않으면 문제의 원인이 되는 단추는 무엇일까요?

## <a name="use-a-global-variable"></a>전역 변수 사용

계산기를 만들려면 누계를 보유할 변수가 필요합니다. Power Apps에서 사용할 가장 간단한 변수는 *전역 변수*입니다.  

전역 변수의 작동 방식은 다음과 같습니다.

* **[Set](functions/function-set.md)** 함수를 사용하여 전역 변수의 값을 설정합니다.  **Set( MyVar, 1 )** 은 **MyVar** 전역 변수를 **1**의 값으로 설정합니다.
* **Set** 함수와 함께 사용할 이름을 참조하여 전역 변수를 사용합니다.  이 경우 **MyVar**는 **1**을 반환합니다.
* 전역 변수에는 문자열, 숫자, 레코드 및 [테이블](working-with-tables.md)을 포함한 모든 값이 포함될 수 있습니다.

전역 변수를 사용하여 계산기를 다시 빌드해 보겠습니다.

1. **TextInput1**이라는 텍스트 입력 컨트롤과 **Button1** 및  **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"** 로 설정하고, **Button2**의 **Text** 속성을 **"지우기"** 로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Set (RunningTotal, RunningTotal + TextInput1)**

    이 수식이 있으면 **+** 연산자로 인해 숫자가 포함 된 전역 변수로 **RunningTotal** 설정 됩니다. 앱의 모든 위치에서 **RunningTotal** 를 참조할 수 있습니다. 사용자가이 앱을 열 때마다 **RunningTotal** 의 초기 값은 *비어*있습니다.

    사용자가 처음으로 **추가** 단추를 선택 하 고 실행을 **[설정](functions/function-set.md)** 하면 **RunningTotal** 가 **RunningTotal + TextInput1**값으로 설정 됩니다.

    ![추가 단추의 OnSelect 속성은 Set 함수로 설정 됩니다.](media/working-with-variables/global-variable-1.png)

4. 사용자가 **지우기** 단추를 선택할 때마다 누계를 **0**으로 설정하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Set( RunningTotal, 0 )**

    ![Clear 단추의 OnSelect 속성은 Set 함수로 설정 됩니다.](media/working-with-variables/global-variable-2.png)

5. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고 **[Text](controls/properties-core.md)** 속성을 **RunningTotal**로 설정합니다.

    이 수식은 자동으로 다시 계산되며, 사용자가 선택하는 단추에 따라 변경될 때 사용자에게 **RunningTotal** 값을 표시합니다.

    ![레이블의 Text 속성은 변수의 이름으로 설정 됩니다.](media/working-with-variables/global-variable-3.png)

6. 앱을 미리 보면 위에서 설명한 대로 계산기가 있습니다. 텍스트 상자에서 숫자를 입력하고 **추가** 단추를 몇 번 누릅니다. 준비가 되면 Esc 키를 사용하여 제작 환경으로 돌아갑니다.

    ![텍스트 입력 컨트롤에는 값이 포함 되 고, 레이블에는 누계가 포함 됩니다.](media/working-with-variables/global-variable-4.png)

7. 전역 변수의 값을 표시 하려면 **파일** 메뉴를 선택 하 고 왼쪽 창에서 **변수** 를 선택 합니다.

    ![파일 메뉴의 변수 옵션](media/working-with-variables/global-variable-file-1.png)

8. 변수를 정의 하 고 사용 하는 모든 위치를 표시 하려면 해당 변수를 선택 합니다.

    ![변수가 사용 되는 위치 목록](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>변수 유형

Power Apps에는 다음과 같은 세 가지 유형의 변수가 있습니다.

| 변수 유형 | 범위 | 설명 | 를 설정 하는 함수 |
| --- | --- | --- | --- |
| 전역 변수 |App |사용이 가장 간편합니다. 앱의 모든 위치에서 참조할 수 있는 숫자, 텍스트 문자열, 부울, 레코드, 테이블 등을 보유합니다. |[**Set**](functions/function-set.md) |
| 컨텍스트 변수 |화면 |다른 언어의 프로시저에 대한 매개 변수와 마찬가지로 화면에 값을 전달하는 데 매우 유용합니다. 한 화면 에서만 참조할 수 있습니다. |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navigate**](functions/function-navigate.md) |
| 수집이 |App |앱의 어디에서 나 참조할 수 있는 테이블을 보유 합니다. 테이블의 내용을 전체적으로 설정하지 않고 수정할 수 있습니다. 나중에 사용하기 위해 로컬 디바이스에 저장할 수 있습니다. |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>변수 만들기 및 제거

모든 변수는 **Set**, **updatecontext**, **Navigate**, **Collect**또는 **clearcollect** 함수에 표시 될 때 암시적으로 생성 됩니다. 변수 및 해당 형식을 선언 하려면 앱의 모든 위치에서 이러한 함수에만 포함 해야 합니다. 이러한 함수는 변수를 만들지 않습니다. 변수는 값으로만 채워집니다. 다른 프로그래밍 도구에서 볼 수 있는 것 처럼 변수를 명시적으로 선언 하지 않으며 모든 입력은 사용에서 암시적입니다.

예를 들어 **Onselect** 수식이 **Set (X, 1)** 와 같은 단추 컨트롤이 있을 수 있습니다. 이 수식은 **X** 를 숫자 형식의 변수로 설정 합니다. 수식에서 **X** 를 숫자로 사용할 수 있으며,이 변수는 앱을 연 후 단추를 선택 하기 전에 *빈* 값을 가집니다. 단추를 선택 하면 **X** 값을 **1**로 지정 합니다.

다른 단추를 추가 하 고 **Onselect** 속성을 **set (X, "Hello")** 로 설정한 경우 유형 (텍스트 문자열)이 이전 **집합** (number)의 유형과 일치 하지 않기 때문에 오류가 발생 합니다. 변수의 모든 암시적 정의는 형식에 동의 해야 합니다. 이러한 모든 수식이 실제로 실행 되었기 때문에이는 수식에서 **X** 를 언급 했기 때문에 발생 합니다.

변수를 암시적으로 설정 하는 모든 **Set**, **updatecontext**, **Navigate**, **Collect**또는 **clearcollect** 함수를 제거 하 여 변수를 제거 합니다. 이러한 함수가 없으면 변수가 존재 하지 않습니다. 오류가 발생 하므로 변수에 대 한 참조도 제거 해야 합니다.

## <a name="variable-lifetime-and-initial-value"></a>변수 수명 및 초기 값

모든 변수는 앱이 실행 되는 동안 메모리에 유지 됩니다. 앱을 닫은 후 변수에 저장 된 값이 손실 됩니다.

**Patch** 또는 **Collect** 함수를 사용 하 여 데이터 원본에 변수의 내용을 저장할 수 있습니다. [**Savedata**](functions/function-savedata-loaddata.md) 함수를 사용 하 여 로컬 장치의 컬렉션에 값을 저장할 수도 있습니다.

사용자가 앱을 열 때 모든 변수의 초기 값은 *비어*있습니다.

## <a name="reading-variables"></a>변수 읽기

변수의 이름을 사용 하 여 해당 값을 읽습니다. 예를 들어 다음 수식을 사용 하 여 변수를 정의할 수 있습니다.

`Set( Radius, 12 )`

그런 다음 숫자를 사용할 수 있는 모든 위치에서 **Radius** 를 사용 하기만 하면 **12**로 바뀝니다.

`Pi() * Power( Radius, 2 )`

컨텍스트 변수에 전역 변수나 컬렉션과 동일한 이름을 지정 하면 컨텍스트 변수가 우선 적용 됩니다. 그러나 [명확성 연산자](functions/operators.md#disambiguation-operator) **@ [Radius]** 를 사용 하는 경우에도 전역 변수 또는 컬렉션을 참조할 수 있습니다.

## <a name="use-a-context-variable"></a>컨텍스트 변수 사용

전역 변수 대신 컨텍스트 변수를 사용하여 계산기를 만드는 방법을 살펴보겠습니다.

컨텍스트 변수의 작동 방식은 다음과 같습니다.

* **[Updatecontext](functions/function-updatecontext.md)** 또는 **[Navigate](functions/function-navigate.md)** 함수를 사용 하 여 컨텍스트 변수를 암시적으로 설정 하 고 설정 합니다. 앱이 시작 되 면 모든 컨텍스트 변수의 초기 값이 *비어*있습니다.
* 컨텍스트 변수는 레코드를 사용 하 여 업데이트 합니다. 다른 프로그래밍 도구에서는 일반적으로 "x = 1"에서와 같이 할당에 "="를 사용합니다. 컨텍스트 변수의 경우 **{ x: 1 }** 을 대신 사용합니다. 컨텍스트 변수를 사용 하는 경우 레코드 구문 없이 해당 이름을 직접 사용 합니다.
* **[Navigate](functions/function-navigate.md)** 함수를 사용 하 여 화면을 표시 하는 경우에도 컨텍스트 변수를 설정할 수 있습니다. 화면을 일종의 프로시저 또는 서브루틴으로 생각 하는 경우이 방법은 다른 프로그래밍 도구에서 전달 하는 매개 변수와 비슷합니다.
* **[Navigate](functions/function-navigate.md)** 를 제외하고 컨텍스트 변수는 단일 화면의 컨텍스트로 제한되며, 여기에서 컨텍스트 변수의 이름을 얻습니다. 이 컨텍스트 외부에서는 사용하거나 설정할 수 없습니다.
* 컨텍스트 변수에는 문자열, 숫자, 레코드 및 [테이블](working-with-tables.md)을 포함한 모든 값이 포함될 수 있습니다.

컨텍스트 변수를 사용하여 계산기를 다시 빌드해 보겠습니다.

1. **TextInput1**이라는 텍스트 입력 컨트롤과 **Button1** 및  **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"** 로 설정하고, **Button2**의 **Text** 속성을 **"지우기"** 로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **UpdateContext ({RunningTotal: RunningTotal + TextInput1})**

    이 수식이 있으면 **+** 연산자 때문에 **RunningTotal** 가 숫자를 포함 하는 컨텍스트 변수로 설정 됩니다. 이 화면에서 **RunningTotal** 를 참조할 수 있습니다. 사용자가이 앱을 열 때마다 **RunningTotal** 의 초기 값은 *비어*있습니다.

    사용자가 처음으로 **추가** 단추를 선택 하 고 **[updatecontext](functions/function-updatecontext.md)** 를 실행 하는 경우 **RunningTotal** 는 **RunningTotal + TextInput1**값으로 설정 됩니다.

    ![추가 단추의 OnSelect 속성](media/working-with-variables/context-variable-1.png)

4. 사용자가 **지우기** 단추를 선택할 때마다 누계를 **0**으로 설정하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **UpdateContext( { RunningTotal: 0 } )**

    다시 말하지만 **[UpdateContext](functions/function-updatecontext.md)** 는 **UpdateContext( { RunningTotal: 0 } )** 수식과 함께 사용됩니다.

    ![Clear 단추의 OnSelect 속성](media/working-with-variables/context-variable-2.png)

5. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고 **[Text](controls/properties-core.md)** 속성을 **RunningTotal**로 설정합니다.

    이 수식은 자동으로 다시 계산되며, 사용자가 선택하는 단추에 따라 변경될 때 사용자에게 **RunningTotal** 값을 표시합니다.

    ![레이블 텍스트 속성](media/working-with-variables/context-variable-3.png)

6. 앱을 미리 보면 위에서 설명한 대로 계산기가 있습니다. 텍스트 상자에서 숫자를 입력하고 **추가** 단추를 몇 번 누릅니다. 준비가 되면 Esc 키를 사용하여 제작 환경으로 돌아갑니다.

    ![텍스트 입력 컨트롤 값을 표시 하 고, 레이블이 누계를 표시 합니다.](media/working-with-variables/context-variable-4.png)

7. 화면을 이동하면서 컨텍스트 변수의 값을 설정할 수 있습니다. 이 경우 한 화면에서 다른 화면으로 "컨텍스트" 또는 "매개 변수"를 전달할 때 유용합니다. 이 방법을 설명 하려면 화면을 삽입 하 고 단추를 삽입 한 다음 **Onselect** 속성을 다음 수식으로 설정 합니다.

    **Navigate( Screen1, None, { RunningTotal: -1000 } )**

    ![단추의 OnSelect 속성](media/working-with-variables/context-variable-5.png)

    Alt 키를 누른 상태에서이 단추를 선택 하 여 **Screen1** 를 표시 하 고 컨텍스트 변수 **RunningTotal** 를-1000로 설정 합니다.

    ![Screen1가 열려 있습니다.](media/working-with-variables/context-variable-6.png)

8. 컨텍스트 변수의 값을 표시 하려면 **파일** 메뉴를 선택 하 고 왼쪽 창에서 **변수** 를 선택 합니다.

    ![파일 메뉴의 변수 옵션](media/working-with-variables/context-variable-file-1.png)

9. 컨텍스트 변수를 정의 하 고 사용 하는 위치를 표시 하려면 해당 변수를 선택 합니다.

    ![변수를 사용 하는 위치 목록](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>컬렉션 사용

마지막으로 컬렉션을 사용하여 계산기를 만드는 방법을 살펴보겠습니다.  컬렉션에는 수정하기 쉬운 테이블이 있으므로 이 계산기에서는 "종이 테이프"의 각 값이 입력되는 대로 유지하게 됩니다.

컬렉션의 작동 방식은 다음과 같습니다.

* **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 함수를 사용하여 컬렉션을 만들고 설정합니다.  **[Collect](functions/function-clear-collect-clearcollect.md)** 함수를 대신 사용할 수 있지만, 실질적으로 이전 변수를 바꾸는 대신 다른 변수가 필요합니다.  
* 컬렉션은 일종의 데이터 원본이며, 따라서 테이블입니다. 컬렉션의 단일 값에 액세스하려면 **[First](functions/function-first-last.md)** 함수를 사용하고 결과 레코드에서 하나의 필드를 추출합니다. **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 에서 단일 값을 사용한 경우 이 예제와 같이 **Value** 필드가 됩니다.<br>
**First(** *VariableName* **).Value**

컬렉션을 사용하여 계산기를 다시 만들어 보겠습니다.

1. **TextInput1**이라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤과 **Button1** 및 **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"** 로 설정하고 **Button2**의 **Text** 속성을 **"지우기"** 로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Collect( PaperTape, TextInput1.Text )**

    이 수식의 존재는 **용지 테이프** 를 텍스트 문자열의 단일 열 테이블을 포함 하는 컬렉션으로 설정 합니다. 이 앱의 어디에서 든 지 **용지 테이프** 를 참조할 수 있습니다. 사용자가이 앱을 열 때마다 **용지 테이프가** 빈 테이블입니다.

    이 수식이 실행 되 면 컬렉션의 끝에 새 값이 추가 됩니다. 단일 값을 추가 하기 때문에 **Collect** 는 단일 열 테이블에 자동으로 배치 하 고, 열 이름은 나중에 사용할 수 있는 **값**입니다.

    ![추가 단추의 OnSelect 속성](media/working-with-variables/papertape-1.png)

4. 사용자가 **지우기** 단추를 선택할 때 용지 테이프를 지우려면 **[onselect](controls/properties-core.md)** 속성을 다음 수식으로 설정 합니다.

    **Clear( PaperTape )**

    ![Clear 단추의 OnSelect 속성](media/working-with-variables/papertape-2.png)

5. 누계를 표시하려면 레이블을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Sum( PaperTape, Value )**

    ![레이블의 텍스트 속성](media/working-with-variables/papertape-3.png)

6. 계산기를 실행하려면 F5 키를 눌러 미리 보기를 열고, 텍스트 입력 컨트롤에 숫자를 입력한 다음, 단추를 선택합니다.

    ![텍스트 입력 컨트롤은 값을 표시 하 고 레이블은 누계를 표시 합니다.](media/working-with-variables/papertape-run-1.png)

7. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.

8. '종이 테이프'를 표시하려면 **데이터 테이블** 컨트롤을 삽입하고, **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **PaperTape**

    오른쪽 창에서 **값** 열을 선택 하 여 표시 합니다.

    ![컬렉션에 추가 된 값을 보여 주는 데이터 테이블](media/working-with-variables/papertape-4.png)

9. 컬렉션의 값을 확인하려면 **파일** 메뉴에서 **컬렉션**을 선택합니다.

    ![용지 테이프 컬렉션의 미리 보기](media/working-with-variables/papertape-file.png)

10. 컬렉션을 저장 하 고 검색 하려면 두 개의 추가 단추 컨트롤을 추가 하 고 해당 **텍스트** 속성을 **로드** 및 **저장**으로 설정 합니다. **로드** 단추의 **onselect** 속성을 다음 수식으로 설정 합니다.

     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**

     **LoadData** 는 저장 된 값을 컬렉션의 끝에 추가 하므로 먼저 컬렉션을 지워야 합니다.

     ![로드 단추의 OnSelect 속성](media/working-with-variables/papertape-5.png)

11. **저장** 단추의 **onselect** 속성을 다음 수식으로 설정 합니다.

     **SaveData( PaperTape, "StoredPaperTape" )**

     ![저장 단추의 OnSelect * 속성](media/working-with-variables/papertape-6.png)

12. F5 키를 눌러 다시 한 번 미리 보고, 텍스트 입력 컨트롤에서 숫자를 입력하고, 단추를 선택합니다. **저장** 단추를 선택합니다. 앱을 닫았다가 다시 로드 하 고 **로드** 단추를 선택 하 여 컬렉션을 다시 로드 합니다.

> [!NOTE]
> **Savedata** 및 **LoadData** 는 power apps Mobile에서 작동 하지만 Power apps Studio 나 PowerApps 용 웹 플레이어에서는 작동 하지 않습니다.