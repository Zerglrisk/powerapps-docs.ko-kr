---
title: 포털에 대해 PowerApps Common Data Service 엔터티 태그 사용 | MicrosoftDocs
description: 포털에서 사용할 수 있는 PowerApps Common Data Service 엔터티 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e4f59acc86211ae59e52c6f022a712209a45446f
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976464"
---
# <a name="powerapps-common-data-service-entity-tags"></a>PowerApps Common Data Service 엔터티 태그

PowerApps 엔터티 태그는 PowerApps 데이터를 로드 하 고 표시 하거나 다른 PowerApps 포털 프레임 워크 서비스를 사용 하는 데 사용 됩니다. 이러한 태그는 수냉 언어에 대 한 PowerApps 고유의 확장입니다.

## <a name="chart"></a>차트

웹 페이지에 PowerApps 차트를 추가 합니다. 웹 페이지의 복사 필드 또는 웹 템플릿의 원본 필드에 차트 태그를 추가할 수 있습니다. 웹 페이지에 PowerApps 차트를 추가 하는 단계는 [포털에서 웹 페이지에 차트 추가](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/add-chart)를 참조 하세요.

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>변수의

차트 태그와 함께 제공 되는 두 가지 매개 변수는 차트 id 및 viewid입니다.

**차트 id**

차트의 시각화 ID입니다. 차트를 내보내이를 가져올 수 있습니다.

**viewid**

뷰 편집기에서 열 때 엔터티의 ID입니다. 

## <a name="powerbi"></a>powerbi

페이지 내에 Power BI 대시보드 및 보고서를 추가 합니다. 웹 페이지의 **복사** 필드 또는 웹 템플릿의 **원본** 필드에 태그를 추가할 수 있습니다. 포털에서 웹 페이지에 Power BI 보고서 또는 대시보드를 추가 하는 단계는 [포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가](../admin/add-powerbi-report.md)를 참조 하세요.

> [!NOTE]
> 태그가 작동 하려면 PowerApps 포털 관리 센터에서 [Power BI 통합을 사용 하도록 설정](../admin/set-up-power-bi-integration.md) 해야 합니다. Power BI 통합이 사용 하도록 설정 되어 있지 않으면 대시보드 또는 보고서가 표시 되지 않습니다.

### <a name="parameters"></a>변수의

Powerbi 태그는 다음 매개 변수를 허용 합니다.

**path**

Power BI 보고서 또는 대시보드의 경로입니다. Power BI 보고서 또는 대시보드가 안전한 경우 인증 유형을 제공 해야 합니다.

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Power BI 보고서 또는 대시보드에 필요한 인증 유형입니다. 이 매개 변수에 유효한 값은 다음과 같습니다.

- **Anonymous**: 게시를 웹 Power BI 보고서에 포함할 수 있습니다. 기본 인증 유형은 익명입니다.

- **AAD**: Power BI Azure Active Directory 인증 된 사용자에 게 보안 Power BI 보고서 또는 대시보드를 공유할 수 있습니다.

- **powerbiembedded**: Power BI 라이선스 또는 Azure Active Directory 인증 설정이 없는 외부 사용자에 게 보안 Power BI 보고서 또는 대시보드를 공유할 수 있습니다. Power BI Embedded 서비스 설정에 대 한 자세한 내용은 [Power BI Embedded 서비스 사용](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)을 참조 하세요. 

보안 Power BI 보고서 또는 대시보드를 추가 하는 동안 Dynamics 365 포털 Azure Active Directory 또는 Power BI Embedded 서비스와 공유 하는지 확인 합니다. 

> [!NOTE]
> `authentication_type` 매개 변수에 대 한 값은 대/소문자를 구분 하지 않습니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

하나 이상의 값에 대해 보고서를 필터링 할 수도 있습니다. 보고서를 필터링 하는 구문은 다음과 같습니다.

