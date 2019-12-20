---
title: API 제한 개요(Common Data Service) | Microsoft Docs
description: Common Data Service API 요청에 대한 제한을 이해합니다.
ms.custom: ''
ms.date: 11/23/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 786994fa531698919d1506dc90217f435e43fb8a
ms.sourcegitcommit: abeedb952afc5e09ae4c158611e4813b63cb49b3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2019
ms.locfileid: "2854784"
---
# <a name="common-data-service-api-limits-overview"></a>Common Data Service API 제한 개요

Common Data Service API 제한은 서비스 수준, 가용성 및 품질을 보장합니다. Common Data Service API 제한은 Power Platform 요청 제한 및 할당의 일부입니다. 이 항목에서는 특히 Dynamics 365의 모델 기반 앱(Dynamics 365 Sales 및 Dynamics 365 Customer Service 등), Power Apps, Common Data Service/Dynamics 365의 모델 기반 앱에 연결하는 Power Automate에 적용 가능한 Common Data Service에 대한 제한을 소개합니다. 

Power Platform 내 모든 영역의 제한에 대한 정보는 [Power Platform 요청 제한 및 할당](/power-platform/admin/api-request-limits-allocations)을 참조하세요.

Common Data Service에는 *권리 유형*과 *서비스 보호* 제한이라는 두 가지 범주의 제한이 적용됩니다.

## <a name="entitlement-limits"></a>권리 유형 제한

이러한 제한은 사용자가 매일 요청할 수 있는 횟수를 나타냅니다. 할당된 제한은 각 사용자에게 할당된 라이선스 유형에 따라 다릅니다.

사용자가 요청 권리 유형을 초과하면 관리자에게 통지되어 해당 사용자에게 Power Apps와 Power Automate 요청 용량을 할당할 수 있습니다. 이 시점에서 사용자는 때때로 합리적인 초과 사용으로 인해 앱을 사용하지 못하도록 차단되지 않습니다.

Common Data Service의 경우, API 요청에는 레코드가 생성, 검색, 업데이트 또는 삭제(CRUD)되는 엔터티 레코드와 상호 작용하는 모든 데이터 작업이 포함됩니다. *공유*와 *할당*과 같은 특수 작업은 업데이트로 간주되므로 여기에 포함됩니다. 이러한 요청은 모든 클라이언트 또는 응용 프로그램에서 끝점을 사용하여 이루어질 수 있습니다. 여기에는 플러그 인, 비동기 워크플로 및 사용자 지정 컨트롤에 의해 수행되는 작업이 포함되며, 이에 국한되지 않습니다. 로그인, 로그아웃 및 시스템 메타데이터 작업과 같이 제외된 작은 시스템 내부 작업 집합이 있습니다.

> [!IMPORTANT]
> Power Platform API 요청 할당에는 Power Automate, AI Builder 및 커넥터 API가 포함됩니다. Common Data Service 요청을 발생시키는 커넥터를 통한 모든 요청은 1개의 Power Platform 요청을 나타냅니다.

이러한 권리 유형 제한에 대한 자세한 내용은 [라이선스 기반 Microsoft Power Platform 요청 할당](/power-platform/admin/api-request-limits-allocations#microsoft-power-platform-requests-allocations-based-on-licenses)을 참조하세요.

용량 추가 기능 보기 및 할당에 대한 내용은 [용량 추가 기능](/power-platform/admin/capacity-add-on)을 참조하십시오.

개별 용량 추가 기능 구매에 대한 자세한 내용은 [Power Apps 및 Power Automate 라이선싱 가이드](https://go.microsoft.com/fwlink/?linkid=2085130)를 참조하세요. 
<!-- There should be some help about purchasing these through the Portal -->


## <a name="service-protection-limits"></a>서비스 보호 제한

모든 사람에게 일관된 가용성과 성능을 보장하기 위해 Common Data Service에서 API를 사용하는 방식에 일부 제한을 적용합니다. 서비스 보호 API 제한은 응용 프로그램을 실행하는 사용자가 리소스 제약 조건에 따라 서로 간섭할 수 없도록 합니다. 이 제한은 플랫폼의 일반 사용자에게는 영향을 주지 않습니다. 많은 수의 API 요청을 수행하는 응용 프로그램만 영향을 받을 수 있습니다. 이 제한은 Common Data Service 플랫폼의 가용성 및 성능 특성을 위협하는 요청 볼륨의 무작위적이고 예상치 못한 갑작스런 증가로부터 보호 수준을 제공합니다.

사용자 계정당 동시 연결 수, 연결당 API 요청 수 및 각 연결에 사용할 수 있는 실행 시간을 제한합니다. 이는 5분 슬라이딩 기간 내에 평가됩니다. 이러한 제한 중 하나를 초과하면 플랫폼에서 예외가 throw됩니다.

> [!NOTE]
> 서비스 보호 제한은 권리 유형 제한에 대해 계산된 엔터티에 대한 CRUD 작업뿐만 아니라 모든 요청에 적용됩니다.
> 
> 플러그 인 및 사용자 지정 워크플로 활동은 로그인한 사용자와 상관없이 서버에서 실행되므로 플러그 인 코드에서 작성된 API 호출에 대해 서비스 보호 API 제한이 적용되지 않습니다.

서비스 보호 제한은 일반적으로 많은 양의 데이터 작업을 수행하는 응용 프로그램에서만 발생하므로 이러한 응용 프로그램을 작성하는 개발자는 이러한 예외가 반환된 후 일정 시간 후에 작업을 다시 시도하기 위해 패턴을 적용하는 것이 좋습니다. 이를 통해 응용 프로그램은 서비스가 보내는 예외에 응답하고, 총 요청 수를 줄이고, 가능한 최고 처리량을 달성할 수 있습니다.

반환될 수 있는 특정 오류 및 개발자가 이러한 오류에 응답하기 위해 패턴을 적용하는 방법에 대한 정보는 [서비스 보호 API 제한](../../developer/common-data-service/api-limits.md)을 참조하십시오.


### <a name="see-also"></a>참조

[Power Platform 관리 / 라이선싱 및 라이선스 관리 / 요청 제한 및 할당](/power-platform/admin/api-request-limits-allocations)<br />
[개발자 / 코드를 사용한 데이터 작업 / 서비스 보호 API 제한](../../developer/common-data-service/api-limits.md)

