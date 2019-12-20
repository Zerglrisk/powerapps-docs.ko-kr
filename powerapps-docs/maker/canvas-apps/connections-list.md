---
title: 캔버스 앱용 커넥터 개요 | Microsoft Docs
description: 캔버스 앱 빌드에 사용할 수 있는 모든 연결 개요
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/10/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d78ce9b571ed925e68747f2307d59f5f143e13eb
ms.sourcegitcommit: 366f0d1b8309ab1fd533ebd7e1b41a69a99fd25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302900"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>Power Apps 용 캔버스-앱 커넥터 개요
데이터는 Power Apps에서 작성 하는 앱을 포함 하 여 대부분의 앱에서 핵심입니다. 데이터는 *데이터 원본*에 저장되며 *연결*을 만들어 해당 데이터를 앱으로 구현합니다. 이 연결은 특정 *커넥터*를 사용하여 데이터 원본과 데이터를 교환합니다. 파워 앱은 인기 있는 많은 서비스 및 온-프레미스 데이터 원본에 대 한 커넥터 (SharePoint, SQL Server, Office 365, Salesforce, Twitter 등)를 포함 합니다. 캔버스 앱에 데이터를 추가 하는 작업을 시작 하려면 [Power Apps에서 데이터 연결 추가](add-data-connection.md)를 참조 하세요.

커넥터는 **테이블** 데이터 또는 **작업**을 제공할 수 있습니다. 일부 커넥터는 테이블만 제공하고 일부 커넥터는 동작만 제공하며 일부 커넥터는 두 가지 모두를 제공합니다. 또한 커넥터는 표준 또는 사용자 지정 커넥터일 수 있습니다.

## <a name="tables"></a>테이블

커넥터가 테이블을 제공하는 경우 데이터 원본을 추가한 다음, 관리하려는 데이터 원본에서 테이블을 선택합니다. Power Apps는 모두 앱에서 테이블 데이터를 검색 하 고 데이터 원본의 데이터를 업데이트 합니다. 예를 들어 **단원**이라는 테이블이 포함된 데이터 원본을 추가한 다음, 캘러리 또는 양식과 같은 컨트롤의 **항목** 속성을 수식 표시줄의 이 값으로 설정할 수 있습니다.

 ![일반 데이터 원본 항목 속성](./media/connections-list/ItemPropertyPlain.png)

데이터를 표시 하는 컨트롤의 **Items** 속성을 사용자 지정 하 여 앱이 검색 하는 데이터를 지정할 수 있습니다. 앞의 예제를 계속하면 **검색** 및 **SortByColumn** 함수의 인수로 해당 이름을 사용하여 **단원** 테이블의 데이터를 정렬하거나 필터링할 수 있습니다. 이 그래픽에서 **항목** 속성을 설정하는 서식은 **TextSearchBox1**의 텍스트를 기준으로 데이터가 정렬되고 필터링되도록 지정합니다. 

 ![확장된 데이터 원본 항목 속성](./media/connections-list/ItemPropertyExpanded.png)

테이블을 사용 하 여 수식을 사용자 지정 하는 방법에 대 한 자세한 내용은 다음 항목을 참조 하세요.

  [Power Apps의 데이터 원본 이해](working-with-data-sources.md)<br> 
  [Excel 데이터에서 앱 생성](get-started-create-from-data.md)<br> 
  [앱을 처음부터 만들기](get-started-create-from-blank.md)<br>
  [Power Apps의 테이블 및 레코드 이해](working-with-tables.md)

  > [!NOTE]
  > Excel 통합 문서의 데이터에 연결하려면 OneDrive와 같은 클라우드 스토리지 서비스에서 호스팅되어야 합니다. 자세한 내용은 [Power Apps에서 클라우드 저장소에 연결](connections/cloud-storage-blob-connections.md)을 참조 하세요.

## <a name="actions"></a>동작

커넥터가 작업을 제공하는 경우 이전과 마찬가지로 데이터 원본을 계속 선택해야 합니다. 그러나 다음 단계로 테이블을 선택하는 대신 데이터를 표시할 컨트롤의 **항목** 속성을 편집하여 수동으로 컨트롤을 작업에 연결합니다. **항목** 속성을 설정하는 수식은 데이터를 검색하는 작업을 지정합니다. 예를 들어 Yammer에 연결한 다음, **항목** 속성을 데이터 원본 이름으로 설정하면 앱에서 데이터를 검색하지 않습니다. 데이터로 컨트롤을 채우려면 **GetMessagesInGroup (5033622).messages**와 같은 작업을 지정합니다.

![작업 데이터 원본 항목 속성](./media/connections-list/ItemPropertyAction.png)

