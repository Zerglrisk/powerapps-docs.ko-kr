---
title: 모델 기반 앱에서 비즈니스 규칙과 흐름을 사용하여 사용자 지정 비즈니스 논리 적용 | MicrosoftDocs
description: 앱에서 사용할 수 있는 다양한 비즈니스 논리 유형에 대해 알아보기
ms.custom: ''
ms.date: 08/02/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="apply-custom-business-logic-with-business-rules-and-flows-in-model-driven-apps"></a>모델 기반 앱에서 비즈니스 규칙과 흐름을 사용하여 사용자 지정 비즈니스 논리 적용

비즈니스 프로세스를 정의하고 일관되게 유지하는 것은 사람들이 모바일 기반 앱을 사용하는 주요 이유 중 하나입니다. 일관된 프로세스를 사용하면 모델 기반 앱을 사용하는 사용자가 기계적인 단계들을 수행하기 위해 기억할 필요 없이 작업에 집중할 수 있습니다. 

## <a name="business-rules"></a>비즈니스 규칙

비즈니스 규칙은 빠르게 변화하고 일반적으로 사용되는 규칙을 구현하고 유지하는 간단한 인터페이스를 제공합니다. 비즈니스 규칙의 *범위*는 비즈니스 규칙이 실행되는 위치를 정의합니다.

|||  
|-|-|  
|**이 항목을 선택하면...**|**범위는 다음으로 설정**|  
|**엔터티**|모든 양식 및 서버|  
|**모든 양식**|모든 양식|  
|특정 양식(예: **거래처** 양식)|해당 양식| 

모델 기반 앱에서 양식의 비즈니스 규칙을 정의하는 방법에 대한 자세한 내용은 [모델 기반 앱 양식에 논리를 적용하는 비즈니스 규칙 만들기](create-business-rules-recommendations-apply-logic-form.md)를 참조하십시오.

> [!NOTE]
> *캔버스 앱* 및 *모델 기반 앱*의 두 서버 수준에서 적용되도록 엔터티에 대한 비즈니스 규칙을 정의하려면 [엔터티를 위한 비즈니스 규칙 만들기](/powerapps/maker/common-data-service/data-platform-create-business-rule)를 참조하십시오.

## <a name="flows"></a>흐름  
  
Microsoft Flow에는 여러 유형의 프로세스가 있고, 각각은 다른 목적을 위해 설계되었습니다.  

-   자동 흐름 이벤트에 의해 트리거된 후 하나 이상의 작업을 자동으로 수행하는 흐름을 만듭니다. 추가 정보: [흐름 만들기](/flow/get-started-logic-flow)
    
-   단추 흐름 모바일 장치에서 단추를 눌러 반복적인 작업을 간단하게 수행합니다. 추가 정보: [단추 흐름 소개](/flow/introduction-to-button-flows)
  
-   예약된 흐름 하루에 한 번, 특정 날짜 또는 특정 시간 이후에 일정에 따라 하나 이상의 작업을 수행하는 흐름을 만듭니다. 자세한 내용: [일정에 따라 흐름 실행](/flow/run-scheduled-tasks)
  
-   비즈니스 프로세스 흐름  비즈니스 프로세스 흐름을 만들어 사용자들이 앱에서 작업할 때마다 데이터를 일관되게 입력하고 동일한 단계를 따르도록 합니다. 추가 정보: [비즈니스 프로세스 흐름 개요](/flow/business-process-flows-overview)

-   워크플로 및 작업. Dynamics 365 사용자 지정자는 클래식 Common Data Service 프로세스, 즉 워크플로 및 작업에 익숙할 수 있습니다. 자세한 내용: [워크플로 프로세스 사용](/flow/workflow-processes) 및 [작업 개요](/flow/actions)
  
## <a name="next-step"></a>다음 단계

[비즈니스 규칙을 만들어 모델 기반 양식에 논리 적용](create-business-rules-recommendations-apply-logic-form.md)

### <a name="see-also"></a>참조

[Common Data Service에 비즈니스 논리 적용](../common-data-service/cds-processes.md)
