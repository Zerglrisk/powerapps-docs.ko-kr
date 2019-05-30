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
ms.openlocfilehash: 8004a39e83ea3615ce8a77637a9f5c0271b67781
ms.sourcegitcommit: 157ab15738e2d0d1bf9097bbb7b9e3d9c29a4015
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265800"
---
# <a name="develop-offline-capable-canvas-apps"></a>오프라인에서 사용 가능한 캔버스 앱 개발

모바일 사용자 생산성을 높이도록 할 경우가 제한 된 경우 또는 연결 되지 않은 합니다. 캔버스 앱을 빌드할 때 이러한 작업을 수행할 수 있습니다.

- PowerApps Mobile 열고 오프 라인 상태인 경우 앱을 실행 합니다.
- [연결](../canvas-apps/functions/signals.md#connection) 신호 개체를 사용하여 앱이 오프라인 상태인지, 온라인 상태인지, 요금제 연결인지를 확인합니다.
- [컬렉션](../canvas-apps/create-update-collection.md)을 사용하고 오프라인에서 기본 데이터 스토리지에 [LoadData 및 SaveData](../canvas-apps/functions/function-savedata-loaddata.md)와 같은 기능을 활용합니다.

## <a name="limitations"></a>제한 사항

**LoadData**와 **SaveData**는 결합하여 로컬 장치에 적은 양의 데이터를 저장하는 간단한 메커니즘을 형성합니다. 이러한 함수를 사용하여 앱에 간단한 오프라인 기능을 추가할 수 있습니다.

이러한 함수는 메모리 내 컬렉션에서 작동하기 때문에 사용 가능한 앱 메모리 양의 제한을 받습니다. 사용 가능한 메모리는 장치, 운영 체제, PowerApps Mobile이 사용하는 메모리 및 화면 및 컨트롤 측면에서의 앱의 복잡성에 따라 달라질 수 있습니다. 겨우 몇 메가바이트의 데이터를 저장하는 경우 예상 실행 장치에 필요한 시나리오를 사용하여 앱을 테스트합니다. 일반적으로 사용 가능한 메모리의 30-70 메가바이트 해야 합니다.

함수 수도 없는 자동으로 병합 충돌을 해결할 장치가 온라인 상태가 되 면 합니다. 저장 되는 데이터와 다시 연결을 처리 하는 방법에 대 한 구성 작성자 최대 경우 식을 작성 합니다.

오프 라인 기능에 대 한 업데이트를이 항목에 돌아와서 구독할 합니다 [PowerApps 블로그](https://powerapps.microsoft.com/blog/)합니다.

## <a name="overview"></a>개요

오프 라인 시나리오를 디자인할 때 데이터를 사용 하 여 앱이 어떻게 작동를 먼저 고려해 야 합니다. PowerApps에서 앱의 집합을 통해 데이터를 주로 액세스할 [커넥터](../canvas-apps/connections-list.md) SharePoint, Office 365 및 Common Data Service와 같은 플랫폼에서 제공 하는 합니다. 앱이 RESTful 엔드포인트를 제공하는 모든 서비스에 액세스할 수 있도록 사용자 지정 커넥터를 빌드할 수 있습니다. Web API 또는 Azure Functions와 같은 서비스일 수 있습니다. 이러한 모든 커넥터는 인터넷을 통해 HTTPS를 사용합니다. 즉, 사용자가 서비스에서 제공하는 데이터 및 모든 기능에 액세스하려면 온라인 상태여야 합니다.

![커넥터를 포함하는 PowerApps 앱](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>오프라인 데이터 처리

PowerApps에서 있습니다 수 필터링, 검색, 정렬, 집계 및 데이터 소스에 관계 없이 일관 된 방식으로 데이터를 조작 합니다. SharePoint 목록 SQL databases 및 Common Data Service에 앱에서 메모리 내 컬렉션에서 범위를 원본입니다. 쉽게이 일관성으로 인해 앱이 다른 데이터 원본을 사용 하 여 대상을 변경할 수 있습니다. 무엇 보다도 오프 라인 시나리오를 사용할 수 있습니다 로컬 컬렉션 데이터 관리를 위한 응용 프로그램의 논리를 거의 변경 하지 않고 있습니다. 실제로 로컬 컬렉션은 오프라인 데이터를 처리하기 위한 기본 메커니즘입니다.

## <a name="build-an-offline-app"></a>오프 라인 앱 빌드

앱 개발의 오프 라인 측면에 초점을를이 항목에서는 Twitter에 기반한 간단한 시나리오를 보여 줍니다. Twitter 게시물을 읽고, 동시에 오프 라인 트 윗을 제출할 수 있는 앱을 빌드합니다. 앱이 온라인 상태가 되면 앱은 트윗을 게시하고 로컬 데이터를 다시 로드합니다.

높은 수준에서 앱이이 작업을 수행합니다.

- 사용자가 앱을 열 때:

  - 장치가 온라인 상태인 경우 앱에서 Twitter 커넥터를 통해 데이터를 인출 하 고 해당 데이터를 사용 하 여 컬렉션을 채웁니다.
  - 장치가 오프 라인 상태인 경우 앱 데이터를 로컬 캐시 파일에서 사용 하 여 로드 된 [ **LoadData** ](../canvas-apps/functions/function-savedata-loaddata.md) 함수입니다.
  - 사용자는 트 윗을 제출할 수 있습니다. 앱이 온라인 상태인 경우 직접 Twitter에 트 윗을 게시 하 고 로컬 캐시를 새로 고칩니다.

- 5 분 마다 앱 온라인 상태일 때:

  - 앱의 로컬 캐시에서 모든 트 윗을 게시합니다.
  - 앱 로컬 캐시 새로 고침 및 사용 하 여 저장 합니다 [ **SaveData** ](../canvas-apps/functions/function-savedata-loaddata.md) 함수입니다.

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>1 단계: 비어 있는 휴대폰 앱에 Twitter 추가

1. PowerApps Studio 선택 **파일** > **새로 만들기**합니다.
1. **빈 앱** 타일에서 **전화 레이아웃**을 선택합니다.
1. **보기**에서 **데이터 원본**을 선택합니다.
1. 에 **데이터** 창 **데이터 원본 추가**합니다.
1. 선택 **새 연결** > **Twitter** > **만들기**합니다.
1. 자격 증명을 입력 한 연결을 만들고 다음 닫습니다 합니다 **데이터** 창입니다.

### <a name="step-2-collect-existing-tweets"></a>2단계: 기존 트 윗을 수집

1. 에 **트리 뷰에서** 창 **앱**를 설정한 후 해당 **OnStart** 속성을 다음이 수식:

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
    > ![트 윗을 로드 하는 수식](./media/offline-apps/load-tweets.png)

1. **트리 보기** 창에 대 한 줄임표 메뉴를 선택는 **앱** 개체를 선택한 후 **OnStart 실행** 해당 수식을 실행 합니다.

    > [!div class="mx-imgBorder"]
    > ![트 윗을 로드 하는 수식을 실행 합니다.](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > 합니다 **LoadData** 하 고 **SaveData** 브라우저를 지원 하지 않으므로 함수 PowerApps Studio 오류가 표시 될 수 있습니다. 그러나에서는 수행 하며 일반적으로 장치에이 앱을 배포한 후 합니다.

이 수식은 장치가 온라인 인지 여부를 확인 합니다.

- 장치가 온라인 상태인 경우 수식을 로드 검색어 "PowerApps"를 사용 하 여 최대 10 개의 트 윗을 **LocalTweets** 컬렉션입니다.
- 장치가 오프 라인 상태인 경우 수식을 사용할 수 있으면 "LocalTweets" 라는 파일에서 로컬 캐시를 로드 합니다.

### <a name="step-3-show-tweets-in-a-gallery"></a>3단계: 갤러리에서 트 윗을 보여 줍니다.

1. 에 **삽입** 탭을 선택 **갤러리** > **유연한 높이 비워 두면**합니다.

1. 설정 합니다 **항목** 의 속성을 [ **갤러리** ](controls/control-gallery.md) 컨트롤을 `LocalTweets`입니다.

1. 갤러리 템플릿 3 개를 추가 [ **레이블을** ](controls/control-text-box.md) 컨트롤을 설정 하 고는 **텍스트** 다음이 값 중 하나에 각 레이블의 속성:

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. 텍스트를 굵게 마지막 레이블에 갤러리에는이 예제와 유사 합니다.

    > [!div class="mx-imgBorder"]
    > ![샘플 트 윗을 보여 주는 갤러리](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>4단계: 연결 상태를 표시 합니다.

1. 갤러리 아래의 레이블을 넣고 설정한 해당 **Color** 속성을 **Red**합니다.

1. 최신 레이블 설정 **텍스트** 속성을 다음이 수식:

    `If( Connection.Connected, "Connected", "Offline" )`

이 수식은 장치가 온라인 인지 여부를 결정 합니다. 이 경우 레이블을 **연결 됨**이 고, 그렇지 않으면 표시 **오프 라인**.

### <a name="step-5-add-a-box-to-compose-tweets"></a>5단계: 트 윗을 작성 하는 상자를 추가 합니다.

1. 연결 상태 레이블 아래 삽입을 [ **텍스트 입력** ](controls/control-text-input.md) 컨트롤을 바꾸거나 **NewTweetTextInput**합니다.

1. 텍스트 입력 상자를 설정 **기본** 속성을 `""`입니다.

    > [!div class="mx-imgBorder"]
    > ![상태 정보 및 텍스트 입력 상자는 갤러리](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>6단계: 트윗을 게시하는 단추 추가

1. 텍스트 입력 상자 아래에 추가 된 **단추** 설정 해당 **텍스트** 속성을이 값:

    `"Tweet"`

1. 설정 단추 **OnSelect** 속성을 다음이 수식:

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. 에 **OnStart** 에 대 한 속성을 **앱**, 수식의 끝 줄을 추가:

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
    > ![주석 처리가 제거 된 줄을 사용 하 여 트 윗을 로드 하는 수식을 실행 합니다.](./media/offline-apps/load-tweets-save.png)

이 수식은 장치가 온라인 인지 여부를 결정 합니다.

- 장치가 온라인 상태인 경우 트 윗 즉시 게시 합니다.
- 트 윗을 캡처하고 장치가 오프 라인 상태인 경우는 **LocalTweetsToPost** 컬렉션 장치에 저장 합니다.

다음 수식은 텍스트 입력 상자에 텍스트를 다시 설정합니다.

### <a name="step-7-check-for-new-tweets"></a>7단계: 새 트 윗에 대 한 확인

1. 단추 오른쪽에 추가 된 **타이머** 제어 합니다.

    > [!div class="mx-imgBorder"]
    > ![최종 앱](./media/offline-apps/final-app.png)

1. 타이머를 설정할 **기간** 속성을 **300000**합니다.

1. 타이머를 설정할 **AutoStart** 하 고 **반복** 속성을 **true**합니다.

1. 타이머를 설정할 **OnTimerEnd** 을 다음이 수식으로:

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

이 수식은 장치가 온라인 인지 여부를 결정 합니다. 앱의 모든 항목을 트 윗 인 경우는 **LocalTweetsToPost** 컬렉션 컬렉션을 지웁니다.

## <a name="test-the-app"></a>앱 테스트

1. 인터넷에 연결 된 모바일 장치에서 앱을 엽니다.

    기존 트 윗 갤러리에 표시 되 고 상태가 **Connected**합니다.

1. 장치의 비행기 모드를 사용 하도록 설정 하 고 wifi를 사용 하지 않도록 설정 하 여 인터넷에서 장치를 분리 합니다.

    상태 레이블 앱 임을 보여 줍니다 **오프 라인**합니다.

1. 장치가 오프 라인 상태인 동안 쓰기를 포함 하는 트 윗 **PowerApps**를 선택한 후 합니다 **트 윗** 단추입니다.

    트 윗에서 로컬로 저장 되는 **LocalTweetsToPost** 컬렉션입니다.

1. 장치의 비행기 모드를 사용 하지 않도록 설정 하 고 wifi를 사용 하도록 설정 하 여 인터넷에 장치를 다시 연결 합니다.

    5 분 내에 앱 갤러리에 표시 되는 트 윗을 게시 합니다.

이 문서를 통해 오프라인 앱을 빌드하기 위해 PowerApps에 있는 기능을 살펴보세요. 언제든지 [포럼](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1)에 피드백을 보내고 [PowerApps 커뮤니티 블로그](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog)에서 오프라인 앱의 예제를 공유해 주세요.