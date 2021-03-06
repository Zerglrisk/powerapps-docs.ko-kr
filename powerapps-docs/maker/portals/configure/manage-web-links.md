---
title: 웹 링크 관리 | MicrosoftDocs
description: 웹 링크 관리 지침.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: d8e2421545247f72b5b164e08b4ac210466048c1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866846"
---
# <a name="manage-web-links"></a>웹 링크 관리

웹 링크는 어느 URL에든 연결될 수 있으며 또는 같은 웹 사이트 내의 다른 웹 페이지에 링크될 수 있습니다. 웹 링크가 웹 페이지에 링크될 때 웹 페이지의 보안 및 게시 상태도 웹 링크에 적용됩니다. 웹 링크는 항상 웹 링크 세트에 속합니다. 웹 링크 세트는 기본 탐색 또는 바닥글 링크 그룹 같은 링크 그룹입니다. 웹 링크 세트는 내부(사이트 맵에서의 배치와 무관) 및 외부 링크가 같이 묶어져 정렬될 수 있게 합니다.

## <a name="manage-web-links-in-power-apps-portals"></a>Power Apps 포털에서 웹 링크 관리

Common Data Service 환경에 포털 맞춤화를 가져오면 웹 링크 집합에서 웹 링크를 관리할 수 있습니다.

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 링크 집합**으로 이동합니다.

3. 새 웹 링크 집합을 만들려면 **새로 만들기**를 선택합니다.

4. 기존 웹 링크 집합을 편집하려면 웹 링크 집합 이름을 선택합니다.

5. 필드에 적절한 값을 입력합니다.

6. 새 웹 링크 집합을 만드는 경우 **저장**을 선택하여 웹 링크를 추가할 수 있도록 레코드를 저장합니다.

7. **링크** 탭으로 이동합니다.

8. 새 웹 링크를 만들려면 **새 웹 링크**를 선택합니다.

    ![웹 링크 추가](../media/add-web-link.png "웹 링크 추가")

9. 기존 웹 링크를 편집하려면 웹 링크 이름을 선택합니다.

9. 필드에 적절한 값을 입력합니다.

6. 변경 내용을 저장합니다.

## <a name="web-link-set-attributes-and-relationships"></a>웹 링크 세트 특성 및 관계

아래 표는 포털에서 사용하는 여러 표준 웹 링크 세트 속성들을 설명합니다. 많은 콘텐츠/표시 지향 속성을 렌더링하는 방식이 사용된 페이지 템플릿에 의해 통제됨을 아는 것이 중요합니다.

| 이름    | 설명                                                                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 이름    | 웹 링크 세트의 설명적 이름. 이 값은 일반적으로 페이지 템플릿에서 기본 탐색 같이 세트 배치를 설명합니다. 이 필드는 필수 필드입니다.                   |
| 웹 사이트 | 엔터티가 속한 웹 사이트입니다. 이 필드는 필수 필드입니다.                                                                                                                             |
| 직함   | 웹 링크 세트의 옵션적 제목. 이 값은 페이지 템플릿의 일부인 경우 포털에 사용될 수 있습니다. 우리 파트너 같은 것일 수 있으며 사이드 바에 표시될 수 있습니다.    |
| 복사    | 웹 링크 세트의 옵션적 설명. 이 값은 페이지 템플릿의 일부인 경우 포털에 사용될 수 있습니다. 우리 파트너 같은 것을 추가 묘사할 수 있으며 사이드 바에 표시될 수 있습니다. |
||

## <a name="web-link-attributes-and-relationships"></a>웹 링크 특성 및 관계

아래 표는 포털이 사용하는 많은 표준 웹 링크 속성들을 설명합니다. 많은 콘텐츠/표시 지향 속성을 렌더링하는 방식이 사용된 페이지 템플릿에 의해 통제됨을 아는 것이 중요합니다.


