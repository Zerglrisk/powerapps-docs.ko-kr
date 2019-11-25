---
title: PowerApps에서 모델 기반 앱 보기의 열 선택 및 구성 | MicrosoftDocs
description: 앱에 대한 보기 선택 및 구성 방법 알아보기
keywords: ''
ms.date: 11/27/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 31bfcf18-58c3-491c-91b5-f9b0f5424852
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d9f34be645a8e3dee1283f064e5aeda6a9d59e9a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754614"
---
# <a name="choose-and-configure-columns-in-model-driven-app-views"></a>모델 기반 앱 보기의 열 선택 및 구성

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 필터 조건에 따라 PowerApps 보기에 표시되는 열은 보기에 제공되는 값에 매우 중요합니다. 이 항목에서는 다음 작업을 수행하여 보기를 만들거나 편집합니다.  

-   [보기 편집기 열기](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [열 추가](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [열 제거](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [열 너비 변경](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [열 이동](choose-and-configure-columns.md#BKMK_MoveAColumns)  
    
  > [!IMPORTANT]
  > 디자이너 보기의 최신 버전은 현재 미리 보기 상태입니다. 열의 상태 표시를 활성화 또는 비활성화하고 찾기 열을 추가하는 등의 일부 기능은 아직 지원되지 않습니다. 이러한 작업을 수행 하려면 [디자이너 보기에서 보기를 엽니다](/dynamics365/customer-engagement/customize/create-and-edit-views#open-the-classic-view-designer).
  >  -   [열의 상태 표시 활성화 또는 비활성화](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_EnableOrDisablePresence)  
  >
  >  -   [찾기 열 추가](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_AddFindColumns) 



### <a name="open-the-view-editor"></a>보기 편집기 열기

1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **보기** 탭을 선택합니다. 

    > [!div class="mx-imgBorder"] 
    > ![ 보기](media/available-views.png)

3. 기존 보기를 선택하여 열거나 도구 모음에서 **보기 추가**를 선택합니다. 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>열 추가  
 현재 엔터티 또는 현재 엔터티와 1:N 엔터티 관계를 가진 관련 엔터티에서 열을 포함할 수 있습니다.  
  
 예를 들어 사용자 담당 엔터티의 담당자를 열에 표시할 수 있습니다. 현재 엔터티의 **담당자** 필드를 선택하여 담당자 이름을 표시할 수 있습니다. 그러면 담당자의 **사용자** 레코드를 열 수 있는 링크로 표시됩니다.  
  
 레코드 담당자의 전화 번호를 표시하려면 **레코드 종류** 드롭다운에서 **담당 사용자(사용자)** 를 선택한 후 **기본 전화** 필드를 선택해야 합니다.  
  
#### <a name="add-columns-to-views"></a>보기에 열 추가  
  
1.  보기를 만들고 편집하는 동안 **필드** 패널이 열려있는지 확인합니다. 그렇지 않은 경우 도구 모음에서 **필드 추가**를 선택합니다. 

    > [!div class="mx-imgBorder"] 
    > ![편집기 보기 열 추가](media/fields-drawer-view-designer.png)

2.  디자이너 보기에 추가할 필드를 선택합니다. 그러면 보기의 오른쪽에 열로 필드가 추가됩니다.

3.  관련 엔터티 및 해당 필드를 보려면 **관련** 탭을 선택합니다.
  
 열을 추가하면 보기 너비를 늘입니다. 보기 너비가 페이지에 표시할 수 있는 공간보다 크면 가로 스크롤 막대로 스크롤하고 숨겨진 열을 볼 수 있습니다.  
  
> [!TIP]
>  보기가 특정 필드의 데이터를 필터링하여 특정 값을 가진 레코드만 표시할 경우 보기에 해당 열을 포함하지 마십시오. 예를 들어 활성 레코드만 표시할 경우 보기에 상태 열을 포함하지 마십시오. 대신 보기에 표시된 모든 레코드가 활성 상태임을 나타내도록 보기 이름을 지정합니다.  
  
> [!NOTE]
>  업데이트된 엔터티에 대한 조회 보기에 열을 추가하면 처음 세 열만 표시됩니다.  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>열 제거  
  
1.  제거할 열의 머리글을 선택합니다.  
  
2.  드롭다운에서 **제거**를 선택합니다.  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>열 너비 변경  
  
1.  보기에서 열 사이의 영역을 커서로 가리킵니다.  
  
2.  선이 나타나고 커서가 양면 화살표가 됩니다.  
  
3.  열을 적절한 너비로 끕니다.  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>열 이동  
  
열 머리글을 클릭하여 올바른 위치로 끕니다.
  
> [!TIP]
>   이동하려는 열의 머리글을 선택하고 드롭다운 메뉴에서 **오른쪽으로 이동** 또는 **왼쪽으로 이동**을 선택할 수도 있습니다.  


  
## <a name="next-steps"></a>다음 단계
[보기 만들기 또는 편집](create-edit-views.md)