URL? filter =**Table**/**필드** eq '**value**'

예를 들어 보고서를 필터링 하 여 Bert 머리카락 이라는 연락처에 대 한 데이터를 볼 수 있습니다. 다음을 사용 하 여 URL을 추가 해야 합니다.

? filter = 임원/임원 eq ' Bert 헤어 '

전체 코드는 다음과 같습니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

보고서 필터링에 대 한 자세한 내용: [URL에서 쿼리 문자열 매개 변수를 사용 하 여 보고서 필터링](https://docs.microsoft.com/en-us/power-bi/service-url-filters)

> [!NOTE]
> 익명 보고서는 필터링을 지원 하지 않습니다. 

또한 아래와 같이 `capture ` 액체 변수를 사용 하 여 동적 경로를 만들 수 있습니다.

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

액체 변수에 대 한 추가 정보: [변수 태그](variable-tags.md)

**tileid**

대시보드의 지정 된 타일을 표시 합니다. 타일의 ID를 제공 해야 합니다.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**역할**

Power BI 보고서에 할당 된 역할입니다. 이 매개 변수는 **authentication_type** 매개 변수가 **powerbiembedded**로 설정 된 경우에만 작동 합니다.

Power BI에서 역할을 정의 하 고 보고서에 할당 한 경우 **powerbi** 액체 태그에 적절 한 역할을 지정 해야 합니다. 역할을 사용 하면 보고서에 표시할 데이터를 필터링 할 수 있습니다. 쉼표로 구분 된 여러 역할을 지정할 수 있습니다. Power BI에서 역할을 정의 하는 방법에 대 한 자세한 내용은 [Power BI를 사용 하 여 RLS (행 수준 보안)](https://docs.microsoft.com/en-us/power-bi/service-admin-rls)를 참조 하세요.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Power BI 보고서에 역할을 할당 했 고 액체 태그에 **roles** 매개 변수를 지정 하지 않았거나 매개 변수에 역할을 지정 하지 않은 경우 오류가 표시 됩니다.

> [!TIP]
> 포털에 정의 된 웹 역할을 Power BI 역할로 사용 하려는 경우 변수를 정의 하 고 웹 역할을 할당할 수 있습니다. 그런 다음, 액체 태그에 정의 된 변수를 사용할 수 있습니다.
>
> 포털에서 두 개의 웹 역할을 Region_East 및 Region_West로 정의 했다고 가정해 보겠습니다. 코드를 사용 하 여 조인할 수 있습니다. `{% assign webroles = user.roles | join: ", " %}`
>
> 위의 코드 조각에서 `webroles`은 변수이 고 Region_East 및 Region_West 웹 역할은 해당 역할에 저장 됩니다.
>
> 액체 태그에서 다음과 같이 `webroles` 변수를 사용 합니다.
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>수정할

지정 된 PowerApps 포털 CMS 개체를 포털에서 편집할 수 있는 사용자에 대해 해당 개체에 대 한 콘텐츠 편집 권한이 있는 사용자로 렌더링 합니다. 편집 가능한 개체에는 [페이지](liquid-objects.md#page), [코드 조각](liquid-objects.md#snippets)및 [weblinks](liquid-objects.md#weblinks)포함 됩니다.  

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

### <a name="parameters"></a>변수의

편집 가능에 제공 되는 첫 번째 매개 변수는 편집 가능한 개체입니다. 예를 들어 웹 링크 집합, 조각 또는 현재 페이지가 될 수 있습니다. 선택적인 두 번째 매개 변수는 렌더링 및 편집할 해당 개체 내에서 특성 이름이 나 키를 지정 하는 것입니다. 예를 들어 엔터티 특성의 이름 또는 코드 조각 이름일 수 있습니다.

이러한 초기 매개 변수 후 태그는 여러 개의 선택적 명명 된 매개 변수를 지원 합니다.

**클래스**

이 태그에 의해 렌더링 되는 루트 요소의 클래스 특성 값을 지정 합니다.

**기본**

편집 가능한 항목에 값이 없는 경우 렌더링할 기본값입니다.

**이스케이프**

이 태그를 통해 렌더링 되는 값이 HTML로 인코딩 되는지 여부를 나타내는 부울 값입니다. 이는 기본적으로 false입니다.

**liquid**

이 태그에 의해 렌더링 되는 텍스트 값에 있는 액체 템플릿 코드가 처리 되는지 여부를 나타내는 부울 값입니다. 이는 기본적으로 true입니다.

**태그가**

이 태그에 의해 렌더링 되는 컨테이너 HTML 태그의 이름입니다. 이 태그는 기본적으로 div 요소를 렌더링 합니다. 일반적으로 div 또는 span을이 매개 변수에 대 한 값으로 선택 하는 것이 좋습니다.

**제목과**

콘텐츠 편집 인터페이스에서이 편집 가능한 항목의 레이블을 지정 합니다. 제공 된 레이블이 없으면 친숙 한 레이블이 자동으로 생성 됩니다.

**입력할**

편집할 수 있는 텍스트 값에 대해 표시할 편집 인터페이스 유형을 나타내는 문자열 값입니다. 이 매개 변수에 사용할 수 있는 값은 html 또는 텍스트입니다. html이 기본값입니다.

## <a name="entitylist"></a>entitylist

이름 또는 ID를 기준으로 지정 된 엔터티 목록을 로드 합니다. 그런 다음 태그 블록 내에서 사용할 수 있는 [entitylist 개체](liquid-objects.md#entitylist) 를 사용 하 여 엔터티 목록의 속성에 액세스할 수 있습니다. 엔터티 목록의 실제 결과 레코드를 렌더링 하려면 블록 내의 [entityview](#entityview) 태그를 사용 합니다.  

엔터티 목록이 성공적으로 로드 되 면 블록 내의 콘텐츠가 렌더링 됩니다. 엔터티 목록이 없는 경우 블록 콘텐츠가 렌더링 되지 않습니다.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
기본적으로 entitylist 개체에는 이름 entitylist 변수가 지정 됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>변수의

Id, 이름 또는 키 중 **하나만** 지정 하 여 로드할 엔터티 목록을 선택할 수 있습니다.

**a-id**

[GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier) ID로 엔터티 목록을 로드 합니다. id는 GUID로 구문 분석할 수 있는 문자열 이어야 합니다.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

일반적으로 리터럴 GUID 문자열은 사용 되지 않습니다. 대신 다른 변수의 GUID 속성을 사용 하 여 id를 지정 합니다.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**이름의**

이름으로 엔터티 목록을 로드 합니다.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**키인지**

ID **또는** 이름으로 엔터티 목록을 로드 합니다. 제공 된 키 값을 [GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier)로 구문 분석할 수 있으면 엔터티 목록이 ID로 로드 됩니다. 그렇지 않으면 이름으로 로드 됩니다.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**언어\_코드**

로드할 엔터티 목록 지역화 된 레이블을 선택 하는 PowerApps 정수 언어 코드입니다. 언어\_코드를 제공 하지 않으면 포털 응용 프로그램 PowerApps 연결의 기본 언어가 사용 됩니다.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

이름 또는 ID를 기준으로 지정 된 PowerApps 뷰를 로드 합니다. ߝ view 열 메타 데이터, 페이지가 매겨진 결과 레코드 등의 속성은 태그 블록 내에서 사용할 수 있는 [entityview 개체](liquid-objects.md#entityview) 를 사용 하 여 액세스할 수 있습니다.  

뷰가 성공적으로 로드 되 면 블록 내의 내용이 렌더링 됩니다. 뷰를 찾을 수 없는 경우 블록 콘텐츠가 렌더링 되지 않습니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

기본적으로 entityview 개체에는 entityview 변수 이름이 지정 됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Entityview가 entityview 블록 내에 중첩 된 경우 엔터티 목록에서 기본 구성 (결과 페이지 크기, 필터 옵션 등)을 상속 합니다. Entityview에 제공 된 뷰 id 또는 이름 매개 변수가 없는 경우에는 바깥쪽 entityview에서 기본 뷰를 로드 합니다.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>변수의

이름 **에** id **또는** 논리적\_이름을 제공 하 여 로드할 PowerApps 보기를 선택 합니다. 둘 다 제공 되지 않고 entityview 태그가 entityview 태그 내에 중첩 되 면 바깥쪽 entityview의 기본 보기가 로드 됩니다.

**a-id**

id는 GUID로 구문 분석할 수 있는 문자열 이어야 합니다.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

일반적으로 리터럴 GUID 문자열은 사용 되지 않습니다. 대신 다른 변수의 GUID 속성을 사용 하 여 id를 지정 합니다.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**논리적\_이름**

로드할 뷰의 PowerApps 엔터티 논리적 이름입니다. Name과 함께 사용 해야 합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**이름의**

로드할 뷰의 PowerApps 이름입니다. 논리적\_이름과 함께 사용 해야 합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**필터가**

사용자 또는 계정 별로 뷰 결과를 필터링 할지 여부를 지정 합니다. 사용자 또는 계정의 문자열 값이 있어야 합니다.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

뷰 결과를 필터링 할 엔터티 목록 메타 데이터 필터 식을 지정 합니다. 이 매개 변수는 entityview와 entityview를 함께 사용 하는 경우에만 유효 합니다. 대부분의 경우이 매개 변수는 [요청](liquid-objects.md#request)에 따라 설정 됩니다.  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**주문을**

뷰 결과를 정렬 하는 정렬 식을 지정 합니다. 정렬 식에는 하나 이상의 엔터티 특성 논리적 이름과 ASC 또는 DESC의 정렬 방향이 차례로 포함 될 수 있습니다.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**페이지**

로드할 뷰 결과 페이지를 지정 합니다. 이 매개 변수를 지정 하지 않으면 첫 번째 결과 페이지가 로드 됩니다.

이 매개 변수는 정수 값 또는 정수로 구문 분석할 수 있는 문자열을 전달 해야 합니다. 이 매개 변수에 값을 제공 했지만 값이 null 이거나 정수로 구문 분석할 수 없는 경우 결과의 첫 페이지가 로드 됩니다.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**페이지\_크기**

현재 결과 페이지에 대해 로드할 결과 수를 지정 합니다. 이 매개 변수에 대 한 값을 제공 하지 않고 [entityview](#entitylist) 블록 내에서 entityview를 사용 하는 경우 엔터티 목록 페이지 크기가 사용 됩니다. Entitylist 블록 내에 없는 경우 기본값인 10이 사용 됩니다.

이 매개 변수는 정수 값 또는 정수로 구문 분석할 수 있는 문자열을 전달 해야 합니다. 이 매개 변수에 값을 제공 했지만 값이 null 이거나 정수로 구문 분석할 수 없는 경우 기본 페이지 크기가 사용 됩니다.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**조건을**

뷰 결과를 필터링 할 검색 식을 지정 합니다. 단순 키워드 검색 식은 특성이 키워드로 시작 하는지 여부에 따라 필터링 됩니다. 와일드 카드 \* 식에 포함 될 수도 있습니다.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하 여 사용자 입력에 따라 검색 필터를 설정할 수 있도록 하는 것입니다.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**\_엔터티\_사용 권한 사용**

뷰 결과에 대해 엔터티 권한 필터링을 적용할지 여부를 지정 합니다. 이 매개 변수는 기본적으로 false로 설정 됩니다. Entityview 블록 내에서 entityview를 사용 하는 경우이 매개 변수 값은 엔터티 목록 구성에서 상속 됩니다.

이 매개 변수는 [부울](liquid-types.md#boolean) 값 또는 부울 값 (true, false)으로 구문 분석할 수 있는 문자열을 전달 해야 합니다. 이 매개 변수에 값을 제공 했지만 값이 null 이거나 부울로 구문 분석할 수 없는 경우 기본값 false가 사용 됩니다.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**언어\_코드**

로드 될 엔터티 뷰 지역화 된 레이블 (열 머리글 레이블 등)을 선택 하는 PowerApps 정수 언어 코드입니다. 언어\_코드를 제공 하지 않으면 포털 응용 프로그램 PowerApps 연결의 기본 언어가 사용 됩니다.

Entityview를 entityview 블록 내에서 사용 하는 경우 entityview는 entityview의 언어 코드 구성을 상속 합니다.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

포털 검색 인덱스에 대해 쿼리를 수행 합니다. 그런 다음 태그 블록 내에서 사용할 수 있는 [searchindex](liquid-objects.md#searchindex) 를 사용 하 여 일치 결과에 액세스할 수 있습니다.  

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

기본적으로 검색 인덱스 개체에는 변수 이름 searchindex가 지정 됩니다. 필요에 따라 다른 변수 이름을 제공할 수 있습니다.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>변수의

Searchindex 태그는 다음 매개 변수를 허용 합니다.

**쿼리입니다**

결과를 일치 시키는 데 사용 되는 쿼리입니다. 이 매개 변수는 인덱스 쿼리의 사용자 지정 부분 (있는 경우)을 허용 하기 위한 것입니다.

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

이 매개 변수 [는 Lucene 쿼리 파서 구문을](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)지원 합니다.

**필터가**

결과를 일치 시키는 데 사용 되는 추가 쿼리입니다. 이 매개 변수는 원하는 경우 결과에 대해 개발자가 지정한 필터를 수락 하기 위한 것입니다.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

이 매개 변수 [는 Lucene 쿼리 파서 구문을](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)지원 합니다.  

> [!Note]     
> 필터와 쿼리 간의 차이점은 두 가지 모두 Lucene 쿼리 파서 구문을 허용 하는 반면, 쿼리는 대부분의 최종 사용자가이 구문을 인식 하지 못하는 것으로 예상 되는 것 처럼이 구문을 구문 분석 하는 방법에 대 한 정보를 제공 하는 것이 ߝ. 따라서이 구문에 따라 쿼리를 구문 분석 하는 데 실패 하는 경우 전체 쿼리가 이스케이프 되어 쿼리 텍스트로 전송 됩니다. 반면에 필터는 정확 하 게 구문 분석 되 고 구문이 잘못 된 경우 오류를 반환 합니다.

**논리적\_이름**

일치 결과를 제한 하는 PowerApps 엔터티 논리적 이름을 쉼표로 구분 된 문자열로 반환 합니다. 지정 하지 않으면 일치 하는 모든 엔터티가 반환 됩니다.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**페이지**

반환 될 검색 결과 페이지입니다. 지정 하지 않으면 첫 번째 페이지 (1)가 반환 됩니다.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

일반적인 사용 사례는 [요청](liquid-objects.md#request)에 따라이 매개 변수를 설정 하는 것입니다.  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**페이지\_크기**

반환할 결과 페이지의 크기입니다. 제공 하지 않으면 기본 크기인 10이 사용 됩니다.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

PowerApps에서 구성 된 엔터티 양식, 이름 또는 ID를 완전히 렌더링 합니다.  

> [!Note]
> Entityform 태그는  <em>[웹 템플릿](store-content-web-templates.md)</em>기반 페이지 템플릿 내에서 렌더링 된 콘텐츠에서 사용할 수 있습니다. 재작성 기반 페이지 템플릿 내에서 태그를 사용 하려고 하면 아무것도 렌더링 되지 않습니다. 페이지당 단일 entityform 또는 webform 태그를 렌더링할 수 있습니다. 첫 번째 뒤의 entityform 또는 webform 태그는 렌더링 되지 않습니다.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>변수의

**이름의**

로드 하려는 엔터티 형식의 이름입니다.

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**webform**

PowerApps에서 구성 된 web form을 이름 또는 ID 별로 완전히 렌더링 합니다. Webform 태그는 [웹 템플릿](store-content-web-templates.md) 기반 페이지 템플릿 내에서 렌더링 된 콘텐츠에서 사용할 수 있습니다. 재작성 기반 페이지 템플릿 내에서 태그를 사용 하려고 하면 아무것도 렌더링 되지 않습니다. 페이지당 단일 entityform 또는 webform 태그를 렌더링할 수 있습니다. 첫 번째 뒤의 entityform 또는 webform 태그는 렌더링 되지 않습니다.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>변수의

**이름의**

로드 하려는 웹 폼의 이름입니다.

`{% webform name:My Web Form %}`

### <a name="see-also"></a>참고 항목

[제어 흐름 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[템플릿 태그](template-tags.md)
