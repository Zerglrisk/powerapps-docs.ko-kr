---
ms.openlocfilehash: dff813dcdf6d025ba47e29699e2047f79cf85600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225481"
---
관련성 검색을 사용하여 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스에서 엔터티 및 특성에 포함된 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 인덱스와 동기화되고 해당 인덱스에 저장되기 시작합니다.  
  
 관련성 검색은 기본적으로 사용되지 않습니다. 시스템 관리자는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스 내에서 기능을 사용해야 합니다. 관련성 검색을 사용하면 시스템 관리자와 사용자 지정자는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 인덱스에 동기화된 데이터를 완벽히 제어할 수 있습니다.  
  
 시스템 사용자는 **사용자 지정 도구**에서 **관련성 검색 구성** 대화 상자를 사용하여 검색에 대해 특정 엔터티를 사용하도록 설정한 다음, 사용된 엔터티에서 빠른 찾기 보기를 구성하여 검색 가능한 특성을 선택할 수 있습니다. 데이터 변경 내용은 보안 연결을 통해 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]와 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 간에 지속적으로 간에 동기화됩니다.  구성 데이터를 암호화하고 필수 암호를 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]에 저장합니다.  
  
 관련성 검색 기능과 관련된 Azure 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Search 서비스](https://azure.microsoft.com/services/search/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 인덱스를 사용하여 응답 시간이 빠른 뛰어난 품질의 검색 결과를 제공할 수 있습니다.  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색은 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]에 강력하고 정교한 차세대 검색 기능을 추가합니다.  이 기능은 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]에서 제공한 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 외부에 전용 검색 서비스를 제공합니다. 새로운 모든 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 인덱스는 미사용 시 암호화됩니다.  2018년 1월 24일 전에 옵트인한 경우 관련성 검색을 옵트아웃하고, 한 시간을 대기하고, 다시 옵트인하여 데이터를 다시 인덱스해야 합니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 관련성 검색은 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]를 사용하여 다음 내용을 저장합니다.  
  
-   조직 및 해당 인덱스와 관련된 구성 데이터  
  
-   검색 서비스 및 인덱스와 관련된 메타데이터  
  
-   변경 내용을 동기화하는 경우 시스템 메타데이터 및 데이터에 대한 포인터  
  
-   향상된 행 수준 보안을 사용하는 권한 부여 데이터  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] 구성 요소를 사용하여 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]와 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 간의 메시지를 교환하고, 동기화 프로세스에 의해 관리되는 작업 항목을 유지 관리합니다. 각 메시지는 조직 ID 및 엔터티 이름과 같은 정보를 저장하여 데이터를 동기화하는 데 사용합니다.  
  
[Azure Service Fabric 클러스터](https://azure.microsoft.com/services/service-fabric/)  
  
데이터의 처리 및 인덱싱은 Service Fabric 런타임을 통해 관리되는 가상 머신에 배포된 마이크로 서비스에서 처리됩니다. 또한 검색 API 및 데이터 동기화 프로세스는 Service Fabric 클러스터에서 호스팅됩니다.  
  
Service Fabric은 업무에 중요 한 클라우드 서비스를 제공 하는 Microsoft의 몇 년간의 경험을 통해 개발 되었으며, 이제 5 년간 프로덕션에서 검증 되었습니다. Service Fabric은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 핵심 인프라를 실행하는 기본 기술이며 [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 및 [!INCLUDE[pn_cortana](pn-cortana.md)] 등의 서비스를 제공하고 초당 5억개 이상의 평가를 처리하도록 확장될 수 있습니다.  
  
[Azure Virtual Machine Scale Sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Machine Scale Sets는 탄력적이며 하이퍼 스케일 아웃 워크로드를 지원하도록 설계되었습니다. [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 클러스터는 가상 머신 확장 집합에서 실행됩니다. 데이터를 처리하고 인덱싱하기 위한 마이크로 서비스는 확장 집합에서 호스팅되며 Service Fabric 런타임에서 관리됩니다.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]는 검색 프로세스에서 사용하는 인증서, 키 및 기타 암호의 보안 관리에 사용됩니다.  
  
[Azure Storage(Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
[!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)]에서 최대 2일 동안 고객 데이터의 변경 내용을 저장합니다.  이러한 Blob은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK의 최신 기능을 활용하여 암호화됩니다. 여기에서는 대칭과 비대칭 암호화 지원 및 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]와 통합을 제공합니다. [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)]에서 이메일 메시지의 메모 및 첨부 파일에서 찾을 수 있는 문서 및 약속은 Blob 스토리지에 동기화될 수도 있습니다.  
  
[Azure Active Directory Service](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]와 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 서비스 간의 인증에 사용됩니다.  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer는 클라우드 서비스의 정상 서비스 인스턴스 또는 부하 분산 장치에서 정의된 가상 머신 간에 들어오는 트래픽을 분산하는 데 사용됩니다. 관련성 검색은 이 기능을 사용하여 배포에서 엔드포인트의 부하를 분산합니다.  
  
[Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
하나 이상의 서브넷에서 실행되는 Service Fabric 클러스터의 Virtual Machines는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 가상 네트워크에서 연결됩니다. 보안 정책, DNS 설정, 경로 테이블 및 IP 주소는 이 가상 네트워크 내에서 완벽하게 제어됩니다. 네트워크 보안 그룹을 활용하여 이 가상 네트워크에서 보안 규칙을 적용합니다. 이러한 규칙은 가상 네트워크의 VM에 대한 네트워크 트래픽을 허용하거나 거부합니다.