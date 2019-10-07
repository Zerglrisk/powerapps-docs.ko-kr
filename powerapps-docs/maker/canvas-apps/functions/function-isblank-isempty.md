---
title: Blank, Coalesce, IsBlank 및 IsEmpty 함수 | Microsoft Docs
description: PowerApps의 Blank, Coalesce, IsBlank 및 IsEmpty 함수에 대한 참조 정보이며, 구문과 예제를 포함하고 있습니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d932d43bd9474f3cd7ca63ef0ef0a51a9e74ca91
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984751"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>PowerApps의 Blank, Coalesce, IsBlank 및 IsEmpty 함수
값이 비어 있거나 [테이블](../working-with-tables.md)에 [레코드](../working-with-tables.md#records)가 없는지 여부를 테스트하고 *공백* 값을 만드는 방법을 제공합니다.

## <a name="overview"></a>개요
*공백*은 "값 없음" 또는 "알 수 없는 값"에 대한 자리 표시자입니다.  예를 들어 사용자가 선택을 하지 않은 경우 **[콤보 상자](../controls/control-combo-box.md)** 컨트롤의 **Selected** 속성은 *공백* 입니다. 대부분의 데이터 소스는 PowerApps에서 *blank*로 표시 되는 NULL 값을 저장 하 고 반환할 수 있습니다.

PowerApps의 모든 속성 또는 계산 된 값은 *비워 둘*수 있습니다.  예를 들어 부울 값은 일반적으로 **true** 또는 **false** 값 중 하나입니다.  그러나 이러한 두 가지 외에도 상태를 알 수 없음을 나타내는 *비워* 둘 수 있습니다.  이는 Microsoft Excel과 유사 합니다. 여기서 워크시트 셀은 내용 없이 공백으로 시작 되지만 **TRUE** 또는 **FALSE** 값을 포함할 수 있습니다. 언제 든 지 셀의 내용을 다시 지워 *빈* 상태로 되돌릴 수 있습니다.

*빈 문자열* 은 문자가 포함 되지 않은 문자열을 참조 합니다.  [ **Len** 함수](function-len.md) 는 이러한 문자열에 대해 0을 반환 하 고, `""` 사이에 아무 것도 없는 두 개의 큰따옴표로 작성 될 수 있습니다.  일부 컨트롤 및 데이터 소스는 빈 문자열을 사용 하 여 "값 없음" 조건을 표시 합니다.  앱 만들기를 간소화 하기 위해 **isblank** 및 **병합** 함수는 *빈* 값 또는 빈 문자열을 모두 테스트 합니다.    

**IsEmpty** 함수의 컨텍스트에서 *empty* 는 레코드가 없는 테이블에만 적용 됩니다. 테이블 구조는 [열](../working-with-tables.md#columns) 이름을 포함한 채 그대로 완벽하게 유지될 수 있지만 테이블에는 데이터가 없습니다. 테이블은 비어있는 것으로 시작하여 레코드를 가져와서 더 이상 비어 있지 않으며, 그런 다음, 레코드를 제거하여 다시 비워둘 수 있습니다.

> [!NOTE]
> 전환 기간이 있습니다.  지금 까지는 *blank* 를 사용 하 여 오류를 보고 하 고 오류 로부터 유효한 "no value"를 구분할 수 없습니다.  이러한 이유로 인해 *빈* 값을 저장 하는 것은 로컬 컬렉션에 대해서만 지원 됩니다.  파일 메뉴, 앱 설정, 고급 설정, 실험적 기능에서 "수식 수준 오류 관리" 실험적 기능을 설정 하면 다른 데이터 원본에 *빈* 값을 저장할 수 있습니다.  이 기능을 완료 하 고 오류에서 *빈* 값의 적절 한 분리를 완료 하기 위해 적극적으로 노력 하 고 있습니다.

## <a name="description"></a>설명
**Blank** 함수는 *공백* 값을 반환합니다. 이 값을 지원하는 데이터 원본에 NULL 값을 저장하여 필드에서 값을 효과적으로 제거합니다.

**Isblank** 함수는 *빈* 값 또는 빈 문자열을 테스트 합니다.  값이 없는 경우 일부 데이터 소스 및 컨트롤에서 빈 문자열을 사용 하므로 응용 프로그램을 쉽게 만들 수 있도록 테스트에 빈 문자열이 포함 되어 있습니다.  *빈* 값을 특별히 테스트 하려면 **isblank**대신 `if( Value = Blank(), ...`을 사용 합니다.

**병합** 함수는 인수를 순서 대로 평가 하 고 *비어* 있지 않은 첫 번째 값 이나 빈 문자열을 반환 합니다.  이 함수를 사용 하 여 *빈* 값 이나 빈 문자열을 다른 값으로 바꿀 수*있지만 비어 있지* 않은 문자열 값 또는 비어 있지 않은 문자열 값은 변경 하지 않고 그대로 둡니다.  모든 인수가 *비어* 있거나 빈 문자열인 경우 함수는 빈 *문자열을 빈 값으로* 변환 하는 좋은 방법을 **병합** 하 *여 빈 문자열을 반환 합니다*.  **Coalesce**에 대한 모든 인수는 같은 형식이어야 합니다. 예를 들어 숫자와 텍스트 문자열을 함께 사용할 수 없습니다.  

`Coalesce( value1, value2 )`은 `If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )`에 해당 하는 보다 간결한 값 이며 **value1** 및 **value2** 를 두 번 평가할 필요가 없습니다.  [ **If** 함수](function-if.md) 는 여기에 있는 경우와 같이 "else" 수식이 없으면 *blank* 를 반환 합니다.

**IsEmpty** 함수는 테이블에 레코드가 있는지 여부를 테스트합니다. **[CountRows](function-table-counts.md)** 함수를 사용하여 0을 확인하는 것과 같습니다. **IsEmpty**를 **[Errors](function-errors.md)** 함수와 결합하여 데이터 원본 오류를 확인할 수 있습니다.

**IsBlank** 및 **IsEmpty** 모두에 대한 반환 값은 **true** 또는 **false** 부울 값입니다.

## <a name="syntax"></a>구문
**Blank**()

**Coalesce**( *Value1* [, *Value2*, ... ] )

* *Value(s)* – 필수 항목이며, 테스트할 값입니다.  *비어 있지 않고* 빈 문자열이 아닌 값을 찾을 때까지 각 값이 순서 대로 평가 됩니다.  이 시점 이후의 값은 계산 되지 않습니다.  

**IsBlank**( *Value* )

* *Value* – 필수 항목입니다. *빈* 값 또는 빈 문자열을 테스트할 값입니다.

**IsEmpty**( *Table* )

* *Table* - 필수 항목입니다. 레코드를 테스트할 테이블입니다.

## <a name="examples"></a>예
### <a name="blank"></a>비어 있음
> [!NOTE]
> 다음 예제는 현재 로컬 컬렉션에서만 작동합니다.  파일 메뉴, 앱 설정, 고급 설정, 실험적 기능에서 "수식 수준 오류 관리" 실험적 기능을 설정 하면 다른 데이터 원본에 *빈* 값을 저장할 수 있습니다.  이 기능을 완료 하 고 오류에서 *빈* 값의 분리를 완료 하기 위해 적극적으로 노력 하 고 있습니다.

1. 앱을 처음부터 만들고 **단추** 컨트롤을 추가합니다.
2. 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. 앱을 미리 보고, 추가한 단추를 클릭하거나 탭한 다음, 미리 보기를 닫습니다.  
4. **파일** 메뉴에서 **컬렉션**을 클릭하거나 탭합니다.

     **Cities** 컬렉션이 나타나서 "Seattle" 및 "비"가 있는 레코드 하나가 표시됩니다.

    !["비" 날씨가 있는 Seattle을 보여 주는 컬렉션](./media/function-isblank-isempty/seattle-rainy.png)
5. 기본 작업 영역으로 돌아가려면 뒤로 화살표를 클릭하거나 탭합니다.
6. **레이블** 컨트롤을 추가하고 **Text** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    **Weather** 필드에 값("비")이 있으므로 레이블에 **false**가 표시됩니다.
7. 두 번째 단추를 추가하고 **OnSelect** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. 앱을 미리 보고, 추가한 단추를 클릭하거나 탭한 다음, 미리 보기를 닫습니다.  

    **Cities**의 첫 번째 레코드의 **Weather** 필드는 *공백*으로 바뀌어 이전에 있었던 "비"를 제거합니다.

    ![공백인 Weather 필드가 있는 Seattle을 보여 주는 컬렉션](./media/function-isblank-isempty/seattle-blank.png)

    **Weather** 필드에 더 이상 값이 없으므로 레이블에 **true**가 표시됩니다.

### <a name="coalesce"></a>Coalesce

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **병합 (&nbsp;Blank (), &nbsp;1 @ no__t)** |**Blank** 함수의 반환 값을 테스트하며, 항상 *공백* 값을 반환합니다. 첫 번째 인수는 *비어* *있으므로 비어 있지 않은 값과* 비어 있지 않은 문자열을 찾을 때까지 다음 인수를 사용 하 여 계산이 계속 됩니다. |**1** |
| **병합 ("", 2)** |빈 문자열인 첫 번째 인수를 테스트 합니다. 첫 번째 인수는 빈 문자열*이므로 비어 있지 않은 값과* 비어 있지 않은 문자열을 찾을 때까지 다음 인수를 사용 하 여 계산이 계속 됩니다. |**2** |
| **병합 (Blank (), "", Blank (), "", 3, 4)** |**병합** 은 인수 목록의 시작 부분에서 시작 하*고 비어 있지 않은 값과* 비어 있지 않은 문자열을 찾을 때까지 각 인수를 차례로 계산 합니다.  이 경우 처음 네 개의 인수는 모두 *빈* 문자열이 나 빈 문자열을 반환 하므로 계산은 다섯 번째 인수를 계속 합니다. 다섯 번째 인수*는 비어 있지 않은 문자열이 며 여기* 에서 계산을 중지 합니다. 다섯 번째 인수의 값이 반환되고, 여섯 번째 인수는 평가되지 않습니다. |**3** |
| **병합 ("")** | 빈 문자열인 첫 번째 인수를 테스트 합니다. 첫 번째 인수가 빈 문자열이 고 더 이상 인수가 없으므로 함수는 *blank*를 반환 합니다.   |*공백* |

### <a name="isblank"></a>IsBlank
1. 앱을 처음부터 만들고, 텍스트 입력 컨트롤을 추가하고, 이름을 **FirstName**으로 지정합니다.
2. 레이블을 추가하고 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    텍스트 입력 컨트롤의 **[Text](../controls/properties-core.md)** 속성은 기본적으로 **"텍스트 입력"** 으로 설정됩니다. 속성에 값이 포함되어 있으므로 공백이 아니며 레이블에 메시지가 표시되지 않습니다.
3. 텍스트 입력 컨트롤에서 모든 공백을 포함하여 모든 문자를 제거합니다.

    **[텍스트](../controls/properties-core.md)** 속성은 더 이상 문자를 포함 하지 않으므로 빈 문자열이 고 **Isblank (FirstName)** 는 **true**가 됩니다. 필수 필드 메시지가 표시됩니다.

다른 도구를 사용하여 유효성 검사를 수행하는 방법에 대한 자세한 내용은 **[Validate](function-validate.md)** 함수 및 [데이터 원본 작업](../working-with-data-sources.md)을 참조하세요.  

다른 예제:

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **IsBlank (&nbsp;Blank () &nbsp;)** |**Blank** 함수의 반환 값을 테스트하며, 항상 *공백* 값을 반환합니다. |**true** |
| **IsBlank( "" )** |문자가 없는 문자열입니다. |**true** |
| **IsBlank( "Hello" )** |하나 이상의 문자가 포함된 문자열입니다. |**false** |
| **IsBlank( *AnyCollection* )** |[컬렉션](../working-with-data-sources.md#collections)이 있으므로 레코드가 없더라도 공백이 아닙니다. 빈 컬렉션을 확인하려면 **IsEmpty**를 대신 사용합니다. |**false** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |**[Mid](function-left-mid-right.md)** 에 대한 시작 문자가 문자열의 끝을 벗어납니다.  결과는 빈 문자열입니다. |**true** |
| **IsBlank( If( false, false ) )** |*ElseResult*가 없는 **[If](function-if.md)** 함수입니다.  조건이 항상 **false**이므로 이 **[If](function-if.md)** 는 항상 *공백*을 반환합니다. |**true** |

### <a name="isempty"></a>IsEmpty
1. 앱을 처음부터 만들고 **단추** 컨트롤을 추가합니다.
2. 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Collect (IceCream, {특색: "Strawberry", 수량: 300}, {버전: "초콜릿", Quantity: 100})**
3. 앱을 미리 보고, 추가한 단추를 클릭하거나 탭한 다음, 미리 보기를 닫습니다.  

    **IceCream**이라는 컬렉션이 만들어지고 다음 데이터가 포함되어 있습니다.

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    이 컬렉션에는 두 개의 레코드가 있으며 비어 있지 않습니다. **IsEmpty( IceCream )** 는 **false**를 반환하고, **CountRows( IceCream )** 는 **2**를 반환합니다.
4. 두 번째 단추를 추가하고 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **Clear( IceCream )**
5. 앱을 미리 보고, 두 번째 단추를 클릭하거나 탭한 다음, 미리 보기를 닫습니다.  

    이제 컬렉션은 다음과 같이 비어 있습니다.

    ![](media/function-isblank-isempty/icecream-clear.png)

    **[Clear](function-clear-collect-clearcollect.md)** 함수는 컬렉션에서 모든 레코드를 제거하여 빈 컬렉션을 만듭니다. **IsEmpty( IceCream )** 는 **true**를 반환하고, **CountRows( IceCream )** 는 **0**을 반환합니다.

또한 다음 예제와 같이 **IsEmpty**를 사용하여 계산된 테이블이 비어 있는지 여부를 테스트할 수 있습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |단일 열 테이블에는 세 개의 레코드가 있으므로 비어 있지 않습니다. |**false** |
| **IsEmpty( [&nbsp;] )** |단일 열 테이블에는 레코드가 없으며 비어 있습니다. |**true** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |단일 열 테이블에는 5보다 큰 값이 없습니다.  필터의 결과에 레코드가 없으며 비어 있습니다. |**true** |

