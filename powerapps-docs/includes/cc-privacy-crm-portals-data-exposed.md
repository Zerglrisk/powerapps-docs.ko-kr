---
ms.openlocfilehash: ac90bfc27e03047cf422c44c83f550608d67b57e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212841"
---
[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]에 대해 포털 기능을 사용하도록 설정하면 외부 대상 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 포털을 통해 고객 이름, 제품 이름, 사례 번호 또는 모든 사용자 지정 엔터티 데이터와 같은 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터가 노출될 수 있습니다. 포털을 통해 노출된 모든 데이터는 Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Web Apps의 메모리에 저장되며, 포털 검색 기능을 사용할 수 있도록 로컬 하드 드라이브의 파일로 저장됩니다.

테넌트 관리자는 [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)]를 통해 구성함으로써 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 포털을 사용하도록 설정할 수 있습니다. 이 경우 선택한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 인스턴스에 패키지(솔루션 및 데이터 포함)도 설치됩니다. 그런 다음, 포털 관리자로 설정된 테넌트 관리자 또는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자는 포털을 통해 노출될 데이터를 지정할 수 있습니다. 이후 포털 기능을 사용하지 않도록 설정하려면 테넌트 관리자가 [!INCLUDE[pn_Office_365](pn-office-365.md)]를 사용하여 포털 추가 기능 구독을 취소할 수 있습니다.

포털 기능과 관련된 중요한 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음과 같습니다.
- [Azure Web Apps](https://azure.microsoft.com/services/app-service/web/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Web Apps는에서 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]포털을 호스트 하는 데 사용 됩니다.
- [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Traffic Manager은 사용자를 실행 중인 Web Apps으로 라우팅하여 서비스의 고가용성을 보장 하는 데 사용 됩니다. 
- [Azure Service Bus](https://azure.microsoft.com/services/service-bus/): [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)](토픽/구독)은 포털의 캐시 무효화에 사용 됩니다. [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 포털 관련 레코드가 변경될 때 트리거되는 메시지를 임시로 저장하고 캐시 무효화를 위해 Web Apps에 전달됩니다. 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): 모든 서비스는 구성 데이터를 [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)]에 저장합니다.
- [Azure Storage](https://azure.microsoft.com/services/storage/): 조직, 테 넌 트 및 포털과 관련 된 데이터는 저장소에 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 저장 됩니다.
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/): 모든 웹 서비스를 사용 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 하 여 인증 합니다.
