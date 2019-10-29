---
title: 포털에 대 한 변수 태그 사용 | MicrosoftDocs
description: 포털에서 사용할 수 있는 변수 태그에 대해 알아보기
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974417"
---
# <a name="variable-tags"></a>변수 태그

변수 태그는 새 액체 변수를 만드는 데 사용 됩니다.

## <a name="assign"></a>할당

새 변수를 만듭니다. 또한 할당에서 [필터](liquid-filters.md) 를 사용 하 여 값을 수정할 수 있습니다.  

**Code**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**출력**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>수집

블록 내에서 콘텐츠를 캡처하여 변수에 할당 합니다. 그런 다음 나중에 출력 태그를 사용 하 여이 콘텐츠를 렌더링할 수 있습니다.

**Code**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**출력**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>참고 항목

[제어 흐름 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[템플릿 태그](template-tags.md)<br>
[PowerApps common data service 엔터티 태그](portals-entity-tags.md)
