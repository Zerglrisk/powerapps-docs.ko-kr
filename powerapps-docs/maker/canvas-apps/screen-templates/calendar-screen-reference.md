---
title: Canvas 앱에 대 한 달력 화면 템플릿에 대 한 참조 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 대 한 달력 화면 템플릿이 작동 하는 방법에 대 한 세부 정보를 이해 합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a586f705780ef370c63dc35e0d63658a437b549e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675358"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Canvas 앱에 대 한 달력 화면 템플릿에 대 한 참조 정보

Power Apps의 캔버스 앱의 경우 달력 화면 템플릿의 각 주요 컨트롤이 화면의 전반적인 기본 기능에 어떻게 기여 하는지 이해 합니다. 이 심층 정보는 컨트롤에서 사용자 입력에 응답 하는 방법을 결정 하는 동작 수식과 기타 속성의 값을 보여 줍니다. 이 화면의 기본 기능에 대 한 개략적인 논의는 [달력 화면 개요](calendar-screen-overview.md)를 참조 하세요.

이 항목에서는 몇 가지 중요 한 컨트롤을 강조 하 고 이러한 컨트롤의 다양 한 속성 (예: **항목** 및 **onselect**)이 설정 되는 식이나 수식을 설명 합니다.

- [일정 드롭다운 (dropdownCalendarSelection)](#calendar-drop-down)
- [달력 아이콘 (iconCalendar)](#calendar-icon)
- [이전 월 펼침 단추 (iconPrevMonth)](#previous-month-chevron)
- [다음-월 펼침 단추 (iconNextMonth)](#next-month-chevron)
- [달력 갤러리 (MonthDayGallery) (+ 자식 컨트롤)](#calendar-gallery)
- [이벤트 갤러리 (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="calendar-drop-down"></a>일정 드롭다운

![dropdownCalendarSelection 컨트롤](media/calendar-screen/calendar-dropdown.png)

- 속성: **항목**<br>
    값: `Office365.CalendarGetTables().value`

    이 값은 앱 사용자의 Outlook 일정을 검색 하는 커넥터 작업입니다. 이 작업에서 검색 하는 [값을](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) 확인할 수 있습니다.

- 속성: **OnChange**<br>값: `Select(dropdownCalendarSelection)`

    사용자가 목록에서 옵션을 선택 하면 컨트롤의 **Onselect** 속성에 있는 함수가 실행 됩니다.

- 속성: **Onselect**<br>
    Value: 다음 코드 블록에 표시 되는 **If** 함수와 그 뒤의 코드 블록에 표시 되는 몇 가지 추가 함수가 있습니다.

   이 수식의 부분은 사용자가 앱을 연 후 드롭다운 목록에서 옵션을 처음 선택 하는 경우에만 실행 됩니다.

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    위의 코드는 다음 변수를 정의 합니다.
    
  - **\_userDomain**: 사용자의 메일 주소에 반영 된 앱 사용자의 회사 도메인입니다.
  - **선택 된\_dateselected**오늘 날짜 (기본적으로)입니다. 달력 갤러리는이 날짜를 강조 표시 하 고 이벤트 갤러리는 해당 날짜에 대해 예약 된 이벤트를 표시 합니다.
  - **\_firstDayOfMonth**: 현재 달의 첫 번째 날입니다. `(Today + (1 - Today)) = Today - Today + 1 = 1`때문에이 **DateAdd** 함수는 항상 월의 첫 번째 날을 반환 합니다.
  - **\_firstDayInView**: 달력 갤러리에서 표시할 수 있는 첫 번째 날짜입니다. 이 값은 해당 월이 일요일에 시작 하지 않는 한 해당 월의 첫 번째 요일과 동일 하지 않습니다. 지난 달의 주 전체가 표시 되지 않도록 하기 위해 **\_firstDayInView** 값이 `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`됩니다.
  - **\_lastDayOfMonth**: 이번 달의 마지막 날으로, 다음 달의 첫 번째 날에서 1 일을 뺀 값입니다.

   사용자가 앱을 처음 열 때 뿐만 아니라 calendar 드롭다운 목록에서 옵션을 선택할 때마다 **If** 함수 뒤의 함수가 실행 됩니다.

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    위의 코드는 다음 변수와 하나의 컬렉션을 정의 합니다.

    - **\_calendarVisible**: 새 선택 항목을 로드 하는 동안 달력이 나타나지 않도록 **false** 로 설정 합니다.
    - **\_showloading**: 새 선택 항목을 로드 하는 동안 로드 표시기가 표시 되도록 **true** 로 설정 합니다.
    - **\_mycalendar**: 올바른 달력의 이벤트가 검색 되도록 **달력 드롭다운** 컨트롤의 현재 값으로 설정 합니다.
    - **\_minDate**: **\_firstDayInView**와 동일한 값으로 설정 합니다. 이 변수는 Outlook에서 이미 검색 되었으며 앱에서 캐시 된 이벤트를 결정 합니다.
    - **\_maxDate**: 달력에서 마지막으로 볼 수 있는 날짜로 설정 합니다. 수식이 `_firstDayInView + 40`되었습니다. 일정은 최대 41 일을 표시 하므로 **\_maxDate** 변수는 항상 마지막으로 볼 수 있는 날을 반영 하 고, Outlook에서 이미 검색 되어 앱에 캐시 된 이벤트를 결정 합니다.
    - **MyCalendarEvents**: **\_MinDate** 에서 **\_maxDate**에 이르는 선택한 달력의 사용자 이벤트 컬렉션으로 설정 합니다.
    - **\_showLoading**: **false**로 설정 합니다. 다른 모든 항목을 로드 한 후에는 **\_calendarVisible** 이 **true** 로 설정 됩니다.

## <a name="calendar-icon"></a>달력 아이콘

![iconCalendar 컨트롤](media/calendar-screen/calendar-today-icon.png)

- 속성: **Onselect**<br>
    Value: 달력 갤러리를 오늘 날짜로 다시 설정 하는 네 가지 함수 **집합** 입니다.

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    위의 코드는 적절 한 달력 뷰를 표시 하는 데 필요한 모든 날짜 변수를 다시 설정 합니다.

    - **선택한\_dateselected** 오늘로 다시 설정 됩니다.
    - **\_firstDayOfMonth** 는 오늘 월의 첫 번째 날로 다시 설정 됩니다.
    - 현재 월을 선택 하는 경우 **\_firstDayInView** 는 볼 수 있는 첫 번째 날짜로 다시 설정 됩니다.
    - **\_lastDayOfMonth** 는 오늘 월의 마지막 날로 다시 설정 됩니다.

    이 항목의 [**Calendar 드롭다운**](#calendar-drop-down) 섹션에서는 이러한 변수에 대해 자세히 설명 합니다.

## <a name="previous-month-chevron"></a>이전 월 펼침 단추

![iconPrevMonth 컨트롤](media/calendar-screen/calendar-back.png)

- 속성: **Onselect**<br>값: 네 개의 **Set** 함수와 달력 갤러리의 이전 월을 표시 하는 **If** 함수:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**, **\_firstDayInView**및 **\_** 에 대 한 정의는이 항목의 [Calendar 드롭다운](#calendar-drop-down) 섹션과 거의 동일 합니다.

    이전 코드의 처음 세 줄은 사용자가 이전 달 펼침 단추를 선택할 때마다 실행 됩니다. 이 코드는 적절 한 달력 뷰를 표시 하는 데 필요한 변수를 설정 합니다. 나머지 코드는 사용자가 이전에 선택한 달력에 대해이 달을 아직 선택 하지 않은 경우에만 실행 됩니다.

    이 경우 **\_minDate** 는 이전 달이 표시 될 때 표시 되는 첫 번째 날입니다. 사용자가이 아이콘을 선택 하기 전에 **\_minDate** 에는 현재 달의 23 일에 대 한 최소 값이 있습니다. 3 월 1 일이 토요일에 속하면 3 월에 대 한 **firstDayInView** 는 2 월 23 일에\_.) 즉, 사용자가이 달을 아직 선택 하지 않은 경우 **\_minDate** 는 새 **\_FirstDayOfMonth**보다 크고 **if** 함수는 **true**를 반환 합니다. 코드가 실행 되 고, 컬렉션과 변수가 업데이트 됩니다.

    - **MyCalendarEvents** 는 [GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) 작업을 사용 하 여 선택한 일정에서 이벤트를 검색 합니다. 날짜 범위는 **\_firstDayInView** 날짜와 **\_minDate** -1 사이입니다. **MyCalendarEvents** 에는 **\_minDate** date의 이벤트가 이미 포함 되어 있으므로이 새 날짜 범위의 최대값에 대해 해당 날짜에서 1을 뺍니다.

    - **\_minDate** 는 이벤트가 검색 된 첫 번째 날짜 이기 때문에 현재 **\_firstDayInView** 로 설정 됩니다. 사용자가 이전 달 펼침 단추를 선택 하 여이 날짜로 반환 하는 경우 **if** 함수는 **false**를 반환 합니다. 이 뷰에 대 한 이벤트가 이미 **MyCalendarEvents**에 캐시 되어 있기 때문에 코드가 실행 되지 않습니다.

## <a name="next-month-chevron"></a>다음 달 갈매기형 수장

![iconNextMonth 컨트롤](media/calendar-screen/calendar-forward.png)

- 속성: **Onselect**<br>
    값: 네 개의 **Set** 함수와 달력 갤러리에서 다음 달을 표시 하는 **If** 함수:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**, **\_firstDayInView**및 **\_** 에 대 한 정의는이 항목의 [Calendar 드롭다운](#calendar-drop-down) 섹션과 거의 동일 합니다.

    사용자가 다음 달 펼침 단추를 선택할 때 실행 되는 이전 코드의 처음 세 줄은 적절 한 달력 뷰를 표시 하는 데 필요한 변수를 설정 합니다. 나머지 코드는 사용자가 이전에 선택한 달력에 대해이 달을 아직 선택 하지 않은 경우에만 실행 됩니다.

    이 경우 **\_maxDate** 는 이전 달이 표시 될 때 마지막으로 표시 되는 날짜입니다. 사용자가 다음 달 펼침 단추를 선택 하기 전에 **\_maxDate** 에는 다음 달의 13 일에 대 한 최대 값이 있습니다. 2 월 1 일은 윤년이 아닌 일요일이 면 **\_maxDate** 는 3 월 13 일 **\_firstDayInView** + 40 일입니다.) 즉, 사용자가이 달을 아직 선택 하지 않은 경우 **\_maxDate** 는 새 **\_LastDayOfMonth**보다 크고 **if** 함수는 **true**를 반환 합니다. 코드가 실행 되 고, 컬렉션과 변수가 업데이트 됩니다.

    - **MyCalendarEvents** 는 [GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) 작업을 사용 하 여 선택한 일정에서 이벤트를 검색 합니다. 날짜 범위는 **\_maxDate** + 1 일, **\_firstDayInView** + 40 일 사이입니다. **MyCalendarEvents** 에 **\_minDate** date의 이벤트가 이미 포함 되어 있으므로이 새 날짜 범위의 최소값에 대해 해당 날짜에 1이 추가 됩니다. **\_firstDayInView** + 40은 **\_maxDate**에 대 한 수식 이므로 범위의 두 번째 날짜는 새 **\_maxDate**뿐입니다.

    - 이벤트가 검색 된 마지막 날짜 이기 때문에 **\_maxDate** 이 **\_firstDayInView** + 40 일로 설정 됩니다. 사용자가 다음 달 펼침 단추를 선택 하 여이 날짜로 반환 하는 경우 **if** 함수는 **false**를 반환 합니다. 이 뷰에 대 한 이벤트가 이미 **MyCalendarEvents**에 캐시 되어 있기 때문에 코드가 실행 되지 않습니다.

## <a name="calendar-gallery"></a>달력 갤러리

![MonthDayGallery 컨트롤](media/calendar-screen/calendar-month-gall.png)

- 속성: **항목**<br>
    값: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  최악의 시나리오에서는 달력 보기가 42 일을 표시 해야 하므로 달력 갤러리의 항목에는 0 ~ 41 집합이 사용 됩니다. 이는 해당 월의 첫 번째가 토요일에 발생 하 고 월의 마지막 날짜가 일요일에 발생 하는 경우에 발생 합니다. 이 경우 달력은 월의 첫 번째를 포함 하는 행에서 6 일을 표시 하 고, 월의 마지막 날짜를 포함 하는 행에서 다음 달의 6 일을 표시 합니다. 이 값은 42의 고유 값 이며,이 값은 선택한 월에 30 분입니다.

- 속성: **WrapCount**<br>
    값: `7`

  이 값은 7 일의 주를 반영 합니다.

### <a name="title-control-in-the-calendar-gallery"></a>달력 갤러리의 제목 컨트롤

![MonthDayGallery 제목 컨트롤](media/calendar-screen/calendar-month-text.png)

- 속성: **텍스트**<br>
    값: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    **\_firstDayInView** 는 ( **\_firstDayOfMonth** ) + 1로 정의 됩니다. 이를 통해 **\_firstDayInView** 는 항상 일요일 이며 **\_FirstDayOfMonth** 는 항상 **monthdaygallery**의 첫 번째 행에 있습니다. 이러한 두 팩트 때문에 **\_firstDayInView** 는 항상 **monthdaygallery**의 첫 번째 셀에 있습니다. **ThisItem** 는 **monthdaygallery** 항목 속성에서 해당 셀의 번호입니다. 따라서 **firstDayInView** 를 시작 점으로\_각 셀은 **\_firstdayinview** + 해당 셀 값의 증분을 표시 합니다.

- 속성: **채우기**<br>
    값: One **If** 함수:

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  **텍스트** 속성 설명에 설명 된 대로 `DateAdd(_firstDayInView, ThisItem.Value)` 표시 되는 셀의 날짜를 나타냅니다. 위의 코드는이를 고려 하 여 다음과 같은 비교를 수행 합니다.
  1. 셀의 값이 오늘 날짜이 고이 셀이 **선택\_** 날짜와 같으면 채우기 값을 제공 하지 마십시오.
  1. 셀의 값이 오늘 날짜 이지만 **선택한\_dateselected**동일 하지 않은 경우 **colorfade 지기** 를 제공 합니다.
  1. 마지막 비교는 명확 하지 않습니다. 셀의 실제 텍스트 값과 셀 항목 값 (표시 되는 숫자 및 항목 번호)을 비교 합니다.<br>

      이를 더 잘 이해 하려면 토요일에 시작 해 서 일요일에 끝나는 월 2018 년 9 월을 고려 합니다. 이 경우 달력은 8 월 31 일까 지 26 일를 표시 하 고 첫 번째 행에 9 월 1 일을 표시 하며 9 월 1 일까 지 `Abs(Title.Text - ThisItem.Value) = 26` 합니다. 그런 다음 `Abs(Title.Text - ThisItem.Value) = 5`합니다. 6 월 30 일과 10 월 1 일부 터 6 월 30 일까 집니다. 이 `Abs(Title.Text - ThisItem.Value)`는 9 월 30 일에 대해 5 이지만 10 월 날짜의 35이 됩니다.<br>

      이는 패턴입니다. 이전 달에서 표시 되는 일의 경우 `Abs(Title.Text - ThisItem.Value)`는 항상 표시 되는 첫째 날의 `Title.Text` 값과 같습니다. 다음 달에 표시 되는 일의 경우 `Abs(Title.Text - ThisItem.Value)`은 항상 해당 월의 첫 번째 셀 (이 경우 10 월 1 일)에서 1을 뺀 값의 **Monthdaygallery** 항목 값과 같습니다. 무엇 보다도, 현재 선택 된 달에 표시 되는 일의 경우, `Abs(Title.Text - ThisItem.Value)`은 항상 해당 월의 첫 번째 항목 값에서 1을 뺀 값과 동일 하며, 이전 예제와 같이 5를 초과 하지 않습니다. 따라서 수식을 `Abs(Title.Text - ThisItem.Value) > 5`으로 작성 하는 것은 완벽 하 게 유효 합니다.

      이 문은 날짜 값이 현재 선택한 월 외부에 있는지 여부를 확인 합니다. 인 경우 **채우기** 는 부분적으로 불투명 한 회색입니다.

    > [!NOTE]
    > **레이블** 컨트롤을 갤러리에 삽입 하 고 **Text** 속성을이 값으로 설정 하 여이 마지막 비교의 유효성을 검사할 수 있습니다.<br>`Abs(Title.Text - ThisItem.Value)`에 대한 답변에 설명되어 있는 단계를 성공적으로 완료하면 활성화됩니다.

- 속성: **표시**<br>
    기본값

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    위의 문은 셀이 현재 선택 된 달이 없는 행에 있는지 여부를 확인 합니다. 해당 날짜 값에서 요일의 요일 값을 빼서 1을 추가 하면 해당 요일이 있는 행의 첫 번째 항목이 항상 반환 됩니다. 따라서이 문은 행의 첫째 요일이 볼 수 있는 월의 마지막 날 이후 인지 여부를 확인 합니다. 이 경우 전체 행에 다음 달의 요일이 포함 되어 있기 때문에 표시 되지 않습니다.

- 속성: **Onselect**<br>
    Value: 선택 된 **\_dateselected** 을 선택한 셀의 날짜로 설정 하는 **집합** 함수입니다.

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>달력 갤러리의 원 컨트롤

![MonthDayGallery Circle 컨트롤](media/calendar-screen/calendar-month-event.png)

- 속성: **표시**<br>
    Value: 선택한 날짜에 대해 이벤트가 예약 되었는지 여부와 **Subcircle** 및 **Title** 컨트롤이 표시 되는지 여부를 결정 하는 수식입니다.

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    모든 이벤트의 **시작** 필드는 해당 셀의 날짜와 동일 하 고, **제목** 컨트롤이 표시 되 면, **subcircle** 컨트롤이 표시 되지 않는 경우 **Circle** 컨트롤이 표시 됩니다. 즉,이 컨트롤은 하루에 하나 이상의 이벤트가 발생 하 고이 날짜가 선택 되지 않은 경우에 표시 됩니다. 이 확인란이 선택 되어 있으면 해당 날짜에 대 한 이벤트가 **CalendarEventsGallery** 컨트롤에 표시 됩니다.

### <a name="subcircle-control-in-the-calendar-gallery"></a>달력 갤러리의 subcircle 컨트롤

![MonthDayGallery Subcircle 컨트롤](media/calendar-screen/calendar-month-selected.png)

- 속성: **표시**<br>
    기본값

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  **Subcircle** 컨트롤은 **선택한\_dateselected** 셀의 날짜와 동일 하 고 **Title** 컨트롤이 표시 될 때 표시 됩니다. 즉, 셀이 현재 선택한 날짜 이면이 컨트롤이 표시 됩니다.

## <a name="events-gallery"></a>이벤트 갤러리

![CalendarEventsGallery 컨트롤](media/calendar-screen/calendar-events-gall.png)

- 속성: **항목**<br>
    Value: 이벤트 갤러리를 정렬 하 고 필터링 하는 수식입니다.

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   **MyCalendarEvents** 컬렉션은 **\_MinDate** 와 **\_maxDate**사이의 모든 이벤트를 포함 합니다. 선택한 날짜에 대해서만 이벤트를 표시 하기 위해 **MyCalendarEvents** 에 필터를 적용 하 여 **\ _dateSelected**에 해당 하는 시작 날짜가 있는 이벤트를 표시 합니다. 그런 다음 항목을 시작 날짜를 기준으로 정렬 하 여 순차적으로 배치 합니다.

## <a name="next-steps"></a>다음 단계

- [이 화면에 대 한 자세한 정보](./calendar-screen-overview.md)
- [PowerApps의 Office 365 Outlook 커넥터에 대 한 자세한 정보](../connections/connection-office365-outlook.md)
- [PowerApps의 Office 365 사용자 커넥터에 대 한 자세한 정보](../connections/connection-office365-users.md)
