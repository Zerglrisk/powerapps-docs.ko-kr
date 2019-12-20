---
title: Power Apps 포털을 사용한 대체 키 정의 | MicrosoftDocs
description: Power Apps 포털을 사용한 대체 키 정의에 대해 알아보기
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
ms.openlocfilehash: d52b3fa67863a43f82f020f3894bbabf5d38df84
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865474"
---
# <a name="define-alternate-keys-using-power-apps-portal"></a>Power Apps 포털을 사용한 대체 키 정의

[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하면 Common Data Service에서 엔터티 대체 키를 쉽게 보고 만들 수 있습니다.

포털을 사용하면 가장 일반적인 옵션을 구성할 수 있지만 특정 옵션은 솔루션 탐색기를 사용하여 설정만 가능 합니다. <br />추가 정보: 
- [레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)
- [솔루션 탐색기를 사용한 대체 키 정의](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>대체 키 보기

1. [Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **모델 기반** 또는 **캔버스** 디자인 모드 중 하나를 선택합니다.
2. **데이터** > **엔터티**를 선택하고 보려는 엔터티를 선택합니다.
3. 정의된 대체 키 목록을 보려면 **키**를 선택합니다.

    ![대체 키 보기](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>대체 키 만들기

1. [대체 키를 보는](#view-alternate-keys) 동안 **키 추가**를 선택합니다.
2. 패널을 사용하여 **표시 이름**을 설정하고 대체 키를 만드는 데 사용할 필드를 선택합니다.

    **이름** 필드는 표시 이름에 따라 채워집니다.

    ![대체 키 정의 예](media/alternate-key-account-number-sic-code.png)

1. **완료**를 선택하여 패널을 닫습니다.
2. **엔터티 저장**을 클릭하여 대체 키를 만듭니다.

> [!NOTE]
> 대체 키를 즉시 사용할 수는 없습니다. 시스템 작업은 대체 키를 지원하기 위한 데이터베이스 색인을 만들기 위해 엔터티를 저장할 때 시작됩니다.

## <a name="delete-an-alternate-key"></a>대체 키 삭제

[대체 키를 보는](#view-alternate-keys) 동안 삭제하려는 키를 선택하고 명령 모음에서 **키 삭제**를 선택합니다.

### <a name="see-also"></a>참조

[레코드를 참조할 대체 키 정의](define-alternate-keys-reference-records.md)<br />
[솔루션 탐색기를 사용한 대체 키 정의](define-alternate-keys-solution-explorer.md)<br />
[개발자 설명서: 엔터티에 대한 대체 키 정의](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
