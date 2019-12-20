---
title: Power Apps의 엔터티 개요 | MicrosoftDocs
description: Power Apps 포털을 사용하여 엔터티를 만들고 편집하는 방법 알아보기
ms.custom: ''
ms.date: 07/25/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: 0
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 199c7705bd283cbc316b6a2b8056eba7f7507ea1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865430"
---
# <a name="entity-relationships-overview"></a>엔터티 관계 개요

엔터티 관계는 다른 엔터티 또는 동일한 엔터티의 레코드에 엔터티 레코드를 연결하는 방법을 정의합니다. 두 가지 유형의 엔터티 관계가 있습니다.
- **일대다 관계** 일대다 엔터티 관계에서는 많은 참조하는(관련) 엔터티 코드를 단일 참조되는(기본) 엔터티 레코드에 연결할 수 있습니다. 참조되는 엔터티 레코드는 "상위"라고 하고, 참조하는 엔터티 레코드는 "하위"라고 합니다.  다대일 관계는 일대다 관계의 하위 관점에 불과합니다.
- **다대다 관계** 다대다 엔터티 관계는 많은 엔터티 레코드를 다른 많은 엔터티 레코드에 연결할 수 있습니다. 다대다 관계를 사용하여 관련된 레코드는 동일한 수준으로 간주할 수 있으며 관계는 상호적입니다. 

## <a name="see-also"></a>참조
[두 엔터티 간 관계 만들기](data-platform-entity-lookup.md) <br/>
[Power Apps 포털을 사용하여 Common Data Service에서 다대다 엔터티 관계 만들기](create-edit-nn-relationships-portal.md)
