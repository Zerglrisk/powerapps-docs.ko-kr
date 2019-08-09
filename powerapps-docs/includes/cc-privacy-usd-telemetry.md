도움말 향상 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 기능은 클라이언트를 설치하는 컴퓨터에서 운영 체제 정보, 브라우저 세부 정보, [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] 응용 프로그램 관련 정보와 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 버전 등의 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 사용 정보를 보냅니다. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]는 조직 인사이트의 보안 연결을 통해 [!INCLUDE[cc_Microsoft](cc-microsoft.md)]에 정보를 보내고 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블 저장소에 저장합니다.
  
> [!NOTE]
>  조직 인사이트는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직의 시스템 관리자에게 어떻게 조직이 사용되고 있는지에 대한 간단한 개요를 제공합니다. 시스템 관리자는 대부분의 활성 사용자, 시작 중인 SDK 요청 수, 보고 있는 SDK 사용자 수 등을 볼 수 있습니다.
  
 Unified Service Desk 개선 기능에 포함되어 있는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스 목록이 아래에 제공됩니다.  
  
> [!NOTE]
>  추가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스 제공 사항에 대한 자세한 내용은 [Microsoft Azure 보안 센터](https://azure.microsoft.com/support/trust-center/)를 참조하십시오.  
  
 [클라우드 서비스](https://azure.microsoft.com/services/cloud-services/) OrgInsights 데이터 REST API(웹 역할)  
  
 이 웹 역할은 조직 인사이트에 데이터를 표시하는 차트의 요청을 수락합니다. API는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블에서 집계된 데이터를 읽고 반환합니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직의 원시 원격 분석 데이터는 모니터링 에이전트(모든 규모의 그룹 컴퓨터에서 실행)에서 수집되고 결합 형식(이진 형식)으로 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 저장소에 업로드됩니다.  
  
 [Azure 테이블 저장소](https://azure.microsoft.com/services/storage/tables/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 저장소의 원시 원격 분석 데이터는 Azure 테이블 저장소에 집계 및 저장되고, 클라우드 서비스에서 판독됩니다.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 조직 인사이트는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 서비스를 사용하여 웹 서비스를 인증합니다.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 모니터링 에이전트는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 저장소에 데이터를 업로드할 때마다 메시지를 만들어 큐에 넣습니다. 이러한 메시지는 업로드한 데이터를 집계하는 CMA 파이프에 의해 선택됩니다.