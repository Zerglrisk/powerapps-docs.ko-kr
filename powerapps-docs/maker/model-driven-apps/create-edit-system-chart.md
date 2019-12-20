---
title: Power Apps에서 모델 기반 앱 시스템 차트 만들기 또는 편집 | MicrosoftDocs
description: 차트를 만들거나 편집하는 방법 알아보기
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e02d58f7-6b1c-4a51-b801-a4d9f24729c5
caps.latest.revision: 29
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 24c932f34c23c42f938f54ffa4f328f25a714c59
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875185"
---
# <a name="create-a-model-driven-app-system-chart"></a>모델 기반 앱 시스템 차트 만들기

이 항목에서는 시스템 차트를 만드는 방법에 대해 설명합니다. 시스템 차트는 조직 소유의 차트로, 앱을 실행하는 데이터를 읽을 수 있는 모든 사용자가 사용할 수 있도록 합니다. 시스템 차트는 특정 앱 사용자에 게 할당하거나 공유할 수 없습니다.  
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.  

    > [!IMPORTANT]
    > "**모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.     
  
2. **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **차트** 탭을 선택합니다.  
  
3.  도구 모음에서 **차트 추가**를 선택합니다.  
  
4.  차트 유형과 차트에 데이터를 표시하는 방법을 지정합니다.  
  
    -   *거래처 별 직원 수*와 같은 차트 이름을 입력합니다.  
  
    -   **필드 선택** 드롭다운에서 다음과 같이 합니다. 
        - **필드 선택** **계열** 축 드롭다운에서 **직원 수**와 같은 필드를 선택합니다.  
        - **필드 선택** **범주** 축 드롭다운에서 **거래처 이름**과 같은 필드를 선택합니다.
  
    -   *이 세로 막대형 차트는 거래처 이름별로 직원 수를 표시합니다*와 같은 차트의 용도를 식별하는 설명을 추가합니다. 

    > [!div class="mx-imgBorder"] 
    > ![샘플 차트](media/sample-chart.png)
  
5.  **저장 후 닫기**를 선택합니다.  

## <a name="known-issues"></a>알려진 문제  
차트 디자이너에서 특정 계산 필드에 순서를 추가하는 것은 지원되지 않으며 오류가 발생합니다.  이를 발생시키는 계산 필드는 다른 계산 필드, 관련 엔터티 필드 또는 엔터티의 로컬 필드를 사용하고 있습니다.

## <a name="next-steps"></a>다음 단계  
[대시보드 만들기 또는 편집](create-edit-dashboards.md)
