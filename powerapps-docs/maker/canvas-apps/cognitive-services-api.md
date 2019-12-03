---
title: Power Apps에서 Cognitive Services 사용 | Microsoft Docs
description: Azure Cognitive Services 텍스트 분석 API를 사용 하 여 텍스트를 분석 하는 기본 캔버스 앱을 빌드합니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/08/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1860320715798d1e3acc72af7f158f91b8f3cd0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724364"
---
# <a name="use-cognitive-services-in-power-apps"></a>Power Apps에서 Cognitive Services 사용
이 문서에서는 [Azure Cognitive Services 텍스트 분석 API](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview) 를 사용 하 여 텍스트를 분석 하는 기본 캔버스 앱을 빌드하는 방법을 보여 줍니다. Text Analytics API를 설정하고 [Text Analytics 커넥터](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/)와 연결하는 방식을 보여주고, 그런 다음, API를 호출하는 캔버스 앱을 빌드하는 방법을 살펴보겠습니다.

> [!NOTE]
> Power Apps에서 앱을 처음 빌드하는 경우이 문서를 살펴보기 전에 [앱을 처음부터 새로 만드는](get-started-create-from-blank.md) 것이 좋습니다.

## <a name="introduction-to-azure-cognitive-services"></a>Azure Cognitive Services 소개
Azure Cognitive Services는 응용 프로그램을 더 지능적이 고, 사용 하 고, 검색 가능 하 게 만드는 데 사용할 수 있는 Api, Sdk 및 서비스 집합입니다. 이 서비스를 통해 사용자는 지능형 기능(예: 감정 및 비디오 감지, 안면, 음성 및 시각 인식, 음성 및 언어 이해)을 애플리케이션에 쉽게 추가할 수 있습니다.

이 문서에서는 Text Analytics API에 사용할 수 있는 "언어 이해"에 초점을 맞추려고 합니다. 이 API를 통해 사용자는 텍스트에서 감정, 핵심 구, 토픽 및 언어를 검색할 수 있습니다. API 데모를 사용해 본 다음, 미리 보기 버전을 등록하여 시작해 보겠습니다.

### <a name="try-out-the-text-analytics-api"></a>Text Analytics API 사용해 보기
API에는 온라인 데모가 있어 작동 방식을 보고 서비스에서 반환하는 JSON을 살펴볼 수 있습니다.

1. [Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) 페이지로 이동합니다.

2. **실제 동작 확인** 섹션에서 예제 텍스트를 사용하거나 직접 텍스트를 입력합니다. 그런 다음 **분석**을 클릭하거나 탭합니다. 
   
    ![Text Analytics API 데모](./media/cognitive-services-api/text-analytics-demo.png)

