---
title: 사용자 지정 엔터티 삭제 | Microsoft Docs
description: PowerApps에서 사용자 지정 엔터티를 삭제하고 모든 데이터를 지우는 방법에 대한 단계별 지침
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b4b9fb7942a7977bf6795ca21985b93c5469d26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754922"
---
# <a name="delete-a-custom-entity"></a>사용자 지정 엔터티 삭제
사용자 지정 엔터티를 삭제할 수 있지만 표준 엔터티를 삭제할 수는 없습니다.

1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭합니다.

    ![엔터티 세부 정보](./media/data-platform-cds-create-entity/entitylist.png "엔터티 목록")

2. 엔터티 목록에서 삭제할 엔터티를 클릭하거나 탭한 다음 명령 모음에서 **엔터티 삭제** 옵션을 클릭하거나 탭합니다.

3. 표시되는 대화 상자에서 **삭제**를 클릭하거나 탭하여 엔터티를 삭제합니다.

>[!NOTE]
>엔터티를 삭제하면 엔터티 정의와 엔터티에 포함된 모든 데이터가 모두 삭제됩니다. 삭제된 엔터티 및 그 안에 있는 데이터는 복구할 수 없습니다.

>[!NOTE]
>해당 앱에서 사용되는 엔터티를 삭제하면 앱 또는 흐름이 중단될 수 있습니다.

>[!NOTE]
>엔터티 A에 엔터티 B에 대한 [조회 필드](data-platform-entity-lookup.md)가 있으면 엔터티 A를 삭제하기 전에 엔터티 B를 삭제해야 할 수 있습니다.

