---
title: 포털에 대 한 유지 관리 모드 사용 | MicrosoftDocs
description: 포털에서 유지 관리 모드를 사용 하도록 설정 하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e53380c39257645e9056a271226b6f7ef8c8c721
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976073"
---
# <a name="maintenance-mode-for-a-portal"></a>포털에 대 한 유지 관리 모드

웹 사이트가 예약 된 유지 관리를 받고 있거나 일시적인 중단으로 인해 중단 된 경우가 있습니다. 유지 관리 중에 고객이 웹 사이트에 액세스 하는 경우 예측할 수 없는 동작 및 일시적으로 사용할 수 없습니다. 

포털 관리자는 유지 관리 작업이 진행 될 때마다 고객에 게 적절 한 메시지를 표시 하도록 포털을 구성할 수 있습니다 (예: "솔루션 패키지를 업그레이드 하는 중"). 포털에서 유지 관리 모드를 사용 하도록 설정 하 여이 기능을 활용할 수 있습니다. 유지 관리 모드를 사용 하도록 설정 하면 메시지가 표시 되 고 고객은 `<portal URL>/_services/about` 페이지를 제외한 모든 웹 페이지를 검색할 수 없습니다.

> [!div class=mx-imgBorder]
> ![기본 유지 관리 모드 페이지](../media/default-maint-page.png "기본 유지 관리 모드 페이지")

## <a name="enable-maintenance-mode"></a>유지 관리 모드 사용

웹 사이트가 예약 된 유지 관리를 사용 하는 경우 예측할 수 없는 동작을 처리 하는 대신 포털에서 유지 관리 모드를 사용 하 여 일관 된 메시지를 제공할 수 있습니다. 이렇게 하면 포털 사용자에 게 더 나은 환경을 제공 합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

3. **포털 작업** > **유지 관리 모드 사용**으로 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드]사용(../media/enable-maint-mode-button.png "유지 관리 모드 사용")

4. **유지 관리 모드 사용** 창에서 다음 값을 입력 합니다.
    - **유지 관리 모드를 사용 하는 경우 사용할 페이지 선택**: 다음 값 중 하나를 선택 합니다.

        - **기본 페이지**: 유지 관리 모드를 사용 하는 경우 기본 페이지를 표시 하려면이 값을 선택 합니다. 이 옵션은 기본적으로 선택 되어 있습니다.

        - **사용자 지정 페이지**: 유지 관리 모드를 사용 하는 경우 사용자 지정 HTML 페이지를 표시 하려면이 값을 선택 합니다.

    - **사용자 지정 페이지 URL**:이 필드는 사용자 지정 HTML 페이지를 표시 하는 옵션을 선택 하는 경우에만 사용할 수 있습니다. 사용자가 제공 하는 페이지 URL은 공개적으로 액세스할 수 있는지 확인 해야 합니다. 지정 된 HTML 페이지에 연결할 수 없는 경우 기본 페이지는 관리자에 게 메모를 표시 합니다.

5. **사용**을 선택 합니다. 유지 관리 모드를 사용 하도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없습니다. 

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 설정을 사용]하 여(../media/enable-maint-mode.png "유지 관리 모드 설정 사용")

## <a name="configure-or-disable-maintenance-mode"></a>유지 관리 모드 구성 또는 사용 안 함

포털에 대해 유지 관리 모드를 사용 하도록 설정한 후에는 유지 관리 모드 설정을 업데이트 하 고 다른 페이지를 선택할 수 있습니다.

웹 사이트의 예약 된 유지 관리가 완료 되 면 포털에서 유지 관리 모드를 사용 하지 않도록 선택할 수도 있습니다. 이제 포털 사용자는 평소와 같이 모든 웹 페이지를 찾아보고 액세스할 수 있습니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. [ **유지 관리 모드]를 구성 하거나 사용 하지 않도록 설정** > **포털 작업** 으로 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드]구성(../media/configure-maint-mode-button.png "유지 관리 모드 구성")

3. 필요에 따라 설정을 수정 하 고 **업데이트**를 선택 합니다. 예를 들어 이전에 사용자 지정 페이지를 표시 하도록 선택한 경우 기본 페이지를 표시 하도록 선택할 수 있습니다.

4. 유지 관리 모드를 해제 하려면 **사용 안 함**을 선택 합니다. 유지 관리 모드를 업데이트 하거나 사용 하지 않도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없습니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 설정 업데이트](../media/configure-maint-mode.png "유지 관리 모드 설정 업데이트")

