---
title: SharePoint Online 통합 시나리오의 엔드투엔드 연습 | Microsoft Docs
description: 이 시리즈의 자습서에서 빌드한 엔드투엔드 연습 시나리오를 수행합니다.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 64a26fbd0e36937427bc679869d5bc942f254130
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61531736"
---
# <a name="walk-end-to-end-through-the-completed-sharepoint-online-integration-scenario"></a>완료된 SharePoint Online 통합 시나리오 엔드투엔드 연습
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악해야 합니다.

이 시리즈의 자습서에서는 캔버스 앱 및 흐름 빌드부터 보고서 생성 및 SharePoint에 포함에 이르기까지 막대한 양의 정보를 설명했습니다. 지금까지 많은 내용을 알아보고 이러한 기술을 통합하는 방법을 충분히 알아보았으므로 고유한 필요에 따라 SharePoint에 캔버스 앱, 흐름 및 보고서를 통합할 수 있습니다. 마무리하기 전에 시나리오를 끝까지 살펴보고 모든 파트가 함께 작동하는 방법을 확인하려고 합니다.

## <a name="step-1-add-a-project-to-the-project-requests-list"></a>1 단계: 프로젝트 요청 목록에 프로젝트 추가
1. **프로젝트 요청** 목록에서 **모든 항목** 및 **프로젝트 요청 앱**을 차례로 클릭하거나 누릅니다.
   
    ![프로젝트 요청 앱 보기](./media/sharepoint-scenario-summary/09-00-01-view-app.png)
2. **열기**를 클릭하면 새 브라우저 탭에서 앱이 열립니다.
   
    ![프로젝트 요청 열기 앱](./media/sharepoint-scenario-summary/09-00-02-open-app.png)
3. 앱에서 ![항목 추가 아이콘](./media/sharepoint-scenario-summary/icon-add-item.png) 을 클릭하거나 탭하여 새 항목을 만듭니다.
4. 다음 값으로 양식을 작성합니다.
   
   * **Title** = "Mobile devices for design team"

   * **Approved** = "Pending"

   * **Description** = "The design team will now use Contoso-supplied devices"

   * **EstimatedDays** = "30"

   * **ProjectType** = "New hardware"

   * **RequestDate** = "03/01/2017"

   * **Requestor** = "Emily Braun"
     
     ![프로젝트 요청 편집 양식](./media/sharepoint-scenario-summary/09-01-01-app-new.png)
5. 을 클릭하거나 탭한 ![확인 표시 아이콘](./media/sharepoint-scenario-summary/icon-check-mark.png)다음 브라우저 탭을 닫습니다.
6. **프로젝트 요청** 목록으로 이동하고, **프로젝트 요청 앱** 및 **모든 항목**을 차례로 클릭하거나 누릅니다.
   
    ![모든 항목 보기](./media/sharepoint-scenario-summary/09-01-01a-view-all.png)
7. 목록에서 새 항목을 확인합니다.
   
    ![새 항목을 포함하는 SharePoint 목록](./media/sharepoint-scenario-summary/09-01-02-list-new.png)

## <a name="step-2-approve-the-project"></a>2단계: 프로젝트 승인
1. 1단계에서 항목을 추가할 때 흐름이 실행되고 승인 메일을 보내도록 해야 합니다. 승인자 전자 메일 계정의 받은 편지함을 확인합니다.
   
    ![승인 요청 전자 메일](./media/sharepoint-scenario-summary/09-02-01-allan-email.png)
2. **승인**을 클릭합니다. 흐름은 다른 프로세스를 실행하고, 전자 메일에서 직접 다음과 같은 피드백을 수신합니다.
   
    ![작업 완료](./media/sharepoint-scenario-summary/09-02-01a-action-complete.png)
3. 요청자 전자 메일 계정의 받은 편지함을 확인하고 승인 전자 메일을 표시합니다.
   
    ![요청자에 대한 승인 전자 메일](./media/sharepoint-scenario-summary/09-02-02-megan-email.png)
4. 목록에서 업데이터된 항목을 확인합니다.
   
    ![업데이트된 항목을 포함하는 SharePoint 목록](./media/sharepoint-scenario-summary/09-02-03-yes.png)

