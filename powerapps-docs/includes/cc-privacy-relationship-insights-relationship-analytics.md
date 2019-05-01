---
ms.openlocfilehash: 864bb7bde775f88cdf43ba5c453bd1ff02f81b85
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61577522"
---
포함된 인텔리전스 기능인 관계 분석을 사용하면 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자와 고객 사이의 관계 KPI를 계산하기 위해 사용자 식별이 가능한 정보를 포함한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 고객 데이터가 Azure에서 실행되는 서비스로 전송되어 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에 저장됩니다. 또한 데이터가 일시적으로 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)]에 저장되고 관계 상태 및 추세와 같은 추가 출력을 위해 처리된 다음, 해당 정보가 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]로 반환된 후 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]로 반환됩니다.  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직의 솔루션으로 설치하여 관계 분석 기능을 사용할 수 있습니다. 또한 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 이 솔루션을 제거하여 해당 기능을 나중에 비활성화할 수 있습니다.  
  
 데이터 원본으로 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터를 사용하면 KPI 계산에 사용되고 다른 분석을 만들 수 있는 추가 데이터를 수집하기 위해 최종 사용자 식별 정보를 포함하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 고객 데이터를 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서 [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)]로 보냅니다.  이 기능을 완벽하게 사용하려면 [!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] 관리자가 [!INCLUDE[pn_Exchange](pn-exchange.md)] 애플리케이션의 별도 동의서에 동의해야 합니다.  두 관리자가 해당 제품을 통해 동의한 후에 [!INCLUDE[pn_Exchange](pn-exchange.md)]는 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에 저장되고  [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 관리자가 결정한 대로 KPI 계산 및 잠재적으로 기타 분석을 개선하기 위해 사용되는 이메일 및 모임 메타데이터를 제공합니다. 관계 분석 구성에서 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터를 데이터 원본으로 사용하지 않으면 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터가 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서 제거되지 않습니다.  [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]의 [!INCLUDE[pn_Exchange](pn-exchange.md)] 데이터 제거는 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]에서만 직접 수행할 수 있습니다.  
  
 관계 분석과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 실행 중인 서비스인 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]는 관계 분석 기능에 대한 출력을 계산하기 위해 고객에 대한 개인 식별 정보를 포함하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터를 저장합니다. [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]의 미리 보기는 다음 [미리 보기 기능에 대한 보충 사용 약관](http://go.microsoft.com/fwlink/p/?LinkId=511446)의 적용을 받습니다.  
  
 [Customer Insights 미리 보기에 대해 자세히 알아봅니다](https://azure.microsoft.com/en-us/services/customer-insights/).  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)]는 관계 분석 기능에 대한 출력을 계산하기 위해 고객에 대한 개인 식별 정보를 포함하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터를 임시로 저장하는 데 사용됩니다.