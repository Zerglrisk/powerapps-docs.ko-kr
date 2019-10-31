---
title: 포털에 대한 PowerApps Common Data Service 엔터티 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 PowerApps Common Data Service 엔터티 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-common-data-service-entity-tags"></a>PowerApps Common Data Service 엔터티 태그

PowerApps 엔터티 태그는 PowerApps 데이터를 로드하고 표시하는 데 사용되거나 다른 PowerApps 포털 프레임워크 서비스를 사용합니다. 이러한 태그는 유동 언어에 대한 PowerApps 특정 확장입니다.

## <a name="chart"></a>차트

웹 페이지에 PowerApps 차트를 추가합니다. 웹 페이지의 복사 필드 또는 웹 템플릿의 원본 필드에 차트 태그를 추가할 수 있습니다. 웹 페이지에 PowerApps 차트를 추가하는 단계를 보려면 [포털의 웹 페이지에 차트 추가](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/add-chart)를 참조하십시오.

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>매개 변수

차트 태그에는 chart id와 viewid라는 두 가지 매개 변수가 제공됩니다.

**chart id**

차트의 시각화 ID입니다. 차트를 내보내 이를 확인할 수 있습니다.

**viewid**

보기 편집기에서 열 때 엔터티의 ID입니다. 

## <a name="powerbi"></a>powerbi

페이지 내에 Power BI 대시보드 및 보고서를 추가합니다. 웹 페이지의 **복사** 필드 또는 웹 템플릿의 **원본** 필드에 태그를 추가할 수 있습니다. 포털의 웹 페이지에 Power BI 보고서 또는 대시보드를 추가하는 단계는 [포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가](../admin/add-powerbi-report.md)를 참조하십시오.

> [!NOTE]
> 태그가 작동하려면 포털 관리 센터에서 [Power BI 통합 사용](../admin/set-up-power-bi-integration.md)을 설정해야 합니다. Power BI 통합이 활성화되지 않으면 대시보드 또는 보고서가 표시되지 않습니다.

### <a name="parameters"></a>매개 변수

powerbi 태그는 다음 매개 변수를 허용합니다.

**path**

Power BI 보고서 또는 대시보드의 경로. Power BI 보고서 또는 대시보드가 보안인 경우 인증 유형을 제공해야 합니다.

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Power BI 보고서 또는 대시보드에 필요한 인증 유형입니다. 이 매개 변수의 올바른 값:

- **익명**: 웹 Power BI 보고서에 게시를 포함할 수 있습니다. 기본 인증 유형은 익명입니다.

- **AAD**: 보안 Power BI 보고서 또는 대시보드를 Power BI Azure Active Directory 인증된 사용자와 공유할 수 있습니다.

- **powerbiembedded**: 보안 Power BI 보고서 또는 대시 보드를 Power BI 라이선스 또는 Azure Active Directory 인증 설정이 없는 외부 사용자와 공유할 수 있습니다. Power BI Embedded 서비스 설정에 대한 정보는 [Power BI Embedded 서비스 사용](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)을 참조하십시오. 

보안 Power BI 보고서 또는 대시보드를 추가하는 동안 Dynamics 365 포털 Azure Active Directory 또는 Power BI Embedded 서비스와 공유되는지 확인하십시오. 

> [!NOTE]
> `authentication_type` 매개 변수의 값은 대/소문자를 구분하지 않습니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

하나 이상의 값을 기준으로 보고서를 필터링 할 수도 있습니다. 보고서를 필터링하는 구문은 다음과 같습니다.

