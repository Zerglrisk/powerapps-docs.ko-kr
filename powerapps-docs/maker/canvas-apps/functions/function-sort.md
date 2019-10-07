---
title: Sort 및 SortByColumns 함수 | Microsoft Docs
description: PowerApps에서 Sort 및 SortByColumns 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aa51c97eff57b9659e5fd246af8016898eeeb9df
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992232"
---
# <a name="sort-and-sortbycolumns-functions-in-powerapps"></a>PowerApps의 Sort 및 SortByColumns 함수
[테이블](../working-with-tables.md)을 정렬합니다.

## <a name="description"></a>설명
**Sort** 함수는 수식에 따라 테이블을 정렬합니다.  

해당 수식은 해당 테이블의 각 [레코드](../working-with-tables.md#records)를 계산하고, 그 결과는 테이블을 정렬하는 데 사용됩니다.  수식은 숫자, 문자열 또는 부울 값이 되어야 하며, 테이블 또는 레코드가 될 수 없습니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

하나의 열로 먼저 정렬 후 다른 열로 정렬하려면 **Sort** 수식을 다른 열에 삽입합니다. 예를 들어 다음 수식을 사용 하 여 먼저 **LastName** 열을 기준으로 contact 테이블을 정렬 한 다음 **FirstName** 열을 기준으로 **연락처** 테이블을 정렬할 수 있습니다.  **Sort (Sort (Contacts, LastName), FirstName)**

**SortByColumns** 함수는 하나 이상의 열을 기준으로 테이블을 정렬하는 데 사용할 수도 있습니다.

**SortByColumns**에 대한 매개 변수 목록은 정렬할 열의 이름 및 열당 정렬 방향을 제공합니다.  정렬 작업은 (첫 번째 열로 먼저 정렬한 후 두 번째 열로 정렬된) 매개 변수의 순서대로 수행됩니다.  열 이름은 매개 변수 목록에 직접 포함될 경우 큰따옴표가 필요한 문자열로 지정됩니다.  예를 들어, **SortByColumns( CustomerTable, "LastName" )** 입니다.

**SortByColumns**를 **[드롭다운](../controls/control-drop-down.md)** 또는 **[목록 상자](../controls/control-list-box.md)** 컨트롤과 결합하면 사용자가 어떤 열로 정렬할지 선택할 수 있게 됩니다.

**SortByColumns**는 오름차순 또는 내림차순의 정렬 방식 외에도, 테이블 값을 하나의 열로 정렬할 수 있습니다.  예를 들어, **["월요일", "화요일", "수요일", "목요일", "금요일", "토요일", "일요일"]** 을 정렬 순서로 제공하여 해당 주의 요일 이름을 기준으로 레코드를 정렬할 수 있습니다.  모든 레코드에는 **월요일**이 먼저 오고, **화요일**이 다음에 옵니다.  정렬 테이블에 표시되지 않지만 찾은 레코드는 해당 목록의 끝에 배치됩니다.

[Table](../working-with-tables.md)은 PowerApps에서 문자열이나 숫자와 같은 값입니다.  테이블을 함수로 전달하거나 함수로부터 반환할 수 있습니다.  **Sort** 및 **SortByColumn**은 테이블을 변경하지 않는 대신 테이블을 인수로 가져오고 정렬된 새 테이블을 반환합니다.  자세한 내용은 [테이블 작업](../working-with-tables.md)을 참조하세요.

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>구문
**Sort**( *Table*, *Formula* [, *SortOrder* ] )

* *Table* - 필수 항목입니다. 정렬할 테이블입니다.
* *Formula* - 필수 항목입니다. 이 수식은 해당 테이블의 각 레코드를 계산하고, 그 결과는 테이블을 정렬하는 데 사용됩니다.  테이블 내의 열을 참조할 수 있습니다.
* *SortOrder* - 선택 항목입니다. 내림차순으로 테이블을 정렬하려면 **SortOrder.Descending**을 지정합니다. **SortOrder.Ascending**이 기본값입니다.

**SortByColumns**( *Table*, *ColumnName1* [, *SortOrder1*, *ColumnName2*, *SortOrder2*, ... ] )

* *Table* - 필수 항목입니다. 정렬할 테이블입니다.
* *ColumnName(s)* - 필수 항목입니다. 문자열로서 정렬할 열 이름입니다.
* *SortOrder(s)* - 선택 항목입니다.  **SortOrder.Ascending** 또는 **SortOrder.Descending**이 있습니다.  **SortOrder.Ascending**이 기본값입니다.  다양한 *ColumnNames*가 제공되면 마지막 열을 제외한 모든 열에는 *SortOrder*가 포함되어야 합니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

**SortByColumns**( *Table*, *ColumnName*, *SortOrderTable* )

* *Table* - 필수 항목입니다. 정렬할 테이블입니다.
* *ColumnName* - 필수 항목입니다. 문자열로서 정렬할 열 이름입니다.
* *SortOrderTable* - 필수 항목입니다.  정렬할 값들의 단일 열 테이블입니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

## <a name="examples"></a>예
다음 예제에서는 이 테이블의 데이터가 포함된 **IceCream** [데이터 원본](../working-with-data-sources.md)을 사용합니다.

![](media/function-sort/icecream.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Sort( IceCream, Flavor )**<br><br>**SortByColumns( IceCream "Flavor" )** |**IceCream**을 **Flavor** 열로 정렬합니다. **Flavor** 열에는 문자열이 포함되어 해당 테이블은 사전순으로 정렬됩니다. 기본적으로 정렬 순서는 오름차순입니다. |<style> img { max-width: none; } </style> ![](media/function-sort/icecream-flavor.png) |
| **Sort( IceCream, Quantity )**<br><br>**SortByColumns( IceCream, "Quantity" )** |**IceCream**을 **Quantity** 열로 정렬합니다.  **Quantity** 열에는 숫자가 포함되어 해당 테이블은 번호순으로 정렬됩니다.  기본적으로 정렬 순서는 오름차순입니다. |![](media/function-sort/icecream-quantity-asc.png) |
| **Sort( IceCream, Quantity, SortOrder.Descending )**<br><br>**SortByColumns( IceCream, "Quantity", SortOrder.Descending )** |**IceCream**을 **Quantity** 열로 정렬합니다.  **Quantity** 열에는 숫자가 포함되어 번호순으로 정렬됩니다.  정렬 순서는 내림차순으로 지정되었습니다. |![](media/function-sort/icecream-quantity-desc.png) |
| **Sort( IceCream, Quantity + OnOrder )** |**IceCream**을 각 레코드에 대해 개별적으로 **Quantity** 및 **OnOrder** 열의 합으로 정렬합니다. 합계는 숫자이므로 해당 테이블이 번호순으로 정렬됩니다.  기본적으로 정렬 순서는 오름차순입니다.  원시 열 값이 아닌 수식으로 정렬하기 때문에 **SortByColumns**를 사용하는 것에는 적용되지 않습니다. |![](media/function-sort/icecream-total.png) |
| **Sort( Sort( IceCream, OnOrder ), Quantity )**<br><br>**SortByColumns( IceCream, "OnOrder", Ascending, "Quantity", Ascending )** |**IceCream**을 **OnOrder** 열로 먼저 정렬한 후 **Quantity** 열로 정렬합니다.  **OnOrder** 기준으로 첫 번째 정렬에서 "Pistachio"는 "Vanilla" 위로 올라간 다음, 둘 모두 **Quantity** 기준에 따른 적절한 위치로 함께 이동합니다. |![](media/function-sort/icecream-onorder-quantity.png) |
| **SortByColumns( IceCream, "Flavor", [&nbsp;"Pistachio",&nbsp;"Strawberry"&nbsp;] )** |"Pistachio" 및 "Strawberry"를 포함하는 단일 열 테이블 기준의 **Flavor** 열로 **IceCream**을 정렬합니다.  "Pistachio" **Flavor**가 있는 레코드가 첫 번째로 표시되고 "Strawberry"를 포함한 레코드가 다음에 나옵니다.  "Vanilla"와 같이 일치하지 않는 **Flavor** 열의 값들은 일치했던 항목들 다음에 표시됩니다. |![](media/function-sort/icecream-onflavor-sorttable.png) |

### <a name="step-by-step"></a>단계별 가이드
이러한 예제를 직접 실행하려면 [Collection](../working-with-data-sources.md#collections)과 같은 **IceCream** 데이터 원본을 만듭니다.

1. 단추 하나를 추가하고 이 수식에 **[OnSelect](../controls/properties-core.md)** 속성을 설정합니다.<br>**ClearCollect (IceCream, {특색: "초콜릿", Quantity: 100, OnOrder: 150}, {버전:  "바닐라", 수량: 200, OnOrder: 20}, {특색: "Strawberry", 수량: 300, OnOrder: 0}, {특색: "Mint 초콜릿", Quantity: 60, OnOrder: 100}, {버전: "Pistachio", 수량: 200, OnOrder: 10})**
2. 앱을 미리 보고, 단추를 선택한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
3. 바로 만든 컬렉션을 표시하려면 **File** 메뉴의 **Collections**를 선택한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.

#### <a name="sort"></a>정렬
1. 또 다른 단추를 추가하고 이 수식에 **[OnSelect](../controls/properties-core.md)** 속성을 설정합니다.<br>
   **ClearCollect( SortByFlavor, Sort( IceCream, Flavor ) )**
   
     앞의 수식은 **Ice Cream**과 동일한 데이터를 포함하는 **SortByFlavor**라는 이름의 2번째 컬렉션을 만듭니다. 단, 새 컬렉션에는 오름차순의 **Flavor** 열로 사전순으로 정렬한 데이터가 포함됩니다.
2. F5 키를 누르고 새 단추를 선택한 다음, Esc 키를 누릅니다.
3. 두 컬렉션을 모두 표시하려면 **File** 메뉴의 **Collections**를 선택한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
4. 마지막 세 단계를 반복하되, 만들려는 컬렉션의 이름을 변경하고, **Sort** 수식을 **Sort**를 사용하는 이 섹션 앞 부분의 예제 테이블의 다른 수식으로 교체합니다.

#### <a name="sortbycolumns"></a>SortByColumns
1. 또 다른 단추를 추가하고 이 수식에 **[OnSelect](../controls/properties-core.md)** 속성을 설정합니다.<br>
   **ClearCollect( SortByQuantity, SortByColumns( IceCream, "Quantity", Ascending, "Flavor", Descending ) )**
   
     앞의 수식은 **Ice Cream**과 동일한 데이터를 포함하는 **SortByQuantity**라는 이름의 3번째 컬렉션을 만듭니다. 그러나 새 컬렉션에는 **Quantity** 열을 기준으로 오름차순으로 정렬 한 다음, **버전** 열을 기준으로 내림차순으로 정렬 된 데이터가 포함 됩니다.
2. F5 키를 누르고 새 단추를 선택한 다음, Esc 키를 누릅니다.
3. 세 컬렉션을 모두 표시하려면 **파일** 메뉴의 **Collections**를 선택한 다음, 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.
4. 마지막 세 단계를 반복하되, 만들려는 컬렉션의 이름을 변경하고, **SortByColumns** 수식을 **SortByColumns**를 사용하는 이 섹션 앞 부분의 예제 테이블의 다른 수식으로 교체합니다.

