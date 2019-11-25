---
title: '미리 보기 기능: Common Data Service에서 SQL API 데이터 공급자를 위한 Azure Cosmos DB 사용 | MicrosoftDocs'
description: 가상 엔터티와 함께 사용할 SQL API 데이터 공급자용 Azure Cosmos DB를 구성하는 방법에 대해 알아봅니다.
keywords: SQL API
ms.date: 02/15/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e9594ada54fb89f77298a4077281dcedbb8c656
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705674"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>미리 보기 기능: DB SQL API 데이터 공급자용 Azure Cosmos DB 요구 사항

이 항목에서는 SQL API 데이터 공급자에 대한 Azure Cosmos DB에 대한 요구 사항과 가상 엔터티를 사용하여 SQL API 데이터 공급자에 대한 Azure Cosmos DB를 사용하는 경우 구성 및 권장 모범 사례에 대해 설명합니다. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Azure Cosmos DB란?

Azure Cosmos DB는 업무상 중요한 애플리케이션을 위한 Microsoft의 전역으로 분산된 다중 모델 데이터베이스 서비스입니다. 스키마 없는 JSON 데이터를 통해 지속적으로 낮은 대기 시간으로 풍부하고 친숙한 SQL 쿼리 기능을 제공합니다. 추가 정보: [Azure Cosmos DB 소개: SQL API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>요구 사항

- Azure Cosmos DB를 포함하는 Azure 구독.
- Azure Cosmos DB SQL API 컬렉션.
- Azure Cosmos DB 데이터베이스 형식이 SQL이어야 합니다. 

## <a name="data-type-mapping"></a>데이터 형식 매핑

다음과 같은 JSON 구조가 있는 *Orders*라는 컬렉션에 Azure Cosmos DB 문서가 있다고 가정합니다.

![SQL API 문서의 예제 JSON.](media/documentdbexample.png)

이 테이블은 Common Data Service의 *주문* 컬렉션의 SQL API 문서에 대한 데이터 형식 매핑을 나타냅니다.

|SQL API 데이터|Common Data Service|
|--|--|
|`id`|기본 키|
|`name`|한 줄 텍스트|
|`quantity`|정수|
|`orderid`|한 줄 텍스트|
|`ordertype`|옵션 집합|
|`amount`|10진수 또는 통화|
|`delivered`|두 개의 옵션|
|`datetimeoffset`|날짜 및 시간|

> [!NOTE]
> - 밑줄(_) 접두사가 있는 특성은 SQL API에 의해 생성됩니다.
> - SQL API 문서에서 선택 사항으로 구성되고 Common Data Service에서 **비즈니스에 필수**로 매핑되는 특성으로 인해 런타임 오류가 발생합니다.
> - ID 특성 값은 guid여야 합니다.
> - SQL API에서 날짜를 사용하는 방법에 대한 자세한 내용은 [Azure Cosmos DB에서 날짜 작업](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/)을 참조하십시오.

## <a name="supported-sql-query-filtering"></a>지원되는 SQL 쿼리 필터링

SQL 쿼리 필터링은 다음 연산자를 지원합니다. 

- 비교 연산자:`<`,`>`,`<=`, `>=`,`!=`
- 논리 연산자: `and`, `or` 
- 집합 연산자: `in`, `not in`
- 문자열 연산자: `like`, `contains`, `begins with`, `ends with`

> [!NOTE]
> Like 연산자의 사용은 동등한 `contains`/`begins with`/`ends with`연산자로 변환됩니다. SQL API는 [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) 항목에 설명된 대로 패턴 인수를 지원하지 않습니다. SQL API 데이터 공급자에 대한 Azure Cosmos DB는 단일 특수 사례 `Like('[aA]%')`를 `BeginsWith('a')` 또는 `BeginsWith('A')`로 변환할 수 있습니다. SQL API의 문자열 비교는 대소문자를 구분합니다.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>SQL API 데이터 공급자용 Azure Cosmos DB를 사용하여 데이터 원본 추가

1. [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview)로 이동하여 **지금 가져오기**를 선택하고 지침에 따라 v9x 이상을 사용하여 애플리케이션을 사용자 환경에 추가합니다.
2. 솔루션을 설치한 후에는 환경에 로그인하고 **설정** > **관리** > **가상 엔터티 데이터 원본**으로 이동합니다.
3. 작업 도구 모음에서 **새로 만들기**를 선택하고 **데이터 공급자 선택** 대화 상자에서 **SQL API 데이터 공급자용 Azure Cosmos DB**를 선택한 다음 **확인**을 선택합니다.
![SQL API 데이터 공급자용 Azure Cosmos DB를 선택합니다.](media/createdatasource.png)
1. 다음 정보를 입력한 다음 **저장 및 닫기**를 선택합니다.

    |필드|설명|
    |--|--|
    |**이름**|데이터 원본을 설명하는 이름을 입력합니다.|
    |**컬렉션 이름**|가상 엔터티에 노출하려는 컬렉션이 들어 있는 Azure Cosmos DB *데이터베이스*의 이름입니다.  |
    |**인증 키**|Azure Cosmos DB 계정에 대한 기본 또는 보조 키입니다. Azure Cosmos DB 계정 아래의 **키** 설정 아래에서 Azure 관리 포털의 키를 찾을 수 있습니다.|
    |**URI**|Azure Cosmos DB 컬렉션이 있는 리소스 그룹의 URI입니다. URI는 `https://contoso/documents.azure.com:443`와 유사하게 구성됩니다. Azure Cosmos DB 계정에 대한 **키** 설정 아래에서 Azure 관리 포털의 URI를 찾을 수 있습니다. |
    |**시간 제한(초)**|데이터 요청 제한 시간 이전에 Azure Cosmos DB 서비스의 응답을 기다리는 시간(초)을 입력 합니다. 예를 들어, 30을 입력하면 제한 시간이 발생하기 전에 최대 30초를 기다립니다. 기본 제한 시간은 120초입니다.|

    > [!div class="mx-imgBorder"] 
    > ![SQL API 데이터 공급자를 사용하여 데이터 원본을 만듭니다.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>모범 사례 및 제한 사항

- Azure Cosmos DB를 데이터 원본으로 사용하는 경우 다음 사항을 확인하십시오.
   - 각 Azure Cosmos DB 데이터 원본은 하나의 가상 엔터티와만 연결할 수 있습니다.
   - 여러 데이터 원본을 Azure Cosmos DB의 동일한 컬렉션에 연결할 수 있습니다.
- 엔터티별로 컬렉션의 데이터를 세분화할 수 없습니다.
- Azure Cosmos DB 데이터베이스에는 스키마가 필요하지 않지만 Azure Cosmos DB 내의 데이터는 예측 가능한 스키마를 사용하여 구조화되어야 합니다. 
- SQL API 데이터 공급자를 위한 Azure Cosmos DB에서는 프로젝션, 필터링 및 정렬 연산자의 쿼리 변환을 구현하지만 조인 작업은 지원하지 않습니다.
- SQL API를 사용하여 단일 열만 필터링할 수 있습니다.

## <a name="see-also"></a>참조

[외부 데이터 원본에서 데이터를 포함하는 가상 엔터티 만들기 및 편집](create-edit-virtual-entities.md)
