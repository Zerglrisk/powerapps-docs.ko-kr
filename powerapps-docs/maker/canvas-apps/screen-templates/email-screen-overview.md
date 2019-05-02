---
title: 전자 메일 화면 템플릿 | Microsoft Docs
description: 캔버스 앱에 대한 전자 메일 화면 템플릿의 작동 방식을 이해하고 고유한 사용 사례에 대한 화면 확장
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1aad5ca9e8c7f8b55b1645b04d6c8dc0b9c707b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539236"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>캔버스 앱에 대한 전자 메일 화면 템플릿 개요

캔버스 앱에서 사용자가 Office 365 Outlook 계정에서 전자 메일을 보낼 수 있는 전자 메일 화면을 추가합니다. 사용자가 해당 조직에서 받는 사람을 검색하고 외부 전자 메일 주소를 추가합니다. 이미지-첨부 파일 지원을 추가하고, 검색 갤러리에 표시되는 사용자 데이터를 변경하고, 다른 사용자 지정을 만들 수 있습니다.

예: [달력](calendar-screen-overview.md), 조직의 [사람들](people-screen-overview.md)과 사용자 모임에 초대하려고 하는 사람들의 [가용성](meeting-screen-overview.md)과 같은 사용자의 Office 365에서 다른 데이터를 표시하는 다른 템플릿 기반 화면을 추가할 수도 있습니다.

개요에서 다음을 설명합니다.
> [!div class="checklist"]
> * 기본 전자 메일 화면을 사용하는 방법.
> * 수정 하는 방법.
> * 앱에 통합 하는 방법.

이 화면의 기본 기능에 대한 심층 분석에 대해서는 [전자 메일 화면 참조](email-screen-reference.md)를 확인합니다.

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들어](../data-platform-create-app-scratch.md) 화면 및 기타 컨트롤을 추가하고 구성하는 방법에 친숙합니다.

## <a name="default-functionality"></a>기본 기능

템플릿에서 전자 메일 화면을 추가:

1. PowerApps에 [로그인](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)한 다음 앱을 만들거나 기존 앱을 PowerApps Studio에서 엽니다.

    이 항목에서는 전화 앱을 보여주지만 태블릿 앱에 동일한 개념이 적용 됩니다.

1. 리본의 **홈** 탭에서 **새 화면** > **전자 메일**을 선택합니다.

    기본적으로 다음 화면과 비슷합니다.

    ![전자 메일 화면](media/email-screen/email-screen-full.png)

몇 가지 유용한 참고 사항:

* 조직에서 사용자를 검색하려면 "To" 아래에 있는 텍스트 입력 상자에 해당 이름을 입력합니다.
* 사용자를 검색할 때 상위 15 결과만 반환 됩니다.
* 조직 외부 전자 메일 받는 사람에게 전자 메일 주소를 추가하려면 전체 유효한 메일 주소를 입력하고 오른쪽에 표시되는 '+' 아이콘을 선택합니다.
* 전자 메일을 보내려면 1명 이상의 받는 사람을 추가하고 제목을 입력해야 합니다.
* 전자 메일을 보내면 받는 사람 목록 뿐만 아니라 제목 줄 및 메시지 본문의 내용은 모두 삭제 됩니다.

## <a name="modify-the-screen"></a>화면 수정

몇 가지 일반적인 방법으로 이 화면의 기본 기능을 수정할 수 있습니다.

