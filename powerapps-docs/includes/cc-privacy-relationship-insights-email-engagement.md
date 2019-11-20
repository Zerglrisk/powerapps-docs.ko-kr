전자 메일 참여, 임베디드 인텔리전스 기능을 사용하면 **팔로우** 설정으로 표시된 전자 메일이 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 전송될 때 받는 사람 활동 KPI와 "팔로우된" 전자 메일에 대한 상호 작용 계산을 위해 받는 사람의 전자 메일 간 상호 작용에 대한 정보가 수집되어 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 저장됩니다.  
  
 시스템 관리자는 임베디드 인텔리전스 내 **전자 메일 참여** 탭의 기능을 프로비전하여 전자 메일 참여를 활성화합니다. 관리자는 이후에 **설정**의 **인텔리전스 구성** 노드에서 조직의 전자 메일 참여를 비활성화할 수 있습니다.  
  
 이 기능을 비활성화하면 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에서 전송된 전자 메일을 사용자 인터페이스 또는 프로그래밍 방식으로 팔로우할 수 없습니다. 또한 수신자 상호 작용 데이터는 더 이상 **팔로우** 설정으로 표시된 발신 전자 메일에서 수집되지 않습니다. 이전에 수집된 모든 데이터는 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]에 남아 있으며 조직에서 이 기능을 다시 활성화할 경우 다시 사용할 수 있습니다. 데이터는 고객이 Microsoft와의 구독을 종료한 후 90일 동안 보존됩니다. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 사용자는 **연락처 선호 설정**의 **전자 메일 팔로우** 설정을 변경하여 연락처 또는 잠재 고객별로 임베디드 인텔리전스 - 전자 메일 참여 기능을 비활성화할 수도 있습니다.  
  
 전자 메일 참여 기능에 포함된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 및 서비스는 아래에서 자세히 설명합니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 전자 메일 참여 기능은 [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]를 사용하여 전자 메일 상호 작용 blob를 임시로 저장합니다.