작업 커넥터에 대한 사용자 지정 데이터 업데이트를 처리해야 하는 경우 **패치** 함수를 포함하는 수식을 빌드합니다. 수식에서 작업에 바인딩할 작업 및 필드를 식별합니다.  

사용자 지정 업데이트에 대 한 수식을 사용자 지정 하는 방법에 대 한 자세한 내용은 다음 항목을 참조 하세요.

[패치](functions/function-patch.md)<br>[수집](functions/function-clear-collect-clearcollect.md)<br>[업데이트](functions/function-update-updateif.md)

> [!NOTE]
>  **Power Apps는 동적 스키마를 사용 하지 않습니다**. 구 동적 스키마는 동일한 작업에서 열이 다른 테이블을 반환할 수 있는 가능성을 나타냅니다. 테이블의 열에는 동작 입력 매개 변수, 작업을 실행 하는 사용자나 역할 및 사용자가 작업 하 고 있는 그룹이 포함 될 수 있는 조건이 있습니다. 예를 들어 다른 입력을 사용 하 여 실행 하는 경우 저장 프로시저 SQL Server 다른 열을 반환할 수 있습니다. 동적 스키마를 사용 하는 작업의 경우 커넥터 설명서에서 **이 작업의 출력을 동적** 으로 보여 줍니다. 반환 값으로 반환 됩니다. 반면, 파워 자동화는 동적 스키마를 사용 하 여 작동 하며 시나리오에 대 한 해결 방법을 제공할 수 있습니다.

## <a name="popular-connectors"></a>가장 많이 사용되는 커넥터

