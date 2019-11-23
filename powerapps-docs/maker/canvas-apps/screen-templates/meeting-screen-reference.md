---
title: Canvas 앱에 대 한 모임 화면 템플릿에 대 한 참조 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 대 한 모임 화면 템플릿이 작동 하는 방법에 대 한 세부 정보 이해
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c62c3de56534201a81e9f4d453796ebd9b3a0366
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989567"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Canvas 앱에 대 한 모임 화면 템플릿에 대 한 참조 정보

PowerApps의 canvas 응용 프로그램의 경우 모임 화면 템플릿의 각 주요 컨트롤이 화면의 전반적인 기본 기능에 어떻게 기여 하는지 이해 합니다. 이 심층 정보는 컨트롤에서 사용자 입력에 응답 하는 방법을 결정 하는 동작 수식과 기타 속성의 값을 보여 줍니다. 이 화면의 기본 기능에 대 한 개략적인 설명은 [모임 화면 개요](meeting-screen-overview.md)를 참조 하세요.

이 항목에서는 몇 가지 중요 한 컨트롤을 강조 하 고 이러한 컨트롤의 다양 한 속성 (예: **항목** 및 **onselect**)이 설정 되는 식이나 수식을 설명 합니다.

* [초대 탭 (LblInviteTab)](#invite-tab)
* [일정 탭 (LblScheduleTab)](#schedule-tab)
* [텍스트 검색 상자](#text-search-box)
* [아이콘 추가 (AddIcon)](#add-icon)
* [사용자 찾아보기 갤러리](#people-browse-gallery) (+ 자식 컨트롤)
* [모임 사람 갤러리](#meeting-people-gallery) (+ 자식 컨트롤)
* [모임 날짜 선택 (MeetingDateSelect)](#meeting-date-picker)
* [모임 기간 드롭다운 (MeetingDurationSelect)](#meeting-duration-drop-down)
* [모임 시간 찾기 갤러리](#find-meeting-times-gallery) (+ 자식 컨트롤)
* [대화방 찾아보기 갤러리](#room-browse-gallery) (+ 자식 컨트롤)
* [뒤로 펼침 단추 (RoomsBackNav)](#back-chevron) (테 넌 트에 방 목록이 없는 경우에는 표시 되지 않을 수 있음)
* [보내기 아이콘](#send-icon)

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="invite-tab"></a>초대 탭

   ![LblInviteTab 컨트롤](media/meeting-screen/meeting-invite-text.png)

* 속성: **Color**<br>
    값: `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** 는 **LblInviteTab** 컨트롤 또는 **LblScheduleTab** 컨트롤이 선택 되었는지 여부를 확인 하는 데 사용 되는 변수입니다. **_ShowDetails** 값이 **true**이면 **LblScheduleTab** 가 선택 되 고, 값이 **false**이면 **LblInviteTab** 가 선택 됩니다. 즉, **_showDetails** 값이 **true** 이면 (이 탭이 선택 *되지 않음* ) 탭 색은 **LblRecipientCount**의 값과 일치 합니다. 그렇지 않으면 **RectQuickActionBar**의 fill 값과 일치 합니다.

* 속성: **Onselect**<br> 
    값: `Set( _showDetails, false )`

    **_ShowDetails** 변수를 **false**로 설정 합니다. 즉, 초대 탭의 내용이 표시 되 고 **일정** 탭의 내용이 숨겨집니다.

## <a name="schedule-tab"></a>일정 탭

   ![LblInviteTab 컨트롤](media/meeting-screen/meeting-schedule-text.png)

* 속성: **Color**<br>
    값: `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** 는 **LblInviteTab** 컨트롤 또는 **LblScheduleTab** 컨트롤이 선택 되었는지 여부를 확인 하는 데 사용 되는 변수입니다. True 이면 **LblScheduleTab** 가 선택 되 고, false 이면 **LblInviteTab** 가입니다. 즉, **_showDetails** true (이 탭이 선택 *됨* ) 인 경우 탭 색은 **RectQuickActionBar**의 채우기 값과 일치 합니다. 그렇지 않으면 **LblRecipientCount**의 색 값과 일치 합니다.

* 속성: **Onselect**<br>
    값: `Set( _showDetails, true )`

    **_ShowDetails** 변수를 **true**로 설정 합니다 .이는 일정 탭의 내용이 표시 되 고 초대 탭의 내용이 숨겨져 있음을 의미 합니다.

## <a name="text-search-box"></a>텍스트 검색 상자

   ![TextSearchBox 컨트롤](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

화면의 다른 여러 컨트롤이이 항목에 종속 되어 있습니다.

* 사용자가 텍스트 입력을 시작 하면 **PeopleBrowseGallery** 가 표시 됩니다.
* 사용자가 유효한 전자 메일 주소를 입력 하면 **Addicon** 이 표시 됩니다.
* 사용자가 **PeopleBrowseGallery** 내에서 사용자를 선택 하면 검색 내용이 다시 설정 됩니다.

## <a name="add-icon"></a>추가 아이콘

   ![AddIcon 컨트롤](media/email-screen/email-add-icon.png)

이 컨트롤을 통해 사용자는 조직 내에 없는 사람을 작성 중인 모임의 참석자 목록에 추가할 수 있습니다.

* 속성: **표시**<br>
    값: 컨트롤이 표시 되려면 모두 **true** 로 평가 되어야 하는 논리적 검사가 세 가지입니다.

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  이 코드 블록은 다음과 같은 경우에만 **Addicon** 컨트롤이 표시 됨을 표시 합니다.

  * **Textsearchbox** 는 텍스트를 포함 합니다.
  * **Textsearchbox** 의 텍스트는 유효한 전자 메일 주소입니다.
  * **Textsearchbox** 의 텍스트는 **MyPeople** 컬렉션에 이미 존재 하지 않습니다.

* 속성: **Onselect**<br> 
    값: 사용자를 참석자 목록에 추가 하는 **Collect** 문, 사용 가능한 모임 시간을 새로 고치는 변수 및 여러 변수를 설정/해제 하는 방법:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage:1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  이 컨트롤을 선택 하면 유효한 전자 메일 주소 (올바른 전자 메일 주소를 **Textsearchbox**에 입력 한 경우에만 표시 됨)가 **MyPeople** 컬렉션 (이 컬렉션은 참석자 목록)에 추가 된 다음 새 사용자 항목으로 사용 가능한 모임 시간이 새로 고쳐집니다.

  낮은 수준에서이 코드 블록은 다음과 같습니다.
  1. 전자 메일 주소를 **MyPeople** 컬렉션으로 수집 하 고, **DisplayName**, **UserPrincipalName**및 **Mail** 필드에 전자 메일 주소를 수집 합니다.
  1. **Textsearchbox** 컨트롤의 내용을 다시 설정 합니다.
  1. **_ShowMeetingTimes** 변수를 **false**로 설정 합니다. 이 변수는 선택한 참석자가 만족할 때까지 열린 시간을 표시 하는 **FindMeetingTimesGallery**의 표시 여부를 제어 합니다.
  1. **_LoadMeetingTimes** 컨텍스트 변수를 **true**로 설정 합니다. 이 변수는 로딩 상태를 설정 합니다 .이는 **_LblTimesEmptyState** 같은 로드 상태 컨트롤의 표시 유형을 전환 하 여 사용자에 게 데이터를 로드 하 고 있음을 알려 주는 것입니다.
  1. **_SelectedMeetingTime** 를 **Blank ()** 로 설정 합니다. **FindMeetingTimesGallery** 컨트롤에서 선택 된 레코드 **_selectedMeetingTime** 입니다. 다른 참석자를 추가 하면 해당 참석자에 게 이전 **_selectedMeetingTime** 정의를 사용할 수 없다는 것을 의미할 수 있습니다.
  1. **_SelectedRoom** 를 **Blank ()** 로 설정 합니다. **RoomBrowseGallery**에서 선택 된 대화방 레코드 **_selectedRoom** 입니다. 방 전반는 **_selectedMeetingTime**값으로 결정 됩니다. 이 값이 숨겨진 경우에는 **_selectedRoom** 값이 더 이상 유효 하지 않으므로 숨겨진 상태 여야 합니다.
  1. **_RoomListSelected** 을 **false**로 설정 합니다. 이 줄은 모든 사용자에 게 적용 되지 않을 수 있습니다. Office에서는 다른 "방 목록"을 기준으로 대화방을 그룹화 할 수 있습니다. 방 목록이 있는 경우이 화면에는 해당 목록에서 공간을 선택 하기 전에 먼저 방 목록을 선택할 수 있는이 화면이 표시 됩니다. **_RoomListSelected** 의 값은 사용자 (대화방 목록만 있는 테 넌 트)가 대화방 목록 또는 방 목록 내에서 대화방을 볼 지 여부를 결정 하는 값입니다. 사용자가 새 대화방 목록을 다시 선택 하도록 하려면 **false** 로 설정 됩니다.
  1. [Office365 FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 작업을 사용 하 여 참석자에 대해 사용 가능한 모임 시간을 확인 하 고 수집 합니다. 이 작업은 다음을 전달 합니다.
      * *RequiredAttendees* 매개 변수에 대해 선택한 각 사용자의 **UserPrincipalName** 입니다.
      * **MeetingDurationSelect**. *MeetingDuration* 매개 변수에 대해 분을 선택 합니다.
      * MeetingDateSelect SelectedDate + 8 시간을 *시작* 매개 변수로 변환 합니다. 기본적으로 달력 컨트롤의 전체 날짜/시간이 선택한 날짜의 12:00이 되므로 8 시간이 추가 됩니다. 정상적인 업무 시간 내에 전반를 검색 하는 것이 좋습니다. 정상 작업 시작 시간은 오전 8:00입니다.
      * **MeetingDateSelect**. SelectedDate + 17 시간을 *끝* 매개 변수로 변환 합니다. 12:00 AM + 17 = 5:00 PM 때문에 17 시간이 추가 됩니다. 정상적인 작업 종료 시간은 오후 5:00입니다.
      * *Maxcandidates* 매개 변수로 *15* 개 즉, 작업에서 선택한 날짜에 대해 상위 15 개의 사용 가능한 시간만 반환 합니다. 이는 8 시간 안에 16 30 분의 청크만 있고 30 분 모임이이 화면에서 설정 하는 것이 가능 하기 때문에 적합 합니다.
      * *1* 은 *MinimumAttendeePercentage* 매개 변수입니다. 기본적으로 참석자를 사용할 수 없는 경우 모임 시간이 검색 됩니다.
      * *IsOrganizerOptional* 매개 변수를 **false로 설정** 합니다. 앱 사용자는이 회의에 대 한 선택적 참석자가 아닙니다.
      * *Activitydomain* 매개 변수로 "작업" 합니다. 즉, 검색 된 시간은 정상적인 작업 기간 내 에서만 검색 됩니다.
  1. **Clearcollect** 함수는 또한 "StartTime" 및 "EndTime" 이라는 두 개의 열을 추가 합니다. 이렇게 하면 반환 되는 데이터가 간단해 집니다. 
  사용 가능한 시작 및 종료 시간이 포함 된 필드는 **MeetingTimeSlot** 필드입니다. 이 필드는 각각의 제안에 대 한 **날짜/시간** 및 **표준 시간대** 값을 포함 하는 시작 및 종료 레코드를 포함 하는 레코드입니다. 이러한 레코드 중첩을 검색 하는 대신, **MeetingTimes** collection에 "StartTime" 및 "EndTime" 열을 추가 하 여 해당 **시작 > datetime** 및 **End > datetime** 값을 컬렉션의 표면으로 가져옵니다.
  1. 이러한 함수가 모두 완료 되 면 **_loadingMeetingTimes** 변수가 **false**로 설정 되 고 로드 상태가 제거 되며 **_showMeetingTimes** 가 **true**로 설정 되어 **FindMeetingTimesGallery**이 표시 됩니다.

## <a name="people-browse-gallery"></a>사용자 찾아보기 갤러리

   ![PeopleBrowseGallery 컨트롤](media/meeting-screen/meeting-browse-gall.png)

* 속성: **항목**<br>
    기본값 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

이 갤러리의 항목은 [Office365 사용자](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업에서 검색 결과로 채워집니다. 작업은 `Trim(**TextSearchBox**)`의 텍스트를 검색 용어로 사용 하 고 해당 검색을 기준으로 상위 15 개 결과를 반환 합니다.
  
공백에 대 한 사용자 검색이 유효 하지 않으므로 **Textsearchbox** 가 **Trim** 함수에 래핑됩니다. 사용자가 검색 하기 전에 검색 결과를 검색 하면 성능이 저하 되기 때문에 `Office365Users.SearchUser` 작업이 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 함수에 래핑됩니다.

### <a name="people-browse-gallery-title"></a>사용자 찾아보기 갤러리 제목

   ![PeopleBrowseGallery Title 컨트롤](media/meeting-screen/meeting-browse-gall-title.png)

* 속성: **텍스트**<br>
    값: `ThisItem.DisplayName`

    Office 365 프로필의 사용자 표시 이름을 표시 합니다.

* 속성: **Onselect**<br>
    값: 사용자를 참석자 목록에 추가 하는 **Collect** 문, 사용 가능한 모임 시간을 새로 고치는 변수 및 여러 변수를 설정/해제 하는 방법:

    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _selectedUser, ThisItem ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem ); 
            Concurrent(
                Set( _showMeetingTimes, false ),
                UpdateContext( { _loadMeetingTimes: true } ),
                Set( _selectedMeetingTime, Blank() ),
                Set( _selectedRoom, Blank() ),
                Set( _roomListSelected, false ),
                ClearCollect( MeetingTimes, 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ),
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                                MaxCandidates: 15, 
                                MinimumAttendeePercentage: 1, 
                                IsOrganizerOptional: false, 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions,
                        "StartTime", MeetingTimeSlot.Start.DateTime, 
                        "EndTime", MeetingTimeSlot.End.DateTime
                    )
                )
            );
            UpdateContext( { _loadingMeetingTimes: false } );
            Set( _showMeetingTimes, true )
        )
    )
    ```

    높은 수준에서이 컨트롤을 선택 하면 사용자가 **MyPeople** collection (참석자 목록의 앱 저장소)에 추가 되 고 새 사용자 추가에 따라 사용 가능한 모임 시간이 새로 고쳐집니다.

    이 컨트롤을 선택 하는 것은 **Addicon** 컨트롤을 선택 하는 것과 매우 비슷합니다. 유일한 차이점은 `Set(_selectedUser, ThisItem)` 문과 작업의 실행 순서입니다. 따라서이 논의는 심층적이 아닙니다. 자세한 설명은 [Addicon 제어](#add-icon) 섹션을 참조 하세요.

    이 컨트롤을 선택 하면 **Textsearchbox**가 다시 설정 됩니다. 그런 다음 선택 항목이 **MyPeople** 컬렉션에 없으면 컨트롤은 다음을 수행 합니다.
    1. **_LoadMeetingTimes** 상태를 **true** 로 설정 하 고 **_showMeetingTimes** 상태를 **false**로 설정 하 고 **_selectedMeetingTime** 및 **_selectedRoom** 변수를 공백으로 지정 하 고 새 추가를 사용 하 **여** **MeetingTimes** 컬렉션을 새로 고칩니다. 
    1. **_LoadMeetingTimes** 상태를 **false**로 설정 하 고 **_showMeetingTimes** 을 **true**로 설정 합니다. 선택 항목이 이미 **MyPeople** 컬렉션에 있으면 **textsearchbox**의 내용만 다시 설정 합니다.

## <a name="meeting-people-gallery"></a>모임 사용자 갤러리

   ![MeetingPeopleGallery 컨트롤](media/meeting-screen/meeting-people-gall.png)

* 속성: **항목**<br>
    값: `MyPeople`

    **MyPeople** 컬렉션은 **PeopleBrowseGallery Title** 컨트롤을 선택 하 여에 초기화 되거나 추가 되는 사용자의 컬렉션입니다.

* 속성: **Height**<br>
    값: 갤러리의 최대 높이를 350으로 늘릴 수 있도록 하는 논리:

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   이 갤러리의 높이는 갤러리의 항목 수에 맞게 조정 되며 최대 높이는 350입니다. 수식은 **MeetingPeopleGallery**의 단일 행 높이로 76를 사용 하 고 행 수를 곱합니다. **WrapCount** 속성은 2로 설정 되므로 true 행의 수는 `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)`됩니다.

* 속성: **Showscrollbar**<br>
    값: `MeetingPeopleGallery.Height >= 350`

    갤러리의 최대 높이 (350)에 도달 하면 스크롤 막대가 표시 됩니다.

### <a name="meeting-people-gallery-title"></a>모임 사람 갤러리 제목

   ![MeetingPeopleGallery Title 컨트롤](media/meeting-screen/meeting-people-gall-title.png)

* 속성: **Onselect**<br>
    
    값: `Set(_selectedUser, ThisItem)`
    
    **_SelectedUser** 변수를 **MeetingPeopleGallery**에서 선택한 항목으로 설정 합니다.

### <a name="meeting-people-gallery-iconremove"></a>사람들 갤러리 아이콘 제거 모임

   ![MeetingPeopleGallery iconRemove 컨트롤](media/meeting-screen/meeting-people-gall-delete.png)

* 속성: **Onselect**<br>
    값: 참석자 목록에서 사용자를 제거 하는 **remove** 문, 사용 가능한 회의 시간을 새로 고치는 **Collect** 문 및 여러 변수를 전환 합니다.

    ```powerapps-dot
    Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  높은 수준에서이 컨트롤을 선택 하면 참석자 목록에서 해당 사용자가 제거 되 고이 사용자의 제거를 기준으로 사용 가능한 모임 시간이 새로 고쳐집니다.

  이전 코드의 첫 번째 줄 뒤에이 컨트롤을 선택 하는 것은 **Addicon** 컨트롤을 선택 하는 것과 거의 동일 합니다. 따라서이 논의는 심층적이 지 않습니다. 자세한 설명은 [Addicon 제어 섹션](#add-icon)을 참조 하세요.

  코드의 첫 번째 줄에서 선택한 항목이 **MyPeople** 컬렉션에서 제거 됩니다. 코드는 다음과 같습니다.
  1. **Textsearchbox**를 다시 설정 하 고 **MyPeople** collection에서 선택 항목을 제거 합니다. 
  1. **_LoadMeetingTimes** 상태를 **true** 로 설정 하 고 **_showMeetingTimes** 상태를 **false**로 설정 하 고 **_selectedMeetingTime** 및 **_selectedRoom** 변수를 공백으로 지정 하 고 새 추가를 사용 하 **여** **MeetingTimes** 컬렉션을 새로 고칩니다. 
  1. **_LoadMeetingTimes** 상태를 **false**로 설정 하 고 **_showMeetingTimes** 을 **true**로 설정 합니다.

## <a name="meeting-date-picker"></a>모임 날짜 선택

   ![MeetingDateSelect 컨트롤](media/meeting-screen/meeting-datepicker.png)

* 속성: **DisplayMode**<br>
    값: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    **MyPeople** 컬렉션에 하나 이상의 참석자가 추가 될 때까지 모임 날짜를 선택할 수 없습니다.

* 속성: **OnChange**<br>
    값: `Select( MeetingDateSelect )`

    선택한 날짜를 변경 하면이 컨트롤의 **Onselect** 속성에 있는 코드가 실행 됩니다.

* 속성: **Onselect**<br>
    Value: 사용 가능한 회의 시간을 새로 고치는 **Collect** 문과 여러 변수를 전환 합니다.
  
    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadingMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  높은 수준에서이 컨트롤을 선택 하면 사용 가능한 모임 시간이 새로 고쳐집니다. 사용자가 날짜를 변경 하는 경우 해당 날짜에 대 한 참석자의 전반을 반영 하기 위해 사용 가능한 모임 시간이 업데이트 되어야 하기 때문에 유용 합니다.

  초기 **Collect** 문을 제외 하 고이는 **Addicon** 컨트롤의 **onselect** 기능과 동일 합니다. 따라서이 논의는 심층적이 지 않습니다. 자세한 설명은 [Addicon 제어](#add-icon) 섹션을 참조 하세요.

  이 컨트롤을 선택 하면 **Textsearchbox**가 다시 설정 됩니다. 그런 후에 다음을 수행 합니다. 
  1. **_LoadMeetingTimes** 상태를 **true** 로 설정 하 고 **_showMeetingTimes** 상태를 **false**로 설정 하 고 **_selectedMeetingTime** 및 **_selectedRoom** 변수를 공백으로 지정 하 고 새 날짜 선택 항목을 사용 하 여 **MeetingTimes** 컬렉션을 새로 고칩니다. 
  1. **_LoadMeetingTimes** 상태를 **false**로 설정 하 고 **_showMeetingTimes** 을 **true**로 설정 합니다.

## <a name="meeting-duration-drop-down"></a>모임 기간 드롭다운

   ![MeetingDateSelect 컨트롤](media/meeting-screen/meeting-timepicker.png)

* 속성: **DisplayMode**<br>
    값: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    하나 이상의 참석자가 **MyPeople** collection에 추가 될 때까지 모임 기간을 선택할 수 없습니다.

* 속성: **OnChange**<br>
    값: `Select(MeetingDateSelect1)`

    선택한 기간을 변경 하면 **MeetingDateSelect** 컨트롤의 **onselect** 속성의 코드가 실행 됩니다.

## <a name="find-meeting-times-gallery"></a>모임 시간 찾기 갤러리

   ![FindMeetingTimesGallery 컨트롤](media/meeting-screen/meeting-time-gall.png)

* 속성: **항목**<br>
    값: `MeetingTimes`

    [FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 작업에서 검색 된 잠재적인 모임 시간 컬렉션입니다.

* 속성: **표시**<br>
    값: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    갤러리는 **_showMeetingTimes** 이 **true**로 설정 되어 있고 사용자가 **LblScheduleTab** 컨트롤을 선택 하 고 모임에 하나 이상의 참석자가 추가 된 경우에만 표시 됩니다.

### <a name="find-meeting-times-gallery-title"></a>모임 시간 찾기 갤러리 제목

   ![FindMeetingTimesGallery Title 컨트롤](media/meeting-screen/meeting-time-gall-title.png)

* 속성: **텍스트**<br>
    값: 사용자의 현지 시간으로 표시 되는 시작 시간 변환:

    ```powerapps-dot
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime ),
            - TimeZoneOffset(), 
            Minutes
        ),
        DateTimeFormat.ShortTime
    )
    ```

  **StartTime** 의 검색 된 값은 UTC 형식입니다. [UTC에서 현지 시간으로 변환](../functions/function-dateadd-datediff.md#converting-from-utc)하려면 **DateAdd** 함수가 적용 됩니다.
  [텍스트 함수](../functions/function-text.md#datetime) 는 첫 번째 인수로 날짜/시간을 사용 하 고 두 번째 인수를 기준으로 형식을 지정 합니다. **ThisItem**의 현지 시간 변환으로 전달 하 고 **DateTimeFormat**로 표시 합니다.

* 속성: **Onselect**<br>
    값: 여러 변수를 설정/해제 하는 것은 물론 회의실 및 제안 된 전반을 수집 하는 몇 가지 **수집** 문입니다.

    ```powerapps-dot
    Set( _selectedMeetingTime, ThisItem );
    UpdateContext( { _loadingRooms: true } );
    If( IsEmpty( RoomsLists ),
        ClearCollect( RoomsLists, 'Office365'.GetRoomLists().value) );
    If( CountRows( RoomsLists ) <= 1,
        Set( _noRoomLists, true );
        ClearCollect( AllRooms, 'Office365'.GetRooms().value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                    Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability,
                        Availability="Free"
                    ), 
                    "Address", Attendee.EmailAddress.Address
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name 
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" ), 
                "Attendee" 
            )
        ),
        Set( _roomListSelected, false) 
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  높은 수준에서이 코드 블록은 모임에 대해 선택한 날짜/시간을 기준으로 대화방 목록이 없는 사용자에 대해 사용 가능한 방을 수집 합니다. 그렇지 않으면 방 목록만 검색 합니다.

  낮은 수준에서이 코드 블록은 다음과 같습니다.
  1. **_SelectedMeetingTime** 를 선택한 항목으로 설정 합니다. 이는 해당 시간 동안 사용할 수 있는 대화방을 찾는 데 사용 됩니다.
  1. 로드 상태 변수 **_loadingRooms** **true**로 설정 하 여 로드 상태를 설정 합니다.
  1. **RoomsLists** 컬렉션이 비어 있는 경우 사용자의 tenant's 목록을 검색 하 여 **RoomsLists** 컬렉션에 저장 합니다.
  1. 사용자에 게 대화방 목록 또는 하나의 방 목록이 없는 경우:
      1. **RoomBrowseGallery** 컨트롤에 표시 되는 항목을 확인 하는 데 사용 되는,이 **변수는** **true**로 설정 됩니다.
      1. `Office365.GetRooms()` 작업은 테 넌 트에서 처음 100 대화방을 검색 하는 데 사용 됩니다. 이러한 컬렉션은 **Allrooms** 컬렉션에 저장 됩니다.
      1. **_AllRoomsConcat** 변수는 **allrooms** 컬렉션에서 대화방의 처음 20 개 전자 메일 주소에 대 한 세미콜론으로 구분 된 문자열로 설정 됩니다. 이는 [Office365 FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 가 단일 작업에서 20 person 개체의 사용 가능한 시간을 검색 하는 것으로 제한 되기 때문입니다.
      1. **RoomTimeSuggestions** 컬렉션은 [Office365](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 를 사용 하 여 **_selectedMeetingTime** 변수의 시간 값을 기반으로 **allrooms** 컬렉션에서 처음 20 개 대화방의 전반를 검색 합니다. **DateTime** 값의 형식을 올바르게 지정 하는 데 `& "Z"` 사용 됩니다.
      1. **AvailableRooms** 컬렉션이 생성 됩니다. 이는 단순히 "Address" 및 "Name" 이라는 두 개의 추가 열이 추가 된 참석자 전반 **RoomTimeSuggestions** 컬렉션입니다. "Address"는 대화방의 메일 주소이 고 "Name"은 대화방의 이름입니다.
      1. 그런 다음 **AvailableRoomsOptimal** 컬렉션을 만듭니다. "가용성" 및 "참석자" 열을 제거 하는 **AvailableRooms** 컬렉션입니다. 이렇게 하면 **AvailableRoomsOptimal** 및 **allrooms**의 스키마가 일치 합니다. 이렇게 하면 **RoomBrowseGallery**의 **Items** 속성에서 두 컬렉션을 모두 사용할 수 있습니다.
      1. **_roomListSelected** **false**로 설정 됩니다.
  1. 로드 상태 **_loadingRooms**은 (는) 다른 모든 항목의 실행이 완료 되 면 **false** 로 설정 됩니다.

## <a name="room-browse-gallery"></a>대화방 찾아보기 갤러리

   ![RoomBrowseGallery 컨트롤](media/meeting-screen/meeting-rooms-gall.png)

* 속성: **항목**<br>
    값: 사용자가 대화방 목록을 선택 했는지 또는 테 넌 트에 대화방 목록이 있는지에 따라 논리적으로 동일한 스키마의 두 내부 컬렉션으로 설정 됩니다.

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  **_RoomListSelected** 또는 **_noRoomLists** **True**이면이 갤러리는 **AvailableRoomsOptimal** 컬렉션을 표시 합니다. 그렇지 않으면 **RoomsLists** 컬렉션을 표시 합니다. 이러한 컬렉션의 스키마가 동일 하기 때문에이 작업을 수행할 수 있습니다.

* 속성: **표시**<br>
    값: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    갤러리는 앞의 세 문이 **true**로 평가 되는 경우에만 표시 됩니다.

### <a name="roombrowsegallery-title"></a>RoomBrowseGallery 제목

   ![RoomBrowseGallery Title 컨트롤](media/meeting-screen/meeting-rooms-gall-title.png)

* 속성: **Onselect**<br>
    값: 사용자가 대화방 목록이 나 대화방을 보고 있는지 여부에 따라 논리적으로 바인딩된 **Collect** 및 **set** 문 집합으로, 트리거될 수도 있고 그렇지 않을 수도 있습니다.

    ```powerapps-dot
    UpdateContext( { _loadingRooms: true } );
    If( !_roomListSelected && !noRoomLists,
        Set( _roomListSelected, true );
        Set( _selectedRoomList, ThisItem.Name );
        ClearCollect( AllRooms, 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability, 
                        Availability = "Free"
                    ),
                    "Address", Attendee.EmailAddress.Address 
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" )
            ), 
            "Attendee" )
        ),
        Set( _selectedRoom, ThisItem )
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  이 컨트롤이 선택 될 때 발생 하는 작업은 사용자가 현재 회의실 목록이 나 회의실 집합을 보고 있는지 여부에 따라 달라 집니다. 이 컨트롤을 선택 하면 선택 된 대화방 목록에서 선택한 시간에 사용할 수 있는 대화방을 검색 합니다. 후자 인 경우이 컨트롤을 선택 하면 **_selectedRoom** 변수가 선택 된 항목으로 설정 됩니다. 위의 문은 [**FindMeetingTimesGallery**](#find-meeting-times-gallery)의 **Select** 문과 매우 유사 합니다.

  낮은 수준에서 위의 코드 블록은 다음과 같습니다.
  1. **_LoadingRooms** 를 **true**로 설정 하 여 대화방의 로드 상태를 설정 합니다.
  1. 대화방 목록이 선택 되었는지와 테 넌 트에 방 목록이 있는지 확인 합니다. 그렇다면 다음과 같이 합니다.
      1. **_RoomListSelected** 를 **true** 로 설정 하 고 **_selectedRoomList** 을 선택 된 항목으로 설정 합니다.
      1. **_AllRoomsConcat** 변수는 **allrooms** 컬렉션에서 대화방의 처음 20 개 전자 메일 주소에 대 한 세미콜론으로 구분 된 문자열로 설정 됩니다. [Office365 FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 작업은 단일 작업에서 20 개의 person 개체에 대해 사용 가능한 시간을 검색 하는 것으로 제한 되기 때문입니다.
      1. **RoomTimeSuggestions** 컬렉션은 [FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) 작업을 사용 하 여 **_selectedMeetingTime** 변수의 시간 값을 기반으로 **allrooms** 컬렉션에서 처음 20 개 대화방의 전반를 검색 합니다. **DateTime** 값의 형식을 올바르게 지정 하는 데 `& "Z"`를 사용 합니다.
      1. **AvailableRooms** 컬렉션이 생성 됩니다. 이는 단순히 "Address" 및 "Name" 이라는 두 개의 추가 열이 추가 된 참석자 전반 **RoomTimeSuggestions** 컬렉션입니다. "Address"는 대화방의 메일 주소이 고 "Name"은 대화방의 이름입니다.
      1. 그런 다음 **AvailableRoomsOptimal** 컬렉션을 만듭니다. "가용성" 및 "참석자" 열을 제거 하는 **AvailableRooms** 컬렉션입니다. 이렇게 하면 **AvailableRoomsOptimal** 및 **allrooms**의 스키마가 일치 합니다. 이렇게 하면 **RoomBrowseGallery**의 **Items** 속성에서 두 컬렉션을 모두 사용할 수 있습니다.
      1. **_roomListSelected** **false**로 설정 됩니다.
  1. 로드 상태 **_loadingRooms**은 (는) 다른 모든 항목의 실행이 완료 되 면 **false** 로 설정 됩니다.

## <a name="back-chevron"></a>뒤로 펼침 단추

   ![RoomsBackNav 컨트롤](media/meeting-screen/meeting-back.png)

* 속성: **표시**<br>
    값: `_roomListSelected && _showDetails`

    이 컨트롤은 대화방 목록이 모두 선택 되어 있고 **일정** 탭이 선택 된 경우에만 표시 됩니다.

* 속성: **Onselect**<br>
    값: `Set( _roomListSelected, false )`

    **_RoomListSelected** 을 **false**로 설정 하면 **RoomsLists** Collection의 항목을 표시 하도록 **RoomBrowseGallery** 컨트롤을 변경 합니다.

## <a name="send-icon"></a>보내기 아이콘

   ![IconSendItem 컨트롤](media/meeting-screen/meeting-send-icon.png)

* 속성: **DisplayMode**<br>
    값: 사용자가 아이콘을 편집할 수 있게 되기 전에 특정 모임 세부 정보를 강제로 입력 하도록 하는 논리입니다.
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  이 아이콘은 모임 제목을 입력 한 경우 모임에 대 한 참석자가 하나 이상 있고 모임 시간이 선택 된 경우에만 선택할 수 있습니다. 그렇지 않으면 사용 하지 않도록 설정 됩니다.

* 속성: **Onselect**<br>

    값: 선택한 참석자에 게 모임 초대를 보내고 모든 입력 필드를 지웁니다.

    ```powerapps-dot
    Set( _myCalendarName, LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name );
    Set( _myScheduledMeeting, 
        'Office365'.V2CalendarPostItem( _myCalendarName,
            TextMeetingSubject1.Text, 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime), -TimeZoneOffset(), Minutes) ),
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime), -TimeZoneOffset(), Minutes) ),
            {
                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ) & _selectedRoom.Address, 
                Body: TextMeetingMessage1.Text, 
                Location: _selectedRoom.Name, 
                Importance: "Normal", 
                ShowAs: "Busy", 
                ResponseRequested: true
            }
        )
    );
    Concurrent(
        Reset( TextMeetingLocation1 ),
        Reset( TextMeetingSubject1 ),
        Reset( TextMeetingMessage1 ),
        Clear( MyPeople ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoomList, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false )
    )
    ```
  
  낮은 수준에서이 코드 블록은 다음과 같습니다.
  1. [Office365 ()](https://docs.microsoft.com/connectors/office365/#get-calendars) 작업에서 **DisplayName** 이 "calendar" 인 달력에 **_myCalendarName** 을 설정 합니다.
  1. [Office365 V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) 작업을 사용 하 여 사용자가 화면 전체에서 만든 다양 한 항목의 모든 입력 값을 사용 하 여 모임을 예약 합니다.
  1. 회의를 만드는 데 사용 되는 모든 입력 필드와 변수를 다시 설정 합니다.

> [!NOTE]
> 사용자의 지역에 따라 원하는 달력에 표시 이름 "Calendar"가 없을 수 있습니다. Outlook으로 이동 하 여 달력의 제목을 확인 하 고 앱에서 적절 하 게 변경 합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 자세한 정보](./meeting-screen-overview.md)
* [PowerApps의 Office 365 Outlook 커넥터에 대 한 자세한 정보](../connections/connection-office365-outlook.md)
* [PowerApps의 Office 365 사용자 커넥터에 대 한 자세한 정보](../connections/connection-office365-users.md)
