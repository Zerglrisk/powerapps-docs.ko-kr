---
title: 포털에서 웹 템플릿을 사용 하 여 원본 콘텐츠 저장 | MicrosoftDocs
description: 포털에서 웹 템플릿을 사용 하 여 콘텐츠를 저장 하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2abdf23376cfbcc0b591afe2efb1699144fbef8f
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974532"
---
# <a name="store-source-content-by-using-web-templates"></a>웹 템플릿을 사용 하 여 원본 콘텐츠 저장

웹 템플릿은 PowerApps 포털에 포함 된 PowerApps 엔터티 (adx\_webtemplate)로, 템플릿 원본 콘텐츠를 저장 하는 데 사용 됩니다. 웹 템플릿은 일반적으로 동적 콘텐츠 렌더링을 위한 액체를 포함 하 고 있으며, 다른 PowerApps 포털 시스템에 액체 템플릿을 통합 하는 데 사용 되는 중앙 엔터티입니다.

웹 템플릿은 다른 콘텐츠에 포함 되거나 템플릿 태그를 사용 하 여 다른 템플릿과 결합 될 수 있으며 해당 **이름** 특성으로 이러한 태그에서 참조 됩니다. 또한 전체 사용자 지정 페이지 템플릿을 만들거나 포털 웹 사이트에 대 한 사용자 지정 머리글 및 바닥글을 만드는 데 사용할 수 있습니다.

## <a name="web-template-attributes"></a>웹 템플릿 특성

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   이름    |                                                                         템플릿의 이름입니다. 다른 콘텐츠에 포함 되거나 다른 템플릿으로 확장 될 때이 템플릿을 참조 하는 데 사용 됩니다.                                                                         |
|  원본   |                                  템플릿의 원본 내용입니다. PowerApps에서 구문 강조 표시 및 기타 코드 편집 기능이 포함 된 소스 코드 편집기가이 필드에 제공 됩니다.                                  |
| MIME 형식 | 필요에 따라 템플릿의 내용에 대 한 MIME 형식을 제공 합니다. 제공 된 항목이 없으면 텍스트/html 형식이 가정 됩니다. 이 값은 템플릿이 페이지 템플릿과 연결 되어 있고 해당 템플릿에 대 한 모든 콘텐츠의 렌더링을 제어 하는 경우에만 사용 됩니다. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>웹 템플릿 (페이지 템플릿)

웹 템플릿은 페이지 템플릿과 함께 사용 하 여 PowerApps 포털 콘텐츠 관리 시스템에 대 한 새 템플릿을 만들 수 있습니다. .NET 코드를 작성 하거나 포털 응용 프로그램을 다시 배포할 필요 없이 PowerApps 내에서 전체 작업을 수행할 수 있습니다.

웹 템플릿을 기반으로 새 페이지 템플릿을 만들려면 새 페이지 템플릿 레코드를 만들 때 웹 템플릿 **유형을** 선택 합니다. 그런 다음 **웹 템플릿을**선택 합니다.

옵션은 **웹 사이트 머리글 및 바닥글 사용** (기본적으로 선택 됨)을 참조 하세요. 이 확인란을 선택 하면 웹 템플릿이 전역 웹 사이트 머리글과 바닥글 사이에 있는 모든 페이지 내용의 렌더링을 제어 합니다. 이 옵션을 선택 하지 않으면 HTML을 렌더링 하는 경우 웹 템플릿이 전체 응답을 렌더링 해야 합니다 .이는 doctype부터 루트 &lt;html&gt; 태그, 그 사이에 있는 모든 항목을 의미 합니다.

