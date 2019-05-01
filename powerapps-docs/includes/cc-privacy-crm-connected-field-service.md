---
ms.openlocfilehash: ce9db35844f46e9779055ec30dcba0f9459c3a16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61575527"
---
[!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)]을(를) 설치하여 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구독 정보를 제공할 때 필수 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 리소스가 배포되고 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스는 데이터(예: 명령 및 등록)를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 전송하여 디바이스를 등록한 다음, 등록된 디바이스에 명령을 보내고 받는 IoT 사용 시나리오를 활성화합니다. 관리자는 연결된 필드 서비스를 제거하여 기능을 제거한 다음, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 포털로 이동하여 더 이상 필요하지 않은 관련된 모든 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스를 관리할 수 있습니다.  
  
 연결된 필드 서비스 기능과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Service Bus 큐](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 및 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 사이를 흐르는 인바운드와 아웃바운드 메시지(명령) 모두에 대한 큐를 제공합니다. IoT 경고가 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 전송되거나 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 IoT 허브로 명령이 전송된 경우 여기에서 큐 대기됩니다.  
  
 [Logic Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 커넥터 및 큐 커넥터를 사용하는 오케스트레이션 서비스를 제공합니다. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 커넥터는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]와(과) 관련된 엔터티를 생성하는 데 사용되며 큐 커넥터는 큐 폴링에 사용됩니다.  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 데이터에서 깊이 있는 통찰력의 잠금을 해제할 수 있도록 완전히 관리되는 실시간 이벤트 처리 엔진을 제공합니다. Stream Analytics를 사용하면 장치, 센서, 웹 사이트, 소셜 미디어, 애플리케이션, 인프라 시스템 등의 데이터 스트리밍에서 실시간 분석 계산을 쉽게 설정할 수 있습니다. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 선택적 IoT 경고를 보내는 깔때기로 작동합니다.  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 연결된 필드 서비스는 IoT Hub를 사용하여 등록된 디바이스 및 자산의 상태를 관리합니다. 또한 IoT Hub는 명령 및 알림을 연결된 디바이스로 보내고 읽음 확인으로 메시지 배달을 추적합니다. 디바이스 메시지는 간헐적으로 연결되는 디바이스를 고려하여 지속적인 방식으로 전송됩니다.  
  
 **시뮬레이터**  
  
 명령을 전송하거나 IoT 허브에서 명령을 수신하는 디바이스를 에뮬레이션하는 테스트 웹앱입니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 연결된 필드 서비스는 SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]을(를) 사용하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 디바이스의 상태를 표시하도록 PowerBI에서 나중에 사용할 디바이스 하트비트 메시지를 저장합니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Stream Analytics에서 사용할 쿼리는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 스토리지에 저장됩니다.