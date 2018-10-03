---
title: PowerApps에서 모델 기반 앱 보기 만들기 또는 편집 | MicrosoftDocs
description: 보기를 만들거나 편집하는 방법 알아보기
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-model-driven-app-views"></a>모델 기반 앱 보기 이해

<a name="BKMK_CreatingAndEditingViews"></a>   

PowerApps 앱에서 보기를 사용하여 특정 엔터티의 레코드 목록이 응용 프로그램에 표시되는 방법을 정의합니다. 보기는 다음을 정의합니다.

- 표시할 열
- 각 열의 너비
- 기본적으로 레코드 목록이 정렬되는 방법
- 목록에 표시할 레코드를 제한하기 위해 적용되는 기본 필터

사용자가 엔터티 데이터의 다른 보기에 대한 옵션을 사용하도록 보기의 드롭다운 목록이 응용 프로그램에 자주 표시됩니다.

개별 보기에 표시되는 레코드는 목록(표라고도 함)에 표시되며 사용자에게 중요한 데이터를 더 쉽게 표시하도록 기본 정렬, 열 너비 및 필터를 변경할 수 있도록 자주 옵션을 제공합니다. 보기는 응용 프로그램에 사용되는 차트의 데이터 원본도 정의합니다.  
  
## <a name="types-of-views"></a>보기 유형  
  
보기 유형은 *개인*, *시스템* 및 *공용*의 세 가지입니다.

이 항목은 시스템 관리자 및 시스템 사용자 지정자가 시스템 보기 및 공용 보기를 사용하는 방법에 대해 설명합니다. 
  
### <a name="personal-views"></a>개인 보기  
  
 저장된 보기 엔터티의 동작에 대해 최소한 사용자 수준 액세스를 가진 사용자는 개인 보기를 만들 수도 있습니다. 시스템 관리자는 개인 보기를 만들거나, 읽거나, 쓰거나, 삭제하거나, 할당하거나, 공유할 수 있도록 사용자 수준을 제어하는 보안 역할에서 각 동작에 대해 액세스 수준을 수정할 수 있습니다.

개인 보기는 사용자의 기본 사용자 수준 액세스 권한이므로 개인적으로 소유되며, 본인 또는 개인 보기를 공유하도록 선택한 다른 사용자에게만 표시됩니다. 상세하기 찾기 또는 보기 목록에서 필터를 새 보기로 저장 및 현재 보기에 필터 저장 옵션을 사용하여 정의하는 쿼리를 저장하여 개인 보기를 만들 수 있습니다. 이러한 보기는 일반적으로 응용 프로그램에서 사용할 수 있는 시스템 보기 또는 공용 보기의 목록 아래쪽에 포함됩니다. 시스템 보기 또는 공용 보기를 기반으로 새로운 개인 보기를 만들 수 있지만 개인 보기를 기반으로 시스템 보기나 공용 보기는 만들 수 없습니다.
  
### <a name="system-views"></a>시스템 보기
시스템 관리자 또는 시스템 사용자 지정자는 시스템 보기를 편집할 수 있습니다. 시스템 보기는 시스템 엔터티에 존재하거나 사용자 지정 엔터티를 만들 때 자동으로 만들어지는 응용 프로그램이 종속된 특수한 보기입니다. 이러한 보기는 특정 용도가 있으며 일부 추가 기능이 있습니다. 


|시스템 보기  |설명  |
|---------|---------|
|빠른 찾기     | 검색할 때 사용되는 기본 보기는 빠른 찾기를 사용하여 수행됩니다. 시스템 보기는 빠른 찾기 및 조회 보기의 검색 기능을 사용할 때 검색할 필드를 정의하기도 합니다.        |
|상세하게 찾기     |  상세하기 찾기를 사용할 때 결과를 표시하는 데 사용되는 기본 보기입니다. 이 보기는 템플릿으로 사용할 보기를 정의하지 않고 새 사용자 지정 공용 보기 또는 개인 보기를 만들 때 기본적으로 사용되는 열도 정의합니다.       |
|관련 보기     |  레코드의 관련 엔터티를 나열하는 기본 보기입니다.       |
|조회     | 조회 필드에 설정할 레코드를 선택할 때 표시되는 보기입니다.        |

이러한 보기는 보기 선택에 표시되지 않으므로 양식의 하위 목록 또는 대시보드의 목록으로 사용할 수 없습니다. 이러한 보기를 삭제하거나 비활성화할 수 없습니다. 추가 정보: [보기 제거](remove-views.md)

