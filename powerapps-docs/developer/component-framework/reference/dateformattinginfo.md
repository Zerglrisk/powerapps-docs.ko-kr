---
title: DateFormattingInfo | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
ms.openlocfilehash: fb6dc5c67cc0ea031ab4e264d282458163ee46a0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344833"
---
# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="abbreviateddaynames"></a>abbreviatedDayNames

{"Sun", "Mon", "화요일", "수요일", "목요일", "금요일", "Sat"}

**형식**: `string`

### <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{"Jan", "2 월", "Mar", "Apr", "5 월", "6 월", "7 월", "8 월", "9 월", "Oct", "11 월", "Dec", ""}

**형식**: `string[]`

### <a name="abbreviatedmonthnames"></a>Datetimeformatinfo.abbreviatedmonthnames

{"Jan", "2 월", "Mar", "Apr", "5 월", "6 월", "7 월", "8 월", "9 월", "Oct", "11 월", "Dec", ""}

**형식**: `string[]`

### <a name="amdesignator"></a>Datetimeformatinfo.amdesignator

오전

**형식**: `string`

### <a name="calendar"></a>캘린더

**형식**: `object`

@No__t_0 개체에는 다음 속성이 포함 되어 있습니다.

|이름|유형|설명|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/날짜 (253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/날짜 (-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

### <a name="calendarweekrule"></a>calendarWeekRule

**형식**: `number`

### <a name="dateseparator"></a>dateSeparator

"/"

**형식**: `string`

### <a name="daynames"></a>Datetimeformatinfo.daynames

{"일요일", "월요일", "화요일", "수요일", "목요일", "금요일", "토요일"}

**형식**: `string[]`

### <a name="firstdayofweek"></a>firstDayOfWeek

**형식**: `number`

@No__t_0 속성은 다음 값 중 하나로 설정할 수 있습니다.

|Value|임을|
|--|--|
|0|일요일|
|1|월|
|2|화요일|
|3|수요일|
|4|자원은|
|5|까지|
|6|토요일|

### <a name="fulldatetimepattern"></a>Datetimeformatinfo.fulldatetimepattern

"dddd, MMMM d, yyyy h:mm: ss tt"

**형식**: `string`

### <a name="longdatepattern"></a>Datetimeformatinfo.longdatepattern

yyyy, MMMM d, yyyy "

**형식**: `string`

### <a name="longtimepattern"></a>Datetimeformatinfo.longtimepattern

"hh: mm: ss tt"

**형식**: `string`

### <a name="monthdaypattern"></a>Datetimeformatinfo.monthdaypattern

"MMMM dd"

**형식**: `string`

### <a name="monthgenitivenames"></a>monthGenitiveNames

{"1 월", "2 월", "3 월", ...  "12 월", ""}

**형식**: `string[]`

### <a name="monthnames"></a>monthNames

{"1 월", "2 월", "3 월", ...  "12 월", ""}

**형식**: `string[]`

### <a name="pmdesignator"></a>Datetimeformatinfo.pmdesignator

M

**형식**: `string`

### <a name="shortdatepattern"></a>Datetimeformatinfo.shortdatepattern

"M/d/yyyy"

**형식**: `string`

### <a name="shorttimepattern"></a>Datetimeformatinfo.shorttimepattern

"h:mm tt"

**형식**: `string`

### <a name="shortestdaynames"></a>shortestDayNames

{"Su", "Mo", "Tu", "당사", "Th", "Fr", "Sa"}

**형식**: `string[]`

### <a name="sortabledatetimepattern"></a>Datetimeformatinfo.sortabledatetimepattern

yyyy'-'mm'-'dd't'hh-'MM'-% Ddn ': ' MM ': ' ss '

**형식**: `string`

### <a name="timeseparator"></a>timeSeparator

":"

**형식**: `string`

### <a name="universalsortabledatetimepattern"></a>System.globalization.datetimeformatinfo.universalsortabledatetimepattern

"yyyy'-'mm'-'dd't'hh-'MM'-'dd HH ': ' MM ': ' ss'Z '"

**형식**: `string`

### <a name="yearmonthpattern"></a>Datetimeformatinfo.yearmonthpattern

"MMMM yyyy"

**형식**: `string`


### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)