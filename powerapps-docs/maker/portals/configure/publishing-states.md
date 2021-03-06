---
title: Power Apps 포털에서 게시 상태 만들기 및 관리 | MicrosoftDocs
description: 포털에서 게시 상태를 만들고 관리하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5ba33887a0b99cc3ddf1eb118ca506a9b740d015
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883920"
---
# <a name="create-and-manage-publishing-states"></a>게시 상태 만들기 및 관리

게시 상태는 포털 웹 사이트의 콘텐츠 수명 주기 정의를 허용합니다. 기본 수준에서 게시 상태는 연결된 엔터티를 포털에서 표시/게시로 간주해야 하는지 여부를 결정할 수 있습니다. 보다 복잡한 구성에서는 각 단계에 대한 보안 제한을 통해 콘텐츠 검토 및 게시를 위한 다단계 프로세스를 정의할 수 있습니다.

게시 상태는 [웹 페이지](web-page.md), [웹 파일](web-files.md), [웹 링크](manage-web-links.md), 포럼 및 광고와 함께 사용할 수 있습니다.

기본적으로 초안 및 게시의 두 게시 상태를 사용할 수 있습니다. 초안은 콘텐츠 작성자가 아닌 사용자에게 표시되어서는 안 되는 콘텐츠를 지정하는 반면, 게시됨은 다른 보안 제한이 없이 모든 포털 사용자에게 표시되어야 하는 콘텐츠를 지정합니다. 원하는 경우 새 상태를 추가하거나 상태 이름을 변경하여 기본 구성을 수정하여 특정 요구 사항을 충족할 수 있습니다.

## <a name="manage-publishing-states"></a>게시 상태 관리

포털 내에서 게시 상태를 만들고, 편집하고, 삭제할 수 있습니다.

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **엡사이트**로 이동합니다.

3. 게시 상태를 관리할 웹 사이트를 선택합니다.

4. **게시 상태** 탭으로 이동합니다. 사용 가능한 게시 상태 목록이 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![게시 상태 관리](../media/publishing-states.png "게시 상태 관리")

5. 새 게시 상태를 추가하려면 **새 게시 상태**를 선택합니다.

6. 기존 게시 상태를 편집하려면 게시 상태 이름을 선택합니다.

7. 게시 상태 창에서 필드에 적절한 값을 입력합니다.

8. **저장 후 닫기**를 선택합니다.


### <a name="publishing-state-attributes"></a>게시 상태 특성

|이름|설명|
|-----|--------|
|이름|상태를 설명하는 이름입니다. 이 필드는 필수 필드입니다.|
|웹 사이트|상태가 속한 웹 사이트입니다. 이 필드는 필수 필드입니다.|
|기본값 여부|이 확인란을 선택하면 웹 사이트의 기본 상태로 지정합니다. 이렇게 하면 포털 전면 편집 인터페이스를 통해 새 엔터티를 생성할 때 선택된 기본 상태가 결정됩니다.<br>**참고**: 지정된 웹 사이트에서 하나의 게시 상태만 기본 상태로 표시되어야 합니다.|
|표시 가능|이 옵션을 선택하면 이 상태와 연결된 엔터티가 포털에 표시되거나 게시된 것으로 간주되도록 지정합니다.<br>표시되지 않는 상태와 연결된 엔터티가 포털에 표시되지 않을 수 있지만, 보안 권한, 만료 날짜 또는 기타 표시 규칙으로 인해 표시 상태와 연결된 엔터티가 표시되지 않을 수도 있습니다.<br>콘텐츠 관리 권한이 있는 사용자는 미리 보기 모드를 사용하여 게시되지 않은 콘텐츠를 미리 볼 수 있습니다.|
|표시 순서|주로 포털 프런트 사이드 편집 인터페이스에서 찾을 수 있는 게시 상태를 선택하기 위한 메뉴 및 드롭다운 목록에서 상태가 배치되는 순서를 나타내는 정수 값입니다.|
|||

