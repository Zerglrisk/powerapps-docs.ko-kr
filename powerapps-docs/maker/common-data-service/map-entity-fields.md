---
title: Power Apps의 엔터티 필드 매핑 | MicrosoftDocs
description: 엔터티 필드를 매핑하는 방법 알아보기
ms.custom: ''
ms.date: 05/29/2018
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
ms.assetid: 7c5aa1c3-bde9-43f1-a369-fdcdbf14dec0
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5da8b9ecfb2bbba2a4e03fbc0d28301c41e2a7c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860902"
---
# <a name="map-entity-fields"></a>엔터티 필드 매핑
 
엔터티 관계가 있는 엔터티 간의 특성을 매핑할 수 있습니다. 따라서 다른 레코드의 컨텍스트에서 만들어진 레코드에 대한 기본값을 설정할 수 있습니다. 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>모델 기반 앱에서 새 레코드를 만드는 손쉬운 방법

특정 거래처의 직원에게 새 연락처 레코드를 추가하려는 경우를 가정해 봅니다. 두 가지 방법으로 이를 수행할 수 있습니다.  
  
### <a name="the-hard-way"></a>어려운 방법

앱에서 이동하여 처음부터 새 연락처 레코드를 만들 수 있습니다. 하지만 그런 다음 상위 거래처를 설정하고 상위 거래처와 같은 여러 가지 정보 항목을 입력해야 합니다(예: 주소 및 전화 정보). 이 경우 시간도 많이 걸리고 오류가 발생할 수도 있습니다.  
  
### <a name="the-easier-way"></a>쉬운 방법

거래처 엔터티로 시작하는 간단한 방법은 양식에서 **연락처** 하위 표를 사용하여 **+** 를 선택하여 연락처에 추가하는 것입니다. 먼저 기존의 관련 연락처를 검색하도록 안내하므로 중복 레코드를 실수로 만들지 않게 됩니다. 기존 레코드를 찾을 수 없는 경우 **새로 만들기**를 선택하여 새 연락처 레코드를 만듭니다. 

새 연락처 레코드 양식은 거래처(예: 주소 및 전화 정보)의 매핑된 특성 값을 기본값으로 포함합니다. 사용자는 레코드를 저장하기 전에 이러한 값을 편집할 수 있습니다.

## <a name="how-this-works"></a>작동 방식

1:N 엔터티 관계에 대한 엔터티 필드를 매핑할 때 기본 엔터티 레코드의 특정 데이터 항목이 새 관련 엔터티 양식에 복사되어 저장하기 전에 사용자가 편집할 수 있는 기본값을 설정합니다.
 
  
> [!NOTE]
> 이러한 매핑은 저장되기 전에 레코드에 기본값을 설정합니다. 사용자는 저장하기 전에 값을 편집할 수 있습니다. 전송되는 데이터는 해당 시점의 데이터입니다. 원본 데이터가 나중에 변경되면 동기화되지 않습니다.
>   
> 이러한 매핑은 워크플로 또는 대화 프로세스를 사용하여 만든 관련 레코드에 적용되지 않습니다. 개발자가 사용 가능한 매핑을 사용하여 새 레코드를 만들기 위해 `InitializeFrom` ([InitializeFrom 함수](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9) 또는 [InitializeFromRequest 클래스](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9))라는 특별한 메시지를 사용해도 코드를 사용하여 만든 새 레코드에 자동으로 적용되지 않습니다.  

## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

엔터티 필드를 매핑하는 유일한 방법은 솔루션 탐색기를 사용하는 것입니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
매핑 필드는 1:N 또는 N:1 엔터티 관계의 컨텍스트에서 수행되므로 먼저 [1:N 또는 N:1 엔터티 관계를 보아야](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships) 합니다.

## <a name="view-mappable-fields"></a>매핑 가능한 필드 보기

필드 매핑은 엔터티 관계 내에서 실제로 정의되지 않지만 관계 사용자 인터페이스에 노출됩니다. 모든 1:N 엔터티 관계에 기본값이 있는 것은 아닙니다. 엔터티에 대한 1:N(또는 N:1) 엔터티 관계의 목록을 볼 때 표시되는 관계를 유형별로 필터링할 수 있습니다. **모두**, **사용자 지정**, **사용자 지정 가능** 또는 **매핑 가능** 중에서 선택할 수 있습니다. 매핑 가능한 엔터티 관계는 엔터티 필드를 매핑할 수 있는 액세스 권한을 제공합니다. 

