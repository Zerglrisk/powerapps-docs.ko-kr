---
title: Distinct 함수 | Microsoft Docs
description: Power Apps의 Distinct 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b77cdf452250fc30e1b8c61867f82e5f109fff49
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731240"
---
# <a name="distinct-function-in-power-apps"></a>Power Apps의 Distinct 함수
[테이블](../working-with-tables.md)의 [레코드](../working-with-tables.md#records)를 요약하여 중복을 제거합니다.

## <a name="description"></a>설명
**Distinct** 함수는 테이블의 각 레코드에 대해 수식을 계산 하 고 중복 값이 제거 된 결과의 열 한 개 테이블을 반환 합니다.  열의 이름은 **Result**입니다.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>구문
**Distinct**( *Table*, *Formula* )

* *Table* - 필수 항목입니다.  계산 대상 테이블입니다.
* *Formula* - 필수 항목입니다.  각 레코드에 대해 계산할 수식입니다.

## <a name="example"></a>예

1. [**Button**](../controls/control-button.md) 컨트롤을 삽입 하 고 **onselect** 속성을이 수식으로 설정 합니다.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ```

1. Alt 키를 누른 채 단추를 선택 합니다.

    수식은 evaluatd이 고 수식 입력줄에서 **CityPopulations** 를 선택 하 여 표시할 수 있는 **CityPopulations** 컬렉션을 만듭니다.

    > [!div class="mx-imgBorder"]
    > 결과 뷰에 표시 된 ![CityPopulations collection](media/function-distinct/citypopulations-create.png)

1. [**데이터 테이블**](../controls/control-data-table.md) 컨트롤을 삽입 하 고 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    수식 입력줄에서 전체 수식을 선택 하 여이 수식의 결과를 볼 수 있습니다.

    > [!div class="mx-imgBorder"]
    > 결과 뷰에 표시 된 고유한 함수의 출력을 ![](media/function-distinct/citypopulations-distinct.png)

1. 데이터 테이블의 속성 창에서 **필드 편집** 링크를 사용 하 여 **결과** 열을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 데이터 테이블에 표시 된 Distinct 함수의 출력을 ![](media/function-distinct/citypopulations-datatable.png)

1. [**레이블**](../controls/control-text-box.md) 컨트롤을 삽입 하 고 **Text** 속성을 수식으로 설정 합니다.

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    이 수식은 [**Sort**](function-sort.md) 함수를 사용 하 여 **Distinct** 의 결과를 정렬 하 고, [**첫**](function-first-last.md) 번째 함수를 사용 하 여 결과 테이블의 첫 번째 레코드를 가져온 다음, **결과** 필드를 추출 하 여 국가 이름만 가져옵니다.

    > [!div class="mx-imgBorder"]
    > 이름으로 첫 번째 국가를 표시 하는 Distinct 함수의 출력을 ![](media/function-distinct/citypopulations-first.png)

     
