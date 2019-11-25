---
title: 솔루션 탐색기를 사용한 대체 키 정의 | MicrosoftDocs
description: 솔루션 탐색기를 사용하여 Common Data Service에서 레코드를 참조하는 데 사용할 수 있는 대체 키를 정의하는 방법에 대해 설명합니다.
ms.custom: ''
ms.date: 05/31/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b1b38c94cbd4615ff0ab449944e65089865a823
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758727"
---
# <a name="define-alternate-keys-using-solution-explorer"></a>솔루션 탐색기를 사용한 대체 키 정의

솔루션 탐색기를 통해 Common Data Service의 대체 키를 보고 만들 수 있습니다.

[PowerApps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정할 수 있습니다. <br />추가 정보: 
- [레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)<br />
- [PowerApps 포털을 사용한 대체 키 정의](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 대체 키의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>대체 키 보기

1. 솔루션 탐색기가 열리면 **구성 요소**에서 **엔터티**를 확장하고 대체 키를 보려는 엔터티를 선택합니다.
2. 엔터티를 확장하고 **키**를 선택합니다.

    ![대체 키 보기](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>대체 키 만들기

1. [대체 키를 보는](#view-alternate-keys) 동안 **새로 만들기**를 선택합니다.
1. 양식에서 **표시 이름**을 입력합니다. **이름** 필드는 **표시 이름**에 따라 채워집니다. 
2. **사용 가능한 속성** 목록에서 각 속성을 선택한 다음 **추가 >** 를 선택하여 속성을 **선택한 속성** 목록으로 이동합니다.
    ![대체 키 만들기](media/create-alternate-key-solution-explorer.png)
1. **확인**을 선택하여 양식을 닫습니다.

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>(선택 사항) 시스템 작업 추적 보기 색인 만들기
1. 새 대체 키를 만든 후 [대체 키를 보는](#view-alternate-keys) 동안 만든 키에 대한 행이 표시됩니다.
2. **시스템 작업** 열에서 대체 키를 지원하기 위해 색인 생성을 모니터링하는 시스템 작업에 대한 링크를 찾을 수 있습니다. 
    
    이 시스템 작업은 `Create index for {0} for entity {1}` 패턴을 따르는 이름을 갖습니다. 여기서 `0`은 대체 키의 **표시 이름**이고 `1`은 엔터티의 이름입니다.

    시스템 작업이 성공적으로 완료된 후에는 시스템 작업에 대한 링크가 표시되지 않습니다. 추가 정보: [시스템 작업 모니터링 및 관리](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>대체 키 삭제

[대체 키를 보는](#view-alternate-keys) 동안 ![삭제](media/delete.gif)를 선택합니다.

### <a name="see-also"></a>참조

[레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)<br />
[PowerApps 포털을 사용한 대체 키 정의](define-alternate-keys-portal.md)<br />
[개발자 설명서: 엔터티에 대한 대체 키 정의](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
