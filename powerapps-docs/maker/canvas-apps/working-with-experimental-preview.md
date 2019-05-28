---
title: 미리 보기 및 실험적 기능 이해 | Microsoft Docs
description: 새 기능을 테스트하고 도입하기 시작합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/20/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 50785382404496c7409eab1b545fdc0b2d930d44
ms.sourcegitcommit: 8bad6bff1b3397b21654df4a9357dd0180fbcfe6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65048432"
---
# <a name="understand-experimental-and-preview-features-in-powerapps"></a>PowerApps에서 실험적 및 미리 보기 기능 이해

모든 릴리스마다 PowerApps를 사용자의 요구 사항에 맞는 최상의 도구로 만들기 위해 변경 사항을 적용하고 기능을 추가합니다. 제품을 발전시켜 나갑니다.  

이전 버전과의 호환성을 매우 진지하게 다룹니다. 그러나 변경 또는 개선으로, 의도하지 않은 부작용이 초래되어 앱이 예전과 똑같이 작동하지 않을 수 있습니다.

개선과 기존 앱에 미치는 영향 간의 균형을 이루기 위해 규모가 큰 기능은 여러 단계를 진행합니다. 이 문서에서는 이러한 프로세스와 개발 중인 기능에 대한 사용자 노출을 제어할 수 있는 방법을 설명합니다.

## <a name="feature-roll-out-stages"></a>기능 롤아웃 단계

기능은 해당 제품의 공식적인 부분이 되기 위해 세 단계를 거칩니다.

1. **실험적**:  이 기능은 진행 중인 작업입니다. 상당한 변화가 있을 수 있으며 아직 신뢰할 수 없습니다.
1. **미리 보기**:  이 기능은 거의 완성되었으며 안정적입니다. 기존 앱을 지금 마이그레이션하기 시작합니다.
1. **탑재**:  이 기능은 완성되었습니다. 모든 앱에서 이 기능이 활성화되었으며 해제할 수 없습니다.

각 단계에서 이 기능을 사용하는 사용자 수가 증가하여 이 기능이 사용자에게 필요한 것이며, 의도하지 않은 부작용을 초래하지 않고 있음을 검증하는 데 도움이 됩니다.

**사용자의 피드백은 이 프로세스에서 중요합니다.**  [PowerApps 커뮤니티 포럼](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)에 피드백을 올려 주세요.

각 단계에서 기능은 얼마나 유지되나요? 기능에 따라 다릅니다. 해당 기능을 사용하는 앱의 수, 보고된 문제의 수는 물론, 이 기능이 얼마나 긴급하게 필요한지 등 많은 요소를 살펴 봅니다. 기능은 한 단계에서 몇 주에서 수개월까지 유지될 수 있습니다.

이 표는 사용자가 기능 사용 시기를 결정하는 데 도움이 될 수 있습니다. 

| 단계 | 언제 사용 해야 하나요? | 확신을 가지고 사용할 수 있나요? | 새 앱에 기본적으로 사용 설정되어 있나요? | 
|----|----|----|-----|------|
| **실험적** | 얼리 어답터인 경우 유용한 무엇인가가 보이고 기능 테스트에 도움이 되길 원합니다. | 아니요.  실험적 기능은 급진적으로 변하거나 언제라도 완전히 사라질 수 있습니다. | 아니요. 기능에 대해 명시적으로 옵트인해야 합니다.  |  
| **미리 보기** | 새 앱은 이 기능을 자동으로 포함합니다.  이 기능은 결국에는 사용 설정될 것이므로 기존 앱에서 활성화하고 테스트를 시작합니다. | 예. 이 기능은 해당 제품의 영구적인 부분이 되고 있습니다.  | 예. 문제가 발생할 경우 해제할 수도 있습니다.  문제를 보고해 주세요. 문제가 있을 수 있다는 것이 이 기능이 미리 보기 단계인 주요 이유입니다. | 
| **탑재**(**고급 설정**에 더 이상 나타나지 않음) | 모든 앱에 이 기능이 있습니다. | 예. | 예.  대부분을 사용하지 않도록 설정할 수 없습니다.  |  

