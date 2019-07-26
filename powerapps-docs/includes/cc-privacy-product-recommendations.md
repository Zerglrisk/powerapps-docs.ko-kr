---
ms.openlocfilehash: 1cdcb40245aae9a23ecb6d3392e412f8a60b95ba
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212300"
---
제품 권장 기능을 사용하여 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 권장 모델을 빌드하는 경우 구성된 Basket Data 엔터티 및 해당 필터에 따라 거래 기록 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]로 전송하여 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 처리하고, 일시적으로 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에 저장하고, 마지막으로 Azure Recommendations API로 보내 기계 학습 모델을 만듭니다. Azure Recommendations API를 사용하여 모델을 빌드한 후 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에서 삭제됩니다. ID(계정 ID, 제품 ID, 트랜잭션 ID)만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)](으)로 전송하여 권장 모델을 빌드합니다.

관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직의 **설정** &gt; **관리** &gt; **시스템 설정** &gt; **미리 보기** 탭에서 제품 권장 기능을 사용하도록 설정할 수 있습니다. 권장 모델을 빌드할 때 데이터를 Azure Recommendations API로 보냅니다. 시스템 관리자는 Azure Recommendations API와 공유된 데이터를 삭제하려면 기존 모델을 삭제할 수 있습니다. 또한 시스템 관리자가 나중에 모든 권장 모델의 빌드를 중지하려면 Azure Recommendations API에 대한 연결을 삭제할 수 있습니다.

제품 권장 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

이 논리 앱은 권장 모델 버전을 빌드하기 위해 Recommendations API를 사용하여 제품 카탈로그 및 트랜잭션 데이터를 동기화하는 오케스트레이션된 데이터 파이프라인을 제공합니다. 이 파이프라인은 Dynamics 365 조직과 Recommendations API 간의 통신을 위해 여러 API 앱을 통해 다중 테넌트 서비스로 실행됩니다. 논리 앱은 모델 버전 ID 및 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직 URL 같은 최소한의 컨텍스트를 사용하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 트리거됩니다. 

[Azure API Apps](https://azure.microsoft.com/services/app-service/api/)

이러한 웹 애플리케이션은 권장 모델을 빌드하기 위해 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직에서 데이터를 읽고 Recommendations API로 데이터를 보내는 웹 작업을 트리거합니다. 3개의 API 앱 및 해당 웹 작업, 즉 제품 데이터를 읽기 위한 API 앱, 트랜잭션 데이터를 읽기 위한 API 앱 및 권장 모델을 빌드하기 위한 API 앱이 있습니다. API 앱은 웹 작업을 사용하여 백그라운드에서 실제 데이터를 처리하고 데이터 출력을 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 작성합니다. 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 일시적으로 저장됩니다. 마지막으로, 모델이 빌드되면 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 스토리지에서 데이터가 삭제됩니다.

[Azure Table](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table은 API 앱 및 웹 작업 간에 모델 버전 및 조직 컨텍스트를 통신하는 데 사용됩니다.

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

데이터는 웹 작업을 통해 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 일시 저장되었다가 논리 앱 파이프라인이 실행을 완료하면 삭제됩니다.

[Azure Recommendations API](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) Azure Recommendations API를 최소한의 데이터(제품 ID, 트랜잭션 ID 및 계정 ID)를 통해 전송하여 권장 모델을 빌드합니다. 데이터는 해당 모델 버전이 생길 때까지 Recommendations API 서비스를 통해 저장됩니다.
