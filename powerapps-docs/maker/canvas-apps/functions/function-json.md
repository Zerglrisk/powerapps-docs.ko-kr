---
title: JSON 함수 | Microsoft Docs
description: PowerApps의 JSON 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 74e10a5b073e16ba9f35139441c94e9911446a0f
ms.sourcegitcommit: 2084789802fc5134dbeb888e759cced46019a017
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66736402"
---
# <a name="json-function-in-powerapps"></a>PowerApps의 JSON 함수

테이블, 레코드 또는 값에 대 한 JSON 텍스트 문자열을 생성합니다.

## <a name="description"></a>설명

합니다 **JSON** 함수를 저장 하거나 네트워크를 통해 전송에 적합 한 텍스트로 데이터 구조의 개체 JSON (JavaScript Notation) 표현을 반환 합니다. [ECMA 404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) 하 고 [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) JavaScript 및 기타 프로그래밍 언어에서 널리 사용 되는 형식을 설명 합니다.

캔버스 앱 지원 합니다 [데이터 형식](data-types.md) 해당 텍스트 표현에 대 한 정보를 사용 하 여이 표에:

| 데이터 형식 | 설명 | 결과 예제 |
|-----------|-------------|---------|
| **Boolean** | *true 이면* 나 *false*합니다. | `true` |
| **Color** | 색에 대 한 8 자리 16 진수 표현을 포함 하는 문자열입니다. 이 표현은 형식은 &#40;*rrggbbaa*여기서 *rr* 빨강 구성 요소 이며 *gg* 은 녹색이 고 *bb* 파랑 이며 *aa* 알파 채널입니다. 알파 채널의 **00** 완전히 투명 하다 고 **ff** 은 완전히 불투명 합니다. 문자열을 전달할 수 있습니다 합니다 [ **ColorValue** ](function-colors.md) 함수입니다.  | `"#102030ff"` |
| **통화** | 사용자의 언어에 대 한 적절 한 소수 구분 기호를 사용 하는 번호입니다. 필요한 경우 과학적 표기법이 사용 됩니다. | `1.345` |
| **날짜** | ISO 8601 날짜를 포함 하는 문자열 **yyyy-월-일** 형식입니다. | `"2019-03-31"` |
| **DateTime** | ISO 8601 날짜/시간을 포함 하는 문자열입니다. 날짜/시간 값은 utc 기준, 끝 "Z" 따르면 됩니다.  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | GUID 값이 들어 있는 문자열입니다. 문자는 소문자입니다. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **이미지 미디어** | 하는 경우 **IncludeBinaryData** 를 지정 하면 미디어 파일에 문자열로 인코딩됩니다. 웹 http를 사용 하는 참조: 또는 https: URL 구성표를 수정 되지 않습니다. 메모리 내 이진 데이터에 대 한 참조를 사용 하 여 인코딩한 합니다 ["데이터:*mimetype*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) 형식입니다. 메모리 내 데이터는 사용자가 사용 하 여 캡처 이미지를 포함 합니다 [ **카메라** ](../controls/control-camera.md) 컨트롤과 appres 사용 하 여 다른 참조: 및 blob: URL 구성표입니다.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **수** | 사용자의 언어에 대 한 적절 한 소수 구분 기호를 사용 하는 번호입니다. 필요한 경우 과학적 표기법이 사용 됩니다. | `1.345` |
| **옵션&nbsp;설정** | 옵션의 숫자 값 설정, 표시에 사용 되는 레이블이 없습니다. 숫자 값은 언어 독립적 이기 때문에 사용 됩니다.  | `1001` |
| **시간** | ISO 8601을 포함 하는 문자열 *hh:mm:ss.fff* 형식입니다.  | `"23:12:49.000"` |
| **레코드** | 쉼표로 구분 된 목록 사이 **{0}** 하 고 **}** 필드와 해당 값입니다. 이 표기는 캔버스 앱의 레코드를 위한 비슷하지만 이름은 항상 큰따옴표 사이입니다. 이 형식은 다 대 일 관계를 기반으로 하는 레코드를 지원 하지 않습니다.  | `{ "First Name": "Fred", "Age": 21 }` |
| **Table** | 쉼표로 구분 된 목록 사이 **[** 하 고 **]** , 레코드입니다. 이 형식에 일 대 다 관계를 기반으로 하는 테이블을 지원 하지 않습니다.  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **Two&nbsp;option** | 두 옵션의 부울 값 *true* 하거나 *false*, 표시에 사용 되는 레이블이 없습니다. 부울 값은 언어 독립적 이기 때문에 사용 됩니다. | `false` |
| **하이퍼링크 텍스트** | 큰따옴표로 문자열입니다. 포함 된 큰따옴표는 백슬래시를 이스케이프 하 고 "\n"을 사용 하 여 줄 바꿈 대체 다른 표준 JavaScript 바꾸기를 수행 합니다. | `"This is a string."` |

선택적으로 지정할 *형식* 하는 방법을 읽을 수 있는 결과 제어 하는 인수 및 지원 되지 않는 방법과 이진 데이터 형식 처리 됩니다. 기본적으로 출력은 불필요 한 공백이 나 줄 바꿈 없이 최대한으로 압축 하 고 지원 되지 않는 데이터 형식 및 이진 데이터 허용 되지 않습니다. 지정 하는 경우에 여러 형식을 결합할 수는 **&** 연산자입니다.

