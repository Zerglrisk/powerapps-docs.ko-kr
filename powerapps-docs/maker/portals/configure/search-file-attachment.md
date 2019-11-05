---
title: 포털에서 파일 첨부 콘텐츠 내에서 검색 | MicrosoftDocs
description: 포털에서 파일 첨부 파일 콘텐츠 내에서 검색 하도록 포털을 구성 하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551649"
---
# <a name="search-within-file-attachment-content"></a>파일 첨부 콘텐츠 내에서 검색

메모 첨부 파일을 사용 하 여 기술 자료 문서에 다운로드 가능한 파일을 포함할 수 있습니다. 웹 파일을 사용 하 여 다운로드 가능한 콘텐츠가 있는 FAQ 페이지를 만들 수도 있습니다.

포털 사용자가 기술 자료 문서의 첨부 파일 콘텐츠 내에서 검색할 수 있도록 포털을 구성할 수 있습니다. 이를 통해 사용자는 원하는 정보를 찾을 수 있습니다.

기술 자료 문서에서 정의 된 접두사를 사용 하는 모든 메모 첨부 파일은 인덱싱됩니다. 웹 파일에서 최신 notes 첨부 파일은 인덱싱됩니다.

첨부 파일을 인덱싱 하려면 다음 사이트 설정을 만들고 해당 값을 **True**로 설정 해야 합니다.

|사이트 설정|설명|
|------------|-----------|
|검색/인덱스 메모 첨부 파일|기술 자료 문서 및 웹 파일에 있는 메모 첨부 파일의 내용을 인덱싱해야 하는지 여부를 나타냅니다. 기본적으로 **False**로 설정 됩니다.|
|KnowledgeManagement/DisplayNotes|기술 자료 문서의 첨부 파일을 인덱싱할 지 여부를 나타냅니다. 기본적으로 **False**로 설정 됩니다.|
|||

> [!NOTE]
> 기술 항목에 첨부 된 파일만 검색할 수 있습니다. 웹 파일에 연결 된 파일은 검색할 수 없습니다.

용어를 검색 하면 검색 결과에 첨부 파일도 포함 됩니다. 검색 단어가 메모 첨부 파일과 일치 하는 경우 해당 기술 자료 문서에 대 한 링크도 제공 됩니다. 다운로드 가능한 첨부 파일을 보려면 왼쪽 창의 **레코드 종류** 에서 **다운로드** 를 선택 합니다. **다운로드** 레이블을 수정 하려면 검색/패싯/다운로드 콘텐츠 조각을 편집 합니다. 기본적으로이 값은 **다운로드**로 설정 됩니다.

![첨부 파일 다운로드](../media/search-attachment-content.png "첨부 파일 다운로드") 

> [!NOTE]
> - 이 기능을 사용 하려면 [관련성 검색을 사용 하도록 설정](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization)해야 합니다. 추가 정보: [관련성 검색](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>포털 구성 업데이트

4 월 2018 이전에 포털이 이미 있고 포털을 최신 버전으로 업그레이드 한 경우에는 다음 구성을 사용 하 여 새 포털 설치와 동일한 사용자 환경을 사용 해야 합니다.

**콘텐츠 조각**

주석 및 웹 파일 다운로드에 대 한 검색 결과에 표시 되는 레이블을 수정 하려면 콘텐츠 조각 검색/패싯/다운로드를 만든 다음 필요에 따라 해당 값을 설정 합니다. 기본값은 **다운로드**입니다.

**웹 파일**

이제 웹 파일과 연결 된 첨부 파일의 콘텐츠를 인덱싱할 수 있습니다. CSS 파일 및 이미지 파일에 대 한 기존 웹 파일 (예: homehero, theme 및)을 검색에서 제외할 수 있도록 업데이트할 수 있습니다. 

1. [포털 관리 앱](configure-portal.md) 을 열고 **포털** > **웹 파일**로 이동 합니다.
2. 검색에서 제외할 파일을 엽니다.
3. **기타**아래의 **검색에서 제외** 필드에서 **예** 를 선택 합니다.

**웹 템플릿**

패싯 검색-결과 템플릿 웹 템플릿은 기술 자료 문서와 관련 된 파일을 관련 문서 링크를 포함 하는 기본 검색 결과 항목으로 표시 하도록 수정 됩니다. 패싯 검색 결과 템플릿 웹 템플릿을 다음 원본으로 업데이트 해야 합니다.

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**사이트 설정**

검색/쿼리 사이트 설정에 `\_logicalname:annotation~0.9^0.25` 값을 추가 해야 합니다. 추가 된 후에는 값이 다음과 같아야 합니다.
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

단일 패싯에서 기술 자료 문서와 웹 파일에 연결 된 주석을 그룹화 하도록 패싯을 구성 하려면 Search/RecordTypeFacetsEntities 사이트 설정 이름을 편집 하 고 `;Downloads:annotation,adx_webfile`를 해당 값에 추가 합니다.

기술 항목과 연결 된 첨부 파일이 포털 및 검색 결과에 표시 되도록 허용 하려면 **KnowledgeManagement/displaynotes** 사이트 설정을 편집 하 고 해당 값을 **True**로 설정 합니다. 사이트 설정 **KnowledgeManagement/메모 필터** 에는 메모의 메모 텍스트 필드 앞에 접두사를 추가 해야 하는 접두사 값이 포함 되어 있습니다. 지정 된 접두사 값을 가진 노트만 포털에 표시 됩니다. 기본적으로이 값은 웹\*\*되지만 사이트 설정을 통해 변경할 수 있습니다.

메모와 연결 된 첨부 파일의 인덱싱을 사용 하도록 설정 하려면 **검색/인덱스 메모 첨부 파일** 사이트 설정을 만들고 해당 값을 **True**로 설정 합니다.
