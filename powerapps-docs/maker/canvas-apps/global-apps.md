---
title: 캔버스 앱에 글로벌 지원 빌드 | Microsoft Docs
description: PowerApps를 사용하여 전 세계에서 사용되는 앱을 빌드합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9ca80511875ff8534e5b07c3a7844485ff70a4a5
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216162"
---
# <a name="build-global-support-into-canvas-apps"></a>캔버스 앱에 글로벌 지원 빌드
PowerApps는 글로벌 제품입니다. 많은 다양한 언어와 지역에서 캔버스 앱을 빌드하고 사용할 수 있습니다.

앱을 빌드하고 실행하는 동안 PowerApps에서 표시되는 텍스트는 다양한 언어로 번역되었습니다.  따라서 메뉴 항목, 대화 상자, 리본 탭은 물론, 기타 텍스트를 모국어로 보게 될 것입니다.  날짜와 숫자의 입력과 표시도 특정 언어와 지역에 맞게 수정됩니다.  예를 들어, 전 세계의 일부 지역은 소수 구분 기호로 **.** (점 또는 마침표)를 사용하는 반면 다른 지역은 **,** (쉼표)를 사용합니다.  

사용자가 만드는 앱도 전 세계적으로 알려질 수 있습니다.  **[Language](functions/function-language.md)**, **[Text](functions/function-text.md)**, **[Value](functions/function-value.md)**, **[DateValue](functions/function-datevalue-timevalue.md)** 및 기타 함수를 사용하여 다른 언어에서 입력으로 표시 및 사용되는 것을 변경합니다.   

## <a name="language-settings"></a>언어 설정
네이티브 스튜디오 또는 플레이어를 사용할 경우 사용하는 언어는 호스트 운영 체제에서 제공합니다.  Windows의 경우 "모든 설정" 및 "시간 및 언어" 설정에서 제어할 수 있습니다.  Windows에서도 사용자가 소수 구분 기호에 사용할 문자를 지정하여 언어 설정을 재정의하도록 허용합니다.  

웹 환경을 사용할 경우 사용하는 언어는 브라우저에서 제공합니다.  대부분 브라우저는 호스트 운영 체제로 기본 설정되며 일부는 언어를 수동으로 설정할 수 있는 방법을 제공하기도 합니다.

## <a name="authoring-environment"></a>제작 환경
제작 환경은 제작자의 언어 설명에 맞게 변경됩니다.  앱 자체가 언어와 관계 없는 방식으로 저장되므로, 다른 언어를 사용하는 제작자는 동일한 앱을 편집할 수 있습니다.

### <a name="names-in-formulas"></a>수식의 이름
대부분의 수식 요소는 항상 영어입니다.

* 함수 이름: **If**, **Navigate**, **Collect**,...
* 컨트롤 속성 이름: **Screen.Fill**, **Button.OnSelect**, **Textbox.Font**, ...
* 열거형 이름: **Color.Aqua**, **DataSourceInfo.MaxValue**, **FontWeight.Bold**...
* 신호 레코드: **Compass.Heading**, **Location. Latitude**, **App.ActiveScreen**, ...
* 연산자: **Parent**, **in**, **exactIn**, ...

제작 환경이 지역화되면 컨트롤 및 기타 개체 이름이 제작자의 모국어로 나타납니다.  스페인어에서 일부 컨트롤 이름은 다음과 같이 나타납니다.

![](media/global-apps/insert-controls-es.png)

다음 중 하나를 앱에 삽입하면 해당 이름이 영어로 기본 지정됩니다.  이것은 컨트롤 속성 이름과 식의 나머지 부분의 일관성을 위해 수행됩니다.  예를 들어 위의 목록에 있는 **Casilla**는 **Checkbox1**으로 삽입됩니다.  

컨트롤을 삽입한 후 원하는 이름으로 변경할 수 있습니다.  선택된 상태에서 “콘텐츠” 리본의 맨 왼쪽은 컨트롤의 이름을 표시합니다.  이 이름을 선택하면 이름을 편집할 수 있는 텍스트 상자가 드롭다운됩니다.

![](media/global-apps/control-rename.png)

원할 경우 여기서 컨트롤 이름을 **Casilla1**으로 변경할 수 있습니다.  이 경우 브라우저에서 표시된 빨강 물결은 이름이 스페인 단어가 아니기 때문이며, 신경 쓰지 않아도 됩니다.

다음 항목에 원하는 이름을 사용할 수 있습니다.

* 컨트롤 이름
* 컬렉션 이름
* 컨텍스트 변수 만들기

### <a name="formula-separators-and-chaining-operator"></a>수식 구분 기호와 연결 연산자
일부 [구분 기호 및 연산자](functions/operators.md)는 제작자 언어의 소수 구분 기호에 따라 전환됩니다.

