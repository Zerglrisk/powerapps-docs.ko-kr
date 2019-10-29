---
title: 포털에 액체 연산자 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 액체 연산자에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976533"
---
# <a name="understand-liquid-operators"></a>Liquid 연산자 이해

액체는 모든 공통 논리 및 비교 연산자에 액세스할 수 있습니다. 이러한 **경우** 를 **제외**하 고는와 같은 태그에서 사용할 수 있습니다.

## <a name="basic-operators"></a>기본 연산자

| ==    | 같거나                          |
|-------|---------------------------------|
| !=    | 같지 않음                  |
| &gt;  | 보다 큼                    |
| &lt;  | 보다 작음                       |
| &gt;= | 보다 크거나 같음        |
| &lt;= | 보다 작거나 같음           |
| 또는    | 조건 A **또는** 조건 B  |
| 하거나   | 조건 A **및** 조건 B |

## <a name="contains"></a>에서는

문자열 내에 부분 문자열이 있는지에 대 한 테스트를 포함 합니다.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains는 문자열 배열 내에 문자열이 있는지를 테스트할 수도 있습니다.

## <a name="startswith"></a>startswith

startswith은 문자열이 지정 된 부분 문자열로 시작 하는지 테스트 합니다.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith는 문자열이 지정 된 부분 문자열로 끝나는지 여부를 테스트 합니다.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>참고 항목

[웹 템플릿을 사용 하 여 원본 콘텐츠 저장](store-content-web-templates.md)  
[액체 유형](liquid-types.md)  
[Defined](liquid-conditional-operators.md)  
[액체 개체](liquid-objects.md)  
[액체 태그](liquid-tags.md)  
[액체 필터](liquid-filters.md) 