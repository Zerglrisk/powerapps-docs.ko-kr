---
title: 조직의 브랜드와 일치하도록 색 구성표를 변경하거나 로고 추가 | MicrosoftDocs
ms.custom: ''
ms.date: 02/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 21a166a0-d25e-4260-a1e4-2ddc528787c2
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1919084b26cb7605b2c32e8569df8ab31fb857a3
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875097"
---
# <a name="create-a-theme"></a>테마 만들기

사용자 지정되지 않은 시스템에서 제공하는 기본 색상과 시각적 요소를 변경하여 앱에 대한 사용자 지정 모양과 느낌(테마)을 만들 수 있습니다. 예를 들어, 회사 로고를 추가하고 엔터티 특정 컬러를 제공하여 개인 제품 브랜드를 만들 수 있습니다. 테마는 개발자가 코드를 작성할 필요 없이 사용자 인터페이스의 사용자 지정 도구를 사용하여 만듭니다. 조직에 사용되는 테마를 만들거나, 변경하거나, 삭제할 수 있습니다. 테마 사용자 지정은 Dynamics 365 for Outlook의 웹 양식에서 지원됩니다. 여러 테마를 정의할 수 있지만 기본 테마로 하나만 설정하고 게시할 수 있습니다.  
  
<a name="UseThemes"></a>   
## <a name="use-themes-to-enhance-the-user-interface-and-create-your-product-branding"></a>테마를 사용하여 사용자 인터페이스를 향상시키고 제품 브랜드를 만들기  
 테마는 획기적인 변경 없이 앱 사용자 인터페이스를 향상시키는 데 사용됩니다. 테마 색상은 응용 프로그램 전체에 전체적으로 적용됩니다. 예를 들어, UI에서 다음 시각적 요소를 향상 시킬 수 있습니다.  
  
-   제품 로고 및 탐색 색상을 변경하여 제품 브랜드 만들기  
  
-   호버 또는 선택 색상 같은 강조 색상 조정  
  
-   엔터티 고유 색상 제공  
    
-   로고  
  
-   로고 도구 설명  
  
-   탐색 모음 색  
  
-   탐색 모음 보조 색

-   통합 인터페이스의 주요 명령 모음 색상
  
-   머리글 색  
  
-   전역 링크 색  
  
-   선택한 링크 효과  
  
-   링크 가리키기 효과  
  
-   레거시 테마 색(프로세스 컨트롤에 사용할 기본 배경)  
  
-   기본 엔터티 색  
  
-   기본 사용자 지정 엔터티 색  
  
-   컨트롤 음영  
  
-   컨트롤 테두리  
  
<a name="Solution"></a>   
## <a name="solution-awareness"></a>솔루션 인식  
 테마는 솔루션 인식이 아닙니다. 조직의 테마 변경은 조직에서 내보내는 솔루션에는 포함되지 않습니다. 데이터는 테마 엔터티에 저장되며 다른 환경에서 내보내고 다시 가져올 수 있습니다. 가져온 테마를 적용하려면 게시해야 합니다.  
  
<a name="CloneAlter"></a>   
## <a name="copy-and-alter-the-existing-theme"></a>기존 테마 복사 및 변경  
 새로운 테마를 만드는 가장 쉽고 빠른 방법은 기존 테마를 복제하고 변경한 다음 저장하고 미리 보고 게시하는 것입니다. 
 
1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

2.  **모델 기반**(왼쪽 아래). 

3.  ![설정 아이콘](../model-driven-apps/media/powerapps-gear.png)(오른쪽 상단) > **고급 사용자 지정**를 선택합니다. 

4. **테마**에서 **모든 테마**를 선택합니다. 

5. **CRM 기본 테마**를 선택합니다. 

다음 스크린샷은 기본 테마 설정의 일부를 보여줍니다.  

