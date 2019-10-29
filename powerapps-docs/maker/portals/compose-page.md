---
title: 웹 페이지 작성 | Microsoft Docs
description: 포털에서 웹 페이지를 작성 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cec2b106ba35f73a34128e9e89233c18d2d70dd1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975705"
---
# <a name="compose-a-page"></a>페이지 작성

필요한 웹 페이지를 추가 하 고 사이트 맵에서 계층 구조를 관리 한 후에는 다양 한 구성 요소를 추가할 수 있습니다. WYSIWYG 편집기를 사용 하면 캔버스에서 필요한 구성 요소를 쉽게 추가 하 고 편집할 수 있습니다. 캔버스에서 다음 구성 요소를 추가 하 고 편집할 수 있습니다.

- 섹션
    - 하나의 열 섹션
    - 두 열 섹션
    - 세 개의 열 섹션
- 포털 구성 요소
    - Text
    - 이미지
    - IFrame
    - 폼
    - 은
    - 막대

> [!NOTE]
> PowerApps portal Studio를 사용 하 여 포털을 사용자 지정 하는 경우 웹 사이트 사용자가 성능에 영향을 줄 수 있습니다. 라이브 포털에서 사용량이 많지 않은 시간에 변경 내용을 적용 하는 것이 좋습니다. 

## <a name="use-the-wysiwyg-editor"></a>WYSIWYG 편집기 사용

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

    > [!NOTE]
    > 편집 가능한 요소는 경계로 경계선 됩니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  추가할 구성 요소를 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![구성 요소 창](media/components-pane.png "구성 요소 창")  

    선택한 구성 요소는 편집 가능한 요소 내의 캔버스에 추가 됩니다.

6.  구성 요소를 삭제 하려면 캔버스에서 구성 요소를 선택한 다음 페이지 맨 위에 있는 명령 모음에서 **삭제** 를 선택 합니다.

    > [!div class=mx-imgBorder]
    > 구성 요소(media/delete-component.png "삭제 구성 요소") ![삭제]  

## <a name="add-sections"></a>섹션 추가

섹션에서는 페이지에 대 한 구조를 정의 하 고이에 따라 포털 구성 요소를 정렬할 수 있습니다. 페이지에 섹션을 추가 하면 요구 사항에 따라 섹션 내에 포털 구성 요소를 추가할 수 있습니다.

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.

2.  섹션을 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.

5.  **섹션 레이아웃**아래에서 삽입할 섹션 형식을 선택 합니다.

6.  화면 오른쪽에 있는 속성 창에서 다음 정보를 입력 하거나 선택 합니다.

    - **최소 높이**: 섹션의 최소 높이를 입력 합니다. 지정 된 높이 보다 더 많은 공간을 차지 하는 구성 요소를 추가 하는 경우 섹션은 구성 요소에 맞게 확장 됩니다. 기본적으로 최소 높이는 100px입니다. 포인트 (pt)와 백분율 (%)을 입력할 수도 있습니다.

        > [!div class=mx-imgBorder]
        > ![](media/section-props-height.png "섹션 맞춤") 섹션 맞춤  

    - **맞춤**: 섹션의 구성 요소를 왼쪽, 가운데 또는 오른쪽에 맞출지 여부를 선택 합니다.

        > [!div class=mx-imgBorder]
        > ![](media/section-props-align.png "섹션 맞춤") 섹션 맞춤  

    - **배경**: 색 또는 이미지를 섹션 배경으로 포함 하려면 선택 합니다.

        - **채우기**: 배경의 색을 선택 합니다.

            > [!div class=mx-imgBorder]
            > (media/section-props-fill.png "섹션의 채우기 색") ![섹션에서 채우기 색]  

        - **이미지**: 목록에서 이미지를 선택 합니다. 새 이미지를 업로드 하려면 **이미지 업로드**를 선택 합니다.

            > [!div class=mx-imgBorder]
            > 섹션 ![에서 이미지 추가]섹션에서(media/section-props-image.png "이미지 추가")  

7.  섹션에 필요한 포털 구성 요소를 추가 합니다.


## <a name="add-portal-components"></a>포털 구성 요소 추가

웹 페이지에서 다음 구성 요소를 추가할 수 있습니다.

