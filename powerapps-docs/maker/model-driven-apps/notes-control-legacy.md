---
title: Power Apps에서 게시물에 대한 정보 액세스를 위한 모델 기반 앱 메모 컨트롤 설정 | MicrosoftDocs
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 52edc0881484d092332cc2ab5a3892d0f7983e30
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862979"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>게시물에 대한 정보 액세스를 위한 모델 기반 앱 메모 컨트롤 설정

 [업데이트된 양식](main-form-presentations.md#updated-forms)을 사용하는 특정 시스템 엔터티의 Power Apps 양식에서 메모 컨트롤은 **게시물**, **활동** 및 **메모**에 대한 정보에 액세스할 수 있는 기능을 제공합니다. 메모 및 활동이 활성화된 사용자 지정 엔터티의 경우 **메모** 및 **활동**만 표시됩니다. **게시물**을 포함하려면 사용자 지정 엔터티에 대한 게시물을 활성화해야 합니다.  
  
## <a name="enable-posts-for-a-custom-entity"></a>사용자 지정 엔터티에 대한 게시물 사용  
  
1.  **[설정](advanced-navigation.md#settings)** > **작업 피드 구성**으로 이동합니다. 
  
2.  사용자 지정 엔터티에 대한 레코드를 엽니다.  
  
3.  **이 유형의 레코드 양식에 대해 담벼락 설정**이 선택되어 있는지 확인하고 레코드를 저장합니다.  
  
4.  명령 모음에서 **활성화**를 선택합니다.  
  
5.  담벼락을 사용해야 할 경우 엔터티를 게시해야 합니다.  
  
 기본적으로 시스템 엔터티의 경우 메모 컨트롤은 양식의 맨 위에 있는 3열 탭 가운데 소셜 창 섹션에 배치됩니다. 한 번만 양식에 나타날 수 있습니다. 메모 컨트롤을 이동하거나 제거할 수 있습니다. 다시 추가하려면 **삽입** 탭의 **컨트롤** 그룹에서 **메모** 단추를 사용합니다.  
  
 다음 표는 메모 컨트롤의 속성을 설명합니다.  
  
|탭|속성|설명|  
|---------|--------------|-----------------|  
|**표시**|**레이블**|**필수**: 기본적으로 레이블이 표시되지 않지만 레이블이 필요합니다.|  
||**양식에 레이블 표시**|레이블을 표시하도록 선택할 수 있습니다.|  
||**양식에서 필드 잠그기**|그러면 실수로 양식에서 메모를 제거하지 못하도록 합니다.|  
||**기본 탭**|기본적으로 어떤 탭을 표시할지 선택합니다. 옵션은 다음과 같습니다.<br /><br /> - **활동**<br />- **게시물**<br />- **메모**|  
|**서식**|**컨트롤이 차지하는 열 수 선택**|메모 컨트롤을 포함하는 섹션에 둘 이상의 열이 있으면 섹션에 사용된 열 수까지 차지하도록 필드를 설정할 수 있습니다.|  
||**행 개수**|컨트롤이 차지하는 행 개수를 선택하여 메모 컨트롤의 높이를 제어합니다.|  
||**사용 가능한 공간을 사용할 수 있도록 자동으로 확장합니다.**|행 개수를 설정하여 높이를 설정하는 대신 메모 컨트롤 높이를 사용 가능한 공간으로 확장할 수 있습니다.|  
  
## <a name="next-steps"></a>다음 단계
[양식 편집기 열기](open-form-editor.md)
