---
title: 캔버스 앱의 화면 크기 및 방향 변경 | Microsoft Docs
description: PowerApps에서 캔버스 앱의 화면 크기 및 방향과 같은 설정을 변경하는 단계별 지침
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c4d9f648a4519ef30887d8d0739d7dc3d940555b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536043"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-powerapps"></a>PowerApps에서 캔버스 앱의 화면 크기 및 방향 변경
화면 크기와 방향을 변경하여 캔버스 앱을 사용자 지정합니다.

## <a name="prerequisites"></a>필수 조건

앱을 생성하거나 또는 편집을 위해 앱을 연 후, **파일** 메뉴에서 **앱 설정**을 선택합니다.

## <a name="change-screen-size-and-orientation"></a>화면 크기 및 방향 변경
1. **앱 설정** 아래에서 **화면 크기 + 방향**을 선택합니다.

    ![앱의 화면 크기 및 방향을 변경하는 옵션](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. **방향** 목록에서 **세로** 또는 **가로**를 선택합니다.

1. (태블릿 앱에만 해당) **가로 세로 비율** 아래에서, 다음 단계 중 하나를 수행합니다.

    - 이 앱의 대상 장치와 일치하는 비율을 선택합니다.
    - 사용자 고유의 크기를 설정하려면 **사용자 지정**을 선택하고 50-3840 사이의 넓이와 50-2160 사이의 높이를 지정합니다.

    ![태블릿 앱의 가로 세로 비율 변경](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. **영역 안에 맞추기** 아래에서 **설정** 또는 **해제**를 지정합니다.

    이 설정은 기본적으로 켜져 있어 앱 화면이 장치에서 사용 가능한 공간에 맞게 조정되도록 합니다. 앱에서 이 설정이 되어 있는 경우 **Width** 속성은 **DesignWidth**와 일치하며, **Height** 속성은 **DesignHeight**와 일치합니다.

    이 설정을 해제하면 앱은 실행되는 장치의 가로 세로 비율에 맞게 조정되고 모든 사용 가능한 공간을 차지합니다. 앱이 조정되지 않아 결과적으로, 화면은 자세한 정보를 표시할 수 있습니다.

    이 설정이 해제된 경우 **가로 세로 비율 고정**은 자동으로 해제되어 사용하지 않도록 설정됩니다 또한 모든 화면의 **Width** 속성은 `Max(App.Width, App.DesignWidth)`로 설정되며 **Height** 속성은 `Max(App.Height, App.DesignHeight)`로 설정되어 앱이 실행되는 창의 크기를 추적합니다. 이 변경으로 다양한 장치 및 창 크기에 응답하는 앱을 만들 수 있습니다. 자세한 정보는 [반응형 레이아웃 만들기](create-responsive-layout.md)를 참조합니다.

1. **가로 세로 비율 고정** 아래에서 **설정** 또는 **해제**를 지정합니다.

    이 설정이 켜져 있으면 장치에 관계 없이 2-3 단계에 지정된 가로 세로 비율과 앱 화면 방향이 유지됩니다. 예를 들어, 웹 브라우저에서 실행 중인 휴대폰 앱은 창을 채우는 대신 각 면에 어두운 색 막대를 보여주며 휴대폰의 비율을 유지합니다.

    이 설정이 off인 경우 앱은 실행하는 장치의 가로 세로 비율을 조정(필요한 경우 UI를 왜곡)합니다.

1. **방향 고정** 아래에서 **설정** 또는 **해제**를 지정합니다.

    앱의 방향을 잠그는 경우 앱은 지정된 방향을 유지합니다. 앱이 다른 방향의 화면의 장치에서 실행 중인 경우 앱이 잘못 표시되고 원치 않는 결과가 나타날 수 있습니다. 앱의 방향을 해제하면, 실행되는 장치의 화면 방향으로 조정됩니다.

    **고급 설정**에서 **사용자 환경을 포함하는 앱을 사용하도록 설정**를 사용하여 앱의 방향을 수정할 수도 있습니다. 이 기능은 호스팅 캔버스의 배경색을 흰색으로 변경하고 앱이 포함되는 경우 왼쪽 위로 앱을 맞춥니다.

1. **적용**을 선택하여 변경 내용을 저장합니다.

## <a name="next-step"></a>다음 단계
**파일** 메뉴에서 **저장**을 선택하여 새롭게 설정된 앱을 다시 게시합니다.