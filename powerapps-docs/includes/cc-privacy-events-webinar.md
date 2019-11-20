이벤트 관리에 대한 이용 약관에 동의하면 웹 세미나 통합 기능이 활성화됩니다. 웹 세미나 통합 기능은 파트너 웹 세미나 공급자를 활용하여 이벤트 또는 세션을 웹 세미나로 실시합니다. 웹 세미나 제공자의 서비스를 사용하려면 계정이 있어야 합니다. 지금 당장 사용할 수 있는 유일한 파트너 웹 세미나 공급자는 ON24입니다. 웹 세미나 통합 기능을 사용할 때 웹 세미나를 제공하고 실행하는 데 필수적인 데이터는 처리되고 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]에 저장된 후 ON24로 전송됩니다. 이러한 데이터는 이름, 전자 메일 및 회사 이름 같은 웹 세미나 참여자의 등록 데이터를 포함합니다. 또한 ON24는 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]을 통해 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]으로 웹 세미나 보기 기간 등과 같은 웹 세미나 메트릭을 보냅니다.

나머지 이벤트 관리 솔루션을 사용하기 위해 웹 세미나 기능을 활성화할 필요가 없습니다. 관리자는 웹 세미나 구성에서 자격 증명을 제거하여 웹 세미나 통합 기능을 해제할 수 있습니다.

웹 세미나 통합 기능에서 사용하는 [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] 구성 요소 및 서비스는 다음과 같습니다.

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Key Vault는 무엇입니까?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis))
  - 고객의 ON24 계정 자격 증명을 암호화/암호 해독하기 위한 암호화 키 제공
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)][Azure Service Fabric의 개요](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - 등록 데이터와 웹 세미나 계정의 자격 증명을 처리하여 ON24로 전송
  - On24에서 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]으로 웹 세미나 메트릭 검색 - 고객의 ON24 계정 자격 증명 저장(사용자 정의 암호화)