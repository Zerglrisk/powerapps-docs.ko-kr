---
title: IfError 함수 | Microsoft Docs
description: PowerApps의 IfError 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8d9916c3fa62aab947315b7c31daa96f7e528acd
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680285"
---
# <a name="iferror-function-in-powerapps"></a>PowerApps의 IfError 함수

오류를 감지하고 대체 값을 제공하거나 작업을 수행합니다.

## <a name="description"></a>설명

> [!NOTE]
> 이 함수는 실험적 기능의 일부이며 변경될 수 있습니다. 이 항목에서 설명 하는 동작은 *수식 수준 오류 관리* 기능이 설정 되어 있는 경우에만 사용할 수 있습니다. 이 앱 수준 설정은 기본적으로 해제 되어 있습니다. 이 기능을 설정 하려면 *파일* 탭을 열고 왼쪽 메뉴에서 *앱 설정* 을 선택한 다음 *실험적 기능*을 선택 합니다. 의견은 microsoft에 매우 유용 합니다. [Power Apps 커뮤니티 포럼](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)에서 의견을 알려주세요.

**IfError** 함수는 오류 결과를 찾을 때까지 하나 이상의 값을 테스트 합니다. 함수에서 오류를 발견 한 경우 함수는 해당 값을 반환 합니다. 그렇지 않으면이 함수는 기본값을 반환 합니다. 두 경우 모두 함수는 표시할 문자열, 평가할 수식 또는 다른 형태의 결과를 반환할 수 있습니다. **IfError** 함수는 **if** 함수와 유사 합니다. **IfError** 에서 오류를 테스트 하는 반면 **if** 는 **true**를 테스트 합니다.

**IfError** 를 사용 하 여 오류 값을 유효한 값으로 바꿉니다. 예를 들어 사용자 입력으로 인해 0으로 나누기가 발생 하는 경우이 함수를 사용 합니다. 결과를 0 또는 앱에 적절 한 다른 값으로 대체 하는 수식을 작성 하 여 다운스트림 계산이 진행 될 수 있도록 합니다. 수식은 다음 예와 같이 간단할 수 있습니다.

```powerapps-dot
IfError( 1/x, 0 )
```

**X** 값이 0이 아닌 경우 수식은 **1/x**를 반환 합니다. 그렇지 않으면 **1/x** 는 오류를 생성 하 고 수식에서 0을 반환 합니다.

[동작 수식](../working-with-formulas-in-depth.md) 에서 **IfError** 를 사용 하 여 작업을 수행 하 고이 패턴에서와 같이 추가 작업을 수행 하기 전에 오류를 확인 합니다.

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

첫 번째 패치에 문제가 발생 하면 첫 번째 **알림이** 실행 되 고, 추가 처리가 발생 하지 않고, 두 번째 패치가 실행 되지 않습니다. 첫 번째 패치가 성공 하면 두 번째 패치가 실행 되 고, 문제가 발생 하면 두 번째 **알림이** 실행 됩니다.

수식에서 오류를 찾을 수 없고 선택적인 *Defaultresult* 인수를 지정한 경우 수식에서 해당 인수에 대해 지정한 값을 반환 합니다. 수식에서 오류를 찾을 수 없고 해당 인수를 지정 하지 않은 경우 수식에서 계산 된 마지막 *값* 인수가 반환 됩니다.

## <a name="syntax"></a>구문

**IfError**( *Value1*, *Fallback1* [, *Value2*, *Fallback2*, ... [, *Defaultresult* ]] )

* *Value (s)* -필수 항목입니다. 오류 값을 테스트할 수식입니다.
* *Fallback(s)* - 필수 항목입니다. 일치 하는 *값* 인수가 오류를 반환한 경우 평가할 수식과 반환할 값입니다.
* *DefaultResult* - 선택 항목입니다.  수식에서 오류를 찾지 못하는 경우 평가할 수식입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **IfError( 1, 2 )** |첫 번째 인수는 오류가 아닙니다. 함수에 확인할 다른 오류가 없으며 기본 반환 값이 없습니다. 함수는 계산 된 마지막 *값* 인수를 반환 합니다.   | 1 |
| **IfError( 1/0, 2 )** | 첫 번째 인수는 0으로 나누기 때문에 오류 값을 반환 합니다. 함수는 두 번째 인수를 계산 하 여 결과로 반환 합니다. | 2 |
| **IfError( 1/0, Notify( "내부 문제가 있었습니다.", NotificationType.Error ) )** | 첫 번째 인수는 0으로 나누기 때문에 오류 값을 반환 합니다. 함수는 두 번째 인수를 계산 하 고 사용자에 게 메시지를 표시 합니다. **IfError**의 반환 값은 **Notify**의 반환 값이며 **IfError**(숫자)의 첫 번째 인수와 동일한 형식으로 강제 변환됩니다. | 1 |
| **IfError (1, 2, 3, 4, 5)** | 첫 번째 인수는 오류가 아니므로 함수는 해당 인수의 해당 대체 (fallback)를 평가 하지 않습니다. 세 번째 인수는 오류가 아니므로 함수는 해당 인수의 해당 대체 (fallback)를 평가 하지 않습니다. 다섯 번째 인수에는 해당 하는 대체 (fallback)가 없으며 기본 결과입니다. 함수는 수식에 오류가 없기 때문에 결과를 반환 합니다. | 5 |

### <a name="step-by-step"></a>단계별 가이드

1. **[텍스트 입력](../controls/control-text-input.md)** 컨트롤을 추가하고 기본 이름이 없는 경우 이름을 **TextInput1**로 지정합니다.

2. **[레이블](../controls/control-text-box.md)** 컨트롤을 추가하고 기본 이름이 없는 경우 이름을 **Label1**로 지정합니다.

3. **Label1**의 **Text** 속성에 대한 수식을 다음과 같이 설정합니다.

    **IfError( Value( TextInput1.Text ), -1 )**

4. **TextInput1**에 **1234**를 입력합니다.  

    Label1에 **1234** 값이 표시됩니다. 이것이 Value 함수에 대한 유효한 입력이기 때문입니다.

5. **TextInput1**에 **ToInfinity**를 입력합니다.

    Label1에 **-1** 값이 표시됩니다. 이것은 Value 함수에 대한 유효한 입력이 아니기 때문입니다.  IfError를 사용하여 Value 함수를 래핑하지 않으면 오류 값이 공백으로 처리되므로 레이블에 값이 표시되지 않습니다. 

