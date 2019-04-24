---
title: 반응 형 레이아웃에서 캔버스 앱 만들기 | Microsoft Docs
description: 캔버스 앱에서 컨트롤의 높이, 너비, X 및 Y 속성을 구성 하는 방법에 대 한 참조 정보
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ddd11ddd40792ef1042536041554737ddb16547b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61562528"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>반응 형 레이아웃에서 캔버스 앱 만들기

PowerApps의 캔버스 앱을 빌드하기 전에 휴대폰 또는 태블릿에 대 한 앱에 맞게 여부를 지정 합니다. 이 선택 항목 크기 및 앱을 빌드할 수 있습니다 캔버스의 모양을 결정 합니다.

선택 하는 경우 몇 가지 다른 옵션 선택 후 해당 선택을 만들 수 있습니다 **파일** > **앱 설정** > **화면 크기 + 방향**합니다. 세로 또는 가로 방향 및 화면 크기 (태블릿에만 해당)를 선택할 수 있습니다. 또한 잠금 또는 가로 세로 비율 잠금 해제 및 (또는 비공유) 장치 회전을 지원 합니다.

이러한 선택 항목에는 화면 레이아웃을 디자인할 때를 확인 하는 다른 모든 선택 기반 갖추어야 합니다. 다른 크기의 장치에서 또는 웹 앱이 실행 되는 경우 전체 레이아웃 앱이 실행 하는 화면에 맞게 조정 합니다. 큰 브라우저 창에서 실행 되는 휴대폰에 대 한 설계 된 앱, 앱은 보정을 위해 크기가 조정 되 고 해당 공간에 대 한 너무 큰 찾습니다 예를 들어. 앱 더 많은 컨트롤 또는 콘텐츠 더 보기를 표시 하 여 추가 픽셀 활용할 수 없습니다.

반응 형 레이아웃을 만든 컨트롤 다양 한 환경 자연스럽 게 느낄 창 크기를 만드는 다양 한 장치에 응답할 수 있습니다. 반응 형 레이아웃을 달성 하려면 일부 설정을 조정 하 고 앱 전체에서 식을 작성 합니다. 

## <a name="disable-scale-to-fit"></a>에 맞게 크기 조정 사용 안 함

해당 레이아웃 앱 실행 되는 실제 공간에 맞게 조정 되도록 각 화면을 구성할 수 있습니다.

앱의 전원을 켜는 방식으로 응답성을 활성화 **규모에 맞게** 기본적으로 사용 되는 설정입니다. 이 설정이 꺼집니다를 설정 하면 끄면 **가로 세로 비율 고정** 특정 화면 셰이프에 대 한 더 이상 디자인할 때문입니다. (지정할 수 있습니다 여전히 앱 장치 회전을 지원 하는지 여부를.)

![확장을 사용 하지 않도록 설정에 맞게](media/create-responsive-layout/scale-to-fit-off.png)

할 수 있게 앱 응답성이 뛰어난 추가 단계를 수행 해야 바인딩되지만 그러한이 변경 응답성을 만들기 위한 첫 단계입니다.

## <a name="understand-app-and-screen-dimensions"></a>앱 및 화면 크기 이해

화면 크기에 대 한 변경 내용에 응답 하는 앱의 레이아웃을 만들려면 사용 하는 수식을 작성 합니다 **너비** 하 고 **높이** 화면의 속성입니다. 이러한 속성을 표시 하려면 PowerApps Studio 앱 열기 하 고 화면을 선택 합니다. 이러한 속성에 대 한 기본 수식을 표시 합니다 **고급** 오른쪽 창의 탭 합니다.

**너비** = `Max(App.Width, App.DesignWidth)`

**Height** = `Max(App.Height, App.DesignHeight)`

이러한 수식 참조를 **너비**를 **높이**를 **DesignWidth**, 및 **DesignHeight** 앱의 속성입니다. 앱의 **너비** 하 고 **높이** 앱 실행 되는 장치 또는 브라우저 창의 크기에 해당 하는 속성입니다. 사용자의 브라우저 창 크기를 조정 하는 경우 (또는 하지 않도록 설정한 경우 장치를 회전 시킵니다 **방향 잠금**), 이러한 속성의 값을 동적으로 변경 합니다. 화면의 수식을 **너비** 하 고 **높이** 속성에는 이러한 값을 변경 하는 경우 다시 계산 됩니다.

