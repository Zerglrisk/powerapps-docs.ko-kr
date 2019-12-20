---
title: Power Apps에서 모델 기반 앱 보기 만들기 또는 편집 | MicrosoftDocs
description: 보기를 만들거나 편집하는 방법 알아보기
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 68d295e6c5426296cf4fb77e794b7c6edbf37021
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875581"
---
# <a name="create-or-edit-a-model-driven-app-view"></a>모델 기반 앱 보기 만들기 또는 편집

<a name="BKMK_CreatingAndEditingViews"></a>   

 이 항목에서는 새 사용자 지정 공용 보기를 만듭니다. 기존 보기를 편집할 수도 있습니다.  
  
### <a name="create-a-new-view"></a>새 보기 만들기  
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

    

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다. 

2.  **데이터**를 확장하고 **엔터티**를 선택하고 **거래처** 엔터티를 선택한 다음 **보기** 탭을 선택합니다. 

3.  도구 모음에서 **보기 추가**를 선택합니다.  

4.  **보기 속성** 대화 상자에서 **25 명 이상의 직원이 있는 거래처**와 같은 **이름**을 제공하고 필요에 따라 보기에 대한 **설명**을 입력한 다음 **확인**을 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![속성 보기](media/view-properties.png)
  
5.  일반 작업 오른쪽 창에서 **열 추가**를 선택하고 **열 추가** 대화 상자에서 **직원 수**를 선택한 다음 **확인**을 선택합니다.  

    > [!div class="mx-imgBorder"] 
    > ![직원 수 열](media/column-no-employees.png)
  
6. 일반 작업 오른쪽 창에서 **필터 조건 편집**을 선택하고 필터 조건 편집 대화 상자에서 **직원 수**를 선택하고 **보다 크거나 같음**을 선택한 다음 **25**를 입력합니다.  

    > [!div class="mx-imgBorder"] 
    > ![필터 조건 편집](media/edit-filter-criteria.png)

7.  **확인**을 선택하여 **필터 조건 편집** 대화 상자를 닫은 다음 보기 편집기에서 **저장 후 닫기**를 선택합니다.  
  
8.  이제 Power Apps 사이트의 **보기** 탭에서 앱에 추가할 수 있도록 보기를 사용할 수 있습니다.
  
### <a name="edit-a-view"></a>보기 편집  
  
1.  Power Apps 사이트의 **보기** 탭에서 **직원 수** 보기를 선택합니다.
  
2.  보기 **이름**을 **애리조나에서 25명 이상의 직원이 있는 경우 직원 수**로 변경하고 **확인**을 선택합니다.  

3.  일반 작업 오른쪽 창에서 **열 추가**를 선택하고 **열 추가** 대화 상자에서 **주소 1: 구/군/시**를 선택한 다음 **확인**을 선택합니다.  

4. 일반 작업 오른쪽 창에서 **필터 조건 편집**을 선택하고 필터 조건 편집 대화 상자에서 두 번째 필터 클로스를 추가합니다. **주소 2: 구/군/시**를 선택하고 **같음**을 선택한 다음 **애리조나**를 입력합니다. 

    > [!div class="mx-imgBorder"] 
    > ![주소 2: 시/도](media/column-address-2-state.png)

5. **확인**을 선택하여 **필터 조건 편집** 대화 상자를 닫은 다음 보기 편집기에서 **저장 후 닫기**를 선택합니다.  
  

## <a name="create-a-new-view-from-an-existing-view"></a>기본 보기에서 새 보기 만들기  
 **저장 후 닫기**를 선택하는 대신 **다른 이름으로 저장**을 선택하고 보기의 새 **이름**과 **설명**을 입력하여 절차에 따라 보기를 편집합니다.  
 
### <a name="next-steps"></a>다음 단계
[열 선택 및 구성](choose-and-configure-columns.md)  
  
[필터 조건 편집](edit-filter-criteria.md)  
  
[정렬 구성](configure-sorting.md)  
