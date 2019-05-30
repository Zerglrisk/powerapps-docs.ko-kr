---
title: 캔버스 앱에 대 한 보조 기술에서 내용을 표시 하거나 숨기려면 | Microsoft Docs
description: 보면서 사용자 에게만 또는 캔버스 앱에 대해서만 화면 읽기 프로그램 사용자만 콘텐츠를 표시 하는 방법
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550091"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>캔버스 앱에 대 한 보조 기술에서 내용을 표시 하거나 숨기려면

대부분의 경우에서 모든 사용자가 모든 콘텐츠에 액세스할 수 있어야 하지만 보면서 사용자 에게만 또는 화면 읽기 프로그램 사용자에만 콘텐츠를 표시 하려는 경우에 따라 합니다. 예를 들어 보면서 사용자에 게 확실 한 차트 추세의 설명에 액세스 하려면 화면 판독기만 사용자를 할 수 있습니다. 인접 한 레이블 설명 하는 경우 화면 읽기 프로그램 사용자의 아이콘을 숨길 수도 있습니다. 또 다른 설명은 아이콘 번거롭습니다 것입니다.

## <a name="hide-content-from-all-users"></a>모든 사용자의 내용 숨기기

* 설정할 **[Visible](controls/properties-core.md)** 를 false로 합니다.

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>보면서 사용자의 콘텐츠를 숨기 거 나 화면 읽기 프로그램 사용자에 게 표시

이러한 기술 중 하나를 사용 합니다.

* 설정할 **[크기](controls/properties-text.md)** 0입니다.
* 설정 **[너비](controls/properties-size-location.md)** 하 고 **[높이](controls/properties-size-location.md)** 1입니다.
* 설정  **[X](controls/properties-size-location.md)** 를  **[Y](controls/properties-size-location.md)** , 또는 두 속성 컨트롤 화면 외부 되도록 합니다.
* 설정할 **[색](controls/properties-color-border.md)** 및 관련 속성을 투명 하 게 합니다.
* 사각형 위치 **[셰이프](controls/control-shapes-icons.md)** 콘텐츠와 집합 위에 **[채우기](controls/properties-color-border.md)** 화면의 배경색으로 동일한 색입니다.

> [!NOTE]
> 사용자 수를 사용 하 여 키보드와 같은 대화형 컨트롤을 액세스는  **[단추](controls/control-button.md)** 위 목록의 기술 중 하나를 사용 하 여 숨기지 하는 경우에 합니다. 설정할 **[TabIndex](controls/properties-accessibility.md)** 사용자가 Tab 키를 눌러 컨트롤에 액세스 하지 못하도록 하려는 경우-1입니다.

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>화면 읽기 프로그램 사용자의 콘텐츠를 숨기고 보면서 사용자에 게 표시

* 에 대 한  **[이미지](controls/control-image.md)** 하십시오  **[아이콘](controls/control-shapes-icons.md)** , 및 **[셰이프](controls/control-shapes-icons.md)** 컨트롤 설정 **[AccessibleLabel](controls/properties-accessibility.md)** 빈 문자열 ""입니다.

## <a name="next-steps"></a>다음 단계

에 대 한 자세한 [접근성 속성](controls/properties-accessibility.md) 캔버스 앱의 컨트롤입니다.
