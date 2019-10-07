---
title: DateValue, TimeValue 및 DateTimeValue 함수 | Microsoft Docs
description: PowerApps의 DateValue, TimeValue 및 DateTimeValue 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: 3914c55bf3be5d172bc80832e437c3e3775a1859
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985076"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-powerapps"></a>PowerApps의 DateValue, TimeValue 및 DateTimeValue 함수
문자열의 날짜, 시간 또는 둘 다를 날짜/시간 값으로 변환합니다.

## <a name="description"></a>설명
**DateValue** 함수는 날짜 문자열(예: "10/01/2014")을 날짜/시간 값으로 변환합니다.

**TimeValue** 함수는 시간 문자열(예: "12:15 PM")을 날짜/시간 값으로 변환합니다.

**DateTimeValue** 함수는 날짜 및 시간 문자열(예: "January 10, 2013 12:13 AM")을 날짜/시간 값으로 변환합니다.

**DateValue** 함수는 날짜 문자열의 시간 정보를 무시하며 **TimeValue** 함수는 시간 문자열의 날짜 정보를 무시합니다.

기본적으로 사용되는 언어는 현재 사용자의 언어이지만 문자열이 제대로 해석되도록 이 값을 재정의할 수 있습니다. 예를 들어 "10/1/1920"이 "en"에서는 10월 1일<sup></sup>로, "fr"에서는 1월 10일<sup></sup>로 해석됩니다.

날짜는 다음 형식 중 하나여야 합니다.

* MM/DD/YYYY
* DD/MM/YYYY
* DD Mon YYYY
* Month DD, YYYY

숫자 구성 요소의 날짜, 월, 일, 시간, 분 및 초를 변환하려면 **[Date](function-date-time.md)** 및 **[Time](function-date-time.md)** 함수를 참조하세요.

[날짜 및 시간 작업](../show-text-dates-times.md)에서도 자세한 내용을 참조하세요.

숫자를 변환하려면 **[Value](function-value.md)** 함수를 참조하세요.

## <a name="syntax"></a>구문
**DateValue**( *String* [, *Language* ])<br>**DateTimeValue**( *String* [, *Language* ])<br>**TimeValue**( *String* [, *Language* ])

* *String* - 필수 항목이며,  날짜, 시간 또는 날짜와 시간의 조합 값이 포함된 텍스트 문자열입니다.
* *Language* - 선택 항목입니다.  **[Language](function-language.md)** 함수의 첫 두 문자로 반환되는, 언어 문자열입니다.  제공되지 않으면 현재 사용자의 클라이언트 언어가 사용됩니다.  

## <a name="examples"></a>예
### <a name="datevalue"></a>DateValue
**Startdate**라는 텍스트 입력 컨트롤에 **10/11/2014**를 입력한 다음, 레이블의 **[Text](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.

* **Text(DateValue(Startdate.Text), DateTimeFormat.LongDate)**
  
    컴퓨터가 **en** 로캘로 설정된 경우 레이블에 **Saturday, October 11, 2014**가 표시됩니다.
  
    > [!NOTE]
  > **LongDateTime** 이외의 여러 옵션을 **DateTimeFormat** 매개 변수와 함께 사용할 수 있습니다. 이러한 옵션 목록을 표시하려면 함수 상자에 매개 변수를 입력하고 바로 뒤에 느낌표를 입력하십시오.
* **Text(DateValue(Startdate.Text, "fr"), DateTimeFormat.LongDate)**
  
    레이블에 **Monday, November 10, 2014**가 표시됩니다.

**October 20, 2014**에 동일한 작업을 수행하면:

* **DateDiff(DateValue(Startdate.Text), Today())**
  
    컴퓨터가 **en** 언어로 설정된 경우, 레이블에 **9**가 표시되어 10월 11일에서 10월 20일 사이의 일 수를 나타냅니다. **[DateDiff](function-dateadd-datediff.md)** 함수는 월, 분기 또는 연도의 차이도 표시할 수 있습니다.

### <a name="datetimevalue"></a>DateTimeValue
**Start**라는 텍스트 입력 컨트롤에 **10/11/2014 1:50:24.765 PM**을 입력한 다음, 레이블의 **[Text](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.

* **Text(DateTimeValue(Start.Text), DateTimeFormat.LongDateTime)**
  
    컴퓨터가 en 로캘로 설정된 경우 레이블에 **Saturday, October 11, 2014 1:50:24 PM**이 표시됩니다.
  
    > [!NOTE]
  > **LongDateTime** 이외의 여러 옵션을 **DateTimeFormat** 매개 변수와 함께 사용할 수 있습니다. 이러한 옵션 목록을 표시하려면 함수 상자에 매개 변수를 입력하고 바로 뒤에 느낌표를 입력하십시오.
* **Text(DateTimeValue(Start.Text, "fr"), DateTimeFormat.LongDateTime)**
  
    레이블에 **Monday, November 10, 2014 1:50:24 PM**이 표시됩니다.
* **Text(DateTimeValue(Start.Text), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM")**
  
    컴퓨터가 **en** 로캘로 설정된 경우 레이블에 **Saturday, October 11, 2014 01:50:24:765 PM**이 표시됩니다.
  
    아니면 **hh:mm:ss.f** 또는 **hh:mm:ss.ff**를 지정하여 가장 가까운 10분의 1초나 100분의 1초로 시간을 반올림할 수 있습니다.

### <a name="timevalue"></a>TimeValue
텍스트 입력 컨트롤 이름을 **FinishedAt**으로 지정하고 레이블의 **[Text](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.

**If(TimeValue(FinishedAt.Text)<TimeValue("5:00:00.000 PM"), "You made it!", "Too late!")**

* **FinishedAt** 컨트롤에 **4:59:59.999 PM**을 입력하면 레이블에 "You made it!"이 표시됩니다.
* **FinishedAt** 컨트롤에 **5:00:00.000 PM**을 입력하면 레이블에 "Too late!"이 표시됩니다.

