---
title: PowerApps의 모델 기반 앱 양식에 대한 탭 속성 | MicrosoftDocs
description: 기본 양식에 대한 탭 속성 이해
Keywords: 탭 속성; Dynamics 365; 기본 양식
author: matp
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: Mattp123
manager: kvivek
ms.date: 06/07/2018
ms.service: powerapps
ms.topic: article
ms.assetid: e0790865-c5a4-4e86-bce2-584af2b8ed93
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bd97c61829aaba7279f56019f0eec7fa9829a6ea
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756263"
---
# <a name="tab-properties-for-model-driven-app-forms-overview"></a>모델 기반 앱 양식에 대한 탭 속성 개요

 양식의 본문에서 탭은 가로 분할을 제공합니다. 탭에는 표시할 수 있는 레이블이 있습니다. 레이블이 표시되면, 탭은 레이블을 선택하여 내용을 표시하거나 숨기도록 확장하거나 축소할 수 있습니다.  
  
 탭에는 최대 3개까지 열을 포함하며 각 열의 너비는 전체 너비에 비례하여 설정할 수 있습니다. 새 탭을 만들 때 각 열은 섹션으로 미리 채워집니다.  

PowerApps 사이트에서 **탭 속성**에 액세스할 수 있습니다. 
1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 사이트에서 **모델 기반**(탐색 창의 왼쪽 아래)을 선택합니다.  

     ![모델 기반 디자인 모드](media/model-driven-switch.png)

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.  

3.  양식 목록에서 유형 **기본**의 양식을 엽니다. 양식 캔버스에서 탭 속성을 보려면 탭 중 하나를 두 번 클릭 합니다.

    ![탭 속성](media/tab-properties.png)
  
 다음 표는 양식에서 탭에 설정할 수 있는 속성을 표시합니다:
  
|탭|속성|설명|  
|---------|--------------|-----------------|  
|**표시**|**이름**|**필수**: 스크립트에서 참조할 때 사용되는 탭의 고유 이름입니다. 이름에는 영숫자 문자와 밑줄만 사용할 수 있습니다.|  
||**레이블**|**필수**: 사용자에게 표시되는 탭에 대해 지역화할 수 있는 레이블입니다.|  
||**양식에 이 탭의 레이블 표시**|레이블이 표시될 때 사용자는 레이블을 선택하여 탭을 확장하거나 축소할지 여부를 전환할 수 있습니다. 레이블을 표시할지 여부를 선택합니다.|  
||**기본적으로 이 탭 확장**|탭 상태는 양식 스크립트를 사용하거나 레이블을 선택하여 확장 또는 축소 사이를 전환할 수 있습니다. 탭의 기본 상태를 선택합니다.|  
||**기본적으로 표시 가능**|탭 표시는 선택 사항이며 스크립트를 사용하여 제어할 수 있습니다. 탭을 표시할지 여부를 선택합니다. 추가 정보: [표시 유형 옵션](visibility-options-legacy.md)|  
||**사용 가능성**|휴대폰에서 탭을 사용할 수 있도록 하려면 선택합니다.|  
|**서식**|**레이아웃**|탭은 열을 최대 3개까지 사용할 수 있습니다. 이러한 옵션을 사용하여 채워야 하는 탭 수와 전체 너비의 비율을 설정할 수 있습니다.|  
|**이벤트**|**양식 라이브러리**|탭 `TabStateChange` 이벤트 처리기에서 사용되는 JavaScript 웹 리소스를 지정합니다.<br /><br />|  
||**이벤트 처리기**|탭 `TabStateChange` 이벤트를 호출해야 하는 함수를 라이브러리에서 구성합니다. 자세한 내용: [이벤트 처리기 구성](configure-event-handlers-legacy.md)|  
  
## <a name="next-steps"></a>다음 단계

[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
