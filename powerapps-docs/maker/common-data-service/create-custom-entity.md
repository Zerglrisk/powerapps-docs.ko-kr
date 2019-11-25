---
title: PowerApps에서 구성 요소가 있는 사용자 지정 엔터티 만들기 | Microsoft Docs
description: PowerApps 앱에서 사용할 엔터티를 만들고 구성하기 위한 단계별 지침이 포함된 항목입니다.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 01/23/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 436e4f03a38efc3d61a0d4fb9f027ae6eff1c931
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754834"
---
# <a name="create-a-custom-entity-that-has-components-in-powerapps"></a>PowerApps에서 구성 요소가 있는 사용자 지정 엔터티 만들기

PowerApps에서 조직의 산업, 용어, 고유한 비즈니스 프로세스에 더 밀접하게 앱을 사용자 지정할 수 있습니다. PowerApps 앱 개발에는 표준 "기본 제공" 엔터티 추가 또는 사용자 지정 엔터티 만들기가 포함됩니다. 엔터티는 일반적으로 회사 이름, 위치, 제품, 전자 메일 및 전화와 같은 속성을 포함하는 레코드 형태로 추적하려는 정보를 정의합니다. 

이 항목에서는 엔터티를 만든 다음 필드, 관계, 보기 및 양식과 같은 주요 구성 요소를 추가하거나 사용자 지정합니다. 다음 방법에 대해 설명합니다.

- 사용자 지정 엔터티 만들기
- 엔터티에 사용자 지정 필드 추가
- 엔터티 관계 추가
- 보기 사용자 지정 
- 양식 사용자 지정

이 항목은 개와 고양이 미용을 하는 애완 동물 사업체인 Contoso사의 경우를 중심으로 설명합니다. Contoso는 다양한 장치에서 직원들이 사용할 수 있는 고객 및 애완 동물 추적 앱이 필요합니다.

## <a name="prerequisites"></a>필수 구성 요소

[PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 아직 PowerApps 계정이 없는 경우 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **무료 시작** 링크를 선택합니다.

## <a name="create-a-custom-entity"></a>사용자 지정 엔터티 만들기

1. 왼쪽 탐색 창에서 **데이터**를 확장하고 **엔터티**를 선택한 다음 **새 엔터티**를 선택합니다.
    > [!div class="mx-imgBorder"] 
    > ![새 엔터티 만들기](media/create-custom-entity/create-new-entity.png)
2. 오른쪽 창에서 다음 값을 입력한 후 **다음**을 선택합니다.
  - **표시 이름**: *애완 동물* 
  - **설명**: *애완 동물 서비스를 추적하는 사용자 지정 엔터티*
3. **엔터티 저장**을 선택합니다.

## <a name="add-and-customize-fields"></a>필드 추가 및 사용자 지정
 
1. 엔터티 목록에서 이전 섹션에서 만든 **애완 동물** 엔터티를 선택합니다.
2. **필드** 탭에서 **애완 동물** 필드를 선택합니다.
3. 오른쪽 창에서 **표시 이름** 필드를 다음과 같이 변경합니다. 
  - **표시 이름**을 **애완 동물**에서 *애완 동물 이름*으로 변경합니다.
  - **검색 가능**을 선택합니다.  
  
    > [!div class="mx-imgBorder"] 
    > ![기본 필드 변경](media/create-custom-entity/primary-field.png)
3. **완료**를 선택합니다.
4. 엔터티 디자이너 도구 모음의 **필드** 탭에서 **필드 추가**를 선택합니다. **필드 속성** 창에서 다음 값 및 옵션을 입력하거나 선택합니다.
  - **표시 이름:** *종*
  - **데이터 형식**. *옵션 집합*
  - **옵션 집합**. *새 옵션 집합*
5. 옵션 집합 만들기

  a. **새 항목 추가**를 선택합니다. 
  
  b. **새 옵션**을 *개*로 바꾸십시오. 
   
  c. **새 항목 추가**를 선택합니다. 
    
  d.  **새 옵션**을 *고양이*로 바꾸십시오. 
    
  e. **저장**을 선택합니다. 

  > [!div class="mx-imgBorder"] 
  > ![새 옵션 집합](media/create-custom-entity/optionset-add-items.png)

6. **검색 가능**을 선택한 다음 **완료**를 선택합니다.

7. 엔터티 디자이너 도구 모음에서 **필드 추가**를 선택합니다. **필드 속성** 창에서 다음 값을 입력하거나 선택한 다음 **완료**를 선택합니다.
  - **표시 이름:** *품종*
  - **데이터 형식**. *텍스트*
  - **검색 가능** *지원*

8. 엔터티 디자이너 도구 모음에서 **필드 추가**를 선택합니다. 

9. **필드 속성** 창에서 다음 값을 입력하거나 선택한 다음 **완료**를 선택합니다. 
  - **표시 이름:** *약속 날짜*
  - **데이터 형식**. *날짜 및 시간*

10. **엔터티 저장**을 선택합니다.

## <a name="add-a-relationship"></a>관계 추가

1. **관계** 탭을 선택하고 엔터티 디자이너 도구 모음에서 **관계 추가**를 선택한 다음 **다대일**을 선택합니다. 
2. 오른쪽 창의 **관련** 목록에서 **거래처**를 선택합니다.
3. **완료**를 선택합니다.
4. **엔터티 저장**을 선택합니다.

  다대일 관계를 추가하면 데이터 형식**조회**가 있는 **거래처** 필드가 **필드** 탭의 필드 목록에 자동으로 추가됩니다.
  > [!div class="mx-imgBorder"]
  > ![거래처 조회 필드](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>보기 사용자 지정

1. **보기** 탭을 선택한 다음 **활성 애완 동물** 보기를 선택합니다. **활성 애완 동물** 보기가 표시되지 않으면 **필터제거**를 선택합니다.
2. 보기 디자이너에서 **열 추가**를 선택하고 다음 열을 선택한 다음 **확인**을 선택합니다.
  - 거래처
  - 약속 날짜 
  - 품종 
  - 종
3. **만든 날짜** 열을 선택하고 **제거**를 선택한 다음 **확인**을 선택하여 열 제거를 확인합니다.
4. 열을 정렬하려면 이동하려는 열을 선택한 다음 보기가 다음과 같은 모양이 될 때까지 <- 및 -> 화살표 단추를 사용합니다.
    > [!div class="mx-imgBorder"] 
    > ![활성 애완 동물 보기](media/create-custom-entity/active-pets-view.png)
5. 보기 디자이너 도구 모음에서 **저장 후 닫기**를 선택합니다.  

## <a name="model-driven-apps-only-customize-the-main-form"></a>모델 기반 앱 전용: 기본 양식 사용자 지정

캔버스 앱에서 애완 동물 엔터티만 사용하려는 경우 이 단계를 건너뜁니다. 

1. 왼쪽 탐색 창에서 **데이터**를 확장하고 **엔터티**를 선택한 다음 **애완 동물**을 선택합니다.
2. **양식** 탭을 선택한 다음 **기본** 양식 유형 옆에 있는 **정보**를 선택하여 양식 편집기를 엽니다.
    > [!div class="mx-imgBorder"] 
    > ![기본 양식 편집](media/create-custom-entity/main-form-edit.png)
3. 양식 편집기에서 필드 탐색기 창에 있는 **종**, **품종**, **약속 날짜** 및 **거래처** 필드를 양식이 다음과 같은 모양이 될 때까지 양식 캔버스의 일반 섹션으로 끌어다 놓습니다.
    > [!div class="mx-imgBorder"] 
    > ![기본 양식의 필드 선택](media/create-custom-entity/main-form-edit2.png) 
4. **저장**을 선택합니다.
5. **게시**를 선택합니다.
6. **저장 후 닫기**를 선택하여 양식 디자이너를 닫습니다.

## <a name="add-the-custom-entity-to-an-app"></a>앱에 사용자 지정 엔터티 추가

이제 엔터티를 사용하여 캔버스 또는 모델 기반 앱을 빌드할 준비가 되었습니다. 

## <a name="next-steps"></a>다음 단계

이 항목에서는 유용한 앱을 만드는 데 사용할 수 있는 엔터티를 만드는 방법을 배웠습니다. 
- 모델 기반 앱을 만드는 방법에 대한 자세한 내용은 [첫 번째 모델 기반 앱빌드](../model-driven-apps/build-first-model-driven-app.md)를 참조하십시오.
- 캔버스 앱을 만드는 방법에 대한 자세한 내용은 [처음부터 새로 앱 만들기](../canvas-apps/get-started-create-from-blank.md)를 참조하십시오.
