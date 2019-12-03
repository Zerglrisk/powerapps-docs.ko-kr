---
title: Twitter 연결 개요 | Microsoft Docs
description: Twitter에 연결하는 방법을 알아보고 몇 가지 예제를 진행하고, 모든 함수를 살펴봅니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/12/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 21effecae904675e39c914145ee10df9c81ec752
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679848"
---
# <a name="connect-to-twitter-from-powerapps"></a>PowerApps에서 Twitter 연결
![Twitter](./media/connection-twitter/twittericon.png)

Twitter를 사용하여 트윗을 보내고 Twitter 계정에서 트윗, 타임라인, 친구, 팔로워를 가져올 수 있습니다.

앱의 레이블에 이 정보를 표시할 수 있습니다. 예를 들어 입력 텍스트 상자를 추가하고 사용자가 일부 트윗 텍스터를 입력하게 한 다음 해당 트윗을 "게시"하는 단추를 추가할 수 있습니다. 비슷한 방법으로 트윗을 가져오거나 검색한 다음 앱의 레이블 또는 갤러리 컨트롤에 텍스트를 표시할 수 있습니다.

이 토픽에서는 앱에서 Twitter 연결을 만들고 Twitter 연결을 사용하는 방을 보여 주며 사용 가능한 함수를 나열합니다.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>Twitter 연결
1. Power Apps를 열고 **새로 만들기**를 선택한 다음, **빈 앱**을 만듭니다. 전화나 태블릿 레이아웃을 선택합니다. 태블릿 레이아웃의 작업 영역이 더 넓습니다.  

   ![비어 있는 앱 열기](./media/connection-twitter/blank-app.png)
2. 오른쪽 창에서 **데이터** 탭을 클릭하거나 탭한 후 **데이터 원본 추가**를 클릭하거나 탭합니다.
3. **새 연결**을 선택한 후 **Twitter**를 선택합니다.  

    ![Twitter 연결](./media/connection-twitter/addconnection.png)

    ![Twitter 연결](./media/connection-twitter/add-twitter.png)
4. **연결**을 선택하고 Twitter 로그인 자격 증명을 입력한 다음 **앱 승인**을 선택합니다.
5. **데이터 원본 추가**를 선택합니다. 연결이 **데이터 원본** 아래에 표시됩니다.  
    ![옵션 창 닫기](./media/connection-twitter/twitterdatasource.png)

Twitter 연결이 만들어지고 앱에 추가됩니다. 이제 사용할 수 있습니다.

## <a name="use-the-twitter-connection-in-your-app"></a>앱에서 Twitter 연결 사용
### <a name="show-a-timeline"></a>타임라인 표시
1. **삽입** 메뉴에서 **갤러리**를 선택하고 **텍스트** 갤러리를 추가합니다.
2. 이제 타임라인을 표시해 보겠습니다.  

   * 현재 사용자의 타임라인을 표시하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식에 설정합니다.

       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * 다른 사용자의 타임라인을 표시하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식에 설정합니다.  

       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`

       큰따옴표로 묶은 Twitter 핸들 또는 해당하는 값을 입력합니다. 예를 들어 수식에 `"satyanadella"` 또는 `"powerapps"`를 직접 입력합니다.
   * 이름이**Tweep**인 텍스트 입력 컨트롤을 추가하고 기본 속성을 `Tweep.Text`로 설정합니다. Tweep 텍스트 상자에 `satyanadella`와 같은 Twitter 핸들을 입력합니다(따옴표 및 @ 기호 없이).

       갤러리 컨트롤에서 Items 속성을 다음 수식으로 설정합니다.  

       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`

       갤러리 컨트롤이 입력한 Twitter 처리기의 트윗을 자동으로 표시합니다.

     > [!TIP]
     > 일부 수식은 **maxResults** 인수를 사용하여 타임라인의 가장 최근 트윗 수 *x*를 표시합니다.
3. 갤러리의 **Items** 속성을 `Twitter.HomeTimeline()`로 설정합니다.

    선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
