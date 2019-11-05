---
title: 사용자-화면 템플릿 | Microsoft Docs
description: 캔버스 앱의 사용자 화면 템플릿 작동 방식 및 사용자 고유의 사용 사례에 맞게 화면을 확장 하는 방법 이해
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4c688232e275cee1e285b22dd4885ea2126e7ad
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541396"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>캔버스 앱의 사용자 화면 템플릿 개요

Canvas 앱에서 사용자가 조직 내에서 사용자를 검색할 수 있는 사람 화면을 추가 합니다. 사용자는 컬렉션을 검색 하 고, 선택 하 고, 사용자를 추가할 수 있습니다. 검색 결과 갤러리에 표시 되는 데이터 형식을 변경 하 고, 사용자 선택 항목을 사용 하 여 전자 메일을 보내고, 다른 사용자 지정을 수행할 수 있습니다.

[전자 메일](email-screen-overview.md), 사용자의 [일정](calendar-screen-overview.md), 사용자의 모임 초대를 받을 수 있는 사용자의 [사용 가능 여부](meeting-screen-overview.md) 와 같은 Office 365의 다른 데이터를 표시 하는 다른 템플릿 기반 화면을 추가할 수도 있습니다.

이 개요에서는 다음과 같은 방법을 배웁니다.
> [!div class="checklist"]
> * 기본 사용자 화면을 사용 하는 방법
> * 화면을 수정 하는 방법
> * 앱에 화면을 통합 하는 방법입니다.

이 화면의 기본 기능을 자세히 알아보려면 [사용자 화면 참조](people-screen-reference.md)를 참조 하세요.

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="default-functionality"></a>기본 기능

템플릿에서 사용자 화면을 추가 하려면 다음을 수행 합니다.

1. PowerApps에 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음 앱을 만들거나 PowerApps Studio에서 기존 앱을 엽니다.

    이 항목은 휴대폰 앱을 표시 하지만 동일한 개념은 태블릿 앱에도 적용 됩니다.

1. 리본의 **홈** 탭에서 **새 화면** > **사용자**를 선택 합니다.

    기본적으로 화면은 다음과 같이 표시 됩니다.

    ![초기 사용자 화면 상태](media/people-screen/people-screen-empty.png)

1. 사용자 검색을 시작 하려면 위쪽에서 텍스트 입력 상자를 선택 하 고 동료 이름을 입력 하기 시작 합니다. 텍스트 입력 상자 아래에 검색 결과가 표시 됩니다.

    ![사용자 화면 검색 상태](media/people-screen/people-browse-gall-full.png)

