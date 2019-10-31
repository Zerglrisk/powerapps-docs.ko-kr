---
title: PowerApps에서 모델 기반 앱 웹 리소스 만들기 또는 편집 | MicrosoftDocs
description: 웹 리소스 생성 및 편집 방법 배우기
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>모델 기반 앱 웹 리소스를 만들거나 편집하여 앱 확장

웹 리소스는 웹 개발에 사용되는 파일을 사용하는 앱 확장을 위해 개발자들이 전형적으로 사용합니다. 앱 사용자는 개발자 또는 디자이너에 의해 제공되는 웹 리소스를 관리할 필요가 있습니다.  

> [!TIP]
> 웹 리소스에 대한 자세한 내용은 [개발자 설명서: 모델 기반 앱용 웹 리소스](/powerapps/developer/model-driven-apps/web-resources)를 참조하십시오.<br /> PowerApps에 추가된 웹 리소스 종속성에 대한 자세한 내용은 [개발자 설명서: 웹 리소스 종속성](/dynamics365/customer-engagement/developer/web-resources)을 참조하십시오.
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>웹 리소스란 무엇입니까?  

웹 리소스는 시스템에 저장되어 있는 가상의 파일입니다. 각 웹 리소스에는 URL에 사용될 수 있는 고유한 이름이 있어 파일을 검색할 수 있습니다. 이렇게 생각해 봅니다. 웹 응용 프로그램을 실행 중인 실제 웹 서버에 대한 액세스 권한이 있을 경우 해당 웹 사이트로 파일을 복사할 수 있습니다. 하지만 대부분의 온라인 서비스에서는 이를 할 수 없습니다.  대신에, 웹 리소스를 사용해 파일을 시스템에 업로드하고 파일을 웹서버에 복사하듯 이름으로 그것들을 참조합니다.  
  
예를 들어 HTML 페이지를 "new_myWebResource.htm" 웹 리소스로 만든 경우 다음과 같은 URL을 사용하여 브라우저에서 해당 페이지를 열 수 있습니다.  
 
`<base URL>/WebResources/new_myWebResource.htm`
  
여기서 *\<기본 URL>* 은 `dynamics.com`으로 끝나는 앱을 보는 데 사용하는 URL의 일부입니다. 웹 리소스가 시스템의 데이터이므로 조직에서 사용이 허가된 사용자만 이 방식으로 액세스할 수 있습니다. 일반적으로 웹 리소스는 직접 참조되기보다 양식에 포함되어 있습니다. 가장 일반적인 사용법은 양식 스크립트에 대해 JavaScript 라이브러리를 제공하는 것입니다.  
    
웹 리소스는 시스템의 데이터이고 솔루션을 인식하므로 솔루션의 일부로 내보낸 후 다른 조직으로 솔루션을 가져와 다른 조직으로 이동할 수 있습니다. 웹 리소스에 대한 작업을 하려면 솔루션 탐색기를 사용해야 합니다.
  
## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 사용자 웹 리소스의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 웹 리소스에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>웹 리소스 보기

솔루션 탐색기를 연 상태에서 **구성 요소**에서 **웹 리소스**을 선택합니다.

