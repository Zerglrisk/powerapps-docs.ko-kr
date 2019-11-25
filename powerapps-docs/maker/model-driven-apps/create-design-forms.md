---
title: 모델 기반 앱 양식 만들기 및 디자인 | MicrosoftDocs
ms.custom: ''
ms.date: 12/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
ms.author: matp
manager: kvivek
author: Mattp123
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e3a3e8bd5527f9707849bf1b54247605d447469
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2704574"
---
# <a name="create-and-design-model-driven-app-forms"></a>모델 기반 앱 양식 만들기 및 디자인 

PowerApps에서 양식은 사용자들이 작업을 수행하는 데 필요한 데이터와 상호 작용하는 데 사용하는 사용자 인터페이스를 제공합니다. 사용자가 사용하는 양식은 필요한 정보를 효율적으로 찾거나 입력할 수 있도록 디자인되어 있습니다. 

기본 솔루션 또는 비관리형 솔루션에서는 양식 사용자 지정이 가능한 모든 엔터티에 대해 새 양식을 만들거나 기존 양식을 편집할 수 있습니다. 비관리형 솔루션에서는 솔루션에 대해 만들어진 비관리형 사용자 지정 엔터티의 관리 속성을 편집할 수 있습니다.
관리형 솔루션에서는 엔터티에 대한 새 양식을 만들거나 기존 양식을 편집할 수 없습니다. 하지만 관리형 솔루션의 엔터티에 대한 관리 속성이 사용자 지정 가능하도록 설정된 경우에는 엔터티에 대해 양식을 추가하거나 편집할 수 있습니다. 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>양식 유형
양식에는 다양한 유형이 있으며 각 유형에는 특정 기능이나 용도가 있습니다. 추가 정보: [PowerApps의 양식 유형](types-forms.md)  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>업데이트된 엔터티와 클래식 엔터티 비교  
PowerApps은 양식을 디자인하는 여러 옵션을 제공합니다. 통합 인터페이스로 대부분의 엔터티는 응답형 인터페이스에 더 잘 맞도록 업데이트되었습니다. 업데이트된 엔터티와 사용자 지정 엔터티에는 Dynamics 365 for tablets 클라이언트, 비즈니스 프로세스 흐름 및 비즈니스 규칙에 대한 지원이 포함됩니다. 이러한 엔터티를 사용하면 한 번 디자인하여 모든 클라이언트에 배포할 수 있습니다.  
  
아직 클래식 엔터티라고 부르는 이전 버전의 기능 및 모양이 포함된 엔터티도 많이 있습니다. 이러한 엔터티는 자주 사용되지 않습니다. 아래에 클래식 엔터티를 나열합니다.  
  
||||||  
|-|-|-|-|-|  
|주소|참조 자료 검색|문서 주석|대량 삭제 작업|연결|  
|할인|할인 목록|문서 위치|전자 메일 첨부 파일|팔로우|  
|목표|목표 메트릭|가져오기 원본 파일|송장 기재 제품|주문 제품|  
|가격표|큐 항목|견적 제품|롤업 필드|롤업 쿼리|  
|저장된 보기|서비스|서비스 활동|SharePoint 사이트|사이트|  
|지역|단위|단위 그룹|||  
  
## <a name="form-display-faq"></a>양식 표시 FAQ

### <a name="why-is-my-form-not-visible-in-the-form-selector-drop-down-in-my-app"></a>앱의 양식 선택기 드롭 다운에서 양식이 표시되지 않는 이유는 무엇입니까?
양식이 앱에 추가되지 않았기 때문에 사용하지 못할 수 있습니다.
1. 앱 디자이너에서 앱을 엽니다.
2. **엔터티 보기** 영역에서 엔터티 옆에 있는 **양식**을 선택합니다.
3. **구성 요소** 탭에서 앱에 포함된 기본 양식을 확인합니다. 표시하려는 양식이 선택되어 있는지 확인합니다. 그렇지 않은 경우에는 선택하고 저장한 다음 앱을 게시합니다.

   > [!div class="mx-imgBorder"] 
   > ![](media/forms-included-in-app.png "Forms included with app")
   
### <a name="why-isnt-my-form-displayed-as-the-default-form-in-the-app"></a>양식이 앱에서 기본 양식으로 표시되지 않는 이유는 무엇입니까?
양식은 양식 순서 구성을 통해 기본 양식으로 설정하거나 사용자가 기본 양식을 개인 설정으로 설정할 때 사용할 수 있습니다.
1. 솔루션 탐색기를 엽니다. 주문을 원하는 양식이 있는 엔터티를 확장한 다음 **양식**을 선택합니다.
2. 도구 모음에서 **양식 주문** > **기본 양식 집합**을 선택합니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-toolbar.png "Form Order toolbar command")
   
3. 엔터티 양식 순서가 표시됩니다. 양식을 선택하고 위쪽 및 아래쪽 화살표를 사용하여 양식 주문 내에서 양식을 이동합니다. 목록 맨 위에 있는 양식이 기본 양식입니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-dialog.png "Form order dialog")
   
4. **확인** 을 선택하여 양식 순서 변경 내용을 저장합니다.
5. 양식 설계자 도구 모음에서 **게시** 를 선택하여 앱에서 양식 주문을 사용할 수 있도록 합니다.
 
#### <a name="form-order-user-personalization-setting"></a>양식 주문 사용자 개인화 설정
앱 사용자가 앱의 양식 선택기 드롭다운에서 양식 선택을 변경하면 해당 양식이 사용자의 기본 양식이 됩니다. 이 개인 설정은 앱의 엔터티에 대해 지정된 기본 양식을 다시 정의합니다.

   > [!div class="mx-imgBorder"] 
   > ![](media/change-form-user-setting.png "User setting to change default form")
   
### <a name="related-topics"></a>관련 항목  
    
[양식 순서 할당](assign-form-order.md) <br />
[양식에 대한 액세스 제어](control-access-forms.md) <br />
[기본 양식이 여러 클라이언트에 표시되는 방식](main-form-presentations.md) <br />
