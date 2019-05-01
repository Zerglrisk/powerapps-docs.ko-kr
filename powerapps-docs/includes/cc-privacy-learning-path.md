---
ms.openlocfilehash: 3840a097743111f6ae89e65426a366207f8364d9
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61574919"
---
정적 html인 학습 경로 기능을 사용하도록 설정하면 이미지 및 스크립트를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] CDN(Content Delivery Network)에 저장할 수 있습니다. 또한 표시되는 모든 동적 콘텐츠는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 데이터베이스에서 사전 캐시하는 데 사용되는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache에 저장됩니다.  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직의 도움말 사용 설정을 사용하여 [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] 인스턴스 내에서 학습 경로 기능을 활성화 및 비활성화할 수 있습니다.  
  
 학습 경로 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
> [!NOTE]
>  추가 Azure 서비스 제공에 대한 자세한 내용은 [Microsoft Azure 보안 센터](https://azure.microsoft.com/en-us/support/trust-center/)를 참조하세요.  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/)  
  
 **학습 경로 런타임(웹 역할)**  
  
 이는 사용자에게 콘텐츠를 제공하는 웹 애플리케이션입니다.  
  
 **학습 경로 서비스(작업자 역할)**  
  
 작업자 역할은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Database에서 데이터를 처리하고 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache에 캐시하는 역할을 담당합니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)  
  
 학습 경로는 SQL Database를 사용하여 다음을 저장합니다.  
  
-   목차  
  
-   콘텐츠 메타데이터  
  
-   시스템 메타데이터  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/)  
  
 HTML, 이미지, [!INCLUDE[pn_JavaScript](pn-javascript.md)] 및 CSS는 모두 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 스토리지에 저장됩니다.  
  
 [Azure CDN(Content Delivery Network)](https://azure.microsoft.com/en-us/services/cdn/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network를 사용하여 HTML, 이미지, [!INCLUDE[pn_JavaScript](pn-javascript.md)] 및 CSS와 같은 정적 콘텐츠를 설문 조사 런타임에 제공합니다.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 학습 경로는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 서비스를 사용하여 디자이너를 위한 웹 서비스를 인증합니다. 현재 디자이너는 고객과 파트너에게 노출되지 않습니다. 따라서 인증은 [!INCLUDE[cc_Microsoft](cc-microsoft.md)] 도메인에서만 가능합니다.  
  
 [Azure Redis Cache](https://azure.microsoft.com/en-us/services/cache/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis Cache를 사용하여 사용자에게 제공하는 동적 콘텐츠를 캐시합니다.  
  
 [Azure Traffic Manager](https://azure.microsoft.com/en-us/services/traffic-manager/)  
  
 학습 경로는 Traffic Manager를 사용하여 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 또는 외부 사이트 및 서비스를 모니터링하고 장애가 발생할 경우 자동으로 사용자를 새 위치로 디렉션함으로써 중요한 애플리케이션의 가용성을 개선합니다.  
  
 [Azure Resource Manager](https://azure.microsoft.com/en-us/features/resource-manager/)  
  
 학습 경로는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Resource Manager를 사용하여 CDN, Redis Cache, SQL Database 및 클라우드 서비스를 리소스 그룹으로 배포하여 일관되고 반복적으로 배포할 수 있도록 합니다.