**DesignWidth** 하 고 **DesignHeight** 속성에서 지정 하는 차원에서 제공 되는 **화면 크기 + 방향** 창 **앱 설정** . 예를 들어 휴대폰 레이아웃을 세로 방향 **DesignWidth** 는 640, 및 **DesignHeight** 1136 됩니다.

화면에 대 한 수식을 사용 되는 대로 **너비** 하 고 **높이** 속성을 생각할 수 있습니다 **DesignWidth** 및 **DesignHeight** 앱을 디자인 하면의 최소 크기입니다. 앱에 사용할 수 있는 실제 영역도 이러한 최소 보다 작은 경우 차원에 화면에 대 한 수식을 **너비** 하 고 **높이** 속성 확인 된 값 보다 작은 것뿐입니다 없습니다 최소값입니다. 이 경우 사용자 모든 화면의 콘텐츠를 보려면 스크롤해야 합니다.

앱을 설정한 후 **DesignWidth** 하 고 **DesignHeight**, (대부분의 경우) 않아도 각 화면에 대 한 기본 수식을 변경할 **너비** 및 **높이** 속성입니다. 나중에이 항목에는 이러한 수식을 사용자 지정 하려는 경우를 설명 합니다.

## <a name="use-formulas-for-dynamic-layout"></a>동적 레이아웃에 대 한 수식을 사용 하 여

반응 형 디자인을 만들려면 찾기 및 절대 (일정) 좌표 값 대신 수식을 사용 하 여 각 컨트롤의 크기입니다. 이러한 수식에는 각 컨트롤의 위치 및 크기가 전체 화면 크기를 기준으로 또는 화면의 다른 컨트롤을 기준으로 표현합니다.

> [!IMPORTANT]
> 에 대 한 수식을 작성 한 후 합니다 **X**, **Y**를 **너비** 하 고 **높이** 컨트롤의 속성을 사용 하 여 수식을 덮어쓰게 됩니다 이후에 캔버스 편집기에서 컨트롤을 끌면 상수 값입니다. 수식을 사용 하 여 동적 레이아웃을 달성을 시작 하면 컨트롤을 끌어서 놓는 하지 마십시오.

가장 간단한 경우 하나의 컨트롤을 전체 화면을 채웁니다. 이 효과 만들려면 이러한 값을 컨트롤의 속성을 설정 합니다.

| 속성      | Value            |
|--------|---------------|
| **X**      | `0`             |
| **Y**      | `0`             |
| **Width**  | `Parent.Width`  |
| **Height** | `Parent.Height` |

이러한 수식을 사용 합니다 **부모** 연산자입니다. 화면에 직접 배치 되는 컨트롤에 대 한 **부모** 화면을 가리킵니다. 이러한 속성 값을 사용 하 여 컨트롤 (0, 0) 화면의 왼쪽 위 모서리에 표시 되 고 동일한 **너비** 하 고 **높이** 화면으로 합니다.

이 항목의 뒷부분에 나오는 이러한 원칙을 적용 합니다 (및 **부모** 연산자) 갤러리와 같은 다른 컨테이너 내에서 컨트롤의 위치, 컨트롤 및 구성 요소를 그룹화 합니다.

대신 컨트롤 화면 위쪽 절반만 채울 수 있습니다. 이 효과 만들려면 다음을 설정 합니다 **높이** 속성을 **Parent.Height** / 2를 두고 변경 하지 않고 다른 수식입니다.

두 번째 컨트롤에 맞게 아래쪽 절반 동일한 화면을 원한다 면 해당 수식을 생성 두 개 이상의 방법이 수행할 수 있습니다. 편의상,이 접근 방식을 사용할 수 있습니다.

| 컨트롤 | 속성 | 수식           |
|-|----------|-------------------|
| **위** | **X**        | `0`                 |
| **위** | **Y**        | `0`                 |
| **위** | **Width**    | `Parent.Width`      |
| **위** | **Height**   | `Parent.Height / 2` |
| **Lower** | **X**        | `0`                 |
| **Lower** | **Y**        | `Parent.Height / 2` |
| **Lower** | **Width**    | `Parent.Width`      |
| **Lower** | **Height**   | `Parent.Height / 2` |

![위 높아지고 컨트롤](media/create-responsive-layout/dynamic-layout.png)

