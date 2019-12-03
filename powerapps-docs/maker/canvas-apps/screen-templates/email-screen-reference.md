---
title: Canvas 앱에 대 한 전자 메일 화면 템플릿에 대 한 참조 | Microsoft Docs
description: Power Apps에서 캔버스 앱에 대 한 전자 메일 화면 템플릿이 작동 하는 방법에 대 한 세부 정보 이해
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
ms.openlocfilehash: f173b4898df8853ef31d1660af6efe9298f838b0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732615"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Canvas 앱에 대 한 전자 메일 화면 템플릿에 대 한 참조 정보

Power Apps의 캔버스 앱의 경우 전자 메일 화면 템플릿의 각 주요 컨트롤이 화면의 전반적인 기본 기능에 어떻게 기여 하는지 이해 합니다. 이 심층 정보는 컨트롤에서 사용자 입력에 응답 하는 방법을 결정 하는 동작 수식과 기타 속성의 값을 보여 줍니다. 이 화면의 기본 기능에 대 한 개략적인 논의는 [전자 메일 화면 개요](email-screen-overview.md)를 참조 하세요.

이 항목에서는 몇 가지 중요 한 컨트롤을 강조 하 고 이러한 컨트롤의 다양 한 속성 (예: **항목** 및 **onselect**)이 설정 되는 식이나 수식을 설명 합니다.

