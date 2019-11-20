관련성 검색 기능을 사용하면 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스에서 엔터티 및 특성에 관여하는 데이터가 동기화되기 시작하고 결국 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 색인에 저장됩니다.  
  
 관련성 검색은 기본적으로 활성화되어 있지 않습니다. 시스템 관리자는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스에서 해당 기능을 활성화해야 합니다. 관련성 검색을 활성화한 후에 시스템 관리자 및 사용자 지정자는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 색인에 동기화되는 데이터에 대한 전체 컨트롤을 갖게 됩니다.  
  
 시스템 사용자 지정자는 **사용자 지정 도구**에서 **관련성 검색 구성** 대화 상자를 사용하여 검색할 특정 엔터티를 활성화한 후 활성화된 엔터티에 대해 빠른 찾기 보기를 구성하여 검색 가능한 특성을 선택할 수 있습니다. 데이터 변경 내용은 보안 연결을 통해 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]과 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 사이에서 지속적으로 동기화됩니다.  구성 데이터는 암호화되고 필요한 암호는 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]에 저장됩니다.  
  
 관련성 검색 기능에 포함된 Azure 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure 검색 서비스](https://azure.microsoft.com/services/search/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 색인은 빠른 응답 시간과 함께 고품질 검색 결과를 제공하는 데 사용됩니다.  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색은 강력하고 정교한 차세대 검색 기능을 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]에 추가합니다.  [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]에서 제공하는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 외부의 전용 검색 서비스입니다. 모든 새로운 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 검색 인덱스는 암호화됩니다.  2018년 1월 24일 이전에 선택한 경우 관련성 검색을 선택 해제하고 1시간 동안 기다렸다가 다시 선택하여 데이터를 다시 인덱싱해야 합니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 관련성 검색은 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]를 사용하여 다음을 저장합니다.  
  
-   조직 및 해당 색인과 관련된 구성 데이터  
  
-   검색 서비스 및 색인과 관련된 메타데이터  
  
-   변경 내용을 동기화할 때 시스템 메타데이터 및 데이터에 대한 포인터  
  
-   향상된 행 수준 보안을 활성화하는 권한 부여 데이터  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] 구성 요소는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]과 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 사이의 메시지 교환에 사용되고 동기화 프로세스에서 관리되는 작업 항목을 유지 관리하는 데 사용됩니다. 각 메시지는 데이터를 동기화하는 데 사용되는 조직 ID 및 엔터티 이름과 같은 정보를 저장합니다.  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
데이터 처리 및 인덱싱은 Service Fabric 런타임을 통해 관리되는 가상 컴퓨터에서 마이크로 서비스로 처리됩니다. 검색 API 및 데이터 동기화 프로세스도 Service Fabric 클러스터에서 호스팅됩니다.  
  
Service Fabric은 Microsoft에서 임무 수행에 필수적인 클라우드 서비스를 제공하는 다년간의 경험에서 탄생하여 이제 5년 이상 생산이 입증되었습니다. [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 및 [!INCLUDE[pn_cortana](pn-cortana.md)] 등의 서비스를 강화하여 초당 5억개 이상의 평가를 처리하도록 확장할 수 있는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 핵심 인프라를 실행하는 기초 기술입니다.  
  
[Azure Virtual Machine Scale Sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Machine Scale Sets은 탄력적이며 하이퍼 규모 확장 작업 부하를 지원하도록 설계되었습니다. [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 클러스터는 가상 컴퓨터 크기 집합에서 실행됩니다. 데이터 처리 및 색인 처리를 위한 마이크로 서비스는 Service Fabric 런타임에서 관리되는 Scale Sets에서 호스팅됩니다.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]은 검색 프로세스에 사용되는 인증서, 키 및 기타 암호의 보안 관리에 사용됩니다.  
  
[Azure Storage(Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
고객 데이터의 변경 내용은 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)]에 최대 2일 동안 저장됩니다.  이러한 Blob는 대칭 및 비대칭 암호화 지원 및 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]와의 통합을 제공하는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK의 최신 기능을 활용하여 암호화됩니다. [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)]을 사용하면 메모에서 발견되는 문서와 이메일 메시지 및 약속의 첨부도 Blob Storage에 동기화됩니다.  
  
[Azure Active Directory 서비스](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]는 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]과 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 서비스 사이를 인증하는 데 사용됩니다.  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer는 부하 분산 집합에 정의된 클라우드 서비스 또는 가상 컴퓨터의 정상적인 서비스 인스턴스에 수신 트래픽을 배포하는 데 사용됩니다. 관련성 검색은 이를 사용하여 배포 시 끝점의 부하를 분산합니다.  
  
[Azure 가상 네트워크](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
하나 이상의 서브넷에서 실행 중인 Service Fabric 클러스터의 Virtual Machines은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 가상 네트워크에 연결됩니다. 보안 정책, DNS 설정, 경로 테이블 및 IP 주소는 이 가상 네트워크에서 완벽하게 제어됩니다. 네트워크 보안 그룹은 이 가상 네트워크에 보안 규칙을 적용하는 데 활용됩니다. 이러한 규칙은 가상 네트워크의 VM에 대한 네트워크 트래픽을 허용하거나 거부합니다.