| JSONFormat 열거형 | 설명 |
|-----------------|-------------|
| **Compact** | 기본값입니다.  출력 추가 공백이 나 줄 바꿈 없이 최대한으로 압축 됩니다. |
| **IndentFour** | 가독성을 높이기 출력 각 열과 중첩 수준에 대 한 줄 바꿈 문자를 포함 하 고 각 들여쓰기 수준에 대 한 네 개의 공백을 사용 합니다. |
| **IncludeBinaryData** | 결과는 이미지, 비디오 및 오디오 클립 열이 포함 됩니다. 크게 형식이으로 결과 크기를 증가 하 고 앱의 성능이 저하 될 수 있습니다. |
| **IgnoreBinaryData** | 결과는 이미지, 비디오 또는 오디오 클립 열을 포함 하지 않습니다. 둘 다 지정 하는 경우 **IncludeBinaryData** 도 **IgnoreBinaryData**, 이진 데이터를 발견할 경우 함수는 오류를 생성 합니다. |
| **IgnoreUnsupportedTypes** | 지원 되지 않는 데이터 형식 수 있지만 결과 포함 하지 않습니다. 기본적으로 지원 되지 않는 데이터 형식 오류가 발생 합니다. |

사용 합니다 [ **ShowColumns** 하 고 **DropColumns** ](function-table-shaping.md) 함수 결과 포함 하는 데이터를 제어 하 고 지원 되지 않는 데이터 형식을 제거 합니다.

때문에 **JSON** 수 메모리 및 계산 집약적이 사용 하 여 함수에 [동작 함수](../working-with-formulas-in-depth.md)합니다. 결과를 캡처할 수 있습니다 **JSON** 에 [변수](../working-with-variables.md)는 데이터 흐름에서 사용할 수 있습니다.

열 표시 이름 및 논리적 이름을 모두 있으면 결과 논리적 이름을 포함 합니다. 표시 이름은 앱 사용자에 있으므로 공용 서비스에 데이터 전송에 대 한 부적절 한 언어를 반영합니다.

## <a name="syntax"></a>구문

**JSON**( *DataStructure* [합니다 *형식* ])

* *DataStructure* – 필수 항목입니다. JSON으로 변환할 데이터 구조입니다.  테이블, 레코드 및 기본 값 지원 임의로 중첩 됩니다.
* *형식* -선택 사항입니다.  **JSONFormat** 열거형 값입니다. 기본값은 **Compact**, 줄 바꿈 또는 공백을 추가 하지 않습니다 있으며 이진 데이터와 지원 되지 않는 열을 차단 합니다.

## <a name="examples"></a>예

### <a name="hierarchical-data"></a>계층적 데이터

1. 삽입 된 [ **단추** ](../controls/control-button.md) 설정 해당 **OnSelect** 속성을 다음이 수식입니다.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Alt 키를 누른 채 단추를 선택 합니다.

    합니다 **CitiesByCountry** 컬렉션을 선택 하 여 표시할 수 있는이 데이터 구조를 사용 하 여 만들어집니다 **컬렉션** 에 **파일** 메뉴와 다음의 이름을 선택 하는 컬렉션입니다.

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry 컬렉션](media/function-json/cities-grouped.png)

    이 컬렉션을 선택 하 여 표시할 수도 있습니다 **파일** > **앱 설정** > **고급 설정**  >   **수식 입력줄 결과 뷰를 사용 하도록 설정**수식 입력줄에서 컬렉션의 이름을 선택 하 고 다음 수식 입력줄 아래에 컬렉션의 이름 옆의 아래쪽 화살표를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![수식 입력줄의 결과 뷰에서 컬렉션](media/function-json/cities-grouped-resultview.png)

1. 또 다른 단추를 삽입 하 고 설정 해당 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    전역 변수를 설정 하는이 수식을 **CitiesByCountryJSON** 에 대 한 JSON 표현을 **CitiesByCountry**합니다.

1. Alt 키를 누른 채 단추를 선택 합니다.

1. 삽입을 [ **레이블을** ](../controls/control-text-box.md) 설정 해당 **텍스트** 이 변수에 속성입니다.

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    레이블에 표시이 결과 공백 없이 한 줄에 모든 네트워크를 통해 전송에 적합 한:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 두 번째 단추의 수식 출력을 더 쉽게 읽을 수 있도록 변경 합니다.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Alt 키를 누른 채 두 번째 단추를 선택 합니다.

    레이블을 더 읽을 수 있는 결과 보여 줍니다.

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>이미지 및 base64 미디어

1. 추가 된 [ **이미지** ](../controls/control-image.md) 제어 합니다.

    이 컨트롤은 **SampleImage** 된 합니다.

1. 추가 된 [ **단추** ](../controls/control-button.md) 설정 해당 **OnSelect** 속성을 다음이 수식입니다.

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Alt 키를 누른 채 단추를 선택 합니다.

1. 레이블을 추가 하 고 설정 해당 **텍스트** 이 변수에 속성입니다.

    ```powerapps-dot
    ImageJSON
    ```

1. 컨트롤의 크기를 조정 하 고 대부분의 결과 표시 하는 데 필요한 글꼴 크기를 줄입니다.

    레이블에 표시 텍스트 문자열을 합니다 **JSON** 캡처된 함수입니다.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
