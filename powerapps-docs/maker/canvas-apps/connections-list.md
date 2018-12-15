---
title: 캔버스 앱용 커넥터 개요 | Microsoft Docs
description: 캔버스 앱 빌드에 사용할 수 있는 모든 연결 개요
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f7a053aff947ffd543381956cf725a7e656d8a65
ms.sourcegitcommit: ebe0a9c41b693a2134e9198ffc7e7a8eabee4330
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "51276375"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>PowerApps용 캔버스 앱 커넥터의 개요
데이터는 PowerApps에서 빌드하는 앱을 포함해 대부분 앱의 핵심입니다. 데이터는 *데이터 원본*에 저장되며 *연결*을 만들어 해당 데이터를 앱으로 구현합니다. 이 연결은 특정 *커넥터*를 사용하여 데이터 원본과 데이터를 교환합니다. PowerApps에는 SharePoint, SQL Server, Office 365, Salesforce, Twitter를 비롯한 많은 인기 서비스 및 온-프레미스 데이터 원본용 커넥터가 있습니다. 캔버스 앱에 데이터 추가를 시작하려면 [PowerApps에서 데이터 연결 추가](add-data-connection.md)를 참조하세요.

커넥터는 **테이블** 데이터 또는 **작업**을 제공할 수 있습니다. 일부 커넥터는 테이블만 제공하고 일부 커넥터는 동작만 제공하며 일부 커넥터는 두 가지 모두를 제공합니다. 또한 커넥터는 표준 또는 사용자 지정 커넥터일 수 있습니다.

## <a name="tables"></a>테이블

커넥터가 테이블을 제공하는 경우 데이터 원본을 추가한 다음, 관리하려는 데이터 원본에서 테이블을 선택합니다. PowerApps는 테이블 데이터를 앱으로 검색하고 데이터 원본의 데이터를 업데이트합니다. 예를 들어 **단원**이라는 테이블이 포함된 데이터 원본을 추가한 다음, 캘러리 또는 양식과 같은 컨트롤의 **항목** 속성을 수식 표시줄의 이 값으로 설정할 수 있습니다.

 ![일반 데이터 원본 항목 속성](./media/connections-list/ItemPropertyPlain.png)

데이터를 표시하는 컨트롤의 **항목** 속성을 사용자 지정하여 앱에서 검색하는 데이터를 지정할 수 있습니다. 앞의 예제를 계속하면 **검색** 및 **SortByColumn** 함수의 인수로 해당 이름을 사용하여 **단원** 테이블의 데이터를 정렬하거나 필터링할 수 있습니다. 이 그래픽에서 **항목** 속성을 설정하는 서식은 **TextSearchBox1**의 텍스트를 기준으로 데이터가 정렬되고 필터링되도록 지정합니다. 

 ![확장된 데이터 원본 항목 속성](./media/connections-list/ItemPropertyExpanded.png)

테이블을 사용하여 수식을 사용자 지정하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

  [PowerApps 데이터 원본에 대한 이해](working-with-data-sources.md)<br> 
  [Excel 데이터에서 앱 생성](get-started-create-from-data.md)<br> 
  [앱을 처음부터 만들기](get-started-create-from-blank.md)<br>
  [PowerApps 테이블 및 레코드에 대한 이해](working-with-tables.md)

  > [!NOTE]
  > Excel 통합 문서의 데이터에 연결하려면 OneDrive와 같은 클라우드 저장소 서비스에서 호스팅되어야 합니다. 자세한 내용은 [PowerApps에서 클라우드 저장소에 연결](connections/cloud-storage-blob-connections.md)을 참조하세요.

## <a name="actions"></a>작업

커넥터가 작업을 제공하는 경우 이전과 마찬가지로 데이터 원본을 계속 선택해야 합니다. 그러나 다음 단계로 테이블을 선택하는 대신 데이터를 표시할 컨트롤의 **항목** 속성을 편집하여 수동으로 컨트롤을 작업에 연결합니다. **항목** 속성을 설정하는 수식은 데이터를 검색하는 작업을 지정합니다. 예를 들어 Yammer에 연결한 다음, **항목** 속성을 데이터 원본 이름으로 설정하면 앱에서 데이터를 검색하지 않습니다. 데이터로 컨트롤을 채우려면 **GetMessagesInGroup (5033622).messages**와 같은 작업을 지정합니다.

![작업 데이터 원본 항목 속성](./media/connections-list/ItemPropertyAction.png)

작업 커넥터에 대한 사용자 지정 데이터 업데이트를 처리해야 하는 경우 **패치** 함수를 포함하는 수식을 빌드합니다. 수식에서 작업에 바인딩할 작업 및 필드를 식별합니다.  

사용자 지정 업데이트를 위해 수식을 사용자 지정하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

[패치](functions/function-patch.md)<br>[수집](functions/function-clear-collect-clearcollect.md)<br>[업데이트](functions/function-update-updateif.md)

## <a name="popular-connectors"></a>가장 많이 사용되는 커넥터

이 표에는 가장 많이 사용되는 커넥터에 대한 자세한 정보의 링크가 있습니다. 커넥터의 전체 목록은 [모든 커넥터](#all-standard-connectors)를 참조하세요.

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![일반 데이터 서비스](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![비즈니스용 OneDrive](./media/connections-list/onedrive.png) |[**비즈니스용 OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365 사용자](./media/connections-list/office365.png) |[**Office 365 사용자**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>표준 및 사용자 지정 커넥터
PowerApps는 위에 나열된 것과 같이 일반적으로 사용되는 많은 데이터 원본에 대해 *표준* 커넥터를 제공합니다. PowerApps에 사용하려는 데이터 원본 유형에 대한 표준 커넥터가 있는 경우 해당 커넥터를 사용해야 합니다. 빌드한 서비스와 같은 다른 유형의 데이터 원본에 연결하려면 [사용자 지정 커넥터 등록 및 사용](../canvas-apps/register-custom-api.md)을 참조합니다.

## <a name="all-standard-connectors"></a>모든 표준 커넥터
모든 표준 커넥터 목록은 [Microsoft Connector Reference](https://docs.microsoft.com/connectors/)를 참조하세요. 프리미엄 커넥터는 PowerApps 요금제 1 또는 요금제 2가 필요합니다. 자세한 내용은 [PowerApps 가요금제](https://powerapps.microsoft.com/pricing/)를 참조하세요.

[PowerApps 포럼](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)에서 특정 커넥터에 대한 질문을 할 수 있으며 [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)에서 추가할 커넥터나 기타 개선 사항을 제안할 수 있습니다.
