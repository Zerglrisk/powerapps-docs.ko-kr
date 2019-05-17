---
title: PowerApps에서 모델 기반 앱 기본 양식에 대한 웹 리소스 속성 | MicrosoftDocs
description: 기본 양식에 대한 웹 리소스 속성 이해
Keywords: 기본 양식; 웹 리소스 속성; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 04/03/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>모델 기반 앱 양식에 대한 웹 리소스 속성

양식에서 웹 리소스를 추가하거나 편집하여 앱 사용자에게 더욱 매력적이거나 유용하게 만들 수 있습니다. 양식 사용 웹 리소스는 이미지 또는 HTML 파일 컨트롤입니다.

> [!NOTE]
> Silverlight 웹 리소스는 더 이상 사용되지 않으며 통합 인터페이스 클라이언트에서 작동하지 않습니다.

## <a name="access-web-resource-properties"></a>웹 리소스 속성 액세스

양식을 보는 동안:
- **웹 리소스를 추가할 때:** 삽입하고자 하는 탭을 선택하고(예를 들어 **일반** 또 **메모**) **삽입** 탭에서 **웹 리소스**를 선택합니다.<br />![웹 리소스 삽입](media/insert-web-resource.png)
- **웹 리소스를 편집할 때**: 편집하려는 양식 탭 및 웹 리소스를 선택하고 **홈** 탭에서, **속성 변경**을 선택합니다. <br />![웹 리소스 속성 변경](media/web-resource-change-properties.png)

**웹 리소스 추가** 또는 **웹 리소스 속성** 대화 상자가 열립니다.

![웹 리소스 추가 대화 상자](media/add-web-resource-dialog.png)

> [!IMPORTANT]
> 웹 리소스를 양식에 표시하고 사용자가 사용할 수 있도록 하려면 **기본적으로 표시 가능** 옵션을 선택해야 합니다.

## <a name="web-resource-properties"></a>웹 리소스 속성

 **웹 리소스 추가** 또는 **웹 리소스 속성** 대화 상자에는 웹 리소스의 유형에 따라 두 개의 탭이 있을 수 있습니다.

### <a name="general-tab"></a>일반 탭

이러한 속성은 사용할 웹 리소스와 동작 방식을 정의합니다.

|필드|설명|
|--|--|
|**웹 리소스**|*필수 특성:* 기존 웹 리소스를 조회하거나 새로 만듭니다. 양식에 시각적 요소로 추가할 수 있는 HTML 및 이미지 웹 리소스만 포함하려면 **양식 사용 웹 리소스** 보기를 사용합니다.|
|**이름**|*필수 특성:* 양식에 추가할 웹 리소스 컨트롤의 이름을 지정합니다. 이 값은 양식에서 컨트롤을 고유하게 식별합니다.|
|**레이블**|*필수 특성:* **이름** 필드 값에 따라 자동으로 생성됩니다. 양식에 추가할 웹 리소스 컨트롤의 현지화 가능한 텍스트를 지정합니다. 이 를 표시하려면 **양식에 레이블 표시**를 선택합니다.|
|**기본적으로 표시 가능**|이 옵션을 사용하면 양식이 로드될 때 웹 리소스가 표시됩니다. 필요에 따라 웹 리소스를 표시하는 비즈니스 규칙 또는 양식 스크립트가 있는 경우 이 필드의 선택을 취소합니다. 추가 정보: [양식 요소 표시 또는 숨기기](visibility-options-legacy.md)|
|**모바일에 사용**|모바일 앱에서이 웹 리소스를 볼 수 있도록 하려면 이 옵션을 선택합니다.|

선택한 웹 리소스의 유형에 따라 추가 속성을 설정합니다.

HTML 웹 리소스의 경우 다음을 볼 수 있습니다.

![HTML 웹 리소스 속성](media/web-resource-general-html-properties.png)