![웹 리소스 보기](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>웹 리소스 만들기 또는 편집  

[웹 리소스를 보는](#view-web-resources) 동안 **새로 만들기**를 선택하여 새 웹 리소스를 만들거나 기존 웹 리소스를 두 번 클릭하여 편집합니다.

![새 웹 리소스 양식](media/new-web-resource-form.png)

양식을 작성하거나 웹 리소스를 편집하려면 다음과 같이 합니다.
  
|필드|설명|  
|-----------|-----------------|  
|**이름**|*필수 특성*: 이 웹 리소스의 고유한 이름입니다. 웹 리소스를 저장한 후에는 변경할 수 없습니다.<br />&bull; 이 이름은 문자, 숫자, 마침표 및 연속되지 않은 슬래시("/") 문자만 포함할 수 있습니다.<br /> &bull; 솔루션 게시자 사용자 지정 접두사가 웹 리소스 이름 앞에 추가됩니다.|  
|**표시 이름**|웹 리소스 목록을 볼 경우 표시되는 이름입니다.|  
|**설명**|웹 리소스에 대한 설명입니다.|  
|**유형**|*필수 특성*: 웹 리소스의 유형입니다. 웹 리소스를 저장한 후에는 변경할 수 없습니다.|  
|**텍스트 편집기**|웹 리소스가 텍스트 파일을 표현할 경우 이 버튼을 눌러 페이지를 열고 텍스트 편집기를 사용해 콘텐츠를 편집합니다.<br />추가 정보: [텍스트 편집기 적절하게 사용](#use-the-text-editor-appropriately)| 
|**언어**|언어를 선택할 수 있습니다. 이 옵션은 웹 리소스 데이터를 저장하는 레코드를 태깅합니다. 웹 리소스의 동작은 변하지 않습니다.|  
|**파일 업로드**|**검색…** 선택 웹 리소스로 업로드할 파일을 선택합니다.<br />&bull; 새 웹 리소스를 만들거나 기존 웹 리소스를 덮어쓸 때 파일을 업로드할 수 있습니다.<br />&bull; 파일의 파일 확장명은 허용된 파일 확장명과 일치해야 합니다.<br />&bull;기본적으로 웹 리소스로 업로드할 수 있는 최대 파일 크기는 5MB입니다. 이 값은 **시스템 설정** > **전자 메일** 탭 > **첨부 파일의 크기 제한 설정** 설정을 사용하여 수정할 수 있습니다. 추가 정보: [시스템 설정 대화 상자 - 전자 메일 탭](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|웹 리소스를 저장한 후 웹 리소스에 대한 URL이 여기에 표시됩니다. 귀하의 브라우저에서 웹 리소스를 보려면 이 링크를 선택합니다.|  
  
변경 내용을 추가한 후 **저장**을 클릭하고 **게시**를 선택합니다.  

> [!NOTE]
> 웹 리소스에 대한 변경 내용은 게시할 때까지 응용 프로그램에 표시되지 않습니다.
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>텍스트 편집기 적절하게 사용

웹 리소스를 위해 응용 프로그램에 제공된 텍스트 편집기는 텍스트 파일의 간단한 편집에만 사용되어야 합니다. HTML 웹 리소스를 만들고 편집하는 데 사용할 수 있지만 텍스트 편집기를 사용하여 만든 HTML 웹 리소스만 편집해야 합니다. 텍스트 편집기는 매우 간단한 HTML 콘텐츠를 위해 디자인되었습니다. 

> [!IMPORTANT]
> 텍스트 편집기를 사용하여 HTML 웹 리소스의 콘텐츠를 만들지 않은 경우 텍스트 편집기를 사용하여 편집하지 마십시오.  
> 텍스트 편집기는 편집하도록 허용하는 방식으로 HTML 소스를 수정하는 컨트롤을 사용합니다. 이러한 변경 내용으로 브라우저에서 페이지가 다르게 동작할 수 있으며 작업을 중지하기 위해 더 복잡한 코드가 필요할 수 있습니다. HTML 웹 리소스를 텍스트 편집기로 열고 변경하지 않고 저장하면 일부 HTML 웹 리소스가 중단될 수 있습니다.  추가 정보: [개발자 설명서: HTML 웹 리소스에 대한 텍스트 편집기 사용](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
외부 편집기를 사용하여 텍스트 파일을 편집한 후 **파일 업로드** 단추를 사용하여 업로드하기 전에 로컬에서 저장하는 것이 좋습니다. 이렇게 하면 이전 버전으로 돌아가야 할 경우 웹 리소스의 복사본을 유지할 수 있습니다. 메모장과 같은 간단한 편집기를 사용할 수 있지만 더 고급 기능을 가진 텍스트 편집기를 사용하는 것이 좋습니다. [Visual Studio Community](https://www.visualstudio.com/vs/community/) 및 [Visual Studio Code](https://code.visualstudio.com/)는 무료이며 텍스트 기반 리소스에 사용된 파일을 편집할 수 있는 강력한 기능을 제공합니다.  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>양식에서 웹 리소스 만들기 및 편집

양식에서 웹 리소스를 추가하거나 편집하여 사용자에게 더욱 매력적이거나 유용하게 만들 수 있습니다. 

> [!NOTE]
> 양식 머리글 또는 바닥글에 웹 리소스를 포함할 수 없습니다.  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>양식으로 이동
솔루션 탐색기를 연 상태에서 **구성 요소**에서 **엔터티**를 확장한 다음 작업할 엔터티를 확장합니다.

목록에서 기본 유형의 **양식**을 클릭하거나 탭한 후 열 항목을 선택하고 양식을 편집합니다.

### <a name="add-or-edit-web-resource-in-a-form"></a>양식에서 웹 리소스 추가 또는 편집

양식에서 웹 리소스에 대해 설정할 수 있는 속성에 대한 자세한 내용은 [웹 리소스 속성](web-resource-properties-legacy.md)을 참조하십시오.

### <a name="preview"></a>미리 보기

기본 양식이 어떻게 표시되고 이벤트가 어떻게 작동하는지 미리 보려면:
- **홈** 탭에서 **미리 보기**를 선택한 후**양식 생성**, **양식 업데이트**,또는 **읽기 전용 양식**을 선택합니다.
- 미리 보기 양식을 닫으려면 **파일** 메뉴에서 **닫기**를 선택합니다.

### <a name="save"></a>저장

양식 편집을 마친 경우 **홈** 탭에서 **저장 및 닫기**를 선택해 양식을 닫습니다. 

### <a name="publish"></a>게시

사용자 지정 작업을 완료했으면 사용자 지정 항목을 게시합니다.
- 현재 편집하는 구성 요소를 사용자 지정하여 게시하려면, 탐색 창에서 작업한 엔터티를 선택하고 **게시**를 선택합니다.
- 한번에 모두 게시되지 않은 구성 요소를 사용자 지정 게시하려면 탐색 창에서 **엔터티**를 선택하고 **작업** 도구 모음에서 **모든 사용자 지정 게시**를 선택합니다.
   
  
### <a name="see-also"></a>참조  

[웹 리소스 속성](web-resource-properties-legacy.md) <br /> 
[양식 만들기 및 디자인](create-design-forms.md) <br />
[모델 기반 앱 구성 요소 이해](model-driven-app-components.md) <br /> 
[개발자 설명서: 모델 기반 앱의 웹 리소스](/powerapps/developer/model-driven-apps/web-resources)
