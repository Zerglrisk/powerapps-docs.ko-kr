---
title: Excel 연결 개요 | Microsoft Docs
description: 클라우드 스토리지 계정으로 통합 문서를 저장한 다음 앱에서 데이터에 연결하여 Excel로 데이터를 표시하고 업데이트할 수 있습니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/02/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 455ffff4813b457c2a439f2081c10418ace2e306
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678721"
---
# <a name="connect-to-excel-from-powerapps"></a>PowerApps에서 Excel에 연결
![Excel](./media/connection-excel/excelicon.png)

Excel은 연결의 *한 종류*입니다. 앱에서 Excel 데이터를 표시하려면 다음을 수행합니다.

1. [Excel 데이터를 표로 서식 지정](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)합니다.
2. Box, Dropbox, Google Drive, OneDrive 및 비즈니스용 OneDrive와 같은 클라우드 스토리지 계정으로 Excel 파일을 저장합니다.
3. [클라우드 스토리지 계정에 연결](../add-manage-connections.md)한 다음, 데이터 원본으로 Excel 테이블을 추가합니다.
4. [앱을 자동으로 생성](../get-started-create-from-data.md)하거나 **갤러리** 컨트롤 등을 추가하고 구성하여 앱에 이 정보를 표시합니다.

> [!NOTE]
> Power Apps에서 Excel 테이블에 연결 하면 Excel 테이블의 각 행에 대 한 고유 ID를 사용 하 여 **\_PowerAppsId_** 라는 열이 생성 됩니다.

[클라우드 스토리지 연결 개요](cloud-storage-blob-connections.md)는 연결을 추가하고 Excel 표를 데이터 원본으로 저장하며 앱에서 Excel 데이터를 사용하는 방법을 보여줍니다.

다른 종류의 데이터에 연결하는 방법에 대한 자세한 내용은 [PowerApps 연결 목록](../connections-list.md)을 참조하십시오.

### <a name="known-limitations"></a>알려진 제한 사항
조직 내에서 Excel 데이터를 공유하는 방법에 대한 자세한 내용은 [이러한 제한 사항을 검토](cloud-storage-blob-connections.md#sharing-excel-tables)하세요.

