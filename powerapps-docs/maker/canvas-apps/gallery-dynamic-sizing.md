---
title: 갤러리에서 높이가 다른 항목 표시 | Microsoft Docs
description: 갤러리의 각 항목에서 콘텐츠 양을 자동으로 맞추도록 높이 조정 가능 갤러리를 추가하고 구성합니다.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/01/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b724bff09e02a3f69166b3c3357833804c8172b6
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61554790"
---
# <a name="show-items-of-different-heights-in-a-powerapps-gallery"></a>PowerApps 갤러리에서 높이가 다른 항목 표시
데이터 집합에 있는 다양한 항목이 같은 필드에 다른 양의 데이터를 포함하고 있다면 적은 데이터가 포함된 항목 다음에 빈 공백을 추가하지 않고 더 많은 데이터를 포함하는 항목을 완전히 표시할 수 있습니다. **높이 조정 가능** 갤러리 컨트롤을 추가 및 구성하여 다음 작업을 수행할 수 있습니다.

* 콘텐츠에 따라 확장 또는 축소하도록 **레이블** 컨트롤을 구성합니다.
* 위의 컨트롤 바로 아래에 자동으로 나타나도록 각 컨트롤을배치합니 다.

이 자습서에서는 **높이 조정 가능** 갤러리 컨트롤의 바닥재 제품에 대한 데이터를 보여줍니다. 각 제품의 이미지는 개요의 5픽셀 아래에 나타나며, 개요는 다섯 줄의 텍스트 또는 두 줄을 포함합니다.

![최종 앱](./media/gallery-dynamic-sizing/dynamic-app.png)

**참고 자료**

갤러리에 컨트롤을 추가하지 않았다면 이 항목에서 계속하기 전에 [항목 목록 표시](add-gallery.md)의 단계를 따르세요.

## <a name="add-data-to-a-blank-app"></a>빈 앱에 데이터 추가
1. 바닥재 제품의 이름, 개요 및 이미지 링크가 포함된 [이 Excel 파일](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)을 다운로드합니다.

    ![바닥재 제품](./media/gallery-dynamic-sizing/flooring-products.png)

2. Excel 파일을 OneDrive, Dropbox 또는 Google Drive와 같은 클라우드 스토리지 계정에 업로드합니다.

3. PowerApps Studio에서 **파일** 메뉴에서 **새로 만들기**를 클릭하거나 탭합니다.

4. **빈 앱** 타일에서 **전화 레이아웃**을 클릭하거나 탭합니다.

    ![파일 메뉴의 새 옵션](./media/gallery-dynamic-sizing/blank-app.png)

5. Excel 파일의 **FlooringEstimates** 테이블에 연결을 추가합니다.

    자세한 내용은 [연결 추가](add-data-connection.md)를 참조하세요.

## <a name="add-data-to-a-gallery"></a>갤러리에 데이터 추가
1. **삽입** 탭에서 **갤러리**를 클릭하거나 탭한 다음, **높이 조정 가능**을 클릭하거나 탭합니다.

    ![갤러리 추가](./media/gallery-dynamic-sizing/add-flexible.png)
2. 전체 화면을 차지하도록 갤러리의 크기를 조정합니다.

3. 갤러리의 **[Items](controls/properties-core.md)** 속성을 **FlooringEstimates**로 설정합니다.

## <a name="show-the-product-names"></a>제품 이름 표시
1. 갤러리의 왼쪽 위 모서리에서 연필 아이콘을 클릭하거나 탭하여 갤러리 템플릿을 선택합니다.

    ![연필 아이콘](./media/gallery-dynamic-sizing/edit-template.png)

2. 갤러리 템플릿이 선택된 상태에서 **[레이블](controls/control-text-box.md)** 컨트롤을 추가합니다.

3. **레이블** 컨트롤의 **Text** 속성을 다음 식으로 설정합니다.<br>
   **ThisItem.Name**

    ![레이블 추가](./media/gallery-dynamic-sizing/add-text-box.png)

## <a name="show-the-product-overviews"></a>제품 개요 표시
1. 갤러리 템플릿이 선택된 상태에서 또 다른 **레이블** 컨트롤을 추가하고 **레이블** 컨트롤 아래로 이동합니다.  

2. 두 번째 **레이블** 컨트롤의 **Text** 속성을 다음 식으로 설정합니다.<br> **ThisItem.Overview**

3. 두 번째 **레이블** 컨트롤이 선택된 상태에서 **콘텐츠** 탭의 이름 태그 아이콘을 클릭하거나 탭하고 이 컨트롤의 이름을 **OverviewText**로 변경합니다.

    ![레이블 이름 바꾸기](./media/gallery-dynamic-sizing/rename-text-box.png)

4. **OverviewText** 상자의 **AutoHeight** 속성을 **true**로 설정합니다.

    이 단계를 통해 해당 상자가 콘텐츠에 맞게 늘어나거나 축소됩니다.

      ![텍스트 자동 높이](./media/gallery-dynamic-sizing/autoheight-text.png)

## <a name="show-the-product-images"></a>제품 이름 표시
1. 높이가 두 배가 되도록 템플릿 크기를 조정합니다.

    앱을 빌드할 때 컨트롤을 템플릿에 더 쉽게 추가할 수 있으며, 이 변경 사항은 앱 실행 시 보이는 방식에 영향을 미치지 않습니다.

2. 갤러리 템플릿이 선택된 상태에서 **[이미지](controls/control-image.md)** 컨트롤을 추가하고 **OverviewText** 상자 아래로 이동합니다.

3. **이미지** 컨트롤의 **Image** 속성이 다음 식으로 설정됩니다.<br>
    **ThisItem.Image**

4. 다음 식에 있는 대로 **OverviewText** 박스의 위치와 크기에 따라 **이미지** 컨트롤의 **[Y](controls/properties-core.md)** 속성을 설정합니다.
   <br>**OverviewText.Y + OverviewText.Height + 5**

    ![최종 앱](./media/gallery-dynamic-sizing/final-app.png)

컨트롤을 더 추가하려는 경우 동일한 개념을 적용합니다. 즉, 위에 있는 컨트롤의 **Y** 및 **Height** 속성에 따라 각 컨트롤의 **Y** 속성을 설정합니다.

## <a name="next-steps"></a>다음 단계
[갤러리](working-with-forms.md) 컨트롤과 [수식](working-with-formulas.md) 사용 방법에 대해 자세히 알아보세요.
