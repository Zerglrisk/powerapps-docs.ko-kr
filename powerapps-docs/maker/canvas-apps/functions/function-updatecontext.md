---
title: UpdateContext 함수 | Microsoft Docs
description: PowerApps에서 UpdateContext 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/08/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7750ad239df87e99d2321be20293b64153110fc1
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71991819"
---
# <a name="updatecontext-function-in-powerapps"></a>PowerApps의 UpdateContext 함수
현재 화면의 [컨텍스트 변수](../working-with-variables.md#use-a-context-variable)를 만들거나 업데이트합니다.

## <a name="overview"></a>개요
**UpdateContext** 함수를 사용하여 정보(예: 사용자가 버튼을 선택한 횟수 또는 데이터 작업의 결과)를 임시로 보관하는 컨텍스트 변수를 만듭니다.

컨텍스트 변수는 범위가 화면으로 한정되므로 다른 화면의 컨텍스트 변수를 참조하는 수식을 작성할 수 없습니다. 다른 프로그래밍 도구를 사용했다면 컨텍스트 변수를 로컬 변수와 비슷하다고 생각할 수 있습니다.  [**Set** 함수](function-set.md)를 사용하여 앱 전체에서 사용할 수 있는 전역 변수로 작업합니다.  

PowerApps는 사용자가 앱과 상호 작용할 때 자동으로 다시 계산되는 수식을 기반으로 합니다.  컨텍스트 변수는 이러한 이점이 활용되지 않기 때문에 앱을 만들고 이해하기 어려울 수 있습니다.  컨텍스트 변수를 사용하기 전에 [변수 작업](../working-with-variables.md)을 검토하세요.

## <a name="description"></a>설명
컨텍스트 변수를 만들거나 업데이트하려면 **UpdateContext** 함수에 단일 [레코드](../working-with-tables.md#records)를 전달합니다. 각 레코드에 변수 이름을 정의하거나 일치시키는 [열](../working-with-tables.md#columns)의 이름과 해당 변수를 설정할 값을 지정합니다.

* 이전에 정의한 변수의 이름을 지정하면 **UpdateContext**는 변수 값을 지정한 값으로 설정합니다.
* 아직 존재하지 않는 변수의 이름을 지정하면 **UpdateContext**는 해당 이름의 변수를 만들고 해당 변수의 값을 사용자가 지정한 값으로 설정합니다.
* 이전에 변수를 정의했지만 이 특정 **UpdateContext** 수식에 지정하지 않은 경우 해당 값은 동일하게 유지됩니다.

컨텍스트 변수는 **UpdateContext** 또는 [**Navigate** 함수](function-navigate.md)를 사용하여 암시적으로 생성합니다.  명시적 선언은 필요하지 않습니다.  컨텍스트 변수에 대한 모든 **UpdateContext** 및 **Navigate** 참조를 제거하는 경우 컨텍스트 변수가 사라집니다.  변수를 지우려면 변수의 값을 [**Blank** 함수](function-isblank-isempty.md)의 결과로 설정하십시오.

변수의 값, 정의 및 용도는 제작 환경의 파일 메뉴에 있는 변수 보기를 사용하여 볼 수 있습니다.

변수의 열 이름을 사용하여 수식에서 컨텍스트 변수를 참조합니다. 예를 들어 **UpdateContext( { ShowLogo: true } )** 는 **ShowLogo**라는 컨텍스트 변수를 만들고 해당 값을 **true**로 설정합니다. 그러면 수식에서 **ShowLogo**라는 이름을 사용하여 이 컨텍스트 변수 값을 사용할 수 있습니다.  이미지 컨트롤의 **Visible** 속성에 대한 수식으로 **ShowLogo**를 쓰고 컨텍스트 변수의 값이 **true** 또는 **false**인지 여부에 따라 해당 컨트롤을 표시하거나 숨길 수 있습니다.

이 항목의 뒷부분에 나오는 예제에서 보듯이 컨텍스트 변수는 다음을 비롯한 여러 가지 정보를 보유할 수 있습니다.

* 단일 값
* 레코드
* 테이블
* 개체 참조
* 수식의 결과

컨텍스트 변수는 앱을 닫을 때까지 값을 유지합니다.  컨텍스트 변수를 정의하고 특정 화면에서 해당 값을 설정하면 사용자가 다른 화면으로 전환하더라도 해당 정보가 그대로 유지됩니다.  앱이 닫히면 컨텍스트 변수의 값이 손실되고 앱이 다시 로드될 때 다시 생성되어야 합니다.  

모든 컨텍스트 변수는 범위가 화면으로 한정됩니다. 한 화면에서 컨텍스트 변수를 정의하고 해당 변수를 다른 화면에서 수정하려면 **[Navigate](function-navigate.md)** 함수를 기반으로 수식을 작성해야 합니다.  또는 전역 변수를 사용합니다.

**UpdateContext**에는 반환 값이 없으며 [동작 수식](../working-with-formulas-in-depth.md) 내에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**UpdateContext**(*UpdateRecord*)

* *UpdateRecord* – 필수. 하나 이상의 열 및 해당 열에 대한 값을 포함하는 레코드입니다. 사용자가 지정한 각 열과 값에 대해 컨텍스트 변수를 만들거나 업데이트합니다.

**Updatecontext**({ *ContextVariable1*: *Value1* [, *ContextVariable2*: *Value2* [, ...] ] } )

* *ContextVariable1* - 필수.  만들거나 업데이트할 컨텍스트 변수의 이름입니다.
* *Value1* - 필수.  컨텍스트 변수에 할당할 값입니다.
* *ContextVariable2*: *Value2*, ...-선택 사항입니다. 만들거나 업데이트할 추가 컨텍스트 변수 및 값입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **UpdateContext( {&nbsp;Counter:&nbsp;1&nbsp;} )** |컨텍스트 변수 **Counter**를 생성하거나 수정하고 값을 **1**로 설정합니다. |**Counter**의 값은 **1**입니다. 수식에 **Counter**라는 이름을 사용하여 해당 변수를 참조할 수 있습니다. |
| **UpdateContext( {&nbsp;Counter:&nbsp;2&nbsp;} )** |앞 예제의 **Counter** 컨텍스트 변수 값을 **2**로 설정합니다. |**Counter**의 값은 **2**입니다. |
| **UpdateContext( {&nbsp;Name:&nbsp;"Lily",&nbsp;Score:&nbsp;10&nbsp;} )** |컨텍스트 변수 **Name** 및 **Score**를 생성하거나 수정하고 값을 각각 **Lily** 및 **10**으로 설정합니다. |**Name**에는 **Lily** 값이 있고 **Score**에는 **10** 값이 있습니다. |
| **UpdateContext( {&nbsp;Person:&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;} )** |컨텍스트 변수 **Person**을 생성하거나 수정하고 값을 레코드로 설정합니다. 이 레코드는 **Name**과 **Address**라는 두 개의 열을 포함합니다. **Name** 열의 값은 **Milton**이고 **Address** 열의 값은 **1 Main St**입니다. |**Person**의 값은 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** 라는 레코드입니다.<br><br>이 레코드 전체를 **Person**이라는 이름으로 참조하거나 이 레코드의 개별 열을 **Person.Name** 또는 **Person.Address**로 참조합니다. |
| **Updatecontext ({&nbsp; 명: Patch (&nbsp;Person, &nbsp; {Address: &nbsp; "2 @ no__t-3Main @ no__t-4St" &nbsp;} &nbsp;)} &nbsp;)** |**[Patch](function-patch.md)** 함수로 **Address** 열의 값을 **2 Main St**로 설정하여 **Person** 컨텍스트 변수를 업데이트합니다. |이제 **Person**의 값은 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** 라는 레코드입니다. |

### <a name="step-by-step-example"></a>단계별 예제
1. 기본 화면 이름을 **Source**로 지정하고 다른 화면을 추가한 후 이름을 **Target**으로 지정합니다.
2. **Source** 화면에서 단추 두 개를 추가하고 해당 **[Text](../controls/properties-core.md)** 속성을 하나는 **English**로, 다른 하나는 **Spanish**로 설정합니다.
3. **English** 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 이 식으로 설정합니다.<br>**Navigate(Target, ScreenTransition.Fade, {Language:"English"})**
4. **Spanish** 단추의 **[OnSelect](../controls/properties-core.md)** 속성을 이 식으로 설정합니다.<br>**Navigate(Target, ScreenTransition.Fade, {Language:"Spanish"})**
5. **Target** 화면에서 레이블을 추가하고 해당 **[Text](../controls/properties-core.md)** 속성을 이 식으로 설정합니다.<br>**If(Language="English", "Hello!", "Hola!")**
6. **Target** 화면의 **Insert** 탭에서 **Shapes**를 선택한 후 뒤로 화살표를 선택합니다.
7. 뒤로 화살표의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.<br>**Navigate(Source, ScreenTransition.Fade)**
8. **Source** 화면에서 F5 키를 누른 후 두 언어 중 하나에 대한 단추를 선택합니다.

    **Target** 화면에 선택한 단추에 해당하는 언어로 레이블이 나타납니다.
9. 뒤로 화살표를 선택하여 **Source** 화면으로 돌아간 후 다른 언어에 대한 단추를 선택합니다.

    **Target** 화면에 선택한 단추에 해당하는 언어로 레이블이 나타납니다.
10. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

[또 다른 예](../add-screen-context-variables.md)

