---
title: 캔버스 앱의 화면 크기 및 방향 변경 | Microsoft Docs
description: Power Apps에서 캔버스 앱의 화면 크기 및 방향과 같은 설정을 변경 하는 방법에 대 한 단계별 지침
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6ec2006266a15b7552d1a83b2d7d67c14560470
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732975"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-power-apps"></a>Power Apps에서 캔버스 앱의 화면 크기 및 방향 변경
화면 크기와 방향을 변경하여 캔버스 앱을 사용자 지정합니다.

## <a name="prerequisites"></a>필수 조건

앱을 만들거나 편집용 앱을 연 다음 **파일** 메뉴에서 **앱 설정** 을 선택 합니다.

## <a name="change-screen-size-and-orientation"></a>화면 크기 및 방향 변경
1. **앱 설정** 아래에서 **화면 크기 + 방향**을 선택합니다.

    ![앱의 화면 크기 및 방향을 변경하는 옵션](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. **방향** 목록에서 **세로** 또는 **가로**를 선택 합니다.

1. (태블릿 앱에만 해당) **가로 세로 비율**에서 다음 단계 중 하나를 수행 합니다.

    - 이 앱의 대상 장치와 일치 하는 비율을 선택 합니다.
    - **사용자 지정** 을 선택 하 여 고유한 크기를 설정한 다음 50-3840 사이의 너비와 50-2160 사이의 높이를 지정 합니다.

    ![태블릿 앱의 가로 세로 비율 변경](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. **크기 조정**아래에서 **설정** 또는 **해제**를 지정 합니다.

    이 설정은 앱 화면 크기를 장치의 사용 가능한 공간에 맞게 조정 하기 위해 기본적으로 설정 되어 있습니다. 이 설정이 켜져 있으면 앱의 **width** 속성이 **designwidth**와 일치 하 고 앱의 **높이가** **designwidth**와 일치 합니다.

    이 설정을 해제 하면 앱이 실행 되는 장치의 가로 세로 비율로 조정 되 고 사용 가능한 모든 공간이 사용 됩니다. 앱이 확장 되지 않고 화면에 추가 정보가 표시 될 수 있습니다.

    이 설정을 끄면 **잠금 가로 세로 비율이** 자동으로 해제 되 고 사용 하지 않도록 설정 됩니다. 또한 모든 화면의 **Width** 속성은 `Max(App.Width, App.DesignWidth)`로 설정 되 고 해당 **Height** 속성은 `Max(App.Height, App.DesignHeight)`으로 설정 되므로 앱이 실행 되는 창의 차원을 추적할 수 있습니다. 이러한 변경을 통해 다양 한 장치 및 창 차원에 응답 하는 앱을 만들 수 있습니다. 추가 정보: [반응 형 레이아웃 만들기](create-responsive-layout.md)

1. **가로 세로 비율 고정** 아래에서 **고정** 또는 **해제**를 지정합니다.

    이 설정이 켜져 있으면 앱은 장치에 관계 없이 2 단계와 3 단계에서 지정한 화면 방향 및 가로 세로 비율을 유지 합니다. 예를 들어 웹 브라우저에서 실행 되는 전화 앱은 휴대폰의 비율을 유지 하 여 창을 채우지 않고 양쪽에 진한 막대를 표시 합니다.

    이 설정이 해제 되어 있으면 앱이 실행 중인 장치의 가로 세로 비율로 조정 되며 필요한 경우 UI를 왜곡 합니다.

1. **방향 고정** 아래에서 **고정** 또는 **해제**를 지정합니다.

    앱의 방향을 잠그면 앱은 지정한 방향을 유지 합니다. 응용 프로그램이 다른 방향의 화면에 있는 장치에서 실행 되는 경우 앱이 잘못 표시 되 고 원치 않는 결과가 표시 될 수 있습니다. 앱의 방향을 잠금 해제 하면 해당 앱이 실행 되는 장치의 화면 방향으로 조정 됩니다.

    **고급 설정**에서 **앱 포함 사용자 환경 사용** 을 사용 하도록 설정 하 여 앱의 방향을 수정할 수도 있습니다. 이 기능은 앱이 포함 될 때 앱에 맞추고 호스팅 캔버스의 배경색을 흰색으로 변경 합니다.

1. **적용**을 선택하여 변경 내용을 저장합니다.

## <a name="next-step"></a>다음 단계
**파일** 메뉴에서 **저장**을 선택하여 새롭게 설정된 앱을 다시 게시합니다.