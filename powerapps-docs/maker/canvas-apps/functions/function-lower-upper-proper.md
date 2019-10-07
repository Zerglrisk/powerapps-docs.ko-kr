---
title: Lower, Upper 및 Proper 함수 | Microsoft Docs
description: PowerApps에서 Lower, Upper 및 Proper 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: 413f07bcca9d238ab1a6f6b020f1d1436f2ca737
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984547"
---
# <a name="lower-upper-and-proper-functions-in-powerapps"></a>PowerApps에서 Lower, Upper 및 Proper 함수
텍스트 문자열의 문자를 모두 소문자, 모두 대문자 또는 적절한 대소문자로 변환합니다.

## <a name="description"></a>설명
**Lower**, **Upper** 및 **Proper** 함수는 문자열의 대/소문자를 변환합니다.

* **Lower**는 모든 대문자를 소문자로 변환합니다.
* **Upper**는 모든 소문자를 대문자로 변환합니다.
* **Proper**는 모든 단어의 첫 글자가 소문자인 경우 대문자로 변환하고 다른 모든 대문자를 소문자로 변환합니다.

세 함수는 모두 글자가 아닌 문자를 무시합니다.

단일 문자열을 전달하면 반환 값은 해당 문자열의 변환된 버전입니다.  문자열이 포함된 단일 열 [테이블](../working-with-tables.md)을 전달하면, 반환 값은 변환된 문자열의 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.

## <a name="syntax"></a>구문
**Lower**( *String* )<br>**Upper**( *String* )<br>**Proper**( *String* )

* *String* - 필수 항목이며, 변환할 문자열입니다.

**Lower**( *SingleColumnTable* )<br>**Upper**( *SingleColumnTable* )<br>**Proper**( *SingleColumnTable* )

* *SingleColumnTable* - 필수 항목입니다. 변환할 문자열의 단일 열 테이블입니다.

## <a name="examples"></a>예
### <a name="single-string"></a>단일 문자열
이 섹션의 예제에서는 **Author**라는 텍스트 입력 컨트롤을 [데이터 원본](../working-with-data-sources.md)으로 사용합니다. “E. E. CummINGS” 문자열을 포함하는 컨트롤입니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Lower(&nbsp;Author.Text&nbsp;)** |문자열의 모든 대문자를 소문자로 변환합니다. |“e. e. cummings” |
| **Upper(&nbsp;Author.Text&nbsp;)** |문자열의 모든 소문자를 대문자로 변환합니다. |“E. E. CUMMINGS” |
| **Proper(&nbsp;Author.Text&nbsp;)** |모든 단어의 첫 글자가 소문자인 경우 대문자로 변환하고 다른 모든 대문자를 소문자로 변환합니다. |“E. E. Cummings” |

### <a name="single-column-table"></a>단일 열 테이블
이 섹션의 예제에서는 다음 데이터를 포함하는 **People** 데이터 원본의 **Address** [열](../working-with-tables.md#columns)의 문자열을 변환합니다.

![](media/function-lower-upper-proper/people-table.png)

각 수식은 변환된 문자열을 포함하는 단일 열 테이블을 반환합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People,&nbsp;“Address”&nbsp;) )** |소문자인 모든 글자를 대문자로 변환합니다. |<style> img { max-width:none; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People,&nbsp;“Address”&nbsp;) )** |소문자인 모든 글자를 대문자로 변환합니다. |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People,&nbsp;“Address”&nbsp;) )** |단어의 첫 글자가 소문자인 경우 대문자로 변환하고 다른 모든 대문자를 소문자로 변환합니다. |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>단계별 예제
1. **[텍스트 입력](../controls/control-text-input.md)** 컨트롤을 추가하고 이름을 **Source**로 지정합니다.
2. 레이블을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.<br>**Proper(Source.Text)**
3. F5 키를 누른 다음 **WE ARE THE BEST!** 를 **Source** 상자에 입력합니다.<br>레이블이 **WE ARE THE BEST!** 로 표시됩니다.

