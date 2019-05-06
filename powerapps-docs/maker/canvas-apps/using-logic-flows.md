---
title: 캔버스 앱에서 흐름 시작 | Microsoft Docs
description: 캔버스 앱에서 사용자의 단추 선택과 같은 이벤트가 발생한 후 하나 이상의 작업을 수행하는 흐름을 만듭니다.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5439399a22b47fcf4195cf878208e0e0bd4e0764
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61532114"
---
# <a name="start-a-flow-in-a-canvas-app"></a>캔버스 앱에서 흐름 시작

Microsoft Flow를 사용하여 캔버스 앱에서 이벤트가 발생할 때 하나 이상의 작업을 수행하는 논리를 만들 수 있습니다. 예를 들어 사용자가 단추를 선택하면 SharePoint 목록에 항목을 만들거나, 전자 메일 또는 모임 요청을 보내거나, 클라우드에 파일을 추가하거나, 이러한 모든 작업을 추가하도록 해당 단추를 구성합니다. 흐름을 시작하도록 앱에서 모든 컨트롤을 구성하여 PowerApps를 닫은 경우에도 계속 실행되도록 할 수 있습니다.

> [!NOTE]
> 사용자가 앱 내에서 흐름을 실행 하는 경우 해당 사용자 흐름에 지정 된 작업을 수행할 권한이 있어야 합니다. 그렇지 않은 경우 흐름이 실패 합니다.

## <a name="prerequisites"></a>필수 조건

- PowerApps에 [등록](../signup-for-powerapps.md)합니다.
- [컨트롤을 구성](add-configure-controls.md)하는 방법을 알아봅니다.

## <a name="create-a-flow"></a>흐름 만들기

1. [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

1. 왼쪽 탐색 모음에서 **비즈니스 논리**를 선택한 후 **흐름**을 선택합니다.

1. **내 흐름** 페이지의 왼쪽 위 모서리에서 **새로 만들기**를 선택한 후 **빈 페이지에서 만들기**를 선택합니다.

    ![템플릿을 사용하지 않고 흐름을 만드는 옵션](./media/using-logic-flows/create-from-blank.png)

1. 표시되는 페이지의 아래쪽에서 **수백 개의 커넥터 및 트리거 검색**을 선택합니다.

1. 검색 상자에 **PowerApps**를 입력한 후 **PowerApps** 아이콘을 선택합니다.

    ![PowerApps 트리거 만들기](./media/using-logic-flows/set-trigger.png)
    
1. 다음 페이지에서 PowerApps 아이콘을 다시 선택한 후 **새 단계**를 선택합니다.

1. **커넥터 및 작업 검색** 상자에서, 이 예제와 같이 흐름에 대한 작업을 지정합니다.

   1. 상자에 **SharePoint**를 입력한 다음 **동작** 아래 목록에서 **항목 만들기**를 선택합니다.

       ![SharePoint 항목을 만드는 옵션](./media/using-logic-flows/create-sharepoint-item.png)

   1. 메시지가 표시되면 SharePoint에 연결하기 위한 자격 증명을 제공합니다.

   1. **사이트 주소** 상자에서 목록이 포함된 SharePoint Online 사이트의 URL을 입력하거나 붙여넣습니다.

       > [!NOTE]
       > URL에 목록 이름을 추가하지 않습니다.

   1. **목록 이름** 상자에서 사용하려는 목록을 지정합니다.
   
       ![목록 지정](./media/using-logic-flows/list-fields.png)

   1. 목록에서 필드에 대한 입력 상자(**제목**과 같은)를 선택하고 동적 콘텐츠 창에서 **자세히 보기**를 선택하고 **PowerApps에서 질문**을 선택합니다. 

       ![[제목] 필드에서 [PowerApps에서 질문] 매개 변수 추가](./media/using-logic-flows/ask-in-powerapps.png)

1. (선택 사항) 다른 데이터 소스에서 관련된 항목을 만들거나 지정한 주소로 승인 메일을 보내기 같은 하나 이상의 추가 단계를 지정 합니다.

1. 왼쪽 위 모서리 근처에서 흐름 이름을 입력하거나 붙여넣기한 후, 오른쪽 모서리 근처의 **저장**을 선택합니다.

## <a name="add-a-flow-to-an-app"></a>앱에 흐름 추가
1. 왼쪽 탐색 모음에서 **만들기**를 선택합니다.

1. **빈 페이지의 캔버스 앱** 타일을 선택한 후 **앱으로 만들기**를 선택합니다.

1. **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하고, **RecordTitle**이라는 이름을 지정합니다.

1. **[단추](controls/control-button.md)** 컨트롤을 추가하고 **RecordTitle** 아래로 이동합니다.

1. **[단추](controls/control-button.md)** 컨트롤을 선택하고 **작업** 탭에서 **Flows**를 선택합니다.

    ![[작업] 탭의 [흐름] 옵션](./media/using-logic-flows/action-tab.png)

1. 표시되는 창에서 이전 절차에서 만든 흐름을 선택합니다.

    > [!NOTE]
   > 만든 흐름을 사용할 수 없는 경우 PowerApps가 흐름을 만든 환경으로 설정되어 있는지 확인합니다.

    ![사용자 지정 창에서 흐름 추가](./media/using-logic-flows/add-flow-from-pane.png)

1. 수식 입력줄에서 자동으로 추가된 수식 끝에 **RecordTitle.Text)** 를 입력하거나 붙여넣습니다.

    ![흐름이 포함된 OnSelect 속성](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>흐름 테스트
1. **텍스트 입력** 컨트롤을 두 번 클릭하고, 텍스트를 입력하거나 붙여넣습니다.

1. Alt 키를 누른 채로 **[단추](controls/control-button.md)** 컨트롤을 선택합니다.

    제목으로 지정한 텍스트를 사용하여 지정한 목록에 SharePoint 항목이 생성됩니다. 흐름이 실행될 때 목록이 열려 있었으면 브라우저 창을 새로 고쳐 변경 내용을 표시합니다.
