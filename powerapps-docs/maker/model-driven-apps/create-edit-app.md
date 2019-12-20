---
title: Power Apps의 앱 디자이너를 사용하여 모델 기반 앱 만들기 또는 편집 | MicrosoftDocs
description: 앱 디자이너를 사용하여 앱을 만들거나 편집하는 방법 알아보기
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 2a44229e-44f0-4c4e-ba21-a476210d0a12
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 19
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ef8fa8e20afd7d0e4ad1593ae169a132246d3992
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875431"
---
# <a name="create-a-model-driven-app-by-using-the-app-designer"></a>앱 디자이너를 사용하여 모델 기반 앱 만들기

이 항목에서는 타일 기반 앱 디자이너를 사용하여 모델 기반 앱을 만들고 편집하는 방법에 대한 기본 사항을 배웁니다.

## <a name="prerequisites"></a>필수 구성 요소
앱 만들기를 시작하기 전에 다음 필수 구성 요소를 확인합니다.
- Power Apps 환경. 추가 정보: [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)
- 시스템 관리자 또는 시스템 사용자 지정자 보안 역할입니다. 추가 정보: [미리 정의된 보안 역할 정보](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app#about-predefined-security-roles)
 
<a name="createApp"></a>   
## <a name="create-an-app"></a>앱 만들기  

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **홈** 페이지에서 모델 기반 앱의 **새 모델 기반 앱** 옵션을 선택합니다.  

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다. 

2. **새 앱 만들기** 페이지에서 다음 정보를 입력합니다. 

    - **이름**: 앱의 이름을 입력합니다.  
  
    - **고유 이름**: 고유 이름은 지정한 앱 이름을 기반으로 자동 입력됩니다. 앞에 게시자 접두사가 붙습니다. 고유 이름의 편집할 수 있는 일부를 변경할 수 있습니다. 고유 이름에는 영문자 및 숫자만 포함할 수 있습니다.  
  
        > [!NOTE]
        >  게시자 접두사는 게시자를 가지고 있는 솔루션에 대해 만든 엔터티나 필드에 추가되는 텍스트입니다.   
  
    - **설명**: 앱의 개요와 기능에 대한 간단한 설명을 입력합니다.  
  
    - **아이콘**: 기본적으로 **기본 앱 사용** 미리 보기 확인란이 체크되어 있습니다. 응용 프로그램에 대한 다른 웹 리소스 아이콘을 선택하려면 확인란의 선택을 취소하고 드롭다운 목록에서 아이콘을 선택합니다. 이 아이콘은 앱의 미리 보기 타일에 표시됩니다.  
  
    - **기존 솔루션을 사용하여 앱 만들기**: 이 옵션을 선택하면 설치된 솔루션 목록에서 앱이 만들어집니다. 이 옵션을 선택하면 머리글에서 **완료**가 **다음**으로 전환됩니다. **다음**을 선택하면 **기존 솔루션에서 앱 만들기** 페이지가 열립니다. **솔루션 선택** 드롭다운 목록에서 앱을 만들고자 하는 솔루션을 선택합니다. 선택한 솔루션에 대해 사이트 맵을 사용할 수 있는 경우에는 **사이트 맵 선택** 드롭다운 목록이 표시됩니다. 사이트 맵을 선택한 후 **완료**를 선택합니다.

      > [!NOTE]
      > 사이트 맵을 추가할 때 **기본 솔루션**을 선택하면 해당 사이트 맵과 연결된 구성 요소가 앱에 자동으로 추가됩니다.  

      ![기존 솔루션을 사용하여 앱 페이지 만들기](media/use-existing-solution-to-create-the-app.png "기존 솔루션을 사용하여 앱 만들기") 

    - **시작 페이지 선택**: 이 옵션을 사용하여 조직에서 사용할 수 있는 웹 리소스를 선택할 수 있습니다. 사용자가 만든 시작 페이지에는 비디오 링크, 업그레이드 지침 또는 시작 정보 등의 유용한 정보가 포함될 수 있습니다. 시작 페이지는 앱을 열 때 표시됩니다. 사용자는 다음에 앱이 시작될 때 표시되지 않도록 페이지를 비활성화하기 위해 시작 페이지에서 **다음에 이 시작 화면을 표시 안 함**을 선택할 수 있습니다. **다음에 이 시작 화면을 표시 안 함** 옵션은 사용자 수준 설정이므로 관리자나 앱 제작자가 제어할 수 없습니다. 시작 페이지로 사용할 수 있는 HTML 파일과 같은 웹 리소스를 만드는 방법에 대한 자세한 내용은 [웹 리소스를 만들고 편집하여 웹 응용 프로그램 확장](create-edit-web-resources.md)을 참조하십시오.  
      
    앱 속성을 나중에 편집하려면 앱 디자이너의 **속성** 탭으로 이동합니다. 추가 정보: [앱 속성 관리](manage-app-properties.md)  
  
     > [!NOTE]
     >  **속성** 탭의 고유 이름 및 앱 URL 접미사는 변경할 수 없습니다.  
  
3. **완료**를 선택하거나 **기존 솔루션을 사용하여 앱 만들기**를 선택한 경우 **다음**을 선택하여 조직에서 가져온 사용 가능한 솔루션에서 선택합니다.  
  
    새로운 앱이 생성되고 임시 상태를 나타냅니다. 새 앱을 위한 앱 디자이너 캔버스를 볼 수 있습니다. 여기에서 엔터티, 보기 및 대시보드와 같은 구성 요소를 추가하여 앱을 유용하게 만들 수 있습니다. 추가 정보: [앱 구성 요소 추가 또는 편집](add-edit-app-components.md)  
   
<a name="editApp"></a>   
## <a name="edit-an-app"></a>앱 편집  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

> [!IMPORTANT]
> "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다. 

2. 왼쪽 탐색 창에서 **앱**을 선택하고 모델 기반 앱을 선택한 다음 도구 모음에서 **편집**을 선택합니다.   

3. 앱 디자이너에서 필요에 따라 앱에 구성 요소를 추가하거나 편집합니다. 추가 정보: [앱 구성 요소 추가 또는 편집](add-edit-app-components.md)  
 
  
### <a name="next-steps"></a>다음 단계  
 [앱 구성 요소 추가 또는 편집](add-edit-app-components.md)   