| 제작자의 언어 소수 구분 기호 | PowerApps 소수 구분 기호 | PowerApps 목록 구분 기호 | PowerApps 연결 연산자 |
| --- | --- | --- | --- |
| **.** (점 또는 마침표) |**.** (점 또는 마침표) |**,** (쉼표) |**;** (세미콜론) |
| **,** (쉼표) |**,** (쉼표) |**;** (세미콜론) |**;;** (이중 세미콜론) |

PowerApps 목록 구분 기호에 변경 내용이 Excel 목록 구분 기호에 어떻게 부합 합니다.  이는 다음에 영향을 미칩니다.

* 함수 호출의 인수
* [레코드](working-with-tables.md#elements-of-a-table)의 필드
* 에 기록 된 [테이블](working-with-tables.md#inline-value-tables)합니다.

예를 들어, 일본과 영국 같은 소수 구분 기호로 점 또는 마침표를 사용하는 언어나 지역에서는 다음 수식을 고려합니다.

![PowerApps 수식 오픈 괄호 slider1 점 값을 쉼표로 12 점 59 보다 큰 경우 알림 오픈 괄호 "유효!" 쉼표로 성공 닫기 괄호 열고 닫는 괄호 없음 "NextScreen" 쉼표로 괄호 세미콜론 탐색 쉼표로 알림 오픈 괄호 "잘못 된 경우 다시 시도" 쉼표로 오류 닫기 괄호 닫기 괄호](media/global-apps/operators-dot.png)

이제 프랑스, 스페인 같은 소수 구분 기호로 쉼표를 사용하는 언어나 지역에서의 동일한 수식을 봅니다.

![PowerApps 수식 오픈 괄호 slider1 점 값 12 쉼표로 세미콜론 59 보다 큰 경우 알림 오픈 괄호 "유효!" 세미콜론으로 성공 닫기 괄호 이중 세미콜론 탐색 열린 괄호 "NextScreen" None 닫기 괄호는 세미콜론으로 세미콜론으로 알림 오픈 괄호 "잘못 된 경우 다시 시도" 세미콜론 오류 닫기 괄호 닫기 괄호](media/global-apps/operators-comma.png)

강조 표시는 두 버전 간에 변경되는 연산자를 보여 줍니다.  **Slider1.Value**에서 속성 선택 연산자 **.** (점 또는 마침표)는 항상 소수 구분 기호와 상관 없이 동일합니다.

내부적으로는 수식이 변경되지 않지만, 제작자가 표시 및 편집하는 방식이 변경 사항의 전부입니다.  두 가지 다른 언어를 사용하는 두 명의 제작자는 각각 자신의 언어에 대한 적합한 구분자와 연산자를 통해 같은 수식을 보고 편집할 수 있습니다.

## <a name="creating-a-global-app"></a>전역 앱 만들기
사용자가 만드는 앱은 다른 언어로 변경되어 전 세계 사용자에게 훌륭한 사용자 경험을 제공할 수 있습니다.

### <a name="language-function"></a>Language 함수
**[Language](functions/function-language.md)** 함수는 현재 사용자의 언어 태그를 반환합니다.  예를 들어 이 함수는 영국의 사용자에게 **"en-GB"** , 독일의 사용자에게 **"de-DE"** 를 반환합니다.  

무엇 보다도 **Language**를 사용하여 사용자를 위해 번역된 텍스트를 표시할 수 있습니다.  앱은 번역된 값의 테이블을 앱에 포함할 수 있으며

![](media/global-apps/loc-table.png)

그런 후 다음과 같은 수식을 사용하여 번역된 문자열을 테이블에서 끌어옵니다.

**LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

다른 언어로 번역된 문자열은 자신의 언어보다 훨씬 오래 걸릴 수 있습니다.  대부분의 경우 사용자 인터페이스에 문자열을 표시하는 레이블 및 기타 요소가 더 넓어져야 합니다.

자세한 내용은 **[Language](functions/function-language.md)** 함수에 대한 문서를 참조하세요.

### <a name="formatting-numbers-dates-and-times"></a>숫자, 날짜 및 시간 형식 지정
숫자, 날짜 및 시간은 전 세계의 다른 부분에서 다른 형식으로 기록됩니다.  쉼표, 소수의 의미와 월, 일 및 연도의 순서는 지역에 따라 다릅니다.   

**[Text](functions/function-text.md)** 함수는 사용자의 언어 설정을 사용하여 숫자와 날짜의 형식을 지정합니다.

**Text**는 숫자 또는 날짜의 형식을 지정하려는 방식을 알기 위해 형식 문자열이 필요합니다.  이 형식 문자열은 두 가지 형태 중 하나를 사용할 수 있습니다.

* **전역 인식 열거형.**  예를 들어, **Text( Now(), DateTimeFormat.LongDate )**  이 수식은 현재 날짜를 언어에 적절한 형식으로 지정합니다.  이 형태는 형식 문자열을 지정하는 위해 선호하는 방식입니다.
* **사용자 지정 형식 문자열.**  예를 들어 **Text( Now(), "[$-en-US]dddd, mmmm dd, yyyy" )** 는 언어 "en-US"에서 사용 시 열거형과 동일한 텍스트를 표시합니다.  사용자 지정 형식 문자열의 이점은 원하는 내용을 정확하게 지정할 수 있다는 것입니다.

사용자 지정 형식의 앞에 있는 "[$-en-US]"는 사용자 지정 형식 문자열을 해석할 언어로 **Text**를 알려 줍니다.  이것은 사용자를 위해 넣은 것이며 제작 언어로 기본 설정됩니다.  일반적으로, 변경할 필요가 없습니다.  다른 언어의 제작자가 동일한 앱을 편집할 때 유용합니다.

**Text**에 대한 세 번째 인수는 이 함수의 결과에 사용할 언어를 지정합니다.  기본값은 현재 사용자의 언어 설정입니다.

자세한 내용은 **[Text](functions/function-text.md)** 함수에 대한 문서를 참조하세요.      

### <a name="reading-numbers-dates-and-times"></a>숫자, 날짜 및 시간 읽기
사용자가 제공하는 숫자, 날짜 및 시간 읽기에 대한 4개의 함수가 있습니다.

* **[Value](functions/function-value.md)**: 텍스트 문자열의 숫자를 숫자 값으로 변환합니다.
* **[DateValue](functions/function-datevalue-timevalue.md)**: 텍스트 문자열의 날짜 값을 날짜/시간 값으로 변환합니다.  텍스트 문자열에서 지정한 시간은 무시됩니다.
* **[TimeValue](functions/function-datevalue-timevalue.md)**: 텍스트 문자열의 시간 값을 날짜/시간 값으로 변환합니다.  텍스트 문자열에서 지정한 날짜는 무시됩니다.
* **[DateTimeValue](functions/function-datevalue-timevalue.md)**: 텍스트 문자열의 날짜 및 시간 값을 날짜/시간 값으로 변환합니다.  

Excel을 사용한 경우 이러한 모든 함수가 단일한 **Value** 함수로 통합됩니다.  PowerApps에는 날짜/시간 값과 숫자에 대해 별도의 값이 있으므로 여기에서는 나누었습니다.

이러한 모든 함수에는 같은 인수가 있습니다.

* *문자열, 필수*: 사용자로터 가져온 문자열입니다. 예를 들어 문자열을 **텍스트 입력** 컨트롤에 입력하고 **Text** 속성으로 컨트롤에서 읽습니다.
* *언어, 선택적*: *문자열*을 해석할 언어입니다.  기본적으로 사용자의 언어 설정입니다.

예:

* **Value( "12,345.678", "en-US" )** 또는 **Value( "12,345.678" )** , "en-US"가 사용자 언어인 경우 계산할 준비가 된 **12345.678**을 반환합니다.
* **DateValue( "1/2/01", "es-ES" )** 또는 **DateValue( "1/2/01" )** , "es-ES"가 사용자 언어인 경우 날짜/시간 값 **February 1, 2001 at midnight**을 반환합니다.
* **TimeValue( "11:43:02", "fr-FR" )** 또는 **DateValue( "11:43:02" )** , "fr-FR"이 사용자 언어인 경우 날짜/시간 값 **January 1, 1970 at 11:43:02**를 반환합니다.
* **TimeDateValue( "11:43:02 1/2/01", "de-DE" )** 또는 **DateValue( "11:43:02" )** , "de-DE"이 사용자 언어인 경우 날짜/시간 값 **February 1, 2001 at 11:43:02**를 반환합니다.

자세한 내용은 **[Value](functions/function-value.md)** 및 **[DateValue, TimeValue, 및 DateTimeValue](functions/function-datevalue-timevalue.md)** 함수와 [날짜 및 시간 작업](show-text-dates-times.md). 문서를 참조하세요.

### <a name="calendar-and-clock-information"></a>달력 및 시계 정보
**[Calendar](functions/function-clock-calendar.md)** 및 **[Clock](functions/function-clock-calendar.md)** 함수는 사용자의 현재 언어에 대한 달력 및 시계 정보를 제공합니다.  

특히, 이러한 함수를 사용하여 선택 옵션이 있는 **드롭다운** 컨트롤을 제공합니다.  

자세한 내용은 **[Calendar](functions/function-clock-calendar.md)** 및 **[Clock](functions/function-clock-calendar.md)** 함수에 대한 문서를 참조하세요.
