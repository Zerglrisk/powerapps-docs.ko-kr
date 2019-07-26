---
ms.openlocfilehash: e9b0446c2fb09cad33f5a3ae4bb69103f7d07d70
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212641"
---
Data Export Service를 사용하여 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 데이터 내보내기 프로필을 활성화하면 프로필에 추가된 엔터티의 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 전송됩니다. 초기 동기화는 내보내기 프로필에 추가된 엔터티와 연결된 모든 데이터를 포함하지만 그 후에 동기화는 Data Export Service에 지속적으로 전송된 새 변경 내용만 포함합니다. Data Export Service로 전송된 데이터는 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 및 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에 일시적으로 저장되고, [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]에서 처리되고, 마지막으로 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구독에서 지정된 대상 데이터베이스로 동기화됩니다(삽입, 업데이트 또는 삭제). 데이터가 동기화된 후 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 및 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에서 삭제됩니다. 데이터 동기화 중에 오류가 있으면 엔터티 유형, 레코드 ID 및 동기화 타임스탬프에 해당하는 최소 데이터는 업데이트되지 않은 레코드의 목록을 다운로드할 수 있도록 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에 저장됩니다.  
  
 관리자는 언제든지 데이터 동기화를 중지하도록 데이터 내보내기 프로필을 비활성화할 수 있습니다. 또한 관리자는 실패한 레코드 로그를 제거하도록 내보내기 프로필을 삭제할 수 있으며 Data Export Service 사용을 중지하도록 Data Export Service 솔루션을 제거할 수 있습니다.  
  
 데이터 동기화는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 및 Data Export Service 간에 안전한 방법으로 지속적으로 발생합니다. 데이터는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 및 Data Export Service 간에 지속적으로 교환되므로 암호화됩니다.  
  
 Data Export Service와 관련된 Azure 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]에서 받은 레코드 동기화 알림을 처리한 다음, 대상 데이터베이스에서 레코드 데이터를 삽입, 업데이트 또는 삭제하도록 처리하기 위한 API 및 컴퓨팅 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] VM을 제공합니다. [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 런타임에서 관리되는 가상 머신에 배포된 마이크로 서비스는 데이터 동기화와 관련된 모든 컴퓨팅 서비스를 처리합니다.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]에서 컴퓨팅 노드에 의해 처리되는 동기화 알림 메시지를 삽입하는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)](으)로 메시지 버스를 제공합니다. 각 메시지는 데이터를 동기화할 org ID 및 레코드와 같은 정보를 저장합니다. Azure Service Bus의 데이터는 미사용 시 암호화되지 않지만 Data Export Service에서만 액세스할 수 있습니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 데이터는 레코드 동기화 알림의 데이터가 메시지에 저장하기에 너무 크거나 동기화 알림을 처리하는 데 일시적인 오류가 발생한 경우 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)]에 임시로 저장됩니다. 이러한 Blob은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK의 최신 기능을 활용하여 암호화됩니다. 여기에서는 대칭과 비대칭 암호화 지원 및 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]와 통합을 제공합니다.  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]은 데이터 내보내기 프로필 구성 및 데이터 동기화 메트릭을 저장합니다.