URL?filter=**Table**/**Field** eq '**value**'

예를 들어, Bert Hair라는 이름의 연락처에 대한 데이터를 보기 위해 보고서를 필터링하려는 경우를 가정해 보겠습니다. URL에 다음을 추가해야 합니다.

?filter=Executives/Executive eq 'Bert Hair'

전체 코드는 다음과 같습니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

보고서를 필터링하는 자세한 정보: [URL에서 쿼리 문자열 매개 변수를 사용하여 보고서 필터링](https://docs.microsoft.com/en-us/power-bi/service-url-filters)

> [!NOTE]
> 익명 보고서는 필터링을 지원하지 않습니다. 

아래와 같이 `capture ` 유동 변수를 사용하여 동적 경로를 만들 수도 있습니다.

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

유동 변수에 대한 자세한 내용: [변수 태그](variable-tags.md)

**tileid**

대시보드의 지정된 타일을 표시합니다. 타일의 ID를 제공해야 합니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**역할**

Power BI보고서에 할당된 역할. 이 매개 변수는 **authentication_type**매개 변수가 **powerbiembedded**로 설정된 경우에만 작동합니다.

Power BI에서 역할을 정의하고 보고서에 할당한 경우 **powerbi** 유동 태그에 적절한 역할을 지정해야 합니다. 역할을 사용하면 보고서에 표시할 데이터를 필터링할 수 있습니다. 여러 역할을 쉼표로 구분하여 지정할 수 있습니다. Power BI에서 역할을 정의하는 방법에 대한 자세한 내용은 [Power BI을 사용한 행 수준 보안(RLS)](https://docs.microsoft.com/en-us/power-bi/service-admin-rls)을 참조하십시오.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Power BI 보고서에 역할을 할당하고 유동 태그에 **역할** 매개 변수를 지정하지 않았거나 매개 변수에 역할을 지정하지 않은 경우 오류가 표시됩니다.

> [!TIP]
> 포털에 정의된 웹 역할을 Power BI 역할로 사용하려면 변수를 정의하고 웹 역할을 할당할 수 있습니다. 그런 다음 유동 태그에서 정의된 변수를 사용할 수 있습니다.
>
> 포털에서 두 개의 웹 역할을 Region_East 및 Region_West로 정의했다고 가정해 보겠습니다. 코드 `{% assign webroles = user.roles | join: ", " %}`를 사용하여 참여할 수 있습니다.
>
> 위의 코드 조각에서 `webroles`은 변수이며 Region_East 및 Region_West 웹 역할이 변수에 저장됩니다.
>
> `webroles` 변수를 유동 태그에서 다음과 같이 사용합니다.
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>편집 가능

해당 개체에 대한 콘텐츠 편집 권한을 가진 사용자를 위해, 제공된 PowerApps 포털 CMS 개체를 포털에서 편집 가능한 개체로 렌더링합니다. 편집 가능한 개체에는 [page](liquid-objects.md#page), [snippets](liquid-objects.md#snippets), [weblinks](liquid-objects.md#weblinks)가 포함됩니다.  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>매개 변수

editable에 제공된 첫 번째 매개 변수가 편집 가능한 개체입니다. 예를 들어, 웹 링크 집합, 조각, 또는 현재 페이지가 될 수 있습니다. 두 번째 옵션 매개 변수는 렌더링하고 편집할 해당 개체 내에서 특성 이름이나 키를 지정하기 위한 것입니다. 엔터티 특성의 이름 또는 조각 이름을 예로 들 수 있습니다.

이러한 초기 매개 변수 뒤에서 태그는 많은 명명된 매개 변수 선택 사항을 지원합니다.

**class**

이 태그로 렌더링된 루트 요소의 class 특성 값을 지정합니다.

**default**

편집 가능 항목에 값이 없는 경우에 렌더링되는 기본값입니다.

**escape**

이 태그로 렌더링된 값이 HTML로 인코딩될지 여부를 나타내는 부울 값입니다. 기본적으로 false입니다.

**liquid**

이 태그로 렌더링된 텍스트 값 내에서 찾은 유동 템플릿 코드가 처리될지 여부를 나타내는 부울 값입니다. 기본적으로 true입니다.

**tag**

이 태그로 렌더링될 컨테이너 HTML 태그의 이름입니다. 이 태그는 기본적으로 div 요소를 렌더링합니다. 일반적으로 이 매개 변수의 값을 div 또는 span 중에서 선택하는 것이 좋습니다.

**title**

콘텐츠 편집 인터페이스에서 이 편집 가능 항목의 레이블을 지정합니다. 아무것도 제공되지 않는 경우, 알기 쉬운 레이블이 자동으로 생성됩니다.

**type**

편집 가능한 텍스트 값의 경우, 표시되는 편집 인터페이스 유형을 나타내는 문자열 값입니다. 이 매개 변수의 유효한 값은 html 또는 텍스트입니다. 기본값은 html입니다.

## <a name="entitylist"></a>entitylist

이름 또는 ID별로 제공된 엔터티 목록을 로드합니다. 엔터티 목록의 속성은 태그 블록 내에서 사용할 수 있는 [entitylist 개체](liquid-objects.md#entitylist)를 사용하여 액세스할 수 있습니다. 엔터티 목록의 실제 결과 레코드를 렌더링하려면 블록 내에서 [entityview](#entityview) 태그를 사용하십시오.  

엔터티 목록이 로드되면 블록 내 콘텐츠가 렌더링됩니다. 엔터티 목록을 찾을 수 없는 경우, 블록 콘텐츠가 렌더링되지 않습니다.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
기본적으로 entitylist 개체에는 변수 이름 entitylist가 제공됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>매개 변수

id, name, 또는 key 중 **하나만** 제공하여 로드할 엔터티 목록을 선택합니다.

**id**

[GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier) ID별로 엔터티 목록을 로드합니다. id는 GUID로 구문 분석 가능한 문자열이어야 합니다.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

일반적으로 리터럴 GUID 문자열은 사용되지 않습니다. 대신, id가 다른 변수의 GUID 속성을 사용하여 지정됩니다.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

이름별로 엔터티 목록을 로드합니다.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

ID **또는** 이름별로 엔터티 목록을 로드합니다. 제공된 된 키 값이 [GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier)로 구문 분석될 수 있는 경우, 엔터티 목록이 ID별로 로드됩니다. 그렇지 않으면 이름별로 로드됩니다.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

로드할 레이블이 지역화되어 있는 엔터티 목록을 선택하기 위한 PowerApps 정수 언어 코드입니다. language\_code가 제공되지 않은 경우, 포털 응용 프로그램 PowerApps 연결의 기본 언어가 사용됩니다.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

이름 또는 ID별로 PowerApps 보기를 로드합니다. 그러면 보기 ߝ열 메타데이터, 페이지를 매긴 결과 레코드 등의 속성은 태그 블록 내에서 사용할 수 있는 [entityview 개체](liquid-objects.md#entityview)를 사용하여 액세스할 수 있습니다.  

보기가 로드되면 블록 내 콘텐츠가 렌더링됩니다. 보기를 찾을 수 없는 경우, 블록 콘텐츠가 렌더링되지 않습니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

기본적으로 entityview 개체에는 변수 이름 entityview가 제공됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

entitylist 블록 내에 entityview가 중첩되는 경우, 엔터티 목록에서 해당 기본 구성(결과 페이지 크기, 필터 옵션 등)을 상속합니다. 보기 id 또는 name 매개 변수가 entityview에 제공되지 않은 경우, 바깥쪽 entitylist에서 기본 보기를 로드합니다.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>매개 변수

**이름과 함께** id **또는** logical\_name을 제공하여 로드할 PowerApps 보기를 선택합니다. 둘 다 제공되지 않고 entityview 태그가 entitylist 태그 내에 중첩된 경우, 바깥쪽 entitylist의 기본 보기가 로드됩니다.

**id**

id는 GUID로 구문 분석 가능한 문자열이어야 합니다.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

일반적으로 리터럴 GUID 문자열은 사용되지 않습니다. 대신, id가 다른 변수의 GUID 속성을 사용하여 지정됩니다.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

로드할 보기의 PowerApps 엔터티 논리 이름입니다. name과 조합하여 사용해야 합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

로드할 보기의 PowerApps 이름입니다. logical\_name과 조합하여 사용해야 합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

결과 보기를 사용자로 필터링할지, 계정으로 필터링할지를 지정합니다. 사용자 또는 계정 문자열 값이 있어야 합니다.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

보기 결과를 필터링하는 엔터티 목록 메타데이터 필터 식을 지정합니다. 이 매개 변수는 entityview가 entitylist와 조합하여 사용될 경우에만 유효합니다. 대부분의 경우 이 매개 변수는 [request](liquid-objects.md#request)를 기반으로 설정됩니다.  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

보기 결과를 순서 지정하기 위한 정렬 식을 지정합니다. 정렬 식에는 하나 이상의 엔터티 특성 논리 이름 뒤에 ASC 또는 DESC의 정렬 방향이 포함될 수 있습니다.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

로드할 보기 결과 페이지를 지정합니다. 이 매개 변수가 지정되지 않으면 결과의 첫 페이지가 로드됩니다.

이 매개 변수는 정수 값 또는 정수로 구문 분석될 수 있는 문자열로 전달되어야 합니다. 이 매개 변수의 값이 제공되지만 값이 null 이거나 달리 정수로 구문 분석할 수 없는 경우, 결과의 첫 페이지가 로드됩니다.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

현재 결과 페이지에 대해 로드할 결과의 수를 지정합니다. 이 매개 변수의 값이 제공되지 않고 [entitylist](#entitylist) 블록 내에서 entityview가 사용될 경우 엔터티 목록 페이지 크기가 사용됩니다. entitylist 블록 내에서 사용되지 않을 경우에는 기본값인 10이 사용됩니다.

이 매개 변수는 정수 값 또는 정수로 구문 분석될 수 있는 문자열로 전달되어야 합니다. 이 매개 변수의 값이 제공되지만 값이 null 이거나 달리 정수로 구문 분석할 수 없는 경우, 기본 페이지 크기가 사용됩니다.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

보기 결과를 필터링하는 검색 식을 지정합니다. 간단한 키워드 검색 식은 특성이 키워드로 시작하는지 여부로 필터링합니다. 와일드카드인 \*도 식에 포함할 수 있습니다.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

일반적인 사용 방법은 사용자 입력에 따라 검색 필터를 설정할 수 있도록 이 매개변수를 [request](liquid-objects.md#request)를 기반으로 설정하는 것입니다.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

보기 결과에 대한 엔터티 권한 필터링 적용 여부를 지정합니다. 기본적으로 이 매개 변수는 false로 설정되어 있습니다. entityview가 entitylist 블록 내에서 사용될 경우, 이 매개 변수의 값은 엔터티 목록 구성에서 상속됩니다.

이 매개 변수는 [boolean](liquid-types.md#boolean) 값 또는 부울(true, false)로 구문 분석될 수 있는 문자열로 전달되어야 합니다. 이 매개 변수의 값이 제공되지만 값이 null 이거나 달리 부울로 구문 분석할 수 없는 경우, 기본값인 false가 사용됩니다.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

로드될 레이블(열 머리글 레이블 등)이 지역화되어 있는 엔터티 보기를 선택하기 위한 PowerApps 정수 언어 코드입니다. language\_code가 제공되지 않은 경우, 포털 응용 프로그램 PowerApps 연결의 기본 언어가 사용됩니다.

entitylist 블록 내에서 entityview가 사용되는 경우 entityview는 entitylist에서 해당 언어 코드 구성을 상속합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>색인 검색

포털 검색 색인에 대해 쿼리를 수행합니다. 그러면 태그 블록 내에서 사용할 수 있는 [searchindex](liquid-objects.md#searchindex)를 사용하여 일치하는 결과에 액세스할 수 있습니다.  

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

기본적으로 검색 색인 개체에는 변수 이름 searchindex가 제공됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>매개 변수

searchindex 태그는 다음 매개 변수를 허용합니다.

**query**

결과 일치에 사용되는 쿼리입니다. 이 매개 변수는 인덱스 쿼리(있는 경우)의 사용자 지정 부분을 수용하기 위한 것입니다.

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

이 매개 변수는 [Lucene 쿼리 파서 구문](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)을 지원합니다.

**filter**

결과 일치에 사용되는 추가 쿼리입니다. 필요한 경우 이 매개 변수는 결과를 위해 개발자 지정 필터를 수용하기 위한 것입니다.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

이 매개 변수는 [Lucene 쿼리 파서 구문](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)을 지원합니다.  

> [!Note]     
> filter와 query의 차이점은 두 가지 모두 Lucene 쿼리 파서 구문을 수용하는 반면, query는 대부분의 최종 사용자가 이 구문을 알 수 없을 것으로 예상될 때 ߝ 이 구문이 구문 분석되는 방법에 대해 유연성이 높다는 것입니다. 따라서 이 구문에 따른 query 구문 분석이 실패할 경우 전체 쿼리가 이스케이프되고 쿼리 텍스트로서 제출됩니다. 반면에 filter는 구문이 잘못된 경우 구문 분석을 엄격하게 수행하여 오류를 반환합니다.

**logical\_names**

쉼표로 구분된 문자열로서, 일치하는 결과를 제한하는 PowerApps 엔터티의 논리 이름입니다. 지정되지 않은 경우에는 일치하는 모든 엔터티가 반환됩니다.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

반환될 검색 결과 페이지입니다. 지정되지 않은 경우에는 첫 번째 페이지(1)가 반환됩니다.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

일반적인 사용 방법은 [request](liquid-objects.md#request)를 기반으로 이 매개 변수를 설정하는 것입니다.  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

반환될 결과 페이지의 크기입니다. 지정되지 않은 경우에는 기본 크기인 10이 사용됩니다.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

이름 또는 ID로 PowerApps 구성 엔터티 양식을 완전히 렌더링합니다.  

> [!Note]
> entityform 태그는 <em>[웹 템플릿](store-content-web-templates.md)</em> 기반 페이지 템플릿 내에 렌더링된 콘텐츠에만 사용할 수 있습니다. 재작성 기반 페이지 템플릿 내의 태그를 사용해도 아무것도 렌더링되지 않습니다. 페이지당 단일 entityform 또는 webform 태그만 렌더링할 수 있습니다. 첫 번째 이후의 entityform 또는 webform 태그는 렌더링되지 않습니다.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>매개 변수

**name**

로드할 엔터티 양식의 이름입니다.

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**webform**

이름 또는 ID로 PowerApps 구성 웹 양식을 완전히 렌더링합니다. webform 태그는 [웹 템플릿](store-content-web-templates.md) 기반 페이지 템플릿 내에 렌더링된 콘텐츠에만 사용할 수 있습니다. 재작성 기반 페이지 템플릿 내의 태그를 사용해도 아무것도 렌더링되지 않습니다. 페이지당 단일 entityform 또는 webform 태그만 렌더링할 수 있습니다. 첫 번째 이후의 entityform 또는 webform 태그는 렌더링되지 않습니다.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>매개 변수

**name**

로드할 웹 양식의 이름입니다.

`{% webform name:My Web Form %}`

### <a name="see-also"></a>참고 항목

[흐름 통제 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[템플릿 태그](template-tags.md)
