---
title: '컨테이너 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯 한 컨테이너 컨트롤에 대 한 정보
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 9/20/2019
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8456e82cfd2680fcbb722c8b4b2b5b32ef73dbde
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540289"
---
# <a name="container-control-in-powerapps-experimental"></a>PowerApps의 컨테이너 컨트롤 (실험적)
계층을 만드는 기능을 제공 합니다.

> [!IMPORTANT]
> 이는 실험적 기능입니다. 실험적 기능은 급진적으로 변하거나 언제라도 완전히 사라질 수 있습니다.
> 자세한 내용은 [PowerApps의 실험적 및 미리 보기 기능 이해](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview)를 참조 하세요.

## <a name="description"></a>설명
 컨테이너는 컨트롤 집합을 보유할 수 있으며 고유한 속성을 가집니다. 

빈 컨테이너를 삽입 한 다음 컨트롤을 추가 하 고, 크기를 조정 하 고, 개체를 숨기고, 다른 변경을 수행 하 여 사용자 지정할 수 있습니다. 여러 컨트롤에서 시작 하 고, 선택 하 고, 트리 뷰의 상황에 맞는 메뉴를 통해 컨테이너에 추가 하거나, 캔버스를 마우스 오른쪽 단추로 클릭할 수도 있습니다. 

## <a name="properties"></a>속성
**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다. 

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다. 


## <a name="known-limitations"></a>알려진 제한 사항

컨테이너는 캔버스 구성 요소 또는 폼 내에서 작동 하지 않습니다. 

## <a name="frequently-asked-questions"></a>질문과 대답

**컨테이너와 그룹 간의 차이점은 무엇 인가요?**
제작 그룹은 컨트롤 주위를 이동 하 고 그룹 내에서 컨트롤의 유사한 속성을 대량으로 편집 하는 데 사용 되는 간단한 개념입니다. 제작 그룹은 앱의 레이아웃에 영향을 주지 않습니다. 

이전에 실험적에서 제공 된 컨테이너 컨트롤은 향상 된 그룹으로 이름이 바뀐 제작 그룹의 대체 항목으로 제공 됩니다. 경량 제작 그룹과 추가 속성이 있는 strutured container 컨트롤 모두에 값이 있으므로 컨테이너 컨트롤로 이름이 변경 되었습니다. 