## <a name="step-3-assign-a-manager-to-the-project"></a>3 단계: 프로젝트에 관리자 할당
1. 먼저 SharePoint에서 **프로젝트 세부 정보** 목록을 살펴보겠습니다. 새 프로젝트에는 **PMAssigned** 열에 **Unassigned** 값이 있습니다.
   
    ![할당되지 않은 SharePoint 목록 항목](./media/sharepoint-scenario-summary/09-03-01-unassigned.png)
2. SharePoint 사이트의 왼쪽 탐색 영역에서 **프로젝트 관리 앱**을 클릭하거나 누릅니다.
3. 첫 번째 화면에서 **관리자 할당**을 클릭하거나 누릅니다.
   
    ![프로젝트에 관리자 할당](./media/sharepoint-scenario-summary/09-03-02-intro-screen.png)
4. **관리자 할당** 화면의 목록에서 할당되지 않은 두 개의 프로젝트가 표시됩니다. **디자인 팀의 모바일 디바이스** 프로젝트를 선택합니다.
   
    ![앱에서 선택된 할당되지 않은 프로젝트](./media/sharepoint-scenario-summary/09-03-03-selected.png)
5. **관리자** 텍스트 입력에서 "Joni Sherman"을 입력한 다음 **확인**을 클릭합니다.
   
    변경 내용을 목록에 적용하고 갤러리를 새로 고치므로 할당되지 않은 나머지 프로젝트만 표시됩니다.
   
    ![프로젝트에 할당된 관리자](./media/sharepoint-scenario-summary/09-03-04-updated.png)
6. 앱을 닫고 SharePoint 목록으로 돌아갑니다. 이제 프로젝트 항목이 프로젝트 관리자 이름으로 업데이트되었음을 알 수 있습니다.
   
    ![할당된 SharePoint 목록 항목](./media/sharepoint-scenario-summary/09-03-05-assigned.png)

## <a name="step-4-add-time-estimates-for-the-project"></a>4단계: 프로젝트에 대한 시간 예상치 추가
1. ![뒤로 아이콘](./media/sharepoint-scenario-summary/icon-back.png)을 클릭하거나 눌러서 첫 번째 화면으로 돌아간 다음, **세부 정보 업데이트**를 클릭하거나 누릅니다.
   
    ![프로젝트 업데이트 세부 정보](./media/sharepoint-scenario-summary/09-04-00-intro-screen.png)
2. **프로젝트 보기** 화면에서 검색 상자에 "모바일"을 입력합니다.
   
    ![앱에서 검색](./media/sharepoint-scenario-summary/09-04-01-search-mobile.png)
3. **디자인 팀의 모바일 디바이스** 항목에서 ![세부 정보 화살표 아이콘](./media/sharepoint-scenario-summary/icon-details-arrow.png)을 클릭합니다.
   
    ![업데이트할 프로젝트 선택](./media/sharepoint-scenario-summary/09-04-02-select-project.png)
4. **세부 정보 업데이트** 화면에서 다음 값을 설정합니다.
   
   * **상태** 필드 = "시작 안 함"

   * **ProjectedStartDate** 필드 = "3/6/2017"

   * **ProjectedEndDate** 필드 = "3/24/2017"

   * **ProjectedDays** 필드 = "15"
     
     ![프로젝트 업데이트 세부 정보](./media/sharepoint-scenario-summary/09-04-03-update.png)
5. 을 클릭하거나 탭한 ![확인 표시 아이콘](./media/sharepoint-scenario-summary/icon-check-mark.png) 변경 내용을 SharePoint 목록에 적용합니다.
6. 앱을 닫고 목록으로 돌아갑니다. 이제 프로젝트 항목이 변경된 날짜 및 일 수로 업데이트됩니다.
   
   ![SharePoint 목록에서 업데이트된 세부 정보](./media/sharepoint-scenario-summary/09-04-04-updated-list.png)

