---
title: PowerApps에서 모델 기반 앱 기본 양식에 대한 iFrame 속성 | MicrosoftDocs
description: 기본 양식에 대한 iFrame 속성 이해
Keywords: 기본 양식; iFrame 속성; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 1b7e6a0c-18a9-47e2-aa7d-0cffb8c93b19
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 532b720277cdc9649e8ef161e9ff623298c5f570
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754045"
---
# <a name="iframe-properties-for-model-driven-app-main-forms"></a>모델 기반 앱 기본 양식에 대한 iFrame 속성

iFrame을 양식에 추가하여 양식 안에 다른 웹 사이트의 콘텐츠를 통합할 수 있습니다. 

IFrame 속성을 보려면 다음 단계를 수행합니다.

1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 

3. 양식 목록에서 유형 **기본**의 양식을 엽니다. 그런 다음 **삽입** 탭에서 IFRAME을 선택하여 IFRAME 속성을 봅니다.

![IFrame 속성](media/iframe-properties.png)


> [!NOTE]
> 양식은 iFrame 내에 표시되도록 디자인되지 않았습니다.  
  
|탭|속성|설명|  
|---------|--------------|-----------------|  
|**일반**|**이름**|**필수**: iFrame의 고유 이름입니다. 이름에는 영숫자 문자와 밑줄만 사용할 수 있습니다.|  
||**URL**|**필수**: iFrame에 표시할 페이지의 URL입니다.|  
||**레코드 개체 유형 코드 및 고유 식별자를 매개 변수로 전달합니다.**|조직, 사용자 및 레코드에 대한 데이터를 iFrame에 전달할 수 있습니다. 추가 정보: [iFrame에 매개 변수 전달](#pass-parameters-to-iframes) |  
||**레이블**|**필수**: iFrame을 표시하는 레이블입니다.|  
||**양식에 레이블 표시**|레이블을 표시할지 여부를 지정합니다.|  
||**지원되는 경우 프레임 간 스크립팅을 제한합니다.**|다른 웹 사이트의 페이지가 스크립트를 사용하여 Dynamics 365 응용 프로그램과 상호 작용할 수 있는 보안 위험으로 간주됩니다. 이 옵션을 사용하여 제어할 수 없는 페이지의 프레임 간 스크립팅을 제한합니다.<br /><br />|  
||**기본적으로 표시 가능**|iFrame 표시는 선택 사항이며 스크립트를 사용하여 제어할 수 있습니다. 추가 정보: [표시 유형 옵션](visibility-options-legacy.md)|
||**모바일에 사용**|모바일의 iFrame을 활성화하려면 확인란을 선택합니다.|  
|**서식**|**컨트롤이 차지하는 열 수 선택**|iFrame을 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.|  
||**컨트롤에 사용되는 행 수를 선택하십시오.**|컨트롤이 차지하는 행 개수를 지정하여 iFrame의 높이를 제어할 수 있습니다.|  
||**사용 가능한 공간을 사용할 수 있도록 자동으로 확장합니다.**|행 개수를 설정하여 높이를 설정하는 대신 iFrame 높이를 사용 가능한 공간으로 확장할 수 있습니다.|  
||**iFrame의 스크롤 유형 선택**|다음 세 가지 옵션이 있습니다.<br /><br /> - **필요한 경우**: iFrame의 크기가 사용 가능한 공간보다 클 때 스크롤 막대를 표시합니다.<br />- **항상**: 항상 스크롤 막대를 표시합니다.<br />- **사용 안 함**: 스크롤 막대를 표시하지 않습니다.|  
||**테두리 표시**|iFrame의 테두리를 표시합니다.|  
|**종속성**|**종속 필드**|iFrame은 스크립트를 사용하여 양식에서 필드와 상호 작용할 수 있습니다. 필드가 양식에서 제거되면 iFrame의 스크립트가 작동하지 않습니다. 실수로 제거되지 않도록 iFrame의 스크립트에서 참조되는 필드를 **종속 필드**에 추가합니다.|  
  
## <a name="pass-parameters-to-iframes"></a>iFrame에 매개 변수 전달  
 레코드에 대한 정보는 **레코드 개체 유형 코드 및 고유 식별자를 매개 변수로 전달합니다.** 옵션을 사용하여 전달할 수 있습니다. 전달된 값은 다음과 같습니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`orglcid`|조직 기본 언어 LCID입니다.|  
|`orgname`|조직의 이름입니다.|  
|`userlcid`|사용자의 선호 언어 LCID|  
|`type`|엔터티 유형 코드입니다. 이 값은 다른 조직의 사용자 지정 엔터티와 다를 수 있습니다. 대신 `typename`을 사용합니다.|  
|`typename`|엔터티 유형 이름입니다.|  
|`id`|레코드의 id 값입니다. 이 매개 변수에는 엔터티 레코드를 저장할 때까지 값이 없습니다.|  

## <a name="next-steps"></a>다음 단계

[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
