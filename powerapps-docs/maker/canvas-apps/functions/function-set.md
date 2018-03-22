---
title: Set 함수 | Microsoft Docs
description: PowerApps의 Set 함수에 대한 구문과 예제를 포함한 참조 정보
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/29/2017
ms.author: gregli
ms.openlocfilehash: ef44d704d16892c7c37ac4fbf7c3eebc0ffcb966
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2018
---
# <a name="set-function-in-powerapps"></a>PowerApps의 Set 함수
전역 변수의 값을 설정합니다.

## <a name="overview"></a>개요
**Set** 함수를 사용하면 정보(예: 사용자가 버튼을 선택한 횟수 또는 데이터 작업의 결과)를 임시로 보관하는 전역 변수의 값을 설정할 수 있습니다.  

전역 변수는 앱 전체의 모든 화면에서 사용할 수 있습니다.  가장 간단한 종류의 변수이며 대부분의 상황에서 필요를 충족합니다.  또한 테이블에 대한 행 수준 수정을 허용하는 컬렉션 및 단일 화면으로 범위가 지정된 컨텍스트 변수도 있습니다.  다른 옵션에 대한 자세한 내용은 [변수 작업](../working-with-variables.md)을 참조하세요.

PowerApps는 사용자가 앱과 상호 작용할 때 자동으로 다시 계산되는 수식을 기반으로 합니다.  전역 변수는 이러한 이점이 활용되지 않기 때문에 앱을 만들고 이해하기 어려울 수 있습니다.  변수를 사용하기 전에 [변수 작업](../working-with-variables.md)을 검토하세요.

## <a name="description"></a>설명
전역 변수는 **Set** 함수를 사용하여 암시적으로 생성됩니다.  명시적 선언은 필요하지 않습니다.  전역 변수에 대한 **Set** 함수를 모두 제거하면 해당 전역 변수가 사라집니다.  변수를 지우려면 변수의 값을 [**Blank** 함수](function-isblank-isempty.md)의 결과로 설정하십시오.

변수의 값, 정의 및 용도는 제작 환경의 파일 메뉴에 있는 변수 보기를 사용하여 볼 수 있습니다.

이 문서의 뒷부분에 나오는 예제에서 보듯이 전역 변수는 다음을 비롯한 여러 가지 정보를 보유할 수 있습니다.

* 단일 값
* 레코드
* 테이블
* 개체 참조
* 수식의 결과

전역 변수는 앱을 닫을 때까지 값을 유지합니다.  전역 변수의 값은 앱이 닫히면 손실되고 앱이 다시 로드될 때 다시 생성되어야 합니다.

전역 변수는 기존 컬렉션이나 컨트롤과 동일한 이름을 사용할 수 없습니다.  컨텍스트 변수와 동일한 이름을 사용할 수 있습니다.  둘 사이의 모호함을 해결하려면 [명확성 연산자](operators.md#disambiguation-operator)를 사용하십시오.

**Set**에는 반환 값이 없으며 [동작 수식](../working-with-formulas-in-depth.md) 내에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Set**( *VariableName*, *Value* )

* *VariableName* - 필수 항목입니다.  만들거나 업데이트할 전역 변수의 이름입니다.
* *Value* - 필수 항목입니다.  컨텍스트 변수에 할당할 값입니다.

## <a name="examples"></a>예
| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Set(&nbsp;Counter,&nbsp;1&nbsp;)** |전역 변수 **Counter**를 생성하거나 수정하고 값을 **1**로 설정합니다. |**Counter**의 값은 **1**입니다. 원하는 화면의 수식에 **Counter**라는 이름을 사용하여 해당 변수를 참조할 수 있습니다. |
| **Set(&nbsp;Counter,&nbsp;2&nbsp;)** |앞 예제의 **Counter** 전역 변수 값을 **2**로 설정합니다. |**Counter**의 값은 **2**입니다. |
| **Set(&nbsp;Counter,&nbsp;Counter + 1&nbsp;)** |앞 예제의 **Counter** 전역 변수 값을 **3**으로 증가시킵니다. |**Counter**의 값은 **3**입니다. |
| **Set(&nbsp;Name,&nbsp;"Lily" )** |전역 변수 **Name**를 생성하거나 수정하고 값을 **Lily**로 설정합니다. |**Name**의 값은 **Lily**입니다. |
| **Set(&nbsp;Person,&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;} )** |전역 변수 **Person**을 생성하거나 수정하고 값을 레코드로 설정합니다. 이 레코드는 **Name**과 **Address**라는 두 개의 열을 포함합니다. **Name** 열의 값은 **Milton**이고 **Address** 열의 값은 **1 Main St**입니다. |**Person** 의 값은 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}**라는 레코드입니다.<br><br>이 레코드 전체를 **Person**이라는 이름으로 참조하거나 이 레코드의 개별 열을 **Person.Name** 또는 **Person.Address**로 참조합니다. |
| **Set(&nbsp;Person, Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;)&nbsp;)** |**[Patch](function-patch.md)** 함수로 **Address** 열의 값을 **2 Main St**로 설정하여 **Person** 전역 변수를 업데이트합니다. |이제 **Person**의 값은 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}**라는 레코드입니다. |

