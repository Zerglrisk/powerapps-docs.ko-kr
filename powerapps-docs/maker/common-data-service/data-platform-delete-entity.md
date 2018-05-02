---
title: 사용자 지정 엔터티 삭제 및 데이터 지우기에 대한 빠른 시작 | Microsoft Docs
description: 사용자 지정 엔터티 삭제 및 모든 데이터 지우기에 대한 빠른 시작
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 971016233578c4eadf397d662a0ea74187548635
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-delete-a-custom-entity"></a>빠른 시작: 사용자 지정 엔터티 삭제
사용자 지정 엔터티를 삭제할 수 있으나, 표준 엔터티는 삭제할 수 없습니다.

1. [powerapps.com](https://web.powerapps.com)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭합니다.

    ![엔터티 세부 정보](./media/data-platform-cds-create-entity/entitylist.png "엔터티 목록")

2. 엔터티 목록에서 삭제할 엔터티를 클릭하거나 탭한 다음, 명령 모음에서 **엔터티 삭제** 옵션을 클릭하거나 탭합니다.
3. 나타나는 대화 상자에서 **삭제**를 클릭하거나 탭하여 엔터티를 삭제합니다.

>[!NOTE]
>엔터티를 삭제하면 해당 엔터티 정의 및 엔터티에 포함된 데이터 전체를 모두 삭제합니다. 해당 항목 내의 엔터티 및 데이터는 삭제한 경우 복구할 수 없습니다.

>[!NOTE]
>해당 앱에서 사용되는 엔터티를 삭제하는 경우 앱 또는 흐름이 중단될 수도 있습니다.

>[!NOTE]
>엔터티 A에 엔터티 B에 대한 [조회 필드](data-platform-entity-lookup.md)가 있는 경우, 엔터티 A를 삭제하려면 엔터티 B를 삭제해야 할 수 있습니다.
