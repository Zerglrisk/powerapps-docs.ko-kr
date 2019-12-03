---
title: Office 365 Outlook 연결 개요 | Microsoft Docs
description: Power Apps에 대 한 Office 365 Outlook 연결에 대 한 예제를 포함 한 참조 정보
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/20/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1886514d036fe2b64ae82712128b14e19189fc73
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74728373"
---
# <a name="connect-to-office-365-outlook-from-power-apps"></a>Power Apps에서 Office 365 Outlook에 연결
![Office 365 Outlook](./media/connection-office365-outlook/office365icon.png)

Office 365 Outlook에 연결하면 다른 작업 외에도 이메일 메시지를 표시, 전송, 삭제 및 답장할 수 있습니다.

앱에서 이러한 함수를 수행하는 컨트롤을 추가할 수 있습니다. 예를 들어 **텍스트 입력** 컨트롤을 추가하여 이메일의 받는 사람, 제목, 본문을 입력하도록 요청하고 이메일을 보내는 **단추**를 추가할 수 있습니다.

이 토픽에서는 앱에 Office 365 Outlook을 연결로 추가하고, 데이터 원본으로 앱에 Office 365 Outlook을 추가하며, 이 데이터를 다양한 컨트롤에서 사용하는 방법을 설명합니다.

> [!IMPORTANT]
> 이 문서를 작성할 당시, 캘린더 작업은 반복 이벤트를 지원하지 않습니다.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-office-365-outlook"></a>Office 365 Outlook 연결
1. [데이터 연결을 추가](../add-data-connection.md)하고 **Office 365 Outlook**을 선택합니다.  
   
    ![Office 365에 연결](./media/connection-office365-outlook/add-office.png)
2. **연결**을 선택하고 로그인하라는 메시지가 표시되면 회사 계정을 입력합니다.

Office 365 Outlook 연결이 만들어지고 앱에 추가됩니다. 이제 사용할 수 있습니다.

## <a name="show-messages"></a>메시지 표시
1. **삽입** 메뉴에서 **갤러리**를 선택하고 **텍스트 갤러리** 컨트롤을 선택합니다.
2. **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    설정을 변경한 후 **레이아웃** **을 제목, 부제목, 본문**으로 변경 합니다.
    
    갤러리 컨트롤에 일부 이메일이 자동으로 채워집니다.
    
3. 갤러리에서 첫 번째 레이블의 **Text** 속성을 `ThisItem.From`로 설정합니다. 두 번째 레이블을 `ThisItem.Subject`로 설정합니다. 세 번째 레이블을 `ThisItem.BodyPreview`로 설정합니다. 레이블의 크기를 조정할 수도 있습니다.
   
    갤러리 컨트롤에 새 속성이 자동으로 채워집니다.
4. 이 함수에는 사용 가능한 몇 가지 선택적 매개 변수가 있습니다. 갤러리의 **Items** 속성을 다음 수식 중 하나로 설정합니다.
   
    `Office365.GetEmails({fetchOnlyUnread:false})`  
    `Office365.GetEmails({fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2})`  
    `Office365.GetEmails({folderPath:"Sent Items", fetchOnlyUnread:false, top:2, searchQuery:"powerapps"})`  
    `Office365.GetEmails({folderPath:"Deleted Items", fetchOnlyUnread:false, top:2, skip:3})`

## <a name="send-a-message"></a>메시지 보내기
1. **삽입** 메뉴에서 **텍스트**를 선택한 다음 **텍스트 입력**을 선택합니다.
2. 이전 단계를 두 번 더 반복하여 3개의 텍스트 입력을 만들고 한 열에 정렬합니다.  
   
    ![열의 세 상자](./media/connection-office365-outlook/threetextinput.png)
3. 컨트롤을 이름을 다음으로 바꿉니다.  
   
   * **inputTo**
   * **inputSubject**
   * **inputBody**
4. **삽입** 메뉴에서 **컨트롤**을 선택한 다음 **단추**를 선택합니다. **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   
    `Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text)`
