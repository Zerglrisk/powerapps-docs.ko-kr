---
title: "변수 이해 | Microsoft Docs"
description: "상태, 컨텍스트 변수 및 컬렉션 작업에 대한 참조 정보입니다."
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/06/2017
ms.author: gregli
ms.openlocfilehash: eb7bb74362a810487e88efb1177b3c1dfa7a694d
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2018
---
# <a name="understand-variables-in-powerapps"></a>PowerApps 변수에 대한 이해
Visual Basic 또는 JavaScript와 같은 다른 프로그래밍 도구를 사용한 경우 **변수가 어디에 있나요?**라고 물어볼 수 있습니다. PowerApps는 약간 다르며 다른 접근 방식이 필요합니다. 변수에 도달하는 대신 자신에게 **Excel에서 무엇을 할 수 있나요?**라고 물어보세요.

다른 도구에서는 명시적으로 계산을 수행하여 결과를 변수에 저장했습니다. 그러나 PowerApps와 Excel에서는 모두 입력 데이터가 변경될 때 수식을 자동으로 다시 계산하므로 일반적으로 변수를 만들고 업데이트할 필요가 없습니다. 가능한 경우 언제든지 이 방법을 사용하면 앱을 더 쉽게 만들고, 이해하고, 유지 관리할 수 있습니다.

어떤 경우에는 [동작 수식](working-with-formulas-in-depth.md)을 추가하여 Excel 모델을 확장하는 PowerApps에서 변수를 사용해야 합니다. 예를 들어 사용자가 단추를 선택할 때 이러한 수식이 실행됩니다. 종종 동작 수식 내에서 다른 수식에 사용할 변수를 설정하는 것이 유용합니다.

일반적으로 변수를 사용하지 마세요. 그러나 때로는 변수만 사용하여 원하는 환경을 설정할 수 있습니다.

## <a name="translate-excel-into-powerapps"></a>Excel을 PowerApps로 변환
### <a name="excel"></a>Excel
Excel의 작동 원리를 검토해 보겠습니다. 셀에는 숫자 또는 문자열과 같은 값 또는 다른 셀의 값을 기반으로 하는 수식이 포함될 수 있습니다. 사용자가 셀에 다른 값을 입력하면 Excel에서는 새 값에 종속된 모든 수식을 자동으로 다시 계산합니다. 이 동작을 프로그래밍하여 사용하도록 설정할 필요가 없습니다.

![](media/working-with-variables/excel-recalc.png)

Excel에서는 변수를 사용하지 않습니다. 수식이 포함된 셀의 값은 입력에 따라 변경되지만 수식의 결과를 기억하고 셀이나 다른 위치에 저장할 방법이 없습니다. 셀의 값을 변경하면 전체 스프레드시트가 변경되고 이전에 계산된 값이 손실될 수 있습니다.  Excel 사용자는 셀을 복사하여 붙여넣을 수 있고 직접 제어할 수 있지만, 수식으로는 가능하지 않습니다.

### <a name="powerapps"></a>PowerApps
PowerApps에서 만드는 앱은 Excel과 매우 비슷하게 작동합니다. 셀을 업데이트하는 대신 화면에 원하는 위치에 컨트롤을 추가하고 수식에 사용할 컨트롤의 이름을 지정할 수 있습니다.

예를 들어**TextBox1**이라는 **[레이블](controls/control-text-box.md)** 컨트롤과 **TextInput1** 및 **TextInput2**라는 2개의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하여 앱에서 Excel 동작을 복제할 수 있습니다. 그런 다음 **TextBox1**의 **[Text](controls/properties-core.md)** 속성을 **TextInput1 + TextInput2**로 설정하면 항상 **TextInput1** 및 **TextInput2**에 있는 숫자의 합계를 자동으로 표시합니다.

![](media/working-with-variables/recalc1.png)

**TextBox1** 컨트롤을 선택하면 화면 위쪽의 수식 입력줄에서 **[Text](controls/properties-core.md)** 수식이 표시됩니다.  여기서 **TextInput1 + TextInput2** 수식을 찾습니다.  이 수식은 Excel 통합 문서에서 셀 간에 종속성을 만든 것처럼 이러한 컨트롤 간에 종속성을 만듭니다.  **TextInput1**의 값을 변경해 보겠습니다.