> [!div class="mx-imgBorder"] 
> ![기본 테마](media/default-theme.png) 
  
 기본 테마를 복제하고 색을 변경합니다. 다음 스크린샷은 탐색 및 강조 표시에 대한 새로운 색상을 보여줍니다. 제품에 대한 새 로고를 선택할 수도 있습니다.  
  
 다음 스크린샷은 새로운 탐색 색상을 보여줍니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![부드러운 녹색 테마 색](media/theme-gentle-green.png "부드러운 녹색 테마 색")  
  
 다음 스크린샷은 새로운 강조 표시 색상과 함께 계정 엔터티 표를 보여줍니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![부드러운 녹색 테마 거래처 표](media/themes-gentle-green-account-grid.png "부드러운 녹색 테마 거래처 표")  
  
<a name="Publish"></a>   
## <a name="preview-and-publish-a-theme"></a>테마 미리 보기 및 게시  
 테마를 미리 보고 게시하려면 다음 단계를 수행하십시오.  
  
-   처음부터 새 테마를 만들거나 기존 테마를 복제합니다.  
  
-   명령 모음에서 **미리 보기**를 선택하여 새 테마를 미리 봅니다. 미리 보기를 끝내려면 명령 모음에서 **미리 보기** 단추 옆의 **미리 보기 끝내기**를 선택합니다.  
  
-   테마를 게시합니다. 명령 모음에서 **테마 게시**를 선택합니다.  
  
 다음 스크린샷은 미리 보기 및 게시에 대한 명령 모음의 단추를 보여 줍니다.  
  
 ![미리 보기 단추를 사용하여 미리 보기 모드를 입력/종료](media/themes-preview-buttons.PNG "미리 보기 단추를 사용하여 미리 보기 모드를 입력/종료")  
  
<a name="BestPracticies"></a>   
## <a name="best-practices"></a>유용한 정보  
 다음은 테마 대비를 디자인하고 색상을 선택하기 위한 권장 사항입니다.  
  
### <a name="theme-contrast"></a>테마 대비  
 다음과 같은 방법을 사용하여 대비 색상을 제공하는 것이 좋습니다.  
  
-   대비 색상을 신중하게 선택합니다. Common Data Service 기본 제공 테마에는 최적의 사용을 위해 올바른 대비 비율로 되어 있습니다. 새로운 테마에 유사한 비율을 사용합니다.  
  
-   고대비 모드의 경우 기본 색 설정을 사용합니다.  
  
### <a name="theme-colors"></a>테마 색  
 너무 많은 수의 다른 색을 사용하지 않는 것이 좋습니다. 모든 엔터티에 대해 다른 색을 설정할 수 있지만 두 패턴 중 하나를 사용하는 것이 좋습니다.  
  
-   모든 엔터티를 무채색으로 만들고 키 엔터티를 강조 표시합니다.  
  
-   큐와 큐 항목 또는 제품 카탈로그 엔터티 같이 비슷한 엔터티 또는 관련 엔터티에 대해 같은 색상을 사용합니다. 그룹의 총 수를 낮게 유지합니다.  
  
<a name="Considerations"></a>   
## <a name="custom-theme-considerations"></a>사용자 지정 테마 고려 사항  
 사용자 지정 테마 사용을 계획할 때 다음을 고려해야 합니다.  
  
-   최신 업데이트된 사용자 인터페이스(UI) 영역은 사용자 지정 테마 색으로 표시됩니다.  
  
-   테마 색상은 응용 프로그램 전체에 전역적으로 적용되지만 그라데이션 단추 같은 일부 레거시 UI 영역은 기본 색상을 유지합니다.  
  
-   특정 영역은 기본 아이콘 색상과 대비를 이루도록 진하거나 밝은 색상을 사용해야 합니다. 아이콘 색은 사용자 지정할 수 없습니다.  
  
-   엔터티는 다른 사이트 맵 노드 아래에서 다른 색으로 표시할 수 없습니다.  
  
-   사이트 맵 노드의 색은 사용자 지정할 수 없습니다.  
  
## <a name="see-also"></a>참조  
         
 [비디오: 테마](https://go.microsoft.com/fwlink/p/?LinkId=529568) [조직 테마 쿼리 및 편집](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme)