이 표에는 가장 많이 사용되는 커넥터에 대한 자세한 정보의 링크가 있습니다. 커넥터의 전체 목록은 [모든 커넥터](https://docs.microsoft.com/connectors/)를 참조하세요.

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![클라우드 저장소](./media/connections-list/onedrive.png) |[**클라우드 저장소**](connections/cloud-storage-blob-connections.md) ** |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Office 365 사용자](./media/connections-list/office365.png) |[**Office 365 사용자**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**Oracle**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

* * Azure Blob, Box, Dropbox, Google Drive, OneDrive 및 비즈니스용 OneDrive에 적용 됩니다.

## <a name="standard-and-custom-connectors"></a>표준 및 사용자 지정 커넥터
Power Apps는 위에 나열 된 것과 같이 일반적으로 사용 되는 다양 한 데이터 원본에 대 한 *표준* 커넥터를 제공 합니다. Power Apps에 사용 하려는 데이터 원본 유형에 대 한 표준 커넥터가 있는 경우 해당 커넥터를 사용 해야 합니다. 빌드한 서비스와 같은 다른 유형의 데이터 원본에 연결하려면 [사용자 지정 커넥터 등록 및 사용](../canvas-apps/register-custom-api.md)을 참조합니다.

## <a name="all-standard-connectors"></a>모든 표준 커넥터
모든 표준 커넥터 목록은 [Microsoft Connector Reference](https://docs.microsoft.com/connectors/)를 참조하세요. 프리미엄 커넥터를 사용 하려면 앱 계획 당 Power Apps 또는 사용자 요금제 당 Power Apps가 필요 합니다. 자세한 내용은 [Power Apps 요금제](https://powerapps.microsoft.com/pricing/)를 참조 하세요.

[Power apps 포럼](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)에서 특정 커넥터에 대 한 질문을 할 수 있으며, [power apps 아이디어](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)에서 수행할 수 있는 다른 향상 된 기능을 추가할 수 있습니다.

## <a name="security-and-types-of-authentication"></a>보안 및 인증 유형

앱을 작성 하 고 데이터 원본에 대 한 연결을 만들 때 커넥터를 선택 하면 다른 방법으로 인증을 사용할 수 있습니다. 예를 들어 SQL Server 커넥터를 사용 하면 Azure AD 통합 SQL Server 인증 및 Windows 인증을 사용할 수 있습니다. 각 인증 유형에는 서로 다른 보안 수준이 연결 되어 있습니다.  응용 프로그램을 사용 하는 사용자와 공유 하는 정보 및 권한을 이해 하는 것이 중요 합니다. 이 문서의 기본 예는 SQL Server 이지만 모든 유형의 연결에는 원칙이 적용 됩니다.

### <a name="azure-ad-integrated"></a>Azure AD 통합

이는 안전한 연결 유형입니다.  예를 들어 SharePoint는 이러한 유형의 인증을 사용 합니다.  또한이 인증 유형을 허용 하는 SQL Server.  연결할 때 Azure AD 서비스는 사용자를 대신 하 여 SharePoint에 대해 개별적으로 사용자를 식별 합니다.  사용자 이름 또는 암호를 제공할 필요는 없습니다.  작성자는 자격 증명을 사용 하 여 데이터 원본을 만들고 사용할 수 있습니다.  응용 프로그램 및 응용 프로그램 사용자 로그를에 게시 하는 경우 자격 증명을 사용 하 여 수행 합니다. 백 엔드에서 데이터를 적절 하 게 보호 하는 경우 사용자는 자격 증명에 따라 볼 수 있는 권한이 있는 사용자만 볼 수 있습니다.   이 보안 유형을 사용 하면 응용 프로그램을 게시 한 후 백 엔드 데이터 원본에서 특정 응용 프로그램 사용자에 대 한 권한을 변경할 수 있습니다.  예를 들어, 액세스 권한을 부여 하거나, 액세스를 거부 하거나, 사용자 또는 사용자 집합이 백 엔드 데이터 원본에서 모두 볼 수 있는 작업을 구체화할 수 있습니다.

### <a name="open-standard-authorization-oauth"></a>오픈 표준 권한 부여 (OAuth)

이 유형의 연결도 안전 합니다.  예를 들어 Twitter는 이러한 형식의 인증을 사용 합니다.  연결할 때 사용자 이름과 암호를 제공 해야 합니다.  작성자는 자격 증명을 사용 하 여 데이터 원본을 만들고 사용할 수 있습니다.  응용 프로그램 및 응용 프로그램 사용자 로그를에 게시 하는 경우에도 자격 증명을 제공 해야 합니다.  따라서 사용자가 자신의 자격 증명을 사용 하 여 데이터 원본 서비스에 액세스 해야 하므로이 유형의 연결은 안전 합니다. 

### <a name="sql-user-name-and-password-authentication"></a>SQL 사용자 이름 및 암호 인증

이 연결 유형은 최종 사용자 인증을 사용 하지 않으므로 안전 하지 않습니다.  또한이 인증 유형을 허용 하는 SQL Server.  SQL Server이 인증 유형을 **SQL Server 인증**이라고 합니다.  다른 많은 데이터베이스 데이터 원본은 비슷한 기능을 제공 합니다.  응용 프로그램을 게시 하면 사용자가 고유한 사용자 이름 및 암호를 제공할 필요가 없습니다.  응용 프로그램을 제작할 때 제공 하는 사용자 이름 및 암호를 사용 합니다.  데이터 원본에 대 한 연결 인증은 사용자와 **암시적으로 공유** 됩니다.  응용 프로그램이 게시 되 면 사용자가 연결도 게시 되 고 사용할 수 있습니다.  또한 최종 사용자는 공유 된 SQL Server 인증을 사용 하 여 모든 연결을 사용 하 여 응용 프로그램을 만들 수 있습니다.  사용자는 암호의 사용자 이름을 볼 수 없지만 해당 사용자에 게는 연결을 사용할 수 있습니다.  이러한 유형의 연결에는 분명히 유효한 시나리오가 있습니다.  예를 들어 회사의 모든 사용자가 사용할 수 있는 읽기 전용 데이터베이스가 있는 경우이 유형의 연결을 사용할 수 있습니다. 

### <a name="windows-authentication"></a>Windows 인증

이 연결 유형은 최종 사용자 인증에 의존 하지 않기 때문에 안전 하지 않습니다.  **온-프레미스에**있는 데이터 원본에 연결 해야 하는 경우 Windows 인증을 사용 합니다.  이러한 연결 형식의 예는 SQL Server 있는 온-프레미스 서버에 대 한 것입니다.  연결은 게이트웨이를 통해 이동 해야 합니다.  커넥터는 게이트웨이를 거치 므로 해당 데이터 원본의 모든 데이터에 액세스할 수 있습니다. 따라서 사용자가 제공 하는 Windows 자격 증명을 사용 하 여 액세스할 수 있는 모든 정보는 커넥터에서 사용할 수 있습니다. 응용 프로그램을 게시 한 후에도 사용자가 연결을 게시 하 고 사용할 수 있습니다.   즉, 최종 사용자는이 동일한 연결을 사용 하 여 응용 프로그램을 만들고 해당 컴퓨터의 데이터에 액세스할 수도 있습니다.  또한 데이터 원본에 대 한 연결은 앱이 공유 되는 사용자와 **암시적으로 공유** 됩니다.  이 유형의 연결은 데이터 원본이 온-프레미스 서버에만 있고 해당 원본의 데이터를 자유롭게 공유할 수 있는 경우에만 유효 합니다.
