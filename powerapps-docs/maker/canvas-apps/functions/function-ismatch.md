---
title: IsMatch, 일치 및 MatchAll 함수 | Microsoft Docs
description: PowerApps의 IsMatch, 일치 및 MatchAll 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2cfa2a93e7bb33dc2c1b26c266b1ecf6680938c4
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67457062"
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>PowerApps의 IsMatch, 일치 및 MatchAll 함수
일치 또는 추출 패턴에 따라 텍스트 문자열 부분을 테스트 합니다.

## <a name="description"></a>설명
**IsMatch** 함수는 텍스트 문자열이 일반 문자, 미리 정의된 패턴 또는 [정규식](#regular-expressions)을 구성할 수 있는 패턴과 일치하는지 여부를 테스트합니다.  **일치** 하 고 **MatchAll** 어떤 일치 하는 경우 하위 검색 항목을 포함 하 여 함수 반환 합니다.  

**IsMatch**를 사용하여 사용자가 **[Text input](../controls/control-text-input.md)** 컨트롤에 입력한 것의 유효성을 검사합니다. 예를 들어, 결과가 데이터 원본에 저장되기 전에 사용자가 유효한 이메일 주소를 입력했는지 여부를 확인할 수 있습니다. 항목이 조건과 일치하지 않는 경우 사용자에게 항목을 수정하도록 하는 다른 컨트롤을 추가합니다.

사용 하 여 **일치** 패턴과 일치 하는 첫 번째 텍스트 문자열을 추출 하 고 **MatchAll** 일치 하는 모든 텍스트 문자열을 추출 하 합니다. 또한 복잡 한 문자열을 구문 분석 하위 검색 항목을 추출할 수 있습니다.   

**일치** 찾을 첫 번째 일치 항목에 대 한 정보는 레코드를 반환 하 고 **MatchAll** 찾은 모든 일치 항목에 대 한 레코드의 테이블을 반환 합니다. 레코드를 포함 합니다.

| 열 | 유형 | 설명 |
|----|----|----|
| *하위 라는&#8209;와 일치 하거나 하위&#8209;와 일치* | Text | 각 명명 된 하위 일치 항목 자체 열을 포함 됩니다. 사용 하 여 일치 하는 명명 된 하위 항목을 만듭니다 **(?&lt; *이름을*&gt;** ... **)** 정규식에서입니다. 일치 하는 명명 된 하위 항목에 미리 정의 된 열 (아래 참조) 중 하 나와 이름이 같은 경우 일치 하는 하위 우선 적용 되어 경고가 생성 됩니다. 이 경고를 방지 하려면 하위 검색 항목을 이름을 바꿉니다. |
| **FullMatch** | Text | 모든 일치 된 텍스트 문자열입니다. |
| **StartMatch** | 번호 | 입력된 텍스트 문자열 내에서 일치 항목의 시작 위치입니다. 문자열의 첫 번째 문자는 1을 반환합니다. | 
| **SubMatches** | 텍스트의 단일 열 테이블 (열 **값**) | 정규식에 나타나는 순서로 명명 되 고 명명 되지 않은 하위 검색 항목의 테이블입니다. 일반적으로 명명 된 하위 검색 항목 사용 하기 쉬운 되며 것이 좋습니다. 사용 된 [ **ForAll** ](function-forall.md) 함수 또는 [ **마지막**](function-first-last.md)( [ **FirstN**](function-first-last.md)( **...**  )) 기능이 개별 하위 일치를 사용 하 여 작동 합니다. 하위 일치 하는 정규식에 정의 된,이 테이블 존재 하지만 비어 있이 됩니다. |

이러한 함수는 지원 [ **MatchOptions**](#match-options)합니다. 기본적으로: 
- 이러한 함수는 대/소문자 구분 일치를 수행합니다. 사용 하 여 **IgnoreCase** 대/소문자 구분 일치를 수행 하 합니다.    
- **IsMatch** 전체 텍스트 문자열을 찾습니다 (**완료** MatchOption)을 하는 동안 **일치** 하 고 **MatchAll** (텍스트문자열에있는일치항목을검색 **포함** MatchOption). 사용 하 여 **완료**, **Contains**합니다 **시작 문자**, 또는 **EndsWith** 시나리오에 적합 하 게 합니다.

**IsMatch**는 텍스트 문자열이 패턴과 일치하는 경우 *true*를 반환하고 그렇지 않은 경우 *false*를 반환합니다. **일치** 반환 *빈* 와 함께 테스트할 수 있는 일치 하는 항목이 없으면 합니다 [ **IsBlank** ](function-isblank-isempty.md) 함수입니다. **MatchAll** 와 함께 테스트할 수 있는 일치 하는 항목이 없으면 빈 테이블을 반환 합니다 [ **IsEmpty** ](function-isblank-isempty.md) 함수입니다.

사용 중인 경우 **MatchAll** 텍스트 문자열을 분할 하려면 사용을 고려 합니다 **[분할](function-split.md)** 함수를 사용 하기 더욱 간편해졌으며 빠르고 합니다.

## <a name="patterns"></a>패턴
이러한 함수를 사용 하 여 키를 일치 시킬 패턴을 설명 하는 경우 다음의 조합으로 텍스트 문자열에서 패턴을 설명합니다.

* **"abc"** 또는 **"123"** 과 같은 일반 문자
* **Letter**, **MultipleDigits** 또는 **Email**과 같은 미리 정의된 패턴 (**Match** 열거는 이러한 패턴을 정의합니다.)
* 와 같은 정규식 코드 **"\d+\s+\d+"** 하거나 **"[a-z] +"** 합니다.

사용 하 여 이러한 요소를 결합 합니다 [문자열 연결 연산자 **&** ](operators.md)합니다. 예를 들어, **"abc" & Digit & "\s+"** 는 "a", "b" 및 "c", 그 뒤에 0~9의 숫자, 그 뒤에 최소 하나의 공백 문자가 오는 문자와 일치하는 유효한 패턴입니다.

### <a name="ordinary-characters"></a>일반 문자
가장 간단한 패턴은 정확히 일치되는 일반 문자의 시퀀스입니다.

예를 사용 하는 경우는 **IsMatch** 함수를 "Hello" 문자열을 패턴과 일치 **"Hello"** 정확 하 게 합니다. 그 이상 그 이하도 아닙니다. 문자열 "hello!" 끝에 느낌표가 인해 패턴과 일치 하지 않습니다 하 고 문자 "h"에 대 한 잘못 된 경우. (이 동작을 수정하는 방법은 [MatchOptions](#match-options)를 참조하세요.)

패턴 언어에서 특정 문자는 특별한 용도로 예약되어 있습니다. 이러한 문자를 사용 하려면 문자에 접두사를 사용 하 여는 **\\** (백슬래시) 문자를 리터럴로 처리 해야 하거나이 항목의 뒷부분에 설명 된 미리 정의 된 패턴 중 하나를 사용 합니다. 이 테이블은 특수 문자를 나열합니다.

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
미리 정의 된 패턴에는 문자 집합 중 하나 또는 여러 문자의 시퀀스와 일치 하는 간단한 방법을 제공 합니다. 사용 된 [문자열 연결 연산자 **&** ](operators.md) 의 구성원과 사용자 고유의 텍스트 문자열을 결합 하는 **일치** 열거형:

| 일치 열거 | 설명 | 정규식 |
| --- | --- | --- |
| **Any** |문자와 일치합니다. |`.` |
| **Comma** |쉼표와 일치합니다. |`,` |
| **Digit** |단일 숫자("0"부터 "9")와 일치합니다. |`\d` |
| **Email** |"at" 기호("\@")를 포함하는 이메일 주소 및 점(".")을 포함하는 도메인 이름과 일치합니다. |`.+\@.+\\.[^\\.]{2,}` |
| **Hyphen** |하이픈과 일치합니다. |`\-` |
| **LeftParen** |왼쪽 괄호"("와 일치합니다. |`\(` |
| **Letter** |문자와 일치합니다. |`\p{L}` |
| **MultipleDigits** |하나 이상의 숫자를 찾습니다. |`\d+` |
| **MultipleLetters** |하나 이상의 문자와 일치합니다. |`\p{L}+` |
| **MultipleNonSpaces** |공백 (공백, 탭 또는 줄 바꿈 하지) 추가 하지 않는 하나 이상의 문자와 대응 합니다. |`\S+` |
| **MultipleSpaces** |공백 (공백, 탭 또는 줄 바꿈)를 추가 하는 하나 이상의 문자와 대응 합니다. |`\s+` |
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
이러한 함수를 사용 하는 패턴은는 [정규식](https://en.wikipedia.org/wiki/Regular_expression)합니다. 일반 문자 및이 항목에서는 도움말의 앞부분에서 설명 하는 미리 정의 된 패턴 정규식을 작성 합니다.  

정규식은 매우 강력하고 여러 프로그래밍 언어에서 사용할 수 있으며 다양한 목적에 사용됩니다. 문장 부호의 임의 시퀀스를 종종 같이 수 있습니다. 정규식의 모든 측면 하지만 다양 한 정보, 자습서,이 문서에서는 설명 하지 않습니다 및 도구는 웹에서 확인할 수 있습니다.  

다른 언어에서 제공 되는 정규식 및 PowerApps는 JavaScript 언어의 변형입니다. 참조 [정규식 구문](https://msdn.microsoft.com/library/1400241x.aspx) 구문에 대 한 소개입니다. 명명 된 하위 검색 항목 (명명 된 캡처 그룹 라고도 함)이 지원 됩니다.

- 하위 검색 항목 이라는: **(?&lt; *이름을* &gt; ...)**
- 역참조 라는:  **\\k&lt;*이름*&gt;**

에 **일치** 열거형이이 항목의 앞부분에 테이블의 해당 정규식과 같은 행에 표시 되는 각 열거형입니다.

## <a name="match-options"></a>일치 옵션
문자열 연결 연산자를 사용 하 여 결합할 수 있는 하나 이상의 옵션을 지정 하 여 이러한 함수의 동작을 수정할 수 있습니다 ( **&amp;** ).  

| MatchOptions 열거 | 설명 | 정규식에 미치는 영향 |
| --- | --- | --- |
| **BeginsWith** |패턴은 텍스트의 시작 부분에서 일치해야 합니다. |**^** 를 정규식의 시작 부분에 추가합니다. |
| **Complete** |에 대 한 기본 **IsMatch**합니다. 패턴 처음부터 끝까지에서 텍스트의 전체 문자열을 일치 해야 합니다. |추가 된 **^** 시작 및 **$** 정규식의 끝에 합니다. |
| **Contains** |에 대 한 기본 **일치** 하 고 **MatchAll**합니다. 패턴은 텍스트의 어딘가에 나타나야 하지만 시작 또는 끝일 필요가 없습니다. |정규식을 수정하지 않습니다. |
| **EndsWith** |패턴은 텍스트 문자열의 끝을 일치 해야 합니다. |**$** 를 정규식의 끝 부분에 추가합니다. |
| **IgnoreCase** |동일한 대/소문자를 대문자로 처리 기본적으로 일치는 대/소문자 구분입니다. |정규식을 수정하지 않습니다. 이 옵션은 정규식에 대 한 표준 "i" 한정자는 것과 같습니다.  |
| **Multiline** |여러 줄과 일치합니다. |정규식을 수정하지 않습니다. 이 옵션은 정규식에 대 한 "m" 표준 한정자는 것과 같습니다. |

사용 하 여 **MatchAll** 정규식에 대 한 표준 "g" 한정자를 사용 하는 것과 같습니다.

## <a name="syntax"></a>구문
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 필수 항목입니다. 테스트할 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 텍스트 문자열로 테스트할 패턴입니다. 미리 정의 된 패턴을 연결 하는 **일치** 열거형을 정의 또는 정규식을 제공 합니다. *패턴* 모든 변수, 데이터 원본 또는 다른 동적 앱 실행 될 때 해당 변경 내용을 참조 하지 않고 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. 텍스트 문자열 조합 **MatchOptions** 열거형 값입니다. 기본적으로 **MatchOptions.Complete**가 사용됩니다.

**일치**( *텍스트*하십시오 *패턴* [합니다 *옵션* ])

* *Text* – 필수 항목입니다. 와 일치 하도록 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 패턴 일치 텍스트 문자열입니다. 미리 정의 된 패턴을 연결 하는 **일치** 열거형을 정의 또는 정규식을 제공 합니다. *패턴* 모든 변수, 데이터 원본 또는 다른 동적 앱 실행 될 때 해당 변경 내용을 참조 하지 않고 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. 텍스트 문자열 조합 **MatchOptions** 열거형 값입니다. 기본적으로 **MatchOptions.Contains** 사용 됩니다.

**MatchAll**( *텍스트*하십시오 *패턴* [합니다 *옵션* ])

* *Text* – 필수 항목입니다. 와 일치 하도록 텍스트 문자열입니다.
* *Pattern* – 필수 항목입니다. 패턴 일치 텍스트 문자열입니다. 미리 정의 된 패턴을 연결 하는 **일치** 열거형을 정의 또는 정규식을 제공 합니다. *패턴* 모든 변수, 데이터 원본 또는 다른 동적 앱 실행 될 때 해당 변경 내용을 참조 하지 않고 상수 수식 이어야 합니다.
* *Options* – 선택 사항입니다. 텍스트 문자열 조합 **MatchOptions** 열거형 값입니다. 기본적으로 **MatchOptions.Contains** 사용 됩니다.

## <a name="ismatch-examples"></a>IsMatch 예제
### <a name="ordinary-characters"></a>일반 문자
앱에 **TextInput1**이라는 **Text input** 컨트롤이 포함되어 있다고 가정합니다. 사용자는 데이터베이스에 저장되도록 이 컨트롤에 값을 입력합니다.   

사용자는 **TextInput1**에 **Hello world**를 입력합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| `IsMatch( TextInput1.Text, "Hello world" )` |테스트 사용자의 입력 여부와 정확히 일치 "Hello world" 문자열입니다. |**true** |
| `IsMatch( TextInput1.Text, "Good bye" )` |테스트 사용자의 입력 여부와 정확히 일치 문자열 "Good bye"입니다. |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains )` |사용자 입력의 단어 "hello" (대/소문자 구분)를 포함 하는지 여부를 테스트 합니다. |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )` |사용자의 입력이 단어 "hello"(대/소문자 구분하지 않음)를 포함하는지 여부를 테스트합니다. |**true** |

### <a name="predefined-patterns"></a>미리 정의된 패턴

|                                                            수식                                                            |                                                                설명                                                                |  결과   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              미국 사회 보장 번호와 일치합니다.                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com", Email )`                                            |                                                         이메일 주소와 일치합니다.                                                          | **true**  |
|                              `IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )`                               |                                   숫자, 마침표, 0개 이상의 숫자 시퀀스와 일치합니다.                                   | **true**  |
|                                `IsMatch( "123", MultipleDigits & Period & OptionalDigits )`                                 | 숫자, 마침표, 0개 이상의 숫자 시퀀스와 일치합니다. 이 패턴은 일치 하지 않습니다 있도록 마침표를 일치 하는 텍스트에 표시 되지 않습니다. | **false** |

### <a name="regular-expressions"></a>정규식

|                                                                              수식                                                                              |                                                                                                                                  설명                                                                                                                                   |  결과   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986", "\d+" )`                                                                   |                                                                                                                    0 보다 큰 정수를 찾습니다.                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02", "\d+(\.\d\d)?" )`                                                              |                                        양수 통화 금액과 일치합니다. 소수점을 포함 하는 입력, 입력 소수점 뒤 두 숫자를도 포함 해야 합니다. 예를 들어, 3.00은 유효하지만 3.1은 유효하지 않습니다.                                         | **true**  |
|                                                            `IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )`                                                             |                                                        양수 또는 음수 통화 금액과 일치합니다. 소수점을 포함 하는 입력, 입력 소수점 뒤 두 숫자를도 포함 해야 합니다.                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )`                                                        | 미국 사회 보장 번호와 일치합니다. 제공된 입력 필드의 형식, 유형 및 길이의 유효성을 검사합니다. 일치 하는 문자열 뒤에 대시를 다음 두 개의 숫자 뒤에 대시를 세 자리 숫자로 및 다음 4 개의 숫자 문자로 구성 되어야 합니다. | **true**  |
|                                                         `IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               이전 예제와 같지만 하이픈 중 하나가 입력에서 제자리에 있지 않습니다.                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        8, 9 또는 10 자 이상의 숫자, 영문자가 하나 이상 실행 하는 것 외에도 포함 해야 하는 강력한 암호를 확인 합니다. 문자열은 특수 문자를 포함할 수 없습니다.                                        | **false** |
| `IsMatch( "<http://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     http, https 또는 ftp URL의 유효성을 검사합니다.                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>일치 및 MatchAll 예제

| 수식 | 설명 | 결과 |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>" & Match.Email & ")>"` | 연락처 정보를 전자 메일 부분만을 추출합니다.  | {<br>email:&nbsp;"bob.jones@contoso.com",<br>FullMatch:&nbsp;"&lt;bob.jones@contoso.com>",<br>SubMatches:&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;],<br>StartMatch: 11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>", "<(?<email>" & Match.Email & ")>"` | 연락처 정보를 전자 메일 부분만을 추출합니다. 없는 올바른 주소를 찾을 수 (방법이 더 @ 기호) 이므로 반환 *빈*합니다. | *공백* |  
| `Match( Language(), "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | 언어의 언어, 스크립트 및 영역 부분을 추출 하는 태그를 **[언어](function-language.md)** 함수에서 반환 합니다. 이러한 결과 미국 반영합니다. 참조를 [ **언어** 함수 설명서](function-language.md) 예를 더 합니다.  합니다 **(?:** 연산자는 다른 하위 검색 항목을 만들지 않고 문자를 그룹화 합니다. | {<br>언어: "en",<br>script: *blank*, <br>region: "US",<br>FullMatch: "EN-US", <br>부분 일치: ["en", "", "미국"], <br>StartMatch: 1<br>} 
| `Match( "PT2H1M39S", "PT(?:(<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | ISO 8601 기간 값에서 시간, 분 및 초를 추출합니다. 텍스트 문자열에서 추출 된 숫자는 사용 합니다 [ **값** ](function-value.md) 전에 수치 연산을 수행 하는 숫자로 변환 하는 함수입니다.  | {<br> 시간: "2",<br>(분): "1",<br>(초): "39",<br>FullMatch: "PT2H1M39S",<br>SubMatches:&nbsp;[&nbsp;"2",&nbsp;"1",&nbsp;"39"&nbsp;],<br>StartMatch: 1<br>} |

마지막 예제를 살펴보겠습니다. 그런데이 문자열을 사용 하 여 날짜/시간 값으로 변환 하는 경우는 **[시간](function-date-time.md)** 함수에 전달 해야 일치 하는 명명 된 하위 항목에 개별적으로 합니다. 이 위해 사용할 수 있습니다는 **[ForAll](function-forall.md)** 함수에서 첫 번째 레코드 **MatchAll** 반환 합니다.

``` powerapps-dot
First( 
    ForAll( 
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ), 
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

이러한 예를 들어 추가 [단추](../controls/control-button.md) 컨트롤 해당 **OnSelect** 속성을이 수식 및 다음 단추를 선택 합니다.

``` powerapps-dot
Set( pangram, "The quick brown fox jumps over the lazy dog." )
```
 
| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| `Match( pangram, "THE", IgnoreCase )` | 문자열이 "THE" 텍스트에서의 모든 일치 항목 찾기는 **pangram** 변수를 포함 합니다. 문자열에 두 개의 일치 하는 않지만 사용 중 이므로 첫 번째 메시지만 반환 **일치** 아니라 **MatchAll**합니다. 부분 일치 열 정의 된 하위 일치 하기 때문에 비어 있습니다.  | {<br>FullMatch: "The",<br>부분 일치: [&nbsp;],<br>StartMatch: 32<br>} |
| `MatchAll( pangram, "the" )` | 텍스트 문자열에서 "the"의 모든 일치 항목을 검색 합니다 **pangram** 변수를 포함 합니다. 테스트에만 "the"의 두 번째 인스턴스를 찾을 수 대 소문자를 구분 합니다. 부분 일치 열 정의 된 하위 일치 하기 때문에 비어 있습니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram, "the", IgnoreCase )` | 텍스트 문자열에서 "the"의 모든 일치 항목을 검색 합니다 **pangram** 변수를 포함 합니다. 이 경우 단어의 두 인스턴스가 있으므로 테스트는 대/소문자를 구분 합니다. 부분 일치 열 정의 된 하위 일치 하기 때문에 비어 있습니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram, "\b\wo\w\b" )` | 중간에 "o"를 사용 하 여 모든 세 글자 단어를 찾습니다. "Brown"이 제외 되었음을 세 문자로 단어 아니며, "\b" (단어 경계)과 일치 하지 않으므로 하므로 note 합니다.  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram, "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | "Fox" 및 "dog" 사이 있는 모든 문자를 찾습니다. | {<br>간의:&nbsp;"점프&nbsp;위에&nbsp;는&nbsp;지연",<br>FullMatch:&nbsp;"fox&nbsp;jumps&nbsp;over&nbsp;the&nbsp;lazy&nbsp;dog",<br>부분 일치: ["jumps over 지연"],<br>StartMatch: 17<br> } |

결과를 보려면 **MatchAll** 갤러리에서:

1. 빈 화면에서 빈 세로 삽입 **[갤러리](../controls/control-gallery.md)** 제어 합니다.

2. 갤러리의 설정 **항목이** 속성을 **MatchAll (pangram, "\w+")** 하거나 **MatchAll (pangram MultipleLetters)** 합니다.

    ![](media/function-ismatch/pangram-gallery1.png)

3. 갤러리의 템플릿을 선택 하는 갤러리 컨트롤 중간 "삽입 탭에서 항목 추가"를 선택 합니다. 

5. 추가 된 **[레이블](../controls/control-text-box.md)** 갤러리의 템플릿에 컨트롤입니다.  

4. 레이블 설정 **텍스트** 속성을 **ThisItem.FullMatch**합니다.  
 
    갤러리 예제에서는 텍스트에서 각 단어를 사용 하 여 채워집니다.  모든 단어를 하나의 화면에 표시 하려면 갤러리의 템플릿 및 레이블 컨트롤을 크기 조정 합니다.

    ![](media/function-ismatch/pangram-gallery2.png)
