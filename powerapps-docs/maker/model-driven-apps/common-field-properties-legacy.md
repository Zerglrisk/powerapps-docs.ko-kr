---
title: PowerApps의 모델 기반 앱 공통 필드 속성 | MicrosoftDocs
description: 기본 양식에 대한 공통 필드 속성 이해
Keywords: 기본 양식; 공통 필드 속성; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e30d84206e92162327f1faf0035450ede9c05a8a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701318"
---
# <a name="model-driven-app-common-field-properties"></a>모델 기반 앱 공통 필드 속성

 양식의 필드는 사용자가 엔터티 레코드의 데이터를 보거나 편집하는 데 사용하는 컨트롤을 표시합니다. 필드는 섹션 내에서 최대 4개까지 열을 차지하도록 서식을 지정할 수 있습니다.  

솔루션 탐색기에서 **공통 필드 속성**에 액세스할 수 있습니다. **구성 요소**에서 **엔터티**를 확장한 후 원하는 엔터티를 확장하고 **포럼**을 선택합니다. 양식 목록에서 유형 **기본**의 양식을 엽니다. 공통 필드 속성을 보려면 필드 중 하나를 더블클릭합니다.

![공통 필드 속성](media/common-field-properties.png)
  
다음 표는 모든 필드가 사용하는 속성을 설명합니다. 특정 유형의 필드에는 특별한 속성이 있습니다. 이러한 특성은 [특수 필드 속성](special-field-properties-legacy.md)에 설명되어 있습니다.  
  
|탭|속성|설명|  
|---------|--------------|-----------------|  
|**표시**|**레이블**|**필수**: 기본적으로 레이블은 필드의 표시 이름과 일치합니다. 여기에서 다른 레이블을 입력하여 양식의 이름을 재정의할 수 있습니다.|  
||**양식에 레이블 표시**|레이블이 전혀 표시되지 않도록 선택할 수도 있습니다.|  
||**필드 동작**|확인란을 사용하여 필드 수준 동작을 지정합니다.|  
||**잠금**|그러면 실수로 양식에서 필드를 제거하지 못하도록 합니다. 필드가 제거된 경우 이벤트 처리기처럼 필드에 적용된 구성이 제거되지 않도록 합니다. 이 필드를 제거하려면 사용자 지정자가 이 설정을 먼저 해제해야 합니다.|  
||**표시**|필드 표시는 선택 사항이며 스크립트를 사용하여 제어할 수 있습니다. 추가 정보: [표시 유형 옵션](visibility-options-legacy.md)|  
||**사용 가능성**|휴대폰에서 탭을 사용할 수 있도록 하려면 선택합니다.|
|**서식**|**컨트롤이 차지하는 열 수 선택**|필드를 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.|  
|**자세히**|**표시 이름**, **이름** 및 **설명**|이 읽기 전용 필드는 참조용입니다. 필드 정의를 편집하려는 경우 간단하게 액세스할 수 있는 **편집** 단추를 클릭합니다.<br /><br /> 양식에서 필드의 각 인스턴스에는 양식 스크립트에서 참조할 수 있도록 이름 속성이 있지만 이 이름은 응용 프로그램에서 관리합니다. 필드의 첫 번째 인스턴스는 필드를 만들 때 지정한 필드의 이름입니다. 추가 정보: [필드 만들기 및 편집](../common-data-service/create-edit-fields.md)<br /><br /> 필드가 양식에 추가될 때마다 이름에 숫자가 1부터 끝까지 추가됩니다. 필드 이름이 ‘new_cost’인 경우 첫 번째 인스턴스는 ‘new_cost’, 두 번째는 ‘new_cost1’, 양식에 필드의 인스턴스가 추가될 때마다 이렇게 숫자가 늘어납니다.<br /><br />**참고:** 필드 **설명** 값은 사용자가 필드 위에 커서를 가져가면 필드에 대한 도구 설명 텍스트를 제공합니다.|  
|**이벤트**|**양식 라이브러리**|필드 `OnChange` 이벤트 처리기에서 사용되는 JavaScript 웹 리소스를 지정합니다.<br /><br />|  
||**이벤트 처리기**|필드 `OnChange` 이벤트를 호출해야 하는 함수를 양식 라이브러리에서 구성합니다. 자세한 내용: [이벤트 처리기 구성](configure-event-handlers-legacy.md)|  
|**비즈니스 규칙**|**비즈니스 규칙**|이 필드를 참조하는 비즈니스 규칙을 보고 관리합니다. 추가 정보: [비즈니스 규칙 및 추천 만들기](create-business-rules-recommendations-apply-logic-form.md)|  
|**컨트롤**|**컨트롤**|웹, 전화 및 태블릿에서 컨트롤을 추가하고 사용 가능 여부를 지정합니다.|  

## <a name="next-steps"></a>다음 단계

[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