## <a name="publishing-state-transition-rules"></a>게시 상태 전환 규칙

게시 상태 전환 규칙을 사용 하면 게시 상태 측면에서 포털의 콘텐츠 변경 내용을 만들 수 있는 권한이 있는 웹 역할을 세부적으로 제어할 수 있습니다.

정확하게 말하면 게시 상태 전환 규칙은 게시 상태(초안 또는 게시됨) 간의 전환을 제어합니다. 사용자가 항목의 게시 상태를 전환하려고 하면 이 전환에 대한 규칙이 있으면 보안 공급자는 로그인한 사용자의 웹 역할에 이 전환을 수행할 권한이 있다고 어설션합니다.

변경하려고 하는 로그인한 사용자가 규칙에 할당한 역할 중 하나라도 있으면 전환이 성공적으로 수행됩니다. 사용자에게 규칙을 변경할 수 있는 권한이 없는 경우에는 프런트 사이드 편집에서 해당 변경 사항을 허용하지 않습니다. 또는 규칙을 만들 수 있습니다. 그런 다음 웹 역할을 만들 때 웹 역할에 규칙을 추가합니다. 하나의 규칙을 여러 웹 역할과 연결할 수 있으며 그 반대의 경우도 마찬가지입니다.

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **비활성 게시 상태 전환 규칙**으로 이동합니다.

3. 새 규칙을 만들려면 **새로 만들기**를 선택합니다.

4. 기존 규칙을 편집하려면 규칙 이름을 선택합니다.

5. 게시 상태 전환 규칙 창에서 필드에 적절한 값을 입력합니다.

6. 웹 역할을 계속 추가할 수 있도록 **저장**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![게시 상태 전환 규칙 만들기](../media/publishing-state-transition-rule.png "게시 상태 전환 규칙 만들기")

7. **웹 역할** 탭에서 **기존 웹 역할 추가**를 선택합니다. **조회 레코드** 창에서 적절한 웹 역할을 찾아서 추가하십시오.

8. **저장**을 선택합니다.

## <a name="state-based-control-rules"></a>상태 기반 제어 규칙

[웹 페이지 액세스 제어 규칙](webpage-access-control.md)은 게시 상태와 연결하여 웹 사이트의 분기 및 해당 분기 내의 콘텐츠 게시 상태를 기반으로 콘텐츠를 보거나 수정할 수 있는 권한을 허용하거나 거부할 수 있습니다. 이를 수행하려면 웹 페이지 액세스 제어 규칙을 게시 상태와 연결합니다. 게시 상태와 연결되면 해당 게시 상태가 활성 상태인 경우에만 규칙이 웹 페이지에 적용됩니다.

예를 들어, 콘텐츠 게시 역할의 다른 사용자가 페이지의 콘텐츠를 수정할 수 있도록 하고 해당 페이지가 초안 모드일 때만 원한다고 가정 합니다.  이렇게 하면 페이지가 '라이브'인 동안 페이지에 대한 변경 작업을 수행하지 않고 보류 중인 변경 내용에 대해 승인 프로세스를 수행할 수 있습니다.

이렇게 하려면 변경 권한 부여 권한이 있는 규칙을 만들어 해당 분기에 적용합니다(또는 규칙이 전체 사이트에 적용되는 경우 홈 페이지). 그런 다음 이 규칙을 초안 상태와 연결합니다.

> [!div class=mx-imgBorder]
> ![상태 기반 제어 규칙 만들기](../media/state-based-control-rule.png "상태 기반 제어 규칙 만들기")

그런 다음 이 규칙을 콘텐츠 게시와 같은 적절한 웹 역할에 연결합니다. 이 웹 역할이 더 관대한 규칙(예: 게시 상태에 관계 없이 변경 권한을 부여하는 규칙)과 연결되어 있지 않다고 가정할 경우 콘텐츠 게시 웹 역할의 사용자는 초안 상태의 페이지를 수정할 수는 있지만 게시된 상태의 페이지는 수정할 수는 없습니다.
