---
title: 솔루션의 기록 보기 | MicrosoftDocs
description: 솔루션의 기록을 보는 방법 알아보기
keywords: null
ms.date: 05/19/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
  - powerapps
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-the-history-of-a-solution"></a>솔루션의 기록 보기
모델 기반 앱의 **솔루션** 영역에서 솔루션 작업에 대한 세부 정보를 볼 수 있습니다. 작업은 솔루션 가져오기, 내보내기 또는 삭제일 수 있습니다. 솔루션 기록에는 솔루션 버전, 솔루션 게시자, 작업 유형, 작업 시작 및 종료 시간, 작업 상태와 같은 정보가 표시됩니다.

> [!div class="mx-imgBorder"] 
> ![](media/solutions-history-custom-view.png "솔루션 기록 사용자 지정 보기")

## <a name="view-solution-history"></a>솔루션 기록 보기
1. **설정**을 선택한 다음, **솔루션 기록**을 선택합니다.

     > [!div class="mx-imgBorder"] 
     > ![](media/solution-history-sitemap.png "솔루션 기록 영역")

     > [!NOTE]
     > PowerApps 통합 인터페이스 모델 기반 응용 프로그램에서 **설정** 영역으로 이동하려면 응용 프로그램 도구 모음에서 **설정** ![설정](../model-driven-apps/media/powerapps-gear.png)을 선택한 다음 **고급 설정**을 클릭합니다. 

2. 기본적으로 **사용자 지정 솔루션 기록** 보기가 표시됩니다. 다음 보기는 **솔루션 기록** 영역에서 사용할 수 있습니다. 
- **모든 솔루션 기록**. 내부 시스템 및 사용자 지정 솔루션 모두에 대한 솔루션 기록을 표시합니다. 
- **사용자 지정 솔루션 기록**. 사용자 지정 솔루션에 대한 솔루션 기록만 표시합니다. 
- **내부 솔루션 기록**. 내부 시스템 솔루션에 대한 솔루션 기록만 표시합니다. 

각 솔루션 기록 레코드는 읽기 전용이며 다음 속성을 포함합니다. 
- **시작 시간**. 작업이 시작된 시간입니다. 
- **종료 시간**: 작업이 종료된 시간입니다. 
- **솔루션 버전**. 솔루션의 버전입니다. 
- **게시자 이름**. 작업과 연결된 게시자의 이름입니다. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md)  
- **작업**. 가져오기, 내보내기 또는 삭제와 같은 작업입니다. 추가 정보: [솔루션 가져오기, 업데이트 및 내보내기](import-update-export-solutions.md)
- **하위 작업**: 새로운 솔루션 가져오기 또는 기존 솔루션의 업데이트와 같은 작업 유형을 나타냅니다. 
- **상태:** 작업의 현재 상태(예: **완료됨** 또는 **완료되지 않음**)입니다. 
- **결과**. 작업의 결과(예: **성공** 또는 **실패**)입니다. 
- **오류 코드**: 작업에서 반환된 오류 코드입니다. 오류 코드 0은 작업이 성공적으로 완료되었음을 의미합니다. 

### <a name="view-solution-operation-error-details"></a>솔루션 작업 오류 세부 정보 보기 
솔루션 작업에 오류가 있는 경우 추가 오류 세부 정보가 포함된 페이지를 표시하도록 선택할 수 있습니다. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-with-failure.png "작업 오류가 있는 솔루션 기록")

세부 정보 페이지에는 작업 실패에 대한 기본 원인을 진단하는 데 도움이 될 수 있는 **예외 메시지**를 포함한 정보가 포함되어 있습니다. 솔루션 종속성 오류를 비롯한 일부 오류에는 문제를 쉽게 진단 할 수 있는 **솔루션 계층** 에 대한 링크가 포함될 수도 있습니다. **활동 ID**는 Microsoft 고객 지원부에 문의해야 하는 경우 유용할 수 있습니다. 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-error-details.png "솔루션 작업 오류 세부 정보")

### <a name="see-also"></a>참조
[솔루션 레이어 보기](solution-layers.md)  <br />
[솔루션 개요](solutions-overview.md) 


