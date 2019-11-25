---
title: 포털의 웹 페이지에 차트 추가 | MicrosoftDocs
description: 모델 기반 앱에서 생성된 차트를 포털의 웹 페이지에 추가하기 위한 지침입니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760701"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>모델 기반 앱에서 생성된 차트를 포털의 웹 페이지에 추가

[차트](../liquid/portals-entity-tags.md#chart)라는 유동 태그를 사용하여 웹 페이지에 차트를 추가합니다. 웹 페이지의 **복사** 필드 또는 [웹 템플릿](../liquid/store-content-web-templates.md)의 **원본** 필드에 차트 유동 태그를 추가할 수 있습니다.
 
{% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}을 예로 들 수 있습니다.

![차트 예](../media/dynamics365-chart-example.png "차트 예")

쿼리를 필터링 할 보기(저장된 쿼리)의 ID를 지정할 수도 있습니다. 예:

<!—Leads by Source – Open Leads -->

{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="get-the-id-of-a-chart"></a>차트의 ID를 가져옵니다.

1.  대상 엔터티로 이동합니다(예: **영업** > **잠재 고객**).
2.  **차트** 영역을 확장합니다.
3.  원하는 차트를 선택합니다.
4.  **추가 명령**을 선택한 다음 **차트 내보내기**를 선택합니다.

    ![차트 내보내기](../media/export-dynamics365-chart.png "차트 내보내기")

5. 내보낸 차트의 XML 파일을 텍스트 편집기에서 엽니다.
6. Copy the value of the \<visualizationid\> 태그의 값을 복사합니다.

    ![차트에 대한 chartid 가져오기](../media/dynamics365-chart-chartid.png "차트의 ID 가져오기")

7. visualizationid 값을 다음과 같이 차트 ID 매개 변수에 대한 유동 차트 태그 선언에 붙여넣습니다.

    {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}

## <a name="get-the-id-of-a-view"></a>보기의 ID를 가져옵니다.

유동 차트 태그와 함께 사용할 보기 ID를 가져오려면 보기 편집기를 열어야 합니다.
 
1.  대상 엔터티로 이동합니다(예: **영업** > **잠재 고객**).
2.  보기 드롭다운 헤더에서 원하는 보기를 선택합니다.
3.  도구 모음에서 **보기**를 선택합니다. 보기 창이 열립니다.

    ![보기 편집기에서 잠재 고객 보기](../media/dynamics365-chart-view.png "보기 편집기에서 잠재 고객 보기")

4. 보기 창의 URL에서 **id** 값을 복사합니다.

    ![보기 편집기에서 보기 ID 가져오기](../media/dynamics365-chart-viewid.png "보기 편집기에서 보기 ID 가져오기")

5. 이 ID를 다음과 같이 viewid 매개 변수에 대한 유동 차트 태그 선언에 붙여넣습니다.

    <!—Leads by Source – Open Leads -->

    {% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="entity-permission-requirement"></a>엔터티 권한 요구 사항

차트에서 쿼리되는 대상 엔터티에 대해 읽기 권한이 어설션됩니다. 익명 또는 인증된 사용자가 차트를 볼 수 있도록 하려면 적절한 [엔터티 권한](assign-entity-permissions.md) 레코드가 만들어지고 적용할 수 있는 [웹 역할](create-web-roles.md)에 할당되었는지 확인해야 합니다. 
 
권한이 부여되지 않으면 사용자에게 액세스가 거부되었습니다 메시지가 표시됩니다.

## <a name="unsupported-charts-and-chart-types"></a>지원되지 않는 차트 및 차트 유형

다음 차트 유형은 현재 포털에서 지원되지 않습니다.
- 도넛형
- 태그

다음 테이블에는 현재 포털에서 지원되지 않는 차트를 나열합니다.

| 차트 이름                              | 차트 ID                             | 엔터티 유형      |
|-----------------------------------------|--------------------------------------|------------------|
| 담당자별 거래처 - 태그 차트           | be178262-6142-4b41-85b7-4ccedc62cfd9 | 거래처          |
| 담당자별 활동 - 태그 차트         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| 우선 순위별 활동 - 도넛형 차트 | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| 거래처별 연락처                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | 연락처          |
| 국가별 연락처                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | 연락처          |
| 선호 연락 방법별 연락처    | 751b7456-308e-4568-a3a9-47135aae833a | 연락처          |
| 목표 진행 상황(개수)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| 목표 진행 상황(금액)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| 금일 대상 및 실제 비교(개수)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| 금일 대상 및 실제 비교(금액)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| 계정별 서비스 케이스                        | 38872e4f-ac99-e511-80da-00155dc1b253 | incident         |
| 우선 순위별 서비스 케이스                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | incident         |
| 제품별 서비스 케이스                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | incident         |
| 담당자별 이 달에 만료되는 문서   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| 담당자별                                | 330068fd-833b-e511-80d1-00155db10d2b | knowledgearticle |
| 제목별                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