- [텍스트](#add-text-box)
- [이미지](#add-image)
- [IFrame](#add-iframe)
- [양식](#add-form)
- [은](#add-list)
- [막대](#add-breadcrumb)


### <a name="add-text-box"></a>텍스트 상자 추가

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**에서 **텍스트**를 선택 합니다.

6.  텍스트 상자에 필요한 텍스트를 입력 합니다.

7.  텍스트의 서식을 지정 하려면 텍스트를 선택 하 여 서식 옵션을 표시 합니다. 필요에 따라 글꼴 크기와 스타일을 수정 합니다.

    > [!div class=mx-imgBorder]
    > ![텍스트 구성 요소](media/text-component.png "텍스트 구성 요소")  

8. 화면 오른쪽에 있는 속성 창에서 다음 정보를 선택 합니다.

    - **맞춤**: 텍스트를 왼쪽, 가운데 또는 오른쪽으로 맞춰야 할지 여부를 선택 합니다.

    - **글꼴 색**: 텍스트의 색을 선택 합니다.

        > [!div class=mx-imgBorder]
        > ![텍스트 맞춤 및 색 선택](media/text-props.png "텍스트 맞춤 및 색 선택")  
 

### <a name="add-image"></a>이미지 추가

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**아래에서 **이미지**를 선택 합니다. 이미지 자리 표시 자가 캔버스에 추가 됩니다.

6.  화면 오른쪽에 있는 속성 창에서 다음 정보를 입력 합니다.

    - **이미지**: 기존 이미지를 선택 하거나 새 이미지를 업로드 하려면이 옵션을 선택 합니다. 이전에 업로드 한 이미지를 선택 하려면 **이미지 선택** 목록에서 이미지를 선택 합니다. 새 이미지를 업로드 하려면 **이미지 업로드**를 선택 합니다. 업로드 된 모든 이미지는 이미지 라이브러리에 포함 됩니다 .이 이미지는 **이미지 선택** 목록에서 다시 선택할 수 있습니다.

        > [!div class=mx-imgBorder]
        > ![이미지 속성](media/image-props.png "이미지 속성")  

        > [!NOTE]
        > - 최대 크기가 5mb 인 png, svg, jpg 및 jpeg 형식의 이미지만 업로드할 수 있습니다.
        > - 이름이 같은 이미지는 업로드할 수 없습니다. 이미지 이름을 수정 하 여 다시 업로드 해야 합니다.

    - **외부 url**: 외부 url에서 이미지를 업로드 하려면이 옵션을 선택 합니다. **외부 url** 필드에 URL을 입력 합니다. 보안 링크만 허용 됩니다. 즉, https://는 필수 항목입니다. 콘텐츠 배달 네트워크에 이미지를 저장 한 경우이 필드에 링크를 제공할 수 있습니다.

        > [!div class=mx-imgBorder]
        > ![이미지 외부 url](media/image-ext-url.png "이미지 외부 url")  

    -   **서식 옵션**

        - **Width**: 이미지의 너비를 입력 합니다.

        - **Height**: 이미지의 높이를 입력 합니다.

    > [!NOTE]
    > 캔버스에서 이미지를 선택 하 고 핸들을 끌어 크기를 조정할 수도 있습니다.

### <a name="add-iframe"></a>IFrame 추가

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**에서 **IFrame**을 선택 합니다. IFrame 자리 표시 자가 캔버스에 추가 됩니다.

6.  화면 오른쪽에 있는 속성 창에서 다음 정보를 입력 합니다.

    - **Width**: IFrame의 너비를 입력 합니다.

    - **Height**: IFrame의 높이를 입력 합니다.

    - **링크**: IFrame에 표시할 웹 사이트의 URL을 입력 합니다. 보안 링크만 허용 됩니다. 즉, https://는 필수 항목입니다. 기본적으로 <https://www.bing.com>는 값으로 사용할 수 있습니다.

        > [!div class=mx-imgBorder]
        > ![iframe 속성](media/iframe-props.png "iframe 속성")  

    > [!NOTE]
    > 캔버스에서 IFrame을 선택 하 고 핸들을 끌어 크기를 조정할 수도 있습니다.

### <a name="add-form"></a>양식 추가

양식은 개발자가 포털에서 양식을 표시 하지 않고도 포털에서 데이터를 수집 하기 위해 양식을 추가 하는 데 사용 하는 데이터 기반 구성입니다. [양식은 Common Data Service에서 만들어지며](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview) , 포털의 웹 페이지나 목록과 함께 사용 하 여 전체 웹 응용 프로그램을 빌드할 수 있습니다.  

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**아래에서 **양식**을 선택 합니다.

6.  화면 오른쪽의 속성 창에서 다음 옵션 중 하나를 선택 합니다.

    - **새로 만들기**: 새 폼을 만듭니다.
    - **기존 사용**: 기존 폼을 사용 합니다.

7. 다음 항목에 대 한 정보를 입력 하거나 선택 합니다.

    - **이름**: 형식의 이름입니다.

    - **Entity**: 폼이 로드 될 엔터티의 이름입니다.

    - **양식 레이아웃**: 렌더링할 Common Data Service의 대상 엔터티에 대 한 폼의 이름입니다.

    - **모드**: 다음 옵션 중 하나를 선택 합니다.

        - **삽입**: 양식이 제출 시 새 레코드를 삽입 함을 나타냅니다.

        - **Edit**: 폼에서 기존 레코드를 편집 해야 함을 나타냅니다.

        - **읽기 전용**: 폼에서 기존 레코드를 편집할 수 없는 양식으로 표시 함을 나타냅니다.

        > [!NOTE]
        > **편집** 및 **읽기 전용** 모드의 기본 옵션은 URL에 ID로 전달 되는 쿼리 문자열 매개 변수 이름으로 설정 됩니다. 이러한 값을 변경 하려면 포털 관리 앱을 열고 양식 속성을 업데이트 해야 합니다.

    - **성공 시**: 다음 옵션 중 하나를 선택 합니다.

        - **성공 메시지 표시**: 양식이 성공적으로 전송 될 때 사용자에 게 메시지를 표시 해야 합니다. **성공 시 양식 숨기기** 를 선택 하 여 성공적인 전송 시 양식을 숨길 수도 있습니다.

        - **웹 페이지로 리디렉션**: 포털에서 사용자를 선택 된 웹 페이지로 리디렉션합니다. **웹 페이지 리디렉션** 목록에서 웹 페이지를 선택 해야 합니다.

        - **Url로 리디렉션**: 사용자를 지정 된 URL로 리디렉션합니다. **Url 리디렉션** 필드에 url을 입력 해야 합니다.

    - **익명 사용자에 대 한 Captcha 표시**: 익명 사용자에 게 captcha를 표시 합니다.

    - **인증 된 사용자에 대 한 Captcha 표시**: 인증 된 사용자에 게 captcha를 표시 합니다.

    - **엔터티 사용 권한 사용**: 폼에 대해 고려할 엔터티 권한입니다. 기본적으로 선택 되어 있지 않습니다. 이 항목을 선택 하는 경우 모든 사용자가 양식에 액세스 하려면 명시적 사용 권한이 필요 합니다. 추가 정보: [엔터티 권한](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)

        > [!div class=mx-imgBorder]
        > ![폼 속성](media/form-props.png "폼 속성")

### <a name="add-list"></a>목록 추가

목록은 개발자가 포털에서 그리드를 표시할 필요 없이 레코드 목록을 렌더링 하는 웹 페이지를 추가 하는 데 사용 하는 데이터 기반 구성입니다. 목록 [Common Data Service 보기](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views) 를 사용 하 여 포털에 레코드를 표시 합니다.  

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**에서 **목록**을 선택 합니다.

6.  화면 오른쪽의 속성 창에서 다음 옵션 중 하나를 선택 합니다.

    - **새로 만들기**: 새 목록을 만듭니다.
    - **기존 사용**: 기존 목록을 사용 합니다.

7.  다음 항목에 대 한 정보를 입력 하거나 선택 합니다.

    - **이름**: 목록 이름입니다.

    - **Entity**: 뷰를 로드 하는 엔터티의 이름입니다.

    - **Views**: 렌더링할 대상 엔터티의 뷰 목록입니다. 여러 뷰를 선택 하 여 목록에 레코드를 표시할 수 있습니다. 먼저 선택한 뷰가 기본 뷰가 됩니다.

    - **새 레코드 만들기**: 사용자가 레코드를 만들 수 있습니다. 새 레코드를 만들 양식을 포함 하는 웹 페이지를 선택 합니다.

    - **세부 정보 보기**: 사용자가 세부 정보를 볼 수 있습니다. 세부 정보를 표시할 양식이 포함 된 웹 페이지를 선택 합니다.

    - **레코드 편집**: 사용자가 레코드를 편집할 수 있습니다. 양식을 포함 하는 웹 페이지를 선택 하 여 레코드를 편집 합니다.

    - **레코드 삭제**: 사용자가 레코드를 삭제할 수 있습니다.

    - **빈 목록 메시지**: 표시할 레코드가 없을 때 표시 될 메시지입니다.

    - 페이지당 **레코드 수**: 페이지에 표시할 레코드 수를 지정 하는 정수 값입니다.

    - **엔터티 목록에서 검색 사용**: 사용자가 목록에서 레코드를 검색할 수 있도록 허용 합니다.

    - **엔터티 사용 권한 사용**: 목록에 대해 고려할 엔터티 권한입니다. 기본적으로 선택 되어 있지 않습니다. 이 항목을 선택 하는 경우 모든 사용자가 양식에 액세스 하려면 명시적 사용 권한이 필요 합니다. 추가 정보: [엔터티 권한](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions)  

    > [!div class=mx-imgBorder]
    > ![목록 속성](media/list-props.png "목록 속성")

### <a name="add-breadcrumb"></a>이동 경로 추가

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.  

2.  구성 요소를 추가 하려는 페이지를 선택 합니다.

3.  캔버스에서 편집할 수 있는 요소를 선택 합니다.

4.  화면 왼쪽의 toolbelt에서 **구성** 요소 ![아이콘 아이콘](media/components-icon.png "구성 요소 아이콘") 을 선택 합니다.  

5.  **포털 구성 요소**에서 **이동 경로**를 선택 합니다.

## <a name="add-a-custom-menu"></a>사용자 지정 메뉴 추가

기본적으로 웹 사이트의 메뉴는 웹 페이지의 계층 구조에 따라 자동으로 만들어집니다. **기본** 메뉴 라고 합니다. 사용자 지정 메뉴를 만들려면 포털 관리 앱에 설정 된 웹 링크를 만들어야 합니다. 추가 정보: [웹 링크 관리](https://docs.microsoft.com/dynamics365/customer-engagement/portals/manage-web-links)

웹 링크 집합을 만든 후 다음을 수행 합니다.

1.  [포털을 편집](manage-existing-portals.md#edit) 하 여 PowerApps 포털 스튜디오에서 엽니다.

2.  헤더 구성 요소를 선택 합니다. 

3.  화면 오른쪽에 있는 속성의 **탐색 메뉴** 목록에서 웹 링크 집합 이름을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![탐색 메뉴](media/navigation-menu.png "탐색 메뉴")

## <a name="use-code-editor"></a>코드 편집기 사용

캔버스에서 구성 요소의 소스를 보려면 구성 요소를 선택한 다음 소스 코드 편집기 아이콘&lt;선택 하 여 바닥글에서 **&gt;/** 합니다.

> [!div class=mx-imgBorder]
> ![코드 편집기 아이콘](media/code-editor-icon.png "코드 편집기 아이콘")  

소스 코드는 화면 아래쪽의 **코드 편집기** 창에 표시 됩니다. 이전에 변경한 내용이 소스 코드에서 업데이트 됩니다. 변경 하려면 소스 코드를 업데이트 하 고 **저장**을 선택 합니다. 변경 내용이 캔버스에 반영 됩니다.

> [!div class=mx-imgBorder]
> ![코드 편집기](media/code-editor.png "코드 편집기") 

> [!NOTE]
> 고급 구성을 위해 소스 코드 편집기에서 액체 태그를 추가할 수도 있습니다. 추가 정보: [액체 템플릿 사용](https://docs.microsoft.com/dynamics365/customer-engagement/portals/custom-templates-dynamic-content)


