---
title: 다중 언어 포털 지원 사용 | MicrosoftDocs
description: 포털에서 여러 언어를 활성화하고 여러 언어로 콘텐츠를 만들기 위한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f8da1ac4be7098fc712faef82f6c9566d5f10512
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760724"
---
# <a name="enable-multiple-language-portal-support"></a>다중 언어 포털 지원 사용
사업은 단일 지역 또는 언어에 국한되지 않습니다. 단일 포털은 전 세계 고객에게 도달하기 위해 여러 언어로 콘텐츠를 표시할 수 있습니다. 포털의 콘텐츠는 단일 컨텐트 계층 구조를 유지하면서 여러 언어로 번역할 수 있습니다.

![다국어 드롭다운](../media/multi-language-dropdown.png "다국어 드롭다운 목록")  

포털에 여러 언어를 사용하려면 다음 단계를 수행하십시오.

1. [Common Data Service 환경에서 언어를 사용하도록 설정합니다.](https://technet.microsoft.com/library/dn832148.aspx)  
2. **포털** > **웹사이트** > **웹사이트**로 이동합니다.
3. 언어 지원을 추가할 웹 사이트를 선택합니다.
4. **지원되는 언어** 섹션의 **일반** 탭 아래에서 **새 웹 사이트 언어**를 선택합니다.
5. **포털 언어**(조직에서 활성화되고 포털에서 지원되는 언어 조회) 및 **게시 상태**를 포함하여 양식을 채웁니다.

   ![새 포털 언어 추가](../media/add-new-portal-language.png "새 포털 언어 추가")

   ![포털의 기본 언어 설정](../media/set-default-language-portal.png "포털의 기본 언어 설정")

> [!Note]
> 포털이 프로비전된 후 새 언어를 활성화하면 [메타데이터 번역을 가져와서](../admin/import-metadata-translation.md) 새로 활성화된 언어에 대한 메타데이터를 가져올 수 있습니다.

## <a name="supported-languages"></a>지원되는 언어

아래 표에서는 기본 제공되는 현재 사용할 수 있는 모든 언어를 보여 줍니다. 이 목록은 **포털** &gt; **콘텐츠** &gt; **포털 언어**로 이동하여 찾을 수 있습니다. 이 페이지에서 변경할 언어를 선택한 후에는 언어의 포털 표시 이름을 변경할 수 있습니다. 이제 목록에는 동아시아 언어(일본어, 중국어 및 한국어)가 포함됩니다.

| **이름**                           | **언어 코드** | **LCID** | **포털 표시 이름** |
|------------------------------------|-------------------|----------|-------------------------|
| 바스크어 - 바스크                    | eu-ES             | 1069     | euskara                 |
| 불가리아어 - 불가리아               | bg-BG             | 1026     | български               |
| 카탈로니아어 - 카탈로니아                  | ca-ES             | 1027     | català                  |
| 중국어 - 중국                    | zh-CN             | 2052     | 中文(中国)              |
| 중국어 - 홍콩 특별 행정구            | zh-HK             | 3076     | 中文(香港特別行政區)    |
| 중국어 - 번체              | zh-TW             | 1028     | 中文(台灣)              |
| 크로아티아어 - 크로아티아                 | hr-HR             | 1050     | hrvatski                |
| 체코어 - 체코 공화국             | cs CZ             | 1029     | čeština                 |
| 덴마크어 - 덴마크                   | da-DK             | 1030     | dansk                   |
| 네덜란드어 - 네덜란드                | nl-NL             | 1043     | Nederlands              |
| 영어                            | ko-KR             | 1042     | 영어                 |
| 에스토니아어 - 에스토니아                 | et-EE             | 1061     | eesti                   |
| 핀란드어 -핀란드                  | fi-FI             | 1035     | suomi                   |
| 프랑스어 - 프랑스                    | fr-FR             | 1036     | français                |
| 갈리시아어 - 스페인                   | gl-ES             | 1110     | galego                  |
| 독일어 - 독일                   | de-DE             | 1031     | Deutsch                 |
| 그리스어 - 그리스                     | el-GR             | 1032     | Ελληνικά                |
| 힌디어 - 인도                      | hi-IN             | 1081     | हिंदी                   |
| 헝가리어 - 헝가리                | hu-HU             | 1038     | magyar                  |
| 인도네시아어 - 인도네시아             | id-ID             | 1057     | Bahasa Indonesia        |
| 이탈리아어 - 이탈리아                    | it-IT             | 1040     | italiano                |
| 일본어 - 일본                   | ja-JP             | 1041     | 日本語                  |
| 카자흐어 - 카자흐스탄                | kk-KZ             | 1087     | қазақ тілі              |
| 한국어 - 한국                     | ko-KR             | 1042     | 한국어                  |
| 라트비아어 - 라트비아                   | lv-LV             | 1062     | latviešu                |
| 리투아니아어 - 리투아니아             | lt-LT             | 1063     | lietuvių                |
| 말레이어 - 말레이시아                   | ms-MY             | 1086     | Bahasa Melayu           |
| 노르웨이어(복말) - 노르웨이        | nb-NO             | 1044     | norsk bokmål            |
| 폴란드어 - 폴란드                    | pl-PL             | 1045     | polski                  |
| 포르투갈어 - 브라질                | pt-BR             | 1046     | português (Brasil)      |
| 포르투갈어 - 포르투갈              | pt-PT             | 2070     | português (Portugal)    |
| 루마니아어 - 루마니아                 | ro-RO             | 1048     | română                  |
| 러시아어 - 러시아                   | ru-RU             | 1049     | русский                 |
| 세르비아어(키릴 자모) - 세르비아        | sr-Cyrl-CS        | 3098     | српски                  |
| 세르비아어(라틴 문자) - 세르비아           | sr-Latn-CS        | 2074     | srpski                  |
| 슬로바키아어 - 슬로바키아                  | sk-SK             | 1051     | slovenčina              |
| 슬로베니아어 - 슬로베니아               | sl-SI             | 1060     | slovenščina             |
| 스페인어(전통 정렬) - 스페인 | es-ES             | 3082     | español                 |
| 스웨덴어 - 스웨덴                   | sv-SE             | 1053     | svenska                 |
| 태국어 - 태국                    | th-TH             | 1054     | ไทย                     |
| 터키어 - 터키                   | tr-TR             | 1055     | Türkçe                  |
| 우크라이나어 - 우크라이나                | uk-UA             | 1058     | українська              |
| 베트남어 - 베트남               | vi-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>여러 언어로 콘텐츠 만들기

1. Dynamics 365 포털에 로그인합니다.
2. 콘텐츠 목록을 보려면 **포털** > **콘텐츠** > **웹 페이지**로 이동합니다. 각 웹 페이지에 포털에 대해 활성화된 각 언어에 대해 페이지의 상위 버전과 페이지의 하위 버전이 있을 것입니다.
3. 페이지의 새 지역화를 추가하려면 기본 페이지로 이동하여 **지역화된 콘텐츠**를 아래로 스크롤합니다.
4. 맨 오른쪽에 있는 **+** 단추를 선택하여 지역화된 버전의 조회를 만듭니다.

    ![지역화된 새 콘텐츠 추가](../media/add-new-localized-content.png "지역화된 새 콘텐츠 추가")  

> [!Note]
> 콘텐츠 페이지의 홈 페이지에 있는 구성 필드는 기존 콘텐츠 페이지에 상속되지 않습니다. 그것은 새 콘텐츠 페이지를 만들 때만 사용됩니다. 사용자가 콘텐츠 페이지 구성을 개별적으로 업데이트해야 합니다.

참조 문서는 사용자가 포털에 표시하도록 설정한 언어로 번역된 경우에만 표시됩니다. 그러나 포럼과 블로그를 통해 다른 언어로 제공하는 방법에 대해 더 많은 제어가 가능합니다. 포럼이나 블로그에 대한 언어를 지정하는 것은 선택 사항입니다. 언어를 지정하지 않으면 포럼 또는 블로그가 조직의 기본 언어로 표시됩니다. 특정 언어의 포럼 또는 블로그를 원하는 경우 이를 작성하고 언어를 할당해야 합니다.

웹 링크 세트는 포털 상단에 있는 탐색 링크입니다. **포털** > **콘텐츠** > **웹 링크 집합**으로 이동하여 콘텐츠가 번역되는 방식을 제어할 수 있습니다. 포털에 대해 언어가 활성화되면 새로 활성화된 언어에 대해 새 링크 세트가 생성됩니다.

![새 언어에 대한 활성 웹 링크](../media/active-weblink-new-language.png "새 언어에 대한 활성 웹 링크")
