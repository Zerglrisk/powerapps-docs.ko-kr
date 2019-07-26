---
ms.openlocfilehash: 80997689e9d4ebca8eb4809cc3e94dab549482b5
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224724"
---
Text Analytics 기능을 사용하여 고급 정보를 제공하는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services Text Analytics API를 활용하는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 내에서 종속 기능을 사용하도록 설정합니다. 이러한 종속 기능은 다음과 같습니다.  
  
-   기술 제안  
  
-   사례 토픽 분석  
  
-   유사한 사례 제안  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직의 **설정** > **관리** > **시스템 설정** > **미리 보기** 탭에서 Text Analytics 기능을 사용하도록 설정할 수 있습니다.  
  
 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 텍스트 분석 기반 기술 제안을 설정한 경우 Text Analytics 기능을 사용하여 대/소문자 및 관련된 엔터티의 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송하여 키워드/문구를 추출합니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API를 사용하여 데이터를 저장하지 않습니다. 기술 문서 구성에서 구성된 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송되어 용어를 추출합니다. 관리자 또는 사용자 지정자에게는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API에 대한 API 호출을 중지하기 위해 기술 문서 구성을 비활성화하는 옵션이 있습니다. 또한 사용자 지정자는 사례 엔터티 양식 구성의 필드 기반 제안으로 다시 전환하여 Text Analytics 기반 제안의 사용을 중지할 수 있습니다.  
  
 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 사례 토픽 분석을 설정한 경우 토픽을 결정하기 위해 Text Analytics 기능을 사용하여 대/소문자 및 관련된 엔터티 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송합니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API를 사용하여 데이터를 저장하지 않습니다. 토픽 모델 구성에서 구성된 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송되어 토픽을 추출합니다. 관리자 또는 사용자 지정자에게는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API 호출을 중지하기 위해 토픽 모델을 비활성화하는 옵션이 있습니다.  
  
 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 유사한 사례 제안을 설정한 경우 고급 Text Analytics 옵션을 유사성 규칙에서 사용하면 Text Analytics 기능을 사용하여 대/소문자 및 관련된 엔터티의 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송하여 키워드 및 문구를 추출합니다. 유사성 규칙에서 구성된 텍스트 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API로 전송됩니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API를 사용하여 데이터를 저장하지 않습니다. 관리자 또는 사용자 지정자에게는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API 호출을 중지하기 위해 유사성 규칙을 비활성화하는 옵션이 있습니다.  
  
 Text Analytics 기반 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API 앱](https://azure.microsoft.com/services/app-service/api/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱은 토픽 분석을 위해 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직에서 데이터를 읽고 Text Analytics API로 데이터를 보내는 웹 작업을 트리거합니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱은 웹 작업을 사용하여 백그라운드에서 실제 데이터를 처리하고 데이터 출력을 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 작성합니다. 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 일시적으로 저장됩니다. 마지막으로, 토픽을 결정하면 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에서 데이터가 삭제됩니다.  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler를 사용하여 토픽 분석을 수행하는 일정에 따라 웹 작업을 트리거합니다. 토픽 모델 빌드 일정은 스케쥴러를 사용해서만 공유됩니다.  
  
 [Azure 테이블](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블을 사용하여 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱 및 웹 작업 간에 모델 버전 및 조직 컨텍스트를 전송합니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 웹 작업은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 데이터를 일시적으로 저장하고 논리 앱 파이프라인에서 실행을 완료하면 삭제합니다.  
  
 [Azure Text Analytics API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API는 활성 기술 검색 필드 또는 토픽 모델 구성이나 유사성 규칙 구성에서 구성된 필드를 기반으로 데이터를 전송합니다. 예를 들어, 관련된 정보 및 작업의 제목, 설명 및 설명 필드와 같은 사례 엔터티 필드를 기술 검색 필드 구성에서 구성합니다.  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 관련성 검색  
  
 관리자에 의해 활성화되어 있는 경우 관련성 검색을 사용하여 사례에 대한 비슷한 레코드를 찾을 수 있습니다. 유사성 규칙에 사용되는 텍스트 일치 필드 및 정확한 일치 필드는 관련성 검색 API를 호출하는 데 사용됩니다. 데이터 처리 세부 정보는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 관련성 검색에 대한 기술 콘텐츠를 참조하세요.