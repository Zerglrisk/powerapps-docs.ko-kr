---
title: PowerApps에서 시스템 엔터티 메시지 편집 | MicrosoftDocs
description: 시스템 엔터티 메시지를 편집하는 방법 알아보기
ms.custom: ''
ms.date: 05/15/2018
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
ms.assetid: 3ccbd8de-8d6f-4058-87f7-15463667cfc6
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f90f2fc6f3a4eb0707eda9d9ce73acfc422ed5d9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705410"
---
# <a name="edit-system-entity-messages"></a>시스템 엔터티 메시지 편집

일부 시스템 엔터티의 기본 표시 이름은 사용자 인터페이스 텍스트 및 Common Data Service의 오류 메시지에 사용됩니다. 표시 이름을 변경할 경우 기본 표시 이름을 사용하는 모든 메시지도 업데이트해야 합니다. 예를 들어 *거래처*의 표시 이름을 *회사*로 변경하면 이전 이름을 사용하는 오류 메시지를 계속 볼 수 있습니다.  

PowerApps 포털을 사용하여 시스템 메시지를 편집할 수 없으며 솔루션 탐색기를 사용해야 합니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

솔루션 탐색기에서 엔터티 아래에 **메시지** 노드가 보이면 원래 엔터티 표시 이름에 대한 참조가 포함되어 있는 특정 텍스트를 편집할 수 있습니다. 

![엔터티 메시지](../model-driven-apps/media/entity-messages.png)

이 텍스트를 편집하는 것은 간단합니다. 메시지를 두 번 클릭하여 필드 세 개가 포함된 양식을 표시합니다.  
  
|필드|설명|  
|-----------|-----------------|  
|**기본 표시 문자열**|원본 텍스트를 표시합니다.|  
|**사용자 지정 표시 문자열**|표시 문자열을 변경하려면 이 텍스트를 편집합니다.|  
|**Comment(설명)**|선택 사항. 변경 내용과 변경 이유에 대한 설명을 포함합니다.|  
  
일부 메시지 텍스트에는 자리 표시자가 있을 수 있습니다. 이러한 자리 표시자는 양쪽에 대괄호를 사용하는 숫자입니다. 예: `{0}`. 메시지의 텍스트에 이러한 자리 표시자를 삽입할 수 있습니다. 메시지를 편집할 경우 이러한 자리 표시자를 유지해야 합니다. 

![저장](media/save-entity-icon-solution-explorer.png)을 선택하여 변경 내용을 저장합니다. 저장할 때 **저장 후 닫기**를 선택하여 양식을 닫습니다.

> [!NOTE]
> 시스템 엔터티 메시지 편집에 노출된 UI에는 엔터티 이름에 대한 참조가 많이 포함되어 있지만 이를 모두 포함하지는 않습니다. 보다 포괄적인 방법은 [기본 언어로 지역화 가능한 텍스트 업데이트](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)를 참조하십시오.

## <a name="programmatically-update-entity-display-strings"></a>프로그래밍 방식으로 엔터티 표시 문자열 업데이트

코드에서 이러한 작업을 하는 방법을 찾는 개발자의 경우 표시 문자열은 [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md) 엔터티에 저장 됩니다. 

`DisplayString` 엔터티에는 기본 표시 문자열이 포함되지 않습니다. 텍스트가 포함된 이 엔터티에 대한 특성 두 가지는 [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) 및 [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString)입니다. 표시 문자열을 사용자 지정하지 않은 경우 기본적으로 이러한 특성 값은 null이고 게시됩니다. `PublishedDisplayString` 값은 읽기 전용이며 현재 게시된 `CustomDisplayString`을 반영합니다.
 
## <a name="see-also"></a>참조
[엔터티 편집](edit-entities.md)<br />
[모델 기반 앱의 지역화 가능한 텍스트 번역](../model-driven-apps/translate-localizable-text.md)
