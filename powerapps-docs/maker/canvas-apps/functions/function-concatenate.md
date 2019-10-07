---
title: Concat 및 Concatenate 함수 | Microsoft Docs
description: PowerApps의 Concat 및 Concatenate 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992878"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps의 Concat 및 Concatenate 함수

[테이블](../working-with-tables.md)에 있는 텍스트와 문자열의 개별 문자열을 연결합니다.

## <a name="description"></a>설명

**Concatenate** 함수는 개별 문자열과 문자열의 단일 열 테이블을 조합하여 연결합니다. 개별 문자열과 함께이 함수를 사용 하는 경우 **&** [연산자](operators.md)를 사용 하는 것과 같습니다.

**Concat** 함수는 테이블의 모든 [레코드](../working-with-tables.md#records)에 적용된 수식의 결과를 연결하여 하나의 문자열을 생성합니다. **[Sum](function-aggregates.md)** 함수가 숫자를 요약하듯 테이블의 문자열을 요약하려면 이 함수를 사용합니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[**Split**](function-split.md) 또는 [**matchall**](function-ismatch.md) 함수를 사용 하 여 문자열을 하위 문자열의 테이블로 분할 합니다.

## <a name="syntax"></a>구문

**Concat**( *Table*, *Formula* )

- *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
- *Formula* - 필수 항목입니다.  테이블의 레코드 전체에 적용할 수식입니다.

**Concatenate**( *String1* [, *String2*, ...] )

- *String(s)* - 필수 항목입니다.  개별 문자열 또는 문자열의 단일 열 테이블의 조합입니다.

## <a name="examples"></a>예

이 섹션의 예제에서는 다음과 같은 전역 변수를 사용 합니다.

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **Products** =  @ no__t 2 개의 열과 4 개의 행 @ no__t-3이 포함 된 테이블

앱에서 이러한 전역 변수를 만들려면 [**단추**](../controls/control-button.md) 컨트롤을 삽입 하 고 **onselect** 속성을 다음 수식으로 설정 합니다.

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

Alt 키를 누른 채 단추를 클릭 하 여 단추를 선택 합니다.

### <a name="concatenate-function-and-the--operator"></a>함수 및 & 연산자 연결

이러한 예에서는 [**레이블**](../controls/control-text-box.md) 컨트롤의 **Text** 속성을 다음 표의 첫 번째 열에 있는 수식으로 설정 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **연결 (&nbsp;LastName, &nbsp; ", &nbsp;", &nbsp;FirstName @ no__t)** | **LastName**의 값, 문자열 **","** (쉼표 뒤에 공백) 및 **FirstName**의 값을 연결 합니다. | "Doe, &nbsp; Jane" |
| **LastName @ no__t @ no__t @ no__t @-3 ", &nbsp;" &nbsp; @ no__t-6 @ no__t-7FirstName** | 함수 대신 **&** 연산자를 사용 하는 경우를 제외 하 고 이전 예제와 동일 합니다. | "Doe, &nbsp; Jane" |
| **연결 (&nbsp;FirstName, &nbsp; "&nbsp;", &nbsp;LastName @ no__t)** | **FirstName**의 값, 문자열 **""** (단일 공백) 및 **LastName**의 값을 연결 합니다. | "Jane @ no__t-0Doe" |
| **FirstName @ no__t @ no__t @ no__t @ @ "&nbsp;" &nbsp; @ no__t-6 @ no__t-7LastName** | 이전 예제와 동일 합니다. 함수 대신 **&** 연산자를 사용 합니다. | "Jane @ no__t-0Doe" |

### <a name="concatenate-with-a-single-column-table"></a>단일 열 테이블을 사용 하 여 연결

이 예에서는 비어 있는 세로 [**갤러리**](../controls/control-gallery.md) 컨트롤을 추가 하 고 **Items** 속성을 다음 표의 수식으로 설정한 다음 갤러리 템플릿에서 레이블을 추가 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **연결 ("Name: &nbsp;", &nbsp;Products.Name, ", &nbsp;Type: &nbsp;", &nbsp;Products. Type)** | **Products** 테이블의 각 레코드에 대해는 **"name:"** 문자열, 제품 이름, 문자열 **", 유형:"** 및 제품 유형을 연결 합니다.  | ![제품 표](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 함수

이러한 예에서는 레이블의 **Text** 속성을 다음 표의 첫 번째 열에 있는 수식으로 설정 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Concat (제품, 이름 & ",")** | 각 **제품** 레코드에 대해 식 **이름 & ","** 를 평가 하 고 결과를 하나의 텍스트 문자열로 연결 합니다.  | "바이올린, &nbsp;Cello, &nbsp;Trumpet, &nbsp;" |
| **Concat (Filter (&nbsp; Products, &nbsp;Type @ no__t-3 @ no__t-4 @ no__t "String" &nbsp;), Name & ",")** | 필터 **유형 = "String"** 을 충족 하는 **제품** 의 각 레코드에 대해 수식 **이름 & ","** 을 계산 하 고 결과를 단일 텍스트 문자열로 연결 합니다.   | "바이올린, &nbsp;Cello, &nbsp;" |

### <a name="trimming-the-end"></a>끝 트리밍

마지막 두 예제에는 결과의 끝에 추가 ","가 포함 되어 있습니다. 함수는 마지막 레코드를 포함 하 여 테이블에 있는 모든 레코드의 **이름** 값에 쉼표와 공백을 추가 합니다.

경우에 따라 이러한 추가 문자는 중요 하지 않습니다. 예를 들어 레이블에 결과를 표시 하는 경우 단일 공백 구분 기호가 나타나지 않습니다. 이러한 추가 문자를 제거 하려면 [**Left**](function-left-mid-right.md) 또는 [**Match**](function-ismatch.md) 함수를 사용 합니다.

이러한 예에서는 레이블의 **Text** 속성을 다음 표의 첫 번째 열에 있는 수식으로 설정 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Left (Concat (&nbsp; Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t ", &nbsp;" &nbsp;), Len (&nbsp;Concat (&nbsp;Products, 0Name @ no__t-11 @ no__t-12 @ no__t ", 4" 5) 6) 7 @ no__t-18 @ no__t-192)** | **Concat** 의 결과를 반환 하지만 불필요 한 구분 기호를 구성 하는 마지막 두 문자를 제거 합니다. | "바이올린, &nbsp;Cello, &nbsp;Trumpet" |
| **Match (Concat (&nbsp; Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t ", &nbsp;" &nbsp;), "^ (? &lt;trim @ no__t-9. *), @no__t-$10"). trim** | 텍스트 문자열 (^)의 시작 부분에서 끝 ($)으로의 **Concat** 문자를 반환 하지만 끝에 원치 않는 쉼표와 공백을 포함 하지 않습니다. | "바이올린, &nbsp;Cello, &nbsp;Trumpet" |

### <a name="split-and-matchall"></a>분할 및 MatchAll

구분 기호를 사용 하 여 **Concat** 을 사용한 경우 **Split** 및 **matchall** 함수를 결합 하 여 작업을 되돌릴 수 있습니다.

이러한 예제에서는 빈 세로 갤러리를 추가 하 고 **Items** 속성을 다음 표의 수식으로 설정한 다음 갤러리 템플릿에서 레이블을 추가 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Split (Concat (&nbsp; Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t ", &nbsp;" &nbsp;), ",")** | **","** 구분 기호를 사용 하 여 텍스트 문자열을 분할 합니다. 문자열이 쉼표와 공백으로 끝나지만 결과의 마지막 행은 빈 문자열입니다.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp; Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t ", &nbsp;" &nbsp;), "[^ \s,] +"). FullMatch** | 공백이 나 쉼표가 아닌 문자를 기준으로 텍스트 문자열을 분할 합니다. 이 수식은 문자열의 끝에 있는 추가 쉼표와 공백을 제거 합니다. | ![Table](media/function-concatenate/matchall.png)