텍스트 분석 기능을 사용하면 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services 텍스트 분석 API를 활용하여 고급 통찰력을 제공하는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 내의 종속 기능을 사용할 수 있습니다. 이러한 종속성 기능은 다음과 같습니다.  
  
-   참조 제안  
  
-   서비스 케이스 항목 분석  
  
-   유사한 서비스 케이스 제안  
  
 관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 **설정** > **관리** > **시스템 설정** > **미리 보기** 탭에서 텍스트 분석 기능을 활성화할 수 있습니다.  
  
 텍스트 분석 기능을 사용하면 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 텍스트 분석 기반 참조 제안을 설정할 때 서비스 케이스와 관련된 엔터티의 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송되어 키워드/구를 추출할 수 있습니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API에 저장된 데이터가 없습니다. 참조 문서 구성에서 구성된 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송되어 용어를 추출합니다. 관리자 또는 사용자 지정자에게는 참조 문서 구성을 비활성화하는 옵션이 있어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API에 대한 API 호출을 중지할 수 있습니다. 또한 사용자 지정자는 서비스 케이스 엔터티 양식 구성에서 필드 기반 제안을 다시 전환하여 텍스트 분석 기반 제안 사용을 중지할 수 있습니다.  
  
 텍스트 분석 기능을 사용하면 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 서비스 케이스 항목 분석을 설정할 때 서비스 케이스와 관련된 엔터티 데이터가 항목 확인을 위해 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송됩니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API에 저장된 데이터가 없습니다. 토픽 모델 구성에서 구성된 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송되어 항목을 추출합니다. 시스템 관리자 또는 사용자 지정자에게는 토픽 모델을 비활성화하는 옵션이 있어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API 호출을 중지할 수 있습니다.  
  
 텍스트 분석 기능을 사용하면 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 유사한 서비스 케이스 제안을 설정할 때 유사성 규칙에 고급 텍스트 분석 옵션이 활성화되어 있을 경우 서비스 케이스와 관련된 엔터티의 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송되어 키워드 및 구를 추출할 수 있습니다. 유사성 규칙에서 구성된 텍스트 필드만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API로 전송됩니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API에 저장된 데이터가 없습니다. 시스템 관리자 또는 사용자 지정자에게는 유사성 규칙을 비활성화하는 옵션이 있어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API 호출을 중지할 수 있습니다.  
  
 텍스트 분석 기반 기능에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API 앱](https://azure.microsoft.com/services/app-service/api/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱은 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직의 데이터를 읽는 웹 작업을 트리거하고 데이터를 텍스트 분석 API에 전송하여 항목 분석을 수행합니다. [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱은 웹 작업을 사용하여 백그라운드에서 실제 데이터 처리를 수행하고 데이터 출력을 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 기록합니다. 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 임시로 저장됩니다. 마지막으로, 항목 확인이 수행된 후에 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에서 삭제됩니다.  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler는 항목 분석을 수행하기 위해 일정에 따라 웹 작업을 트리거하는 데 사용됩니다. 토픽 모델 빌드 일정만 공정 관리자와 공유합니다.  
  
 [Azure 테이블](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블은 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 앱과 웹 작업 간에 모델 버전 및 조직 컨텍스트를 전달하는 데 사용됩니다.  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 웹 작업은 데이터를 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 임시로 저장하고 논리 앱 파이프라인 실행을 마친 후에 삭제됩니다.  
  
 [Azure 텍스트 분석 API](https://www.microsoft.com/cognitive-services/text-analytics-api)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 텍스트 분석 API는 활성 참조 검색 필드나 토픽 모델 구성 또는 유사성 규칙 구성에 구성된 필드를 기반으로 데이터가 전송됩니다. 예를 들어 제목 및 설명과 같은 서비스 케이스 엔터티 필드와 관련 메모 및 활동의 설명 필드는 참조 검색 필드 구성에서 구성됩니다.  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 관련성 검색  
  
 관리자가 관련성 검색을 활성화한 경우 관련성 검색을 사용하여 서비스 케이스에 대한 유사한 레코드를 찾을 수 있습니다. 유사성 규칙에 사용되는 텍스트 일치 필드 및 완전 일치 필드는 관련성 검색 API를 호출하는 데 사용됩니다. 데이터 처리 세부 정보는 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 관련성 검색의 기술적인 내용을 참조하십시오.