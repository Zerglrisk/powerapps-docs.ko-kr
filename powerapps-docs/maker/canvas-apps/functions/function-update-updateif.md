---
title: Update 및 UpdateIf 함수 | Microsoft Docs
description: PowerApps에서 Update 및 UpdateIf 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8dd673c343b484e6c24e218818cdfbba654dcbb7
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983694"
---
# <a name="update-and-updateif-functions-in-powerapps"></a>PowerApps에서 Update 및 UpdateIf 함수
[데이터 원본](../working-with-data-sources.md)의 [레코드](../working-with-tables.md#records)를 업데이트합니다.

## <a name="description"></a>설명
### <a name="update-function"></a>Update 함수
**Update** 함수는 데이터 원본의 전체 레코드를 교체합니다. 반대로 **UpdateIf** 및 **[Patch](function-patch.md)** 함수는 다른 값은 그대로 두면서 레코드에서 하나 이상의 값을 수정합니다.

[컬렉션](../working-with-data-sources.md#collections)의 경우 전체 레코드가 일치해야 합니다. 컬렉션은 중복 레코드를 허용하므로 여러 레코드가 일치할 수도 있습니다. **All** 인수를 사용하여 레코드의 모든 복사본을 업데이트하거나, 레코드 중 복사본 하나만 업데이트할 수 있습니다.

데이터 원본에서 열의 값이 자동으로 생성되는 경우 해당 [열](../working-with-tables.md#columns)의 값을 재확인해야 합니다.

### <a name="updateif-function"></a>UpdateIf 함수
**UpdateIf** 함수는 하나 이상의 조건에 일치하는 하나 이상의 레코드에서 하나 이상의 값을 수정합니다. 조건은 결과가 **true** 또는 **false**가 되는 수식이 될 수 있고 이름으로 데이터 원본의 열을 참조할 수 있습니다. 함수는 각 레코드에 대한 조건을 평가하고 결과가 **true**인 레코드를 수정합니다.  

수정을 지정하려면 새 속성 값을 포함하는 변경 레코드를 사용합니다. 중괄호를 사용하여 이 변경 레코드 인라인을 제공하는 경우 속성 수식은 수정되는 레코드의 속성을 참조할 수 있습니다. 이 동작을 사용하여 수식에 따라 레코드를 수정할 수 있습니다.

**UpdateIf**와 유사하게 **[Patch](function-patch.md)** 함수를 사용하여 다른 열에 영향을 주지 않으면서 레코드의 특정 열을 변경할 수 있습니다.

**Update** 및 **UpdateIf**는 모두 수정된 데이터 원본을 [테이블](../working-with-tables.md)로 반환합니다. 두 함수 모두 [동작 수식](../working-with-formulas-in-depth.md)에서 사용해야 합니다.

### <a name="delegation"></a>위임
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>구문
**Update**( *DataSource*, *OldRecord*, *NewRecord* [, **All** ] )

* *DataSource* – 필수 항목입니다. 교체할 레코드가 포함된 데이터 원본입니다.
* *OldRecord* – 필수 항목입니다. 교체할 레코드입니다.
* *NewRecord* – 필수 항목입니다. 대체 레코드입니다. 이는 변경 레코드가 아닙니다. 전체 레코드가 변경되고, 누락된 속성은 *blank*를 포함하게 됩니다.
* **All** – 선택 사항입니다. 컬렉션에서 동일한 레코드가 두 번 이상 나타날 수 있습니다. **All** 인수를 지정하여 레코드의 모든 복사본을 제거할 수 있습니다.

**UpdateIf**( *DataSource*, *Condition1*, *ChangeRecord1* [, *Condition2*, *ChangeRecord2*, ... ] )

* *DataSource* – 필수 항목입니다. 제거할 레코드가 포함된 데이터 원본입니다.
* *Condition(s)* – 필수 항목입니다. 수정할 레코드에 대해 **true**로 평가되는 수식입니다.  수식에서 *DataSource*의 열 이름을 사용할 수 있습니다.  
* *ChangeRecord(s)* – 필수 항목입니다.  각 해당 조건에서 조건을 충족하는 *DataSource*의 레코드에 적용할 새 속성 값의 변경 레코드입니다. 중괄호를 사용하여 레코드 인라인을 제공하는 경우 기존 레코드의 속성 값을 속성 수식에 사용할 수 있습니다.

## <a name="examples"></a>예
이러한 예제에서는 다음 테이블의 데이터로 시작되며 이름이 **IceCream**인 데이터 원본의 레코드를 교체 또는 수정하게 됩니다.

![](media/function-update-updateif/icecream.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor=“Chocolate”&nbsp;)&nbsp;), {&nbsp;ID:&nbsp;1,&nbsp;Flavor:&nbsp;“Mint&nbsp;Chocolate”,&nbsp;Quantity:150&nbsp;} )** |데이터 원본에서 레코드를 교체합니다. |<style> img { max-width: none } </style> ![](media/function-update-updateif/icecream-mint.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **UpdateIf(&nbsp;IceCream, Quantity > 175, {&nbsp;Quantity:&nbsp;Quantity&nbsp;+&nbsp;10&nbsp;} )** |**Quantity**가 **150**보다 큰 레코드를 수정합니다.  **Quantity** 필드는 10씩 증가하고 다른 필드는 수정되지 않습니다. |![](media/function-update-updateif/icecream-mint-plus10.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **Update(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream, Flavor=“Strawberry”&nbsp;)&nbsp;),<br>{&nbsp;ID:&nbsp;3, Flavor:&nbsp;“Strawberry Swirl”} )** |데이터 원본에서 레코드를 교체합니다. **Quantity** 속성이 대체 레코드에서 적용되지 않아 해당 속성이 결과에서 *blank*로 나타납니다. |![](media/function-update-updateif/icecream-mint-swirl.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **UpdateIf(&nbsp;IceCream, true, {&nbsp;Quantity:&nbsp;0&nbsp;} )** |데이터 원본의 모든 레코드에 대해 **Quantity** 속성의 값을 0으로 설정합니다. |![ ](./media/function-update-updateif/icecream-mint-zero.png)<br> <br>**IceCream** 데이터 원본이 수정되었습니다. |

### <a name="step-by-step"></a>단계별 가이드
1. **Inventory**라는 컬렉션을 가져오거나 만들고, [갤러리에 데이터 표시](../show-images-text-gallery-sort-filter.md)의 설명에 따라 갤러리에 표시합니다.
2. 갤러리의 이름을 **ProductGallery**로 지정합니다.
3. **UnitsSold**라는 슬라이더를 추가하고, 해당 **Max** 속성을 다음 식으로 설정합니다.<br>**ProductGallery.Selected.UnitsInStock**
4. 단추 하나를 추가하고 이 수식에 **[OnSelect](../controls/properties-core.md)** 속성을 설정합니다.<br>**UpdateIf(Inventory, ProductName = ProductGallery.Selected.ProductName, {UnitsInStock:UnitsInStock-UnitsSold.Value})**
5. F5 키를 눌러 갤러리에서 제품을 선택하고, 슬라이더로 값을 지정한 다음, 단추를 선택합니다.
   
    지정한 제품의 재고에서 단위 개수가 지정한 크기로 감소합니다.

