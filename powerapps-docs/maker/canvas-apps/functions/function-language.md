---
title: Language 함수 | Microsoft Docs
description: PowerApps에서 Language 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 33dcc3ab5e1682783c997adf4dd1185d59b0db2b
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678330"
---
# <a name="language-function-in-powerapps"></a>PowerApps의 Language 함수
현재 사용자의 언어 태그를 반환합니다.

## <a name="description"></a>설명
**Language** 함수는 현자 사용자의 언어, 스크립트 및 지역을 언어 태그로 반환합니다.

언어 정보를 사용하여 로캘 간에 앱을 조정합니다.  예를 들어 이탈리아와 프랑스에서 사용할 앱을 만드는 경우 **Language**를 사용하여 다른 위치에 있는 사용자에게 이탈리아어와 프랑스어 문자열을 자동으로 표시할 수 있습니다. 

### <a name="language-tags"></a>언어 태그
*언어 태그*는 세 가지 형식 중 하나가 될 수 있습니다.

| 반환 값 | 설명 |
| --- | --- |
| **"*lg&#8209;RE*"** |*lg*는 언어에 대한 두 자의 약어이고 *RE*는 지역에 대한 두 자의 약어입니다.  가장 일반적인 반환 형식입니다.  예를 들어 "en-GB"는 영국에 대해 반환됩니다. |
| **"*lg*"** |*lg*는 언어에 대한 두 자의 약어입니다.  이는 전원 앱에 언어에 대 한 정보가 있지만 특정 지역에 대 한 정보가 없는 경우에 사용 되는 형식입니다. |
| **"*lg&#8209;scrp&#8209;RE*"** |*lg*는 언어에 대한 두 자의 약어이고 *scrp*는 스크립트에 대한 네 자의 약어이며 *RE*는 지역에 대한 두 자의 약어입니다. |

Power Apps는 [IETF BCP-47 언어 태그](https://tools.ietf.org/html/bcp47) 형식을 사용 합니다.  

수식 입력줄 또는 고급 뷰에서 지원된 언어 태그, 형식 **Value( "1", )** 목록을 보려면 두 번째 인수에 대해 제안된 로캘의 목록 전체를 스크롤합니다.  

**[Text](function-text.md)** 및 **[Value](function-value.md)** 함수 모두 언어 태그를 사용합니다.  전역적으로 인식된 방식으로 텍스트 문자열을 변환하는 데 이러한 함수를 사용합니다.  언어 태그를 이러한 함수에 전달하고 지역에 차이가 없으면 태그의 언어 부분만 사용하면 됩니다.

## <a name="syntax"></a>구문
**Language**()

## <a name="examples"></a>예
### <a name="users-locale"></a>사용자의 로캘
호스트 운영 체제 및/또는 브라우저가 위치에 대한 기본 로캘을 사용한다고 가정합니다.

| 수식 | 위치 | 반환 값 |
| --- | --- | --- |
| **Language()** |리스본, 포르투갈 |"pt-PT" |
| **Language()** |리우데자네이루, 브라질 |"pt-BR" |
| **Language()** |애틀랜타, 미국 |"en-US" |
| **Language()** |맨체스터, 영국 |"en-GB" |
| **Language()** |파리, 프랑스 |"fr-FR" |
| **Language()** |로조, 도미니카 |"en" |
| **Language()** |벨그라드, 세르비아 |사용자의 시스템 설정에 따라 "sr-cyrl-RS" 또는 "sr-latn-RS" |

### <a name="localization-table"></a>지역화 테이블
지역화를 위한 간단한 접근 방법은 작성자가 정의한 **TextID**를 사용자 언어의 번역된 텍스트에 매핑하는 Excel 스프레드시트 매핑을 만드는 것입니다.  이 테이블에 대해 다른 데이터 원본이나 컬렉션을 사용할 수는 있지만 번역사가 앱 외부에서 쉽게 편집하고 관리할 수 있는 Excel을 선택했습니다.

1. Excel에서 다음 테이블을 만듭니다. 
   
    ![](media/function-language/loc-table.png)
   
    지정된 언어에 대해 특정 텍스트 문자열이 발견되지 않으면 **Language** 열이 *공백*인 항목이 기본값으로 사용됩니다. 이 항목은 주어진 **TextID**에 대한 다른 모든 항목 다음에 나타나야 합니다.
   
    목적에 맞게, 지역이 아닌 로캘의 언어를 확인해야 합니다.  지역별 고려 사항이 중요한 경우 위 테이블에 전체 언어 태그 값을 포함할 수 있습니다. 
2. **Insert** 리본, **Table** 명령을 사용하여 적절한 Excel 테이블로 만듭니다.  기본적으로 이름은 **Table1**이지만 왼쪽 멀리 있는 **테이블 도구/디자인**  리본과 **테이블 이름:** 텍스트 상자로 원하는 이름을 지정할 수 있습니다.
3. 로컬 파일 시스템에 Excel 파일을 저장합니다.   
4. Power Apps의 오른쪽 창에서 **데이터 원본** 탭을 클릭 하거나 탭 한 다음 **데이터 원본 추가**를 클릭 하거나 탭 합니다.
5. **앱에 정적 데이터 추가**를 클릭하거나 탭하고, 저장한 Excel 파일을 클릭하거나 탭한 다음, **열기**를 클릭하거나 탭합니다.
6. 생성한 테이블을 선택한 후 **연결**을 클릭하거나 탭합니다.

앱에서 텍스트 **"Hello"** 를 사용했던 위치마다 대신 다음 수식을 사용합니다.

* **LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

이 수식은 사용자의 언어에 해당하는 적절한 **LocalizedText**를 조회하고 없는 경우 기본 *공백* 버전에서 대체(Fallback)합니다. 

다른 언어로 번역된 문자열은 자신의 언어보다 훨씬 오래 걸릴 수 있습니다.  대부분의 경우 사용자 인터페이스에 문자열을 표시하는 레이블 및 기타 요소가 더 넓어져야 합니다.

### <a name="translation-service"></a>번역 서비스
Microsoft Translator 서비스와 같은 번역 서비스를 사용하여 필요에 따라 텍스트를 번역할 수 있습니다.  

1. Power Apps의 오른쪽 창에서 **데이터 원본** 탭을 클릭 하거나 탭 한 다음 **데이터 원본 추가**를 클릭 하거나 탭 합니다.
2. **Microsoft Translator**를 클릭하거나 탭합니다.

앱에서 텍스트 **"Hello"** 를 사용했던 위치마다 대신 다음 수식을 사용합니다.

* **MicrosoftTranslator.Translate( "Hello", Language() )**

Microsoft Translator 서비스는 **Language** 함수에서 반환하는 동일한 언어 태그를 사용합니다.

이 접근 방법은 사전 번역된 텍스트 문자열 테이블을 사용했던 이전 예제와 비교할 때 몇 가지 단점이 있습니다.

* 번역 작업을 완료하는 데 시간이 걸리므로 네트워크를 통해 서비스를 호출해야 합니다.  이렇게 하면 앱의 번역된 텍스트가 지연되어 표시됩니다. 
* 번역은 기계적으로 이루어지므로 예상한 내용이 아니거나 앱 내의 상황에 가장 적합한 번역이 아닐 수 있습니다.

