---
title: 구성 요소에 대 한 동작 수식 | Microsoft Docs
description: 구성 요소 기반 작업이 발생할 때 하나 이상의 작업을 수행 하도록 앱을 트리거합니다.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8ec4edd835f12fb6fccf04ba0fb27f1e755cac0
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310053"
---
# <a name="behavior-formulas-for-components"></a>구성 요소에 대 한 동작 수식

> [!IMPORTANT]
> 이 기능은 여전히 실험적이며 기본적으로 비활성화됩니다. 자세한 내용은 [실험적 및 미리 보기 기능](working-with-experimental.md)을 확인합니다.

이벤트에서 구성 요소 인스턴스의 변경을 트리거할 때 실행 되는 하나 이상의 [동작 수식을](working-with-formulas-in-depth.md) 지정 합니다. 예를 들어 구성 요소의 **Onreset** 속성을 초기화를 수행 하 고, 입력을 지우고, **다시** 설정 함수가 구성 요소 인스턴스에서 실행 될 때 값을 다시 설정 하는 하나 이상의 수식으로 설정 합니다.

## <a name="onreset"></a>OnReset

구성 요소가 선택 된 상태에서 수식 입력줄의 오른쪽에 있는 속성의 드롭다운 목록에서 **Onreset** 을 선택 하 고 하나 이상의 수식을 입력 합니다.

> [!div class="mx-imgBorder"]
> ![OnReset 예제](./media/component-behavior/example-onreset.png)

**Onreset**을 테스트 하려면 구성 요소를 다시 설정 하도록 컨트롤을 구성 합니다. 예를 들어 단추의 **Onselect** 속성을 다음 수식으로 설정 합니다. **다시 설정** (*ComponentName*)

> [!div class="mx-imgBorder"]
> ![다시 설정 단추](./media/component-behavior/reset-button.png)
