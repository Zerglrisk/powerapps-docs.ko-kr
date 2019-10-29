---
title: 포털에 액체 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 액체 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976556"
---
# <a name="available-liquid-tags"></a>사용 가능한 Liquid 태그

태그는 템플릿을 통해 수행할 작업을 알려주는 프로그래밍 논리를 구성 합니다. 태그가 {%%}에 래핑됩니다.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>공백 컨트롤

일반적으로 액체는 모든 공백을 있는 그대로 사용 하 여 변수 및 태그 블록의 외부에 있는 모든 것을 렌더링 합니다. 경우에 따라 불필요 한 공백을 원하지는 않지만 공백으로 서식 지정 하는 것이 좋습니다.

Start 또는 end 블록 태그에 하이픈 (-)을 추가 하 여 모든 선행 또는 후행 공백을 제거 하도록 엔진에 지시할 수 있습니다.

**Code**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**출력**

```
12345
```
### <a name="see-also"></a>참고 항목

[액체 유형](liquid-types.md)  
[액체 개체](liquid-objects.md)  
[액체 필터](liquid-filters.md) 