시스템 보기는 조직에서 소유하므로 누구나 볼 수 있습니다. 예를 들어 누구나 보기(savedquery) 엔터티의 레코드를 읽을 수 있는 조직 수준 액세스 권한이 있습니다. 이러한 보기는 특정 엔터티에 연결되어 있으며 솔루션 탐색기에 표시됩니다. 이러한 보기는 엔터티에 연결되어 있으므로 솔루션에 포함할 수 있습니다.

### <a name="public-views"></a>공용 보기

공용 보기는 사용자가 원하는 대로 사용자 지정할 수 있는 일반 용도의 보기입니다. 이러한 보기는 보기 선택에서 사용할 수 있으므로 양식의 하위 표 또는 대시보드의 목록으로 사용할 수 있습니다. 일부 공용 보기는 시스템 엔터티 및 사용자 지정 엔터티에 대해 기본적으로 존재합니다. 예를 들어 새 사용자 지정 엔터티를 만들 때 다음 공용 보기와 시스템 보기 다음 조합을 사용합니다.


|이름  |그런 다음  |
|---------|---------|
|활성 *엔터티 복수 이름*     |  공공 사업       |
|비활성 *엔터티 복수 이름*    |  공공 사업       |
|빠른 찾기 *활성 엔터티 복수 이름*     | 빠른 찾기        |
|*엔터티 이름* 상세하게 찾기 보기     | 상세하기 찾기        |
|*엔터티 이름* 관련 보기     |  관련 보기       |
|*엔터티 이름* 조회 보기     | 조회        |

사용자 지정 공용 보기를 만들 수 있습니다. 비관리형 솔루션에서 만든 사용자 지정 공용 보기를 삭제할 수 있습니다. 시스템 정의 공용 보기는 삭제할 수 없습니다. 관리형 솔루션을 가져와서 추가된 사용자 지정 공용 보기는 관리형 솔루션을 제거할 때를 제외하고 삭제되지 않도록 관리 속성을 설정할 수 있습니다.

## <a name="places-where-you-can-access-the-view-editor-to-create-or-edit-views"></a>보기 편집기를 액세스하여 보기를 작성하거나 편집할 수 있는 위치

- PowerApps 사이트 : **모델 기반** 영역 > **데이터** > **엔터티** > **보기** 탭에서 보기 디자이너에 액세스할 수 있습니다. 기존 보기를 열거나 새 보기를 만듭니다. 추가 정보: [보기 만들기 또는 편집](create-and-edit-views.md)
- 앱 디자이너: 앱에서 작업하는 경우 만들어진 보기에 대해 끌어서 놓기 기능이 있는 간단하고 직관적인 UI를 제공하는 앱 디자이너를 사용할 수 있습니다. 추가 정보: [자습서: 앱 디자이너를 사용하여 공용 또는 시스템 보기 만들기 및 편집](create-edit-views-app-designer.md)
- 솔루션 탐색기: Dynamics 365를 이미 사용해 본 경우에는 솔루션 탐색기를 사용할 수 있습니다. 추가 정보: [고급 앱 제작 및 사용자 지정 영역으로 이동](advanced-navigation.md#solution-explorer)
 
## <a name="customize-views"></a>보기 사용자 지정

시스템 지정자는 표(목록)를 편집 가능하게 하고 통합 인터페이스와 호환되게 하여 컨트롤을 통해 보기를 사용자 지정할 수 있습니다. 다음과 같은 컨트롤이 사용됩니다.

- 편집 가능한 표: 사용자가 웹 앱, 태블릿, 또는 휴대폰을 사용하여 표와 하위 표에서 직접 서식 있는 인라인 편집할 수 있습니다. 추가 정보: [편집 가능한 표 사용자 지정 컨트롤을 사용하여 표를 편집 가능하도록 만들기](make-grids-lists-editable-custom-control.md)
- 읽기 전용 표: 응답성이 뛰어난 디자인 원칙을 사용하여 모바일 및 태블릿 등의 모든 화면 크기 또는 방향에 최적화된 보기 및 상호 작용 환경을 제공합니다. 추가 정보: [통합 인터페이스 앱의 속성 지정](specify-properties-for-unified-interface-apps.md)

## <a name="next-steps"></a>다음 단계

[보기 만들기 또는 편집](create-and-edit-views.md)