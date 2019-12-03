---
title: Rand 함수 | Microsoft Docs
description: Power Apps에서 Rand 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5f34be9a38f4e30bdf19f337a24580615a16697c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730439"
---
# <a name="rand-function-in-power-apps"></a>Power Apps의 Rand 함수
의사 난수를 반환합니다.

## <a name="description"></a>설명
**Rand** 함수는 0을 초과하고 1 미만인 의사 난수를 반환합니다.

## <a name="volatile-functions"></a>일시적 함수
**Rand**는 일시적 함수입니다.  이러한 함수는 평가될 때마다 다른 값을 반환합니다.  

데이터 흐름 수식을 사용하면 표시되는 수식을 다시 계산하는 경우 일시적 함수는 다른 값만을 반환합니다.  수식에서 변경되는 내용이 없으면 앱의 실행 과정에서 같은 값을 갖습니다.

예를 들어 앱이 활성화되어 있는 동안 **Label1.Text = Rand()** 를 포함한 레이블 컨트롤은 변경되지 않습니다.  앱을 닫았다가 다시 열면 새로운 값이 나타납니다.

함수가 다른 내용이 변경된 수식의 일부인 경우 다시 평가됩니다.  예를 들어 이 예제가 **Label1.Text = Slider1.Value + Rand()** 를 포함한 슬라이더 컨트롤을 포함하도록 변경하면 슬라이더 컨트롤의 값이 변경되고 레이블의 텍스트 속성이 다시 평가될 때마다 새로운 난수가 생성됩니다.  이 예제는 아래를 참조하세요.

[동작 수식](../working-with-formulas-in-depth.md)에서 사용될 경우 **Rand**는 동작 수식이 계산될 때마다 평가됩니다.  예제는 아래를 참조하세요.

## <a name="syntax"></a>구문
**Rand**()

## <a name="examples"></a>예

#### <a name="display-a-different-random-number-as-user-input-changes"></a>다른 난수를 사용자 입력 변경 내용으로 표시합니다.
1. **[슬라이더](../controls/control-slider.md)** 컨트롤을 추가하고, 다른 이름이 있는 경우 이름을 **Slider1**로 지정합니다.

1. **[레이블](../controls/control-text-box.md)** 컨트롤을 추가하고, **Text** 속성을 다음 수식으로 설정합니다.

    **Slider1.Value + Rand()**

    레이블은 **50**(슬라이더에 대한 기본값) 및 임의의 10진수를 표시합니다.

    ![50.741을 사용하여 레이블 컨트롤을 표시하는 화면](media/function-rand/rand-slider-1.png)

1. Alt 키를 누른 채 슬라이더의 값을 변경합니다.

    슬라이더의 값을 변경할 때마다 레이블의 소수 부분이 다른 난수를 표시합니다.

    ![네 개의 다른 슬라이더 설정에 대해 네 가지 임의의 10진수 값(70.899, 84.667, 90.134, 99.690)으로 레이블 컨트롤을 표시하는 네 개의 화면](media/function-rand/rand-slider-results.png)

#### <a name="create-a-table-of-random-numbers"></a>난수 테이블 만들기
1. **[단추](../controls/control-button.md)** 컨트롤을 추가하고 이 수식에 **[OnSelect](../controls/properties-core.md)** 속성을 설정합니다.

    **ClearCollect( RandomNumbers, ForAll( [ 1, 2, 3, 4, 5 ], Rand() ))**

    이 수식은 다섯 번 반복하는 데 사용되는 단일 열 테이블을 만들어서 다섯 개의 난수가 생성됩니다.

1. **[데이터 테이블](../controls/control-data-table.md)** 을 추가하고, 해당 **항목** 속성을 **RandomNumbers**로 설정하고, **값** 필드를 표시합니다.

    ![다른 다섯 개의 10진수 값(0.857, 0.105, 0.979, 0.167, 0.814)이 포함된 데이터 테이블을 보여주는 화면](media/function-rand/set-show-data.png)

1. Alt 키를 누른 채 클릭하거나 눌러 단추를 선택합니다.

    데이터 테이블은 다섯 가지 임의의 10진수를 표시합니다.

    ![다른 다섯 개의 10진수 값(0.857, 0.105, 0.979, 0.167, 0.814)이 포함된 데이터 테이블을 보여주는 화면](media/function-rand/rand-collection-1.png)

1. 다시 단추를 선택하여 다른 난수 목록을 표시합니다.

    ![다른 다섯 개의 10진수 값(0.414, 0.128, 0.860, 0.303, 0.568) 집합이 포함된 데이터 테이블을 보여주는 동일한 화면](media/function-rand/rand-collection-2.png)

테이블 대신 단일 난수를 생성하려면 **Set( RandomNumber, Rand() )** 를 사용합니다.
