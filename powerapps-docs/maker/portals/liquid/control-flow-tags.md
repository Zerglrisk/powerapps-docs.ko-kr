---
title: 포털에 대 한 제어 흐름 태그 사용 | MicrosoftDocs
description: 포털에서 사용할 수 있는 제어 흐름 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975107"
---
# <a name="control-flow-tags"></a>제어 흐름 태그

제어 흐름 태그는 실행할 코드 블록과 지정 된 조건에 따라 렌더링 해야 하는 콘텐츠를 결정 합니다. 조건은 사용 가능한 [액체 연산자](liquid-operators.md)를 사용 하 여 작성 되거나 지정 된 [값의 참 또는 falsehood](liquid-conditional-operators.md)을 기준으로 작성 됩니다.  

## <a name="if"></a>때

지정 된 조건이 충족 되는 경우 코드 블록을 실행 합니다.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>하지 않는 한

If는 지정 된 조건이 충족**되지 않는** 경우 코드 블록을 실행 한다는 점을 제외 하 고는와 같습니다.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

블록에 조건이 추가 되 면이 고, 그렇지 않으면입니다.

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

변수를 서로 다른 값과 비교 하 고 각 값에 대해 다른 코드 블록을 실행 하는 switch 문입니다.

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

### <a name="see-also"></a>참고 항목

[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[템플릿 태그](template-tags.md)<br>
[PowerApps common data service 엔터티 태그](portals-entity-tags.md)
