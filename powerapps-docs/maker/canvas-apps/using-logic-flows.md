---
title: 캔버스 앱에서 흐름 시작 | Microsoft Docs
description: 캔버스 앱에서 사용자의 단추 선택과 같은 이벤트가 발생한 후 하나 이상의 작업을 수행하는 흐름을 만듭니다.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a4e19b4b261bb489dd5c63e4393452a500ab3df9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732905"
---
# <a name="start-a-flow-in-a-canvas-app"></a>캔버스 앱에서 흐름 시작

Power 자동화를 사용 하 여 캔버스 앱에서 이벤트가 발생할 때 하나 이상의 작업을 수행 하는 논리를 만들 수 있습니다. 예를 들어 사용자가 단추를 선택하면 SharePoint 목록에 항목을 만들거나, 전자 메일 또는 모임 요청을 보내거나, 클라우드에 파일을 추가하거나, 이러한 모든 작업을 추가하도록 해당 단추를 구성합니다. 앱에서 모든 컨트롤을 구성 하 여 흐름을 시작할 수 있습니다 .이는 Power Apps를 닫은 경우에도 계속 실행 됩니다.

> [!NOTE]
> 사용자가 앱 내에서 흐름을 실행 하는 경우 해당 사용자에 게 흐름에 지정 된 작업을 수행할 수 있는 권한이 있어야 합니다. 그렇지 않으면 흐름이 실패 합니다.

## <a name="prerequisites"></a>필수 조건

- Power Apps에 [등록](../signup-for-powerapps.md) 합니다.
- [컨트롤을 구성](add-configure-controls.md)하는 방법을 알아봅니다.

## <a name="create-a-flow"></a>흐름 만들기

1. [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인 합니다.

1. 왼쪽 탐색 모음에서 **비즈니스 논리**를 선택 하 고 **흐름**을 선택 합니다.

1. **내 흐름** 페이지의 왼쪽 위 모서리에서 **새로**만들기를 선택 하 고 **빈 페이지에서 만들기**를 선택 합니다.

    ![템플릿을 사용하지 않고 흐름을 만드는 옵션](./media/using-logic-flows/create-from-blank.png)

1. 표시 되는 페이지의 아래쪽 근처에서 수백 개의 **연결 및 트리거 검색**을 선택 합니다.

1. 검색 상자에 **powerapps**를 입력 한 다음 **powerapps** 아이콘을 선택 합니다.

    ![Power Apps 트리거 만들기](./media/using-logic-flows/set-trigger.png)
    
1. 다음 페이지에서 전원 앱 아이콘을 다시 선택 하 고 **새 단계**를 선택 합니다.

1. **커넥터 및 작업 검색**상자에서 다음 예제와 같이 흐름에 대 한 작업을 지정 합니다.

   1. 상자에 **SharePoint** 를 입력 하 고 **작업**아래 목록에서 **항목 만들기** 를 선택 합니다.

       ![SharePoint 항목을 만드는 옵션](./media/using-logic-flows/create-sharepoint-item.png)

   1. 메시지가 표시되면 SharePoint에 연결하기 위한 자격 증명을 제공합니다.

   1. **사이트 주소** 상자에서 목록이 포함된 SharePoint Online 사이트의 URL을 입력하거나 붙여넣습니다.

       > [!NOTE]
       > 목록의 이름을 URL에 추가 하지 마세요.

   1. **목록 이름** 상자에서 사용 하려는 목록을 지정 합니다.
   
       ![목록 지정](./media/using-logic-flows/list-fields.png)

   1. 목록에서 필드의 입력 상자 (예: **제목**)를 선택 하 고 동적 콘텐츠 창에서 **자세히 보기** 를 선택한 다음, **Power Apps에서 묻기**를 선택 합니다. 

       ![제목 필드에 Power Apps 매개 변수에 Ask 추가](./media/using-logic-flows/ask-in-powerapps.png)

1. 필드 지정 된 주소로 승인 메일을 보내거나 다른 데이터 원본에서 관련 항목을 만드는 등의 추가 단계를 하나 이상 지정 합니다.

1. 왼쪽 위 모서리에서 흐름의 이름을 입력 하거나 붙여 넣은 다음, 오른쪽 위 모퉁이 근처에서 **저장** 을 선택 합니다.

## <a name="add-a-flow-to-an-app"></a>앱에 흐름 추가
1. 왼쪽 탐색 모음에서 **만들기**를 선택 합니다.

1. **빈 타일에서 캔버스 앱** 을 마우스로 가리킨 다음 **이 앱 만들기**를 선택 합니다.

1. **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하고, **RecordTitle**이라는 이름을 지정합니다.

1. **[단추](controls/control-button.md)** 컨트롤을 추가하고 **RecordTitle** 아래로 이동합니다.

1. **[단추](controls/control-button.md)** 컨트롤을 선택하고 **작업** 탭에서 **흐름**을 선택합니다.

    ![[작업] 탭의 [흐름] 옵션](./media/using-logic-flows/action-tab.png)

1. 표시되는 창에서 이전 절차에서 만든 흐름을 선택합니다.

    > [!NOTE]
   > 만든 흐름을 사용할 수 없는 경우에는 전원 앱이 흐름을 만든 환경으로 설정 되어 있는지 확인 합니다.

    ![사용자 지정 창에서 흐름 추가](./media/using-logic-flows/add-flow-from-pane.png)

1. 수식 입력줄에서 자동으로 추가된 수식 끝에 **(RecordTitle.Text)** 를 입력하거나 붙여넣습니다.

    ![흐름이 포함된 OnSelect 속성](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>흐름 테스트
1. **텍스트 입력** 컨트롤을 두 번 클릭 하 고 일부 텍스트를 입력 하거나 붙여 넣습니다.

1. Alt 키를 누른 채로 **[단추](controls/control-button.md)** 컨트롤을 선택 합니다.

    제목으로 지정한 텍스트를 사용 하 여 지정한 목록에 SharePoint 항목이 생성 됩니다. 흐름이 실행될 때 목록이 열려 있었으면 브라우저 창을 새로 고쳐 변경 내용을 표시합니다.