* [이미지-첨부 파일 지원 추가](email-screen-overview.md#add-image-attachment-support)
* [사용자에 대한 다양한 데이터 표시](email-screen-overview.md#show-different-data-for-people)

화면을 추가로 수정하려는 경우 가이드로 [전자 메일 화면 참조](./email-screen-reference.md)를 사용합니다.

> [!IMPORTANT]
> 다음 단계는 앱에 하나의 전자 메일 화면을 추가한 것을 가정합니다. 둘 이상의 컨트롤을 추가한 경우 컨트롤 이름에 다른 숫자를 사용(예: **iconMail1**)하여 끝나게 되고 수식을 적절하게 조정해야 합니다.

### <a name="add-image-attachment-support"></a>이미지-첨부 파일 지원 추가

이 전자 메일을 사용하여 단일 이미지를 첨부 파일로 보낼 수가 있습니다.

1. **삽입** 탭에서 **미디어**를 선택한 후 **사진 추가**를 선택합니다.
1. 새 컨트롤의 **Y** 속성을 다음 식으로 설정합니다.

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. 삽입된 **AddMediaWithImage** 컨트롤의 높이는 210 보다 작게 설정합니다.
1. 컨트롤 트리 보기에서 **AddMediaWithImage** > **...** > **순서 바꾸기** > **맨 뒤로 보내기**를 선택합니다.
   컨트롤이 **PeopleBrowseGallery** 컨트롤의 앞에 위치하지 않도록 합니다.
1. **EmailPeopleGallery**의 **Height** 속성을 다음 수식으로 변경합니다.

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. **EmailPeopleGallery**의 **ShowScrollbar** 속성을 다음 식으로 설정합니다.

    ```EmailPeopleGallery1.Height >= 304```
    
    이것은 **AddMediaWithImage** 컨트롤을 페이지에서 밀어내지 않도록 최대 높이를 제한합니다.
    
1. **iconMail** 컨트롤의 **OnSelect** 속성을 다음 수식으로 변경합니다.

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    이 수식은 업로드된 이미지를 확인합니다. 없는 경우 전과 동일한 `Office365.SendEmail` 작업을 사용합니다. 이미지가 있다면 Attachments Table의 첨부 파일로 추가됩니다.
    전자 메일을 보낸 후 업로드된 이미지를 제거하기 위해 **AddMediaButton**에서 **Reset** 작업이 수행됩니다.
> [!NOTE]
> 전자 메일에 둘 이상의 첨부를 추가하려면 Attachments Table에 레코드를 추가합니다.

### <a name="show-different-data-for-people"></a>사용자에 대한 다양한 데이터 표시.

이 화면은 조직에서 사용자를 검색하기 위해 [Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업을 사용합니다. **PeopleBrowseGallery** 컨트롤에 나타나는 각 이벤트에 대한 추가 필드를 제공합니다. 갤러리에서 필드를 변경하거나 추가하는 것은 간단합니다.

1. **PeopleBrowseGallery** 컨트롤에서, 수정하려는(또는 추가한 후 선택) 레이블을 선택합니다.

1. **Text** 속성을 선택하고 수식 입력줄에서 `ThisItem.`으로 내용을 바꿉니다.

    IntelliSense는 선택할 수 있는 필드의 목록을 보여줍니다.

1. 원하는 필드를 선택 합니다.

    **Text** 속성을 `ThisItem.{FieldSelection}`으로 업데이트합니다.

## <a name="integrate-the-screen-into-an-app"></a>앱에 화면 통합

전자 메일 화면은 자체로 컨트롤의 강력한 번들이지만 일반적으로 가장 큰, 더 다양 한 응용 프로그램의 일부로 수행합니다. [일정 화면에 연결](email-screen-overview.md#linking-to-the-calendar-screen)을 포함하여 다양한 방법으로 더 큰 앱에 이 화면을 통합할 수 있습니다.

### <a name="linking-to-the-calendar-screen"></a>일정 화면에 연결

[일정 화면 개요](./calendar-screen-overview.md#show-event-attendees)의 "이벤트 참석자 표시" 섹션에 설명된 단계를 수행하고 마지막 단계에서 전자 메일 화면을 열도록 **Navigate** 함수를 설정합니다. 이러한 단계를 완료한 후, 사용자는 선택한 이벤트에 참석하는 사람들에게 전자 메일을 보낼 수 있는 **MyPeople** 컬렉션을 채웁니다.

> [!NOTE]
> 이 전자 메일 보내기는 Outlook에서 실제 이벤트에서 별도 전자 메일을 보냅니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대한 참조 설명서](./email-screen-reference.md)
* [PowerApps에서 Office 365 사용자 커넥터에 대해 자세히 알아보기](../connections/connection-office365-users.md)
* [PowerApps에서 사용 가능한 모든 연결 참조](../connections-list.md)