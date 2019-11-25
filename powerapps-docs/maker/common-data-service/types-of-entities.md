---
title: 엔터티 유형 | MicrosoftDocs
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2587dbcd76fe228ed017b2832bb37d05f6a1e884
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703298"
---
# <a name="types-of-entities"></a>엔터티 타입

Common Data Service에서 엔터티를 만들거나 편집하기 전에 다른 유형의 엔터티가 있다는 것을 알고 있어야 합니다. 사용자 지정 엔터티를 만든 후에는 이러한 유형을 변경할 수 없습니다. 주요 두 부문은 엔터티 소유권 형태와 엔터티가 활동 엔터티인지 여부에 따라 달라집니다.  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>엔터티 소유권 형태  

엔터티 소유권의 유형은 4가지입니다. 사용자 지정 엔터티를 만들 때 유일한 옵션은 **사용자 또는 팀 담당**이거나 **조직 담당**이지만 다른 엔터티에는 다른 유형의 소유권 형태가 있습니다.  
  
|소유권 형태|설명|  
|---------------|-----------------|  
|**업무 담당**|이러한 엔터티의 데이터는 사업부에 속합니다. 데이터에 대한 액세스는 비즈니스 단위 수준에서 제어할 수 있습니다.|  
|**없음**|다른 엔터티가 소유하지 않은 데이터입니다.|  
|**조직 담당**|데이터는 조직에 속합니다. 데이터에 대한 액세스는 조직 수준에서 제어됩니다.|  
|**사용자 또는 팀 담당**|데이터는 사용자 또는 팀에 속합니다. 이러한 레코드에 대해 수행할 수 있는 작업은 사용자 수준에서 제어할 수 있습니다.|  
  
  
> [!IMPORTANT]
>  엔터티를 만든 후 소유권 형태를 변경할 수 없습니다. 엔터티를 만들기 전에 올바른 유형의 소유권 형태를 선택해야 합니다. 나중에 사용자 지정 엔터티가 다른 유형이어야 한다고 결정하면 삭제하고 새 엔터티를 만들어야 합니다.
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>활동 엔터티

활동은 달력에서 항목을 만들 수 있는 작업으로 생각할 수 있습니다. 활동에는 작업이 발생한 시간 또는 발생할 시간을 결정하는 데 도움이 되는 시간 크기(시작 시간, 중지 시간, 기한 및 기간)이 있습니다. 활동에는 제목 및 설명과 같이 활동에서 나타낼 작업을 결정하는 데 도움이 되는 데이터도 포함됩니다. 활동은 시작하거나, 취소하거나, 완료할 수 있습니다. 완료된 상태의 활동에는 활동이 완료된 방법을 명확히 하기 위해 관련된 여러 가지 하위 상태 값이 있습니다.  
  
활동 엔터티는 사용자 또는 팀에서만 담당할 수 있으며 조직에서 담당할 수 없습니다.  
  
다음 표에는 Common Data Service 기본 환경에서 사용할 수 있는 활동 엔터티가 나열되어 있습니다.
  
|이름|설명|활동 메뉴에 표시|참조|
|----------|-----------------|----------------|---------------|  
|**약속**|시작/종료 시간 및 기간으로 시간 간격을 표시하는 약정입니다.|지원|[약속](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|전자 메일 프로토콜을 사용하여 배달된 활동입니다.|지원|[Email](/powerapps/developer/common-data-service/reference/entities/email)|
|**팩스**|팩스의 통화 결과 및 페이지 수를 추적하고 선택적으로 문서의 전자 복사본을 저장하는 활동입니다.|지원|[팩스](/powerapps/developer/common-data-service/reference/entities/fax)|
|**편지**|편지 배달을 추적하는 활동입니다. 활동에는 편지 전자 사본이 포함될 수 있습니다.|지원|[편지](/powerapps/developer/common-data-service/reference/entities/letter)|
|**전화 통화**|전화 통화를 추적하는 활동입니다.|지원|[PhoneCall](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**되풀이 약속**|되풀이 약속 시리즈의 마스터 약속입니다.|지원|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**작업**|수행해야 할 작업을 나타내는 일반 활동입니다.|지원|[작업](/powerapps/developer/common-data-service/reference/entities/task)|
  
새 사용자 지정 활동 엔터티를 만들 수 있습니다. 예를 들어 사용자 지정 활동 엔터티를 만들어 인스턴스 메시지 통신을 기록할 수 있습니다. 활동 엔터티를 만드는 것은 기본 필드를 지정하지 않으므로 비활동 엔터티를 만드는 것과 다릅니다. 모든 활동 엔터티에는 **제목**으로 설정된 **기본 필드**와 활동 엔터티에서 정의되는 다른 공통 필드가 있습니다. 따라서 공통 필드가 표시되는 보기에 모든 유형의 활동을 표시할 수 있습니다.  

> [!NOTE]
> PowerApps 포털을 사용하여 사용자 지정 활동을 만들 수 없습니다. **고급** 단추를 사용하여 솔루션 탐색기를 열어야 합니다.
  
사용자 지정 활동 엔터티를 만들려면 **활동 엔터티로 정의**를 선택합니다. 이 옵션을 선택하면 **활동 메뉴에 표시**가 선택됩니다. 이 설정을 사용하면 활동 메뉴에서 이 유형의 활동을 만들 수 있습니다. 이 설정은 일반적으로 특정 이벤트에 연결되고 코드를 사용하거나 워크플로로 뒤에서 만든 활동에 대해 선택되지 않습니다. 엔터티를 저장한 후 이러한 설정을 변경할 수 없습니다.  

### <a name="see-also"></a>참조
[엔터티 만들기 또는 편집](create-edit-entities.md)
