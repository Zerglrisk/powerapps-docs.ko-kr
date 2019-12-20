---
title: Power Apps에서 상태 설명 전환 정의 | MicrosoftDocs
description: 상태 설명 전환을 정의하는 방법 알아보기
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5dd257a07a21b2d0b0d2a449feb9df855d51d604
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861122"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>서비스 케이스 또는 사용자 지정 엔터티에 대한 상태 설명 전환 정의

인시던트(**서비스 케이스**) 엔터티 또는 사용자 지정 엔터티에 대한 상태 설명 전환을 지정할 수 있습니다.

> [!NOTE]
> 인시던트(서비스 케이스) 엔터티는 기본 Common Data Service 환경에 포함되지 않지만 [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/)에서 사용되고 [Common Data Model](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json) 내에서 정의됩니다.
  
상태 설명 전환은 각 상태 설명에 대해 변경될 수 있는 상태 설명 값을 정의하는 선택적인 추가 필터링 수준입니다. 제한된 올바른 옵션 목록을 정의하면 올바른 상태 설명 값의 조합을 많이 사용할 때 사람들이 레코드에 대해 올바른 다음 상태 설명을 쉽게 선택할 수 있습니다.  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>상태 및 상태 설명 필드 간 연결이란 무엇입니까?  

다른 상태 값을 사용할 수 있는 엔터티는 다음 데이터를 캡처하는 두 필드가 있습니다.  
  
|표시 이름|설명|  
|------------------|-----------------|  
|**상태**|레코드의 상태를 나타냅니다. 일반적으로 **활성** 또는 **비활성**입니다. 새 상태 옵션을 추가할 수 없습니다.|  
|**상태 설명**|특정 상태에 연결되어 있는 설명을 나타냅니다. 각 상태에는 가능한 상태 설명이 하나 이상 있어야 합니다. 추가 상태 설명 옵션을 추가할 수 있습니다.|  
  
필드에 대한 메타데이터는 지정된 상태에 대해 유효한 상태 값을 정의합니다. 예를 들어 인시던트(**서비스 케이스**) 엔터티의 경우 기본 상태 및 상태 설명 옵션은 다음과 같습니다.  
  
|상태|상태 설명|  
|------------|-------------------|  
|**활성**|<li>**진행 중**</li><li>**보류 중**</li><li>**세부 정보 대기**</li><li>**연구 중**</li>| 
|**해결됨**|<li>**문제점 해결됨**</li><li>**정보 제공됨**</li>|
|**취소됨**|<li>**취소됨**</li><li>**병합됨**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>상태 설명 전환 편집
 
서비스 케이스 엔터티와 사용자 지정 엔터티에 대한 상태 설명 필드 옵션을 수정하여 사람들이 선택할 수 있는 다음 상태 설명 옵션을 정의할 수 있습니다. 유일한 제한 사항은 활성 상태에 대한 각 상태 설명 옵션은 비활성 상태에 대한 하나 이상의 경로를 허용해야 한다는 것입니다. 그렇지 않을 경우 서비스 케이스를 해결하거나 취소할 수 없는 조건을 만들 수 있습니다.  

> [!NOTE]
> 상태 설명 변환을 편집하려면 솔루션 탐색기를 사용해야 합니다. 필드를 편집하는 방법에 대한 자세한 내용은 [Power Apps 솔루션 탐색기를 사용하여 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md)을 참조하십시오.
  
 상태 설명 필드를 편집하면 **상태 설명 전환 편집** 단추가 메뉴에 표시됩니다. 

![상태 설명 전환 편집 명령](media/status-reason-transitions-command.png)

이 단추를 클릭하면 **상태 설명 전환** 대화 상자에서 **상태 설명 전환 사용**을 선택할 수 있는 옵션을 제공합니다. 이 옵션을 선택하면 각 상태 설명에 허용되는 *기타* 상태 설명 값을 정의해야 합니다. 적용된 필터링을 제거하려면 **상태 설명 전환 사용** 선택을 취소합니다. 정의한 전환은 유지되지만 적용되지 않습니다.  
  
다음 스크린샷은 다음 요구 사항을 충족하는 예를 제공합니다. 
 
- 서비스 케이스는 언제든지 병합할 수 있습니다. 상태 설명 전환에서 허용하지 않을 경우 서비스 케이스를 병합할 수 없습니다.  
- 활성 서비스 케이스는 언제든지 취소할 수 있습니다.  
- 해결되거나 취소된 서비스 케이스는 다시 활성화할 수 없습니다.  
- 모든 서비스 케이스는 해결하려면 **진행 중** > **보류 중** > **세부 정보 대기** > **연구 중** 스테이지를 모두 통과해야 합니다. 이 구성에서는 서비스 케이스를 이전 상태로 설정할 수 없습니다.  
  > [!NOTE]
  >  이는 실제 작업에 대한 좋은 예는 아니지만 상태 스테이지가 상태 설명 전환을 통해 적용될 수 있는 방법을 보여 줍니다.  
  
 ![서비스 케이스에 대한 상태 설명 전환의 예](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>참고 항목  

[Power Apps 솔루션 탐색기를 사용하여 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md)<br />
[엔터티 메타데이터 > 엔터티 상태](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[사용자 지정 상태 모델 전환 정의](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

