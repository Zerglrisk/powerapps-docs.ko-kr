---
title: Power Apps의 모델 기반 앱 기본 양식에 대한 하위 표 | MicrosoftDocs
description: 기본 양식에 대한 하위 표 속성 이해
Keywords: 기본 양식; 하위 표 속성; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/07/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 82892cd3-3436-4677-b96b-f2ccd0a4f078
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ff9b79565525cee42eedfcd48c59669c4fe277d8
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2872832"
---
# <a name="sub-grid-properties-for-model-driven-app-main-forms-overview"></a>모델 기반 앱 기본 양식에 대한 하위 표 속성 개요

레코드 또는 차트의 목록을 표시하려면 양식에 하위 표를 구성할 수 있습니다. **표시** 탭에서 **차트만 표시**를 선택하여 목록 대신 차트를 표시합니다.  

Power Apps 사이트에서 **하위 표 속성**에 액세스할 수 있습니다. 
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 사이트에서 **모델 기반**(탐색 창의 왼쪽 아래)을 선택합니다.  

     ![모델 기반 디자인 모드](media/model-driven-switch.png)

2.  **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다. 

3.  양식 목록에서 유형 **기본**의 양식을 엽니다. 그런 다음 **삽입** 탭에서 **하위 표**를 선택하여 하위 표 속성을 봅니다.

    ![하위 표 속성](media/sub-grid-properties.png)
  
