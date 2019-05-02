---
title: 캔버스 앱에 대한 전자 메일 화면 템플릿에 대한 참조 | Microsoft Docs
description: PowerApps의 캔버스 앱에 대한 전자 메일 화면 템플릿을 작동하는 방법의 세부 정보 이해
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8f77fe1194ace2f8cb5abeb3f9657cc76aab263a
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61538829"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>캔버스 앱의 전자 메일 화면 템플릿에 대한 참조 정보

PowerApps의 캔버스 앱에 대한 전자 메일 화면 템플릿의 각 중요한 컨트롤이 화면의 전체 기본 기능에 기여하는 방법을 이해합니다. 이 깊이 있는 정보는 컨트롤이 사용자 입력에 응답하는 방법을 결정하는 다른 속성의 값과 동작 수식을 표시합니다. 이 화면의 기본 기능의 간략한 설명은 [전자 메일 화면 개요](email-screen-overview.md)를 참조합니다.

이 항목에서는 몇 가지 중요한 컨트롤을 강조 표시하고 각 컨트롤의 다양한 속성(**Items**와 **OnSelect** 같은)에 설정하는 수식 또는 식을 설명합니다.

* [텍스트 검색 상자](#text-search-box)
* [추가 아이콘](#add-icon)
* [사람 찾아보기 갤러리](#people-browse-gallery)
* [전자 메일 사용자 갤러리](#email-people-gallery) (+ 자식 컨트롤)
* [메일 아이콘](#mail-icon)

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들어](../data-platform-create-app-scratch.md) 화면 및 기타 컨트롤을 추가하고 구성하는 방법에 친숙합니다.

## <a name="text-search-box"></a>텍스트 검색 상자

   ![TextSearchBox 컨트롤](media/email-screen/email-search-box.png)

**텍스트 검색 상자** 컨트롤은 화면의 다른 여러 컨트롤에 대해 종속성을 가집니다.

* 사용자가 텍스트를 입력하기 시작할 경우 **PeopleBrowseGallery**가 나타납니다.
* 유효한 전자 메일 주소를 입력하면 **AddIcon**이 나타납니다.
* 사용자가 **PeopleBrowseGallery**에서 사용자를 선택하는 경우, 검색 내용이 다시 설정됩니다.

## <a name="add-icon"></a>추가 아이콘

   ![AddIcon 컨트롤](media/email-screen/email-add-icon.png)

**추가 아이콘** 컨트롤을 사용하여 앱 사용자는 해당 조직 내에서 존재하지 않는 사람을 전자 메일 받는사람 목록에 추가할 수 있습니다.

* 속성: **Visible**<br>
    값: 검색 상자에 유효한 전자 메일 주소를 입력하는 경우에만 컨트롤을 표시하는 논리입니다.

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  한 줄씩, 앞에 나오는 코드 블록에 따르면 **추가 아이콘** 컨트롤은 다음 경우에 해당되면 표시됩니다.

    * **TextSearchBox**가 텍스트를 포함합니다.
    * **TextSearchBox**의 텍스트가 유효한 전자 메일 주소입니다.
    * **TextSearchBox**의 텍스트가 **MyPeople** 컬렉션에 존재하지 않습니다.

* 속성: **OnSelect**<br>
    값: 선택하면 올바른 전자 메일 주소를 **MyPeople** 컬렉션에 추가합니다. 이 컬렉션은 받는 사람 목록으로 화면에서 사용됩니다.

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
  
  이 코드 블록은 **TextSearchBox**에 있는 텍스트를 사용하여 세 개의 필드를 채우고 **MyPeople** 컬렉션에 행을 추가합니다. 이러한 세 가지 필드는 **DisplayName**, **UserPrincipalName** 및 **Mail**입니다. **TextSearchBox**의 내용을 다시 설정합니다.

## <a name="people-browse-gallery"></a>사람 찾아보기 갤러리

   ![PeopleBrowseGallery 컨트롤](media/email-screen/email-browse-gall.png)

* 속성: **Items**<br>
    값: **TextSearchBox** 컨트롤에 입력된 검색 텍스트의 상위 15개 검색 결과가 나타납니다.
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  이 갤러리의 항목은 [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업의 검색 결과로 채워집니다. 이 작업은 검색어를 `Trim(TextSearchBox)`하여 텍스트를 가져와서 검색에 따라 상위 15개 결과를 반환합니다.
  
  **TextSearchBox**는 사용자 검색에 빈 칸이 유효하지 않으므로 `Trim()` 함수로 래핑됩니다. `Office365Users.SearchUser` 작업은 검색 상자에 사용자가 입력한 텍스트를 포함하는 경우 수행하도록 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 함수에서 래핑됩니다. 이것은 성능을 향상시킵니다. 

### <a name="people-browse-gallery-title-control"></a>사람 찾아보기 갤러리 제목 컨트롤

   ![PeopleBrowseGallery 제목 컨트롤](media/email-screen/email-browse-gall-title.png)

* 속성: **Text**<br>
    값: `ThisItem.DisplayName`

  Office 365 프로필에서 사용자의 표시 이름을 표시합니다.

* 속성: **OnSelect**<br>
    값: 응용 프로그램 수준 컬렉션에 추가할 코드 및 사용자를 선택합니다.

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
이 컨트롤은 다음 세 가지를 동시에 수행합니다.

   * **_selectedUser** 변수를 선택한 항목으로 설정합니다.
   * **TextSearchBox**의 검색 용어를 다시 설정합니다.
   * 선택한 항목을 **MyPeople** 컬렉션에 추가합니다. **MyPeople** 컬렉션은 받는 사람 집합이며, 전자 메일 화면에서 사용하는 선택된 모든 사용자의 컬렉션입니다.

## <a name="email-people-gallery"></a>전자 메일 사용자 갤러리

   ![EmailPeopleGallery 컨트롤](media/email-screen/email-people-gall.png)

* 속성: **Items**<br>
    값: `MyPeople`

  **PeopleBrowseGallery Title** 컨트롤을 선택하여 추가된 또는 초기화된 사용자 컬렉션입니다.

* 속성: **Height**<br>
    값: 갤러리에서 현재 항목의 수에 따라, 높이를 설정합니다.

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  이 갤러리의 높이는 최대 304로 갤러리에서 항목의 수를 조정합니다.
  
  **EmailPeopleGallery** 단일 행의 총 높이로 `TemplateHeight + TemplatePadding * 2`에 행의 수를 곱합니다. `WrapCount = 2`로서 실제 행의 수는 `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`가 됩니다.

* 속성: **ShowScrollbar**<br>
    값: `EmailPeopleGallery.Height >= 304`
  
  갤러리의 높이가 304에 도달하면 스크롤 막대가 표시됩니다.

### <a name="email-people-gallery-title-control"></a>전자 메일 사용자 갤러리 제목 컨트롤

   ![EmailPeopleGallery 제목 컨트롤](media/email-screen/email-people-gall-text.png)

* 속성: **OnSelect**<br>
    값: `Set(_selectedUser, ThisItem)`

  **_selectedUser** 변수를 **EmailPeopleGallery**에서 선택된 항목으로 설정합니다.

### <a name="email-people-gallery-iconremove-control"></a>전자 메일 사용자 갤러리 iconRemove 컨트롤

   ![MonthDayGallery 제목 컨트롤](media/email-screen/email-people-gall-delete.png)

* 속성: **OnSelect**<br>
    값: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  선택된 항목의 **UserPrincipalName**과 일치하는 **UserPrincipalName**이 있는 **MyPeople** 컬렉션 레코드를 찾아 컬렉션에서 레코드를 삭제합니다.

## <a name="mail-icon"></a>메일 아이콘

* 속성: **OnSelect**<br>
    값: 사용자의 전자 메일 메시지를 보냅니다.

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

  전자 메일 주소들이 세미콜론으로 구분된 문자열은 전자 메일 메시지를 보낼 때 필요합니다. 위의 코드:
  1. 코드의 첫 번째 줄은 **MyPeople** 컬렉션에서 모든 행의 **Mail** 필드를 가져오고, 전자 메일 주소들을 세미콜론으로 구분된 단일 문자열로 연결하고 **\_emailRecipientString** 변수를 문자열로 설정합니다.

  1. 사용 하 여는 [Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) 받는 사람에 게 전자 메일을 보내는 작업을 합니다.
    작업에 세 개의 필수 매개 변수를 **하**, **주체**, 및 **본문**, 및 하나의 선택적 매개 변수-**중요도**합니다. 이들은 위의 코드에서 **_emailRecipientString**하십시오 **TextEmailSubject**합니다. 텍스트 **TextEmailMessage**합니다. 텍스트 및 **Normal**, 각각.
  1. 마지막으로 다시 설정 합니다 **TextEmailSubject** 및 **TextEmailMessage** 컨트롤과 지웁니다 합니다 **MyPeople** 컬렉션입니다.

* 속성: **DisplayMode**<br>
    값: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` 보낼 전자 메일에 대 한 텍스트 및 받는 사람 전자 메일 제목 줄 있어야 합니다 (**MyPeople**) 컬렉션은 비워둘 수 없습니다.

## <a name="next-steps"></a>다음 단계

* [이 화면 자세히 알아보기](./email-screen-overview.md)
* [PowerApps에서 Office 365 Outlook 커넥터 자세히 알아보기](../connections/connection-office365-outlook.md)
* [PowerApps에서 Office 365 사용자 커넥터 자세히 알아보기](../connections/connection-office365-users.md)
