---
ms.openlocfilehash: fa4a17c2a3131f49f8a702388bdb405661855c10
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "61550022"
---
이벤트 관리에 대한 사용 약관에 동의하는 경우 웹 세미나 통합 기능이 활성화됩니다. 웹 세미나 통합 기능은 파트너 웹 세미나 공급자를 활용하여 이벤트 또는 세션을 웹 세미나로 수행합니다. 모든 웹 세미나 공급자의 서비스를 사용하려면 해당 계정이 있어야 합니다. 이번에 기본적으로 제공되는 유일한 파트너 웹 세미나 공급자 서비스는 ON24입니다. 웹 세미나 통합 기능을 사용하는 경우 웹 세미나를 제공하고 실행하는 데 필수적인 데이터는 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]에서 처리 및 저장된 다음, ON24로 전송됩니다. 이러한 데이터에는 해당 이름, 이메일 및 회사 이름과 같은 웹 세미나 참가자 등록 데이터가 포함됩니다. 또한 ON24는 웹 세미나 보기 기간과 같은 웹 세미나 메트릭을 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]를 통해 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]로 보냅니다.

나머지 이벤트 관리 솔루션을 사용하려면 웹 세미나 기능을 활성화하지 않아도 됩니다. 관리자는 웹 세미나 구성에서 자격 증명을 제거하여 웹 세미나 통합 기능을 해제할 수 있습니다.

웹 세미나 통합 기능에서 사용하는 [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] 구성 요소 및 서비스는 다음과 같습니다.

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)]([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Key Vault란?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis))
  - 고객의 ON24 계정 자격 증명을 암호화/암호 해독하기 위한 암호화 키 제공
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Service Fabric 개요](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - 등록 데이터 및 웹 세미나 계정 자격 증명을 처리하고 ON24로 전송
  - On24에서 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]까지 웹 세미나 메트릭을 검색 - 고객의 ON24 계정 자격 증명(사용자 지정 암호화된)을 저장