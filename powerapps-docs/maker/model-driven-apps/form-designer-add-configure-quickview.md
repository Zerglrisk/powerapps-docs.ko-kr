---
title: 양식에 빠른 보기 구성 요소 추가 또는 구성 | MicrosoftDocs
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>양식에 빠른 보기 구성 요소 추가 또는 구성  
레코드 세부 사항을 표시하는 기본 양식은 빠른 보기 구성 요소를 사용하여 관련 레코드(조회)의 읽기 전용 세부 정보를 표시할 수 있습니다. 빠른 보기 구성 요소에 의해 표시되는 데이터는 관련 엔터티의 빠른 보기 양식에 의해 정의됩니다. 조회와 같은 관련 레코드가 없으면 빠른 보기 구성 요소가 자동으로 숨겨집니다.

## <a name="add-a-quick-view-component"></a>빠른 보기 구성 요소 추가
다른 구성 요소를 추가할 때와 같은 방법으로 빠른 보기 구성 요소를 추가합니다. 추가 정보: [양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>빠른 보기 구성 요소 구성
양식 디자이너를 사용하여 양식에서 빠른 보기 구성 요소를 사용할 때 다음 속성을 구성할 수 있습니다.


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|영역형   |이름  |설명  |
|---------|---------|---------|
|**표시 옵션** | **레이블** | 사용자에게 표시되는 빠른 보기에 대해 지역화할 수 있는 레이블입니다. <br /><br /> 이 속성은 필수입니다. |
| **표시 옵션** | **이름** |  스크립트에서 참조할 때 사용되는 빠른 보기의 고유 이름입니다. 이름에는 영숫자 문자와 밑줄만 사용할 수 있습니다. <br /> <br />이 속성은 필수입니다. |
| **표시 옵션**  | **레이블 숨기기** |  이 항목을 선택하면 빠른 보기 레이블이 숨겨집니다. |
| **표시 옵션**  | **빠른 보기 양식** |  앱 사용자에게 표시되는 빠른 보기 양식 목록입니다. <br /><br />빠른 보기 양식 목록을 구성하려면 <br /><br /> **양식 선택...** 을 선택한 다음 **조회** 드롭다운 메뉴에서 빠른 보기 양식을 표시할 조회 필드를 선택하십시오. <br /><br />**조회** 드롭다운에서 선택한 조회 필드에 따라 하나 이상의 엔터티에 대한 빠른 보기 양식을 선택할 수 있는 드롭다운이 표시됩니다. |

## <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성](create-and-edit-forms.md)  
[양식의 필드 추가, 구성, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)  
[양식의 섹션 추가, 구성, 이동 또는 삭제](add-move-or-delete-sections-on-form.md)  
[양식의 탭 추가, 구성, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식 디자이너에서 머리글 속성 구성](form-designer-header-properties.md)  
[양식에 하위 표 구성 요소 추가 또는 구성](form-designer-add-configure-subgrid.md)  
[양식에서 조회 구성 요소 구성](form-designer-add-configure-lookup.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)  