![](media/working-with-variables/recalc2.png)

**TextBox1**에 대한 수식이 자동으로 다시 계산되어 새 값이 표시됩니다.

PowerApps에서 수식을 사용하여 컨트롤의 기본값뿐만 아니라 서식과 같은 속성도 결정할 수 있습니다. 다음 예제에서 레이블의 **[Color](controls/properties-color-border.md)** 속성에 대한 수식은 자동으로 음수 값을 빨간색으로 표시합니다. **[If](functions/function-if.md)** 함수는 Excel과 매우 친숙해야 합니다.
<br>**If( Value(TextBox1.Text) < 0, Red, Black )**

![](media/working-with-variables/recalc-color1.png)

이제 **TextBox1.Text**의 계산 결과가 음수이면 숫자가 빨간색으로 표시됩니다.

![](media/working-with-variables/recalc-color2.png)

다음과 같은 다양한 시나리오에 수식을 사용할 수 있습니다.

* 장치의 GPS를 사용하면 지도 컨트롤에서 **Location.Latitude** 및 **Location.Longitude**를 사용하는 수식으로 현재 위치를 표시할 수 있습니다.  이동하는 대로 지도에서 내 위치를 자동으로 추적합니다.
* 다른 사용자가 [데이터 원본](working-with-data-sources.md)을 업데이트할 수 있습니다.  예를 들어 팀의 다른 구성원이 SharePoint 목록의 항목을 업데이트할 수 있습니다.  데이터 원본을 새로 고치면 종속된 모든 수식이 업데이트된 데이터를 반영하도록 자동으로 다시 계산됩니다. 예를 들어 **Filter( SharePointList )** 수식에 갤러리의 **[Items](controls/properties-core.md)** 속성을 설정하여 새로 필터링된 [레코드](working-with-tables.md#records) 집합을 자동으로 표시할 수 있습니다.

### <a name="benefits"></a>혜택
수식을 사용하여 앱을 빌드하면 다음과 같은 많은 이점이 있습니다.

* Excel을 알고 있으면 PowerApps도 알 수 있습니다. 모델과 수식 언어가 동일하기 때문입니다.
* 다른 프로그래밍 도구를 사용했으면 이러한 예제를 수행하는 데 필요한 코드의 양을 생각하면 됩니다.  Visual Basic에서는 각 텍스트 입력 컨트롤에 변경 이벤트에 대한 이벤트 처리기를 작성해야 합니다.  이러한 컨트롤 각각에서 계산을 수행하는 코드가 중복되고 동기화되지 못하거나 일반적인 서브루틴을 작성해야 합니다.  PowerApps에서는 단 한 줄의 수식으로 이러한 모든 작업을 수행합니다.
* **TextBox1**의 텍스트가 제공되는 위치를 이해하려면 찾으려는 위치, 즉 **[Text](controls/properties-core.md)** 속성의 수식을 정확히 알아야 합니다.  이 컨트롤의 텍스트에 영향을 줄 수 있는 다른 방법은 없습니다.  기존의 프로그래밍 도구에서 모든 이벤트 처리기 또는 서브루틴은 프로그램의 모든 위치에서 레이블의 값을 변경할 수 있습니다.  이로 인해 변수가 언제 어디서 변경되었는지 추적하기가 어려워질 수 있습니다.
* 사용자가 슬라이더 컨트롤을 변경한 다음 생각을 바꾸면 슬라이더를 원래 값으로 다시 변경할 수 있습니다.  그러면 마치 아무 것도 변경되지 않은 것처럼 됩니다. 즉 앱에서 이전과 동일한 컨트롤 값을 표시합니다.  Excel에서 아무 효과가 없는 것처럼 "what if"를 실험하고 요청하는 것에 대해 아무 효과가 없습니다.  

일반적으로 수식을 사용하여 결과를 얻을 수 있는 경우가 더 효과적입니다. PowerApps에서 수식 엔진을 사용하여 작업해 보겠습니다.  

## <a name="know-when-to-use-variables"></a>변수를 사용하는 경우 확인
구식의 계산기처럼 작동하도록 단순한 가산기를 누계로 변경해 보겠습니다. **추가** 단추를 선택하는 경우 누계에 숫자를 추가합니다. **지우기** 단추를 선택하는 경우 누계를 0으로 다시 설정합니다.

![](media/working-with-variables/button-changes-state.png)

계산기는 Excel에 존재하지 않는 단추를 사용합니다. 이 앱에서는 사용자가 수행하는 일련의 작업에 따라 값이 달라지므로 수식만으로는 누계를 계산할 수 없습니다. 대신 누계를 수동으로 기록하고 업데이트해야 합니다. 대부분의 프로그래밍 도구에서는 이 정보를 *변수*에 저장합니다.    

앱이 원하는 방식으로 작동하도록 변수가 필요할 수도 있습니다.  그러나 이 방법에는 다음과 같은 주의 사항이 있습니다.

* 누계를 수동으로 업데이트해야 합니다. 자동 다시 계산을 수행하지 않습니다.
* 누계는 더 이상 다른 컨트롤의 값을 기준으로 계산되지 않습니다. 사용자가 **추가** 단추를 선택한 횟수와 매번 텍스트 입력 컨트롤에 있던 값에 따라 누계가 달라집니다. 사용자가 77을 입력하고 **추가**를 두 번 추가했나요? 아니면 각 추가에 대해 24와 130을 지정했나요? 합계가 154에 도달한 후에는 그 차이를 알 수 없습니다.
* 합계에 대한 변경은 다른 경로에서 제공될 수 있습니다. 이 예제에서는 **추가** 및 **지우기** 단추 모두에서 합계를 업데이트할 수 있습니다. 앱이 예상대로 작동하지 않으면 문제의 원인이 되는 단추는 무엇일까요?

## <a name="create-a-global-variable"></a>전역 변수 만들기
계산기를 만들려면 누계를 보유할 변수가 필요합니다. PowerApps에서 사용할 가장 간단한 변수는 *전역 변수*입니다.  

전역 변수의 작동 방식은 다음과 같습니다.

* **[Set](functions/function-set.md)** 함수를 사용하여 전역 변수의 값을 설정합니다.  **Set( MyVar, 1 )**은 **MyVar** 전역 변수를 **1**의 값으로 설정합니다.
* **Set** 함수와 함께 사용할 이름을 참조하여 전역 변수를 사용합니다.  이 경우 **MyVar**는 **1**을 반환합니다.
* 전역 변수에는 문자열, 숫자, 레코드 및 [테이블](working-with-tables.md)을 포함한 모든 값이 포함될 수 있습니다.

전역 변수를 사용하여 계산기를 다시 빌드해 보겠습니다.

1. **TextInput1**이라는 텍스트 입력 컨트롤과 **Button1** 및  **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"**로 설정하고, **Button2**의 **Text** 속성을**"지우기"**로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **Set( RunningTotal, RunningTotal + Text1 )**
   
    사용자가 처음으로 **추가** 단추를 선택하고 **[Set](functions/function-set.md)**이 호출되면 **RunningTotal**이 기본값인 '공백'으로 만들어집니다.  또한 이는 0으로 처리됩니다.
   
    ![](media/working-with-variables/global-variable-1.png)
4. 사용자가 **지우기** 단추를 선택할 때마다 누계를 **0**으로 설정하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **Set( RunningTotal, 0 )**
   
    ![](media/working-with-variables/global-variable-2.png)
5. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고 **[Text](controls/properties-core.md)** 속성을 **RunningTotal**로 설정합니다.
   
    이 수식은 자동으로 다시 계산되며, 사용자가 선택하는 단추에 따라 변경될 때 사용자에게 **RunningTotal** 값을 표시합니다.
   
    ![](media/working-with-variables/global-variable-3.png)
6. 앱을 미리 보면 위에서 설명한 대로 계산기가 있습니다.  텍스트 상자에서 숫자를 입력하고 **추가** 단추를 몇 번 누릅니다.  준비가 되면 Esc 키를 사용하여 제작 환경으로 돌아갑니다.  
   
    ![](media/working-with-variables/global-variable-4.png)
7. 전역 변수의 값을 확인하려면 **파일** 메뉴를 선택하고 왼쪽 창에서 **변수**를 선택합니다.
   
    ![](media/working-with-variables/global-variable-file-1.png)
8. 변수가 정의되고 사용되는 모든 위치를 보려면 해당 변수를 선택합니다.
   
    ![](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>변수 유형
PowerApps에는 다음과 같은 세 가지 유형의 변수가 있습니다.

| 변수 유형 | 범위 | 설명 | Functions |
| --- | --- | --- | --- |
| 전역 변수 |앱 |사용이 가장 간편합니다.  앱의 모든 위치에서 참조할 수 있는 숫자, 텍스트 문자열, 부울, 레코드, 테이블 등을 보유합니다. |[**Set**](functions/function-set.md) |
| 컨텍스트 변수 |화면 |다른 언어의 프로시저에 대한 매개 변수와 마찬가지로 화면에 값을 전달하는 데 매우 유용합니다.  한 화면에서만 참조할 수 있습니다. |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navigate**](functions/function-navigate.md) |
| 컬렉션 |앱 |앱의 모든 위치에서 참조할 수 있는 테이블을 보유합니다.  테이블의 내용을 전체적으로 설정하지 않고 수정할 수 있습니다. 나중에 사용하기 위해 로컬 장치에 저장할 수 있습니다. |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md)<br>[**Patch**](functions/function-patch.md)<br>[**Update**](functions/function-update-updateif.md)<br>[**Remove**](functions/function-remove-removeif.md)<br>[**SaveData**](functions/function-savedata-loaddata.md)<br>[**LoadData**](functions/function-savedata-loaddata.md)<br>등 |

