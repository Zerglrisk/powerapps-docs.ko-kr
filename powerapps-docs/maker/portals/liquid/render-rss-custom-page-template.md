---
title: 포털에 대한 사용자 지정 페이지 템플릿을 사용하여 RSS 피드 렌더링 | MicrosoftDocs
description: 사용자 지정 페이지 템플릿을 만들어 RSS 피드를 렌더링하는 데 사용하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>RSS 피드를 렌더링하기 위해 사용자 지정 페이지 템플릿 만들기
이 예에서는 유동 및 웹 템플릿 페이지 템플릿을 사용해서 뉴스 기사의 [RSS 피드](http://en.wikipedia.org/wiki/RSS)를 렌더링하기 위한 사용자 지정 페이지 템플릿을 만듭니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>1단계: 새 PowerApps 보기 만들기

처음으로 피드 데이터를 로드하기 위해 사용할 새 PowerApps 보기를 만듭니다. 이 예에서는 웹 페이지에서 보기를 만들고, 이 엔터티를 사용하여 기사를 저장합니다. 이 보기를 사용해 결과에 대한 분류 및 필터링을 구성하고 유동 템플릿에서 사용할 수 있는 엔터티 특성을 열 형식으로 추가할 수 있습니다.

![페이지 템플릿 편집](../media/edit-page-template.png "페이지 템플릿 편집")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>2단계: RSS 피드에 대한 웹 템플릿 만들기

이 단계에서는 RSS 피드에 대한 웹 템플릿을 만듭니다. 이 템플릿은 웹 사이트의 특정 웹 페이지에 적용됩니다. 따라서 그 페이지의 제목과 요약을 피드의 제목과 설명으로 사용할 것입니다. 그 다음 entityview 태그를 사용하여 새로 생성된 뉴스 기사 보기를 로드합니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md). 웹 템플릿의 **MIME 유형** 필드 또한 application/rss+xml로 설정합니다. 템플릿이 렌더링되었을 때 표시될 응답 콘텐츠 유형을 나타냅니다.  

![RSS 피드에 대한 웹 템플릿 구성](../media/web-template-rss-feed.png "RSS 피드에 대한 웹 템플릿 구성")  

### <a name="rss-feed-web-template"></a>RSS 피드(웹 템플릿)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>3단계: RSS 피드 템플릿을 할당할 페이지 템플릿 만들기

이제 새 페이지 템플릿을 만들어 RSS 피드 템플릿을 웹 사이트의 어느 웹 페이지에든 할당할 수 있습니다. **웹 사이트 머리글 및 바닥글 사용**을 선택 해제하여 피드에 대해 전체 페이지 반응이 렌더링되지 않게 합니다.

![RSS 피드에 대한 페이지 템플릿 구성](../media/page-template-rss-feed.png "RSS 피드에 대한 페이지 템플릿 구성")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>4단계: RSS 피드를 호스팅할 웹 페이지 만들기

이제 남은 것은 RSS 피드 템플릿을 사용하여 새 웹 페이지를 만들어 피드를 호스팅하는 것입니다. 새 웹 페이지를 요청하면 RSS 피드 XML이 나타납니다.

![RSS 피드의 예](../media/rss-feed-example.png "RSS 피드의 예")  

이 예에서는 유동, 웹 템플릿, PowerApps 보기 및 포털 콘텐츠 관리 기능을 통합하여 사용자 지정 RSS 피드를 만드는 방법에 대해 알아보았습니다. 이 기능들을 통합하면 어느 포털 응용 프로그램에든 강력한 사용자 지정 기능을 추가할 수 있습니다.

### <a name="see-also"></a>참조

[유동과 웹 템플릿 페이지 템플릿을 사용하여 사용자 지정 페이지 템플릿을 만드십시오.](create-custom-template.md)  
[현재 페이지와 연관된 엔터티 목록 렌더링](render-entity-list-current-page.md)  
[웹 사이트 머리글 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  
[하이브리드 탐색을 사용하여 최대 3 레벨의 페이지 계층을 렌더링하기](hybrid-navigation-render-page-hierachy.md)  