|탭|속성|설명|  
|---------|--------------|-----------------|  
|**표시**|**이름**|**필수**: 스크립트에서 참조할 때 사용되는 하위 표의 고유 이름입니다. 이름에는 영숫자 문자와 밑줄만 사용할 수 있습니다.|  
||**레이블**|**필수**: 사용자에게 표시되는 하위 표에 대해 지역화할 수 있는 레이블입니다.|  
||**양식에 레이블 표시**|양식에 레이블을 표시할지 여부를 지정합니다. **검색 상자 표시**를 사용할 경우 필요합니다. 패널 머리글 색을 선택할 수도 있습니다.|  
||**레코드**|두 가지 옵션 중에서 선택합니다.<br /><br /> - **관련 레코드만**: 하위 표는 현재 레코드와 관련된 레코드만 표시합니다.<br />- **모든 레코드 종류**: 하위 표는 기본 보기 또는 보기 선택기를 사용하는 경우 사용자가 선택한 모든 보기로 필터링된 레코드를 표시합니다.<br /><br /> 선택한 옵션은 목록 컨트롤 표시 동작에 영향을 줍니다. 추가 정보: [목록 표시 동작](#show-list-behavior) |  
||**엔터티**|**레코드**에 대해 선택한 옵션에 따라 이 목록은 둘 중 하나를 표시합니다.<br /><br /> - **관련 레코드만**: 괄호로 관계를 정의하는 해당 엔터티에 대해 조회 필드의 이름을 사용하여 이 엔터티와 관련된 엔터티 목록을 표시합니다.<br />- **모든 레코드 종류**: 모든 엔터티 목록입니다.|  
||**기본 보기**|기본적으로 적용되는 보기를 선택합니다. **보기 선택** 속성을 사용하여 다른 보기를 사용하도록 설정하지 않은 경우입니다. 이 보기가 유일한 보기가 됩니다.<br /><br /> **편집** 단추를 사용하여 편집할 기본 보기를 엽니다. **새로 만들기** 단추를 사용하여 새 보기를 만들어 이 하위 표에 사용합니다.|  
||**검색 상자 표시**|검색 상자를 표시합니다. 이 옵션을 선택하면 **양식에 레이블 표시** 옵션이 필요합니다.|  
||**색인 표시**|[클래식 양식](main-form-presentations.md#classic-forms)을 사용하는 양식만 색인 표시를 지원합니다.<br /><br /> 목록에서 사전순 색인을 사용하려면 이 확인란을 선택합니다. 그러면 특정 문자 또는 숫자로 시작하는 레코드로 이동할 수 있습니다.|  
||**보기 선택**|다음 세 가지 옵션이 있습니다.<br /><br /> - **끄기**: 기본 보기만 사용할 수 있습니다.<br />- **모든 보기 표시**: 사용자가 아무 보기나 선택할 수 있습니다.<br />- **선택한 보기 표시**: 커서와 Ctrl 키를 사용하여 표시할 사용 가능한 보기를 선택합니다.|  
||**기본 차트**|**차트만 표시**를 선택한 경우 표시할 차트를 선택합니다.|  
||**차트만 표시**|레코드 목록이 아니라 차트가 표시됩니다.|  
||**차트 선택 표시**|**차트만 표시**를 선택한 경우 사용자는 다른 차트를 선택할 수 있습니다.|  
||**사용 가능성**|섹션을 전화에서 사용할 수 있어야 하는지 여부를 지정합니다.|
|**서식**|**레이아웃**|**컨트롤이 차지하는 열 수 선택**.<br /><br /> 하위 필드를 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.|  
||**행 레이아웃**|**행 개수**는 하위 표의 페이지에 표시되는 레코드 수를 결정합니다.<br /><br /> **사용 가능한 공간을 사용할 수 있도록 자동으로 확장합니다.** 가 선택되면 양식에서는 레코드 두 개에 대한 공간을 허용하고 레코드 수가 증가할 때 공간을 확장합니다. 그 수가 **행 개수**를 초과하면 추가 페이지로 이동하여 레코드를 볼 수 있습니다.<br /><br /> **사용 가능한 공간을 사용할 수 있도록 자동으로 확장합니다.** 가 선택되어 있지 않으면 양식에서는 **행 개수**에 정의된 레코드 수만큼의 공간을 제공하고 사용자는 추가 페이지로 이동하여 추가 레코드를 볼 수 있습니다.|  
|**컨트롤**|**컨트롤**|컨트롤을 추가하고 웹, 전화 또는 태블릿에 대한 라디오 단추를 선택합니다.|
  
 양식에서 [클래식 양식](main-form-presentations.md#classic-forms)을 사용하면 에서처럼 하위 표에서 수행되는 작업은 리본에서 사용할 수 있습니다. 개발자가 이러한 작업의 동작을 사용자 지정하거나 리본을 사용자 지정하여 추가 작업을 추가할 수 있습니다.  
  
 [업데이트된 양식](main-form-presentations.md#updated-forms)을 사용하는 양식에서 하위 표에 대한 작업은 쉽게 액세스할 수 있도록 하위 표 근처에 배치됩니다. 그러나 명령 모음에서는 사용자 지정 작업을 추가할 수 없습니다. 개발자는 리본을 편집하여 나머지 세 작업(목록 표시, 레코드 추가 및 레코드 삭제)에 대한 작업을 수정할 수 있습니다.  
  

## <a name="show-list-behavior"></a>목록 표시 동작  
 [업데이트된 양식](main-form-presentations.md#updated-forms)을 사용하여 양식에 목록을 표시할 경우 각 하위 표는 엔터티도 양식 편집기의 탐색 영역에 포함되는 엔터티 중 하나로 표시되는 오른쪽 위에 **보기 열기** 단추 ![보기 열기 단추](media/crm-itpro-cust-openview.PNG "보기 단추 열기")를 표시합니다. 이 단추를 선택하면 보기가 열립니다. 동작은**레코드** 속성에서 선택한 옵션에 따라 변합니다.  
  
 **관련 레코드만**을 선택하면 보기는 같은 창에서 관련 보기 중 하나를 사용하여 열립니다. 양식으로 돌아가려면 뒤로 단추를 사용하거나 탐색 모음에서 현재 레코드 기본 이름 값을 선택합니다.  
  
 **모든 레코드 종류**를 선택하여 보기가 새 창에서 열립니다.  

## <a name="add-record-behavior"></a>레코드 추가 동작  
 [업데이트된 양식](main-form-presentations.md#updated-forms)을 사용하여 양식에 목록을 표시할 경우 각 하위 표는 하위 표의 오른쪽 위에 **레코드 추가** 단추 ![추가 단추](media/crm-itpro-cust-subgridadd.PNG "추가 단추")를 표시합니다. 이 단추를 선택하면 레코드를 추가할 수 있습니다. 이 동작은 **레코드** 속성에서 선택한 옵션과 활동 레코드에 대한 조회인지에 따라 달라집니다.  
  
 **관련 레코드만**을 선택하면 기본 동작은 기본 레코드를 추가하는 동작입니다. 사용자는 기존 레코드를 먼저 검색하기 위해 인라인 조회를 봅니다. 이렇게 하면 중복 레코드를 만드는 것을 방지합니다.  기존 레코드를 찾을 수 없으면 **새로 만들기** 옵션을 선택할 수 있습니다. 새 레코드를 만들 때 관계에서 정의된 필드 매핑이 적용됩니다. 추가 정보: [지도 엔터티 필드](../common-data-service/map-entity-fields.md)   
  
 **모든 레코드 종류**를 선택하면 기본 동작은 새 레코드를 추가하는 것입니다. 대상 엔터티에 빨리 만들기 양식이 있으면 표시됩니다. 그렇지 않은 경우에는 기본 엔터티 기본 양식이 표시됩니다.  
  
 하위 표에 활동이 표시되면 활동 유형을 선택해야 "새 레코드 추가" 동작이 표시됩니다.  
  
## <a name="delete-record-behavior"></a>레코드 삭제 동작  
 하위 레코드에서 레코드를 선택하면 **삭제** 단추 ![하위 목록 삭제 아이콘](media/crm-itpro-cust-subgriddelete.PNG "하위 목록 삭제 아이콘")가 행의 오른쪽에 나타납니다. 이 삭제 작업의 동작은 현재 엔터티를 사용하는 관계 유형에 따라 다릅니다.  
  
 하위 표에서 1:N(일대다) 관계를 사용하면 일반적인 레코드 삭제 동작은 레코드를 삭제하기 전에 확인 대화 상자를 표시합니다.  
  
 하위 표에서 N:N(다대다) 관계를 사용하면 두 레코드와 관련된 관계(또는 교차) 엔터티의 레코드가 확인 없이 삭제되고 해당 레코드는 하위 표에 더 이상 표시되지 않습니다. 하지만 표시된 레코드는 삭제되지 않습니다.  

## <a name="next-steps"></a>다음 단계

[주요 양식 및 구성 요소 사용하기](use-main-form-and-components.md)
