---
title: Left, Mid 및 Right 함수 | Microsoft Docs
description: PowerApps의 Left, Mid 및 Right 함수에 대한 참조 정보이며, 구문과 예제를 포함하고 있습니다.
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
ms.openlocfilehash: 81220ab8df16dcea74dbdc9db48e692e379e1b4d
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992597"
---
# <a name="left-mid-and-right-functions-in-powerapps"></a>PowerApps의 Left, Mid 및 Right 함수
텍스트 문자열의 왼쪽, 가운데 또는 오른쪽 부분을 추출합니다.

## <a name="description"></a>설명
**Left**, **Mid** 및 **Right** 함수는 문자열의 일부를 반환합니다.

* **Left**는 문자열의 시작 문자를 반환합니다.
* **Mid**는 문자열의 가운데 문자를 반환합니다.
* **Right**는 문자열의 끝 문자를 반환합니다.

단일 문자열을 인수로 지정하면 함수에서 문자열에 대해 요청한 부분을 반환합니다. 문자열이 포함된 단일 열 [테이블](../working-with-tables.md)을 지정하면 함수에서 해당 문자열을 요청한 부분의 단일 열 테이블을 반환합니다. 여러 열 테이블을 지정하면 [테이블 작업](../working-with-tables.md)에서 설명한 대로 단일 열 테이블로 만들 수 있습니다.

시작 위치가 음수이거나 문자열 끝을 초과하는 경우 **Mid**는 *공백*을 반환합니다.  **[Len](function-len.md)** 함수를 사용하여 문자열 길이를 확인할 수 있습니다. 문자열에 포함된 것보다 많은 문자를 요청하면 이 함수는 가능한 한 많은 문자를 반환합니다.

## <a name="syntax"></a>구문
**Left**( *String*, *NumberOfCharacters* )<br>**Mid**( *String*, *StartingPosition*, *NumberOfCharacters* )<br>**Right**( *String*, *NumberOfCharacters* )

* *String* - 필수 항목이며, 결과를 추출할 문자열입니다.
* *StartingPosition* - 필수 항목(**Mid** 전용)이며,  시작 위치입니다.  문자열의 첫 번째 문자는 위치 1입니다.
* *Numberofcharacters* -필수 (**왼쪽** 및 **오른쪽** 만)입니다.  반환할 문자 수입니다.  **Mid** 함수에서 생략 된 경우 함수는 문자열의 끝까지 시작 위치에서 부분을 반환 합니다.

**Left**( *SingleColumnTable*, *NumberOfCharacters* )<br>**Mid**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters* )<br>**Right**( *SingleColumnTable*, *NumberOfCharacters* )

* *SingleColumnTable* - 필수 항목입니다. 결과를 추출할 문자열의 단일 열 테이블입니다.
* *StartingPosition* - 필수 항목(**Mid** 전용)이며,  시작 위치입니다.  문자열의 첫 번째 문자는 위치 1입니다.
* *Numberofcharacters* -필수 (**왼쪽** 및 **오른쪽** 만)입니다.  반환할 문자 수입니다.  **Mid** 함수에서 생략 된 경우 함수는 문자열의 끝까지 시작 위치에서 부분을 반환 합니다.

## <a name="examples"></a>예
### <a name="single-string"></a>단일 문자열
이 섹션의 예제에서는 텍스트 입력 컨트롤을 [데이터 원본](../working-with-data-sources.md)으로 사용합니다. 컨트롤 이름은 **Author**이며, "E. E. Cummings" 문자열을 포함합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Left( Author.Text, 5 )** |문자열의 시작 부분에서 최대 5개 문자를 추출합니다. |"E. E." |
| **Mid( Author.Text, 7, 4 )** |문자열에서 7번째 문자부터 최대 4개 문자를 추출합니다. |"Cumm" |
| **중간 (만든이, 텍스트 7)** |문자열에서 일곱 번째 문자부터 시작 하 여 모든 문자를 추출 합니다. |"Cummings" |
| **Right( Author.Text, 5 )** |문자열의 끝 부분에서 최대 5개 문자를 추출합니다. |"mings" |

### <a name="single-column-table"></a>단일 열 테이블
이 섹션의 각 예제에서는 **People**이라는 데이터 원본의 **Address** [열](../working-with-tables.md#columns)에서 문자열을 추출하고, 결과가 포함된 단일 열 테이블을 반환합니다.

![](media/function-left-mid-right/people-table.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 8 )** |각 문자열에서 처음 8개 문자를 추출합니다. |<style> img { max-width: none } </style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 5, 7 )** |각 문자열에서 다섯 번째 문자부터 시작하여 가운데 7개 문자를 추출합니다. |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 7 )** |각 문자열에서 마지막 7개 문자를 추출합니다. |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>단계별 예제
1. [갤러리에서 이미지 및 텍스트 표시](../show-images-text-gallery-sort-filter.md)에서 설명하는 첫 번째 절차에 따라 **Inventory**라는 [컬렉션](../working-with-data-sources.md#collections)을 가져오거나 만들어 갤러리에 표시합니다.
2. 갤러리에 있는 하위 레이블의 **[Text](../controls/properties-core.md)** 속성을 이 함수로 설정합니다.
   
    **Right(ThisItem.ProductName, 3)**
   
    각 제품 이름의 마지막 세 개 문자가 레이블에 표시됩니다.

