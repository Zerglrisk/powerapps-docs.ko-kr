---
title: AddColumns, DropColumns, RenameColumns 및 ShowColumns 함수 | Microsoft Docs
description: PowerApps에서 AddColumns, DropColumns, RenameColumns 및 ShowColumns 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc682694bb22ecc63ecc762a735df07950ce29d3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61543775"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>PowerApps에서 AddColumns, DropColumns, RenameColumns 및 ShowColumns 함수
해당 [열](../working-with-tables.md#columns)을 추가, 삭제, 이름 바꾸기 및 선택하여 [테이블](../working-with-tables.md)을 셰이프합니다.

## <a name="overview"></a>개요
이러한 함수는 해당 열을 조정하여 테이블을 셰이프합니다.

* **[Lower](function-lower-upper-proper.md)** 또는 **[Abs](function-numericals.md)** 와 같은 단일 열 함수를 사용하도록 여러 열을 포함하는 테이블을 단일 열로 축소시킵니다.  
* 테이블에 계산된 열을 추가합니다(예: **Quantity**에 **Unit Price**를 곱한 결과를 표시하는 **Total Price** 열).
* 사용자에게 표시하거나 수식에서 사용할 수 있도록 열의 이름을 더 의미 있게 변경합니다.

테이블은 문자열이나 숫자처럼 PowerApps의 값입니다.  테이블을 수식의 인수로 지정할 수 있으며 함수는 테이블을 결과로 반환할 수 있습니다.

> [!NOTE]
> 이 항목에 설명 된 함수는 원래 테이블을 수정 하지 마세요. 대신, 해당 테이블을 인수로 사용 하며 적용 된 변환을 사용 하 여 새 테이블을 반환 합니다. 자세한 내용은 [테이블 작업](../working-with-tables.md)을 참조하세요.  

이러한 함수를 사용하여 [데이터 원본](../working-with-data-sources.md)의 열을 수정할 수는 없습니다. 데이터는 해당 원본에서 수정해야 합니다. **[Collect](function-clear-collect-clearcollect.md)** 함수를 사용하여 열을 [컬렉션](../working-with-data-sources.md#collections)에 추가할 수 있습니다. 자세한 내용은 [데이터 원본 작업](../working-with-data-sources.md)을 참조하세요.  

## <a name="description"></a>설명
**AddColumns** 함수는 열을 테이블에 추가하고, 수식은 해당 열의 값을 정의합니다. 기존 열은 수정되지 않고 유지됩니다.

수식은 각 테이블의 레코드에 대해 평가됩니다.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**DropColumns** 함수는 테이블에서 열을 제외합니다.  다른 모든 열은 수정되지 않고 유지됩니다. **DropColumns**는 열을 제외하고 **ShowColumns**는 열을 포함합니다.

**RenameColumns** 함수를 사용하여 테이블에 포함된 열의 이름(바꾸려는 이전 이름)과 테이블에 포함되지 않은 열의 이름(사용하려는 새 이름)을 지정하는 하나 이상의 인수 쌍을 제공하여 하나 이상의 테이블 열 이름을 바꿉니다. 이전 이름은 테이블에 이미 있어야 하고 새 이름이 없어야 합니다. 각 열 이름은 이전 열 이름이거나 새 열 이름이므로 인수 목록에 한 번만 나올 수 있습니다. 열 이름을 기존 열 이름으로 바꾸려면 먼저 **DropColumns**를 사용하여 기존 열을 삭제하거나 하나의 **RenameColumns** 함수를 다른 함수에 중첩하여 기존 열의 이름을 다른 열 중 하나로 바꿉니다.

**ShowColumns** 함수는 테이블의 열을 포함하고 다른 모든 열을 삭제합니다. **ShowColumns**를 사용하여 다중 열 테이블에서 단일 열 테이블을 만들 수 있습니다.  **ShowColumns**는 열을 포함하고 **DropColumns**는 열을 제외합니다.  

이러한 모든 함수의 경우 적용된 변환을 사용하는 새 테이블이 만들어집니다. 원래 테이블은 수정되지 않습니다. 수식을 사용하여 기존 테이블을 수정할 수 없습니다. SharePoint, Common Data Service, SQL Server 및 기타 데이터 원본 목록은 엔터티 및 스키마라고도 하는 테이블의 열을 수정하기 위한 도구를 제공합니다. 이 문서에서 포함된 함수는 추가 사용을 위해 출력 테이블에 원래 테이블을 수정하지 않고 입력 테이블만 변환합니다

이러한 함수에 대한 인수는 위임을 지원합니다. 예를 들어, 관련된 레코드를 가져오는데 인수로 사용된 **Filter** 함수는 **'[dbo]. [ AllListings]'** 데이터 원본이 백만 행을 포함하는 경우라도 모든 리스팅을 검색합니다.

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

그러나 이러한 함수의 출력은 [비-위임 레코드 제한](../delegation-overview.md#non-delegable-limits)의 적용을 받습니다.  이 예제에서는 **RealEstateAgents** 데이터 원본에 레코드가 501개 이상 존재하더라도 500개의 레코드만 반환됩니다.

이런 방식으로 **AddColumns**를 사용하는 경우, **Filter** 함수는 **RealEstateAgents**의 해당 첫 번째 레코드의 각 데이터 원본에 대한 별도 호출을 사용해야 하므로, 많은 경우 네트워크 트래픽이 발생합니다. 만약 **[dbo]. [ AllListings]** 이 아주 작고 변경 되지 않은 경우라면, 앱이 시작할 때 데이터 원본을 캐시하도록 [**OnStart**](signals.md#app)에서 **Collect** 함수를 호출할 수 있습니다. 또는 사용자가 요청하는 경우에만 관련된 레코드를 가져올 수 있도록 앱을 재구성할 수 있습니다.  

## <a name="syntax"></a>구문
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
* *ColumnName(s)* - 필수 항목입니다. 추가할 열의 이름입니다.  이 인수에 대해 문자열(예를 들어 큰따옴표가 포함된 **“Name”** )을 지정해야 합니다.
* *Formula(s)* - 필수 항목입니다.  각 레코드에 대해 평가할 수식입니다. 결과는 해당하는 새 열 값으로 추가됩니다. 이 수식에서 테이블의 다른 열을 참조할 수 있습니다.

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
* *ColumnName(s)* - 필수 항목입니다. 삭제할 열의 이름입니다. 이 인수에 대해 문자열(예를 들어 큰따옴표가 포함된 **“Name”** )을 지정해야 합니다.

**RenameColumns**( *Table*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*, ... ] )

* *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
* *OldColumnName* -필수 항목입니다. 원래 테이블에서 이름을 바꿀 열의 이름입니다. 이 요소는 인수 쌍의 맨 처음(또는 수식에 둘 이상의 쌍이 포함된 경우 각 인수 쌍의 처음)에 나타납니다. 이 이름은 문자열(예를 들어 큰따옴표가 포함된 **“Name”** )이어야 합니다.
* *NewColumnName* - 필수 항목입니다. 교체 이름입니다. 이 요소는 인수 쌍 마지막(또는 수식에 둘 이상의 쌍이 포함된 경우 각 인수 쌍의 마지막)에 나타납니다. 이 인수에 대해 문자열(예를 들어 큰따옴표가 포함된 **“Customer Name”** )을 지정해야 합니다.

**ShowColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
* *ColumnName(s)* - 필수 항목입니다. 포함할 열의 이름입니다. 이 인수에 대해 문자열(예를 들어 큰따옴표가 포함된 **“Name”** )을 지정해야 합니다.

## <a name="examples"></a>예
이 섹션의 예제에서는 다음 테이블의 데이터가 포함된 **IceCreamSales** 데이터 원본을 사용합니다.

![](media/function-table-shaping/icecream.png)

이러한 예제는 모두 **IceCreamSales** 데이터 원본을 수정하지 않습니다. 각 함수는 데이터 원본의 값을 테이블로 변환하고 결과로 해당 값을 반환합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **AddColumns( IceCreamSales, “Revenue”, UnitPrice * QuantitySold )** |**Revenue** 열을 결과에 추가합니다.  각 레코드의 경우 **UnitPrice * QuantitySold**가 평가되고 결과가 새 열에 배치됩니다. |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, “UnitPrice” )** |**UnitPrice** 열을 결과에서 제외합니다. 이 함수를 사용하여 열을 제외하고 **ShowColumns**를 사용하여 포함합니다. |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, “Flavor” )** |**Flavor** 열만 결과에 포함합니다. 이 함수를 사용하여 열을 포함하고 **DropColumns**를 사용하여 제외합니다. |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, “UnitPrice”, “Price”)** |결과에서 **UnitPrice**의 열 이름을 바꿉니다. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, “UnitPrice”, “Price”, “QuantitySold”, “Number”)** |결과에서 **UnitPrice** 및 **QuantitySold** 열의 이름을 바꿉니다. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, “Revenue”,<br>UnitPrice * QuantitySold ),<br>“UnitPrice”, “Price” ),<br>“Quantity” )** |다음 테이블 변환을 수식의 내부부터 순서대로 수행합니다. <ol><li>**UnitPrice * Quantity**의 레코드별 계산을 기반으로 **Revenue** 열을 추가합니다.<li>**UnitPrice**의 이름을 **Price**로 변경합니다.<li>**Quantity** 열을 제외합니다.</ol>  순서는 중요합니다. 예를 들어 이름이 변경된 후에는 **UnitPrice**로 계산할 수 없습니다. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>단계별 가이드

