---
ms.openlocfilehash: 747ea34b784b852261debe91f587d64ee3277804
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61574946"
---
[!INCLUDE[pn_gamification](pn-gamification.md)] 솔루션을 설치 및 활성화하면 활성화된 사용자의 계정 식별자(예: 이름, 성 및 이메일 주소)는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 호스팅된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스를 사용하여 권한 부여를 허용하도록 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]에 저장됩니다. 이는 해당 관리자에 의해 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 서비스에서 활성화된 모든 사용자에게 적용됩니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 솔루션은 관리자가 구성한 KPI(핵심 성과 표시기) 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스에 보내고 해당 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구조화된 스토리지 및 Blob 스토리지에 저장됩니다.  각 사용자의 아바타, 사용자 지정 보상 및 회사 로고는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 저장되지만 정보는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)](으)로 반환되지 않습니다.  
  
관리자 및 인증된 사용자는 전화 통화, 기회 및 예약된 수익과 같은 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 데이터를 활용하여 게임에서 사용할 KPI를 구성할 수 있습니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 서비스는 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]에 대한 호출을 시작하지 않고 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)](으)로 되돌아가는 KPI가 사용되는 게임과 같은 데이터에만 응답합니다.  
  
관리자는 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV 스트림을 공개로 만들 수도 있습니다. [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV 스트림을 설정하고 공용 스트리밍을 활성화하는 게임 관리자는 스트림 링크가 있는 모든 사용자가 인터넷에서 TV 스트림을 볼 수 있도록 합니다.  
  
관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 이 솔루션을 제거하여 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 기능을 나중에 제거할 수 있습니다.  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]와(과) 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **디자이너 서비스(웹 역할)**  
  
[!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 조직과 다중 테넌트 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 간의 통신을 위해 여러 웹 서비스를 제공합니다. 예를 들어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage에 저장된 게이미피케이션 세부 정보입니다.  게임 계산은 [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] 큐를 사용하고 점수를 매기고 서비스에 표시하도록 반환됩니다.  고객 및 사용자 업로드 이미지는 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]에 저장됩니다. [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]에 대한 모든 요청을 인증합니다.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
모든 서비스는 구성 데이터를 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]에 저장합니다.  
  
[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은(는) SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]을(를) 사용하여 다음을 저장합니다.  
  
- KPI 데이터  
  
- 게임 계산  
  
- 조직(테넌트) 데이터  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
아바타, 회사 로고 및 기타 고객 업로드 이미지는 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]에 저장됩니다.  
  
[Azure CDN(Content Delivery Network)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은(는) [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Content Delivery Network를 사용하여 이미지(고객 로고와 같은 업로드 이미지 포함), [!INCLUDE[pn_JavaScript](pn-javascript.md)] 및 CSS와 같은 런타임에 정적 콘텐츠를 제공합니다.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]은(는) [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]을(를) 사용하여 사용자를 인증하고 플랫폼을 사용하도록 자격을 확인합니다.