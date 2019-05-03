---
title: 캔버스 앱에서 반응형 레이아웃 만들기 | Microsoft Docs
description: 캔버스 앱에서 컨트롤의 높이, 너비, X 및 Y 속성을 구성하는 방법에 대한 참조 정보
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61562528"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>캔버스 앱에서 반응형 레이아웃 만들기

PowerApps의 캔버스 앱을 빌드하기 전에, 휴대폰 또는 태블릿 앱 여부를 지정합니다. 이 선택은 빌드하는 앱의 캔버스 모양과 크기를 결정합니다.

선택하고 나서, **파일** > **앱 설정** > **화면 크기 + 방향**을 선택하게 되면 몇 가지 더 많은 선택을 할 수 있습니다. 세로 또는 가로 방향 및 화면 크기(태블릿에만 해당)를 선택할 수 있습니다. 또한 가로 세로 비율 잠금 및 잠금 해제와 장치 회전 지원 여부를 선택할 수 있습니다.

이러한 선택은 화면 레이아웃 설계할 때 결정하는 다른 모든 선택의 기반이 됩니다. 다른 크기의 장치에서 또는 웹에서 앱이 실행되는 경우, 전체 레이아웃 크기는 앱이 실행하는 화면에 맞게 조정됩니다. 휴대폰을 위해 설계된 앱이 큰 브라우저 창에서 실행되는 경우, 앱의 보정을 위해 크기가 조정되고 해당 공간에 바해 지나치게 커보이게 됩니다. 앱은 더 많은 컨트롤 또는 콘텐츠를 표시하여 추가 픽셀을 활용할 수 없게 됩니다.

반응형 레이아웃을 만들게 되면, 컨트롤이 다양한 장치와 창 크기에 반응하여 다양한 환경에서 더 자연스럽게 느껴지도록 할 수 있습니다. 반응형 레이아웃을 만드려면 앱의 일부 설정을 조정하고 앱 전체에 걸쳐 식을 작성합니다. 

## <a name="disable-scale-to-fit"></a>영역 안에 맞추기 해제

앱이 실행되는 실제 공간에 해당 레이아웃이 맞게 조정되도록 각 화면을 구성할 수 있습니다.

기본적으로 켜져 있는 **영역 안에 맞추기** 설정을 해제하여 응답성을 활성화합니다. 이 설정을 해제하게 되면, 특정 화면 모양에 맞춰 디자인하지 못하기 때문에 **가로 세로 비율 고정**도 해제됩니다. (앱이 장치 회전을 지원하는지 여부는 여전히 지정할 수 있습니다.)

![확장을 사용 하지 않도록 설정에 맞게](media/create-responsive-layout/scale-to-fit-off.png)

앱이 응답성이 있게 하려면, 추가 단계를 수행해야 하지만, 해당 변경은 응답성을 만들기 위한 첫 단계입니다.

## <a name="understand-app-and-screen-dimensions"></a>앱 및 화면 크기 이해

앱의 레이아웃이 화면 크기에 대한 변경 내용에 응답하게 하려면 화면의 **Width**와 **Height** 속성을 사용하는 수식을 작성합니다. 이러한 속성을 표시하려면, PowerApps Studio에서 앱을 열고 화면을 선택합니다. 오른쪽 창의 **고급** 탭에 이러한 속성에 대한 기본 수식이 표시됩니다.

**Width** = `Max(App.Width, App.DesignWidth)`

**Height** = `Max(App.Height, App.DesignHeight)`

이 수식은 앱의 **Width**, **Height**, **DesignWidth** 및 **DesignHeight** 속성을 참조합니다. 앱의 **Width**와 **Height** 속성은 앱이 실행되는 장치 또는 브라우저 창의 크기에 해당하는 속성입니다. 사용자가 브라우저 창 크기를 조정하는 경우(또는 **방향 고정**이 해제되어 있는 장치를 회전하는 경우), 이러한 속성의 값은 동적으로 변경됩니다. 이러한 값이 변경되는 경우 화면의 **Width**와 **Height** 속성의 수식은 다시 계산됩니다.

	
**DesignWidth**와 **DesignHeight** 속성은 **앱 설정**의 **화면 크기 + 방향** 창에서 지정한 크기입니다. 예를 들어, 휴대폰 레이아웃을 세로 방향으로 선택하게 되면, **DesignWidth**은 640이며 **DesignHeight**는 1136이 됩니다.

