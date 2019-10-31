---
title: 포털에 대한 유동 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-tags"></a>사용 가능한 유동 태그

태그는 템플릿에 수행할 작업을 알려 주는 프로그래밍 논리를 만듭니다. 태그는 {% %}로 둘러싸여 사용됩니다.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>공백 제어

일반적으로 유동은 모든 공백을 현재 상태로 그대로 하여 변수 및 태그 블록 공백 밖에 있는 모든 것을 렌더링합니다. 추가 공백을 원하지는 않지만, 공백을 필요로 하는 명확한 템플릿 서식 지정을 해야 하는 경우가 있을 수 있습니다.

이 때에는 하이픈(-)을 시작 또는 끝 블록 태그에 추가하면 모든 선행 또는 후행 공백을 제거하도록 엔진에 지시할 수 있습니다.

**코드**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**출력**

```
12345
```
### <a name="see-also"></a>참조

[유동 유형](liquid-types.md)  
[유동 개체](liquid-objects.md)  
[유동 필터](liquid-filters.md) 
