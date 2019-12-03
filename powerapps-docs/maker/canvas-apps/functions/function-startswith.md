---
title: EndsWith 및 StartsWith 함수 | Microsoft Docs
description: Power Apps의 EndsWith 및 StartsWith 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/24/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 018c6fc80c1fa1c6dfbb66ae70696b6f426fdfb5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730098"
---
# <a name="endswith-and-startswith-functions-in-power-apps"></a>Power Apps의 EndsWith 및 StartsWith 함수
텍스트 문자열이 다른 텍스트 문자열로 시작되거나 끝나는지 테스트합니다.

## <a name="description"></a>설명
**EndsWith** 함수는 텍스트 문자열이 다른 텍스트 문자열로 끝나는지 테스트합니다.

**StartsWith** 함수는 텍스트 문자열이 다른 텍스트 문자열로 시작하는지 테스트합니다.    

두 함수 모두, 테스트에서 대/소문자를 구분하지 않습니다.  두 함수의 반환 값은 부울 **true** 또는 **false**입니다.  

**EndsWith**와 **StartsWith**를 **[Filter](function-filter-lookup.md)** 함수와 함께 사용하여 앱 내의 데이터를 검색합니다. **[in](operators.md#in-and-exactin-operators)** 연산자나 **[Search](function-filter-lookup.md)** 함수를 사용하면 시작이나 끝뿐만 아니라 텍스트 문자열 내 어디든지 볼 수 있습니다.  함수의 선택은 앱의 필요에 따라 달라지며 특정 데이터 원본에 대해 [위임](../delegation-overview.md)할 수 있는 함수에 따라 달라집니다.  이러한 함수 중 위임할 수 없는 함수가 있으면 이러한 제한 사항을 경고하기 위해 수식 작성 시 위임 경고가 표시됩니다.

## <a name="syntax"></a>구문
**EndsWith**( *Text*, *EndText* )

* *Text* – 필수 항목입니다.  테스트할 텍스트입니다.
* *EndText* – 필수 항목입니다.  *Text*의 끝에서 검색할 텍스트입니다.  *EndText*가 빈 문자열이면 **EndsWith**는 *true*를 반환합니다.

**StartsWith**( *Text*, *StartText* )

* *Text* – 필수 항목입니다.  테스트할 텍스트입니다.
* *StartText* – 필수 항목입니다.  *Text*의 시작 부분에서 검색할 텍스트입니다.  *StartText*가 빈 문자열이면 **StartsWith**는 *true*를 반환합니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **EndsWith( "Hello World", "world" )** |**"Hello World"** 가 **"world"** 로 끝나는지 테스트합니다.  이 테스트는 대/소문자를 구분하지 않습니다. |**true** |
| **EndsWith( "Good bye", "good" )** |**"Good bye"** 가 **"good"** 으로 끝나는지 테스트합니다.  *EndText* 인수( **"good"** )가 텍스트에 나타나지만 끝에 나타나지는 않습니다. |**false** |
| **EndsWith( "Always say hello", "hello" )** |**"Always say hello"** 가 **"hello"** 로 끝나는지 테스트합니다. |**true** |
| **EndsWith ("Bye bye", "")** |**"Bye bye"** 가 빈 텍스트 문자열(**Len**이 0을 반환함)로 끝나는지 테스트합니다.  **필터** 식에서 사용을 줄이면, 이런 경우 **EndsWith**가 **true**를 반환하도록 정의됩니다. |**true** |

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **StartsWith( "Hello World", "hello" )** |**"Hello World"** 가 **"hello"** 로 시작하는지 테스트합니다.  이 테스트는 대/소문자를 구분하지 않습니다. |**true** |
| **StartsWith( "Good bye", "hello" )** |**"Good bye"** 가 **"hello"** 로 시작하는지 테스트합니다. |**false** |
| **StartsWith( "Always say hello", "hello" )** |**"Always say hello"** 가 **"hello"** 로 시작하는지 테스트합니다.  **"hello"** 가 텍스트에 나타나지만 처음에 나타나지는 않습니다. |**false** |
| **StartsWith( "Bye bye", "" )** |**"Bye bye"** 가 빈 텍스트 문자열(**Len**이 0을 반환함)로 시작하는지 테스트합니다.  **필터** 식에서 사용을 줄이면, 이런 경우 **StartsWith**가 **true**를 반환하도록 정의됩니다. |**true** |

### <a name="search-user-experience"></a>검색 사용자 환경
많은 앱에서 하나 이상의 문자를 검색 상자에 입력하면 큰 데이터 집합의 레코드 목록을 필터링할 수 있습니다. 입력하는 동안 검색 조건과 일치하는 레코드만 목록에 표시됩니다.

이 문서의 나머지 부분에 있는 예제는 다음 데이터가 포함된 **Customers** 목록을 검색한 결과를 보여줍니다.

![](media/function-startswith/customers.png)

이 데이터 원본을 컬렉션으로 만들려면 **[Button](../controls/control-button.md)** 컨트롤을 만들고 **OnSelect** 속성을 다음 수식으로 설정합니다.

**ClearCollect( Customers, Table( { Name: "Fred Garcia", Company: "Northwind Traders" }, { Name: "Cole Miller", Company: "Contoso" }, { Name: "Glenda Johnson", Company: "Contoso" }, { Name: "Mike Collins", Company: "Adventure Works" }, { Name: "Colleen Jones", Company: "Adventure Works" } ) )**

이 예제에서와 같이 화면 하단의 [**갤러리 컨트롤**](../controls/control-gallery.md)에 레코드 목록을 표시할 수 있습니다. 사용자가 관심 있는 레코드를 지정할 수 있도록 화면 맨 위 가까이에 **SearchInput**이라는 [**텍스트 입력**](../controls/control-text-input.md) 컨트롤을 추가합니다.

![](media/function-startswith/customers-ux-unfiltered.png)

사용자가 **SearchInput**에 문자를 입력하면 갤러리의 결과가 자동으로 필터링됩니다. 이 경우 갤러리는 고객 이름(회사 이름 아님)이 **SearchInput**의 문자 시퀀스로 시작하는 레코드를 표시하도록 구성됩니다. 사용자가 검색 상자에 **co**를 입력하면 갤러리에 다음 결과가 표시됩니다.

![](media/function-startswith/customers-ux-startswith-co.png)

**Name** 열을 기준으로 필터링하려면 갤러리 컨트롤의 **Items** 속성을 다음 수식 중 하나로 설정합니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) )** |**Customers** 데이터 원본을 **Name** 열의 시작 부분에 검색 문자열이 나타나는 레코드로 필터링합니다. 이 테스트는 대/소문자를 구분하지 않습니다. 사용자가 검색 창에 **co**를 입력하면 갤러리에 **Colleen Jones**와 **Cole Miller**가 표시됩니다. **Mike Collins**는 레코드의 **Name** 열이 검색 문자열로 시작하지 않기 때문에 갤러리에 표시되지 않습니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name )** |**Customers** 데이터 원본을 **Name** 열의 아무 곳에나 검색 문자열이 나타나는 레코드로 필터링합니다. 이 테스트는 대/소문자를 구분하지 않습니다. 사용자가 검색 상자에 **co**를 입력하면 **Colleen Jones,** **Cole Miller,** **Mike Collins**가 갤러리에 표시됩니다. 이러한 레코드의 **Name** 열 어딘가에 검색 문자열이 나타나기 때문입니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name" )** |**in** 연산자를 사용하는 경우와 유사하게, **Search** 함수는 각 레코드의 **Name** 열 내에서 일치하는 항목을 검색합니다. 열 이름은 큰따옴표로 묶어야 합니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-name-co-contains.png) |

