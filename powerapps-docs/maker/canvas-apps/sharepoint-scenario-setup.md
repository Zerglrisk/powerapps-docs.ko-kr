---
title: PowerApps, Microsoft Flow 및 Power BI와의 통합을 위한 SharePoint Online 목록 설정 | Microsoft Docs
description: 이 작업에서는 앱, 흐름, 보고서 및 대시보드의 데이터 원본으로 사용할 SharePoint 목록을 설정합니다.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7be4a0574c1a81684188eaede4b6e80b02e7b7cc
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63319157"
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-powerapps-microsoft-flow-and-power-bi"></a>PowerApps, Microsoft Flow 및 Power BI와의 통합을 위한 SharePoint Online 목록 설정
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악해야 합니다.

SharePoint는 많은 공유 및 공동 작업 기능이 있지만 이 시나리오에서는 [SharePoint 목록](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7) 기능을 초점을 맞춥니다. 목록은 팀 구성원 및 다른 사이트 사용자와 공유할 수 있는 데이터 컬렉션입니다. 이 시나리오에 사용된 목록을 검토한 다음 사용자 고유의 SharePoint Online 사이트에서 목록을 만들 수 있습니다.

## <a name="step-1-understand-the-lists"></a>1 단계: 목록 이해
첫 번째 목록은 프로젝트 요청자가 요청을 추가하는 **프로젝트 요청**입니다. 그런 다음 프로젝트 승인자가 해당 요청을 검토하여 승인하거나 거부합니다.

| **목록 열** | **데이터 형식** | **설명** |
| --- | --- | --- |
| Title |한 줄 텍스트 |프로젝트 이름에 사용되는 기본 열 |
| Description |한 줄 텍스트 | |
| ProjectType |한 줄 텍스트 |값: 새 하드웨어, 업그레이드된 하드웨어, 새 소프트웨어, 업그레이드된 소프트웨어 |
| RequestDate |Date | |
| Requestor |한 줄 텍스트 | |
| EstimatedDays |번호 |요청자 예상 값과 프로젝트 관리자 예상 및 실제 값의 비교를 사용하도록 설정합니다. |
| Approved |한 줄 텍스트 |값: 보류 중, 예, 아니요 |

