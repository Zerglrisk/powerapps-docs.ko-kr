---
title: 갤러리에서 데이터 표시, 정렬 및 필터링 | Microsoft Docs
description: 갤러리를 사용하여 이미지와 텍스트를 표시합니다. Power Apps에서 이미지를 정렬 하 고 필터링 합니다.
author: adrianorth
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/02/2015
ms.author: aorth
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 14925b5e50f1731efc935bc8a3379342283ec2a0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732447"
---
# <a name="show-sort-and-filter-data-in-a-power-apps-gallery"></a>Power Apps 갤러리에서 데이터 표시, 정렬 및 필터링
갤러리를 만들어 여러 제품에 대한 이미지와 텍스트를 표시하고 해당 정보를 정렬 및 필터링합니다.

Power Apps에서 갤러리를 사용 하 여 카탈로그에 표시 되는 것 처럼 여러 관련 항목을 표시할 수 있습니다. 갤러리는 이름 및 가격과 같은 제품에 대한 정보를 표시하는 데 유용합니다. 이 항목에서는 갤러리를 만들고 Excel과 비슷한 함수를 사용하여 정보를 정렬 및 필터링합니다. 또한 항목이 선택되면 항목 주위에 테두리가 배치됩니다.

> [!NOTE]
> 이 항목에서는 태블릿 앱을 사용합니다. 전화 앱을 사용할 수 있지만 일부 컨트롤의 크기를 조정해야 합니다.
> 
> 

### <a name="prerequisites"></a>필수 조건
* Power Apps에 [등록](../signup-for-powerapps.md) 한 다음 등록 하는 데 사용한 것과 동일한 자격 증명을 사용 하 여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.
* [템플릿](get-started-test-drive.md)에서, [데이터](get-started-create-from-data.md)에서 또는 [처음부터](get-started-create-from-blank.md) 태블릿 앱을 만듭니다.
* [컨트롤을 구성](add-configure-controls.md)하는 방법을 알아봅니다.
* 이러한 단계에서는 .jpg 이미지가 포함된 [CreateFirstApp](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)을 입력 데이터 샘플로 사용합니다. zip 파일에는 Excel로 변환할 수 있는 XML 파일이 포함되어 있습니다. 그렇지 않으면 Power Apps에서 자동으로 .zip 파일의 파일을 읽고 성공적으로 가져옵니다. 이 샘플 데이터를 다운로드하여 사용하거나 직접 가져올 수 있습니다.

