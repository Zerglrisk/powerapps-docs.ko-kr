---
title: 액세스 가능한 캔버스 앱 만들기 | Microsoft Docs
description: 장애가 있는 사용자가 캔버스 앱에 액세스할 수 있도록 하는 방법
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9f80332a490289cc5b59de7131d1c2b2483633e1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725312"
---
# <a name="create-accessible-canvas-apps-in-power-apps"></a>Power Apps에서 액세스 가능한 캔버스 앱 만들기
액세스 가능한 캔버스 앱에서는 시각, 청각 및 기타 장애가 있는 사용자가 앱을 사용할 수 있습니다.  여러 정부 및 조직의 요구 사항인 점을 별개로 하더라도 아래 지침을 따르면 사용자의 능력에 상관없이 모든 사용자의 사용 편의성이 개선됩니다.

**[접근성 검사기](accessibility-checker.md)** 를 사용하여 앱의 잠재적인 접근성 문제를 검토하십시오. 

## <a name="layout-and-color"></a>레이아웃 및 색
상식적이고 복잡하지 않은 디자인을 사용하면 모든 사용자가 앱에 쉽게 액세스하는 데 도움이 됩니다.  앱의 사용자 지정을 많이 수행하는 경우 아래 제안 사항에 유의하세요.  Power Apps 테마는 기본적으로 액세스할 수 있습니다.
- 모든 요소가 명확하게 표시되고 텍스트가 충분한 크기인지 확인하세요.  모든 콘텐츠를 육안으로 쉽게 읽고 이해할 수 있어야 합니다.
- 항목의 표시 유형 속성을 사용하여 요소를 표시하지 마세요.  조건부로 표시해야 하는 항목이 있으면 새 화면에서 콘텐츠를 만들고 해당 화면으로 이동한 후 되돌아오세요.
- 화면에서 입력 요소에 레이블이 지정되어 있어야 합니다. **[AccessibilityLabel](controls/properties-accessibility.md)** 속성은 화면 판독기가 알릴 내용을 정의합니다.
- 색을 사용자 지정할 경우 텍스트:배경의 대비가 4.5:1 이상이어야 합니다.  이 프로세스를 지원하는 소프트웨어 도구를 바로 사용할 수 있습니다.
- 상하와 좌우로 읽을 때 레이아웃이 논리 흐름에 맞는지 확인하세요.


## <a name="keyboard-support"></a>키보드 지원
앱 접근성을 테스트할 때는 iOS 및 Android의 접근성 모드에서 키보드만으로 앱을 사용할 수 있는지 확인하고, 화면 판독기를 사용하도록 설정하고 앱을 탐색할 수 있는지도 확인하세요.

화면 판독기 사용 여부와 관계없이 키보드 탐색을 위해서는 각 컨트롤의 **[TabIndex](controls/properties-accessibility.md)** 속성을 설정하여 Tab 키를 사용하여 입력 필드로 이동할 때 논리적 순서를 따라야 합니다.
- 레이블, 이미지, 아이콘, 모양 컨트롤-대화형 요소 (예: 단추)를 나타내면 TabIndex를 0으로 설정 합니다. 장식 요소나 텍스트인 경우 TabIndex를-1로 설정 합니다.
- 탭 인덱스를 0보다 크게 설정하지 마세요.

## <a name="screen-reader-support"></a>화면 판독기 지원
다음 소프트웨어 조합은 화면 판독기로 Power Apps를 사용 하는 데 지원 되는 권장 사항입니다.

- **Windows**: Microsoft Edge/내레이터
- **macOS**: Safari/VoiceOver
- **Android**: Power Apps 앱/Talkback
- **iOS**: Power Apps 앱/VoiceOver

만족스러운 화면 판독기 환경을 위해서는 다음을 수행하는 것이 좋습니다.

- 모든 입력 컨트롤의 **[AccessibilityLabel](controls/properties-accessibility.md)** 속성을 설정해야 합니다.
- 이미지의 경우 **[AccessibilityLabel](controls/properties-accessibility.md)** 을 적절한 설명으로 설정합니다.
  - 사진이 단추 또는 링크로 사용되지 않고(즉, 아이콘이 장식용으로만 사용됨) 화면 판독기에서 일지 않아야 하는 경우 **[AccessibilityLabel](controls/properties-accessibility.md)** 이 비어 있거나 설정되어 있지 않아야 합니다.
  - 사진이나 아이콘이 단추로 사용되는 경우에는 **[TabIndex](controls/properties-accessibility.md)** 를 0으로, **[AccessibilityLabel](controls/properties-accessibility.md)** 을 링크 설명으로 설정합니다.


## <a name="multimedia"></a>멀티미디어
모든 비디오에 자막이 있고 모든 오디오 녹음의 대본이 사용자에게 제공되는지 확인합니다.  **비디오** 컨트롤은 **ClosedCaptionsUrl** 속성을 통해 WebVTT 형식의 폐쇄 캡션을 지원 합니다.

화면 판독기를 사용하도록 설정한 경우 **타이머**에서 단추 텍스트를 알리지 않지만 경과된 시간은 알립니다.  타이머가 낮은 불투명도로 숨겨진 경우에도 알림을 끌 수 없습니다.

## <a name="working-with-signatures"></a>서명 작업
PenInput 컨트롤을 사용하는 서명 필드가 있는 경우 서명 입력의 대체 방법을 사용하도록 설정해야 합니다.  이 경우 사용자가 이름을 입력할 수 있는 TextInput 컨트롤을 표시하는 것이 좋습니다.  서명 지침은 **[AccessibilityLabel](controls/properties-accessibility.md)** 속성에 배치되고 컨트롤은 펜 입력 옆 즉, 오른쪽이나 바로 아래에 배치됩니다.



관련:
- [접근성 속성](controls/properties-accessibility.md)
- [접근성 검사기 사용](accessibility-checker.md)
- [Power Apps에서 액세스할 수 있는 색](accessible-apps-color.md)
