---
title: 포털에 액체 필터 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 액체 필터에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 68a595ee72704cf81241ecfee19f90728fb95aeb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975153"
---
# <a name="available-liquid-filters"></a>사용 가능한 Liquid 필터

액체 필터는 문자열, 숫자, 변수 및 개체의 출력을 수정 하는 데 사용 됩니다. 이러한 값은 |에서 적용 되는 값과 구분 됩니다.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

일부 필터는 매개 변수를 허용 합니다. 필터를 결합 하 여 왼쪽에서 오른쪽 순서로 적용할 수도 있습니다.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
다음 섹션에서는 다양 한 필터에 대해 설명 합니다. 

## <a name="array-filters"></a>배열 필터

배열 필터는 배열 작업에 사용 [됩니다.](liquid-types.md#array)  

### <a name="batch"></a>처리

배열을 지정 된 크기의 여러 배열로 나눕니다.

**Code**

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

### <a name="concat"></a>사용한

두 배열을 하나의 새 배열에 연결 합니다.

단일 항목이 매개 변수로 지정 된 경우 concat는 지정 된 항목을 마지막 요소로 사용 하 여 원래 배열로 구성 된 새 배열을 반환 합니다.

**Code**

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

### <a name="except"></a>남기고

지정 된 특성에 지정 된 값이 없는 배열에서 모든 개체를 선택 합니다. 이는**where**와 반대입니다.

**Code**

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

### <a name="first"></a>기본

배열의 첫 번째 요소를 반환 합니다.

첫 번째는 태그 내에서 사용 해야 하는 경우 특별 한 점 표기법으로 사용할 수도 있습니다.

**Code**

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

지정 된 특성에 따라 배열의 항목을 그룹화 합니다.

**Code**

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

### <a name="join"></a>조인

배열의 요소와 매개 변수로 전달 된 문자를 조인 합니다. 결과는 단일 문자열입니다.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**출력**

```
This, is, a, run, of, text
```

### <a name="last"></a>최신

배열의 마지막 요소를 반환 합니다.

마지막은 태그 내에서 사용 해야 하는 경우 특별 한 점 표기법으로 사용할 수도 있습니다.

**Code**

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

### <a name="order_by"></a>주문\_

배열 요소의 지정 된 특성을 기준으로 정렬 된 배열의 요소를 반환 합니다.

필요에 따라 desc를 두 번째 매개 변수로 제공 하 여 오름차순이 아닌 내림차순으로 요소를 정렬할 수 있습니다.

**Code**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**출력**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>임의

임의로 선택 된 단일 항목을 배열에서 반환 합니다.

**Code**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**출력**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>선택

배열의 각 항목에 대해 지정 된 특성의 값을 선택 하 고 이러한 값을 배열로 반환 합니다.

**Code**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**출력**

```
Redmond, New York
```

### <a name="shuffle"></a>섞기

배열에 적용 되 고, 동일한 항목을 사용 하 여 임의 순서로 새 배열을 반환 합니다.

**Code**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**출력**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>크기가

배열의 항목 수를 반환 합니다.

태그 내에서 사용 해야 하는 경우에는 특수 점 표기법으로 크기를 사용할 수도 있습니다.

**Code**

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

### <a name="skip"></a>킵

배열에서 지정 된 수의 항목을 건너뛰고 나머지를 반환 합니다.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**출력**

```
run, of, text
```

### <a name="take"></a>노트

배열에서 지정 된 수의 항목을 가져와 가져온 항목을 반환 합니다.

**Code**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**출력**

```

This, is, a
```

### <a name="then_by"></a>그런 다음\_

**는에 의해\_순서 대로**정렬 된 배열에 후속 순서를 추가 합니다.

필요에 따라 desc를 두 번째 매개 변수로 제공 하 여 오름차순이 아닌 내림차순으로 요소를 정렬할 수 있습니다.

**Code**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**출력**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>위치

지정 된 특성에 지정 된 값이 있는 배열의 모든 개체를 선택 합니다.

**Code**

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

날짜 계산에 날짜 필터를 사용 하거나 DateTime 값을 다양 한 형식으로 변환할 수 있습니다.

### <a name="date"></a>날

.NET 형식 문자열을 사용 하 여 DateTime 값의 서식을 지정 합니다.

[표준 날짜 및 시간 형식 문자열](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[사용자 지정 날짜 및 시간 형식 문자열](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Code**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**출력**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>날짜\_추가\_일

DateTime 값에 지정 된 정수 및 소수로 계산 된 날짜 수를 더 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_add_hours"></a>날짜\_\_시간 추가

정수 및 소수로 계산 된 지정 된 시간 수를 DateTime 값에 추가 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_add_minutes"></a>날짜\_추가\_분

DateTime 값에 지정 된 정수 및 소수로 계산 된 분 수를 더 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_add_months"></a>날짜\_추가\_월

DateTime 값에 지정 된 개월 수를 더 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_add_seconds"></a>날짜\_\_초 추가

정수 및 소수로 계산 된 초 수를 DateTime 값에 추가 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_add_years"></a>날짜\_\_년 추가

DateTime 값에 지정 된 연도 수를 더 합니다. 매개 변수는 양수 또는 음수일 수 있습니다.

**Code**

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

### <a name="date_to_iso8601"></a>iso8601\_에 대 한 날짜\_

[ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) 표준에 따라 DateTime 값의 서식을 지정 합니다. [*Atom 피드*](http://tools.ietf.org/html/rfc4287)또는 HTML5 &lt;time&gt; 요소를 만들 때 유용 합니다.  

**Code**

```
{{ now | date_to_iso8601 }}
```

**출력**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>rfc822\_에 대 한 날짜\_

[RFC 822](https://www.ietf.org/rfc/rfc0822.txt) 표준에 따라 DateTime 값의 서식을 지정 합니다. [*RSS 피드*](http://cyber.law.harvard.edu/rss/rss.html)를 만들 때 유용 합니다.  

**Code**

```
{{ now | date_to_rfc822 }}
```

**출력**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>엔터티 목록 필터

엔터티 목록 필터는 특정 [entitylist](liquid-objects.md#entitylist) 특성 값을 사용 하 여 작업 하 고 엔터티 목록 뷰를 만드는 데 사용 됩니다.  

### <a name="current_sort"></a>현재\_정렬

정렬 식이 지정 된 경우 지정 된 특성에 대 한 현재 정렬 방향을 반환 합니다.

**Code**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**출력**

```
DESC
```

### <a name="metafilters"></a>metafilters

[Entitylist](liquid-objects.md#entitylist) 필터\_정의 JSON 값을 필터 옵션 그룹 개체로 구문 분석 합니다.  

metafilters은 현재 특성 필터 쿼리 및 현재 [entitylist](liquid-objects.md#entitylist)를 사용 하 여 선택적으로 제공할 수 있으므로 반환 된 필터 개체를 선택 하거나 선택 하지 않은 상태로 플래그가 지정 될 수 있습니다.

**Code**

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

### <a name="reverse_sort"></a>역순\_정렬

정렬 방향이 지정 된 경우에는 반대 정렬 방향을 반환 합니다.

**Code**

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

수학 필터를 사용 하 여 [숫자](liquid-types.md#number)에 대 한 수치 연산을 수행할 수 있습니다.  

모든 필터와 마찬가지로 수학 필터를 연결 하 고 왼쪽에서 오른쪽 순서로 적용할 수 있습니다.

**Code**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**출력**

```
5
```

### <a name="ceil"></a>ceil

값을 가장 가까운 정수로 반올림 합니다.

**Code**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**출력**

```
5

5
```

### <a name="divided_by"></a>분할 된\_

숫자를 다른 숫자로 나눕니다.

**Code**

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

### <a name="floor"></a>평면

값을 가장 가까운 정수로 반올림 합니다.

**Code**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**출력**

```
4

4
```

### <a name="minus"></a>음수

숫자를 다른 숫자에서 뺍니다.

**Code**

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

### <a name="modulo"></a>나눈

숫자를 다른 숫자로 나누고 나머지를 반환 합니다.

**Code**

```
{{ 12 | modulo: 5 }}
```

**출력**

```
2
```

### <a name="plus"></a>더하기

숫자를 다른 숫자에 추가 합니다.

**Code**

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

### <a name="round"></a>둥근

값을 가장 가까운 정수나 지정 된 소수 자릿수로 반올림 합니다.

**Code**

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

### <a name="times"></a>곱한

숫자를 다른 숫자에 곱합니다.

**Code**

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

문자열 필터는 [문자열](liquid-types.md#string)을 조작 합니다.  

### <a name="append"></a>추가할

문자열을 다른 문자열의 끝에 추가 합니다.

**Code**

```
{{ 'filename' | append: '.js' }}
```

**출력**

```
filename.js
```

### <a name="capitalize"></a>**투자**

문자열에서 첫 번째 단어를 대문자로 바꿉니다.

**Code**

```
{{ 'capitalize me' | capitalize }}
```

**출력**

```
Capitalize Me
```

### <a name="downcase"></a>**다운 사례**

문자열을 소문자로 변환 합니다.

**Code**

```
{{ 'MIxed Case TExt' | downcase }}
```

**출력**

```
mixed case text
```

### <a name="escape"></a>**이스케이프**

HTML-문자열을 이스케이프 합니다.

**Code**

```
{{ '<p>test</p>' | escape }}
```

**출력**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**\_br로 줄 바꿈\_**

문자열의 각 줄 바꿈에 &lt;br/&gt; 줄 바꿈 HTML 태그를 삽입 합니다.

**Code**

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

### <a name="prepend"></a>**추가할지**

문자열을 다른 문자열의 시작 부분에 앞에 추가할 수 있습니다.

**Code**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**출력**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**삭제**

문자열에서 부분 문자열의 모든 항목을 제거 합니다.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**출력**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**먼저\_제거**

문자열에서 맨 처음 발견 되는 부분 문자열을 제거 합니다.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**출력**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**바꾸십시오**

문자열의 모든 항목을 하위 문자열로 바꿉니다.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**출력**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**\_를 먼저 바꿉니다.**

문자열의 처음 발견 되는 부분 문자열을 바꿉니다.

**Code**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**출력**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**분리할**

분할 필터는 하위 문자열을 매개 변수로 사용 합니다. 부분 문자열을 구분 기호로 사용 하 여 문자열을 배열로 나눕니다.

**Code**

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

### <a name="strip_html"></a>**줄무늬\_html**

문자열에서 모든 HTML 태그를 제거 합니다.

**Code**

```
<p>Hello</p>
```

**출력**

```
Hello
```

### <a name="strip_newlines"></a>**줄무늬\_줄바꿈**

문자열에서 줄 바꿈을 제거 합니다.

**Code**

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

### <a name="text_to_html"></a>**html\_\_텍스트**

일반 텍스트 문자열을 간단한 HTML로 서식 지정 합니다. 모든 텍스트는 HTML로 인코딩됩니다. 빈 줄로 구분 된 텍스트 블록은 단락 &lt;p&gt; 태그로 래핑됩니다. 한 줄 바꿈는 &lt;br&gt;로 바뀌고 Url은 하이퍼링크로 변환 됩니다.

**Code**

```
{{ note.notetext | text_to_html }}
```

**출력**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**잘라내야**

문자열을 지정 된 문자 수 만큼 아래로 자릅니다. 문자열에 줄임표 (...)가 추가 되 고 문자 수에 포함 됩니다.

**Code**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**출력**

```
This is...
```

### <a name="truncate_words"></a>**\_단어 잘림**

문자열을 지정 된 단어 수까지 자릅니다. 잘린 문자열에 줄임표 (...)가 추가 됩니다.

**Code**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**출력**

```
This is a...
```

### <a name="upcase"></a>**upcase**

문자열을 대문자로 변환 합니다.

**Code**

```
{{ 'MIxed Case TExt' | upcase }}
```

**출력**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_이스케이프**

URL에 포함 될 문자열을 URI 이스케이프 합니다.

**Code**

```
{{ 'This & that//' | url_escape }}
```

**출력**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_이스케이프**

Xml 출력에 포함 하기 위해 문자열을 이스케이프 합니다.

**Code**

```
{{ '<p>test</p>' | xml_escape }}
```

**출력**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>유형 필터

형식 필터를 사용 하면 한 형식의 값을 다른 형식으로 변환할 수 있습니다.

### <a name="boolean"></a>**부울**

문자열 값을 부울로 변환 하려고 합니다. 값이 이미 부울 인 경우 변경 되지 않은 상태로 반환 됩니다. 값을 부울로 변환할 수 없는 경우 null이 반환 됩니다.

이 필터는 또한 설정, 사용 또는 예를 true로, 해제, 사용 안 함 및 아니요를 false로 허용 합니다.

**Code**

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

### <a name="decimal"></a>**진수가**

문자열 값을 10 진수로 변환 하려고 합니다. 값이 이미 10 진수 이면 변경 되지 않은 상태로 반환 됩니다. 값을 10 진수로 변환할 수 없는 경우 null이 반환 됩니다.

**Code**

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

### <a name="integer"></a>**값**

문자열 값을 정수로 변환 하려고 합니다. 값이 이미 정수인 경우 변경 되지 않은 상태로 반환 됩니다. 값을 정수로 변환할 수 없는 경우 null이 반환 됩니다.

**Code**

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

### <a name="string"></a>**문자열**

값을 해당 문자열 표현으로 변환 하려고 합니다. 값이 이미 문자열이 면 변경 되지 않은 상태로 반환 됩니다. 값이 null 이면 null이 반환 됩니다.



## <a name="url-filters"></a>URL 필터

URL 필터를 사용 하 여 url의 일부를 빌드하거나 추출할 수 있습니다.

### <a name="add_query"></a>**\_쿼리 추가**

URL에 쿼리 문자열 매개 변수를 추가 합니다. 매개 변수가 이미 URL에 있으면 매개 변수 값이 업데이트 됩니다.

이 필터가 전체 절대 URL에 적용 되는 경우 업데이트 된 절대 URL이 결과로 반환 됩니다. 경로에 적용 되는 경우 업데이트 된 경로가 반환 됩니다.

**Code**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**출력**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**하단**

지정 된 URL의 기본 URL을 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**출력**

```
http://example.com
```

### <a name="host"></a>**호스팅하기**

URL의 호스트 파트를 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**출력**

```
example.com
```

### <a name="path"></a>**path**

URL의 경로 부분을 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**출력**

```
/path

/path
```

### <a name="path_and_query"></a>**경로\_및\_쿼리**

URL의 경로 및 쿼리 부분을 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**출력**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**포트인**

URL의 포트 번호를 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**출력**

```
80

443

9000
```

### <a name="remove_query"></a>**\_쿼리 제거**

URL에서 쿼리 문자열 매개 변수를 제거 합니다. URL에 매개 변수가 없는 경우에는 URL이 변경 되지 않은 상태로 반환 됩니다.

이 필터가 전체 절대 URL에 적용 되는 경우 업데이트 된 절대 URL이 결과로 반환 됩니다. 경로에 적용 되는 경우 업데이트 된 경로가 반환 됩니다.

**Code**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**출력**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**체계가**

URL의 스키마 부분을 가져옵니다.

**Code**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**출력**

```
http

https
```


## <a name="additional-filters"></a>추가 필터

이러한 필터는 유용한 일반 기능을 제공 합니다.

### <a name="default"></a>**기본**

할당 된 값이 없는 모든 변수에 대 한 기본값을 반환 합니다 (즉, null).

**Code**

```
{{ snippets[Header] | default: 'My Website' }}
```

**출력**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**파일\_크기**

바이트 수를 나타내는 숫자 값에 적용 되며 적절 한 소수 자릿수 단위의 형식이 지정 된 파일 크기를 반환 합니다.

필요에 따라 전체 자릿수 매개 변수를 전달 하 여 결과의 소수 자릿수를 제어할 수 있습니다. 기본 전체 자릿수는 1입니다.

**Code**

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

### <a name="has_role"></a>**\_역할 있음**

사용자에 게 적용 [되며, 사용자](liquid-objects.md#user)가 지정 된 역할에 속하는 경우 true를 반환 합니다. 그렇지 않으면 false를 반환 합니다.  

**Code**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

문자열을 액체 코드로 렌더링 합니다. 이 코드는 현재 액체 실행 컨텍스트 (변수 등)에 액세스할 수 있습니다.

> [!Note] 
> 이 필터는 주의 해 서 사용 해야 하며, 일반적으로 포털 콘텐츠 작성자의 단독 제어 아래에 있는 값 또는 액체 코드를 작성 하는 데 신뢰할 수 있는 다른 사용자에만 적용 해야 합니다.

**Code**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>참고 항목

[웹 템플릿을 사용 하 여 원본 콘텐츠 저장](store-content-web-templates.md)  
액체 [형식](liquid-types.md) 
[액체 연산자 이해](liquid-operators.md)  
[액체 개체](liquid-objects.md)  
[액체 태그](liquid-tags.md)  
[액체 필터](liquid-filters.md)  
