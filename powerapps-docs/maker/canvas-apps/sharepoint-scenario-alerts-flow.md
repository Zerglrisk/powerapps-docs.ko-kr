---
title: Power BI 대시보드에 대한 데이터 경고 설정 | Microsoft Docs
description: 이 작업에서는 보류 중인 프로젝트를 승인하는 데 너무 오래 걸리는지를 알리는 Power BI의 경고 및 해당 경고가 발생할 때 응답하는 흐름을 추가합니다.
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
ms.openlocfilehash: 37ea7a123562cf4ec9216d484bd6173f33046d72
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674798"
---
# <a name="set-up-data-alerts-for-the-power-bi-dashboard"></a>Power BI 대시보드에 대한 데이터 경고 설정
> [!NOTE]
> 이 문서는 SharePoint Online에서 Power Apps, 파워 자동화 및 Power BI 사용에 대 한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악하도록 합니다.

이 작업에서는 보류 중인 프로젝트를 승인하는 데 너무 오래 걸리는지를 알리는 Power BI의 경고 및 해당 경고가 발생할 때 응답하는 흐름을 추가합니다. 경고에 대한 자세한 내용은 [Power BI 서비스의 데이터 경고](https://docs.microsoft.com/power-bi/service-set-data-alerts)를 참조하세요.

## <a name="step-1-create-an-alert"></a>1단계: 경고 만들기
1. Power BI 서비스에서는 최근 작업에서 만든 대시보드를 엽니다.
2. 단일 숫자를 포함하는 카드에서 줄임표( **...** )를 클릭하거나 누릅니다.
   
    ![최대 승인 보류 일 수 카드](./media/sharepoint-scenario-alerts-flow/07-01-01-tile-ellipsis.png)
3. 연필 편집 아이콘을 ![클릭하거나 누릅니다.](./media/sharepoint-scenario-alerts-flow/icon-bell.png)줄임표(...)를 클릭한 다음
   
    ![타일 메뉴](./media/sharepoint-scenario-alerts-flow/07-01-02-tile-bell.png)
4. 오른쪽 창에서 **경고 규칙 추가**를 클릭하거나 누릅니다.
   
    ![경고 규칙 추가](./media/sharepoint-scenario-alerts-flow/07-01-03-add-alert.png)
5. 경고를 실행하는 빈도와 같이 경고에 사용할 수 있는 옵션을 확인합니다. **임계값**에 25 값을 입력한 다음 **저장 후 닫기**를 클릭하거나 누릅니다.
   
    ![경고 임계값 설정 및 저장](./media/sharepoint-scenario-alerts-flow/07-01-04-save-alert.png)

56이 25라는 임계값을 초과하더라도 경고가 지금 바로 발생하지 않습니다. 데이터가 업데이트될 때 발생합니다. 이것은 [시나리오를 끝까지 실행](sharepoint-scenario-summary.md)할 때 표시됩니다.

경고가 발생 하면 Power BI는 경고 작성자에 게 전자 메일을 보내고, 다음 단계에서 전원 자동화를 사용 하 여 추가 메일을 전송 하는 방법을 알아봅니다.

## <a name="step-2-create-a-flow-that-responds-to-the-alert"></a>2단계: 경고에 응답하는 흐름 만들기
1. flow.microsoft.com에 로그인하고, **서비스** 및 **Power BI**를 클릭하거나 누릅니다.
   
    ![전원 자동화의 Power BI](./media/sharepoint-scenario-alerts-flow/07-01-05-power-bi.png)
2. **Power BI 데이터 경고가 트리거될 때 모든 대상에게 전자 메일 보내기**를 클릭하거나 누릅니다.
   
    ![Power BI 데이터 경고가 트리거될 때 전자 메일 보내기](./media/sharepoint-scenario-alerts-flow/07-01-06-alert-flow.png)
3. **이 템플릿 사용**을 클릭하거나 누릅니다.
4. 아직 로그인하지 않은 경우 Outlook 및 Power BI에 로그인한 다음 **계속**을 클릭하거나 누릅니다.
   
    ![로그인 및 계속](./media/sharepoint-scenario-alerts-flow/07-01-08-continue.png)
5. **경고 ID** 드롭 다운 목록에서 **최대 승인 보류 일 수에 대한 경고**를 선택합니다.
   
    ![경고를 트리거로 지정](./media/sharepoint-scenario-alerts-flow/07-01-09-choose-alert.png)
6. **받는 사람**에서 유효한 전자 메일 주소를 입력합니다.
   
    ![전자 메일을 보내는 사람 지정](./media/sharepoint-scenario-alerts-flow/07-01-10-choose-email.png)
7. **편집**을 클릭하거나 눌러서 업데이트할 수 있는 다른 필드를 확인합니다.
   
    ![경고 전자 메일 편집](./media/sharepoint-scenario-alerts-flow/07-01-11-email-full.png)
8. 화면의 오른쪽 위에서 **흐름 만들기** 및 **완료**를 클릭합니다.
   
    ![완료 단추](./media/sharepoint-scenario-alerts-flow/07-01-12-done.png)

[시나리오를 끝까지 실행](sharepoint-scenario-summary.md)할 때 이 흐름 실행을 확인합니다. 이제 Power BI 보고서를 SharePoint에 포함 시나리오에서 최근 작업으로 이동합니다.

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [SharePoint Online에서 Power BI 프로젝트 보고서를 포함합니다](sharepoint-scenario-embed-report.md).

