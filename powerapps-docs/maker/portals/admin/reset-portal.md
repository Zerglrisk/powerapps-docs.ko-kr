---
title: 포털 다시 설정 | MicrosoftDocs
description: 포털을 다시 설정 하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7b5bbc05ca7adf7fad9725215f8a7d6c06c035bb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975728"
---
# <a name="reset-a-portal"></a>포털 다시 설정

포털이 프로 비전 되 면 조직에서 다른 테 넌 트 또는 다른 데이터 센터로 이동 하거나 조직에서 포털을 제거 하려는 경우와 같이 특정 상황에서 포털에서 리소스를 삭제 해야 할 수 있습니다.

이렇게 하려면 포털을 다시 설정 하면 연결 된 모든 호스트 된 리소스가 삭제 됩니다. 그런 다음 포털을 다시 프로 비전 할 수 있습니다. 다시 설정 작업이 완료 되 면 포털 URL에 더 이상 액세스할 수 없게 됩니다.

포털을 다시 설정 해도 사용자의 인스턴스에 있는 포털 구성 또는 솔루션은 제거 되지 않고 그대로 유지 됩니다.

완전히 구성 된 포털 또는 인스턴스를 프로 비전 또는 업데이트 하지 못한 포털을 다시 설정할 수 있습니다.

구성 된 포털을 다시 설정 하려면:

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  포털 **작업** > **포털 다시 설정**으로 이동 합니다.

    > [!div class=mx-imgBorder]
    > 포털 ![재설정]포털 다시(../media/reset-portal.png "설정")

3.  확인 창에서 **다시 설정** 을 선택 합니다.

> [!NOTE]
> - 연결 된 Azure Active Directory 응용 프로그램에 대 한 적절 한 권한이 없는 경우 오류가 표시 됩니다. 해당 권한을 전역 관리자에 게 문의 해야 합니다.
> - 이전 포털 추가 기능을 사용 하 여 포털을 프로 비전 한 경우 포털이 성공적으로 다시 설정 되 면 Dynamics 365 관리 센터의 **응용 프로그램** 탭에서 포털 이름 및 해당 상태가 변경 되지 않습니다. 예를 들어 포털 이름과 상태가 포털 1이 고 각각 구성 된 경우 포털을 다시 설정한 후에는 이러한 값이 변경 되지 않습니다. 포털 이름을 변경 하려는 경우 PowerApps 포털 관리 센터의 **포털 세부 정보** 탭에서 변경할 수 있습니다. 그러나 상태 값을 구성 되지 않음으로 되돌릴 수는 없습니다.
> - **응용 프로그램** 탭에서 포털의 상태가 프로 비전 상태를 나타내지 않으며 포털의 기능에 영향을 주지 않는다는 점에 유의 해야 합니다. 해당 포털에 대해 PowerApps 포털 관리 센터에 액세스 한 적이 있는지 여부를 표시 합니다.

포털이 올바르게 프로 비전 되지 않은 경우에는 오류 상태로 전환 되 고 다음 화면이 표시 됩니다. 이 경우 오류 화면에서 **포털 다시 설정** 을 선택 하 여 포털을 다시 설정할 수도 있습니다.

> [!div class=mx-imgBorder]
> (../media/provision-portal-error.png "포털을 프로 비전 하는 동안 포털 오류") ![를 프로 비전 하는 동안 오류 발생]

## <a name="troubleshooting"></a>문제 해결

이 섹션에서는 포털을 다시 설정 하는 동안 문제 해결에 대 한 정보를 제공 합니다.

### <a name="reset-request-could-not-be-submitted"></a>재설정 요청을 제출할 수 없습니다.

포털 재설정 요청을 제출할 수 없는 경우 다음 이미지와 같이 오류가 표시 됩니다. 이 경우 PowerApps 포털 관리 센터를 닫았다가 다시 연 후 포털을 다시 설정 해 봅니다. 문제가 계속 되 면 Microsoft 지원에 문의 하세요.

> [!div class=mx-imgBorder]
> (../media/reset-portal-request-error.png "포털을 다시 설정 하는 동안 포털 오류") ![를 다시 설정 하는 동안 오류 발생]

### <a name="reset-portal-job-fails"></a>포털 다시 설정 작업이 실패 합니다.

포털 다시 설정 작업이 실패 하면 **포털 다시 설정** 작업과 함께 오류 메시지가 표시 됩니다.

> [!div class=mx-imgBorder]
> (../media/reset-portal-error.png "포털을 다시 설정 하는 동안 포털 오류") ![를 다시 설정 하는 동안 오류 발생]

일반적으로 일시적인 오류 이며 작업을 다시 시작 하려면 **포털 다시 설정** 을 선택 해야 합니다. 문제가 계속 되 면 Microsoft 지원에 문의 하세요.

