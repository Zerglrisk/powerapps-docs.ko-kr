---
title: Power Apps에서 모델 기반 앱 양식 요소 표시 또는 숨기기 | MicrosoftDocs
description: 탭, 섹션 또는 필드와 같은 요소를 표시하거나 숨기는 방법 알아보기
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 637ee2f171eaae493a219e245c2bf1147cd13bd2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867506"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>모델 기반 앱 양식 요소 표시 또는 숨기기

 여러 유형의 양식 요소에는 기본적으로 표시하거나 숨길 옵션이 있습니다. 탭, 섹션, 필드, iFrame 및 웹 리소스는 모두 이 옵션을 제공합니다. 양식 스크립트 또는 비즈니스 규칙을 사용하면 양식의 조건에 맞게 조정하는 사용자 인터페이스를 제공하는 동적 양식을 만들기 위해 이러한 요소의 표시 유형을 제어할 수 있습니다.  
  
> [!NOTE]
>  양식 요소를 숨기는 것은 보안을 강화하기 위해 권장되는 방법이 아닙니다. 여러 가지 방법으로 요소가 숨겨져 있을 때 사용자가 양식의 모든 요소와 데이터를 볼 수 있습니다. 
  
 옵션의 표시 유형을 제어하는 스크립트에 의존하는 양식을 디자인하는 대신 비즈니스 프로세스 흐름, 대화, 다른 양식으로 전환이 요구 사항에 더 적합할 수 있습니다. 스크립트를 사용하는 경우 숨길 수 있는 모든 요소가 기본적으로 숨겨져 있는지 확인하십시오. 논리가 호출할 때 스크립트와 함께 표시합니다. 이렇게 스크립트를 지원하지 않는 프레젠테이션에 표시되지 않습니다.  

## <a name="next-steps"></a>다음 단계

[양식 편집기 인터페이스 개요](form-editor-user-interface-legacy.md)
