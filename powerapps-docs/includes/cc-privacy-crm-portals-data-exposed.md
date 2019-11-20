[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]의 포털 기능을 사용하면 고객 이름, 제품 이름, 서비스 케이스 번호 또는 임의의 사용자 지정 엔터티 데이터와 같은 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 데이터가 외부 연결 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 포털을 통해 노출될 수 있습니다. 포털을 통해 노출된 데이터는 캐시을 위해 Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 웹 앱의 메모리에 저장되고 로컬 하드 드라이브에 있는 파일로도 저장되어 포털 검색 기능을 사용 할 수 있습니다.

테넌트 관리자는 선택한 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 인스턴스에 패키지(솔루션 및 데이터 포함)를 설치할 수도 있는 [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)]를 통해 구성하여 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 포털을 활성화할 수 있습니다. 그러면 포털 관리자로 설정된 테넌트 관리자 또는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자는 포털을 통해 노출되는 데이터를 지정할 수 있습니다. 이후 포털 기능을 사용하지 않으려면 테넌트 관리자는 [!INCLUDE[pn_Office_365](pn-office-365.md)]를 통해 포털 추가 기능 구독을 취소할 수 있습니다.

포털 기능에 포함된 중요 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음과 같습니다.
- [Azure Web Apps](https://azure.microsoft.com/services/app-service/web/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 포털을 호스팅하는 데 사용됩니다.
- [Azure Traffic Manager](https://azure.microsoft.com/services/traffic-manager/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Azure Traffic Manager는 실행 중인 웹 앱에 사용자를 라우팅하여 서비스의 높은 가용성을 보장하는 데 사용됩니다. 
- [Azure Service Bus](https://azure.microsoft.com/services/service-bus/): [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] (주제/구독)은 포털의 캐시 무효화에 사용됩니다. [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]는 포털 관련 레코드가 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 변경될 때 트리거되는 메시지를 임시로 저장하고 캐시 무효화를 수행하기 위해 웹 앱에 전달합니다. 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): 모든 서비스는 [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)]에 구성 데이터를 저장합니다.
- [Azure Storage](https://azure.microsoft.com/services/storage/): 조직, 테넌트 및 포털 관련 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에 저장됩니다.
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/): 모든 웹 서비스는 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]를 사용하여 인증합니다.
