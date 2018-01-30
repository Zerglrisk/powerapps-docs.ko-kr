---
title: "Power BI 프로젝트 보고서 게시 및 대시보드 만들기 | Microsoft Docs"
description: "이 작업에서는 데이터 집합을 게시하고 Power BI 서비스에 보고합니다. 그런 다음 보고서를 기반으로 하여 대시보드를 만듭니다."
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: cb300617fbf08f7b9ed5ff87ed5633d7714d51e0
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2018
---
# <a name="publish-the-power-bi-project-report-and-create-a-dashboard"></a>Power BI 프로젝트 보고서 게시 및 대시보드 만들기
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악해야 합니다.

이 작업에서는 데이터 집합을 게시하고 Power BI 서비스에 보고합니다. 그런 다음 보고서를 기반으로 하여 대시보드를 만듭니다. 대부분의 경우 보고서에는 많은 수의 시각화가 있으며, 대시보드에는 하위 집합만 사용됩니다. 여기서는 네 가지 시각화를 모두 대시보드에 추가합니다.

## <a name="step-1-publish-the-dataset-and-report"></a>1단계: 데이터 집합 및 보고서 게시
1. Power BI Desktop의 **홈** 탭에서 **게시**를 클릭하거나 탭합니다.
   
    ![데이터 집합 및 보고서 게시](./media/sharepoint-scenario-publish-report/06-01-01-publish.png)
2. Power BI 서비스에 아직 로그인하지 않은 경우 계정을 입력한 다음 **로그인**을 클릭하거나 탭합니다.
   
    ![계정에 로그인](./media/sharepoint-scenario-publish-report/06-01-02-account.png)
3. 암호를 입력하고 **로그인**을 클릭하거나 탭합니다.
   
    ![계정 암호 입력](./media/sharepoint-scenario-publish-report/06-01-03-password.png)
4. 보고서의 대상을 선택한 다음 **선택**을 클릭하거나 탭합니다. SharePoint에서 보고서에 쉽게 액세스하려면 그룹 작업 영역에 게시하는 것이 좋습니다. 이 경우 **프로젝트 관리** 그룹 작업 영역에 게시됩니다. 자세한 내용은 [Power BI에서 그룹 만들기](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-group-in-power-bi)를 참조하세요.
   
    ![대상 작업 영역](./media/sharepoint-scenario-publish-report/06-01-04-workspace.png)
5. 게시가 완료되면 **Power BI에서 'project-analysis.pbx' 열기**를 클릭하거나 탭합니다.
   
    ![게시 성공](./media/sharepoint-scenario-publish-report/06-01-05-open-report.png)
6. Power BI 서비스는 브라우저에서 보고서를 로드합니다. 왼쪽 위**(a)**에 있는 메뉴를 클릭하거나 탭하여 왼쪽 탐색 창을 표시합니다.
   
    ![Power BI 서비스의 보고서](./media/sharepoint-scenario-publish-report/06-01-06-service-report.png)
   
    게시할 때 Power BI Desktop에서 데이터 집합**(d)**과 보고서**(c)**를 업로드했음을 알 수 있습니다. Power BI Desktop이 아닌 서비스에서 대시보드를 만든 경우 이 작업 영역에는 아직 대시보드**(b)**가 없습니다. 이제 대시보드를 만들어 보겠습니다.
   
    > [!NOTE]
> Power BI에는 새로운 탐색 환경이 제공되어 사이트에서 사용하도록 설정할 수 있습니다. 왼쪽 탐색 창이 위의 이미지와 다르게 표시되는 경우 자세한 내용은 [새로운 Power BI 탐색 환경](https://powerbi.microsoft.com/documentation/powerbi-service-the-new-power-bi-experience)을 참조하세요.

## <a name="step-2-configure-credentials-for-refresh"></a>2단계: 새로 고침에 대한 자격 증명 구성
1. 서비스의 오른쪽 위 모서리에서 ![기어 아이콘](./media/sharepoint-scenario-publish-report/icon-gear.png), **설정**을 차례로 클릭하거나 탭합니다.
2. **데이터 집합**,**프로젝트 분석**을 차례로 클릭하거나 탭합니다.
   
    ![프로젝트 분석 데이터 집합](./media/sharepoint-scenario-publish-report/06-01-07-dataset.png)
3. **데이터 원본 자격 증명**을 펼친 다음 **자격 증명 편집**을 클릭하거나 탭합니다.
   
    ![데이터 원본 자격 증명 편집](./media/sharepoint-scenario-publish-report/06-01-08-credentials.png)
4. 인증 방법으로 **OAuth2**를 선택하고 **로그인**을 클릭하거나 탭합니다.
   
    ![SharePoint에 로그인](./media/sharepoint-scenario-publish-report/06-01-09-sign-in.png)
5. SharePoint 목록에 대한 권한이 있는 계정을 선택하거나 로그인합니다.
   
    ![Office 365에 로그인](./media/sharepoint-scenario-publish-report/06-01-10-account.png)
   
    프로세스가 완료되면 서비스에서 다음 메시지가 표시됩니다.
   
    ![데이터 원본이 업데이트됨](./media/sharepoint-scenario-publish-report/06-01-11-updated.png)

## <a name="step-3-create-a-dashboard"></a>3단계: 대시보드 만들기
1. 서비스에서 왼쪽 위의 차트를 클릭하거나 탭한 다음 ![핀 고정 아이콘을 클릭하거나](./media/sharepoint-scenario-publish-report/icon-pin.png)줄임표(...)를 클릭한 다음
   
    ![차트 고정](./media/sharepoint-scenario-publish-report/06-01-12-pin-projected.png)
2. 고정하려는 대시보드에 대한 이름을 입력한 다음 **핀 고정**을 클릭하거나 탭합니다.
   
    ![새 대시보드에 차트 고정](./media/sharepoint-scenario-publish-report/06-01-13-pin-new.png)
3. 왼쪽 위의 차트를 클릭하거나 탭한 다음 ![핀 고정 아이콘을 클릭하거나](./media/sharepoint-scenario-publish-report/icon-pin.png)줄임표(...)를 클릭한 다음
   
    ![차트 고정](./media/sharepoint-scenario-publish-report/06-01-14-pin-variance.png)
4. 기존 대시보드를 선택하고 **핀 고정**을 클릭하거나 탭합니다.
   
    ![기존 대시보드에 차트 고정](./media/sharepoint-scenario-publish-report/06-01-15-pin-existing.png)

5. 다른 두 시각적 개체에 대해 핀 고정 프로세스를 반복합니다.

6. 왼쪽 탐색 창에서 대시보드 이름을 클릭하거나 탭합니다.
   
    ![사이트 탐색 창의 새 대시보드](./media/sharepoint-scenario-publish-report/06-01-16-dashboard-menu.png)

7. 대시보드를 검토합니다. 타일을 클릭하면 보고서로 돌아갑니다.
   
    ![완성된 대시보드](./media/sharepoint-scenario-publish-report/06-01-17-dashboard-completed.png)

이제 대부분의 Power BI 작업을 마무리했습니다. 보고서와 대시보드를 만드는 첫 번째 경험이었다면 축하합니다! 이미 숙련된 전문가라면 신속히 다음 단계로 진행하시기를 바랍니다. 이제는 대시보드에 주의를 기울여야 할 때 알릴 수 있도록 경고를 추가합니다.

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [Power BI 프로젝트 보고서에 대한 데이터 경고를 설정합니다](sharepoint-scenario-alerts-flow.md).

