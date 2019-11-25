---
title: PowerApps에서 첫 모델 기반 앱을 처음부터 빌드하기 | Microsoft Docs
description: 단순한 모델 기반 앱을 빌드하는 방법 알아보기
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9c41feb81fbe90c1ca675105fe898b667f61b2b9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752568"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>첫 모델 기반 앱을 처음부터 새로 빌드하기
모델 기반 앱 디자인은 앱 개발에 대한 구성 요소 중심의 접근 방식입니다. 이 항목에서는 PowerApps 환경에서 사용할 수 있는 표준 엔터티 중 하나를 사용하여 간편하게 모델 기반 앱을 만드는 방법을 설명합니다.

> [!TIP]
> 모델 기반 앱을 빌드하는 방법에 대한 자세한 내용은 먼저 [모델 기반 앱 구성 요소 이해](model-driven-app-components.md)를 참조하십시오. 

## <a name="sign-in-to-powerapps"></a>PowerApps에 로그인합니다.
[PowerApps](https://make.powerapps.com/)에 로그인합니다. 아직 [!INCLUDE [powerapps](../../includes/powerapps.md)] 계정이 없는 경우 **무료 시작** 링크를 선택합니다. 

## <a name="create-your-model-driven-app"></a>모델 기반 앱 만들기

1.  원하는 환경을 선택하거나 [PowerApps 관리 센터](https://admin.powerapps.com/)로 이동하여 새로 만듭니다.

  > [!IMPORTANT]
  > **모델 기반** 디자인 모드를 사용할 수 없는 경우 [환경 만들기](https://docs.microsoft.com/powerapps/administrator/create-environment)를 해야 할 수 있습니다.   

2. **홈** 페이지에서 **새 모델 기반 앱**을 선택합니다.
<!-- ![Start-from-blank_model](media/build-first-model-driven-app/start-from-blank-model-driven.png) -->

3.  **새 앱 만들기** 페이지에서 다음 세부 정보를 입력하고 **완료**를 선택합니다. 
  - **이름**: *내 첫 번째 앱*과 같은 앱의 이름을 입력합니다. 
  - **고유 이름**: 기본적으로 고유 이름은 **이름** 상자에 지정하는 이름을 공백 없이 사용하고 게시자 접두사 및 밑줄(_)이 앞에 표시됩니다. 예를 들어, *crecf_Myfirstapp*. 추가 정보: [솔루션 게시자 접두사 변경](../common-data-service/change-solution-publisher-prefix.md)
  - **설명**: *앱이 내 첫 번째 앱*과 같은 응용 프로그램의 내용 또는 수행에 대한 간단한 설명을 입력합니다.
추가 앱 속성에 대한 자세한 내용은 [앱 만들기](create-edit-app.md#create-an-app)를 참조하십시오.

    > [!div class="mx-imgBorder"] 
    > ![](media/create-new-app.png "Create a new app") 


## <a name="add-components-to-your-app"></a>앱에 구성 요소를 추가합니다.
앱 디자이너에서 앱에 구성 요소를 추가합니다.
1.  **사이트 맵 디자이너 열기** 화살표를 선택하여 사이트맵 디자이너를 엽니다. 

    ![Create-new-sitemap](media/build-first-model-driven-app/new-sitemap.png)

2.  사이트 맵 디자이너에서 **새 하위 영역**을 선택하고 오른쪽 창에서 **속성** 탭을 선택한 후 다음 속성을 선택합니다.
  - **유형**: 엔터티
  - **엔터티**: 거래처

    ![사이트 맵에 구성 요소 추가](media/build-first-model-driven-app/sitemap.png)

3.  **저장 후 닫기**를 선택합니다.
4.  앱 디자이너 캔버스에서 **양식**을 선택한 다음 오른쪽 창에 있는 **기본 양식** 그룹에서 **거래처** 양식을 선택합니다.

    ![거래처 기본 양식](media/build-first-model-driven-app/main-form.png)

5.  앱 디자이너 캔버스에서 **보기**를 선택한 다음 **활성 거래처**, **모든 거래처** 및 **내 활성 거래처** 보기를 선택합니다.

    ![거래처 보기](media/build-first-model-driven-app/views.png)

6. 앱 디자이너 캔버스에서 **차트**를 선택한 다음 **산업별 거래처** 차트를 선택합니다.
7. 앱 디자이너 도구 모음에서 **저장**을 선택합니다.

    ![앱 디자이너 도구 모음 저장](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>앱 게시
앱 디자이너 도구 모음에서 **게시**를 선택합니다.

앱을 게시 한 후에는 다른 사용자와 실행하거나 공유할 준비가 된 것입니다.

![단순한 계정 엔터티 앱](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>다음 단계
이 항목에서는 간단한 모델 기반 앱을 작성했습니다. 
- 앱을 실행할 때 어떻게 보이는지 확인하려면 [모바일 장치에서 모델 기반 앱 실행](../../user/run-app-client-model-driven.md)을 참조하십시오.
- 앱을 공유하는 방법을 알아보려면 [모델 기반 앱 공유](share-model-driven-app.md)를 참조하십시오.
- 시작 및 모델 기반 앱을 빌드하는 방법에 대한 자세한 내용은 [모델 기반 앱 구성 요소 이해](model-driven-app-components.md)를 참조하십시오.
