---
title: 레코드에 조회 필드 사용 | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/06/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4ef67695603f3badeba92f46c6da90e21715c98b
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177842"
---
#  <a name="use-the-lookup-field-on-a-record"></a>레코드에 조회 필드 사용

Lookup을 사용 하면 관련 엔터티에서 레코드를 선택할 수 있습니다. 관련 엔터티를 선택 하 고 검색 조건 (예: 이름 또는 전자 메일 주소)을 입력 하는 경우 조회가 자동으로 부분 텍스트를 확인 하기 시작 하 고 일치 하는 레코드를 표시 합니다. 검색 조건의 전체 텍스트를 입력 한 후 레코드가 표시 되지 않으면 레코드가 없음을 지정 하는 메시지가 표시 됩니다.

예를 들어 **Adrian Dumitrascu**이름을 검색할 수 있습니다. **Ad**를 입력 하면 일치 하는 레코드를 자동으로 채우고 표시할 수 있습니다.

  > [!div class="mx-imgBorder"]
  > ![일치 하는 레코드를 자동으로 채웁니다.](media/automatically-populate-matching-records.png "일치 하는 레코드를 자동으로 채웁니다.")
  
>[!NOTE] 
>관리자는 조회에서 부분 검색 텍스트를 확인 하는 데 사용 하는 조건을 정의할 수 있습니다.

또한 **새로** 만들기 단추를 선택 하 여 새 레코드를 만들 수 있습니다. **새** 단추를 보고 레코드를 만들 수 있는 권한이 있어야 합니다. 조회 필드를 선택 하면 가장 최근에 사용한 5 개의 레코드가 5 개의 즐겨 찾는 레코드와 함께 표시 됩니다. 표시 되는 레코드는 보기 기록과 고정 된 즐겨찾기에 따라 달라 집니다. 

예를 들어 기록에 세 개의 레코드만 있는 경우 조회는 자주 사용 하는 레코드 중 7 개와 함께이 세 가지를 표시 합니다. 즐겨찾기를 고정 하지 않은 경우 가장 최근에 본 레코드만 표시 됩니다.

## <a name="types-of-lookups"></a>조회 유형

조회는 다음과 같이 분류 됩니다. 

- **간단한 조회:** 단일 엔터티의 필드에서 단일 레코드를 선택 합니다. 

- **Attributetype.partylist-형식 필드:** 를 사용 하 여 조회에서 여러 엔터티의 여러 레코드를 선택할 수 있습니다. Attributetype.partylist-type 필드를 사용 하 여 여러 레코드를 선택 합니다. 이렇게 하면 새 검색을 여러 번 수행 하 여 각 레코드를 추가할 수 있습니다. 레코드를 선택할 때마다 다른 레코드에 대해 새 검색을 수행할 수 있습니다.
  
- **관련-형식 필드:** 를 사용 하 여 조회에서 여러 엔터티의 단일 레코드를 선택 합니다. 

## <a name="search-in-a-lookup-field"></a>조회 필드에서 검색 
조회를 검색 하려면 텍스트 상자를 선택 하 고 검색 조건을 입력 합니다. 조회를 위해 최근 레코드를 사용 하는 경우 텍스트 상자를 선택 하면 최근 레코드가 표시 됩니다.

  > [!div class="mx-imgBorder"]
  > ![조회 필드 찾아보기](media/MRU.png "조회 필드 찾아보기")  
  
>[!NOTE]   
> 조회 검색의 기본 검색 결과는로 시작 합니다. 즉, 결과는 특정 단어로 시작 하는 레코드를 포함 합니다. 예를 들어 **알파인 스키 집을**검색 하려면 검색 상자에 **alp** 를 입력 합니다. **ski**를 입력 하는 경우 레코드가 검색 결과에 표시 되지 않습니다.
>
> 와일드 카드 검색의 경우 별표를 사용 합니다. 예를 들어 * ski 또는 * ski를 입력 합니다.

## <a name="browse-in-a-lookup-field"></a>조회 필드에서 찾아보기
조회를 찾아보려면 조회 아이콘 (돋보기)을 선택 합니다. 드롭다운에 항목의 전체 목록이 표시 됩니다.

  > [!div class="mx-imgBorder"]
  > ![조회 필드 검색](media/MRU_1.png "조회 필드 검색")  
 
## <a name="most-recently-used-record-type-images"></a>가장 최근에 사용한 레코드 형식 이미지
가장 최근에 사용 된 레코드 목록에는 레코드 유형을 구분 하는 데 도움이 되는 이미지가 표시 됩니다.

>[!NOTE] 
>최근 레코드는 검색어 또는 선택한 보기를 기준으로 필터링 되지 않습니다.

  > [!div class="mx-imgBorder"]
  > ![조회 필드가 이미지를 표시 합니다.](media/Lookup_03-MRU_Entity_Images_56[1].png "조회 필드가 이미지를 표시 합니다.")  
  
## <a name="record-type-selection-list"></a>레코드 유형 선택 목록  
결과가 여러 레코드 형식으로 확장 되 면 해당 레코드의 형식 수를 확인 하 고 목록에서 선택할 수 있습니다.

  > [!div class="mx-imgBorder"]
  > ![레코드 수 보기](media/Lookup_04-MultipleEntityTypes[1].gif "레코드 수 보기")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>기존 레코드를 찾을 수 없는 경우 새 레코드 만들기

레코드를 찾을 수 없는 경우 조회 영역에서 **새로** 만들기를 선택 하 여 새 레코드를 만듭니다.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>조회 필드에서 기존 레코드 바꾸기

단순 및 관련 형식 조회를 사용 하는 동안 기존 레코드를 바꿀 수 있습니다. 레코드를 검색 합니다. 그런 다음 레코드를 선택 하 고 새 레코드로 바꿉니다.

### <a name="change-a-view-in-a-lookup-field"></a>조회 필드의 뷰 변경 

**변경 보기** 를 선택 하면 다음을 확인할 수 있습니다.
 - **팔 로우**하는 연락처, **연락처 조회 보기**또는 **활성 연락처**와 같은 레코드를 확인 하는 방법입니다.
 - 이름, 전자 메일 또는 전화 번호와 같이 레코드에서 보려는 항목입니다. 예를 들어 팔 로우 하는 연락처만 보려면 **보기 변경** \> **연락처를 팔 로우**합니다 .를 선택 합니다. 여기에 나와 있는 것 처럼 다음에 나오는 연락처만 표시 됩니다. 

    ![뷰 연락처 유형 변경](media/change-view.png "뷰 연락처 유형 변경")

>[!IMPORTANT] 
>관리자가 보기에 표시 되는 옵션을 구성 하지 않은 경우 **보기 변경** 옵션이 표시 되지 않습니다.

### <a name="choose-from-multiple-records"></a>여러 레코드에서 선택

조회에서 사용 가능한 표시 영역에 맞출 수 있는 것 보다 많은 레코드를 필드에 포함 하는 경우 표시 영역이 축소 됩니다. 즉, 표시 영역에 맞는 레코드가 표시 되지 않는 레코드 수 옆에 표시 됩니다. 모든 레코드를 보려면 숫자를 선택 합니다. 다음 이미지는 축소 된 필드와 축소 되지 않은 필드의 차이점을 보여 줍니다.

**되었는지**

![축소 된 다중 조회 표시 영역](media/collapsed-multi-lookup-display-area.png "축소 된 다중 조회 표시 영역")


**축소 안 됨:**

![축소 되지 않은 다중 조회 표시 영역](media/non-collapsed-multi-lookup-display-area.png "축소 되지 않은 다중 조회 표시 영역")
