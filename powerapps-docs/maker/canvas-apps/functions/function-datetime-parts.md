---
title: Day, Month, Year, Hour, Minute, Second 및 Weekday 함수 | Microsoft Docs
description: PowerApps의 Day, Month, Year, Hour, Minute, Second 및 Weekday 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bc5d17903ea5cfe834fd4e0987b4fc4613a1ad65
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992805"
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-powerapps"></a>PowerApps의 Day, Month, Year, Hour, Minute, Second 및 Weekday 함수
날짜/시간 값의 개별 구성 요소를 반환합니다.

## <a name="description"></a>설명
**Day** 함수는 1에서 31까지, 날짜/시간 값의 일 구성 요소를 반환합니다.

**Month** 함수는 1에서 12까지, 날짜/시간 값의 월 구성 요소를 반환합니다.

**Year** 함수는 1900부터, 날짜/시간 값의 연도 구성 요소를 반환합니다.

**Hour** 함수는 0(12:00 AM)부터 23(11:00 PM)까지, 날짜/시간 값의 시간 구성 요소를 반환합니다.

**Minute** 함수는 0부터 59까지, 날짜/시간 값의 분 구성 요소를 반환합니다.

**Second** 함수는 0부터 59까지, 날짜/시간 값의 초 구성 요소를 반환합니다.

**Weekday** 함수는 날짜/시간 값의 요일을 반환합니다.  기본적으로 결과의 범위는 1(일요일)에서 7(토요일)까지 입니다.  Microsoft Excel Weekday 함수 코드 또는 StartOfWeek 열거형 값을 사용하여 다른 범위를 지정할 수 있습니다.

| Excel 코드 | StartOfWeek 열거형 | 설명 |
| --- | --- | --- |
| **1**, **17** |**StartOfWeek.Sunday** |숫자 1(일요일) ~ 7(토요일).  기본값. |
| **2**, **11** |**StartOfWeek.Monday** |숫자 1(월요일) ~ 7(일요일). |
| **3** |**StartOfWeek.MondayZero** |숫자 0(월요일) ~ 6(일요일). |
| **12** |**StartOfWeek.Tuesday** |숫자 1(화요일) ~ 7(월요일). |
| **13** |**StartOfWeek.Wednesday** |숫자 1(수요일) ~ 7(화요일). |
| **14** |**StartOfWeek.Thursday** |숫자 1(목요일) ~ 7(수요일). |
| **15** |**StartOfWeek.Friday** |숫자 1(금요일) ~ 7(목요일). |
| **16** |**StartOfWeek.Saturday** |숫자 1(토요일) ~ 7(금요일). |

모든 함수는 숫자를 반환합니다.

자세한 내용은 [날짜 및 시간 작업](../show-text-dates-times.md)을 참조하세요.

## <a name="syntax"></a>구문
**Day**( *DateTime* )<br>**Month**( *DateTime* )<br>**Year**( *DateTime* )<br>**Hour**( *DateTime* )<br>**Minute**( *DateTime* )<br>**Second**( *DateTime* )

* *DateTime* - 필수 항목이며,  연산을 수행할 날짜/시간 값입니다.  

**Weekday**( *DateTime* [, *WeekdayFirst* ] )<br>

* *DateTime* - 필수 항목입니다.  연산을 수행할 날짜/시간 값입니다. 
* *WeekdayFirst* - 선택 항목입니다.  주를 시작할 요일을 지정하는 Excel 코드입니다.  제공되지 않으면 1(일요일부터)이 사용됩니다.

## <a name="examples"></a>예
아래 예제에서 현재 시간은 **Thursday, April 9, 2015**의 **3:59:37 PM**입니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Year(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 연도 구성 요소를 반환합니다. |2015 |
| **Month(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 월 구성 요소를 반환합니다. |4 |
| **Day(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 일 구성 요소를 반환합니다. |9 |
| **Hour(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 시간 구성 요소를 반환합니다. |15 |
| **Minute(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 분 구성 요소를 반환합니다. |59 |
| **Second(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 초 구성 요소를 반환합니다. |37 |
| **Weekday(&nbsp;Now()&nbsp;)** |현재 시간과 날짜의 평일 구성 요소를 반환하고, 기본 시작 요일을 일요일로 사용합니다. |5 |
| **Weekday(&nbsp;Now(),&nbsp;14&nbsp;)** |Excel 코드를 사용하여 주의 시작을 목요일로 지정하여 현재 시간 및 날짜의 요일 구성 요소를 반환합니다. |1 |
| **Weekday(&nbsp;Now(),&nbsp;StartOfWeek.Wednesday&nbsp;)** |**StartOfWeek** 열거형을 사용하여 주의 시작을 수요일로 지정하여 현재 시간 및 날짜의 요일 구성 요소를 반환합니다. |2 |