이 구성의 원하는 효과 달성 하 하지만 마음이 컨트롤의 상대 크기를 변경한 경우 각 수식 편집 해야 합니다. 예를 들어, 최상위 컨트롤 채우기 하위 2 / 3 아래쪽 컨트롤과는 최상위의 1/3 화면을 차지를 결정할 수 있습니다. 

업데이트 해야 해당 효과 만들려면를 **높이** 의 속성을 **위** 컨트롤 및 **Y** 및 **높이** 의 속성은 **낮은** 제어 합니다. 고려해 야 하는 수식을 작성 합니다 **낮은** 측면의 제어를 **위** 컨트롤 (및 자체),이 예제와 같이:


| 컨트롤 | 속성 | 수식           |
|-|----------|-------------------|
| **위** | **X**        | `0`                 |
| **위** | **Y**        | `0`                 |
| **위** | **Width**    | `Parent.Width`      |
| **위** | **Height**   | `Parent.Height / 2` |
| **Lower** | **X**        | `0`                       |
| **Lower** | **Y**        | `Upper.Y + Upper.Height`  |
| **Lower** | **Width**    | `Parent.Width`            |
| **Lower** | **Height**   | `Parent.Height - Lower.Y` |

![상위 및 하위 컨트롤 상대 크기 조정](media/create-responsive-layout/dynamic-layout2.png)

유일 하 게 변경 해야이 수식의 **높이** 의 속성을 **위** 화면의 높이의 다른 부분을 표현 하는 컨트롤. 합니다 **낮은** 컨트롤에서 자동으로 이동 하 고 변경에 맞게 크기를 조정 합니다.

이러한 수식 패턴을 사용 하 여 일반적인 레이아웃 컨트롤, 명명 된 관계를 표현 하기 위한 **C**, 및 부모 또는 형제 컨트롤 이라는 **D**합니다.

| C와 해당 부모 간의 관계 | 속성 | 수식 | 그림 |
|--|--|--|--|
| **C** 여백을 부모의 너비를 채웁니다 *N* | **X**| `N` | ![부모의 C 채우기 너비의 예](media/create-responsive-layout/c1.png) |
|  | **Width** | `Parent.Width - (N * 2)` |  |
| **C** 여백을 부모의 높이 채우는 *N* | **Y** | `N` | ![부모의 C 채우기 높이의 예](media/create-responsive-layout/c2.png) |
|  | **Height** | `Parent.Height - (N * 2)` |  |
| **C** 여백에 부모의 오른쪽 가장자리에 맞춥니다 *N* | **X** | `Parent.Width - (C.Width + N)` | ![부모의 가장자리에 맞게 조정 하는 C의 예](media/create-responsive-layout/c3.png) |
| **C** 여백에 부모의 아래쪽 가장자리에 맞춥니다 *N* | **Y** | `Parent.Height - (C.Height + N)` | ![부모의 가장자리에 맞게 조정 하는 C의 예](media/create-responsive-layout/c4.png) |
| **C** 부모에서 가로 방향으로 가운데 | **X** | `(Parent.Width - C.Width) / 2` | ![부모에서 가로 방향으로 가운데 C의 예](media/create-responsive-layout/c5.png) |
| **C** 부모에 세로 방향으로 가운데 | **Y** | `(Parent.Height - C.Height) / 2` | ![부모에서 세로 방향으로 가운데 C의 예](media/create-responsive-layout/c6.png) |