## <a name="show-data-in-a-gallery"></a>갤러리에서 데이터 표시
1. 샘플 데이터를 사용하여 **Inventory**라는 컬렉션을 만듭니다. 단계는 다음과 같습니다.  
   
   1. **삽입** 탭에서 **컨트롤**을 선택한 다음 **가져오기**를 선택합니다.
      
      ![][1]  
   2. 가져오기 컨트롤의 **[OnSelect](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
      **Collect (Inventory, Import1)**
      
      ![][12]  
   3. **데이터 가져오기** 단추를 선택하여 Windows 탐색기를 엽니다. *CreateFirstApp.zip*을 선택하고 **열기**를 선택합니다.
   4. **파일** 메뉴에서 **컬렉션**을 선택합니다. 가져온 데이터가 있는 Inventory 컬렉션이 나열됩니다.
      
      ![][3]  
      
      이제 디자인 이미지, 제품 이름 및 재고 단위 수를 포함하여 5개 제품에 대한 정보가 포함된 Inventory 컬렉션을 만들었습니다.
      
      > [!NOTE]
      > 가져오기 컨트롤은 Excel과 같은 데이터를 가져와서 컬렉션을 만드는 데 사용됩니다. 가져오기 컨트롤은 앱을 만들고 앱을 미리 볼 때 데이터를 가져옵니다. 현재 가져오기 컨트롤은 앱을 게시할 때는 데이터를 가져오지 않습니다.
      > 
      > 
2. 뒤로 화살표를 선택하여 디자이너로 돌아갑니다.
3. **삽입** 탭에서 **갤러리**, **가로** 갤러리를 차례로 클릭하거나 탭합니다.
   
    ![][4]
4. 오른쪽 창에서 제목과 부제목이 그래픽을 오버레이하는 옵션을 클릭하거나 탭합니다.
   
    ![][15]
5. 갤러리의 **[Items](controls/properties-core.md)** 속성을 **Inventory**로 설정합니다.
   
    ![][5]
6. 갤러리의 이름을 **ProductGallery**로 바꾸고 다른 컨트롤을 차단하지 않도록 갤러리를 이동합니다. 갤러리의 크기를 조정하여 세 개 제품을 표시합니다.
   
    ![][6]
7. 갤러리의 첫 번째 항목에서 아래쪽 레이블을 선택합니다.  
   
    ![][7]  
   
   > [!NOTE]
   > 갤러리에서 첫 번째 항목을 변경하면 갤러리의 다른 모든 항목이 자동으로 변경됩니다.  
   > 
   > 
8. 레이블의 **[Text](controls/properties-core.md)** 속성을 다음 식으로 설정합니다.  
    **ThisItem. UnitsInStock** <br/>
   
    이렇게 하면 레이블에 각 제품의 재고 단위가 표시됩니다.

![][8]  

> [!NOTE]
> 기본적으로 최상위 레이블의 **[Text](controls/properties-core.md)** 속성은 ```ThisItem.ProductName```으로 설정됩니다. 컬렉션의 다른 항목으로 변경할 수 있습니다. 예를 들어 컬렉션에 'ProductDescription' 또는 'Price' 필드가 있는 경우 레이블을 ```ThisItem.ProductDescription``` 또는 ```ThisItem.Price```로 설정할 수 있습니다.
> 
> 

이러한 단계를 사용하여 .jpg 이미지가 포함된 데이터를 컬렉션으로 가져왔습니다. 그런 다음 데이터를 표시하는 갤러리를 추가했고 각 제품의 재고 단위를 표시하는 레이블을 구성했습니다.

## <a name="highlight-the-gallery-item-you-select"></a>선택한 갤러리 항목 강조 표시
1. 갤러리에서 첫 번째 항목을 '제외한' 항목을 선택합니다. 편집 아이콘이 표시됩니다(왼쪽 위 모서리). 편집 아이콘을 선택합니다.  
   ![][9]  
2. **삽입** 탭에서 **도형**을 선택한 다음 사각형을 선택합니다. 파란색 실선의 사각형이 각 갤러리 항목에 표시됩니다.
3. **홈** 탭에서 **채우기**를 선택한 다음 **채우기 없음**을 선택합니다.
4. **테두리**, **테두리 스타일**, 실선을 차례로 선택합니다.
5. **테두리**를 다시 선택하고 두께를 3으로 설정합니다. 갤러리 항목을 둘러싸도록 사각형의 크기를 조정합니다. 이제 갤러리의 항목에 파란색 테두리가 있으며 다음과 비슷합니다.  
   ![][10]  
6. **도형** 탭에서 **테두리 표시**를 선택한 다음, 수식 입력줄에 다음 수식을 입력합니다.  
   
    **If (ThisItem. IsSelected, true)**
   
    파란색 사각형이 갤러리에서 현재 선택한 항목을 둘러쌉니다. 몇 가지 갤러리 항목을 선택하여 선택한 각 항목 주위에 사각형이 표시되는지 확인합니다. 또한 **미리 보기** ![][2]를 열어 만들고 있는 항목을 보고 테스트할 수도 있습니다.

> [!TIP]
> 사각형을 선택하고, **홈** 탭에서 **순서 다시 매기기**를 선택한 다음, **맨 뒤로 보내기**를 선택합니다. 이 기능을 사용하면 다른 항목을 차단하는 테두리가 없는 갤러리 항목을 선택할 수 있습니다.
> 
> 

이러한 단계를 사용하여 갤러리에서 현재 선택한 항목 주위에 테두리를 추가했습니다.

## <a name="sort-and-filter-items-in-the-gallery"></a>갤러리에서 항목 정렬 및 필터링
이 단계에서는 갤러리 항목을 오름차순과 내림차순으로 정렬합니다. 또한 슬라이더 컨트롤을 추가하여 선택한 재고 단위별로 갤러리 항목을 '필터링'합니다.

#### <a name="sort-in-ascending-or-descending-order"></a>오름차순 또는 내림차순 정렬
1. 갤러리에서 첫 번째 항목을 '제외한' 항목을 선택합니다.
2. **[Items](controls/properties-core.md)** 속성은 현재 Inventory(컬렉션 이름)로 설정되어 있습니다. 다음과 같이 변경합니다.  
   
    **Sort(Inventory, ProductName)**
   
    이렇게 하면 갤러리의 항목이 제품 이름별로 오름차순으로 정렬됩니다. ![][11]  
   
    내림차순으로 정렬해 보세요. 갤러리의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   
    Sort(Inventory, ProductName, Descending)  

#### <a name="add-a-slider-control-and-filter-items-in-the-gallery"></a>슬라이더 컨트롤 추가 및 갤러리 항목 필터링
1. 슬라이더 컨트롤(**삽입** 탭> **컨트롤**)을 추가하고, 이름을 **StockFilter**로 바꾼 다음, 갤러리 아래로 이동합니다.
2. 사용자가 재고 단위의 범위를 벗어나는 값으로 설정할 수 없도록 슬라이더를 구성합니다.  
   
   1. **용량** 탭에서 **최소**를 선택하고 다음 식을 입력합니다.  
      ```Min(Inventory, UnitsInStock)```  
   2. **용량** 탭에서 **최대**를 선택하고 다음 식을 입력합니다.  
      ```Max(Inventory, UnitsInStock)```
3. 갤러리에서 첫 번째 항목을 '제외한' 항목을 선택합니다. 갤러리의 **[Items](controls/properties-core.md)** 속성을 다음 식으로 설정합니다.  
   ```Filter(Inventory, UnitsInStock<=StockFilter.Value)```
4. **미리 보기**에서 슬라이더를 갤러리에서 가장 높은 수량과 가장 낮은 수량 사이의 값으로 조정합니다. 슬라이더를 조정하면 갤러리에는 선택한 값보다 작은 제품만 표시됩니다.  
   ![][13]  

이제 필터에 추가해 보겠습니다.

1. 디자이너로 돌아갑니다.
2. **삽입** 탭에서 **텍스트**를 선택하고, **텍스트 입력**을 선택한 다음, 새 컨트롤의 이름을 **NameFilter**로 바꿉니다. 텍스트 컨트롤을 슬라이더 아래로 이동합니다.
3. 갤러리의 **[Items](controls/properties-core.md)** 속성을 다음 식으로 설정합니다.  
   ```Filter(Inventory, UnitsInStock<=StockFilter.Value && NameFilter.Text in ProductName)```
4. **미리 보기**에서 슬라이더를 '30'으로 설정하고, 텍스트 입력 컨트롤에 'g' 문자를 입력합니다. 갤러리에는 이름에 "g" 문자가 있고 재고 단위가 30개 미만인 제품만 표시됩니다.  
   ![][14]  

## <a name="tips-and-tricks"></a>팁과 요령
* 언제든지 미리 보기(![][2]) 단추를 선택하여 만든 항목을 보고 테스트할 수 있습니다.
* 앱을 디자인할 때 컨트롤의 크기를 조정하고, 클릭한 다음 끌기를 사용하여 이동할 수 있습니다.
* **Esc** 키를 누르거나 **X**를 선택하여 미리 보기 창을 닫습니다.
* 갤러리를 사용할 때 갤러리의 모든 항목을 변경하려면 갤러리에서 첫 번째 항목을 선택합니다. 예를 들어 갤러리의 모든 항목에 테두리를 추가하려면 첫 번째 항목을 선택합니다.
* 갤러리의 속성을 업데이트하려면 갤러리에서 첫 번째 항목을 '제외한' 항목을 선택합니다. 예를 들어 두 번째 항목을 선택하여 'Items', 'ShowScrollbar' 및 갤러리에 적용되는 기타 속성(갤러리의 항목 아님)을 업데이트합니다.  

## <a name="what-you-learned"></a>학습 내용
이 항목에서는 다음을 수행했습니다.

* 컬렉션을 만들고, .jpg 이미지가 포함된 데이터를 해당 컬렉션에 가져오고, 갤러리에서 해당 데이터를 표시했습니다.
* 갤러리의 각 이미지 아래에서 해당 항목의 재고 단위가 나열되는 레이블을 구성했습니다.
* 선택한 항목 주위에 테두리를 추가했습니다.
* 항목을 제품 이름별로 오름차순 및 내림차순으로 정렬했습니다.
* 슬라이더 및 입력 텍스트 컨트롤을 추가하여 제품을 재고 단위 및 제품 이름별로 필터링했습니다.

[1]: ./media/show-images-text-gallery-sort-filter/import.png
[2]: ./media/show-images-text-gallery-sort-filter/preview.png
[3]: ./media/show-images-text-gallery-sort-filter/inventorycollection.png
[4]: ./media/show-images-text-gallery-sort-filter/insert-vertical.png
[5]: ./media/show-images-text-gallery-sort-filter/itemsinventory.png
[6]: ./media/show-images-text-gallery-sort-filter/threeimages.png
[7]: ./media/show-images-text-gallery-sort-filter/firstitem.png
[8]: ./media/show-images-text-gallery-sort-filter/bottomlabel.png
[9]: ./media/show-images-text-gallery-sort-filter/editgallery.png
[10]: ./media/show-images-text-gallery-sort-filter/border.png
[11]: ./media/show-images-text-gallery-sort-filter/sort.png
[12]: ./media/show-images-text-gallery-sort-filter/onselect.png
[13]: ./media/show-images-text-gallery-sort-filter/slider.png
[14]: ./media/show-images-text-gallery-sort-filter/inputandslider.png
[15]: ./media/show-images-text-gallery-sort-filter/select-overlay.png
