---
ms.openlocfilehash: 252f09737dbf55309a64ef5d02d479fde0e61c0e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224849"
---
포함된 인텔리전스 기능인 이메일 참여 기능을 사용하면, **Follow** 설정으로 표시된 이메일이 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 전송될 때 수신자 활동 KPI 및 "followed" 이메일에 대한 상호 작용을 계산하기 위해 받는 사람이 이메일과 상호 작용하는 정보가 수집되어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 저장됩니다.  
  
 시스템 관리자는 포함된 인텔리전스 내의 **이메일 참여** 탭에서 기능을 프로비저닝하여 이메일 참여를 사용할 수 있습니다. 그런 다음, 관리자는 **설정** 아래의 **인텔리전스 구성** 노드에서 조직의 이메일 참여를 사용하지 않도록 설정할 수 있습니다.  
  
 이 기능을 사용하지 않도록 설정하면 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 보낸 이메일을 사용자 인터페이스 또는 프로그래밍 방식으로 추적할 수 없습니다. 또한 받는 사람 상호 작용 데이터는 **Follow** 설정으로 표시된 보낸 이메일에서 더 이상 수집되지 않습니다. 이전에 수집된 모든 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 남아 있으며, 조직에서 이 기능을 다시 사용하도록 설정하면 다시 사용할 수 있습니다. 데이터는 고객이 Microsoft로 구독을 종료한 후 90일 동안 보존됩니다. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자는 **연락처 환경 설정**에서 **이메일 준수** 설정을 변경하여 연락처별 또는 잠재 고객별로 포함된 인텔리전스 - 이메일 참여 기능을 비활성화할 수도 있습니다.  
  
 이메일 참여 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 아래에 자세히 설명되어 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 이메일 참여 기능은 [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]를 사용하여 이메일 상호 작용 BLOB을 임시로 저장합니다.