> [!NOTE]
> 또한 SharePoint로 생성되고 기본적으로 숨겨진 **ID** 열을 사용합니다. 간단히 하기 위해 기본 데이터 형식을 사용하지만, 실제 앱에서는 **개인 또는 그룹**과 같이 **Requestor** 열에 대해 더 복잡한 형식을 사용할 수 있습니다. PowerApps에서 지원하는 데이터 형식에 대한 자세한 내용은 [Microsoft PowerApps에서 SharePoint로 연결](connections/connection-sharepoint-online.md#known-issues)을 참조하세요.

두 번째 목록은 프로젝트 관리자 할당과 같이 승인된 모든 프로젝트에 대한 세부 정보를 추적하는 **프로젝트 세부 정보**입니다.

| **목록 열** | **데이터 형식** | **설명** |
| --- | --- | --- |
| Title |한 줄 텍스트 |프로젝트 이름에 사용되는 기본 열 |
| RequestID |번호 |**프로젝트 요청** 목록 **ID** 열의 값과 일치합니다. |
| ApprovedDate |Date | |
| Status |한 줄 텍스트 |값: 시작되지 않음, 진행 중, 완료됨 |
| ProjectedStartDate |Date |프로젝트 관리자가 프로젝트를 시작할 것으로 예상하는 시기 |
| ProjectedEndDate |Date |프로젝트 관리자가 프로젝트를 종료할 것으로 예상하는 시기 |
| ProjectedDays |번호 |작업일 - 일반적으로 계산되지만 이 시나리오에서는 그렇지 않습니다. |
| ActualDays |번호 |프로젝트를 완료한 시기 |
| PMAssigned |한 줄 텍스트 |프로젝트 관리자 |

## <a name="step-2-create-and-review-the-lists"></a>2단계: 목록 생성 및 검토
이 시나리오를 계속하려면 두 개의 SharePoint 목록을 만들어 샘플 데이터로 채워야 합니다. 이제 목록을 만들고 샘플 데이터를 이 목록에 붙여넣는 방법을 보여 주겠습니다. [다운로드 패키지](https://aka.ms/o4ia0f)의 Excel 파일이 있는지 확인합니다.

> [!NOTE]
> 이 단계에서는 Internet Explorer를 사용합니다.

### <a name="create-the-lists"></a>목록 만들기

1. Internet Explorer의 SharePoint 사이트에서 **새로 만들기**, **목록**을 차례로 클릭하거나 탭합니다.
   
    ![새 SharePoint 목록 만들기](./media/sharepoint-scenario-setup/01-01-01-new-list.png)

2. "프로젝트 요청" 이름을 입력한 다음 **만들기**를 클릭하거나 탭합니다.
   
    ![새 목록에 대한 이름 지정](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    기본 **Title** 필드가 포함된 **프로젝트 요청** 목록이 만들어집니다.
   
    ![프로젝트 요청 목록](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>목록에 열 추가

1. ![새 항목 아이콘](./media/sharepoint-scenario-setup/icon-new.png), **한 줄 텍스트**를 차례로 클릭하거나 탭합니다.
   
    ![한 줄 텍스트 필드 추가](./media/sharepoint-scenario-setup/01-01-04-add-column.png)

2. [이름]에서 "Description"을 입력한 다음 **저장**을 클릭하거나 탭합니다.
   
3. **1** 및 **2** 단계를 반복합니다. 목록의 다른 열은 다음과 같습니다.
   
   1. **한 줄 텍스트** > "ProjectType"
   2. **날짜** > "RequestDate"
   3. **한 줄 텍스트** > "Requestor"
   4. **숫자** > "EstimatedDays"
   5. **한 줄 텍스트** > "Approved"

### <a name="copy-data-into-the-list"></a>목록에 데이터 복사
1. **빠른 편집**을 클릭하거나 탭합니다.
   
    ![목록에 대한 빠른 편집](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. 그리드에서 셀을 선택합니다.
   
    ![모든 열이 있는 목록](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. project-requests.xlsx 통합 문서를 열고 모든 데이터(머리글 제외)를 선택합니다.
   
    ![프로젝트 요청 Excel 테이블](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. 데이터를 복사하여 SharePoint의 그리드에 붙여넣은 다음 **완료**를 클릭하거나 탭합니다.
   
    ![완성된 목록(데이터 포함)](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. project-details.xlsx 통합 문서를 사용하여 "프로젝트 세부 정보" 목록에 대한 목록 만들기 및 복사 프로세스를 반복합니다. 열 이름과 데이터 형식에 대해서는 [1단계: 목록 이해](#step-1-understand-the-lists)에서 프로젝트 세부 정보 테이블을 참조합니다.

## <a name="step-3-update-connections-to-samples---optional"></a>3단계: 선택 사항 - 샘플에 대한 연결 업데이트
이 자습서 시리즈의 소개 부분에서 설명했듯이 [다운로드 패키지](https://aka.ms/o4ia0f)에는 두 개의 샘플 앱과 보고서가 포함되어 있습니다. 이러한 샘플을 사용하지 않고 이 시나리오를 완료할 수 있지만, 샘플을 사용하려면 SharePoint 목록에 대한 연결을 업데이트해야 합니다. *사용자*의 목록을 데이터 원본으로 사용하도록 연결을 업데이트합니다.

### <a name="update-connections-for-the-sample-apps"></a>샘플 앱에 대한 연결 업데이트

1. [PowerApps Studio](https://create.powerapps.com/studio/)의 왼쪽 창에서 **열기**를 클릭하거나 탭합니다. 

2. **찾아보기**를 클릭하거나 탭한 다음 다운로드한 **project-management-app.msapp** 파일을 엽니다.

3. PowerApps에서 SharePoint를 사용할 수 있도록 **허용**을 클릭하거나 탭합니다.

4. 리본의 **보기** 탭에서 **데이터 원본**을 클릭하거나 탭합니다.

    ![PowerApps 데이터 원본](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
5. **데이터** 창에서 **프로젝트 세부 정보** 옆의 줄임표(**. . .**)를 클릭하거나 탭한 다음**제거**를 클릭하거나 탭합니다.
   
    ![프로젝트 세부 정보 데이터 원본 제거](./media/sharepoint-scenario-setup/01-03-02-remove.png)
6. **데이터 원본 추가**를 클릭하거나 탭합니다.
   
    ![데이터 원본 추가](./media/sharepoint-scenario-setup/01-03-03-add.png)

7. PowerApps에서 SharePoint 연결이 설정되어 있는지 여부에 따라 목록에 연결하는 방법이 두 가지 있습니다. 

    * SharePoint 연결이 이미 표시되어 있으면 해당 연결을 클릭하거나 누릅니다.

        ![기존 연결](./media/sharepoint-scenario-setup/01-03-03aa-existing-connection.png)

    * SharePoint 연결이 표시되지 않으면 **새 연결**을 클릭하거나 탭합니다.

        ![새 연결](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)

        그런 다음 **SharePoint**와 **만들기**를 차례로 클릭하거나 탭합니다.
   
        ![SharePoint 연결](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)

8. 만든 목록이 포함된 SharePoint Online 사이트에 대한 URL을 입력한 다음 **이동**을 클릭하거나 탭합니다.
   
    ![SharePoint URL](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. **프로젝트 세부 정보** 목록을 선택한 다음 **연결**을 클릭하거나 탭합니다.
   
    ![프로젝트 세부 정보 목록](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    설정한 연결이 이제 **데이터** 창에 표시됩니다.
   
    ![데이터 원본](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)

10. **프로젝트 세부 정보** 옆의 줄임표(**. . .**), **새로 고침**을 차례로 클릭하거나 탭합니다.
    
    ![프로젝트 세부 정보 데이터 원본 새로 고침](./media/sharepoint-scenario-setup/01-03-02-remove.png)

11. 오른쪽 위 모서리에서 ![앱 실행 아이콘을 클릭하여](./media/sharepoint-scenario-setup/icon-run-arrow.png) 앱을 실행하고 연결이 제대로 작동하는지 확인합니다.

12. **파일**을 클릭하거나 탭한 다음 앱을 클라우드에 저장합니다. 

12. **프로젝트 요청** 목록을 사용하여 **project-requests-app.msapp**에 대해 이 섹션의 단계를 반복합니다.

### <a name="update-connections-for-the-sample-report"></a>샘플 보고서에 대한 연결 업데이트
1. Power BI Desktop에서 **project-analysis.pbix**를 엽니다.

2. 리본의 **홈** 탭에서 **쿼리 편집**, **데이터 원본 설정**을 차례로 클릭하거나 탭합니다.
   
    ![쿼리 편집](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)

3. **원본 변경**을 클릭하거나 탭합니다.
   
    ![데이터 원본 설정](./media/sharepoint-scenario-setup/01-03-05-settings.png)

4. SharePoint Online 사이트에 대한 URL을 입력한 다음 **확인**과 **닫기**를 차례로 클릭하거나 탭합니다.
   
    ![SharePoint 목록 URL](./media/sharepoint-scenario-setup/01-03-06-list-url.png)

5. Power BI Desktop은 리본 아래에 배너를 표시하므로 변경 내용을 적용하고 새 원본에서 데이터를 가져올 수 있습니다. **변경 내용 적용**을 클릭하거나 탭합니다.
   
    ![쿼리 변경 내용 적용](./media/sharepoint-scenario-setup/01-03-07-apply.png)

6. Microsoft 계정(SharePoint Online에 액세스하는 데 사용하는 계정)으로 로그인한 다음 **연결**을 클릭하거나 탭합니다.
   
    ![SharePoint Online에 연결](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [프로젝트 요청을 처리하는 앱을 생성합니다](sharepoint-scenario-generate-app.md).

