데이터 내보내기 서비스를 사용하면 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 데이터 내보내기 프로필을 활성화할 때 프로필에 추가된 엔터티의 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]로 전송됩니다. 초기 동기화에는 내보내기 프로필에 추가된 엔터티에 연결된 데이터가 모두 포함되지만 동기화한 후에는 데이터 내보내기 서비스에 지속적으로 전송되는 새로운 변경 내용만 포함됩니다. 데이터 내보내기 서비스에 전송된 데이터는 임시로 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 및 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에 저장되고 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]에서 처리되고, 마지막으로 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구독에 지정된 대상 데이터베이스에 동기화(삽입, 업데이트 또는 삭제)됩니다. 데이터가 동기화된 후에는 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 및 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에서 삭제됩니다. 데이터 동기화 중에 오류가 발생하면, 엔터티 유형, 레코드 ID 및 동기화 타임스탬프에 해당하는 최소 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에 저장되어 업데이트되지 않은 레코드 목록을 다운로드할 수 있습니다.  
  
 관리자는 데이터 내보내기 프로필을 언제든지 활성화하여 데이터 동기화를 중지할 수 있습니다. 또한 관리자는 내보내기 프로필을 삭제하여 실패한 레코드 로그를 제거하고 데이터 내보내기 서비스 솔루션을 제거하여 데이터 내보내기 서비스 사용을 중단할 수 있습니다.  
  
 데이터 동기화는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]과 데이터 내보내기 서비스 간에 안전한 방식으로 지속적으로 일어납니다. 데이터는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]과 데이터 내보내기 서비스 간에 지속적으로 교환될 때 암호화됩니다.  
  
 데이터 내보내기 서비스에 포함된 Azure 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 API를 제공하고 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] VM을 계산하여 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]에서 받은 레코드 동기화 알림을 처리한 후 대상 데이터베이스에서 레코드 데이터를 삽입, 업데이트 또는 삭제하도록 처리합니다. [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 런타임에서 관리되는 가상 컴퓨터에 배포되는 마이크로 서비스는 데이터 동기화와 관련된 모든 계산 서비스를 처리합니다.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]에서 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]의 계산 노드에서 처리되는 동기화 알림 메시지를 삽입하는 메시지 버스를 제공합니다. 각 메시지는 데이터를 동기화하는 데 필요한 조직 id 및 레코드와 같은 정보를 저장합니다. Azure Service Bus의 데이터는 미사용 시 암호화되어 있지 않지만, 데이터 내보내기 서비스에서만 액세스할 수 있습니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 레코드 동기화 알림의 데이터가 너무 커서 메시지에 저장할 수 없거나 일시적 오류가 발생하여 동기화 알림을 처리하지 못할 경우 데이터가 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)]에 임시로 저장됩니다. 이러한 blob는 대칭 및 비대칭 암호화 지원 및 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]와의 통합을 제공하는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK의 최신 기능을 활용하여 암호화됩니다.  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]는 데이터 내보내기 프로필 구성 및 데이터 동기화 메트릭을 저장합니다.