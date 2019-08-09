학습 경로 기능, 정적 html을 사용하면 이미지와 스크립트를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] CDN(콘텐츠 배달 네트워크)에 저장할 수 있습니다. 또한 표시되는 모든 동적 콘텐츠는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 데이터베이스에서 사전 캐시하는 데 사용되는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache에 저장됩니다.  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 문제 해결 도우미 사용 설정을 통해 [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] 인스턴스 내에서 학습 경로 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.  
  
 학습 경로 기능에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
> [!NOTE]
>  추가 Azure 서비스 제품에 대한 자세한 내용은 [Microsoft Azure 보안 센터](https://azure.microsoft.com/support/trust-center/)를 참조하십시오.  
  
 [클라우드 서비스](https://azure.microsoft.com/services/cloud-services/)  
  
 **학습 경로 런타임(웹 역할)**  
  
 사용자에게 콘텐츠를 제공하는 웹 응용 프로그램입니다.  
  
 **학습 경로 서비스(작업자 역할)**  
  
 작업자 역할은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 데이터베이스에서 데이터를 처리하고 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache에 캐싱하는 작업을 담당합니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 학습 경로는 SQL 데이터베이스를 사용하여 다음을 저장합니다.  
  
-   내용  
  
-   콘텐츠 메타데이터  
  
-   시스템 메타데이터  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 HTML, 이미지, [!INCLUDE[pn_JavaScript](pn-javascript.md)], 및 CSS는 모두 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 저장소에 저장됩니다.  
  
 [Azure 콘텐츠 배달 네트워크(CDN)](https://azure.microsoft.com/services/cdn/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 콘텐츠 배달 네트워크를 사용하여 정적 콘텐츠를 HTML, 이미지, [!INCLUDE[pn_JavaScript](pn-javascript.md)] 및 CSS와 같은 설문 런타임에 제공합니다.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 학습 경로는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 서비스를 사용하여 디자이너에 대해 구체적으로 웹 서비스를 인증합니다. 현재 디자이너는 고객 및 파트너에게 노출되지 않습니다. 따라서 인증은 [!INCLUDE[cc_Microsoft](cc-microsoft.md)] 도메인 내에만 있습니다.  
  
 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache를 사용하여 사용자에게 제공되는 동적 콘텐츠를 캐싱합니다.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/)  
  
 학습 경로는 트래픽 관리자를 통해 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 또는 외부 사이트 및 서비스를 모니터링하고 오류가 있을 경우 언제든지 자동으로 사용자를 새로운 위치로 안내하여 중요한 응용 프로그램의 가용성을 향상시킵니다.  
  
 [Azure 리소스 관리자](https://azure.microsoft.com/features/resource-manager/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 리소스 관리자를 사용하여 CDN, Redis Cache, SQL 데이터베이스 및 클라우드 서비스를 일정한 상태를 유지하고 반복해서 배포할 수 있도록 리소스 그룹으로 배포합니다.