|           이름           |                                                                                                               설명                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           이름           |                                                          웹 링크의 제목. 이 값은 대부분의 템플릿에서 웹 링크 제목으로 사용됩니다. 이 필드는 필수 필드입니다.                                                           |
|       웹 링크 세트       |                                                                                  엔터티가 속한 웹 링크 세트. 이 필드는 필수 필드입니다.                                                                                  |
|     상위 웹 링크      |                                      다단계 웹 링크 세트에서 엔터티의 상위 웹 링크. 상위 웹 링크가 지정되지 않은 경우, 엔터티는 웹 링크 세트의 최상위/루트 레벨에 있습니다.                                      |
|           페이지           |                                                                                          같은 웹 사이트에 링크되는 옵션적 웹 페이지.                                                                                          |
|        외부 URL      |                                                                                링크될 URL 옵션. 이 값은 적절한 형식의 임의의 URL일 수 있습니다.                                                                                |
|       설명        |                                                              웹 링크의 옵션적 요약. 이 값은 페이지 템플릿의 일부인 경우 포털에 사용될 수 있습니다.                                                              |
|     게시 상태     | 웹 링크의 현재 게시 워크플로 상태, 웹 링크가 사이트에서 보이는지 여부를 지시할 수 있습니다. 이 기능은 콘텐츠의 게시/초안에 대한 제어를 제공하는 데 가장 일반적으로 사용됩니다. 이 필드는 필수 필드입니다. |
|    링크를 따르는 로봇    |                                                           검색 인덱서가 링크의 콘텐츠를 따라 색인해야 하는지의 여부를 표시합니다. 이 필드는 필수 필드입니다.                                                            |
|      표시 순서       |                                                  웹 링크가 같은 웹 링크 세트 내의 다른 웹 링크와의 관계에서 배치될 순서를 표시하는 정수 값.                                                  |
| 페이지 하위 링크 표시 |  다단계 웹 링크 세트를 지원하는 템플릿에서 포털 사이트 맵 공급자를 사용하여 이 엔터티를 위한 하위 링크를 생성합니다. 이 옵션은 외부 URL이 아닌 내부 페이지를 참조하는 웹 링크의 경우에만 유효합니다.  |
|    새 창에서 열기    |                                                                            링크를 선택했을 때 링크가 새 브라우저 창에 로드될 것인지 여부를 표시합니다.                                                                             |
| 페이지 유효성 검사 사용 안 함  |                                                                       링크된 웹 페이지의 보안이 웹 링크에도 적용될 것인지의 여부를 표시합니다.                                                                       |
|        이미지 URL         |                                                   이미지 URL 옵션. 링크된 이미지는 페이지 템플릿의 일부인 경우 포털에 사용될 수 있습니다; 예컨대 아이콘으로.                                                   |
|       이미지 높이       |                                                                                      이미지 URL 속성으로부터의 이미지를 위한 높이 옵션.                                                                                      |
|       이미지 너비        |                                                                                      이미지 URL 속성으로부터의 이미지를 위한 너비 옵션.                                                                                       |
|      이미지 대체 텍스트      |                                                                                   이미지 URL 속성으로부터의 이미지를 위한 설명 옵션.                                                                                    |
|    이미지만 표시    |                                                   템플릿이 이미지와 링크 이름을 같이 렝더링하지 않고 이 웹 링크를 위한 이미지 링크만 렌더링해야 함을 표시합니다.                                                    |
|                          |                                                                                                                                                                                                                                         |

> [!Note]
> - 웹 링크가 웹 페이지에 링크될 때 웹 페이지의 보안 및 게시 상태도 웹 링크에 적용됩니다. 이 검증은 페이지 검증 비활성화 옵션으로 비활성화할 수 있습니다. 
>   - 콘텐츠 관리 권한이 있는 사용자는 미리 보기 모드를 사용하여 게시되지 않은 콘텐츠를 미리 볼 수 있습니다.

### <a name="see-also"></a>참조

[콘텐츠 코드 조각을 사용하여 콘텐츠 사용자 지정](customize-content-snippets.md)
