---
title: Power Apps에서 모델 기반 앱 양식 성능 최적화 | MicrosoftDocs
description: 양식이 느리게 로드되도록 하는 양식 디자인을 피하는 방법 알아보기
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5df20edea9440d407c75b114d24dcb3c0f39306a
ms.sourcegitcommit: 5e6d71967902c463f34a9254f988b9c10e431eb4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "2890662"
---
# <a name="optimize-model-driven-app-form-performance"></a>모델 기반 앱 양식 성능 최적화

느리게 로드되는 양식은 생산성과 사용자 채택을 줄일 수 있습니다. 다음 권장 사항을 따라 양식을 빠르게 로드하는 방법을 극대화합니다. 이러한 권장 사항의 대부분은 개발자가 조직의 양식 스크립트를 구현할 수 있는 방법에 대한 것입니다. 양식의 양식 스크립트를 만든 개발자와 이러한 권장 사항에 대해 의논해야 합니다.  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>양식 디자인  
 사용자와 양식의 상호 작용과 그 안에 표시되어야 하는 데이터 양을 생각해 봅니다.  
  
 **필드 수 최소로 유지**  
 양식에 필드가 많을 수록 각 레코드를 표시하기 위해 인터넷이나 인트라넷을 통해 전송해야 하는 데이터가 더 많습니다.
 
 **성능을 위한 디자인**  
 양식과 페이지를 디자인할 때 사용자가 가장 쉽게 액세스할 수 있도록 맨 위에 가장 중요한 것을 배치하십시오. 자주 사용하지 않는 구성 요소를 양식의 다른 탭으로 이동하고, 구성 요소를 표시하거나 숨기는 대신 역할 기반 양식을 사용하고, 다른 워크플로에 전용 대시보드와 보기가 있는지 확인하십시오. 섹션을 사용하여 컨트롤을 구성하십시오. 이렇게 하면 양식 속도가 느려지지 않습니다.
 
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>양식 스크립트  
 양식 스크립트를 사용하는 사용자 지정 항목이 있을 경우 개발자가 이러한 전략을 이해하여 성능을 향상시킬 수 있어야 합니다.  
  
 **불필요한 JavaScript 웹 리소스 라이브러리 포함 방지**  
 양식에 스크립트를 더 많이 추가할 수록 다운로드하는 데 더 많은 시간이 걸립니다. 일반적으로 스크립트는 처음 로드된 후 브라우저에 캐시되지만 양식이 처음으로 표시될 때의 성능은 종종 상당한 인상을 불러일으킵니다.  
  
 **Onload 이벤트 시 모든 스크립트 로드 방지**  
 필드에 대한 `OnChange` 이벤트 또는 `OnSave` 이벤트만 지원하는 코드가 있을 경우 `OnLoad` 이벤트 대신 해당 이벤트의 이벤트 처리기로 스크립트 라이브러리를 설정하도록 합니다. 이 방식으로 해당 라이브러를 로드하면 지연되거나 양식이 로드될 때 성능이 향상될 수 있습니다.  
  
 **축소된 탭을 사용하여 웹 리소스 로드 지연**  
 웹 리소스 또는 IFRAMES가 축소된 탭 안의 섹션에 포함되어 있으면 탭이 축소되면 로드되지 않습니다. 탭이 확장되면 로드됩니다. 탭 상태가 변경되면 `TabStateChange` 이벤트가 발생합니다. 축소된 탭 안의 웹 리소스 또는 IFRAME을 지원하는 데 필요한 코드는 **TabStateChange** 이벤트에 대해 이벤트 처리기를 사용할 수 있고 `OnLoad` 이벤트에서 발생하는 코드를 줄일 수 있습니다.  
  
 **기본 표시 유형 옵션 설정**  
 양식 요소를 숨기는 `OnLoad` 이벤트에서 양식 스크립트를 사용하지 않도록 합니다. 양식이 로드될 때 기본적으로 표시되지 않고 숨길 수 있는 양식 요소에 대해 기본 표시 유형 옵션을 설정합니다. 그런 다음 `OnLoad` 이벤트에서 스크립트를 사용하여 표시하려는 양식 요소를 표시합니다.  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>명령 모음 또는 리본  
 명령 모음이나 리본을 편집할 때 다음 권장 사항을 고려해야 합니다.  
  
 **컨트롤 수 최소로 유지**  
 양식의 명령 모음 또는 리본 안에서 필요한 컨트롤을 평가하고 필요 없는 컨트롤을 숨깁니다. 표시되는 모든 컨트롤은 브라우저에 다운로드하는 데 필요한 리소스를 증가시킵니다.  
  
## <a name="next-steps"></a>다음 단계  
 [양식 만들기 및 디자인](create-design-forms.md)    
    
 