1. 검색 결과에서 개인을 선택 하면 **MyPeople** 컬렉션에 추가 됩니다. 검색 창 입력 값이 다시 설정 되어 사용자가 선택한 사용자의 컬렉션을 표시 합니다.

    ![사용자 화면 컬렉션 결과](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>화면 수정

[사용자에 대 한 다양 한 데이터를 표시](people-screen-overview.md#show-different-data-for-people)하 여이 화면의 기본 기능을 수정할 수 있습니다.

화면을 추가로 수정 하려면 [사용자 화면 참조](./people-screen-reference.md) 를 가이드로 사용 합니다.

### <a name="show-different-data-for-people"></a>사용자에 대 한 다양 한 데이터 표시

이 화면에서는 [Office365Users 사용자](https://docs.microsoft.com/connectors/office365users/#searchuser) 작업을 사용 하 여 조직에서 사용자를 검색 합니다. **UserBrowseGallery** 컨트롤에 표시 되는 것 외에 각 이벤트에 대 한 추가 필드를 제공 합니다. 갤러리에서 필드를 추가 하거나 변경 하는 작업은 간단한 프로세스입니다.

1. **UserBrowseGallery**에서 수정할 레이블을 선택 하거나 하나 추가 하 고 선택 된 상태로 유지 합니다.

1. **텍스트** 속성을 선택 하 고 수식 입력줄에서 내용을 `ThisItem.` 바꿉니다.

    IntelliSense는 선택할 수 있는 필드 목록을 표시 합니다.

1. 원하는 필드를 선택 합니다.

    **텍스트** 속성을 `ThisItem.{FieldSelection}`로 업데이트 해야 합니다.

## <a name="integrate-the-screen-into-an-app"></a>앱에 화면 통합

사용자 화면은 자신의 오른쪽에 있는 강력한 컨트롤 번들 이지만 일반적으로 더 크고 더 다양 한 앱의 일부로 가장 효과적으로 수행 됩니다. [캐시 된 사용자 목록을 사용](people-screen-overview.md#use-your-cached-list-of-people)하는 등 여러 가지 방법으로이 화면을 더 큰 앱에 통합할 수 있습니다.

### <a name="use-your-cached-list-of-people"></a>캐시 된 사용자 목록 사용

사용자 화면은 **MyPeople** collection에서 사용자가 선택한 항목을 캐시 합니다. 비즈니스 시나리오에서 사용자 조회를 호출 해야 하는 경우이 컬렉션을 사용 하는 방법을 알고 있어야 합니다. 여기서는이 화면을 기본적인 전자 메일 화면에 연결 하 고 **MyPeople** collection의 사용자에 게 전자 메일을 보내는 방법을 안내 합니다. 또한 [전자 메일 화면이](./email-screen-overview.md) 작동 하는 방식을 파악할 수 있습니다.

1. **보기** 탭을 선택 하 **고 데이터** **소스 > 데이터 소스를 추가**하 고 office 365 Outlook 커넥터를 검색 하 여 office 365 outlook 데이터 원본을 앱에 추가 합니다. **새 연결** 을 선택 하 여 찾을 수 있습니다.
1. 사용자 화면을 삽입 한 후 빈 화면을 새로 삽입 합니다. 이 화면에서 뒤로 화살표 아이콘, 두 개의 텍스트 상자 및 송신 아이콘을 추가 합니다.
1. 화면 이름을 **Emailscreen**로, 뒤로 화살표 아이콘을 **backicon**으로, 한 텍스트 입력 상자를 **선**으로, 기타를 **Messagebody**로, 송신 아이콘을 **sendicon**으로 바꿉니다.
1. **Backicon** 의 **onselect** 속성을 `Back()`로 설정 합니다.
1. **Sendicon** 의 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    여기서는 Outlook 커넥터를 사용 하 여 전자 메일을 보냅니다. 이 `Concat(MyPeople, UserPrincipalName & ";")` 받는 사람 목록으로 전달 합니다. 이 수식은 **MyPeople** collection의 모든 전자 메일 주소를 세미콜론으로 구분 하 여 단일 문자열로 연결 합니다. 이는 선호 하는 전자 메일 클라이언트의 "대상" 줄에서 세미콜론으로 구분 된 전자 메일 주소 문자열을 작성 하는 것과 다르지 않습니다.
    * 메시지의 제목으로 `SubjectLine.Text`를 전달 하 고 `MessageBody.Text` 메시지의 본문으로 전달 합니다.
1. 사용자 화면의 오른쪽 위 모서리에서 **메일** 아이콘을 삽입 합니다.
   아이콘 색을 원하는 대로 변경 합니다.
1. **Sendicon** 의 **onselect** 속성을 `Navigate( EmailScreen, None )`로 설정 합니다.

    이제 사용자를 선택 하 고 전자 메일 메시지를 작성 한 다음 보낼 수 있는 2 화면 앱이 있습니다. 앱이 **MyPeople** collection에 추가 하는 모든 사용자에 게 전자 메일을 보내기 때문에 자유롭게 테스트해 볼 수 있습니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 참조 설명서를 봅니다](./people-screen-reference.md).
* [Office 365 Outlook 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-outlook.md).
* [Office 365 사용자 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-users.md).
