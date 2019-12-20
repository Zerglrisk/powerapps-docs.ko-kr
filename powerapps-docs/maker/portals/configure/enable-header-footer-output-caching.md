---
title: 포털의 머리글 및 바닥글 출력 캐싱 활성화 | MicrosoftDocs
description: 기존 사용자를 위한 포털 머리글 및 바닥글 출력 캐싱을 활성화하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 705035ef04fd728f9e9e99462b32c62985db2a23
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "2817970"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>포털의 머리글 및 바닥글 출력 캐싱 활성화

포털에서 머리글/바닥글 웹 서식 파일의 처리 성능을 향상시키려면 머리글 및 바닥글 출력 캐싱을 활성화합니다. 페이지가 로드될 때마다 머리글 및 바닥글 웹 템플릿이 구문 분석되고 렌더링됩니다. 머리글 및 바닥글 출력을 캐싱하면 페이지 처리 시간이 크게 줄어듭니다.

새 사용자의 경우 출력 캐싱은 기본적으로 사용됩니다. 이 기능을 지원하기 위해 다음 사이트 설정값을 사용할 수 있으며 기본적으로 true로 설정되어 있습니다:
- 머리글/출력 캐시/활성화: 머리글에 대한 출력 캐싱을 활성화하려면 값을 true로 설정합니다.
- 바닥글/출력 캐시/활성화: 바닥글에 대한 출력 캐싱을 활성화하려면 값을 true로 설정합니다.

포털의 최신 버전으로 업그레이드한 사용자의 경우 출력 캐싱은 기본적으로 비활성화됩니다. 즉, 머리글/바닥글 웹 템플릿은 모든 페이지 로드에서 구문 분석되고 렌더링됩니다. 출력 캐싱을 활성화하려면 머리글, 바닥글 및 언어 드롭다운 웹 템플릿을 업데이트하고 요구되는 사이트 설정값을 만들어야 합니다.

> [!Note]
> 사이트 설정값을 만드는 경우에만 출력 캐싱을 활성화하면 머리글과 바닥글의 일부가 제대로 렌더링되지 않으며 오류 메시지가 표시됩니다.

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>기존 사용자를 위한 머리글 및 바닥글 출력 캐싱 활성화

**단계 1: 머리글 웹 템플릿 업데이트**

1. [포털 관리 앱](configure-portal.md)을 엽니다.
2. **포털** > **웹 템플릿**으로 이동합니다.
3. 머리글 웹 템플릿을 엽니다.
4. **소스** 필드에서 다음을 하십시오:
    - 다음 코드를 찾아 업데이트합니다.
    
        **기존 코드**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **업데이트된 코드**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - 다음 코드를 찾아 업데이트합니다.

        **기존 코드**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **업데이트된 코드**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. 웹 템플릿을 저장합니다.

**단계 2: 바닥글 웹 템플릿 업데이트**

1. [포털 관리 앱](configure-portal.md)을 엽니다.
2. **포털** > **웹 템플릿**으로 이동합니다.
3. 바닥글 웹 템플릿을 엽니다.
4. **소스** 필드에서 다음 코드를 찾아 업데이트합니다.
    
    **기존 코드**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **업데이트된 코드**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. 웹 템플릿을 저장합니다.

**단계 3: 언어 드롭다운 웹 템플릿 업데이트**

1. [포털 관리 앱](configure-portal.md)을 엽니다.
2. **포털** > **웹 템플릿**으로 이동합니다.
3. 언어 드롭다운 웹 템플릿을 엽니다.
4. **소스** 필드에서 다음 코드를 찾아 업데이트합니다.
    
    **기존 코드**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **업데이트된 코드**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. 웹 템플릿을 저장합니다.

**단계 4: 사이트 설정값 만들기**

다음 사이트 설정값을 만듭니다.

|이름|값|
|----|-----|
|머리글/출력 캐시/활성화|True|
|바닥글/출력 캐시/활성화|True|
|||
