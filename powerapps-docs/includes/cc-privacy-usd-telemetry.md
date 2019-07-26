---
ms.openlocfilehash: 7b58f302f694246564d7073a954ecd53b1b25361
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456889"
---
도움말 개선 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 기능은 운영 체제 세부 정보, 브라우저 세부 정보, [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] 애플리케이션별 정보 및 클라이언트가 설치된 컴퓨터의 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 버전과 같은 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 사용 정보를 전송합니다. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]는 조직 인사이트에 대한 보안 연결을 통해 정보를 [!INCLUDE[cc_Microsoft](cc-microsoft.md)]에 전송하고 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage에 저장합니다.
  
> [!NOTE]
>  조직 인사이트는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직의 시스템 관리자에게 조직 사용 방법에 대한 빠른 개요를 제공합니다. 시스템 관리자는 가장 활동적인 사용자, 시작 중인 SDK 요청 수 및 SDK 사용자가 보고 있는 수를 볼 수 있습니다.
  
 도움말 개선 통합 서비스 데스크 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스 목록이 아래에 나와 있습니다.  
  
> [!NOTE]
>  추가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스 제공에 대한 자세한 내용은 [Microsoft Azure 보안 센터](https://azure.microsoft.com/support/trust-center/)를 참조하세요.  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/) OrgInsights 데이터 REST API(웹 역할)  
  
 이 웹 역할은 조직 인사이트에 데이터를 표시하는 차트의 요청을 수락합니다. API는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블에서 집계된 데이터를 읽고 반환합니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직의 원시 원격 분석 데이터는 모니터링 에이전트(모든 확장 그룹 컴퓨터에서 실행됨)에서 수집되고 본드 형식(이진 형식)으로 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 업로드됩니다.  
  
 [Azure Table Storage](https://azure.microsoft.com/services/storage/tables/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage의 원시 원격 분석 데이터는 집계되어 Azure Table Storage에 저장되며 Cloud Service에서 읽습니다.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 조직 인사이트는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 서비스를 사용하여 웹 서비스를 인증합니다.  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 모니터링 에이전트는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 데이터를 업로드할 때마다 메시지를 만들고 대기합니다. 이러한 메시지는 업로드된 데이터를 집계하기 위해 CMA 파이프에 의해 수집됩니다.