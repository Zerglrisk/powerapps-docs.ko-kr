---
ms.openlocfilehash: 3fb3961dc88033a44c60c4b6f09124c7c38a11bf
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212781"
---
Voice of the Customer for Dynamics 365을 사용하도록 설정하여 Dynamics 365 내에서 설문 조사를 게시하는 경우 설문 조사 정의를 Azure로 전송하고 Azure Storage에 저장합니다. 응답자가 설문 조사를 제출하는 경우(이메일을 통해 응답자에게 전송된 설문 조사 초대 링크를 열어) 설문 조사 응답은 일시적으로 Azure Service Bus에 저장된 다음, Dynamics 365에서 검색되고 저장됩니다. 이 응답은 Dynamics 365에 저장됐으면 Azure에서 삭제됩니다.  
  
 설문 조사를 렌더링하는 경우 설문 조사(질문, 답변 등과 같은 설문 조사 요소 내)에 고객 이름, 제품 이름, 사례 번호 등과 같은 Dynamics 365 데이터를 포함할 수 있습니다. 설문 조사 초대 링크를 생성하는 경우 이러한 Dynamics 365 데이터는 설문 초대 링크 내에서 사용되는 식별자 대신 Dynamics 365에서 전송되고 Azure SQL Database에 저장됩니다. 설문 조사 초대 링크를 사용하여 설문 조사를 연 후 설문 조사 내에서 Dynamics 365 데이터를 표시하는 데 이 식별자가 사용됩니다. 이메일을 통해 응답자에게 전송되는 설문 조사 링크 내의 식별자는 응답자의 이메일 시스템에 저장됩니다.  
  
 관리자는 Dynamics 365 조직에 솔루션으로 Voice of the Customer for Dynamics 365 기능을 설치하여 해당 기능을 사용하도록 설정할 수 있습니다. 또한 관리자가 Dynamics 365 조직에서 이 솔루션을 제거하여 해당 기능을 나중에 비활성화할 수 있습니다.  
  
 Voice of the Customer for Dynamics 365 기능과 관련된 Azure 구성 요소 및 서비스는 다음 섹션에 자세히 나와 있습니다.  
  
 참고: 추가 Azure 서비스 제공에 대 한 자세한 내용은 Microsoft Azure 보안 센터 ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/))를 참조 하세요.  
  
 **클라우드 서비스**([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **디자이너 서비스(웹 역할)**  
  
 이 서비스는 다중 테넌트 Voice of the Customer for Dynamics 365 Azure 구성 요소 및 Dynamics 365 조직 간의 통신을 위해 여러 웹 서비스를 제공합니다.  예를 들어 설문 조사는 게시된 후 Azure Blob Storage에 저장됩니다.  설문 조사 응답은 Azure Service Bus 큐에서 검색되고 Dynamics 365 조직에서 지속되도록 반환됩니다.  Azure Active Directory에 대한 모든 요청을 인증합니다.  
  
 **설문 조사 런타임(웹 역할)**  
  
 이 웹 애플리케이션은 응답자에게 설문 조사를 제공합니다.  제출된 설문 조사 응답은 처리되기 전에 Dynamics 365 비동기 서비스에서 검색된 Azure Service Bus 큐에 일시적으로 저장됩니다.  
  
 **응답 프로세서(작업자 역할)**  
  
 이 작업자 역할은 Dynamics 365에서 만들 수 있는 유효한 설문 조사 응답에 완료된 원시 설문 조사를 처리하는 일을 담당합니다.  
  
 **푸시 프로세서 (작업자 역할)**   이 작업자 역할은 유효한 설문 조사 응답을 처리 하 고 Dynamics 365 엔터티 레코드로 업데이트 하는 작업을 담당 합니다. 
 
 **Azure Key Vault**([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 모든 클라우드 서비스는 구성 데이터를 Azure Key Vault에 저장합니다.  조직으로서 테넌트 데이터는 SQL Azure에 저장됩니다.  
  
 **Azure SQL Database**([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Dynamics 365 대한 고객 의견은 다음을 저장하는 데 SQL Azure를 사용합니다.  
  
-   파이프로 연결된 데이터  
  
-   설문 조사 메타데이터  
  
-   조직(테넌트) 데이터  
  
 **Azure Blob Storage**([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 설문 조사 정의 및 일부만 완료된(저장된) 응답은 Azure Blob Storage에 저장됩니다.  
  
 **Azure CDN(Content Delivery Network)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Voice of the Customer for Dynamics 365 솔루션은 Azure Content Delivery Network를 사용하여 이미지 같은 설문 조사 런타임(고객 로고, JavaScript 및 CSS와 같은 업로드된 이미지를 포함하여)에 정적 콘텐츠를 제공합니다.  
  
 **Azure Active Directory**([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Voice of the Customer for Dynamics 365 솔루션은 Azure Active Directory 서비스를 사용하여 웹 서비스를 인증합니다.  
  
 **Azure Service Bus**([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 설문 조사를 표시/제출할 때 생성된 메시지는 Azure 작업자 역할이 설문 조사 응답을 조직의 Dynamics 365 인스턴스로 푸시하여 Dynamics 365 엔터티 레코드로 계속 유지될 때까지 조직(테넌트)의 Azure Service Bus 큐에 일시적으로 저장됩니다.
