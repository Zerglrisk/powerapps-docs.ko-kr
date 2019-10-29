---
title: 포털에 반복 태그 사용 | MicrosoftDocs
description: 포털에서 사용할 수 있는 반복 태그에 대해 알아보기
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976510"
---
# <a name="iteration-tags"></a>반복 태그

반복 태그는 코드 블록을 반복적으로 실행/렌더링 하는 데 사용 됩니다.

## <a name="for"></a>에 대 한

코드 블록을 반복 해 서 실행 합니다. 배열 또는 사전의 항목을 반복 하는 데 가장 일반적으로 사용 됩니다.

For tag 블록 내에서 [forloop 개체](liquid-objects.md#forloop) 를 사용할 수 있습니다.  

**Code**

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

### <a name="parameters"></a>변수의

의에 대 한 이러한 매개 변수는 단독으로 사용 하거나 조합 하 여 사용할 수 있습니다.

**제한**

지정 된 항목 수 이후에 루프를 종료 합니다.

**Code**

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

**이동**

지정 된 인덱스에서 루프를 시작 합니다.

**Code**

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

**벗어납니다**

반복할 숫자 범위를 정의 합니다.

**Code**

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

**반대**

마지막 항목부터 시작 하 여 역순으로 루프를 반복 합니다.

**Code**

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

## <a name="cycle"></a>순환이

문자열 그룹을 반복 하 고 매개 변수로 전달 된 순서로 출력 합니다. 각 시간 주기를 호출할 때 매개 변수로 전달 된 다음 문자열이 출력 됩니다.

**Code**

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

## <a name="tablerow"></a>system.windows.documents.tablerow>

HTML 테이블을 생성 합니다. 는 여는 &lt;테이블&gt; 하 고 &lt;/table&gt; HTML 태그를 닫는 방법으로 래핑해야 합니다.

System.windows.documents.tablerow> 태그 블록 내에서 [tablerowloop](liquid-objects.md#tablerowloop) 을 사용할 수 있습니다.  

**Code**

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

### <a name="parameters"></a>변수의

이러한 tablerowcan 매개 변수는 단독으로 사용 하거나 조합 하 여 사용할 수 있습니다.

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

**Code**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

생성 된 테이블에 포함 되어야 하는 행 수를 지정 합니다.

**cols.colname**

**제한**

지정 된 항목 수 이후에 루프를 종료 합니다.

**Code**

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

지정 된 인덱스에서 루프를 시작 합니다.

**Code**

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

**벗어납니다**

반복할 숫자 범위를 정의 합니다.

**Code**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>참고 항목

[태그
](variable-tags.md) [제어 흐름 태그](control-flow-tags.md)
[템플릿 태그](template-tags.md)
[PowerApps common data service 엔터티 태그](portals-entity-tags.md)
