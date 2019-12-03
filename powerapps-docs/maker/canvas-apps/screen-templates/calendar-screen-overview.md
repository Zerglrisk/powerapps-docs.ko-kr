---
title: 달력-화면 템플릿 | Microsoft Docs
description: 캔버스 앱에 대 한 달력 화면 템플릿이 어떻게 작동 하는지 이해 하 고, 화면을 수정 하 고, 앱의 일부로 확장
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 945a4fd3c017363a8c43171c8e891e0c32c84a0f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675214"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Canvas 앱에 대 한 달력 화면 템플릿 개요

Canvas 앱에서 사용자의 Office 365 Outlook 계정에서 예정 된 이벤트를 보여 주는 달력 화면을 추가 합니다. 사용자는 달력에서 날짜를 선택 하 고 해당 일의 이벤트 목록을 스크롤할 수 있습니다. 목록에 표시 되는 세부 정보를 변경 하 고, 각 이벤트에 대 한 자세한 정보를 표시 하는 두 번째 화면을 추가 하 고, 각 이벤트에 대 한 참석자 목록을 표시 하 고, 다른 사용자 지정할 수 있습니다.

또한 [전자 메일](email-screen-overview.md), 조직의 [사용자](people-screen-overview.md) 및 모임에 초대 하는 사용자의 [사용 가능 여부](meeting-screen-overview.md) 와 같이 Office 365의 다른 데이터를 표시 하는 다른 템플릿 기반 화면을 추가할 수 있습니다.

이 개요에서는 다음과 같은 방법을 배웁니다.
> [!div class="checklist"]
> * 기본 달력 화면을 사용 하는 방법입니다.
> * 수정 하는 방법
> * 앱에 통합 하는 방법

이 화면의 기본 기능을 자세히 알아보려면 [달력 화면 참조](calendar-screen-reference.md)를 참조 하세요.

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="default-functionality"></a>기본 기능

템플릿에서 일정 화면을 추가 하려면 다음을 수행 합니다.

1. 파워 앱에 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음 앱을 만들거나 Power apps 스튜디오에서 기존 앱을 엽니다.

    이 항목은 휴대폰 앱을 표시 하지만 동일한 개념은 태블릿 앱에도 적용 됩니다.

1. 리본의 **홈** 탭에서 **새 화면** > **달력**을 선택 합니다.

    기본적으로 화면은 다음과 같이 표시 됩니다.

    ![달력 화면](media/calendar-screen/calendar-initial.png)

1. 데이터를 표시 하려면 화면 위쪽의 드롭다운 목록에서 옵션을 선택 합니다.

    ![로드 완료 후의 달력 화면](./media/calendar-screen/calendar-screen.png)

몇 가지 유용한 참고 사항:

* 오늘 날짜가 기본적으로 선택 되어 있으며, 오른쪽 위 모퉁이에 있는 달력 아이콘을 선택 하 여 쉽게 반환할 수 있습니다.
* 다른 날짜를 선택 하는 경우 원 안에 원이 표시 되 고 밝은 색 사각형 (기본 테마가 적용 된 경우 파란색)이 오늘 날짜를 둘러쌉니다.
* 특정 날짜에 대 한 이벤트를 하나 이상 예약 하면 달력의 해당 날짜 아래에 작은 색 원이 나타납니다.
* 하나 이상의 이벤트가 예약 된 날짜를 선택 하는 경우 해당 이벤트는 일정 아래 목록에 표시 됩니다.

## <a name="modify-the-screen"></a>화면 수정

몇 가지 일반적인 방법으로이 화면의 기본 기능을 수정할 수 있습니다.

