---
title: Select 함수 | Microsoft Docs
description: PowerApps에서 Select 함수에 대한 구문을 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/11/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed31bd165eb2289819800b6f2e01121c2681ae9e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984074"
---
# <a name="select-function-in-powerapps"></a>PowerApps의 Select 함수
컨트롤에 select 작업을 시뮬레이트하여 **OnSelect** 수식을 계산합니다.

## <a name="description"></a>설명
**Select** 함수는 사용자가 컨트롤을 클릭하거나 탭한 것처럼 컨트롤에 select 작업을 시뮬레이트합니다. 그 결과 대상 컨트롤에서 **OnSelect** 수식이 계산됩니다.

**Select**를 사용하여 select 작업을 부모 컨트롤에 전파합니다. 이 유형의 전파는 예를 들면 갤러리에서 기본 동작입니다. 기본적으로 **[갤러리](../controls/control-gallery.md)** 컨트롤에서 모든 컨트롤의 **OnSelect** 속성은 **Select( Parent )** 로 설정됩니다. 이런 식으로 갤러리 컨트롤 자체의 **OnSelect** 속성의 값을 설정할 수 있으며, 사용자가 갤러리에서 클릭하거나 탭하는 위치와 상관없이 수식이 계산됩니다.

갤러리에서 하나 이상의 컨트롤이 갤러리 자체의 작업과 다른 작업을 수행하도록 하려면 해당 컨트롤의 **OnSelect** 속성을 기본값이 아닌 다른 값으로 설정합니다. 갤러리 자체와 동일한 작업을 수행하도록 하려면 갤러리에 있는 대부분 컨트롤의 **OnSelect** 속성을 기본값으로 두면 됩니다.

**Select**는 이후 처리에 대해 대상 **OnSelect**를 큐에 넣으며, 이는 현재 수식 계산이 완료된 후 발생할 수 있습니다. **Select**는 대상 **OnSelect**가 즉시 계산되도록 하지 않으며 **Select**는 **OnSelect**가 계산이 완료될 때까지 기다리지도 않습니다.

**Select**는 갤러리나 폼 같은 컨테이너 컨트롤의 경계를 넘을 수 없습니다. 컨테이너 컨트롤 내의 컨트롤은 동일한 컨테이너 컨트롤 내에 있는 수식에서만 **Select** 함수의 주체가 될 수 있습니다. 화면 간에 **Select**를 사용할 수 없습니다.

**OnSelect** 속성이 있는 컨트롤에만 **Select**를 사용할 수 있습니다.

**Select**를 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

컨트롤은 다른 컨트롤을 통해 직접 또는 간접적으로 자체를 **Select**할 수 없습니다.

## <a name="syntax"></a>구문
**Select**( *Control* )

* *Control* – 필수 항목입니다.  사용자를 대신하여 선택하는 컨트롤입니다.

## <a name="examples"></a>예

#### <a name="basic-usage"></a>기본 사용법

1. **[단추](../controls/control-button.md)** 컨트롤을 추가하고, 다른 이름이 있는 경우 이름을 **Button1**로 지정합니다.

1. **Button1**의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    **Notify( "Hello World" )**

1. 동일한 화면에서 두 번째 **단추** 컨트롤을 추가하고, **OnSelect** 속성을 다음 수식으로 설정합니다.

    **Select( Button1 )**

1. Alt 키를 누른 상태에서 두 번째 단추를 선택합니다.

    앱의 맨 위에 알림이 나타납니다. **Button1**의 **OnSelect** 속성이 이 알림을 생성했습니다.

    ![두 단추를 클릭했을 때 알림과 두 단추에 대한 OnSelect 속성 설정을 보여 주는 애니메이션입니다.](media/function-select/basic-select.gif)

#### <a name="gallery-control"></a>갤러리 컨트롤

1. 다른 컨트롤을 포함하는 세로 **[갤러리](../controls/control-gallery.md)** 컨트롤입니다.

    ![컨트롤을 포함하는 세로 갤러리를 선택합니다.](media/function-select/select-gallery.png)

2. 갤러리의 **OnSelect** 속성을 다음 수식으로 설정합니다.
 
    **Notify( "갤러리 선택됨" )**

3. Alt 키를 누른 상태에서 갤러리의 배경 또는 갤러리의 컨트롤을 클릭하거나 탭합니다.

    모든 작업이 앱의 맨 위에 **갤러리 선택됨** 알림을 표시합니다.

    갤러리의 **OnSelect** 속성을 사용하여 사용자가 갤러리에서 항목을 클릭하거나 탭할 때 수행할 기본 동작을 지정합니다.

5. 이미지 컨트롤의 **OnSelect** 속성을 다음 수식으로 설정합니다.

    **Notify( "이미지 선택됨", Success )**

6. Alt 키를 누른 상태에서 갤러리의 다양한 요소를 클릭하거나 탭합니다.

    이미지를 제외하고 갤러리에서 컨트롤을 클릭하거나 탭하면 이전처럼 **갤러리 선택됨**이 표시됩니다. 이미지를 클릭하거나 탭하면 **이미지 선택됨**이 표시됩니다.
 
    갤러리의 각 컨트롤을 사용하여 갤러리의 기본 동작과 다른 동작을 수행합니다.

    ![갤러리 컨트롤의 OnSelect 속성의 기본값과 다른 작업을 수행하는 컨트롤을 보여 주는 애니메이션입니다.](media/function-select/gallery-select.gif)
