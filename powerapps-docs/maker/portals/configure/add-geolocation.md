---
title: 포털에서 관리 되는 양식에 지리적 위치 추가 | MicrosoftDocs
description: 지리적 위치를 관리 되는 폼에 추가 하는 지침입니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553558"
---
# <a name="add-geolocation"></a>지리적 위치 추가

*지리적* 위치는 개체의 실제 지리적 위치를 식별 하는 것입니다. 지리적 위치는 위치 지정 시스템의 사용과 밀접 하 게 관련 되어 있지만 지리적 좌표 집합 뿐만 아니라 의미 있는 위치 (예: 주소)를 결정 하는 데 더 중점을 둡니다. 지리적 위치 라는 단어는 특정 위치의 위도 및 경도 좌표를 의미할 수도 있습니다.

기존 위치를 지도에 고정으로 표시 하거나 사용자가 위치를 지정할 수 있는 기능을 제공 하는 지도 컨트롤을 표시 하도록 관리 되는 폼을 구성할 수 있습니다.

![양식의 위치 데이터입니다.](../media/location-data-form.png "양식의 위치 데이터")

양식 또는 주소 줄 필드가 편집 가능 하 고이 필드가 비어 있는 경우 페이지가 로드 되 면 사용자에 게 위치를 공유할지 묻는 메시지가 표시 됩니다. 해당 위치를 공유 하도록 선택 하는 경우 맵은 현재 검색 된 위치를 사용 하 여 업데이트 됩니다. 사용자는 pin을 끌어서 위치를 조정할 수 있습니다. 사용자가 해당 위치를 공유 하지 않도록 선택 하는 경우 제공 된 필드에 위치를 수동으로 지정할 수 있으며, 매핑 서비스를 쿼리하여 위치를 찾고, 위도 및 경도를 업데이트 하 고, 맵의 핀을 적절 하 게 변경 합니다.

## <a name="add-geolocation"></a>지리적 위치 추가
관리 되는 폼에 지리적 위치 기능을 추가 하려면 다음 작업을 완료 해야 합니다.

### <a name="form-customization"></a>양식 사용자 지정
폼 디자이너를 사용 하 여 엔터티 양식을 편집 하 고 다음과 같이 수정 합니다.

1. 새 섹션을 만들고 **Map**과 같은 적절 한 레이블을 제공 합니다. 이 섹션에는 지도가 포함 됩니다.
2. 섹션의 이름을 섹션 **\_map** 으로 설정 하거나 _섹션\_map_로 끝나는 이름 (예: **contoso\_section\_map**)으로 설정 합니다. 이 이름은 양식 엔진이 지도를 렌더링할 시기를 결정 하기 위해이 이름으로 섹션을 검색 하기 때문에 중요 합니다. 
3. 서식이 지정 된 주소를 저장할 새 필드 또는 기존 필드를 추가 하 고 이전 단계에서 만든 **맵** 섹션에 추가 합니다.
4. 새 섹션을 만들고 **위치**와 같은 적절 한 레이블을 제공 합니다. 이 섹션에는 선택한 위치에 대 한 주소 필드가 포함 됩니다.
5. 이전 단계에서 만든 **Location** 섹션에 필요한 주소 필드를 추가 합니다. 
    - 주소 줄
    - 대도시
    - 홍보할
    - 시/도
    - 국가/지역
    - 우편 번호
    - 위도
    - 경도

결과 폼은 다음과 같이 표시 됩니다. 이러한 필드에 대해 다른 표시 이름을 선택할 수 있습니다. 원하는 방식으로 이러한 섹션을 레이아웃 하도록 선택할 수도 있습니다.

![사용자 지정 지리적 위치 형식입니다.](../media/custom-geolocation-form.png "사용자 지정 지리적 위치 형식")

### <a name="site-settings"></a>사이트 설정
관리 되는 폼에서 맵 기능이 있는 지리적 위치에는 매핑 서비스 REST 끝점을 사용 하 여 요청을 완료 하기 위한 구성 설정이 필요 합니다. 다음 사이트 설정은 위치 서비스를 구성 하는 데 사용 됩니다.

|이름|Value|
|---|---|
|Bingmaps/자격 증명|Bing Maps API에 대 한 요청을 인증 하는 고유 키입니다. [Www.bingmapsportal.com](https://www.bingmapsportal.com) 를 방문 하 여 Bing Maps 계정을 만들고 키를 가져옵니다. 필수.|
|Bingmaps/restURL|Bing 지도 REST API에 대 한 URL입니다. 선택 사항 값을 지정 하지 않으면 기본 https://dev.virtualearth.net/REST/v1/Locations 사용 됩니다.|
| |

### <a name="field-configurations"></a>필드 구성
지도 컨트롤에는 다양 한 위치 필드의 Id를 알리기 위해 추가 구성이 필요 하기 때문에 값을 할당 하거나 값을 검색할 수 있습니다. 구성은 관리 되는 양식의 유형에 따라 달라 집니다.

- 엔터티 폼의 경우 [엔터티 형식에 대 한 지리적 위치 구성](entity-forms.md#geolocation-configuration-for-entity-forms)을 참조 하세요.

- Web forms의 경우 [웹 폼에 대 한 지리적 위치 구성](web-form-properties.md#geolocation-configuration-for-web-form)을 참조 하세요.
