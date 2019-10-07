---
title: JSON 함수 | Microsoft Docs
description: PowerApps의 JSON 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba852093da05c3fa69cc47b219a0bef65908c170
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992628"
---
# <a name="json-function-in-powerapps"></a>PowerApps의 JSON 함수

테이블, 레코드 또는 값에 대 한 JSON 텍스트 문자열을 생성 합니다.

## <a name="description"></a>설명

**Json** 함수는 네트워크를 통해 저장 하거나 전송 하는 데 적합 하도록 데이터 구조의 JAVASCRIPT OBJECT NOTATION (json) 표현을 텍스트로 반환 합니다. [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) 및 [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) 은 JavaScript 및 기타 프로그래밍 언어에서 널리 사용 되는 형식을 설명 합니다.

Canvas 앱은이 테이블에 표시 되는 [데이터 형식을](data-types.md) 텍스트 표현에 대 한 세부 정보와 함께 지원 합니다.

| 데이터 형식 | 설명 | 결과 예제 |
|-----------|-------------|---------|
| **부울** | *true* 또는 *false*입니다. | `true` |
| **색상** | 색에 대 한 8 자리 16 진수 표현을 포함 하는 문자열입니다. 이 표현은 #*rrggbbaa*형식을 사용 합니다. 여기서 *rr* 은 빨강 구성 요소이 고, *gg* 는 녹색, *bb* 는 파란색, *aa* 는 알파 채널입니다. 알파 채널의 경우 **00** 은 완전히 투명 하 고 **ff** 는 완전히 불투명 합니다. 문자열을 [**Colorvalue**](function-colors.md) 함수로 전달할 수 있습니다.  | `"#102030ff"` |
| **통화** | 사용자 언어에 적절 한 소수 구분 기호를 사용 하는 숫자입니다. 필요한 경우 과학적 표기법이 사용 됩니다. | `1.345` |
| **날** | ISO 8601 **yyyy-mm-dd** 형식의 날짜를 포함 하는 문자열입니다. | `"2019-03-31"` |
| **날짜** | ISO 8601 날짜/시간을 포함 하는 문자열입니다. 종료 "Z"가 표시 되는 날짜/시간 값은 UTC입니다.  | `"2019-03-31T22:32:06.822Z"`  |
| **EID** | GUID 값을 포함 하는 문자열입니다. 문자는 소문자입니다. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **이미지, 미디어** | **IncludeBinaryData** 를 지정 하면 미디어 파일이 문자열로 인코딩됩니다. Http: 또는 https를 사용 하는 웹 참조: URL 구성표는 수정 되지 않습니다. 메모리 내 이진 데이터에 대 한 참조는 ["data:*mimetype*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) 형식으로 인코딩됩니다. 메모리 내 데이터에는 사용자가 [**카메라**](../controls/control-camera.md) 컨트롤과 appres: 및 blob을 사용 하 여 다른 참조를 사용 하 여 캡처하는 이미지가 포함 됩니다. URL 스키마.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **수많은** | 사용자 언어에 적절 한 소수 구분 기호를 사용 하는 숫자입니다. 필요한 경우 과학적 표기법이 사용 됩니다. | `1.345` |
| **옵션 @ no__t-1set** | 표시에 사용 되는 레이블이 아닌, 옵션 집합의 숫자 값입니다. 숫자 값은 언어와 무관 하기 때문에 사용 됩니다.  | `1001` |
| **런타임** | ISO 8601 *hh: mm: ss. fff* 형식을 포함 하는 문자열입니다.  | `"23:12:49.000"` |
| **기록은** | 필드와 값의 **{** 와 **}** 사이에서 쉼표로 구분 된 목록입니다. 이 표기법은 캔버스 앱의 레코드와 유사 하지만 이름이 항상 큰따옴표 사이에 있습니다. 이 형식은 다 대 일 관계를 기반으로 하는 레코드를 지원 하지 않습니다.  | `{ "First Name": "Fred", "Age": 21 }` |
| **테이블** | 레코드의 **[** 및 **]** 사이에 있는 쉼표로 구분 된 목록입니다. 이 형식은 일 대 다 관계를 기반으로 하는 테이블을 지원 하지 않습니다.  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **두 개의 @ no__t-1option** | 표시에 사용 되는 레이블이 아닌 *true* 또는 *false*의 두 옵션에 대 한 부울 값입니다. 부울 값은 언어와 무관 하기 때문에 사용 됩니다. | `false` |
| **하이퍼링크, 텍스트** | 큰따옴표 사이의 문자열입니다. 함수는 백슬래시를 사용 하 여 포함 된 큰따옴표를 이스케이프 하 고 줄바꿈을 "\n"으로 바꾸고 다른 표준 JavaScript 대체를 만듭니다. | `"This is a string."` |

선택적인 *형식* 인수를 지정 하 여 결과를 읽을 수 있는 방법과 지원 되지 않는 이진 데이터 형식과 이진 데이터 형식을 처리 하는 방법을 제어 합니다. 기본적으로 출력은 불필요 한 공백 또는 줄바꿈 없이 가능한 한 간결한 것 이며 지원 되지 않는 데이터 형식 및 이진 데이터는 허용 되지 않습니다. **@No__t-1** 연산자를 지정 하는 경우 여러 형식을 결합할 수 있습니다.

| JSONFormat 열거형 | 설명 |
|-----------------|-------------|
| **구문** | 기본값입니다.  출력은 공백이 나 줄바꿈를 추가 하지 않고 최대한 압축 됩니다. |
| **IndentFour** | 가독성을 높이기 위해 출력에는 각 열 및 중첩 수준에 대 한 줄 바꿈이 포함 되며 각 들여쓰기 수준에 4 개의 공백을 사용 합니다. |
| **IncludeBinaryData** | 결과에는 이미지, 비디오 및 오디오 클립 열이 포함 됩니다. 이 형식은 결과 크기를 크게 증가 시키고 앱의 성능을 저하 시킬 수 있습니다. |
| **IgnoreBinaryData** | 결과에는 이미지, 비디오 또는 오디오 클립 열이 포함 되지 않습니다. **IncludeBinaryData** 또는 **IgnoreBinaryData**를 모두 지정 하지 않으면 함수에서 이진 데이터를 발견 하면 오류를 생성 합니다. |
| **IgnoreUnsupportedTypes** | 지원 되지 않는 데이터 형식은 허용 되지만 결과에는 포함 되지 않습니다. 지원 되지 않는 데이터 형식은 기본적으로 오류를 생성 합니다. |

[ **Showcolumns** 및 **dropcolumns** ](function-table-shaping.md) 함수를 사용 하 여 결과에 포함 되는 데이터를 제어 하 고 지원 되지 않는 데이터 형식을 제거 합니다.

**JSON** 은 메모리와 계산 집약적 일 수 있으므로이 함수는 [동작 함수](../working-with-formulas-in-depth.md)에서만 사용할 수 있습니다. **JSON** 의 결과를 [변수로](../working-with-variables.md)캡처하여 데이터 흐름에서 사용할 수 있습니다.

열에 표시 이름과 논리적 이름이 모두 있으면 결과에 논리적 이름이 포함 됩니다. 표시 이름은 앱 사용자의 언어를 반영 하므로 공통 서비스로 데이터를 전송 하는 데 적합 하지 않습니다.

## <a name="syntax"></a>구문

**JSON**( *datastructure* [, *Format* ])

* *Datastructure* – 필수 항목입니다. JSON으로 변환할 데이터 구조체입니다.  테이블, 레코드 및 기본 값은 임의로 중첩 되어 지원 됩니다.
* *Format* -선택 사항입니다.  **JSONFormat** 열거형 값입니다. 기본값은 **Compact**이며, 줄바꿈 또는 공백을 추가 하지 않고 이진 데이터 및 지원 되지 않는 열을 차단 합니다.

## <a name="examples"></a>예

### <a name="hierarchical-data"></a>계층적 데이터

1. [**Button**](../controls/control-button.md) 컨트롤을 삽입 하 고 **onselect** 속성을이 수식으로 설정 합니다.

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

    **Citiesbycountry** 컬렉션은이 데이터 구조를 사용 하 여 생성 됩니다 .이 데이터 구조는 **파일** 메뉴에서 **컬렉션** 을 선택한 다음 컬렉션 이름을 선택 하 여 표시할 수 있습니다.

    > [!div class="mx-imgBorder"]
    > @no__t 0CitiesByCountry collection @ no__t-1

    **파일** > **앱 설정** > **고급 설정** > **수식 입력줄 결과 뷰를 사용 하도록 설정**하 고 수식 입력줄에서 컬렉션의 이름을 선택한 다음을 선택 하 여이 컬렉션을 표시할 수도 있습니다. 수식 입력줄 아래에 있는 컬렉션의 이름 옆에 있는 아래쪽 화살표입니다.

    > [!div class="mx-imgBorder"]
    > 수식 입력줄의 결과 뷰에서 ![Collection @ no__t-1

1. 다른 단추를 삽입 하 고 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    이 수식은 **CitiesByCountryJSON** 전역 변수를 **Citiesbycountry**에 대 한 JSON 표현으로 설정 합니다.

1. Alt 키를 누른 채 단추를 선택 합니다.

1. [**레이블**](../controls/control-text-box.md) 컨트롤을 삽입 하 고 **Text** 속성을이 변수로 설정 합니다.

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    레이블에는이 결과가 모두 공백 없이 단일 줄에 표시 되며 네트워크를 통해 전송 하는 데 적합 합니다.

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 두 번째 단추의 수식을 변경 하 여 출력을 보다 읽기 쉽게 만듭니다.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Alt 키를 누른 채 두 번째 단추를 선택 합니다.

    레이블에 더 읽기 쉬운 결과가 표시 됩니다.

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

### <a name="images-and-media-in-base64"></a>B a s e 64의 이미지 및 미디어

1. [**이미지**](../controls/control-image.md) 컨트롤을 추가 합니다.

    이 컨트롤은 **SampleImage** 를 가져옵니다.

1. [**Button**](../controls/control-button.md) 컨트롤을 추가 하 고 **onselect** 속성을이 수식으로 설정 합니다.

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Alt 키를 누른 채 단추를 선택 합니다.

1. 레이블을 추가 하 고 **Text** 속성을이 변수로 설정 합니다.

    ```powerapps-dot
    ImageJSON
    ```

1. 대부분의 결과를 표시 하기 위해 필요에 따라 컨트롤의 크기를 조정 하 고 글꼴 크기를 줄입니다.

    레이블은 **JSON** 함수가 캡처한 텍스트 문자열을 표시 합니다.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
