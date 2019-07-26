---
ms.openlocfilehash: f331670a2fd6b051c91a7fe2bfa607c54c9ab41a
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225245"
---
일부 마케팅 프로세스를 수행하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]를 사용하도록 설정하여 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]에서 특정 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스로의 데이터 흐름을 허용하는 데 동의합니다. 이러한 서비스는 집합적으로 "[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스"라고 합니다.

고객 경험을 위해 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]는 고객 경험, 이메일, 제출 양식 및 마케팅 페이지 정의를 [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]에서 실행되는 이러한 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스로 보내야 합니다. 마케팅 페이지는 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]에 대한 포털 기능의 고객 고유의 인스턴스로 추가 전송됩니다.

보낸 이메일을 개인 설정하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]는 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 간의 데이터 흐름을 사용하도록 설정해야 합니다. [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 서비스에 대한 자세한 내용은 아래를 참조하세요. [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로의 데이터 흐름에는 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에 대한 연락처 및 계정의 동기화가 포함됩니다. [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스는 이 데이터를 사용하여 이메일 콘텐츠를 개인 설정합니다. 포함되는 데이터는 이메일 정의에 따라서만 달라집니다.

잠재 고객 점수 매기기 모델 및 마케팅 세그먼트를 다시 계산하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]는 잠재 고객 점수 매기기 모델 정의 및 세그먼트 정의를 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에 보내고 이러한 계산 내에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]의 프로필 및 상호 작용을 활용해야 합니다.

[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 캡처하지 않은 이메일 및 인터넷 상호 작용에 대한 인사이트를 제공하려면 수집된 데이터가 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 및 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 모두로 흘러야 합니다.

또한 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 이벤트 관리 통합을 사용하도록 설정하는 경우 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]는 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)](직접 [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]에 대한 커넥터를 통해) 및 이벤트 등록과 체크인(상호 작용으로 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해)에 이벤트를 동기화합니다.

[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]와 관련된 데이터 흐름은 다음과 같습니다.
- 이메일 개인 설정, 잠재 고객 점수 매기기 및 조각화(주로 연락처 및 계정, 또한 잠재 고객 및 이벤트)에 대한 콘텐츠를 제공하기 위해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]의 정기적인 인바운드 커넥터를 사용하여 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로 흐르는 엔터티 데이터
- 상호 작용 및 인사이트(고객 경험, 마케팅 이메일, 마케팅 페이지)에 대한 식별자를 제공하기 위해 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로 흐르는 엔터티 데이터
- [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)](이메일 추적, 웹 사이트 추적, 고객 경험 진행률)로 흐르는 상호 작용
- [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)](이벤트 등록 및 체크 인)로 흐르는 상호 작용
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)](주로 고객 경험 및 이메일 전송 진행률과 잠재 고객 점수 매기기 결과)로 흐르는 [!INCLUDE[pn-insights](../includes/pn-insights.md)](상호 작용 및 KPI)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에서 직접 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]의 형식으로 전용 및 샌드박스 UI 요소로 흐르는 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 앱(조각화 및 위젯)

### <a name="marketing-services"></a>마케팅 서비스

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]는 이러한 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스를 사용합니다.

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 스토리지

> [!NOTE]
> 추가 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스 제품에 대한 자세한 내용은 [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)](<https://azure.microsoft.com/support/trust-center/>)를 참조하세요.

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]를 사용하여 추가 처리를 위해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로 고객 데이터의 전송을 활성화합니다. [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]에 대한 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]의 사용에는 특정 개인정보보호법을 준수해야 할 수 있습니다. 조직의 적절한 담당자에게 질문을 해주시기 바랍니다.

현재 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]는 공개 미리 보기 상태에 있으며, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 또는 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 고객 참여와 같은 수준의 개인정보 및 보안 약정을 제공하지는 않습니다. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]는 기본적으로 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스를 기반으로 빌드되었으며, 적용 가능한 각 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스에 대한 해당 규정 준수 및 보안 표준이 적용됩니다. 자세한 내용은 [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] 보안 센터([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/))로 이동합니다.

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]는 이러한 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스를 사용합니다.

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight(Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Event Hub
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Monitoring
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Metrics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 스토리지
