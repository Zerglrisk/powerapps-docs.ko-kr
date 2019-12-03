---
title: Revert 함수 | Microsoft Docs
description: Power Apps의 Revert 함수에 대 한 구문과 예제를 포함 한 참조 정보
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
ms.openlocfilehash: efaffeac79c104d517d8e7da5b2e324fcac3eecb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730336"
---
# <a name="revert-function-in-power-apps"></a>Power Apps에서 함수 되돌리기
[데이터 원본](../working-with-data-sources.md)의 [레코드](../working-with-tables.md#records)를 새로 고치고 오류를 지웁니다.

## <a name="description"></a>설명
**Revert** 함수는 전체 데이터 원본을 새로 고치거나 데이터 원본의 단일 레코드를 새로 고칩니다. 다른 사용자가 변경한 내용을 볼 수 있습니다.

되돌린 레코드에 대해 **Revert**는 **[Errors](function-errors.md)** 함수가 반환한 [테이블](../working-with-tables.md)에 오류가 있으면 지웁니다.

**[Errors](function-errors.md)** 함수가 **[Patch](function-patch.md)** 나 기타 데이터 작업 후에 충돌을 보고하면 충돌하는 버전으로 시작하도록 레코드를 **되돌리고** 변경 사항을 다시 적용합니다.

**Revert**는 반환 값이 없습니다. [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Revert**( *DataSource* [, *Record* ] )

* *DataSource* – 필수 항목이며, 되돌릴 데이터 원본입니다.
* *Record* - 선택 항목입니다.  되돌릴 레코드입니다.  레코드를 지정하지 않으면 전체 데이터 원본이 되돌려집니다.

## <a name="example"></a>예
아래 예제는 다음 테이블의 데이터로 시작하는 **IceCream**이라는 데이터 원본을 되돌립니다.

![](media/function-revert/icecream.png)

다른 디바이스의 사용자가 **Strawberry** 레코드의 **Quantity** 속성을 **400**으로 변경합니다.  같은 시간에 다른 변경을 모르는 상태에서 같은 레코드의 동일한 속성을 **500**으로 변경합니다.

**[Patch](function-patch.md)** 함수를 사용하여 레코드를 업데이트합니다.<br>
**Patch( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ), { Quantity: 500 } )**

**[Errors](function-errors.md)** 테이블을 확인하고 오류를 찾습니다.

| 레코드 | [열](../working-with-tables.md#columns) | 메시지 | 오류 |
| --- | --- | --- | --- |
| **{ ID: 1, Flavor: "Strawberry", Quantity: 300 }** |*공백* |**"수정 하려는 레코드를 다른 사용자가 수정 했습니다.  레코드를 되돌린 후 다시 시도 하십시오. "** |**ErrorKind.Conflict** |

**오류** 열에 따라 **[OnSelect](../controls/properties-core.md)** 속성이 다음 수식으로 설정된 **다시 설정** 단추가 있습니다.<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

**Reload** 단추를 선택한 후 **[오류](function-errors.md)** 테이블이 [비워지고](function-isblank-isempty.md) **Strawberry**에 대한 새 값이 로드됩니다.

![](media/function-revert/icecream-after.png)

이전 변경 사항 위에 변경 사항을 다시 적용하면 충돌이 해결되었으므로 변경이 성공합니다.

![](media/function-revert/icecream-success.png)

