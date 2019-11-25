---
title: PowerApps에서 카드 양식 만들기 | MicrosoftDocs
description: PowerApps에서 카드 양식을 만들고 사용하는 방법에 대해 알아보기
keywords: ''
ms.date: 03/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d9adcde6d35b0f2d336bf86b8e4e26bcec1edec2
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752426"
---
# <a name="create-a-card-form"></a>카드 양식을 만듭니다.
카드 양식은 통합 인터페이스 앱에 대한 보기에 사용됩니다. 카드 양식은 모바일 장치에 적합한 간결한 형식으로 정보를 제공하도록 설계되었습니다. 예를 들어, 내 활성 거래처 보기의 기본 카드 양식은 각 거래처 레코드에 대해 표시되는 정보를 정의합니다. 

> [!div class="mx-imgBorder"] 
> ![](media/account-cardform-for-myactiveaccounts-view.png "Account card form for my active accounts view")

카드 양식은 다른 양식 유형과 동일한 방식으로 작성 및 편집할 수 있지만 카드 양식은 앱에 다르게 추가됩니다. 양식을 앱 구성 요소로 추가하는 대신 사용자 지정 카드 양식은 **읽기 전용 표** 컨트롤을 사용하여 보기에 추가됩니다. 

## <a name="create-a-card-form"></a>카드 양식을 만듭니다.
1. 카드 양식을 만들려면 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
2. **데이터**를 확장하고 **엔터티**를 선택하고 원하는 엔터티를 선택한 다음 **양식** 탭을 선택합니다.
3. 도구 모음에서 **양식 추가**를 선택한 다음, **카드 양식**을 선택합니다. 또는 **카드** 양식으로 된 기존 **양식 유형**을 열어서 편집할 수 있습니다.
4. 원하는 필드를 추가합니다. 작은 화면에서 양식이 잘 표시되도록 필드 수를 제한하는 것이 좋습니다. 
5. **저장**을 선택하고 **게시**를 선택합니다. 

## <a name="add-a-card-form-to-a-view"></a>보려는 카드 양식 추가 
1. [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
2. **데이터**를 확장하고 원하는 엔터티를 선택한 다음 **보기** 탭을 선택합니다.
3. 원하는 보기를 선택하고 디자이너 보기 도구 모음에서 **클래식으로 전환**을 선택합니다.
4. **일반 작업** 창에서 **사용자 지정 컨트롤**을 선택합니다.
5. **컨트롤 추가**를 선택하고 컨트롤 목록에서 **읽기 전용 표**를 선택한 다음 **추가**를 선택합니다.

   > [!NOTE]
   > 두 개의 읽기 전용 표 컨트롤이 있습니다. **읽기 전용 표(기본값)** 라는 기본 읽기 전용 표 컨트롤은 사용자 지정 카드 양식을 지원하지 않습니다. 

6. **읽기 전용 표** 속성 페이지에서 다음 속성을 구성한 다음 **확인**을 선택합니다. 
   - **카드 양식**. 연필 아이콘 ![컨트롤 속성 편집](media/ccf-pencil-icon.png)을 선택하고 보기에 표시하려는 카드 양식을 선택합니다. 기본적으로 보기와 연결된 기본 엔터티는 이미 선택되어 있지만 변경할 수 있습니다. 
   - **재배치 동작**. 크기를 조정할 때 카드 양식을 표시할지 여부를 변경하려는 경우 연필 아이콘 ![컨트롤 속성 편집](media/ccf-pencil-icon.png)을 선택합니다. 추가 정보: [표가 목록으로 재배치되도록 허용](specify-properties-for-unified-interface-apps.md#allow-grid-to-reflow-into-list)  
   - **읽기 전용 표** 컨트롤을 표시하려는 클라이언트 유형, **웹**, **전화** 또는 **태블릿**을 선택합니다.

     ![카드 양식에 대한 읽기 전용 표](media/read-only-grid-for-cardform.png)

7. **확인**을 선택하여 **사용자 지정 컨트롤** 속성 페이지를 닫습니다. 
8. 클래식 디자이너 보기 도구 모음에서 **저장 후 닫기**를 선택합니다. 

## <a name="see-also"></a>참조
[모델 기반 앱 데이터 시각화를 위한 사용자 지정 컨트롤 사용](use-custom-controls-data-visualizations.md)