이 값들은 화면의 **Width**와 **Height** 속성을 위한 수식에서 사용되므로, 앱을 디자인하기 위한 최소 크기로 **DesignWidth** 및 **DesignHeight**를 생각할 수 있습니다. 앱에 사용할 수 있는 실제 영역이 이러한 최소 크기보다 훨씬 작은 경우, 화면의 **Width**와 **Height** 속성의 수식은 이러한 값이 최소값보다 더 작지 않도록 합니다. 이 경우 사용자는 모든 화면의 콘텐츠를 보려면 스크롤해야 합니다.

앱의 **DesignWidth**와 **DesignHeight**를 설정한 후, (대부분의 경우) 각 화면의 **Width**와 **Height** 속성의 기본 수식을 변경하지 않아도 됩니다. 이 문서의 뒤에서 이러한 수식을 사용자 지정하려는 경우를 설명합니다.

## <a name="use-formulas-for-dynamic-layout"></a>동적 레이아웃에 대한 수식 사용

반응형 디자인을 만들려면 각 컨트롤의 크기와 위치에 절대(일정) 좌표 값 대신 수식을 사용합니다. 이러한 수식은 각 컨트롤의 위치 및 크기를 전체 화면 크기를 기준으로 또는 화면의 다른 컨트롤을 기준으로 표현합니다.

> [!IMPORTANT]
> 컨트롤의 **X**, **Y**, **Widht**와 **Height** 속성에 대한 수식을 작성한 후, 캔버스 편집기에서 컨트롤을 끌게 되면 수식은 상수 값으로 덮어쓰이게 됩니다. 수식을 사용하여 동적 레이아웃을 만들려면, 컨트롤을 끌어서 놓는 것을 하지 마세요.

가장 간단한 경우로 하나의 컨트롤로 전체 화면을 채웁니다. 이 효과를 만들려면 컨트롤의 속성을 다음 값으로 설정합니다.

| 속성      | 값            |
|--------|---------------|
| **X**      | `0`             |
| **Y**      | `0`             |
| **Width**  | `Parent.Width`  |
| **Height** | `Parent.Height` |

위 수식은 **Parent** 연산자를 사용합니다. 화면에 직접 배치되는 컨트롤에 대해 **Parent**는 화면을 가리킵니다. 이러한 속성 값을 사용하여 컨트롤은 화면의 왼쪽 위 모서리(0, 0)에 표시되고 화면과 동일한 **Width**와 **Height**를 갖게 됩니다.

이 문서의 뒷부분에서, 갤러리, 그룹 컨트롤, 구성요소와 같은 다른 컨테이너 내에서의 컨트롤의 위치에 이러한 원칙과 **Parent** 연산자를 적용합니다.

또는 컨트롤이 화면 위쪽 절반만 채우게 할 수 있습니다. 이 효과를 만들려면 다른 수식은 변경하지 않고 **Height** 속성을 **Parent.Height/2**로 설정합니다.

두 번째 컨트롤로 동일한 화면의 아래쪽 절반을 채우려면, 해당 수식을 만드는 두 개 이상의 방법을 수행할 수 있습니다. 편의상, 다음 접근 방식을 사용할 수 있습니다.

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

이렇게 구성하여 원하는 효과를 달성할 수 있지만, 컨트롤의 상대 크기를 변경하고자 하는 경우 각 수식을 편집해야 합니다. 예를 들어, 위쪽 컨트롤이 화면의 1/3을 차지하도록 하고 아래쪽 컨트롤이 아래 2/3를 채우도록 결정할 수 있습니다. 

해당 효과를 만들려면, **Upper** 컨트롤의 **Height** 속성과 **Lower** 컨트롤의 **Height** 속성을 업데이트해야 합니다**Y**. 또는, 다음 예제와 같이 **Upper** 컨트롤(및 자체)을 기준으로 **Lower** 컨트롤의 수식을 작성하는 것을 고려할 수 있습니다.


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

화면 높이를 나누는 다양한 방식을 표현하기 위해서는 이 수식에서 **Upper** 컨트롤의 **Height**의 속성만 업데이트하면 됩니다. **Lower** 컨트롤은 자동으로 이동하고 변경에 맞게 크기를 조정합니다.

이러한 수식 패턴을 사용하여 **C**라는 컨트롤과 부모 또는 형제 컨트롤인 **D** 사이의 일반적인 레이아웃 관계를 표현할 수 있습니다.

