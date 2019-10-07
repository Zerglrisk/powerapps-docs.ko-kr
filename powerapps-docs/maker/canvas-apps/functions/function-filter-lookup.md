---
title: Filter, Search 및 LookUp 함수 | Microsoft Docs
description: PowerApps에서 Filter 및 LookUp 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1412cdd79531f70a1c029d7657940200823e5ba0
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992850"
---
# <a name="filter-search-and-lookup-functions-in-powerapps"></a>PowerApps의 Filter, Search 및 LookUp 함수
[테이블](../working-with-tables.md)에서 하나 이상의 [레코드](../working-with-tables.md#records)를 찾습니다.

## <a name="description"></a>설명
**Filter** 함수는 수식을 충족하는 테이블에서 레코드를 찾습니다.  **Filter**를 사용하여 하나 이상의 조건과 일치하는 레코드 집합을 찾고 그렇지 않은 것은 취소합니다.

**LookUp** 함수는 수식을 충족하는 테이블에서 첫 번째 레코드를 찾습니다.  **LookUp**을 사용하여 하나 이상의 조건과 일치하는 단일 레코드를 찾습니다.

둘 다 수식은 각 테이블의 레코드에 대해 평가됩니다.  *true*가 되는 레코드는 결과에 포함됩니다.  일반적인 수식 [연산자](operators.md) 이외에도 하위 문자열 일치에 **[in](operators.md#in-and-exactin-operators)** 및 **[exactin](operators.md#in-and-exactin-operators)** 연산자를 사용할 수 있습니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**Search** 함수는 해당 열 중 하나에 문자열을 포함하는 테이블의 레코드를 찾습니다. 문자열은 열 내의 아무 곳에서나 발생할 수 있습니다. 예를 들어, "rob" 또는 "bert" 검색으로 "Robert"를 포함하는 열에서 일치 항목을 찾습니다. 검색은 대/소문자를 구분합니다. **Filter** 및 **LookUp**과 달리 **Search** 함수는 단일 문자열을 사용하여 수식 대신 일치하도록 합니다.

**Filter** 및 **Search**는 원본 테이블과 동일한 열을 포함하는 테이블 및 조건과 일치하는 레코드를 반환합니다. **LookUp**은 단일 값으로 레코드를 줄이기 위해 수식을 적용한 후 발견한 첫 번째 레코드만을 반환합니다. 레코드가 발견되지 않는 경우 **Filter** 및 **Search**는 [빈](function-isblank-isempty.md) 테이블을 반환하고 **LookUp**은 *공백*을 반환합니다.  

[Table](../working-with-tables.md)은 PowerApps에서 문자열이나 숫자와 같은 값입니다. 테이블을 함수로 전달하거나 함수로부터 반환할 수 있습니다.  **Filter**, **Search** 및 **LookUp**은 테이블을 수정하지 않습니다. 대신 테이블을 인수로 사용하며 여기에서 테이블, 레코드 또는 단일 값을 반환합니다. 자세한 내용은 [테이블 작업](../working-with-tables.md)을 참조하세요.

[!INCLUDE [delegation](../../../includes/delegation.md)]

## <a name="syntax"></a>구문
**Filter**( *Table*, *Formula1* [, *Formula2*, ... ] )

* *Table* - 필수 항목입니다. 검색할 테이블입니다.
* *Formula(s)* - 필수 항목입니다. 각 테이블의 레코드에 의한 수식은 평가됩니다. 함수는 **true**가 되는 모든 레코드를 반환합니다. 테이블 내의 열을 참조할 수 있습니다. 둘 이상의 수식을 제공하는 경우 모든 수식의 결과는 **[And](function-logicals.md)** 함수와 결합됩니다.

**Search**( *Table*, *SearchString*, *Column1* [, *Column2*, ... ] )

* *Table* - 필수 항목입니다. 검색할 테이블입니다.
* *SearchString* -필수 항목입니다. 검색할 문자열입니다. *공백* 또는 빈 문자열인 경우 모든 레코드가 반환됩니다.
* *Column(s)* - 필수 항목입니다. 찾을 *테이블* 내의 열의 이름입니다. 검색할 열은 텍스트를 포함해야 합니다. 열 이름은 문자열이어야 하며 큰따옴표로 묶여야 합니다. 그러나 열 이름은 정적이어야 하며 수식으로 계산될 수 없습니다. 이러한 열의 데이터 내에서 부분 일치 항목으로 *SearchString*이 발견되는 경우 전체 레코드가 반환됩니다.

> [!NOTE]
> 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

**LookUp**( *Table*, *Formula* [, *ReductionFormula* ] )

* *Table* - 필수 항목입니다. 검색할 테이블입니다. UI에서 구문은 함수 상자 위에 *source*로 표시됩니다.
* *Formula* - 필수 항목입니다.
  각 테이블의 레코드에 의한 수식은 평가됩니다. 함수는 **true**가 되는 첫 번째 레코드를 반환합니다. 테이블 내의 열을 참조할 수 있습니다. UI에서 구문은 함수 상자 위에 *condition*으로 표시됩니다.
* *ReductionFormula* - 선택 사항입니다. 이 수식은 발견된 레코드를 통해 평가된 다음 단일 값으로 레코드를 감소시킵니다. 테이블 내의 열을 참조할 수 있습니다. 이 매개 변수를 사용하지 않는 경우 함수는 테이블의 전체 레코드를 반환합니다. UI에서 구문은 함수 상자 위에 *result*로 표시됩니다.

## <a name="examples"></a>예
다음 예에서는 **IceCream** [data source](../working-with-data-sources.md)를 사용합니다.

![](media/function-filter-lookup/icecream.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Filter( IceCream, OnOrder > 0 )** |**OnOrder**가 0보다 큰 레코드를 반환합니다. |<style> img { max-width: none; } </style> ![](media/function-filter-lookup/icecream-onorder.png) |
| **Filter( IceCream, Quantity + OnOrder > 225 )** |**Quantity** 및 **OnOrder** 열의 합이 225보다 큰 레코드를 반환합니다. |![](media/function-filter-lookup/icecream-overstock.png) |
| **Filter( IceCream, "chocolate" in Lower( Flavor ) )** |대문자 또는 소문자와 관계 없이 "chocolate"이라는 단어가 **Flavor** 이름에 나타나는 레코드를 반환합니다. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Filter( IceCream, Quantity < 10  && OnOrder < 20 )** |**Quantity**가 10보다 작고 **OnOrder**가 20보다 작은 레코드를 반환합니다.  이러한 조건과 일치하는 레코드가 없으므로 빈 테이블이 반환됩니다. |![](media/function-filter-lookup/icecream-empty.png) |
| **Search( IceCream, "choc", "Flavor" )** |대문자 또는 소문자와 관계 없이 "choc"이라는 문자열이 **Flavor** 이름에 나타나는 레코드를 반환합니다. |![](media/function-filter-lookup/icecream-chocolate.png) |
| **Search( IceCream, "", "Flavor" )** |검색어가 비어 있으므로 모든 레코드가 반환됩니다. |![](media/function-filter-lookup/icecream.png) |
| **LookUp( IceCream, Flavor = "Chocolate", Quantity )** |적어도 하나가 있는 "Chocolate"과 같은 **Flavor**로 레코드를 검색합니다.  발견된 첫 번째 레코드의 경우 해당 레코드의 **Quantity**를 반환합니다. |100 |
| **LookUp( IceCream, Quantity > 150, Quantity + OnOrder )** |여러 개가 있는 100보다 큰 **Quantity**로 레코드를 검색합니다.  "Vanilla" **Flavor**인 발견된 첫 번째 레코드의 경우 **Quantity** 및 **OnOrder** 열의 합계를 반환합니다. |250 |
| **LookUp( IceCream, Flavor = "Pistachio", OnOrder )** |하나도 없는 "Pistachio"와 같은 **Flavor**로 레코드를 검색합니다.  아무 것도 발견되지 않았으므로 **Lookup**은 *공백*을 반환합니다. |*공백* |
| **LookUp( IceCream, Flavor = "Vanilla" )** |적어도 하나가 있는 "Vanilla"와 같은 **Flavor**로 레코드를 검색합니다.  감소가 없는 수식이 제공됐으므로 전체 레코드가 반환됩니다. |버전과 "바닐라", 수량: 200, OnOrder: 75} |

### <a name="search-user-experience"></a>검색 사용자 환경
많은 앱에서 하나 이상의 문자를 검색 상자에 입력하면 큰 데이터 집합의 레코드 목록을 필터링할 수 있습니다. 입력하는 동안 검색 조건과 일치하는 레코드만 목록에 표시됩니다.

이 문서의 나머지 부분에 있는 예제는 다음 데이터가 포함된 **Customers**라는 목록을 검색한 결과를 보여 줍니다.

![](media/function-filter-lookup/customers.png)

이 데이터 원본을 컬렉션으로 만들려면 **[Button](../controls/control-button.md)** 컨트롤을 만들고 **OnSelect** 속성을 다음 수식으로 설정합니다.

**ClearCollect (Customers, Table ({Name: "Fred 가르시아 섬", 회사: "Northwind Traders"}, {이름: "Cole", 회사: "Contoso"}, {Name: "글 록 enda Johnson", 회사: "Contoso"}, {Name: "Mike Collins", 회사: "놀이 Works"}, {Name: "Colleen Jones", 회사: "놀이 Works"})**

이 예제에서와 같이 화면 하단의 [**갤러리 컨트롤**](../controls/control-gallery.md)에 레코드 목록을 표시할 수 있습니다. 사용자가 관심 있는 레코드를 지정할 수 있도록 화면 맨 위 가까이에 **SearchInput**이라는 [**텍스트 입력**](../controls/control-text-input.md) 컨트롤을 추가합니다.

![](media/function-filter-lookup/customers-ux-unfiltered.png)

사용자가 **SearchInput**에 문자를 입력하면 갤러리의 결과가 자동으로 필터링됩니다. 이 경우 갤러리는 고객 이름(회사 이름 아님)이 **SearchInput**의 문자 시퀀스로 시작하는 레코드를 표시하도록 구성됩니다. 사용자가 검색 상자에 **co**를 입력하면 갤러리에 다음 결과가 표시됩니다.

![](media/function-filter-lookup/customers-ux-startswith-co.png)

**Name** 열을 기준으로 필터링하려면 갤러리 컨트롤의 **Items** 속성을 다음 수식 중 하나로 설정합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) )** |**Customers** 데이터 원본을 **Name** 열의 시작 부분에 검색 문자열이 나타나는 레코드로 필터링합니다. 이 테스트는 대/소문자를 구분하지 않습니다. 사용자가 검색 창에 **co**를 입력하면 갤러리에 **Colleen Jones**와 **Cole Miller**가 표시됩니다. **Mike Collins**는 레코드의 **Name** 열이 검색 문자열로 시작하지 않기 때문에 갤러리에 표시되지 않습니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name )** |**Customers** 데이터 원본을 **Name** 열의 아무 곳에나 검색 문자열이 나타나는 레코드로 필터링합니다. 이 테스트는 대/소문자를 구분하지 않습니다. 사용자가 검색 상자에 **co**를 입력하면 **Colleen Jones,** **Cole Miller,** **Mike Collins**가 갤러리에 표시됩니다. 이러한 레코드의 **Name** 열 어딘가에 검색 문자열이 나타나기 때문입니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name" )** |**in** 연산자를 사용하는 경우와 유사하게, **Search** 함수는 각 레코드의 **Name** 열 내에서 일치하는 항목을 검색합니다. 열 이름은 큰따옴표로 묶어야 합니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-name-co-contains.png) |

**Company** 열과 **Name** 열을 포함하도록 검색 범위를 확장할 수 있습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) &#124;&#124; StartsWith( Company, SearchInput.Text ) )** |**Customers** 데이터 원본을 **Name** 열 또는 **Company** 열이 검색 문자열(예: **co**)로 시작하는 레코드로 필터링합니다.  **StartsWith** 함수 중 하나가 *true*이면 [ **&#124;&#124;** 연산자](operators.md)는 *true*입니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name &#124;&#124; SearchInput.Text in Company )** |**Customers** 데이터 원본을 **Name** 열 또는 **Company** 열에 검색 문자열(예: **co**)이 들어 있는 레코드로 필터링합니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name", "Company" )** |**in** 연산자를 사용하는 경우와 유사하게, **Search** 함수는 **Customers** 데이터 원본에서 **Name** 열 또는 **Company** 열에 검색 문자열(예: **co**)이 들어 있는 레코드를 검색합니다. 여러 열 및 다수의 **in** 연산자를 지정하는 경우 **Search** 함수가 **Filter**보다 읽고 쓰기 쉽습니다. 열 이름은 큰따옴표로 묶어야 합니다. |<style> img { max-width: none } </style> ![](media/function-filter-lookup/customers-all-co-contains.png) |