## <a name="step-5-review-report-data-for-existing-projects"></a>5단계: 기존 프로젝트에 대한 보고서 데이터 검토
1. SharePoint Online에서 **사이트 콘텐츠** 및 **사이트 페이지**를 차례로 클릭하거나 누릅니다.
2. 앞에서 만든 **프로젝트 분석** 페이지를 엽니다.
   
    ![포함된 프로젝트 분석 보고서](./media/sharepoint-scenario-summary/09-05-01-report-complete.png)
3. 분산 시각화를 검토합니다.
   
    ![분산을 보여주는 차트](./media/sharepoint-scenario-summary/09-05-02-chart-variance.png)
   
    이 시각화를 만들 때와 같이 Irvin Sayers 및 Joni Sherman이 실행한 프로젝트에 더 많은 분산이 있습니다.
4. 시각화를 분석하면 대부분의 분산이 예상보다 훨씬 오래 걸린 두 개의 프로젝트에서 비롯되는 것을 확인할 수 있습니다.
   
    ![분산 세부 정보를 보여주는 차트](./media/sharepoint-scenario-summary/09-05-03-chart-variance-drill.png)
5. 프로젝트가 승인에서 프로젝션된 시작 날짜로 이동하는 데 걸리는 시간을 보여주는 표를 검토합니다.
   
    ![시작 날짜 차이를 보여주는 표](./media/sharepoint-scenario-summary/09-05-04-chart-diff-completed.png)
   
    우리가 이 시각화를 만들었을 때 주목했던 대로, Irvin Sayers에 할당한 프로젝트가 시작하는 데 더 많은 시간이 걸리며, 두 프로젝트가 나머지 프로젝트보다 훨씬 오래 걸립니다.

## <a name="step-6-respond-to-pending-project-delays"></a>6 단계: 보류 중인 프로젝트 지연에 응답
1. Power BI 서비스에서 **프로젝트 분석** 데이터 세트를 클릭하거나 누르고 **지금 새로 고침**을 클릭하거나 누릅니다. 새로 고침은 보류 중인 프로젝트에 설정한 경고를 트리거합니다.
   
    ![지금 데이터 세트 새로 고침](./media/sharepoint-scenario-summary/09-06-01-refresh.png)
2. 새로 고침이 완료된 후에 오른쪽 위에 있는 **알림 센터**는 새 알림 아이콘을 표시합니다.
   
    ![Power BI 알림 센터](./media/sharepoint-scenario-summary/09-06-02-alert.png)
   
    약간의 시간이 걸릴 수 있습니다. 따라서 바로 표시되지 않는 경우 다시 확인합니다.
3. 알림 센터를 열어서 발생한 경고의 세부 정보를 확인합니다.
   
    ![데이터 경고에 대한 알림](./media/sharepoint-scenario-summary/09-06-03-notification.png)
4. 경고를 만든 사용자의 받은 편지함을 확인합니다(이 경우 Megan Bowen).
   
    ![Power BI에서 보낸 경고 전자 메일](./media/sharepoint-scenario-summary/09-06-04-email-powerbi.png)
5. 데이터 경고 흐름에 추가한 사용자의 받은 편지함을 확인합니다(이 경우 Allan DeYoung).
   
    ![Microsoft Flow에서 보낸 경고 전자 메일](./media/sharepoint-scenario-summary/09-06-05-email-flow.png)
6. 이제 보류 중인 프로젝트에 대한 정보가 있으므로 뒤로 돌아가서 확인해야 하는 항목을 승인할 수 있습니다.

그러면 엔드투엔드 연습 및 이 시리즈의 자습서를 완료할 수 있습니다. 다음 사이트에서 사용자 경험을 계속하는 것이 좋습니다.

* [PowerApps](http://www.powerapps.com/)
* [Microsoft Flow](http://flow.microsoft.com)
* [Power BI](http://www.powerbi.com)
* [Power Users Community](https://powerusers.microsoft.com/)
* [SharePoint](http://sharepoint.microsoft.com)
* [Microsoft Tech Community](https://techcommunity.microsoft.com/)

이 시리즈에 대한 피드백, 추가할 제안 사항 또는 추가 콘텐츠에 대한 아이디어가 있는 경우 의견을 보내주세요. 이를 통해 앞서 설명한 기술을 사용할 수 있습니다.

