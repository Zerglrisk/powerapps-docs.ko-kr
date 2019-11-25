---
title: 모델 기반 양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성 | MicrosoftDocs
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
ms.openlocfilehash: c357649ba68e6bce1b9df51d9601507c337afd31
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752470"
---
# <a name="create-edit-or-configure-forms-using-the-form-designer"></a>양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성 
새 양식 디자이너를 사용하여 모델 기반 앱에 대한 양식을 만들고, 편집하거나, 구성합니다. 

> [!IMPORTANT]
> 새 모델 기반 양식 디자이너는 현재 카드 양식 편집을 지원하지 않습니다. 추가 정보: [양식 유형](types-forms.md)

## <a name="create-a-form"></a>양식 만들기 
1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
2. 왼쪽 탐색 창에서 **데이터**를 확장하고 **엔터티**를 선택합니다. 
3. 거래처 엔터티 같은 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 
4. **양식 추가**를 선택하고 다음 중 하나를 선택합니다.
    - **기본 양식**  
    새 양식의 내용은 기존 기본 양식 정의를 사용하여 입력됩니다. 여러 개의 기본 양식이 존재하는 경우 양식 주문의 목록 맨 위에 있는 양식이 새 양식을 채우는 데 사용됩니다. 
    - **빨리 만들기 양식**
    - **빠른 보기 양식**
5. 양식을 변경한 후 **저장**을 선택하여 양식을 저장하거나 변경 사항을 저장하고 앱 사용자에게 표시하려면 **게시**를 선택합니다.  

## <a name="edit-a-form"></a>양식 편집 
1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
2. 왼쪽 탐색 창에서 **데이터**를 확장하고 **엔터티**를 선택합니다. 
3. 거래처 엔터티 같은 엔터티를 선택한 다음 **양식** 탭을 선택합니다.
4. 편집할 양식 이름을 선택합니다.  
    - 양식 행을 선택한 다음 명령 모음에서 **양식 편집**을 선택할 수도 있습니다.
    - 또 다른 방법은 양식 이름 옆의 **...** 를 선택한 다음 메뉴에서 **양식 편집**을 선택하는 것입니다. 
5. 양식을 변경한 후 **저장**을 선택하여 양식을 저장하거나 변경 사항을 저장하고 앱 사용자에게 표시하려면 **게시**를 선택합니다. 

## <a name="configure-a-form"></a>양식 구성
양식 디자이너를 사용하여 양식을 만들거나 편집할 때 양식을 구성하는 데 사용할 수 있는 속성이 있습니다.

|이름  |설명  |
|---------|---------|
|**제목**  | 다른 제조업체 및 앱 사용자에게 의미 있는 이름을 입력하십시오. 이 이름은 앱 사용자에게 표시됩니다. 사용자가 엔터티에 대한 여러 양식에 액세스할 수 있는 경우 이 이름을 사용하여 사용 가능한 다른 양식과 구분합니다. <br /><br />이 속성은 필수입니다. |
|**설명** |  양식이 다른 기본 양식과 어떻게 다른지 설명하는 설명을 입력합니다. 이 설명은 솔루션 탐색기의 엔터티에 대한 양식 목록에서만 제조업체에게 표시됩니다. |
|**최대 너비** | 양식의 너비를 제한하기 위한 최대 너비(픽셀 단위)를 설정합니다. 기본값은 1900입니다. <br /><br />이 속성은 필수입니다. |
|**이미지 표시** | 엔터티의 **기본 이미지**에 하나의 집합이 있는 경우 이를 표시합니다. 이 설정을 사용하면 양식의 헤더에 이미지 필드를 표시할 수 있습니다. <br /><br /> 엔터티 옵션에 대한 자세한 내용은 엔터티 옵션 사용 또는 사용 안 함을 참조하십시오. |

## <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식의 필드 추가, 구성, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)  
[양식의 섹션 추가, 구성, 이동 또는 삭제](add-move-or-delete-sections-on-form.md)  
[양식의 탭 추가, 구성, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식 디자이너에서 머리글 속성 구성](form-designer-header-properties.md)  
[양식에 하위 표 구성 요소 추가 또는 구성](form-designer-add-configure-subgrid.md)  
[양식에 빠른 보기 구성 요소 추가 또는 구성](form-designer-add-configure-quickview.md)  
[양식에서 조회 구성 요소 구성](form-designer-add-configure-lookup.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)  