5. 버튼을 움직여 모든 다른 컨트롤 아래 표시되게 하고 **[Text](../controls/properties-core.md)** 속성을 **"이메일 보내기"** 로 설정합니다.
6. F5 키를 누르거나 미리 보기 단추(![미리 보기 단추](./media/connection-office365-outlook/preview.png))를 선택합니다. **inputTo**에 올바른 이메일 주소를 입력한 다음 다른 두 **텍스트 입력** 컨트롤을 표시할 순서를 입력합니다.
7. **이메일 보내기**를 선택하여 메시지를 보냅니다. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

## <a name="send-a-message-with-an-attachment"></a>첨부 파일이 있는 메시지 보내기
예를 들어, 디바이스의 카메라를 사용하여 사진을 촬영한 다음 첨부 파일로 보내는 앱을 만들 수 있습니다. 사용자가 여러 종류의 파일을 이메일 앱에 첨부할 수도 있습니다.

메시지에 첨부 파일을 추가하려면 이전 섹션의 단계를 따르면서 첨부 파일을 지정하는 매개 변수를 추가합니다(단추의 **OnSelect** 속성을 설정할 때). 이 매개 변수는 각 첨부 파일에 대해 최대 3개의 속성을 지정하는 테이블 형태로 구성됩니다.

* 이름
* ContentBytes
* @odata.type

> [!NOTE]
> 한 첨부 파일에 @odata.type 속성만 지정하고 빈 문자열로 설정할 수 있습니다.

이 예제에서는 사진을 **file1.jpg**로 보냅니다.

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""})})`

이 예제에서는 사진과 함께 오디오 파일이 전송됩니다.

`Office365.SendEmail(inputTo.Text, inputSubject.Text, inputBody.Text, {Attachments:Table({Name:"file1.jpg", ContentBytes:Camera1.Photo, '@odata.type':""}, {Name:"AudioFile", ContentBytes:microphone1.audio })})`

## <a name="delete-a-message"></a>메시지 삭제
1. **삽입** 메뉴에서 **갤러리**를 선택하고 **텍스트 갤러리** 컨트롤을 선택합니다.
2. **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   
    `Office365.GetEmails({fetchOnlyUnread:false})`
   
    갤러리 컨트롤에 일부 이메일이 자동으로 채워집니다.
3. 갤러리에서 첫 번째 레이블의 **Text** 속성을 `ThisItem.Id`로 설정합니다. 두 번째 레이블을 `ThisItem.Subject`로 설정합니다. 세 번째 레이블을 `ThisItem.Body`로 설정합니다.
4. 갤러리에서 첫 번째 레이블을 선택하고 이름을 **EmailID**로 변경합니다.
   
    ![첫 번째 레이블 이름 변경](./media/connection-office365-outlook/renameheading.png)
5. 갤러리에서 세 번째 레이블을 선택 하고 **단추**를 추가합니다(**삽입** 메뉴). 단추의 **OnSelect** 속성을 다음 수식으로 설정합니다.  
   
    `Office365.DeleteEmail(EmailID.Text)`
6. F5 키를 누르거나 미리 보기 단추(![미리 보기 단추](./media/connection-office365-outlook/preview.png))를 선택합니다. 갤러리에서 이메일 중 하나를 선택하고 단추를 클릭합니다. 
    
    > [!NOTE]
    > 그러면 받은 편지함에서 선택한 이메일이 삭제됩니다. 그러니 신중하게 선택해야 합니다.
7. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

## <a name="mark-a-message-as-read"></a>메시지를 읽은 상태로 표시
이 섹션에서는 [메시지 삭제](connection-office365-outlook.md#delete-a-message)와 같은 컨트롤을 사용합니다.

1. 단추의 **OnSelect** 속성을 다음 수식으로 설정합니다.  
   
    `Office365.MarkAsRead(EmailID.Text)`
2. F5 키를 누르거나 미리 보기 단추(![미리 보기 단추](./media/connection-office365-outlook/preview.png))를 선택합니다. 읽지 않은 메일 중 하나를 선택하 고 단추를 클릭합니다.
3. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

## <a name="helpful-links"></a>유용한 링크
* 모든 함수 및 매개 변수 목록은 [Office 365 Outlook 참조](https://docs.microsoft.com/connectors/office365connector/)에서 확인하세요.
* [사용 가능한 연결](../connections-list.md)을 모두 보세요.  
* [연결 관리](../add-manage-connections.md) 방법을 알아보세요.

