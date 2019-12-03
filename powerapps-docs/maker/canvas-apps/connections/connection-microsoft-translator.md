---
title: Microsoft Translator 연결 개요 | Microsoft Docs
description: Microsoft Translator에 연결하는 방법을 알아보고 몇 가지 예제를 진행하고, 모든 함수를 살펴봅니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 387089ea2ee40e8a0d418ab110d7544c17d7c423
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679894"
---
# <a name="connect-to-microsoft-translator-from-powerapps"></a>PowerApps에서 Microsoft Translator에 연결
![Microsoft Translator](./media/connection-microsoft-translator/translatoricon.png)

Microsoft Translator 커넥터를 추가하여 앱의 **레이블** 컨트롤에 번역된 텍스트를 표시합니다. 예를 들어, 사용자에게 번역할 텍스트를 입력하도록 요청하는 입력 텍스트 상자를 만들 수 있습니다. 다른 레이블에서는 번역된 텍스트를 표시할 수 있습니다.

이 토픽에서는 앱에서 Microsoft Translator 연결을 만들고 Microsoft Translator 연결을 사용하는 방법을 보여 주며 사용 가능한 함수를 나열합니다.

> [!NOTE]
> 이 커넥터는 매일 사용자당 150개 호출로 제한됩니다.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-microsoft-translator"></a>Microsoft Translator 연결
1. Power Apps를 열고 **새로 만들기**를 선택한 다음, **빈 앱**을 만듭니다. 전화나 태블릿 레이아웃을 선택합니다. 태블릿 레이아웃의 작업 영역이 더 넓습니다.  

   ![비어 있는 앱 열기](./media/connection-microsoft-translator/blank-app.png)
2. 오른쪽 창에서 **데이터** 탭을 클릭하거나 탭한 후 **데이터 원본 추가**를 클릭하거나 탭합니다.
3. **새 연결**을 선택한 후 **Microsoft Translator**를 선택합니다.  

    ![Microsoft Translator 연결](./media/connection-microsoft-translator/addconnection.png)

    ![Microsoft Translator 연결](./media/connection-microsoft-translator/add-translator.png)
4. **연결**을 선택합니다. 연결이 **데이터 원본** 아래에 표시됩니다.  

    ![Microsoft Translator 연결](./media/connection-microsoft-translator/translatordatasource.png)

## <a name="use-the-microsoft-translator-connection-in-your-app"></a>앱에서 Microsoft Translator 연결 사용
### <a name="translate-text"></a>텍스트 번역
1. **삽입** 메뉴에서 **텍스트**를 선택한 다음 **텍스트 입력**을 선택합니다. 텍스트 입력 컨트롤의 이름을 **Source**로 바꿉니다.  

    ![바꾸면](./media/connection-microsoft-translator/renametosource.png)
2. **드롭다운** 목록(**삽입** 메뉴 > **컨트롤**)을 추가하고 이름을 **TargetLang**으로 변경한 다음, **Source** 아래로 이동합니다.
3. **TargetLang**의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

    `MicrosoftTranslator.Languages()`
4. 레이블을 추가하고 **TargetLang** 아래로 이동한 다음, **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

    `MicrosoftTranslator.Translate(Source.Text, TargetLang.Selected.Value)`
5. 일부 텍스트를 **Source**에 입력하고 **TargetLang**에서 언어를 선택합니다. 레이블은 입력한 텍스트를 사용자가 선택한 언어로 표시합니다.  

    ![영어에서 스페인어로 텍스트 번역](./media/connection-microsoft-translator/translate-text.png)

### <a name="speak-translated-text"></a>번역된 텍스트 말하기
아직 하지 않았다면 이전 절의 단계에 따라 일부 텍스트를 번역합니다. 이러한 다음 단계는 동일한 컨트롤을 사용합니다.

1. **TargetLang** 드롭다운 목록의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

    `MicrosoftTranslator.SpeechLanguages()`
2. 두 번째 레이블(**Source** 상자 아님)의 이름을 **Target**으로 바꿉니다.
3. **오디오** 컨트롤을 추가하고 (**삽입** 메뉴 > **Media**) **Media** 속성을 다음 수식으로 설정합니다.  

    `MicrosoftTranslator.TextToSpeech(Target.Text, TargetLang.Selected.Value)`
