---
title: Power Apps에서 모델 기반 앱 기본 양식 및 구성 요소 사용 | Microsoft Docs
description: 통합된 인터페이스 기반 앱에서 주요 양식 및 구성 요소 사용하는 방법 알기
keywords: 메인 양식; 고객 서비스; 고객 서비스 허브; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 43bfface-4dc2-411d-99a1-83e934646989
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3232099a5ad1526ad351aea37e8952afc6e474bf
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884281"
---
# <a name="use-the-model-driven-app-main-form-and-its-components"></a>모델 기반 앱 기본 양식 및 해당 구성 요소 사용

통합 인터페이스 기반 앱의 양식은 최적의 에이전트 생산성을 향상시키는 사용자 환경을 제공하며 관련 레코드를 작업하는 동안 컨텍스트를 유지 관리합니다. 솔루션 탐색기에 등록된 양식을 볼 수 있습니다. 새로운 양식의 양식 유형은 **메인**입니다.

이 주제는 메인 양식 편집 및 양식의 다양한 요소를 추가 또는 변경하는 방법을 설명합니다.

## <a name="open-the-form-editor"></a>양식 편집기 열기

양식을 편집하거나 요소를 추가 또는 변경하려면 양식 편집기를 사용합니다. 양식 편집기는 모든 통합된 인터페이스 기반 앱의 양식을 편집할 수 있습니다.

양식 편집기에 액세스하기 위해 아래 주어진 절차를 따르십시오. 

> [!NOTE]
> 양식을 편집하는 과정에서 새로운 솔루션 구성 요소를 만드는 경우 구성 ㅇ소 이름은 기본 솔루션의 솔루션 게시자 사용자 지정 접두사를 사용하고 이러한 구성 요소는 기본 솔루션에만 포함됩니다. 새 솔루션 구성 요소를 특정 비관리형 솔루션에 포함하려면 비관리형 솔루션을 통해 양식 편집기를 엽니다.


### <a name="access-the-form-editor-through-app-designer-in-power-apps"></a>Power Apps에서 앱 디자이너를 통한 양식 편집기 액세스

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

2.  왼쪽 탐색 창에서 **앱**을 선택하고 원하는 앱을 선택한 다음 도구 모음에서 **편집**을 선택합니다.  

3. 앱 디자이너 캔버스에서 아래 화살표를 선택합니다. ![앱 디자이너를 위한 아래쪽 화살표](media/down-arrow-app-designer.png) 를 사용하여 해당 엔터티에 대해 사용할 수 있는 양식을 볼 수 있습니다. 

4. 디자이너 단추 열기 선택하기 ![디자이너 열기](media/site-map-designer.png)편집할 양식에 해당합니다.

   ![앱 디자이너 내 양식 편집기](media/app-designer-forms.png)
 
5. 양식 디자이너에서 **변경한 다음 저장** 을 선택하여 변경 내용을 저장하고 **게시**를 선택하여 앱에서 사용할 수 있도록 게시합니다. 

> [!NOTE]
> 앱에 다른 변경이 필요한 경우 앱 레벨의 게시 옵션을 사용해서 그것들을 게시합니다. 자세한 내용은 [앱 디자이너를 사용하여 앱 유효성 검사 및 게시](validate-app.md)를 참조하십시오.

> [!NOTE]
> 웹클라이언트 메인 양식은 또한 Customer Service 허브와 호환가능하며 앱 디자이너를 사용하여 편집될 수 있습니다.


### <a name="access-the-form-editor-through-the-default-solution"></a>기본 솔루션을 통해 양식 편집기에 액세스

