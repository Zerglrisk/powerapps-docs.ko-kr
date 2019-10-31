[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]을(를) 활성화함으로써 일부 마케팅 프로세스를 수행하기 위해 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]에서 특정 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스로 데이터 흐름을 허용하는 것에 동의합니다. 이러한 서비스를 통칭하여 "[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스"라고 합니다.

고객의 여정을 수행하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]은(는) 고객 여정, 전자 메일, 제출 양식 및 마케팅 페이지 정의를 [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]에서 실행되는 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에 전송해야 합니다. 마케팅 페이지는 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 포털 기능의 고유한 고객 인스턴스로도 보내집니다.

보낸 전자 메일을 개인 설정하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]은(는) [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]와의 데이터 흐름을 활성화해야 합니다.  [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 서비스에 대한 자세한 내용은 아래를 참조하십시오. [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]와의 데이터 흐름은 연락처 및 거래처를 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]와 동기화하는 것을 포함합니다. [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스는 이 데이터를 사용하여 전자 메일 내용을 개인 설정합니다. 포함되는 데이터는 전자 메일 정의에 따라서만 달라집니다.

잠재 고객 점수 모델 및 마케팅 세그먼트를 다시 계산하려면 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]은(는) 잠재 고객 점수 모델 정의와 세그먼트 정의를 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에 보내고 이러한 계산 내에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]의 프로필 및 상호 작용을 활용해야 합니다.

[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 캡처한 전자 메일과 인터넷 상호 작용에 관한 통찰력을 제공하기 위해 수집된 데이터는 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 및 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로 흐릅니다.

또한 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 이벤트 관리 통합이 활성화되어 있는 경우 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]은(는) 이벤트를 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] ([!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]용 커넥터를 통해 직접) 및 이벤트 등록과 체크인([!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 상호 작용으로)과 동기화합니다.

[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]와 관련된 데이터 흐름은 다음과 같습니다.
- 전자 메일 개인 설정, 잠재 고객 채점 및 세분화에 대한 콘텐츠를 제공하기 위해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]의 일반 인바운드 커넥터를 사용하여 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로의 엔터티 데이터(주로 연락처 및 거래처, 결국에는 잠재 고객 및 이벤트)
- 상호 작용 및 통찰력을 위한 식별자를 제공하기 위해 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로의 엔터티 데이터(고객 여정, 마케팅 전자 메일, 마케팅 페이지) 
- [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스에서 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로의 상호 작용(전자 메일 추적, 웹사이트 추적, 고객 여정 진행)
- [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로의 상호 작용(이벤트 등록 및 체크인)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에서 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 서비스를 통해 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]로의 [!INCLUDE[pn-insights](../includes/pn-insights.md)](상호 작용 및 KPI)(주로 고객 여정과 전자 메일 전송 진행 및 잠재 고객 채점 결과)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]에서 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]의 형식으로 직접 전용 및 샌드백스 UI 요소로 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 앱(세분화 및 위젯)

### <a name="marketing-services"></a>마케팅 서비스

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]은(는) 다음과 같은 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스를 사용합니다.

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 저장소

> [!NOTE]
> 추가 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스 제품에 대한 자세한 내용은 [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)](<https://azure.microsoft.com/support/trust-center/>)를 참조하십시오.

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]을(를) 사용하면 추가 처리를 위해 고객 데이터를 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]로 전송하는 작업이 활성화됩니다. [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]용 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]를 사용하려면 특정 개인 정보 보호 법률을 준수해야 할 수도 있습니다.  조직의 담당자에게 직접 문의하십시오.

현재 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]는 공개 미리 보기에 있으며, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 또는 Common Data Service와 동일한 수준의 개인 정보 및 보안 노력을 제공하지 않습니다. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]는 기본적으로 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스에 구축되며 각 적용 가능한 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스에 대한 각각의 준수 및 보안 표준입니다. 자세한 내용은 [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] 보안 센터[https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)를 참조하십시오.

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)]은(는) 다음과 같은 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 서비스를 사용합니다.

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight(Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 이벤트 허브
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 모니터링
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 메트릭
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 웹 사이트
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 저장소
