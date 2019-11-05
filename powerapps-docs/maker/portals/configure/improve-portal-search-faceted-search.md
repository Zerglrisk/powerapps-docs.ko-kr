---
title: 패싯 검색을 사용 하 여 포털 검색 개선 | MicrosoftDocs
description: 패싯 검색을 사용 하거나 사용 하지 않도록 설정 하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552339"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>패싯 검색을 사용 하 여 포털 검색 향상

콘텐츠 특성을 기반으로 하는 필터를 사용 하 여 포털 콘텐츠를 검색할 수 있습니다. 패싯 포털 검색에서 구현 된 필터를 사용 하면 고객이 기존 검색 보다 더 빠르게 원하는 콘텐츠를 찾을 수 있습니다.

## <a name="enable-or-disable-faceted-search"></a>패싯 검색 사용 또는 사용 안 함

포털에서 기본 패싯 검색을 사용할 수 있습니다. 이를 제어 하거나 사용 하도록 설정 하려면 다음 단계를 수행 합니다.

1. [포털 관리 앱](configure-portal.md) 을 열고 **포털** &gt; **웹** 사이트 &gt; **사이트 설정**으로 이동 합니다.
2. **Search/FacetedView** 사이트 설정을 선택 합니다. 
3. 또는 **False** 로 설정 하 여 패싯 검색을 사용 하지 않도록 설정 하려면 **값** 을 **True** 로 변경 합니다.

패싯 뷰의 단일 부분을 사용 하지 않도록 설정 하려면 다음을 수행 합니다.

1. [포털 관리 앱](configure-portal.md) 을 열고 **포털** &gt; **웹 템플릿**으로 이동 합니다.
2. 사용 하지 않을 뷰 선택 (즉, 기술 자료 관리-상위 등급 문서)
3. 페이지 위쪽에서 **비활성화** 를 선택 합니다.

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>패싯 보기에 대 한 레코드 형식의 일부로 엔터티 그룹화

사이트 설정 **search/RecordTypeFacetsEntities** 를 사용 하면 유사한 엔터티를 함께 그룹화 하 여 사용자가 논리적으로 검색 결과를 필터링 할 수 있습니다. 예를 들어 포럼, 포럼 게시물 및 포럼 스레드에 대 한 별도의 옵션을 포함 하는 대신 이러한 엔터티는 포럼 레코드 유형으로 그룹화 됩니다.

**포털** &gt; **Websites** &gt; **사이트 설정** 으로 이동 하 여 **Search/recordtypefacetsentities** 사이트 설정을 엽니다. 

다른 엔터티에는 **포럼**이라는 단어가 붙습니다. 첫 번째 값은로 그룹화 된 이름이 기 때문입니다. 이 단어는 포털에서 사용 되는 언어를 기준으로 변환 됩니다.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>패싯 검색을 사용 하 여 기술 자료 검색 결과 개선

패싯 검색을 사용 하면 포털에서 가장 왼쪽에 검색 필터를 사용 하 여 포럼, 블로그 및 기술 항목과 같은 항목 중에서 선택할 수 있습니다. 특정 검색 형식에 대 한 추가 필터가 추가 되었습니다. 예를 들어 기술 항목은 고객이 필요한 콘텐츠를 찾을 수 있도록 레코드 유형, 수정 된 날짜, 등급 및 제품을 기준으로 필터링 할 수 있습니다. 오른쪽에는 고객의 관련성 또는 보기 수를 기준으로 결과를 정렬 하는 드롭다운 상자 (기술 항목에 특정)도 있습니다. 다음은 사용 가능한 필터의 예가 포함 된 화면 캡처입니다.

![필터를 사용 하 여 검색 결과 개선](../media/faceted-search-filter.png "필터를 사용 하 여 검색 결과 개선")
