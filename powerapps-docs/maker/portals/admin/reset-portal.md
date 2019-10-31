---
title: 포털 재설정 | MicrosoftDocs
description: 포털을 다시 설정하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="reset-a-portal"></a>포털 다시 설정

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

포털이 프로비저닝되면 조직을 다른 테넌트 또는 다른 데이터 센터로 이동하는 경우 또는 조직에서 포털을 제거하려는 경우와 같이 특정 상황에서 포털에서 리소스를 삭제해야 할 수 있습니다.

이렇게 하려면 포털을 다시 설정하여 연결된 모든 호스팅된 리소스를 삭제합니다. 그런 다음 포털을 다시 프로비저닝할 수 있습니다. 다시 설정 작업이 완료되면 포털 URL에 더 이상 액세스할 수 없습니다.

포털을 다시 설정해도 인스턴스에 있는 포털 구성이나 솔루션은 제거되지 않으며 그대로 유지됩니다.

완전히 구성된 포털 또는 인스턴스의 프로비저닝 또는 업데이트가 실패한 포털을 다시 설정할 수 있습니다.

구성된 포털을 다시 설정하려면:

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 작업** > **포털 다시 설정**으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![포털 다시 설정](../media/reset-portal.png "포털 다시 설정")

3.  확인 창에서 **다시 설정**을 선택합니다.

> [!NOTE]
> - 연결된 Azure Active Directory 응용 프로그램에 대한 적절한 권한이 없는 경우 오류가 표시됩니다. 적절한 권한에 대해서는 전역 관리자에게 문의해야 합니다.
> - 포털이 성공적으로 다시 설정되면 PowerApps 포털 관리 센터의 **애플리케이션** 탭에 있는 포털 이름과 상태는 변경되지 않습니다. 예를 들어 포털 이름 및 상태가 포털 1이고 각각 구성된 경우 포털을 다시 설정한 후 이러한 값은 변경되지 않습니다. 포털 이름을 변경하려면 포털 관리 센터의 **포털 세부 정보** 탭에서 변경할 수 있습니다. 그러나 상태 값은 구성되지 않음으로 되돌릴 수 없습니다.
> 
> **응용 프로그램** 탭의 포털 상태는 프로비저닝 상태를 나타내지 않으며 포털의 기능에 영향을 미치지 않는다는 점에 유의해야 합니다. 해당 포털에 대한 포털 관리 센터에 액세스한 적이 있는지 여부를 보여 줍니다.

포털이 올바르게 프로비저닝되지 않으면 오류 상태가 되고 다음 화면이 표시됩니다. 이 경우 오류 화면에서 **포털 다시 설정**을 선택하여 포털을 다시 설정할 수도 있습니다.

> [!div class=mx-imgBorder]
> ![포털을 프로비저닝하는 동안 오류](../media/provision-portal-error.png "포털을 프로비저닝하는 동안 오류")

## <a name="troubleshooting"></a>문제 해결

이 섹션에서는 포털을 다시 설정하는 동안 문제 해결에 대한 정보를 제공합니다.

### <a name="reset-request-could-not-be-submitted"></a>다시 설정 요청을 제출할 수 없음

포털 다시 설정 요청을 제출할 수 없는 경우 다음 이미지와 같이 오류가 표시됩니다. 이 경우에는 포털 관리 센터를 닫았다가 다시 열어야 하며 포털 다시 설정을 다시 시도하십시오. 문제가 지속되면 Microsoft 지원팀에 문의하십시오.

> [!div class=mx-imgBorder]
> ![포털을 다시 설정하는 동안 오류](../media/reset-portal-request-error.png "포털을 다시 설정하는 동안 오류")

### <a name="reset-portal-job-fails"></a>포털 다시 설정 작업 실패

포털 다시 설정 작업이 실패하는 경우 **포털 다시 설정** 작업과 함께 오류 메시지가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털을 다시 설정하는 동안 오류](../media/reset-portal-error.png "포털을 다시 설정하는 동안 오류")

일반적으로 이는 일시적인 오류이므로 **포털 다시 설정**을 선택하여 작업을 다시 시작해야 합니다. 문제가 지속되면 Microsoft 지원팀에 문의하십시오.

