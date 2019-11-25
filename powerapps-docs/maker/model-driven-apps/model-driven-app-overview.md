---
title: PowerApps에서 모델 기반 앱 빌드 개요 | Microsoft Docs
description: PowerApps 앱에서 사용할 엔터티를 만들고 구성하기 위한 단계별 지침입니다.
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 08/09/2018
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 38ea420dc973e5e6c0a4df2ff361344c4704137a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711746"
---
# <a name="what-are-model-driven-apps-in-powerapps"></a>PowerApps의 모델 기반 앱이란 무엇입니까?

모델 기반 앱 디자인은 앱 개발에 대한 구성 요소 중심의 접근 방식입니다. 모델 기반 앱 디자인에는 코드가 필요하지 않으며 사용자가 만드는 앱은 간단하거나 매우 복잡할 수 있습니다.  디자이너가 앱 레이아웃을 완벽하게 제어할 수 있는 캔버스 앱 개발과 달리 모델 기반 앱은 대부분 레이아웃을 결정하고 앱에 추가하는 구성 요소에 의해 주로 지정됩니다. 

![샘플 모델 기반 앱](media/model-driven-app-overview/model-app-sample.png)

모델 기반 앱 디자인은 다음과 같은 이점을 제공합니다.
- 풍부한 구성 요소 중심의 코드 없는 디자인 환경 
- 데스크톱에서 모바일에 이르기까지 다양한 장치에서 유사한 UI를 사용하여 복잡한 반응형 앱 만들기
- 풍부한 디자인 기능 
- 앱을 솔루션으로 배포할 수 있습니다.
 
## <a name="the-approach-to-model-driven-app-making"></a>모델 기반 앱 제작에 대한 접근 방식
기본 수준에서 모델 기반 앱 만들기는 세 가지 주요 포커스 영역으로 구성됩니다.

- 비즈니스 데이터 모델링 
- 비즈니스 프로세스 정의 
- 앱 작성

### <a name="modeling-business-data"></a>비즈니스 데이터 모델링
비즈니스 데이터를 모델링하려면 앱에 필요한 데이터와 이 데이터가 다른 데이터와 관련되는 방식을 결정해야 합니다. 모델 기반 디자인에서는 디자이너가 코드를 작성하지 않고도 응용 프로그램을 사용자 지정할 수 있도록 메타데이터 기반 아키텍처를 사용합니다. 메타데이터는 "데이터에 대한 데이터"를 의미하고 시스템에 저장된 데이터의 구조를 정의합니다. [자습서: PowerApps에서 구성 요소가 있는 사용자 지정 엔터티 만들기](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>비즈니스 프로세스 정의
일관된 비즈니스 프로세스를 정의하고 적용하는 것은 모델 기반 앱 디자인의 핵심 요소입니다. 일관된 프로세스를 사용하면 앱 사용자가 기계적인 단계들을 수행하기 위해 기억할 필요 없이 작업에 집중할 수 있습니다. 프로세스는 간단하거나 복잡할 수 있으며 시간이 지나면 변경되는 경우가 많습니다. 프로세스를 만들려면 PowerApps.com 모델 기반 영역에서 ![설정](media/powerapps-gear.png) > **고급 사용자 지정** > **솔루션 탐색기**를 선택합니다. 그런 다음 솔루션 탐색기의 왼쪽 탐색 창에서 **프로세스**를 선택한 다음 **새로 만들기**를 선택합니다. 추가 정보: [비즈니스 프로세스 흐름 개요](/flow/business-process-flows-overview) 및 [Common Data Service에 비즈니스 논리 적용](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>모델 기반 앱 작성
데이터를 모델링하고 프로세스를 정의한 후에는 앱 디자이너를 사용하여 필요한 구성 요소를 선택하고 구성하여 앱을 빌드합니다.

![앱 디자이너](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>다음 단계

[첫 모델 기반 앱을 빌드하기](build-first-model-driven-app.md)

[모델 기반 앱 구성 요소 이해](model-driven-app-components.md)

