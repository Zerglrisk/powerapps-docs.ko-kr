---
title: Power Apps에서 보기에 대한 모델 기반 앱 관리 속성 | MicrosoftDocs
description: 보기의 관리 속성을 설정하는 방법 알아보기
ms.custom: ''
ms.date: 06/12/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 335084ee98cdfe82382eac775d068a62c9a429d9
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860022"
---
# <a name="model-driven-app-managed-properties-for-views"></a>보기에 대한 모델 기반 앱 관리 속성

<a name="BKMK_ManagedProperties"></a>   
 
 배포할 관리형 솔루션에 포함하려는 사용자 지정 공용 보기를 Power Apps에서 만들 경우 보기를 사용자 지정하여 해당 솔루션을 설치하는 사용자의 기능을 제한하는 옵션이 있습니다.  
  
 기본적으로 대부분의 보기에는 **사용자 지정 가능** 관리 속성이 참으로 설정되어 있어 다른 사용자가 이를 사용자 지정할 수 있습니다. 이를 변경할 적합한 이유가 없는 한 앱에서 보기를 다른 사용자가 사용자 지정할 수 있도록 하는 것이 좋습니다.  
  
## <a name="set-managed-properties-for-a-view"></a>보기의 관리 속성 설정  
  
1.  [솔루션 탐색기](advanced-navigation.md#solution-explorer)을 열고 원하는 **엔터티**를 확장한 다음 **보기**를 선택합니다.  
  
2.  사용자 지정 공용 보기를 선택합니다.  
  
3.  메뉴 모음에서 **기타 작업** > **관리 속성**을 선택합니다.  

    > [!div class="mx-imgBorder"] 
    > ![관리 속성 메뉴](media/managed-properties.png)
  
4.  설정 **사용자 정의** 또는 **삭제 가능** 옵션을 **True** 또는 **False**로 설정합니다.  

    > [!div class="mx-imgBorder"] 
    > ![관리 속성 설정](media/set-managed-properties.png)
  
> [!NOTE]
> 설정은 관리형 솔루션으로 보기가 포함된 솔루션을 내보내고 다른 환경에 설치할 때까지 적용되지 않습니다.  

## <a name="next-steps"></a>다음 단계
[보기 이해 ](create-edit-views.md)
