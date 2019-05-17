---
title: 포함된 캔버스 앱 내에서 호스트 양식에 대한 작업 수행 | MicrosoftDocs
ms.custom: ''
ms.date: 03/29/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
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
# <a name="perform-predefined-actions-on-the-host-form-from-within-an-embedded-canvas-app"></a>포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행
포함된 캔버스 앱은 호스트 양식에 대한 미리 정의된 작업을 수행하는 기능을 제공합니다. 이러한 작업을 통해 제조업체는 호스트 양식을 탐색하고, 새로 고치고, 저장할 수 있습니다. 이러한 작업을 사용하면 포함된 캔버스 앱이 양식과 모델 기반 앱의 더 중요한 부분으로 작용할 수 있습니다.  

> [!NOTE]
> 이 기능은 현지 미리 보기로 제공됩니다. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)] 

**ModelDrivenFormIntegration** 개체에는 이제 제작자가 호스트 양식에서 작업을 수행할 수 있도록 하는 다음과 같은 새로운 메서드가 포함되어 있습니다.  
  
### <a name="navigatetomainformentityname-mainformname-recordid"></a>NavigateToMainForm(entityName, mainFormName, recordId)
호스트 양식을 기본 양식으로 이동하고 지정된 레코드를 표시합니다.  
* **entityName** - 기본 양식의 상위 엔터티를 지정하는 필수 문자열 매개 변수입니다.  
* **formName** - 탐색할 기본 양식의 이름을 지정하는 필수 문자열 매개 변수입니다.  
* **recordId** - 기본 양식에 표시할 레코드의 ID를 지정하는 필수 문자열 매개 변수입니다.  
 
NavigateToMainForm 메서드를 호출하면 다음과 같은 오류 메시지가 표시될 수 있습니다.
  
| 오류 메시지 | 문제 해결 가이드 |
|:--------------|:-------------------------|
|**엔터티가 없음: *[EntityName]*** | *entityName* 매개 변수의 값을 확인하고 유효한 엔터티 이름이고 사용자가 액세스할 수 있는지 확인하십시오. |
|**양식이 없음: *[FormName]*** | *mainFormName* 매개 변수의 값을 확인하고 유효한 기본 양식 이름이고 사용자가 액세스할 수 있는지 확인하십시오. |
|**레코드를 로딩하는 동안 문제가 발생했습니다.** | *recordId* 매개 변수의 값을 확인하고 유효한 레코드 ID이고 사용자가 액세스할 수 있는지 확인하십시오. |
  
  
### <a name="navigatetoviewentityname-viewname"></a>NavigateToView(entityName, viewName)
보려는 호스트 양식으로 이동합니다.  
* **entityName** - 보기의 상위 엔터티를 지정하는 필수 문자열 매개 변수입니다.  
* **viewName** - 탐색할 기본 양식의 이름을 지정하는 필수 문자열 매개 변수입니다.  
 
NavigateToView 메서드를 호출하면 다음과 같은 오류 메시지가 표시될 수 있습니다.
  
| 오류 메시지 | 문제 해결 가이드 |
|:--------------|:-------------------------|
|**엔터티가 없음: *[EntityName]*** | *entityName* 매개 변수의 값을 확인하고 유효한 엔터티 이름이고 사용자가 액세스할 수 있는지 확인하십시오. |
|**보기 없음: *[ViewName]*** | *viewName* 매개 변수의 값을 확인하고 유효한 보기 이름이고 사용자가 액세스할 수 있는지 확인하십시오. |
  
  
### <a name="openquickcreateformentityname"></a>OpenQuickCreateForm(entityName)  
엔터티에 대한 기본 빨리 만들기 양식을 엽니다.  
* **entityName** - 빨리 만들기 양식의 상위 엔터티를 지정하는 필수 문자열 매개 변수입니다.  
 
OpenQuickCreateForm 메서드를 호출하면 다음과 같은 오류 메시지가 표시될 수 있습니다.
  
| 오류 메시지 | 문제 해결 가이드 |
|:--------------|:-------------------------|
|**엔터티가 없음: *[EntityName]*** | *entityName* 매개 변수의 값을 확인하고 유효한 엔터티 이름이고 사용자가 액세스할 수 있는지 확인하십시오. |
  
  
### <a name="refreshformshowprompt"></a>RefreshForm(showPrompt)  
호스트 양식의 데이터를 새로 고칩니다.  
* **showPrompt** - 호스트 양식에서 저장되지 않은 데이터를 저장하기 전에 사용자에게 확인 프롬프트를 표시할지 여부를 나타내는 필수 부울 매개 변수입니다. 값은 "true" 또는 "false"여야 합니다.
 
RefreshForm 메서드를 호출하면 다음과 같은 오류 메시지가 표시될 수 있습니다.
  
| 오류 메시지 | 문제 해결 가이드 |
|:--------------|:-------------------------|
|**매개 변수 값으로 "참" 또는 "거짓"을 사용하십시오.** | *showPrompt* 매개 변수의 값을 확인하고 "true" 또는 "false"인지 확인하십시오. |
  
  
### <a name="saveform"></a>SaveForm()  
호스트 양식의 데이터를 저장합니다.  


> [!NOTE]
> 기능을 사용할 수 있게 되기 전에 만들어진 포함된 캔버스 앱에서 미리 정의된 작업을 수행하는 메서드에 대한 IntelliSense가 표시되지 않는 경우 앱을 저장하고 닫은 후 다시 엽니다. 

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[포함된 캔버스 앱을 사용하여 현재 레코드를 데이터 컨텍스트로 전달](pass-current-embedded-canvas-app.md) <br />
[포함된 캔버스 앱을 사용하여 관련 레코드의 목록을 데이터 컨텍스트로 전달](pass-related-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md)
