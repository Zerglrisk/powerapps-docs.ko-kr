---
title: 포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가 | MicrosoftDocs
description: 포털에서 웹 페이지에 Power BI 보고서 또는 대시보드를 추가하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 722789d726d02b306eb794aa51665c13ce7f495d
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874701"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가

[powerbi](../liquid/portals-entity-tags.md#powerbi) 유동 태그를 사용하여 포털의 웹 페이지에 Power BI 보고서 또는 대시보드를 추가할 수 있습니다. 웹 페이지의 **복사** 필드 또는 웹 템플릿의 **원본** 필드에 태그를 추가할 수 있습니다. Power BI의 새 작업 영역에서 만든 Power BI 보고서 또는 대시보드를 추가하는 경우에는 powerbi 유동 태그에 **powerbiembedded**로 인증 유형을 지정해야 합니다.

예:  

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Powerbi 유동 태그의 인증 유형으로 AAD를 지정한 경우 포털의 웹 페이지에 보안 Power BI 보고서 또는 대시보드를 추가하기 전에 필수 사용자와 공유해야 합니다. 추가 정보: [Power BI 작업 영역 공유](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) 및 [Power BI 대시보드 및 보고서 공유](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>대시보드 또는 보고서의 경로 가져오기

1.  [Power BI](https://powerbi.microsoft.com/)에 로그인합니다.

2.  포털에 포함하려는 대시보드 또는 보고서를 엽니다.

3.  주소 표시줄에서 URL을 복사합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 대시보드의 경로 가져오기](../media/powerbi-dashboard-url.png "Power BI 대시보드의 경로 가져오기")

## <a name="get-the-id-of-a-dashboard-tile"></a>대시보드 타일의 ID 가져오기

1.  [Power BI](https://powerbi.microsoft.com/)에 로그인합니다.

2.  포털에 타일을 포함하려는 대시보드를 엽니다.

3.  타일을 가리키고 **추가 옵션**을 선택한 다음 **포커스 모드에서 열기**를 선택합니다.

    > [!div class=mx-imgBorder]
    > ![포커스 모드의 Power BI 대시보드 타일 열기](../media/powerbi-dashboard-tile-focus.png "포커스 모드의 Power BI 대시보드 타일 열기")

4.  주소 표시줄의 URL에서 타일 ID를 복사합니다. 타일 ID는 /tiles/ 다음에 있는 값입니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 대시보드 타일 ID](../media/powerbi-dashboard-tile-id.png "Power BI 대시보드 타일 ID")


### <a name="see-also"></a>참조


[powerbi 유동 태그](../liquid/portals-entity-tags.md#powerbi)<br> 
[Power BI 통합 설정](set-up-power-bi-integration.md)