4. 첫 번째 목록에서 **TweetText**, 두 번째 목록에서 **TweetedBy**, 세 번째 목록에서 **CreatedAt**을 선택합니다.

    이제 갤러리에 사용자가 선택한 속성 값이 표시됩니다.

### <a name="show-followers"></a>팔로워 표시
1. **텍스트** 갤러리를 사용하여 일부 팔로워를 표시해 보겠습니다.  

   * 현재 사용자의 팔로워를 표시하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * 다른 사용자의 팔로워를 표시하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

       `Twitter.Followers( *TwitterHandle* )`

       큰따옴표로 묶은 Twitter 핸들 또는 해당하는 값을 입력합니다. 예를 들어 수식에 `"satyanadella"` 또는 `"powerapps"`를 직접 입력합니다.
   * 이름이**Tweep**인 텍스트 입력 컨트롤을 추가하고 기본 속성을 `Tweep.Text`로 설정합니다. Tweep 텍스트 상자에 `satyanadella`와 같은 Twitter 핸들을 입력합니다(따옴표 및 @ 기호 없이).

       갤러리 컨트롤에서 Items 속성을 다음 수식으로 설정합니다.  

       `Twitter.Followers(Tweep.Text, {maxResults:5})`

       갤러리 컨트롤이 입력한 Twitter 핸들을 팔로우하는 사용자를 자동으로 표시합니다.

     > [!TIP]
     > 일부 수식은 **maxResults** 인수를 사용하여 타임라인의 가장 최근 트윗 수 *x*를 표시합니다.
2. 갤러리의 **Items** 속성을 `Twitter.MyFollowers()`로 설정합니다.

    선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
3. 두 번째 목록에서 **UserName**, 세 번째 목록에서 **FullName**을 선택합니다.

    이제 갤러리에 사용자가 선택한 속성 값이 표시됩니다.

### <a name="show-followed-users"></a>팔로우 대상 사용자 표시
1. **텍스트** 갤러리를 사용하여 일부 팔로우 대상 사용자를 표시해 보겠습니다.  

   * 현재 사용자가 팔로우하는 사용자를 표시하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * 다른 사용자가 수행 하는 사용자를 표시 하려면 갤러리의 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정 합니다.

       `Twitter.Following( *TwitterHandle* )`

       큰따옴표로 묶은 Twitter 핸들 또는 해당하는 값을 입력합니다. 예를 들어 수식에 `"satyanadella"` 또는 `"powerapps"`를 직접 입력합니다.
   * 이름이**Tweep**인 텍스트 입력 컨트롤을 추가하고 기본 속성을 `Tweep.Text`로 설정합니다. Tweep 텍스트 상자에 `satyanadella`와 같은 Twitter 핸들을 입력합니다(따옴표 및 @ 기호 없이).

       갤러리 컨트롤에서 Items 속성을 다음 수식으로 설정합니다.  

       `Twitter.Following(Tweep.Text, {maxResults:5})`

       갤러리 컨트롤이 사용자가 팔로우하는 다른 핸들을 자동으로 표시합니다.

     선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
2. **Body1** 목록에서 **Description**, **Heading1** 목록에서 **UserName**, **Subtitle1** 목록에서 **FullName**을 선택합니다.

    이제 갤러리에 사용자가 선택한 속성 값이 표시됩니다.

### <a name="show-information-about-a-user"></a>사용자에 대한 정보 표시
레이블을 추가하고 해당 **[텍스트](../controls/properties-core.md)** 속성을 이러한 수식 중 하나로 설정합니다.  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

큰따옴표로 묶은 Twitter 핸들 또는 해당하는 값을 입력합니다. 예를 들어 수식에 `"satyanadella"` 또는 `"powerapps"`를 직접 입력합니다.

또는 이 토픽에서 살펴본 내용과 마찬가지로 Twitter 핸들에 입력 텍스트 컨트롤을 사용할 수 있습니다.

