---
title: IfError 함수 | Microsoft Docs
description: PowerApps의 IfError 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 63a837eff2944569f5f66223690b11ddcfd399f6
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215921"
---
# <a name="iferror-function-in-powerapps"></a>PowerApps의 IfError 함수

오류를 감지하고 대체 값을 제공하거나 작업을 수행합니다.

## <a name="description"></a>설명

> [!NOTE]
> 이 함수는 실험적 기능의 일부이며 변경될 수 있습니다. 이 항목에 설명 된 동작은 경우에만 사용할 수는 *수식 수준 오류 관리* 기능이 설정 되어 있습니다. 이 응용 프로그램 수준 설정은 기본적으로 해제 되어 있습니다. 이 기능을 켜려면 엽니다는 *파일* 탭을 선택 *앱 설정* 에서 왼쪽 메뉴를 선택 합니다 *실험적 기능*합니다. 여러분의 피드백은 매우 소중합니다. [PowerApps 커뮤니티 포럼](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)에 의견을 남겨주세요.

합니다 **IfError** 함수는 오류 결과 찾을 때까지 하나 이상의 값을 테스트 합니다. 함수는 오류를 찾은 경우 해당 값을 반환 합니다. 그렇지 않은 경우 기본값을 반환합니다. 두 경우 모두, 함수, 평가할 수식 또는 다른 형태의 결과 표시 하려면 문자열을 반환할 수 있습니다. 합니다 **IfError** 함수와 유사 합니다 **경우** 함수: **IfError** 오류에 대 한 테스트 하는 동안 **하는 경우** 에 대 한 테스트 **true**합니다.

사용 하 여 **IfError** 오류 값 유효한 값으로 바꿔야 합니다. 예를 들어, 사용자 입력 0으로 나누기에서 발생할 경우이 함수를 사용 합니다. 수식을 작성 하는 결과 0 이거나 적합 한 앱에 대 한 다운스트림 계산을 진행할 수 있도록 하는 다른 값으로 바꿉니다. 수식이 예제 처럼 간단할 수 있습니다.

```powerapps-dot
IfError( 1/x, 0 )
```

경우 값 **x** 수식은 0 되지 **1 / x**합니다. 그렇지 않으면 **1 / x** 는 오류를 생성 하 고 수식을 0이 대신 반환 합니다.

사용 하 여 **IfError** 에 [동작 수식](../working-with-formulas-in-depth.md) 이 패턴에서와 같이 추가 작업을 수행 하기 전에 오류에 대 한 작업 및 검사를 수행 하려면:

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

첫 번째 패치 문제, 첫 번째 발생 하는 경우 **알릴** 실행, 추가 처리 없이 발생 하 고 두 번째 패치를 실행 하지 않습니다. 두 번째 패치를 실행 하는 첫 번째 패치가 성공 하면 두 번째를 문제가 발생 하는 경우 **알릴** 실행 합니다.

수식 오류를 찾지 못하면 및 선택적 지정한 경우 *DefaultResult* 인수를 수식에는 해당 인수에 대해 지정한 값을 반환 합니다. 수식 오류를 찾지 못하면 해당 인수를 지정 하지 않은 경우 수식은 마지막 *값* 인수를 평가 합니다.

## <a name="syntax"></a>구문

**IfError**( *Value1*, *Fallback1* [, *Value2*, *Fallback2*, ... [, *DefaultResult* ] ] )

* *값* -필수 항목입니다. 오류 값을 테스트할 수식입니다.
* *Fallback(s)* - 필수 항목입니다. 수식을 평가 하 고 일치 하는 경우에 반환할 값 *값* 인수 오류를 반환 합니다.
* *DefaultResult* - 선택 항목입니다.  수식은 오류를 찾지 못하면 평가할 수식입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **IfError( 1, 2 )** |첫 번째 인수는 오류가 아닙니다. 함수를 확인 하려면 다른 오류가 있고 값을 반환 합니다. 기본값은 없습니다. 반환 된 마지막 *값* 인수를 평가 합니다.   | 1 |
| **IfError( 1/0, 2 )** | 첫 번째 인수 (때문에 0으로 나누기) 오류 값을 반환 합니다. 함수는 두 번째 인수를 평가 하 고 결과로 반환 합니다. | 2 |
| **IfError( 1/0, Notify( "내부 문제가 있었습니다.", NotificationType.Error ) )** | 첫 번째 인수 (때문에 0으로 나누기) 오류 값을 반환 합니다. 두 번째 인수를 평가 하 고 사용자에 게 메시지를 표시 합니다. **IfError**의 반환 값은 **Notify**의 반환 값이며 **IfError**(숫자)의 첫 번째 인수와 동일한 형식으로 강제 변환됩니다. | 1 |
| **IfError( 1, 2, 3, 4, 5 )** | 첫 번째 인수는 함수 인수의 대체 (fallback) 해당 계산 되지 않고 있으므로 오류가 아닙니다. 세 번째 인수를 함수 인수의 대체 (fallback) 해당 계산 되지 않고 있으므로 오류가 발생 하거나, 아닙니다. 다섯 번째 인수 없는 해당 대체 (fallback) 고 기본 결과입니다. 함수는 수식에 오류가 포함 되어 있으므로 해당 결과 반환 합니다. | 5 |

### <a name="step-by-step"></a>단계별 가이드

1. **[텍스트 입력](../controls/control-text-input.md)** 컨트롤을 추가하고 기본 이름이 없는 경우 이름을 **TextInput1**로 지정합니다.

2. **[레이블](../controls/control-text-box.md)** 컨트롤을 추가하고 기본 이름이 없는 경우 이름을 **Label1**로 지정합니다.

3. **Label1**의 **Text** 속성에 대한 수식을 다음과 같이 설정합니다.

    **IfError( Value( TextInput1.Text ), -1 )**

4. **TextInput1**에 **1234**를 입력합니다.  

    Label1에 **1234** 값이 표시됩니다. 이것이 Value 함수에 대한 유효한 입력이기 때문입니다.

5. **TextInput1**에 **ToInfinity**를 입력합니다.

    Label1에 **-1** 값이 표시됩니다. 이것은 Value 함수에 대한 유효한 입력이 아니기 때문입니다.  IfError를 사용하여 Value 함수를 래핑하지 않으면 오류 값이 공백으로 처리되므로 레이블에 값이 표시되지 않습니다. 