웹 템플릿에 대 한 가장 일반적인 사용 사례는 HTML을 렌더링 하 고 웹 **사이트 머리글 및 바닥글 사용**을 선택 취소 하 여 전체 응답을 렌더링 하면 선택한 텍스트 기반 형식을 렌더링 하는 옵션을 제공 합니다. 웹 템플릿의 **MIME 형식** 특성이 관련 됩니다. 웹 사이트 머리글 및 바닥글을 사용 하지 않는 페이지 템플릿이 렌더링 되는 경우 HTTP 응답 콘텐츠 형식 헤더는 연결 된 웹 템플릿의 MIME 형식으로 설정 됩니다. (MIME 형식을 제공 하지 않으면 텍스트/html이 사용 됩니다.) 이는 액체를 사용 하 여 비 HTML 콘텐츠를 렌더링 하는 다양 한 옵션을 제공 합니다. 일반적인 사용 사례는 응용 프로그램/rss + xml의 MIME 형식을 설정 하 여 [RSS](http://en.wikipedia.org/wiki/RSS) 피드를 렌더링 하는 것입니다.  

## <a name="web-templates-as-website-headers-and-footers"></a>웹 사이트 머리글 및 바닥글로 웹 템플릿

웹 템플릿을 사용 하 여 PowerApps 포털에서 사용 하는 전역 머리글 및 바닥글을 재정의할 수도 있습니다. 이렇게 하려면 웹 사이트의 **머리글 템플릿** 또는 **바닥글 템플릿** 필드를 선택한 웹 템플릿으로 설정 합니다. **웹 사이트 헤더**를 재정의 하는 경우 선택한 템플릿은 기본적으로 일반적으로 처리 되는 사이트 인터페이스 요소에 대해 기본 탐색, 로그인/로그 아웃 링크, 검색 인터페이스 등을 렌더링 하는 역할을 담당 합니다. 헤더 템플릿.

## <a name="built-in-web-templates"></a>기본 제공 웹 템플릿

PowerApps 포털 내에서 사용할 수 있는 미리 만들어져 있는 액체 템플릿 집합이 있습니다. 이러한 파일을 사용 하려면 아래 목록을 참조로 사용 하 여 이름을 기준으로 포함 해야 합니다.

| 이름                        | 설명                                                                                                                                                                                                                             | Code                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 임시                          | 이 템플릿은 ad 배치에서 이름 또는 임의 광고를 기준으로 광고를 렌더링 합니다.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| 블로그                       | 이 템플릿은 최근 블로그 게시물을 목록 그룹에 렌더링 합니다.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| 이동 경로                 | 이 템플릿은 상위 페이지의 링크를 현재 페이지의 홈 페이지로 다시 렌더링 합니다.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| 자식 링크 목록 그룹       | 이 템플릿은 목록 그룹에 있는 현재 페이지의 자식 페이지에 대 한 링크를 렌더링 합니다.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| 이벤트: 예정            | 이 템플릿은 현재부터 60 일 사이에 발생 하는 이벤트에 대 한 링크를 렌더링 합니다.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| 포럼                      | 이 템플릿은 웹 사이트의 포럼 목록을 해당 스레드 및 게시물의 수와 함께 렌더링 합니다.                                                                                                                                 | `{% include 'forums' %}`                                       |
| 레이아웃 1 열             | 이 템플릿은 이동 경로, 페이지 제목 및 페이지 복사 콘텐츠가 포함 된 단일 열 레이아웃을 렌더링 합니다.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| 레이아웃 2 열 너비 남음   | 이 템플릿은 두 개의 열 레이아웃을 렌더링 합니다. 왼쪽 열이 오른쪽 보다 큽니다. 페이지 맨 위에 이동 경로, 페이지 제목 및 페이지 복사 콘텐츠가 왼쪽 열에 있습니다.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| 레이아웃 2 열 너비 오른쪽  | 이 템플릿은 두 개의 열 레이아웃을 렌더링 합니다. 오른쪽 열이 왼쪽 보다 더 큽니다. 페이지 맨 위에 이동 경로, 페이지 제목 및 페이지 복사 내용이 오른쪽 열에 있습니다.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| 레이아웃 3 열 너비 중간 | 이 템플릿은 세 개의 열 레이아웃을 렌더링 합니다. 가운데 열이 왼쪽과 오른쪽 보다 큽니다. 레이아웃에는 페이지 위쪽의 이동 경로와 페이지 제목 및 페이지 복사 콘텐츠가 가운데 열에 있습니다.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| 페이지 복사                   | 이 템플릿은 포함 된 액체를 지 원하는 편집 가능한 페이지 복사 콘텐츠 HTML을 렌더링 합니다.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| 페이지 머리글                 | 이 템플릿은 페이지 제목을 렌더링 합니다.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| 여론                        | 이 템플릿은 폴링 배치에서 이름 또는 임의 폴링으로 폴링을 렌더링 합니다.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Search                      | 이 템플릿은 단일 텍스트 입력 및 검색 단추를 사용 하 여 기본 검색 폼을 렌더링 합니다.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| 쪽 탐색             | 이 템플릿은 세로 트리 뷰 스타일 탐색을 렌더링 합니다. 부모 페이지에 대 한 링크는 첫 번째 수준 (또는 지정 된 깊이 오프셋), 현재 페이지의 형제 페이지에 대 한 링크 및 현재 페이지의 자식에 대 한 링크를 포함 합니다. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| 살펴보겠습니다                     | 이 템플릿은 편집 가능한 HTML 콘텐츠 코드 조각을 이름으로 렌더링 합니다.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| 위쪽 탐색              | 이 템플릿은 기본 탐색 웹 링크 집합의 드롭다운 메뉴를 사용 하 여 편집 가능한 탐색 모음을 렌더링 합니다.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Weblink List 그룹          | 이 템플릿은 웹 링크 집합에 대 한 링크의 목록 그룹을 렌더링 합니다.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>참고 항목

[액체 연산자 이해](liquid-operators.md)  
[액체 유형](liquid-types.md)  
[Defined](liquid-conditional-operators.md)  
[액체 개체](liquid-objects.md)  
[액체 태그](liquid-tags.md)  
[액체 필터](liquid-filters.md)  
