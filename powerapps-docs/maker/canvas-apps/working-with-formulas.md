---
title: 캔버스 앱에서 수식 시작 | Microsoft Docs
description: PowerApps에서 수식을 사용하여 캔버스 앱을 사용자 지정합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 715f82a1db2c8a4bb495e41b45a3911182024158
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541625"
---
# <a name="get-started-with-canvas-app-formulas-in-powerapps"></a>PowerApps에서 캔버스 앱 수식 시작

Excel에서 작업하는 것처럼 값을 계산하고 다른 작업을 수행하는 것 외에도 캔버스 앱에서 요구하는 사용자의 입력 값에 응답하는 등 수식을 사용하여 앱을 구성할 수 있습니다.

* Excel의 경우 셀을 채우고 표와 차트를 작성하는 등에 대한 수식을 작성합니다.
* PowerApps의 경우 셀 대신 컨트롤을 구성하는 것과 같은 수식을 작성합니다. 또한 스프레드시트 대신 앱에만 적용되는 수식을 작성합니다.

예를 들어, 사용자가 단추를 선택하거나, 슬라이더를 조정하거나, 다른 입력 값을 제공할 때 앱이 응답하는 방식을 결정하기 위한 수식을 작성합니다. 이러한 수식으로 다른 화면을 표시하거나 앱 외부의 데이터 원본을 앱에 업데이트하거나, 기존 표에 있는 데이터의 하위 집합을 포함하는 표를 만들 수 있습니다.

다양한 시나리오에 대한 수식을 사용할 수 있습니다. 예를 들어 현재 위치를 표시하려면 GPS 디바이스, 지도 컨트롤, 및 **위치.위도**와 **위치.경도**를 사용하는 수식을 사용할 수 있습니다. 지도는 사용자가 이동하는 대로 위치를 자동으로 추적합니다.

이 토픽에서는 수식 작업의 개요만을 다룹니다. 사용 가능한 함수, 연산자 및 기타 구성 요소에 대한 자세한 내용과 전체 목록은 [수식 참조](formula-reference.md)를 확인하세요.

## <a name="prerequisites"></a>필수 조건

* PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 입력하여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
* PowerApps에서 [컨트롤 구성](add-configure-controls.md)을 어떻게 하는지 알아봅니다.

## <a name="show-a-simple-value"></a>간단한 값 표시

Excel의 경우 숫자 **42**나 문구 **Hello World**와 같이 같단한 특정 데이터를 셀에 입력할 수 있습니다. 해당 셀은 사용자가 입력한 대로 해당 데이터를 항상 표시합니다. PowerApps의 경우 레이블의 **[텍스트](controls/properties-core.md)** 속성을 큰따옴표로 묶인 정확한 문자 시퀀스로 설정하여 데이터의 일부가 변경되지 않도록 지정할 수 있습니다.

1. (화면의 왼쪽 가장자리에 있는) **파일** 메뉴에서 **새로 만들기**를 선택합니다.
2. **앱 만들기** 아래에서 **새 앱** 타일에 있는 **휴대폰 레이아웃**을 선택합니다.

    수식 입력줄이 화면 맨 위에 나타납니다.

    ![수식 입력줄](./media/working-with-formulas/formula-bar.png)

    이 입력줄은 다음 두 부분으로 구성됩니다.

   * *속성 목록*: 각 컨트롤과 화면에는 [속성 집합](reference-properties.md)이 있습니다.  이 목록을 사용하여 특정 속성을 선택합니다.  
   * *수식*: 수식은 이 속성에 따라 계산되며 [값, 연산자 및 함수](formula-reference.md)로 구성됩니다.

     수식 입력줄에서는 선택한 컨트롤이 없다면 선택한 컨트롤 또는 화면에 대한 속성을 확인하고 편집할 수 있습니다.  **콘텐츠** 탭에서 선택한 컨트롤의 이름을 볼 수 있습니다.

     ![콘텐츠 막대에 현재 선택된 컨트롤이 표시됩니다.](./media/working-with-formulas/content-tab-selection.png)

     **콘텐츠** 탭에서 이름을 클릭하여 선택한 컨트롤의 이름을 변경할 수 있습니다.
3. 화면에 **[레이블](controls/control-text-box.md)** 컨트롤을 추가합니다.

    ![텍스트 상자 컨트롤이 추가됩니다.](./media/working-with-formulas/add-a-label.png)

    레이블을 추가하면 속성 목록에 컨트롤이 표시하는 항목을 구동하는 **[Text](controls/properties-core.md)** 속성이 자동으로 표시됩니다. 기본적으로 이 속성의 값은 **"텍스트"** 입니다.  