3. 이 페이지에서는 **분석 된 텍스트** 탭의 서식이 지정 된 결과와 **JSON 탭의 json 응답** 을 보여 줍니다. [json](https://json.org/) 은 데이터를 표현 하는 방법입니다 .이 경우에는 텍스트 분석 API에서 반환 된 데이터입니다.

## <a name="sign-up-for-the-text-analytics-api"></a>Text Analytics API를 등록합니다.
API는 무료 미리 보기로 사용 가능하며 Azure 구독과 연결되어 있습니다. Azure Portal을 통해 API를 관리합니다.

1. Azure 구독이 아직 없는 경우 [무료 구독에 등록](https://azure.microsoft.com/free/)합니다.

2. 이 [페이지](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics)에서이 이미지에 표시 된 텍스트 분석 API에 대 한 정보를 입력 합니다. **F0**(무료) 가격 책정 계층을 선택합니다.
   
    ![Text Analytics API 만들기](./media/cognitive-services-api/azure-create.png)

5. 왼쪽 아래 모서리에서 **만들기**를 클릭하거나 탭합니다.

6. **대시보드**에서 방금 사용자가 만든 API를 클릭하거나 탭합니다.
   
    ![Azure 대시보드](./media/cognitive-services-api/azure-dashboard.png)

7. **키**를 클릭하거나 탭합니다.
   
    ![Azure 메뉴](./media/cognitive-services-api/azure-menu-keys.png)

8. 화면 오른쪽에 있는 키 중 하나를 복사합니다. API에 대한 연결을 만들 때 나중에 이 키를 사용합니다.
   
    ![API 키](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>앱 빌드
텍스트 분석 API 이제 실행 중이 고, Power Apps에서 연결 하 고, API를 호출 하는 앱을 빌드합니다. Text Analytics API 페이지의 데모와 유사한 기능을 제공하는 단일 화면 앱입니다. 이제 빌드를 시작해 보겠습니다!

### <a name="create-the-app-and-add-a-connection"></a>앱 만들기 및 연결 추가
먼저, 빈 휴대폰 앱을 만들고 **Text Analytics** 커넥터와의 연결을 추가하겠습니다. 이러한 작업에 대 한 자세한 정보가 필요한 경우 [처음부터 앱 만들기](get-started-create-from-blank.md) 및 [Power Apps에서 연결 관리](add-manage-connections.md)를 참조 하세요.

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **비어 있는 상태에서 시작** > ![Phone 앱 아이콘](./media/cognitive-services-api/icon-phone-app.png)(휴대폰) > **이 앱 만들기**를 선택합니다.

    ![비어 있는 상태에서 시작](./media/cognitive-services-api/start-from-blank.png)

2. Power Apps 스튜디오의 가운데 창에서 **데이터에 연결**을 선택 합니다.

3. **데이터** 창에서 **새 연결** > **텍스트 분석**을 클릭하거나 탭합니다.

4. 키를 **계정 키**에 복사한 다음, **만들기**를 클릭하거나 탭합니다.
   
    ![Text Analytics 커넥터](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>앱에 컨트롤 추가
앱을 만드는 다음 단계는 모든 컨트롤을 추가하는 것입니다. 일반적으로 앱을 빌드할 때 저는 진행하면서 컨트롤에 수식을 추가하지만, 이 경우에서는 먼저 컨트롤에 집중한 후 다음 섹션에서 몇 개의 수식을 추가하려고 합니다. 다음 이미지는 모든 컨트롤이 포함된 앱을 보여줍니다.

![완료된 앱](./media/cognitive-services-api/finished-app-no-data.png)

아래 단계에 따라 이 화면을 만듭니다. 컨트롤 이름이 지정되면 해당 이름은 다음 섹션의 수식에 사용됩니다.

1. **홈** 탭에서 **새 화면**, **스크롤 가능 화면**을 차례로 클릭하거나 탭합니다. 

2. **Screen2**에서 **[Title]** 을 선택하고 **텍스트 분석**으로 변경합니다.

3. 소개 텍스트에 대한 **레이블** 컨트롤을 추가합니다.

4. 분석할 텍스트를 입력할 수 있도록 **텍스트 입력** 컨트롤을 추가합니다. 컨트롤 이름을 **tiTextToAnalyze**로 변경합니다. 앱은 이제 다음 이미지와 같습니다.
   
    ![제목, 부제목 및 텍스트 입력이 있는 앱](./media/cognitive-services-api/partial-app-step1.png)

5. 수행할 API 작업을 선택할 수 있도록 세 개의 **확인란** 컨트롤을 추가합니다. 컨트롤 이름을 **chkLanguage**, **chkPhrases** 및 **chkSentiment**로 지정합니다.

6. 수행할 작업을 선택한 후 API를 호출할 수 있도록 단추를 추가합니다. 앱은 이제 다음 이미지와 같습니다.
   
    ![확인란과 단추가 있는 앱](./media/cognitive-services-api/partial-app-step2.png)

7. 세 개의 **레이블** 컨트롤을 추가합니다. 처음 두 개는 언어와 감정 API 호출의 결과를 포함하고 세 번째는 화면 맨 아래에 있는 갤러리에 대한 소개에 불과합니다.

8. **비어 있는 세로 갤러리** 컨트롤을 추가한 다음 **레이블** 컨트롤을 갤러리에 추가합니다. 이 갤러리에는 핵심 문구 API 호출의 결과가 저장됩니다. 앱은 이제 다음 이미지와 같습니다.
   
    ![갤러리 및 레이블이 있는 앱](./media/cognitive-services-api/partial-app-step3.png)

9. 왼쪽 창에서 **Screen1** > 줄임표( **. . .** ) > **삭제**를 선택합니다(앱에는 이 화면이 필요하지 않음).

Text Analytics API 호출에 집중하기 위해 이 앱을 단순하게 유지하고 있지만, 선택한 확인란에 따라 컨트롤을 표시하고 숨기는 논리, 사용자가 옵션을 선택하지 않을 경우 오류 처리 등을 추가할 수 있습니다.

### <a name="add-logic-to-make-the-right-api-calls"></a>올바른 API 호출을 하도록 논리 추가
자, 좋아 보이지만 아직 아무것도 수행하지 않는 앱이 있습니다. 잠시 후 해결해 보겠습니다. 하지만 세부 정보를 살펴 보기 전에 앱이 따르는 패턴을 알아보겠습니다.

1. 이 앱은 앱에서 선택한 확인란에 따라 특정 API 호출을 합니다. **텍스트 분석**을 클릭하거나 탭하면 이 앱은 1, 2 또는 3개의 API 호출을 수행합니다.

2. 이 앱은 API에서 반환하는 데이터를 세 가지 다른 [컬렉션](working-with-variables.md#use-a-collection)(예: **languageCollect**, **sentimentCollect** 및 **phrasesCollect**)에 저장합니다.

3. 이 앱은 세 개의 컬렉션에 있는 항목을 기반으로 두 개의 레이블에 대한 **Text** 속성과 갤러리의 **Items** 속성을 업데이트합니다.

이러한 배경을 가지고 단추의 **OnSelect** 속성에 대한 수식을 추가해 보겠습니다. 마술과 같은 일이 벌어집니다.

```powerapps-dot
If( chkLanguage.Value = true,
    ClearCollect( languageCollect, 
        TextAnalytics.DetectLanguage(
            {
                numberOfLanguagesToDetect: 1, 
                text: tiTextToAnalyze.Text
            }
        ).detectedLanguages.name
    )
);

If( chkPhrases.Value = true,
    ClearCollect( phrasesCollect, 
        TextAnalytics.KeyPhrases(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).keyPhrases
    )
);

If( chkSentiment.Value = true,
    ClearCollect( sentimentCollect, 
        TextAnalytics.DetectSentiment(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).score
    )
)
```

여기서 약간 자세히 살펴 보겠습니다.

* **If** 명령문은 직관적입니다. 특정 확인란을 선택한 경우 해당 작업에 대해 API 호출을 합니다.

* 각 호출 내에서 적합한 매개 변수를 지정합니다.

  * 세 개의 호출 모두에서 **tiTextToAnalyze.Text**를 입력 텍스트로 지정합니다.

  * **DetectLanguage()** 에서 **numberOfLanguagesToDetect**는 1로 하드 코딩되지만, 앱의 일부 논리에 따라 이 매개 변수를 전달할 수 있습니다.

  * **KeyPhrases ()** 및 **DetectSentiment ()** 에서 **언어** 는 "en"으로 하드 코딩 되지만, 앱의 일부 논리에 따라이 매개 변수를 전달할 수 있습니다. 예를 들어 언어를 먼저 감지한 다음, **DetectLanguage()** 에서 반환하는 내용에 따라 이 매개 변수를 설정할 수 있습니다.

* 각 호출에 대해 결과를 적합한 컬렉션에 추가합니다.

    * **languageCollect**의 경우 텍스트에서 식별된 언어의 **이름**을 추가합니다.

    * **phrasesCollect**의 경우 텍스트에서 식별된 **keyPhrases**를 추가합니다.

    * **sentimentCollect**의 경우 텍스트에 대한 감정 **점수**를 0-1의 값으로 추가합니다(여기서 1은 100% 긍정임).

### <a name="display-the-results-of-the-api-calls"></a>API 호출의 결과 표시
API 호출의 결과를 표시하려면 각 컨트롤에서 적절한 컬렉션을 참조합니다.

1. 언어 레이블의 **Text** 속성을 다음으로 설정합니다: `"The language detected is " & First(languageCollect).name`.
   
    **First()** 함수는 **languageCollect**에서 첫 번째(그리고 이 사례에서 유일한) 레코드를 반환하며 해당 레코드와 연결된 **이름**(유일한 필드)을 표시합니다.

2. 감정 레이블의 **Text** 속성을 다음으로 설정합니다: `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)\*100 & "% positive."`.
   
    또한 이 수식은 **First()** 함수를 사용하고 첫 번째이자 유일한 레코드에서 **값**(0-1)을 가져온 후 백분율로 형식을 지정합니다.

3. 핵심 문구 갤러리의 **Items** 속성을 다음으로 설정합니다: `phrasesCollect`.
   
    이제 갤러리를 사용하므로 단일 값을 추출하기 위해 **First()** 함수가 필요하지 않습니다. 컬렉션을 참조하고, 갤러리는 핵심 구를 목록으로 표시합니다.

## <a name="run-the-app"></a>앱 실행

이제 앱이 완료되었으니 앱을 실행하여 어떻게 작동하는지 살펴봅니다. 오른쪽 상단의 실행 버튼을 클릭하거나 탭합니다. ![앱 실행](./media/cognitive-services-api/icon-run-app.png)줄임표(...)를 클릭한 다음 다음 이미지에서는 모두 세 개의 옵션이 선택되었으며 텍스트는 Text Analytics API 페이지의 기본 텍스트와 동일합니다.

![데이터가 있는 완성된 앱](./media/cognitive-services-api/finished-app.png)

이 문서의 시작 부분에서 Text Analytics API 페이지와 이 앱의 출력을 비교할 경우 같은 결과가 동일한 것을 볼 수 있습니다.

이제 Text Analytics API에 대해 좀 더 이해하고 앱으로 통합하는 방법을 확인하셨길 바랍니다. 문서에서 집중적으로 다뤘으면 하는 다른 Cognitive Services(또는 일반적으로 기타 서비스)가 있다면 저희에게 알려주세요. 늘 그렇듯이 의견에 피드백과 궁금한 점을 남겨 주시기 바랍니다.

