---
title: Canvas 앱에 대 한 내게 필요한 옵션 속성 | Microsoft Docs
description: TabIndex 및 Tooltip과 같은 속성에 대 한 참조 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2c11e05c93d5a505408948178bf3efbd31f2dbf7
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986161"
---
# <a name="accessibility-properties-for-canvas-apps"></a>Canvas 앱에 대 한 내게 필요한 옵션 속성

장애가 있는 사용자에게 적합한 컨트롤과 상호 작용하는 다른 방법을 지원하는 속성의 구성입니다.

## <a name="properties"></a>속성

**AccessibleLabel** – 화면 읽기 프로그램의 레이블입니다. 이미지, 아이콘 및 셰이프 컨트롤에 대한 값이 비어 있으면 컨트롤이 화면 판독기에서 보이지 않고 장식으로 처리됩니다.

**라이브** – 화면 읽기 프로그램이 콘텐츠 변경 내용을 알리는 방법입니다. **[레이블](control-text-box.md)** 컨트롤에만 사용할 수 있습니다.

* **Off**로 설정 하면 화면 판독기가 변경 내용을 알리지 않습니다.
* **처리 완료 후**로 설정 되 면 화면 판독기가 말하는 동안 발생 한 변경 내용을 알리기 전에 화면 판독기가 말하기를 마칩니다.
* **Assertive**로 설정 되 면 화면 판독기에서 화면 판독기가 말하는 동안 발생 한 모든 변경 내용을 알리기 위해 자체적으로 중단 됩니다.

[라이브 지역에서 동적 변경을 발표](../accessible-apps-live-regions.md)하는 방법에 대해 알아봅니다.

**TabIndex** – 컨트롤이 키보드 탐색에 참여 하는지 여부를 결정 합니다.

키보드 탐색은 모든 앱의 중요 한 측면입니다.  터치 나 마우스를 사용 하는 것 보다 많은 키보드를 사용 하는 것이 더 효율적 이며 시각적으로 손상 된 화면 판독기를 사용할 수 있습니다.  탐색 순서는 다음과 같아야 합니다.
- 시각적으로 표시 되는 내용을 미러링합니다.
- 대화형 인 컨트롤에는 탭 정지만 있습니다.
- 직관적인 전체를 수행 하 고 "Z" 순서 또는 아래쪽으로 이동 하 여 "역방향-N" 순서를 따릅니다.

위의 요구 사항은 기본 **TabIndex** 값을 사용 하 여 충족 되며 변경 하지 않는 것이 좋습니다.  기본값은 대부분의 사용자가 시각적으로 필요로 하며 화면 판독기에서 잘 작동 하는 것입니다.  그러나 기본값을 재정의 하는 경우가 있을 수 있습니다.  **TabIndex** 속성 및 [ **고급 그룹** 컨트롤](https://powerapps.microsoft.com/en-us/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) (실험적)을 사용 하 여 탐색 순서를 조정 합니다.  

**TabIndex** 속성에는 두 가지 권장 값이 있습니다.

| TabIndex 값 | 동작 | 기본 |
|----------------|----------|-------------|
| 0 | 컨트롤이 키보드 탐색에 참여 합니다. | [**단추**](control-button.md), [**텍스트 입력**](control-text-input.md), [**콤보 상자**](control-combo-box.md)및 기타 일반적으로 대화형 컨트롤입니다. |
| &minus;1 | 컨트롤이 키보드 탐색에 참여 하지 않습니다. | [**레이블**](control-text-box.md), [**이미지**](control-image.md), [**아이콘**](control-shapes-icons.md)및 기타 일반적으로 비 대화형 컨트롤입니다. |

탐색 순서는 일반적으로 왼쪽에서 오른쪽으로 이동한 다음 위쪽에서 아래쪽으로 "Z" 패턴으로 이동 합니다. 순서는 컨트롤의 **X** 및 **Y** 속성 값을 기반으로 합니다. 예를 들어 타이머 나 기타 컨트롤을 기반으로 **X** 또는 **Y** 에 대 한 수식을 사용 하 여 컨트롤이 화면에서 동적으로 이동 하는 경우 탐색 순서는 동적으로 변경 됩니다.

[ **고급 그룹** 컨트롤](https://powerapps.microsoft.com/en-us/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) (실험적)을 사용 하 여 함께 탐색 해야 하는 컨트롤을 번들로 가져오거나 "역방향 N" 패턴으로 열을 만들 수 있습니다.  다음 예의 맨 위에는 이름 필드가 확장 된 그룹 컨트롤 내에 포함 되어 있으므로 이동 하기 전에 탐색을 계속 진행 합니다.  예의 맨 아래에는 그룹 컨트롤이 사용 되지 않으며,이 경우에는 컨트롤 그룹화를 사용 하 여 직관적이 지 않으며 정상적으로 탐색이 진행 됩니다. 

![위로 이동 하기 전에 그룹 내에서 탐색을 수행 하는 향상 된 그룹 컨트롤을 보여 주는 애니메이션](media/properties-accessibility/enhanced-group.gif)

마찬가지로, [**양식**](control-form-detail.md) 및 [**갤러리**](control-gallery.md) 컨트롤과 같은 컨테이너 간을 이동 하는 것은 컨테이너 외부의 다음 컨트롤로 진행 하기 전에 컨테이너의 모든 요소를 탐색 합니다.  

**표시** 속성 값이 *false* 이거나 **DisplayMode** 속성 값이 **Disabled** 인 컨트롤은 탐색에 포함 되지 않습니다.  

브라우저를 사용 하는 경우 화면의 마지막 컨트롤에서 탐색 하면 URL 주소와 같은 브라우저의 기본 제공 컨트롤로 이동 합니다.  

> [!WARNING]
> 0 보다 큰 **TabIndex** 값을 사용 하지 마십시오. 궁극적으로 컨트롤은 W3C에도 "작성자가 이러한 값을 사용 하지 않는 것이 좋습니다." 라는 [경고](https://www.w3.org/TR/wai-aria-practices/#kbd_general_between) 를 표시 하는 HTML로 렌더링 됩니다. 많은 HTML 도구는 "화면 항목의 순서 확인"을 보고할 때 [앱 검사기](../accessibility-checker.md) 에서 0 보다 큰 값에 대해 경고 합니다.  좋은 이유: 이러한 방식으로 **TabIndex** 를 사용 하는 것은 매우 어려울 수 있으며 화면 판독기와 같은 보조 기술을 사용할 수 없게 만들 수 있습니다.
> 
> **Tabindex** 가 0 보다 큰 컨트롤이 있으면 사용자가 **tabindex** 값이 늘어나는 컨트롤 (1, 다음 2 등)로 이동 합니다. 사용자가 양의 **tabindex** 값이 있는 모든 컨트롤을 탐색 한 후에는 브라우저의 기본 제공 컨트롤을 포함 하 여 0의 **TabIndex** 를 사용 하 여 컨트롤을 탐색 합니다. 동일한 **TabIndex**를 사용 하는 컨트롤이 여러 개 있는 경우 해당 **X** 및 **Y** 위치는 상대적 순서를 결정 합니다.





