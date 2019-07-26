---
title: 모델 기반 앱에서 레코드 검색 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 35cd4e4f0393f28d6cca5a2bd67497018a12ae26
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "61559360"
---
# <a name="search-for-records-in-an-app"></a>앱에서 레코드 검색

모델 기반 앱에서 관련성 검색 또는 항목별 검색을 사용 하 여 여러 엔터티 간에 레코드를 검색할 수 있습니다. 관련성 검색은 단일 목록에서 관련성을 기준으로 정렬 된 여러 엔터티에 대해 빠르고 포괄적인 결과를 제공 합니다. 항목별 검색은 계정, 연락처, 잠재 고객 등의 엔터티 유형별로 그룹화 된 검색 결과를 반환 합니다.

일반적으로 분류 된 검색은 기본 검색 옵션입니다. 그러나 조직에서 관련성 검색을 사용 하도록 설정 하면 기본 검색 환경이 됩니다.   
  
### <a name="normal-quick-find-categorized-search"></a>표준 빠른 찾기 (분류 된 검색) 
  
- **시작 문자**: 결과는 특정 단어로 시작 하는 레코드를 포함 합니다. 예를 들어 "알파인 스키 집"을 검색 하려는 경우 검색 상자에 **alp** 를 입력 합니다. **ski**를 입력 하면 레코드가 표시 되지 않습니다.  
  
- **와일드 카드**: 예: * ski 또는 * ski\*  
  
### <a name="relevance-search"></a>관련성 검색
  
- **내 검색**: 결과에는 검색 용어의 모든 단어가 포함 된 필드가 포함 된 레코드가 포함 됩니다.  개별 단어는 임의의 순서로 문자열의 어디에 나 나타날 수 있습니다.  예를 들어 "알파인 스키 집"을 검색 하는 경우 모든 검색 단어는 문자열의 어딘가에 표시 되기 때문에 "현재 집에서 집에 있는 스키 Meadows"에 대 한 결과를 찾을 수 있습니다.  

## <a name="switch-between-relevance-and-categorized-search"></a>관련성 및 범주화 된 검색 간 전환

조직에서 두 검색 옵션 (관련성 및 항목별 검색)을 모두 켠 경우 둘 사이를 전환할 수 있습니다.

1. 검색 형식 간을 전환 하려면 탐색 모음에서 **검색** 단추를 선택 합니다.

2. 왼쪽에서 드롭다운 메뉴를 선택 하 여 **관련성 검색** 또는 **항목별 검색**사이를 전환 합니다.

## <a name="start-a-search"></a>검색 시작  
  
1.  위쪽 탐색 모음에서 **검색**을 선택 합니다.  
  
2.  검색 상자에 검색어를 입력 한 다음 **검색**을 선택 합니다.  
  
## <a name="filter-search-results"></a>검색 결과 필터링  
  
-   한 레코드 종류를 기준으로 결과를 필터링 하려면 검색 화면의 **필터 기준:** 드롭다운 상자에서 레코드 형식을 선택 합니다.  
  
-   모든 레코드 유형을 검색 하려면 **필터 사용:** 드롭다운 상자에서 **없음** 을 선택 합니다.  
  
 
