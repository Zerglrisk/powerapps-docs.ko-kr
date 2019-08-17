---
title: 캔버스 앱의 테이블 이해 | Microsoft Docs
description: PowerApps에서 캔버스 앱 테이블, 열 및 레코드 작업에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b35f8efdc090cc899476a65d73fd8cb3a4200faf
ms.sourcegitcommit: 9163abbe9a24298f216f15139f977adfd2c3f2ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550379"
---
# <a name="understand-canvas-app-tables-and-records-in-powerapps"></a>PowerApps에서 캔버스 앱 테이블 및 레코드 이해

PowerApps에서 Microsoft Excel, SharePoint, SQL Server 및 레코드와 테이블에 데이터를 저장하는 다른 여러 원본의 정보에 액세스하는 캔버스 앱을 만들 수 있습니다. 이러한 종류의 데이터로 가장 효과적으로 작업하려면 이러한 구조의 기반이 되는 개념을 검토합니다.

* 레코드는 사람, 장소 또는 사물에 대한 하나 이상의 정보 범주를 포함합니다. 예를 들어 레코드에는 단일 고객의 이름, 이메일 주소 및 전화 번호가 포함될 수 있습니다. 다른 도구에서는 레코드를 "행" 또는 "항목"이라고 합니다.
* 테이블은 동일한 범주의 정보가 포함된 하나 이상의 레코드를 포함합니다. 예를 들어 테이블에는 50명 고객의 이름, 이메일 주소 및 전화 번호가 포함될 수 있습니다.

