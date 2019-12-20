---
title: 엔터티의 라이선스 요구 사항| Microsoft Docs
description: Common Data Service 내의 엔터티의 라이선스 요구 사항에 대한 설명입니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a44bdc829defb8434b9b6de24392e360039de3c4
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864219"
---
# <a name="license-requirements-for-entities"></a>엔터티의 라이선스 요건

> [!IMPORTANT]
> 이 항목은 최신 버전이 아니며 2019년 10월 1일부터 적용 가능한 최신 라이선스 변경 사항을 반영하여 곧 업데이트될 예정입니다. 엔터티의 라이선스 요구 사항에 대한 최신 정보는 [Power Apps 라이선스 가이드](https://go.microsoft.com/fwlink/?linkid=2085130)를 참조하십시오.

앱 제작자는 Common Data Service에서 사용 가능한 대부분의 엔터티를 앱(Common Data Model의 일부인 사용자 지정 엔터티 및 엔터티 포함)에 사용하여 Power Apps 플랜 1 또는 Power Automate 플랜 1 라이선스가 있는 사용자를 위한 앱과 흐름을 만들 수 있습니다. 일부 경우에는 엔터티에는 복잡한 비즈니스 논리가 포함되거나 앱 사용자에게 특정 라이선스가 필요한 Dynamics 365 응용 프로그램에 연결되어 있습니다. 


|엔터티    |설명    |요구 사항    |
|---------|---------|---------|
|복잡한 비즈니스 논리가 있는 엔터티   | 이러한 엔터티는 복합 서버 쪽 비즈니스 논리를 사용하는 엔터티입니다. 예를 들어 실시간 워크플로 또는 코드 플러그 인을 사용하는 엔터티입니다.       |  [Power Apps 플랜 2](https://powerapps.microsoft.com/pricing/) 또는 [Flow 플랜 2](https://flow.microsoft.com/pricing/)        |
|제한된 엔터티  |  이는 Common Data Service에서 표준이 아니며, Dynamics 365(예: Dynamics 365 Sales 또는 Dynamics 365 Customer Service) 또는 타사 솔루션에서 사용할 수 있는 모델 기반 앱에 포함된 엔터티입니다. 예를 들어 참조 문서, 목표 및 권리 유형 엔터티가 있습니다.     |  [Dynamics 365 계획](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> 이러한 엔터티를 사용하는 앱 및 흐름에서는 앱이나 흐름의 제작자 또는 개발자가 아닌 앱 및 흐름 사용자에게 적절하게 라이선스를 부여 받아야 합니다.

## <a name="entities-with-complex-business-logic"></a>복잡한 비즈니스 논리가 있는 엔터티
다음과 같은 복잡한 서버 쪽 논리를 포함하는 엔터티에는 이러한 엔터티를 사용하는 앱 또는 흐름 사용자에게 Power Apps 플랜 2 또는 Power Automate 플랜 2 라이선스가 있어야 합니다.

* 코드 플러그 인(자세한 내용은 [플러그 인 개발](/powerapps/developer/common-data-service/plug-ins) 참조)
* 실시간 워크플로(자세한 내용은 [워크플로 프로세스](/flow/workflow-processes) 참조)

    > [!NOTE]
    >  실시간 워크플로로 변환된 워크플로만 실시간 및 동기식으로 간주됩니다. 백그라운드에서 실행되는 워크플로는 적절한 Power Apps 플랜에 계속 사용할 수 있으며 추가 라이선스가 필요하지 않습니다.

엔터티에 복잡한 비즈니스 논리를 추가했는지 여부를 확인 하려면 사용자 환경에서 구성된 플러그 인 어셈블리 및 워크플로 목록을 검토합니다. Dynamics 365(예: Dynamics 365 Sales 또는 Dynamics 365 Customer Service)에서 모델 기반 앱을 설치한 후 서버 쪽 논리를 포함할 수 이씨는 엔터티 목록은 [Power Apps 플랜 2 라이선스가 필요한 복합 엔터티](data-platform-complex-entities.md)를 참조하십시오.  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>복잡한 비즈니스 논리를 추가할 때 라이선스 요구 사항에 영향
앱 제작자는 Common Data Service의 엔터티에 코드 플러그 인 및 실시간 워크플로를 추가할 수 있지만 이렇게 하면 이미 배포된 앱의 사용자에 대한 라이선스 요구 사항이 변경될 수 있습니다. 앱 제작자는 엔터티에 복잡한 비즈니스 논리를 추가할 때 주의해야 하며, 먼저 해당 엔터티를 사용하는 앱과 해당 앱의 사용자에게 적절한 라이선스가 있는지 확인해야 합니다.

## <a name="restricted-entities"></a>제한된 엔터티
Dynamics 365 응용 프로그램의 기능에 연결된 특정 엔터티는 엔터티 내에서 레코드를 생성, 업데이트 또는 삭제하려는 경우 앱 사용자가 해당 응용 프로그램에 해당하는 라이선스를 가지고 있어야 합니다. 제한된 엔터티의 전체 목록은 [Dynamics 365 라이선스가 필요한 제한된 엔터티](data-platform-restricted-entities.md)를 참조하십시오.

## <a name="licensing-examples"></a>라이선스 예
Barb과 Isaac은 앱이 데이터를 저장하기 위해 Common Data Service를 사용하여 Power Apps에서 앱을 만들고 있습니다.

Barb은 다음 두 개의 캔버스 응용 프로그램을 만듭니다.

* 앱 1 &ndash; 관련 정보를 저장하는 사용자 지정 엔터티와 함께 약속 엔터티를 사용합니다.
* 앱 2 &ndash; 제한된 엔터티인 문제 엔터티와 함께 약속 엔터티를 사용합니다.

Isaac은 다음 두 가지 모델 기반 앱을 만듭니다.

* 앱 3 &ndash; 관련 정보를 저장하는 사용자 지정 엔터티와 함께 약속 엔터티를 사용합니다.
* 앱 4 &ndash; 제한된 엔터티인 문제 엔터티와 함께 약속 엔터티를 사용합니다.

Barb과 Issac은 다음과 같은 라이선스가 필요합니다.
* Barb은 Common Data Service를 사용하여 캔버스 앱을 만들 수 있는 Power Apps 플랜 1 라이선스가 필요합니다. 데이터베이스를 만들거나 사용자 지정 엔터티를 만들어야 하는 경우에는 Power Apps 플랜 2 라이선스가 필요합니다.

* Isaac은 모델 기반 앱을 빌드할 수 있는 Power Apps 플랜 2 라이선스가 필요합니다.

앱 사용자는 다음 라이선스가 필요합니다.
* 앱에 복잡한 비즈니스 논리 또는 제한된 엔터티가 있는 엔터티가 포함되어 있지 않기 때문에 앱 1 사용자에게는 Power Apps 플랜 1 또는 플랜 2 라이선스만 필요합니다.

* 앱에 제한된 엔터티가 포함되어 있으므로 앱 2 사용자는 Dynamics 365 Customer Service, Enterprise Edition 라이선스(또는 Dynamics 365 또는 Dynamics 365 Customer Engagement 플랜)가 필요합니다.

* 이는 모델 기반 앱이기 때문에 앱 3 사용자는 Power Apps 플랜 2 라이선스가 필요합니다.

* 앱에 제한된 엔터티가 포함되어 있으므로 앱 4 사용자는 Dynamics 365 for Customer Service, Enterprise Edition 라이선스(또는 Dynamics 365 또는 Dynamics 365 Customer Engagement 플랜)가 필요합니다.

    Dynamics 365 for Customer Service 플랜에는 사용자가 모델 중심 앱을 실행할 수 있는 Power Apps 플랜 2 라이선스가 포함되어 있습니다.

이제 Barb과 Isaac이 앱에서 사용하는 사용자 지정 엔터티에 실시간 워크플로를 추가하면 어떻게 되는지 알아보겠습니다.

Barb과 Issac은 다음과 같은 라이선스가 필요합니다.
* Barb은 여전히 Common Data Service를 사용하여 캔버스 앱을 만들 수 있는 Power Apps 플랜 1 라이선스가 필요합니다.

* Isaac은 여전히 모델 기반 앱을 빌드할 수 있는 Power Apps 플랜 2 라이선스가 필요합니다.

앱 사용자는 다음 라이선스가 필요합니다.
* 앱에 실시간 워크플로가 있는 엔터티가 포함되어 있으므로 앱 1 사용자에게는 이제 Power Apps 플랜 2 라이선스가 필요합니다.

* 앱에 제한된 엔터티가 포함되어 있으므로 앱 2 사용자는 여전히 Dynamics 365 for Customer Service, Enterprise Edition 라이선스(또는 Dynamics 365 또는 Dynamics 365 Customer Engagement 플랜)가 필요합니다. 

* 이는 모델 기반 앱이기 때문에 앱 3 사용자는 여전히 Power Apps 플랜 2 라이선스가 필요합니다.

* 앱에 제한된 엔터티가 포함되어 있으므로 앱 4 사용자는 여전히 Dynamics 365 for Customer Service, Enterprise Edition 라이선스(또는 Dynamics 365 또는 Dynamics 365 Customer Engagement 플랜)가 필요합니다.

    Dynamics 365 for Customer Service 플랜에는 사용자가 모델 중심 앱을 실행할 수 있는 Power Apps 플랜 2 라이선스가 포함되어 있습니다.

이 변경의 영향을 받는 유일한 앱은 이전에 Power Apps 플랜 1 라이선스가 필요했지만 이제는 복잡한 비즈니스 논리가 있는 엔터티가 포함되어 있기 때문에 Power Apps 플랜 2 라이선스가 필요합니다. 

## <a name="more-about-licensing"></a>라이선싱 자세히 알아보기
Power Apps 및 Dynamics 365 라이선스에 대한 자세한 내용은 [라이선스 개요](../../administrator/pricing-billing-skus.md)를 참조하십시오.
