---
title: Concat 및 Concatenate 함수 | Microsoft Docs
description: PowerApps의 Concat 및 Concatenate 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 889f612f3da208d4edfccc43a579ced07933b40d
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216114"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps의 Concat 및 Concatenate 함수

[테이블](../working-with-tables.md)에 있는 텍스트와 문자열의 개별 문자열을 연결합니다.

## <a name="description"></a>설명

**Concatenate** 함수는 개별 문자열과 문자열의 단일 열 테이블을 조합하여 연결합니다. 이 함수를 사용 하 여 개별 문자열을 사용 하 여 때 사용 하는 **&** [연산자](operators.md)합니다.

**Concat** 함수는 테이블의 모든 [레코드](../working-with-tables.md#records)에 적용된 수식의 결과를 연결하여 하나의 문자열을 생성합니다. **[Sum](function-aggregates.md)** 함수가 숫자를 요약하듯 테이블의 문자열을 요약하려면 이 함수를 사용합니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

사용 된 [ **분할** ](function-split.md) 또는 [ **MatchAll** ](function-ismatch.md) 문자열 부분 문자열의 테이블로 분할 하는 함수입니다.

## <a name="syntax"></a>구문

**Concat**( *Table*, *Formula* )

- *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
- *Formula* - 필수 항목입니다.  테이블의 레코드 전체에 적용할 수식입니다.

**Concatenate**( *String1* [, *String2*, ...] )

- *String(s)* - 필수 항목입니다.  개별 문자열 또는 문자열의 단일 열 테이블의 조합입니다.

## <a name="examples"></a>예

이 섹션의 예에서는 이러한 전역 변수를 사용합니다.

- **FirstName** "Jane" =
- **LastName** = "Doe"
- **제품** = ![두 개의 열과 네 개의 행이 있는 테이블](media/function-concatenate/products.png)

앱에서 이러한 전역 변수를 만들려면 삽입을 [ **단추** ](../controls/control-button.md) 설정 해당 **OnSelect** 속성을 다음이 수식:

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

Alt 키를 누른 채로 클릭) 하는 것 (여는 단추를 선택 합니다.

### <a name="concatenate-function-and-the--operator"></a>Concatenate 함수는 & 연산자

이러한 예를 들어 설정 합니다 **텍스트** 의 속성을 [ **레이블** ](../controls/control-text-box.md) 다음 테이블의 첫 번째 열에서 수식에 컨트롤입니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Concatenate(&nbsp;LastName,&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | 값을 연결 **LastName**, 문자열 **","** (쉼표 뒤에 공백이), 및에 값 **FirstName**합니다. | "Doe,&nbsp;Jane" |
| **LastName&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | 사용 하 여 제외 하 고 이전 예제와 동일 합니다 **&** 함수 대신 연산자입니다. | "Doe,&nbsp;Jane" |
| **Concatenate(&nbsp;FirstName,&nbsp;"&nbsp;",&nbsp;LastName&nbsp;)** | 값을 연결 **FirstName**, 문자열 **""** (공백)에 값 **LastName**합니다. | "Jane&nbsp;Doe" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;LastName** | 이전 예제와 동일한 사용 하는 **&** 함수 대신 연산자입니다. | "Jane&nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>단일 열 테이블을 사용 하 여 연결

예를 들어 추가 세로 비어 [ **갤러리** ](../controls/control-gallery.md) 컨트롤 해당 **항목** 속성을 다음 테이블에서 수식 다음 레이블을 갤러리 템플릿을 추가 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Concatenate( "Name:&nbsp;",&nbsp;Products.Name, ",&nbsp;Type:&nbsp;",&nbsp;Products.Type )** | 각 레코드에는 **제품** 테이블에서 연결 문자열 **"이름:"** , 문자열 제품의 이름을 **", 형식:"** 제품의 형식과.  | ![제품 테이블을](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 함수

이러한 예제를 보려면 설정 합니다 **텍스트** 다음 테이블의 첫 번째 열에서 수식에 레이블의 속성입니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Concat( Products, Name & ", " )** | 식을 계산 **이름 & ","** 의 각 레코드에 대 한 **제품** 및 결과 단일 텍스트 문자열로 연결 합니다.  | ", Violin&nbsp;Cello를&nbsp;Trumpet,&nbsp;" |
| **Concat (필터 (&nbsp;제품인&nbsp;형식을&nbsp;=&nbsp;"String"&nbsp;), 이름 및 ",")** | 수식을 평가 **이름 & ","** 의 각 레코드 **제품** 필터를 충족 하는 **형식 = "String"** , 결과 단일 텍스트 문자열로 연결 합니다.   | ", Violin&nbsp;Cello,&nbsp;" |

### <a name="trimming-the-end"></a>끝 트리밍

마지막 두 예로 추가 "," 결과의 끝입니다. 함수, 쉼표 및 공간을 추가 합니다 **이름을** 마지막 레코드를 포함 하 여 테이블의 모든 레코드의 값입니다.

일부 경우에 이러한 추가 문자 중요 하지 않습니다. 예를 들어, 한 공백 (경우) 구분 기호는 레이블에 결과 표시 하는 경우에 표시 되지 않습니다. 이러한 추가 문자를 제거 하려는 경우 사용 합니다 [ **왼쪽** ](function-left-mid-right.md) 또는 [ **일치** ](function-ismatch.md) 함수입니다.

이러한 예제를 보려면 설정 합니다 **텍스트** 다음 테이블의 첫 번째 열에서 수식에 레이블의 속성입니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Left( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len(&nbsp;Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2 )** | 결과 반환 합니다 **Concat** 있지만 불필요 한 구분 기호를 형성 하는 마지막 두 문자를 제거 합니다. | ", Violin&nbsp;Cello,&nbsp;Trumpet" |
| **Match( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^(?&lt;trim&gt;.*),&nbsp;$" ).trim** | 문자를 반환 **Concat** ($) 끝에 텍스트 문자열 (^)의 시작 부분에서 불필요 한 쉼표와 끝에 공백이 포함 되지 않습니다. | ", Violin&nbsp;Cello,&nbsp;Trumpet" |

### <a name="split-and-matchall"></a>분할 및 MatchAll

사용 하는 경우 **Concat** 는 구분 기호로 결합 하 여 작업을 되돌릴 수 있습니다 합니다 **분할** 하 고 **MatchAll** 함수입니다.

예를 빈, 세로 갤러리 추가 설정 해당 **항목** 속성을 다음 표에 수식으로 다음 레이블을 갤러리 템플릿을 추가 합니다.

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Split( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), ", " )** | 구분 기호를 사용 하 여 텍스트 문자열을 분할 **","** 합니다. 결과의 마지막 행에 빈 문자열 이므로 문자열 쉼표 및 공백을 사용 하 여 종료 합니다.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll( Concat(&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "[^\s,]+" ).FullMatch** | 공백이 나 쉼표 아닌 문자를 기준으로 텍스트 문자열을 분할 합니다. 이 수식 문자열의 끝에 공백이 고 여분의 쉼표를 제거합니다. | ![Table](media/function-concatenate/matchall.png)