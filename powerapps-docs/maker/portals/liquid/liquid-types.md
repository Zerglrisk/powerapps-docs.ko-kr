---
title: 포털에 대한 유동 유형 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 유형에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-types"></a>사용 가능한 유동 유형

유동 개체는 **문자열**, **숫자**, **부울**, **배열**, **사전**, **날짜/시간**, 또는 **Null**의 7가지 기본 형식 중 하나를 반환할 수 있습니다. 유동 변수는 **할당** 또는 **캡처** 태그를 사용하여 초기화할 수 있습니다.

## <a name="string"></a>문자열

문자열은 텍스트를 단일 또는 이중 따옴표 안에 배치하여 선언합니다.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

크기 속성을 가진 문자열의 문자 수를 가져옵니다.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>번호

숫자는 정수 또는 부동 소수점일 수 있습니다.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

부울은 true 또는 false입니다.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>배열

배열은 모든 형식의 값에 대한 목록을 담고 있습니다. \[ \]을(를) 사용하여 (0부터 시작하는) 색인으로 주어진 항목에 액세스하고, **for 태그**를 사용하여 항목들을 반복하고, 크기 속성을 사용하여 배열의 항목 수를 얻을 수 있습니다.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>사전

사전은 문자열 키를 사용하여 액세스할 수 있는 값 모음을 담고 있습니다. \[ \]을(를) 사용하여 문자열 키로 주어진 항목에 액세스하고, **for 태그**를 사용하여 항목들을 반복하고, 크기 속성을 사용하여 사전의 항목 수를 얻을 수 있습니다.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

날짜/시간 개체는 특정 날짜 및 시간을 나타냅니다.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

null은 비어 있거나 존재하지 않는 값을 나타냅니다. null 값에 대한 반환을 시도하면 어떤 출력도 렌더링되지 않습니다. 조건에서 false로 간주됩니다.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>참조

[웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md)  
[유동 연산자의 이해](liquid-operators.md)  
[조건부](liquid-conditional-operators.md)  
[유동 개체](liquid-objects.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md)  