앱에서 [수식](working-with-formulas.md)을 사용하여 레코드와 테이블을 생성, 업데이트 및 조작합니다. 아마 확장된 테이블인 외부 [데이터 원본](working-with-data-sources.md)에서도 데이터를 읽고 쓸 것입니다. 또한 [컬렉션](working-with-data-sources.md#collections)라고 하는 하나 이상의 내부 테이블을 만들 수도 있습니다.

Excel 수식에서 하나 이상의 셀 참조를 인수로 사용하는 것처럼 테이블 이름을 인수로 사용하여 다양한 수식을 작성할 수 있습니다. PowerApps 수식 중 일부는 지정한 다른 인수를 반영하는 테이블을 반환합니다. 예를 들어 다음을 수행하는 수식을 만들 수 있습니다.

* **[Patch](functions/function-patch.md)** 함수에 대한 여러 인수 중 하나로 테이블을 지정하여 테이블의 레코드를 업데이트합니다.
* **[AddColumns](functions/function-table-shaping.md)** , **[DropColumns](functions/function-table-shaping.md)** 또는 **[RenameColumns](functions/function-table-shaping.md)** 함수에 대한 인수로 테이블을 지정하여 해당 테이블의 열을 추가, 제거 및 이름 변경합니다. 이러한 함수 중 어느 것도 원래 테이블을 수정하지는 않지만, 지정한 다른 인수에 따라 다른 테이블을 반환합니다.

## <a name="elements-of-a-table"></a>테이블 요소
![](media/working-with-tables/elements-of-a-table.png)

### <a name="records"></a>레코드
각 레코드에는 사람, 장소 또는 사물에 대한 정보 범주가 하나 이상 포함됩니다. 위의 예제에서는 각 제품(**초콜릿**, **빵** 및 **음료수**)에 대한 레코드와 각 정보 범주에 대한 열(**Price**, **Quantity on Hand** 및 **Quantity on Order**)을 표시합니다.

수식에서는 테이블의 컨텍스트 외부에 중괄호를 사용하여 레코드를 단독으로 참조할 수 있습니다. 예를 들어 다음 레코드 **는 {Name: "딸기", 가격: 7.99}** 은 (는) 테이블과 연결 되어 있지 않습니다. 이 예제에서 **Name** 및 **Price**와 같은 필드 이름은 큰따옴표로 묶지 않습니다.

### <a name="fields"></a>필드
필드는 레코드의 개별 정보 요소입니다. 이러한 종류의 필드를 특정 레코드에 대한 열의 값으로 시각화할 수 있습니다.

컨트롤과 마찬가지로 레코드에 **.** [연산자](functions/operators.md)를 사용하여 레코드의 필드를 참조합니다.  예를 들어 **First(Products).Name**은 **Products** 테이블의 첫 번째 레코드에 대한 **Name** 필드를 반환합니다.

필드는 **[GroupBy](functions/function-groupby.md)** 함수의 예제와 같이 다른 레코드 또는 테이블을 포함할 수 있습니다. 많은 수준의 레코드와 테이블을 원하는 만큼 중첩할 수 있습니다.

### <a name="columns"></a>열
열은 테이블에 있는 하나 이상의 레코드에 대해 동일한 필드를 참조합니다. 위의 예제에서 각 제품에는 가격 필드가 있으며, 해당 가격은 모든 제품에 대해 동일한 열에 있습니다.  위의 테이블에는 4개의 열이 있으며, 위쪽에서 가로로 표시됩니다.

* **Name**
* **Price**
* **Quantity on Hand**
* **Quantity on Order**

열의 이름은 해당 열의 필드를 반영합니다.

열 내의 모든 값은 동일한 데이터 형식입니다. 위의 예제에서 "Quantity on Hand"는 항상 숫자를 포함하며, 한 레코드에서 "12 단위"와 같은 문자열은 포함할 수 없습니다.  모든 필드의 값이 '공백'일 수도 있습니다.  

다른 도구에서 열을 "필드"로 참조했을 수도 있습니다.

> [!NOTE]
> 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 PowerApps는 공백을 **"\_x0020\_"** 으로 바꿉니다. 예를 들어 SharePoint 또는 Excel의 **"Column Name"** 은 데이터 레이아웃에 표시되거나 수식에 사용될 때 PowerApps에 **"Column_x0020_Name"** 으로 나타납니다.

### <a name="table"></a>Table
테이블은 하나 이상의 레코드로 구성되며, 각 레코드에는 레코드 간에 일관된 이름을 갖는 여러 필드가 있습니다.

데이터 원본 또는 컬렉션에 저장된 모든 테이블에는 테이블을 참조하고 테이블을 인수로 사용하는 함수로 전달하는 데 사용되는 이름이 있습니다.  또한 테이블은 함수 또는 수식의 결과일 수도 있습니다.

다음 예제와 같이 중괄호로 표현된 레코드 집합이 포함된 **[Table](functions/function-table.md)** 함수를 사용하여 수식에서 테이블을 표현할 수 있습니다.

`Table( { Value: "Strawberry" }, { Value: "Vanilla" } )`

대괄호가 있는 단일 열 테이블도 정의할 수 있습니다.  위에서 작성한 방법과 동일합니다.

`[ "Strawberry", "Vanilla" ]`

## <a name="table-formulas"></a>테이블 수식
Excel 및 PowerApps에서는 수식을 사용하여 숫자와 텍스트 문자열을 비슷한 방식으로 조작합니다.

* Excel의 경우 **A1** 셀에 **42**와 같은 값을 입력한 다음, 다른 셀에 **A1+2**와 같은 수식을 입력하여 **44**라는 값을 표시합니다.
* PowerApps의 경우 **Slider1**의 **[Default](controls/properties-core.md)** 속성을 **42**로 설정하고, 레이블의 **[Text](controls/properties-core.md)** 속성을 **Slider1.Value + 2**로 설정하여 **44**라는 값을 표시합니다.

두 경우 모두 인수 값(예: **A1** 셀의 숫자 또는 **Slider1**의 값)을 변경하면 계산된 값이 자동으로 변경됩니다.

마찬가지로 수식을 사용하여 테이블과 레코드의 데이터에 액세스하고 조작할 수 있습니다. **Min(Catalog, Price)** 와 같은 일부 수식에서는 **Catalog** 테이블의 **Price** 열에 있는 가장 낮은 값을 표시하기 위해 테이블 이름을 인수로 사용할 수 있습니다. **RenameColumns(Catalog, "Price", "Cost")** 와 같은 다른 수식은 전체 테이블을 반환 값으로 사용하여 **Catalog** 테이블의 모든 레코드를 반환하지만 **Price** 열의 이름을 **Cost**로 변경합니다.

숫자와 마찬가지로 테이블과 레코드를 포함한 수식은 기본 테이블 또는 레코드가 변경되면 자동으로 다시 계산됩니다. **Catalog** 테이블의 제품 원가가 이전 최소값 아래로 낮아지면 **[Min](functions/function-aggregates.md)** 수식의 반환 값이 이러한 변경과 일치하도록 자동으로 변경됩니다.

몇 가지 간단한 예제를 살펴보겠습니다.

1. 휴대폰에 비어 있는 앱을 만들고 다른 컨트롤을 포함하는 세로 **[갤러리](controls/control-gallery.md)** 컨트롤을 추가합니다.

    기본적으로 화면에는 **CustomGallerySample**이라는 테이블의 자리 표시자 텍스트가 표시됩니다. 화면 **[Gallery](controls/control-gallery.md)** 컨트롤의 **[Items](controls/properties-core.md)** 속성이 자동으로 해당 테이블로 설정됩니다.

    ![](media/working-with-tables/gallery-items.png)

    > [!NOTE]
    > 일부 컨트롤은 이해를 돕기 위해 다시 정렬되고 확대되었습니다.

2. **[Items](controls/properties-core.md)** 속성을 테이블 이름으로 설정하는 대신 다음 예제와 같이 테이블 이름을 인수로 포함하는 수식으로 설정합니다.

    `Sort(CustomGallerySample, SampleHeading, Descending)`

    이 수식은 테이블 이름을 첫 번째 인수로 사용하고, 테이블의 열 이름을 두 번째 인수로 사용하는 **[Sort](functions/function-sort.md)** 함수를 통합합니다. 또한 이 함수는 데이터를 내림차순으로 정렬하도록 규정하는 선택적인 세 번째 인수를 지원합니다.

    ![](media/working-with-tables/gallery-items-sort.png)

3. **[Items](controls/properties-core.md)** 속성을 다음 예제와 같이 이전 단계의 수식을 인수로 사용하고 테이블을 반환하는 수식으로 설정합니다.

    `FirstN(Sort(CustomGallerySample, SampleHeading, Descending), 2)`

    이 수식에서는 **[FirstN](functions/function-first-last.md)** 함수를 사용하여 테이블에 있는 특정 수의 레코드를 표시합니다. **[Sort](functions/function-sort.md)** 함수를 **[FirstN](functions/function-first-last.md)** 의 첫 번째 인수로, 숫자(이 경우 **2**)를 두 번째 인수로 사용하여 표시할 레코드 수를 지정합니다.

    전체 수식은 **SampleHeading** 열 기준 내림차순으로 정렬된 **CustomGallerySample** 테이블의 처음 두 레코드가 포함된 테이블을 반환합니다.

    ![](media/working-with-tables/gallery-items-sort-firstn.png)

## <a name="table-functions-and-control-properties"></a>Table 함수 및 컨트롤 속성

**Lower** 함수를 고려 하십시오. **시작** 변수에 **"hello, 세계"** 라는 텍스트 문자열이 포함 된 경우, 수식 **아래쪽 (환영)** 은 **"hello, 세계"** 를 반환 합니다.  이 함수는 어떤 방식으로든 해당 변수의 값을 변경 하지 않습니다. **Lower** 는 입력을 처리 하 고 출력을 생성 하는 순수 함수입니다. 이것이 전부입니다. 파생 작업이 없습니다. Excel의 모든 함수 및 PowerApps의 대부분의 함수는 통합 문서 또는 앱을 자동으로 다시 계산 하는 데 사용할 수 있는 순수 함수입니다.

PowerApps는 동일한 방식으로 테이블에서 작동 하는 일련의 함수를 제공 합니다. 이러한 함수는 테이블을 입력으로 사용 하 고 데이터의 전체 테이블을 필터링, 정렬, 변환, 축소 및 요약 합니다. 실제로는 **작은** 값으로 단일 값을 사용 하는 다른 많은 함수는 단일 열 테이블을 입력으로 사용할 수도 있습니다.

* **[Sort](functions/function-sort.md)** , **[Filter](functions/function-filter-lookup.md)** - 레코드를 정렬하고 필터링합니다.
* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** - 테이블의 처음 N 또는 마지막 N 레코드를 반환합니다.
* **[Abs](functions/function-numericals.md)** , **[Sqrt](functions/function-numericals.md)** , **[Round](functions/function-round.md)** , **[RoundUp](functions/function-round.md)** , **[RoundDown](functions/function-round.md)** - 단일 열 테이블의 각 레코드에 대한 산술 연산을 수행하여 결과의 단일 열 테이블을 만듭니다.
* **[Left](functions/function-left-mid-right.md)** , **[Mid](functions/function-left-mid-right.md)** , **[Right](functions/function-left-mid-right.md)** , **[Replace](functions/function-replace-substitute.md)** , **[Substitute](functions/function-replace-substitute.md)** , **[Trim](functions/function-trim.md)** , **[Lower](functions/function-lower-upper-proper.md)** , **[Upper](functions/function-lower-upper-proper.md)** , **[Proper](functions/function-lower-upper-proper.md)** - 단일 열 테이블의 각 레코드에 대한 문자열 조작을 수행하여 문자열의 단일 열 테이블을 만듭니다.
* **[Len](functions/function-len.md)** - 문자열 열의 경우 각 문자열의 길이가 포함된 단일 열 테이블을 반환합니다.
* **[Concatenate](functions/function-concatenate.md)** - 문자열의 여러 열을 연결하여 문자열의 단일 열 테이블을 만듭니다.
* **[AddColumns](functions/function-table-shaping.md)** , **[DropColumns](functions/function-table-shaping.md)** , **[RenameColumns](functions/function-table-shaping.md)** , **[ShowColumns](functions/function-table-shaping.md)** - 테이블에 대한 열 조작을 수행하여 다른 열이 포함된 새 테이블을 만듭니다.
* **[Distinct](functions/function-distinct.md)** - 중복 레코드를 제거합니다.
* **[Shuffle](functions/function-shuffle.md)** - 임의의 순서로 레코드를 섞습니다.
* **[HashTags](functions/function-hashtags.md)** - 문자열의 해시 태그를 검색합니다.
* **[Errors](functions/function-errors.md)** - 데이터 원본으로 작업할 때 오류 정보를 제공합니다.

이러한 함수 중 상당수는 단일 열 테이블을 입력으로 사용 합니다. 전체 테이블에 열이 하나만 있는 경우 이름을 기준으로 열을 지정할 수 있습니다. 테이블에 여러 열이 있는 경우에는 *table. 열* 구문을 사용 하 여 이러한 열 중 하나를 지정할 수 있습니다. 예를 들어 **Products.Name** 는 **Products** 테이블에서 **이름** 값이 하나인 단일 열 테이블을 반환 합니다.

**[Addcolumns](functions/function-table-shaping.md)** , **[RenameColumns](functions/function-table-shaping.md)** , **[showcolumns](functions/function-table-shaping.md)** 또는 **[dropcolumns](functions/function-table-shaping.md)** 함수를 사용 하 여 테이블의 모양을 완전히 변경할 수 있습니다. 다시 이러한 함수는 소스가 아닌 출력만 변경 합니다.

컨트롤의 속성은 테이블 일 수도 있습니다.

* **Items** -갤러리, 목록 상자 및 콤보 상자에 적용 됩니다. 이 속성은 갤러리 또는 목록에 표시 되는 테이블을 정의 합니다.
* **SelectedItems** -목록 상자와 콤보 상자에 적용 됩니다. **Selectmultiple** 이 사용 하도록 설정 된 경우이 속성은 사용자가 선택한 항목의 테이블을 정의 합니다.

## <a name="behavioral-formulas"></a>동작 수식

다른 함수는 데이터를 수정 하 고 부작용을 발생 시킬 수 있도록 특별히 설계 되었습니다. 이러한 함수는 순수 하지 않으므로 신중 하 게 빌드해야 하며 앱에서 값을 자동으로 다시 계산 하는에 참여할 수 없습니다. 이러한 함수는 [동작 수식](working-with-formulas-in-depth.md)내 에서만 사용할 수 있습니다.

* **[수집](functions/function-clear-collect-clearcollect.md)** , **[지우기](functions/function-clear-collect-clearcollect.md)** , **[clearcollect](functions/function-clear-collect-clearcollect.md)** -컬렉션 만들기, 지우기 및 데이터를 추가 합니다.
* **[Patch](functions/function-patch.md)** -레코드에서 하나 이상의 필드를 수정 합니다.
* **[Update](functions/function-update-updateif.md)** , **[UpdateIf](functions/function-update-updateif.md)** - 지정한 하나 이상의 기준과 일치하는 레코드를 업데이트합니다.
* **[Remove](functions/function-remove-removeif.md)** , **[RemoveIf](functions/function-remove-removeif.md)** - 지정한 하나 이상의 기준과 일치하는 레코드를 삭제합니다.

## <a name="record-formulas"></a>레코드 수식

개별 레코드에 대한 데이터를 계산하고, 개별 레코드를 인수로 사용하고, 개별 레코드를 반환 값으로 제공하는 수식을 작성할 수도 있습니다. 위의 갤러리 예제로 돌아가서 **Gallery1.Selected** 속성을 사용하여 사용자가 갤러리에서 선택한 레코드의 정보를 표시해 보겠습니다.

1. [**단추**](controls/control-button.md)를 추가 하 고 **[onselect](controls/properties-core.md)** 속성을 다음 수식으로 설정 합니다.<br>
    **Collect( SelectedRecord, Gallery1.Selected )**

2. Alt 키를 누른 상태에서 단추를 선택합니다.

3. **파일** 메뉴에서 **컬렉션**을 선택합니다.

    ![](media/working-with-tables/selected-collection.png)

이 수식은 갤러리에서 현재 선택한 레코드의 데이터뿐만 아니라 해당 갤러리의 각 컨트롤도 포함한 레코드를 반환합니다. 예를 들어 원래 테이블의 **SampleText** 열과 일치하는 **SampleText** 열 및 해당 열의 데이터가 표시되는 레이블을 나타내는 **Subtitle1** 열이 레코드에 모두 포함됩니다. **Subtitle1** 열에서 테이블 아이콘을 선택하여 해당 데이터를 드릴합니다.

> [!NOTE]
> **Subtitle1** 열의 이름은 **Subtitle2**이거나 이 항목에서 지정한 것과 다른 요소를 추가한 경우 유사할 수 있습니다.

이제 선택한 레코드가 있으므로 **.** 연산자를 사용하여 해당 레코드에서 개별 필드를 추출할 수 설정합니다.

1. **[Label](controls/control-text-box.md)** 컨트롤을 추가한 다음, 갤러리 및 단추 아래로 이동합니다.

1. 레이블의 **[Text](controls/properties-core.md)** 속성을 다음 식으로 설정합니다.<br>
    **"Selected: " & Gallery1.Selected.SampleHeading**

    ![](media/working-with-tables/gallery-selected.png)

레코드인 **Selected** 속성을 가져와서 **SampleHeading** 속성을 추출했습니다.

또한 레코드를 명명된 관련 값에 대한 범용 컨테이너로 사용할 수도 있습니다.

* **[UpdateContext](functions/function-updatecontext.md)** 및 **[Navigate](functions/function-navigate.md)** 함수 주위에 수식을 작성하면 레코드를 사용하여 업데이트하려는 [컨텍스트 변수](working-with-variables.md#use-a-context-variable)를 수집합니다.
* **[편집 양식](controls/control-form-detail.md)** 컨트롤에 **[Updates](controls/control-form-detail.md)** 속성을 사용하여 양식에서 사용자가 변경한 내용을 수집합니다.
* **[Patch](functions/function-patch.md)** 함수를 사용하여 데이터 원본을 업데이트하고 레코드도 병합합니다.

이 경우 레코드는 테이블의 일부가 되지 않습니다.

## <a name="record-functions-and-control-properties"></a>레코드 함수 및 컨트롤 속성
레코드를 반환하는 함수는 다음과 같습니다.

* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** - 테이블의 첫 번째 또는 마지막 레코드 또는 레코드를 반환합니다.
* **[Lookup](functions/function-filter-lookup.md)** - 테이블에서 하나 이상의 기준과 일치하는 첫 번째 레코드를 반환합니다.
* **[Patch](functions/function-patch.md)** - 데이터 원본을 업데이트하거나 레코드를 병합합니다.
* **[Defaults](functions/function-defaults.md)** - 데이터 원본에 대한 기본값을 반환합니다.

레코드를 반환하는 속성은 다음과 같습니다.

* **Selected** - 갤러리 및 목록 상자에 적용됩니다. 현재 선택한 레코드를 반환합니다.
* **Updates** - 갤러리에 적용됩니다.  사용자가 데이터 입력 양식에서 수행한 모든 변경 내용을 함께 가져옵니다.
* **[Update](functions/function-update-updateif.md)** - 텍스트 입력 컨트롤 및 슬라이더와 같은 입력 컨트롤에 적용됩니다. 갤러리에서 함께 가져올 수 있도록 개별 속성을 설정합니다.

## <a name="record-scope"></a>레코드 범위

일부 함수는 테이블의 모든 레코드에서 수식을 개별적으로 평가하여 작동합니다. 수식 결과는 다음과 같이 다양한 방법으로 사용됩니다.

* **AddColumns** - 수식에서 추가된 필드의 값을 제공합니다.
* **Average**, **Max**, **Min**, **Sum**, **StdevP**, **VarP** - 수식에서 집계할 값을 제공합니다.
* **Filter**, **Lookup** - 수식에서 레코드가 출력에 포함되어야 하는지 여부를 결정합니다.
* **Concat** - 수식에서 함께 연결할 문자열을 결정합니다.
* **Distinct** - 수식에서 중복된 레코드를 식별하는 데 사용되는 값을 반환합니다.
* **ForAll** 은 잠재적으로 부작용이 있는 모든 값을 반환할 수 있습니다.
* **Sort** - 수식에서 레코드를 정렬할 값을 제공합니다.
* **With** -Formula는 잠재적으로 부작용이 있는 모든 값을 반환할 수 있습니다.

이러한 수식 내에서는 처리되는 레코드의 필드를 참조할 수 있습니다. 이러한 각 함수는 수식이 평가되는 "레코드 범위"를 만들어 레코드의 필드를 최상위 식별자로 사용할 수 있습니다. 또한 앱 전체에서 컨트롤 속성과 다른 값을 참조할 수도 있습니다.

예를 들어 다음 **Products** 테이블을 가져옵니다.

![](media/working-with-tables/requested.png)

앱에서이 예제 테이블을 만들려면 단추를 삽입 하 고, **Onselect** 속성을이 수식으로 설정한 다음, 단추를 선택 합니다 (PowerApps Studio에서 Alt 키를 누르고 있는 동안 클릭).

```powerapps-dot
Set( Products,
    Table(
        { Product: "Widget",    'Quantity Requested': 6,  'Quantity Available': 3 },
        { Product: "Gadget",    'Quantity Requested': 10, 'Quantity Available': 20 },
        { Product: "Gizmo",     'Quantity Requested': 4,  'Quantity Available': 11 },
        { Product: "Apparatus", 'Quantity Requested': 7,  'Quantity Available': 6 }
    )
)
```

이러한 제품 중 하나를 사용 가능한 것 보다 더 많이 요청 했는지 여부를 확인 하려면 다음을 수행 합니다.

`Filter( Products, 'Quantity Requested' > 'Quantity Available' )`

**Filter**의 첫 번째 인수는 작업할 레코드의 테이블이고, 두 번째 인수는 수식입니다.  **Filter**는 각 레코드의 필드를 사용할 수 있는 이 수식을 평가할 레코드 범위를 만듭니다. 이 경우에는 **Product**, **Quantity Requested** 및 **Quantity Available**입니다.  비교 결과는 각 레코드가 함수의 결과에 포함되어야 하는지 여부를 결정합니다.

![](media/working-with-tables/needed.png)

이 예제에 추가하여 주문할 각 제품의 양을 계산할 수 있습니다.

```powerapps-dot
AddColumns( 
    Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
    "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
)
```

여기서는 계산 열을 결과에 추가합니다. **AddColumns**에는 요청된 항목과 사용 가능한 항목 간의 차이를 계산하는 데 사용하는 자체의 레코드 범위가 있습니다.

![](media/working-with-tables/toorder.png)

마지막으로, 결과 테이블을 원하는 열로만 줄일 수 있습니다.

```powerapps-dot
ShowColumns(
    AddColumns(
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ),
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available'
    ),
    "Product",
    "Quantity To Order"
)
```

![](media/working-with-tables/toorderonly.png)

위의 예제에서 일부 항목에는 큰따옴표(")를 사용하고 다른 항목에는 작은따옴표(')를 사용했습니다.  개체 이름에 공백이 포함된 개체(예: 필드 또는 테이블)의 값을 참조할 때는 작은따옴표가 필요합니다.  큰따옴표는 **AddColumns**의 경우와 같이 개체의 값을 참조하지 않고 해당 개체에 대해 언급하는 경우, 특히 개체가 아직 없는 상황에서 사용됩니다.

## <a name="disambiguation"></a>명확성

레코드 범위에 추가된 필드 이름은 앱의 다른 위치에서 동일한 이름을 재정의합니다.  이 경우 [ **@** 명확성](functions/operators.md) 연산자를 사용하여 레코드 범위 외부의 값에 계속 액세스할 수 있습니다.

* 중첩된 레코드 범위의 값에 액세스하려면 다음 패턴을 사용하여 작업 중인 테이블의 이름에 **@** 연산자를 사용합니다.<br>_Table_ **[@** _FieldName_ **]**
* 데이터 원본, 컬렉션 및 컨텍스트 변수와 같은 전역 값에 액세스하려면 테이블 지정 없이 **[@** _ObjectName_ **]** 패턴을 사용합니다.

작업 중인 테이블이 **Filter(** _Table_ **,** ... **)** 과 같은 식이면 명확성 연산자를 사용할 수 없습니다.  가장 안쪽의 레코드 범위만 명확성 연산자를 사용하지 않고 이 테이블 식의 필드에 액세스할 수 있습니다.

예를 들어 **X** 컬렉션이 있다고 가정해 보겠습니다.

![](media/working-with-tables/X.png)

**ClearCollect( X, \[1, 2\] )** 를 사용하여 이 컬렉션을 만들 수 있습니다.

그리고 또 다른 **Y** 컬렉션이 있습니다.

![](media/working-with-tables/Y.png)

**ClearCollect( Y, ["A", "B"] )** 를 사용하여 이 컬렉션을 만들 수 있습니다.

또한 다음 수식을 사용 하 여 **값** 이라는 컨텍스트 변수를 정의 합니다. **UpdateContext ({Value: "!"})**

이제 모두 정리해 보겠습니다. 이 컨텍스트에서 수식은 다음과 같습니다.

```powerapps-dot
Ungroup(
    ForAll( X,
        ForAll( Y,
            Y[@Value] & Text( X[@Value] ) & [@Value]
        )
    ),
    "Value"
)
```

다음 테이블이 생성됩니다.

![](media/working-with-tables/XY.png)

여기서는 무슨 일이 있나요?  가장 바깥쪽의 **ForAll** 함수는 **X**에 대한 레코드 범위를 정의하므로 처리되는 각 레코드의 **Value** 필드에 대한 액세스를 허용합니다.  단순히 **Value** 단어를 사용하거나 **X[@Value]** 를 사용하여 액세스할 수 있습니다.

가장 안쪽의 **ForAll** 함수는 **Y**에 대한 다른 레코드 범위를 정의합니다.  이 테이블에는 **Value** 필드가 정의되어 있으므로 여기서 **Value**를 사용하면, **Y** 레코드의 필드를 참조하고 더 이상 **X**의 필드는 참조하지 않습니다.  여기서 **X**의 **Value** 필드에 액세스하려면 명확성 연산자와 함께 더 긴 버전을 사용해야 합니다.

**Y**가 가장 안쪽의 레코드 범위이므로 이 테이블의 필드에 액세스하는 데 명확성이 필요하지 않습니다. 따라서 다음 수식을 사용하여 동일한 결과를 얻을 수 있습니다.

```powerapps-dot
Ungroup(
    ForAll( X,
        ForAll( Y,
            Value & Text( X[@Value] ) & [@Value]
        )
    ),
    "Value"
)
```

모든 **ForAll** 레코드 범위는 전역 범위를 재정의합니다. 정의한 **값** 컨텍스트 변수는 명확성 연산자 없이 이름으로 사용할 수 없습니다. 이 값에 액세스 하려면 **[@Value]** 을 사용 합니다.

중첩 된 **ForAll** 함수는 중첩 된 결과 테이블을 생성 하기 때문에 **그룹을 해제** 하면 결과가 평면화 됩니다.

## <a name="single-column-tables"></a>단일 열 테이블

테이블에서 단일 열에 대해 작업 하려면 다음 예제와 같이 **Showcolumns** 함수를 사용 합니다.

```powerapps-dot
ShowColumns( Products, "Product" )
```

이 수식은 다음과 같은 단일 열 테이블을 생성 합니다.

![](media/working-with-tables/single-column.png)

또 다른 방법은 *테이블*에서 *열* 만의 단일 열 테이블을 추출 하는 *table. column*을 지정 하는 것입니다. 예를 들어이 수식은 **Showcolumns**를 사용 하는 것과 정확히 동일한 결과를 생성 합니다.

```powerapps-dot
Products.Product
```

## <a name="inline-records"></a>인라인 레코드

레코드는 명명된 필드 값이 포함된 중괄호를 사용하여 표현합니다.  예를 들어 다음 수식을 사용하여 이 항목의 시작 부분에 테이블의 첫 번째 레코드를 표현할 수 있습니다.

`{ Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 }`

다음 예제와 같이 다른 수식 내에 수식을 포함할 수도 있습니다.

`{ Name: First(Products).Name, Price: First(Products).Price * 1.095 }`

다음 예제와 같이 중괄호를 중첩하여 레코드를 중첩할 수 있습니다.

`{ 'Quantity': { 'OnHand': ThisItem.QuantOnHand, 'OnOrder': ThisItem.QuantOnOrder } }`

공백이나 콜론과 같은 특수 문자가 포함된 각각의 열 이름은 작은따옴표로 묶습니다.  열 이름 내에서 작은따옴표를 사용하려면 작은따옴표를 두 번 지정합니다.

**Price** 열의 값에는 $ 기호와 같은 통화 기호가 포함되지 않습니다. 값이 표시될 때 해당 형식이 적용됩니다.  

## <a name="inline-tables"></a>인라인 테이블
**[Table](functions/function-table.md)** 함수와 레코드 집합을 사용하여 테이블을 만들 수 있습니다. 다음 수식을 사용하여 이 항목의 시작 부분에 테이블을 표현할 수 있습니다.

```powerapps-dot
Table( 
    { Name: "Chocolate", Price: 3.95, 'Quantity on Hand': 12, 'Quantity on Order': 10 },
    { Name: "Bread", Price: 4.95, 'Quantity on Hand': 34, 'Quantity on Order': 0 },
    { Name: "Water", Price: 4.95, 'Quantity on Hand': 10, 'Quantity on Order': 0 } 
)
```

테이블을 중첩할 수도 있습니다.

```powerapps-dot
Table( 
    { Name: "Chocolate", 
      'Quantity History': Table( { Quarter: "Q1", OnHand: 10, OnOrder: 10 },
                                 { Quarter: "Q2", OnHand: 18, OnOrder: 0 } ) 
    }
)
```

## <a name="inline-value-tables"></a>인라인 값 테이블
대괄호 안에 값을 지정하여 단일 열 테이블을 만들 수 있습니다. 결과 테이블에는 **Value**라는 단일 열이 있습니다.

예 `[ 1, 2, 3, 4 ]` 를 들어는 `Table( { Value: 1 }, { Value: 2 }, { Value: 3 }, { Value: 4 } )` 와 같으며이 테이블을 반환 합니다.

![](media/working-with-tables/inline-table.png)

