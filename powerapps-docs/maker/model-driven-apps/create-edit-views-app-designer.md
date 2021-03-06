---
title: Power Apps를 사용하여 공용 또는 시스템 모델 기반 앱 보기 만들기 및 편집 | MicrosoftDocs
description: 앱 디자이너를 사용하여 보기를 만들거나 편집하는 방법 알아보기
keywords: ''
ms.date: 11/27/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03bfaec424624be1094314dbae763114892d2a59
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884876"
---
# <a name="create-and-edit-public-or-system-model-driven-app-views"></a>공용 또는 시스템 모델 기반 앱 보기 만들기 및 편집

이 항목에서는 공용 보기 만들기, 앱에 기존 보기 추가, 보기의 열, 필터 및 정렬 순서 변경과 같은 보기 작업에 필요한 몇 가지 작업을 수행합니다.

Power Apps에서 보기는 특정 엔터티에 대한 레코드가 표시되는 방식을 정의합니다. 보기는 다음을 정의합니다.
-  표시할 열(특성)
-  열의 너비
-  기본적으로 레코드를 정렬하는 방법
-  기본적으로 목록에 표시할 레코드를 결정하기 위해 적용할 필터

일반적으로 보기는 세 가지 유형으로 분류됩니다.
- **개인**: 개별 사용자는 개인 요구 사항에 따라 개인 보기를 만들 수 있습니다. 이러한 보기는 해당 보기를 만든 사용자와 공유하도록 선택한 모든 사람에게만 표시됩니다. 
- **공개:** 앱 제작자는 조직의 요구 사항에 맞게 공개 보기를 만들고 수정할 수 있습니다. 이러한 보기는 보기 선택기에서 사용할 수 있으므로 양식의 하위 표 또는 대시보드의 목록으로 사용할 수 있습니다.
- **시스템:** 앱 제작자는 조직의 요구 사항에 맞게 시스템 보기를 수정할 수도 있습니다. 이 보기는 시스템 엔터티에 존재하거나 사용자 지정 엔터티를 만들 때 자동으로 만들어지는 응용 프로그램이 종속된 특수한 보기입니다. 이러한 보기는 사용 권한에 따라 일부 또는 모든 사용자가 사용할 수 있습니다.

추가 정보: [보기 이해](create-edit-views.md)

## <a name="create-a-public-view-in-power-apps"></a>Power Apps에서 공용 보기 만들기
앱 제조업체는 Power Apps를 사용하여 공용 보기를 만들고 편집할 수 있습니다.
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  


    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.   
  
2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **보기** 탭을 선택합니다. 

3. 도구 모음에서 **보기 추가**를 선택합니다. 

4. **보기 만들기** 대화 상자에서 이름과 설명(선택 사항)을 입력한 다음 **만들기**를 선택합니다. 
    