| C와 해당 부모 간의 관계 | 속성 | 수식 | 그림 |
|--|--|--|--|
| **C**는 *N*의 여백을 두고 부모의 너비를 채웁니다 | **X**| `N` | ![C의 부모 채우기 너비의 예](media/create-responsive-layout/c1.png) |
|  | **Width** | `Parent.Width - (N * 2)` |  |
| **C**는 *N*의 여백을 두고 부모의 높이를 채웁니다 | **Y** | `N` | ![C의 부모 높이 채우기의 예](media/create-responsive-layout/c2.png) |
|  | **Height** | `Parent.Height - (N * 2)` |  |
| **C**를 *N* 여백으로 부모의 오른쪽 가장자리에 맞춥니다 | **X** | `Parent.Width - (C.Width + N)` | ![부모의 가장자리에 맞게 조정하는 C의 예](media/create-responsive-layout/c3.png) |
| **C**를 *N* 여백으로 부모의 아래쪽 가장자리에 맞춥니다 | **Y** | `Parent.Height - (C.Height + N)` | ![부모의 가장자리에 맞게 조정하는 C의 예](media/create-responsive-layout/c4.png) |
| **C**를 가로 방향으로 부모의 가운데에 맞춥니다 | **X** | `(Parent.Width - C.Width) / 2` | ![가로 방향으로 부모 가운데 맞추기 C의 예](media/create-responsive-layout/c5.png) |
| **C**를 세로 방향으로 부모의 가운데에 맞춥니다 | **Y** | `(Parent.Height - C.Height) / 2` | ![부모의 세로 방향 가운데 맞추기 C의 예](media/create-responsive-layout/c6.png) |

