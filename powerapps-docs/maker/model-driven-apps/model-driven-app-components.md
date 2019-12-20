---
title: Power Apps의 모델 기반 앱 구성 요소 이해 | MicrosoftDocs
description: 데이터, UI, 논리 및 시각화와 같은 모델 기반 앱의 다양한 구성 요소를 이해합니다.
Keywords: 필드, 특성, 모델 기반 앱
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 10/17/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4f1c05ca41e6873a0072e8ea6720343e468e38bb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863067"
---
# <a name="understand-model-driven-app-components"></a>모델 기반 앱 구성 요소 이해
잘 디자인된 모델 기반 앱은 완성된 앱의 모양과 기능을 빌드하기 위해 디자이너를 사용하여 선택한 여러 구성 요소로 구성됩니다. 디자이너가 앱을 구성하는 데 사용하는 컴포넌트 및 구성 요소 속성은 메타데이터가 됩니다. 

이러한 각 구성 요소가 앱 디자인에 어떻게 관련되는지를 이해하기 위해 여기서는 *데이터*, *UI*, *논리*및 *시각화* 범주로 구분됩니다. 

## <a name="data"></a>데이터
이러한 구성 요소는 앱의 기반이 되는 데이터와 구성 요소를 만들거나 편집하는 데 사용할 디자이너를 결정합니다.


|구성 요소  |설명  |디자이너  |
|---------|---------|---------|
|엔터티     |연락처나 거래처처럼 추적하는 속성을 가진 항목입니다. 여러 표준 엔터티는 사용할 수 없습니다. 비시스템 표준 엔터티(생산 엔터티)를 사용자 지정하거나 처음부터 사용자 지정 엔터티를 만들 수 있습니다.     | [!INCLUDE [powerapps](../../includes/powerapps.md)] 엔터티 디자이너        |
|관계     | 엔터티 관계는 엔터티가 서로 관련되는 방법을 정의할 수 있습니다. 하나는 1:N(일대다), N:1(다대일), 및 N:N(다대다) 유형의 관계입니다. 예를 들어 조회 필드를 엔터티에 추가하면 두 엔터티 간에 새로운 1:N 관계를 만들고 양식에 조회 필드를 배치할 수 있습니다.   | [!INCLUDE [powerapps](../../includes/powerapps.md)] 엔터티 디자이너        |
|필드     | 엔터티와 연결된 속성입니다. 필드는 입력하거나 선택할 수 있는 데이터 형식을 결정하는 데이터 형식으로 정의됩니다. 텍스트, 숫자, 날짜 및 시간, 통화 또는 조회를 예로 들 수 있습니다(다른 엔터티와의 관계를 만듦). 필드는 일반적으로 양식, 보기 및 검색과 함께 사용됩니다.        | [!INCLUDE [powerapps](../../includes/powerapps.md)] 엔터티 디자이너   |
|옵션 집합 필드     | 사용자에게 미리 정해진 옵션 집합을 제공하는 특수한 유형의 필드입니다. 각 옵션에는 숫자 값 및 레이블이 있습니다. 양식에 추가할 때 이 필드는 옵션을 선택할 수 있는 사용자를 위한 컨트롤을 표시합니다.  옵션 집합에는 두 가지 종류, 즉 사용자가 하나의 옵션만 선택할 수 있는 옵션 집합과 여러 개를 선택할 수 있는 다중 선택 옵션 집합입니다.  | [!INCLUDE [powerapps](../../includes/powerapps.md)] 옵션 집합 디자이너     |

추가 정보: [모델 기반 앱에 대한 데이터 정의](define-data-model-driven-app.md) 

## <a name="ui"></a>UI
이러한 구성 요소는 사용자가 앱과 상호 작용하는 방법을 결정합니다. 

|구성 요소  |설명  |디자이너  |
|---------|---------|---------|
|앱     | 앱의 구성 요소, 속성, 클라이언트 유형 및 URL과 같은 응용 프로그램 기본 사항을 결정합니다.      | 앱 디자이너   |
|사이트 맵     | 앱에 대한 탐색을 지정합니다.        | 사이트 맵 디자이너        |
|양식     | 조직에서 엔터티에 대해 추적하는 항목과 일치하는 지정된 엔터티에 대한 데이터 입력 필드 집합입니다. 예를 들어 사용자가 입력한 관련 정보를 특정 요청된 재주문 날짜와 함께 고객의 이전 주문을 추적하는 데이터 입력 필드 집합입니다.        | 양식 디자이너        |
|보기     | 보기는 특정 엔터티의 레코드 목록이 응용 프로그램에 표시되는 방법을 정의합니다. 보기는 표시할 열, 각 열의 너비, 정렬 동작 및 기본 필터를 정의합니다.   |  디자이너 보기       |

