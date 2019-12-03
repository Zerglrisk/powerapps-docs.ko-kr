---
title: Now, Today 및 IsToday 함수 | Microsoft Docs
description: Power Apps의 Now, Today 및 IsToday 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43f6dfcff0c4174301eda5cb8dde2067081d91e2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730526"
---
# <a name="now-today-and-istoday-functions-in-power-apps"></a>Power Apps의 Now, Today 및 IsToday 함수
현재 날짜와 시간을 반환하고, 날짜/시간 값이 오늘인지 테스트합니다.

## <a name="description"></a>설명
**Now** 함수는 현재 날짜와 시간을 날짜/시간 값으로 반환합니다.

**Today** 함수는 현재 날짜를 날짜/시간 값으로 반환합니다. 시간 부분은 자정입니다. **Today**는 오늘 자정부터 내일 자정까지의 하루 동안에 동일한 값을 갖습니다.

**IsToday** 함수는 날짜/시간 값이 오늘 자정과 내일 자정 사이에 속하는지 여부를 테스트합니다. 이 함수는 부울(**true** 또는 **false**) 값을 반환합니다.

이러한 함수는 모두 현재 사용자의 현지 시간으로 작동합니다.

자세한 내용은 [날짜 및 시간 작업](../show-text-dates-times.md)을 참조하세요.

## <a name="volatile-functions"></a>일시적 함수
**Now** 및 **Today**는 일시적 함수입니다.  이러한 함수 중 하나는 평가될 때마다 다른 값을 반환합니다.  

데이터 흐름 수식을 사용하면 표시되는 수식을 다시 계산하는 경우 일시적 함수는 다른 값만을 반환합니다.  수식에서 변경되는 내용이 없으면 앱의 실행 과정에서 같은 값을 갖습니다.

예를 들어 앱이 활성화되어 있는 동안 **Label1.Text = Now()** 를 포함한 레이블 컨트롤은 변경되지 않습니다.  앱을 닫았다가 다시 열면 새로운 값이 나타납니다.

함수가 다른 내용이 변경된 수식의 일부인 경우 다시 평가됩니다.  예를 들어 이 예제가 **Label1.Text = DateAdd( Now(), Slider1.Value, Minutes )** 를 포함한 슬라이더 컨트롤을 포함하도록 변경하면 슬라이더 컨트롤의 값이 변경되고 레이블의 텍스트 속성이 다시 평가될 때마다 현재 시간이 검색됩니다.

[동작 수식](../working-with-formulas-in-depth.md)에서 사용될 경우 일시적 함수는 동작 수식이 계산될 때마다 평가됩니다.  예제는 아래를 참조하세요.

## <a name="syntax"></a>구문
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DateTime* - 필수 항목입니다.  테스트할 날짜/시간 값입니다.

## <a name="examples"></a>예
이 섹션의 예제에서 현재 시간은 **2015년 2월 12일** **오전 3시 59분**이며, 언어는 **ko-kr**입니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |현재 날짜와 시간을 검색하여 문자열로 표시합니다. |"02/12/2015 03:59:00" |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |시간 부분은 자정으로 유지한 채 현재 날짜만 검색하여 문자열로 표시합니다. |"02/12/2015 00:00:00" |
| **IsToday( Now() )** |현재 날짜와 시간이 오늘 자정과 내일 자정 사이에 속하는지 여부를 테스트합니다. |**true** |
| **IsToday( Today() )** |현재 날짜가 오늘 자정과 내일 자정 사이에 속하는지 여부를 테스트합니다. |**true** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |현재 날짜와 시간을 검색하고, 결과에 12일을 추가하여 이를 문자열로 표시합니다. |"02/24/2015 03:59:00" |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |현재 날짜를 검색하고, 결과에 12일을 추가하여 이를 문자열로 표시합니다. |"02/24/2015 00:00:00" |
| **IsToday( DateAdd( Now(), 12 ) )** |현재 날짜와 시간에 12일을 추가한 값이 오늘 자정과 내일 자정 사이에 속하는지 여부를 테스트합니다. |**false** |
| **IsToday( DateAdd( Today(), 12 ) )** |현재 날짜에 12일을 추가한 값이 오늘 자정과 내일 자정 사이에 속하는지 여부를 테스트합니다. |**false** |

#### <a name="display-a-clock-that-updates-in-real-time"></a>실시간으로 업데이트되는 시계 표시

1. **[Timer](../controls/control-timer.md)** 제어를 추가하고, 해당 **Duration** 속성을 **1000**으로 설정하고, 해당 **Repeat** 속성을 **true**로 설정합니다.

    타이머는 1초 동안 실행되고, 자동으로 다시 시작되며, 해당 패턴을 계속합니다. 

1. 컨트롤의 **OnTimerEnd** 속성을 이 수식으로 설정합니다.

    **Set( CurrentTime, Now() )**

    (매초 후에) 타이머가 다시 시작될 때마다 이 수식은 **CurrentTime** 전역 변수를 **Now** 함수의 현재 값으로 설정합니다.

    ![수식 OnTimerEnd = Set(CurrentTime, Now())를 포함한 타이머 컨트롤을 포함하는 화면](media/function-now-today-istoday/now-set-currenttime.png)

1. **[레이블](../controls/control-text-box.md)** 컨트롤을 추가하고, **Text** 속성을 다음 수식으로 설정합니다.

    **Text( CurrentTime, LongTime24 )**

    **[Text](function-text.md)** 함수를 사용하여 원하는 시간 및 날짜를 지정하거나 이 속성을 **CurrentTime**으로 설정하여 시간 및 분을 표시합니다(초 제외).

    ![Text( CurrentTime, LongTime24)로 설정된 Text 속성을 포함한 레이블 컨트롤을 포함하는 화면](media/function-now-today-istoday/now-use-currenttime.png)

1. F5 키를 눌러 앱을 미리 본 다음, 클릭하거나 탭하여 타이머를 시작합니다.

    레이블은 지속적으로 현재 시간을 보여줍니다(초 포함).

    ![네 개의 시간 값(13:50:22, 13:50:45, 13:51:03 및 13:51:25)을 보여주는 네 개의 화면](media/function-now-today-istoday/now-four-times.png)

1. 타이머의 **AutoStart** 속성을 **true**로 설정하고 해당 **Visible** 속성을 **false**로 설정합니다.

    타이머는 표시되지 않으며 자동으로 시작합니다.

1. 다음 예제와 같이 **CurrentTime** 변수에 유효한 값이 있도록 화면의 **[OnStart](../controls/control-screen.md)** 속성을 설정합니다.

    **Set(CurrentTime, Now())**

    (1초 동안 타이머를 실행하기 전에) 앱이 시작되자마자 레이블이 나타납니다.
