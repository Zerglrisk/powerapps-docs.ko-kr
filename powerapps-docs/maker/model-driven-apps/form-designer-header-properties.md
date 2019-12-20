---
title: 양식 디자이너에서 머리글 속성 구성 | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: crm-online
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1832d3bd9fc222f3c71089ae386e455a53f512f7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868166"
---
# <a name="configure-header-properties-in-the-form-designer"></a>양식 디자이너에서 머리글 속성 구성

제조업체는 양식을 사용하는 모든 이의 요구에 맞게 모델 중심 앱 양식 머리글의 밀도를 제어할 수 있습니다.

> [!NOTE]
> 이 기능은 2019 릴리스 웨이브 2 기능의 초기 미리 보기를 선택한 환경에서만 사용할 수 있습니다. 추가 정보: [2019 릴리스 웨이브 2 조기 선택](https://docs.microsoft.com/power-platform/admin/preview-october-2019-updates) 

## <a name="high-density-header"></a>고밀도 머리글

고밀도 양식 머리글은 주요 정보가 항상 사용자에게 표시되도록 합니다. 고밀도 머리글을 사용하면 레코드 제목이 절대로 잘리지 않습니다. 긴 레코드 제목도 여러 줄로 표시됩니다. 마찬가지로 고밀도 머리글은 머리글에서 직접 최대 4개의 필드 값을 볼 수 있으며 잘리거나 숨겨지지 않도록 합니다.  

키 정보가 항상 표시되도록 하기 위해 프레임워크는 읽기 전용 필드 값을 표시하며 사용자는 머리글에서 필드 값을 직접 편집할 수 없습니다. 사용자 지정 구성 요소 또는 웹 리소스와 같은 시각화도 허용되지 않습니다.

양식이 머리글 밀도를 지정하지 않거나 새 양식이 작성될 때 프레임워크의 기본값은 고밀도 머리글입니다.

> [!div class="mx-imgBorder"] 
> ![고밀도 양식 머리글](media/form-header-high-density.png "고밀도 양식 머리글")
    
## <a name="low-density-header"></a>저밀도 머리글
저밀도 양식 머리글을 사용하면 머리글의 필드 값을 직접 편집할 수 있습니다. 사용자 지정 구성 요소 및 웹 리소스와 같은 시각화도 허용됩니다.  
  
그러나 종종 이로 인해 주요 정보가 잘리거나 쉽게 보이지 않게 됩니다. 저밀도 머리글은 레코드 제목과 머리글에 표시된 필드 값을 자릅니다. 종종 하나 또는 두 개의 필드만 머리글과 나머지 오버플로에 직접 표시되며 추가 클릭이 필요한 플라이아웃에 표시됩니다.

> [!div class="mx-imgBorder"] 
> ![저밀도 양식 머리글](media/form-header-low-density.png "저밀도 양식 머리글")

### <a name="configuring-header-density"></a>머리글 밀도 구성

모델 기반 양식의 머리글 밀도를 구성하려면 다음 단계를 수행하십시오.
1.  양식 디자이너를 열어 [양식을 만들거나 편집합니다](create-and-edit-forms.md).
2.  양식 미리 보기에서 머리글을 선택하거나 [트리 보기](using-tree-view-on-form.md)를 사용하여 양식 머리글을 선택합니다.
3.  속성 창에서 **고밀도**를 선택하여 고밀도 양식 머리글을 사용하거나 저밀도 양식 머리글을 사용하려면 선택을 취소합니다.
4.  명령 모음에서 **저장**을 선택하여 양식을 저장하거나 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다.

> [!NOTE]
> 새로운 양식 디자이너를 사용합니다. 기본 양식 디자이너는 머리글 밀도를 구성하는 기능을 제공하지 않습니다.

## <a name="header-flyout"></a>머리글 플라이아웃
사용자가 양식 머리글에서 펼침을 선택하면 머리글 플라이아웃이 표시됩니다. 사용자가 필드 값을 편집하고 양식 머리글의 일부인 사용자 지정 구성 요소 또는 웹 리소스와 같은 시각화를 표시할 수 있습니다.

머리글 플라이아웃의 동작은 머리글 밀도 구성에 따라 달라집니다.

### <a name="high-density-header-flyout"></a>고밀도 머리글 플라이아웃
고밀도 양식 머리글을 사용하면 머리글 플라이아웃에 머리글에 직접 표시되는 4개의 필드를 포함한 모든 머리글 필드가 표시됩니다. 프레임워크는 기본적으로 고밀도 머리글이 사용될 때 머리글 플라이아웃을 표시합니다. 제조업체는 고밀도 머리글로 머리글 플라이아웃의 가시성을 제어할 수 있습니다.

> [!div class="mx-imgBorder"] 
> ![고밀도 머리글이 있는 머리글 플라이아웃](media/form-header-flyout-high-density.png "고밀도 머리글이 있는 머리글 플라이아웃")

### <a name="low-density-header-flyout"></a>저밀도 머리글 플라이아웃
저밀도 양식 머리글의 경우 머리글 플라이아웃은 양식의 너비를 기준으로 양식을 머리글에 직접 표시할 수 없는 필드와 같은 오버플로 필드만 표시합니다. 머리글 플라이아웃은 머리글의 필드 수와 양식 너비에 따라 자동으로 표시되거나 숨겨집니다. 제조업체는 저밀도 머리글을 사용할 때 머리글 플라이아웃의 가시성을 제어할 수 없습니다.

> [!div class="mx-imgBorder"] 
> ![저밀도 머리글이 있는 머리글 플라이아웃](media/form-header-flyout-low-density.png "저밀도 머리글이 있는 머리글 플라이아웃")

### <a name="show-or-hide-the-header-flyout"></a>머리글 플라이아웃 표시 또는 숨기기
모델 기반 양식의 머리글 플라이아웃을 표시하거나 숨기려면 다음 단계를 수행하십시오.

1.  양식 디자이너를 열어 [양식을 만들거나 편집합니다](create-and-edit-forms.md).
2.  양식 미리 보기에서 양식 머리글을 선택하거나 [트리 보기](using-tree-view-on-form.md)를 사용하여 양식 머리글을 선택합니다.
3.  속성 창에서 **고밀도**를 선택하여 고밀도 양식 머리글을 사용합니다. 
4.  속성 창에서 **머리글 플라이아웃 표시**를 선택하여 머리글 플라이아웃을 표시하거나 머리글 플라이아웃을 숨기려면 확인란 선택을 취소합니다.
5.  명령 모음에서 **저장**을 선택하여 양식을 저장하거나 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다.

> [!NOTE]
> - 새로운 양식 디자이너를 사용합니다. 기본 양식 디자이너는 머리글 플라이아웃을 표시하거나 숨기는 기능을 제공하지 않습니다.   
> - 머리글 플라이아웃의 가시성은 고밀도 양식 머리글을 사용할 때만 제어할 수 있습니다. 저밀도 머리글을 사용하면 머리글 플라이아웃은 머리글의 필드 수와 양식 너비에 따라 자동으로 표시되거나 숨겨집니다.
> - 엔터티의 이미지는 **기본 이미지** 특성이 엔터티에 대해 정의되어 있고 양식 속성 **양식에 이미지 표시**가 활성화된 경우에만 헤더에 표시됩니다. 추가 정보: [이미지 필드](../common-data-service/types-of-fields.md#image-fields) <br />
    개발자는 [EntityMetadata.PrimaryImageAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.primaryimageattribute?view=dynamics-general-ce-9) 속성을 사용하여 엔터티의 이미지를 지정할 수 있습니다. 


## <a name="form-designer-messages-related-to-form-headers"></a>양식 머리글과 관련된 양식 디자이너 메시지
새 양식 디자이너 또는 기본 양식 디자이너를 사용하여 양식을 편집하면 양식 머리글과 관련된 일부 메시지가 표시될 수 있습니다. 아래에서 각 메시지에 대한 자세한 내용과 그 이유를 확인할 수 있습니다.

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>더 많은 데이터를 표시하는 고밀도 머리글을 표시하도록 양식을 업그레이드했습니다. 머리글의 속성에서 이 설정을 편집할 수 있습니다. 
제조업체가 새 기본 양식(작업으로 저장 포함)을 작성하거나 이전에 머리글 밀도에 대해 구성되지 않은 기본 양식을 편집할 때 이 메시지가 양식 디자이너에 표시됩니다.  
  
프레임워크는 기본적으로 고밀도 머리글로 설정되며 이 메시지는 제조업체가 해당 동작을 인식하는 데 도움이 됩니다. 제조업체는 앞에서 설명한대로 양식 머리글 밀도를 수동으로 구성하여 언제든지 프레임워크 기본값을 무시할 수 있습니다.

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>이 양식은 고밀도 머리글을 사용하지 않고 머리글 속성의 설정에 액세스합니다. 고밀도 머리글은 더 많은 데이터를 표시하는 데 도움이 됩니다. 
제조업체가 저밀도 머리글을 사용하도록 구성된 기본 양식을 편집을 위해 열 때 이 메시지가 양식 디자이너에 표시됩니다. 

메시지는 고밀도 머리글 및 그 이점에 대한 인식을 높이는 데 도움이 됩니다.

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>필드가 머리글 플라이아웃으로 이동: 머리글은 최대 4개의 읽기 전용 필드 값 표시를 지원합니다. 필드 *[필드 표시 이름]* 은 이제 플라이아웃에서만 사용할 수 있습니다.
이 메시지는 양식이 머리글 플라이아웃이 표시된 고밀도 머리글을 사용하는 경우 양식 디자이너에 표시됩니다.  
  
고밀도 머리글은 머리글에서 처음 네 필드의 읽기 전용 값을 표시합니다. 제조업체가 상위 4개 위치의 머리글에 필드를 추가하면 머리글에 직접 표시된 기존 필드가 확장되어 머리글 플라이아웃에서만 표시됩니다.      

메시지는 제조업체에 변경 사항을 알리고 작업 진행 여부를 확인합니다.

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>머리글 필드 제한 초과됨: 머리글은 최대 4개의 읽기 전용 필드 값 표시를 지원합니다. 더 추가하려면 사용하지 않는 필드를 제거하십시오. 
이 메시지는 양식이 머리글 플라이아웃이 숨겨진 고밀도 머리글을 사용하는 경우 양식 디자이너에 표시됩니다.  
  
고밀도 머리글은 머리글에서 최대 네 필드의 읽기 전용 값을 표시합니다. 머리글 플라이아웃이 숨겨져 있기 때문에 사용자는 추가 필드를 볼 수 없습니다.  

메시지는 머리글에 이미 4개의 필드가 있음을 제조업체에 알리고 머리글에 사용자가 볼 수 없는 추가 필드를 추가하지 못하게 합니다.

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>머리글에 사용자 지정 구성 요소가 표시되지 않음: 머리글은 최대 4개의 읽기 전용 필드 값 표시를 지원합니다. 머리글에 추가하기 전에 필드에서 사용자 구성 요소를 제거합니다.  
이 메시지는 양식이 머리글 플라이아웃이 숨겨진 고밀도 머리글을 사용하는 경우 양식 디자이너에 표시됩니다.  
  
고밀도 머리글은 머리글에서 필드의 읽기 전용 값을 표시합니다. 머리글 플라이아웃이 숨겨져 있기 때문에 사용자는 머리글의 필드와 연관된 사용자 구성 요소를 볼 수 없습니다.  

메시지는 제조업체에 관련 사용자 지정 구성 요소가 있는 필드를 머리글에 추가하려고 한다는 것을 알리고 필드를 머리글에 추가하기 전에 사용자 지정 구성 요소를 제거해야 합니다. 사용자가 머리글에서 사용자 지정 구성 요소를 볼 수 없기 때문입니다.

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>머리글에 읽기 전용 필드 값 표시: 머리글은 최대 4개의 읽기 전용 필드 값 표시를 지원합니다. 사용자에게 편집 기능을 제공하려면 양식의 섹션에 필드를 추가합니다.  
이 메시지는 양식이 머리글 플라이아웃이 숨겨진 고밀도 머리글을 사용하는 경우 양식 디자이너에 표시됩니다.  
  
고밀도 머리글은 머리글에서 필드의 읽기 전용 값을 표시합니다. 머리글 플라이아웃이 숨겨져 있기 때문에 사용자는 필드 값을 편집할 수 없습니다.  
  
메시지는 머리글에 추가된 모든 필드가 읽기 전용이며 사용자가 편집할 필드도 양식의 섹션에 추가되어야 함을 제조업체에 알려줍니다.

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>헤더 필드 값을 편집할 수 없음: 본문에서 머리글로 필드를 이동하면 읽기 전용 값으로 표시됩니다. 편집 기능을 유지하려면 필드를 머리글에 복사합니다.  
이 메시지는 머리글 플라이아웃이 숨겨진 고밀도 머리글을 사용하는 양식의 경우에만 양식 디자이너에 표시됩니다.  
  
고밀도 머리글은 머리글에서 필드의 읽기 전용 값을 표시합니다. 머리글 플라이아웃이 숨겨져 있기 때문에 사용자는 필드 값을 편집할 수 없습니다.  

메시지는 양식 본문에서 양식 머리글로 필드를 이동하려고 한다는 것을 제조업체에 알려줍니다. 그렇게 하면 읽기 전용이 됩니다. 따라서 제조업체가 필드를 머리글로 이동하거나 필드 사본을 머리글에 추가할 수 있습니다. 필드를 머리글로 이동하면 사용자가 편집할 수 있도록 양식 본문의 원래 위치에서 필드를 사용할 수 없습니다. 필드 사본을 헤더에 추가하면 사용자가 양식 본문 내에서 계속 편집 할 수 있도록 필드가 원래 위치에 그대로 남아 있습니다.

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>양식 머리글은 이제 더 많은 데이터를 표시하기 위해 기본적으로 고밀도로 설정됩니다. 새 양식 디자이너를 사용하여 머리글 밀도를 편집합니다.  
제조업체가 저밀도 머리글을 사용하도록 구성된 기본 양식을 편집을 위해 열 때 이 메시지가 클래식 양식 디자이너에 표시됩니다. 

메시지는 고밀도 머리글과 그 이점에 대한 인식을 높이는 데 도움이 되며 제조업체는 새로운 양식 디자이너를 사용하여 머리글 밀도를 구성해야 합니다.  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>이 양식에서는 고밀도 머리글을 사용하고 있습니다. 이 양식을 사용하는 최상의 작성 환경을 위해 새 양식 디자이너를 사용하십시오. 
제조업체가 고밀도 머리글을 사용하도록 구성된 기본 양식을 편집을 위해 열 때 이 메시지가 클래식 양식 디자이너에 표시됩니다.  
  
기본 양식 디자이너는 WYSIWYG 작성 환경을 제공하지 않습니다. 또한 제조업체가 양식 머리글에 대한 변경의 영향을 감지하고 방지하거나 경고하지 않습니다. 예를 들어, 머리글 플라이아웃이 숨겨져 있는 고밀도 머리글을 사용하는 양식을 편집할 때 기본 양식 디자이너는 이러한 필드를 사용자가 사용할 수 없어도 제조업체가 머리글에 4개 이상의 필드를 추가하지 못하도록 하지 않습니다.  
  
메시지는 고밀도 머리글을 사용하는 양식을 편집할 때 새로운 양식 디자이너를 사용해야 함을 제조업체에 알립니다. 이를 통해 제조업체는 변경 사항이 양식 머리글에 미치는 영향을 인식할 수 있습니다.

## <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식 디자이너를 사용하여 양식 만들기, 편집 또는 구성](create-and-edit-forms.md)  
[양식의 필드 추가, 구성, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식의 구성 요소 추가, 구성, 이동 또는 삭제](add-move-configure-or-delete-components-on-form.md)  
[양식의 섹션 추가, 구성, 이동 또는 삭제](add-move-or-delete-sections-on-form.md)  
[양식의 탭 추가, 구성, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식에 하위 표 구성 요소 추가 또는 구성](form-designer-add-configure-subgrid.md)  
[양식에 빠른 보기 구성 요소 추가 또는 구성](form-designer-add-configure-quickview.md)  
[양식에서 조회 구성 요소 구성](form-designer-add-configure-lookup.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)  
