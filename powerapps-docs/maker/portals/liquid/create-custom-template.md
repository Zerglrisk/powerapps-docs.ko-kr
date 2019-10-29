---
title: 포털에 대해 액체 및 웹 템플릿 페이지 템플릿을 사용 하 여 사용자 지정 페이지 템플릿 만들기 | MicrosoftDocs
description: 액체 연산자를 사용 하 여 사용자 지정 페이지 템플릿을 만드는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7717bd75fe7149ea3b0af957055975ad10e752ae
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975061"
---
# <a name="create-a-custom-page-template"></a>사용자 지정 페이지 템플릿 만들기

이 예제에서는 웹 템플릿을 기반으로 하는 페이지 템플릿 및 액체를 사용 하 여 사용자 지정 페이지 템플릿을 만듭니다. [웹 템플릿을 사용 하 여 소스 콘텐츠를 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] 저장](store-content-web-templates.md)합니다. 여기서의 목표는 왼쪽 탐색으로 [설정 된 웹 링크](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links) 를 사용 하 고 페이지 내용이 오른쪽에 있는 간단한 두 개의 열로 구성 된 템플릿을 빌드하는 것입니다. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>1 단계: 웹 템플릿 만들기 및 액체 템플릿 코드 작성

먼저 웹 템플릿을 만들고 액체 템플릿 코드를 작성 합니다. 이후 템플릿에서이 템플릿의 몇 가지 공통 요소를 다시 사용할 수 있습니다. 따라서 특정 템플릿을 사용 하 여 확장 하는 일반적인 기본 템플릿을 만듭니다. 기본 템플릿은 한 열 레이아웃을 정의 하는 것은 물론 이동 경로 링크와 페이지 제목/머리글을 제공 합니다.

> [!div class=mx-imgBorder]
![웹 템플릿 1 열 레이아웃](../media/web-template-two-column-layout.png "웹 템플릿 1 열 레이아웃")

> [!TIP]
> 블록 및 확장 태그를 사용 하 여 템플릿 상속에 대 한 자세한 내용은 [템플릿 태그](template-tags.md#extends) 를 참조 하세요.

### <a name="two-column-layout-web-template"></a>두 개의 열 레이아웃 (웹 템플릿)

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>2 단계: 기본 레이아웃 템플릿을 확장 하는 새 웹 템플릿 만들기

현재 페이지와 연결 된 탐색 웹 링크 집합을 사용 하 여 탐색 링크를 통해 기본 레이아웃 템플릿을 확장 하는 새 웹 템플릿을 만들 수 있습니다.

> [!div class=mx-imgBorder]
![웹 템플릿 웹 링크 왼쪽 탐색 레이아웃](../media/web-template-weblinks-left-navigation-layout.png "웹 템플릿 웹 링크 왼쪽 탐색 레이아웃")  

> [!TIP]
> [Weblinks](liquid-objects.md#weblinks) 개체를 사용 하 여 웹 링크 집합을 로드 하는 방법을 숙지 하세요.

### <a name="weblinks-left-navigation-web-template"></a>Weblinks 왼쪽 탐색 (웹 템플릿)

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>3 단계: 웹 템플릿을 기반으로 새 페이지 템플릿 만들기

이 단계에서는 이전 단계에서 만든 웹 템플릿을 기반으로 하는 새 페이지 템플릿을 만듭니다.

> [!div class=mx-imgBorder]
![페이지 템플릿 weblinks 왼쪽 탐색 레이아웃](../media/page-template-weblinks-left-navigation-layout.png "페이지 템플릿 weblinks 왼쪽 탐색 레이아웃")  

## <a name="step-4-create-a-web-page-to-display-content"></a>4 단계: 콘텐츠를 표시 하는 웹 페이지 만들기

이제 페이지 템플릿을 사용 하 고 연결 된 웹 링크 집합을 포함 하는 웹 페이지를 만들고 그 결과를 얻을 수 있습니다.

> [!div class=mx-imgBorder]
왼쪽 탐색 웹 페이지 ![를 사용 하는 웹 페이지 (](../media/web-page-left-navigation.png "왼쪽 탐색") )  

### <a name="see-also"></a>참고 항목

[RSS 피드를 렌더링 하는 사용자 지정 페이지 템플릿 만들기](render-rss-custom-page-template.md)  
[현재 페이지와 연결 된 엔터티 목록을 렌더링 합니다.](render-entity-list-current-page.md)  
[웹 사이트 헤더 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  
[하이브리드 탐색을 사용 하 여 최대 3 수준까지 페이지 계층 구조 렌더링](hybrid-navigation-render-page-hierachy.md)  

