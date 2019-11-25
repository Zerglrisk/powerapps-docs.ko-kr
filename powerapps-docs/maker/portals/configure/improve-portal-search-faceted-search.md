---
title: 패싯 검색을 사용하여 포털 검색 개선 | MicrosoftDocs
description: 패싯 검색을 사용하거나 사용하지 않도록 설정하는 지침입니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760718"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>패싯 검색을 사용하여 포털 검색 개선

콘텐츠 특성을 기준으로 필터를 사용하여 포털 콘텐츠를 검색할 수 있습니다. 패싯 포털 검색으로 구현된 필터는 고객이 기존의 검색보다 빠르게 원하는 콘텐츠를 찾을 수 있도록 합니다.

## <a name="enable-or-disable-faceted-search"></a>패싯 검색 사용 또는 사용 안 함

기본 제공 패싯 검색은 귀하의 포털에서 활성화됩니다. 이를 제어하거나 사용하도록 설정하려면 다음 단계를 수행합니다.

1. [포털 관리 앱](configure-portal.md)을 열고 **포털** &gt; **웹 사이트** &gt; **사이트 설정**으로 이동합니다.
2. **Search/FacetedView** 사이트 설정을 선택합니다. 
3. **값**을 **true**로 변경하여 패싯 검색을 활성화하거나 **false**로 변경하여 비활성화합니다.

패싯 보기의 단일 조각을 비활성화하려면 다음과 같이 하십시오.

1. [포털 관리 앱](configure-portal.md)을 열고 **포털** &gt; **웹 템플릿**으로 이동합니다.
2. 보기를 선택하여 비활성화(즉, 참조 자료 관리 - 최고 평점 문서)
3. 페이지 상단에 있는 **비활성화** 버튼을 선택합니다.

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>패싯 보기에 대한 레코드 종류의 일부로 엔터티 그룹화

**검색/레코드 유형 패싯 엔터티** 사이트 설정으로 유사한 엔터티를 그룹화하여 사용자가 논리적인 방법으로 검색 결과를 필터링할 수 있습니다. 예를 들어 포럼, 포럼 게시물, 포럼 스레드에 대한 개별 옵션 대신 이러한 엔터티들이 포럼 레코드 종류 아래에 그룹화됩니다.

**포털** &gt; **웹 사이트** &gt; **사이트 설정**으로 이동하여 **검색/RecordTypeFacetsEntities** 사이트 설정을 엽니다. 

다른 엔터티는 단어 **포럼** 뒤에 위치합니다. 이는 첫 번째 값이 그룹화된 이름이기 때문입니다. 이 단어는 포털에 사용되는 언어에 따라 번역됩니다.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>패싯 검색을 사용하여 참조 자료 검색 결과 개선

패싯 검색으로 포털의 맨 왼쪽에 포럼, 블로그, 참조 문서 같은 항목에서 선택할 수 있는 검색 필터를 가질 수 있습니다. 특정 검색 유형에 대해 더 많은 필터가 추가됩니다. 예를 들어 참조 문서는 레코드 종류, 수정한 날짜, 등급 및 제품으로 필터링하여 고객이 필요한 콘텐츠를 찾을 수 있도록 도와줍니다. 맨 오른쪽에는 고객의 관련성 또는 조회수(참조 문서 관련)를 기준으로 결과를 정렬하는 드롭다운 상자가 있습니다. 다음은 사용 가능한 필터 중 일부에 대한 예가 포함된 화면 캡처입니다.

![필터를 사용하여 검색 결과 개선](../media/faceted-search-filter.png "필터를 사용하여 검색 결과 개선")
