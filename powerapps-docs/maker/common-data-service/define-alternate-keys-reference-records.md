---
title: Common Data Service에서 레코드를 참조할 대체 키 정의 | MicrosoftDocs
description: Common Data Service에서 레코드 참조에 사용될 수 있는 대체 키를 정의하는 방법 알기
ms.custom: ''
ms.date: 06/04/2019
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
ms.assetid: 29e53691-0b18-4fde-a1d0-7490aa227898
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7ad5f422c0d45bbeb60ae43e687329b1fb770c2b
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861166"
---
# <a name="define-alternate-keys-to-reference-records"></a>레코드를 참조할 대체 키 정의

*대체 키*로 데이터를 외부 시스템과 효율적이고 정확하게 통합할 수 있습니다. 외부 시스템에서 Common Data Service의 레코드를 고유하게 식별하는 GUID(Globally Unique Identifier) ID를 저장하지 않는 경우에 필수적입니다. 

데이터 통합 시스템은 고유 조합을 나타내는 하나 이상의 엔터티 필드 값을 사용하여 레코드를 고유하게 식별하기 위해 대체 키를 사용합니다. 각 대체 키에는 고유한 이름이 있습니다. 

예를 들어 대체 키를 사용하여 거래처 레코드를 식별하려면 계정 번호 또는 계정 번호 필드를 변경할 수 없는 값이 있는 다른 필드와 함께 사용하면 됩니다.

> [!NOTE]
> Power Apps에서 대체 키를 정의할 수 있는 반면 코드에서 프로그래밍 방법으로만 사용될 수 있습니다. 대체 키 프로그래밍 기능 사용에 대한 자세한 내용은 다음을 참조하십시오.   
> - [개발자 설명서: 대체 키를 사용하여 레코드 만들기](/dynamics365/customer-engagement/developer/use-alternate-key-create-record) 
> - [개발자 설명서: 대체 키를 사용하여 웹 API로 레코드 검색](/dynamics365/customer-engagement/developer/webapi/retrieve-entity-using-web-api#retrieve-using-an-alternate-key)

대체 키의 몇 가지 이점은 다음과 같습니다.  
  
- 레코드를 더욱 빠르게 조회합니다.  
- 강력한 대량 데이터 작동  
- 레코드 Id없이 외부 시스템으로부터 가져오기한 데이터로 프로그래밍 단순화  
  

## <a name="creating-an-alternate-key"></a>대체 키 만들기

대체를 만드는 데 사용할 수 있는 디자이너는 두 가지가 있습니다.

|디자이너| 설명|
|--|--|
|[Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 옵션은 사용할 수 없습니다.<br />추가 정보: [Power Apps 포털을 사용한 대체 키 정의](define-alternate-keys-portal.md)|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다.<br />추가 정보: [솔루션 탐색기를 사용한 대체 키 정의](define-alternate-keys-solution-explorer.md) |

> [!NOTE]
> 다음을 사용하여 환경에서 대체 키를 만들 수도 있습니다.
> - 대체 키의 정의가 포함된 솔루션을 가져옵니다.
> - 또한 개발자는 코드를 작성하여 만들 수 있습니다. 추가 정보: [개발자 설명서: 엔터티에 대한 대체 키 정의](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 

다음 요구 사항 중 하나를 해결 해야 하는 경우가 아니면 [Power Apps 포털](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)을 사용하여 대체 키를 만들어야 합니다.

- Common Data Service 기본 솔루션 이외의 솔루션 내에서 대체 키 만들기
- 지원 색인 만들기의 진행 상황을 추적하는 시스템 작업을 쉽게 추적하길 원할 것입니다.


## <a name="limits-in-creating-alternate-keys"></a>대체 키 만들기의 제한

대체 키를 만들 때 제약 조건이 있습니다.

### <a name="fields-that-can-be-used-for-alternate-keys"></a>대체 키에 사용할 수 있는 필드

이러한 종류의 필드만 대체 키를 만드는 데 사용할 수 있습니다.
 - 소수
 - 정수(Integer)
 - 한 줄 텍스트(String)
 - 날짜 및 시간
 - 조회
 - 옵션 집합

### <a name="number-of-keys"></a>키 수

엔터티에 대해 최대 5개의 다른 키를 정의할 수 있습니다.
 
### <a name="valid-key-size"></a>유효한 키 크기

키를 만들 때 시스템은 총 키 크기가 키당 900바이트 및 키당 16개 열 같은 SQL 기반 색인 제약 조건을 위반하지 않는지를 포함하여 해당 키를 플랫폼에서 지원할 수 있는지를 확인합니다. 키 크기가 제약 조건을 충족하지 않는 경우 오류 메시지가 표시됩니다.

### <a name="unicode-characters-in-key-value"></a>키 값의 유니코드 문자

대체 키에 사용되는 필드 내의 데이터에 문자 `<`,`>`,`*`,`%`,`&`,`:`,`/`,`\\` 중 하나가 포함되면 패치 또는 upsert 작업이 작동하지 않습니다. 

고유성만 필요한 경우에는 이 방법이 효과가 있지만 데이터 통합의 일부로 이러한 키를 사용해야 하는 경우에는 이러한 문자를 사용하는 데이터가 없는 필드에 키를 만드는 것이 가장 좋습니다.

## <a name="track-the-status-of-the-creation-of-the-alternate-key"></a>대체 키 만들기 상태 추적

대체 키를 만들면 대체 키에서 사용하는 필드에 고유 제약 조건을 적용하기 위해 데이터베이스 테이블에 색인을 만드는 시스템 작업을 시작합니다. 대체 키는 이러한 색인을 만들 때까지 적용되지 않습니다. 이러한 색인을 만드는 데는 시스템의 데이터 양에 따라 시간이 걸릴 수 있습니다. 

시스템 작업의 상태에 따라 대체 키의 상태가 결정됩니다. 대체 키는 다음과 같은 상태를 가질 수 있습니다.
- **보류 중**
- **진행 중**
- **활성**
- **실패함**

시스템 작업이 완료되면 대체 키 상태가 **활성** 상태이며 사용할 수 있습니다.

시스템 작업이 실패하면 시스템 작업을 찾아 오류를 확인합니다. 시스템 작업은 `Create index for {0} for entity {1}` 패턴을 따르는 이름을 갖습니다. 여기서 `0`은 대체 키의 **표시 이름**이고 `1`은 엔터티의 이름입니다.


> [!NOTE]
> 시스템 작업의 상태를 모니터링하려면 솔루션 탐색기를 사용하여 색인을 만들어야 합니다. 여기에는 모니터링할 수 있도록 시스템 작업에 연결된 링크가 포함됩니다. 추가 정보: [(선택 사항) 시스템 작업 추적 보기 색인 만들기](define-alternate-keys-solution-explorer.md#optional-view-the-system-job-tracking-creation-of-indexes)
  
  
### <a name="see-also"></a>참조  

[Power Apps 포털을 사용한 대체 키 정의](define-alternate-keys-portal.md)<br />
[솔루션 탐색기를 사용한 대체 키 정의](define-alternate-keys-solution-explorer.md)<br />
[개발자 설명서: 엔터티에 대한 대체 키 정의](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)<br />
[개발자 설명서: 대체 키를 사용하여 레코드 만들기](/dynamics365/customer-engagement/developer/use-alternate-key-create-record)
