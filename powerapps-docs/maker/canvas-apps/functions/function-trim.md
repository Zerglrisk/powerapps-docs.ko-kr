---
title: Trim 및 TrimEnds 함수 | Microsoft Docs
description: PowerApps의 Trim 및 TrimEnds 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/09/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5997df0d6e2a6a2d6732d10cefa146f4ba6e33dc
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852491"
---
# <a name="trim-and-trimends-functions-in-powerapps"></a>PowerApps의 Trim 및 TrimEnds 함수
텍스트 문자열에서 여분의 공백을 제거합니다.

## <a name="description"></a>설명
**Trim** 함수는 텍스트 문자열에서 단어 사이의 한 칸 공백을 제외한 모든 공백을 제거합니다.  

**TrimEnds** 함수는 텍스트 문자열의 시작과 끝에 있는 모든 공백을 제거하지만 단어 사이의 공백은 남겨둡니다.

단일 텍스트 문자열을 지정하는 경우, 두 함수의 반환 값은 여분의 공백이 제거된 문자열입니다. 문자열이 포함된 단일 열 [테이블](../working-with-tables.md)을 지정하면, 반환 값은 잘린 문자열의 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.

단어 사이의 공백을 제거한다는 면에서 **Trim**은 Microsoft Excel에 있는 동일한 이름의 함수와 일치합니다. 단 **TrimEnds**는 각 문자열의 시작과 끝에서만 공백을 제거하는 프로그래밍 도구와 일치합니다.

## <a name="syntax"></a>구문
**Trim**( *String* )<br>**TrimEnds**( *String* )

* *String* - 필수 항목이며, 공백을 제거할 텍스트 문자열입니다.

**Trim**( *SingleColumnTable* )<br>**TrimEnds**( *SingleColumnTable* )

* *SingleColumnTable* - 필수 항목입니다. 공백을 제거할 문자열의 단일 열 테이블입니다.

## <a name="example"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Trim(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |문자열의 시작과 끝에서 모든 공백을 제거하고 문자열 내에서 여분의 공백을 제거합니다. |"Hello World" |
| **TrimEnds(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |문자열의 시작과 끝에서 모든 공백을 제거합니다. |"Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World" |

다음 예제는 다음과 같은 문자열이 포함된 **Spaces**라는 이름의 단일 열 컬렉션을 사용합니다.

![](media/function-trim/input-strings.png)

이 컬렉션을 만들려면 **[Button](../controls/control-button.md)** 컨트롤의 **OnSelect** 속성을 다음 수식으로 설정하고 미리 보기 모드를 연 다음 단추를 클릭하거나 탭합니다.
<br>**ClearCollect( Spaces, [ "&nbsp;&nbsp;&nbsp;Jane&nbsp;&nbsp;&nbsp;Doe&nbsp;&nbsp;&nbsp;", "&nbsp;&nbsp;&nbsp;&nbsp;Jack&nbsp;&nbsp;&nbsp;and&nbsp;&nbsp;&nbsp;Jill", "Already&nbsp;trimmed", "&nbsp;&nbsp;&nbsp;Venus,&nbsp;&nbsp;&nbsp;Earth,&nbsp;&nbsp;&nbsp;Mars&nbsp;&nbsp;", "Oil&nbsp;and&nbsp;Water&nbsp;&nbsp;&nbsp;" ] )**

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Trim(&nbsp;Spaces&nbsp;)** |**Spaces** 컬렉션의 각 문자열 내에서 여분의 공백을 제거하고 각 문자열의 시작과 끝에 있는 모든 공백을 제거합니다. |<style> img { max-width: none } </style> ![](media/function-trim/output-trim.png) |
| **TrimEnds(&nbsp;Spaces&nbsp;)** |**Spaces** 컬렉션에 있는 각 문자열의 시작과 끝에서 모든 공백을 제거합니다. |<style> img { max-width: none } </style> ![](media/function-trim/output-trimends.png) |

> [!NOTE]
> **파일** 메뉴에서 **컬렉션**을 클릭하거나 탭하여 컬렉션을 표시하면 여분의 공백이 나타나지 않습니다. 문자열 길이를 확인하려면 **[Len](function-len.md)** 함수를 사용하십시오.

