---
title: 솔루션 계층 보기 | MicrosoftDocs
description: 솔루션 계층를 사용하는 방법 알아보기
keywords: ''
ms.date: 04/18/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5b507384b3fdf157aa029ad98d4d4203f624d8f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702110"
---
<!--note from editor: Best practice is that H1 title and title in metadata are different.    -->

# <a name="view-solution-layers"></a>솔루션 계층 보기
솔루션 계층를 사용하면 시간이 지남에 따라 솔루션 변경으로 인해 발생하는 모든 구성 요소 변경 내용을 볼 수 있습니다. 솔루션 계층 내에서 드릴다운하여 구성 요소에 대한 특정 변경 및 변경되지 않은 속성 세부 정보를 볼 수 있습니다. 

솔루션 계층: 
-   이제 솔루션에서 구성 요소를 변경한 순서가 표시됩니다. 
-   구성 요소의 변경 내용을 포함하여 특정 솔루션 내에서 구성 요소의 모든 속성을 볼 수 있습니다. 
-   솔루션 변경에 의해 도입된 구성 요소에 대한 변경 내용을 표시하여 종속성 또는 솔루션 계층 문제를 해결하는 데 사용할 수 있습니다.

## <a name="view-the-solution-layers-for-a-component"></a>구성 요소에 대한 솔루션 계층 보기
솔루션 계층는 솔루션 탐색기의 **구성 요소** 목록 또는 **종속성 정보** 대화 상자에서 액세스할 수 있습니다. 

<!--note from editor: In step 2 below, does the page display a name at top? If so, use the same capitalization in text. -->

1. **구성 요소** 목록에서 솔루션 계층를 보려면 [솔루션 탐색기](../model-driven-apps/advanced-navigation.md#solution-explorer)를 엽니다. **구성 요소** 목록에서 **거래처** 같은 구성 요소를 선택한 다음 도구 모음에서 **솔루션 계층**를 선택합니다. 

   > [!div class="mx-imgBorder"] 
   > ![솔루션 계층 단추](media/solution-layers-toolbar.png "솔루션 계층 단추")

2. 솔루션 계층 페이지가 나타납니다. 여기에 표시된 **거래처** 엔터티와 같은 구성 요소에 대한 각 계층이 맨 위에 가장 최근의 계층과 함께 표시됩니다. 솔루션 계층에 대한 세부 정보를 보려면 레이어를 선택합니다. 

   > [!div class="mx-imgBorder"] 
   > ![솔루션 계층 목록](media/solution-layers-list.png "솔루션 계층 목록")

3. **솔루션 계층** 대화 상자에서 **변경된 속성** 탭에는 특정 솔루션 계층의 일부로 수정된 속성만 표시됩니다. 

   > [!div class="mx-imgBorder"] 
   > ![솔루션 계층 변경된 속성](media/solution-layers-change-prop.png "솔루션 계층 변경된 속성")

4. **모든 속성** 탭을 선택하여 솔루션 계층에 대한 변경된 속성과 변경되지 않은 속성을 포함한 모든 속성을 봅니다. 

   > [!div class="mx-imgBorder"] 
   > ![솔루션 계층 모든 속성](media/solution-layers-all-prop.png "솔루션 계층 모든 속성")

### <a name="see-also"></a>참조
[솔루션 개요](solutions-overview.md)
