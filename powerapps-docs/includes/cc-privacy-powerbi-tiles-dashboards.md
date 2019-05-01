---
ms.openlocfilehash: 41ec7aed42a950e5adf0b87783fc568dbe9d02af
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61581196"
---
Power BI 타일 및 대시보드를 포함하도록 설정하여 사용자가 Power BI 타일 또는 대시보드를 포함할 경우 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]에 대한 해당 사용자의 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 권한 부여 토큰은 암시적으로 권한을 부여하여 Power BI 서비스에서 인증하는 데 사용되며 최종 사용자에게 원활한 "Single Sign-On" 환경을 제공합니다.  
  
 관리자는 언제든 Power BI 타일 및 대시보드를 포함하지 않도록 설정하여 Power BI 서비스에서 인증하는 데 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 권한 부여 토큰의 사용을 중지할 수 있습니다. 모든 기존 타일 또는 대시보드는 최종 사용자에 대한 렌더링을 중지합니다.  
  
 Power BI 타일 포함과 관련된 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 구성 요소 또는 서비스는 다음 섹션에 자세히 설명되어 있습니다.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 이 서비스는 API 및 UI 인증용 Power BI 서비스와 교환된 인증 토큰을 제공합니다.