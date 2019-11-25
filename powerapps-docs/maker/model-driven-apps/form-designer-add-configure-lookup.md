---
title: 양식에서 조회 구성 요소 구성 | MicrosoftDocs
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
ms.openlocfilehash: 8ba09c46a46d0a4d40891419e1f6eb787f75f096
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703914"
---
# <a name="configure-a-lookup-component-on-a-form"></a>양식에서 조회 구성 요소 구성  
조회 필드를 사용하여 다른 엔터티의 레코드에 연결할 수 있습니다. 조회 필드가 양식에 추가될 때 조회 구성 요소가 자동으로 사용됩니다. 제조업체는 양식 디자이너를 사용하여 조회 구성 요소를 구성할 수 있습니다.

## <a name="configure-a-lookup-component"></a>조회 구성 요소 구성
양식 디자이너를 사용하여 양식의 조회 구성 요소를 사용할 때 구성하는 데 사용할 수 있는 속성이 있습니다.


<!--from editor: "Drop-down" should only be an adjective. In the following table, is it a list? A menu? -->


|영역형  |이름  |설명  |
|---------|---------|---------|
| **표시 옵션** | **엔터티** |  조회 필드가 연결되는 관련 엔터티입니다. |
| **표시 옵션** | **기본 보기** |  앱 사용자가 조회 드롭다운에서 선택할 수 있는 레코드 목록을 가져와 표시하는 데 사용할 수 있는 **엔터티** 속성에서 선택된 엔터티 보기입니다. |
| **표시 옵션** | **사용자가 보기를 변경하도록 허용** |  선택된 경우 앱 사용자가 **기본 보기**에서 **엔터티** 속성에서 선택된 엔터티의 다른 보기로 변경할 수 있습니다. |
| **표시 옵션** | **모든 보기 표시** |  선택된 경우 앱 사용자가 **기본 보기**에서 **엔터티** 속성에서 선택된 엔터티의 모든 다른 보기로 변경할 수 있습니다. <br /><br />이 속성은 **사용자가 보기를 변경하도록 허용**이 선택되어 있을 때만 사용할 수 있습니다. |
| **표시 옵션** | **선택된 보기** |  앱 사용자가 **기본 보기**에서 변경할 수 있는 **엔터티** 속성에서 선택된 엔터티 보기 목록입니다. <br /><br />이 속성은 **사용자가 보기를 변경하도록 허용**이 선택되어 있고 **모든 보기 표시**가 선택되어 있지 않을 때만 사용할 수 있습니다. |

## <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성](create-and-edit-forms.md)  
[양식의 필드 추가, 구성, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)  
[양식의 섹션 추가, 구성, 이동 또는 삭제](add-move-or-delete-sections-on-form.md)  
[양식의 탭 추가, 구성, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식 디자이너에서 머리글 속성 구성](form-designer-header-properties.md)  
[양식에 하위 표 구성 요소 추가 또는 구성](form-designer-add-configure-subgrid.md)  
[양식에 빠른 보기 구성 요소 추가 또는 구성](form-designer-add-configure-quickview.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)  