![앱 디자이너 및 양식 디자이너](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>논리
앱의 비즈니스 프로세스, 규칙 및 자동화를 결정합니다. [!INCLUDE [powerapps](../../includes/powerapps.md)] 제작자는 프로세스나 규칙의 유형과 관련된 디자이너를 사용합니다. 


|논리 유형  |설명  |디자이너  |
|---------|---------|---------|
|비즈니스 프로세스 흐름     | 표준 비즈니스 프로세스를 통해 사용자를 안내하는 온라인 프로세스입니다. 예를 들어 모든 직원이 고객 서비스 요청을 동일한 방식으로 처리하도록 하거나, 주문을 제출하기 전에 송장 승인을 얻도록 할 경우 비즈니스 프로세스 흐름을 사용합니다.        | 비즈니스 프로세스 흐름 디자이너        |
|워크플로     |  워크플로는 사용자 인터페이스 없이 비즈니스 프로세스를 자동화합니다. 디자이너는 워크플로를 사용하여 사용자 상호 작용이 필요 없는 자동화를 시작합니다.       | 워크플로 디자이너        |
|작업    |  작업은 사용자 지정 작업을 비롯한 작업을 워크플로에서 직접 호출할 수 있도록 하는 프로세스 유형입니다.       |  프로세스 디자이너       |
|비즈니스 규칙     | 필드 요구 사항 설정, 필드 숨기기 또는 데이터 유효성 검사와 같은 규칙 또는 권장 사항 논리를 양식에 적용하는 데 사용됩니다. 앱 디자이너는 빠르게 변화하고 일반적으로 사용되는 규칙을 구현하고 유지하는 간단한 인터페이스를 사용합니다.         |  비즈니스 규칙 디자이너       |
|흐름     | 흐름은 앱과 서비스 간에 자동화된 워크플로를 만들어 알림을 수신하고, 파일을 동기화하고, 데이터를 수집하는 등의 클라우드 기반 서비스입니다.        | Power Automate        |

![워크플로, 작업 및 비즈니스 프로세스 흐름 디자이너](media/model-driven-app-overview/designer-mash.png)

추가정보: [모델 기반 앱에서 비즈니스 논리 적용](guide-staff-through-common-tasks-processes.md) 

### <a name="additional-options-for-adding-custom-business-logic"></a>사용자 지정 비즈니스 논리 추가를 위한 추가 옵션
[플러그 인을 사용하여 비즈니스 프로세스 확장](../../developer/common-data-service/plug-ins.md) <br />
[워크플로 확장](../../developer/common-data-service/workflow/workflow-extensions.md)

## <a name="visualizations"></a>시각화
앱이 사용할 수 있는 데이터 시각화 및 보고의 유형을 결정합니다.


|구성 요소  |설명  |디자이너  |
|---------|---------|---------|
|차트     | 보기 또는 양식에 표시하거나 대시보드에 추가할 수 있는 단일 그래픽 시각화입니다.        | 차트 디자이너        |
|대시보드     | 실행 가능한 비즈니스 데이터의 개요를 제공하는 하나 이상의 그래픽 시각화에 대한 팔레트 역할을 합니다.        | 대시보드 디자이너        |
|포함된 Power BI     | 앱에 포함된 Power BI 타일 및 대시보드를 추가합니다. Power BI는 비즈니스 인텔리전스 인사이트를 제공하는 클라우드 기반 서비스입니다.        |  차트 디자이너, 대시보드 디자이너 및 Power BI의 결합       |

![샘플 대시보드](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>고급 모델 기반 앱 제작
솔루션 탐색기는 고급 모델 기반 앱 빌드에 사용되는 포괄적인 도구입니다. 솔루션 탐색기에서 도구의 왼쪽에 있는 탐색 창을 사용하여 모든 앱 구성 요소로 구성된 계층 구조를 탐색할 수 있습니다.

![솔루션 탐색기](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

솔루션 탐색기를 열려면 [!INCLUDE [powerapps](../../includes/powerapps.md)]의 왼쪽 창에서 **모델 기반**을 선택합니다 .

  ![모델 기반 선택](media/model-driven-app-overview/app-type-picker-mod.png)

그 다음 **고급** 탭을 선택합니다.

추가 정보: [고급 앱 제작 및 사용자 지정](advanced-navigation.md)

## <a name="related-topics"></a>관련 항목

[모델 기반 앱 유효성 검사 및 게시](validate-app.md)

[모델 기반 앱 공유](share-model-driven-app.md)
