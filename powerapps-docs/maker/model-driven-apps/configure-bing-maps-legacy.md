---
title: Power Apps에서 모델 기반 앱의 Bing 지도 구성 | MicrosoftDocs
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: f9729664-561c-4758-86ce-7216d68075d9
caps.latest.revision: 63
ms.author: matp
author: Mattp123
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 132f5c2cfb5763714176a86c1ea846085588f862
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875229"
---
# <a name="configure-a-map-on-a-form"></a>양식에서 지도 구성
기본적으로 Bing 지도 컨트롤은 거래처 및 연락처 엔터티에 대한 기본 양식으로 구성되어 엔터티 레코드에 지도를 표시할 수 있습니다. 기본적으로 구성되어 있지는 않지만 Bing 지도 컨트롤을 시스템 사용자 엔터티에 추가할 수 있습니다. Bing 지도 컨트롤은 Dynamics 365 Sales 및 Dynamics 365 Customer Service와 같이 Dynamics 365의 모델 기반 앱에 포함된 일부 엔터티와 함께 사용할 수도 있습니다. 예를 들면 잠재 고객, 견적, 주문, 송장 및 경쟁 업체 등입니다. Bing 지도 컨트롤은 사용자 지정 엔터티와 함께 사용할 수 없습니다.  

활성화된 경우 지도는 주어진 레코드의 주소 복합 필드에 지정된 위치를 표시합니다. 

> [!div class="mx-imgBorder"] 
> ![앱의 Bing 지도 컨트롤](media/bing-map-example.png "앱의 Bing 지도 컨트롤")

> [!IMPORTANT]
> 지도를 사용하려면 양식의 Bing 지도 표시 시스템 설정을 활성화해야 합니다. 추가 정보: [환경에 지도를 사용하도록 설정](#enable-maps-for-your-environment)

양식 편집기에서 지도 영역을 제거하거나 클래식 양식 편집기의 **삽입** 탭에서 **Bing 지도** 단추를 사용하여 다시 추가할 수 있습니다.

## <a name="enable-maps-for-your-environment"></a>환경에 지도를 사용하도록 설정
1. 모델 기반 앱을 연 다음 **설정** > **고급 설정**을 선택합니다. 
2. **설정** > **관리** > **시스템 설정**을 선택합니다. 
3. **일반** 탭에서 **양식에 Bing지도 표시**를 선택한 다음 **승인**을 선택합니다. 
 
    ![양식에서 지도 사용](media/enable-maps.png)

## <a name="configure-a-map"></a>지도 구성 
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
2. **데이터** > **엔터티**로 이동한 다음 기본 양식에서 지도를 구성할 엔터티를 선택하십시오. 
3. **양식** 탭을 선택한 다음 기본 양식을 선택하고 명령 모음에서 **클래식으로 전환**을 선택합니다. 
4. 클래식 양식 디자이너에서 **지도 보기** 컨트롤을 두 번 클릭하여 속성을 보고 편집할 수 있습니다. 추가 정보: [지도 속성 보기 및 편집](#view-and-edit-map-properties)

    ![지도 보기 컨트롤](media/map-view-control.png)

양식에서 지도 컨트롤을 제거하려면 **지도 보기** 컨트롤을 선택한 다음 Delete 키를 누릅니다.

## <a name="view-and-edit-map-properties"></a>지도 속성보기 및 편집

|      탭       |                        속성                         |                                                                                                  설명                                                                                                   |
|----------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **일반**   |                        **레이블**                        |                                                                              **필수**: Bing 지도를 표시하는 레이블입니다.                                                                               |
|                |              **양식에 레이블 표시**              |                                                                                     레이블을 표시할지 여부를 지정합니다.                                                                                     |
|                | **Bing 지도 컨트롤에 사용할 주소 선택** |                                                                        지도에 대한 데이터를 제공하기 위해 사용해야 할 주소를 선택합니다.                                                                        |
|                |                 **기본적으로 표시 가능**                  | Bing 지도 표시는 선택 사항이며 비즈니스 규칙 또는 스크립트를 사용하여 제어할 수 있습니다. 추가 정보: [표시 유형 옵션](visibility-options-legacy.md) |
| **서식** |  **컨트롤이 차지하는 열 수 선택**  |                              Bing 지도를 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.                              |
|                |   **컨트롤에 사용되는 행 수를 선택하십시오.**    |                                                                  행 개수를 지정하여 Bing 지도의 높이를 제어할 수 있습니다.                                                                   |
|                |     **사용 가능한 공간을 사용할 수 있도록 자동으로 확장합니다.**     |                                                                        Bing 지도 높이를 사용 가능한 공간으로 확장할 수 있습니다.                                                                        |

### <a name="see-also"></a>참조
[모델 기반 앱 양식 만들기 및 디자인](create-design-forms.md) 
