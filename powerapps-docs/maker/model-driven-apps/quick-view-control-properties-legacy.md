---
title: PowerApps에서 모델 기반 앱 기본 양식의 빠른 보기 컨트롤 속성 | MicrosoftDocs
description: 기본 양식의 빠른 보기 컨트롤 속성 이해
Keywords: 빠른 보기 컨트롤 속성; Dynamics 365; 기본 양식
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 10/28/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b2d4a8f55bf9b6f3e54f948ad16be36fdecb6d20
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755098"
---
# <a name="model-driven-app-quick-view-control-properties"></a>모델 기반 앱 빠른 보기 컨트롤 속성

모델 기반 앱 양식의 빠른 보기 컨트롤은 양식의 조회에서 선택한 레코드의 데이터를 표시합니다. 컨트롤에 표시되는 데이터는 빠른 보기 양식을 사용하여 정의됩니다. 표시되는 데이터는 편집할 수 없지만 기본 필드가 빠른 보기 양식에 포함되어 있으면 관련 레코드를 여는 링크가 됩니다. 추가 정보: [빠른 보기 양식 만들기 및 편집](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![거래처 양식의 연락처 빠른 보기 양식](media/quick-view-form-contact.png "거래처 양식의 연락처 빠른 보기 양식")  

PowerApps 사이트에서 **빠른 보기 컨트롤 속성**에 액세스할 수 있습니다. 
1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  


2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 

3. 양식 목록에서 유형 **기본**의 양식을 엽니다. 그런 다음 **삽입** 탭에서 **빠른 보기 양식**을 선택하여 빠른 보기 컨트롤 속성을 봅니다.

    ![빠른 보기 컨트롤](media/quick-view-control.png)
  
|속성|설명|  
|--------------|-----------------|  
|**이름**|**필수**: 스크립트에서 참조할 때 사용되는 빠른 보기 양식의 고유 이름입니다.|  
|**레이블**|**필수**: 빠른 보기 양식을 표시하는 레이블입니다.|  
|**양식에 레이블 표시**|양식에 레이블을 표시합니다.|  
|**조회 필드**|양식에 포함된 조회 필드 중 하나를 선택합니다.|  
|**관련 엔터티**|이 값은 선택한 **조회 필드**에 따라 다릅니다. 일반적으로 조회에 대한 1:N 엔터티 관계의 기본 엔터티입니다.<br /><br /> 엔터티에 거래처 또는 연락처를 허용할 수 있는 **잠재 고객** 조회가 포함되면 이 값을 변경하여 **빠른 보기 양식** 필드에서 거래처 및 연락처 둘 다에 대해 빠른 보기 양식을 선택한 후 다른 빠른 보기 양식을 선택할 수 있습니다.|  
|**빠른 보기 양식**|**관련 엔터티**에 빠른 보기 양식이 있을 경우 여기에서 선택할 수 있습니다. 그렇지 않으면 **새로 만들기**를 선택하여 새로 만듭니다.<br /><br /> **편집**을 선택하여 선택한 빠른 보기 양식을 변경합니다.|  
|**추가 속성**|확인란을 선택하여 기본 렌더링 스타일을 지정할 수 있습니다.|

## <a name="next-steps"></a>다음 단계

[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
 
