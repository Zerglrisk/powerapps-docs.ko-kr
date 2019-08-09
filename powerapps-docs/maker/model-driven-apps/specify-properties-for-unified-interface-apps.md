---
title: PowerApps의 모델 기반 통합 인터페이스 앱에 대한 속성 지정 | MicrosoftDocs
description: 앱에 대한 표 제어를 구성하는 방법 알아보기
keywords: ''
ms.date: 06/03/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 3ecea4a7-0d18-4ccd-9609-3a62179e9e1b
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 0
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>모델 기반 통합 인터페이스 앱의 속성 지정

통합 인터페이스 프레임워크는 응답성이 뛰어난 디자인 원칙을 사용하여 모든 화면 크기 또는 방향에 최적화된 보기 및 상호 작용 환경을 제공합니다. 통합 인터페이스 프레임워크를 사용하는 모델 기반 응용 프로그램에서 표(보기) 컨트롤의 응답이 빠릅니다. 예컨대 휴대폰과 작은 뷰포트 등으로 컨테이너의 크기가 줄어들면 표가 목록으로 변환됩니다. 

읽기 전용 표 컨트롤은 표가 다른 화면 크기로 재배치하는 방법을 지정합니다. 앱 제작자는 통합 인터페이스 앱으로 작업하는 경우 읽기 전용 표 컨트롤과 사용자 지정 표 및 목록에 대한 해당 속성을 구성할 수 있습니다.
- **카드 양식** 속성: 기본 목록 템플릿 대신 목록에 대한 카드 양식을 사용합니다. 카드 양식은 목록 항목에 대해 기본 목록 템플릿보다 자세한 정보를 제공합니다.
- **재배치 동작** 속성: 이 매개 변수를 사용하여 목록에 재배치할 표를 지정합니다.

## <a name="allow-grid-to-reflow-into-list"></a>목록에 표를 재배치하도록 허용

컨트롤 목록에 읽기 전용 표 컨트롤을 추가하면 다음과 같은 기능을 구성할 수 있습니다. 
- 모바일과 같은 작은 디스플레이에서 표를 목록으로 재배치할 수 있습니다.
- 렌더링 모드를 표 전용 또는 목록 전용으로 지정합니다.  

1. [솔루션 탐색기](advanced-navigation.md#solution-explorer)를 엽니다.
2. 탐색 창에서 **엔터티**를 확장하고 적절한 엔터티(예: **거래처** 또는 **연락처**)를 선택한 다음 **컨트롤** 탭에서 **컨트롤 추가**를 선택합니다.

    ![컨트롤 추가 열기](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "컨트롤 추가 열기")

3. 컨트롤 목록에서 **읽기 전용 표**를 선택한 다음 **추가**를 선택합니다.

    사용 가능한 컨트롤 목록에 컨트롤이 추가됩니다.
   
    ![컨트롤 선택](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "컨트롤 선택")
    
4. 표를 읽기 전용으로 만들 장치(**웹**, **전화** 또는 **태블릿**)를 선택합니다.

    ![장치 유형 선택](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "장치 유형 선택")

5. **카드 양식** 속성을 구성합니다.

    기본 목록 템플릿 대신 카드 양식 속성을 사용하여 목록 항목을 표시할 수 있습니다. 카드 양식은 목록 항목에 대해 기본 목록 템플릿보다 자세한 정보를 제공합니다.    

    a. **카드 양식** 옆에 있는 연필 아이콘을 선택합니다.

    ![카드 양식 편집](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "카드 양식 편집")

    b.  **엔터티** 및 **카드 양식** 유형을 선택합니다.

    ![카드 양식 속성](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "카드 양식 속성")

    c. **확인**을 선택합니다.
6. **재배치 동작** 속성을 구성합니다. 
    
    a. **재배치 동작** 옆에 있는 연필 아이콘을 선택합니다.

    ![재배치 동작 편집](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "재배치 동작 편집")

    b. **정적 옵션에 바인딩** 드롭다운에서 표 흐름 유형을 선택합니다. 

    |흐름 유형|설명|
    |--------------|--------------------|
    |**재배치**|표시 공간이 충분하지 않은 경우 표를 목록 모드로 렌더링하도록 합니다.|
    |**표만**|표시 공간이 충분하지 않은 경우 표를 목록으로 재배치하는 것을 제한할 수 있습니다.|
    |**목록만**|표로 표시할 공간이 충분한 경우에도 목록으로만 표시됩니다.|
    
     ![재배치 동작 속성](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "재배치 동작 속성")

    c. **확인**을 선택합니다.


7.  변경을 저장하고 게시합니다. 


## <a name="conditional-image"></a>조건부 이미지
목록에 값 대신 사용자 지정 아이콘을 표시하고 JavaScript를 사용하여 열의 값을 기준으로 이를 선택하기 위해 사용되는 논리를 설정할 수 있습니다. 조건부 이미지에 대한 자세한 내용은 [목록 보기에서 값 대신 사용자 지정 아이콘 표시](../common-data-service/display-custom-icons-instead.md)를 참조하십시오.

## <a name="next-steps"></a>다음 단계
[보기 만들기 또는 편집](create-edit-views.md)
