---
title: Remove 및 RemoveIf 함수 | Microsoft Docs
description: PowerApps의 Remove 및 RemoveIf 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: 57432024254598ff8216d6fefafa5354844bb7a4
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984300"
---
# <a name="remove-and-removeif-functions-in-powerapps"></a>PowerApps의 Remove 및 RemoveIf 함수
[데이터 원본](../working-with-data-sources.md)에서 [레코드](../working-with-tables.md#records)를 제거합니다.

## <a name="description"></a>설명
### <a name="remove-function"></a>Remove 함수
데이터 원본에서 특정 레코드나 여러 레코드를 제거하려면 **Remove** 함수를 사용합니다.  

[컬렉션](../working-with-data-sources.md#collections)의 경우 전체 레코드가 일치해야 합니다. **All** 인수를 사용하여 레코드의 모든 복사본을 제거하거나 레코드의 복사본을 하나만 제거할 수 있습니다.

### <a name="removeif-function"></a>RemoveIf 함수
조건 또는 조건 집합을 기반으로 레코드를 제거하려면 **RemoveIf** 함수를 사용합니다. 각 조건은 결과가 **true** 또는 **false**가 되는 수식이 될 수 있고 이름으로 데이터 원본의 [열](../working-with-tables.md#columns)을 참조할 수 있습니다. 각 조건은 각 레코드에 대해 개별적으로 계산되며 모든 조건이 **true**로 평가되면 레코드가 제거됩니다.

**Remove** 및 **RemoveIf**는 수정된 데이터 원본을 [테이블](../working-with-tables.md)로 반환합니다. 두 함수는 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

**[Clear](function-clear-collect-clearcollect.md)** 함수를 사용하여 데이터 원본의 모든 레코드를 제거할 수도 있습니다.

### <a name="delegation"></a>위임
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>구문
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *DataSource* – 필수 항목입니다. 제거할 레코드가 포함된 데이터 원본입니다.
* *Record(s)* – 필수 항목입니다. 제거할 레코드입니다.
* **All** – 선택 사항입니다. 컬렉션에서 동일한 레코드가 두 번 이상 나타날 수 있습니다.  **All** 인수를 추가하여 레코드의 모든 복사본을 제거할 수 있습니다.

**Remove**( *DataSource*, *Table* [, **All** ] )

* *DataSource* – 필수 항목입니다. 제거할 여러 레코드가 포함된 데이터 원본입니다.
* *Table* – 필수 항목입니다. 제거할 레코드의 테이블입니다.
* **All** – 선택 사항입니다. 컬렉션에서 동일한 레코드가 두 번 이상 나타날 수 있습니다.  **All** 인수를 추가하여 레코드의 모든 복사본을 제거할 수 있습니다.

**RemoveIf**( *DataSource*, *Condition* [, ... ] )

* *DataSource* – 필수 항목입니다. 제거할 레코드가 포함된 데이터 원본입니다.
* *Condition(s)* – 필수 항목입니다. 제거할 레코드에 대해 **true**로 평가되는 수식입니다.  수식에서 *DataSource*의 열 이름을 사용할 수 있습니다.  여러 *Condition*을 지정하는 경우 제거할 레코드에 대해 모두가 **true**로 평가되어야 합니다.

## <a name="examples"></a>예
이 예제에서는 다음 테이블의 데이터로 시작되는 **IceCream**이라는 데이터 원본의 레코드를 제거합니다.

![](media/function-remove-removeif/icecream.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |데이터 원본에서 **Chocolate**을 제거합니다. |<style> img { max-width: none } </style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |데이터 원본에서 레코드를 두 개 제거합니다. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150 )** |**Quantity**가 **150**보다 큰 레코드를 제거합니다. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |**Quantity**가 150보다 크고 **Flavor**가 **S**로 시작되는 레코드를 제거합니다. |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>**IceCream** 데이터 원본이 수정되었습니다. |
| **RemoveIf(&nbsp;IceCream, true )** |데이터 원본에서 모든 레코드를 제거합니다. |![](media/function-remove-removeif/icecream-empty.png)<br><br>**IceCream** 데이터 원본이 수정되었습니다. |

### <a name="step-by-step"></a>단계별 가이드
1. **Inventory**라는 컬렉션을 가져오거나 만들고, [갤러리에 데이터 표시](../show-images-text-gallery-sort-filter.md)의 설명에 따라 갤러리에 표시합니다.
2. 갤러리에서 이미지의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 식으로 설정합니다.<br>**Remove(Inventory, ThisItem)**
3. F5 키를 누른 다음 갤러리에서 이미지를 선택합니다.<br>해당 항목이 갤러리와 컬렉션에서 제거됩니다.

