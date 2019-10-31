---
title: 양식에 하위 표 구성 요소 추가 또는 구성 | MicrosoftDocs
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



<!-- note from editor: I recommend removing the hyphen from "sub-grid" based on the style guide entry for sub: https://styleguides.azurewebsites.net/Styleguide/Read?id=2700&topicid=28872. I didn't change it here because I don't know how wide an impact that might have. -->


# <a name="add-and-configure-a-sub-grid-component-on-a-form"></a>양식에 하위 표 구성 요소 추가 또는 구성  
레코드의 세부 사항을 표시하는 양식은 하위 표 구성 요소를 사용하여 관련 또는 관련되지 않은 레코드 목록을 테이블 형식으로 표시할 수 있습니다. 제조업체는 양식 디자이너를 사용하여 하위 표 구성 요소를 추가하고 구성할 수 있습니다.

## <a name="add-a-sub-grid-component"></a>하위 표 구성 요소 추가
다른 구성 요소를 추가할 때와 같은 방법으로 하위 표 구성 요소를 추가합니다. 추가 정보: [양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-sub-grid-component"></a>하위 표 구성 요소 구성
양식 디자이너를 사용하여 양식에서 하위 표 구성 요소를 사용할 때 다음 속성을 구성할 수 있습니다.


|영역형   |이름  |설명  |
|---------|---------|---------|
| **표시 옵션** | **레이블** | 사용자에게 표시되는 하위 표에 대해 지역화할 수 있는 레이블입니다. <br /><br />이 속성은 필수입니다.|
| **표시 옵션** |  **이름** |  스크립트에서 참조할 때 사용되는 하위 표의 고유 이름입니다. 이름에는 영숫자 문자와 밑줄만 사용할 수 있습니다. <br /><br />이 속성은 필수입니다. |
| **표시 옵션** | **휴대폰에서 숨기기** |  구성 요소 를 숨겨 휴대폰 화면에서 양식의 압축된 버전을 렌더링할 수 있습니다. |
| **표시 옵션** | **관련 레코드 표시** |  선택한 경우 하위 표는 양식에 표시되는 현재 레코드와 관련된 레코드만 표시합니다. <br /><br />**엔터티** 드롭다운 목록은 현재 엔터티와 관련된 엔터티만 나열하도록 필터링됩니다. |
| **표시 옵션** | **엔터티** |  하위 표에 레코드를 표시할 엔터티입니다. <br /><br />**관련 레코드 표시**를 선택하면 엔터티 목록이 필터링되어 현재 엔터티와 관련된 엔터티만 표시됩니다. 엔터티 이름 외에도 조회 필드 이름도 괄호 안에 표시됩니다. |
| **표시 옵션** | **기본 보기** |  하위 표에 레코드 목록을 가져와 표시하는 데 사용되는 **엔터티** 속성에서 선택된 엔터티 보기입니다. |
| **표시 옵션** | **사용자가 보기를 변경하도록 허용** |  선택된 경우 앱 사용자가 **기본 보기**에서 **엔터티** 속성에서 선택된 엔터티의 다른 보기로 변경할 수 있습니다. |
| **표시 옵션** | **모든 보기 표시** |  선택된 경우 앱 사용자가 **기본 보기**에서 **엔터티** 속성에서 선택된 엔터티의 모든 다른 보기로 변경할 수 있습니다. <br /><br />이 속성은 **사용자가 보기를 변경하도록 허용**이 선택되어 있을 때만 사용할 수 있습니다. |
| **표시 옵션** | **선택된 보기** |  앱 사용자가 **기본 보기**에서 변경할 수 있는 **엔터티** 속성에서 선택된 엔터티 보기 목록입니다. <br /><br />이 속성은 **사용자가 보기를 변경하도록 허용**이 선택되어 있고 **모든 보기 표시**가 해제되어 있을 때만 사용할 수 있습니다. |

## <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성](create-and-edit-forms.md)  
[양식의 필드 추가, 구성, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)  
[양식의 섹션 추가, 구성, 이동 또는 삭제](add-move-or-delete-sections-on-form.md)  
[양식의 탭 추가, 구성, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식 디자이너에서 머리글 속성 구성](form-designer-header-properties.md)  
[양식에 빠른 보기 구성 요소 추가 또는 구성](form-designer-add-configure-quickview.md)  
[양식에서 조회 구성 요소 구성](form-designer-add-configure-lookup.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)  
