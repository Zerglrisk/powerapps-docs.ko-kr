---
title: SharePoint Online과 Power Apps, 파워 자동화 및 Power BI 통합 (소개) | Microsoft Docs
description: 이 자습서 시리즈에서는 sharepoint 목록과 SharePoint Online과 통합 되는 세 가지 주요 기술 (Power Apps, 파워 자동화 및 Power BI)을 기반으로 하는 프로젝트 관리를 위한 기본 캔버스 앱을 빌드하는 방법에 대해 살펴봅니다.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/05/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 45f33285b288dc273caeff1e85591210cc3deb8c
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959544"
---
# <a name="integrate-power-apps-power-automate-and-power-bi-with-sharepoint-online"></a>SharePoint Online과 Power Apps, 파워 자동화 및 Power BI 통합
SharePoint Online을 가지고 있고 비즈니스 프로세스를 더 효율적으로 자동화하고 간소화하고 싶습니까? Power Apps, 파워 자동화 또는 Power BI으로 작업 했지만 SharePoint Online에서 사용 하는 방법을 잘 모를 수 있습니다. 그렇다면 제대로 찾아오셨습니다! 이 자습서 시리즈에서는 sharepoint 목록과 SharePoint Online과 통합 되는 세 가지 주요 기술 (Power Apps, 파워 자동화 및 Power BI)을 기반으로 하는 프로젝트 관리를 위한 기본 캔버스 앱을 빌드하는 방법에 대해 살펴봅니다. 이러한 기술을 함께 사용하면 비즈니스를 *측정*하고 결과에서 *작동*하고 워크플로를 *자동화*할 수 있습니다. 이 시리즈를 마치면 다음과 같이 멋진 시나리오를 갖게 됩니다.

![완성된 시나리오에 대한 다이어그램](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>비즈니스 시나리오
이 시리즈의 자습서에서 Contoso 회사는 요청, 승인, 개발, 최종 검토에 이르기까지 프로젝트의 수명 주기를 관리하는 SharePoint Online 사이트를 운영하고 있습니다. 부서 책임자와 같은 *프로젝트 요청자*는 SharePoint 목록에 항목을 추가하여 IT 프로젝트를 요청합니다. IT 관리자와 같은 *프로젝트 승인자*는 이 프로젝트를 검토한 다음 승인하거나 거부합니다. 승인되면 프로젝트가 *프로젝트 관리자*에게 할당되고 추가 세부 정보가 동일한 앱을 통해 두 번째 목록에 추가됩니다. *비즈니스 분석가*는 SharePoint에 포함된 Power BI 보고서를 사용하여 현재 및 완성된 프로젝트를 검토합니다.  전원 자동화는 승인 전자 메일을 보내고 Power BI 경고에 응답 하는 데 사용 됩니다.

## <a name="getting-started-quickly"></a>빠른 시작
이 시리즈의 자습서에서 소개하는 시나리오는 완전한 프로젝트 관리 및 분석 앱에 비해 간단하지만, 모든 작업을 완료하는 데 약간의 시간이 걸립니다. Power Apps를 사용 하는 방법에 대 한 간략 한 소개, 파워 자동화 및 SharePoint와의 Power BI을 원하는 경우 다음 문서를 확인 하세요.

* **PowerApps**: sharepoint [내에서 Power Apps를 사용 하 여 앱 만들기](app-from-sharepoint.md#create-an-app-from-within-sharepoint-online) 및 [sharepoint 목록의 데이터를 관리 하는 앱 만들기](app-from-sharepoint.md)
* **전원 자동화**: [전원 자동화에서 승인 대기](https://docs.microsoft.com/flow/wait-for-approvals)
* **Power BI**: [SharePoint Online에서 보고서 웹 파트 포함](https://docs.microsoft.com/power-bi/service-embed-report-spo)

완료되었으면 이 전체 시나리오를 다시 확인하시기 바랍니다.

시나리오 내에서도 관심 있는 작업에 집중하고 시간이 지나면서 작업을 완료할 수 있습니다. 작업 1에서 SharePoint 목록을 설정하면 임의의 순서로 작업 2-5를 수행할 수 있습니다. 그런 다음 작업 6-8을 순차적으로 수행하면 됩니다. 마지막으로, 이 시나리오에 대한 [다운로드 패키지](https://aka.ms/o4ia0f)의 일부로 완성된 두 개의 앱과 Power BI Desktop 보고서를 포함시켰습니다. 각 작업의 모든 단계를 거치지 않아도 예제를 통해 이러한 단계를 확인하고 알아볼 수 있습니다.

## <a name="prerequisites"></a>필수 조건
이 시나리오를 완료하려면 다음 구독 및 데스크톱 도구가 필요합니다. Office 365 Business Premium subscription에는 Power Apps 및 파워 자동화가 포함 됩니다.

| **구독 또는 도구** | **링크** |
| --- | --- |
| Office 365 Business Premium 구독 |[평가판 구독](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| Power BI Pro 구독 |[평가판 구독](https://powerbi.microsoft.com/get-started/)(**평가판 사용해 보기** 클릭) |
| Power BI Desktop |[무료 다운로드](https://powerbi.microsoft.com/get-started/)(**무료 다운로드** 클릭) |

이론적으로는 각 기술에 대한 기본 지식이 있지만, 이러한 기술 중 일부를 처음 사용하는 경우에도 시나리오를 완료할 수 있습니다. 속도를 높이려면 다음 콘텐츠를 사용합니다.

* [SharePoint 시작](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Power Apps 단계별 학습](../../guided-learning/index.md)
* [파워 자동화 단계별 학습](https://docs.microsoft.com/flow/guided-learning/)
* [Power BI 단계별 학습](https://docs.microsoft.com/power-bi/guided-learning/)

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 시리즈 전체에서 사용하는 [SharePoint Online 목록을 설정합니다](sharepoint-scenario-setup.md).

