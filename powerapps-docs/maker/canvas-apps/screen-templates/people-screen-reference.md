---
title: 사용자-화면 템플릿 참조 | Microsoft Docs
description: PowerApps에서 캔버스 앱의 사용자 화면 템플릿이 작동 하는 방법에 대 한 세부 정보 이해
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ab4b7683d4ea550ebe5704cb7e5580ccbae48deb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674972"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>캔버스 앱의 사용자 화면 템플릿에 대 한 참조 정보

Power Apps의 캔버스 앱의 경우 사용자 화면 템플릿의 각 주요 컨트롤이 화면의 전반적인 기본 기능에 어떻게 기여 하는지 이해 합니다. 이 심층 정보는 동작 수식과 컨트롤에서 사용자 입력에 응답 하는 방법을 결정 하는 기타 속성의 값을 제공 합니다. 이 화면의 기본 기능에 대 한 개략적인 설명은 [사용자 화면 개요](people-screen-overview.md)를 참조 하세요.

이 항목에서는 몇 가지 중요 한 컨트롤을 강조 하 고 이러한 컨트롤의 다양 한 속성 (예: **항목** 및 **onselect**)이 설정 되는 식이나 수식을 설명 합니다.

* [텍스트 검색 상자](#text-search-box)
* [사용자-찾아보기 갤러리](#user-browse-gallery) (+ 자식 컨트롤)
* [추가 된 갤러리](#people-added-gallery) (+ 자식 컨트롤)

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="text-search-box"></a>텍스트 검색 상자

![TextSearchBox 컨트롤](media/people-screen/people-search-box.png)

다른 두 컨트롤이 상호 작용 하거나 텍스트 검색 상자에 대 한 종속성이 있습니다.

* 사용자가 텍스트 입력을 시작 하면 **UserBrowseGallery** 가 표시 됩니다.
* 사용자가 **UserBrowseGallery**내에서 사용자를 선택 하면 검색 내용이 다시 설정 됩니다.

## <a name="user-browse-gallery"></a>사용자-갤러리 찾아보기

![UserBrowseGallery 컨트롤](media/people-screen/people-browse-gall.png)

* 속성: **항목**<br>
    값: 사용자가 입력을 시작할 때 사용자를 조회 하는 논리:
    
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
    
이 갤러리의 항목은 [Office365 사용자](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업에서 검색 결과로 채워집니다. 작업은 `Trim(TextSearchBox)`의 텍스트를 검색 용어로 사용 하 고 해당 검색을 기준으로 상위 15 개 결과를 반환 합니다. 공백에 대 한 사용자 검색이 잘못 되었으므로 **Textsearchbox** 가 `Trim()` 함수에 래핑됩니다.

`Office365Users.SearchUser` 작업은 검색 상자에 사용자가 입력 한 텍스트가 포함 된 경우에만 작업을 호출 하면 되므로 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 함수에서 래핑됩니다. 이렇게 하면 성능이 향상 됩니다.

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery Title 컨트롤

![UserBrowseGallery Title 컨트롤](media/people-screen/people-browse-gall-title.png)

* 속성: **텍스트**<br>값: `ThisItem.DisplayName`

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

   * **\_selectedUser** 변수를 선택한 항목으로 설정 합니다.
   * **Textsearchbox**에서 검색 단어를 다시 설정 합니다.
   * 앱 사용자가 선택한 모든 사람의 컬렉션인 **MyPeople** 컬렉션에 선택한 항목을 추가 합니다.

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery ProfileImage 컨트롤

![UserBrowseGallery ProfileImage 컨트롤](media/people-screen/people-browse-gall-image.png)

* 속성: **이미지**<br>
    Value: 사용자의 프로필 사진을 검색 하는 논리입니다.

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**이미지** 컨트롤은 [Office365Users](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) 작업을 사용 하 여 사용자의 이미지를 검색 합니다. 그러나이 작업을 수행 하기 전에 다음 두 가지를 확인 합니다.
  
   * ID 필드가 비어 있거나 비어 있지 않은지 여부입니다. 이렇게 하면 갤러리에 검색 결과가 채워지기 전에 **이미지** 컨트롤이 사용자 사진을 검색 하지 못합니다.
   * 사용자에 게 사진이 있는지 여부를 나타냅니다 ( [Office365Users 메타 데이터](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) 작업을 사용 하는 경우). 이렇게 하면 사용자에 게 프로필 그림이 없는 경우 `Office365Users.UserPhoto` 조회가 예외를 반환 하지 않습니다.

이미지를 검색 하지 않으면 **이미지** 컨트롤이 비어 있고 **iconuser** 컨트롤이 대신 표시 됩니다.

## <a name="people-added-gallery"></a>사용자-추가 된 갤러리

![PeopleAddedGallery 컨트롤](media/people-screen/people-people-gall.png)

* 속성: **항목**<br>
    값: `MyPeople`

**UserBrowseGallery Title** 컨트롤을 선택 하 여에 초기화 되거나 추가 되는 사용자의 컬렉션입니다.

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery Title 컨트롤

![PeopleAddedGallery Title 컨트롤](media/people-screen/people-people-gall-title.png)

* 속성: **Onselect**<br>
    값: `Set( _selectedUser, ThisItem )`

**_SelectedUser** 변수를 **EmailPeopleGallery**에서 선택한 항목으로 설정 합니다.

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove 컨트롤

![PeopleAddedGallery iconRemove 컨트롤](media/people-screen/people-people-gall-delete.png)

* 속성: **Onselect**<br>
    값: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

**MyPeople** collection에서 레코드를 조회 합니다. 여기서 **UserPrincipalName** 는 선택한 항목의 **UserPrincipalName** 와 일치 하 고 컬렉션에서 해당 레코드를 제거 합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대해 자세히 알아보세요](./people-screen-overview.md).
* [Office 365 Outlook 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-outlook.md).
* [Office 365 사용자 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-users.md).