5. 보기 디자이너에서 더하기 단추를 선택하여 보기에 표시할 열을 추가합니다. 추가 정보: [앱 디자이너에서 보기에 열 추가](#add-a-column-to-your-view-in-app-designer) 

   ![열 추가](../common-data-service/media/add-column-to-view.png)

6. 디자이너 보기에서 다음 작업을 수행할 수 있습니다. 
   - 열 필터링을 변경하려면 필터링 할 열의 머리글을 선택한 다음 드롭다운 메뉴에서 **필터 기준**을 선택합니다.
   - 열 정렬을 변경하려면 필터링 할 열의 머리글을 선택한 다음 **Sort A-Z** 또는 **Sort Z-A**을 선택합니다.
   - 열을 원하는 위치로 끌릭하고 끌어 열 너비를 구성합니다.
   - 열을 이동하려는 위치로 끌어서 열 순서를 변경합니다. 

    > [!NOTE]
    > 열 머리글을 클릭하고 **오른쪽으로 이동** 또는 **왼쪽으로 이동**을 선택하여 열 순서를 변경할 수도 있습니다.

10. **게시**를 선택하여 조직의 다른 사용자가 보기 및 만들기를 저장할 수 있도록 합니다. 
   

## <a name="work-with-views-in-app-designer"></a>앱 디자이너에서 보기를 사용하여 작업
다음 섹션에서는 앱 디자이너에서 보기를 만들고 편집하는 방법에 대해 설명합니다.

### <a name="open-and-add-a-view-in-the-app-designer"></a>앱 디자이너에서 보기를 열고 추가합니다.

다음 단계에서는 앱 디자이너에서 보기를 열고 추가하는 방법에 대해 설명합니다.
1. Power Apps의 왼쪽 탐색 창에서 **앱**을 선택하고 원하는 앱 옆의 **...** 를 선택한 다음 **편집**을 선택합니다. 

2. 앱 디자이너 **엔터티 보기** 섹션에서 **보기**를 선택합니다.

    이 예제에서는 **거래처** 엔터티에서 **보기**를 선택합니다.

    ![앱 디자이너 보기](media/ViewAppDesigner_AccountAppDesignerView.png "거래처 엔터티의 앱 디자이너 보기")

3. 보기를 추가하려면 공용, 상세하게 찾기, 관련 및 조회와 같은 보기 유형을 사용하여 보기를 선택합니다. 보기는 **보기** 목록에 자동으로 추가됩니다.

    > [!NOTE]
    > 선택한 엔터티에 따라 보기가 표시됩니다. 예를 들어 **거래처**를 선택하면 거래처 엔터티와 관련된 보기가 표시됩니다.

앱 디자이너에 대한 자세한 내용: [앱 디자이너를 사용하여 사용자 지정 비즈니스 앱 디자인](design-custom-business-apps-using-app-designer.md)


### <a name="add-a-column-to-your-view-in-app-designer"></a>앱 디자이너에서 보기에 열 추가
보기는 행과 열을 포함하는 테이블에 레코드를 표시합니다. 각 행은 레코드이고, 레코드에서 표시하는 필드는 사용자가 보기에 추가한 열에 의해 결정됩니다.

1. 앱 디자이너에서 원하는 엔터티 보기를 선택한 다음 오른쪽 창에서 원하는 보기 옆에 있는 편집(연필 모양 단추)을 선택합니다.  
2. **구성 요소** 탭에서 **기본 엔터티** 또는 **관련 엔터티**에 대한 **열 특성** 목록을 선택합니다.

    ![열 추가](media/ViewAppDesigner_AddColumn.png "보기에 열 추가") 

3. 목록에서 원하는 특성을 선택하여 열 머리글로 끕니다. 특성을 두 번 클릭하여 추가할 수도 있습니다.
4. 보기에 표시하려는 모든 속성을 추가할 때까지 3 단계를 반복합니다.

특성을 추가할 때 기존 열 머리글 사이의 임의의 위치로 끌 수 있습니다. 또한 보기에 특성을 추가한 후에도 열을 이동할 수 있습니다.


### <a name="define-filter-criteria-in-app-designer"></a>앱 디자이너에서 필터 조건 정의
보기에 레코드의 하위 집합만 표시되도록 필터 조건을 설정할 수 있습니다. 사용자가 보기를 열면 정의된 필터 조건에 맞는 레코드만 표시됩니다. 기본 엔터티와 관련 엔터티 모두에서 필드를 선택하여 필터링할 수 있습니다.
1. 앱 디자이너에서 **필터 조건** 섹션을 확장합니다.
   
    ![필터 조건 설정](media/ViewAppDesigner_FilterCriteria.png "필터 조건 설정") 

2. **필터 추가**를 선택합니다.
3. 첫 번째 열의 드롭다운 목록에서 특성을 선택합니다. 
4. 두 번째 열의 드롭다운 목록에서 연산자를 선택합니다.

    ![필터 조건 설정 연산자](media/ViewAppDesigner_FilterCriteriaOption.png "필터 조건 설정 연산자")

5. 세 번째 열에서 필터링할 값을 입력합니다.

기본 엔터티와 함께 관련 엔터티의 특성을 기준으로 데이터를 필터링할 수 있습니다. 

1. **구성 요소** 탭에서 **관련 엔터티**의 **열 특성** 목록을 선택하고 맨 위의 필드에서 **엔터티 선택** 아래쪽 화살표를 선택한 다음 원하는 엔터티를 선택합니다.

    이렇게 하면 별도의 섹션이 추가됩니다.

2. 이전 절차에서 2~5 단계를 반복합니다.

추가 정보: [엔터티 간 관계 만들기 및 편집](../common-data-service/create-edit-entity-relationships.md)

#### <a name="group-multiple-filters-in-app-designer"></a>앱 디자이너에서 여러 필터 그룹화
여러 개의 필드를 사용하여 레코드를 필터링하려는 경우에는 보기에 여러 필터를 추가할 수 있습니다. 

1. 그룹화할 필터를 선택하십시오.
    ![그룹 필터 설정](media/ViewAppDesigner_GroupFilter.png "Se그룹 필터 설정")
2. '및 그룹화' 또는 '또는 그룹화'를 선택하여 필터를 그룹화합니다.
    ![그룹 필터 선택](media/ViewAppDesigner_GroupFilterSelection.png "Se그룹 필터 선택") **및 그룹화**를 선택하면 보기에 두 조건을 모두 충족하는 레코드만 표시됩니다. **또는 그룹화**를 선택하면 필터 조건에 맞는 모든 레코드가 표시됩니다. 예를 들어 높음 또는 보통, 그리고 활성 상태의 우선 순위인 레코드만 표시하려면 **및 그룹화**를 선택합니다.

그룹에서 필터를 제거하려면 그룹을 선택한 다음 **그룹 해제**를 선택합니다. 

### <a name="set-primary-and-secondary-sort-order-for-columns-in-app-designer"></a>앱 디자이너에서 열에 대한 기본 및 보조 정렬 순서 설정
보기가 열렸을 때 표시되는 보기를 만들 때 설정한 순서대로 레코드가 정렬됩니다.   정렬 순서를 선택하지 않은 경우 기본적으로 레코드는 보기의 첫 번째 열에 따라 정렬됩니다. 단일 열을 기준으로 정렬하도록 선택 하거나 두 개의 열(기본 및 보조)을 선택하여 정렬할 수 있습니다. 보기가 열렸을 때 먼저 기본 정렬 순서에 사용할 열을 기준으로 레코드가 정렬되며 그 다음 보조 정렬 순서에 사용할 열을 기준으로 정렬됩니다. 

> [!NOTE]
> 기본 엔터티에서 추가한 열 특성에 대해서는 기본 및 보조 정렬 순서만 설정할 수 있습니다.

1. 정렬하기 위해 사용할 열을 선택하십시오.
2. 아래쪽 화살표를 선택하고 **기본 정렬** 또는 **보조 정렬**을 선택합니다.
 
    ![레코드 정렬](media/ViewAppDesigner_SortRecords.png "기본 및 보조 정렬 순서를 기준으로 레코드 정렬") 

기본 정렬 순서에 대해 선택한 열을 제거하면 보조 정렬 순서에 대해 선택한 열은 기본 정렬이 됩니다.

### <a name="define-a-web-resource-in-app-designer"></a>앱 디자이너에서 웹 리소스 정의
보기의 열과 연결할 스크립트 형식의 웹 리소스를 지정합니다. 이러한 스크립트는 열에 대한 아이콘을 표시하는 데 도움이 됩니다.

1. 웹 리소스를 추가할 열을 선택합니다.
2. **속성** 탭에서 **고급**을 선택합니다.
3. **웹 리소스** 드롭다운 목록에서 사용할 웹 리소스를 선택합니다.
4. **함수 이름** 입력란에 함수 이름을 입력합니다.

### <a name="edit-a-public-or-system-view-in-app-designer"></a>앱 디자이너에서 공용 또는 시스템 보기 편집
열을 추가, 구성 또는 제거하여 공용 또는 시스템 보기가 표시되는 방식을 변경할 수 있습니다.
1. 엔터티에 대한 **보기** 목록에서 **참조 목록 표시** 아래쪽 화살표 ![드롭다운](media/DownArrow.png "드롭다운 화살표")를 선택합니다.
    ![보기 편집](media/ViewAppDesigner_EditView.png "Ed공개 또는 시스템 보기 편집")
2. 편집하려는 보기 옆에 있는 **디자이너 보기 열기** ![디자이너 보기 열기](media/dynamics365-open-designer.png "디자이너 보기 열기")를 선택합니다. 

    디자이너 보기에서 보기가 열립니다. 

공용 또는 시스템 보기를 편집할 때 응용 프로그램에서 표시되기 전에 변경 내용을 저장하여 게시해야 합니다.


## <a name="community-tools"></a>커뮤니티 도구
**레이아웃 복제기 보기**및 **디자이너 보기**는 XrmToolBox 커뮤니티가 Power Apps용으로 개발한 도구입니다.

추가 정보: [개발자 도구 ](/powerapps/developer/common-data-service/developer-tools).

> [!NOTE]
> 이러한 도구는 XrmToolBox에서 제공하며 Microsoft에서 지원하지 않습니다. 도구와 관련된 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com/) 

### <a name="next-steps"></a>다음 단계
[1:N(일대다) 또는 N:1(다대일) 관계 만들기](../common-data-service/create-edit-1n-relationships.md)
