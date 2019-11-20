임베디드 인텔리전스 기능의 하나인 관계 분석을 사용함으로써 사용자 식별 가능한 정보를 포함한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 고객 데이터는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자와 고객 간의 관계 KPI를 계산할 목적으로 Azure에서 실행되는 서비스인 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에 전송되고 저장됩니다. 또한 데이터는 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)]에 임시로 저장되고 관계 상태 및 추세 같은 추가 출력을 위해 처리되고 해당 정보는 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]에 반환되고 이후에 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 반환됩니다.  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 하나의 솔루션으로 관계 분석 기능을 설치하여 사용할 수 있습니다. 또한 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 이 솔루션을 제거하여 기능을 사용하지 않을 수 있습니다.  
  
 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터를 데이터 원본으로 사용함으로써 KPI를 계산하고 다른 분석을 생성하는 데 사용될 추가 데이터를 수집할 목적으로 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서 [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)]으로 최종 사용자 식별 가능한 정보를 포함한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 고객 데이터를 전송합니다.  이 기능을 완벽하게 사용하려면 [!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] 관리자 권한이 있어야 하며 [!INCLUDE[pn_Exchange](pn-exchange.md)] 응용 프로그램에서 별도의 동의서에 동의해야 합니다.  두 관리자가 해당 제품을 통해 동의를 제공하고 나면 [!INCLUDE[pn_Exchange](pn-exchange.md)]는 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 관리자가 결정한 대로 KPI 계산 및 기타 분석을 개선할 목적으로 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에 저장되고 사용될 전자 메일과 모임 메타데이터를 제공합니다. 관계 분석 구성에서 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터를 데이터 원본으로 사용하지 않도록 설정하면 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터가 제거되지 않습니다.  [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터를 제거하는 작업은 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서만 직접 수행할 수 있습니다.  
  
 관계 분석에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 실행 중인 서비스인 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]는 관계 분석 기능을 위한 출력을 계산할 목적으로 고객에 대한 개인 식별 가능한 정보를 포함한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터를 저장합니다. [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]의 미리 보기는 이러한 [미리 보기에 대한 보충 사용 약관](https://go.microsoft.com/fwlink/p/?LinkId=511446)이 적용됩니다.  
  
 [Customer Insights의 미리 보기에 대해 자세히 알아보십시오.](https://azure.microsoft.com/services/customer-insights/)  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)]은 관계 분석 기능을 위한 출력을 계산할 목적으로 고객에 대한 개인 식별 가능한 정보를 포함한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터를 임시 저장하는 데 사용됩니다.