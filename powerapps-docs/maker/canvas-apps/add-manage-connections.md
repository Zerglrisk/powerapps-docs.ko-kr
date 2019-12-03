---
title: 캔버스 앱에서 연결 추가 및 관리 | Microsoft Docs
description: 캔버스 앱에서 SharePoint, SQL Server, 비즈니스용 OneDrive와 같은 데이터 원본에 대한 연결 추가, 삭제 및 업데이트
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/09/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5eb7bac0197856988f344ae2779bf2b43d1f797f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679986"
---
# <a name="manage-canvas-app-connections-in-powerapps"></a>PowerApps에서 캔버스 앱 연결 관리
[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 하나 이상의 데이터 원본으로의 연결을 만들거나, 연결을 삭제하거나, 또는 해당 자격 증명을 업데이트합니다.

캔버스 앱의 데이터 연결은 SharePoint, SQL Server, Office 365, 비즈니스용 OneDrive, Salesforce, Excel 및 기타 [데이터 원본](connections-list.md)에 연결할 수 있습니다.

이 문서 이후 단계는 다음 예와 같이 앱에서 데이터 원본의 데이터를 표시하고 관리하기 위한 것입니다.

* 비즈니스용 OneDrive에 연결하고 사용자 앱에서 Excel 통합 문서로 데이터를 관리합니다.
* SharePoint 사이트의 목록을 업데이트합니다.
* SQL Server에 연결하고 사용자 앱에서 테이블을 업데이트합니다.
* Office 365에서 이메일을 보냅니다.
* 트윗을 보냅니다.
* Twilio에 연결하고 사용자 앱에서 SMS 메시지를 보냅니다.

## <a name="prerequisites"></a>필수 조건
1. PowerApps에 [등록](../signup-for-powerapps.md)합니다.
2. 등록 시 사용한 동일한 자격 증명을 사용하여 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

## <a name="background-on-data-connections"></a>데이터 연결에 대한 배경
대부분의 Power Apps 앱은 cloud services에 저장 된 **데이터 원본** 이라는 외부 정보를 사용 합니다. 일반적인 예로 비즈니스용 OneDrive에 저장된 Excel 파일의 테이블이 있습니다. 앱에서 **연결**을 사용하여 이러한 데이터 원본에 액세스할 수 있습니다.

데이터 원본의 가장 흔한 유형은 정보 검색 및 저장에 사용할 수 있는 테이블입니다. 데이터 원본에 대한 연결을 사용하여 데이터를 비즈니스용 OneDrive, DropBox, SQL Server 등과 같은 클라우드 서비스에 저장할 수 있는 Microsoft Excel 통합 문서, SharePoint 목록, SQL 테이블 및 다른 많은 형식으로 읽고 쓸 수 있습니다.

전자 메일, 일정, twitter 및 알림과 같이 테이블이 아닌 다른 종류의 데이터 원본이 있습니다.

**[갤러리](controls/control-gallery.md)** , **[폼 표시](controls/control-form-detail.md)** 및 **[폼 편집](controls/control-form-detail.md)** 컨트롤을 사용하면 데이터 원본의 데이터를 읽고 쓸 수 있는 앱을 손쉽게 만들 수 있습니다. 시작하려면 [데이터 폼 이해](working-with-forms.md)를 읽어 보세요.

[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 연결을 만들고 관리하는 것 외에도 다음 작업을 수행할 때 연결을 만들 수 있습니다.

* 사용자 지정 SharePoint 목록과 같은 [데이터에서 앱](app-from-sharepoint.md)을 자동으로 생성합니다.
* 기존 앱을 업데이트하거나, [연결 추가](add-data-connection.md)에서 설명하는 대로 처음부터 다시 만듭니다.
* 다른 사용자가 생성하여 [사용자와 공유](share-app.md)한 앱을 엽니다.

> [!NOTE]
> 대신 Power Apps Studio를 사용 하려는 경우 **파일** 메뉴를 열고 **연결**을 클릭 하거나 탭 하면 연결을 만들고 관리할 수 있도록 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 이 열립니다.

## <a name="create-a-new-connection"></a>새 연결 만들기
1. 아직 수행하지 않은 경우 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
2. 왼쪽 탐색 표시줄에서 **연결**을 클릭하거나 탭합니다.
   
    ![연결 관리](./media/add-manage-connections/open-connections.png)
3. 오른쪽 위 모서리에서 **새 연결**을 클릭하거나 탭합니다.
   
    ![연결 추가](./media/add-manage-connections/add-connection.png)
4. 나타나는 목록에서 커넥터를 클릭하거나 탭한 다음, 표시되는 메시지에 따릅니다.
   
   ![연결 추가](./media/add-manage-connections/choose-connection.png)
5. **만들기** 단추를 클릭하거나 탭합니다.
   
   ![연결 추가](./media/add-manage-connections/create-connection.png)
6. 표시되는 메시지에 따릅니다. 일부 커넥터의 경우 자격 증명을 제공하고, 데이터의 특정 집합을 지정하거나 다른 단계를 수행하라는 메시지가 표시됩니다. **Microsoft Translator**와 같은 항목은 해당하지 않습니다.
   
   예를 들어, 다음과 같은 커넥터는 사용하기 전에 추가 정보가 필요합니다.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

**연결** 아래에 새 커넥터가 표시되면 [앱으로 연결 추가](add-data-connection.md)를 실행하면 됩니다.

## <a name="update-or-delete-a-connection"></a>연결 업데이트 또는 삭제
연결 목록에서 업데이트 또는 삭제할 연결을 찾은 다음, 연결의 오른쪽에 있는 줄임표(...)를 클릭하거나 탭합니다.

![연결 업데이트](./media/add-manage-connections/auth-or-delete.png)

* 연결에 대한 자격 증명을 업데이트하려면 키 아이콘을 클릭하거나 탭한 다음, 해당 연결에 대한 자격 증명을 제공합니다.
* 연결을 삭제하려면 휴지통 아이콘을 클릭하거나 탭합니다.
* 정보 아이콘을 클릭 하거나 탭 하 여 연결 정보를 확인 합니다.