| C 및 D 간의 관계 | 속성 | 수식 | 그림 |
|--|--|--|--|
| **C**를 **D**와 동일한 너비로 하고 **D**와 가로로 맞춥니다 | **X** | `D.X` | ![패턴의 예](media/create-responsive-layout/d1.png) |
|  | **Width**    | `D.Width` |  |
| **C**를 **D**와 같은 높이로 하고 **D**와 세로로 맞춥니다  | **Y** | `D.Y` | ![패턴의 예](media/create-responsive-layout/d2.png) |
|  | **Height** | `D.Height` |  |
| **C**의 오른쪽 가장자리를 **D**의 오른쪽 가장자리에 맞춥니다 | **X** | `D.X + D.Width - C.Width` | ![패턴의 예](media/create-responsive-layout/d3.png) |
| **C**의 아래쪽 가장자리를 **D**의 아래쪽 가장자리에 맞춥니다 | **Y** | `D.Y + D.Height - C.Height` | ![패턴의 예](media/create-responsive-layout/d4.png) |
| **C**를 **D** 기준으로 가로 방향으로 가운데에 맞춥니다 | **X** | `D.X + (D.Width - C.Width) / 2`  | ![패턴의 예](media/create-responsive-layout/d5.png) |
| **C**를 **D** 기준으로 세로 방향으로 가운데에 맞춥니다 | **Y** | `D.Y + (D.Height - C.Height) /2` | ![패턴의 예](media/create-responsive-layout/d6.png) |
| **C**를 N 간격으로 **D**의 오른쪽에 배치합니다 | **X** | `D.X + D.Width - N` | ![패턴의 예](media/create-responsive-layout/d7.png) |
| **C**를 N 간격으로 **D**의 아래쪽에 배치합니다             | **Y** | `D.Y + D.Height + N` | ![패턴의 예](media/create-responsive-layout/d8.png) |
| **C**가 **D**와 부모의 오른쪽 가장자리의 공간을 채웁니다 | **X** | `D.X + D.Width` | ![패턴의 예](media/create-responsive-layout/d9.png) |
|  | **Width** | `Parent.Width - C.X` |  |
| **C**가 **D**와 부모의 아래쪽 가장자리 사이의 공간을 채웁니다 | Y | `D.Y + D.Height` | ![패턴의 예](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>계층형 레이아웃

더 많은 컨트롤을 포함하는 화면을 생성하게 될 때 형제 컨트롤 또는 화면을 기준으로 하지 않고 부모 컨트롤을 기준으로 컨트롤을 배치하는 것이 보다 더 편리합니다(또는 필요할 수 있습니다). 계층 구조로 컨트롤을 구성하면, 수식을 쉽게 작성하고 유지 관리할 수 있습니다.

### <a name="galleries"></a>갤러리

앱에서 갤러리를 사용하는 경우, 갤러리의 템플릿 내에 컨트롤을 배치해야 합니다. 갤러리 템플릿을 참조하는 **Parent** 연산자를 사용하는 수식을 작성하여 이러한 컨트롤을 배치할 수 있습니다. 갤러리 템플릿 내 컨트롤의 수식에 **Parent.TemplateHeight** 및 **Parent.TemplateWidth** 속성을 사용합니다. 갤러리의 전체 크기를 나타내는 **Parent.Width** 및 **Parent.Height**를 사용하지 마세요.

![세로 갤러리 템플릿 너비와 높이 표시 합니다.](media/create-responsive-layout/gallery-vertical.png)

### <a name="enhanced-group-control"></a>향상된 그룹 컨트롤

부모 컨트롤로 향상된 **그룹** 컨트롤의 실험적 기능을 사용할 수 있습니다. 이 기능을 켜려면 **파일** > **앱 설정** > **고급 설정**을 선택합니다.

화면 맨 위에 있는 머리글의 예를 살펴보세요. 머리글에는 일반적으로 제목과 사용자와 상호 작용할 수 있는 여러 아이콘이 있습니다. **레이블** 컨트롤과 두 **아이콘** 컨트롤을 포함하는 향상된 **그룹** 컨트롤을 사용하여 이러한 머리글을 생성할 수 있습니다.

![그룹을 사용 하는 헤더 예제](media/create-responsive-layout/header-group.png)

이러한 컨트롤에 대한 속성을 다음 값으로 설정합니다.

| 속성 | Header | Menu | Close | Title |
|--|--|--|--|--|
| **X** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **Y** | `0` | `0` | `0` | `0` |
| **Width**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Height** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

**Header** 컨트롤의 경우 `Parent`는 화면을 가리킵니다. 다른 컨트롤의 경우 `Parent`는 **Header** 컨트롤을 가리킵니다.

이러한 수식을 작성하였으므로, 해당 속성에 대한 수식을 변경하여 **Header** 컨트롤의 크기 또는 위치를 조정할 수 있습니다. 자식 컨트롤의 위치와 크기는 자동으로 적절하게 조정됩니다.

### <a name="components"></a>구성 요소

Components로 명명된 다른 실험적 기능을 사용하는 경우, 빌딩 블록을 생성할 수 있으며 앱 전체에서 재사용할 수 있습니다. **그룹** 컨트롤과 마찬가지로, 구성 요소 내에 배치한 컨트롤은 크기와 위치 수식을 구성 요소의 크기를 참조하는 `Parent.Width` 및 `Parent.Height`를 기준으로 해야 합니다. 자세한 정보: [구성 요소를 만드는](create-component.md)

## <a name="adapting-layout-for-device-size-and-orientation"></a>장치 크기 및 방향에 대한 레이아웃 조정

지금까지 수식을 사용하여 서로를 기준으로 상대적으로 정렬된 컨트롤을 유지하며 사용 가능한 공간에 반응하여 각 컨트롤의 크기를 변경하는 방법을 알아보았습니다. 하지만 다른 장치 크기 및 방향에 반응하는 더 많은 레이아웃 변경이 필요하거나 이를 원할 수 있습니다. 장치를 세로 방향에서 가로 방향으로 회전할 때, 수직 레이아웃을 수평 레이아웃으로 전환하기를 원할 수 있습니다. 더 큰 장치에서는 더 많은 콘텐츠를 제공할 수도 있고 보다 매력적 레이아웃을 제공하도록 다시 정렬할 수 있습니다. 더 작은 장치에서는 여러 화면으로 콘텐츠를 분할해야 합니다.

### <a name="device-orientation"></a>장치 방향

앞에서 설명한 화면의 **Width**와 **Height** 속성의 기본 수식은 사용자가 장치를 회전한다면 제대로 된 결과를 제공하지 않습니다. 예를 들어, 세로 방향으로 휴대폰을 위해 설계된 앱은 **DesignWidth**이 640, **DesignHeight**이 1136이 됩니다. 가로 방향 휴대폰에서 동일한 앱에는 다음 속성 값이 적용됩니다.

- 화면의 **Width** 속성을 `Max(App.Width, App.DesignWidth)`로 설정합니다. 앱의 **Width**(1136)는 해당 **DesignWidth**(640)보다 큽니다. 따라서 수식은 1136으로 계산됩니다.
- 화면의 **Height** 속성을 `Max(App.Height, App.DesignHeight)`로 설정합니다. 앱의 **Height**(640)는 해당 **DesignHeight**(1136)보다 작습니다. 그러므로 수식은 1136으로 계산됩니다.

화면의 **Height**는 1136이고 장치 높이(이 방향에서)는 640이므로, 사용자는 모든 컨텐츠를 표시하려면 세로로 화면을 스크롤해야 하므로 이는 사용자가 원하는 경험이 아닐 수 있습니다.

화면의 **Width**와 **Height** 속성을 장치 방향에 맞도록 하려면, 다음 수식을 사용할 수 있습니다.

**Width** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Height** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

이러한 수식은 장치의 너비가 높이가 작은지(세로 방향) 높이보다 작은지(가로 방향) 여부에 따라 앱의 **DesignWidth**와 **DesignHeight**를 교환합니다.

화면의 **Width**와 **Height** 수식을 조정한 후, 사용 가능한 공간을 더욱 효율적으로 사용하기 위해 화면 내에서 컨트롤을 다시 정렬할 수 있습니다. 예를 들어, 화면의 절반을 두 컨트롤이 차지하는 경우, 세로 방향일 때는 컨트롤을 수직으로 쌓지만 가로 방향일 때는 나란히 정렬할 수 있습니다.

화면을 사용할 수 있습니다 **방향을** 가로 또는 세로로 화면 방향 인지 확인 하는 속성입니다.

> [!NOTE]
> 가로 방향에서는 **Upper**와 **Lower** 컨트롤이 왼쪽 및 오른쪽 컨트롤로 표시됩니다.

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

| 상수              | 값 | 일반적인 장치 유형 (기본 앱 설정을 사용 하 여) |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize.Small      | 1     | 전화                                            |
| ScreenSize.Medium     | 2     | 세로 태블릿                          |
| ScreenSize.Large      | 3     | 태블릿, 가로로 보유                        |
| ScreenSize.ExtraLarge | 4     | 데스크톱 컴퓨터                                 |

이러한 크기를 사용 하 여 앱의 레이아웃에 대 한 결정을 내릴 수 있습니다. 예를 들어, phone 크기가 장치에서 볼 수 있지만 고, 그렇지 표시 되지 않도록 컨트롤을 원한다 면 컨트롤의 설정 수 **Visible** 속성을 다음이 수식:

`Parent.Size >= ScreenSize.Medium`

이 수식으로 계산 되 **true** 중간 또는 큰 크기의 경우와 **false** 그렇지 않은 경우.

화면 크기에 따라 화면 너비의 다른 부분을 차지 하는 컨트롤을 원한다 면 컨트롤의 설정 **Width** 속성을 다음이 수식:

```powerapps-dot
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
이 수식은 3-보통 화면에서 화면 너비의 1/10 초 및 다른 모든 화면에서 화면 너비 사분기 작은 화면에서 화면 너비의 절반을 컨트롤의 너비를 설정합니다.

## <a name="custom-breakpoints"></a>사용자 지정 중단점

화면의 **크기** 속성은 화면을 비교 하 여 계산 **Width** 앱의 값으로 속성 **SizeBreakpoints** 속성입니다. 이 속성은 명명 된 화면 크기를 구분 하는 너비 중단점을 나타내는 숫자의 단일 열 테이블:

태블릿 또는 웹에 대해 만든 앱에서 앱의 기본 값 **SizeBreakpoints** 속성은 **[600, 900, 1200]** 합니다. 휴대폰에 대해 만든 앱에서 값이 **[1200, 1800, 2400]** 합니다. (이러한 앱에는 다른 앱에서 사용 되는 좌표를 효과적으로 double 좌표를 사용 하기 때문에 phone 앱에 대 한 값을 두 배가 됩니다.)

![App.SizeBreakpoints 속성의 기본값](media/create-responsive-layout/default-breakpoints.png)

앱의 값을 변경 하 여 앱의 중단점을 사용자 지정할 수 있습니다 **SizeBreakpoints** 속성입니다. 선택 **앱** 트리 뷰에서 선택 **SizeBreakpoints** 속성의 목록을 연 후 수식 입력줄에서 값을 편집 합니다. 명명 된 화면 크기에 해당 앱에 필요한 있지만 크기를 1 ~ 4 많은 중단점을 만들 수 있습니다. 수식에서 숫자 값을 기준으로 초과 ExtraLarge 크기를 참조할 수 있습니다 (5, 6, 등).

또한 더 적은 중단점을 지정할 수 있습니다. 예를 들어, 소형, 중형 및 대형 가능한 화면 크기 되도록 3 개 크기 (두 개의 중단점)만 앱 해야 할 수 있습니다.

## <a name="known-limitations"></a>알려진 제한 사항

제작 캔버스는 크기 조정 수식에 응답하지 않습니다. 반응형 동작을 테스트하려면, 앱을 저장하고 게시한 다음 다양한 크기 및 방향의 장치나 브라우저 창에서 엽니다.

컨트롤의 **X**, **Y**, **Width** 및 **Height** 속성에 식이나 수식을 작성하는 경우, 이후에 다른 위치로 컨트롤을 끌거나 컨트롤의 테두리를 끌어 크기를 조정하는 경우 해당 식이나 수식을 덮어쓰게 됩니다.
