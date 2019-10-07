---
title: DateAdd, DateDiff 및 TimeZoneOffset 함수 | Microsoft Docs
description: PowerApps의 DateAdd, DateDiff 및 TimeZoneOffset 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8108dbc1c78ba57e989f7bebeb8bd0f42f696360
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985138"
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-powerapps"></a>PowerApps의 DateAdd, DateDiff 및 TimeZoneOffset 함수
날짜/시간 값의 차이를 추가하거나 찾아서 현지 시간과 UTC 사이의 변환을 수행합니다.

## <a name="description"></a>설명
**DateAdd** 함수는 날짜/시간 값에 단위 수를 추가합니다. 결과는 새 날짜/시간 값입니다. 음수 값을 지정하여 날짜/시간 값에서 단위 수를 뺄 수도 있습니다.

**DateDiff** 함수는 두 날짜/시간 값의 차이를 반환합니다. 결과는 단위 수입니다.

두 함수 모두 **밀리초**, **초**, **분**, **시간**, **일**, **월**, **분기** 또는 **연도** 단위를 사용할 수 있습니다.  기본적으로 두 함수 모두 **일**을 단위로 사용합니다.

**TimeZoneOffset** 함수는 사용자의 현지 시간과 UTC(협정 세계시) 사이의 시간을 분 단위로 반환합니다.   

**DateAdd** 및 **TimeZoneOffset**을 사용하면 사용자의 현지 시간과 UTC(협정 세계시) 사이에서 변환이 가능합니다.  **TimeZoneOffset**을 추가하면 현지 시간이 UTC로 변환되고 빼면(음수를 추가)하면 UTC에서 현지 시간으로 변환됩니다.

또한 [날짜, 시간 및 날짜/시간 데이터 형식](/data-types#date-time-and-datetime) 및 자세한 내용은 날짜 [및 시간 작업](../show-text-dates-times.md) 을 참조 하세요.

## <a name="syntax"></a>구문
**DateAdd**( *DateTime*, *Addition* [, *Units* ] )

* *DateTime* - 필수 항목이며, 연산을 수행할 날짜/시간 값입니다.
* *Addition* - 필수 항목입니다. *DateTime*에 추가할 *Units*에 해당하는 숫자입니다.
* *Units* - 선택 사항입니다. 추가할 *단위* 유형입니다. **밀리초**, **초**, **분**, **시간**, **일**, **월**, **분기**또는 **년**입니다.  지정하지 않으면 **일**이 사용됩니다.

**DateDiff**( *StartDateTime*, *EndDateTime* [, *Units* ] )

* *StartDateTime* - 필수 항목입니다. 시작 날짜/시간 값입니다.
* *EndDateTime* - 필수 항목입니다. 종료 날짜/시간 값입니다.
* *Units* - 선택 사항입니다. 추가할 *단위* 유형입니다. **밀리초**, **초**, **분**, **시간**, **일**, **월**, **분기**또는 **년**입니다.  지정하지 않으면 **일**이 사용됩니다.

**TimeZoneOffset**( [ *DateTime* ] )

* *DateTime* - 선택 사항입니다.  오프셋을 반환할 날짜/시간 값입니다.  기본적으로 현재 날짜/시간이 사용됩니다.

## <a name="examples"></a>예
이 모든 예에서 현재 날짜와 시간이 **July 15, 2013, 1:02 PM**이라고 가정합니다.

### <a name="simple-dateadd"></a>간단한 DateAdd

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |현재 날짜 및 시간에 3일(기본 단위)을 추가합니다. |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Hours ),<br>"dd-mm-yyyy hh:mm" )** |현재 날짜 및 시간에 4시간을 추가합니다. |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Months ),<br>"dd-mm-yyyy hh:mm" )** |현재 날짜에 시간 없이 한 달을 추가합니다. **Today**는 시간 구성 요소를 반환하지 않기 때문입니다. |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minutes ),<br>"dd-mm-yyyy hh:mm" )** |현재 날짜 및 시간에서 30분을 뺍니다. |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>간단한 DateDiff

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |두 단위의 차이를 기본 단위인 **일**로 반환합니다. |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Months )** |두 값의 차이를 **월** 단위로 반환합니다. |6 |
| **DateDiff( Now(), Today(), Minutes )** |현재 날짜/시간과 현재 날짜(시간 없음) 사이의 차이를 분 단위로 반환합니다.  **Now**는 **Today**보다 늦기 때문에 결과는 음수가 됩니다. |-782 |

### <a name="converting-to-utc"></a>UTC로 변환
UTC(협정 세계시)로 변환하려면 주어진 시간에 대한 **TimeZoneOffset**을 추가합니다.  

예를 들어 현재 날짜 및 시간이 PDT(태평양 일광 절약 시간), UTC-7 기준 **July 15, 2013, 1:02 PM**이라고 가정하겠습니다.  UTC 기준 현재 시간을 확인하려면 다음을 사용하십시오.

* **DateAdd( Now(), TimeZoneOffset(), Minutes )**

**TimeZoneOffset**의 기본값은 현재 시간이므로 인수를 전달할 필요가 없습니다.

결과를 보기 위해 *dd-mm-yyyy hh:mm* 형식으로 **Text** 함수를 사용하면 **15-07-2013 20:02**가 반환됩니다.

### <a name="converting-from-utc"></a>UTC에서 변환
UTC에서 변환하려면 주어진 시간에서 **TimeZoneOffset**을 뺍니다(음수를 더합니다).

예를 들어 UTC 날짜 및 시간인 **July 15, 2013, 8:02 PM**이 **StartTime**이라는 변수에 저장되어 있다고 가정하겠습니다. 사용자의 표준 시간대를 조정하려면 다음을 사용합니다.

* **DateAdd (StartTime, &minus;TimeZoneOffset (StartTime), Minutes)**

오프셋을 추가하지 않고 빼기 위해 **TimeZoneOffset** 앞에 음수 기호가 있습니다.

결과를 보기 위해 *dd-mm-yyyy hh:mm* 형식으로 **Text** 함수를 사용하면 사용자가 태평양 일광 절약 시간대에 있는 경우 **15-07-2013 13:02**가 반환됩니다.

