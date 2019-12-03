---
title: 캔버스 앱에서 데이터 연결 추가 | Microsoft Docs
description: 기존 캔버스 앱 또는 빈 앱에 데이터 연결 추가
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d81b1648fc3c45d0498efb9eba0cc14ffbc6142b
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679273"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-powerapps"></a>PowerApps의 캔버스 앱에 데이터 연결 추가

Power Apps에서 처음부터 작성 하는 기존 캔버스 앱 또는 앱에 데이터 연결을 추가 합니다. 앱은 SharePoint, Common Data Service, Salesforce, OneDrive 또는 [다른 많은 데이터 원본](connections-list.md)에 연결할 수 있습니다.

이 문서 이후 [다음 단계](#next-steps)는 다음 예와 같이 앱에서 데이터 원본의 데이터를 표시하고 관리하기 위한 것입니다.

* OneDrive에 연결하고 사용자 앱에서 Excel 통합 문서의 데이터를 관리합니다.
* Twilio에 연결하고 사용자 앱에서 SMS 메시지를 보냅니다.
* Common Data Service에 연결 하 고 앱에서 엔터티를 업데이트 합니다.
* SQL Server에 연결하고 사용자 앱에서 테이블을 업데이트합니다.

## <a name="prerequisites"></a>필수 조건

Power Apps에 [등록](../signup-for-powerapps.md) 한 다음 등록 하는 데 사용한 것과 동일한 자격 증명을 제공 하 여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 합니다.

## <a name="open-a-blank-app"></a>비어 있는 앱 열기

1. **홈** 탭의 **빈 페이지에서 캔버스 앱**을 선택 합니다.

1. 앱의 이름을 지정 하 고 **만들기**를 선택 합니다.

1. **Power Apps 스튜디오 시작** 대화 상자가 나타나면 **건너뛰기**를 선택 합니다.

## <a name="add-data-source"></a>데이터 원본 추가

1. 가운데 창에서 **데이터에 연결** 을 선택 하 여 **데이터** 창을 엽니다.

    기존 앱이 고 화면에 이미 컨트롤이 포함 되어 있는 경우 **데이터 원본** **보기** > 선택 하 여 동일한 창을 엽니다.

1. **데이터 원본 추가**를 선택 합니다.

1. 연결 목록에 원하는 항목이 포함 되어 있으면 해당 연결을 선택 하 여 앱에 추가 합니다. 그렇지 않은 경우 다음 단계를 건너뜁니다.

    ![기존 연결 선택](./media/add-data-connection/choose-existing-connection.png)

1. **새 연결** 을 선택 하 여 연결 목록을 표시 합니다.

    ![연결 추가](./media/add-data-connection/add-connection.png)

1. 검색 창에서 원하는 연결의 처음 몇 글자를 입력 하거나 붙여 넣은 다음 표시 되 면 연결을 선택 합니다.

    ![연결 검색](./media/add-data-connection/search-connections.png)

1. **만들기**를 선택하여 연결을 만들고 앱에 추가합니다.

    **Office 365 Outlook**과 같은 일부 커넥터는 추가 단계가 필요하지 않으며 즉시 데이터를 표시할 수 있습니다. 다른 커넥터의 경우 자격 증명을 제공하고, 데이터의 특정 집합을 지정하거나 다른 단계를 수행하라는 메시지가 표시됩니다. 예를 들어 [SharePoint](connections/connection-sharepoint-online.md) 및 [SQL Server](connections/connection-azure-sqldatabase.md)는 사용하기 전에 추가 정보가 필요합니다. [Common Data Service](connections/connection-common-data-service.md)를 사용 하 여 엔터티를 선택 하기 전에 환경을 변경할 수 있습니다.

## <a name="identify-or-change-a-data-source"></a>데이터 원본 식별 또는 변경
앱을 업데이트하는 경우 갤러리, 양식 또는 다른 컨트롤에 표시되는 데이터의 원본을 식별하거나 변경해야 할 수 있습니다. 예를 들어 다른 사용자가 만들었거나 이전에 만든 앱을 업데이트할 때 데이터 원본을 식별 해야 할 수 있습니다.

1. 갤러리와 같은 컨트롤을 선택 하 여 데이터 원본을 확인 하거나 변경 합니다.

    데이터 원본의 이름이 오른쪽 창의 **속성** 탭에 나타납니다.

    ![연결 식별](./media/add-data-connection/identify-connection.png)

1. 데이터 원본에 대 한 자세한 정보를 표시 하거나 변경 하려면 해당 이름 옆에 있는 아래쪽 화살표를 선택 합니다.

    현재 데이터 원본에 대 한 자세한 정보가 표시 되며, 다른 원본을 선택 하거나 만들 수 있습니다.

    ![연결 변경](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>다음 단계

* Excel, SharePoint, Common Data Service 또는 SQL Server와 같은 원본의 데이터를 표시 하 고 업데이트 하려면 갤러리를 [추가](add-gallery.md)하 고 [양식을 추가](add-form.md)합니다.
* 다른 원본에 있는 데이터의 경우, [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) 및 [Microsoft Translator](connections/connection-microsoft-translator.md)에 대한 데이터와 같이 커넥터 특정 기능을 사용합니다.
