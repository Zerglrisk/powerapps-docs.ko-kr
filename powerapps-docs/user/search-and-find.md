---
title: Common Data Service의 검색 및 찾기 옵션 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c7192b98d3f97a4aba57f58c52b02245cb71b155
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950890"
---
# <a name="compare-search-and-find-options-in-common-data-service"></a>Common Data Service 검색 및 찾기 옵션 비교

Common Data Service에서 데이터를 찾는 방법에는 다음 네 가지가 있습니다.

-   관련성 검색  
  
-   전체 텍스트 빠른 찾기 (단일 엔터티 또는 다중 엔터티)  
  
-   빠른 찾기 (단일 엔터티 또는 다중 엔터티)  

-   고급 찾기

> [!NOTE]
> 다중 엔터티 빠른 찾기를 항목별 검색이 라고도 합니다. 
  
다음 표에서는 사용 가능한 네 가지 옵션에 대해 간략하게 설명 합니다.

|기능성|[관련성 검색](search-records.md#relevance-search)|[전체 텍스트 빠른 찾기](search-records.md#start-a-search)|[빠른 찾기](search-records.md#start-a-search)|[고급 찾기](create-edit-or-save-advanced-find-search.md)|  
|-------------------|----------------------|---------------------------|----------------|-------------------|  
|기본적으로 사용 하도록 설정 되어 있나요?|아니요. 관리자는 수동으로 사용 하도록 설정 해야 합니다.|아니요. 관리자는 수동으로 사용 하도록 설정 해야 합니다.|예|예|  
|단일 엔터티 검색 범위|엔터티 표에서는 사용할 수 없습니다. 결과 페이지에서 엔터티를 기준으로 검색 결과를 필터링 할 수 있습니다.|엔터티 표에서 사용 가능 합니다.|엔터티 표에서 사용 가능 합니다.|엔터티 표에서 사용 가능 합니다.|  
|다중 엔터티 검색 범위|검색할 수 있는 엔터티 수에 대 한 최대 제한은 없습니다. **참고:**  검색할 수 있는 엔터티 수에 대 한 최대 제한은 없지만 레코드 유형 필터는 10 개의 엔터티에 대 한 데이터만 표시 합니다.|엔터티를 기준으로 그룹화 하 여 최대 10 개의 엔터티를 검색 합니다.|엔터티를 기준으로 그룹화 하 여 최대 10 개의 엔터티를 검색 합니다.|다중 엔터티 검색을 사용할 수 없습니다.|  
|검색 동작|엔터티의 모든 필드에서 검색 용어의 모든 단어와 일치 하는 항목을 찾습니다.|엔터티의 한 필드에서 검색 용어의 모든 단어와 일치 하는 항목을 찾습니다. 그러나 필드의 순서에 관계 없이 단어를 일치 시킬 수 있습니다.|"Like" 절이 있는 SQL 쿼리와 일치 하는 항목을 찾습니다. 문자열 내에서 검색 하려면 검색 용어에서 와일드 카드 문자를 사용 해야 합니다. 모든 일치 항목은 검색 용어와 정확히 일치 해야 합니다.|선택한 레코드 종류에 대 한 검색 조건을 정의할 수 있는 쿼리 작성기입니다. 를 사용 하 여 Office Excel로 내보내기 위한 데이터를 준비 하 여 데이터를 분석, 요약 또는 집계 하거나 피벗 테이블을 만들어 여러 관점에서 데이터를 볼 수도 있습니다.|  
|검색 가능한 필드|텍스트 한 줄, 여러 줄의 텍스트, 조회 및 옵션 집합과 같은 텍스트 필드입니다. 는 Numeric 또는 Date 데이터 형식의 필드 검색을 지원 하지 않습니다.|모든 검색 가능 필드입니다.|모든 검색 가능 필드입니다.|모든 검색 가능 필드입니다.|  
|검색 결과|단일 목록에서 검색 결과를 관련성 순서로 반환 합니다.|단일 엔터티의 경우 엔터티 표에서 검색 결과를 반환 합니다. 다중 엔터티의 경우 계정, 연락처, 잠재 고객 등 범주별로 그룹화 된 검색 결과를 반환 합니다.|단일 엔터티의 경우 엔터티 표에서 검색 결과를 반환 합니다. 다중 엔터티의 경우 계정, 연락처, 잠재 고객 등 범주별로 그룹화 된 검색 결과를 반환 합니다.|사용자가 지정한 열을 사용 하 여 선택한 레코드 형식의 검색 결과를 구성한 정렬 순서 대로 반환 합니다.|
|와일드 카드 (*)|단어 완성을 지 원하는 후행 와일드 카드입니다.|선행 와일드 카드가 지원 됩니다. 기본적으로 추가 된 후행 와일드 카드입니다.|선행 와일드 카드가 지원 됩니다. 기본적으로 추가 된 후행 와일드 카드입니다.|지원 되지 않습니다.|  
