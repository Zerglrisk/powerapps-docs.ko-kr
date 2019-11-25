---
title: 포털에 대한 가변 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 가변 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707742"
---
# <a name="variable-tags"></a>변수 태그

변수 태그는 새로운 유동 변수를 만들기 위해 사용됩니다.

## <a name="assign"></a>할당

새 변수를 만듭니다. 할당 시 [필터](liquid-filters.md)를 사용하여 값을 수정할 수 있습니다.  

**코드**

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

## <a name="capture"></a>캡처

블록 내의 내용을 캡처하여 이를 변수에 할당합니다. 그러면 이 내용은 추후에 출력 태그를 사용하여 렌더링됩니다.

**코드**

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

### <a name="see-also"></a>참조

[흐름 통제 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[템플릿 태그](template-tags.md)<br>
[PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md)