**Company** 열과 **Name** 열을 포함하도록 검색 범위를 확장할 수 있습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Filter( Customers, StartsWith( Name, SearchInput.Text ) &#124;&#124; StartsWith( Company, SearchInput.Text ) )** |**Customers** 데이터 원본을 **Name** 열 또는 **Company** 열이 검색 문자열(예: **co**)로 시작하는 레코드로 필터링합니다.  **StartsWith** 함수 중 하나가 *true*이면 [ **&#124;&#124;** 연산자](operators.md)는 *true*입니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-startswith.png) |
| **Filter( Customers, SearchInput.Text in Name &#124;&#124; SearchInput.Text in Company )** |**Customers** 데이터 원본을 **Name** 열 또는 **Company** 열에 검색 문자열(예: **co**)이 들어 있는 레코드로 필터링합니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |
| **Search( Customers, SearchInput.Text, "Name", "Company" )** |**in** 연산자를 사용하는 경우와 유사하게, **Search** 함수는 **Customers** 데이터 원본에서 **Name** 열 또는 **Company** 열에 검색 문자열(예: **co**)이 들어 있는 레코드를 검색합니다. 여러 열 및 다수의 **in** 연산자를 지정하는 경우 **Search** 함수가 **Filter**보다 읽고 쓰기 쉽습니다. 열 이름은 큰따옴표로 묶어야 합니다. |<style> img { max-width: none } </style> ![](media/function-startswith/customers-all-co-contains.png) |