![매핑 가능한 엔터티 관계 보기](media/mappable-entity-relationships.png) 

매핑할 수 있는 엔터티 관계를 열 때 왼쪽 탐색에서 **매핑**을 선택합니다.

![엔터티 관계에 대한 관계 선택](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>매핑 삭제

적용하지 않으려는 매핑이 있는 경우에는 매핑을 선택하고 ![아이콘 삭제](media/delete.gif) 아이콘을 클릭합니다.

## <a name="add-new-mappings"></a>새 매핑 추가

새 매핑을 만들려면 도구 모음에서 **새로 만들기**를 클릭합니다. 이렇게 하면 **필드 매핑 만들기** 대화 상자가 열립니다.

![필드 매핑 만들기 대화 상자](media/create-field-mapping-dialog.png)

매핑할 값이 포함된 하나의 원본 엔터티 필드와 하나의 대상 엔터티 필드를 선택합니다. 

![필드 매핑 구성](media/configure-field-mapping.png)

그 다음 **확인**을 선택하여 대화 상자를 닫습니다.

다음 규칙은 매핑할 수 있는 데이터 종류를 표시합니다.  
  
- 두 필드 모두의 유형 및 형식이 동일해야 합니다.  
- 대상 필드의 길이는 원본 필드의 길이보다 길거나 같아야 합니다.  
- 대상 필드가 다른 필드에 이미 매핑되어 있어서는 안 됩니다.  
- 원본 필드는 양식에 표시되어야 합니다.  
- 대상 필드는 사용자가 데이터를 입력할 수 있는 필드여야 합니다.  
- 주소 ID 값은 매핑할 수 없습니다.
- 양식에 표시되지 않는 필드로 매핑하거나 그러한 필드에서 매핑되는 경우에는 해당 필드가 양식에 추가될 때까지 매핑이 완료되지 않습니다.
- 필드가 옵션 집합인 경우 각 옵션의 정수 값이 동일해야 합니다.  
  
> [!NOTE]
>  옵션 집합 필드를 매핑해야 하는 경우 동일한 전역 옵션 집합을 사용하여 두 필드를 모두 구성하는 것이 좋습니다. 그렇지 않으면 수동으로 동기화하는 별도의 두 옵션 집합을 유지하기 어려울 수 있습니다. 각 옵션의 정수 값이 올바르게 매핑되지 않으면 데이터에 문제가 발생할 수 있습니다. 추가 정보: [Common Data Service에 대한 전역 옵션 집합(선택 목록) 만들기 및 편집](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>자동으로 필드 매핑 생성  

**추가 작업** 메뉴에서 **매핑 생성**을 선택하여 매핑을 자동으로 생성할 수도 있습니다.

시스템 엔터티를 사용하여 이 작업을 수행할 때는 주의해야 합니다. 사용자 지정 엔터티를 만들고 매핑을 활용하려고 할 경우 사용합니다. 

> [!WARNING]
> 그러면 모든 기존 매핑을 제거하고 유사한 이름 및 데이터 형식을 가진 필드에만 기반한 제안된 매핑으로 바꿉니다. 시스템 엔터티에서 이를 사용할 경우 일부 필수 매핑이 손실될 수 있습니다. 사용자 지정 엔터티의 경우 필요 없는 매핑을 더욱 쉽게 삭제할 수 있고 매핑 생성 작업으로 만들지 않는 다른 매핑을 추가할 수 있습니다.  


## <a name="publish-customizations"></a>사용자 지정 항목 게시 

필드 매핑은 메타데이터가 아니므로 변경 내용을 적용하기 전에 게시해야 합니다. 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>참조
[솔루션 탐색기를 사용하여 1:N(일대다) 또는 N:1(다대일) 엔터티 관계 만들기 및 편집](create-edit-1n-relationships-solution-explorer.md)<br />
[개발자 설명서: 엔터티 및 특성 매핑 사용자 지정](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[개발자 설명서: 웹 API 다른 엔터티에서 새 엔터티 만들기](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
