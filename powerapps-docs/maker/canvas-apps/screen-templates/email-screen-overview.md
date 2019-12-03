---
title: 전자 메일-화면 템플릿 | Microsoft Docs
description: Canvas 앱에 대 한 전자 메일 화면 템플릿의 작동 원리를 이해 하 고 사용자의 사용 사례에 맞게 화면을 확장 합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 861d343e653a78af685a1e0cb82deb5b2ad59591
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732563"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>Canvas 앱에 대 한 전자 메일 화면 템플릿 개요

Canvas 앱에서 사용자가 Office 365 Outlook 계정에서 전자 메일을 보낼 수 있는 전자 메일 화면을 추가 합니다. 사용자는 자신의 조직에서 받는 사람을 검색 하 고 외부 전자 메일 주소도 추가할 수 있습니다. 이미지 첨부 파일 지원을 추가 하 고, 검색 갤러리에 표시 되는 사용자 데이터를 변경 하 고, 다른 사용자 지정을 수행할 수 있습니다.

사용자의 [일정](calendar-screen-overview.md), 조직의 [사용자](people-screen-overview.md) 및 모임에 초대 하려는 사용자의 [사용 가능 여부](meeting-screen-overview.md) 와 같이 Office 365에서 다른 데이터를 표시 하는 다른 템플릿 기반 화면을 추가할 수도 있습니다.

이 개요에서는 다음과 같은 방법을 배웁니다.
> [!div class="checklist"]
> * 기본 전자 메일 화면을 사용 하는 방법입니다.
> * 수정 하는 방법
> * 앱에 통합 하는 방법

이 화면의 기본 기능을 자세히 알아보려면 [전자 메일 화면 참조](email-screen-reference.md)를 참조 하세요.

## <a name="prerequisite"></a>필수 조건

