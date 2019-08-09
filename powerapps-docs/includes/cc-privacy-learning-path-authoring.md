[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직에 대해 학습 경로 작성 기능을 사용하면 올바른 보안 권한을 가진 사용자가 만든 학습 경로 콘텐츠(게시됨 또는 초안)는 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]에 저장됩니다. 또한 이 기능을 사용하면 [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)]에서 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직 관련 다음 데이터를 캡처할 수 있습니다.  
  
-   테넌트의 조직 목록  
  
-   최종 사용자의 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 클라이언트 및 해당 브라우저/OS 구성  
  
-   최종 사용자의 사용 데이터 – 학습 경로에 사용된 시간 또는 기록된 클릭  
  
-   집계된 최종 사용자 데이터 – 위치, 보안 역할, 사용자 언어  
  
-   집계된 최종 사용자 데이터 – 위치, 보안 역할, 사용자 언어  
  
-   최종 사용자의 원문 피드백  
  
 관리자는 **시스템 설정** 대화 상자의 **일반** 탭의 설정을 통해 학습 경로 작성 기능을 사용하도록 설정하고 다시 사용하지 않도록 설정할 수 있습니다.  
  
 학습 경로 작성 기능에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **웹 서비스**  
  
 웹 서비스는 학습 경로 런타임에 클라이언트에서 렌더링되는 컨트롤을 제공합니다. 웹 서비스는 학습 경로 작성에서 사용되는 디자이너 API도 지원합니다. 컨트롤은 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]의 서비스에 저장됩니다.  
  
 **컴파일러(작업자 역할)**  
  
 컴파일러 역할은 게시 그룹에 대한 컨트롤의 게시를 관리합니다. 컴파일러는 큐를 사용하여 게시 작업에 대한 메시지를 저장합니다. 결과는 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]에 저장됩니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 학습 경로는 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]를 사용하여 다음을 저장합니다.  
  
-   학습 경로를 사용하여 생성된 컨트롤.  
  
-   구성 관련 학습 경로 작성.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 학습 경로는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]를 사용하여 웹 서비스를 인증합니다.  
  
 [Azure 트래픽 관리자](https://azure.microsoft.com/services/traffic-manager/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Traffic Manager를 사용하여 가용성과 성능을 위해 웹 서비스의 부하를 분산합니다.  
  
 [Azure Storage 큐](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage 큐는 웹 서비스와 컴파일러 역할 간의 통신을 조정하는 데 사용됩니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 학습 경로는 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]를 사용하여 정적 콘텐츠(클라이언트 측 [!INCLUDE[pn_JavaScript](pn-javascript.md)], 이미지, CSS 콘텐츠)를 저장합니다.  
  
 [Azure 콘텐츠 배달 네트워크(CDN)](https://azure.microsoft.com/services/cdn/)  
  
 CDN은 클라이언트 측 정적 콘텐츠([!INCLUDE[pn_JavaScript](pn-javascript.md)], 이미지 및 CSS 파일)를 전역 CDN 네트워크에서 제공하기 위해 캐시하는 데 사용됩니다.