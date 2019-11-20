Dynamics 365를 위한 고객의 소리 기능을 활성화하면 Dynamics 365 내에서 설문을 게시할 때 설문 정의가 Azure에 발송되어 Azure Storage에 저장됩니다. 이메일을 통해 응답자에게 발송된 설문 초대 링크를 열어 응답자가 설문을 제출하면 설문 응답이 일시적으로 Azure Service Bus에 저장된 후 회수되어 Dynamics 365에 저장됩니다. 응답이 Dynamics 365에 저장되고 나면 Azure에서 삭제됩니다.  
  
 응답자를 위해 설문을 렌더링할 때 고객 이름, 제품 이름, 서비스 케이스 번호 등의 Dynamics 365 데이터를 설문(질문과 답변과 같은 설문 요소 내)에 포함할 수 있습니다. 설문 초대 링크가 생성되면 이 Dynamics 365 데이터는 Dynamics 365에서 전송되어 설문 초대 링크 내 사용된 식별자와 교환되어 Azure SQL Database에 저장됩니다. 이 식별자는 설문 초대 링크를 사용하여 설문이 열린 후 설문에서 Dynamics 365 데이터를 표시하는 데 사용됩니다. 전자 메일을 통해 응답자에게 전송된 설문 링크 내 식별자는 응답자의 전자 메일 시스템에 저장됩니다.  
  
 관리자는 Dynamics 365 조직에 하나의 솔루션으로 Dynamics 365용 고객의 소리 기능을 설치하여 활성화할 수 있습니다. 또한 관리자는 그후에 Dynamics 365 조직에서 이 솔루션을 제거함으로써 그 기능을 불능화할 수 있습니다.  
  
 Dynamics 365용 고객의 소리 기능에 포함된 Azure 구성 요소 및 서비스는 다음 섹션에서 자세히 설명합니다.  
  
 참고: 추가 Azure 서비스 제공에 대한 자세한 내용은 Microsoft Azure 보안 센터([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/))를 참조하십시오.  
  
 **클라우드 서비스** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **디자이너 서비스(웹 역할)**  
  
 이 서비스는 Dynamics 365 조직과 Dynamics 365용 다중 테넌트 고객의 소리 Azure 구성 요소 사이의 통신을 위한 여러 웹 서비스를 제공합니다.  예를 들어, 설문이 게시되면 Azure Blob Storage에 저장됩니다.  설문 응답은 Azure Service Bus 큐에서 검색되어 Dynamics 365 조직에서 유지되도록 반환됩니다.  모든 요청은 Azure Active Directory에 대해 인증됩니다.  
  
 **설문 런타임(웹 역할)**  
  
 설문을 응답자에게 제공하는 웹 응용 프로그램입니다.  제출된 설문 응답은 Dynamics 365 비동기 서비스에서 검색 프로세스를 처리하기 전에 Azure Service Bus 큐에 임시로 저장됩니다.  
  
 **응답 프로세서(작업자 역할)**  
  
 이 작업자 역할은 완료된 원시 설문을 Dynamics 365에서 작성할 수 있는 유효한 설문 응답으로의 처리를 담당합니다.  
  
 **푸시 프로세서(작업자 역할)**   이 작업자 역할은 유효한 설문 응답을 처리하고 Dynamics 365 엔터티 레코드로의 업데이트를 담당합니다. 
 
 **Azure Key Vault**([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 모든 클라우드 서비스는 Azure Key Vault에 데이터를 저장합니다.  조직, 테넌트 데이터는 SQL Azure에 저장됩니다.  
  
 **Azure SQL Database**([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Dynamics 365용 고객의 소리는 SQL Azure를 사용하여 다음을 저장합니다.  
  
-   파이프 데이터  
  
-   설문 메타데이터  
  
-   조직(테넌트) 데이터  
  
 **Azure Blob Storage**([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 설문 정의 및 부분적으로 완료된(저장된) 응답은 Azure Blob Storage에 저장됩니다.  
  
 **Azure Content Delivery Network(CDN)**([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Dynamics 365용 고객의 소리 솔루션은 Azure Content Delivery Network를 사용하여 이미지(고객 로고와 같은 업로드된 이미지 포함), JavaScript 및 CSS와 같은 정적 콘텐츠를 설문 런타임에 제공합니다.  
  
 **Azure Active Directory**([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Dynamics 365용 고객의 소리 솔루션은 Azure Active Directory 서비스를 사용하여 웹 서비스를 인증합니다.  
  
 **Azure Service Bus**([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 설문이 표시/제출될 때 작성된 메시지는 Azure 작업자 역할이 조직의 Dynamics 365 인스턴스로 설문 응답을 밀어 넣고 Dynamics 365 엔터티 레코드로 유지할 때까지 조직의(테넌트의) Azure Service Bus 큐에 임시로 저장됩니다.
