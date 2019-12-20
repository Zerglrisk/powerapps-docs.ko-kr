---
title: Power Apps의 관련 엔터티에 대한 탐색에서 모델 기반 앱 추가 | MicrosoftDocs
description: 관련 엔터티의 양식 탐색을 추가하는 방법 알아보기
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9751a917dc553355c89aa2a42865ad69bfee5c10
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874920"
---
# <a name="add-model-driven-app-form-navigation-for-related-entities"></a>관련 엔터티에 대한 탐색에서 모델 기반 앱 추가

이 항목에서는 관련 엔터티에 링크를 추가하는 데 사용되는 양식 탐색 창을 사용할 수 있습니다. 앱 사용자가 레코드에서 이러한 링크 중 하나를 클릭하면 엔터티의 관련 보기가 표시됩니다.   
  
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

  
    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다. 

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 
  
3.  목록에서 유형 **기본** 유형의 양식을 열어 편집합니다.  
  
4.  관련 엔터티에 링크를 추가하려면 **홈**탭의 **선택** 그룹에서 **탐색**을 선택합니다.  
  
     그러면 양식 편집기의 오른쪽에 **관계 탐색기** 창이 표시됩니다.  
  
5.  **관계 탐색기** 창의 **필터** 목록에서 다음 옵션 중 하나를 선택합니다.  
  
    - **사용 가능한 관계**. 양식이 연결된 엔터티에 연결할 수 있는 모든 엔터티를 나열합니다.  
  
    - **1:N 관계**. 양식이 연결된 엔터티에 1:N 관계로 연결할 수 있는 엔터티를 나열합니다.  
  
    - **N:N_Relationships**. 양식이 연결된 엔터티에 N:N 관계로 연결할 수 있는 엔터티를 나열합니다.  
  
    > [!NOTE]
    >  **관계 탐색기** 창에 표시되는 관련 엔터티가 없으면 이 양식에서 관련 엔터티에 대한 링크를 만들 수 없습니다.  
  
6.  연결할 관련 엔터티를 선택하고 탐색 창으로 끌어 표시할 위치에 놓습니다.  
  
    > [!TIP]
    >  **관계 탐색기** 창에서 **새 1:N** 또는 **새 N:N**을 선택하여 새 관계를 만들 수도 있습니다.   
  
7. 이 링크 또는 다른 관련 엔터티 링크의 속성을 편집하려면 탐색 창에서 해당 링크를 선택한 다음 **홈** 탭에서 **속성 변경**을 선택합니다.  
  
8. **관계 속성** 대화 상자의 **표시** 탭에서 새 표시 레이블을 입력합니다.  
  
9. **이름** 탭에서 **편집**을 선택하여 관계 레코드에 연결된 정보를 보거나 편집할 수 있습니다.  
  
10. **확인**을 선택합니다.  
  
11. 미리 보기를 통해 기본 양식이 어떻게 표시되고 이벤트가 어떻게 작동하는지 확인할 수 있습니다.  
  
    1.  **읽기 전용 양식** 탭에서 **미리 보기**를 선택하고 **양식 만들기**, **양식 업데이트** 또는 **홈**을 선택합니다.  
  
    2.  **미리 보기** 양식을 닫으려면 **파일** 메뉴에서 **닫기**를 선택합니다.  
  
12. 양식 편집이 끝났으면 **저장 후 닫기**를 선택하여 양식을 닫습니다.  
  
13. 사용자 지정 작업을 완료했으면 사용자 지정 항목을 게시합니다.  
  
    -   현재 편집 중인 구성 요소의 사용자 지정 항목만 게시하려면 탐색 창에서 작업 중이던 엔터티를 선택한 후 **게시**를 선택합니다.  
  
    -   게시되지 않은 모든 구성 요소의 사용자 지정 항목을 한번에 게시하려면 탐색 창에서 **엔터티**를 선택한 후 명령 도구 모음에서 **모든 사용자 지정 항목 게시**를 선택합니다.  
  
> [!NOTE]
> 솔루션 설치 또는 사용자 지정 항목 게시 작업은 일반적인 시스템 작업과 충돌할 수 있습니다. 사용자에게 가장 지장을 덜 줄 때 솔루션을 가져오도록 예약하는 것이 좋습니다.
  
## <a name="next-steps"></a>다음 단계  
 [Common Data Service용 엔터티 관계 만들기 및 편집](../common-data-service/create-edit-entity-relationships.md)
