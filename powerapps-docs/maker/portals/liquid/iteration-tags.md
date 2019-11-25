---
title: 포털에 대한 반복 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 반복 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708402"
---
# <a name="iteration-tags"></a>반복 태그

반복 태그는 반복되는 코드 블록을 실행/렌더링하는 데 사용됩니다.

## <a name="for"></a>for

코드 블록을 반복하여 실행합니다. 배열 또는 사전에 있는 항목을 반복하는 데 가장 일반적으로 사용됩니다.

for 태그 블록 내에서 [forloop 개체](liquid-objects.md#forloop)를 사용할 수 있습니다.  

**코드**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**출력**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>매개 변수

이러한 for 매개 변수는 단독으로 또는 조합하여 사용할 수 있습니다.

**limit**

주어진 개수의 항목 이후에 루프를 종료합니다.

**코드**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**출력**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**offset**

주어진 색인에서 루프를 시작합니다.

**코드**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**출력**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**range**

반복할 숫자의 범위를 정의합니다.

**코드**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**출력**

```
2 3 4

10 11 12 14
```

**reversed**

마지막 항목에서 시작하는 정반대 순서로 루프를 반복합니다.

**코드**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**출력**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>주기

매개 변수로 전달된 순서대로 문자열 그룹을 반복하여 출력합니다. 각 주기를 호출할 때마다 매개 변수로 전달된 다음 문자열이 출력됩니다.

**코드**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**출력**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>tablerow

HTML 테이블을 생성합니다. &lt;table&gt; HTML 태그로 열고 &lt;/table&gt; HTML 태그로 닫아야 합니다.

tablerow 태그 블록 내에서 [tablerowloop](liquid-objects.md#tablerowloop)를 사용할 수 있습니다.  

**코드**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**출력**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>매개 변수

이러한 tablerowcan 매개 변수는 단독으로 또는 조합하여 사용할 수 있습니다.

**출력**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**코드**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

생성된 테이블이 가져야 할 행의 수를 지정합니다.

**cols**

**limit**

주어진 개수의 항목 이후에 루프를 종료합니다.

**코드**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**출력**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

주어진 색인에서 루프를 시작합니다.

**코드**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**출력**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**range**

반복할 숫자의 범위를 정의합니다.

**코드**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>참조

[제어 흐름 태그](control-flow-tags.md)
[변수 태그](variable-tags.md)
[템플릿 태그](template-tags.md)
[PowerApps Common Data Service 엔터티 태그](portals-entity-tags.md)