|필드|설명|
|--|--|
|**사용자 지정 매개 변수(데이터)**|일반적으로 `data` 쿼리 문자열 매개 변수로 HTML 웹 리소스로 전달되는 구성 데이터입니다. HTML 페이지와 관련된 스크립트는 이 데이터에 액세스하여 페이지의 동작을 변경하는 데 사용할 수 있습니다.|
|**지원되는 경우 프레임 간 스크립팅을 제한합니다.**|HTML 웹 리소스의 내용을 완전히 신뢰하지 않는 경우 이 옵션을 사용합니다. 추가 정보: [개발자 설명서: 프레임 간 스크립팅을 제한할지 여부 선택](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**레코드 개체 유형 코드 및 고유 식별자를 매개 변수로 전달합니다.**|양식에 표시되는 현재 레코드에 대한 데이터를 HTML 웹 리소스 페이지로 전달하여 페이지에서 실행되는 스크립트가 레코드에 대한 데이터에 액세스할 수 있도록 할 수 있습니다. 추가 정보: <br />[웹 리소스에 매개 변수 전달](#pass-parameters-to-web-resources)<br />[개발자 설명서: 레코드에 대한 컨텍스트 정보 전달](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

이미지 웹 리소스의 경우 모든 사용자가 페이지에 액세스할 수 있도록 하는 보조 기술에 중요한 **대체 텍스트**를 지정하는 옵션이 있습니다.

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>서식 탭

**서식** 탭에서 표시되는 옵션은 삽입한 웹 리소스의 유형 및 삽입된 컨텍스트에 따라 다릅니다. 이러한 옵션에는 표시할 열 및 행 개수, 테두리 표시 여부 및 스크롤 동작 지정이 포함됩니다.

![웹 리소스 서식 속성](media/web-resource-formatting-properties.png)

|속성|설명|  
|--------------|-----------------|
|**컨트롤이 차지하는 열 수 선택**|웹 리소스를 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.|  
|**컨트롤에 사용되는 행 수를 선택하십시오.**|여러 행을 지정하여 웹 리소스의 높이를 제어하거나 **사용 가능한 공간을 사용하기 위해 자동으로 확장**을 선택하여 웹 리소스 높이가 사용 가능한 공간으로 확장되도록 허용할 수 있습니다.|  
|**IFRAME의 스크롤 유형 선택**|HTML 웹 리소스는 IFRAME을 사용하여 양식에 추가됩니다.<br /><br /> - **필요한 경우**: 웹 리소스의 크기가 사용 가능한 것보다 클 때 스크롤 막대를 표시합니다.<br />- **항상**: 항상 스크롤 막대를 표시합니다.<br />- **사용 안 함**: 스크롤 막대를 표시하지 않습니다.|  
|**테두리 표시**|웹 리소스의 테두리를 표시합니다.|  


### <a name="dependencies-tab"></a>종속성 탭

웹 리소스는 스크립트를 사용하여 양식에서 필드와 상호 작용할 수 있습니다. 필드가 양식에서 제거되면 웹 리소스의 스크립트가 작동하지 않습니다. 실수로 제거되지 않도록 웹 리소스의 스크립트에서 참조되는 필드를 **종속 필드**에 추가합니다.

![웹 리소스 종속성 속성](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>웹 리소스에 매개 변수 전달 

HTML 웹 리소스는 매개 변수를 쿼리 문자열 매개 변수로 전달하도록 허용할 수 있습니다.  
  
레코드에 대한 정보는 **레코드 개체 유형 코드 및 고유 식별자를 매개 변수로 전달합니다.** 옵션을 사용하여 전달할 수 있습니다. 정보를 **사용자 지정 매개 변수(데이터)** 필드에 입력하면 데이터 매개 변수를 사용하여 전달됩니다. 전달된 값은 다음과 같습니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`data`|이 매개 변수는 **사용자 지정 매개 변수(데이터)** 에 텍스트가 제공될 경우에만 전달됩니다.|  
|`orglcid`|조직 기본 언어 LCID입니다.|  
|`orgname`|조직의 이름입니다.|  
|`userlcid`|사용자의 선호 언어 LCID|  
|`type`|**이것을 사용하지 마십시오.** 엔터티 유형 코드입니다. 이 숫자 값은 다른 조직의 사용자 지정 엔터티와 다를 수 있습니다. 대신 엔터티 유형 이름을 사용합니다.|  
|`typename`|엔터티 유형 이름입니다.|  
|`id`|레코드의 id 값입니다. 이 매개 변수에는 엔터티 레코드를 저장할 때까지 값이 없습니다.|  
  
다른 매개 변수는 허용되지 않으므로 다른 매개 변수를 사용하면 웹 리소스가 열리지 않습니다. 여러 값을 전달해야 할 경우 데이터 매개 변수는 그 안에 더 많은 매개 변수를 포함하도록 오버로드할 수 있습니다.

추가 정보: [개발자 설명서: 레코드에 대한 컨텍스트 정보 전달](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>참조

[앱 확장을 위해 웹 리소스 생성 및 편집하기](create-edit-web-resources.md)<br />
[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
