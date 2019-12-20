---
title: Power Apps의 모델 기반 앱 양식 내에서 탐색 변경 | MicrosoftDocs
description: 양식 내에서 탐색을 변경하는 방법에 대해 알아보기
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 4c379202-9f0e-4003-a49c-efff53e7f79f
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 92d76b056c21ebe583679bc51b73b04dcf812e69
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867594"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>모델 기반 앱 양식 내에서 탐색 변경

 양식 내 탐색 컨트롤이 있으면 앱 사용자가 관련 레코드 목록을 볼 수 있습니다. 각 엔터티 관계에는 표시 여부를 제어하는 속성이 있습니다. 추가 정보: [기본 엔터티에 대한 탐색 창 항목](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 표시되도록 구성되어 있는 모든 엔터티 관계는 양식 편집기에서 재정의할 수 있습니다. 양식 탐색을 통해 다른 웹 사이트 또는 웹 리소스를 표시하도록 탐색 링크를 포함할 수 있습니다.  
  
 단계별 지침은 [Common Data Service용 엔터티 관계 만들기 및 편집](../common-data-service/create-edit-entity-relationships.md)을 참조하십시오.  
  
 탐색을 편집할 수 있으려면 먼저 양식 디자이너의 **홈** 탭의 **선택** 그룹에서 **탐색**을 선택해야 합니다.  
 
> [!div class="mx-imgBorder"] 
> ![탐색 명령](media/navigation-command.png)
 
 오른쪽 창의 **관계 탐색기**에서 1:N(일대다) 또는 N:N(다대다) 관계로 필터링하거나 사용 가능한 모든 관계를 볼 수 있습니다. **사용되지 않는 관계만 표시** 확인란이 비활성화되어 있고 선택되어 있습니다. 따라서 각 관계를 한 번만 추가할 수 있습니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![관계 탐색기](media/relationship-explorer.png)

 **관계 탐색기**에서 관계를 추가하려면 관계를 두 번 클릭하기만 하면 탐색 영역에서 현재 선택된 관계 아래에 추가됩니다. 탐색 영역에서 관계를 두 번 클릭하면 **표시** 탭의 레이블을 변경할 수 있습니다. **이름** 탭에서 관계에 대한 정보를 볼 수 있습니다. **편집** 단추를 사용하여 엔터티의 정의를 엽니다.  
  
 탐색 영역에는 5개의 그룹이 있습니다. 끌어서 위치를 변경하고 두 번 클릭하여 레이블을 변경할 수 있지만 제거할 수 없습니다. 이러한 그룹은 그 안에 내용이 있는 경우에만 표시됩니다. 따라서 그룹을 표시하지 않으려면 아무 것도 추가하지 마십시오.  
  
 **삽입** 탭의 **컨트롤** 그룹에서 **탐색 링크** 단추를 사용하여 링크를 웹 리소스 또는 외부 URL에 추가합니다.  
 
 ![탐색 링크](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>탐색 링크 속성  
 탐색 링크에는 다음과 같은 속성이 있습니다.  
  
|속성|설명|  
|--------------|-----------------|  
|이름|**필수**: 레이블로 표시할 텍스트입니다.|  
|아이콘|32x32 픽셀 웹 리소스를 사용합니다. 투명 배경의 PNG 이미지를 사용하는 것이 좋습니다.|  
|웹 리소스|양식의 기본 창에 표시할 웹 리소스를 지정합니다.|  
|외부 URL|양식의 기본 창에 표시할 페이지의 URL을 지정합니다.|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>개인정보취급방침  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>다음 단계

[양식 편집기 사용자 인터페이스 개요](form-editor-user-interface-legacy.md)
