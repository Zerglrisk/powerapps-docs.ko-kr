---
title: 앱에서 팀 엔터티를 조회 옵션으로 추가 | MicrosoftDocs
description: 앱에서 팀 엔터티를 조회 옵션으로 추가하는 방법 알아보기
ms.custom: ''
ms.date: 07/24/2019
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
ms.assetid: null
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-the-team-entity-as-a-lookup-option-in-your-app"></a>앱에서 팀 엔터티를 조회 옵션으로 추가

통합 인터페이스 앱을 사용하여 팀 엔터티를 조회할 수 있으려면 앱에 추가해야 합니다. 예를 들어, 연락처 레코드는 사용자 또는 팀에 할당할 수 있습니다.  

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-teams.png "사용 가능한 사용자 및 팀 모두가 있는 엔터티 조회")

그러나 사용자 엔터티가 앱에 포함되어 있지만 팀 엔터티는 포함되지 않은 경우 사용자 레코드만 조회에 나타납니다. 

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-user-only.png "사용자만 있는 엔터티 조회")

## <a name="add-the-team-entity-to-an-app"></a>앱에 팀 엔터티 추가

1. 앱 디자이너에서 앱을 엽니다. 
2. **구성 요소** 탭을 선택하고 **엔터티**를 선택한 다음 **팀**을 선택합니다.    

    > [!div class="mx-imgBorder"] 
    > ![](media/add-team-entity-app.png "앱에 팀 엔터티 추가")

3. **저장**을 선택하고 **게시**를 선택하여 앱 사용자가 변경할 수 있도록 합니다.   

