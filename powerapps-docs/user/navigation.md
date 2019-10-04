---
title: 모델 기반 앱의 기본 탐색 | Microsoft Docs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a46698ddf454c9d0f563575a3553e874f3a7b109
ms.sourcegitcommit: 9a16bb75c856f7c84cd385811b7135ab2804ae69
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71924518"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>모델 기반 앱의 기본 탐색 

탐색 막대를 사용하여 작업 영역으로 이동하고, 새 레코드를 만들거나, 검색하거나, 모델 기반 앱에서 다른 작업을 수행합니다.

> [!div class="mx-imgBorder"]
> ![모델 기반 앱 탐색](media/nav.png "모델 기반 앱 탐색")

1. 기본적으로 사이트 맵은 확장된 상태로 유지됩니다.
2. 현재 위치한 하위 영역은 앱의 현재 위치를 나타내기 위해 강조 표시됩니다.
3. **최근** 및 **고정** 항목은 쉬운 액세스를 위해 맨 위에 있습니다. 
4. 영역 전환기를 사용하여 앱을 전환합니다.
5. 명령 간의 차이점을 표시하기 위해 명령 모음의 아이콘에는 고유한 색이 있어야 합니다.
  
## <a name="get-back-to-recent-records-items-or-view"></a>최근 레코드, 항목 또는 보기로 돌아가기
아마도 대부분의 시간 동안 동일한 레코드를 사용하게 될 것입니다. 예를 들어, 정기적으로 동일한 연락처 또는 계정에 액세스할 수 있습니다. 동일한 데이터 목록(보기)을 계속 사용할 수도 있습니다. 최근에 사용된 레코드 또는 사이트 맵의 보기로 신속하게 이동할 수 있습니다. 보다 쉽게 찾을 수 있도록 레코드 및 보기를 고정할 수도 있습니다. 
  
1. **사이트 맵**에서 **최근**을 선택합니다.
  
2. **최근**에서 돌아가려는 레코드, 항목 또는 보기를 선택합니다. 

## <a name="pin-records-items-or-view"></a>레코드, 항목 또는 보기 고정

1. **사이트 맵**에서 **최근**을 선택하여 최근에 액세스된 항목의 목록을 확장합니다.
2. 최근 목록에서 항목 옆에 있는 고정 아이콘을 선택하면 고정된 목록에 추가됩니다.

   > [!div class="mx-imgBorder"]
   > ![고정된 레코드](media/pinnedrecords.png "고정된 레코드")

## <a name="unpin-records-items-or-view"></a>레코드, 항목 또는 보기 고정 해제

1. **사이트 맵**에서 **고정됨**을 선택하여 고정된 항목의 목록을 확장합니다.
2. 항목 옆에 있는 고정 해제 아이콘을 선택하면 목록에서 삭제됩니다.  

   > [!div class="mx-imgBorder"]
   > ![레코드 고정 해제](media/unpinnedrecords.png "레코드 고정 해제")

## <a name="record-set-navigation"></a>레코드 세트 탐색 
미리 설정된 보기 및 쿼리를 사용하여 여러 레코드를 탐색합니다. 레코드에 초점을 맞춘 탐색은 사용자가 목록에서 레코드 간을 이동하고 해당 작업 목록의 손실 없이 다시 쉽게 탐색할 수 있도록 하여 생산성을 개선시킵니다.

> [!div class="mx-imgBorder"]
> ![레코드 세트 탐색](media/recordset.png "레코드 세트 탐색")

## <a name="reference-panel"></a>참조 패널
참조 패널은 현재 화면을 이동하지 않고 작업을 완료하는 좋은 방법입니다. 다른 화면으로 이동하지 않고 보고 있는 레코드의 컨텍스트 내에서 계정의 사례 또는 기회와 같은 다른 관련된 항목을 조회할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![참조 패널](media/reference-panel.png "참조 패널")

 참조 패널에 대해 자세히 알아보려면 이 비디오를 시청하세요.

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/en-us/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>알림 

양식에 표시되는 알림에는 다음과 같은 세 가지 형식이 있습니다. 정보, 경고 및 오류 알림은 항상 헤더 바로 위에 있는 양식의 맨 위에 제공됩니다.

오류 알림을 선택 하면 오류가 발생 한 폼의 필드로 이동 됩니다.

![알림의 예제](media/notifications.png "알림의 예제")

알림이 한 개이면 단일 줄로 표시됩니다.

![단일 알림의 예제](media/single_notification.png "단일 알림의 예제")

둘 이상의 알림이 있으면 알림 수가 표시됩니다. 각 메시지를 보려면 펼침 단추를 선택합니다.

![다중 알림의 예제](media/multiple_notification.png "다중 알림의 예제")

## <a name="grids"></a>배경

통합 인터페이스의 표가 화면에 표시 될 수 있는 데이터의 양을 늘리기 위해 개선 되었습니다. 또한 그리드는 마지막 필터를 기억 하 고 순서를 정렬 하는 등의 필터링 옵션을 향상 시켰습니다. 향상 된 기능에 대 한 자세한 내용은이 블로그 게시물의 [통합 인터페이스 그리드에서 향상 된 기능](https://powerapps.microsoft.com/en-us/blog/enhanced-functionality-in-unified-interface-grids)을 참조 하세요.



