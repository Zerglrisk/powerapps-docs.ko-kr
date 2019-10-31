---
title: PowerApps 앱 디자이너에서 모델 기반 앱 속성 관리 | MicrosoftDocs
description: 앱의 속성을 관리하는 방법 알아보기
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 14
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>앱 디자이너에서 모델 기반 앱 속성 관리

앱 속성은 제목 또는 URL과 같은 앱에 대한 중요한 세부 정보를 정의합니다. 앱을 만들 때 앱 속성을 정의할 수 있습니다. 나중에 이 속성은 앱 디자이너에서 변경할 수 있습니다.  
  
1.  앱 디자이너에서 오른쪽에 있는 **속성** 탭을 선택합니다.  

    > [!div class="mx-imgBorder"] 
    > ![앱 디자이너 속성 창](media/app-designer-properties-tab.png "앱 디자이너 속성 창")  
  
2.  필요에 따라 정보를 변경합니다.  

    |속성|설명|  
    |--------------|-----------------|
    |**이름**|앱에 대한 고유하고 알기 쉬운 이름을 입력합니다.|  
    |**설명**|앱에 대한 간단한 설명을 입력합니다.|  
    |**아이콘**|기본적으로 **기본 앱 사용** 확인란이 선택되어 있습니다. 응용 프로그램에 대한 다른 웹 리소스 아이콘을 선택하려면 확인란의 선택을 취소하고 드롭다운 목록에서 아이콘을 선택합니다. 이 아이콘은 앱의 미리 보기 타일에 표시됩니다.|
    |**고유 이름**| 고유한 이름은 변경할 수 없습니다. 고유 이름을 사용하면 테이블을 쿼리하여 데이터베이스에서 데이터를 가져올 수 있습니다.|
    |**앱 URL 접두사<sup>1</sup>**| 앱을 만들 때 선택한 URL이 기본적으로 여기에 나타납니다. **앱 관리** 대화 상자에서 앱 URL을 변경할 수 있습니다. 현재 솔루션을 통해 앱 URL 접미사를 내보내거나 가져올 수 없습니다.|
    |**앱의 시작 페이지를 선택합니다**|이 옵션을 사용하여 환경에서 사용할 수 있는 웹 리소스를 선택할 수 있습니다. 사용자가 만든 시작 페이지에는 비디오 링크, 업그레이드 지침 또는 시작 정보 등의 유용한 정보가 포함될 수 있습니다. 시작 페이지로 사용할 수 있는 HTML 파일과 같은 웹 리소스를 만드는 방법에 대한 자세한 내용은 [웹 리소스를 만들고 편집하여 웹 응용 프로그램 확장](create-edit-web-resources.md)을 참조하십시오.|
    |**Mobile Offline 활성화**|이 옵션을 사용하면 **Mobile offline 프로필** 드롭다운 목록에서 선택한 프로필에 대해 휴대폰에서 오프라인으로 앱을 사용할 수 있습니다.|

    <sup>1</sup>**클라이언트** 및 **앱 URL 접미사** 속성은 새 앱을 만들 때 더 이상 사용할 수 없습니다.
3.  앱을 저장합니다.  
  
## <a name="next-steps"></a>다음 단계  
 [앱 만들기 또는 편집](create-edit-app.md)
