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
ms.openlocfilehash: f0b095b3cb69eb7b6fd373b28eb2255291c7893a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543520"
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
   > ![고정 된 레코드](media/pinnedrecords.png "고정 된 레코드")

## <a name="unpin-records-items-or-view"></a>레코드, 항목 또는 보기 고정 해제

1. **사이트 맵**에서 **고정됨**을 선택하여 고정된 항목의 목록을 확장합니다.
2. 항목 옆에 있는 고정 해제 아이콘을 선택하면 목록에서 삭제됩니다.  

   > [!div class="mx-imgBorder"]
   > ![레코드 고정 해제](media/unpinnedrecords.png "레코드 고정 해제")

## <a name="record-set-navigation"></a>레코드 세트 탐색 
미리 설정된 보기 및 쿼리를 사용하여 여러 레코드를 탐색합니다. 레코드에 초점을 맞춘 탐색은 사용자가 목록에서 레코드 간을 이동하고 해당 작업 목록의 손실 없이 다시 쉽게 탐색할 수 있도록 하여 생산성을 개선시킵니다.

> [!div class="mx-imgBorder"]
> ![레코드 집합 탐색](media/recordset.png "레코드 세트 탐색")

## <a name="reference-panel"></a>참조 패널
참조 패널은 현재 화면을 이동하지 않고 작업을 완료하는 좋은 방법입니다. 다른 화면으로 이동하지 않고 보고 있는 레코드의 컨텍스트 내에서 계정의 사례 또는 기회와 같은 다른 관련된 항목을 조회할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![참조 패널](media/reference-panel.png "참조 패널")

 참조 패널에 대해 자세히 알아보려면 이 비디오를 시청하세요.

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>알림 

양식에 표시 되는 알림 유형은 정보, 경고 및 오류의 세 가지입니다. 알림은 항상 헤더 바로 위에 있는 양식의 맨 위에 제공됩니다.

오류 알림을 선택 하면 오류가 발생 한 폼의 필드로 이동 됩니다.

![알림 예제](media/notifications.png "알림 예제")

알림이 한 개이면 단일 줄로 표시됩니다.

![단일 알림의 예](media/single_notification.png "단일 알림의 예")

둘 이상의 알림이 있으면 알림 수가 표시됩니다. 각 메시지를 보려면 펼침 단추를 선택합니다.

![여러 알림의 예](media/multiple_notification.png "여러 알림의 예")

## <a name="grids"></a>배경

통합 인터페이스의 표가 화면에 표시 될 수 있는 데이터의 양을 늘리기 위해 개선 되었습니다. 또한 그리드는 마지막 필터를 기억 하 고 순서를 정렬 하는 등의 필터링 옵션을 향상 시켰습니다. 

그리드 영역에서 데이터를 검색할 때 시스템이 데이터 검색에 대해 작동 하 고 있음을 알리는 로드 표시기가 표시 됩니다.

주 그리드 페이지는 앞뒤로 이동할 때 필터, 정렬 및 페이지 상태를 기억 합니다. 여기에는 빠른 찾기, 열 필터링, 페이지 번호 등이 포함 됩니다. 페이지 외부의 탐색은 초기 상태로 열립니다.


   > [!div class="mx-imgBorder"]
   > ![표 상태 기억을](media/grid-remember-state-on-back-navigate.gif "표 상태 기억을")


점프 막대는 첫 번째 정렬 된 필드를 사용 합니다. 정렬 변경이 수행 되지 않은 경우에는 기본 필드를 사용 하는 점프 막대가 표시 됩니다. 

   > [!div class="mx-imgBorder"]
   > ![표 상태 기억을](media/jumpbar-filter-on-sorted-column.gif "표 상태 기억을")
   

**작업 유형** 필드를 필터링 하 고 여러 필터링 유형을 선택할 수 있습니다. 또한 소유자, 상태, 이유 등의 관련 엔터티 필드도 필터링 할 수 있습니다.

   > [!div class="mx-imgBorder"]
   > ![표 필터링](media/grid-activity-type-column-filter.gif "표 필터링")
   
계층 구조 아이콘을 선택 하는 경우 계층 구조 폼으로 이동 합니다.

   > [!div class="mx-imgBorder"]
   > ![계층 아이콘](media/grid-row-hierarchy-icon.png "계층 아이콘")
   
새 탭 또는 창에서 기본 필드 및 조회 필드를 열 수도 있습니다.

   > [!div class="mx-imgBorder"]
   > ![새 창에서 열기](media/newtab.png "[새 창에서 열기")


