---
title: 포털에 대한 유동 필터 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 유동 필터에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 996b31766641376e9a01cbefc876f3eb2b7aabc7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757275"
---
# <a name="available-liquid-filters"></a>사용 가능한 유동 필터

유동 필터는 문자열, 숫자, 변수 및 개체의 출력을 수정하는 데 사용됩니다. 이 필터는 |에 의해 적용되는 값에서 분리됩니다.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

일부 필터는 매개 변수를 허용합니다. 또한 필터는 조합이 가능하며 왼쪽에서 오른쪽 순서로 적용됩니다.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
아래 섹션에서는 다양한 필터에 대해 설명합니다. 

## <a name="array-filters"></a>배열 필터

배열 필터는 [배열](liquid-types.md#array)에 대한 작업을 수행하기 위해 사용됩니다.  

### <a name="batch"></a>batch

배열을 주어진 크기의 여러 배열로 나눕니다.

**코드**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**출력**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>concat

두 배열을 새 단일 배열로 연결합니다.

단일 항목이 매개 변수로 주어졌을 때 concat은 주어진 항목을 마지막 요소로 하는 원본 배열로 구성된 새 배열을 반환합니다.

**코드**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**출력**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>except

주어진 특성이 주어진 값을 가지지 않는 배열의 모든 개체를 선택합니다. (**where**의 반대 필터입니다.)

**코드**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**출력**

```
Jack Robinson
```

### <a name="first"></a>첫째

배열의 첫 요소를 반환합니다.

first는 태그 안에 사용되어야 하는 경우 특수 점 표기법으로 사용할 수도 있습니다.

**코드**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**출력**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

배열의 항목을 주어진 특성으로 그룹화합니다.

**코드**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**출력**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>join

매개 변수로 전달된 문자를 가진 배열의 요소들을 결합합니다. 결과는 단일 문자열입니다.

**코드**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**출력**

```
This, is, a, run, of, text
```

### <a name="last"></a>마지막

배열의 마지막 요소를 반환합니다.

last는 태그 안에 사용되어야 하는 경우 특수 점 표기법으로 사용할 수도 있습니다.

**코드**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**출력**

```
text

The last word is text.
```

### <a name="order_by"></a>order\_by

배열의 요소들의 주어진 특성 순으로 정렬된 배열의 요소를 반환합니다.

선택적으로 desc를 두 번째 매개 변수로 제공하여 오름차순이 아닌 내림차순으로 요소를 정렬할 수 있습니다.

**코드**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**출력**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random

배열에서 임의로 선택된 단일 항목을 반환합니다.

**코드**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**출력**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select

배열의 각 항목에 대해 주어진 특성의 값을 선택하여 이 값을 배열로 반환합니다.

**코드**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**출력**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle

배열에 적용되며, 임의의 순서대로 같은 항목에 대한 새 배열을 반환합니다.

**코드**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**출력**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size

배열의 항목 수를 반환합니다.

size는 태그 안에 사용되어야 하는 경우 특수 점 표기법으로 사용할 수도 있습니다.

**코드**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**출력**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

배열에서 주어진 수의 항목을 건너뛴 나머지를 반환합니다.

**코드**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**출력**

```
run, of, text
```

### <a name="take"></a>take

주어진 수의 항목을 배열에서 가져와서 반환합니다.

**코드**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**출력**

```

This, is, a
```

### <a name="then_by"></a>then\_by

**order\_by**로 이미 정렬된 배열에 정렬을 추가합니다.

선택적으로 desc를 두 번째 매개 변수로 제공하여 오름차순이 아닌 내림차순으로 요소를 정렬할 수 있습니다.

**코드**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**출력**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>where

주어진 특성이 주어진 값을 가진 배열의 모든 개체를 선택합니다.

**코드**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**출력**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>날짜 필터

날짜 필터는 날짜를 산술하거나 여러 형식으로 날짜/시간 값을 변환하는 데 사용할 수 있습니다.

### <a name="date"></a>날짜

.NET 형식 문자열을 사용하여 날짜/시간 값의 형식을 설정합니다.

[표준 날짜 및 시간 형식 문자열](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[사용자 지정 날짜 및 시간 형식 문자열](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**코드**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**출력**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>date\_add\_days

전체 또는 일부 날짜에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**출력**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>date\_add\_hours

전체 또는 일부 시간에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**출력**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>date\_add\_minutes

전체 또는 일부 분에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**출력**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>date\_add\_months

전체 달에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**출력**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>date\_add\_seconds

전체 또는 일부 초에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**출력**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>date\_add\_years

전체 연도에 대해 지정된 수를 날짜/시간 값에 추가합니다. 매개 변수는 양수이거나 음수일 수 있습니다.

**코드**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**출력**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>date\_to\_iso8601

[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) 표준에 따라 날짜/시간 값의 형식을 지정합니다. [*Atom 피드*](https://tools.ietf.org/html/rfc4287) 또는 HTML5 &lt;time&gt; 요소를 만들 때 유용합니다.  

**코드**

```
{{ now | date_to_iso8601 }}
```

**출력**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

[RFC 822](https://www.ietf.org/rfc/rfc0822.txt) 표준에 따라 날짜/시간 값의 형식을 지정합니다. [*RSS 피드*](https://cyber.law.harvard.edu/rss/rss.html)를 만들 때 유용합니다.  

**코드**

```
{{ now | date_to_rfc822 }}
```

**출력**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>엔터티 목록 필터

엔터티 목록 필터는 특정 [entitylist](liquid-objects.md#entitylist) 특성 값으로 작업하기 위해 그리고 엔터티 목록 보기를 생성하기 위해 사용됩니다.  

### <a name="current_sort"></a>current\_sort

정렬 식이 주어지면 주어진 특성에 대한 현재의 정렬 방향을 반환합니다.

**코드**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**출력**

```
DESC
```

### <a name="metafilters"></a>metafilters

[entitylist](liquid-objects.md#entitylist) filter\_definition JSON 값을 필터 옵션 그룹 개체로 구문 분석합니다.  

현재의 특성 필터 쿼리 및 현재의 [entitylist](liquid-objects.md#entitylist)와 함께 metafilters를 제공하여, 반환된 필터 개체에 선택 또는 선택 해제로 플래그 표시할 수 있습니다.

**코드**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>reverse\_sort

정렬 방향이 주어지면 반대 정렬 방향을 반환합니다.

**코드**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**출력**

```
DESC

ASC
```


## <a name="math-filters"></a>수학 필터

수학 필터를 사용하면 [numbers](liquid-types.md#number)에 대해 수학 연산을 수행할 수 있습니다.  

다른 모든 필터와 마찬가지로, 수학 필터는 연결이 가능하며 왼쪽에서 오른쪽 순서로 적용됩니다.

**코드**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**출력**

```
5
```

### <a name="ceil"></a>ceil

값을 가장 가까운 정수로 반올림합니다.

**코드**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**출력**

```
5

5
```

### <a name="divided_by"></a>divided\_by

숫자를 다른 숫자로 나눕니다.

**코드**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**출력**

```
5

3

3.333333
```

### <a name="floor"></a>floor

값을 가장 가까운 정수로 반내림합니다.

**코드**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**출력**

```
4

4
```

### <a name="minus"></a>minus

숫자에서 다른 숫자를 뺍니다.

**코드**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**출력**

```
10

9

9.1
```

### <a name="modulo"></a>modulo

숫자를 다른 숫자로 나누고 나머지를 반환합니다.

**코드**

```
{{ 12 | modulo: 5 }}
```

**출력**

```
2
```

### <a name="plus"></a>plus

숫자를 다른 숫자에 추가합니다.

**코드**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**출력**

```
12

11

11.1
```

### <a name="round"></a>round

값을 가장 가까운 정수나 지정된 소수 자릿수로 반올림합니다.

**코드**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**출력**

```
5

4

4.56
```

### <a name="times"></a>times

숫자에 다른 숫자를 곱합니다.

**코드**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**출력**

```
20

20

20.2
```


## <a name="string-filters"></a>문자열 필터

[strings](liquid-types.md#string)를 조작하는 문자열 필터입니다.  

### <a name="append"></a>추가

문자열을 다른 문자열의 끝에 추가합니다.

**코드**

```
{{ 'filename' | append: '.js' }}
```

**출력**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

문자열의 첫 글자를 대문자로 시작합니다.

**코드**

```
{{ 'capitalize me' | capitalize }}
```

**출력**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

문자열을 소문자로 변환합니다.

**코드**

```
{{ 'MIxed Case TExt' | downcase }}
```

**출력**

```
mixed case text
```

### <a name="escape"></a>**escape**

문자열을 HTML-이스케이프합니다.

**코드**

```
{{ '<p>test</p>' | escape }}
```

**출력**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

문자열에서 각 줄 바꿈 위치에 &lt;br /&gt; 줄 바꿈 HTML 태그를 삽입합니다.

**코드**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**출력**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**prepend**

문자열을 다른 문자열의 앞에 추가합니다.

**코드**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**출력**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

문자열에서 모든 부분 문자열을 제거합니다.

**코드**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**출력**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

문자열에서 첫 부분 문자열을 제거합니다.

**코드**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**출력**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

모든 문자열을 부분 문자열로 바꿉니다.

**코드**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**출력**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

첫 문자열을 부분 문자열로 바꿉니다.

**코드**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**출력**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

부문 문자열에 매개 변수로 작용하는 split 필터입니다. 부분 문자열은 문자열을 배열로 나누는 구분 기호로서 사용됩니다.

**코드**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**출력**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**strip\_html**

문자열에서 모든 HTML 태그를 제거합니다.

**코드**

```
<p>Hello</p>
```

**출력**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

문자열에서 모든 줄 바꿈을 제거합니다.

**코드**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**출력**

```
ABC
```

### <a name="text_to_html"></a>**text\_to\_html**

일반 텍스트 문자열을 단순 HTML 형식으로 설정합니다. 모든 텍스트는 HTML로 인코딩되고, 줄 공백으로 구분된 텍스트 블록은 문단 내에 &lt;p&gt; 태그로 줄 바꿈되며, 단일 줄 바꿈은 &lt;br&gt;로 교체되고, URL은 하이퍼링크로 변환됩니다.

**코드**

```
{{ note.notetext | text_to_html }}
```

**출력**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

주어진 문자 수로 문자열을 자릅니다. 줄임표(...)가 문자열에 추가되고 문자 수에 포함됩니다.

**코드**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**출력**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

주어진 단어 수로 문자열을 자릅니다. 줄임표(...)가 잘린 문자열에 추가됩니다.

**코드**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**출력**

```
This is a...
```

### <a name="upcase"></a>**upcase**

문자열을 대문자로 변환합니다.

**코드**

```
{{ 'MIxed Case TExt' | upcase }}
```

**출력**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

URL에 포함하기 위해 문자열을 URI-이스케이프합니다.

**코드**

```
{{ 'This & that//' | url_escape }}
```

**출력**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

XML 출력에 포함하기 위해 문자열을 XML-이스케이프합니다.

**코드**

```
{{ '<p>test</p>' | xml_escape }}
```

**출력**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>타입 필터

타입 필터를 통해 한 타입의 값을 다른 타입으로 전환할 수 있습니다.

### <a name="boolean"></a>**boolean**

문자열 값을 부울 값으로 전환 시도. 값이 이미 부울 값인 경우에는 바뀌지 않고 반환됩니다. 값을 부울 값으로 전환할 수 없는 경우에는 null이 반환됩니다.

이 필터는 또한 켜짐, 활성화, 또는 예를 true로, 꺼짐, 비활성화, 및 아니요를 false로 수락할 것입니다.

**코드**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**출력**

```
true

false

true

false
```

### <a name="decimal"></a>**decimal**

문자열 값을 10진수로 전환 시도. 값이 이미 10진수인 경우에는 바뀌지 않고 반환됩니다. 값을 10진수로 전환할 수 없는 경우에는 null이 반환됩니다.

**코드**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**출력**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**integer**

문자열 값을 정수로 전환 시도. 값이 이미 정수인 경우에는 바뀌지 않고 반환됩니다. 값을 정수로 전환할 수 없는 경우에는 null이 반환됩니다.

**코드**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**출력**

```
10

10


2
```

### <a name="string"></a>**string**

값을 문자열 표현으로 전환 시도. 값이 이미 문자열인 경우에는 바뀌지 않고 반환됩니다. 값이 null인 경우에는 null이 반환됩니다.



## <a name="url-filters"></a>URL 필터

URL 필터를 사용하면 URL의 일부를 빌드 또는 추출할 수 있습니다.

### <a name="add_query"></a>**add\_query**

URL에 쿼리 문자열 매개 변수를 추가합니다. 매개 변수가 이미 URL에 존재할 경우, 매개 변수 값이 업데이트됩니다.

이 필터가 전체 절대 URL에 적용된 경우, 업데이트된 절대 URL이 결과값이 됩니다. 경로에 적용된 경우, 업데이트된 경로가 결과값이 됩니다.

**코드**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**출력**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

주어진 URL의 기본 URL을 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**출력**

```
https://example.com
```

### <a name="host"></a>**host**

URL의 호스트 부분을 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**출력**

```
example.com
```

### <a name="path"></a>**path**

URL의 경로 부분을 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**출력**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

URL의 경로 및 쿼리 부분을 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**출력**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

URL의 포트 번호를 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**출력**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

URL에서 쿼리 문자열 매개 변수를 제거합니다. 매개 변수가 URL에 존재하지 않는 경우, URL이 변경되지 않은 상태로 반환됩니다.

이 필터가 전체 절대 URL에 적용된 경우, 업데이트된 절대 URL이 결과값이 됩니다. 경로에 적용된 경우, 업데이트된 경로가 결과값이 됩니다.

**코드**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**출력**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

URL의 스키마 부분을 가져옵니다.

**코드**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**출력**

```
http

https
```


## <a name="additional-filters"></a>추가 필터

이러한 필터는 유용한 일반 기능을 제공합니다.

### <a name="default"></a>**default**

할당된 값이 없는 모든 변수에 대해 기본값을 반환합니다(예: null).

**코드**

```
{{ snippets[Header] | default: 'My Website' }}
```

**출력**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

바이트 수를 나타내는 숫자 값에 적용되어, 적절한 크기의 형식이 지정된 파일 크기를 반환합니다.

필요에 따라 정밀도 매개 변수는 결과의 소수 자릿수를 제어하기 위해 전달될 수 있습니다. 기본 자릿수는 1입니다.

**코드**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**출력**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**has\_role**

[user](liquid-objects.md#user)에 적용되며, 사용자가 주어진 역할에 속한 경우 true를 반환합니다. 그렇지 않으면 false를 반환합니다.  

**코드**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

유동 코드로서 문자열을 렌더링합니다. 이 코드는 현재 유동 실행 컨텍스트(변수 등)에 액세스할 수 있습니다.

> [!Note] 
> 이 필터는 신중하게 사용해야 하며 일반적으로 포털 콘텐츠 작성자 또는 유동 코드를 작성할 수 있는 신뢰할 수 있는 다른 사용자가 단독으로 제어하는 값에만 적용되어야 합니다.

**코드**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>참조

[웹 템플릿을 이용하여 소스 콘텐츠 저장](store-content-web-templates.md)  
[유동 연산자 이해](liquid-operators.md) 
[유동 유형](liquid-types.md)  
[유동 개체](liquid-objects.md)  
[유동 태그](liquid-tags.md)  
[유동 필터](liquid-filters.md)  
