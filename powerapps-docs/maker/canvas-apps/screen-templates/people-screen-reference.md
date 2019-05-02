---
title: 사용자 화면 템플릿 참조 | Microsoft Docs
description: PowerApps의 캔버스 앱에 대한 사용자 화면 템플릿을 작동하는 방법의 세부 정보 이해
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b92a1e2bc87ac6f4e2ec651aa67a845e0f07b1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540784"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>캔버스 앱의 사용자 화면 템플릿에 대한 참조 정보

PowerApps의 캔버스 앱의 사용자 화면 템플릿에 중요한 각 컨트롤 화면이 전체 기본 기능에 기여하는 방법을 이해합니다. 이 깊이 있는 정보는 컨트롤이 사용자 입력에 응답하는 방법을 결정하는 다른 속성의 값 및 동작 수식을 표시합니다. 이 화면의 기본 기능의 간략한 설명에 대해서는 [사용자 화면 개요](people-screen-overview.md)를 참조합니다.

이 항목에서는 몇 가지 중요한 컨트롤을 강조 표시하고 각 컨트롤의 다양한 속성(**Items**와 **OnSelect** 등)에 설정하는 수식 또는 식을 설명합니다.

* [텍스트 검색 상자](#text-search-box)
* [사용자 찾아보기 갤러리](#user-browse-gallery) (+ 자식 컨트롤)
* [사용자 추가 갤러리](#people-added-gallery) (+ 자식 컨트롤)

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들어](../data-platform-create-app-scratch.md) 화면 및 기타 컨트롤을 추가하고 구성하는 방법에 친숙합니다.

## <a name="text-search-box"></a>텍스트 검색 상자

![TextSearchBox 컨트롤](media/people-screen/people-search-box.png)

텍스트 검색 상자 컨트롤은 화면의 다른 여러 컨트롤에 대해 다음과 같은 종속성을 가집니다.

* 사용자가 텍스트를 입력하기 시작하면 **UserBrowseGallery**가 표시됩니다.
* 사용자가 **UserBrowseGallery**에서 사용자를 선택하는 경우, 검색 내용이 다시 설정됩니다.

## <a name="user-browse-gallery"></a>사용자 찾아보기 갤러리

![UserBrowseGallery 컨트롤](media/people-screen/people-browse-gall.png)

* 속성: **Items**<br>
    값: 사용자가 입력을 시작하는 경우 사용자를 조회합니다.
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
이 갤러리의 항목이 [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업에 따라 검색 결과에 나타납니다. 이 작업은 검색어를 `Trim(TextSearchBox)`하여 가져오고 상위 15개의 검색 결과를 반환합니다. 사용자 검색에서 빈 칸은 유효하지 않기 떄문에 **TextSearchBox**는 `Trim()` 함수로 래핑됩니다.

`Office365Users.SearchUser` 작업은 검색 상자가 사용자 입력한 텍스트를 포함하는 경우에만 작업을 호출할 필요가 있기 때문에`If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 함수로 래핑됩니다. 이것은 성능을 향상시킵니다.

### <a name="userbrowsegallery-title-control"></a>사용자 찾아보기 갤러리 제목 컨트롤

![사용자 찾아보기 갤러리 제목 컨트롤](media/people-screen/people-browse-gall-title.png)

* 속성: **Text**<br>값: `ThisItem.DisplayName`

  Office 365 프로필에서 사용자의 표시 이름을 표시합니다.

* 속성: **OnSelect**<br>
    값: text응용 프로그램 수준 컬렉션에 사용자를 추가한 다음 사용자를 선택합니다.

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
이 컨트롤을 선택하면 다음 세 가지가 동시에 수행됩니다.

   * **\_selectedUser** 변수를 선택한 항목으로 설정합니다.
   * **TextSearchBox**에 검색어를 다시 설정합니다.
   * 앱 사용자가 선택한 모든 사용자의 컬렉션인 **MyPeople** 컬렉션에 선택된 항목을 추가합니다.

### <a name="userbrowsegallery-profileimage-control"></a>사용자 찾아보기 갤러리 프로필 이미지 컨트롤

![사용자 찾아보기 갤러리 프로필 이미지 컨트롤](media/people-screen/people-browse-gall-image.png)

* 속성: **Image**<br>
    값: 사용자의 프로필 사진을 검색합니다.

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**Image** 컨트롤은 [Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) 작업으로 사용자의 이미지를 검색합니다. 그러나 그렇게 하기 전에 다음 두 가지를 확인합니다.
  
   * ID 필드가 비있는지 또는 비어 있지 않은지 확인합니다. 이것은 **Image** 컨트롤이 갤러리가 검색 결과로 채워지기 전에 사용자 사진을 검색하는 것을 방지합니다.
   * 사용자의 사진이 있는지 여부를 확인합니다([Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) 작업 사용). 이것은 사용자의 프로필 사진이 없는 경우`Office365Users.UserPhoto` 조회에서 예외를 반환하는 것을 방지합니다.

이미지가 검색되지 않는 경우, **Image** 컨트롤은 비게 되고 대신 **iconUser** 컨트롤이 표시됩니다.

## <a name="people-added-gallery"></a>사용자 추가 갤러리

![PeopleAddedGallery 컨트롤](media/people-screen/people-people-gall.png)

* 속성: **Items**<br>
    값: `MyPeople`

**UserBrowseGallery Title** 컨트롤을 선택하여 사용자 컬렉션을 초기화하거나 추가합니다.

### <a name="peopleaddedgallery-title-control"></a>사용자 추가 갤러리 제목 컨트롤

![사용자 추가 갤러리 제목 컨트롤](media/people-screen/people-people-gall-title.png)

* 속성: **OnSelect**<br>
    값: `Set( _selectedUser, ThisItem )`

**_selectedUser** 변수를 **EmailPeopleGallery**에서 선택된 항목으로 설정합니다.

### <a name="peopleaddedgallery-iconremove-control"></a>사용자 추가 갤러리 제거 아이콘 컨트롤

![사용자 추가 갤러리 제거 아이콘 컨트롤](media/people-screen/people-people-gall-delete.png)

* 속성: **OnSelect**<br>
    값: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

**MyPeople** 컬렉션에서 **UserPrincipalName**이 선택한 항목의 **UserPrincipalName**과 일치하는 레코드를 조회한 다음 컬렉션에서 해당 레코드를 제거합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면 자세히 알아보기](./people-screen-overview.md)
* [Office 365 Outlook 커넥터에 대해 자세히 알아보기](../connections/connection-office365-outlook.md)
* [Office 365 사용자 커넥터에 대해 자세히 알아보기](../connections/connection-office365-users.md)
