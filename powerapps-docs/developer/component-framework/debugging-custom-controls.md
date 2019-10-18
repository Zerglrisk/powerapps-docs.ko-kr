---
title: 디버그 코드 구성 요소 | MicrosoftDocs
description: Fiddler 및 네이티브 디버깅을 사용 하 여 코드 구성 요소를 디버깅 하는 방법
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 088792a32f401ddaf7d3a3cd4fd4d5aa9fa472ff
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346926"
---
# <a name="debug-code-components"></a>디버그 코드 구성 요소

코드 구성 요소 논리를 구현 하는 작업이 완료 되 면 `npm start` 명령을 사용 하 여 코드 구성 요소 테스트 및 디버깅을 시작할 수 있습니다. 그러면 코드 구성 요소가 빌드되고 로컬 테스트 도구에서 열립니다.

> [!div class="mx-imgBorder"]
> ![테스트 도구 1](media/test-harness-1.png "테스트 도구 1")

위의 이미지에 표시 된 것 처럼 브라우저 창은 네 개의 섹션으로 열립니다. 오른쪽 창에 **컨텍스트 입력**, **데이터 입력**및 **출력** 섹션이 있는 동안 코드 구성 요소가 왼쪽 창에 렌더링 됩니다.

- **컨텍스트 입력** 은 폼 팩터를 지정 하 고 각 폼 팩터 (web, 태블릿, phone)를 사용 하 여 코드 구성 요소를 테스트 하는 방법을 제공 합니다. 이는 코드 구성 요소가 특정 폼 팩터 기능에 종속 된 경우에 유용 합니다.
- **데이터 입력** 은 [매니페스트](manifest-schema-reference/manifest.md) 파일에 정의 된 모든 속성과 해당 [형식](manifest-schema-reference/types.md) 또는 [형식 그룹](manifest-schema-reference/type-group.md) 을 표시 하는 대화형 UI입니다. 이를 통해 각 속성에 대 한 모의 데이터에서 키를 사용할 수 있습니다. 
- **출력** 은 구성 요소의 [getoutputs](reference/control/getoutputs.md) 메서드가 호출 될 때마다 출력을 렌더링 합니다.  

     > [!div class="mx-imgBorder"]
     > ![테스트 도구 2](media/test-harness-2.png "테스트 도구 2")

> [!NOTE]
> @No__t_0 파일을 수정 하거나 추가 속성을 만들려는 경우 입력 섹션에 표시 되기 전에 디버그 프로세스를 다시 시작 해야 합니다.

## <a name="test-code-components-with-mock-data"></a>모의 데이터를 사용 하 여 코드 구성 요소 테스트

- *필드* 형식 구성 요소에 대해 다음과 같이 **controlmanifest. input .xml** 에 정의 된 모든 속성에 대해 값을 입력 하 고 형식을 입력할 수 있습니다.

   > [!div class="mx-imgBorder"]
   > ![테스트 도구 2.5](media/test-harness-2.5.png "테스트 도구 2.5")

- *데이터 집합* 형식 구성 요소의 경우 테스트 데이터를 사용 하 여 CSV 파일을 로드할 수 있습니다. 사용자 환경에서 직접 .csv 형식을 수동으로 만들거나 내보낼 수 있습니다. 유효한 CSV 파일을 사용할 수 있게 되 면 다음과 같이 로드할 수 있습니다.

   > [!div class="mx-imgBorder"]
   > ![테스트 도구 3](media/test-harness-3.png "테스트 도구 3")

- CSV 파일을 로드 한 후에는 **Controlmanifest** 에 정의 된 각 속성을 csv 파일의 열에 바인딩합니다. 이렇게 하려면 다음과 같이 각 속성에 대 한 열을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![테스트 도구 4](media/test-harness-4.png "테스트 도구 4")

- **Controlmanifest. Input .xml** 파일에 정의 된 속성이 없으면 모든 열이 자동으로 테스트 도구에 로드 됩니다.

   > [!div class="mx-imgBorder"]
   > ![테스트 도구 5](media/test-harness-5.png "테스트 도구 5")


## <a name="watch-mode-in-test-harness"></a>테스트 도구의 조사식 모드

테스트 도구는 PowerApps 구성 요소 프레임 워크 프로젝트의를 활용할 수 있는 `watch` 모드를 지원 합니다. @No__t_0 모드를 사용 하도록 설정 하려면 명령 `npm start watch`를 사용 하 여 테스트 도구를 시작 합니다. @No__t_0 모드에서 다음 구성 요소 자산에 대 한 변경 내용은 다시 시작 하지 않고 테스트 도구에 자동으로 반영 됩니다.

1.  `index.ts` 파일입니다.
2.  `ControlManifest.Input.xml` 파일입니다.
3.  @No__t_0에서 가져온 라이브러리.
4.  매니페스트 파일에 나열 된 모든 리소스

## <a name="debug-code-components-using-native-browsers"></a>네이티브 브라우저를 사용 하 여 코드 구성 요소 디버깅

브라우저의 디버깅 기능을 사용 하 여 구성 요소 동작을 관찰할 수 있습니다. 각 브라우저는 브라우저에서 기본적으로 코드를 디버그 하는 데 도움이 되는 디버깅 도구를 제공 합니다. 일반적으로 디버깅에 사용 되는 네이티브 개발자 도구를 표시 하려면 **F12** 키를 눌러 브라우저에서 디버깅을 활성화할 수 있습니다.

예를 들어 **Microsoft Edge**에서 다음을 수행 합니다.

- **F12** 키를 눌러 검사기를 엽니다.
- 구성 요소를 선택 합니다.
- 위쪽 막대에서 **디버거** 로 이동한 다음 검색 표시줄의 매니페스트 파일에 설명 된 구성 요소 이름을 검색 합니다. 예를 들어 `Hello World component`와 같은 구성 요소 이름을 입력 합니다.

     > [!div class="mx-imgBorder"]
     > ![디버그 구성]요소(media/debug-control.png "디버그 구성 요소")

> [!NOTE]
> [Init](reference/control/init.md) 및 [updateview](reference/control/updateview.md)와 같은 구성 요소의 수명 주기 메서드에 중단점을 설정 하는 것이 항상 좋은 방법입니다.

다음과 같이 *소스* 탭에서 중단점을 설정 하 여 실시간으로 구성 요소와 상호 작용 하 고 DOM의 요소를 관찰할 수도 있습니다.

> [!div class="mx-imgBorder"]
> ![디버그 구성]요소(media/debug-control-1.png "디버그 구성 요소 1")

## <a name="fiddler-autoresponder"></a>Fiddler AutoResponder

Fiddler AutoResponder를 사용 하 여 코드 구성 요소를 신속 하 게 디버그할 수 있습니다. [Fiddler](https://www.telerik.com/download/fiddler) 를 설치 하 고 단계에 따라 [AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)를 구성 합니다.

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
