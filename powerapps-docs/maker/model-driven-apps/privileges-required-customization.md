---
title: 모델 기반 앱 사용자 지정에 필요한 권한 | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 43cf7f3a-7e26-4990-8b5a-c817ac6d51bb
caps.latest.revision: 13
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2dd56a541ab765bc990bba8fe7911d193b3eacc7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711526"
---
# <a name="privileges-required-for-model-driven-app-customization"></a>모델 기반 앱 사용자 지정에 필요한 권한

앱 사용자는 시스템을 개인 설정하고 다른 사용자와 일부 사용자 지정 항목을 공유할 수 있지만 올바른 권한이 있는 사용자만 을 사용하는 모든 사용자의 변경 내용을 적용할 수 있습니다.  
  
> [!NOTE]
>  이 섹션에서는 보안 역할을 사용하는 방법을 잘 알고 있다고 가정합니다. 보안 역할을 사용하는 방법에 대한 자세한 내용은 [사용자 만들기 및 보안 역할 할당](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)을 참조하십시오.  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>시스템 관리자 및 시스템 사용자 지정자 보안 역할  
 사용자 지정하는 모든 사용자는 계정과 함께 시스템 관리자 또는 시스템 사용자 지정자 보안 역할을 가지고 있습니다. 이러한 보안 역할은 앱을 사용자 지정하는 데 필요한 권한을 제공합니다.  
  
|시스템 관리자|시스템 맞춤자|  
|--------------------------|-----------------------|  
|시스템을 사용자 지정하는 전체 권한이 있음|시스템을 사용자 지정하는 전체 권한이 있음|  
|시스템의 모든 데이터를 볼 수 있음|만든 시스템 엔터티의 레코드만 볼 수 있음|  
  
 시스템 관리자와 시스템 사용자 지정자 보안 역할의 차이는 시스템 관리자에게는 시스템의 대부분의 레코드에 대한 읽기 권한이 있고 모든 항목을 볼 수 있다는 것입니다. 사용자 지정 작업을 수행해야 하는 사용자에게 시스템 사용자 지정자 역할을 할당하면 시스템 엔터티의 데이터를 일부 볼 수 없습니다. 하지만 테스트는 시스템을 사용자 지정하는 중요한 부분입니다. 시스템 사용자 지정자가 데이터를 볼 수 없을 경우 해당 사용자 지정 항목을 테스트할 레코드를 만들어야 합니다. 기본적으로 시스템 사용자 지정자에게는 사용자 지정 엔터티에 대한 전체 액세스 권한이 있습니다. 시스템 엔터티에 대해 있는 동일한 제한 사항을 가지려면 사용자 지정 엔터티에 대한 액세스 수준이 **조직**이 아니라 **사용자**가 되도록 시스템 사용자 지정자 보안 역할을 조정해야 합니다.  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>사용자 지정 작업 위임  
 필요한 변경 내용을 적용할 수 있도록 신뢰할 수 있는 사용자에게 일부 작업을 위임할 수 있습니다. 누구나 사용자 계정과 관련된 보안 역할을 여러 개 가질 수 있고, 보안 역할에서 부여한 권한과 액세스 권한은 권한의 *최소 제한* 수준을 기반으로 합니다.  
  
 즉, 이미 다른 보안 역할이 있는 사용자(예: 영업 관리자)에게 시스템 사용자 지정자 보안 역할을 제공할 수 있습니다. 이 역할로 사용자는 이미 가지고 있는 다른 권한 이외의 시스템을 사용자 정의할 수 있습니다. 이미 가지고 있는 보안 역할을 편집할 필요가 없으므로 원할 때 시스템 사용자 지정자 보안 역할을 사용자의 사용자 계정에서 제거할 수 있습니다.  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>사용자 지정 권한 없이 사용자 지정 항목 테스트  
 사용자 지정 권한이 없는 사용자 계정으로 수행한 모든 사용자 지정 항목을 항상 테스트해야 합니다. 이런 방식으로 시스템 관리자 또는 시스템 사용자 지정자 보안 역할이 없는 사용자가 사용자 지정 항목을 사용할 수 있습니다. 효과적으로 수행하려면 두 사용자 계정에 대한 액세스 권한이 필요합니다(시스템 관리자 보안 역할이 있는 계정 하나와 사용자 지정 항목을 사용할 사용자를 나타내는 보안 역할을 가진 계정 하나).  
  
> [!IMPORTANT]
>  사용자 계정이 하나만 있을 경우 시스템 관리자 보안 역할을 제거하지 마십시오. 시도하면 시스템에서 경고를 표시하지만 계속 시도하면 되돌릴 수 없습니다. 대부분의 보안 역할은 사용자의 보안 역할 편집을 허용하지 않습니다.  
  
## <a name="next-steps"></a>다음 단계  
[모델 기반 앱 구성 요소 이해](model-driven-app-components.md)

