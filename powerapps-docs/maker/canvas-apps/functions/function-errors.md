---
title: Errors 함수 | Microsoft Docs
description: PowerApps의 Errors 함수에 대한 참조 정보이며, 구문과 예제를 포함하고 있습니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 114474696f85980da315b6dd225250dc1b197805
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992802"
---
# <a name="errors-function-in-powerapps"></a>PowerApps의 Errors 함수
[데이터 원본](../working-with-data-sources.md)의 이전 변경에 대한 오류 정보를 제공합니다.

## <a name="overview"></a>개요
데이터 원본의 [레코드](../working-with-tables.md#records)가 변경되면 오류가 발생할 수 있습니다.  네트워크 중단, 부적절한 권한 및 편집 충돌을 포함한 여러 가지 원인이 있을 수 있습니다.  

**[Patch](function-patch.md)** 함수 및 다른 데이터 함수는 오류를 직접 반환하지 않습니다. 대신 해당 작업의 결과를 반환합니다. 데이터 함수가 실행된 후에 **Errors** 함수를 사용하여 오류의 세부 정보를 얻을 수 있습니다.  **IsEmpty( Errors ( ... ) )** 수식에 **[IsEmpty]** 함수를 사용하여 오류가 있는지 확인할 수 있습니다.

**[Validate](function-validate.md)** 및 **[DataSourceInfo](function-datasourceinfo.md)** 함수를 사용하여 오류가 발생하기 전에 몇 가지 오류를 방지할 수 있습니다.  오류를 처리하고 방지하는 방법에 대한 더 많은 제안 사항은 [데이터 원본 작업](../working-with-data-sources.md)을 참조하세요.

## <a name="description"></a>설명
**Errors** 함수는 다음 [열](../working-with-tables.md#columns)이 포함된 오류의 [테이블](../working-with-tables.md)을 반환합니다.

* **레코드** -  오류가 발생한 데이터 원본의 레코드입니다.  레코드를 만드는 동안 오류가 발생하면 이 열은 *공백*입니다.
* **열** -  단일 열에 원인이 있는 오류인 경우 오류가 발생한 열입니다. 그렇지 않으면 *공백*이 됩니다.
* **메시지** -  오류에 대한 설명입니다.  이 오류 문자열은 최종 사용자에게 표시될 수 있습니다.  이 메시지는 데이터 원본에서 생성될 수 있고, 긴 메시지일 수도 있으며, 사용자에게 아무 의미가 없는 원시 열 이름을 포함할 수 있습니다.
* **오류** -  오류를 해결할 수 있도록 수식에 사용할 수 있는 다음과 같은 오류 코드입니다.

| ErrorKind | 설명 |
| --- | --- |
| ErrorKind.Conflict |동일한 레코드에 대한 또 다른 변경으로 인해 변경 충돌이 발생했습니다.  **[Refresh](function-refresh.md)** 함수를 사용하여 레코드를 다시 로드한 다음, 다시 변경합니다. |
| ErrorKind.ConstraintViolation |하나 이상의 제약 조건을 위반했습니다. |
| ErrorKind.CreatePermission |레코드를 만들려고 했지만 현재 사용자에게 레코드를 만들 수 있는 권한이 없습니다. |
| ErrorKind.DeletePermission |레코드를 삭제하려고 했지만 현재 사용자에게 레코드를 삭제할 수 있는 권한이 없습니다. |
| ErrorKind.EditPermission |레코드를 편집하려고 했지만 현재 사용자에게 레코드를 편집할 수 있는 권한이 없습니다. |
| ErrorKind.GeneratedValue |데이터 원본에서 자동으로 생성하는 열을 변경하려고 했습니다. |
| ErrorKind.MissingRequired |레코드에서 필수 열에 대한 값이 누락되었습니다. |
| ErrorKind.None |오류가 없습니다. |
| ErrorKind.NotFound |레코드를 편집하거나 삭제하려고 했지만 레코드를 찾을 수 없습니다.  다른 사용자가 해당 레코드를 변경했을 수 있습니다. |
| ErrorKind.ReadOnlyValue |읽기 전용 열을 변경하려고 했습니다. |
| ErrorKind.Sync |데이터 원본에서 오류가 보고되었습니다.  자세한 내용은 메시지 열을 확인합니다. |
| ErrorKind.Unknown |오류가 있었지만 알 수 없는 종류입니다. |
| ErrorKind.Validation |다른 종류 중 하나에 적합하지 않은 일반적인 유효성 검사 문제가 발견되었습니다. |

함수에 *Record* 인수를 제공하여 전체 데이터 원본 또는 선택한 행에 대한 오류를 반환할 수 있습니다.  

예를 들어 레코드를 만들 수 없는 경우 **[Patch](function-patch.md)** 또는 다른 데이터 함수에서 *공백* 값을 반환할 수 있습니다. *공백*을 **Errors**에 전달할 수 있으며, 이러한 경우 적절한 오류 정보를 반환합니다.  이후 동일한 데이터 원본에서 데이터 함수를 사용하면 이 오류 정보가 지워집니다.

오류가 없으면 **Errors**에서 반환하는 테이블은 [비어 있으며](function-isblank-isempty.md), **[IsEmpty](function-isblank-isempty.md)** 함수에서 테스트할 수 있습니다.

## <a name="syntax"></a>구문
**Errors**( *DataSource* [, *Record* ] )

* *DataSource* – 필수 항목이며, 오류를 반환하려는 데이터 원본입니다.
* *Record* – 선택 항목이며,  오류를 반환하려는 특정 레코드입니다. 이 인수를 지정하지 않으면 함수에서 전체 데이터 원본에 대한 오류를 반환합니다.

## <a name="examples"></a>예
### <a name="step-by-step"></a>단계별 예제
이 예제에서는 다음과 같은 **IceCream** 데이터 원본을 사용합니다.

![](media/function-errors/icecream.png)

사용자가 앱을 통해 초콜릿 레코드를 데이터 입력 양식에 로드한 다음, **Quantity** 값을 90으로 변경합니다.  사용할 레코드는 다음과 같은 **EditRecord** [컨텍스트 변수](../working-with-variables.md#use-a-context-variable)에 배치됩니다.

* **Updatecontext ({EditRecord: First (Filter (IceCream, 특색 = "초콜릿"))})**

데이터 원본에서 이 변경 작업을 수행하려면 **[Patch](function-patch.md)** 함수를 다음과 같이 사용합니다.

* **Patch( IceCream, EditRecord, Gallery.Updates )**

여기서 **Gallery. 업데이트** 는 **{수량:으로 평가 됩니다. **Quantity** 속성만 수정 되었으므로 90}** 입니다.

아쉽게도 **[Patch](function-patch.md)** 함수가 호출되기 직전에 다른 사람이 초콜릿에 대한 **Quantity**를 80으로 수정했습니다.  PowerApps는 이를 감지하고 충돌하는 변경이 발생하지 않도록 합니다.  다음 수식을 사용하여 이 상황을 확인할 수 있습니다.

* **IsEmpty( Errors( IceCream, EditRecord ) )**

여기서는 **Errors** 함수에서 다음 테이블을 반환했으므로 **false**가 반환됩니다.

| 레코드 | 열 | 메시지 | 오류 |
| --- | --- | --- | --- |
| 버전과 "초콜릿", Quantity: 100} |*공백* |"다른 사용자가 수정하려는 레코드를 수정했습니다. 레코드를 다시 로드하여 다시 시도하십시오." |ErrorKind.Conflict |

양식에 레이블을 배치하여 사용자에게 이 오류를 표시할 수 있습니다.

* 오류를 표시하려면 레이블의 **[Text](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
  **Label.Text = First(Errors( IceCream, EditRecord )).Message**

사용자가 충돌을 효율적으로 해결할 수 있도록 양식에 **다시 로드** 단추를 추가할 수도 있습니다.

* 충돌이 발생한 경우에만 단추를 표시하려면 단추의 **[Visible](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
    **!IsEmpty( Lookup( Errors( IceCream, EditRecord ), Error = ErrorKind.Conflict ) )**
* 사용자가 단추를 선택하는 변경 내용을 되돌리려면 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>
    **ReloadButton.OnSelect = Revert( IceCream, EditRecord )**