1.  [Power Apps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.  

3. 양식 목록에서 유형 **기본**의 양식을 엽니다.

### <a name="access-the-form-editor-for-an-unmanaged-solution"></a>비관리형 솔루션의 양식 편집기에 액세스

1. [솔루션](advanced-navigation.md#solutions)을 엽니다.
2. 사용할 비관리형 솔루션을 두 번 클릭합니다. 관리형 또는 비관리형 솔루션 유형이 **패키지 유형** 열에 표시됩니다.
3. 구성 요소 목록에서 편집하려는 양식이 있는 엔터티를 찾습니다. 엔터티가 거기에 없으면 추가해야 합니다.

#### <a name="add-an-entity-to-an-unmanaged-solution"></a>비관리형 솔루션에 엔터티를 추가합니다.

1. 솔루션 탐색기에서 비관리형 솔루션을 연 경우 **엔터티** 노드를 선택하고 목록 위의 도구 모음에서 **기존 항목 추가**를 선택합니다.

     > [!div class="mx-imgBorder"] 
     > ![기존 엔터티 추가](media/add-existing-entity.png)

2. **솔루션 구성 요소 선택** 대화 상자에서 **구성 요소 유형** 선택기를 **엔터티**로 설정하고 추가할 엔터티를 선택하고 **확인**을 선택합니다.

3. **필수 구성 요소 누락** 대화 상자가 나타나면 이 비관리형 솔루션을 다른 조직에 내보내지 않으려면 **아니요, 필수 구성 요소를 포함하지 않습니다.** 를 선택할 수 있습니다. 이번에 누락된 필수 구성 요소를 포함하지 않으려면 나중에 추가할 수 있습니다. 나중에 이 솔루션을 내보낼 경우 다시 알림을 받습니다.

4. 솔루션 탐색기에서 편집하려는 양식이 있는 엔터티를 확장하고 **양식**을 선택합니다.

5. 양식 목록에서 유형 **기본**의 양식을 엽니다.

#### <a name="publish-the-changes-for-use-in-the-app"></a>앱 내 사용을 위하여 변경 내용 게시하기

사용자 인터페이스를 변경하는 특정 사용자 지정 항목은 사용자가 응용 프로그램에서 사용하기 전에 먼저 게시해야 합니다. 사용자 지정 항목을 게시하려면 솔루션 탐색기 도구모음에서 **모든 사용자 지정 항목 게시**를 선택합니다.

## <a name="form-editor-user-interface"></a>양식 편집기 사용자 인터페이스

양식 편집기 사용자 인터페이스에 대하여 자세히 이해하려면 [양식 편집기 사용자 인터페이스 개요](form-editor-user-interface-legacy.md)를 참조하십시오.

## <a name="form-properties"></a>양식 속성

양식 속성을 더 자세히 알고 싶으면, [양식 속성](form-properties-legacy.md)을 참조하십시오.

## <a name="visibility-options"></a>표시 유형 옵션  
 여러 유형의 양식 요소에는 기본적으로 표시하거나 숨길 옵션이 있습니다. 탭, 섹션 및 필드 모두 이 옵션을 제공합니다. 양식 스크립트 또는 비즈니스 규칙을 사용하면 양식의 조건에 맞게 조정하는 사용자 인터페이스를 제공하는 동적 양식을 만들기 위해 이러한 요소의 표시 유형을 제어할 수 있습니다. 
  
> [!NOTE]
>  양식 요소를 숨기는 것은 보안을 강화하기 위해 권장되는 방법이 아닙니다. 여러 가지 방법으로 요소가 숨겨져 있을 때 사용자가 양식의 모든 요소와 데이터를 볼 수 있습니다. 자세한 내용은 [양식 요소 표시 또는 숨기기](visibility-options-legacy.md)를 참조하십시오. 
  
## <a name="tab-properties"></a>탭 속성  

양식의 본문에서 탭은 가로 분할을 제공합니다. 탭에는 표시할 수 있는 레이블이 있습니다. 레이블이 표시되면, 탭은 레이블을 선택하여 내용을 표시하거나 숨기도록 확장하거나 축소할 수 있습니다. 탭 속성을 더 자세히 알고 싶으면, [탭 속성](tab-properties-legacy.md)을 참조하십시오.


## <a name="section-properties"></a>섹션 속성  

양식의 섹션은 탭 열에서 사용 가능한 공간을 차지합니다. 섹션에는 표시할 수 있는 레이블이 있고 레이블 아래에는 줄이 표시될 수 있습니다. 섹션 속성을 더 자세히 알고 싶으면, [섹션 속성](section-properties-legacy.md)을 참조하십시오.
  
## <a name="timeline"></a>타임라인  
 타임라인은 구체적인 엔터티에 대해 관련된 활동을 보여줍니다.  
  
 작업, 약속, 전화 통화, 전자 메일, 소셜 활동, 사용자 지정 활동 같은 활동 유형이 지원됩니다.  
  
 타임라인은 또한 노트, 시스템, 사용자 포스트를 보여줍니다. 이는 귀하가 보고 있는 엔터티에 설정된 **관련** 필드를 갖는 활동을 보여줍니다. 노트의 경우 **관련** 필드는 사용자에게 보여지지 않습니다; 그것은 타임라인에서 암시적으로 생성됩니다.  
  
 타임라인에서 보여지는 각 활동은 활동 명령 모음에서 가능한 동일한 빠른 작업을 갖습니다.  

## <a name="common-field-properties"></a>공통 필드 속성  

공통 필드 속성을 더 자세히 알고 싶으면, [공통 필드 속성](common-field-properties-legacy.md)을 참조하십시오. 
  
## <a name="special-field-properties"></a>특수 필드 속성  
 모든 필드에는 [공통 필드 속성](common-field-properties-legacy.md)에 나와 있는 속성을 사용하지만 특정 필드에는 추가 속성을 사용합니다. 더 자세히 알고 싶으면 [특정 필드 속성](special-field-properties-legacy.md)을 참조하십시오.

  
## <a name="sub-grid-properties"></a>하위 표 속성  

레코드 또는 차트의 목록을 표시하려면 양식에 하위 표를 구성할 수 있습니다. 서브 그리드 속성을 더 자세히 알고 싶으면, [서브 그리드 속성](sub-grid-properties-legacy.md)을 참조하십시오.

## <a name="quick-view-control-properties"></a>빠른 보기 컨트롤 속성  

양식의 빠른 보기 컨트롤은 양식의 조회에서 선택한 레코드의 데이터를 표시합니다. 빠른 보기 제어 속성을 탐색하고 싶은 경우 [빠른 보기 제어 속성](quick-view-control-properties-legacy.md)을 참조하십시오.
  
## <a name="web-resource-properties"></a>웹 리소스 속성  

양식에서 웹 리소스를 추가하거나 편집하여 앱 사용자에게 더욱 매력적이거나 유용하게 만들 수 있습니다. 양식 사용 웹 리소스는 이미지, HTML 파일 또는 Silverlight 컨트롤입니다. 웹 리소스 속성에 대해 상세히 알아보기 [웹 리소스 속성](web-resource-properties-legacy.md)으로 이동하기. 
  
## <a name="iframe-properties"></a>IFRAME 속성  

iFrame을 양식에 추가하여 양식 안에 다른 웹 사이트의 콘텐츠를 통합할 수 있습니다. IFRAME 속성을 더 자세히 알고 싶으면, [IFRAME 속성](iframe-properties-legacy.md)을 참조하십시오. 
  
## <a name="edit-navigation"></a>탐색 편집  
 양식 내 탐색 컨트롤이 있으면 관련 레코드 목록을 볼 수 있습니다. 각 엔터티 관계에는 표시 여부를 제어하는 속성이 있습니다. 추가 정보: [기본 엔터티에 대한 탐색 창 항목](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
 표시되도록 구성되어 있는 모든 엔터티 관계는 양식 편집기에서 재정의할 수 있습니다.  
  
 단계별 지시를 원할 경우 [관련 엔터티에 대해 양식 내비게이션 추가하기](add-edit-form-navigation-related-entities.md)를 참조하십시오.
  
 탐색을 편집할 수 있으려면 먼저 **홈** 탭의 **선택** 그룹에서 **탐색**을 선택해야 합니다.  
  
 **관계 탐색기**에서 1:N(일대다) 또는 N:N(다대다) 관계로 필터링하거나 사용 가능한 모든 관계를 볼 수 있습니다. **사용되지 않는 관계만 표시** 확인란이 비활성화되어 있고 선택되어 있습니다. 따라서 각 관계를 한 번만 추가할 수 있습니다.  
  
 **관계 탐색기**에서 관계를 추가하려면 관계를 두 번 클릭하기만 하면 탐색 영역에서 현재 선택된 관계 아래에 추가됩니다. 내비게이션 영역에서 관계를 더블 클릭하면 **디스플레이** 탭에 있는 라벨을 변경할 수 있습니다. **이름** 탭에서 관계에 대한 정보를 확인할 수 있습니다. **편집** 단추를 사용하여 엔터티의 정의를 엽니다.  
  
 탐색 영역에는 5개의 그룹이 있습니다. 끌어서 위치를 변경하고 두 번 클릭하여 레이블을 변경할 수 있지만 제거할 수 없습니다. 이러한 그룹은 그 안에 내용이 있는 경우에만 표시됩니다. 따라서 그룹을 표시하지 않으려면 아무 것도 추가하지 마십시오.  
  
## <a name="configure-event-handlers"></a>이벤트 처리기 구성  

이벤트 처리기는 JavaScript 웹 리소스에 대한 참조와 이벤트가 발생할 때 실행하는 해당 웹 리소스 내에 정의된 함수로 구성됩니다. 이벤트 처리기 구성에 대한 더 자세한 내용이 알고 싶으면 [이벤트 처리기 구성](configure-event-handlers-legacy.md)에 대해 참조하십시오. 
  
## <a name="next-steps"></a>다음 단계  
 [양식 만들기 및 디자인](create-design-forms.md)   
 [빨리 만들기 양식 만들기 및 편집](create-edit-quick-view-forms.md)   
 [빠른 보기 양식 만들기 및 편집](create-edit-quick-view-forms.md)
