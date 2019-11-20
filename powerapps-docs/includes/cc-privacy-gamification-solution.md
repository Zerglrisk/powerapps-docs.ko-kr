[!INCLUDE[pn_gamification](pn-gamification.md)] 솔루션을 설치하여 활성화함으로써 활성화하는 사용자의 계정 ID(예: 이름, 성 및 이메일 주소)가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 저장되어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 호스팅되는 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 서비스를 승인할 수 있습니다. 이는 관리자가 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 서비스에 활성화한 모든 사용자에게 적용됩니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 솔루션이 관리자에 의해 구성된 핵심 성과 지표(KPI) 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스에 보내면, 해당 데이터는 Blob Storage 뿐만 아니라 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구조 저장소에도 저장됩니다.  각 사용자의 아바타, 맞춤 어워드 및 회사 로고는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 저장되지만, 그 정보가 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]에 반환되지는 않습니다.  
  
관리자와 권한이 부여된 사용자는 전화 통화, 영업 기회 및 예약 수익과 같은 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 데이터를 활용하여 게임에서 사용할 KPI를 구성할 수 있습니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 서비스는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]의 호출을 개시하지 않으며 KPI가 사용되고 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]으로 흘러가는 게임 같은 데이터에만 응답합니다.  
  
또한 관리자는 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV 스트림이 공개되도록 활성화할 수 있습니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV 스트림을 설정하고 공개 스트리밍을 활성화하는 게임 관리자는 인터넷 상에서 스트림 링크를 가진 사람은 누구든 TV 스트림을 볼 수 있도록 할 것입니다.  
  
그후에 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 이 솔루션을 제거함으로써 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 기능을 제거할 수 있습니다.  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]와 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[클라우드 서비스](https://azure.microsoft.com/services/cloud-services/)  
  
 **디자이너 서비스(웹 역할)**  
  
이것은 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직과 다중 테넌트 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 사이의 통신을 위한 여러 웹 서비스를 제공합니다. 예: [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 저장소에 저장되는 Gamification 세부 정보.  게임 계산은 [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] 큐를 사용하여 반환되어 채점되며 서비스에 표시됩니다.  고객과 사용자가 업로드한 이미지는 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]에 저장됩니다. 모든 요청은 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]에 대해 인증됩니다.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
모든 서비스는 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]에 구성 데이터를 저장합니다.  
  
[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은 SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]를 사용하여 다음을 저장합니다.  
  
- KPI 데이터  
  
- 게임 계산  
  
- 조직(테넌트) 데이터  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
아바타, 회사 로고 및 기타 고객이 업로드한 이미지는 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]에 저장됩니다.  
  
[Azure Content Delivery Network(CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network를 사용하여 이미지(고객 로고 같은 업로드된 이미지 포함), [!INCLUDE[pn_JavaScript](pn-javascript.md)] 및 CSS 같은 정적 콘텐츠를 런타임에 제공합니다.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]을 사용하여 사용자를 인증하고 플랫폼을 사용할 수 있는 자격을 판단합니다.