4. F5를 누르거나 미리 보기 단추(![](./media/connection-microsoft-translator/preview.png))를 선택합니다. 일부 텍스트를 **Source**에 입력하고 **TargetLang**에서 언어를 선택한 다음, 오디오 컨트롤에서 재생 단추를 선택합니다.

    앱은 사용자가 입력한 텍스트의 오디오 버전을 사용자가 선택한 언어로 재생합니다.
5. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

### <a name="detect-the-source-language"></a>원본 언어 검색
이러한 다음 단계는 동일한 **Source** 텍스트 입력 및 **Target** 텍스트 컨트롤을 사용합니다. 원하는 경우 새 컨트롤을 만들거나, 수식에서 이름을 업데이트할 수 있습니다.

1. **Target** 텍스트 컨트롤을 선택하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

    `MicrosoftTranslator.Detect(Source.Text).Name`
2. 일부 텍스트를 **Source**에 입력합니다.

    레이블은 사용자가 입력한 텍스트의 언어를 표시합니다. 예를 들어, 사용자가 **bonjour**를 입력하면 **프랑스어**, 또는 **ciao**를 입력하면 **이탈리아어**를 표시합니다.

## <a name="view-the-available-functions"></a>사용할 수 있는 함수 보기
이 연결에는 다음 함수가 포함됩니다.

| 함수 이름 | 설명 |
| --- | --- |
| [Languages](connection-microsoft-translator.md#languages) |Microsoft Translator가 지원하는 모든 언어를 검색합니다. |
| [Translate](connection-microsoft-translator.md#translate) |Microsoft Translator를 사용하여 지정된 언어로 텍스트를 번역합니다. |
| [Detect](connection-microsoft-translator.md#detect) |지정된 텍스트의 원본 언어를 검색합니다. |
| [SpeechLanguages](connection-microsoft-translator.md#speechlanguages) |음성 합성에 사용할 수 있는 언어를 검색합니다. |
| [TextToSpeech](connection-microsoft-translator.md#texttospeech) |지정된 텍스트를 웨이브 형식의 오디오 스트림 음성으로 변환합니다. |

### <a name="languages"></a>언어들
언어 가져오기: Microsoft Translator가 지원하는 모든 언어를 검색합니다.

#### <a name="input-properties"></a>입력 속성
없음

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| Code |문자열 |아니요 | |
| 이름 |문자열 |아니요 | |

### <a name="translate"></a>Translate
텍스트 번역: Microsoft Translator를 사용하여 지정된 언어로 텍스트를 번역합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 쿼리 |문자열 |예 |번역할 텍스트 |
| languageTo |문자열 |예 |대상 언어 코드(예: 'fr') |
| languageFrom |문자열 |아니요 |원본 언어(제공되지 않을 경우 Microsoft Translator는 자동 검색을 시도함)(예: en) |
| 범주 |문자열 |아니요 |번역 범주(기본값: '일반') |

#### <a name="output-properties"></a>출력 속성
없음

### <a name="detect"></a>검색
언어 검색: 지정된 텍스트의 원본 언어를 검색합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 쿼리 |문자열 |예 |식별할 언어가 있는 텍스트 |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| Code |문자열 |아니요 | |
| 이름 |문자열 |아니요 | |

### <a name="speechlanguages"></a>SpeechLanguages
음성 언어 가져오기: 음성 합성에 사용할 수 있는 언어를 검색합니다.

#### <a name="input-properties"></a>입력 속성
없음

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| Code |문자열 |아니요 | |
| 이름 |문자열 |아니요 | |

### <a name="texttospeech"></a>TextToSpeech
텍스트를 음성으로 변환: 지정된 텍스트를 웨이브 형식의 오디오 스트림 음성으로 변환합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 쿼리 |문자열 |예 |변환할 텍스트 |
| 언어 |문자열 |예 |음성을 생성할 언어 코드(예: 'en-us') |

#### <a name="output-properties"></a>출력 속성
없음

## <a name="helpful-links"></a>유용한 링크
[사용 가능한 연결](../connections-list.md)을 모두 보세요.  
앱에 [연결을 추가](../add-manage-connections.md)하는 방법을 알아보세요.

