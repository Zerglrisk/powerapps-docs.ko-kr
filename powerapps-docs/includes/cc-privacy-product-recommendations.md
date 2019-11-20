제품 추천 기능을 사용하면 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 내에서 추천 모델을 빌드할 때 구성된 장바구니 데이터 엔터티 및 해당 필터에 기반한 거래 데이터가 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]로 전송되고, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에서 처리되어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에 임시로 저장되고, 마지막으로 Azure 추천 API에 전송되어 기계 학습 모델을 빌드합니다. 모델이 Azure 추천 API로 빌드된 후에 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에서 삭제됩니다. ID(계정 ID, 제품 ID, 거래 ID)만 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]로 전송되어 추천 모델을 빌드합니다.

관리자는 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 조직에서 **설정** &gt; **관리** &gt; **시스템 설정** &gt; **미리 보기** 탭에서 제품 추천 기능을 활성화할 수 있습니다. 추천 모델이 빌드될 경우에만 데이터가 Azure 추천 API로 전송됩니다. 시스템 관리자에게는 기존 모델을 삭제할 수 있는 옵션이 있어 Azure 추천 API와 공유되는 데이터를 삭제할 수 있습니다. 또한 시스템 관리자는 Azure 추천 API와의 연결을 삭제하여 향후 추천 모델 빌드를 중지할 수 있습니다.

제품 추천에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure 논리 앱](https://azure.microsoft.com/services/app-service/logic/)

조율된 데이터 파이프라인을 제공하여 제품 카탈로그 및 거래 데이터를 Azure 추천 API와 동기화하여 추천 모델 버전을 빌드합니다. 이 파이프라인은 Dynamics 365 조직과 Azure 추천 API 간의 통신을 위해 여러 API 응용 프로그램이 있는 다중 테넌트 서비스로 실행됩니다. 논리 앱은 모델 버전 ID 및 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직 URL과 같은 최소한의 컨텍스트로 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 트리거됩니다. 

[Azure API 앱](https://azure.microsoft.com/services/app-service/api/)

[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 조직의 데이터를 읽어 Azure 추천 API에 데이터를 보내 추천 모델을 빌드하는 웹 작업을 트리거하는 웹 응용 프로그램입니다. 제품 데이터 읽기용, 거래 데이터 읽기용, 추천 모델 빌드용의 3가지 API 앱 및 해당하는 웹 작업이 있습니다. API 앱은 웹 작업을 사용하여 백그라운드에서 실제 데이터 처리를 수행하고 데이터 출력을 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 기록합니다. 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 임시로 저장됩니다. 마지막으로, 모델이 빌드된 후에 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage에서 삭제됩니다.

[Azure 테이블](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 테이블은 API 앱과 웹 작업 간에 모델 버전 및 조직 컨텍스트를 전달하는 데 사용됩니다.

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage에 웹 작업별로 임시로 저장되고 논리 앱 파이프라인 실행을 마친 후에 삭제됩니다.

[Azure 추천 API](https://www.microsoft.com/cognitive-services/recommendations-api) Azure 추천 API는 최소 데이터 제품 ID, 거래 ID 및 계정 ID로 전송되어 추천 모델을 빌드합니다. 데이터는 해당 모델 버전이 존재할 때까지 추천 API 서비스에 저장됩니다.
