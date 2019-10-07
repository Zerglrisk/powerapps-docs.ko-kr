---
title: '펜 입력 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 펜 입력 컨트롤에 관한 정보
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1600f765e40849b47cb41b29c5d4c3fab86b4caf
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993388"
---
# <a name="pen-input-control-in-powerapps"></a>PowerApps의 펜 입력 컨트롤
사용자가 그리고 삭제하고 이미지의 영역을 강조 표시할 수 있는 컨트롤입니다.

## <a name="description"></a>설명
사용자는 이 컨트롤을 화이트보드처럼 사용하여 입력된 텍스트로 변환할 수 있는 다이어그램을 그리고 단어를 쓸 수 있습니다.

## <a name="key-properties"></a>주요 속성
**Image** – 최종 사용자가 그린 이미지를 나타내는 출력 속성입니다.

**[Color](properties-color-border.md)** – 입력 스트로크의 색입니다.

**Mode** – 컨트롤이 **그리기** 또는 **삭제** 모드 상태입니다.  선택 모드는 사용되지 않습니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 컨트롤의 목적과 대체 입력 방법을 설명하는 데 사용할 수 있습니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**Input** - **사용되지 않음.** 입력 기능이 마우스, 펜 또는 터치 입력을 지원하는지 여부입니다.  기본값(7)은 세 가지를 모두 지원합니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**[SelectionColor](properties-color-border.md)** – 목록에서 선택한 항목의 텍스트 색 또는 펜 컨트롤에 있는 선택 도구의 색입니다.

**SelectionThickness** – 펜 입력 컨트롤에 대한 선택 도구의 두께입니다.

**ShowControls** - 오디오 또는 비디오 플레이어에서 재생 단추, 볼륨 슬라이더 등을 표시하는지 및 펜 컨트롤에서 그리기, 삭제 및 지우기 아이콘 등을 표시하는지 여부입니다.

**[Size](properties-text.md)** -컨트롤에 표시되는 텍스트의 글꼴 크기입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 위쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 위쪽 가장자리 사이의 거리입니다.

## <a name="related-functions"></a>관련된 함수
[**Collect**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>예
### <a name="create-a-set-of-images"></a>이미지 집합 만들기
1. **펜 입력** 컨트롤을 추가하고 이름을 **MyDoodles**로 지정한 다음, **ShowControls** 속성을 **true**로 설정합니다.
   
    [컨트롤을 추가, 이름을 지정하고, 구성](../add-configure-controls.md)하는 방법을 모르시나요?
2. **[단추](control-button.md)** 컨트롤을 추가하고 **MyDoodles** 아래로 이동하며 **추가**를 표시하도록 **[단추](control-button.md)** 컨트롤의 **[Text](properties-core.md)** 속성을 설정합니다.
3. **[단추](control-button.md)** 컨트롤의 **[OnSelect](properties-core.md)** 속성을 이 수식으로 설정합니다.<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. **이미지 갤러리** 컨트롤을 추가하고 **[단추](control-button.md)** 컨트롤 아래로 이동한 다음, 세 개 항목이 표시될 때까지 **이미지 갤러리** 컨트롤의 너비를 축소합니다.
5. **이미지 갤러리** 컨트롤의 **[항목](properties-core.md)** 속성을 **Doodles**로 설정하고 F5 키를 누릅니다.
6. **MyDoodles**에서 이미지를 그리고, **[단추](control-button.md)** 컨트롤을 클릭하거나 탭합니다.
   
    사용자가 그린 이미지가 **이미지 갤러리** 컨트롤에 나타납니다.
7. (선택 사항) **펜 입력** 컨트롤에서 아이콘을 클릭하거나 탭하여 그린 이미지를 지우고 다른 이미지를 그린 다음, **[버튼](control-button.md)** 컨트롤을 클릭하거나 탭합니다.
8. **이미지 갤러리** 컨트롤에서 **[이미지](control-image.md)** 컨트롤의 **[OnSelect](properties-core.md)** 속성을 이 서식으로 설정합니다.<br>
   **Remove(Doodles, ThisItem)**
9. **이미지 갤러리** 컨트롤에서 클릭하거나 탭하여 드로잉을 제거합니다.

**[SaveData](../functions/function-savedata-loaddata.md)** 함수를 사용하여 드로잉을 로컬에서 저장하거나, **[Patch](../functions/function-patch.md)** 함수를 사용하여 데이터 원본에 저장합니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **[BorderColor](properties-color-border.md)** 및 컨트롤 외부 색(테두리가 있는 경우)
* **[Fill](properties-color-border.md)** 및 컨트롤 외부 색(테두리가 없는 경우)

### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

    > [!IMPORTANT]
  > 화면 읽기 프로그램 사용자는 **펜 입력**에 액세스할 수 없습니다. 항상 대체 입력 양식을 제공하세요. 예를 들어 스케치가 필요한 경우 사용자가 이미지를 업로드할 수 있는 **[그림 추가](control-add-picture.md)** 컨트롤을 추가하는 것이 좋습니다. 두 가지 방법을 모두 제공할 수 있고 사용자가 더 익숙한 방법을 선택할 수 있습니다.

### <a name="keyboard-support"></a>키보드 지원

> [!IMPORTANT]
> 키보드 사용자는 **펜 입력**에 액세스할 수 없습니다. 항상 대체 입력 양식을 제공하세요. 예를 들어 서명이 필요한 경우 사용자가 이름을 입력할 수 있는 **[텍스트 입력](control-text-input.md)** 을 추가하는 것이 좋습니다. 두 가지 방법을 모두 제공할 수 있고 사용자가 더 익숙한 방법을 선택할 수 있습니다.
