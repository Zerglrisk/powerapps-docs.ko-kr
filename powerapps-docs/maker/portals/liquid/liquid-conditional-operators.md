---
title: 포털에 대한 조건부 연산자 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 조건부 연산자에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-conditional-operators"></a>사용 가능한 유동 조건부 연산자

조건문(**if**, **unless**)에 사용되는 경우 일부 유동값은 true로 취급되고, 일부는 false로 간주됩니다.

유동값에서 null과 부울값 false는 false로 간주되고, 다른 모든 값은 true로 간주됩니다. 빈 문자열, 빈 배열 등은 true로 간주됩니다. 예를 들어,

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
필요하다면 empty 특수 값을 사용하여 빈 문자열과 배열을 테스트할 수 있습니다.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
특수 크기 속성을 사용하여 [유동 유형](liquid-types.md), [유동 유형](liquid-types.md), 또는 [유동 유형](liquid-types.md)의 ㅣ크기를 데스트할 수도 있습니다.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>요약

|                           | True | False |
|---------------------------|------|-------|
| True                      | ×    |       |
| False                     |      | ×     |
| Null                      |      | ×     |
| 문자열                    | ×    |       |
| 빈 문자열              | ×    |       |
| 0                         | ×    |       |
| 1, 3.14                   | ×    |       |
| 배열 또는 사전       | ×    |       |
| 빈 배열 또는 사전 | ×    |       |
| 개체                    | ×    |       |

### <a name="see-also"></a>참조

[웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md)  
[유동 연산자의 이해](liquid-operators.md)  
[유동 유형](liquid-types.md)  
[유동 개체](liquid-objects.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md)  
