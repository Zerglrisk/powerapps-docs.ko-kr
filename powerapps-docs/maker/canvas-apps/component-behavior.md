---
title: 구성 요소에 대 한 동작 수식 | Microsoft Docs
description: 구성 요소 기반 작업이 수행 될 때 하나 이상의 작업을 수행 하는 앱을 트리거하십시오.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7275395a4c21afaebc60e9635461afc08f5e84a0
ms.sourcegitcommit: afe958805d8e1cfa4fdf02c7bceea947185f71f2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66420317"
---
# <a name="behavior-formulas-for-components"></a>구성 요소에 대 한 동작 수식

> [!IMPORTANT]
> 이 기능은 여전히 실험적이며 기본적으로 비활성화됩니다. 자세한 내용은 [실험적 및 미리 보기 기능](working-with-experimental.md)을 확인합니다.

하나 이상을 지정할 [동작 수식](working-with-formulas-in-depth.md) 이벤트가 변경 구성 요소 인스턴스를 트리거할 때 실행 되는 합니다. 예를 들어 구성 요소를 설정 **OnReset** 경우 입력, 지우기 및 다시 설정, 초기화를 수행 하는 하나 이상의 수식 속성 값을 **재설정** 함수는 구성 요소 인스턴스에서 실행 합니다.

## <a name="onreset"></a>OnReset ##

선택한 구성 요소를 사용 하 여 선택할 **OnReset** 속성 (오른쪽에 있는 수식 입력줄)를 드롭다운 목록에서 하나 이상의 수식을 입력 합니다.

> [!div class="mx-imgBorder"]
> ![OnReset 예제](./media/component-behavior/example-onreset.png)

테스트할 **OnReset**, 구성 요소를 다시 설정 하기 위한 컨트롤을 구성 합니다. 예를 들어 설정 된 **OnSelect** 속성을 다음이 수식으로 단추: **Reset**(*ComponentName*)

> [!div class="mx-imgBorder"]
> ![다시 설정 단추](./media/component-behavior/reset-button.png)
