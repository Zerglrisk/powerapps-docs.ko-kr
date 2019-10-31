---
title: 포털에 대한 유지 보수 모드 사용 | MicrosoftDocs
description: 포털에서 유지 관리 모드를 활성화하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="maintenance-mode-for-a-portal"></a>포털에 대한 유지 관리 모드

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

웹 사이트가 예정된 유지 관리 중이거나 일시적인 중단으로 인해 중단된 경우가 있을 수 있습니다. 고객이 유지 관리 중에 웹 사이트에 액세스하는 경우 예측할 수 없는 동작과 간헐적 가용성을 경험할 수 있습니다. 

포털 관리자는 이제 유지 관리 작업이 진행 중일 때(예: 솔루션 패키지를 업그레이드하는 경우) 고객에게 적절한 메시지를 표시하도록 포털을 구성할 수 있습니다. 포털에서 유지 관리 모드를 활성화하여 이 기능을 활용할 수 있습니다. 유지 관리 모드를 활성화하면 메시지가 표시되고 고객은 `<portal URL>/_services/about` 페이지를 제외하고 모든 웹 페이지가 검색되지 않도록 제한됩니다.

> [!div class=mx-imgBorder]
> ![기본 유지 관리 모드 페이지](../media/default-maint-page.png "기본 유지 관리 모드 페이지")

## <a name="enable-maintenance-mode"></a>유지 관리 모드 사용

웹 사이트가 예약된 유지 관리 상태에 있을 때 예측할 수 없는 동작을 처리하는 대신 일관된 메시지를 제공하기 위해 포털에서 유지 관리 모드를 활성화할 수도 있습니다. 이렇게 하면 포털 사용자에게 더 나은 환경을 제공할 수 있습니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

3. **포털 작업** > **유지 관리 모드 활성화**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 활성화](../media/enable-maint-mode-button.png "유지 관리 모드 활성화")

4. **유지 관리 모드 활성화** 창에서 다음 값을 입력합니다.
    - **유지 관리 모드가 활성화된 경우 사용할 페이지 선택**: 다음 값 중 하나를 선택합니다.

        - **기본 페이지**: 유지 관리 모드를 활성화한 경우 기본 페이지를 표시하려면 이 값을 선택합니다. 이 옵션은 기본적으로 선택되어 있습니다.

        - **사용자 지정 페이지**: 유지 관리 모드를 활성화한 경우 사용자 지정 HTML 페이지를 표시하려면 이 값을 선택합니다.

    - **사용자 지정 페이지 URL**: 이 필드는 사용자 지정 HTML 페이지를 표시하는 옵션을 선택하는 경우에만 사용할 수 있습니다. 제공하는 페이지 URL에 공개적으로 액세스할 수 있는지 확인해야 합니다. 지정된 HTML 페이지에 연결할 수 없는 경우 기본 페이지가 관리자에게 메모와 함께 표시됩니다.

5. **사용**을 선택합니다. 유지 관리 모드를 활성화하는 동안 포털이 다시 시작되고 몇 분 동안 사용할 수 없습니다. 

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 설정 활성화](../media/enable-maint-mode.png "유지 관리 모드 설정 활성화")

## <a name="configure-or-disable-maintenance-mode"></a>유지 관리 모드 구성 또는 비활성화

포털에 대한 유지 관리 모드를 활성화한 후 유지 관리 모드 설정을 업데이트하고 다른 페이지를 선택할 수 있습니다.

또한 웹 사이트의 예약된 유지 관리가 완료되면 포털에서 유지 관리 모드를 비활성화하도록 선택할 수 있습니다. 이제 포털 사용자는 평소와 같이 모든 웹 페이지를 찾아보고 액세스할 수 있습니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **유지 관리 모드 구성 또는 비활성화**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 구성](../media/configure-maint-mode-button.png "유지 관리 모드 구성")

3. 필요에 따라 설정을 수정하고 **업데이트**를 선택합니다. 예를 들어 이전에 사용자 지정 페이지를 표시하도록 선택한 경우 기본 페이지를 표시하도록 선택할 수 있습니다.

4. 유지 관리 모드를 비활성화하려면 **사용 안 함**을 선택합니다. 유지 관리 모드를 업데이트하거나 비활성화하는 동안 포털이 다시 시작되고 몇 분 동안 사용할 수 없습니다.

    > [!div class=mx-imgBorder]
    > ![유지 관리 모드 설정 업데이트](../media/configure-maint-mode.png "유지 관리 모드 설정 업데이트")

