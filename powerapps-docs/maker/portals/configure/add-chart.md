---
title: 포털에서 웹 페이지에 차트 추가 | MicrosoftDocs
description: 모델 기반 앱에서 만든 차트를 포털의 웹 페이지에 추가 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cc2e390b988689e9a21317d80aa7d94d2ea9e6d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553880"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>포털의 웹 페이지에 모델 기반 앱에서 만든 차트 추가

[Chart](../liquid/portals-entity-tags.md#chart)라는 액체 태그를 사용 하 여 웹 페이지에 차트를 추가할 수 있습니다. 웹 페이지의 **복사** 필드 또는 [웹 템플릿의](../liquid/store-content-web-templates.md) **원본** 필드에 차트 액체 태그를 추가할 수 있습니다.
 
예를 들어 {% chart id: EE3C733D-5693-DE11-3CC-00155DA3B01E%}

![차트 예제](../media/dynamics365-chart-example.png "차트 예제")

뷰 (저장 된 쿼리)의 ID를 지정 하 여 쿼리를 필터링 할 수도 있습니다. 예:

<!—Leads by Source – Open Leads -->

{% chart id: "EE3C733D-5693-DE11 D4-00155DA3B01E" viewid: "00000000-0000-0000-000010001006"%}

## <a name="get-the-id-of-a-chart"></a>차트의 ID 가져오기

1.  대상 엔터티로 이동 합니다 (예: **판매** > **잠재 고객**).
2.  **차트** 영역을 확장 합니다.
3.  원하는 차트를 선택 합니다.
4.  **기타 명령**을 선택 하 고 **차트 내보내기**를 선택 합니다.

    ![차트 내보내기](../media/export-dynamics365-chart.png "차트 내보내기")

5. 내보낸 차트의 XML 파일을 텍스트 편집기에서 엽니다.
6. \<visualizationid\> 태그의 값을 복사 합니다.

    ![차트에 대 한 chartid 가져오기](../media/dynamics365-chart-chartid.png "차트의 차트 ID 가져오기")

7. Visualizationid 값을 차트 ID 매개 변수에 대 한 액체 차트 태그 선언에 붙여넣습니다. 예를 들면 다음과 같습니다.

    {% chart id: EE3C733D-5693-DE11-15DA-3B01E%}.

## <a name="get-the-id-of-a-view"></a>뷰의 ID 가져오기

보기 편집기를 열어 액체 차트 태그에 사용할 뷰 ID를 가져와야 합니다.
 
1.  대상 엔터티로 이동 합니다 (예: **판매** > **잠재 고객**).
2.  보기 드롭다운 헤더에서 원하는 보기를 선택 합니다.
3.  도구 모음에서 **보기** 를 선택 합니다. 보기 창이 열립니다.

    ![보기 편집기에서 잠재 고객 보기](../media/dynamics365-chart-view.png "보기 편집기에서 잠재 고객 보기")

4. 보기 창의 URL에서 **id** 값을 복사 합니다.

    ![뷰 편집기에서 뷰 id 가져오기](../media/dynamics365-chart-viewid.png "뷰 편집기에서 보기 ID 가져오기")

5. 이 ID를 viewid 매개 변수에 대 한 액체 차트 태그 선언에 붙여넣습니다. 예를 들면 다음과 같습니다.

    <!—Leads by Source – Open Leads -->

    {% chart id: "EE3C733D-5693-DE11 D4-00155DA3B01E" viewid: "00000000-0000-0000-000010001006"%}

## <a name="entity-permission-requirement"></a>엔터티 권한 요구 사항

차트에서 쿼리 되는 대상 엔터티에 대해 읽기 권한이 어설션 되었습니다. 익명 또는 인증 된 사용자가 차트를 볼 수 있도록 하려면 적절 한 [엔터티 권한](assign-entity-permissions.md) 레코드가 만들어지고 적용 가능한 [웹 역할](create-web-roles.md)에 할당 되었는지 확인 해야 합니다. 
 
권한이 부여 되지 않은 경우 사용자에 게 액세스 거부 메시지가 표시 됩니다.

## <a name="unsupported-charts-and-chart-types"></a>지원 되지 않는 차트 및 차트 종류

다음 차트 종류는 현재 포털에서 지원 되지 않습니다.
- 차트
- 태그가

다음 표에는 포털에서 현재 지원 되지 않는 차트가 나열 되어 있습니다.

| 차트 이름                              | 차트 ID                             | 엔터티 형식      |
|-----------------------------------------|--------------------------------------|------------------|
| 소유자 태그 차트 별 계정           | be178262-6142-4b41-85b7-4ccedc62cfd9 | 계정일          |
| 소유자-태그 차트 별 활동         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| 우선 순위 별 활동-도넛형 차트 | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| 거래처 별 연락처                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | 상대의          |
| 국가별로 연락처                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | 상대의          |
| 기본 연락 방법 별 연락처    | 751b7456-308e-4568-a3a9-47135aae833a | 상대의          |
| 목표 진행률 (개수)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | 목표             |
| 목표 진행률 (Money)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | 목표             |
| 오늘 대상과 실제 데이터 비교 (개수)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | 목표             |
| 오늘 대상과 실제 데이터 비교 (Money)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | 목표             |
| 계정에의 한 사례                        | 38872e4f-ac99-e511-80da-00155dc1b253 | 인시던트         |
| 우선 순위별로 사례                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | 인시던트         |
| 제품별 사례                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | 인시던트         |
| 이 달에 소유자가 만료 하는 문서   | 47d696ad-7c3b-e511-80d1-00155db10d2b | 기술 문서 |
| 소유자별                                | 330068fd-833b-e511-80d1-00155db10d2b | 기술 문서 |
| 제목별                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | 기술 문서 | 
| | |
