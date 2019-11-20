[!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)]를 설치하면 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구독 정보를 제공할 때 아래에 나열되는 필수 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 리소스가 배포되고 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 인스턴스에서 데이터(예: 명령 및 등록)를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 보내 IoT 사용 시나리오를 사용하여 장치를 등록한 후 등록된 장치로 명령을 보내고 받습니다. 관리자는 Connected Field Service를 제거하여 기능을 제거한 후 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 포털로 이동하여 더 이상 필요 없는 모든 관련 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 서비스를 관리할 수 있습니다.  
  
 Connected Field Service 기능에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [서비스 버스 큐](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]과 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 간 인바운드 및 아웃바운드 메시지(명령) 흐름 모두에 대한 큐를 제공합니다. IoT 알림이 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 전송되거나 명령이 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 IoT Hub로 전송되면 이 큐에 대기하게 됩니다.  
  
 [논리 앱](https://azure.microsoft.com/services/logic-apps/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 커넥터와 큐 커넥터를 사용하는 오케스트레이션 서비스를 제공합니다. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 커넥터는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 관련 엔터티를 구성하는 데 사용되고 큐 커넥터는 큐를 폴링하는 데 사용됩니다.  
  
 [Stream analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 데이터에서 깊은 통찰력을 드러내는 데 도움이 되는 완전히 관리되는 실시간 이벤트 처리 엔진을 제공합니다. Stream Analytics을 사용하면 장치, 센서, 웹 사이트, 소셜 미디어, 응용 프로그램, 인프라 시스템 등에서 데이터 스트리밍에 대한 실시간 분석 계산을 쉽게 설정할 수 있습니다. 선택적인 IoT 알림을 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 보내는 깔때기 역할을 합니다.  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services는 IoT Hub를 사용하여 등록된 장치 및 자산의 상태를 관리합니다. 또한 IoT Hub는 연결된 장치에 명령 및 알림을 보내고 수신 확인을 통해 메시지 배달을 추적합니다. 장치 메시지는 간헐적으로 연결된 장치를 수용할 수 있도록 내구성 있는 방식으로 전송됩니다.  
  
 **시뮬레이터**  
  
 명령을 보내거나 IoT Hub에서 명령을 받는 장치를 에뮬레이션하는 테스트 웹 앱입니다.  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service는 SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]를 사용하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]의 장치 상태를 표시하기 위해 PowerBI에서 나중에 사용할 장치 하트 비트 메시지를 저장합니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Stream Analytics에서 사용할 쿼리는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 저장됩니다.