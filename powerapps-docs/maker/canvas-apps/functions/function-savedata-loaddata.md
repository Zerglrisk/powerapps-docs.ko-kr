---
title: SaveData 및 LoadData 함수 | Microsoft Docs
description: PowerApps의 SaveData 및 LoadData 함수에 대한 구문을 비롯한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e716de7a3551e2195d3f3459540a6f68acb4fd51
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992281"
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>PowerApps의 SaveData 및 LoadData 함수
[컬렉션](../working-with-data-sources.md#collections)을 저장하고 다시 로드합니다.

## <a name="description"></a>설명
**SaveData** 함수는 나중에 이름으로 사용할 컬렉션을 저장합니다.  

**LoadData** 함수는 이전에 **SaveData**를 사용하여 저장한 이름으로 컬렉션을 다시 로드합니다. 이 함수는 다른 원본에서 컬렉션을 로드하는 데 사용할 수 없습니다.  

이러한 함수를 사용 하 여 첫 번째 실행에서 App.config 수식의 데이터를 캐시 한 다음 후속 실행 시 로컬 캐시를 다시 로드 하 여 앱 시작 성능을 향상 시킬 수 있습니다 **[.](../controls/control-screen.md#additional-properties)** 이러한 기능을 사용 하 여 [간단한 오프 라인 기능](../offline-apps.md) 을 앱에 추가할 수도 있습니다.

PowerApps Studio에서 앱을 제작 하거나 웹 플레이어에서 앱을 실행할 때 브라우저 내에서 이러한 기능을 사용할 수 없습니다. 앱을 테스트 하려면 iPhone 또는 Android 장치의 PowerApps Mobile에서 앱을 실행 합니다.

이러한 함수는 메모리 내 컬렉션에서 작동 하기 때문에 사용 가능한 앱 메모리의 양에 따라 제한 됩니다. 사용 가능한 메모리는 장치 및 운영 체제, PowerApps 플레이어에서 사용 하는 메모리, 화면 및 컨트롤 측면에서 응용 프로그램의 복잡성에 따라 달라질 수 있습니다. 몇 메가바이트 이상의 데이터를 저장 하는 경우 앱을 실행할 것으로 예상 되는 장치에서 예상 시나리오로 앱을 테스트 합니다. 일반적으로는 30 ~ 70 메가바이트의 사용 가능한 메모리가 필요 합니다.  

**LoadData**는 컬렉션을 만들지 않습니다. 함수는 기존 컬렉션을 채우기만 합니다. 먼저 **[Collect](function-clear-collect-clearcollect.md)** 를 사용하여 올바른 [열](../working-with-tables.md#columns)이 있는 컬렉션을 만들어야 합니다. 로드 된 데이터가 컬렉션에 추가 됩니다. 빈 컬렉션으로 시작 하려면 먼저 **[Clear](function-clear-collect-clearcollect.md)** 함수를 사용 합니다.

스토리지는 암호화되어 로컬 디바이스의 비공개 위치에 다른 사용자 및 다른 앱과 격리되어 있습니다.

## <a name="syntax"></a>구문
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 필수 항목입니다.  저장하거나 로드할 컬렉션입니다.
* *Name* - 필수 항목입니다.  스토리지 이름입니다. 동일한 데이터 집합을 저장하고 로드하려면 동일한 이름을 사용해야 합니다. 네임스페이스는 다른 앱이나 사용자와 공유되지 않습니다.
* *IgnoreNonexistentFile* - 선택 항목입니다. **LoadData** 함수가 일치하는 파일을 찾을 수 없을 때 오류를 표시하거나 무시할지 나타내는 부울(**true**/**false**) 값입니다. **false**를 지정하면 오류가 표시됩니다. **true**를 지정하면 오류가 무시되고, 오프라인 시나리오에 유용합니다. **SaveData**는 디바이스가 오프라인인 경우 (즉, **Connection.Connected** 상태가 **false**인 경우) 파일을 만들 수 있습니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **If (Connection, ClearCollect (LocalTweets, SearchTweet ("PowerApps", {maxResults: 100}), LoadData (LocalTweets, "트 윗", true))** |디바이스가 연결되어 있으면 Twitter 서비스에서 LocalTweets 컬렉션을 로드하고, 그렇지 않으면 로컬 파일 캐시에서 컬렉션을 로드합니다. |콘텐츠는 디바이스가 온라인 또는 오프라인 상태인지 여부에 관계없이 렌더링됩니다. |
| **SaveData(LocalTweets, "Tweets")** |LocalTweets 컬렉션을 디바이스의 로컬 파일 캐시로 저장합니다. |데이터는 **LoadData**가 컬렉션에 로드할 수 있도록 로컬에 저장됩니다. |