| C 및 D 간의 관계 | 속성 | 수식 | 그림 |
|--|--|--|--|
| **C** 가로로 맞추어 **D** 와 동일한 너비로 **D** | **X** | `D.X` | ![패턴의 예](media/create-responsive-layout/d1.png) |
|  | **Width**    | `D.Width` |  |
| **C** 세로로 맞추어 **D** 와 같은 높이로 **D**  | **Y** | `D.Y` | ![패턴의 예](media/create-responsive-layout/d2.png) |
|  | **Height** | `D.Height` |  |
| 가장자리를 마우스 오른쪽 단추로 **C** 의 오른쪽 가장자리에 맞춥니다 **D** | **X** | `D.X + D.Width - C.Width` | ![패턴의 예](media/create-responsive-layout/d3.png) |
| 아래쪽 가장자리 **C** 의 아래쪽 가장자리에 맞춥니다 **D** | **Y** | `D.Y + D.Height - C.Height` | ![패턴의 예](media/create-responsive-layout/d4.png) |
| **C** 기준으로 가로 방향으로 가운데 **D** | **X** | `D.X + (D.Width - C.Width) / 2`  | ![패턴의 예](media/create-responsive-layout/d5.png) |
| **C** 기준으로 세로 방향으로 가운데 **D** | **Y** | `D.Y + (D.Height - C.Height) /2` | ![패턴의 예](media/create-responsive-layout/d6.png) |
| **C** 의 오른쪽에 배치 **D** N 간격으로 | **X** | `D.X + D.Width - N` | ![패턴의 예](media/create-responsive-layout/d7.png) |
| **C** 아래에 배치 **D** 간격으로 *N*             | **Y** | `D.Y + D.Height + N` | ![패턴의 예](media/create-responsive-layout/d8.png) |
| **C** 사이 공백을 채웁니다 **D** 부모의 가장자리를 마우스 오른쪽 단추로 및 | **X** | `D.X + D.Width` | ![패턴의 예](media/create-responsive-layout/d9.png) |
|  | **Width** | `Parent.Width - C.X` |  |
| **C** 사이 공백을 채웁니다 **D** 및 부모의 가장자리 아래쪽 | Y | `D.Y + D.Height` | ![패턴의 예](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>계층형 레이아웃

더 많은 컨트롤을 포함 하는 화면을 생성 하는 대로 될 것 보다 편리한 (또는 필요한) 형제 컨트롤 또는 화면을 기준으로 아닌 부모 컨트롤을 기준으로 컨트롤을 배치 합니다. 컨트롤 계층 구조로 구성 하 여 할 수 있습니다 수식을 쉽게 쓰고 유지 관리할 수 있습니다.

### <a name="galleries"></a>갤러리

갤러리를 사용 하 여 앱에서 갤러리의 템플릿 내에서 컨트롤을 배치 해야 합니다. 사용 하는 수식을 작성 하 여 이러한 컨트롤을 배치할 수 있습니다 합니다 **부모** 갤러리 템플릿을 참조 하는 연산자가 있습니다. 갤러리 템플릿 내에서 컨트롤의 수식에 사용 합니다 **Parent.TemplateHeight** 및 **Parent.TemplateWidth** 속성을 사용 하지 마십시오 **Parent.Width** 및  **Parent.Height**, 갤러리의 전체 크기를 나타냅니다.

![세로 갤러리 템플릿 너비와 높이 표시 합니다.](media/create-responsive-layout/gallery-vertical.png)

### <a name="enhanced-group-control"></a>향상 된 그룹 컨트롤

향상 된 실험적 기능을 사용할 수 있습니다 **그룹** 부모 컨트롤로 제어 합니다. 선택이 기능을 켜려면 **파일** > **앱 설정** > **고급 설정**합니다.

화면 맨 위에 있는 헤더의 예를 살펴보세요. 것 제목 및 사용자에 게 작용할 수 있는 여러 아이콘을 사용 하 여 헤더에 공통적으로 적용 합니다. 확장을 사용 하 여 이러한 헤더를 생성할 수 있습니다 **그룹** 컨트롤을 포함 하는 **레이블을** 컨트롤과 두 **아이콘** 컨트롤:

![그룹을 사용 하는 헤더 예제](media/create-responsive-layout/header-group.png)

이러한 값을 이러한 컨트롤에 대 한 속성을 설정 합니다.

| 속성 | 헤더 | 메뉴 | 닫기 | Title |
|--|--|--|--|--|
| **X** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **Y** | `0` | `0` | `0` | `0` |
| **Width**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Height** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

에 대 한 합니다 **머리글** 컨트롤을 `Parent` 화면을 가리킵니다. 서로 `Parent` 가리킵니다 합니다 **헤더** 컨트롤입니다.

이러한 수식을 작성 하지를 조정할 수 있습니다 크기 또는 위치를 **헤더** 해당 속성에 대 한 수식을 변경 하 여 제어 합니다. 크기 및 자식 컨트롤의 위치는 자동으로 적절 하 게 조정 됩니다.

### <a name="components"></a>구성 요소

명명 된 구성 요소를 다른 실험적 기능을 사용 하는 경우에 구성 요소를 생성할 수 있으며 앱 전체에서 재사용할 수 있습니다. 와 마찬가지로 합니다 **그룹** 컨트롤, 구성 요소 내에 배치한 컨트롤 해야 기준 위치와 크기 수식을 `Parent.Width` 및 `Parent.Height`, 요소의 크기를 나타냅니다. 자세한 정보: [구성 요소를 만드는](create-component.md)합니다.

## <a name="adapting-layout-for-device-size-and-orientation"></a>장치 크기 및 방향에 대 한 레이아웃 조정

지금 수식을 사용 하 여 서로 기준으로 정렬 된 제어를 유지 하는 동안 사용 가능한 공간에 대 한 응답에서 각 컨트롤의 크기를 변경 하는 방법을 알아보았습니다. 하지만 원하는 하거나 다른 장치 크기 및 방향에 대 한 응답에서 더 많은 레이아웃 변경 해야 할 수 있습니다. 장치를 가로 방향으로 세로에서 회전할 때 수평 세로 레이아웃에서 전환 하려는 예를 들어, 합니다. 더 큰 장치에 더 많은 콘텐츠를 제공할 수도 있고 보다 매력적 레이아웃을 제공 하는 다시 정렬 수 있습니다. 더 작은 장치에서 여러 화면 콘텐츠를 분할 해야 합니다.

### <a name="device-orientation"></a>장치 방향

화면에 대 한 기본 수식을 **너비** 하 고 **높이** 속성을 앞에서 설명한이 항목으로 제공 하지 않습니다 반드시 좋은 경험을 사용자가 장치를 회전할 경우. 예를 들어 세로 방향으로 휴대폰에 대 한 설계 된 앱에는 **DesignWidth** 640의와 **DesignHeight** 1136입니다. 가로 방향으로 휴대폰에서 동일한 앱 이러한 속성 값이 적용 됩니다.

- 화면의 **너비** 속성이 `Max(App.Width, App.DesignWidth)`합니다. 앱의 **너비** (1136) 보다 큽니다. 해당 **DesignWidth** (640), 되므로 1136으로 수식을 계산 합니다.
- 화면의 **높이** 속성이 `Max(App.Height, App.DesignHeight)`합니다. 앱의 **높이** (640) 보다 작으면 해당 **DesignHeight** (1136), 되므로 1136으로 수식을 계산 합니다.

화면이 **높이** 1136의 장치 높이 (이 방향)으로 640의 사용자 모두를 경험 하지 않을 내용을 표시 하려면 세로 화면을 스크롤합니다 해야 합니다.

화면에 맞게 **너비** 하 고 **높이** 속성 장치 방향으로 이러한 수식을 사용할 수 있습니다.

**너비** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Height** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

이러한 수식은 앱의 스왑 **DesignWidth** 하 고 **DesignHeight** 장치의 너비 보다 높이가 (세로 방향) 높이가 (가로 방향) 보다 작거나 인지 여부에 따라 값 .

화면을 조정한 후 **너비** 하 고 **높이** 수식 수도 있습니다를 더욱 효율적으로 사용 가능한 공간을 사용 하 여 화면 내에서 컨트롤을 다시 정렬 하려면. 예를 들어, 화면의 절반을 차지 두 컨트롤의 각 세로 세로로 쌓을 하 하지만 환경에 나란히 정렬할 수 있습니다.

화면을 사용할 수 있습니다 **방향을** 가로 또는 세로로 화면 방향 인지 확인 하는 속성입니다.

> [!NOTE]
> 가로 방향으로는 **위쪽** 하 고 **낮은** 컨트롤 왼쪽 및 오른쪽 컨트롤로 표시 합니다.

| 컨트롤 | 속성 | 수식 |
|--|----------|---|
| **위** | **X** | `0` |
| **위** | **Y** | `0` |
| **위** | **Width** | `If(Parent.Orientation = Layout.Vertical, Parent.Width, Parent.Width / 2)` |
| **위** | **Height**   | `If(Parent.Orientation = Layout.Vertical, Parent.Height / 2, Parent.Height)` |
| **Lower** | X | `If(Parent.Orientation = Layout.Vertical, 0, Upper.X + Upper.Width)`  |
| **Lower** | Y | `If(Parent.Orientation = Layout.Vertical, Upper.Y + Upper.Height, 0)` |
| **Lower** | **Width** | `Parent.Width - Lower.X` |
| **Lower** | **Height** | `Parent.Height - Lower.Y` |

![세로 방향에 맞게 식](media/create-responsive-layout/portrait.png)

![가로 방향에 맞게 식](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>화면 크기 및 중단점

장치 크기에 따라 레이아웃을 조정할 수 있습니다. 화면의 **크기** 현재 장치 크기를 분류 하는 속성입니다. 크기는 양의 정수입니다. ScreenSize 형식 가독성에 도움이 되는 명명 된 상수를 제공 합니다. 이 테이블에는 상수를 나열 합니다.

| 상수              | Value | 일반적인 장치 유형 (기본 앱 설정을 사용 하 여) |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize.Small      | 1     | 전화                                            |
| ScreenSize.Medium     | 2     | 세로 태블릿                          |
| ScreenSize.Large      | 3     | 태블릿, 가로로 보유                        |
| ScreenSize.ExtraLarge | 4     | 데스크톱 컴퓨터                                 |

이러한 크기를 사용 하 여 앱의 레이아웃에 대 한 결정을 내릴 수 있습니다. 예를 들어, phone 크기가 장치에서 볼 수 있지만 고, 그렇지 표시 되지 않도록 컨트롤을 원한다 면 컨트롤의 설정 수 **Visible** 속성을 다음이 수식:

`Parent.Size >= ScreenSize.Medium`

이 수식으로 계산 되 **true** 중간 또는 큰 크기의 경우와 **false** 그렇지 않은 경우.

화면 크기에 따라 화면 너비의 다른 부분을 차지 하는 컨트롤을 원한다 면 컨트롤의 설정 **너비** 속성을 다음이 수식:

```
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
이 수식은 3-보통 화면에서 화면 너비의 1/10 초 및 다른 모든 화면에서 화면 너비 사분기 작은 화면에서 화면 너비의 절반을 컨트롤의 너비를 설정합니다.

## <a name="custom-breakpoints"></a>사용자 지정 중단점

화면의 **크기** 속성은 화면을 비교 하 여 계산 **너비** 앱의 값으로 속성 **SizeBreakpoints** 속성입니다. 이 속성은 명명 된 화면 크기를 구분 하는 너비 중단점을 나타내는 숫자의 단일 열 테이블:

태블릿 또는 웹에 대해 만든 앱에서 앱의 기본 값 **SizeBreakpoints** 속성은 **[600, 900, 1200]** 합니다. 휴대폰에 대해 만든 앱에서 값이 **[1200, 1800, 2400]** 합니다. (이러한 앱에는 다른 앱에서 사용 되는 좌표를 효과적으로 double 좌표를 사용 하기 때문에 phone 앱에 대 한 값을 두 배가 됩니다.)

![App.SizeBreakpoints 속성의 기본값](media/create-responsive-layout/default-breakpoints.png)

앱의 값을 변경 하 여 앱의 중단점을 사용자 지정할 수 있습니다 **SizeBreakpoints** 속성입니다. 선택 **앱** 트리 뷰에서 선택 **SizeBreakpoints** 속성의 목록을 연 후 수식 입력줄에서 값을 편집 합니다. 명명 된 화면 크기에 해당 앱에 필요한 있지만 크기를 1 ~ 4 많은 중단점을 만들 수 있습니다. 수식에서 숫자 값을 기준으로 초과 ExtraLarge 크기를 참조할 수 있습니다 (5, 6, 등).

또한 더 적은 중단점을 지정할 수 있습니다. 예를 들어, 소형, 중형 및 대형 가능한 화면 크기 되도록 3 개 크기 (두 개의 중단점)만 앱 해야 할 수 있습니다.

## <a name="known-limitations"></a>알려진 제한 사항

제작 캔버스 크기 조정 수식 만든 응답 하지 않습니다. 반응 형 동작을 테스트 하려면 저장 하 고 앱을 게시 하 다음 장치에서 또는 다양 한 크기 및 방향의 브라우저 창에서 엽니다.

식 또는에서 수식을 작성 하는 경우는 **X**, **Y**합니다 **너비**, 및 **높이** 속성 컨트롤의 해당 덮어쓸 수 있습니다 식 또는 나중에 다른 위치로 컨트롤을 끌어 옵니다. 또는 컨트롤의 테두리를 끌어 크기를 조정할 경우 수식입니다.