* [달력을 지정](calendar-screen-overview.md#specify-the-calendar)합니다.
* [이벤트에 대 한 다른 정보를 표시](calendar-screen-overview.md#show-different-details-about-an-event)합니다.
* [비블로킹 이벤트를 숨깁니다](calendar-screen-overview.md#hide-nonblocking-events).

화면을 추가로 수정 하려면 [달력 화면 참조](./calendar-screen-reference.md) 를 가이드로 사용 합니다.

### <a name="specify-the-calendar"></a>일정 지정

사용자가 볼 수 있는 달력을 이미 알고 있는 경우 앱을 게시 하기 전에 해당 달력을 지정 하 여 화면을 단순화할 수 있습니다. 이렇게 변경 하면 일정을 제거할 수 있도록 일정 드롭다운 목록이 필요 없게 됩니다.

1. 앱에서 기본 화면의 **[OnStart](../controls/control-screen.md)** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > 이 수식은 일정을 선택 하는 드롭다운 목록의 **Onselect** 속성 기본값에서 약간 편집 됩니다. 해당 컨트롤에 대 한 자세한 내용은 [달력 화면 참조](./calendar-screen-reference.md#calendar-drop-down)에서 해당 섹션을 참조 하세요.

1. 중괄호를 포함 하 여 `{YourCalendarNameHere}`을 표시할 달력의 이름 (예: **calendar**)으로 바꿉니다.

    > [!IMPORTANT]
    > 다음 단계에서는 앱에 달력 화면을 하나만 추가 했다고 가정 합니다. 하나 이상의를 추가한 경우 컨트롤 이름 (예: **iconCalendar1**)이 다른 숫자로 종료 되 고 그에 따라 수식을 조정 해야 합니다.

1. **IconCalendar1** 컨트롤의 **Y** 속성을 다음 식으로 설정 합니다.

    `RectQuickActionBar1.Height + 20`

1. **LblMonthSelected1** 컨트롤의 **Y** 속성을 다음 식으로 설정 합니다.

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. **LblNoEvents1** 컨트롤의 **Text** 속성을 다음 값으로 설정 합니다.

    `"No events scheduled"`

1. **LblNoEvents1** 의 **Visible** 속성을 다음 수식으로 설정 합니다.

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. 다음 컨트롤을 삭제 합니다.

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. 달력 화면이 기본 화면이 아닌 경우 응용 프로그램을 테스트할 수 있도록 기본 화면에서 일정 화면으로 이동 하는 단추를 추가 합니다.

    예를 들어, 빈 페이지에서 만든 앱에 달력 화면을 추가한 경우 **Screen2** 로 이동 하는 **Screen1** 에 단추를 추가 합니다.

1. 앱을 저장 한 다음 브라우저 또는 모바일 장치에서 테스트 합니다.

### <a name="show-different-details-about-an-event"></a>이벤트에 대 한 다른 세부 정보 표시

기본적으로 **CalendarEventsGallery**라는 달력 아래 갤러리에는 시작 시간, 기간, 제목 및 각 이벤트의 위치가 표시 됩니다. [Office 365 커넥터가](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) 지 원하는 필드 (예: 구성 도우미)를 표시 하도록 갤러리를 구성할 수 있습니다.

1. **CalendarEventsGallery**에서 새 또는 기존 레이블의 **Text** 속성을 `ThisItem` 다음에 마침표를 설정 합니다.

    IntelliSense는 선택할 수 있는 필드를 나열 합니다.

1. 원하는 필드를 선택 합니다.

    레이블은 지정한 정보 유형을 표시 합니다.

### <a name="hide-nonblocking-events"></a>비블로킹 이벤트 숨기기

많은 사무실에서 팀 멤버는 사무실에서 사라질 때 서로를 알리기 위해 모임 요청을 보냅니다. 사용자의 일정이 차단 되지 않도록 요청을 보내는 사람은 해당 가용성을 **무료**로 설정 합니다. 이러한 이벤트는 일정 및 갤러리에서 몇 가지 속성을 업데이트 하 여 숨길 수 있습니다.

1. **CalendarEventsGallery** 의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    이 수식에서 **필터** 함수는 선택한 것 외의 날짜에 대해 예약 된 이벤트 뿐만 아니라 가용성을 **Free**로 설정 하는 이벤트도 숨깁니다.

1. 달력에서 **Circle** 컨트롤의 **Visible** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    이 수식에는 이전 수식과 동일한 필터가 포함 되어 있습니다. 따라서 선택 된 날짜에 있고 가용성을 **Free**로 설정 하지 않은 이벤트가 하나 이상 있는 경우에만 이벤트 표시기 원이 날짜 아래에 나타납니다.

## <a name="integrate-the-screen-into-an-app"></a>앱에 화면 통합

달력 화면은 자체의 강력한 컨트롤 번들로, 일반적으로 더 크고 더 다양 한 앱의 일부로 가장 효과적으로 수행 됩니다. 이러한 옵션을 추가 하는 등 여러 가지 방법으로이 화면을 더 큰 앱에 통합할 수 있습니다.

* [이벤트 세부 정보를 봅니다](calendar-screen-overview.md#view-event-details).
* [이벤트 참석자를 표시](calendar-screen-overview.md#show-event-attendees)합니다.

### <a name="view-event-details"></a>이벤트 세부 정보 보기

사용자가 **CalendarEventsGallery**에서 이벤트를 선택 하는 경우 해당 이벤트에 대 한 자세한 정보를 보여 주는 다른 화면을 열 수 있습니다.

> [!NOTE]
> 이 절차에서는 동적 콘텐츠가 있는 갤러리에 이벤트 세부 정보를 표시 하지만 다른 방법을 사용 하 여 비슷한 결과를 달성할 수 있습니다. 예를 들어, 일련의 레이블을 대신 사용 하 여 더 많은 디자인 제어를 얻을 수 있습니다.

1. 빈 유연한 높이 갤러리와 일정 화면으로 다시 이동 하는 단추를 포함 하는 **EventDetailsScreen**라는 빈 화면을 추가 합니다.

1. 유연한 높이 갤러리에서 **Label** 컨트롤과 **HTML 텍스트** 컨트롤을 추가 하 고 둘 다의 **autoheight** 속성을 **true**로 설정 합니다.

    > [!NOTE]
    > Power Apps는 각 이벤트의 메시지 본문을 HTML 텍스트로 검색 하므로 **html 텍스트** 컨트롤에 해당 내용을 표시 해야 합니다.

1. **HTML 텍스트** 컨트롤의 **Y** 속성을 다음 식으로 설정 합니다.

    `Label1.Y + Label1.Height + 20`

1. 필요에 따라 스타일 요구에 맞게 추가 속성을 조정 합니다.

    예를 들어 **HTML 텍스트** 컨트롤 아래에 구분선을 추가 하는 것이 좋습니다.

1. 유연한 높이 갤러리의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    이 수식은 **_selectedCalendarEvent**의 필드 값으로 설정 되는 동적 데이터의 갤러리를 만듭니다 .이 갤러리는 사용자가 **CalendarEventsGallery** 컨트롤에서 이벤트를 선택할 때마다 설정 됩니다. 더 많은 레이블을 추가 하 여 더 많은 필드를 포함 하도록이 갤러리를 확장할 수 있지만이 집합은 좋은 시작 지점을 제공 합니다.

1. 갤러리 항목을 배치한 상태에서 **Label** 컨트롤의 **Text** 속성을 `ThisItem.Title`로 설정 하 고 **HTML 텍스트** 컨트롤의 **HtmlText** 속성을 `ThisItem.Value`로 설정 합니다.

1. **CalendarEventsGallery**에서 **Title** 컨트롤의 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > **_SelectedCalendarEvent** 변수를 사용 하는 대신 **CalendarEventsGallery**를 대신 사용할 수 있습니다. 선택.

### <a name="show-event-attendees"></a>이벤트 참석자 표시

`Office365.GetEventsCalendarViewV2` 작업은 세미콜론으로 구분 된 필수 및 선택적 참석자 집합을 포함 하 여 각 이벤트에 대 한 다양 한 필드를 검색 합니다. 이 절차에서는 각 참석자 집합을 구문 분석 하 고, 조직 내에 있는 참석자를 확인 하 고, 모든 사용자의 Office 365 프로필을 검색 합니다.

1. 앱에 Office 365 사용자 커넥터가 없는 경우 [추가](../add-data-connection.md)합니다.

1. 모임 참석자의 Office 365 프로필을 검색 하려면 **CalendarEventsGallery** 에 있는 **Title** 컨트롤의 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

이 목록에서는 각 **Clearcollect** 작업에서 수행 하는 작업을 설명 합니다.

- ClearCollect (AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    이 수식은 필수 및 선택 참석자를 단일 문자열로 연결한 다음 각 세미콜론에서 개별 주소로 해당 문자열을 분할 합니다. 그런 다음 수식은 해당 집합에서 빈 값을 필터링 하 고 다른 값을 **AttendeeEmailsTemp**라는 컬렉션에 추가 합니다.

- ClearCollect (AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    이 수식에서는 참석자가 조직에 있는지 여부를 대략적으로 확인 합니다. **_UserDomain** 정의는 앱을 실행 하는 사람의 전자 메일 주소에 있는 도메인 URL 일 뿐입니다. 이 줄은 **AttendeeEmailsTemp** 컬렉션에 **inorg**라는 추가 true/false 열을 만듭니다. **Userdomain** 이 **AttendeeEmailsTemp**의 특정 행에 있는 전자 메일 주소의 도메인 URL과 동일한 경우이 열에 **true** 가 포함 됩니다.

    이 접근 방식은 항상 정확한 것은 아니지만 매우 가깝습니다. 예를 들어 조직의 특정 참석자는 Jane@OnContoso.com와 같은 전자 메일 주소를 포함할 수 있지만 **_userDomain** 는 Contoso.com입니다. 앱 사용자와 Jane은 동일한 회사에서 작동할 수 있지만 전자 메일 주소에는 약간의 차이가 있습니다. 이와 같은 경우에는 다음 수식을 사용할 수 있습니다.

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    그러나이 수식은 Contoso.com와 같은 **_userDomain** 와 Jane@NotTheContosoCompany.com 같은 전자 메일 주소를 찾지만 이러한 사용자는 같은 회사에서 작동 하지 않습니다.

- ClearCollect (MyPeople)

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    Office 365 프로필을 검색 하려면 [Office365Users](https://docs.microsoft.com/connectors/office365users/#userprofile) 또는 [Office365Users UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) 작업을 사용 해야 합니다. 이러한 작업은 먼저 사용자의 조직에 있는 참석자에 대 한 모든 Office 365 프로필을 수집 합니다. 그런 다음 작업은 조직 외부의 참석자를 위한 몇 가지 필드를 추가 합니다. **ForAll** 루프가 순서를 보장 하지 않기 때문에 이러한 두 항목을 별개의 작업으로 구분 했습니다. 따라서 **ForAll** 는 조직 외부의 참석자를 먼저 수집할 수 있습니다. 이 경우 **MyPeople** 에 대 한 스키마는 **DisplayName**, **Id**, **JobTitle**및 **UserPrincipalName**만 포함 합니다. 그러나 UserProfile 작업은 보다 더 다양 한 데이터를 검색 합니다. 따라서 **MyPeople** 컬렉션을 강제로 실행 하 여 다른 프로필 전에 Office 365 프로필을 추가 합니다.

    > [!NOTE]
    > **Clearcollect** 함수를 하나만 사용 하 여 동일한 결과를 얻을 수 있습니다.

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

이 연습을 완료 하려면 다음을 수행 합니다.

1. **Items** 속성이 **MyPeople**로 설정 된 갤러리를 포함 하는 화면을 추가 합니다.

1. **CalendarEventsGallery**에 있는 **제목** 컨트롤의 **onselect** 속성에서 이전 단계에서 만든 화면에 **Navigate** 함수를 추가 합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 참조 설명서를 봅니다](calendar-screen-reference.md).
* [Office 365 Outlook 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-outlook.md).
* [Office 365 사용자 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-users.md).
