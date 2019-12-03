---
title: 프로젝트를 분석하는 Power BI 보고서 만들기 | Microsoft Docs
description: 이 작업에서는 두 가지 SharePoint 목록을 기반으로 하여 Power BI 보고서를 만듭니다.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/10/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dbe706b19ccc974eda95f47145ced2e9ff14a4c6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674887"
---
# <a name="create-a-power-bi-report-to-analyze-projects"></a>프로젝트를 분석하는 Power BI 보고서 만들기
> [!NOTE]
> 이 문서는 SharePoint Online에서 Power Apps, 파워 자동화 및 Power BI 사용에 대 한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악하도록 합니다.

이 작업에서는 두 가지 SharePoint 목록을 기반으로 하여 Power BI 보고서를 만듭니다. 목록 데이터를 Power BI Desktop으로 가져오고, 약간 정리하고, 몇 가지 기본 데이터 모델링을 수행하고, 데이터에 대한 중요한 의미를 알려주는 일단의 시각적 개체를 만듭니다.

> [!TIP]
> 이 시나리오에 대한 [다운로드 패키지](https://aka.ms/o4ia0f)에는 이 보고서의 완성된 버전인 project-analysis.pbix가 포함되어 있습니다.

## <a name="quick-review-of-power-bi-desktop"></a>Power BI Desktop에 대한 빠른 검토
보고서를 만드는 방법을 살펴보기 전에 Power BI Desktop을 검토해 보겠습니다. 이는 많은 기능을 갖춘 강력한 도구이므로 이 작업에서 사용할 영역의 개요에 대해 중점적으로 설명합니다. Power BI Desktop에는 세 가지 기본 작업 영역(또는 '보기'), 즉 **보고서** 보기, **데이터** 보기 및 **관계** 보기가 있습니다. 또한 Power BI Desktop에는 별개의 창에서 열리는 **쿼리 편집기**도 있습니다.

다음 화면에서는 Power BI Desktop 왼쪽을 따라 위에서 아래로 세 가지 보기 아이콘(**보고서**, **데이터** 및 **관계**)을 표시합니다. 왼쪽의 노란색 막대는 현재 보기를 나타내며, 여기서는 **보고서** 보기가 표시되어 있습니다. 이러한 세 아이콘 중 하나를 선택하여 보기를 변경합니다.

![Power BI Desktop 보기](./media/sharepoint-scenario-build-report/05-00-00-tabs.png)

**보고서** 보기에는 다음 5개 기본 영역이 있습니다.

1. 리본 - 보고서 및 시각화와 관련된 일반적인 작업을 표시합니다.
2. **보고서** 보기 또는 캔버스 - 시각화를 만들고 정렬합니다.
3. **페이지** 탭 영역(아래쪽) - 보고서 페이지를 선택하거나 추가할 수 있습니다.
4. **시각화** 창 - 시각화를 변경하고, 색 또는 축을 사용자 지정하고, 필터를 적용하고, 필드를 끌어오는 등의 작업을 수행합니다.
5. **필드** 창 - 쿼리 요소와 필터를 **보고서** 보기로 끌거나 **시각화** 창의 **필터** 영역으로 끌 수 있는 영역입니다.

![Power BI Desktop 탭, 보기 및 창](./media/sharepoint-scenario-build-report/05-00-01-report.png)

**데이터** 보기에는 다음 3개 기본 영역이 있습니다.

1. 리본 - **모델링** 탭이 아래에 선택되어 있습니다. 이 탭에서 계산된 테이블과 열을 만들고 데이터 모델을 변경합니다.
2. 가운데 창 - 선택한 테이블에 대한 데이터를 표시합니다.
3. **필드** 창 - 보고서에 필드가 표시되는 방법을 제어하는 영역입니다.

![Power BI Desktop 데이터 보기](./media/sharepoint-scenario-build-report/05-00-02-data.png)

이 작업에서는 **관계** 보기를 사용하지 않지만, 나중에 목록 데이터를 Power BI Desktop으로 가져오면 확인할 수 있습니다.

**쿼리 편집기**에서 쿼리를 작성하고, 데이터를 변환한 다음, 구체화된 데이터 모델을 Power BI Desktop에 로드합니다. **쿼리 편집기**에는 다음 4개 기본 영역이 있습니다.

1. 리본 - 가져온 데이터를 모양 지정하고 변환하는 여러 옵션이 있습니다.
2. 왼쪽 창 - 쿼리가 나열되고 선택, 보기 및 모양 지정에 사용할 수 있는 영역입니다.
3. 가운데 창 - 선택한 쿼리의 데이터가 표시되고 모양 지정에 사용할 수 있는 영역입니다.
4. **쿼리 설정** 창 - 적용된 쿼리의 속성과 데이터 변환 단계를 나열합니다.

![Power BI Desktop 쿼리 편집기](./media/sharepoint-scenario-build-report/05-00-03-query.png)

## <a name="step-1-get-data-into-power-bi-desktop"></a>1단계: Power BI Desktop에 데이터 가져오기
이 단계에서는 먼저 두 목록에 연결합니다. 그런 다음 데이터 분석에 필요하지 않은 열을 제거하여 데이터를 정리합니다. 또한 계산이 제대로 작동하도록 나머지 열 중 일부의 데이터 형식을 변경합니다. Power BI Desktop에서 데이터를 가져오고 정리하는 방법에 대한 자세한 내용은 단계별 학습 과정의 [데이터 가져오기](https://powerbi.microsoft.com/guided-learning/powerbi-learning-1-1-overview-of-power-bi-desktop) 섹션을 참조하세요.

### <a name="connect-to-sharepoint-lists"></a>SharePoint 목록에 연결
1. Power BI Desktop의 **홈** 탭에서 **데이터 가져오기**, **자세히...** 를 차례로 클릭하거나 탭합니다.
   
    ![데이터 가져오기](./media/sharepoint-scenario-build-report/05-01-01-get-data.png)
2. **데이터 가져오기** 대화 상자에서 **SharePoint Online 목록**, **연결**을 차례로 클릭하거나 탭합니다.
   
    ![SharePoint 목록에 연결](./media/sharepoint-scenario-build-report/05-01-02-sharepoint-list.png)
3. SharePoint 사이트에 대한 URL을 입력한 다음 **확인**을 클릭하거나 탭합니다.
   
    ![SharePoint 목록 URL](./media/sharepoint-scenario-build-report/05-01-03-sharepoint-url.png)
4. 다음 대화 상자가 표시되면 올바른 자격 증명으로 로그인했는지 확인한 다음 **연결**을 클릭하거나 탭합니다.
   
    ![SharePoint 목록 자격 증명](./media/sharepoint-scenario-build-report/05-01-04-credentials.png)
5. **프로젝트 세부 정보** 및 **프로젝트 요청**을 선택한 다음 **편집**을 클릭하거나 탭합니다.
   
    ![SharePoint 목록 선택](./media/sharepoint-scenario-build-report/05-01-05-list-navigator.png)
   
    이제 쿼리 편집기에서 목록이 테이블로 표시됩니다.
   
    ![쿼리 편집기의 테이블](./media/sharepoint-scenario-build-report/05-01-06-query-editor.png)

### <a name="remove-unnecessary-columns-from-the-tables"></a>테이블에서 불필요한 열 제거
1. 왼쪽 탐색 창에서 **프로젝트 세부 정보**를 클릭하거나 탭합니다.
2. 가운데 창에서 **FileSystemObjectType** 열을 선택한 다음 **열 제거**를 클릭하거나 탭합니다.
   
    ![열 제거](./media/sharepoint-scenario-build-report/05-01-07-remove-column.png)
3. **ID** 열 뒤에 있는 두 열, 즉 **ServerRedirectedEmbedURL** 및 **ContentTypeId**를 제거합니다. 
   > [!TIP]
   > Shift 키를 사용하여 두 열을 선택한 다음 **열 제거**를 클릭하거나 탭합니다.
4. **PMAssigned** 열(총 22열)의 오른쪽에 있는 모든 열을 제거합니다. 테이블은 다음 이미지와 같습니다.
   
    ![쿼리 편집기의 프로젝트 세부 정보 테이블](./media/sharepoint-scenario-build-report/05-01-08-table-details.png)
5. 방금 진행한 과정을 **프로젝트 요청**에 대해 반복합니다. **FileSystemObjectType**, **ServerRedirectedEmbedURL**, **ContentTypeId** 및 모든 열을 **승인됨** 열 오른쪽으로 제거합니다(총 22열). 테이블은 다음 이미지와 같습니다.
   
    ![ 쿼리 편집기의 프로젝트 요청 테이블](./media/sharepoint-scenario-build-report/05-01-09-table-requests.png)

### <a name="change-the-data-type-on-project-details-columns"></a>프로젝트 세부 정보 열의 데이터 형식 변경
1. **ProjectedDays** 열을 선택하고 **데이터 형식: 모두**, **정수**를 차례로 클릭하거나 탭합니다.
   
    ![데이터 형식을 정수로 변경](./media/sharepoint-scenario-build-report/05-01-10-datatype-number.png)
2. **ActualDays** 열에 대해 이전 단계를 반복합니다.
3. **ApprovedDate** 열을 선택하고 **데이터 형식: 모두**, **날짜**를 차례로 클릭하거나 탭합니다.
   
    ![ 데이터 형식을 날짜로 변경](./media/sharepoint-scenario-build-report/05-01-11-datatype-date.png)

4. **ProjectedStartDate** 및 **ProjectedEndDate** 열에 대해 이전 단계를 반복합니다.

### <a name="change-the-data-type-on-project-requests-columns"></a>프로젝트 요청 열의 데이터 형식 변경

1. **EstimatedDays** 열을 선택하고 **데이터 형식: 모두**, **정수**를 차례로 클릭하거나 탭합니다.

2. **RequestDate** 열을 선택하고 **데이터 형식: 모두**, **날짜**를 차례로 클릭하거나 탭합니다.

### <a name="apply-and-save-changes"></a>변경 내용 적용 및 저장

1. **홈** 탭에서 **닫기 및 적용**을 클릭하여 쿼리 편집기를 닫고 기본 Power BI Desktop 창으로 돌아갑니다.
   
    ![변경 내용 닫기 및 적용](./media/sharepoint-scenario-build-report/05-01-12-close-apply.png)

2. **파일**, **저장**을 차례로 클릭하거나 탭하고 project-analysis.pbix라는 이름으로 저장합니다.

## <a name="step-2-improve-the-data-model"></a>2단계: 데이터 모델 향상
이제 SharePoint 목록의 데이터를 Power BI Desktop으로 가져왔으므로 데이터 모델링으로 이동합니다. 데이터 모델링은 시간이 많이 걸리는 프로세스일 수 있지만, Power BI Desktop의 목록 데이터를 더 많이 활용하기 위해 수행할 수 있는 몇 가지 흥미로운 작업에 대해 간략히 살펴보겠습니다.

* 두 테이블 간의 관계를 변경합니다.
* 평일(월-금)을 기준으로 계산할 수 있도록 날짜 테이블을 추가합니다.
* 계산 열을 추가하여 프로젝트 중요 시점 간의 시간 간격을 계산합니다.
* 측정값을 추가하여 프로젝트에 대한 예상 날짜와 실제 날짜의 차이를 계산합니다.

이러한 단계가 완료되면 모델에 향상된 기능을 활용하는 시각화를 작성할 수 있습니다. Power BI Desktop의 데이터 모델링에 대한 자세한 내용은 단계별 학습 과정의 [모델링](https://powerbi.microsoft.com/guided-learning/powerbi-learning-2-1-intro-modeling-data) 섹션을 참조하세요.

### <a name="change-table-relationships"></a>테이블 관계 변경
Power BI Desktop에서 목록을 가져올 때 두 테이블의 **ID** 열을 기준으로 하는 관계가 만들어집니다. 관계는 실제로 **프로젝트 요청** 테이블의 **ID** 열과 **프로젝트 세부 정보** 테이블의 **RequestId** 열 간의 관계입니다. 이제 수정해 보겠습니다.

1. **데이터 보기** 아이콘을 클릭하거나 탭합니다.
   
    ![데이터 보기](./media/sharepoint-scenario-build-report/05-02-01-data-view.png)

2. **모델링** 탭에서 **관계 관리**를 클릭하거나 탭합니다. 모든 데이터 모델링 단계에 대해 **데이터** 보기에서 이 탭을 유지합니다.
   
    ![관계 관리](./media/sharepoint-scenario-build-report/05-02-02-manage-relationships.png)

3. 기존 관계가 선택되어 있는지 확인하고, **삭제**를 클릭하거나 탭한 다음, **삭제**를 다시 클릭하거나 탭하여 확인합니다.
   
    ![관계 삭제](./media/sharepoint-scenario-build-report/05-02-03-delete-relationship.png)

4. **새로 만들기**를 클릭하여 다른 관계를 만듭니다.

5. **관계 만들기** 대화 상자에서 다음을 수행합니다.
   
   1. 첫 번째 테이블의 경우 **프로젝트 요청** 및 **ID** 열을 선택합니다.
   
   2. 두 번째 테이블의 경우 **프로젝트 세부 정보** 및 **RequestId** 열을 선택합니다.
   
   3. 화면은 다음 이미지와 같습니다. 준비가 되면 **확인**과 **닫기**를 차례로 클릭하거나 탭합니다.
      
       ![관계 만들기](./media/sharepoint-scenario-build-report/05-02-04-create-relationship.png)

### <a name="add-a-date-table-to-make-date-based-calculations-easier"></a>날짜를 기준으로 더 쉽게 계산하도록 날짜 테이블 추가
1. **새 테이블**을 클릭하거나 탭합니다.
   
    ![새 테이블](./media/sharepoint-scenario-build-report/05-02-05-modeling-table.png)
2. 수식 입력줄에 **Dates = CALENDARAUTO()** 수식을 입력합니다.
   
    ![Dates = CALENDARAUTO()가 있는 수식 입력줄](./media/sharepoint-scenario-build-report/05-02-06-formula-bar.png)
   
    이 수식은 단일 날짜 열이 있는 **Dates**라는 테이블을 만듭니다. 이 테이블은 다른 테이블의 모든 날짜를 포함하고 있으며, 날짜가 더 추가되면(예: 데이터를 새로 고친 경우) 자동으로 업데이트됩니다.
   
    이 수식과 이 섹션의 다른 수식에서는 Power BI 및 기타 기술의 수식 언어인 DAX(Data Analysis Expressions)를 사용합니다. 자세한 내용은 [Power BI Desktop의 DAX 기본 사항](https://docs.microsoft.com/power-bi/desktop-quickstart-learn-dax-basics)을 참조하세요.
3. Enter 키를 눌러 **Dates** 테이블을 만듭니다.
   
    ![Dates 테이블](./media/sharepoint-scenario-build-report/05-02-07-date-table.png)

### <a name="add-a-calculated-column-to-the-dates-table"></a>Dates 테이블에 계산 열 추가
1. 아직 Dates 테이블에 있으면 **새 열**을 클릭하거나 탭합니다.
   
    ![새 열](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 수식 입력줄에 **IsWeekDay = SWITCH(WEEKDAY(Dates[Date]), 1,0,7,0,1)** 수식을 입력합니다.
   
    이 수식은 **날짜** 열의 날짜가 평일인지 여부를 결정합니다. 날짜가 평일이면 **IsWeekDay** 열의 값이 1이고, 그렇지 않으면 0입니다.
3. Enter 키를 눌러 **IsWeekDay** 열을 **Dates** 테이블에 추가합니다.
   
    ![IsWeekDay 열 추가](./media/sharepoint-scenario-build-report/05-02-08-column-isweekday.png)

### <a name="add-a-calculated-column-to-the-project-details-table"></a>프로젝트 세부 정보 테이블에 계산 열 추가
1. 오른쪽 창에서 **프로젝트 세부 정보** 테이블, **새 열**을 차례로 클릭하거나 탭합니다.
   
    ![새 열](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 다음 수식을 수식 입력줄에 입력합니다.
   
    ```dax
    ApprovedStartDiff = CALCULATE(SUM(Dates[IsWeekday]),
       DATESBETWEEN(Dates[Date],
          'Project Details'[ApprovedDate],
          'Project Details'[ProjectedStartDate]
      )
    )
    ```
   
    이 수식은 프로젝트의 승인 시점과 예상 시작 시점 간의 차이를 계산합니다. **Dates** 테이블의 **IsWeekday** 열을 사용하므로 평일만 계산됩니다.
3. Enter 키를 눌러 **ApprovedStartDiff** 열을 **프로젝트 세부 정보** 테이블에 추가합니다.
   
    ![ApprovedStartDiff 열 추가](./media/sharepoint-scenario-build-report/05-02-09-column-approvedstartdiff.png)

### <a name="add-a-calculated-column-to-the-project-requests-table"></a>프로젝트 요청 테이블에 계산 열 추가
1. 오른쪽 창에서 **프로젝트 요청** 테이블, **새 열**을 차례로 클릭하거나 탭합니다.
   
    ![새 열](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 다음 수식을 수식 입력줄에 입력합니다.
   
    ```dax
    RequestDateAge = CALCULATE(SUM(Dates[IsWeekday]),
       DATESBETWEEN(Dates[Date],
          'Project Requests'[RequestDate],
          NOW()
       )
    )
    ```
   
    이 수식은 프로젝트를 요청한 날짜와 오늘 날짜(NOW ()) 간의 차이를 계산합니다. 다시 말하면 이 수식은 평일만 계산합니다. 이 열은 가장 오랫동안 보류 중인 프로젝트를 찾는 데 사용됩니다.
3. Enter 키를 눌러 **RequestDateAge** 열을 **프로젝트 요청** 테이블에 추가합니다.
   
    ![RequestDateAge 열 추가](./media/sharepoint-scenario-build-report/05-02-10-column-requestdateage.png)

### <a name="add-a-measure-to-the-project-details-table"></a>프로젝트 세부 정보 테이블에 측정값 추가
1. 오른쪽 창에서 **프로젝트 세부 정보** 테이블, **새 측정값**을 차례로 클릭하거나 탭합니다.
   
    ![새 측정값](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. 다음 수식을 수식 입력줄에 입력합니다.
   
    ```dax
    VarProjectedActual = DIVIDE(
        SUM('Project Details'[ActualDays]) - SUM('Project Details'[ProjectedDays]),
        SUM('Project Details'[ProjectedDays])
    )
    ```
   
    이 수식은 프로젝트의 실제 일 수와 예상 일 수 간의 차이를 계산합니다. 이 값을 계산 열 대신 측정값으로 추가하여 보고서에서 데이터가 필터링되거나 집계되는 방식에 관계 없이 올바른 결과를 반환합니다.
3. Enter 키를 눌러 **VarProjectedActual** 측정값을 **프로젝트 세부 정보** 테이블에 추가합니다.
   
    ![VarProjectedActual 측정값 추가](./media/sharepoint-scenario-build-report/05-02-11-measure-varprojectedactual.png)

### <a name="add-a-measure-to-the-project-requests-table"></a>프로젝트 요청 테이블에 측정값 추가
1. 오른쪽 창에서 **프로젝트 요청** 테이블, **새 측정값**을 차례로 클릭하거나 탭합니다.
   
    ![새 측정값](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. 다음 수식을 수식 입력줄에 입력합니다.
   
    ```dax
    MaxDaysPending = MAXX(
        FILTER('Project Requests', 'Project Requests'[Approved]="Pending"),
        'Project Requests'[RequestDateAge]
    )
    ```
   
    이 수식은 앞에서 정의한 계산 열을 기준으로 가장 오랫동안 보류 중인 프로젝트를 찾습니다.
3. Enter 키를 눌러 **MaxDaysPending** 측정값을 **프로젝트 요청** 테이블에 추가합니다.
   
    ![MaxDaysPending 측정값 추가](./media/sharepoint-scenario-build-report/05-02-12-measure-maxdayspending.png)

## <a name="step-3-create-report-visualizations"></a>3단계: 보고서 시각화 만들기
이제 많은 사람들이 데이터 분석을 고려하는 단계에 있습니다. 시각화를 만들어 데이터에서 패턴을 찾을 수 있도록 합니다. 이 단계에서는 네 가지 시각화를 만듭니다.

* 프로젝트에 예상 일 수와 실제 일 수를 표시하는 세로 막대형 차트
* 각 프로젝트의 차이를 표시하는 세로 막대형 차트
* 가장 오랫동안 보류 중인 프로젝트를 표시하는 카드
* 프로젝트의 승인 날짜와 예상 시작 날짜 사이의 시간을 표시하는 테이블

Power BI Desktop에서 이러한 보고서 시각화를 만들면, Power BI 서비스에 데이터와 보고서를 게시하여 대시보드를 만들고 공유할 수 있습니다. Power BI Desktop에서 보고서를 만드는 방법에 대한 자세한 내용은 단계별 학습 과정의 [시각화](https://powerbi.microsoft.com/guided-learning/powerbi-learning-3-1-intro-visualizations) 섹션을 참조하세요.

### <a name="create-a-bar-chart-to-show-projected-versus-actual"></a>예상 및 실제 데이터를 표시하는 막대형 차트 만들기
1. **보고서** 보기 아이콘을 클릭하거나 탭합니다. 이 보기는 나머지 시간 동안 Power BI Desktop에서 유지됩니다.
   
    ![보고서 보기](./media/sharepoint-scenario-build-report/05-03-01-report-view.png)
2. 오른쪽의 **시각화** 창에서 **묶은 세로 막대형 차트**를 클릭하거나 탭합니다.
   
    ![시각화 - 묶은 세로 막대형 차트](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. **PMAssigned** 및 **Title**을 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **축**으로 끌어갑니다.
   
    ![시각화 창의 축](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. **ActualDays** 및 **ProjectedDays**를 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **값**으로 끌어갑니다.
   
    ![시각화 창의 값](./media/sharepoint-scenario-build-report/05-03-03-value-projected.png)
5. 이제 시각화는 다음 이미지와 같습니다.
   
    ![PMAssigned별 ProjectedDays 및 ActualDays](./media/sharepoint-scenario-build-report/05-03-04-chart-projected.png)
6. **Status**를 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **필터** 영역으로 끌어간 다음, **완료됨** 확인란을 선택합니다.
   
   ![Status 열 기준 필터링](./media/sharepoint-scenario-build-report/05-03-05-filters-projected.png)
   
   이제 차트는 완료된 프로젝트만 표시하도록 필터링되어 예상 일 수와 실제 일 수를 비교하기 때문에 의미가 있습니다.
7. 차트의 왼쪽 위 모서리에 있는 화살표를 클릭하여 프로젝트 관리자와 프로젝트의 계층 구조를 위/아래로 이동합니다. 다음 이미지에서는 프로젝트를 드릴다운한 결과가 표시됩니다.
   
   ![자세한 세로 막대형 차트 분석](./media/sharepoint-scenario-build-report/05-03-06-chart-projected-drill.png)

### <a name="create-a-bar-chart-to-show-variance-from-projected"></a>예상 데이터를 표시하는 막대형 차트 만들기
1. 방금 만든 시각화 외부에서 캔버스를 클릭하거나 탭합니다.
2. 오른쪽의 **시각화** 창에서 **묶은 세로 막대형 차트**를 클릭하거나 탭합니다.
   
    ![시각화 - 묶은 세로 막대형 차트](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. **PMAssigned** 및 **Title**을 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **축**으로 끌어갑니다.
   
    ![시각화 창의 축](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. **VarProjectedActual**을 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **값**으로 끌어갑니다.
   
    ![시각화 창의 값](./media/sharepoint-scenario-build-report/05-03-07a-value-variance.png)
5. **Status**를 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **필터** 영역으로 끌어간 다음, **완료됨** 확인란을 선택합니다.
   
    ![Status 열 기준 필터링](./media/sharepoint-scenario-build-report/05-03-07b-filters-variance.png)
   
    이제 시각화는 다음 이미지와 같습니다.
   
    ![PMAssigned별 VarProjectedActual](./media/sharepoint-scenario-build-report/05-03-08-chart-variance.png)
   
    이 차트에서는 Irvin Sayers와 Joni Sherman이 실행한 프로젝트를 비교하여 가변성의 정도를 확인할 수 있습니다. 프로젝트별 가변성 및 예상 일 수가 실제 일 수보다 많거나 적은지 여부를 자세히 확인합니다.
   
    ![Title별 VarProjectedActual](./media/sharepoint-scenario-build-report/05-03-09-chart-variance-drill.png)
6. 더 많은 시각화를 만들기 전에 이미 만든 시각화를 이동하고 크기를 조정하여 나란히 맞춥니다.
   
    ![나란히 차트 맞춤](./media/sharepoint-scenario-build-report/05-03-10-two-charts.png)

### <a name="create-a-card-that-shows-the-longest-pending-project"></a>가장 오랫동안 보류 중인 프로젝트를 표시하는 카드 만들기
1. 방금 만든 시각화 외부에서 캔버스를 클릭하거나 탭합니다.
2. 오른쪽의 **시각화** 창에서 **카드**를 클릭하거나 탭합니다.
   
    ![시각화 - 카드](./media/sharepoint-scenario-build-report/05-03-11-visuals-card.png)
3. **MaxDaysPending**을 **필드** 창의 **프로젝트 요청**에서 **시각화** 창의 **필드**로 끌어갑니다.
   
    ![시각화 창의 필드](./media/sharepoint-scenario-build-report/05-03-12-value-max.png)
4. **서식**(페인트 롤러)을 클릭하거나 탭한 다음 **테두리**를 **켜기**로 설정합니다.
   
    ![서식 복사 - 테두리](./media/sharepoint-scenario-build-report/05-03-13a-format.png)
5. **제목**을 **켜기**로 설정하고 "최대 승인 보류 일 수"라는 제목을 추가합니다.
   
    ![제목 추가](./media/sharepoint-scenario-build-report/05-03-13b-title.png)
   
    이제 시각화는 다음 이미지와 같습니다.
   
    ![ 최대 승인 보류 일 수](./media/sharepoint-scenario-build-report/05-03-14-chart-max.png)
   
    이 보고서를 게시한 후 보류 중인 프로젝트에 대한 최대값이 특정 임계값에 도달하면 이 타일을 사용하여 경고를 트리거합니다.

### <a name="create-a-table-that-shows-the-time-between-project-approval-and-projected-start-date"></a>프로젝트의 승인 날짜와 예상 시작 날짜 사이의 시간을 표시하는 테이블을 만듭니다.
1. 방금 만든 시각화 외부에서 캔버스를 클릭하거나 탭합니다.
2. 오른쪽의 **시각화** 창에서 **테이블**을 클릭하거나 탭합니다.
   
    ![시각화 - 테이블](./media/sharepoint-scenario-build-report/05-03-15-visuals-table.png)
3. **PMAssigned** **Title** 및 **ApprovedStartDiff**를 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **값**으로 끌어갑니다.
   
    ![시각화 창의 값](./media/sharepoint-scenario-build-report/05-03-16-value-diff.png)
4. **ProjectedStartDate**를 **필드** 창의 **프로젝트 세부 정보**에서 **시각화** 창의 **필터** 영역으로 끌어간 다음, **(비어 있음)** 을 제외한 모든 날짜를 선택합니다.
   
    ![ProjectedStartDate별 필터링](./media/sharepoint-scenario-build-report/05-03-17-filters-diff.png)
5. 모든 데이터가 표시되도록 테이블 열의 크기를 조정하고 **ApprovedStartDiff**를 기준으로 내림차순으로 정렬합니다. 이제 시각화는 다음 이미지와 같습니다.
   
    ![ApprovedStartDiff 값이 있는 테이블](./media/sharepoint-scenario-build-report/05-03-18-chart-diff.png)
6. **값** 영역에서 **ApprovedStartDiff**의 아래쪽 화살표를 클릭하거나 탭한 다음 **평균**을 클릭하거나 탭합니다. 이제 프로젝트 승인과 예상 시작 날짜 사이의 평균 기간이 표시됩니다.
   
    ![평균 계산](./media/sharepoint-scenario-build-report/05-03-20a-average-menu.png)
7. **ApprovedStartDiff**의 아래쪽 화살표를 다시 클릭하거나 탭하고, **조건부 서식**을 클릭하거나 탭한 다음 **배경색 눈금**을 클릭하거나 탭합니다.
   
   ![조건부 서식](./media/sharepoint-scenario-build-report/05-03-20b-conditional-menu.png)
8. **최소** 및 **최대** 필드의 색을 아래와 같이 설정한 다음 **확인**을 클릭하거나 탭합니다.
   
   ![조건부 서식 옵션](./media/sharepoint-scenario-build-report/05-03-21-conditional-dialog.png)
   
   이제 시각화는 다음 이미지와 같습니다.
   
   ![완성된 조건부 서식](./media/sharepoint-scenario-build-report/05-03-22-chart-diff-completed.png)
   
   여기서 알 수 있듯이 Irvin Sayers가 실행하는 프로젝트는 승인 후 훨씬 나중에 시작되는 경향이 있습니다. 할당된 관리자 이외의 다른 요인이 있을 수 있지만 이는 조사할 가치가 있습니다.

보고서 섹션의 끝 부분에 있으며, 이제 SharePoint에서 가져온 데이터를 기반으로 하여 완전한 보고서를 만들고 Power BI Desktop에서 정리 및 모델링해야 합니다. 모든 작업이 계획에 따라 진행되었으면 보고서는 다음 이미지와 같습니다.

![완성된 보고서](./media/sharepoint-scenario-build-report/05-03-23-report-completed.png)

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [Power BI 프로젝트 보고서를 게시하고 대시보드를 만듭니다](sharepoint-scenario-publish-report.md).