* [텍스트 검색 상자](#text-search-box)
* [추가 아이콘](#add-icon)
* [사용자 찾아보기 갤러리](#people-browse-gallery)
* [전자 메일 사용자 갤러리](#email-people-gallery) (+ 자식 컨트롤)
* [메일 아이콘](#mail-icon)

## <a name="prerequisite"></a>필수 조건

[Power Apps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="text-search-box"></a>텍스트 검색 상자

   ![TextSearchBox 컨트롤](media/email-screen/email-search-box.png)

화면의 여러 다른 컨트롤은 **텍스트 검색 상자** 컨트롤에 종속 되어 있습니다.

* 사용자가 텍스트 입력을 시작 하면 **PeopleBrowseGallery** 가 나타납니다.
* 사용자가 유효한 전자 메일 주소를 입력 하면 **Addicon** 이 표시 됩니다.
* 사용자가 **PeopleBrowseGallery**내에서 사용자를 선택 하면 검색 내용이 다시 설정 됩니다.

## <a name="add-icon"></a>추가 아이콘

   ![AddIcon 컨트롤](media/email-screen/email-add-icon.png)

앱 사용자는 **추가 아이콘** 컨트롤을 사용 하 여 조직 내에 없는 사용자를 구성 된 전자 메일의 받는 사람 목록에 추가할 수 있습니다.

* 속성: **표시**<br>
    값: 사용자가 검색 상자에 유효한 전자 메일 주소를 입력 하는 경우에만 컨트롤을 표시 하는 논리입니다.

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  위의 코드 블록에서는 다음 경우에만 **추가 아이콘** 컨트롤이 표시 됨을 기준으로 한 줄로 표시 됩니다.

    * **Textsearchbox** 에 텍스트가 있습니다.
    * **Textsearchbox** 의 텍스트는 유효한 전자 메일 주소입니다.
    * **Textsearchbox** 의 텍스트는 **MyPeople** 컬렉션에 이미 존재 하지 않습니다.

* 속성: **Onselect**<br>
    값:이를 선택 하면 유효한 전자 메일 주소가 **MyPeople** 컬렉션에 추가 됩니다. 이 컬렉션은 화면에서 받는 사람 목록으로 사용 됩니다.

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  이 코드 블록은 **MyPeople** 컬렉션에 행을 추가 하 고 **textsearchbox**의 텍스트를 사용 하 여 3 개의 필드를 채웁니다. 이러한 세 필드는 **DisplayName**, **UserPrincipalName**및 **Mail**입니다. 그런 다음 **Textsearchbox**의 내용을 다시 설정 합니다.

## <a name="people-browse-gallery"></a>사용자 찾아보기 갤러리

   ![PeopleBrowseGallery 컨트롤](media/email-screen/email-browse-gall.png)

* 속성: **항목**<br>
    값: **Textsearchbox** 컨트롤에 입력 된 검색 텍스트의 상위 15 개 검색 결과:
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  이 갤러리의 항목은 [Office365 사용자](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업에서 검색 결과로 채워집니다. 작업은 `Trim(TextSearchBox)`의 텍스트를 검색 용어로 사용 하 고 해당 검색을 기준으로 상위 15 개 결과를 반환 합니다.
  
  공백에 대 한 사용자 검색이 잘못 되었으므로 **Textsearchbox** 가 `Trim()` 함수에 래핑됩니다. `Office365Users.SearchUser` 작업은 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 함수에서 래핑됩니다. 즉, 검색 상자에 사용자가 입력 한 텍스트가 포함 된 경우에만 작업이 수행 됩니다. 이렇게 하면 성능이 향상 됩니다. 

### <a name="people-browse-gallery-title-control"></a>사용자 찾아보기 갤러리 제목 컨트롤

   ![PeopleBrowseGallery Title 컨트롤](media/email-screen/email-browse-gall-title.png)

* 속성: **텍스트**<br>
    값: `ThisItem.DisplayName`

  Office 365 프로필의 사용자 표시 이름을 표시 합니다.

* 속성: **Onselect**<br>
    값: 앱 수준 컬렉션에 사용자를 추가 하는 코드를 만든 다음 사용자를 선택 합니다.

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
이 컨트롤을 선택 하면 세 가지 작업을 동시에 수행 합니다.

   * **_SelectedUser** 변수를 선택한 항목으로 설정 합니다.
   * **Textsearchbox**에서 검색 단어를 다시 설정 합니다.
   * **MyPeople** 컬렉션에 선택한 항목을 추가 합니다 .이 컬렉션에는 전자 메일 화면에서 받는 사람 집합으로 사용 하는 선택한 모든 사용자의 컬렉션이 추가 됩니다.

## <a name="email-people-gallery"></a>전자 메일 사용자 갤러리

   ![EmailPeopleGallery 컨트롤](media/email-screen/email-people-gall.png)

* 속성: **항목**<br>
    값: `MyPeople`

  **PeopleBrowseGallery Title** 컨트롤을 선택 하 여에 초기화 되거나 추가 되는 사용자의 컬렉션입니다.

* 속성: **Height**<br>
    값: 현재 갤러리에 있는 항목 수에 따라 높이를 설정 하는 논리입니다.

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  이 갤러리의 높이는 갤러리의 항목 수로 조정 되며 최대 높이는 304입니다.
  
  **EmailPeopleGallery**의 단일 행에 대 한 총 높이로 `TemplateHeight + TemplatePadding * 2`를 사용 하 고 행 수를 곱합니다. `WrapCount = 2`있으므로 true 행의 수는 `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`됩니다.

* 속성: **Showscrollbar**<br>
    값: `EmailPeopleGallery.Height >= 304`
  
  갤러리의 높이가 304에 도달 하면 스크롤 막대가 표시 됩니다.

### <a name="email-people-gallery-title-control"></a>전자 메일 사용자 갤러리 제목 컨트롤

   ![EmailPeopleGallery Title 컨트롤](media/email-screen/email-people-gall-text.png)

* 속성: **Onselect**<br>
    값: `Set(_selectedUser, ThisItem)`

  **_SelectedUser** 변수를 **EmailPeopleGallery**에서 선택한 항목으로 설정 합니다.

### <a name="email-people-gallery-iconremove-control"></a>전자 메일 사용자 갤러리 아이콘 제거 컨트롤

   ![MonthDayGallery 제목 컨트롤](media/email-screen/email-people-gall-delete.png)

* 속성: **Onselect**<br>
    값: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  **MyPeople** collection에서 레코드를 조회 합니다. 여기서 **UserPrincipalName** 는 선택한 항목의 **UserPrincipalName** 와 일치 하 고 컬렉션에서 해당 레코드를 제거 합니다.

## <a name="mail-icon"></a>메일 아이콘

* 속성: **Onselect**<br>
    값: 사용자의 전자 메일 메시지를 보내는 논리:

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  전자 메일 메시지를 보내려면 세미콜론으로 구분 된 전자 메일 주소 문자열이 필요 합니다. 위의 코드에서 다음을 수행 합니다.
  1. 첫 번째 코드 줄은 **MyPeople** 컬렉션에 있는 모든 행의 **메일** 필드를 가져와 세미콜론으로 구분 된 단일 문자열의 전자 메일 주소로 연결 하 고 **_emailRecipientString** 변수를 해당 문자열 값으로 설정 합니다.

  1. 그런 다음 [Office365. SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) 작업을 사용 하 여 받는 사람에 게 전자 메일을 보냅니다.
    작업에는 세 가지 필수 매개 변수인 **To**, **Subject**및 **Body**와 하나의 선택적 매개 변수--**중요도**가 있습니다. 위의 코드에서는 **_emailRecipientString** **TextEmailSubject**입니다. 텍스트, **TextEmailMessage** Text 및 **Normal**의 각각에 해당 합니다.
  1. 마지막으로 **TextEmailSubject** 및 **TextEmailMessage** 컨트롤을 다시 설정 하 고 **MyPeople** 컬렉션을 지웁니다.

* 속성: **DisplayMode**<br>
    값: 보낼 전자 메일에 대 한 `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` 전자 메일 제목 줄에 텍스트가 있어야 하 고 받는 사람 (**MyPeople**) 컬렉션이 비어 있지 않아야 합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 자세한 정보](./email-screen-overview.md)
* [Power Apps에서 Office 365 Outlook 커넥터에 대 한 자세한 정보](../connections/connection-office365-outlook.md)
* [Power Apps의 Office 365 사용자 커넥터에 대 한 자세한 정보](../connections/connection-office365-users.md)
