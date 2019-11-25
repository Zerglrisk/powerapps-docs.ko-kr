---
title: '미리 보기: 솔루션에서 환경 변수 사용 | MicrosoftDocs'
description: 환경 변수를 사용하여 솔루션에서 애플리케이션 구성 데이터를 마이그레이션하십시오.
Keywords: 환경 변수, 변수, 모델 기반 앱, 구성 데이터
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0c3189fceebb785a022d04c58ff6cf71fd388bc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758287"
---
# <a name="preview-environment-variables-overview"></a>미리 보기: 환경 변수 개요 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

앱과 흐름에는 종종 환경에 따라 다른 구성 설정이 필요합니다. 구성 가능한 입력 매개 변수인 환경 변수를 사용하면 사용자 지정 내의 하드 코딩 값 또는 추가 도구를 사용하는 것에 비해 데이터를 별도로 관리할 수 있습니다. 솔루션 구성 요소이므로 구성 데이터를 레코드 데이터로 가져오는 것보다 수행 능력이 훨씬 우수합니다.

환경 변수 사용의 이점:
- 프로덕션 환경에서 구성 가능한 값을 수동으로 편집할 필요가 없습니다.
- 한 곳에서 하나 이상의 변수를 구성하고 매개 변수처럼 여러 솔루션 구성 요소에서 참조합니다.
- 코드 변경 없이 값을 업데이트합니다.
- [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)에서 관리하는 세분화된 수준의 보안.
- 제한이 없는 변수 수(최대 솔루션 크기는 29MB입니다).
- 정의와 값을 독립적으로 또는 함께 제공합니다.
- [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager)와 [DevOps](/powerapps/developer/common-data-service/build-tools-overview) 도구에서 지원하여 지속적인 통합 및 지속적인 제공(CI/CD)을 가능하게 합니다.
- 지역화를 지원합니다.
- 기능 플래그 및 기타 애플리케이션 설정을 제어하는 데 사용할 수 있습니다.

> [!IMPORTANT]
> - 이는 미리 보기 기능입니다.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-they-work"></a>작동 방식은 어떻습니까?
환경 변수는 최신 솔루션 인터페이스를 통해 또는 [코드를 사용](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds)하여 만들고 관리할 수 있습니다. 값을 위해 솔루션 패키지 내에 별도의 JSON 파일이 생성되며 소스 제어에서 관리하고 빌드 파이프라인에서 수정할 수도 있습니다. Excel로 내보내기 및 Excel에서 가져오기가 지원됩니다. 환경 변수를 작성한 후에는 플러그 인, 흐름 및 기타 구성 요소 내에서 입력으로 변수를 사용할 수 있습니다.

## <a name="default-value"></a>기본값
이 필드는 환경 변수 정의 엔터티의 일부이며 필수는 아닙니다. 프로덕션 환경에 대해 또는 다른 환경에 대해 값을 변경할 필요가 없는 경우 기본값을 설정하십시오.

## <a name="value"></a>값
현재 값 또는 재정의 값이라고도 하는 이 필드는 선택 사항이며 환경 변수 값 엔터티의 일부입니다. 현재 환경에서 기본값을 다시 정의하려면 값을 설정하십시오. 다음 환경에서 사용하지 않으려면 솔루션에서 값을 제거하십시오. 값은 내보내는 solution.zip 파일 내에서 별도의 JSON 파일로도 분리됩니다. 

>[!NOTE]
> 정의 없이는 값이 존재할 수 없습니다. 인터페이스는 정의당 하나의 값만 생성할 수 있습니다. 

기본값과 현재 값을 분리하면 정의와 기본값을 현재 값과 별도로 서비스할 수 있습니다. 또한 특정 런타임 컨텍스트에 속하는 여러 값을 지원하도록 향후에 기능을 확장할 수 있습니다.

## <a name="notifications"></a>알림
환경 변수에 값이 없으면 알림이 표시됩니다. 변수에 종속된 구성 요소가 실패하지 않도록 값을 설정해야 합니다. 또한 파트너가 값 없이 변수를 전달할 수 있으며 고객에게 값을 입력하라는 메시지가 표시됩니다.

>[!NOTE]
> 파트너는 고객에게 값을 제공하도록 요구하는 자체 인터페이스를 구축하는 것이 좋습니다. 이 단계를 건너뛰면 알림이 실패를 방지하는 데 도움이 됩니다. 

## <a name="security"></a>보안
환경 변수 정의 및 환경 변수 값 엔터티는 모두 [사용자 또는 팀이 담당](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities)합니다. 환경 변수를 사용하는 애플리케이션을 만들 때는 사용자에게 적절한 수준의 권한을 할당해야 합니다. 추가 정보: [Common Data Service의 보안](https://docs.microsoft.com/power-platform/admin/wp-security). 

## <a name="current-limitations"></a>현재 제한 사항
- 캐싱. 값을 가져오기 위해 플러그 인이 쿼리를 실행해야 합니다. 
- 캔버스 앱 및 흐름은 엔터티 레코드 데이터와 같은 환경 변수를 사용할 수 있습니다. 추후에 캔버스 앱 및 흐름 디자이너에 추가 작업을 구축할 계획입니다. 이를 통해 작성을 단순화하고 특정 앱 또는 흐름에서 사용 중인 환경 변수에 대한 가시성을 높일 수 있습니다.
- 암호 관리를 위한 Azure Key Vault 통합. 현재 환경 변수를 사용하여 암호 및 키와 같은 보안 데이터를 저장해서는 안 됩니다.
- 데이터 유형은 최신 솔루션 인터페이스에서만 검증되지만 현재 미리 보기 중에는 서버에서 검증되지 않습니다. 
- 특정 구성 요소 유형에 대해서는 종속성이 적용되지 않습니다.
- Excel을 사용하여 환경 변수를 가져오는 경우 게시자 접두사를 SchemaName 앞에 추가해야 합니다.

### <a name="see-also"></a>참조
[플러그 인을 사용하여 비즈니스 프로세스 확장](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[웹 API 샘플](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[Common Data Service를 사용하여 처음부터 Canvas 앱 만들기.](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[Common Data Service로 흐름 만들기](https://docs.microsoft.com/flow/connection-cds)
