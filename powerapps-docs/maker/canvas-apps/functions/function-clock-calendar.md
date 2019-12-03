---
title: Calendar 및 Clock 함수 | Microsoft Docs
description: 구문 및 예제를 포함 하 여 Power Apps의 Calendar 및 Clock 함수에 대 한 참조 정보
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
ms.openlocfilehash: 62a500ad6e39451a3fb62932b9eeafb1d38f772a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679388"
---
# <a name="calendar-and-clock-functions-in-powerapps"></a>PowerApps의 Calendar 및 Clock 함수
현재 로캘에 대한 달력 및 시계 정보를 검색합니다.

## <a name="description"></a>설명
**Calendar** 및 **Clock** 함수는 현재 로캘에 대한 정보를 검색하는 함수 집합입니다.

이 함수를 사용하여 현재 사용자의 언어로 날짜와 시간을 표시할 수 있습니다.  **Calendar** 및 **Clock** 함수에서 반환된 단일 열 테이블은 Dropdown 및 Listbox 컨트롤의 **[Items](../controls/properties-core.md)** 속성과 함께 직접 사용할 수 있습니다.

| 함수 | 설명 |
| --- | --- |
| **Calendar.MonthsLong()** |각 월의 전체 이름이 "1월"부터 포함된 단일 열 테이블입니다. |
| **Calendar.MonthsShort()** |각 월의 약식 이름이 1월의 "1월"부터 포함된 단일 열 테이블입니다. |
| **Calendar.WeekdaysLong()** |각 요일의 전체 이름이 "일요일"부터 포함된 단일 열 테이블입니다. |
| **Calendar.WeekdaysShort()** |각 요일의 약식 이름이 일요일의 "일"부터 포함된 단일 열 테이블입니다. |
| **Clock.AmPm()** |긴 대문자 "AM" 및 "PM" 지정이 포함된 단일 열 테이블입니다.  24시간 시계를 사용하는 언어의 경우 테이블이 비어 있습니다. |
| **Clock.AmPmShort()** |짧은 대문자 "A" 및 "P" 지정이 포함된 단일 열 테이블입니다.  24시간 시계를 사용하는 언어의 경우 테이블이 비어 있습니다. |
| **Clock.IsClock24()** |24시간제가 이 로캘에 사용되는지 나타내는 부울입니다. |

이 동일한 정보를 사용하여 날짜 및 시간 값의 서식을 지정하려면 **[Text](function-text.md)** 함수를 사용합니다.  **[Language](function-language.md)** 함수는 현재 언어 및 지역 코드를 반환합니다.

## <a name="syntax"></a>구문
**Calendar.MonthsLong**()

**Calendar.MonthsShort**()

**Calendar.WeekdaysLong**()

**Calendar.WeekdaysShort**()

**Clock.AmPm**()

**Clock.AmPmShort**()

**Clock.IsClock24**()

## <a name="examples"></a>예
1. Dropdown 컨트롤을 삽입합니다.
2. **[Items](../controls/properties-core.md)** 속성의 수식을 다음과 같이 설정합니다.
   
   * **Calendar.MonthsLong()**
3. 앱 사용자가 자신의 언어로 달을 선택할 수 있습니다.  **MonthsLong**을 **Calendar**에서 반환하는 단일 열 테이블로 대체하여 요일 및 시간 선택기를 만들 수 있습니다.

"en-US"를 반환하는 **[Language](function-language.md)** 가 사용되는 미국의 **Calendar** 함수는 다음을 반환합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Calendar.MonthsLong()** |반환 값에는 각 월의 전체 이름이 "1 월"부터 포함 됩니다. |[ "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" ] |
| **Calendar.MonthsShort()** |반환 값에는 각 월의 약식 이름이 "1 월"부터 포함 됩니다. |[ "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" ] |
| **Calendar.WeekdaysLong()** |반환 값에는 각 요일의 전체 이름이 "일요일"부터 포함 됩니다. |[ "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" ] |
| **Calendar.WeekdaysShort()** |반환 값에는 각 요일의 약식 이름이 "일요일"부터 포함 됩니다. |[ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" ] |
| **Clock.AmPm()** |이 언어는 12시간제를 사용합니다. 반환 값에 전체 AM 및 PM 지정의 대문자 버전이 포함됩니다. |[ "AM", "PM" ] |
| **Clock.AmPmShort()** |이 언어는 12시간제를 사용합니다. 반환 값에 짧은 AM 및 PM 지정의 대문자 버전이 포함됩니다. |[ "A", "P" ] |
| **Clock.IsClock24()** |이 언어는 12시간제를 사용합니다. |**false** |

