---
title: 모델 기반 앱에 대 한 통합 인터페이스를 사용 하 여 향상 된 사용자 환경 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 9/23/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 76241ae2e26752a98e32e7ad72c54780da3934ae
ms.sourcegitcommit: 60fd1792430b9f3da08ec161cb2277506d795e3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71705326"
---
# <a name="enhanced-user-experience-with-the-unified-interface-for-model-driven-apps"></a>모델 기반 앱에 대 한 통합 인터페이스를 사용 하 여 향상 된 사용자 환경 

모델 기반 앱에 대 한 통합 인터페이스는 데스크톱, 랩톱, 태블릿 또는 휴대폰에 상관 없이 장치 간에 일관 되 고 액세스 가능한 사용자 환경을 제공 합니다. 앱은 화면에서 구성 요소를 reflowing 하 여 크기를 조정 합니다. 응답성이 뛰어난 디자인은 화면 크기에 따라 사용자 환경에 적응 하므로 사용 가능한 공간이 더 많이 표시 될 수 있습니다.

> [!div class="mx-imgBorder"]
> ![통합 인터페이스가 화면에 적응](media/Reflow.png "통합 인터페이스가 화면에 적응")

> [!NOTE]
> 레거시 웹 클라이언트는 더 이상 사용 되지 않으며 고객은 2020 년 10 월 1 일 이전에 통합 인터페이스로 전환 해야 합니다. 자세한 내용은 [Blog를 참조 하세요. 통합 인터페이스 으로 이동할 타임 라인을 발표 합니다](https://cloudblogs.microsoft.com/dynamics365/it/2019/09/10/announcing-the-timeline-to-move-to-unified-interface/). 전환 방법에 대해 자세히 알아보려면 전환 [에 대 한 빠른 시작](https://docs.microsoft.com/en-us/powerapps/maker/model-driven-apps/transition-web-app)을 참조 하세요.

## <a name="navigation"></a>내비게이션

메뉴 옵션을 사용 하면 시스템에서 다양 한 앱을 빠르게 탐색할 수 있습니다. 최근 본 레코드 및 고정 된 즐겨찾기에 빠르게 액세스할 수 있도록 합니다. 

> [!div class="mx-imgBorder"]
> ![모델 기반 앱 탐색](media/nav.png "모델 기반 앱 탐색")

1. 사이트 맵은 기본적으로 확장 되 고 유지 됩니다.
2. 현재 있는 하위 영역을 강조 표시 하 여 앱의 위치를 표시 합니다.
3. **최근** 및 **고정** 항목은 쉬운 액세스를 위해 맨 위에 있습니다. 
4. 영역 전환기를 사용하여 앱을 전환합니다.
5. 명령 간의 차이점을 표시하기 위해 명령 모음의 아이콘에는 고유한 색이 있어야 합니다.

자세한 내용은 [모델 기반 앱의 기본 탐색](navigation.md)을 참조 하세요.

## <a name="dashboards-and-charts"></a>대시보드 및 차트
통합 인터페이스 앱 내에서 모든 시스템 및 사용자 대시보드에 액세스할 수 있습니다. 이제 풍부한 대화형 대시보드 기능이 있는 모든 레코드 유형에 대화형 대시보드를 사용할 수 있습니다. 자세한 내용은 [대시보드 및 차트를 사용 하 여 진행률 추적](track-your-progress-with-dashboard-and-charts.md)을 참조 하세요.

## <a name="timeline-control"></a>타임라인 컨트롤 
타임 라인 보기를 사용 하면 읽기 쉬운 보기에서 단일 페이지의 레코드에서 고객 통신을 추적 하 여 팀과 공동 작업을 수행할 수 있습니다. 게시물 및 음성 첨부 파일에서 전자 메일 및 메모에 이르기까지 모든 항목을 볼 수 있습니다. 전체 통신 스레드를 빠르게 확인 하는 방법을 제공 합니다. 자세한 내용은 [타임 라인에 약속, 전자 메일, 전화 통화, 메모 또는 작업 활동 추가](add-activities.md)를 참조 하세요.

## <a name="business-process"></a>비즈니스 프로세스 
도킹 메커니즘이 비즈니스 프로세스 흐름을 개선 했습니다. 비즈니스 프로세스 흐름에서 작업에 집중 하는 데 도움이 되도록 화면에 비즈니스 프로세스 단계를 도킹할 수 있습니다. 특히 프로세스의 단계를 완료 하는 데 복잡 한 단계가 있는 경우에 유용 합니다. 자세한 내용은 [비즈니스 프로세스](work-with-business-processes.md)에 대 한 작업을 참조 하세요.

## <a name="accessibility"></a>내게
향상 된 접근성 환경에서는 화면 판독기를 사용 하 여 화면에 있는 정보를 가청 소리로 변환 하 고 더 많은 사람들이 앱을 사용할 수 있도록 브라유 점자 판독기로 인쇄할 수 있습니다. 자세한 내용은 [화면 판독기 사용](screen-reader.md)을 참조 하세요.

## <a name="create-a-unified-interface-app"></a>통합 인터페이스 앱 만들기
통합 인터페이스에 대 한 사용자 고유의 환경을 만들기 위한 요구 사항이 있는 경우 앱 디자이너를 사용 하 여 모델 기반 앱을 만들 수 있습니다. [모델 기반 앱 빌드 개요를](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)참조 하세요.

![새 통합 인터페이스 앱 만들기](media/uci-model-driven-app.png "새 통합 인터페이스 앱 만들기")

## <a name="unified-interface-community"></a>통합 인터페이스 커뮤니티

통합 인터페이스 [커뮤니티 사이트로](https://community.dynamics.com/365/unified-interface/) 이동 하 여 통합 인터페이스에 대 한 원활한 전환을 계획 하 고 실행 하는 데 도움을 받고 블로그, 웹 세미나, 비디오, 이벤트 등에 대 한 전문가 및 동료와 협력 하세요.
