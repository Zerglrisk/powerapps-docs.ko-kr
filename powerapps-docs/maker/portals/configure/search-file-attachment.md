---
title: 포털에서 첨부 파일 콘텐츠 내 검색 | MicrosoftDocs
description: 포털에서 파일 첨부 콘텐츠 내에서 검색하도록 포털을 구성하는 방법에 대해 알아봅니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760712"
---
# <a name="search-within-file-attachment-content"></a>첨부 파일 콘텐츠 내에서 검색

메모 첨부 파일을 사용하여 참조 자료 문서에 다운로드 가능한 파일을 포함할 수 있습니다. 웹 파일을 사용하여 다운로드 가능한 콘텐츠가 포함된 FAQ 페이지를 만들 수도 있습니다.

포털 사용자가 참조 자료 문서의 첨부 파일 콘텐츠 내에서 검색할 수 있도록 포털을 구성할 수 있습니다. 이렇게 하면 사용자가 원하는 정보를 찾을 수 있습니다.

참조 자료 문서에서 정의된 접두사를 사용한 메모 첨부 파일이 모두 인덱싱됩니다. 웹 파일에서 최신 메모 첨부 파일이 인덱싱됩니다.

첨부 파일을 인덱싱하려면 다음 사이트 설정을 만들고 해당 값을 **True**로 설정해야 합니다.

|사이트 설정|설명|
|------------|-----------|
|Search/IndexNotesAttachments|참조 자료 문서 및 웹 파일의 메모 첨부 파일이 인덱싱되어야 하는지 여부를 나타냅니다. 기본적으로는 **False**로 설정됩니다.|
|KnowledgeManagement/DisplayNotes|참조 자료 문서의 첨부 파일을 인덱싱할 지 여부를 나타냅니다. 기본적으로는 **False**로 설정됩니다.|
|||

> [!NOTE]
> 참조 문서에 첨부된 파일만 검색할 수 있습니다. 웹 파일에 첨부된 파일은 검색할 수 없습니다.

용어를 검색하면 검색 결과에 첨부 파일도 포함됩니다. 검색 용어가 메모 첨부 파일과 일치하는 경우 해당 참조 자료 문서에 연결되는 링크도 함께 제공됩니다. 다운로드 가능한 첨부 파일을 보려면 왼쪽 창의 **레코드 종류**에서 **다운로드**를 선택합니다. **다운로드** 레이블을 수정하려면 검색/패싯/다운로드 콘텐츠 조각을 편집합니다. 기본적으로 이 값은 **다운로드**로 설정되어 있습니다.

![첨부 파일 다운로드](../media/search-attachment-content.png "첨부 파일 다운로드") 

> [!NOTE]
> - 이 기능을 사용하려면 [관련성 검색을 사용하도록 설정](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization)해야 합니다. 추가 정보: [관련성 검색](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>포탈 구성 업데이트

2018년 4월 이전에 이미 포털을 보유하고 있고 포털을 최신 버전으로 업그레이드한 경우 다음 구성을 사용하여 새 포털 설치와 동일한 사용자 경험을 가져야 합니다.

**내용 조각**

주석 및 웹 파일 다운로드에 대한 검색 결과에 표시되는 레이블을 수정하려면 검색/패싯/다운로드 내용 조각을 만들고 필요에 따라 해당 값을 설정합니다. 기본값은 **다운로드**입니다.

**웹 파일**

이제 웹 파일과 관련된 첨부 파일의 내용을 인덱싱할 수 있습니다. 검색에서 제외할 CSS 파일 및 이미지 파일(예: bootstrap.min.css, theme.css 및 homehero.jpg)에 대한 기존 웹 파일을 업데이트할 수 있습니다. 

1. [포털 관리 앱](configure-portal.md)을 열고 **포털** > **웹 파일**로 이동합니다.
2. 검색에서 제외할 파일을 엽니다.
3. **기타**에서 **검색에서 제외** 필드에서 **예**를 선택합니다.

**웹 템플릿**

패싯 검색 - 결과 템플릿 웹 템플릿이 개정되어 참조 자료 문서와 관련된 파일이 관련 문서 링크와 함께 기본 검색 결과 항목으로 표시됩니다. 패싯 검색 - 결과 템플릿 웹 템플릿 파일을 다음 원본으로 업데이트해야 합니다.

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

검색/쿼리 사이트 설정에 `\_logicalname:annotation~0.9^0.25` 값을 추가해야 합니다. 추가된 후 값은 다음과 같아야 합니다.
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

단일 패싯에서 참조 자료 문서 및 웹 파일과 관련된 주석을 그룹화하도록 패싯을 구성하려면 Search/RecordTypeFacetsEntities 사이트 설정 이름을 편집하고 해당 값에 `;Downloads:annotation,adx_webfile`을 추가합니다.

참조 문서와 관련된 첨부 파일을 포털 및 검색 결과에 표시하려면 **KnowledgeManagement/DisplayNotes** 사이트 설정을 편집하고 해당 값을 **True**로 설정합니다. 사이트 설정 **KnowledgeManagement/NotesFilter**에는 메모의 메모 텍스트 필드에 붙는 접두사 값이 있어야 합니다. 지정된 접두사 값을 가진 메모만 포털에 나타납니다. 기본적으로 이 값은 \*WEB\*이지만 사이트 설정을 통해 변경할 수 있습니다.

메모와 관련된 첨부 파일의 인덱싱을 사용하려면 **Search/IndexNotesAttachments** 사이트 설정을 만들고 그 값을 **True**로 설정합니다.
