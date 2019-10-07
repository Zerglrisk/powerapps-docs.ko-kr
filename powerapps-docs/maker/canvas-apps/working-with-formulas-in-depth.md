---
title: 캔버스 앱의 동작 수식 이해 | Microsoft Docs
description: PowerApps에서 캔버스 앱의 상태를 변경하는 동작 수식 작업에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 546c19dd0bc767758fcf854e383be0f075717525
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71988014"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-powerapps"></a>PowerApps의 캔버스 앱에 대한 동작 수식 이해

대부분의 수식은 값을 계산합니다.  Excel 스프레드시트와 마찬가지로 값이 변경될 때마다 다시 계산이 자동으로 수행됩니다.  예를 들어 **[레이블](controls/control-text-box.md)** 컨트롤의 값은 0보다 작으면 빨간색으로 표시하고, 그렇지 않으면 검정색으로 표시할 수 있습니다. 따라서 해당 컨트롤의 **[Color](controls/properties-color-border.md)** 속성을 다음 수식으로 설정할 수 있습니다.

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

이 컨텍스트에서 사용자가 **[단추](controls/control-button.md)** 컨트롤을 선택하는 경우 어떤 의미가 있을까요?  값이 변경되지 않았으므로 계산할 새 항목은 없습니다. Excel에는 **[단추](controls/control-button.md)** 컨트롤에 해당하는 함수가 없습니다.  

**[단추](controls/control-button.md)** 컨트롤을 선택하면 다음과 같이 사용자가 앱의 상태를 변경하는 일련의 작업 또는 동작을 시작합니다.

* 표시 되는 화면을 변경 합니다. **[뒤로](functions/function-navigate.md)** 및 **[탐색](functions/function-navigate.md)** 함수
* [신호](functions/signals.md)제어: 함수를 **[설정](functions/function-enable-disable.md)** 및 **[해제](functions/function-enable-disable.md)** 합니다.
* [데이터 원본](working-with-data-sources.md)에서 항목 새로 고침, 업데이트 또는 제거: **[Refresh](functions/function-refresh.md)** , **[Update](functions/function-update-updateif.md)** , **[updateif](functions/function-update-updateif.md)** , **[Patch](functions/function-patch.md)** , **[remove](functions/function-remove-removeif.md)** , **[removeif](functions/function-remove-removeif.md)** 함수
* [컨텍스트 변수](working-with-variables.md#use-a-context-variable)를 업데이트 합니다.  **[Updatecontext](functions/function-updatecontext.md)** 함수입니다.
* [컬렉션](working-with-data-sources.md#collections)에서 항목 만들기, 업데이트 또는 제거:  **[Collect](functions/function-clear-collect-clearcollect.md)** , **[Clear](functions/function-clear-collect-clearcollect.md)** , **[clearcollect](functions/function-clear-collect-clearcollect.md)** 함수

이러한 함수는 앱의 상태를 변경하기 때문에 자동으로 다시 계산할 수 없습니다. 동작 수식이라고 하는 **[OnSelect](controls/properties-core.md)** , **[OnVisible](controls/control-screen.md)** , **[OnHidden](controls/control-screen.md)** 및 기타 **On...** 속성의 수식에 사용할 수 있습니다.

### <a name="more-than-one-action"></a>둘 이상의 작업
세미콜론을 사용하여 수행할 작업의 목록을 만듭니다. 예를 들어 다음과 같이 컨텍스트 변수를 업데이트한 다음 이전 화면으로 돌아갈 수도 있습니다.

* **Updatecontext ({x: 1}); Back ()**

작업은 수식에 표시된 순서대로 수행됩니다.  현재 함수가 완료될 때까지 다음 함수는 시작되지 않습니다. 오류가 발생하면 후속 함수가 시작되지 않을 수 있습니다.

