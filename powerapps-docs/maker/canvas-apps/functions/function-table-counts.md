---
title: Count, CountA, CountIf 및 CountRows 함수 | Microsoft Docs
description: PowerApps의 Count, CountA, CountIf 및 CountRows 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 70950a52050226a25270be7531f4589671f0d46f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983891"
---
# <a name="count-counta-countif-and-countrows-functions-in-powerapps"></a>PowerApps의 Count, CountA, CountIf 및 CountRows 함수
[테이블](../working-with-tables.md)에 있는 모든 [레코드](../working-with-tables.md#records)의 수를 계산하거나 조건을 충족하는 모든 레코드의 수를 계산합니다.

## <a name="description"></a>설명
**Count** 함수는 단일 열 테이블에서 숫자가 포함된 레코드 수를 계산합니다.

**CountA** 함수는 단일 열 테이블에서 *공백*이 아닌 레코드 수를 계산합니다. 이 함수에는 [빈](function-isblank-isempty.md) 텍스트("")가 포함됩니다.

**CountIf** 함수는 테이블에서 논리 수식에 대해 **true**인 레코드 수를 계산합니다.  수식에서 테이블의 [열](../working-with-tables.md#columns)을 참조할 수 있습니다.

**CountRows** 함수는 테이블의 레코드 수를 계산합니다.

이러한 함수 각각은 숫자를 반환합니다.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>구문
**Count**( *SingleColumnTable* )<br>
**CountA**( *SingleColumnTable* )

* *SingleColumnTable* - 필수 항목입니다.  개수를 계산할 레코드의 열입니다.  

**CountIf**( *Table*, *LogicalFormula* )

* *Table* - 필수 항목입니다.  개수를 계산할 레코드의 테이블입니다.
* *LogicalFormula* - 필수 항목이며,  테이블의 각 레코드를 평가하는 수식입니다.  이 수식에 대해 **true**를 반환하는 레코드의 수가 계산됩니다.  수식에서 테이블의 열을 참조할 수 있습니다.

**CountRows**( *Table* )

* *Table* - 필수 항목입니다.  개수를 계산할 레코드의 테이블입니다.

## <a name="example"></a>예
1. [갤러리에서 이미지 및 텍스트 표시](../show-images-text-gallery-sort-filter.md)에서 설명하는 첫 번째 하위 절차에 따라 **Inventory**라는 [컬렉션](../working-with-data-sources.md#collections)을 가져오거나 만듭니다.
2. 레이블을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **CountIf(Inventory, UnitsInStock < 30)**
   
    두 제품(Ganymede 및 Callisto)의 재고가 30개 단위 미만이므로 레이블에 **2**가 표시됩니다.
3. 다른 레이블을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **CountA(Inventory.UnitsInStock)**
   
    레이블에 **UnitsInStock** 열에서 비어 있지 않은 셀의 수로 **5**가 표시됩니다.
4. 다른 레이블을 추가하고, **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   
    **CountRows(Inventory)**
   
    컬렉션에 5개 행이 있으므로 레이블에 **5**가 표시됩니다.