### <a name="search-tweets"></a>트윗 검색
1. **텍스트** 갤러리를 추가하고 **[Items](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  

    `Twitter.SearchTweet( *SearchTerm* ).TweetText`

    큰 따옴표에 묶거나 해당하는 값을 참조하여 *검색어*를 입력합니다. 예를 들어 수식에 `"PowerApps"` 또는 `"microsoft"`를 직접 입력합니다.

    또는 이 토픽에서 살펴본 내용과 마찬가지로 **입력 텍스트** 컨트롤을 사용하여 검색어를 지정할 수 있습니다.

    > [!TIP]
   > maxResults를 사용하여 처음 5개 결과를 표시합니다.  

    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. 갤러리의 **Items** 속성을 `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})`로 설정합니다.

    선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
3. 첫 번째 목록에서 **TweetText**, 두 번째 목록에서 **TweetedBy**, 세 번째 목록에서 **CreatedAt**을 선택합니다.

    이제 갤러리에 사용자가 선택한 속성 값이 표시됩니다.

### <a name="send-a-tweet"></a>트윗 보내기
1. 텍스트 입력 컨트롤을 추가하고 이름을 **MyTweet**으로 변경합니다.
2. 단추를 추가하고 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. F5를 누르거나 미리 보기 단추(![](./media/connection-twitter/preview.png))를 선택합니다. **MyTweet**에 텍스트를 입력한 다음 단추를 선택하여 입력한 텍스트를 트윗합니다.
4. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

## <a name="view-the-available-functions"></a>사용할 수 있는 함수 보기
이 연결에는 다음 함수가 포함됩니다.

| 함수 이름 | 설명 |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |지정된 사용자가 게시한 가장 최근의 트윗 컬렉션 검색 |
| [HomeTimeline](connection-twitter.md#hometimeline) |나와 내 팔로워가 게시한 가장 최근의 트윗과 리트윗 검색 |
| [SearchTweet](connection-twitter.md#searchtweet) |특정 쿼리와 일치하는 관련 트윗 컬렉션 검색 |
| [Followers](connection-twitter.md#followers) |지정된 사용자를 팔로우하는 사용자 검색 |
| [MyFollowers](connection-twitter.md#myfollowers) |나를 팔로우하는 사용자 검색 |
| [Following](connection-twitter.md#following) |지정된 사용자가 팔로우하는 사용자 검색 |
| [MyFollowing](connection-twitter.md#myfollowing) |내가 팔로우하는 사용자 검색 |
| [User](connection-twitter.md#user) |지정된 사용자의 세부 정보 검색(예: 사용자 이름, 설명, 팔로워 수) |
| [Tweet](connection-twitter.md#tweet) |트윗 |
| [OnNewTweet](connection-twitter.md#onnewtweet) |검색 쿼리에 부합하는 새 트윗이 게시되었을 때 워크플로 트리거 |

### <a name="usertimeline"></a>UserTimeline
사용자 타임라인 가져오기: 지정된 사용자가 게시한 가장 최근의 트윗 컬렉션 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| userName |문자열 |예 |Twitter 핸들 |
| maxResults |정수 |아니요 |검색할 최대 트윗 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| TweetText |문자열 |예 | |
| TweetId |문자열 |아니요 | |
| createdAt |문자열 |아니요 | |
| RetweetCount |정수 |예 | |
| TweetedBy |문자열 |예 | |
| MediaUrls |배열 |아니요 | |

### <a name="hometimeline"></a>HomeTimeline
홈 타임라인 가져오기: 나와 내 팔로워가 게시한 가장 최근의 트윗과 리트윗 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| maxResults |정수 |아니요 |검색할 최대 트윗 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| TweetText |문자열 |예 | |
| TweetId |문자열 |아니요 | |
| createdAt |문자열 |아니요 | |
| RetweetCount |정수 |예 | |
| TweetedBy |문자열 |예 | |
| MediaUrls |배열 |아니요 | |

### <a name="searchtweet"></a>SearchTweet
트윗 검색: 특정 쿼리와 일치하는 관련 트윗 컬렉션 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| SearchQuery |문자열 |예 |쿼리 텍스트(Twitter가 지원하는 모든 쿼리 연산자 사용 가능: https://www.twitter.com/search) |
| maxResults |정수 |아니요 |검색할 최대 트윗 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| TweetText |문자열 |예 | |
| TweetId |문자열 |아니요 | |
| createdAt |문자열 |아니요 | |
| RetweetCount |정수 |예 | |
| TweetedBy |문자열 |예 | |
| MediaUrls |배열 |아니요 | |

### <a name="followers"></a>Followers
팔로워 가져오기: 지정된 사용자를 팔로우하는 사용자 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| userName |문자열 |예 |사용자의 Twitter 핸들 |
| maxResults |정수 |아니요 |검색할 최대 사용자 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 전체 이름 |문자열 |예 | |
| 위치 |문자열 |예 | |
| ID입니다. |정수 |아니요 | |
| UserName |문자열 |예 | |
| FollowersCount |정수 |아니요 | |
| 설명 |문자열 |예 | |
| StatusesCount |정수 |아니요 | |
| FriendsCount |정수 |아니요 | |

### <a name="myfollowers"></a>MyFollowers
내 팔로워 가져오기: 나를 팔로우하는 사용자 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| maxResults |정수 |아니요 |검색할 최대 사용자 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 전체 이름 |문자열 |예 | |
| 위치 |문자열 |예 | |
| ID입니다. |정수 |아니요 | |
| UserName |문자열 |예 | |
| FollowersCount |정수 |아니요 | |
| 설명 |문자열 |예 | |
| StatusesCount |정수 |아니요 | |
| FriendsCount |정수 |아니요 | |

### <a name="following"></a>Following
팔로잉 가져오기: 지정된 사용자가 팔로우하는 사용자 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| userName |문자열 |예 |사용자의 Twitter 핸들 |
| maxResults |정수 |아니요 |검색할 최대 사용자 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 전체 이름 |문자열 |예 | |
| 위치 |문자열 |예 | |
| ID입니다. |정수 |아니요 | |
| UserName |문자열 |예 | |
| FollowersCount |정수 |아니요 | |
| 설명 |문자열 |예 | |
| StatusesCount |정수 |아니요 | |
| FriendsCount |정수 |아니요 | |

### <a name="myfollowing"></a>MyFollowing
내 팔로잉 가져오기: 내가 팔로워하는 사용자 검색

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| maxResults |정수 |아니요 |검색할 최대 사용자 수(예: {maxResults:5}) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 전체 이름 |문자열 |예 | |
| 위치 |문자열 |예 | |
| ID입니다. |정수 |아니요 | |
| UserName |문자열 |예 | |
| FollowersCount |정수 |아니요 | |
| 설명 |문자열 |예 | |
| StatusesCount |정수 |아니요 | |
| FriendsCount |정수 |아니요 | |

### <a name="user"></a>User
사용자 가져오기: 지정된 사용자의 세부 정보 검색(예: 사용자 이름, 설명, 팔로워 수)

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| userName |문자열 |예 |사용자의 Twitter 핸들 |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 전체 이름 |문자열 |예 | |
| 위치 |문자열 |예 | |
| ID입니다. |정수 |아니요 | |
| UserName |문자열 |예 | |
| FollowersCount |정수 |아니요 | |
| 설명 |문자열 |예 | |
| StatusesCount |정수 |아니요 | |
| FriendsCount |정수 |아니요 | |

### <a name="tweet"></a>트윗
새 트윗 게시: 트윗

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| tweetText |문자열 |아니요 |게시할 텍스트(예: {tweetText:"hello"}) |
| 본문 |문자열 |아니요 |미디어할 미디어 |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| TweetId |문자열 |예 | |

### <a name="onnewtweet"></a>OnNewTweet
새 트윗이 표시될 때: 검색 쿼리에 부합하는 새 트윗이 게시되었을 때 워크플로 트리거

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| SearchQuery |문자열 |예 |쿼리 텍스트(Twitter가 지원하는 모든 쿼리 연산자 사용 가능: https://www.twitter.com/search) |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 값 |배열 |아니요 | |

## <a name="helpful-links"></a>유용한 링크
[사용 가능한 연결](../connections-list.md)을 모두 보세요.  
앱에 [연결을 추가](../add-manage-connections.md)하는 방법을 알아보세요.

