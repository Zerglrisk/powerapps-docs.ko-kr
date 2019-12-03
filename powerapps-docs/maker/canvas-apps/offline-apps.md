---
title: 오프라인에서 사용 가능한 캔버스 앱 개발 | Microsoft Docs
description: 온라인에 있든 오프라인에 있든 사용자 생산성을 유지할 수 있도록 오프라인에서 사용 가능한 캔버스 앱을 개발합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1dbf192664f2c8a812650b487a9931de0160eeab
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675528"
---
# <a name="develop-offline-capable-canvas-apps"></a>오프라인에서 사용 가능한 캔버스 앱 개발

모바일 사용자는 연결을 제한 하거나 연결 되지 않은 경우에도 생산성을 유지 해야 하는 경우가 많습니다. 캔버스 앱을 빌드하는 경우 다음 작업을 수행할 수 있습니다.

- Power Apps Mobile을 열고 오프 라인일 때 앱을 실행 합니다.
- [연결](../canvas-apps/functions/signals.md#connection) 신호 개체를 사용하여 앱이 오프라인 상태인지, 온라인 상태인지, 요금제 연결인지를 확인합니다.
- [컬렉션](../canvas-apps/create-update-collection.md)을 사용하고 오프라인에서 기본 데이터 스토리지에 [LoadData 및 SaveData](../canvas-apps/functions/function-savedata-loaddata.md)와 같은 기능을 활용합니다.

## <a name="limitations"></a>제한 사항

**LoadData** 및 **savedata** 는 결합 되어 작은 양의 데이터를 로컬 장치에 저장 하는 간단한 메커니즘을 형성 합니다. 이러한 기능을 사용 하 여 간단한 오프 라인 기능을 앱에 추가할 수 있습니다.

이러한 함수는 메모리 내 컬렉션에서 작동 하기 때문에 사용 가능한 앱 메모리의 양에 따라 제한 됩니다. 사용 가능한 메모리는 장치, 운영 체제, Power Apps Mobile에서 사용 하는 메모리 및 화면 및 컨트롤 측면에서 응용 프로그램의 복잡성에 따라 달라질 수 있습니다. 몇 메가바이트 이상의 데이터를 저장 하는 경우 응용 프로그램이 실행 될 것으로 예상 되는 장치에서 예상 시나리오로 앱을 테스트 합니다. 일반적으로 30-70 메가바이트의 사용 가능한 메모리가 있습니다.

또한 장치가 온라인 상태가 되 면 함수는 병합 충돌을 자동으로 해결 하지 않습니다. 식을 작성할 때 저장 되는 데이터와 다시 연결을 처리 하는 방법에 대 한 구성이 작성자에 게 있습니다.

오프 라인 기능에 대 한 업데이트는이 항목으로 돌아와서 [Power Apps 블로그](https://powerapps.microsoft.com/blog/)를 구독 합니다.

## <a name="overview"></a>개요

오프 라인 시나리오를 설계할 때 먼저 앱에서 데이터를 사용 하는 방법을 고려해 야 합니다. Power Apps의 앱은 주로 플랫폼에서 제공 하는 [커넥터](../canvas-apps/connections-list.md) 집합 (예: SharePoint, Office 365 및 Common Data Service)을 통해 데이터에 액세스 합니다. 앱이 RESTful 엔드포인트를 제공하는 모든 서비스에 액세스할 수 있도록 사용자 지정 커넥터를 빌드할 수 있습니다. Web API 또는 Azure Functions와 같은 서비스일 수 있습니다. 이러한 모든 커넥터는 인터넷을 통해 HTTPS를 사용합니다. 즉, 사용자가 서비스에서 제공하는 데이터 및 모든 기능에 액세스하려면 온라인 상태여야 합니다.

![커넥터를 사용 하는 파워 앱 앱](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>오프라인 데이터 처리

Power Apps에서 데이터 원본에 관계 없이 일관 된 방식으로 데이터를 필터링, 검색, 정렬, 집계 및 조작할 수 있습니다. 소스는 응용 프로그램의 메모리 내 컬렉션에서 SharePoint 목록으로 SQL database 및 Common Data Service에 이르기까지 다양 합니다. 이러한 일관성 때문에 다른 데이터 원본을 사용 하도록 앱을 쉽게 변경할 수 있습니다. 더 중요 한 것은 오프 라인 시나리오의 경우 응용 프로그램 논리를 거의 변경 하지 않고 데이터 관리에 로컬 컬렉션을 사용할 수 있다는 것입니다. 실제로 로컬 컬렉션은 오프라인 데이터를 처리하기 위한 기본 메커니즘입니다.

## <a name="build-an-offline-app"></a>오프 라인 앱 빌드

앱 개발의 오프 라인 측면에 중점을 두기 위해이 항목에서는 Twitter에 초점을 맞춘 간단한 시나리오를 설명 합니다. 사용자가 오프 라인 상태에서 Twitter 게시물을 읽고 트 윗을 제출할 수 있도록 하는 앱을 빌드합니다. 앱이 온라인 상태가 되면 앱은 트윗을 게시하고 로컬 데이터를 다시 로드합니다.

상위 수준에서 앱은 다음 작업을 수행 합니다.

- 사용자가 앱을 열 때:

  - 장치가 온라인 상태인 경우 앱은 Twitter 커넥터를 통해 데이터를 인출 하 고 컬렉션을 해당 데이터로 채웁니다.
  - 장치가 오프 라인 상태인 경우 앱은 [**LoadData**](../canvas-apps/functions/function-savedata-loaddata.md) 함수를 사용 하 여 로컬 캐시 파일에서 데이터를 로드 합니다.
  - 사용자가 트 윗를 제출할 수 있습니다. 앱이 온라인 상태 이면 트 윗를 Twitter에 직접 게시 하 고 로컬 캐시를 새로 고칩니다.

- 앱이 온라인 상태인 동안 5 분 마다:

  - 앱은 로컬 캐시에 모든 트 윗을 게시 합니다.
  - 앱은 로컬 캐시를 새로 고치고 [**Savedata**](../canvas-apps/functions/function-savedata-loaddata.md) 함수를 사용 하 여 저장 합니다.

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>1 단계: 빈 휴대폰 앱에 Twitter 추가

1. Power Apps 스튜디오에서 **파일** > **새로 만들기**를 선택 합니다.
1. **빈 앱** 타일에서 **전화 레이아웃**을 선택합니다.
1. **보기**에서 **데이터 원본**을 선택합니다.
1. **데이터** 창에서 **데이터 원본 추가**를 선택 합니다.
1. **새 연결** > **Twitter** > **만들기**를 선택 합니다.
1. 자격 증명을 입력 하 고, 연결을 만든 다음, **데이터** 창을 닫습니다.

### <a name="step-2-collect-existing-tweets"></a>2 단계: 기존 트 윗 수집

1. **트리 뷰** 창에서 **앱**을 선택 하 고 **OnStart** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    ```

    > [!div class="mx-imgBorder"]
    > 트 윗](./media/offline-apps/load-tweets.png)를 로드 하 ![수식

1. **트리 뷰** 창에서 **앱** 개체에 대 한 줄임표 메뉴를 선택 하 고 **OnStart 실행** 을 선택 하 여 해당 수식을 실행 합니다.

    > [!div class="mx-imgBorder"]
    > 트 윗](./media/offline-apps/load-tweets-run.png)를 로드 하 ![수식을 실행 합니다.

    > [!NOTE]
    > 브라우저에서 지원 하지 않기 때문에 **LoadData** 및 **Savedata** 함수는 Power Apps 스튜디오에서 오류를 표시할 수 있습니다. 그러나 장치에이 앱을 배포한 후에는 정상적으로 수행 됩니다.

이 수식은 장치가 온라인 상태 인지 여부를 확인 합니다.

- 장치가 온라인 상태인 경우 수식은 검색 용어 "PowerApps"를 **LocalTweets** 컬렉션으로 최대 10 트 윗 로드 합니다.
- 장치가 오프 라인인 경우 수식은 "LocalTweets" 라는 파일에서 로컬 캐시를 로드 합니다 (사용할 수 있는 경우).

### <a name="step-3-show-tweets-in-a-gallery"></a>3 단계: 갤러리에 트 윗 표시

1. **삽입** 탭에서 **갤러리** > **빈 높이**를 선택 합니다.

1. [**갤러리**](controls/control-gallery.md) 컨트롤의 **Items** 속성을 `LocalTweets`로 설정 합니다.

1. 갤러리 템플릿에서 세 개의 [**레이블**](controls/control-text-box.md) 컨트롤을 추가 하 고 각 레이블의 **Text** 속성을 다음 값 중 하나로 설정 합니다.

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. 갤러리를이 예제와 비슷하게 하기 위해 마지막 레이블의 텍스트를 굵게 표시 합니다.

    > [!div class="mx-imgBorder"]
    > 샘플 트 윗](./media/offline-apps/tweet-gallery.png)를 보여 주는 ![갤러리

### <a name="step-4-show-connection-status"></a>4 단계: 연결 상태 표시

1. 갤러리에서 레이블을 삽입 한 다음 **Color** 속성을 **Red**로 설정 합니다.

1. 최신 레이블의 **Text** 속성을 다음 수식으로 설정 합니다.

    `If( Connection.Connected, "Connected", "Offline" )`

이 수식은 장치가 온라인 상태 인지 여부를 확인 합니다. 표시 되는 경우 레이블이 **연결 됨**을 표시 합니다. 그렇지 않으면 **오프 라인으로**표시 됩니다.

### <a name="step-5-add-a-box-to-compose-tweets"></a>5 단계: 트 윗를 작성 하는 상자 추가

1. 연결 상태 레이블에서 [**텍스트 입력**](controls/control-text-input.md) 컨트롤을 삽입 하 고 이름을 **NewTweetTextInput**로 바꿉니다.

1. 텍스트 입력 상자의 **기본** 속성을 `""`로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 상태 정보 및 텍스트 입력 상자](./media/offline-apps/status-input.png) 갤러리를 ![합니다.

### <a name="step-6-add-a-button-to-post-the-tweet"></a>6 단계: 트 윗을 게시 하는 단추 추가

1. 텍스트 입력 상자에서 **단추** 컨트롤을 추가 하 고 **text** 속성을 다음 값으로 설정 합니다.

    `"Tweet"`

1. 단추의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. **앱**에 대 한 **OnStart** 속성에서 수식의 끝에 줄을 추가 합니다.

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 100} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    LoadData( LocalTweetsToPost, "LocalTweetsToPost", true );  // added line
    ```

    > [!div class="mx-imgBorder"]
    > 주석 처리가 제거 line](./media/offline-apps/load-tweets-save.png)를 사용 하 여 트 윗를 로드 하 ![수식을 실행 합니다.

이 수식은 장치가 온라인 상태 인지 여부를 확인 합니다.

- 장치가 온라인 상태 이면 트 윗를 즉시 게시 합니다.
- 장치가 오프 라인 상태인 경우에는 **LocalTweetsToPost** 컬렉션에서 트 윗를 캡처하여 장치에 저장 합니다.

그런 다음 수식에서 텍스트 입력 상자의 텍스트를 다시 설정 합니다.

### <a name="step-7-check-for-new-tweets"></a>7 단계: 새 트 윗 확인

1. 단추 오른쪽에 **타이머** 컨트롤을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 최종 앱 ![](./media/offline-apps/final-app.png)

1. 타이머의 **Duration** 속성을 **30만**으로 설정 합니다.

1. 타이머의 **자동** 시작 및 **반복** 속성을 **true**로 설정 합니다.

1. 타이머의 **Ontimerend** 를 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

이 수식은 장치가 온라인 상태 인지 여부를 확인 합니다. 인 경우 앱은 **LocalTweetsToPost** collection의 모든 항목을 트 윗 다음 컬렉션을 지웁니다.

## <a name="test-the-app"></a>앱 테스트

1. 인터넷에 연결 된 모바일 장치에서 앱을 엽니다.

    기존 트 윗 갤러리에 표시 되 고 상태에는 **연결 됨**이 표시 됩니다.

1. 장치의 비행기 모드를 사용 하도록 설정 하 고 wi-fi를 사용 하지 않도록 설정 하 여 인터넷에서 장치 연결을 끊습니다.

    상태 레이블은 앱이 **오프 라인 상태임**을 표시 합니다.

1. 장치가 오프 라인 상태인 동안 **PowerApps**를 포함 하는 트 윗을 작성 한 다음 **트 윗** 단추를 선택 합니다.

    트 윗는 **LocalTweetsToPost** 컬렉션에 로컬로 저장 됩니다.

1. 장치의 비행기 모드를 사용 하지 않도록 설정 하 고 wi-fi를 사용 하도록 설정 하 여 장치를 인터넷에 다시 연결 합니다.

    5 분 이내에 앱은 갤러리에 표시 되는 트 윗을 게시 합니다.

이 문서에서는 Power Apps에서 오프 라인 앱을 빌드하기 위한 기능을 설명 하는 것이 좋습니다. 언제 든 지 [포럼](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) 에 피드백을 제공 하 고 [Power apps 커뮤니티 블로그에서](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog)오프 라인 앱의 예제를 공유 하세요.