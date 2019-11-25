---
title: 포털의 관리 양식에 지리적 위치 추가 | MicrosoftDocs
description: 관리 양식에 지리적 위치를 추가하기 위한 지침.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a3c583658a5593d8e6c5f6c139a5c967e9581626
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760700"
---
# <a name="add-geolocation"></a>지리적 위치 추가

*지리적 위치*는 객체의 실제 지리적 위치의 ID입니다. 지리적 위치는 포지셔닝 시스템 사용과 밀접하게 관련 되어 있지만 단순한 지리 좌표 집합 보다는 의미 있는 위치(예: 번지)의 표시를 더 강조합니다. 또한 지리적 위치란 단어는 특정 위치의 위도 및 경도 좌표를 뜻하기도 합니다.

관리 양식은 기존 위치를 지도에 핀으로 표시하거나 또는 사용자가 위치를 지정할 수 있는 기능을 제공하기 위해 맵 컨트롤 표시하도록 구성될 수 있습니다.

![양식의 위치 데이터.](../media/location-data-form.png "양식의 위치 데이터")

양식 또는 주소 행 필드를 편집할 수 있는데 이 필드가 비어 있으면, 페이지가 로드될 때 자신의 위치를 공유하고 싶은지를 사용자에게 묻는 메시지가 표시됩니다. 위치를 공유하도록 선택하면 지도는 현재 검색된 위치로 업데이트됩니다. 사용자는 핀을 드래그하여 위치를 구체화할 수 있습니다. 사용자가 자신의 위치를 공유하지 않기로 선택한 경우, 제공된 필드에 위치를 수동으로 지정할 수 있으며 매핑 서비스가 대기하고 있다가 위치를 찾아 위도 및 경도를 업데이트할 뿐만 아니라 지도상의 핀 위치를 적절히 변경합니다.

## <a name="add-geolocation"></a>지리적 위치 추가
관리 양식에 지리적 위치 기능을 추가하려면 다음 작업을 완료해야 합니다.

### <a name="form-customization"></a>양식 사용자 지정
양식 디자이너를 사용하여 엔터티 양식을 편집하고 다음을 수정하십시오.

1. 새 섹션을 만들고 적절한 레이블, 예컨대, **지도**를 제공합니다. 이 섹션에는 지도가 포함됩니다.
2. 섹션의 이름을 **section\_map**으로 또는 _section\_map_으로 끝나는 이름, 예컨대 **contoso\_section\_map**으로 설정합니다. 양식 엔진이 지도를 렌더링할 시기를 결정하기 위해 이름을 가진 섹션을 찾기 때문에 이 이름이 중요합니다. 
3. 포맷된 주소를 저장할 새 필드 또는 기존 필드를 추가하고 그것을 이전 단계에서 생성된 **지도** 섹션에 추가합니다.
4. 새 섹션을 만들고 적절한 표식, 예컨대, **위치**를 제공합니다. 이 섹션에는 선택된 위치의 주소 필드가 포함됩니다.
5. 이전 단계에서 만든 **위치** 섹션에 요구되는 주소 필드를 추가합니다. 
    - 주소란
    - 구/군/시
    - 군
    - 시/도
    - 국가/지역
    - 우편 번호
    - 위도
    - 경도

생성 양식은 다음과 비슷합니다. 이러한 필드에 대해 다른 표시 이름을 선택할 수 있습니다. 또한 선호하는 방식으로 이러한 섹션들을 레이아웃할 수 있습니다.

![사용자 지정 지리적 위치 양식.](../media/custom-geolocation-form.png "사용자 지정 지리적 위치 양식")

### <a name="site-settings"></a>사이트 설정
관리 양식에서 지도 기능을 가진 지리적 위치는 매핑 서비스 REST 끝점으로 요청을 완료하기 위해 구성 설정을 요구합니다. 다음 사이트 설정은 위치 서비스를 구성하는 데 사용됩니다.

|이름|값|
|---|---|
|Bing 지도/자격 증명|Bing 지도 API에 요청을 인증하기 위한 고유 키. Bing 지도 계정을 만들고 키를 받으려면 [www.bingmapsportal.com](https://www.bingmapsportal.com)을 방문하십시오. 필수 특성:|
|Bing 지도/REST URL|Bing 지도 REST API의 URL. 선택 사항. 값을 지정하지 않으면 기본 https://dev.virtualearth.net/REST/v1/Locations가 사용됩니다.|
| |

### <a name="field-configurations"></a>필드 구성
지도 컨트롤은 값을 할당하거나 값을 검색하기 위해 다양한 위치 필드의 ID가 무엇인지를 알려주는 추가 구성을 요구합니다. 구성은 관리 양식의 타입에 의존합니다.

- 엔터티 양식의 경우, [엔터티 양식을 위한 지리적 위치 구성](entity-forms.md#geolocation-configuration-for-entity-forms)을 참조하십시오.

- 웹 양식의 경우, [웹 양식을 위한 지리적 위치 구성](web-form-properties.md#geolocation-configuration-for-web-form)을 참조하십시오.
