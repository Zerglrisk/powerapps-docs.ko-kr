---
title: 포털에서 웹 템플릿을 사용하여 소스 콘텐츠 저장 | MicrosoftDocs
description: 포털에서 웹 템플릿을 사용하여 콘텐츠를 저장하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: d75a8afd6b269078a4be3c0c7cc9b370cb9fe9f5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866450"
---
# <a name="store-source-content-by-using-web-templates"></a>웹 템플릿을 이용하여 소스 콘텐츠 저장

웹 템플릿은 Power Apps 포털에 포함된 Power Apps 엔터티(adx\_webtemplate)로서, 템플릿 소스 콘텐츠를 저장하기 위해 사용됩니다. 웹 템플릿은 일반적으로 동적 콘텐츠 렌더링을 위한 유동을 포함할 것이며, 유동 템플릿을 Power Apps 포털 시스템의 나머지와 통합하는 데 사용되는 중심 엔터티입니다.

웹 템플릿은 다른 콘텐츠에 포함되거나 템플릿 태그를 이용하여 다른 템플릿과 통합될 수 있으며, 이러한 태그에서는 **이름** 특성에 의해 지칭됩니다. 웹 템플릿을 이용하여 완전 맞춤 페이지 템플릿을 만들거나, 사용자의 포털 웹사이트를 위한 맞춤 머리글 및 바닥글을 생성할 수 있습니다.

## <a name="web-template-attributes"></a>웹 템플릿 특성

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   이름    |                                                                         템플릿의 이름. 다른 콘텐츠에 포함되어 있거나 다른 템플릿에 의해 연장될 때 이 템플릿을 지칭하기 위해 사용됩니다.                                                                         |
|  원본   |                                  템플릿의 소스 콘텐츠. Power Apps에서는 이 필드에 구문 강조 기능이 있는 소스 코드 편집기와 기타 코드 편집 기능이 제공됩니다.                                  |
| MIME 형식 | 옵션으로서 템플릿의 콘텐츠를 위한 MIME 형식을 제공합니다. 아무 것도 제공되지 않으면 text/html 형식으로 간주됩니다. 이 값은 템플릿이 페이지 템플릿과 연계되어 해당 템플릿을 위한 모든 콘텐츠의 렌더링을 통제하는 경우에만 사용될 것입니다. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>페이지 템플릿으로서의 웹 템플릿

웹 템플릿을 페이지 템플릿과 함께 사용하여 Power Apps 포털 콘텐츠 관리 시스템을 위한 새 템플릿을 만들 수 있습니다. .NET 코드를 쓰거나 포털 응용 프로그램을 재배치할 필요 없이 온전히 Power Apps 내에서 수행할 수 있습니다.

웹 템플릿에 근거하여 새 페이지 템플릿을 만들려면 새 페이지 템플릿 레코드를 생성할 때 웹 템플릿의 **형식**을 선택하십시오. 이어서 **웹 템플릿**을 선택합니다.

옵션 **웹사이트 머리글 및 바닥글 사용**(기본적으로 체크되어 있음)에 주목하십시오. 이것이 체크되어 있으면 웹 템플릿이 글로벌 웹 사이트 머리글 및 바닥글 사이의 모든 페이지 콘텐츠의 렌더링을 통제할 것입니다. 이 옵션을 체크 해제하면 사용자가 HTML을 렌더링하는 경우에 웹 템플릿이 전체 반응을 렌더링해야 하며, 이는 문서 형식에서 루트 &lt;html&gt; 태그까지의 모든 것과 그 사이의 모든 것을 의미합니다.

