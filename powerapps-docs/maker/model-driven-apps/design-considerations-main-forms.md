---
title: PowerApps에서 모델 기반 앱 기본 양식에 대한 디자인 고려 사항 | MicrosoftDocs
description: 기본 양식을 디자인하는 방법 알아보기
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>모델 기반 앱 기본 양식에 대한 디자인 고려 사항

기본 양식은 사용자가 사용자의 데이터를 보고 상호 작용하는 기본 사용자 인터페이스입니다. 기본 양식은 광범위한 옵션을 제공하며 Dynamics 365 for phones를 제외한 모델 기반 앱에서 사용할 수 있습니다.  
  
 기본 양식의 주요 디자인 목표 중 하나는 한 번 디자인해서 어디에나 배포할 수 있다는 것입니다. 모델 기반 앱에 대해 디자인하는 기본 양식도 Dynamics 365 for Outlook 및 태블릿용 Dynamics 365에 사용됩니다. 이러한 방식의 장점은 변경 내용을 여러 양식에 통합할 필요가 없다는 것입니다. 하지만 이러한 양식을 디자인할 때 고려해야 할 몇 가지 중요한 요소가 있습니다.  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>다른 그룹에 대한 사용자 지정 양식  
 여러 기본 양식을 만들고 각 양식에 다른 보안 역할을 할당할 수 있으므로 응용 프로그램을 사용하는 방법에 최적화된 양식으로 조직의 다른 그룹을 표시할 수 있습니다. 각 그룹에 다른 옵션을 제공하여 다른 양식을 선택할 수도 있습니다. 추가 정보: [양식에 대한 액세스 제어](control-access-forms.md)  
  
 관리자와 의사 결정자는 주요 데이터 요소에 대한 빠른 참조를 제공하도록 최적화된 양식을 원할 수 있습니다. 목록보다 차트를 더 선호하고 많은 양의 데이터 입력을 수행하지 않을 수 있습니다.  
  
 고객과 직접적으로 상호 작용하는 사용자는 가장 자주 수행하는 작업에 맞는 양식이 필요할 수 있습니다. 대부분의 효율적인 데이터 입력을 허용하는 양식을 원할 수도 있습니다.  
  
 조직의 사용자의 필요와 요구를 파악해야 합니다. 이는 주로 입력을 수집하고 다른 것을 시도하고 사용자가 사용할 수 있는 양식을 작성하는 반복적인 프로세스입니다. 사용할 수 있는 도구는 다양하지만 이 모든 도구를 양식 안에 모두 수행해야 하는 것은 아닙니다. 양식에 비즈니스 규칙, 워크플로 프로세스, 대화 및 비즈니스 프로세스 흐름을 함께 사용하여 조직에 적합한 솔루션을 제공합니다.  
  
 양식을 관리하는 데 사용할 시간과 조정해야 합니다. 양식을 만들고 편집하는 것은 상대적으로 쉽지만 양식을 많이 만들 수록 더 많은 양식을 관리해야 합니다.  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>프레젠테이션 차이  
 각 프레젠테이션에 대해 여러 양식을 관리할 필요는 없지만 기본 양식에서 프레젠테이션의 차이가 고려될 수 있음을 생각해야 합니다. [기본 양식 프레젠테이션](main-form-presentations.md)은 기본 양식이 표시될 수 있는 다른 방식에 대해 설명합니다. 고려해야 할 주요 사항은 다음과 같습니다.  
  
- Dynamics 365 for tablets는 양식에 추가되는 이미지, HTML 또는 Silverlight 웹 리소스를 지원하지 않습니다.  
  
-   Dynamics 365 for tablets 양식의 레이아웃은 기본 양식에 따라 자동으로 생성됩니다. Dynamics 365 for tablets에 대한 특별한 양식 편집기가 없습니다. 양식 프레젠테이션이 두 클라이언트에서 잘 작동하는지 확인해야 합니다.  
  
-   웹 응용 프로그램에 있는 DOM 요소와 상호 작용하는 지원되지 않는 스크립트가 있을 경우 이러한 스크립트는 동일한 DOM 요소를 사용할 수 없으므로 Dynamics 365 for tablets 양식에서 작동하지 않습니다.  
  
- Dynamics 365 for Outlook 읽기 창 양식은 스크립팅을 허용하지 않습니다. 양식 요소의 표시 유형은 기본 설정에 따라 다르며 스크립트를 사용하는 런타임에 변경될 수 있습니다.  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>양식 성능  
 느리게 로드되거나 신속하게 응답하지 않는 양식은 앱의 생산성과 사용자 채택에 영향을 줄 수 있습니다. [양식 성능 최적화](optimize-form-performance.md)에서는 사용자 지정이 양식 성능에 나쁜 영향을 미치지 않도록 양식을 디자인할 때 고려해야 하는 몇 가지 권장 사항을 제공합니다.  
  
### <a name="next-steps"></a>다음 단계 
 [양식 만들기 및 디자인](create-design-forms.md)    
 [빨리 만들기 양식 만들기 및 편집](create-edit-quick-create-forms.md)   

 
