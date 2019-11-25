---
title: PowerApps에서 모델 기반 앱 빠른 보기 양식 만들기 또는 편집 | MicrosoftDocs
description: 빠른 보기 양식을 만들거나 편집하는 방법 알아보기
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
- powerapps
author: Mattp123
ms.assetid: 9b101734-cc11-4d05-bd45-eb611eae9931
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0384b233ddd9df0f88019df6064f5a99ef8af0bd
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759123"
---
# <a name="create-a-model-driven-app-quick-view-form-to-view-information-about-a-related-entity"></a>모델 기반 앱 빠른 보기 양식을 만들어 관련 엔터티에 대한 정보 보기

이 항목에서는 빠른 보기 양식을 만드는 방법과 기본 양식에 빠른 보기 컨트롤을 추가하는 방법에 대해 설명합니다. 

빠른 보기 양식은 빠른 보기 컨트롤로 다른 양식에 추가할 수 있습니다. 이 양식은 다른 엔터티 레코드에 대해 양식 내에서 관련 엔터티 레코드에 대한 정보를 표시하는 템플릿을 제공합니다. 즉, 앱 사용자가 작업에 필요한 정보를 보기 위해 다른 레코드로 이동할 필요가 없습니다.  
  
 빠른 보기 컨트롤은 양식에 포함되어 있는 조회 필드와 관련 있습니다. 조회 필드 값이 설정되어 있지 않으면 빠른 보기 컨트롤을 표시할 수 없습니다. 빠른 보기 컨트롤의 데이터는 편집할 수 없고 빠른 보기 양식은 양식 스크립트를 지원하지 않습니다.  
  
 빠른 보기 양식은 양식의 빠른 보기 컨트롤을 사용하여 표시되므로 머리글, 바닥글 또는 탐색 영역이 포함되어 있지 않습니다. 보안 역할은 빠른 보기 양식에 할당할 수 없으므로 활성화하거나 비활성화할 수 없습니다.  
  
<a name="BKMK_CreateQFV"></a>   
## <a name="create-a-quick-view-form"></a>빠른 보기 양식 만들기  
 다른 양식을 만드는 방식과 유사한 방식으로 양식 편집기를 사용하여 빠른 보기 양식을 만듭니다. 빠른 보기 양식은 읽기 전용입니다. 이를 사용하여 읽기 전용 양식을 만듭니다.  
  
1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  


    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.     
  
2. **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 
  
3. 도구 모음에서 **양식 추가** > **빠른 보기 양식**을 선택합니다.  
  
4. 양식 편집기 도구 모음에서 **양식 속성**을 선택합니다.  
  
5. **양식 속성** 대화 상자에서 이 빠른 보기 양식을 다른 양식과 구분하는 **양식 이름**과 **설명**을 입력합니다. **확인**을 선택하여 **양식 속성** 대화 상자를 닫습니다.  
  
6. 양식 디자이너에서 **필드 탐색기**로부터 필드를 양식의 섹션으로 끌어옵니다. 
  
    > [!IMPORTANT]
    >  필드를 추가하고 **필드 요구 사항** > **업무상 필수**를 선택한 후 저장하면 필드를 삭제할 수 없습니다.  
  
7. 양식을 저장하고 양식 편집기를 닫으려면 **저장**을 선택합니다.  

8. 응용 프로그램에서 새 양식을 보려면 **게시**를 선택합니다.
  
<a name="BKMK_EditQVF"></a>   
## <a name="edit-a-quick-view-form"></a>빠른 보기 양식 편집  
 빠른 보기 양식은 양식 섹션 내에서 보도록 설계되었으므로 간소화된 레이아웃을 사용합니다. 하나의 단일 열 탭만 사용할 수 있습니다. 하나의 열 섹션, 필드, 하위 표 및 공백만 추가로 추가할 수 있습니다.   
  
> [!NOTE]
>  **업무상 필수** 필드는 삭제할 수 없습니다. 필드를 삭제하려고 하면 "제거하려는 필드는 시스템 필수 또는 업무상 필수 필드입니다."라는 메시지가 표시됩니다. 이 양식의 필드를 원하지 않을 경우 전체 양식을 삭제한 후 다시 만들어야 합니다.  
  
 빠른 보기 양식을 편집하면 응용 프로그램에서 표시되기 전에 변경 내용을 게시해야 합니다.  
  
<a name="BKMK_AddQVF"></a>   
## <a name="add-a-quick-view-control-to-a-main-form"></a>기본 양식에 빠른 보기 컨트롤 추가  
 빠른 보기 양식은 빠른 보기 양식의 엔터티를 대상으로 하는 조회 필드가 있는 기본 양식에만 추가할 수 있습니다.  
  
1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.     
  
2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.  

3. **유형**이 **기본**인 양식을 선택합니다.

4. 양식 디자이너에서 **삽입** 탭을 선택한 다음 도구 모음에서 **빠른 보기 양식**을 선택합니다.  
  
5.  **빠른 보기 컨트롤 속성** 대화 상자에서 빠른 보기 컨트롤의 속성(예: **이름**, **레이블**및 **빠른 보기 양식**)을 설정합니다. 추가 정보: [빠른 보기 컨트롤 속성](quick-view-control-properties-legacy.md)  
  
6.  **확인**을 선택하여 **빠른 보기 컨트롤 속성** 대화 상자를 닫습니다.  
  
7.  **홈** 탭을 선택한 다음 **게시**를 선택하여 양식에 빠른 보기 컨트롤을 표시합니다.  
  
## <a name="next-steps"></a>다음 단계   
 [양식 만들기 및 디자인](create-design-forms.md)   
 [빨리 만들기 양식 만들기 또는 편집](create-edit-quick-create-forms.md)
