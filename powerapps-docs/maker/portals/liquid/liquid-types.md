---
title: 포털에 액체 유형 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 액체 형식에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974946"
---
# <a name="available-liquid-types"></a>사용 가능한 Liquid 유형

액체 개체는 **문자열**, **숫자**, **부울**, **배열**, **사전**, **DateTime**또는 **Null**의 7 가지 기본 형식 중 하나를 반환할 수 있습니다. **할당** 또는 **캡처** 태그를 사용 하 여 액체 변수를 초기화할 수 있습니다.

## <a name="string"></a>문자열

문자열은 작은따옴표 또는 큰따옴표로 텍스트를 래핑하여 선언 됩니다.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Size 속성을 사용 하 여 문자열의 문자 수를 가져옵니다.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>번호

숫자는 정수 또는 부동 소수점 일 수 있습니다.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>부울

부울은 true 또는 false입니다.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>배열과

배열에는 모든 형식의 값 목록이 포함 됩니다. \[ \]를 사용 하 여 (0부터 시작) 인덱스를 사용 하 여 지정 된 항목에 액세스 하 고 **for 태그**를 사용 하 여 해당 항목을 반복 하 고 size 속성을 사용 하 여 배열의 항목 수를 가져올 수 있습니다.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>사전순

사전은 문자열 키로 액세스할 수 있는 값의 컬렉션을 포함 합니다. \[ \]를 사용 하 여 문자열 키로 지정 된 항목에 액세스 하 고 **for 태그**를 사용 하 여 해당 항목을 반복 하 고 size 속성을 사용 하 여 사전에 있는 항목 수를 가져올 수 있습니다.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

DateTime 개체는 특정 날짜와 시간을 나타냅니다.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>N

Null은 비어 있거나 존재 하지 않는 값을 나타냅니다. Null 값을 반환 하려고 시도 하는 모든 출력은 아무 것도 렌더링 하지 않습니다. 조건에서 false로 처리 됩니다.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>참고 항목

[웹 템플릿을 사용 하 여 원본 콘텐츠 저장](store-content-web-templates.md)  
[액체 연산자 이해](liquid-operators.md)  
[Defined](liquid-conditional-operators.md)  
[액체 개체](liquid-objects.md)  
[액체 태그](liquid-tags.md)  
[액체 필터](liquid-filters.md)  