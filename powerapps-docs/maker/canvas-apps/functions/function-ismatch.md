---
title: IsMatch, Match 및 MatchAll 함수 | Microsoft Docs
description: PowerApps의 IsMatch, Match 및 MatchAll 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ac6e5196de03a3c2d292696f1216c443f4c5b7e6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992664"
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>PowerApps의 IsMatch, Match 및 MatchAll 함수
패턴을 기반으로 하 여 텍스트 문자열의 일부를 찾거나 일치 하는지 여부를 테스트 합니다.

## <a name="description"></a>설명
**IsMatch** 함수는 텍스트 문자열이 일반 문자, 미리 정의된 패턴 또는 [정규식](#regular-expressions)을 구성할 수 있는 패턴과 일치하는지 여부를 테스트합니다.  **Match** 및 **matchall** 함수는 하위 일치를 포함 하 여 일치 된 항목을 반환 합니다.  

**IsMatch**를 사용하여 사용자가 **[Text input](../controls/control-text-input.md)** 컨트롤에 입력한 것의 유효성을 검사합니다. 예를 들어, 결과가 데이터 원본에 저장되기 전에 사용자가 유효한 이메일 주소를 입력했는지 여부를 확인할 수 있습니다. 항목이 조건과 일치하지 않는 경우 사용자에게 항목을 수정하도록 하는 다른 컨트롤을 추가합니다.

**Match** 를 사용 하 여 패턴과 일치 하는 첫 번째 텍스트 문자열 **을 추출** 하면 일치 하는 모든 텍스트 문자열을 추출할 수 있습니다. 복합 문자열을 구문 분석 하기 위해 하위 일치 항목을 추출할 수도 있습니다.   

**일치** 는 첫 번째로 발견 된 일치 항목에 대 한 정보 레코드를 반환 하 고 **matchall** 은 찾은 모든 일치 항목에 대 한 레코드 테이블을 반환 합니다. 레코드에 포함 된 레코드는 다음과 같습니다.

| 열 | 유형 | 설명 |
|----|----|----|
| *명명 된&#8209;하위 일치 또는&#8209;하위 항목 일치* | Text | 각 명명 된 하위 항목에는 자체 열이 있습니다. **(? @No__t-1*이름*&gt;** ...을 사용 하 여 명명 된 하위 일치 항목을 만듭니다. 정규식의 명명 된 하위 일치가 미리 정의 된 열 (아래) 중 하 나와 동일한 이름을 가진 경우 하위 일치가 우선적으로 적용 되 고 경고가 생성 됩니다. 이 경고를 방지 하려면 하위 항목의 이름을 바꿉니다. |
| **FullMatch** | Text | 일치 된 모든 텍스트 문자열입니다. |
| **StartMatch** | 번호 | 입력 텍스트 문자열 내에서 일치 항목의 시작 위치입니다. 문자열의 첫 번째 문자는 1을 반환 합니다. | 
| **부분 일치** | 텍스트의 단일 열 테이블 (열 **값**) | 정규식에 표시 되는 순서 대로 명명 된 하위 항목 및 명명 되지 않은 하위 항목의 테이블입니다. 일반적으로 명명 된 하위 일치는와 함께 사용 하기 쉬우며 권장 됩니다. [**ForAll**](function-forall.md) 함수 또는 [**Last**](function-first-last.md)( [**firstn**](function-first-last.md) **(...)) 함수** 를 사용 하 여 개별 하위 항목에 대 한 작업을 수행할 수 있습니다. 정규식에 정의 된 하위 일치가 없는 경우이 테이블은 표시 되지만 비어 있습니다. |

이러한 함수는 [**Matchoptions**](#match-options)를 지원 합니다. 기본적으로: 
- 이러한 함수는 대/소문자를 구분 하는 일치를 수행 합니다. 대/소문자를 구분 하지 않는 일치를 수행 하려면 **IgnoreCase** 를 사용 합니다.    
- **IsMatch** 는 전체 텍스트 문자열 (**전체** matchoption)과 일치 하는 반면 **일치** 및 **matchoption** 검색은 텍스트 문자열 (matchoption**포함** )의 모든 위치에서 일치 항목을 검색 합니다. 시나리오에 적합 한 **Complete**, **Contains**, **시작 문자**또는 **EndsWith** 를 사용 합니다.

**IsMatch**는 텍스트 문자열이 패턴과 일치하는 경우 *true*를 반환하고 그렇지 않은 경우 *false*를 반환합니다. **Match** 는 [**isblank**](function-isblank-isempty.md) 함수를 사용 하 여 테스트할 수 있는 일치 항목이 없으면 *blank* 를 반환 합니다. **Matchall** 은 [**IsEmpty**](function-isblank-isempty.md) 함수를 사용 하 여 테스트할 수 있는 일치 항목이 없으면 빈 테이블을 반환 합니다.

**Matchall** 을 사용 하 여 텍스트 문자열을 분할 하는 경우 **[split](function-split.md)** 함수를 사용 하는 것이 좋습니다 .이 함수를 사용 하는 것이 더 간단 합니다.

## <a name="patterns"></a>패턴
이러한 함수를 사용 하는 핵심은 일치 시킬 패턴을 설명 하는 것입니다. 다음의 조합으로 텍스트 문자열에서 패턴을 설명합니다.

* **"abc"** 또는 **"123"** 과 같은 일반 문자
* **Letter**, **MultipleDigits** 또는 **Email**과 같은 미리 정의된 패턴 (**Match** 열거는 이러한 패턴을 정의합니다.)
* **"\D + \s + \d +"** 또는 **"[a-z] +"** 와 같은 일반 식 코드

문자열 연결 연산자를 사용 하 여 이러한 요소를 결합 합니다 [ **&** ](operators.md). 예를 들어, **"abc" & Digit & "\s+"** 는 "a", "b" 및 "c", 그 뒤에 0~9의 숫자, 그 뒤에 최소 하나의 공백 문자가 오는 문자와 일치하는 유효한 패턴입니다.

### <a name="ordinary-characters"></a>일반 문자
가장 간단한 패턴은 정확히 일치되는 일반 문자의 시퀀스입니다.

예를 들어 **IsMatch** 함수와 함께 사용 하는 경우 문자열 "hello"는 패턴 **"hello"** 와 정확히 일치 합니다. 그 이상 그 이하도 아닙니다. 문자열 "hello!" 는 끝에 느낌표가 오고 문자 "h"에 대 한 대/소문자가 잘못 되었기 때문에 패턴과 일치 하지 않습니다. (이 동작을 수정하는 방법은 [MatchOptions](#match-options)를 참조하세요.)

패턴 언어에서 특정 문자는 특별한 용도로 예약되어 있습니다. 이러한 **@no__t** 문자를 사용 하려면 문자를 문자 그대로 사용 하거나이 항목의 뒷부분에서 설명 하는 미리 정의 된 패턴 중 하나를 사용 하 여 문자를 문자 그대로 사용 하거나이 항목의 뒷부분에 설명 된 미리 정의 된 패턴 중 하나를 사용 합니다. 이 테이블은 특수 문자를 나열합니다.

| 특수 문자 | 설명 |
| --- | --- |
| **.** |점 또는 마침표 |
| **?** |물음표 |
| **&#42;** |별표 |
| **\+** |더하기 |
| **( )** |괄호 |
| **[ ]** |대괄호 |
| **{ }** |중괄호 |
| **^** |캐럿 |
| **$** |달러 기호 |
| **\|** |세로 막대 또는 파이프 |
| **\\** |백슬래시 |

예를 들어 "Hello?"를 찾아 볼 수 있습니다. 패턴을 사용 하 여 **"Hello\\?"** 물음표 앞에 백슬래시와.

### <a name="predefined-patterns"></a>미리 정의된 패턴
미리 정의 된 패턴은 문자 집합 또는 여러 문자 시퀀스 중 하나를 일치 시키는 간단한 방법을 제공 합니다. [문자열 연결 연산자 **&** ](operators.md) 를 사용 하 여 사용자 고유의 텍스트 문자열을 **Match** 열거형의 멤버와 결합 합니다.

| 열거형 일치 | 설명 | 정규식 |
| --- | --- | --- |
| **Any** |문자와 일치합니다. |`.` |
| **Comma** |쉼표와 일치합니다. |`,` |
| **Digit** |단일 숫자("0"부터 "9")와 일치합니다. |`\d` |
| **Email** |"at" 기호("\@")를 포함하는 이메일 주소 및 점(".")을 포함하는 도메인 이름과 일치합니다. |`.+\@.+\\.[^\\.]{2,}` |
| **Hyphen** |하이픈과 일치합니다. |`\-` |
| **LeftParen** |왼쪽 괄호"("와 일치합니다. |`\(` |
| **Letter** |문자와 일치합니다. |`\p{L}` |
| **MultipleDigits** |하나 이상의 숫자와 대응 합니다. |`\d+` |
| **MultipleLetters** |하나 이상의 문자와 일치합니다. |`\p{L}+` |
| **MultipleNonSpaces** |공백을 추가 하지 않는 하나 이상의 문자 (공백, 탭 또는 줄 바꿈)와 대응 합니다. |`\S+` |
| **MultipleSpaces** |공백 (공백, 탭 또는 줄 바꿈)을 추가 하는 하나 이상의 문자와 일치 합니다. |`\s+` |
| **NonSpace** |공백을 추가하지 않는 단일 문자와 일치합니다. |`\S` |
| **OptionalDigits** |0개, 1개 또는 더 많은 숫자와 일치합니다. |`\d*` |
| **OptionalLetters** |0개, 1개 또는 더 많은 문자와 일치합니다. |`\p{L}*` |
| **OptionalNonSpaces** |공백을 추가하지 않는 0개, 1개 또는 더 많은 문자와 일치합니다. |`\S*` |
| **OptionalSpaces** |공백을 추가하는 0개, 1개 또는 더 많은 문자와 일치합니다. |`\s*` |
| **Period** |마침표 또는 점(".")과 일치합니다. |`\.` |
| **RightParen** |오른쪽 괄호")"와 일치합니다. |`\)` |
| **Space** |공백을 추가하는 문자와 일치합니다. |`\s` |

예를 들어, 패턴 **"A" & MultipleDigits**는 하나 이상의 숫자가 뒤에 오는 문자 "A"와 일치합니다.  

### <a name="regular-expressions"></a>정규식
이러한 함수에서 사용 하는 패턴은 [정규식](https://en.wikipedia.org/wiki/Regular_expression)입니다. 이 항목의 앞부분에서 설명 하는 일반 문자 및 미리 정의 된 패턴은 정규식을 작성 하는 데 도움이 됩니다.  

정규식은 매우 강력하고 여러 프로그래밍 언어에서 사용할 수 있으며 다양한 목적에 사용됩니다. 또한 종종 임의의 문장 부호 시퀀스와 같이 보일 수 있습니다. 이 문서에서는 정규식의 모든 측면을 설명 하지는 않지만 다양 한 정보, 자습서 및 도구를 웹에서 사용할 수 있습니다.  

정규식은 다양 한 언어로 제공 되며 PowerApps는 JavaScript 언어의 변형을 사용 합니다. 구문에 대 한 소개는 [정규식 구문](https://msdn.microsoft.com/library/1400241x.aspx) 을 참조 하세요. 명명 된 하위 일치 (간혹 명명 된 캡처 그룹 이라고 함)가 지원 됩니다.

- 명명 된 하위 일치: **(? &lt;*name*&gt; ...)**
- 명명 된 역참조: **\\k @ no__t-2*이름*&gt;**

이 항목의 앞부분에 나오는 enum enum 표에서 각 **열거형은 해당** 정규식과 동일한 행에 표시 됩니다.

## <a name="match-options"></a>일치 옵션
문자열 연결 연산자 ( **&amp;** )를 사용 하 여 결합할 수 있는 하나 이상의 옵션을 지정 하 여 이러한 함수의 동작을 수정할 수 있습니다.  

| MatchOptions 열거형 | 설명 | 정규식에 대 한 영향 |
| --- | --- | --- |
| **BeginsWith** |패턴은 텍스트의 시작 부분에서 일치해야 합니다. |**^** 를 정규식의 시작 부분에 추가합니다. |
| **Complete** |**IsMatch**에 대 한 기본값입니다. 패턴은 전체 텍스트 문자열을 시작부터 끝까지 일치 해야 합니다. |시작에 **^** 을 추가 하 고 정규식의 끝에 **$** 을 추가 합니다. |
| **Contains** |**Match** 및 **matchall**에 대 한 기본값입니다. 패턴은 텍스트의 어딘가에 나타나야 하지만 시작 또는 끝일 필요가 없습니다. |정규식을 수정하지 않습니다. |
| **EndsWith** |패턴은 텍스트 문자열의 끝과 일치 해야 합니다. |**$** 를 정규식의 끝 부분에 추가합니다. |
| **IgnoreCase** |는 대 문자와 소문자를 동일 하 게 처리 합니다. 기본적으로 일치는 대/소문자 구분입니다. |정규식을 수정하지 않습니다. 이 옵션은 정규식에 대 한 표준 "i" 한정자와 동일 합니다.  |
| **Multiline** |여러 줄과 일치합니다. |정규식을 수정하지 않습니다. 이 옵션은 정규식에 대 한 표준 "m" 한정자와 동일 합니다. |

**Matchall** 을 사용 하는 것은 정규식에 표준 "g" 한정자를 사용 하는 것과 같습니다.

## <a name="syntax"></a>구문
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 필수 항목입니다. 테스트할 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 텍스트 문자열로 테스트할 패턴입니다. **일치** 하는 열거형이 정의 하는 미리 정의 된 패턴을 연결 하거나 정규식을 제공 합니다. *패턴* 은 변수, 데이터 원본 또는 앱이 실행 될 때 변경 되는 기타 동적 참조가 없는 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. **Matchoptions** 열거형 값의 텍스트 문자열 조합입니다. 기본적으로 **MatchOptions.Complete**가 사용됩니다.

**Match**( *Text*, *Pattern* [, *Options* ])

* *Text* – 필수 항목입니다. 일치 시킬 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 텍스트 문자열로 일치 시킬 패턴입니다. **일치** 하는 열거형이 정의 하는 미리 정의 된 패턴을 연결 하거나 정규식을 제공 합니다. *패턴* 은 변수, 데이터 원본 또는 앱이 실행 될 때 변경 되는 기타 동적 참조가 없는 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. **Matchoptions** 열거형 값의 텍스트 문자열 조합입니다. 기본적으로 **Matchoptions. Contains** 가 사용 됩니다.

**Matchall**( *Text*, *Pattern* [, *Options* ])

* *Text* – 필수 항목입니다. 일치 시킬 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 텍스트 문자열로 일치 시킬 패턴입니다. **일치** 하는 열거형이 정의 하는 미리 정의 된 패턴을 연결 하거나 정규식을 제공 합니다. *패턴* 은 변수, 데이터 원본 또는 앱이 실행 될 때 변경 되는 기타 동적 참조가 없는 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. **Matchoptions** 열거형 값의 텍스트 문자열 조합입니다. 기본적으로 **Matchoptions. Contains** 가 사용 됩니다.

## <a name="ismatch-examples"></a>IsMatch 예제
### <a name="ordinary-characters"></a>일반 문자
앱에 **TextInput1**이라는 **Text input** 컨트롤이 포함되어 있다고 가정합니다. 사용자는 데이터베이스에 저장되도록 이 컨트롤에 값을 입력합니다.   

사용자는 **TextInput1**에 **Hello world**를 입력합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| `IsMatch( TextInput1.Text, "Hello world" )` |사용자의 입력이 문자열 "Hello w"와 정확히 일치 하는지 여부를 테스트 합니다. |**true** |
| `IsMatch( TextInput1.Text, "Good bye" )` |사용자의 입력이 정확히 "좋은 bye" 문자열과 정확히 일치 하는지 테스트 합니다. |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains )` |사용자의 입력이 단어 "hello" (대/소문자 구분)를 포함 하는지 여부를 테스트 합니다. |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )` |사용자의 입력이 단어 "hello"(대/소문자 구분하지 않음)를 포함하는지 여부를 테스트합니다. |**true** |

### <a name="predefined-patterns"></a>미리 정의된 패턴

|                                                            수식                                                            |                                                                설명                                                                |  결과   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              미국 사회 보장 번호와 일치합니다.                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com", Email )`                                            |                                                         이메일 주소와 일치합니다.                                                          | **true**  |
|                              `IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )`                               |                                   숫자, 마침표, 0개 이상의 숫자 시퀀스와 일치합니다.                                   | **true**  |
|                                `IsMatch( "123", MultipleDigits & Period & OptionalDigits )`                                 | 숫자, 마침표, 0개 이상의 숫자 시퀀스와 일치합니다. 텍스트에 마침표를 표시 하지 않으므로이 패턴은 일치 하지 않습니다. | **false** |

### <a name="regular-expressions"></a>정규식

|                                                                              수식                                                                              |                                                                                                                                  설명                                                                                                                                   |  결과   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986", "\d+" )`                                                                   |                                                                                                                    0 보다 큰 정수를 찾습니다.                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02", "\d+(\.\d\d)?" )`                                                              |                                        양수 통화 금액과 일치합니다. 입력에 소수점이 포함 된 경우에는 소수점 뒤에 두 개의 숫자 문자도 입력에 포함 되어야 합니다. 예를 들어, 3.00은 유효하지만 3.1은 유효하지 않습니다.                                         | **true**  |
|                                                            `IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )`                                                             |                                                        양수 또는 음수 통화 금액과 일치합니다. 입력에 소수점이 포함 된 경우에는 소수점 뒤에 두 개의 숫자 문자도 입력에 포함 되어야 합니다.                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )`                                                        | 미국 사회 보장 번호와 일치합니다. 제공된 입력 필드의 형식, 유형 및 길이의 유효성을 검사합니다. 일치 시킬 문자열은 세 개의 숫자, 대시, 대시, 숫자 4 자 순서로 구성 되어야 합니다. | **true**  |
|                                                         `IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               이전 예제와 같지만 하이픈 중 하나가 입력에서 제자리에 있지 않습니다.                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        하나 이상의 숫자와 하나 이상의 영문자 외에도 8, 9 또는 10 자를 포함 해야 하는 강력한 암호의 유효성을 검사 합니다. 문자열은 특수 문자를 포함할 수 없습니다.                                        | **false** |
| `IsMatch( "<https://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     http, https 또는 ftp URL의 유효성을 검사합니다.                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>Match 및 MatchAll 예제

| 수식 | 설명 | 결과 |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>" & Match.Email & ")>"` | 연락처 정보의 전자 메일 부분만 추출 합니다.  | {<br>전자 메일: &nbsp; "bob.jones@contoso.com",<br>FullMatch: &nbsp; "&lt; @ no__t >",<br>부분 일치: &nbsp; [&nbsp; "bob.jones@contoso.com" &nbsp;],<br>StartMatch: pt<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>", "<(?<email>" & Match.Email & ")>"` | 연락처 정보의 전자 메일 부분만 추출 합니다. 올바른 주소 (@ 기호가 없음)를 찾을 수 없으므로 함수는 *blank*를 반환 합니다. | *공백* |  
| `Match( Language(), "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | **[언어 함수에서](function-language.md)** 반환 하는 언어 태그의 언어, 스크립트 및 영역 부분을 추출 합니다. 이러한 결과는 미국을 반영 합니다. 더 많은 예제는 [ **언어** 함수 설명서](function-language.md) 를 참조 하세요.  **(?:** 연산자는 다른 하위 일치를 만들지 않고 문자를 그룹화 합니다. | {<br>언어: "en",<br>script: *blank*, <br>국가별 "US",<br>FullMatch: "en-us", <br>부분 일치: ["en", "", "US"], <br>StartMatch: 1<br>} 
| `Match( "PT2H1M39S", "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | ISO 8601 기간 값에서 시간, 분 및 초를 추출 합니다. 추출 된 숫자는 여전히 텍스트 문자열에 있습니다. 수치 연산을 수행 하기 전에 [**값**](function-value.md) 함수를 사용 하 여 숫자로 변환 합니다.  | {<br> 시간의 "2",<br>내 "1",<br>까지의 "39",<br>FullMatch: "PT2H1M39S",<br>부분 일치: &nbsp; [&nbsp; "2", &nbsp; "1", &nbsp; "39" &nbsp;],<br>StartMatch: 1<br>} |

마지막 예제를 자세히 살펴보겠습니다. **[Time](function-date-time.md)** 함수를 사용 하 여이 문자열을 날짜/시간 값으로 변환 하려면 명명 된 하위 일치 항목을 개별적으로 전달 해야 합니다. 이렇게 하려면 **일치** 하는 레코드에 대해 작동 하는 **[With](function-with.md)** 함수를 사용 하면 됩니다.

``` powerapps-dot
With( 
    Match( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ), 
    Time( Value( hours ), Value( minutes ), Value( seconds ) )
)
```

이러한 예제에서는 [단추](../controls/control-button.md) 컨트롤을 추가 하 고, **onselect** 속성을이 수식으로 설정 하 고, 단추를 선택 합니다.

``` powerapps-dot
Set( pangram, "The quick brown fox jumps over the lazy dog." )
```
 
| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| `Match( pangram, "THE", IgnoreCase )` | 텍스트 문자열에서 "the"와 일치 **하는 모든** 항목을 찾습니다. 문자열에 두 개의 일치 항목이 포함 되어 있지만 **Match** 를 사용 하 고 **matchall**을 사용 하지 않으므로 첫 번째만 반환 됩니다. 하위 일치가 정의 되지 않았기 때문에 일치 하는 열이 비어 있습니다.  | {<br>FullMatch: "The",<br>부분 일치: [&nbsp;],<br>StartMatch: 32<br>} |
| `MatchAll( pangram, "the" )` | 텍스트 문자열에서 "the"와 일치 **하는 모든** 항목을 찾습니다. 테스트는 대/소문자를 구분 하므로 "the"의 두 번째 인스턴스만 찾을 수 있습니다. 하위 일치가 정의 되지 않았기 때문에 일치 하는 열이 비어 있습니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram, "the", IgnoreCase )` | 텍스트 문자열에서 "the"와 일치 **하는 모든** 항목을 찾습니다. 이 경우 테스트는 대/소문자를 구분 하지 않으므로 단어의 두 인스턴스를 모두 찾을 수 있습니다. 하위 일치가 정의 되지 않았기 때문에 일치 하는 열이 비어 있습니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram, "\b\wo\w\b" )` | 가운데에 "o"가 있는 세 문자 단어를 모두 찾습니다. "갈색"은 세 문자로 된 단어가 아니므로 "\b" (단어 경계)와 일치 하지 않기 때문에 제외 됩니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram, "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | "Fox"와 "dog" 사이의 모든 문자를 찾습니다. | {<br>between: &nbsp; "은 @ no__t를 통해 @ no__t를 점프 합니다. @ no__t-3lazy",<br>FullMatch: &nbsp; "fox @ no__t-1jumps @ no__t-2over @ no__t-3the @ no__t-4lazy @ no__t-5dog",<br>부분 일치: ["lazy를 위로 이동"],<br>StartMatch: 17@@<br> } |

갤러리에서 **Matchall** 의 결과를 보려면 다음을 수행 합니다.

1. 빈 화면에서 빈 세로 **[갤러리](../controls/control-gallery.md)** 컨트롤을 삽입 합니다.

2. 갤러리의 **Items** 속성을 **matchall ("\w +")** 또는 **matchall (MultipleLetters)** 로 설정 합니다.

    ![](media/function-ismatch/pangram-gallery1.png)

3. 갤러리의 템플릿을 선택 하려면 갤러리 컨트롤의 가운데에 있는 "삽입 탭에서 항목 추가"를 선택 합니다. 

5. 갤러리의 템플릿에 **[레이블](../controls/control-text-box.md)** 컨트롤을 추가 합니다.  

4. 레이블의 **Text** 속성을 **ThisItem**로 설정 합니다.  
 
    갤러리는 예제 텍스트의 각 단어로 채워집니다.  한 화면에 모든 단어를 표시 하려면 갤러리의 템플릿 및 레이블 컨트롤의 크기를 조정 합니다.

    ![](media/function-ismatch/pangram-gallery2.png)