이 항목의 앞부분에서 예제 중 일부를 사용해 보겠습니다.  

1. **[단추](../controls/control-button.md)** 컨트롤을 추가하여 컬렉션을 생성하고 해당 **OnSelect** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Alt 키를 누른 채 단추를 선택하여 수식을 실행합니다.

1. 두 번째 **단추** 컨트롤을 추가하고 해당 **OnSelect** 속성을 다음 수식으로 설정한 다음 실행합니다.

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. **파일** 메뉴에서 **컬렉션**을 선택한 후, **IceCreamSales**를 선택하여 컬렉션을 표시합니다.
 
    이 그래픽에서 볼 수 있듯이 두 번째 수식은 이 컬렉션을 수정하지 않았습니다. **AddColumns** 함수는 읽기 전용 인수로 **IceCreamSales**를 사용합니다. 해당 함수는 인수가 참조하는 테이블을 수정하지 않습니다.
    
    ![수입 열이 포함 되지 않은 아이스크림 판매 컬렉션의 세 개의 레코드를 보여 주는 컬렉션 뷰어](media/function-table-shaping/ice-cream-sales-collection.png)

1. **FirstExample**을 선택합니다.

    이 그림에서 두 번째 수식은 열이 추가된 새 테이블을 반환합니다. **ClearCollect** 함수는 **FirstExample** 컬렉션의 새 테이블을 캡처하며, 원본을 수정하지 않고 함수를 통해 적용된 대로 원래 테이블에 항목을 추가합니다:

    ![새 수입 열이 포함 된 첫 번째 예에서는 컬렉션의 세 개의 레코드를 보여 주는 컬렉션 뷰어](media/function-table-shaping/first-example-collection.png)
