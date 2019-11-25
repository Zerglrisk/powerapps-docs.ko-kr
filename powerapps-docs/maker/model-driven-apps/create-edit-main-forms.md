---
title: PowerApps에서 모델 기반 앱 기본 양식 만들기 또는 편집 | MicrosoftDocs
description: 기본 양식을 만들거나 편집하는 방법 알아보기
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
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 52b80ac0809bbcfe0b008e6fc31fd8b97b894959
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759211"
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>엔터티의 모델 기반 앱 기본 양식 만들기 또는 편집 

이 항목에서는 엔터티의 기본 양식을 만들거나 편집하는 방법에 대해 설명합니다.

엔터티의 새 양식을 만들 때 양식 유형은 기본입니다. 열리는 새 양식은 정보라는 이름의 양식과 같습니다. 양식과 연결된 필드, 섹션, 탭, 탐색 및 속성을 추가하거나 편집한 후 양식을 저장할 수 있습니다.

각 기본 양식은 하나 이상의 탭으로 구성됩니다. 각 탭은 섹션을 하나 이상 포함할 수 있습니다. 각 섹션에는 필드 또는 IFRAME이 하나 이상 포함됩니다. 기존 양식을 기반으로 새 양식을 만들려면 양식을 복제합니다. 

이 작업을 수행하려면 시스템 관리자 또는 시스템 사용자 지정자 보안 역할이나 이와 동급의 권한이 있는지 확인하십시오.

## <a name="how-to-create-or-edit-a-main-form"></a>기본 양식을 만들거나 편집하는 방법
  
1.   [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.


> [!IMPORTANT]
> "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.   
  
2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 

3. 새 기본 양식을 만들려면 도구 모음에서 **양식 추가** > **기본 양식**을 선택 합니다.  
    \-또는- 기존 기본 양식을 편집하려면 **유형**이 **기본**인 양식을 선택합니다.
  
3.  필요에 따라 다음 방식으로 양식 디자인을 변경합니다.
    -   양식에 탭 추가
    -   양식에 섹션 추가
    -   양식에 필드 추가
    -   양식 IFRAME 추가 또는 편집
    -   양식에 하위 표 추가 또는 편집
    -   양식 웹 리소스 추가 또는 편집
    -   관련 엔터티의 양식 탐색 추가 또는 편집
    -   양식 머리글 및 바닥글 편집
    -   탭 섹션 필드 또는 IFRAME 제거
    -   양식 도우미 사용 또는 사용 안 함
    
4.  필요에 따라 양식에 포함되는 요소의 속성들을 편집합니다.
    -   양식 속성 편집
    -   양식 필드 속성 편집
    -   편집 탭 속성
    -   섹션 속성 편집

5.  필요에 따라 이벤트 스크립트를 추가합니다. 

6.  양식을 볼 수 있도록 보안 역할을 결정합니다. 추가 정보:  [양식에 보안 역할 할당](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)

7.  기본 양식이 표시되는 방식과 이벤트가 작동하는 방식 미리 보기:
    - **홈** 탭에서 **미리 보기**를 선택한 후**양식 생성**, **양식 업데이트**,또는 **읽기 전용 양식**을 선택합니다.
    - 미리 보기 양식을 닫으려면 **파일** 메뉴에서 **닫기**를 선택합니다.

8.  양식 편집이 끝났으면 **다른 이름으로 저장**을 선택하고 양식 이름을 입력한 다음 **확인**을 선택합니다.

9.  사용자 지정 작업을 완료했으면 사용자 지정 항목을 게시합니다.
    -   현재 편집 중인 구성 요소의 사용자 지정 항목만 게시하려면 **구성 요소**에서 작업 중이던 엔터티를 클릭한 후 **게시**를 클릭합니다.
    -   게시되지 않은 모든 구성 요소의 사용자 지정 항목을 한번에 게시하려면 **구성 요소**에서 **엔터티**를 클릭한 후 명령 모음에서 **모든 사용자 지정 항목 게시**를 클릭합니다.
    
 
### <a name="next-steps"></a>다음 단계  
[양식 편집기 사용자 인터페이스 개요](form-editor-user-interface-legacy.md)
 