4. 수식 입력줄에 이중 따옴표로 묶은 문자열을 입력하여 **[텍스트](controls/properties-core.md)** 속성 값을 **"Hello World"** 로 설정합니다.

    !["Hello World" 레이블 사용](./media/working-with-formulas/label-hello-world.png)

    입력하는 대로 새 값이 레이블에 바로 반영됩니다.  입력하는 동안 노란색 느낌표 아이콘이 화면에 나타날 수 있습니다. 이 아이콘은 입력한 값에 오류가 있음을 나타내며, 유효한 값이 입력되면 바로 사라집니다. 예를 들어, 양쪽에 큰따옴표가 없는 문자열은 유효하지가 않습니다.

    Excel의 경우 해당 숫자를 셀에 입력하거나 **=SUM(30,12)** 와 같이 해당 숫자가 나오는 수식을 입력하여 **42**와 같은 숫자를 표시할 수 있습니다. PowerApps에서는 레이블과 같은 컨트롤의 **Text** 속성을 **42** 또는 **Sum(30,12)** 에 설정하여 동일한 효과를 얻을 수 있습니다. 셀과 레이블은 워크시트 또는 앱의 변경에 관계 없이 항상 해당 숫자를 표시합니다.

    > [!NOTE]
   > PowerApps의 경우도 Excel에서와 마찬가지로 등호 또는 더하기 기호가 있는 수식은 앞에 오지 않아야 합니다. 수식 입력줄은 입력하는 모든 내용은 기본적으로 수식으로 간주합니다. 또한 텍스트 문자열을 지정할 때 이전과 마찬가지로 큰따옴표(")로 수식을 묶지 않아야 합니다.
5. 레이블의 **[Text](controls/properties-core.md)** 속성에서 **"Hello World"** 를 **Sum(1,2,3)** 으로 바꿉니다.

    ![닫는 괄호 없이 부분 함수 Sum(1,2,3을 입력하여 오류가 나타나는 경우](./media/working-with-formulas/label-sum-partial.png)

    사용자가 입력하는 동안 수식 입력줄은 이 함수에 필요한 설명과 예상되는 인수를 표시합니다.  **"Hello World"** 의 오른쪽 큰따옴표와 마찬가지로, 화면은 이 식의 오른쪽 괄호를 입력할 때까지 오류를 나타내는 노란색 느낌표를 표시합니다.

    ![완전한 수식 Sum(1,2,3) 사용](./media/working-with-formulas/label-sum.png)

## <a name="change-a-value-based-on-input"></a>입력에 따라 값 변경

Excel에서는 **= a1 + a2** 를 셀에 입력 하 여 **a1** 및 **a2** 셀에 포함 된 모든 값의 합계를 표시 합니다. 하나 또는 모든 셀의 값을 변경하면 수식이 포함된 셀은 업데이트된 결과를 자동으로 보여줍니다.

![Excel 애니메이션은 두 숫자의 합계를 계산 합니다.](./media/working-with-formulas/excel-recalc.gif)

PowerApps에서 화면에 컨트롤을 추가 하 고 속성을 설정 하 여 비슷한 결과를 얻을 수 있습니다. 이 예제에서는 **TextInput1** 및 **TextInput2**라는 두 개의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤과 **Label1** 이라는 레이블 컨트롤을 보여 줍니다.

![두 숫자의 합계를 계산 하는 PowerApps의 그림](./media/working-with-formulas/recalc1.png)

텍스트 입력 컨트롤에 어떤 숫자를 입력하든 **[Text](controls/properties-core.md)** 속성이 다음 수식으로 설정되어 있으므로 레이블에는 항상 해당 숫자의 합이 표시됩니다.

`TextInput1 + TextInput2`

![PowerApps 애니메이션 두 숫자의 합계를 계산 합니다.](./media/working-with-formulas/recalc2.gif)

Excel에서는 조건부 서식 수식을 사용 하 여 빨간색의 음수 값을 표시할 수 있습니다. PowerApps에서 수식을 사용하여 컨트롤의 기본값뿐만 아니라 서식과 같은 속성도 결정할 수 있습니다. 다음 예제에서는 레이블의 **[Color](controls/properties-color-border.md)** 속성에 대 한 수식이 자동으로 음수 값을 빨간색으로 표시 합니다. **[If](functions/function-if.md)** 함수는 Excel과 매우 친숙해야 합니다.

`If( Value(Label1.Text) < 0, Red, Black )`

![조건부 서식 지정 애니메이션](media/working-with-variables/recalc-color.gif)

## <a name="change-a-color-based-on-user-input"></a>입력하는 사용자에 따라 색상 변경

수식이 포함된 앱을 구성하면 사용자는 앱의 모양이나 동작을 변경할 수 있게 됩니다. 예를 들어, 사용자가 지정한 텍스트 문자열이 포함된 데이터만 표시하는 필터를 만들거나, 데이터 집합에 있는 특정 열을 기준으로 데이터의 집합을 정렬하도록 할 수 있습니다. 이러한 절차로 사용자는 하나 이상의 슬라이더를 조정하여 화면의 색상을 변경할 수 있게 됩니다.

1. 이전 절차에서 만든 컨트롤을 제거하거나 이전에 수행한 것처럼 새 앱을 만들고, 3개의 슬라이더 컨트롤을 추가합니다.

    ![슬라이더 컨트롤 삽입](./media/working-with-formulas/insert-slider.png)
2. 슬라이더가 겹치지 않도록 정렬하고, 3개의 레이블을 추가한 다음 **빨간색**, **녹색**, **파란색**으로 표시되도록 구성합니다.

    ![슬라이더 정렬 후 각 색상의 구성 요소에 대한 레이블 추가](./media/working-with-formulas/three-sliders.png)
3. 각 슬라이더의 **최대** 속성 값을 **[RGBA](functions/function-colors.md)** 함수에 대한 색상 구성 요소의 최대 값인 255로 설정합니다.

    **콘텐츠** 탭 또는 속성 목록에서 **최대** 속성 값을 선택하여 지정할 수 있습니다.

    ![각 슬라이더의 최대 값 변경](./media/working-with-formulas/three-sliders-max.png)
4. 모든 컨트롤에서 클릭하여 화면을 선택한 후 다음 수식으로 화면의 **[채우기](controls/properties-color-border.md)** 속성을 설정합니다.<br>**RGBA( Slider1.Value, Slider2.Value, Slider3.Value, 1 )**

    앞서 설명한 대로 **.** 연산자를 사용하여 컨트롤 속성에 액세스합니다.  **Slider1.Value**는 **최소** 값과 **최대** 값 사이에 사용자가 슬라이더를 배치하도록 반영한 값인 슬라이더의 **[값](controls/properties-core.md)** 속성을 의미합니다. 이 수식을 입력하면서 포함된 각 컨트롤은 화면과 수식 입력줄 사이에서 색상이 코딩됩니다.

    ![화면의 배경 채우기 색상에 대한 수식을 미완료 상태로 변경](./media/working-with-formulas/three-sliders-partial-rgba.png)

    닫는 괄호를 입력하면 화면의 배경은 각 슬라이더의 기본값이 **50**인 진한 회색으로 변경됩니다. 이는 수식 입력이 끝날 때 배경 채우기 색상 값으로 계산되어 사용됩니다. 기본 작업 영역에 있는 동안 미리 보기를 열지 않고도 앱과 상호 작용할 수 있습니다.

    ![각 슬라이더의 최대 값 변경](./media/working-with-formulas/three-sliders-complete-rgba.png)
5. 슬라이더를 조정하고, 변경 내용이 배경 색상에 어떻게 영향을 주는지 확인합니다.

    각 슬라이더가 변경되면 **[RGBA](functions/function-colors.md)** 함수가 포함된 수식이 다시 계산되면서 화면의 표시 방식을 바로 변경합니다.

    ![화면의 배경 채우기 색상에 대한 수식을 완료 상태로 변경](./media/working-with-formulas/color-sliders.gif)

## <a name="manage-app-behavior"></a>앱 동작 관리

수식을 사용하여 계산을 수행하고 모양을 변경하며 작업을 수행할 수 있습니다. 예를 들어, **[OnSelect](controls/properties-core.md)** 속성 단추에 **[Navigate](functions/function-navigate.md)** 함수가 포함된 수식을 설정할 수 있습니다. 사용자가 해당 단추를 선택할 경우 해당 수식에서 사용자가 지정한 화면이 나타납니다.

**[Navigate](functions/function-navigate.md)** 및 **[Collect](functions/function-clear-collect-clearcollect.md)** 와 같은 일부 함수는 동작 수식에서만 사용할 수 있습니다.  이 컨텍스트에 한해 함수를 사용할 경우 수식 참조가 호출됩니다.  

세미콜론(;)으로 함수를 분리하면 동작 수식에서 하나 이상의 작업을 수행할 수 있습니다. 예를 들어, 컨텍스트 변수를 업데이트하여 데이터를 데이터 원본으로 푸시하고 마지막으로 다른 화면으로 이동할 수 있습니다.

## <a name="view-a-list-of-properties-by-category"></a>범주별로 속성 목록 보기

속성 목록의 속성은 사전순으로 표시되지만 **보기** 탭에서 **고급** 옵션을 선택하면 컨트롤의 모든 속성을 범주별로 볼 수 있습니다.

![고급 보기](./media/working-with-formulas/advanced-open.png)

이 보기 내에서 수식을 직접 편집할 수 있습니다.  창 맨 위에 있는 컨트롤 선택기를 사용하여 해당 컨트롤과 함께 작업할 컨트롤을 빠르게 찾을 수 있습니다.  또한 속성 검색을 사용하여 해당 컨트롤의 속성을 빠르게 찾을 수 있습니다.

이 보기는 처음에 가장 중요한 속성을 표시합니다.  모든 속성을 표시하려면 창 아래쪽에 있는 아래쪽 화살표를 클릭합니다.  각 컨트롤에는 해당 컨트롤의 동작과 모양의 모든 측면을 컨트롤하는 속성의 긴 목록이 있습니다. 여기에서 해당 목록 전체를 스크롤하거나, 창 위쪽 입력란에 속성을 입력하여 검색할 수 있습니다.

## <a name="formula-syntax"></a>수식 구문

수식 입력줄에 수식을 입력할 때 서로 다른 구문 요소는 가독성을 높여주고 긴 수식을 쉽게 이해할 수 있도록 여러 색으로 나타납니다. 다음은 PowerApps의 색 코드 목록입니다.

![구문 강조 표시](./media/working-with-formulas/syntax-highlighting.png)