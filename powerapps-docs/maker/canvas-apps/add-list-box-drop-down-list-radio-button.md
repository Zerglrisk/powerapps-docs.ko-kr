---
title: 캔버스 앱에 목록 상자, 드롭다운 목록 또는 라디오 단추 추가 | Microsoft Docs
description: Power Apps에서 캔버스 앱의 다중 선택 옵션을 만들거나 구성 합니다.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9bf03693a182a9c6f85ad43c431b10fabf21b48d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678951"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>캔버스 앱에 목록 상자, 드롭다운 목록 또는 라디오 단추 추가

사용자가 목록에서 하나 이상의 항목을 선택할 수 있도록 캔버스 앱에 단일 데이터 열(예: 다중 열 테이블에 포함됨)을 표시합니다.

- 사용자가 둘 이상의 옵션을 선택할 수 있는 목록 상자를 추가합니다.
- 화면에서 공간을 적게 차지하는 드롭다운 목록을 추가합니다.
- 특정 디자인 효과를 위해 라디오 단추 집합을 추가합니다.

이 항목에서는 목록 상자 및 라디오 단추에 초점을 맞추지만 동일한 원칙이 드롭다운 목록에 적용됩니다.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>간단한 목록 만들기

1. **MyListBox**라는 **목록 상자** 컨트롤을 추가하고 해당 **Items** 속성을 다음 식으로 설정합니다.

    ```["circle","triangle","rectangle"]```  <br/>

    디자이너가 다음과 유사하게 표시됩니다.

    ![][4]

4. **삽입** 탭에서 **아이콘**을 선택하고, 원을 선택하고, **MyListBox** 아래로 이동합니다.

    ![][5]  

5. 삼각형 및 사각형을 추가한 다음, **MyListBox** 아래의 행에 셰이프를 정렬합니다.

    ![][6]  

6. 다음 셰이프의 **[Visible](controls/properties-core.md)** 속성을 다음 함수로 설정합니다.  

   | 셰이프 | Visible 함수 설정 대상 |
   | --- | --- |
   | 원 |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | 삼각형 |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | 사각형 |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Alt 키를 누른 상태로 **MyListBox**에서 하나 이상의 셰이프를 선택합니다.

    선택한 셰이프만 표시됩니다.

이 단계에서는 항목 목록을 만드는 데 식을 사용했습니다. 이를 비즈니스 내에서 다른 요소에 적용할 수 있습니다. 예를 들어, **드롭다운** 컨트롤을 사용하여 제품 이미지, 제품 설명 등을 표시할 수 있습니다.

## <a name="add-radio-buttons"></a>라디오 단추 추가
1. **홈** 탭에서 **새 화면**을 선택한 다음, **비어 있음**을 선택합니다.

2. **삽입** 탭에서 **컨트롤**을 선택한 다음 **라디오**를 선택합니다.

    ![][10]  

3. **라디오** 컨트롤의 이름을 **Choices**로 바꾸고 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    필요한 경우 모든 옵션을 표시하도록 컨트롤의 크기를 조정합니다.

4. **삽입** 탭에서 **아이콘**을 선택한 다음 원을 선택합니다.

5. 원의 **[Fill](controls/properties-color-border.md)** 속성을 다음 함수로 설정합니다.  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    이 수식에서 원은 선택한 라디오 단추에 따라 색을 변경합니다.

6. 다음 예와 같이 **라디오** 단추 아래로 원을 이동합니다.

    ![][14]  

7. Alt 키를 누른 상태로 다른 라디오 단추를 선택하여 원의 색을 변경합니다.

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
