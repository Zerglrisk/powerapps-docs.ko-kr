---
title: SQL Server 연결 개요 | Microsoft Docs
description: Azure SQL 또는 온-프레미스 SQL Server 데이터베이스에 연결하는 방법에 대한 단계별 지침
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 08e54e48b371e71364edd2da09648af354a4d9ec
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723905"
---
# <a name="connect-to-sql-server-from-power-apps"></a>Power Apps에서 SQL Server에 연결
![SQL Server 아이콘](./media/connection-azure-sqldatabase/sqlicon.png)

Azure 또는 온-프레미스 데이터베이스에서 SQL Server에 연결 하 여 Power Apps에서 정보를 표시할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

* Power Apps에 [등록](../../signup-for-powerapps.md) 한 다음 등록 하는 데 사용한 것과 동일한 자격 증명을 제공 하 여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.
* 기본 키와 함께 최소 1개 이상의 테이블을 포함한 데이터베이스에 대한 다음 정보를 수집합니다.
  
  * 데이터베이스 이름
  * 데이터베이스가 호스팅된 서버의 이름
  * 데이터베이스에 연결할 유효한 사용자 이름과 암호
  * 데이터베이스에 연결하는 데 필요한 인증 유형
    
    이 정보가 없는 경우 사용하려는 데이터베이스의 관리자에게 문의하십시오.
* 온-프레미스 데이터베이스의 경우 사용자와 공유한 [데이터 게이트웨이](../gateway-management.md)를 식별하거나 하나 만듭니다.
  
    > [!NOTE]
  > 게이트웨이 및 온-프레미스 연결은 사용자의 [기본 환경](../working-with-environments.md)에서만 생성하고 사용할 수 있습니다.

## <a name="generate-an-app-automatically"></a>자동으로 앱 생성
1. Power Apps 스튜디오에서 **파일** 메뉴 (왼쪽 모서리를 따라)에서 **새로 만들기** 를 클릭 하거나 탭 합니다.
   
    ![파일 메뉴의 새 옵션](./media/connection-azure-sqldatabase/file-new.png)
2. **데이터를 통해 시작**에서 커넥터 행 끝에 있는 오른쪽 화살표를 클릭하거나 탭합니다.
3. 이미 사용하려는 데이터베이스에 연결되어 있는 경우에는 클릭하거나 탭한 다음, 이 절차의 7단계로 건너 뜁니다.
4. **새 연결**을 클릭하거나 탭하고 **SQL Server**를 클릭하거나 탭합니다.
   
    ![SQL Server 연결 추가](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. 다음의 단계 중 하나를 수행합니다.
   
   * **직접 연결(클라우스 서비스)** 을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙여 넣습니다.
     
       ![Azure에서 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-azure.png)
   * **온-프레미스 데이터 게이트웨이를 사용하여 연결**을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙어 넣고 인증 유형과 게이트웨이를 지정합니다.
     
       ![온-프레미스 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
     > 게이트웨이가 없는 경우 [하나 설치](../gateway-reference.md)하고 **게이트웨이 목록 새로 고침**을 클릭하거나 탭합니다.
6. **연결**을 클릭 하거나 탭합니다.
7. **데이터 세트 선택**에서 옵션을 클릭하거나 탭하고 **테이블 선택**에서 옵션을 클릭하거나 탭한 다음, **연결**을 클릭하거나 탭합니다.
   
    Power Apps는 세 개의 화면에 데이터를 표시 하는 앱을 만듭니다. 추론은 표시할 데이터의 종류를 제안하지만, 사용자의 요구 사항에 맞게 UI를 사용자 지정해야 합니다.
8. 먼저 앱 레이아웃 바꾸기부터 시작하여 [Excel에서 앱 만들기](../get-started-create-from-data.md)에서 설명한 것과 비슷한 기법을 사용하여 앱을 사용자 지정합니다.

## <a name="build-an-app-from-scratch"></a>앱을 처음부터 빌드
1. Power Apps에 등록 하는 데 사용한 것과 동일한 계정으로 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 에 로그인 합니다.
2. 왼쪽 탐색 모음에서 **연결**을 클릭하거나 탭합니다.  
   
    ![연결 관리](./media/connection-azure-sqldatabase/manage-connections.png)
3. 오른쪽 위 모서리에서 **새 연결**을 클릭하거나 탭하고 **SQL Server**를 클릭하거나 탭합니다.
4. 다음의 단계 중 하나를 수행합니다.
   
   * **직접 연결(클라우스 서비스)** 을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙여 넣습니다.
     
       ![Azure에서 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * **온-프레미스 데이터 게이트웨이를 사용하여 연결**을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙어 넣고 인증 유형과 게이트웨이를 지정합니다.
     
       ![Azure에서 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
     > 게이트웨이가 없는 경우 [하나 설치](../gateway-reference.md)하고 시계 방향 아이콘을 클릭하거나 탭하여 목록을 새로 고칩니다.
5. **만들기**를 클릭하거나 탭하여 연결을 만듭니다.
6. [처음부터 앱 만들기](../get-started-create-from-blank.md)에서 설명한 것과 비슷한 기법을 사용하여 앱을 만듭니다.

## <a name="update-an-existing-app"></a>기존 앱 업데이트
1. Power Apps 스튜디오에서 업데이트 하려는 앱을 엽니다.
2. 리본의 **보기** 탭에서 **데이터 원본**을 클릭하거나 탭합니다.
3. 오른쪽 창에서 **데이터 원본 추가**를 클릭하거나 탭합니다.
   
    ![데이터 원본 추가](./media/connection-azure-sqldatabase/add-data-source.png)
4. **새 연결**, **SQL Server**, **연결**을 차례로 클릭하거나 탭합니다.
5. 다음의 단계 중 하나를 수행합니다.
   
   * **직접 연결(클라우스 서비스)** 을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙여 넣습니다.
     
       ![Azure에서 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * **온-프레미스 데이터 게이트웨이를 사용하여 연결**을 지정하고 서버 이름, 데이터베이스 이름, 사용자 이름, 그리고 사용하려는 데이터베이스의 암호를 입력하거나 붙어 넣고 인증 유형과 게이트웨이를 지정합니다.
     
       ![Azure에서 데이터베이스에 연결](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
     > 게이트웨이가 없는 경우 [하나 설치](../gateway-reference.md)하고 원형 아이콘을 클릭하거나 탭하여 목록을 새로 고칩니다.
6. **연결**을 클릭 하거나 탭합니다.
7. **데이터 세트 선택**에서 옵션을 클릭하거나 탭합니다.
8. **표 선택**에서 하나 이상의 확인란을 선택한 다음 **연결**을 클릭하거나 탭합니다.

## <a name="next-steps"></a>다음 단계
* [데이터 원본에서 데이터 표시](../add-gallery.md) 방법 알아보기
* [세부 정보 보기 및 레코드 만들기 또는 업데이트](../add-form.md) 방법 알아보기
* 연결할 다른 [데이터 원본](../connections-list.md) 유형 참조  
* 테이블 형식의 데이터 원본과 함께 [테이블 및 레코드를 이해](../working-with-tables.md)합니다.

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
