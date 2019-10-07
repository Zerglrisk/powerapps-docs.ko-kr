---
title: Patch 함수 | Microsoft Docs
description: PowerApps의 Patch 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 711a15a93d1e3ed9839f5d51c0bfa32e00563852
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984338"
---
# <a name="patch-function-in-powerapps"></a>PowerApps의 Patch 함수
[데이터 원본](../working-with-data-sources.md)의 [레코드](../working-with-tables.md#records)를 하나 이상 수정 또는 생성하거나 데이터 원본 외부의 레코드를 병합합니다.

**Patch** 함수를 사용하여 복잡한 상황(예: 사용자 상호 작용이 필요하지 않거나 여러 화면에 걸쳐 있는 양식을 사용하는 업데이트를 수행하는 경우)의 레코드를 수정합니다.

덜 복잡한 상황에서는 **편집 양식** 컨트롤을 사용하여 데이터 원본의 레코드를 보다 쉽게 업데이트할 수 있습니다. **편집 양식** 컨트롤을 추가하면 사용자에게 양식을 제공하여 채운 다음 데이터 원본에 변경 내용을 저장합니다. 자세한 내용은 [데이터 폼 이해](../working-with-forms.md)를 참조하세요.

## <a name="overview"></a>개요
데이터 원본의 레코드를 하나 이상 수정하려면 **Patch** 함수를 사용합니다.  특정 [필드](../working-with-tables.md#elements-of-a-table)의 값은 다른 속성에 영향을 주지 않고 수정됩니다. 예를 들어 다음 수식은 Contoso라는 고객의 전화 번호를 변경합니다.

`Patch( Customers, First( Filter( Customers, Name = "Contoso" ) ), { Phone: “1-212-555-1234” } )`

레코드를 생성하려면 **Patch**를 **[Defaults](function-defaults.md)** 함수와 함께 사용합니다. 이 동작을 사용하여 레코드를 만들고 편집할 수 있는 [단일 화면](../working-with-data-sources.md)을 만듭니다. 예를 들어 다음 수식은 Contoso라는 고객의 레코드를 만듭니다.

`Patch( Customers, Defaults( Customer ), { Name: “Contoso” } )`

데이터 원본으로 작업하지 않더라도 **Patch**를 사용하여 둘 이상의 레코드를 병합할 수 있습니다. 예를 들어 다음 수식은 Contoso의 전화 번호와 위치를 식별하는 두 개의 레코드를 하나로 병합합니다.

`Patch( { Name: "Contoso", Phone: “1-212-555-1234” }, { Name: "Contoso", Location: “Midtown”  } )`

## <a name="description"></a>설명
### <a name="modify-or-create-a-record-in-a-data-source"></a>데이터 원본의 레코드 수정 또는 만들기
이 함수를 데이터 원본과 함께 사용하려면 데이터 원본을 지정한 다음, 기본 레코드를 지정합니다.

* 레코드를 수정하려면 데이터 원본에서 기본 레코드를 가져와야 합니다.  기본 레코드는 갤러리의 **[Items](../controls/properties-core.md)** 속성을 통해 오거나 [컨텍스트 변수](../working-with-variables.md#use-a-context-variable)에 있거나 다른 경로를 통해 올 수 있습니다. 다만, 기본 레코드를 데이터 원본으로 다시 추적할 수 있어야 합니다.  레코드에는 수정을 위해 다시 레코드를 찾는 데 도움이 되는 추가 정보가 포함되기 때문에 중요합니다.  
* 레코드를 만들려면 **[Defaults](function-defaults.md)** 함수를 사용하여 기본값으로 기본 레코드를 만듭니다.  

그런 다음, 기본 레코드의 속성 값을 재정의하는 새 속성이 포함된 변경 레코드를 하나 이상 지정합니다. 변경 레코드는 인수 목록의 처음부터 끝까지 순서대로 처리되며, 이후 속성 값이 이전 속성 값보다 우선합니다.

**Patch**의 반환 값은 사용자가 수정하거나 만든 레코드입니다.  레코드를 만든 경우, 반환 값에는 데이터 원본이 자동으로 생성한 속성이 포함될 수 있습니다.

데이터 원본을 업데이트할 때 하나 이상의 문제가 발생할 수 있습니다. **[Errors](function-errors.md)** 함수를 사용하여 [데이터 원본 작업](../working-with-data-sources.md)의 설명과 같이 문제를 식별하고 검사합니다.

관련 함수에는 전체 레코드를 바꾸는 데 사용할 수 있는 **[Update](function-update-updateif.md)** 함수와 레코드를 만드는 데 사용할 수 있는 **[Collect](function-clear-collect-clearcollect.md)** 함수가 있습니다.  **[UpdateIf](function-update-updateif.md)** 함수를 사용하여 조건에 따라 여러 레코드의 특정 속성을 수정할 수 있습니다.

### <a name="modify-or-create-a-set-of-records-in-a-data-source"></a>데이터 원본의 레코드 집합 수정 또는 만들기
**Patch**를 사용하면 단일 호출로 여러 레코드를 만들거나 수정할 수 있습니다.

단일 기본 레코드를 전달하는 대신 기본 레코드 테이블을 두 번째 인수에 제공할 수 있습니다.  변경 기록은 테이블에도 제공되며, 기본 레코드와 일대일 대응합니다.  각 변경 테이블의 레코드 수는 기본 테이블의 레코드 수와 동일해야 합니다.

이 방식으로 **Patch**를 사용하는 경우 반환 값 역시 기본 레코드와 변경 레코드가 일대일 대응하는 레코드가 있는 테이블입니다.

### <a name="merge-records-outside-of-a-data-source"></a>데이터 원본 외부에서 레코드 병합
병합할 둘 이상의 레코드를 지정합니다. 레코드는 인수 목록의 처음부터 끝까지 순서대로 처리되며, 이후 속성 값이 이전 속성 값보다 우선합니다.

**Patch**는 병합된 레코드를 반환하고 데이터 원본의 인수 또는 레코드를 수정하지는 않습니다.

## <a name="syntax"></a>구문
#### <a name="modify-or-create-a-record-in-a-data-source"></a>데이터 원본의 레코드 수정 또는 만들기
**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord1* [, *ChangeRecord2*, … ])

* *DataSource* – 필수 항목입니다. 수정할 레코드를 포함하거나 만들려는 레코드가 포함될 데이터 원본입니다.
* *BaseRecord* – 필수 항목입니다. 수정하거나 만들 레코드입니다.  데이터 원본에서 레코드를 받으면 레코드가 발견되고 수정됩니다. **[Defaults](function-defaults.md)** 의 결과가 사용되면 레코드가 생성됩니다.
* *ChangeRecord(s)* – 필수 항목입니다.  *BaseRecord*에서 수정할 속성이 포함된 하나 이상의 레코드입니다.  변경 레코드는 인수 목록의 처음부터 끝까지 순서대로 처리되며, 이후 속성 값이 이전 속성 값보다 우선합니다.

#### <a name="modify-or-create-a-set-of-records-in-a-data-source"></a>데이터 원본의 레코드 집합 수정 또는 만들기
**Patch**( *DataSource*, *BaseRecordsTable*, *ChangeRecordTable1* [, *ChangeRecordTable2*, ... ] )

* *DataSource* – 필수 항목입니다. 수정할 레코드를 포함하거나 만들려는 레코드가 포함될 데이터 원본입니다.
* *BaseRecordTable* – 필수 항목입니다. 수정하거나 만들 레코드 테이블입니다.  데이터 원본에서 레코드를 받으면 레코드가 발견되고 수정됩니다. **[Defaults](function-defaults.md)** 의 결과가 사용되면 레코드가 생성됩니다.
* *ChangeRecordTable(s)* – 필수 항목입니다.  *BaseRecordTable*의 각 레코드에 대해 수정할 속성이 포함된 하나 이상의 레코드 테이블입니다.  변경 레코드는 인수 목록의 처음부터 끝까지 순서대로 처리되며, 이후 속성 값이 이전 속성 값보다 우선합니다.

#### <a name="merge-records"></a>레코드 병합
**Patch**( *Record1*, *Record2* [, …] )

* *Record(s)* - 필수 항목입니다.  병합할 둘 이상의 레코드입니다. 레코드는 인수 목록의 처음부터 끝까지 순서대로 처리되며, 이후 속성 값이 이전 속성 값보다 우선합니다.

## <a name="examples"></a>예
#### <a name="modify-or-create-a-record-in-a-data-source"></a>레코드 수정 또는 만들기(데이터 원본 내부)
이 예제에서는 다음 [테이블](../working-with-tables.md)의 데이터를 포함하는 **IceCream**이라는 데이터 원본에서 레코드를 수정하거나 생성하고 **ID** [열](../working-with-tables.md#columns)에 값을 자동으로 생성합니다.

![](media/function-patch/icecream.png)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Patch(&nbsp;IceCream,<br>First( Filter( IceCream, Flavor = "Chocolate" ) ), {&nbsp;Quantity:&nbsp;400&nbsp;} )** |**IceCream** 데이터 원본의 레코드를 수정합니다.<ul><li> 수정할 레코드의 **ID** 열에는 값 **1**이 포함됩니다. (**Chocolate** 레코드가 이 ID를 갖습니다.)</li><li>**Quantity** 열의 값이 **400**으로 변경됩니다. |{&nbsp;ID:&nbsp;1, Flavor:&nbsp;"Chocolate", Quantity:&nbsp;400 }<br><br>**IceCream** 데이터 원본의 **Chocolate** 항목이 수정되었습니다. |
| **Patch( IceCream, Defaults(&nbsp;IceCream ), {&nbsp;Flavor:&nbsp;“Strawberry”&nbsp;}&nbsp;)** |**IceCream** 데이터 원본에 레코드를 만듭니다.<ul><li>**ID** 열에는 데이터 원본이 자동으로 생성한 값 **3**이 있습니다.</li><li>**Quantity** 열에는 **[Defaults](function-defaults.md)** 함수가 지정한 대로 **IceCream** 데이터 원본의 해당 열에 대한 기본값인 **0**이 있습니다.<li>**Flavor** 열에는 **Strawberry**라는 값이 있습니다.</li> |{ ID:&nbsp;3, Flavor:&nbsp;“Strawberry”, Quantity:&nbsp;0&nbsp;}<br><br>**IceCream** 데이터 원본에 **Strawberry** 항목이 생성되었습니다. |

이전 수식이 계산된 후 데이터 원본은 다음 값으로 끝납니다.

![](media/function-patch/icecream-after.png)

#### <a name="merge-records-outside-of-a-data-source"></a>레코드 병합(데이터 원본 외부)

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Patch(&nbsp;{&nbsp;Name:&nbsp;"James",&nbsp;Score:&nbsp;90&nbsp;}, {&nbsp;Name:&nbsp;"Jim",&nbsp;Passed:&nbsp;true&nbsp;} )** |데이터 원본 외부의 두 레코드를 병합합니다.<br><ul><li>각 레코드의 **Name** 열 값은 일치하지 않습니다. 결과에는 인수 목록의 시작에 더 가까운 레코드의 값(**James**) 대신 인수 목록의 끝에 더 가까운 레코드의 값(**Jim**)이 포함됩니다.</li><li>첫 번째 레코드에 두 번째 레코드에 없는 열(**Score**)이 포함되어 있습니다. 결과에는 이 열이 해당하는 값(**90**)과 함께 포함됩니다.</li><li>두 번째 레코드에 첫 번째 레코드에 없는 열(**Passed**)이 포함되어 있습니다. 결과에는 이 열이 해당하는 값(**true**)과 함께 포함됩니다. |{&nbsp;Name:&nbsp;"Jim", Score:&nbsp;90, Passed:&nbsp;true&nbsp;} |

