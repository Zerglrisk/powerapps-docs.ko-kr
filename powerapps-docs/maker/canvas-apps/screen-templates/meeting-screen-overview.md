---
title: 모임 화면 템플릿 | Microsoft Docs
description: 캔버스 앱에 대 한 모임 화면 템플릿 작동 방법 이해 및 사용자 고유의 사용 사례에 맞게 화면 확장
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
ms.openlocfilehash: 2b300b0d90803ae08aaf262dde5642f4d448c05f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541427"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>캔버스 앱에 대 한 모임 화면 템플릿 개요

Canvas 앱에서 사용자가 Office 365 Outlook 계정에서 모임 요청을 만들고 보낼 수 있는 모임 화면을 추가 합니다. 사용자는 조직에서 참가자를 검색 하 고 외부 전자 메일 주소를 추가할 수 있습니다. 테 넌 트에 Outlook에 기본 제공 된 대화방이 있는 경우 사용자가 위치도 선택할 수 있습니다.

[전자 메일](email-screen-overview.md), 조직의 [사용자](people-screen-overview.md) 및 사용자 [달력과](calendar-screen-overview.md)같은 Office 365의 다른 데이터를 표시 하는 다른 템플릿 기반 화면을 추가할 수도 있습니다.

이 개요에서는 화면의 상위 수준 기능에 대해 설명 합니다.

이 화면의 기본 기능을 자세히 알아보려면 [모임 화면 참조](meeting-screen-reference.md)를 참조 하세요.

## <a name="prerequisite"></a>필수 조건

[PowerApps에서 앱을 만들](../data-platform-create-app-scratch.md)때 화면과 기타 컨트롤을 추가 하 고 구성 하는 방법을 잘 알고 있어야 합니다.

## <a name="default-functionality"></a>기본 기능

템플릿에서 모임 화면을 추가 하려면 다음을 수행 합니다.

1. PowerApps에 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 한 다음 앱을 만들거나 PowerApps Studio에서 기존 앱을 엽니다.

    이 항목은 휴대폰 앱을 표시 하지만 동일한 개념은 태블릿 앱에도 적용 됩니다.

1. 리본의 **홈** 탭에서 **새 화면** > **모임**을 선택 합니다.

  입력 하는 경우 모임 화면의 두 탭은 다음과 유사 하 게 표시 됩니다.

  ![모임 화면, 두 탭 모두](media/meeting-screen/meeting-screen-full-both.png)

몇 가지 유용한 참고 사항:

* 모임 화면에서 앱 사용자는 Outlook에서 모임을 만들 수 있습니다.
  사용자는 참석자를 검색 및 추가 하 고 필요에 따라 모임 대화방을 모임에 추가할 수 있습니다.
* 조직에서 사용자를 검색 하려면 "참석자" 아래의 텍스트 입력 상자에 이름을 입력 합니다.
* 사용자를 검색 하면 상위 15 개 결과만 반환 됩니다.
* 조직 외부에 있는 참석자에 대 한 전자 메일 주소를 추가 하려면 전체 유효한 전자 메일 주소를 입력 하 고 전자 메일 주소 오른쪽에 표시 되는 ' + ' 아이콘을 선택 합니다.
* 모임을 만들려면 참석자로 하나 이상의 사용자를 추가 하 고 제목을 입력 한 다음 **일정** 탭에서 모임 시간을 선택 해야 합니다.
* 모임 요청을 보내면 해당 모임에 대 한 모든 정보가 지워집니다.
* 보내기 아이콘 (오른쪽 위 모서리)의 **Onselect** 문에는 다음 수식이 포함 되어 있습니다.
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* "Calendar"는 대부분의 Office 사용자 달력에 대 한 기본 표시 이름 이지만 조직 마다 다를 수 있습니다. 그렇다면 조직의 적절 한 용어로 "일정"을 변경할 수 있습니다.
* 이전에 발생 한 모임을 예약 하거나 모임에 20 명 이상의 사용자를 추가 하려고 하면 오류가 발생 합니다.

## <a name="next-steps"></a>다음 단계

* [이 화면에 대 한 참조 설명서를 봅니다](./meeting-screen-reference.md).
* [Office 365 Outlook 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-outlook.md).
* [Office 365 사용자 커넥터에 대해 자세히 알아보세요](../connections/connection-office365-users.md).
