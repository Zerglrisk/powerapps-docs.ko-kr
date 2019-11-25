---
title: PowerApps의 모델 기반 앱에 필드 추가 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eb7d5c88031f7269472906b5bfcad7c91214417
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2751872"
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>모델 기반 앱 양식에 필드 추가 

표준 엔터티에 대한 PowerApps 양식이 조직의 비즈니스 요구 사항을 만족하지 못할 경우 기존 필드를 변경하거나 새 필드를 추가하여 양식을 사용자 지정할 수 있습니다. 양식에서 기존 필드를 편집하는 것이 더 간단할 수 있지만 특정 비즈니스 문제를 해결하기 위해 필드를 추가하는 것이 좋을 때도 있습니다.

이 항목에서는 양식에 필드를 추가합니다.   
  
1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  


    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다. 

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.  

3.  목록에서 유형 **기본** 유형의 양식을 열어 편집합니다.  
  
4.  양식에서 필드를 추가할 섹션을 클릭한 후 **필드 탐색기** 창에서 양식에 추가할 필드를 두 번 클릭합니다.  
  
    > [!TIP]
    >  양식에 옵션 집합 필드를 추가하면 옵션 집합 값이 들어있는 드롭다운 목록이 두 값만을 표시할 수 있습니다. 목록에 더 많은 값을 보려면 스크롤해야 합니다. 사용자가 스크롤할 필요가 없이 두 개 이상의 값을 표시하려면 양식의 옵션 집합 아래의 **공백** 컨트롤을 하나 이상 추가합니다. 각 **공백** 컨트롤은 하나의 추가 옵션 설정 값에 대한 공간을 제공합니다. 예를 들어, 드롭다운 목록에서 스크롤 없이 4개의 값을 표시하려는 경우 양식의 옵션 집합 아래의 **공백** 컨트롤을 2개 추가합니다.  
  
5.  양식이 표시되는 방식과 이벤트가 작동하는 방식을 미리 보려면:  
  
    1.  **읽기 전용 양식** 탭에서 **미리 보기**를 클릭하고 **양식 만들기**, **양식 업데이트** 또는 **홈**을 선택합니다.  
  
    2.  미리 보기 양식을 닫으려면 **닫기**를 클릭합니다.  
  
    3.  편집할 양식의 사용자 지정 항목을 게시하려면 양식을 열고 **게시**를 클릭합니다.  
  
6.  양식 편집이 끝났으면 **저장 후 닫기**를 클릭합니다.  
  
7. 게시되지 않은 모든 구성 요소에 대한 사용자 지정 항목을 한 번에 게시하려면 **파일**을 클릭한 다음 **모든 사용자 지정 항목 게시**를 클릭합니다.  
  
> [!NOTE]
>  사용자 지정 항목을 게시하는 것은 정상적인 시스템 작동을 방해할 수 있습니다. 사용자에게 가장 지장을 덜 줄 때 항목을 게시하는 것이 좋습니다.  
  
## <a name="next-steps"></a>다음 단계  
 
 [양식 만들기 및 디자인](create-design-forms.md)
