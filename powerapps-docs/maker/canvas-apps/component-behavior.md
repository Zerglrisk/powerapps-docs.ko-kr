---
title: 구성 요소에 대 한 동작 수식 | Microsoft Docs
description: 구성 요소 기반 작업이 발생할 때 하나 이상의 작업을 수행 하도록 앱을 트리거합니다.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 9/30/2019
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: baf7e74581819b3ea21542f30f96a0a6f517c0d5
ms.sourcegitcommit: 60fd1792430b9f3da08ec161cb2277506d795e3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71705041"
---
# <a name="behavior-formulas-for-components"></a>구성 요소에 대 한 동작 수식

> [!IMPORTANT]
> 이 기능은 아직 실험적 이며 기본적으로 사용 하지 않도록 설정 되어 있습니다. 자세한 내용은 [실험적 및 미리 보기 기능](working-with-experimental.md)을 참조 하세요.

이벤트에서 구성 요소 인스턴스의 변경을 트리거할 때 실행 되는 하나 이상의 [동작 수식을](working-with-formulas-in-depth.md) 지정 합니다. 예를 들어 구성 요소의 **Onreset** 속성을 초기화를 수행 하 고, 입력을 지우고, **다시** 설정 함수가 구성 요소 인스턴스에서 실행 될 때 값을 다시 설정 하는 하나 이상의 수식으로 설정 합니다.

## <a name="onreset"></a>OnReset

구성 요소 마스터가 선택 된 상태에서 수식 입력줄의 왼쪽에 있는 속성의 드롭다운 목록에서 **Onreset** 을 선택 하 고 하나 이상의 수식을 입력 합니다.

> [!div class="mx-imgBorder"]
> ![OnReset 예 @ no__t-1

**Onreset**을 테스트 하려면 구성 요소를 다시 설정 하도록 컨트롤을 구성 합니다. 예를 들어 단추의 **Onselect** 속성을 다음 수식으로 설정 합니다. **Reset**(*ComponentName*).

### <a name="example---reset-timer"></a>예제-타이머 다시 설정

> [!div class="mx-imgBorder"]
> ![OnReset 예 @ no__t-1

이 시간 선택 구성 요소에는 시간 _selectedHour 및 _Selectedhour을 표시 하는 두 개의 변수가 사용 됩니다. 선택이 다시 설정 되 면 다음 변수를 기본값으로 다시 설정 해야 합니다 (예: 12: 10.  구성 요소의 OnReset 속성에는 다음 수식이 있습니다. **Set (_selectedHour, 12); Set (_selectedMinute, 12)**

재설정을 트리거하려면 화면으로 이동 하 여 구성 요소의 인스턴스를 삽입 합니다. 단추를 추가 하 고 **reset (TimerComponent_instance)** 을 호출 하 여 onselect을 트리거하는 단추의 onselect를 구성 합니다.

> [!div class="mx-imgBorder"]
> ![Reset 단추 @ no__t-1

## <a name="update-onreset-using-custom-property"></a>사용자 지정 속성을 사용 하 여 OnReset 업데이트

구성 요소의 외부에서 구성 요소 인스턴스를 다시 설정 하는 것 외에도, 내부에서 OnReset을 트리거하는 또 다른 방법이 있습니다. "**값이 변경 될 때 OnReset 설정**"은 사용자 지정 입력 속성을 만들 때 옵션 이며이 속성의 값을 변경 하 여 구성 요소의 onreset을 트리거할 수 있습니다. 이 메서드는 기본값을 쉽게 설정 하 고 다시 설정 하도록 디자인 되었습니다. 

> ![OnReset 예제](./media/component-behavior/property-trigger.png)

### <a name="example"></a>예

> [!div class="mx-imgBorder"]
> ![OnReset 예 @ no__t-1

주문 번호를 검토 하 고 숫자를 업데이트 하는 예입니다. 숫자 위쪽 및 아래쪽 구성 요소는 주문 수를 늘리거나 줄이는 데 사용 됩니다. 왼쪽의 갤러리를 선택 하면 선택한 도구의 주문 번호를 표시 하도록 기본 숫자 위로 및 아래로 구성 요소가 다시 설정 됩니다. "**값이 변경 되 면 설정 다시 설정 발생**"을 통해 입력이 변경 될 때 기본값을 다시 설정할 수 있습니다. 

이렇게 하려면 기본 입력 속성의 "**값이 변경 될 때 다시 설정 발생**"을 선택 합니다. 구성 요소의 **Onreset** 은 **set (_NumericValue, ' Numeric up ')로 설정 됩니다. DefaultValue)** . _numericValue는 현재 순서 값의 값을 저장 하는 변수입니다. 텍스트 입력 컨트롤의 **기본값** 을 **If (Isblank (_numericValue), ' Numeric up ')로 설정 합니다. DefaultValue, _numericValue)** . 
