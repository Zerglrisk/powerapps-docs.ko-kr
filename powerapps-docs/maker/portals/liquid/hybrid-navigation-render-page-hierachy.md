---
title: 하이브리드 탐색을 사용 하 여 포털에 대 한 페이지 계층 구조 렌더링 | MicrosoftDocs
description: 하이브리드 탐색을 사용 하 여 포털의 페이지 계층을 렌더링 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: aace949be3cc191af5edd95c461e422b9c3217f5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975038"
---
# <a name="render-up-to-three-levels-of-page-hierarchy-by-using-hybrid-navigation"></a>하이브리드 탐색을 사용 하 여 최대 3 수준까지 페이지 계층 구조 렌더링

이 예제에서는 포털 사이트 맵을 기반으로 하는 하이브리드 탐색 유형을 렌더링 하 여 최대 3 개의 페이지 계층 수준을 렌더링 합니다. 이 구성 요소에 대 한 규칙은 다음과 같습니다.

* 현재 페이지의 상위 페이지는 홈 페이지에 다시 표시 되 고, 선택적 깊이\_offset 매개 변수로 지정 된 최대 깊이에 표시 됩니다. 
* 현재 페이지에 자식이 있으면 해당 자식 페이지가 표시 됩니다.
* 현재 페이지에 자식이 없는 경우 현재 페이지의 형제 항목이 표시 됩니다.

```xml
{% assign depth_offset = depth_offset | default: 0 %}
{% assign current_page = current_page | default: page %}
{% assign current_depth = 0 %}

{% if current_page.children.size > 0 %}
  {% assign leaf_page = false %}
{% else %}
  {% assign leaf_page = true %}
{% endif %}

{% capture page_item %}
  <li class=active>
    <a href={{ current_page.url | h }} title={{ current_page.title | h }}>
      {% if leaf_page %}
        <span class=fa fa-fw aria-hidden=true></span>
      {% else %}
        <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
      {% endif %}
      {{ current_page.title | h }}
    </a>
    {% unless leaf_page %}
      <ul>
        {% for child in current_page.children %}
          <li>
            <a href={{ child.url | h }} title={{ child.title | h }}>
              {% if child.children.size > 0 %}
                <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
              {% else %}
                <span class=fa fa-fw aria-hidden=true></span>
              {% endif %}
              {{ child.title | h }}
              {% if child.entity.logical_name == 'adx_shortcut' %}
                &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
              {% elsif child.entity.logical_name == 'adx_webfile' %}
                &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
              {% endif %}
            </a>
          </li>
        {% endfor %}
      </ul>
    {% endunless %}
  </li>
{% endcapture %}

<ul class=side-nav role=navigation>
  {% assign crumb_count = 0 %}
  {% assign leaf_mode = false %}
  
  {% for crumb in current_page.breadcrumbs %}
    {% unless current_depth < depth_offset %}
      {% if forloop.last and leaf_page %}
        {% assign leaf_mode = true %}
      {% else %}
        <li>
          <a href={{ crumb.url | h }} title={{ crumb.title | h }}>
            <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
            {{ crumb.title | h }}
          </a>
        </li>
      {% endif %}
      {% assign crumb_count = crumb_count | plus: 1 %}
    {% endunless %}
    {% assign current_depth = current_depth | plus: 1 %}
  {% endfor %}
  
  {% if crumb_count < 1 %}
    {{ page_item }}
  {% elsif crumb_count < 2 and leaf_mode %}
    {% for parent_sibling in current_page.parent.parent.children %}
      {% if parent_sibling.url == current_page.parent.url %}
        <li>
          <a href={{ current_page.parent.url | h }} title={{ current_page.parent.title | h }}>
            <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
            {{ current_page.parent.title | h }}
          </a>
          <ul>
            {% for sibling in current_page.parent.children %}
              <li {% if sibling.url == current_page.url %}class=active{% endif %}>
                <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                  {% if sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ sibling.title | h }}
                  {% if sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endfor %}
          </ul>
        </li>
      {% else %}
        <li>
          <a href={{ parent_sibling.url | h }} title={{ parent_sibling.title | h }}>
            {% if parent_sibling.children.size > 0 %}
              <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
            {% else %}
              <span class=fa fa-fw aria-hidden=true></span>
            {% endif %}
            {{ parent_sibling.title | h }}
            {% if parent_sibling.entity.logical_name == 'adx_shortcut' %}
              &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
            {% elsif parent_sibling.entity.logical_name == 'adx_webfile' %}
              &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
            {% endif %}
          </a>
        </li>
      {% endif %}
    {% endfor %}
  {% else %}
    <li>
      <ul>
        {% if leaf_mode %}
          {% for parent_sibling in current_page.parent.parent.children %}
            {% if parent_sibling.url == current_page.parent.url %}
              <li>
                <a href={{ current_page.parent.url | h }} title={{ current_page.parent.title | h }}>
                  <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
                  {{ current_page.parent.title | h }}
                </a>
                <ul>
                  {% for sibling in current_page.parent.children %}
                    <li {% if sibling.url == current_page.url %}class=active{% endif %}>
                      <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                        {% if sibling.children.size > 0 %}
                          <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                        {% else %}
                          <span class=fa fa-fw aria-hidden=true></span>
                        {% endif %}
                        {{ sibling.title | h }}
                        {% if sibling.entity.logical_name == 'adx_shortcut' %}
                          &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                        {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                          &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                        {% endif %}
                      </a>
                    </li>
                  {% endfor %}
                </ul>
              </li>
            {% else %}
              <li>
                <a href={{ parent_sibling.url | h }} title={{ parent_sibling.title | h }}>
                  {% if parent_sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ parent_sibling.title | h }}
                  {% if parent_sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif parent_sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endif %}
          {% endfor %}
        {% else %}
          {% for sibling in current_page.parent.children %}
            {% if sibling.url == current_page.url %}
              {{ page_item }}
            {% else %}
              <li>
                <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                  {% if sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ sibling.title | h }}
                  {% if sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endif %}
          {% endfor %}
        {% endif %}
      </ul>
    </li>
  {% endif %}
</ul>

<style type=text/css>
  .side-nav {
    border-right: solid 1px #eee;
  }
  
  .side-nav,
  .side-nav ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .side-nav ul {
    margin-left: 20px;
  }
  
  .side-nav a {
    display: block;
    line-height: 30px;
    overflow: hidden;
    text-decoration: none;
    white-space: nowrap;
  }
  
  .side-nav li > a:hover {
    border-right: solid 1px #23527c;
  }
  
  .side-nav li.active > a,
  .side-nav li.active > a:hover {
    border-right: solid 1px #333;
    color: #333;
    font-weight: bold;
  }
</style>
```
### <a name="see-also"></a>참고 항목

[액체 및 웹 템플릿 페이지 템플릿을 사용 하 여 사용자 지정 페이지 템플릿 만들기](create-custom-template.md)  
[RSS 피드를 렌더링 하는 사용자 지정 페이지 템플릿 만들기](render-rss-custom-page-template.md)  
[현재 페이지와 연결 된 엔터티 목록을 렌더링 합니다.](render-entity-list-current-page.md)  
[웹 사이트 헤더 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  
