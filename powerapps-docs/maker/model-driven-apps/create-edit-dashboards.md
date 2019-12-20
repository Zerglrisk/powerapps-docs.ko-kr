---
title: 모델 기반 앱 대시보드 만들기 또는 편집 | MicrosoftDocs
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81943d73ac8c6189e62d25af4ff38b993182c269
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875493"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>모델 기반 앱 대시보드 만들기 또는 편집

시스템 대시보드 및 사용자 대시보드의 두 가지 대시보드 유형이 있습니다. 앱 사용자는 권한이 있는 앱 영역에만 표시되는 대시보드를 만들 수 있습니다. 관리자 또는 사용자 지정자는 게시되었을 때 모든 앱 사용자가 볼 수 있는 시스템 대시보드를 만들거나 사용자 지정할 수 있습니다. 사용자는 자신의 사용자 대시보드를 기본 대시보드로 설정하고 시스템 대시보드 재정의를 선택할 수 있습니다. 이 항목은 시스템 대시보드를 중점적으로 설명합니다.  
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-dashboard"></a>새 대시보드 만들기  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.   
  
2. **데이터**를 확장하고 **엔터티**를 선택하고 **거래처** 엔터티와 같이 대시보드의 기반으로 사용할 엔터티를 선택한 다음 **대시보드** 탭을 선택합니다. 

3. 도구 모음에서 **대시보드 추가**를 선택한 다음 2, 3 또는 4열 레이아웃을 선택합니다.  
  
4.  **대시보드: 새로 만들기** 대화 상자에서 대시보드 이름을 입력합니다.  
  
5.  구성 요소 영역 중 하나를 선택한 다음 차트 또는 목록의 아이콘을 선택합니다.  
  
     대시보드에는 최대 6개의 구성 요소가 있을 수 있습니다.  
  
6.  예를 들어, 차트를 추가하려면 **구성 요소 추가** 대화 상자에서 **레코드 유형**, **보기** 및 **차트**의 값을 선택한 다음 **추가**를 선택하여 대시보드에 차트를 추가합니다.  
  
7.  대시보드에 구성 요소 추가를 완료했으면 **저장**을 선택한 다음 **게시**를 선택합니다.  
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>기존 대시보드 편집  
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.    
  
2. **데이터**를 확장하고 **엔터티**를 선택하고 **거래처** 엔터티와 같이 대시보드의 기반으로 사용할 엔터티를 선택한 다음 **대시보드** 탭을 선택합니다.  

3. 대시보드를 열고 구성 요소 영역 중 하나를 선택한 다음 도구 모음에서 **구성 요소 편집**을 선택합니다.  
  
4.  **속성 설정** 대화 상자에서 엔터티 변경, 기본 보기, 차트 선택기 추가 또는 모바일 앱에서 대시보드를 사용할 수 있도록 하는 것과 같은 차트 또는 목록에 대한 변경 작업을 수행합니다. 완료되면 **설정**을 선택합니다.  
  
     대시보드 구성 요소 속성을 설정하는 방법에 대한 자세한 내용은 [대시보드에 포함된 차트 또는 목록의 속성 설정](set-properties-chart-list-included-dashboard.md)을 참조 하십시오.  
  
4.  변경이 완료되면 저장한 다음 게시합니다.  
  
수행할 수 있는 추가 시스템 대시보드 작업은 다음과 같습니다.  
  
-   대시보드에서 목록 또는 차트 제거  

-   대시보드에 목록 또는 차트 추가  

-   기본 대시보드 설정  

-   보안 역할을 사용하여 대시보드를 특정 역할만 볼 수 있도록 만들기    

## <a name="next-steps"></a>다음 단계  
[대시보드에 포함된 차트 또는 목록의 속성 설정](set-properties-chart-list-included-dashboard.md)
