---
title: 포털에 대한 유동 및 웹 템플릿 페이지 템플릿을 사용하여 사용자 지정 페이지 템플릿 만들기 | MicrosoftDocs
description: 유동 연산자를 사용하여 사용자 지정 페이지 템플릿을 만드는 방법에 관한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8fe2d6f6496c609a9811ddb4ca28c3df47d8e04d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757407"
---
# <a name="create-a-custom-page-template"></a>사용자 지정 페이지 템플릿 만들기

이 예에서는 유동 및 웹 템플릿을 기반으로 하는 페이지 템플릿을 만듭니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md). 우리의 목표는 [웹 링크 집합](../configure/manage-web-links.md)을 왼쪽에 두어 탐색 기능으로 사용하면서 페이지 콘텐츠가 오른쪽에 표시되는 간단한 2열 템플릿을 빌드하는 것입니다. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>1단계: 웹 템플릿 만들기 및 유동 템플릿 코드 작성

먼저 웹 템플릿을 만들고 유동 템플릿 코드를 작성합니다. 이후의 템플릿에 이 템플릿의 몇 가지 공통 요소를 다시 사용할 것입니다. 따라서 특정 템플릿을 사용하여 확장할 공통 기본 템플릿을 만듭니다. 기본 템플릿은 1열 레이아웃을 정의할 뿐 아니라 이동 경로 링크와 페이지 제목/머리글을 제공합니다.

> [!div class=mx-imgBorder]
![웹 템플릿 1열 레이아웃](../media/web-template-two-column-layout.png "웹 템플릿 1열 레이아웃")

> [!TIP]
> 블록을 사용하는 템플릿 상속대해 읽어 보고 [템플릿 태그](template-tags.md#extends)를 확장합니다.

### <a name="two-column-layout-web-template"></a>두 개의 열 레이아웃(웹 템플릿)

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>2단계: 기본 레이아웃 템플릿을 확장하는 새 웹 템플릿 만들기

탐색 링크의 현재 페이지와 관련된 탐색 웹 링크 집합을 사용하여 기본 레이아웃 템플릿을 확장하는 새 웹 템플릿을 만듭니다.

> [!div class=mx-imgBorder]
![웹 템플릿 웹 링크 왼쪽 탐색 레이아웃](../media/web-template-weblinks-left-navigation-layout.png "웹 템플릿 웹 링크 왼쪽 탐색 레이아웃")  

> [!TIP]
> [웹 링크](liquid-objects.md#weblinks) 개체를 사용하여 웹 링크 집합을 로드하는 방법에 대해 숙지합니다.

### <a name="weblinks-left-navigation-web-template"></a>웹 링크 왼쪽 탐색(웹 템플릿)

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>3단계: 웹 템플릿을 기반으로 하는 새 웹 페이지 템플릿 만들기

이 단계에서는 이전 단계에서 만든 웹 템플릿을 기반으로 하는 새 페이지 템플릿을 만듭니다.

> [!div class=mx-imgBorder]
![페이지 템플릿 웹 링크 왼쪽 탐색 레이아웃](../media/page-template-weblinks-left-navigation-layout.png "페이지 템플릿 웹 링크 왼쪽 탐색 레이아웃")  

## <a name="step-4-create-a-web-page-to-display-content"></a>4단계: 콘텐츠를 표시할 웹 페이지 만들기

이제 남은 일은 페이지 템플릿을 사용하고 관련된 웹 링크 집합이 있는 웹 페이지를 만들어 그 결과를 보는 것입니다.

> [!div class=mx-imgBorder]
![왼쪽 탐색이 있는 웹 페이지](../media/web-page-left-navigation.png "왼쪽 탐색이 있는 웹 페이지")  

### <a name="see-also"></a>참조

[RSS 피드를 렌더링하기 위해 사용자 지정 페이지 템플릿 만들기](render-rss-custom-page-template.md)  
[현재 페이지와 연관된 엔터티 목록 렌더링](render-entity-list-current-page.md)  
[웹 사이트 머리글 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  
[하이브리드 탐색을 사용하여 최대 3 레벨의 페이지 계층을 렌더링하기](hybrid-navigation-render-page-hierachy.md)  

