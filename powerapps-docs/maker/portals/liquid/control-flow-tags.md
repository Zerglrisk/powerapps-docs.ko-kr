---
title: 포털에 대한 제어 흐름 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 제어 흐름 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8f5b3701aedc0e0e98d203d5048577647c276120
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864773"
---
# <a name="control-flow-tags"></a>흐름 통제 태그

제어 흐름 태그는 주어진 조건에 따라 실행해야 할 코드의 블록과 렌더링할 콘텐츠를 결정합니다. 조건은 사용 가능한 [유동 연산자](liquid-operators.md)를 사용하여, 또는 단지 [주어진 값의 진실 또는 허위](liquid-conditional-operators.md)에 따라 구축됩니다.  

## <a name="if"></a>if

주어진 조건이 충족되면 코드 블록을 실행합니다.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

if처럼, 주어진 조건이 충족되지 **않으면** 코드 블록을 실행하는 경우를 제외.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

if 또는 unless 블록에 더 많은 조건을 추가합니다.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

변수를 다른 값들과 비교하여 각 값에 대해 다른 블록의 코드를 실행시키는 전환 명령.

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>참조

[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[템플릿 태그](template-tags.md)<br>
[Power Apps Common Data Service 엔터티 태그](portals-entity-tags.md)
