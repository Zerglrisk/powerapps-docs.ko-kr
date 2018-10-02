---
title: PowerApps에서 모델 기반 앱 빠른 만들기 양식 만들기 또는 편집 | MicrosoftDocs
description: 빠른 만들기 양식을 만들거나 편집하는 방법 알아보기
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 68ca9059-cc5a-45e7-88bd-cc57186bbb48
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>간소화된 데이터 입력 환경을 위한 모델 기반 앱 빨리 만들기 양식 만들기 또는 편집

이 항목에서는 빠른 만들기 양식을 만들고 편집합니다.

 빨리 만들기 양식을 사용하면 앱은 양식 스크립트와 비즈니스 규칙에 정의된 논리를 완벽하게 지원하며 효율적인 데이터 입력 환경을 즐길 수 있습니다. PowerApps 모델 기반 앱에서, 조회 또는 하위 표에서 새 레코드를 만들 때 탐색 모음의 **만들기** 단추를 선택하거나 **+ 새로 만들기**를 선택하면 빨리 만들기 양식이 나타납니다.
  
 Dynamics 365 Customer Engagement 모바일 앱은 새 레코드를 만들기 위한 빠른 양식 작성을 사용합니다. 엔터티에 빨리 만들기 양식이 이미 구성된 경우 모바일 응용 프로그램은 해당 양식을 사용합니다. 엔터티에 빨리 만들기 양식이 구성되지 않은 경우 PowerApps는 모바일 응용 프로그램에서 기본 양식 정의에 따라 빨리 만들기 양식을 만들어 새 레코드를 만듭니다.  
  
<a name="BKMK_QuickCreateFormEntities"></a>   
## <a name="entities-with-quick-create-forms"></a>빨리 만들기 양식이 있는 엔터티  
 기본적으로 다음 시스템 엔터티에만 빨리 만들기 양식이 있습니다.  
  
|||||  
|-|-|-|-|  
|거래처|캠페인 반응|서비스 케이스|경쟁 업체|  
|연락처|잠재 고객|영업 기회||  
  
시스템 활동 엔터티에 대해 빨리 만들기 양식을 만들 수 있지만 약속 엔터티를 제외하고는 빨리 만들기 양식을 지원하지 않습니다. Dynamics 365 버전 9.0 출시로 약속 엔터티에는 통합 인터페이스에 사용할 수 있는 빨리 만들기 양식이 포함되어 있습니다. 현재 약속 엔터티에 대한 빠른 만들기 양식을 비활성화하는 옵션은 지원되지 않습니다. 다른 [업데이트된 엔터티](create-design-forms.md) 및 사용자 지정 엔터티는 엔터티 정의에서 **빨리 만들기 허용**을 선택하고 빨리 만들기 양식을 만들어 이러한 양식을 지원하도록 할 수 있습니다. 

사용자 지정 활동 엔터티를 활성화하여 빨리 만들기 양식을 지원하고 이러한 엔터티에 대해 빨리 만들기 양식을 만들 수 있습니다. 하지만 사용자 지정 활동 엔터티에 대한 빨리 만들기 양식은 다른 사용자가 탐색 모음에서 **만들기**를 선택할 때 사용되지 않습니다. 이러한 빨리 만들기 양식은 다른 사용자가 특정 사용자 지정 활동 엔터티를 표시하는 하위 표에 대해 새 레코드를 추가할 때만 사용할 수 있습니다.  
  
<a name="BKMK_CreateQuickCreate"></a>   
## <a name="create-a-quick-create-form"></a>빨리 만들기 양식 만들기  
 빨리 만들기 양식을 여러 개 정의할 수 있지만 모든 사용자가 사용할 수 있는 빨리 만들기 양식은 하나뿐입니다. 모든 사용자가 사용할 양식은 양식 순서를 사용하여 설정됩니다. 빨리 만들기 양식은 보안 역할에 할당할 수 없으므로 양식을 전환하는 사용자에게 기능을 제공하지 않습니다.  
  
> [!NOTE]
>  빨리 만들기 양식을 표시하려면 엔터티의 **빨리 만들기 허용** 옵션을 활성화해야 합니다. 
  
### <a name="how-to-create-a-quick-create-form"></a>빨리 만들기 양식을 만드는 방법  
  
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 사이트에서 **모델 기반**(탐색 창의 왼쪽 아래)을 선택합니다.  

     ![모델 기반 디자인 모드](media/model-driven-switch.png)

> [!IMPORTANT]
> "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.     
  
2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.  

3.  도구 모음에서 **양식 추가** > **빨리 만들기 양식**을 선택합니다.  
  
4.  양식 디자이너에서 **필드 탐색기**로부터 필드를 양식의 섹션으로 끌어옵니다.  
  
5.  완료되면 **저장**을 선택합니다.  
  
6.  응용 프로그램에서 새 양식을 보려면 **게시**를 선택합니다.  
  
<a name="BKMK_EditQuickCreate"></a>   
## <a name="edit-a-quick-create-form"></a>빨리 만들기 양식 편집  
 빨리 만들기 양식이 양식 스크립트와 비즈니스 규칙을 지원하지만 그 목적은 기본 양식과 다르므로 기본 양식의 일부 기능은 지원하지 않습니다. 빨리 만들기 양식에는 항상 열이 세 개인 섹션이 하나 있습니다. 섹션이나 열을 추가로 추가할 수 없습니다.  
  
 다음 컨트롤은 빨리 만들기 양식에 추가할 수 없습니다.  
  
-   하위 표  
  
-   빠른 보기 양식  
  
-   웹 리소스  
  
-   iFrames  
  
-   메모  
  
-   Bing 지도  
  
빨리 만들기 양식에 합성 필드를 추가하면 별도의 필드로 표시됩니다.  
  
### <a name="to-edit-a-quick-create-form"></a>빨리 만들기 양식을 편집하려면  
  
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 사이트에서 **모델 기반**(탐색 창의 왼쪽 아래)을 선택합니다.  

> [!IMPORTANT]
> "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.    
  
2. **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.    

3. 양식 목록에서 양식 **유형**이 **빨리 만들기**인 양식을 선택합니다.  
  
3.  **필드 탐색기**에서 필드를 양식의 섹션으로 끌어옵니다.  
  
     양식 스크립트의 이벤트 처리기에 대한 자세한 내용은 [이벤트 처리기 구성](configure-event-handlers-legacy.md)을 참조하십시오.  
  
4.  완료되면 **저장**을 선택합니다.  
  
5.  응용 프로그램에서 수정된 양식을 보려면 **게시**를 선택합니다.  
  
### <a name="next-steps"></a>다음 단계  
[양식 편집기 사용자 인터페이스 개요](form-editor-user-interface-legacy.md)
