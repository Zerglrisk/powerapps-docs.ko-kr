---
title: Power Apps에서 솔루션 사용 | MicrosoftDocs
description: 솔루션을 사용하여 앱을 만들거나 사용자 지정하는 방법 알아보기
ms.custom: ''
ms.date: 10/28/2019
ms.reviewer: tapanm
ms.service: powerapps
ms.topic: article
author: caburk
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: caburk
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e4d8b6b69ab820541b822fc58ce5c079df7b5b19
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2885337"
---
# <a name="use-solutions-in-power-apps"></a>Power Apps에서 솔루션 사용

 Power Apps 내의 왼쪽 탐색에서 **솔루션**을 선택하여 솔루션 목록을 볼 수 있습니다. 그런 다음 솔루션을 선택하여 모든 구성 요소를 볼 수 있습니다. 
 
> [!div class="mx-imgBorder"]  
> ![모든 구성 요소가 포함된 데모 솔루션](media/solution-all-items-list.PNG "모든 구성 요소가 포함된 데모 솔루션")  
 
> [!NOTE]
>  솔루션 환경은 온라인 환경 및 환경 버전 9.1.0.267 이상에서만 사용할 수 있습니다. 버전을 확인하려면 [Power Apps 관리 센터](https://admin.powerapps.com/)> **환경**으로 이동하여 환경을 선택하고 **세부 정보** 탭을 선택합니다. 이전 버전 환경의 경우 솔루션을 선택하면 기본 환경에서 열립니다.  
 
 항목을 스크롤하여 솔루션의 모든 구성 요소를 탐색할 수 있습니다. 목록에 100개 이상의 항목이 있는 경우 추가 항목을 보려면 **다음 100개 항목 로드**를 선택할 수 있습니다. 
 
> [!div class="mx-imgBorder"]  
> ![추가 구성 요소 로드](media/load-more.PNG "추가 구성 요소 로드")  

 ## <a name="search-and-filter-in-a-solution"></a>솔루션에서 검색 및 필터링
 
 특정 구성 요소를 이름으로 검색할 수도 있습니다. 
 
> [!div class="mx-imgBorder"]  
> ![구성 요소 검색](media/solution-search-box.png "구성 요소 검색")  
 
 또는 구성 요소 유형에 따라 목록의 모든 항목을 필터링합니다.
  
> [!div class="mx-imgBorder"]  
> ![유형별로 구성 요소 필터링](media/solution-filter.PNG "유형별로 구성 요소 필터링")  
 
 ## <a name="contextual-commands"></a>상황별 명령
 
 각 구성 요소를 선택하면 명령 모음에 사용할 수 있는 작업은 솔루션이 선택한 구성 요소 유형 및 기본 솔루션인지 또는 관리형 솔루션인지 여부에 따라 변경됩니다. 
 
> [!div class="mx-imgBorder"]  
> ![구성 요소별 명령](media/component-commands.png "구성 요소별 명령")  
 
 구성 요소를 선택하지 않으면 솔루션 자체에 적용된 작업이 명령 모음에 표시됩니다. 
 
> [!div class="mx-imgBorder"]  
> ![솔루션별 명령](media/solution-commands.PNG "솔루션별 명령")  
 
 ## <a name="create-components-in-a-solution"></a>솔루션에서 구성 요소 만들기
 비관리형 솔루션 또는 기본 솔루션의 경우 **새로 만들기** 명령을 사용하여 다양한 유형의 구성 요소를 만들 수 있습니다. 이렇게 하면 선택한 구성 요소 유형에 따라 다른 만들기 환경으로 이동합니다. 구성 요소 만들기를 마치면 솔루션에 추가됩니다. 
 
> [!div class="mx-imgBorder"]  
> ![솔루션에서 새 구성 요소 만들기](media/solution-new-component.PNG "솔루션에서 새 구성 요소 만들기")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>솔루션에 기존 구성 요소 추가
 
 기본 솔루션이 아닌 비관리형 솔루션을 사용하면 **기존 항목 추가** 명령을 사용하여 솔루션에 아직 없는 구성 요소를 가져옵니다.  
 
> [!div class="mx-imgBorder"]  
> ![솔루션에 기존 구성 요소 추가](media/solution-add-existing-component.PNG "솔루션에 기존 구성 요소 추가")  
  
 관리형 솔루션을 사용하면 특정 명령만 사용할 수 있으므로 다음과 같은 메시지가 표시됩니다. 구성 요소를 사용자 지정하기 위해 생성한 관리되지 않는 다른 솔루션에 추가해야 합니다. 구성 요소는 사용자 지정할 수 없습니다. 자세한 내용은 [관리 속성](solutions-overview.md#managed-properties)을 참조하십시오.

> [!div class="mx-imgBorder"]  
> ![관리형 솔루션](media/managed-solution.PNG "관리형 솔루션")  

 수행하려는 많은 사용자 지정 항목에는 엔터티가 포함됩니다. **엔터티** 필터를 사용하여 어떤 방식으로든 사용자 지정할 수 있는 현재 솔루션의 모든 엔터티 목록을 표시할 수 있습니다. 엔터티로 드릴다운하면 다음 스크린샷에 거래처 엔터티와 같이 표시된 엔터티의 일부인 솔루션 구성 요소를 확인할 수 있습니다. 
   
> [!div class="mx-imgBorder"]  
> ![확장된 거래처 엔터티를 표시하는 데모 솔루션](media/solution-entity-account.png "확장된 거래처 엔터티를 표시하는 데모 솔루션")  

## <a name="classic-solution-explorer"></a>기본 솔루션 탐색기

Power Apps의 왼쪽 탐색 창에서 **솔루션**을 선택한 다음 명령 모음에서 **클래식으로 전환**을 선택하여 클래식 솔루션 탐색기를 볼 수 있습니다. 기본 솔루션 탐색기는 Power Apps의 **설정 > 고급 사용자 지정** 영역을 통해 이전에 사용할 수 있었던 항목입니다. 

## <a name="known-limitations"></a>알려진 제한 사항

솔루션에서 캔버스 앱, 흐름 및 사용자 지정 커넥터를 사용하는 경우 다음 제한 사항이 적용됩니다. 

- 캔버스 앱 트리거 흐름은 솔루션에서 사용할 수 없습니다.
- 캔버스 앱이 관리형 솔루션에 패키징되어 있는 경우 대상 환경에서 편집하여 다시 게시할 수 없습니다. 대상 환경에서 앱을 편집해야 하는 경우 비관리형 솔루션을 사용하십시오. 
- 연결에는 인증 및 동의가 필요하며 대화식 사용자 세션이 필요하므로 솔루션을 통해 전송할 수 없습니다. 솔루션을 가져온 후 앱을 재생하여 연결을 인증하십시오. 솔루션을 가져오기 전에 대상 환경에서 연결을 생성할 수도 있습니다. 
-   Azure Active Directory(AAD) 보안 그룹의 공동 담당자로 공유된 캔버스 앱은 솔루션에 추가할 수 없습니다. 솔루션에 앱을 추가하기 전에 앱의 공유를 해제하십시오.
-   기본 솔루션 탐색기에 캔버스 앱이 표시되지 않습니다. 최신 환경을 사용하십시오.
-   캔버스 앱 액세스(CRUD 및 보안)는 Power Apps에서 전적으로 관리되고 Common Data Service 데이터베이스에서 관리되지 않습니다.
- 캔버스 앱 및 흐름에는 백업, 복원 및 복사와 같은 데이터베이스 작업이 지원되지 않습니다. 이러한 작업으로 인해 캔버스 앱과 흐름이 손상될 수 있습니다.
- 관리형 솔루션을 삭제해도 다른 캔버스 앱 버전으로 롤백되지 않습니다. 대신, 모든 버전의 앱이 삭제됩니다.
- 흐름이 포함된 솔루션을 가져와도 필요한 연결이 자동으로 생성되거나 연결되지는 않습니다. 연결을 수정하려면 흐름을 편집해야 합니다.
  - 관리형 솔루션을 사용하는 경우 비관리형 계층에서 활성 사용자 지정이 생성됩니다. 따라서 흐름에 대한 후속 솔루션 업데이트는 반영되지 않습니다. 
- 솔루션에서 생성된 흐름은 "팀 흐름" 목록에 표시되지 않습니다. 솔루션을 통해 액세스해야 합니다. 
- 버튼 트리거 흐름은 솔루션에서 사용할 수 없습니다.
- Excel과 같은 Microsoft 365 애플리케이션에서 트리거된 흐름은 솔루션에서 사용할 수 없습니다.
- SharePoint에 연결하는 흐름은 솔루션에서 사용할 수 없습니다.
- 솔루션의 흐름은 위임된 인증을 지원하지 않습니다. 예를 들어 흐름에 대한 액세스는 흐름이 만들어진 SharePoint 목록에 대한 액세스 권한을 기반으로 자동 부여되지 않습니다.
- 솔루션 외부에서 생성된 사용자 지정 커넥터는 현재 솔루션에 추가할 수 없습니다.


 솔루션에서 개별 솔루션 구성 요소를 사용자 지정하는 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.  
  
-   엔터티, 엔터티 관계, 필드 및 메시지 사용자 지정에 대한 자세한 내용은 [메타데이터](create-edit-metadata.md)를 참조하십시오.  
  
-   엔터티 항목에 대한 자세한 내용은 [양식](../model-driven-apps/create-design-forms.md)을 참조하십시오.  
  
-   프로세스에 대한 자세한 내용은 [프로세스](../model-driven-apps/guide-staff-through-common-tasks-processes.md)를 참조하십시오.  
  
-   비즈니스 규칙은 [비즈니스 규칙](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)을 참조하십시오.  