가장 일반적인 웹 템플릿 사용 경우는 HTML을 렌더링하기 위한 것이지만, 전체 반응을 렌더링하는 경우에는(**웹사이트 머리글 및 바닥글 사용**을 선택 해제함으로써) 선택하는 텍스트 기반 형식을 렌더링할 수 있는 옵션이 생깁니다. 이것이 웹 템플릿의 **MIME 유형** 특성이 타당해지는 경우입니다. 웹사이트 머리글 및 바닥글을 사용하지 않는 페이지 템플릿을 렌더링할 때 HTTP 응답 콘텐츠 형식 머리글이 관련 웹 템플릿의 MIME 형식에 설정될 것입니다. (형식이 제공되지 않은 경우 text/html이 사용됩니다.) This gives you a wide variety of options for rendering non-HTML content by using Liquid. 일반적인 사용 사례는 MIME 형의 application/rss+xml을 설정함으로써 [RSS](https://en.wikipedia.org/wiki/RSS) 피드를 렌더링하기 위한 것입니다.  

## <a name="web-templates-as-website-headers-and-footers"></a>웹사이트 머리글 및 바닥글로서의 웹 템플릿

Power Apps 포털이 사용하는 글로벌 머리글 및 바닥글을 회피하기 위해 웹 템플릿을 사용할 수도 있습니다. 그렇게 하려면 웹사이트의 **머리글 템플릿** 또는 **바닥글 템플릿** 필드를 원하는 웹 템플릿으로 설정하십시오. **웹 사이트 머리글**을 다시 정의하는 경우 일반적으로 선택된 템플릿이 기본 머리글 템플릿으로 처리되는 사이트 인터페이스 요소를 위한 기본 탐색, 로그인/로그아웃 링크, 검색 인터페이스 등을 렌더링합니다.

## <a name="built-in-web-templates"></a>내장 웹 템플릿

Power Apps 포털 내에서 사용할 수 있는 일련의 선제작 유동 템플릿이 있습니다. 이를 사용하려면 아래 목록을 참조하여 이름으로 포함해야 합니다.

| 이름                        | 설명                                                                                                                                                                                                                             | 코드                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 광고                          | 이 템플릿은 이름별 광고 또는 광고 배치의 무작위 광고를 렌더링합니다.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| 블로그                       | 이 템플릿은 목록 그룹의 최근 블로그 게시물을 렌더링합니다.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| 현재 위치                 | 이 템플릿은 현재 페이지로부터 상위 페이지의 링크를 홈 페이지에 렌더링합니다.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| 하위 링크 목록 그룹       | 이 템플릿은 목록 그룹에 있는 현재 페이지의 하위 페이지의 링크를 렌더링합니다.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| 이벤트: 박두            | 이 템플릿은 지금과 지금으로부터 60일 사이에 발생하는 이벤트의 링크를 렌더링합니다.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| 포럼                      | 이 템플릿은 웹 사이트의 포럼 목록을 해당 수의 스레드 및 게시물과 함께 렌더링합니다.                                                                                                                                 | `{% include 'forums' %}`                                       |
| 1열 레이아웃             | 이 템플릿은 이동 경로, 페이지 제목 및 페이지 복사 콘텐츠를 포함하는 단일 열 레이아웃을 렌더링합니다.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| 레이아웃 2열 넓은 왼쪽   | 이 템플릿은 2열 레이아웃을 렌더링합니다. 왼쪽 열이 오른쪽 보다 더 넓습니다. 이동 경로, 페이지 제목은 페이지 상단에 포함되어 있고 페이지 복사 콘텐츠는 왼쪽 열에 위치합니다.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| 레이아웃 2열 넓은 오른쪽  | 이 템플릿은 2열 레이아웃을 렌더링합니다. 오른쪽 열이 왼쪽 보다 더 넓습니다. 이동 경로, 페이지 제목은 페이지 상단에 포함되어 있고 페이지 복사 콘텐츠는 오른쪽 열에 위치합니다.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| 레이아웃 3열 넓은 중간 | 이 템플릿은 3열 레이아웃을 렌더링합니다. 중간 열이 왼쪽과 오른쪽 보다 더 넓습니다. 이 레이아웃은 이동 경로와 페이지 제목을 페이지 상단에 포함하고 페이지 복사 콘텐츠는 중간 열에 위치합니다.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| 페이지 복사                   | 이 템플릿은 내장된 유동 지원과 함께 편집 가능 페이지 복사 콘텐츠 HTML을 렌더링합니다.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| 페이지 머리글                 | 이 템플릿은 페이지 제목을 렌더링합니다.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| 폴링                        | 이 템플릿은 이름별 폴링 또는 폴링 배치의 무작위 폴링을 렌더링합니다.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| 검색                      | 이 템플릿은 단일 텍스트 입력과 검색 버튼을 가진 기본 검색 양식을 렌더링합니다.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| 측면 탐색             | 이 템플릿은 수직 트리 보기 스타일 탐색을 렌더링합니다. 이 템플릿은 첫 번째 레벨(또는 지정된 깊이 오프셋)로 돌아가는 상위 페이지 링크, 현재 페이지의 동위 페이지 링크 및 현재 페이지의 하위 페이지 링크를 갖습니다. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| 조각                     | 이 템플릿은 편집 가능한 이름별 HTML 콘텐츠 조각을 렌더링합니다.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| 위쪽 탐색              | 이 템플릿은 기본 탐색 웹 링크 세트를 위한 드롭다운 메뉴와 함께 편집 가능한 탐색 바를 렌더링합니다.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| 웹 링크 목록 그룹          | 이 템플릿은 웹 링크 설정에 대한 링크 목록 그룹을 렌더링합니다.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>참조

[유동 연산자의 이해](liquid-operators.md)  
[유동 유형](liquid-types.md)  
[조건부](liquid-conditional-operators.md)  
[유동 개체](liquid-objects.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md)  