[Power Apps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="default-functionality"></a>기본 기능

템플릿에서 전자 메일 화면을 추가 하려면 다음을 수행 합니다.

1. 파워 앱에 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음 앱을 만들거나 Power apps 스튜디오에서 기존 앱을 엽니다.

    이 항목은 휴대폰 앱을 표시 하지만 동일한 개념은 태블릿 앱에도 적용 됩니다.

1. 리본의 **홈** 탭에서 **새 화면** > **전자 메일**을 선택 합니다.

    기본적으로 화면은 다음과 같이 표시 됩니다.

    ![전자 메일 화면](media/email-screen/email-screen-full.png)

몇 가지 유용한 참고 사항:

* 조직에서 사용자를 검색 하려면 "To" 아래의 텍스트 입력 상자에 이름을 입력 합니다.
* 사용자를 검색 하는 경우 상위 15 개 결과만 반환 됩니다.
* 조직 외부의 전자 메일 받는 사람에 대 한 전자 메일 주소를 추가 하려면 전체 유효한 전자 메일 주소를 입력 하 고 오른쪽에 표시 되는 ' + ' 아이콘을 선택 합니다.
* 받는 사람을 한 명 이상 추가 하 고 전자 메일을 보낼 제목을 제공 해야 합니다.
* 전자 메일을 보낸 후에는 제목 줄과 메시지 본문의 내용 및 받는 사람 목록이 모두 지워집니다.

## <a name="modify-the-screen"></a>화면 수정

몇 가지 일반적인 방법으로이 화면의 기본 기능을 수정할 수 있습니다.

* [이미지 첨부 파일 지원 추가](email-screen-overview.md#add-image-attachment-support)
* [사용자에 대 한 다양 한 데이터 표시](email-screen-overview.md#show-different-data-for-people)

화면을 추가로 수정 하려면 [전자 메일 화면 참조](./email-screen-reference.md) 를 가이드로 사용 합니다.

> [!IMPORTANT]
> 다음 단계에서는 앱에 전자 메일 화면을 하나만 추가 했다고 가정 합니다. 하나 이상의를 추가한 경우 컨트롤 이름 (예: **iconMail1**)이 다른 숫자로 종료 되 고 그에 따라 수식을 조정 해야 합니다.

### <a name="add-image-attachment-support"></a>이미지 첨부 파일 지원 추가

이를 통해 사용자는 전자 메일을 첨부 파일로 사용 하 여 단일 이미지를 보낼 수 있습니다.

1. **삽입** 탭에서 **미디어**를 선택 하 고 **사진 추가**를 선택 합니다.
1. 새 컨트롤의 **Y** 속성을 다음 식으로 설정 합니다.

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. **Addmediawithimage** 컨트롤이 삽입 된 상태에서 높이를 210 미만으로 설정 합니다.
1. 컨트롤 트리 뷰에서 **Addmediawithimage** >  **...** 을 선택 하 > 다시 **정렬** > **다시 전송**합니다.
   이렇게 하면 컨트롤이 **PeopleBrowseGallery** 컨트롤 앞에 앉아 있지 않습니다.
1. **EmailPeopleGallery** 의 **Height** 속성을 다음 수식으로 변경 합니다.

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. **EmailPeopleGallery** 의 **showscrollbar** 속성을 다음 식으로 설정 합니다.

    ```EmailPeopleGallery1.Height >= 304```
    
    그러면 최대 높이가 페이지에서 **Addmediawithimage** 컨트롤을 푸시하는 것을 방지 합니다.
    
1. **Iconmail** 컨트롤의 **onselect** 속성을 다음 수식으로 변경 합니다.

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
    
    이 수식은 업로드 된 이미지를 확인 합니다. 없는 경우 이전과 동일한 `Office365.SendEmail` 작업을 사용 합니다. 이미지가 있으면 첨부 파일 테이블에 첨부 파일로 추가 됩니다.
    전자 메일을 보낸 후 추가 **다시 설정** 작업은 **Addmediabutton** 에 대해 수행 되어 업로드 된 이미지를 제거 합니다.
> [!NOTE]
> 전자 메일에 첨부 파일을 여러 개 추가 하려면 첨부 파일 테이블에 레코드를 추가 합니다.

### <a name="show-different-data-for-people"></a>사용자에 대 한 다양 한 데이터 표시

이 화면에서는 [Office365Users 사용자](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업을 사용 하 여 조직에서 사용자를 검색 합니다. **PeopleBrowseGallery** 컨트롤에 표시 되는 것 외에 각 이벤트에 대 한 추가 필드를 제공 합니다. 갤러리에서 필드를 추가 하거나 변경 하는 작업은 간단 합니다.

1. **PeopleBrowseGallery** 컨트롤에서 수정할 레이블을 선택 하거나 하나 추가 하 고 선택 된 상태로 유지 합니다.

1. **텍스트** 속성을 선택 하 고 수식 입력줄에서 내용을 `ThisItem.` 바꿉니다.

    IntelliSense는 선택할 수 있는 필드 목록을 표시 합니다.

1. 원하는 필드를 선택 합니다.

    **텍스트** 속성은 `ThisItem.{FieldSelection}`로 업데이트 됩니다.

## <a name="integrate-the-screen-into-an-app"></a>앱에 화면 통합

전자 메일 화면은 자체의 강력한 컨트롤 번들 이지만 일반적으로 더 크고 광범위 한 앱의 일부로 가장 효과적으로 수행 됩니다. [일정 화면에 연결](email-screen-overview.md#linking-to-the-calendar-screen)하는 등 여러 가지 방법으로이 화면을 더 큰 앱에 통합할 수 있습니다.

### <a name="linking-to-the-calendar-screen"></a>달력 화면에 연결

[일정 화면 개요](./calendar-screen-overview.md#show-event-attendees) 의 "이벤트 참석자 표시" 섹션에 설명 된 단계를 수행 하지만 마지막 단계에서 **Navigate** 함수를 설정 하 여 전자 메일 화면을 엽니다. 이러한 단계를 완료 한 후에는 사용자가 선택한 이벤트에 참석 하는 사람에 게 전자 메일을 보낼 수 있도록 하는 **MyPeople** 컬렉션이 채워집니다.

> [!NOTE]
> 이 전자 메일을 보내면 Outlook의 실제 이벤트에서 별도의 메일을 보냅니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 참조 설명서를 봅니다](./email-screen-reference.md).
* [Power Apps의 Office 365 사용자 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-users.md).
* [Power Apps에서 사용 가능한 모든 연결을 참조](../connections-list.md)하세요.