**Set**, **UpdateContext**, **Navigate** 또는 **Collect** 함수를 사용할 때 모든 변수가 암시적으로 만들어집니다.  다른 프로그래밍 도구에서 수행되는 것과 같이 변수에 대한 명시적 선언이 없습니다.  또한 변수 유형은 변수에 배치된 값에서 암시적으로 파생됩니다.

모든 변수는 앱이 실행되는 동안 메모리에서 유지됩니다.  앱을 닫으면 변수에 보유된 값이 손실됩니다.  **Patch** 또는 **Collect** 함수를 사용하여 데이터 원본에 변수의 내용을 저장하거나, 컬렉션의 경우 **SaveData** 함수를 사용하여 로컬 장치에 저장할 수 있습니다.  앱을 처음 로드하는 경우 모든 변수에 '공백' 값이 있습니다.

변수 이름을 사용하여 해당 값을 읽습니다.  예를 들어 **Set( MyColor, Red )**로 정의된 경우 색상 값을 사용할 수 있는 곳이면 어디서든 **MyVar**를 간단히 사용할 수 있으며 **Red**로 바뀝니다.  컨텍스트 변수와 이름이 같은 전역 변수 또는 컬렉션을 사용할 수 있습니다.  이 경우 컨텍스트 변수가 우선 적용됩니다.  **@[MyColor]** [명확성 연산자](functions/operators.md#disambiguation-operator)를 사용하여 전역 변수 또는 컬렉션을 계속 참조할 수 있습니다.

## <a name="create-a-context-variable"></a>컨텍스트 변수 만들기
전역 변수 대신 컨텍스트 변수를 사용하여 계산기를 만드는 방법을 살펴보겠습니다.    

컨텍스트 변수의 작동 방식은 다음과 같습니다.

* **[UpdateContext](functions/function-updatecontext.md)** 함수를 사용하여 컨텍스트 변수를 만들고 설정합니다.  컨텍스트 변수가 처음 업데이트될 때 아직 존재하지 않으면 기본값인 '공백'으로 만들어집니다.
* 컨텍스트 변수를 만들고 레코드로 업데이트합니다. 다른 프로그래밍 도구에서는 일반적으로 "x = 1"에서와 같이 할당에 "="를 사용합니다.  컨텍스트 변수의 경우 **{ x: 1 }**을 대신 사용합니다. 컨텍스트 변수를 사용하는 경우 해당 이름을 직접 사용합니다.  
* **[Navigate](functions/function-navigate.md)** 함수를 사용하여 화면이 표시될 때 컨텍스트 변수를 설정할 수도 있습니다. 화면이 일종의 프로시저 또는 서브루틴으로 간주되면 다른 프로그래밍 도구에서 전달하는 매개 변수와 비슷합니다.
* **[Navigate](functions/function-navigate.md)**를 제외하고 컨텍스트 변수는 단일 화면의 컨텍스트로 제한되며, 여기에서 컨텍스트 변수의 이름을 얻습니다.  이 컨텍스트 외부에서는 사용하거나 설정할 수 없습니다.
* 컨텍스트 변수에는 문자열, 숫자, 레코드 및 [테이블](working-with-tables.md)을 포함한 모든 값이 포함될 수 있습니다.

컨텍스트 변수를 사용하여 계산기를 다시 빌드해 보겠습니다.

1. **TextInput1**이라는 텍스트 입력 컨트롤과 **Button1** 및  **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"**로 설정하고, **Button2**의 **Text** 속성을**"지우기"**로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **UpdateContext( { RunningTotal: RunningTotal + Text1 } )**
   
    사용자가 처음으로 **추가** 단추를 선택하고 **[UpdateContext](functions/function-updatecontext.md)**가 호출되면 **RunningTotal**이 기본값인 '공백'으로 만들어집니다 .  또한 이는 0으로 처리됩니다.
   
    ![](media/working-with-variables/context-variable-1.png)
4. 사용자가 **지우기** 단추를 선택할 때마다 누계를 **0**으로 설정하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **UpdateContext( { RunningTotal: 0 } )**
   
    다시 말하지만 **[UpdateContext](functions/function-updatecontext.md)**는 **UpdateContext( { RunningTotal: 0 } )** 수식과 함께 사용됩니다.
   
    ![](media/working-with-variables/context-variable-2.png)
5. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고 **[Text](controls/properties-core.md)** 속성을 **RunningTotal**로 설정합니다.
   
    이 수식은 자동으로 다시 계산되며, 사용자가 선택하는 단추에 따라 변경될 때 사용자에게 **RunningTotal** 값을 표시합니다.
   
    ![](media/working-with-variables/context-variable-3.png)
6. 앱을 미리 보면 위에서 설명한 대로 계산기가 있습니다.  텍스트 상자에서 숫자를 입력하고 **추가** 단추를 몇 번 누릅니다.  준비가 되면 Esc 키를 사용하여 제작 환경으로 돌아갑니다.  
   
    ![](media/working-with-variables/context-variable-4.png)
7. 화면을 이동하면서 컨텍스트 변수의 값을 설정할 수 있습니다.  이 경우 한 화면에서 다른 화면으로 "컨텍스트" 또는 "매개 변수"를 전달할 때 유용합니다.  이를 확인하려면 새 화면을 삽입하고 **OnSelect** 속성이 다음과 같이 설정된 단추를 삽입합니다.
   
    **Navigate( Screen1, None, { RunningTotal: -1000 } )**
   
    ![](media/working-with-variables/context-variable-5.png)
   
    **Screen2**에서 이 단추를 선택하면(끝 방향으로 단추를 선택하면 제작 중에 수행할 수 있음), **Screen1**이 표시되고 **RunningTotal** 컨텍스트 변수도 -1000으로 설정됩니다.
   
    ![](media/working-with-variables/context-variable-6.png)
8. 컨텍스트 변수의 값을 확인하려면 **파일** 메뉴를 선택하고 왼쪽 창에서 **변수**를 선택합니다.
   
    ![](media/working-with-variables/context-variable-file-1.png)
9. 컨텍스트 변수가 정의되고 사용되는 위치를 보려면 해당 컨텍스트 변수를 선택합니다.
   
    ![](media/working-with-variables/context-variable-file-2.png)

## <a name="create-a-collection"></a>컬렉션 만들기
마지막으로 컬렉션을 사용하여 계산기를 만드는 방법을 살펴보겠습니다.  컬렉션에는 수정하기 쉬운 테이블이 있으므로 이 계산기에서는 "종이 테이프"의 각 값이 입력되는 대로 유지하게 됩니다.

컬렉션의 작동 방식은 다음과 같습니다.

* **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 함수를 사용하여 컬렉션을 만들고 설정합니다.  **[Collect](functions/function-clear-collect-clearcollect.md)** 함수를 대신 사용할 수 있지만, 실질적으로 이전 변수를 바꾸는 대신 다른 변수가 필요합니다.  
* 컬렉션은 일종의 데이터 원본이며, 따라서 테이블입니다. 컬렉션의 단일 값에 액세스하려면 **[First](functions/function-first-last.md)** 함수를 사용하고 결과 레코드에서 하나의 필드를 추출합니다. **[ClearCollect](functions/function-clear-collect-clearcollect.md)**에서 단일 값을 사용한 경우 이 예제와 같이 **Value** 필드가 됩니다.<br>**First(** *VariableName* **).Value**

컬렉션을 사용하여 계산기를 다시 만들어 보겠습니다.

1. **TextInput1**이라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤과 **Button1** 및 **Button2**라는 두 개의 단추를 추가합니다.

2. **Button1**의 **[Text](controls/properties-core.md)** 속성을 **"추가"**로 설정하고 **Button2**의 **Text** 속성을 **"지우기"**로 설정합니다.

3. 사용자가 **추가** 단추를 선택할 때마다 누계를 업데이트하려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **Collect( PaperTape, TextInput1.Text )**
   
    이 수식은 컬렉션의 끝에 새 값을 추가합니다.  하나의 값을 추가하므로 **Collect**는 나중에 사용할 **값**이라는 열 이름이 있는 단일 열 테이블에 자동으로 배치됩니다.
   
    ![](media/working-with-variables/papertape-1.png)
4. 사용자가 **지우기** 단추를 선택할 때 '종이 테이프'를 지우려면 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다:
   
    **Clear( PaperTape )**
   
    ![](media/working-with-variables/papertape-2.png)
5. 누계를 표시하려면 레이블을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **Sum( PaperTape, Value )**
   
    ![](media/working-with-variables/papertape-3.png)
6. 계산기를 실행하려면 F5 키를 눌러 미리 보기를 열고, 텍스트 입력 컨트롤에 숫자를 입력한 다음, 단추를 선택합니다.
   
    ![](media/working-with-variables/papertape-run-1.png)
7. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
8. '종이 테이프'를 표시하려면 **데이터 테이블** 컨트롤을 삽입하고, **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **PaperTape**
   
    오른쪽 창에서 표시할 열도 선택해야 합니다. 이 경우 **값** 열이 표시됩니다.
   
    ![](media/working-with-variables/papertape-4.png)
9. 컬렉션의 값을 확인하려면 **파일** 메뉴에서 **컬렉션**을 선택합니다.
   
    ![](media/working-with-variables/papertape-file.png)
10. 컬렉션을 저장하고 검색하려면 두 개의 단추 컨트롤을 더 추가하고 해당 텍스트를 **로드** 및 **저장**으로 설정합니다.  **로드**의 경우 **OnSelect** 속성을 다음과 같이 설정합니다.
    
     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**
    
     **LoadData**는 저장된 값을 컬렉션의 끝에 추가하므로 먼저 컬렉션을 지워야 합니다.
    
     ![](media/working-with-variables/papertape-5.png)
11. **저장**의 경우 **OnSelect** 속성을 다음과 같이 설정합니다.
    
     **SaveData( PaperTape, "StoredPaperTape" )**
    
     ![](media/working-with-variables/papertape-6.png)
12. F5 키를 눌러 다시 한 번 미리 보고, 텍스트 입력 컨트롤에서 숫자를 입력하고, 단추를 선택합니다.  **저장** 단추를 선택합니다.  앱을 닫고 다시 로드하고, **로드** 단추를 선택하여 컬렉션을 다시 로드합니다.  
    
    > [!NOTE]
    > **SaveData** 및 **LoadData**는 웹 브라우저에서 실행 시 작동하지 않습니다. Windows에 설치된 스튜디오 또는 모바일 장치용 플레이어 중 하나를 사용해야 합니다.  

