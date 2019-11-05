---
title: 포털에 대 한 사용자 지정 페이지 템플릿을 사용 하 여 RSS 피드 렌더링 | MicrosoftDocs
description: 사용자 지정 페이지 템플릿을 만들어 RSS 피드를 렌더링 하는 데 사용 하는 지침을 제공 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 240af2f54e153490794358dc1598b72a16fe1c38
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543314"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>RSS 피드를 렌더링 하는 사용자 지정 페이지 템플릿 만들기
이 예제에서는 액체 및 웹 템플릿 페이지 템플릿을 사용 하 여 뉴스 아티클의 [RSS 피드](https://en.wikipedia.org/wiki/RSS) 를 렌더링 하는 사용자 지정 페이지 템플릿을 만듭니다. [웹 템플릿을 사용 하 여 소스 콘텐츠 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] 저장](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>1 단계: 새 PowerApps 보기 만들기

먼저 피드에 대 한 데이터를 로드 하는 데 사용할 새 PowerApps 보기를 만듭니다. 이 예제에서는 웹 페이지에 대 한 보기를 만들고이 엔터티를 사용 하 여 문서를 저장 합니다. 이 뷰를 사용 하 여 결과의 정렬과 필터링을 구성 하 고 액체 템플릿에서 사용할 엔터티 특성을 열로 포함할 수 있습니다.

![페이지 템플릿 편집](../media/edit-page-template.png "페이지 템플릿 편집")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>2 단계: RSS 피드에 대 한 웹 템플릿 만들기

이 단계에서는 RSS 피드에 대 한 웹 템플릿을 만듭니다. 이 템플릿은 웹 사이트의 특정 웹 페이지에 적용 되므로 해당 페이지의 제목과 요약을 피드의 제목 및 설명으로 사용 합니다. 여기서는 entityview 태그를 사용 하 여 새로 만든 뉴스 기사 뷰를 로드 합니다. [PowerApps common data service 엔터티 태그](portals-entity-tags.md)를 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] 합니다. 또한 웹 템플릿의 **MIME 형식** 필드를 application/rss + xml로 설정 합니다. 이는 템플릿이 렌더링 될 때 응답 콘텐츠 형식을 나타냅니다.  

![RSS 피드에 대 한 웹 템플릿 구성](../media/web-template-rss-feed.png "RSS 피드에 대 한 웹 템플릿 구성")  

### <a name="rss-feed-web-template"></a>RSS 피드 (웹 템플릿)

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

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>3 단계: RSS 피드 템플릿을 할당 하는 페이지 템플릿 만들기

이제 새 페이지 템플릿을 만들어 웹 사이트의 웹 페이지에 RSS 피드 템플릿을 할당할 수 있습니다. 피드에 대 한 전체 페이지 응답의 렌더링을 수행 하려는 경우에는 **웹 사이트 헤더 및 바닥글 사용**을 선택 취소 합니다.

![RSS 피드에 대 한 페이지 템플릿 구성](../media/page-template-rss-feed.png "RSS 피드에 대 한 페이지 템플릿 구성")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>4 단계: RSS 피드를 호스트 하는 웹 페이지 만들기

이제 RSS 피드 템플릿을 사용 하 여 피드를 호스팅하는 새 웹 페이지를 만들 수 있습니다. 이 새 웹 페이지를 요청 하면 RSS 피드 XML을 받게 됩니다.

![RSS 피드의 예](../media/rss-feed-example.png "RSS 피드의 예")  

이 예제에서는 액체, 웹 템플릿, PowerApps 보기 및 포털 콘텐츠 관리 기능을 결합 하 여 사용자 지정 RSS 피드를 만드는 방법을 살펴보았습니다. 이러한 기능의 조합은 모든 포털 응용 프로그램에 강력한 사용자 지정 기능을 추가 합니다.

### <a name="see-also"></a>참고 항목

[액체 및 웹 템플릿 페이지 템플릿을 사용 하 여 사용자 지정 페이지 템플릿 만들기](create-custom-template.md)  
[현재 페이지와 연결 된 엔터티 목록을 렌더링 합니다.](render-entity-list-current-page.md)  
[웹 사이트 헤더 및 기본 탐색 모음 렌더링](render-site-header-primary-navigation.md)  
[하이브리드 탐색을 사용 하 여 최대 3 수준까지 페이지 계층 구조 렌더링](hybrid-navigation-render-page-hierachy.md)  

