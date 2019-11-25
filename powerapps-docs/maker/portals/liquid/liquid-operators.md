---
title: 포털에 대한 유동 연산자 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 연산자에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708182"
---
# <a name="understand-liquid-operators"></a>유동 연산자의 이해

유동은 모든 공통 논리 및 비교 연산자에 액세스할 수 있습니다. 이러한 연산자는 **if** 및 **unless**와 같은 태그에 사용할 수 있습니다.

## <a name="basic-operators"></a>기본 연산자

| ==    | 같음                          |
|-------|---------------------------------|
| !=    | 같지 않음                  |
| &gt;  | 보다 큼                    |
| &lt;  | 보다 작음                       |
| &gt;= | 보다 크거나 같음        |
| &lt;= | 보다 작거나 같음           |
| 또는    | 조건 A **또는** 조건 B  |
| 및   | 조건 A **및** 조건 B |

## <a name="contains"></a>contains

contains는 문자열 내에 하위 문자열이 있는지 테스트합니다.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains는 문자열 배열 내에 문자열이 있는지도 테스트할 수 있습니다.

## <a name="startswith"></a>startswith

startswith는 문자열이 제공된 하위 문자열로 시작하는지 여부를 테스트합니다.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith는 문자열이 제공된 하위 문자열로 끝나는지 여부를 테스트합니다.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>참조

[웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md)  
[유동 유형](liquid-types.md)  
[조건부](liquid-conditional-operators.md)  
[유동 개체](liquid-objects.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md) 