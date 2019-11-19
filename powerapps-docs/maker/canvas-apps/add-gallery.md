---
title: 캔버스 앱의 항목 목록 표시 | Microsoft Docs
description: 갤러리를 사용하여 캔버스 앱에서 항목 목록을 표시하고 조건을 지정하여 목록을 필터링합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6d48b7b6ef1d9d691b733bea9af6ce74d0f2b07a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540919"
---
# <a name="show-a-list-of-items-in-powerapps"></a>PowerApps에서 항목 목록 표시

**[갤러리](controls/control-gallery.md)** 컨트롤을 캔버스 앱에 추가하여 모든 데이터 원본에서 항목 목록을 표시합니다. 이 토픽에서는 데이터 원본으로 Excel을 사용합니다. 텍스트 입력 **[ 컨트롤의 필터 조건과 일치하는 항목만 표시하도록 ](controls/control-text-input.md)갤러리** 컨트롤을 구성하여 목록을 필터링합니다.

## <a name="prerequisites"></a>필수 조건

- PowerApps에서 [컨트롤을 추가하고 구성](add-configure-controls.md)하는 방법을 알아봅니다.

- 샘플 데이터 설정:
    1. 이 자습서에 대한 샘플 데이터를 포함하는 [이 Excel 파일](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)을 다운로드합니다.

    2. Excel 파일을 비즈니스용 OneDrive와 같은 [클라우드 스토리지 계정](connections/cloud-storage-blob-connections.md)에 업로드합니다.

- 빈 앱을 엽니다.
    1. [PowerApps에 로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.

    1. **고유한 앱 만들기**에서 **빈 페이지의 캔버스 앱**을 선택합니다.

    1. 앱의 이름을 지정하고, **휴대폰**을 선택한 다음, **만들기**를 선택합니다.

    1. **PowerApps Studio 시작** 대화 상자에서 **건너뛰기**를 선택합니다.

    1. Excel 파일의 [FlooringEstimates](add-data-connection.md) 테이블에 **연결을 추가**합니다.

## <a name="add-a-gallery-to-a-blank-screen"></a>빈 화면에 갤러리 추가

1. **삽입** 탭에서 **갤러리**를 선택 하 고 **세로**를 선택 합니다.

    ![세로 갤러리 추가](./media/add-gallery/gallery-dropdown.png)

1. 오른쪽 창의 **속성** 탭에서 **항목** 목록을 연 다음 **바닥 재 추정치**를 선택 합니다.

    ![바닥 재 예상치](./media/add-gallery/select-layout.png)

1. 필드 **레이아웃** 목록에서 다른 옵션을 선택 합니다.

## <a name="add-a-gallery-in-a-screen"></a>화면에 갤러리 추가

1. **홈** 탭에서 **새 화면** > **목록 화면**을 선택 합니다.

    **갤러리** 컨트롤이 포함 된 화면과 검색 표시줄과 같은 기타 컨트롤이 나타납니다.

1. 갤러리의 **Items** 속성을 `FlooringEstimates`로 설정합니다.

    **갤러리** 컨트롤은 샘플 데이터를 보여 줍니다.

    ![데이터 표시](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>갤러리 컨트롤에 컨트롤 추가
다른 사용자 지정을 수행 하기 전에 **갤러리** 컨트롤의 레이아웃이 원하는 항목과 가장 가깝게 일치 하는지 확인 합니다. 여기에서 **갤러리 컨트롤의** 모든 데이터가 표시 되는 방법을 결정 하는 **갤러리** 템플릿을 추가로 수정할 수 있습니다.

1. **갤러리** 컨트롤의 아래쪽 근처를 클릭 하거나 탭 한 다음 왼쪽 위 모퉁이에 있는 연필 아이콘을 선택 하 여 템플릿을 선택 합니다.

    ![갤러리 템플릿 편집](./media/add-gallery/edit-item.png)

2. 템플릿을 여전히 선택한 채로 **[레이블](controls/control-text-box.md)** 컨트롤을 추가한 다음 템플릿의 다른 컨트롤과 겹치지 않도록 이동하고 크기를 조정합니다.

    ![레이블 추가](./media/add-gallery/add-text-box.png)

3. 갤러리를 선택 하 고 오른쪽 창의 **속성** 탭에서 **필드** 옆에 있는 **편집** 을 선택 합니다.

4. 이 절차의 앞부분에서 추가한 레이블을 선택한 다음 **데이터** 창에서 강조 표시된 목록을 엽니다.

    ![드롭다운 목록 열기](./media/add-gallery/open-dropdown.png)

5. 해당 목록에서 **가격**을 클릭하거나 탭합니다.

    **갤러리** 컨트롤은 새 값을 보여 줍니다.

    ![최종 갤러리](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>갤러리 필터링 및 정렬
**갤러리[ 컨트롤의 ](controls/properties-core.md)** Items 속성은 표시하는 항목을 결정합니다. 이 절차에서는 필터 조건을 기반으로 표시 되는 레코드와 순서를 결정 하도록 해당 속성을 구성 합니다.

![검색 상자 및 정렬 아이콘](./media/add-gallery/text-search-box.png)

1. **갤러리[ 컨트롤의 ](controls/properties-core.md)** Items 속성을 이 수식으로 설정합니다.

    ```powerapps-dot
    Sort
        (If
            (IsBlank(TextSearchBox1.Text),
            FlooringEstimates,
            Filter(
                FlooringEstimates,
                TextSearchBox1.Text in Text(Name)
            )
        ),
        Name,
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

    이 수식의 함수에 대한 자세한 내용은 [수식 참조](formula-reference.md)를 참조하세요.

1. 검색 상자를 두 번 클릭 한 다음 제품 이름 일부 또는 전체를 입력 합니다.

    필터 조건을 충족 하는 항목만 표시 됩니다.

1. Alt 키를 누른 상태에서 정렬 아이콘을 한 번 이상 선택 하 여 정렬 순서를 전환 합니다.

    레코드는 제품 이름을 기준으로 오름차순 및 내림차순 사전순으로 전환 됩니다.

## <a name="highlight-the-selected-item"></a>선택한 항목 강조 표시
**갤러리** 컨트롤의 템플릿 **채우기** 속성을이 예와 비슷한 수식으로 설정 하지만 원하는 경우 다른 색을 지정할 수 있습니다.

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>기본 선택 변경
**갤러리** 컨트롤의 **Default** 속성을 기본으로 선택하려는 레코드로 설정합니다. 예를 들어 **FlooringEstimates** 데이터 원본에 다섯 번째 항목을 지정할 수 있습니다.

**Last(FirstN(FlooringEstimates, 5))**

이 예제에서는 **FlooringEstimates** 데이터 원본의 **Hardwood** 범주에서 첫 번째 항목을 지정합니다.

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>다음 단계
[양식](working-with-forms.md) 및 [수식](working-with-formulas.md)을 사용하는 방법을 알아봅니다.