미리 보기의 끝부분으로 가면서 모든 앱에 이 기능을 한 번에 활성화할 수 있으며, 이를 **최종 유효성 검증**이라고 합니다.  이 변경은 대부분 사용자에게 이 기능을 사용해 보고 해제할 수 있는 마지막 기회를 제공합니다. 다음 단계에서는 이 기능이 완전 탑재되어 해제할 수 없게 되므로 시기적절한 피드백은 이 기간에서 중요합니다.

**탑재**로의 최종 전환에서는 기능이 이미 설정된 앱에서는 미리 보기 스위치를 제거하여 효과적으로 기능을 영구적으로 설정할 수 있습니다. 해당 시점 전에 그 기능이 기본값이 되므로 이 변경은 대부분의 앱에 적용됩니다. 해당 기능이 꺼져 있는 앱의 경우, 미리 보기 스위치는 여전히 켜고 기능을 테스트하고 동일한 PowerApps Studio 세션 내에서 해제 할수 있습니다. 그러나 스위치가 켜져 있을 때 앱을 저장하면 다시 로드될 때 사용할 수 없으므로 이를 수행할 수 없습니다. 이 때, 기능을 켜기 전 상태로 앱을 되돌리기 위해 [이전 버전으로 앱을 복원](restore-an-app.md)할 수 있습니다.

## <a name="documentation"></a>설명서

이러한 기능에 대한 정보는 어디서 찾을 수 있을까요?  미리 보기 기능은 완성된 기능으로 다루어지며, 다음과 같은 다른 제품 기능과 마찬가지로 이 기능에 대해서 자세히 알아볼 수 있습니다. 
- [PowerApps 설명서](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started). 새 기능에 대한 기본 사항(예: 이점, 시작 방법 및 참조 정보)을 제공합니다.
- [PowerApps 커뮤니티 포럼](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1).  다른 사용자와 함께 새로운 기능을 살펴봅니다. 다른 사용자의 경험으로부터 배우고 자신의 경험을 공유합니다.
- [PowerApps 블로그](https://powerapps.microsoft.com/blog/).  항상 그렇지는 않지만 종종 블로그 게시물에 새 기능이 소개됩니다.

실험적 기능은 다릅니다.  진행 중인 작업이며 완성된 것으로 생각하지 않습니다. **앱 설정** 창(아래 참조)의 짧은 설명이 해당 기능에 대한 유일한 정보가 될 수 있습니다. 실험적 기능은 일반적으로 설명서에 나타나지 않습니다. 커뮤니티 포럼이 정보를 얻을 수 있는 가장 좋은 곳일 것입니다.  초기 블로그 게시물에서 이 기능에 대해 설명하는 경우도 있습니다.  충분한 정보를 찾을 수 없는 경우에는 포럼에 묻거나 기능이 미리 보기 단계로 진행될 때까지 기다려 주세요.

## <a name="controlling-which-features-are-enabled"></a>사용 가능한 기능 제어

실험적 및 미리 보기 기능은 앱의 **고급 설정**에 나와 있습니다.  이 앱 내에서 **파일** 메뉴를 선택하고 **앱 설정**을 선택한 다음, **고급 설정**을 선택합니다. **미리 보기 기능** 및 **실험적 기능** 섹션까지 아래로 스크롤합니다.

![](media/working-with-experimental/advanced-settings.png)

각 기능에 설정/해제 스위치가 있습니다.  **해제**는 기능을 사용하지 않도록 설정했음을 의미합니다.  모든 스위치를 해제 상태로 두는 것이 기본이며 앱을 실행하는 가장 안전한 방법입니다.

설정을 변경한 후 앱을 닫았다가 다시 열어야 하는 경우도 있습니다.  기능 설명에서 이 단계를 수행해야 하는 경우를 명시해야 합니다.

**고급 설정** 패널 맨 위에서, 미리 보기 또는 실험적 기능이 아니며 완벽하게 신뢰할 수 있는 완전 탑재 기능에 대한 설정을 찾을 수 있습니다. 

이 설정은 각 앱에 특정적이므로, 설정/해제 스위치를 변경하면 현재 열려 있는 앱에만 영향을 미칩니다. 앱을 만드는 경우 이러한 스위치는 해당 앱에 대한 기본 설정으로 되돌아갑니다.