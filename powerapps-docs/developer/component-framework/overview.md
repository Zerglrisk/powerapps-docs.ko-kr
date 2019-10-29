---
title: PowerApps 구성 요소 프레임 워크 개요 | Microsoft Docs
description: PowerApps 구성 요소 프레임 워크를 사용 하 여 사용자가 양식, 보기 및 대시보드에서 데이터를 보고 작업할 수 있는 향상 된 환경을 제공 하는 코드 구성 요소를 만들 수 있습니다.
keywords: 구성 요소 프레임 워크, 코드 구성 요소, PowerApps 컨트롤
author: nkrb
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.custom:
- dyn365-a11y
- dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
ms.openlocfilehash: a9f157dfb3d0a7d29cebadee935c84826ae040d6
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025674"
---
# <a name="powerapps-component-framework-overview"></a>PowerApps 구성 요소 프레임 워크 개요

PowerApps 구성 요소 프레임 워크는 전문 개발자와 앱 제작자가 모델 기반 앱 및 캔버스 앱에 대 한 코드 구성 요소를 만들 수 있도록 지원 합니다. (실험적 미리 보기) 사용자가 양식, 보기에서 데이터를 보고 작업할 수 있는 향상 된 사용자 환경을 제공 합니다. 및 대시보드. 예:

- 숫자 텍스트 값을 표시 하는 필드를 `dial` 또는 `slider` 코드 구성 요소로 바꿉니다.
- 목록을 `Calendar` 또는 `Map` 같은 데이터 집합에 바인딩된 완전히 다른 시각적 환경으로 변환 합니다.

> [!IMPORTANT]
> - PowerApps 구성 요소 프레임 워크는 캔버스 앱에 대 한 실험적 미리 보기와 모델 기반 앱에 대 한 GA에 있습니다. 이는 모델 기반 앱에 대해 지원 되는 모든 Api가 캔버스 앱에서 아직 지원 되지 않을 수 있음을 의미 합니다.
> - 기본적으로 PowerApps 구성 요소 프레임 워크는 모델 기반 앱에 대해 사용 하도록 설정 됩니다. Canvas 앱에 대해이 기능을 사용 하려면 [canvas 앱에 대 한 가용성](component-framework-for-canvas-apps.md)을 참조 하세요.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas 앱은 *데이터 집합* 형식이 아닌 코드 구성 요소의 *필드* 형식만 지원 합니다.


Powerapps 구성 요소 프레임 워크를 사용 하 여 모든 다양 한 PowerApps 기능에서 사용할 수 있는 코드 구성 요소를 만듭니다. HTML 웹 리소스와 달리 코드 구성 요소는 동일한 컨텍스트의 일부로 렌더링 되 고 다른 구성 요소와 동시에 로드 되므로 사용자에 게 원활한 환경을 제공 합니다. 개발자는 모든 HTML, CSS 및 TypeScript 또는 JavaScript 파일을 단일 솔루션 패키지 파일에 묶을 수 있습니다. 코드 구성 요소는 여러 엔터티 및 폼에서 여러 번 다시 사용할 수 있습니다.

코드 구성 요소는 구성 요소 수명 주기 관리, 상황별 데이터 및 메타 데이터 액세스, Web API를 통한 원활한 서버 액세스, 유틸리티 및 데이터 형식 지정 방법, 카메라와 같은 장치 기능 등을 제공 하는 풍부한 프레임 워크 Api 집합에 액세스할 수 있습니다. 대화 상자, 조회, 전체 페이지 렌더링 등의 호출 하기 쉬운 UX 요소와 함께 위치 및 마이크  

개발자와 앱 제조업체는 최신 웹 사례를 사용 하 고 외부 라이브러리의 기능을 활용 하 여 고급 사용자 상호 작용을 만들 수 있습니다. 프레임 워크는 구성 요소 수명 주기를 자동으로 처리 하 고, 응용 프로그램 비즈니스 논리를 유지 하며, 성능을 위해 최적화 합니다 (비동기 Iframe 없음). 구성 요소 정의, 종속성 및 구성은 모두 [솔루션](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) 으로 패키지 되 고 환경 간에 이동 될 수 있으며 [appsource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365)를 통해 제공 될 수 있습니다.  

## <a name="related-topics"></a>관련 항목

[코드 구성 요소 정의](custom-controls-overview.md)<br/>
[Canvas 앱에 대 한 가용성](component-framework-for-canvas-apps.md)<br/>
[코드 구성 요소 만들기 및 빌드](create-custom-controls-using-pcf.md)<br/>
[개발자용 PowerApps](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

