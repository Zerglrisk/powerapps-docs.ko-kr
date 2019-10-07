---
title: GroupBy 및 Ungroup 함수 | Microsoft Docs
description: PowerApps의 GroupBy 및 Ungroup 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: 6354862823122d332c7e70fba08829d3fc8147eb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985046"
---
# <a name="groupby-and-ungroup-functions-in-powerapps"></a>PowerApps의 GroupBy 및 Ungroup 함수
[테이블](../working-with-tables.md)의 [레코드](../working-with-tables.md#records)를 그룹화하고 그룹을 해제합니다.

## <a name="description"></a>설명
**GroupBy** 함수는 하나 이상의 [열](../working-with-tables.md#columns) 값을 기반으로 레코드가 그룹화된 테이블을 반환합니다. 동일한 그룹의 레코드는 단일 레코드에 배치되고 나머지 열의 중첩 테이블을 보유하는 열이 추가됩니다.   

**Ungroup** 함수는 **GroupBy** 프로세스를 되돌립니다. 이 함수는 함께 그룹화된 레코드를 별도의 레코드로 분리하는 테이블을 반환합니다.

**GroupBy**를 사용하여 레코드를 그룹화하고, 반환되는 테이블을 수정한 다음, **Ungroup**을 사용하여 수정된 테이블의 레코드 그룹을 해제할 수 있습니다. 예를 들어 다음과 같은 방법으로 레코드 그룹을 제거할 수 있습니다.

* **GroupBy** 함수를 사용합니다.
* **[Filter](function-filter-lookup.md)** 함수를 사용하여 전체 레코드 그룹을 제거합니다.
* **Ungroup** 함수를 사용합니다.  

그룹화를 기반으로 결과를 집계할 수도 있습니다.

* **GroupBy** 함수를 사용합니다.
* **[Sum](function-aggregates.md)** , **[Average](function-aggregates.md)** 및 기타 집계 함수와 함께 **[AddColumns](function-table-shaping.md)** 함수를 사용하여 그룹 테이블의 집계인 새 열을 추가합니다.
* **[DropColumns](function-table-shaping.md)** 함수를 사용하여 그룹 테이블을 삭제합니다.

**Ungroup**은 **GroupBy**에 공급된 레코드의 원래 순서를 유지하려고 합니다.  이것이 항상 가능하지는 않습니다(예: 원래 테이블에 *공백* 레코드가 있는 경우).

테이블은 문자열이나 숫자처럼 PowerApps의 값입니다. 테이블을 함수의 인수로 지정할 수 있으며 함수는 테이블을 반환할 수 있습니다. **GroupBy**와 **Ungroup**은 테이블을 수정하지 않습니다. 대신 테이블을 인수로 취하여 다른 테이블을 반환합니다. 자세한 내용은 [테이블 작업](../working-with-tables.md)을 참조하세요.

## <a name="syntax"></a>구문
**GroupBy**( *Table*, *ColumnName1* [, *ColumnName2*, ... ], *GroupColumnName* )

* *Table* - 필수 항목입니다. 그룹화할 테이블입니다.
* *ColumnName(s)* - 필수 항목입니다.  레코드를 그룹화할 기준이 되는 *테이블*의 열 이름입니다.  이 열은 결과 테이블의 열이 됩니다.
* *GroupColumnName* - 필수 항목입니다.  *ColumnName(s)* 에 없는 레코드 데이터의 스토리지에 대한 열 이름입니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

**Ungroup**( *Table*, *GroupColumnName* )

* *Table* - 필수 항목입니다. 그룹을 해제할 테이블입니다.
* *GroupColumnName* - 필수 항목입니다. **GroupBy** 함수를 사용하여 레코드 데이터 설정을 포함하는 열입니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

## <a name="examples"></a>예
### <a name="create-a-collection"></a>컬렉션 만들기
1. 단추를 추가하고 단추가 **원본**으로 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정합니다.
2. **원본** 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

```powerapps-dot   
ClearCollect( CityPopulations, 
    { City: "London",    Country: "United Kingdom", Population: 8615000}, 
    { City: "Berlin",    Country: "Germany",        Population: 3562000}, 
    { City: "Madrid",    Country: "Spain",          Population: 3165000}, 
    { City: "Rome",      Country: "Italy",          Population: 2874000}, 
    { City: "Paris",     Country: "France",         Population: 2273000}, 
    { City: "Hamburg",   Country: "Germany",        Population: 1760000}, 
    { City: "Barcelona", Country: "Spain",          Population: 1602000}, 
    { City: "Munich",    Country: "Germany",        Population: 1494000}, 
    { City: "Milan",     Country: "Italy",          Population: 1344000}
)
```

3. Alt 키를 누른 상태에서 **원본** 단추를 선택합니다.
   
    다음 데이터가 포함된 **CityPopulations**라는 [컬렉션](../working-with-data-sources.md#collections)이 생성되었습니다.
   
    ![](media/function-groupby/cities.png)
4. 이 컬렉션을 표시하려면 **파일** 메뉴에서 **컬렉션**을 선택한 다음, **CityPopulations** 컬렉션을 선택합니다.  컬렉션의 처음 5개 레코드가 나타납니다.
   
    ![](media/function-groupby/citypopulations-collection.png)

### <a name="group-records"></a>레코드 그룹화
1. 또 다른 단추를 추가하고 **[Text](../controls/properties-core.md)** 속성을 **"그룹"** 으로 설정합니다.
2. 이 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )**
3. Alt 키를 누른 상태에서 **그룹** 단추를 선택합니다.
   
    **CitiesByCountry**라는 컬렉션이 생성되었으며 이전 컬렉션의 레코드가 **Country** 열을 기준으로 그룹화되어 있습니다.
   
    ![](media/function-groupby/cities-grouped.png)
4. 이 컬렉션의 처음 5개 레코드를 표시하려면 **파일** 메뉴에서 **컬렉션**을 선택합니다.
   
    ![](media/function-groupby/citiesbycountry-collection.png)
5. 한 국가의 도시 인구를 표시하려면 해당 국가(예: 독일)의 **Cities** 열에서 테이블 아이콘을 선택합니다.
   
    ![](media/function-groupby/population-germany.png)

### <a name="filter-and-ungroup-records"></a>레코드 필터링 및 그룹 해제
1. 단추를 추가하고 단추가 **"필터"** 로 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정합니다.
2. 이 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **ClearCollect( CitiesByCountryFiltered, Filter( CitiesByCountry, "e" in Country ) )**
3. Alt 키를 누른 상태에서 추가한 단추를 선택합니다.
   
    **CitiesByCountryFiltered**라는 세 번째 컬렉션이 생성되었습니다. 이 컬렉션에는 이름에 "e"가 포함된 국가(즉, Spain 또는 Italy 제외)만 포함됩니다.
   
    ![](media/function-groupby/cities-grouped-hase.png)
4. 단추를 추가하고 단추가 **"그룹 해제"** 로 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정합니다.
5. 이 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **ClearCollect( CityPopulationsUngrouped, Ungroup( CitiesByCountryFiltered, "Cities" ) )**
   
    결과는 다음과 같습니다.
   
    ![](media/function-groupby/cities-hase.png)

### <a name="aggregate-results"></a>결과 집계
그룹화된 테이블로 수행할 수 있는 다른 작업은 결과를 집계하는 것입니다.  다음 예제에서는 각 국가의 주요 도시 인구를 합산합니다.

1. 단추를 추가하고 단추가 **"합계"** 로 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정합니다.
2. **"합계"** 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **ClearCollect( CityPopulationsSum, AddColumns( CitiesByCountry, "Sum of City Populations", Sum( Cities, Population ) ) )**
   
    결과는 다음과 같습니다.
   
    ![](media/function-groupby/cities-sum.png)
   
    **[AddColumns](function-table-shaping.md)** 는 기본 **CitiesByCountry** 컬렉션으로 시작하여 **Sum of City Populations**라는 새 열을 추가합니다.  이 열의 값은 **Sum( Cities, Population )** 수식을 기반으로 행 단위로 계산됩니다.  **AddColumns**은 각 행에 대한 **Cities** 열(테이블)의 값을 제공하고 **[Sum](function-aggregates.md)** 은 하위 테이블의 각 행에 대한 **Population**을 합산합니다.

    원하는 합계를 얻었으니 **[DropColumns](function-table-shaping.md)** 를 사용하여 하위 테이블을 제거할 수 있습니다.
  
3. 단추를 추가하고 단추가 **“SumOnly”** 로 표시되도록 **[Text](../controls/properties-core.md)** 속성을 설정합니다.
4. **“SumOnly”** 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **ClearCollect( CityPopulationsSumOnly, DropColumns( CityPopulationsSum, "Cities" ) )**
   
    결과는 다음과 같습니다.
   
    ![](media/function-groupby/cities-sum-drop-cities.png)
   
    이 테이블의 그룹을 해제할 필요는 없습니다.

