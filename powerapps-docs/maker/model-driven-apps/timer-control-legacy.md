---
title: PowerApps의 모델 기반 앱 타이머 컨트롤 | MicrosoftDocs
description: 타이머 컨트롤을 사용하는 방법 이해
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
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 31b7f2b55f10e404841517aada26b0b38df7fbbf
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710822"
---
# <a name="model-driven-app-timer-control-overview"></a>모델 기반 앱 타이머 컨트롤 개요

 레코드가 필요한 양식에서 타이머 컨트롤을 사용하여 특정 시간 기반 중요 시점을 충족합니다. 타이머 컨트롤은 활성 레코드를 해결하여 작업을 완료하는 데 사용할 수 있는 시간이나 작업을 완료하기 위해 시간이 경과된 시간을 보여 줍니다. 최소한 타이머 컨트롤은 작업 완료 성공 또는 실패를 표시하도록 구성되어야 합니다. 또한 해당 조건이 실패에 도달할 경우 경고를 표시하도록 구성할 수 있습니다.  
  
 타이머 컨트롤은 엔터티의 양식에 추가할 수 있지만 서비스 케이스 엔터티에 가장 많이 사용됩니다. 특히 서비스 수준 약정을 추적하는 필드에 연결될 때 많이 사용됩니다. 양식의 본문에 타이머 컨트롤을 여러 개 추가할 수 있습니다. 머리글이나 바닥글에는 추가할 수 없습니다.  
  
 타이머 컨트롤 **데이터 원본** 속성은 엔터티에 대한 필드를 사용합니다.  
  
-   **실패 시간 필드**는 날짜-시간 필드를 사용하여 시간을 설정합니다.  
  
-   세 조건 필드는 엔터티에 대해 **옵션 집합**, **두 개 옵션**, **상태** 또는 **상태 설명** 필드 중 하나를 사용합니다.  

Timer 컨트롤을 만들려면 양식 디자이너에서 **삽입** 탭을 선택한 다음 도구 모음에서 **타이머**를 선택합니다. 

  > [!div class="mx-imgBorder"] 
  > ![타이머 컨트롤 삽입](media/insert-timer-control.png)

타이머 컨트롤 속성 페이지에서 원하는 속성을 입력하거나 선택한 다음 **확인**을 선택합니다. 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>타이머 컨트롤 속성  
 다음 표는 타이머 컨트롤의 속성을 설명합니다.  
  
|그룹|이름|설명|  
|-----------|----------|-----------------|  
|이름|이름|**필수 특성**: 컨트롤에 대한 고유 이름입니다.|  
||레이블|**필수 특성**: 타이머 컨트롤에 표시할 레이블입니다.|  
|데이터 원본|실패 시간 필드|**필수 특성**: 엔터티에 대해 날짜-시간 필드 중 하나를 선택하여 언제 중요 시점이 성공적으로 완료되어야 하는지를 나타냅니다.|  
||성공 조건|**필수 특성**: 엔터티에 대한 필드를 선택하여 중요 시점의 성공을 평가한 후 성공을 나타내는 옵션을 선택합니다.|  
||경고 조건|엔터티에 대한 필드를 선택하여 경고를 표시하도록 중요 시점의 성공이 위험한 상태인지 여부를 평가한 후 경고를 표시할 옵션을 선택합니다.|  
||취소 조건|엔터티에 대한 필드를 선택하여 중요 시점 달성의 취소 여부를 평가한 후 중요 시점의 취소를 나타내는 옵션을 선택합니다.|  

## <a name="next-steps"></a>다음 단계

[양식 편집기 사용자 인터페이스 개요](form-editor-user-interface-legacy.md)
