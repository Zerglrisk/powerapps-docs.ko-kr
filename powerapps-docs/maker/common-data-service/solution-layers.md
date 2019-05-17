---
title: 솔루션 레이어 보기 | MicrosoftDocs
description: 솔루션 레이어를 사용하는 방법 알아보기
keywords: null
ms.date: 04/10/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
  - powerapps
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-solution-layers"></a>솔루션 레이어 보기
솔루션 레이어를 사용하면 시간이 지남에 따라 솔루션 변경으로 인해 발생하는 모든 구성 요소 변경 내용을 볼 수 있습니다. 솔루션 계층 내에서 드릴다운하여 구성 요소에 대한 특정 변경 및 변경되지 않은 속성 세부 정보를 볼 수 있습니다. 

솔루션 레이어는 다음과 같은 이점을 제공합니다. 
-   이제 솔루션에서 구성 요소를 변경한 순서가 표시됩니다. 
-   구성 요소의 변경 내용을 포함하여 특정 솔루션 내에서 구성 요소의 모든 속성을 볼 수 있습니다. 
-   솔루션 변경에 의해 도입된 구성 요소에 대한 변경 내용을 표시하여 종속성 또는 솔루션 레이어 문제를 해결하는 데 사용할 수 있습니다.

## <a name="view-the-solution-layers-for-a-component"></a>구성 요소에 대한 솔루션 레이어 보기
솔루션 레이어는 솔루션 탐색기의 **구성 요소** 목록 또는 **종속성 정보** 대화 상자에서 액세스할 수 있습니다. 

1. **구성 요소** 목록에서 솔루션 레이어를 보려면 [솔루션 탐색기를 열고](../model-driven-apps/advanced-navigation.md#solution-explorer) **구성 요소** 목록에서 구성 요소(예: **거래처**)를 선택하고 도구 모음에서 **솔루션 레이어**를 선택합니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-toolbar.png "솔루션 레이어 단추")

2. 여기에 표시된 거래처 엔터티와 같이 구성 요소에 대한 각 레이어가 맨 위에 가장 최근의 레이어로 표시되는 솔루션 레이어 페이지가 나타납니다. 솔루션 레이어에 대한 세부 정보를 보려면 레이어를 선택합니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-list.png "솔루션 레이어 목록")

3. **솔루션 레이어** 대화 상자에서 **변경된 속성** 탭에는 특정 솔루션 레이어의 일부로 수정된 속성만 표시됩니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-change-prop.png "솔루션 레이어 변경된 속성")

4. **모든 속성** 탭을 선택하여 솔루션 레이어에 대한 변경된 속성과 변경되지 않은 속성을 포함한 모든 속성을 봅니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-all-prop.png "솔루션 레이어 모든 속성")

## <a name="see-also"></a>참조
[솔루션 개요](solutions-overview.md)