---
title: PowerApps에서 모델 기반 앱 양식 편집기 열기 | MicrosoftDocs
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 8478a07a-c697-4784-874b-36958eb4f95d
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="open-the-model-driven-app-form-editor"></a>모델 기반 앱 양식 편집기 열기 
양식 편집기에서는 섹션, 탭, 필드 및 컨트롤과 같은 구성 요소를 양식 편집기 캔버스에 놓아 양식을 디자인할 수 있습니다. 이 항목에서는 양식 편집기에 액세스하는 여러 가지 방법에 대해 설명합니다.
 
양식을 편집하는 프로세스에서 새 솔루션 구성 요소를 만드는 경우(예: 웹 리소스) 구성 요소의 이름은 기본 솔루션에 대한 솔루션 게시자 사용자 지정 접두사를 사용하고 이러한 구성 요소는 기본 솔루션에만 포함됩니다. 새 솔루션 구성 요소를 특정 비관리형 솔루션에 포함하려면 비관리형 솔루션을 통해 양식 편집기를 열어야 합니다.  

## <a name="access-the-form-editor-from-the-powerapps-site"></a>PowerApps 사이트에서 양식 편집기 액세스

1. [PowerApps](https://web.powerapps.com/)에 로그인합니다. 

2. **데이터** > **엔터티**를 선택한 다음 거래처 엔터티와 같은 원하는 엔터티를 선택합니다. 

3. **양식** 탭을 선택한 다음 **거래처** 기본 양식과 같은 원하는 양식을 엽니다.

## <a name="access-the-form-editor-from-solution-explorer"></a>솔루션 탐색기에서 양식 편집기 액세스
  
1.  [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.
  
2.  **구성 요소**에서 **엔터티**를 확장한 후 원하는 엔터티를 확장하고 **포럼**을 클릭합니다.  
  
3.  양식 목록에서 편집할 양식을 클릭합니다.  
  

## <a name="access-the-form-editor-through-the-command-bar-within-a-model-driven-app"></a>모델 기반 앱 내에서 명령 모음을 통해 양식 편집기에 액세스 
  
1.  레코드를 엽니다.  
  
2.  엔터티에 대한 기본 양식이 여러 개 있으면 편집할 양식인지 확인합니다. 그렇지 않을 경우 양식 선택기를 사용하여 편집할 양식을 선택합니다.  
  
3.  **추가 명령** 단추 ![약속 활동의 추가 명령 단추](media/more-commands.gif "약속 활동의 추가 명령 단추")를 선택합니다.  
  
4.  **양식 편집기**를 선택합니다.  

## <a name="access-the-form-editor-from-within-app"></a>앱 내에서 양식 편집기 액세스
  
 엔터티에 따라 명령 모음 또는 리본을 통해 양식 편집기에 액세스할 수 있습니다. 이러한 방법은 둘 다 기본 솔루션의 컨텍스트에서 양식을 엽니다. 

## <a name="access-the-form-editor-for-an-unmanaged-solution"></a>비관리형 솔루션의 양식 편집기에 액세스  
  
1.  [솔루션](advanced-navigation.md#solutions)을 엽니다.  
  
2.  사용할 비관리형 솔루션을 두 번 클릭합니다.  
  
3.  편집할 양식으로 엔터티를 찾습니다. 엔터티가 거기에 없으면 추가해야 합니다. 추가 정보: [비관리형 솔루션에 엔터티 추가](#add-an-entity-to-an-unmanaged-solution) 
  
### <a name="add-an-entity-to-an-unmanaged-solution"></a>비관리형 솔루션에 엔터티를 추가합니다.  
  
1.  **엔터티** 노드를 선택하고 목록 위의 도구 모음에서 **기존 항목 추가**를 클릭합니다.  
  
2.  **솔루션 구성 요소 선택** 대화 상자에서 **구성 요소 유형** 선택기를 **엔터티**로 설정하고 추가할 엔터티를 선택하고 **확인**을 클릭합니다.  
  
3.  **필수 구성 요소 누락** 대화 상자가 나타나면 이 비관리형 솔루션을 다른 환경에 내보내지 않으려면 **아니요, 필수 구성 요소를 포함하지 않습니다.** 를 클릭할 수 있습니다. 이번에 누락된 필수 구성 요소를 포함하지 않도록 선택하면 나중에 추가할 수 있습니다. 나중에 이 솔루션을 내보낼 경우 다시 알림을 받습니다.  
  
5.  솔루션 탐색기에서 편집하려는 양식이 있는 엔터티를 확장하고 **양식**을 선택합니다.  
  
6.  양식 목록에서 편집할 양식을 두 번 클릭합니다.  

## <a name="next-steps"></a>다음 단계

[양식 만들기 및 디자인](create-design-forms.md)
