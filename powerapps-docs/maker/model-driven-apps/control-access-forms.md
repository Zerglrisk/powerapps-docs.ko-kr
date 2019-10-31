---
title: PowerApps에서 모델 기반 앱 양식에 대한 액세스 제어 | MicrosoftDocs
description: 기본 양식에 대한 액세스를 제어하는 방법 알아보기
ms.custom: ''
ms.date: 06/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="control-access-to-model-driven-app-forms"></a>모델 기반 앱 양식에 대한 액세스 제어

 두 가지 방법으로 기본 양식에 대한 액세스를 제어할 수 있습니다.  
  
- **기본 양식 비활성 확인**  
  
     활성 또는 비활성 속성을 기본 양식으로 설정할 수 없습니다. 이 기능은 주로 Common Data Service 환경을 업그레이드할 때 포함된 새 양식을 관리하기 위해 포함되었지만 이를 사용하여 사용자가 모든 기본 양식을 사용할 수 없도록 할 수 있습니다.   
  
- **기본 양식에 보안 역할 할당**  
  
     이 기능을 사용하여 기본 양식을 특정 그룹에 사용할 수 있도록 합니다.  
  
 조직의 다른 사용자는 동일한 데이터를 다른 방식으로 상호 작용할 수 있습니다. 관리자는 레코드의 정보를 빠르게 검색할 수 있는지에 따라 달라지며 서비스 사용자는 데이터 입력을 간소화하는 양식이 필요할 수 있습니다. 다른 사용자 그룹이 속하는 보안 역할에 양식을 할당하여 다른 요구 사항에 맞게 조정할 수 있습니다.  
  
 단계별 절차는 [양식에 보안 역할 할당](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)을 참조하십시오.  
  
 엔터티에 정의된 기본 양식 또는 기타 양식 유형이 둘 이상일 경우 사용자의 보안 역할에 따라 사용할 수 있는 양식을 선택할 수 있습니다. 각 엔터티는 사용자에 대해 양식을 표시할 수 있어야 하므로 하나 이상의 양식이 "대체" 양식(명시적으로 할당된 양식이 없는 보안 역할을 가진 사용자에게 표시되는 양식)이 지정되어 있어야 합니다.  
  
> [!NOTE]
>  빨리 만들기 양식, 빠른 보기 양식 및 카드 양식에는 보안 역할을 할당할 수 없습니다.  
  
 양식 편집기 또는 양식 표에서 기본 양식에 보안 역할을 할당할 수 있습니다. 하지만 엔터티에 대해 양식이 하나만 있으면 **보안 역할 할당** 대화 상자에서 **폴백 활성화** 옵션을 해제할 수 없습니다. 이 경우 양식에 보안 역할을 지정했더라도 폴백이 설정되어 있으므로 포함하지 않은 보안 역할 연결 사용자가 양식을 볼 수 있습니다.  
  
 엔터티에 대해 두 번째 기본 양식을 만든 다음에는 양식 중 하나에 대해 **폴백 활성화** 옵션을 해제할 수 있습니다. 시스템에서는 항상 적어도 하나의 양식이 폴백 활성화인지 확인합니다.  
  
 기본 양식이 둘 이상 있을 경우 기본적으로 사용자에게 표시되는 양식을 제어하는 양식 순서를 지정할 수 있습니다. 사용할 수 있는 양식이 둘 이상 있을 경우 양식을 변경할 수 있고 다른 양식을 선택하기 전까지 선택한 양식이 기본 양식이 됩니다. 이 기본 설정은 브라우저에 저장됩니다. 다른 컴퓨터나 브라우저를 사용할 경우 원래 기본 양식이 표시됩니다.  
  
## <a name="strategies-to-manage-the-fallback-form"></a>대체 양식 관리 전략  
 대체 양식 관리 전략은 다음과 같습니다.  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>모든 사용자게 동일한 양식이 표시됩니다.  
 엔터티에 대해 여러 양식이 필요하지 않은 경우 대체 양식이 필요하지 않습니다.  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>대응 양식 만들기  
 사용자가 보거나 편집할 수 있는 정보를 제한하기 원하므로 역할 기반 양식을 사용할 경우 표시되는 최소 정보를 가진 양식을 만드는 것이 좋습니다. **보안 역할 할당** 대화 상자에서 **선택한 보안 역할에만 표시**를 선택하고 시스템 관리자를 제외한 다른 역할을 선택하지 않고 **폴백 활성화**를 선택합니다. 시스템 관리자를 제외한 모든 사용자 및 보안 역할이 특정 양식에 연결되지 않은 사용자에게는 이 양식이 표시되지 않습니다. 양식에 표시되는 정보가 거의 없는 이유에 대한 정보와 양식과 관련된 보안 역할에 요청을 추가하는 방법과 양식에 대한 새 보안 역할을 포함하는 방법에 대한 정보에 대한 링크와 함께 HTML 웹 리소스를 양식에 포함할 수 있습니다.  
  
> [!NOTE]
>  양식 머리글 또는 바닥글에 웹 리소스를 포함할 수 없습니다.  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>일반 양식 만들기  
 역할 기반 양식을 사용하여 사용자의 역할에 따라 사용자 지정된 환경을 제공할 경우 가장 일반적인 양식을 대체 양식으로 설정하고 모든 사용자에게 표시되도록 구성할 수 있습니다. 그런 다음 특정 보안 역할에 대한 사용자 지정 양식을 만들고 해당 보안 역할에만 표시되도록 구성합니다. 이러한 양식을 폴백 활성화하지 마십시오. 마지막으로 **양식** 목록에서 **양식 순서** 대화 상자를 사용하여 가장 배타적인 것부터 그렇지 않은 것까지 순위를 정해 양식을 표시하도록 지정합니다. 대체 양식은 목록의 맨 아래에 있습니다. 사용자의 역할에 맞게 사용자 지정된 양식이 기본 양식으로 표시되지만 경우 양식 선택기를 사용하여 가장 많이 사용되는 양식을 선택할 수 있습니다. 어떤 양식을 선택하든 다른 양식을 선택하기 전에는 기본 양식으로 남습니다.  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>양식 스크립팅 사용  
클라이언트 API 양식 컨텍스트(formContext)는 현재 코드가 실행되는 양식 또는 양식의 항목(예: 빠른보기 컨트롤 또는 편집 가능한 표의 행)에 대한 참조를 제공합니다. 추가 정보: [클라이언트 API 양식 컨텍스트](/dynamics365/customer-engagement/developer/clientapi/clientapi-form-context)

> [!IMPORTANT]
> Xrm.Page 개체가 [더 이상 사용되지 않으며](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) 전달된 실행 컨텍스트 개체의 [getFormContext](/powerapps/developer/model-driven-apps/clientapi/reference/executioncontext/getformcontext) 메서드를 사용하여 적절한 양식이나 양식의 항목에 대한 참조를 반환해야 합니다.
<!-- 
 Finally, in the web application it is possible, but not recommended, for a developer to use scripts in the form Onload event to use the [Xrm.Page.ui.formSelector.items collection](http://go.microsoft.com/fwlink/p/?LinkID=513300) to query available forms and use the navigate method to direct users to a specific form. Remember that the [navigate method](http://go.microsoft.com/fwlink/p/?LinkID=513301) will cause the form to load again (and the Onload event to occur again). Your logic in the event handler should always check some condition before you use the navigate method to avoid an endless loop or unnecessarily restrict users options to navigate between forms.  
  
 This approach will not work for Dynamics 365 for tablets because multiple forms are not available for selection.  -->

### <a name="see-also"></a>참조  

[양식에 보안 역할 할당](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
