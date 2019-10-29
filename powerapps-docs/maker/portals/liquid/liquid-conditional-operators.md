---
title: 포털에 액체 조건부 연산자 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 액체 조건부 연산자에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975015"
---
# <a name="available-liquid-conditional-operators"></a>사용 가능한 Liquid 조건 연산자

조건문에서 사용 되는**경우**(**제외**) 일부 액체 값은 true로 처리 되 고 일부는 false로 처리 됩니다.

액체에서 null 및 부울 값 false는 false로 처리 되 고 다른 모든 항목은 true로 처리 됩니다. 빈 문자열, 빈 배열 등은 true로 처리 됩니다. 예를 들면

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
필요한 경우 비어 있는 특수 값을 사용 하 여 빈 문자열 및 배열을 테스트할 수 있습니다.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
특수 크기 속성을 사용 하 여 [액체](liquid-types.md)유형, [액체 유형](liquid-types.md)또는 [액체 유형의](liquid-types.md) 크기를 테스트할 수도 있습니다.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>정리

|                           | True | 허위 |
|---------------------------|------|-------|
| True                      | ×    |       |
| 허위                     |      | ×     |
| N                      |      | ×     |
| 문자열                    | ×    |       |
| 빈 문자열              | ×    |       |
| 0                         | ×    |       |
| 1, 3.14                   | ×    |       |
| 배열 또는 사전       | ×    |       |
| 빈 배열 또는 사전 | ×    |       |
| 개체가                    | ×    |       |

### <a name="see-also"></a>참고 항목

[웹 템플릿을 사용 하 여 원본 콘텐츠 저장](store-content-web-templates.md)  
[액체 연산자 이해](liquid-operators.md)  
[액체 유형](liquid-types.md)  
[액체 개체](liquid-objects.md)  
[액체 태그](liquid-tags.md)  
[액체 필터](liquid-filters.md)  
