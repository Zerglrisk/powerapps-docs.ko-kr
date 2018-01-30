---
title: "SharePoint Online에서 Power BI 프로젝트 보고서 포함 | Microsoft Docs"
description: "이 작업에서는 두 개의 목록을 호스팅하는 동일한 SharePoint Online 사이트에 Power BI 보고서를 포함합니다."
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
ms.openlocfilehash: 481e6d13cce7624cf46cadbf78f877fdfb9fd481
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2018
---
# <a name="embed-the-power-bi-project-report-in-sharepoint-online"></a>SharePoint Online에서 Power BI 프로젝트 보고서 포함
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악해야 합니다.

이 시나리오의 최근 작업은 두 개의 목록을 호스팅하는 동일한 SharePoint Online 사이트에 Power BI 보고서를 포함했습니다. Power BI는 포함하는 다양한 방법을 지원하며, 최근에 웹 및 모바일 보기를 위해 SharePoint 페이지에 직접 통합을 추가했습니다.

Power BI는 이 형식의 포함을 사용하여 보고서를 웹 파트로 포함하고, 사용자에게 적절한 액세스 권한을 제공하고, 포함된 보고서 및 powerbi.com에 있는 보고서를 클릭할 수 있습니다. 먼저 Power BI에서 embed 링크를 생성한 다음 만든 페이지에서 해당 링크를 사용합니다. 포함에 대한 자세한 내용은 [SharePoint Online에서 보고서 웹 파트 포함](https://powerbi.microsoft.com/documentation/powerbi-service-embed-report-spo)(특히 요구 사항 섹션)을 참조하세요.

## <a name="step-1-generate-an-embed-link"></a>1단계: embed 링크 생성
1. Power BI에 로그인하고, 왼쪽 탐색 창에서 보고서 이름을 클릭하거나 누릅니다.
   
    ![보고서로 이동](./media/sharepoint-scenario-embed-report/08-01-01-reports.png)
2. **SharePoint Online에 포함**을 클릭하거나 누릅니다.
   
    ![SharePoint Online에 포함](./media/sharepoint-scenario-embed-report/08-01-02-embed-spo.png)
3. 대화 상자에서 파일로 embed 링크를 복사한 다음 **닫기**를 클릭합니다. SharePoint 페이지를 만든 다음 링크를 사용합니다.
   
    ![SharePoint의 Embed 링크](./media/sharepoint-scenario-embed-report/08-01-03-embed-url.png)

## <a name="step-2-embed-the-report"></a>2단계: 보고서 포함
1. SharePoint에 로그인한 다음 **사이트 콘텐츠**를 클릭하거나 누릅니다.
   
    ![SharePoint 사이트 콘텐츠](./media/sharepoint-scenario-embed-report/08-01-04-site-contents.png)
2. 팀 홈페이지에서 보고서만 포함할 수 있지만 이에 대한 별도 페이지를 만드는 방법을 보여줍니다. **새로 만들기** 및 **페이지**를 차례로 클릭하거나 누릅니다.
   
    ![새 SharePoint 페이지](./media/sharepoint-scenario-embed-report/08-01-05-new-page.png)
3. "프로젝트 분석"과 같이 페이지의 이름을 입력합니다.
4. ![더하기 아이콘](./media/sharepoint-scenario-embed-report/icon-plus.png) 및 **Power BI**를 차례로 클릭하거나 누릅니다.
   
    ![Power BI 페이지 추가 파트](./media/sharepoint-scenario-embed-report/08-01-06-add-page-part.png)
5. **보고서 추가**를 차례로 클릭하거나 누릅니다.
   
    ![보고서 추가](./media/sharepoint-scenario-embed-report/08-01-07-add-report.png)
6. 오른쪽 창에서 embed URL을 **Power BI 보고서 링크** 상자에 복사합니다. **필터 창 표시** 및 **탐색 창 표시**를 모두 **켜기**로 설정합니다.
   
    ![보고서 설정](./media/sharepoint-scenario-embed-report/08-01-08-report-settings.png)
7. 이제 보고서는 페이지에 포함됩니다. **게시**를 클릭하여 기본 보고서에 액세스할 수 있는 모든 사용자가 사용할 수 있도록 설정합니다.
   
    ![완료를 포함하는 보고서](./media/sharepoint-scenario-embed-report/08-01-09-report-complete.png)

## <a name="step-3-grant-access-to-the-report"></a>3단계: 보고서에 액세스 권한 부여
권장한 대로 Office 365 그룹을 사용 중인 경우 액세스 권한이 필요한 사용자가 Power BI 서비스 내에서 그룹 작업 영역의 멤버여야 합니다. 이렇게 하면 사용자는 해당 그룹의 콘텐츠를 볼 수 있습니다. 자세한 내용은 [Power BI에서 그룹 만들기](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-group-in-power-bi)를 참조하세요.

그러면 이 시나리오의 경우 Power BI에서 작업을 래핑합니다. Power BI에 SharePoint 목록의 데이터를 끌어오기 시작하여 이제는 Power BI 보고서를 SharePoint에 완전히 포함하게 되었습니다.

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [만든 워크플로를 끝까지 실행](sharepoint-scenario-summary.md)합니다.

