---
title: 포털에 대한 유동 개체 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 개체에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 857c65097800420662aafe825f61333037b4e31c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757319"
---
# <a name="available-liquid-objects"></a>사용 가능한 유동 개체

유동 개체는 페이지에 동적 콘텐츠를 출력하는 특성을 포함합니다. 예를 들어, 페이지 개체는 현재 페이지의 제목을 출력하는 데 쓰일 수 있는 제목이라 불리는 특성을 가집니다.

이름으로 개체 특성에 액세스하려면 점을 사용하십시오. 템플릿에서 개체의 특성을 렌더링하려면 {{ 및 }} 사이에 배치하십시오.

```
{{ page.title }}
```
개체의 특성은 문자열 이름과 \[\]을 사용하여 액세스할 수도 있습니다. 특성의 이름이 . 구문을 사용할 때 원하는 특성을 동적으로 확인할 때나 유효하지 않은 문자, 공백, 특수 문자 등을 포함하는 경우 유용합니다.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

다음 개체는 어디서든, 어느 템플릿에서든 사용하고 액세스할 수 있습니다.


|   개체    |                                                                                                                                                                                          설명                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  엔터티   |                                                                                                 ID로 모든 PowerApps 엔터티를 로드할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [엔터티](#entities)                                                                                                 |
|     지금     |                                          템플릿이 렌더링될 때 현재 UTC 시간을 나타내는 날짜/시간 개체입니다.<br>**참고**: 이 값은 포털 웹 앱에 의해 캐싱되며 매번 새로 고쳐지지 않습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [날짜 필터](liquid-filters.md#date-filters)                                          |
|    페이지     | 현재 포털 요청 페이지를 참조합니다. 페이지 개체는 현재 페이지의 이동 경로, 현재 페이지의 제목 또는 URL, 그리고 기본 PowerApps 레코드의 기타 특성 또는 관련된 엔터티에 대한 액세스를 제공합니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [페이지](#page) |
|   params    |                                                                                                                             request.params에 대한 편리한 바로 가기입니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [요청](#request)                                                                                                                              |
|   요청   |                                                                                                                        현재 HTTP 요청에 대한 정보가 담겨 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [요청](#request)                                                                                                                        |
|  설정   |                                                                                                            이름을 사용하여 모든 [사이트 설정](../configure/configure-site-settings.md)을 로드할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [설정](#settings)                                                                                                            |
|   sitemap   |                                                                                                                               포털 사이트 맵에 대한 액세스를 허용합니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [사이트 맵](#sitemap)                                                                                                                                |
| 사이트 마커 |                                                                                                                        이름을 사용하여 모든 사이트 마커를 로드할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [sitemarkers](#sitemarkers)                                                                                                                        |
|  조각   |                                                                                                         이름으로 [콘텐츠 조각](../configure/customize-content-snippets.md)을 로드할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [코드 조각](#snippets)                                                                                                         |
|    사용자     |                             현재 포털 사용자를 참조하여 기본 PowerApps 연락처 레코드의 모든 특성에 액세스할 수 있습니다. 로그인한 사용자가 없으면 이 변수는 [null](liquid-types.md#null)입니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [사용자](#user)                              |
|  웹 링크   |                                                                                                                        이름 또는 ID로 모든 웹 링크 집합을 로드할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [웹 링크](#weblinks)                                                                                                                        |
|   웹 사이트   |                                                      포털 웹 사이트 레코드를 참조하여 포털에 대한 PowerApps 웹 사이트(adx\_website) 레코드의 모든 특성에 액세스할 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [웹 사이트](#website)                                                       |

## <a name="ads"></a>광고


광고에 액세스하고 광고를 렌더링하는 기능을 제공합니다.

광고 개체를 사용하여 특정 광고 또는 광고 배치를 선택할 수 있습니다.

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>광고 특성

|특성   |설명   |
|---|---|
| placements        | 광고 배치 개체를 반환합니다.    |
| \[광고 이름 또는 ID\] | 이름 또는 ID 속성으로 어느 광고에든 액세스할 수 있습니다. <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>광고 배치 특성

|특성   |설명   |
|---|---|
| \[광고 배치 이름 또는 ID\] | 이름 또는 ID 속성으로 어느 광고 배치에든 액세스할 수 있습니다.<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>광고 배치 특성

광고 배치는 아래에 나열된 특성 이외에 모두 동일한 특성을 가진 엔터티 개체입니다.

|특성   |설명   |
|---|---|
| 광고            | 배치와 연관된 광고 개체 모음을 반환합니다.  [반복 태그](iteration-tags.md) 및 [배열 필터](liquid-filters.md#array-filters)는 이 모음과 함께 사용할 수 있습니다.  |  
| 이름           | 광고 배치의 이름 필드를 반환합니다.                                                                |
| placement\_url | 템플릿으로 완전히 렌더링된 광고 배치를 검색하는 데 사용할 수 있는 URL입니다.                         |
| random\_url    | 템플릿으로 완전히 렌더링된 배치에서 무작위로 광고를 검색하는 데 사용할 수 있는 URL입니다.           |

### <a name="ad-attributes"></a>광고 특성

> [!Note]
> 광고는 아래에 나열된 특성 이외에 모두 동일한 특성을 가진 엔터티 개체입니다.

|특성   |설명   |
|---|---|
| ad\_url |  템플릿으로 완전히 렌더링된 광고를 검색하는 데 사용할 수 있는 URL입니다.   |
| 복사| 광고의 복사 필드를 반환합니다.|
| image| 광고의 이미지 개체(있는 경우)를 반환합니다.|
| 이름| 광고의 이름 필드를 반환합니다.|
| open\_in\_new\_window | redirect\_url이 지정한 URL이 새 창에서 열리는 경우 true를 반환합니다. |
| redirect\_url| 사용자가 광고를 선택했을 때 리디렉션되는 URL입니다.|

### <a name="ad-image-attributes"></a>광고 이미지 특성

|특성   |설명   |
|---|---|
| alternate\_text | 태그의 대체 특성에 나타내고자 하는 텍스트를 반환합니다. |
| height          | 이미지의 높이를 픽셀로 반환합니다.                             |
| URL             | 이미지에 대한 URL 원본을 반환합니다.                                  |
| width           | 이미지의 너비를 픽셀로 반환합니다.                              |


## <a name="blogs"></a>blogs

블로그 및 블로그 게시물에 액세스하고 렌더링할 수 있는 기능을 제공합니다.

블로그 개체는 특정 블로그 또는 블로그 게시물의 선택을 가능하게 합니다.

```
{% assign posts = blogs.posts | paginate: 0,4 %}

<div class=content-panel panel panel-default>

<div class=panel-heading>

{% assign sitemarker = sitemarkers[Blog Home] %}

{% assign snippet = snippets[Home Blog Activity Heading] %}

<a class=pull-right href={{sitemarker.url}}> All Blogs </a>

<h4>

<a class=feed-icon fa fa-rss-square href={{ blogs.feedpath }} />

{{ snippet.adx_value }}

</h4>

</div>

<ul class=list-group>

{% for post in posts.all %}

<li class=list-group-item >

<a class=user-avatar href={{ post.author_url }}>

<img src={{ post.user_image_url }} />

</a>

<h4 class=list-group-item-heading>

<a href={{ post.app_relative_path }}>{{ post.title }}</a>

</h4>

<div class=content-metadata>

<abbr class=timeago>{{ post.publish_date }}</abbr>

&ndash;

<a href={{ post.author_url }}> {{ post.author_name }} </a>

&ndash;

<a href={{ post.application_path }}#comments>

<span class=fa fa-comment aria-hidden=true></span> {{ post.comment_count }}

</a>

</div>

</li>

{% endfor %}

</ul>

</div>
```

### <a name="blogs-object"></a>blogs 개체

블로그 개체를 통해 포털의 특정 블로그에 액세스하거나 (블로그에 관계 없이) 포털의 모든 블로그 게시물에 액세스할 수 있습니다.

다음 표는 블로그 개체와 관련된 특성을 설명합니다.

|특성   |설명   |
|---|---|
| posts               | 포털의 모든 블로그 게시물을 포함하는 블로그 게시물 개체를 반환합니다.     |
| \[블로그 이름 또는 ID\] | 이름 또는 ID 속성으로 어떤 블로그에든 액세스할 수 있습니다.                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>blog 개체

블로그 개체를 통해 단일 블로그로 작업하여 해당 블로그를 위한 게시물에 액세스할 수 있습니다.

다음 표는 blog 개체와 관련된 다양한 특성을 설명합니다.

|특성   |설명   |
|---|---|
| posts | 블로그를 위한 모든 블로그 게시물을 포함하는 블로그 게시물 개체를 반환합니다. |
| 이름  | 블로그의 이름.                                              |
| title | 블로그의 제목.                                             |
| URL   | 블로그의 URL.                                               |

### <a name="blogposts-object"></a>blogposts 개체

블로그 게시물 개체를 사용하여 블로그 게시물 개체 모음에 액세스할 수 있습니다. 블로그 게시물의 순서를 정하고 페이지를 매기며 유동 필터를 사용할 수 있습니다.

{% assign blogposts = blogs.posts | order\_by “adx\_name”, “desc” | paginate: 0,4 | all %} blogs.posts.all 또한 모든 블로그 게시물 blogs.posts를 가져오는 유효한 방법 | from\_index: 0 | take: 2 또한 가능

다음 표는 blogposts 개체와 관련된 다양한 특성을 설명합니다.

|특성   |설명   |
|---|---|
| 모두 | 컬렉션에 있는 모든 블로그 게시물 개체를 반환합니다. |

### <a name="blogpost-object"></a>blogpost 개체

단일 블로그 게시물을 지칭합니다.

다음 표는 blogpost 개체와 관련된 다양한 특성을 설명합니다.

|특성   |설명   |
|---|---|
| url            | 게시물의 URL.                                                                |
| content        | 게시물의 콘텐츠 필드를 반환합니다.                                             |
| content        | 게시물의 콘텐츠 필드를 반환합니다.                                             |
| author         | 게시물의 작성자(단순히 연락처 엔터티 개체)를 반환합니다.          |
| title          | 게시물의 제목.                                                              |
| comment\_count | 특정 게시물에 달린 댓글 수의 정수값을 반환합니다. |
| publish\_date  | 게시물이 게시된 날짜.                                           |

## <a name="entities"></a>엔터티

ID로 모든 PowerApps 엔터티를 로드할 수 있습니다. 엔터티가 존재하는 경우, 엔터티 개체가 반환될 것입니다. 주어진 ID의 엔터티가 발견되지 않으면 [null](liquid-types.md#null)이 반환될 것입니다.  

```
{% assign account = entities.account['936DA01F-9ABD-4d9d-80C7-02AF85C822A8'] %}

{% if account %}

{{ account.name }} ({{ account.statecode.label }})

{% endif %}

{% assign entity_logical_name = 'contact' %}

{% assign contact = entities[entity_logical_name][request.params.contactid] %}

{% if contact %}

{{ contact.fullname }} ({{ contact.parentcustomerid.name }})

{% endif %}
```

### <a name="entity"></a>Entity

엔터티 개체는 PowerApps 엔터티 레코드의 특성에 대한 접근 권한을 제공합니다.


|             특성              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 Id                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    문자열로서의 엔터티의 GUID ID. 예: 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           logical\_name            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   엔터티의 PowerApps 논리적 이름입니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               메모                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             엔터티와 연계된 메모(annotation)를 이전부터 최신의 순서로 로드합니다(createdon). 메모는 메모 개체로 반환됩니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            권한             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             엔터티에 대한 엔터티 권한 주장 결과를 로드합니다. 결과는 권한 개체로 반환됩니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                URL                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    엔터티에 대한 PowerApps 포털 콘텐츠 관리 시스템 URL 경로를 반환합니다. 엔터티가 현재 웹사이트에 유효한 URL을 갖고 있지 않는 경우 null을 반환합니다. 귀하가 응용 프로그램에서 URL 공급자를 맞춤화하지 않은 한 일반적으로 이것은 포털 CMS 에 통합된 특정 엔터티 타입을 위한 값만 반환할 것입니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[특성 또는 관계 이름\] | 논리적 이름으로 PowerApps 엔터티의 특성에 액세스할 수 있습니다. `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>대부분의 엔터티 특성들의 값은 직접 [유동 유형](liquid-types.md)에 매핑됩니다. 두 옵션 필드는 부울에, 텍스트 필드는 문자열에, 숫자/통화 필드는 숫자에, 날짜/시간 필드는 날짜 개체에 매핑됩니다. 그러나 일부 특성 유형은 다음 개체로 반환됩니다.<ul><li>조회(엔터티 참조) 필드는 엔터티 참조 개체로 반환됩니다.</li><li>옵션 설정/픽리스트 필드는 옵션 설정값 개체로 반환됩니다.</li><li>관련된 엔터티를 관계 스키마 이름에 의해서도 로드할 수 있습니다.</li>`{{ page.adx_webpage_entitylist.adx_name }}`관계가 재귀 관계(즉, 자가 참조적)인 경우에는 재귀 관계 개체가 반환될 것입니다. (그렇지 않으면, 결과가 애매모호할 것입니다.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**참고**: 단일 템플릿에서 큰 수의 관련 엔터티를 로드하거나 큰 수의 관계에 액세스하는 것은 템플릿 렌더링 수행에 부정적 영향을 미칠 수 있습니다. 한 루프 내에서 연속으로 각 항목의 관련 엔터티 로드를 피하십시오. 가능하면 엔터티 모음을 로드하기 위해 [PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md)를 사용하십시오. |

### <a name="entity-reference"></a>엔터티 참조

특성 조회 값은 다음 특성을 가진 엔터티 참조 개체로 반환됩니다.


|   특성   |                                                설명                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      Id       | 문자열로서의 참조된 엔터티의 GUID ID. <br> 예: 936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| logical\_name |  참조된 엔터티의 PowerApps 논리적 이름입니다.   |
|     이름      |                           참조된 엔터티의 기본 이름 특성.                            |

### <a name="note"></a>메모

메모는 주석 레코드의 특성과 관계에 대한 접근 권한을 제공하는 엔터티 개체입니다. 엔터티 개체의 모든 특성뿐만 아니라 메모는 다음 추가 특성을 갖습니다.


|  특성   |                                                                                                                                                                                                                                  설명                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | 메모 주석 레코드의 documentbody 특성을 Base64 인코딩 문자열로 로드합니다. 이 특성의 콘텐츠가 클 수 있기 때문에 나머지 메모 특성과 함께 로드되지 않고 요구 시에만 로드됩니다. <br> **참고**: documentbody 특성 사용은 템플릿 렌더링 성능에 부정적 영향을 미칠 수 있으므로 조심해서 사용해야 합니다.<br>그 대신에 가능하면 url 특성을 사용하여 메모 첨부의 링크를 제공하십시오. |
|     URL      |                                                                                                                                   내장된 포털 주석 첨부 핸들러를 위한 URL 경로를 반환합니다. 사용자에게 권한이 있고 메모에 첨부 파일이 있는 경우, 이 URL 요청은 메모 파일 첨부를 다운로드할 것입니다.                                                                                                                                    |

>[!Note]
> [추가 필터](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>옵션 집합 값

옵션 설정/픽리스트 특성 값은 다음 특성을 가진 엔터티 참조 개체로 반환됩니다.

| 특성 | 설명                                                     |
|-----------|-----------------------------------------------------------------|
| 레이블     | 옵션 설정/픽리스트 특성 값의 현지화된 레이블. 예: 활성|
| 값     | 옵션 설정/픽리스트 특성 값의 정수 값. 예: 0                                                           |

### <a name="entity-permissions"></a>엔터티 권한

엔터티 권한 개체는 엔터티에 대한 총합 권한 주장 결과에 대한 액세스 권한을 제공합니다.

| 특성       | 설명                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| can\_append     | 레코드를 이 레코드 관계에 첨부할 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                              |
| can\_append\_to | 이 레코드를 다른 엔터티 관계에 첨부할 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                      |
| can\_create     | 이 엔터티 타입의 새 레코드를 생성할 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                      |
| can\_delete     | 이 레코드를 삭제할 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                                          |
| can\_read       | 이 레코드를 읽을 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                                            |
| can\_write      | 이 레코드를 업데이트할 권한이 현재의 사용자에게 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                                          |
| rules\_exist    | 이 개체가 대표하는 권한 결과가 명시적으로 정의된 권한 규칙의 결과인 경우 true를 반환합니다. 명시적으로 정의된 권한이 없을 때 기본 결과인 경우 false를 반환합니다. |

### <a name="reflexive-relationship"></a>재귀 관계

엔터티에 대한 재귀(즉, 자가 참조적)인 관계를 로드하려는 시도는 다음 특성을 가진 개체로 반환됩니다.

| 특성     | 설명                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| is\_reflexive | true를 반환합니다. 관계가 반환한 개체가 재귀 관계 개체인 경우인지 테스트하는 데 사용될 수 있습니다. |
| referenced    | 특정 관계에 대해 참조된 엔터티 전체를 반환합니다.                                           |
| referencing   | 특정 관계에 대해 참조된 엔터티를 반환합니다. 참조 엔터티가 존재하지 않는 경우 null을 반환합니다. 관계가 다수 대 다수(N:N)인 경우, 참조 엔터티 전체를 반환합니다.                          

## <a name="entitylist"></a>entitylist

엔터티 목록 개체는 [PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md) 내에서 사용됩니다. 주어진 엔터티 목록의 모든 특성에 대한 액세스를 제공합니다.  

> [!Note]                                                       
> [현재 페이지와 연관된 엔터티 목록 렌더링](render-entity-list-current-page.md)

### <a name="attributes"></a>특성

> [!Note]
> [entities](#entities)

|               특성               |                                                                                                                            설명                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            create\_enabled            |                                                                                엔터티 목록을 위해 새 레코드 만들기가 구성된 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                |
|              create\_url              |                                                                                          엔터티 목록의 만들기 링크/단추를 위해 구성된 URL 경로를 반환합니다.                                                                                          |
|            detail\_enabled            |                                                                         개별 레코드의 세부 정보 보기가 엔터티 목록을 위해 구성되어 있는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                          |
|         detail\_id\_parameter         |               레코드 세부 정보 보기 URL을 작성할 때 레코드 ID에 사용할 쿼리 문자열 매개 변수 이름을 반환합니다. 유동 필터를 사용하여 URL을 작성하는 데 대한 자세한 내용은 [URL 필터](liquid-filters.md#url-filters)를 참조하십시오. 예: id                |
|             detail\_label             |                                                                                     엔터티 목록의 세부 정보 보기 링크/단추를 위해 구성된 지역화된 레이블을 반환합니다.                                                                                     |
|              detail\_url              |                                                                                       엔터티 목록의 세부 정보 보기 링크/단추를 위해 구성된 URL 경로를 반환합니다.                                                                                        |
|           empty\_list\_text           |                                                                                엔터티 목록 보기에 결과가 반환되지 않을 때 표시하도록 구성된 지역화된 텍스트를 반환합니다.                                                                                |
|      enable\_entity\_permissions      |                                                                               엔터티 권한 필터링이 이 엔터티 목록에 사용된 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                               |
|         entity\_logical\_name         |                                                 이 엔터티 목록으로 표시되는 레코드의 PowerApps 엔터티 논리 이름을 반환합니다. 예: contact                                                 |
|   filter\_account\_attribute\_name    |                                            현재 포털 사용자의 상위 계정으로 결과 레코드를 필터링하는 데 사용할 거래처에 대한 조회를 위해 특성 논리 이름을 반환합니다. 예: accountid                                            |
|         filter\_apply\_label          |                                                            엔터티 목록 결과에 고급 특성 필터를 적용하는 링크/단추에 사용하도록 구성된 지역화된 레이블을 반환합니다.                                                            |
|          filter\_definition           |                      엔터티 목록의 JSON 특성 필터 정의를 반환합니다. metafilters 유동 필터를 사용하여 이 정의를 처리하는 방법에 대한 자세한 내용은 [엔터티 목록 필터](liquid-filters.md#entity-list-filters)를 참조하십시오.                       |
|            filter\_enabled            |                                                                               고급 특성 필터링이 엔터티 목록에 사용되는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                               |
| filter\_portal\_user\_attribute\_name |                                                 현재 포털 사용자의 거래처로 결과 레코드를 필터링하는 데 사용할 연락처에 대한 조회를 위해 특성 논리 이름을 반환합니다. 예: contactid                                                  |
|   filter\_website\_attribute\_name    |                                              현재 포털 웹 사이트로 결과 레코드를 필터링하는 데 사용할 adx\_website에 대한 조회를 위해 특성 논리 이름을 반환합니다. 예: adx\_websiteid                                              |
|            language\_code             |                                               이 엔터티 목록의 모든 지역화된 레이블을 선택하는 데 사용될 PowerApps 정수 언어 코드를 반환합니다.                                                |
|              page\_size               |                                                                                                   엔터티 목록의 구성된 결과 페이지 크기를 반환합니다.                                                                                                    |
|          primary\_key\_name           |                                                                                  이 엔터티 목록으로 표시되는 레코드의 기본 키 특성 논리 이름을 반환합니다.                                                                                  |
|            search\_enabled            |                                                                                         검색이 이 엔터티 목록에 사용된 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                          |
|          search\_placeholder          |                                                                                        엔터티 목록 검색 필드 자리 표시자를 위해 구성된 지역화된 텍스트를 반환합니다.                                                                                        |
|            search\_tooltip            |                                                                                             엔터티 목록 검색 도구 설명을 위해 구성된 지역화된 텍스트를 반환합니다.                                                                                             |
|                 보기                 |                                                                                           엔터티 목록 보기 개체로서 엔터티 목록에 사용할 수 있는 보기를 반환합니다.                                                                                           |
|      \[특성 논리적 이름\]       | [entity](liquid-objects.md#entity) 개체와 동일하게 논리적 이름별로 엔터티 목록(adx\_entitylist) PowerApps 레코드의 특성에 액세스할 수 있습니다. 예: {{ entitylist.adx\_name }} |

### <a name="entity-list-view-attributes"></a>엔터티 목록 보기 특성

|          Attribute(특성)          |                                                                                     설명                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                                                         엔터티 목록 보기 열 개체로서 해당 보기의 열을 반환합니다.                                                         |
|    entity\_logical\_name    |               보기에 포함된 레코드의 PowerApps 엔터티 논리 이름을 반환합니다. 예: contact                |
|             Id              |                                                                          보기의 GUID ID를 반환합니다.                                                                           |
|       language\_code        | 보기에 대해 모든 지역화된 레이블(열 머리글 등)을 선택하는 데 사용될 PowerApps 정수 언어 코드를 반환합니다. |
|            이름             |                                          보기의 PowerApps 디스플레이 이름을 반환합니다.                                          |
| primary\_key\_logical\_name |        보기에 포함된 레코드의 PowerApps 엔터티 기본 키 논리 이름을 반환합니다. 예: contactid         |
|      sort\_expression       |                                               보기의 기본 정렬 식을 반환합니다. 예: name ASC, createdon DESC                                               |

### <a name="entity-list-view-column-attributes"></a>엔터티 목록 보기 열 특성

|    특성     |                                                                                    설명                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| attribute\_type  | 열의 PowerApps 특성 유형 이름을 문자열로 반환합니다. 예: Lookup, Picklist, String, Boolean, DateTime |
|  logical\_name   |                       열의 PowerApps 특성 논리 이름을 반환합니다. 예: createdon                       |
|       이름       |                      열의 지역화된 PowerApps 디스플레이 이름을 반환합니다. 예: Created On                       |
| sort\_ascending  |                                      열을 오름차순으로 정렬하기 위한 정렬 식 문자열을 반환합니다. 예: createdon ASC                                       |
| sort\_descending |                                     열을 내림차순으로 정렬하기 위한 정렬 식 문자열을 반환합니다. 예: createdon DESC                                      |
|  sort\_disabled  |                                                   열에서 정렬을 사용하지 않는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                    |
|  sort\_enabled   |                                                    열에서 정렬을 사용하는 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                    |
|      width       |                                                              열의 구성된 너비를 픽셀 단위로 반환합니다.                                                              |

## <a name="entityview"></a>entityview

entityview 개체는 엔터티 보기 태그 내에서 사용되며, 결과 레코드 보기를 포함한 보기에 대한 메타데이터에 대한 액세스를 제공합니다.

### <a name="attributes"></a>특성

|          특성          |                                                                               설명                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                         [엔터티 보기 열 개체](liquid-objects.md#entity-list-view-column-attributes)로서 해당 보기에 열을 반환합니다.                          |
| entity\_permission\_denied  | 현재 사용자에게 충분한 엔터티 권한이 없기 때문에 결과 보기에 대한 액세스가 거부된 경우 true를 반환합니다. 결과 보기에 대한 읽기 액세스 권한이 부여되면 false를 반환합니다. |
|    entity\_logical\_name    |                   결과 보기 레코드의 PowerApps 엔터티 논리 이름입니다. 예: contact                   |
|         first\_page         |                 결과 보기 첫 페이지의 페이지 번호입니다. 반환된 결과가 없는 경우 1이며, 이 경우 null입니다.                  |
|             Id              |                            이 entityview를 정의하는 PowerApps 보기의 GUID ID입니다.                             |
|       language\_code        |             현재 보기에 대해 현지화된 레이블을 로드하는 데 사용되는 PowerApps 정수 언어 코드입니다.              |
|         last\_page          |                                 결과 보기 마지막 페이지의 페이지 번호입니다. 반환된 결과가 없다면 null입니다.                                  |
|            이름             |              이 entityview를 정의하는 PowerApps 보기의 이름입니다(예: 활성 연락처).               |
|         next\_page          |                                결과 보기의 다음 페이지의 페이지 번호입니다. 다음 페이지의 결과가 없는 경우 null입니다.                                 |
|            페이지             |                                                           결과 보기의 현재 페이지의 페이지 번호입니다.                                                           |
|            모든 페이지            |                                          현재 보기에 대해 모든 페이지 결과를 포함하는 페이지 번호의 배열을 반환합니다.                                          |
|         page\_size          |                                                      현재 보기에 대해 페이지당 반환되는 결과의 수입니다.                                                       |
|       previous\_page        |                              결과 보기의 다음 페이지의 페이지 번호입니다. 이전 페이지의 결과가 없는 경우 null입니다.                               |
| primary\_key\_logical\_name |  이 보기에 대한 결과 엔터티의 기본 키 특성의 PowerApps 논리 이름입니다. 예: contactid   |
|           레코드           |                                                   엔터티 개체로서 해당 보기에 대한 결과 레코드의 현재 페이지입니다.                                                    |
|      sort\_expression       |                                             보기에 대한 기본 정렬 식입니다. 예: nameASC, createdon DESC                                              |
|        total\_pages         |                                                              보기에 대한 총 결과 페이지 수입니다.                                                              |
|       total\_records        |                                                       (모든 페이지에 걸친) 보기에 대한 총 결과 수입니다.                                                       |

## <a name="events"></a>events

이벤트에 액세스하고 이벤트를 렌더링하는 기능을 제공합니다. events 개체를 사용하여 특정 이벤트 또는 모든 이벤트를 선택할 수 있습니다.

### <a name="events-object"></a>events 개체

events 개체로 (이벤트에 관계 없이) 포털에서 특정 이벤트 또는 모든 이벤트에 액세스할 수 있습니다.

events 개체에는 다음과 같은 특성이 있습니다.

|특성   |설명   |
|---|---|
|occurences |포털에 모든 이벤트 항목을 포함하는 eventoccurancessobject를 반환합니다. |
|[이벤트 이름 또는 ID] |이름 또는 ID 속성으로 어떤 이벤트에든 액세스할 수 있습니다.<br>{% assign event = events[&quot;이벤트 이름&quot;] %}<br>{% assign event = events[&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;] %} |

### <a name="event-object"></a>event 개체

event 개체를 사용하여 특정 이벤트의 일정 및 항목에 액세스하는 등 단일 이벤트에 대한 조작이 가능합니다.

event 개체에는 다음과 같은 특성이 있습니다.

|특성   |설명   |
|---|---|
| 번 발생 | 이벤트에 대해 모든 항목을 포함하는 eventoccurrencesobject를 반환합니다. |
| 이름       | 이벤트의 이름입니다.                                                     |
| URL        | 이벤트의 URL입니다.                                                      |

### <a name="eventoccurences-object"></a>eventoccurences 개체

eventoccurrences 개체를 사용하여 이벤트 항목 개체의 모음에 액세스할 수 있습니다. 유동 필터를 사용하여 이벤트 항목을 정렬하고, 검색할 항목들에 대한 날짜 범위를 지정하고, 페이지를 찾을 수도 있습니다.

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

다음 사항에 주의하십시오.

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

또한 가능합니다.

다음의 특성들은 eventoccurrences 개체와 연관됩니다.

|특성   |설명   |
|---|---|
| 모두 | 컬렉션에 있는 모든 eventoccurance 개체를 반환합니다. |

### <a name="eventoccurence-object"></a>eventoccurence 개체

단일 이벤트 항목을 나타냅니다. 관련된 특성은 다음과 같습니다.

|특성   |설명   |
|---|---|
| URL                 | 항목의 URL입니다.    |
| is\_all\_day\_event | 하루 종일 진행되는 이벤트입니까?     |
| start\_time         | 이벤트의 시작 시간입니다. |
| end\_time           | 이벤트의 종료 시간입니다.   |


## <a name="forloop"></a>forloop

[for](iteration-tags.md#for) 루프 블록 내에서 유용하게 사용되는 속성을 포함하고 있습니다.  

> [!Note]
> forloop는 [for](iteration-tags.md#for) 태그 내에서만 사용할 수 있습니다.

**코드**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**출력**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| 첫째   | 루프의 첫 번째 반복인 경우 true를 반환합니다. 첫 번째 반복이 아닌 경우 false를 반환합니다.       |
| 색인   | 모음에서 현재 항목의 위치, 이 때 첫 번째 항목은 1의 위치를 갖습니다.                   |
| index0  | 모음에서 현재 항목의 위치, 이 때 첫 번째 항목은 0의 위치를 갖습니다.                   |
| 마지막    | 루프의 마지막 반복인 경우 true를 반환합니다. 마지막 반복이 아닌 경우 false를 반환합니다.         |
| length  | 모음에서 반복되고 있는 항목의 수, 즉, 루프에 대한 반복의 수를 반환합니다. |
| rindex  | 루프(길이 - 지수)에 남아 있는 항목의 수, 이 때 1은 마지막 항목의 지수입니다.              |
| rindex0 | 루프(길이 - 지수)에 남아 있는 항목의 수, 이 때 0은 마지막 항목의 지수입니다.              |


## <a name="forums"></a>forums

포럼 및 포럼 스레드에 액세스하고 렌더링하는 기능을 제공합니다. 유동을 사용하여 포럼 데이터를 렌더링하는 기능을 게시물에도 사용할 수 있지만 새 게시물 또는 스레드를 만들기 위해서는 언급된 내장 기능(기본 포럼 스레드, 포럼 게시 페이지 템플릿 등)이 있는 ASP.NET 웹 양식 페이지 템플릿을 사용해야 합니다.

포럼 개체를 사용하여 포럼 또는 포럼 스레드를 선택할 수 있습니다.

```
<div class=content-panel panel panel-default>

<div class=panel-heading>

<h4>

<span class=fa fa-comments aria-hidden=true></span>

{{ snippets[Home Forum Activity Heading] | default: Forum Activity | h }}

</h4>

</div>

{% for forum in website.forums %}

<ul class=list-group>

<li class=list-group-item>

<div class=row>

<div class=col-sm-6>

<h4 class=list-group-item-heading><a href="{{ forum.url | h }}"> {{ forum.name | h }}</a></h4>

<div class=list-group-item-text content-metadata>{{ forum.adx_description | h }}</div>

</div>

<div class=col-sm-3 content-metadata>{{ forum.thread_count }} threads</div>

<div class=col-sm-3 content-metadata>{{ forum.post_count }} posts</div>

</div>

</li>

</ul>

{% endfor %}

</div>
```

### <a name="forums-object"></a>포럼 개체

포럼 개체로 포털의 특정 포럼에 액세스하거나 (이벤트에 관계 없이) 포털의 모든 포럼 스레드에 액세스할 수 있습니다.

forum 개체를 사용하여 단일 포럼에서 작업할 수 있으며 해당 포럼의 스레드에 액세스할 수 있습니다.

forumthreads 개체를 사용하여 forumthread 개체의 모음에 액세스할 수 있습니다. 유동 필터를 사용하여 포럼 스레드를 정렬하고 페이지 번호도 지정할 수 있습니다.

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

단일 포럼 스레드

forumposts 개체를 사용하여 forumpost 개체 컬렉션에 액세스할 수 있습니다.

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| threads              | 포털의 모든 forumthread 개체를 포함하는 forumthreads 개체를 반환합니다.             |
| 모두                  | 포털의 모든 forum 개체를 반환합니다. 또한 website.forums도 등가입니다.    |
| thread\_count        | 전체 웹 사이트에 있는 스레드 수의 정수 값을 반환합니다. |
| post\_count          | 포털에 있는 총 게시물 수의 정수 값을 반환합니다.                       |
| \[포럼 이름 또는 ID\] | 이름 또는 ID 속성으로 어떤 포럼에든 액세스할 수 있습니다. <br>`{% assign forum = forums[포럼 이름] %}<br>{% assign forum = forums[da8b8a92-2ee6-476f-8a21-782b047ff460] %} 

### <a name="forum-object"></a>forum 개체

### <a name="attributes"></a>특성

> [!Note]
> [엔터티](#entities)

|Attribute(특성)   |설명   |
|---|---|
| threads       | 포럼의 모든 포럼 스레드를 포함하는 forumthreads 개체를 반환합니다.               |
| 이름          | 포럼의 이름입니다.                                                                  |
| thread\_count | 포럼에 있는 스레드 수의 정수 값을 반환합니다.      |
| post\_count   | 전체 포럼에 있는 게시물 수의 정수 값을 반환합니다. |

### <a name="forumthreads-object"></a>forumthreads 개체

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| 모두 | 컬렉션에 있는 모든 forumthread 개체를 반환합니다. |

### <a name="forumthread-object"></a>forumthread 개체

### <a name="attributes"></a>특성

> [!Note]
> [entities](#entities)

|특성   |설명   |
|---|---|
| posts        | 스레드의 모든 포럼 게시물을 포함하는 forumposts 개체를 반환합니다.            |
| author       | 스레드의 작성자(단순히 연락처 엔터티 개체)를 반환합니다.      |
| latest\_post | 스레드의 최신 게시물을 반환합니다.                                            |
| first\_post  | 스레드의 첫 번째 게시물을 반환합니다.                                             |
| post\_count  | 스레드에 있는 게시물 수의 정수 값을 반환합니다. |
| is\_answered | 스레드가 답변되었습니까?                                                    |
| is\_sticky   | 스레드가 고정 스레드입니까?                                                    |

### <a name="forumposts-object"></a>forumposts 개체

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| 모두 | 컬렉션에 있는 모든 forumthread 개체를 반환합니다. |

단일 포럼 게시물

### <a name="attributes"></a>특성

> [!Note] 
> [entities](#entities)

|특성   |설명   |
|---|---|
| author     | 게시물의 작성자(단순히 연락처 엔터티 개체)를 반환합니다. |
| content    | 게시물의 내용입니다.                                                   |
| is\_answer | 이 게시물이 스레드에 대한 답입니까?                                      |


## <a name="knowledge"></a>지식

PowerApps 참조 자료 및 범주 엔터티 레코드에 대한 액세스를 제공하여 포털에서 기사와 범주를 렌더링합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---|---|
|기사|포털에서 사용할 수 있는 참조 문서 엔터티 레코드에 대한 기사 개체가 포함된 기사 개체를 반환합니다.|
|범주|포털에서 사용할 수 있는 범주 엔터티 레코드에 대한 범주 개체가 포함된 범주 개체를 반환합니다.|
|||

### <a name="articles-object"></a>기사 개체

기사 개체를 사용하여 기사 개체 모음에 액세스할 수 있습니다. 유동 필터를 사용하여 기사를 정렬하고 페이지 번호도 지정할 수 있습니다.

```
{% assign count = count | default: 3 %}
{% assign languagecode = website.selected_language.code %}
{% assign popular_articles = knowledge.articles | popular: count,languagecode  %}
{% if popular_articles %}
    <div class=list-group>
    {% for article in popular_articles %}
      <div class=list-group-item clearfix>
        <a class=title href={{ article.url | escape }}>{{ article.title | escape }}</a>
        <p class=description>{{ article.description | escape }}</p>
      </div>
    {% endfor %}
    </div>
{% endif %}
```

### <a name="attributes"></a>특성

|특성|설명|
|---|---|
|인기 |가장 많은 뷰가 포함된 기사 개체의 모음을 반환합니다. `{% assign popular_articles = knowledge.articles.popular %}` |
|최근 |최근 수정일이 포함된 기사 개체의 모음을 반환합니다. `{% assign recent_articles = knowledge.articles.recent %}` |
|최고 |최고 등급이 포함된 기사 개체의 모음을 반환합니다. `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>필터

다음 필터는 페이지 크기 및 언어에 대한 선택적 항목을 수락할 수 있습니다. 첫 번째 항목은 검색할 숫자 또는 레코드입니다. 기본 페이지 크기는 5입니다. 두 번째 항목은 특정 언어에 대한 기사를 검색하기 위한 언어 코드입니다. 필터는 다른 [유동 필터](liquid-filters.md)와 결합될 수 있습니다.

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|특성|설명|
|---|---|
|인기 |가장 많은 뷰가 포함된 기사 개체의 모음을 반환합니다. `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|최근 |최근 수정일이 포함된 기사 개체의 모음을 반환합니다. `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|최고 |최고 등급이 포함된 기사 개체의 모음을 반환합니다. `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>범주 개체

범주 개체를 사용하여 범주 개체 모음에 액세스할 수 있습니다. 유동 필터를 사용하여 범주의 순서를 정하고 페이지를 매길 수도 있습니다.

```
{% assign category_url = sitemarkers['Category'].url %}
  {% assign count = count | default: 0 %}  
  {% assign categories = knowledge.categories | top_level: count %}
  {% if categories %}
    <div class=list-group unstyled>
    {% for category in categories %}
      <a href={{ category_url | add_query: 'id', category.categorynumber }} class=list-group-item>
        {{ category.title }}
      </a>
    {% endfor %}
    </div>
  {% endif %}
```

### <a name="attributes"></a>특성

|특성|설명|
|---|---|
|최근 |최근 수정일이 포함된 범주 개체의 모음을 반환합니다. |
|top_level |상위 범주가 없는 범주 개체의 모음을 반환합니다. |
|||

### <a name="filters"></a>필터

다음 필터는 페이지 크기를 표시하는 선택적 항목을 수락할 수 있습니다. 기본 페이지 크기는 5입니다. 필터는 다른 [유동 필터](liquid-filters.md)와 결합될 수 있습니다.

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|특성|설명|
|---|---|
|최근 |최근 수정일이 포함된 범주 개체의 모음을 반환합니다. 매개 변수 `{% assign recent_categories = knowledge.categories \| recent: 10 %}`을(를) 제공할 수 있습니다. |
|top_level |상위 범주가 없는 범주 개체의 모음을 반환합니다. `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>기사 개체

기사 개체를 사용하면 단일 참조 자료로 작업하여 포털에서 해당 기사의 세부 사항을 표시할 수 있습니다.

### <a name="attributes"></a>특성

기사는 아래에 나열된 속성 이외에 모두 동일한 속성을 가진 [엔터티](#entity) 개체입니다.

|특성|설명|
|---|---|
|article_public_number| 기사의 공개 번호.|
|comment_count| 특정 기사에 달린 댓글 수의 정수값을 반환합니다.|
|content|기사 내용.|
|current_user_can_comment|현재 사용자가 기사에 대한 코멘트를 추가할 수 있는지의 여부를 나타내는 부울 값을 반환합니다.|
|is_rating_enabled|기사의 등급이 활성화되는지의 여부를 나타내는 부울 값을 반환합니다.|
|키워드|기사의 키워드.|
|이름|기사의 제목에 대한 대체 별칭.|
|등급|기사의 10진수 등급 값.|
|title|문서의 제목입니다.|
|view_count|기사가 열람된 횟수의 정수값.|
|||

### <a name="category-object"></a>범주 개체

범주 개체를 사용하면 단일 범주로 작업하여 포털에서 그 세부 사항을 표시할 수 있습니다.

### <a name="attributes"></a>특성

범주는 아래에 나열된 속성 이외에 모두 동일한 속성을 가진 [엔터티](#entity) 개체입니다.

|특성|설명|
|---|---|
|범주 번호|범주의 번호.|
|이름|범주의 제목에 대한 대체 별칭.|
|title|범주의 제목.|
|||

## <a name="page"></a>페이지

현재 포털 요청 페이지를 참조합니다. 이 개체는 [sitemap](#sitemap)과 현재 요청 [entities](#entities)(일반적으로 웹 페이지)의 특성을 결합합니다.  

페이지 개체는 현재 페이지의 이동 경로, 현재 페이지의 제목 또는 URL, 그리고 기본 PowerApps 레코드의 기타 특성 또는 관련된 엔터티에 대한 액세스를 제공합니다.

```
<ul class=breadcrumb>

{% for crumb in page.breadcrumbs %}

<li><a href={{ crumb.url | escape }}>{{ crumb.title | escape }}</a></li>

{% endfor %}

<li class=active>{{ page.title | escape }}</li>

</ul>

<div class=page-header>

<h1>{{ page.title | escape }}</h1>

</div>

<div class=page-copy>

{{ page.adx_copy }}

</div>

<div class=list-group>

{% for child in page.children %}

<a class=list-group-item href={{ child.url | escape }}>

{{ child.title | escape }}

</a>

{% endfor %}

</div>

<!-- Page {{ page.id }} was last modified on {{ page.modifiedon }}. -->
```

### <a name="page-attributes"></a>페이지 특성

> [!Note]  
> [entities](#entities)

|             특성              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            breadcrumbs             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 사이트 맵 루트 노드에서 시작하여 상위에서 끝나는 페이지에 대한 이동 경로 사이트 맵 노드 개체를 반환합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              children              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 페이지에 대한 하위 사이트 맵 노드 개체를 반환합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               parent               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           페이지에 대한 상위 사이트 맵 노드를 반환합니다. 페이지가 홈 페이지인 경우 상위는 null이 됩니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               title                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                페이지의 제목입니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                url                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 페이지 URL                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[특성 또는 관계 이름\] | 논리 이름으로 페이지의 기본 PowerApps 레코드의 모든 특성에 액세스할 수 있습니다.<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>대부분의 엔터티 특성들의 값은 직접 [유동 유형](liquid-types.md)에 매핑됩니다. 두 옵션 필드는 부울에, 텍스트 필드는 문자열에, 숫자/통화 필드는 숫자에, 날짜/시간 필드는 날짜 개체에 매핑됩니다. 그러나 일부 특성 유형은 다음 개체로 반환됩니다.<ul><li>조회(엔터티 참조) 필드는 [엔터티 참조 개체](#entity-reference)로 반환됩니다.</li><li>옵션 설정/픽리스트 필드는 [옵션 설정값 개체](#option-set-value)로 반환됩니다.</li> 관련된 엔터티를 관계 스키마 이름에 의해서도 로드할 수 있습니다. <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>재귀 관계인 경우(즉, 자체 참조) [entities](#entities) 개체가 반환됩니다. (그렇지 않으면, 결과가 애매모호할 것입니다.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**참고**: 단일 템플릿에서 큰 수의 관련 엔터티를 로드하거나 큰 수의 관계에 액세스하는 것은 템플릿 렌더링 수행에 부정적 영향을 미칠 수 있습니다. 한 루프 내에서 연속으로 각 항목의 관련 엔터티 로드를 피하십시오. 가능하면 엔터티 모음을 로드하기 위해 [PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md)를 사용하는 것이 좋습니다. |

## <a name="polls"></a>polls

설문 조사에 액세스하고 렌더링하는 기능을 제공합니다.

polls 개체를 사용하면 특정 설문 조사 또는 설문 조사 배치를 선택할 수 있습니다.

```
<div>

{% assign poll = polls[Poll Name] %}

<h4>{{ poll.question }}</h4>

{% for option in poll.options %}

<div>

<input type=radio name={{ poll.name }} id={{ option.id }} />

<label for={{ option.id }}>{{ option.answer }}</label>

</div>

{% endfor %}

<button type=button>{{ poll.submit_button_label }}</button>

</div>
```

### <a name="polls-attributes"></a>설문 조사 특성

|특성   |설명   |
|---|---|
| placements          | pollplacements 개체를 반환합니다.                                      |
| \[설문 조사 이름 또는 ID\] | 이름 또는 ID 속성으로 어떤 설문 조사에든 액세스할 수 있습니다. `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>설문 조사 배치 특성

|특성   |설명   |
|---|---|
| \[설문 조사 배치 이름 또는 ID\] | 이름 또는 ID 속성으로 어느 설문 조사 배치에든 액세스할 수 있습니다.`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>설문 조사 배치 특성

> [!Note] 
> [엔터티](#entities)                                       

|특성   |설명   |
|---|---|
| 이름           | 설문 조사 배치를 위한 이름 필드를 반환합니다.                            
| placement\_url | 템플릿으로 완전히 렌더링된 설문 조사 배치를 검색하는 데 사용할 수 있는 URL입니다.                       |
| 설문 조사          | 배치와 관련된 poll 개체의 컬렉션을 반환합니다. [반복 태그](iteration-tags.md) 및 [배열 필터](liquid-filters.md#array-filters)는 이 모음과 함께 사용할 수 있습니다.  |  
| random\_url    | 템플릿으로 완전히 렌더링된 배치에서 무작위 설문을 검색하는 데 사용할 수 있는 URL입니다.         |
| submit\_url    | 완료된 설문이 전송되는 URL입니다.                                                             |

### <a name="poll-attributes"></a>설문 조사 특성

> [!Note] 
> [entities](#entities)                                          

|특성   |설명   |
|---|---|
| has\_user\_voted       | 현재 사용자(로그인했거나 익명)가 이미 이 설문 조사에 투표한 경우 true를 반환합니다.         |
| 이름                   | 설문 조사의 이름 필드를 반환합니다.                                                              |
| options                | 설문 조사와 관련된 설문 조사 옵션 개체의 컬렉션을 반환합니다. [반복 태그](iteration-tags.md) 및 [entities](#entities)는 이 모음과 함께 사용할 수 있습니다.  |  
| poll\_url              | 템플릿으로 완전히 렌더링된 설문 조사를 검색하는 데 사용할 수 있는 URL입니다.                       |
| 질문               | 설문 조사를 위한 질문 필드를 반환합니다.                                                          |
| submit\_button\_label  | 설문 조사를 위한 제출 단추 레이블을 다시 정의하는 데 사용할 수 있는 문자열을 반환합니다.               |
| submit\_url            | 완료된 설문이 전송되는 URL입니다.                                                   |
| user\_selected\_option | (이미 투표한 경우)사용자가 선택한 polloption 개체를 반환합니다.                  |
| votes                  | 설문 조사를 위해 표로 만들어진 투표의 수를 반환합니다.                                |

### <a name="poll-option-attributes"></a>설문 조사 옵션 특성

>[!Note]
> [entities](#entities)                                         

|특성   |설명   |
|---|---|
| answer     | 설문 조사를 위한 답변 필드를 반환합니다. |
| percentage | 옵션에 대한 설문 조사에서 투표의 비율을 0~100의 10진수로 반환합니다. |
| votes      | 옵션을 위해 표로 만들어진 투표의 수를 반환합니다.                              |


## <a name="request"></a>요청

현재 HTTP 요청에 대한 정보가 담겨 있습니다.

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> URL 필터를 이용하여 동적으로 유동 URL을 구축할 수 있습니다. 

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| params           | 현재 요청에 대한 명명된 매개 변수 값입니다. params는 URL 쿼리 연산자 매개 변수, 양식 게시물 매개 변수, 그리고 쿠키의 조합입니다.  |
| 경로             | 현재 요청 URL의 경로입니다. <br> /profile/|
| path\_and\_query | 현재 요청 URL의 경로 및 쿼리입니다.<br> /profile/?foo=1&bar=something|
| 쿼리            | 현재 요청 URL의 쿼리 일부입니다. <br> ?foo=1&bar=something |
| URL              | 현재 요청의 전체 URL입니다.<br>  https://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>색인 검색

searchindex 개체는 [PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md) 내에서 사용되며, 쿼리 결과 접근권을 제공합니다.  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| approximate\_total\_hits | 색인 쿼리에 일치하는 총 적중의 대략 수를 반환합니다. 보안 필터링 및 기타 설계 요인과 관련하여 검색 색인이 작동하는 방식으로 인해, 이 숫자는 대략일 뿐이며 일부 상황에서는 현재 사용자에게 제공되는 결과의 총 수와 정확하게 일치하지 않을 수 있습니다.  |
| 페이지                     | 현재 쿼리의 페이지 수를 반환합니다.                                                                                                                                                                                                           |
| page\_size               | 현재 쿼리의 최대 페이지 크기를 반환합니다. 현재 페이지에 대해 반환된 결과의 실제 수를 보기 원하는 경우(이것이 표시된 최대 페이지 크기보다 작을 수 있으므로) results.size를 사용하십시오.                                                                                           |
| 결과                  | 검색 색인 결과 개체로서의 쿼리 결과 페이지를 반환합니다.                                                                                                                                                                                          |

### <a name="search-index-results"></a>검색 색인 결과

|   특성   |                                                                                                                                                설명                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    엔터티     |                                                                                                                            결과의 기저 [entities](#entities).                                                                                                                            |
|   fragment    | &lt;em&gt; HTML 태그를 사용하여 강조 표시된 지정된 쿼리와 일치하는 조건을 포함한 결과에 대한 관련 짧은 텍스트 조각. 특정 타입의 쿼리는 강조 표시된 조각을 지원하지 않습니다, 예컨대 퍼지 쿼리(~) 및 와일드카드 쿼리(\*). 그러한 경우에 이 속성은 널값입니다. |
|      Id       |                                                             문자열로서의 결과를 위한 기저 레코드의 PowerApps 엔터티 ID. 예: 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| logical\_name |                                                                           결과를 위한 기저 레코드의 PowerApps 엔터티 논리적 이름. 예: adx\_webpage                                                                           |
|    번호     |                                                            모든 결과 페이지에 걸친 결과의 수, 1에서 시작. 예컨대, 페이지 크기가 10인 결과의 두 번째 페이지의 첫 번째 결과의 경우, 이 값은 11입니다.                                                             |
|     score     |                                                                                                 부동점 값으로서의 결과의 루씬 점수. 결과는 이 값 순서로 반환됩니다.                                                                                                 |
|     title     |                                                                                                                                          결과의 제목.                                                                                                                                          |
|      URL      |                                                            결과의 URL. 이는 전체 URL이기 보다는 일반적으로 현재 응용 프로그램의 절대 경로이지만 반드시 그렇지는 않습니다. 예: /articles/article1/                                                             |

## <a name="settings"></a>설정

이름을 사용하여 모든 [사이트 설정](../configure/configure-site-settings.md)을 로드할 수 있습니다. 주어진 이름의 설정을 찾지 못한 경우 [null](liquid-types.md#null) 이 반환됩니다.  

> [!Note]
> 설정은 [문자열](liquid-types.md#string) 유형으로 반환되지만 [유형 필터](liquid-filters.md#type-filters)를 사용하여 다른 유형으로 변환할 수도 있습니다.

```
{{ settings[My Setting] }}

{% assign search_enabled = settings[Search/Enabled] | boolean %}

{% if search_enabled %}

Search is enabled.

{% endif %}

{% assign pagesize = settings['page size'] | integer | default: 10 %}

{% if pagesize > 10 %}

Page size is greater than 10.

{% endif %}
```

> [!Note]
> [웹사이트 머리글 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>sitemap

포털 사이트 맵에 대한 액세스를 허용합니다.

```
<h1>{{ sitemap.root.title }}</h1>

<ul class=breadcrumb>

{% for crumb in sitemap.current.breadcrumbs %}

<li><a href={{ crumb.title }}>{{ crumb.title }}</a></li>

{% endfor %}

<li class=active>{{ sitemap.current.title }}</li>

</ul>

{% for child in sitemap.current.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

It's also possible to load a site map node by URL path:

{% assign node = sitemap[/content/page1/] %}

{% if node %}

{% for child in node.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

{% endif %}
```

### <a name="site-map-attributes"></a>사이트 맵 특성

|특성   |설명   |
|---|---|
| 현재 | 현재 페이지에 대한 사이트 맵 노드 개체를 반환합니다.                    |
| 루트    | 웹 사이트의 루트(홈) 페이지에 대한 사이트 맵 노드 개체를 반환합니다. |

### <a name="site-map-node-attributes"></a>사이트 맵 노드 특성

|특성   |설명   |
|-------|-------|
| 이동 경로           | 사이트 맵 루트 노드에서 시작하여 상위에서 끝나는 노드에 대한 이동 경로 사이트 맵 노드 개체를 반환합니다. |
| 하위              | 노드에 대한 하위 사이트 맵 노드 개체를 반환합니다.                                                                  |
| 설명           | 노드에 대한 설명/요약 내용입니다. (이 필드는 HTML을 포함할 수 있습니다.)                                          |
| 엔터티                | 노드의 기본 [entities](#entities)를 반환합니다. 노드에 기본 엔터티가 없는 경우, 이 값은 null입니다.                                                         |
| is\_sitemap\_ancestor | 사이트 맵 노드가 현재 노드의 상위인 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                         |
| is\_sitemap\_current  | 사이트 맵 노드가 현재 노드인 경우 true를 반환합니다. 그렇지 않은 경우 false를 반환합니다.                                                                                                         |
| 상위                | 노드에 대한 상위 사이트 맵 노드를 반환합니다. 노드가 루트 노드인 경우 상위는 null입니다.                                                                     |
| 직책                 | 노드의 제목입니다.                                                                                                |
| URL                   | 노드의 URL입니다.                                                                                                  |


## <a name="sitemarkers"></a>사이트 마커

이름을 사용하여 모든 사이트 마커를 로드할 수 있습니다. 사이트 마커가 존재하는 경우 사이트 마커 개체가 반환됩니다. 주어진 이름의 사이트 마커를 찾지 못한 경우 [null](liquid-types.md#null) 이 반환됩니다.  

```
{{ sitemarkers[Login].url }}

{% assign my_sitemarker = sitemarkers[My Site Marker] %}

{% if my_sitemarker %}

<a href={{ my_sitemarker.url }}>{{ my_sitemarker.adx_name }}</a>

{% else %}

Site marker My Site Marker does not exist.

{% endif %}
```

> [!Note]
> [웹사이트 머리글 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>사이트 마커 특성

|         특성          |                                                                                    설명                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            URL             |                                                                         사이트 마커 대상의 URL입니다.                                                                         |
| \[특성 논리적 이름\] | 논리 이름을 사요아여 사이트 마커 대상 PowerApps 레코드의 모든 특성에 액세스할 수 있습니다. 예: {{ sitemarker.adx\_name }} |

## <a name="snippets"></a>조각

콘텐츠 조각을 이름에 의해 로드할 수 있습니다. 주어진 이름의 조각이 발견되지 않으면 [null](liquid-types.md#null)이 반환될 것입니다.  

```
{{ snippets[Header] }}

{% assign footer = snippets[Footer] %}

{% if footer %}

{{ footer }}

{% else %}

No footer snippet was found.

{% endif %}
```


## <a name="tablerowloop"></a>tablerowloop

[반복 태그](iteration-tags.md) 루프 블록 내에서 유용하게 사용되는 속성을 포함하고 있습니다.  

> [!Note] 
> tablerowloop는 [반복 태그](iteration-tags.md) 태그 내에서만 사용할 수 있습니다.

### <a name="attributes"></a>특성

|특성   |설명   |
|---|---|
| col        | 1에서 시작하여 현재 행의 색인을 반환합니다.                                                       |
| col0       | 0에서 시작하여 현재 행의 색인을 반환합니다.                                                       |
| col\_first | 현재 열이 행의 첫 번째 열인 경우 true를 반환하고, 그렇지 않은 경우에는 false를 반환합니다.               |
| col\_last  | 현재 열이 행의 마지막 열인 경우 true를 반환하고, 그렇지 않은 경우에는 false를 반환합니다.                |
| 처음      | 루프의 첫 번째 반복인 경우 true를 반환합니다. 첫 번째 반복이 아닌 경우 false를 반환합니다.       |
| 인덱스      | 모음에서 현재 항목의 위치, 이 때 첫 번째 항목은 1의 위치를 갖습니다.                   |
| index0     | 모음에서 현재 항목의 위치, 이 때 첫 번째 항목은 0의 위치를 갖습니다.                   |
| 마지막       | 루프의 마지막 반복인 경우 true를 반환합니다. 마지막 반복이 아닌 경우 false를 반환합니다.         |
| 길이     | 모음에서 반복되고 있는 항목의 수, 즉, 루프에 대한 반복의 수를 반환합니다. |
| rindex     | 루프(길이 - 지수)에 남아 있는 항목의 수, 이 때 1은 마지막 항목의 지수입니다.              |
| rindex0    | 루프(길이 - 지수)에 남아 있는 항목의 수, 이 때 0은 마지막 항목의 지수입니다.              |



## <a name="user"></a>user

현재 포털 사용자를 참조하여 기본 PowerApps 연락처 레코드의 모든 특성에 액세스할 수 있습니다. 로그인한 사용자가 없으면 이 변수는 [null](liquid-types.md#null)입니다.  

사용자가 [엔터티](#entity) 개체입니다.  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>특성

[entity](#entity) 개체의 모든 특성 외에도 user에는 다음과 같은 특성이 있습니다.


|    특성     |                                                                                                                                                                                     설명                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      역할       |                                                      사용자가 속한 역할을 [배열](liquid-types.md#array)로 반환합니다.<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**참고**: `has_role` 필터를 사용하여 개별 역할 구성원 자격을 테스트할 수도 있습니다.                                                       |
| basic_badges_url | 사용자의 배지를 검색하는 서비스 url을 반환합니다.<br>사용자에 대 한 배지를 렌더링하려면 "데이터-배지" 및 "데이터-uri" 특성을 가진 태그를 포함해야 합니다. 현재 사용자의 배지를 렌더링하려면 다음을 수행합니다.<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>id(가변 userid)별로 사용자 배치를 렌더링하려면:<br>\`<div data-badge data-uri='{{user.basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>웹 링크

이름 또는 ID로 모든 웹 링크를 로드할 수 있습니다.  

웹 링크 세트가 존재하는 경우, [웹 링크 세트 개체](#web-link-set-attributes)가 반환될 것입니다. 주어진 이름 또는 ID의 웹 링크 세트가 발견되지 않으면 [null](liquid-types.md#null)이 반환될 것입니다.


```
<!-- Load web link set by ID -->

{{ weblinks[page.adx_navigation.id].name }}

<!-- Load web link set by name -->

{% assign nav = weblinks[Primary Navigation] %}

{% if nav %}

<h1>{{ nav.title | escape }}</h1>

<ul>

{% for link in nav.weblinks %}

<li>

<a href={{ link.url | escape }} title={{ link.tooltip | escape }}>

{% if link.image %}

<img src={{ link.image.url | escape }} alt={{ link.image.alternate_text | escape }} />

{% endif %}

{{ link.name | escape }}

</a>

</li>

{% endfor %}

</ul>

{% endif %}
```

> [!Note]
> [웹 사이트 머리글 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>웹 링크 세트 특성

> [!Note]
> 웹 링크는 아래에 나열된 속성 이외에 모두 동일한 속성을 가진 [엔터티](#entity) 개체입니다.                                         

|         특성          |                                                                                 설명                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            복사            |                                                                      웹 링크 세트의 HTML 사본.                                                                      |
|            이름            |                                                                        웹 링크 세트의 이름.                                                                         |
|           직책            |                                                                        웹 링크 세트의 제목.                                                                        |
|          웹 링크          |                                                       웹 링크 세트와 연계된 웹 링크 개체군.                                                        |
| \[특성 논리적 이름\] | 논리적 이름으로 웹 링크 세트 PowerApps 레코드의 특성에 액세스할 수 있습니다. 예: {{ weblinkset.createdon }} |

### <a name="web-link-attributes"></a>웹 링크 특성

> [!Note]
> 웹 링크는 아래에 나열된 속성 이외에 모두 동일한 속성을 가진 [엔터티](#entity) 개체입니다.

|          특성          |                                                                              설명                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         설명         |                                                                 웹 링크의 HTML 설명.                                                                 |
|    display\_image\_only     |                              웹 링크를 링크 텍스트 없이 이미지로서만 표시해야 하는지의 여부를 나타내는 부울 특성.                               |
| display\_page\_child\_links |            웹 링크가 하위 링크로서의 링크된 페이지의 [*사이트 맵*](#sitemap) 하위 페이지에 대한 링크를 표시해야 하는지의 여부를 나타내는 부울 특성.             |
|            이미지            |                                     이 링크를 위한 웹 링크 이미지 개체. 이미지가 존재하지 않는 경우 이 특성은 널값입니다.                                      |
|        is\_external         |                 웹 링크의 목표 URL이 (내부 포털 페이지에 대한 것이 아닌) 외부 사이트에 대한 것인지의 여부를 나타내는 부울 특성.                  |
|    is\_sitemap\_ancestor    |                                웹 링크의 URL이 현재 사이트 맵 노드의 상위를 참조하는 경우 true를 반환하고, 그렇지 않으면 false를 반환합니다.                                 |
|    is\_sitemap\_current     |                                        웹 링크의 URL이 현재 사이트 맵 노드를 참조하는 경우 true를 반환하고, 그렇지 않으면 false를 반환합니다.                                        |
|            이름             |                                                                    웹 링크의 이름/제목.                                                                    |
|          nofollow           |                                         웹 링크를 rel=nofollow로 표시해야 하는지의 여부를 나타내는 부울 특성.                                         |
|    open\_in\_new\_window    |                             웹 링크를 선택했을 때 새 브라우저 창/탭에서 열지 여부를 나타내는 부울 특성.                             |
|           도구 설명           |                                                                    웹 링크의 툴팁 제목.                                                                     |
|             URL             |                                                                       웹 링크의 URL.                                                                        |
|          웹 링크           |                                                   웹 링크와 연계된 하위 웹 링크 개체군.                                                   |
| \[특성 논리적 이름\]  | 논리적 이름으로 웹 링크 PowerApps 레코드의 특성에 액세스할 수 있습니다. 예: {{ weblink.createdon }} |

### <a name="web-link-image-attributes"></a>웹 링크 이미지 특성

| alternate\_text | 이미지에 대한 대체 텍스트.                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| 높이          | 이미지의 지정된 높이를 포함하는 정수. 높이 값이 제공되지 않은 경우, 이 특성은 널값입니다. |
| URL             | 이미지의 URL.                                                                                               |
| 너비           | 이미지의 지정된 너비를 포함하는 정수. 너비 값이 제공되지 않은 경우, 이 특성은 널값입니다.   |


## <a name="website"></a>웹 사이트

포털 웹 사이트를 참조하여 포털에 대한 PowerApps 웹 사이트(adx\_website) 레코드의 모든 특성에 액세스할 수 있습니다.  

> [!Note]
> 웹 사이트는 동일한 특성을 가진 [엔터티](#entity) 개체입니다.

**코드**

```
{{ website.adx_name }} ({{ website.id }})
```

**출력**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>참조

[유동 유형](liquid-types.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md)  
