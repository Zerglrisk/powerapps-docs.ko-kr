---
title: PowerApps에서 포털 만들기 | Microsoft Docs
description: PowerApps에서 포털을 만드는 방법에 대해 설명 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b818db8fb72fe36fcc7ea049a4e5b4cfb17eb0d9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542645"
---
# <a name="create-a-common-data-service-starter-portal"></a>Common Data Service 스타터 포털 만들기

PowerApps에서 포털을 빌드하는 기능을 사용 하 여 외부 및 내부 사용자를 위한 웹 사이트를 만들어 Common Data Service에 저장 된 데이터와 상호 작용할 수 있습니다.

포털을 만들 때 다음과 같은 이점이 있습니다.

- 데이터는 Common Data Service에 저장 되므로 SharePoint와 같은 데이터 원본, Dynamics 365의 모델 기반 앱 또는 Salesforce와 마찬가지로 PowerApps에서 연결을 만들 필요가 없습니다. 포털에서 표시 하거나 관리 하려는 엔터티만 지정 해야 합니다.

- 웹 페이지에서 구성 요소를 추가 하 고 구성 하 여 WYSIWYG PowerApps 포털 스튜디오를 통해 포털을 디자인할 수 있습니다.

새 환경이 나 기존 환경에서 포털을 만들 수 있습니다.

새 환경 **만들기** 링크를 사용 하 여 새 환경에서 포털을 만들도록 선택 하는 경우 환경을 만들 때 엔터티, 데이터 및 시작 포털 템플릿과 같은 필수 포털 필수 구성 요소가 설치 됩니다. 이 방법에서는 포털이 몇 분 안에 프로 비전 됩니다.

포털 필수 구성 요소가 없는 기존 환경에서 포털을 만들도록 선택 하는 경우 필수 구성 요소가 먼저 설치 된 후 포털이 생성 됩니다. 이 방법에서는 포털 프로 비전에 시간이 걸릴 수 있으며 포털이 프로 비전 되 면 알림이 표시 됩니다.

PowerApps에서 선택한 환경에 따라 Dynamics 365에서 모델 기반 앱을 포함 하는 환경에서 Common Data Service 스타터 포털 또는 포털을 만들 수 있습니다.

환경 사용에 대 한 자세한 내용: [환경 및 Microsoft PowerApps 작업](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

사용 가능한 포털 템플릿에 대 한 자세한 내용: [포털 템플릿](portal-templates.md)

포털을 만들려면 다음을 수행 합니다.

1.  [PowerApps](https://make.powerapps.com)에 로그인합니다.  

2.  **자신의 앱 만들기**에서 **포털**을 선택 합니다.

3.  선택한 환경에 포털 필수 구성 요소가 포함 되어 있지 않으면 다른 환경을 선택 하거나 새 환경을 만드는 것을 제안 하는 **빈 창에서 포털** 에 메시지가 표시 됩니다.

    > [!div class=mx-imgBorder]
    > ![새 환경 메시지 만들기](media/create-portal-message.png "새 환경 메시지 만들기")

4.  현재 환경을 진행 하도록 선택 하는 경우 다음 단계에 설명 된 대로 창에 필요한 정보를 입력 합니다. 새 환경을 만들도록 선택 하는 경우 [새 환경 만들기](#create-new-environment)를 참조 하세요.

5.  Portal의 **빈** 창에서 웹 사이트에 대 한 포털의 이름과 주소를 입력 하 고 드롭다운 목록에서 언어를 선택 합니다. 완료 되 면 **만들기**를 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![새 포털 만들기](media/create-new-portal.png "새 포털 만들기")  

**만들기**를 선택 하면 포털에서 프로 비전을 시작 하 고 [알림을](#portal-provisioning-notifications)통해 프로 비전 상태가 표시 됩니다.

포털 필수 구성 요소가 설치 되지 않은 환경에서 포털을 만든 경우 프로 비전 상태도 표에 표시 됩니다.

> [!div class=mx-imgBorder]
> ![그리드 알림](media/provision-progress-notif.png "그리드 알림")

포털이 성공적으로 프로 비전 되 면 상태가 업데이트 되 고 그리드에 포털이 표시 됩니다.

> [!div class=mx-imgBorder]
> ![프로 비전 된 포털](media/recent-apps.png "프로 비전 된 포털")

PowerApps 포털 스튜디오에서 포털을 편집 하려면 [포털 편집](manage-existing-portals.md#edit)을 참조 하세요.

> [!NOTE]
> - 테 넌 트에서 최대 5 개의 포털을 만들 수 있습니다. 그러나 환경에서 만든 각 유형의 포털은 하나만 있을 수 있습니다.
> - 포털을 프로 비전 할 수 있는 권한이 없는 경우 오류가 표시 됩니다. 포털을 만들려면 Common Data Service의 시스템 관리자 역할이 있어야 합니다. 또한 사용자 레코드에서 **CAL (클라이언트 액세스 라이선스) 정보** 를 사용 하 여 **읽기/쓰기로** 설정 된 **액세스 모드** 를 사용 해야 합니다.
> - 이전 포털 추가 기능을 구매한 경우 추가 기능을 사용 하 여 포털을 프로 비전 하려면 **Dynamics 365 관리 센터** 페이지로 이동 해야 합니다. 추가 정보: [이전 포털 추가 기능을 사용 하 여 포털 프로 비전](provision-portal-add-on.md)
> - 이전 포털 추가 기능을 사용 하 여 포털을 프로 비전 한 경우에도 [make.powerapps.com](https://make.powerapps.com)에서 사용자 지정 하 고 관리할 수 있습니다.
> - [Make.powerapps.com](https://make.powerapps.com) 에서 포털을 프로 비전 하면 이전 포털 추가 기능이 사용 되지 않습니다. 또한 이러한 포털은 **Dynamics 365 관리 센터** 페이지의 **응용 프로그램** 탭에 나열 되지 않습니다.
> - **Dynamics 365 관리 센터** 페이지에서 Common Data Service 스타터 포털을 만들 수 없습니다.
> - PowerApps 포털은 프랑스 지역에서 사용할 수 없습니다.

## <a name="create-new-environment"></a>새 환경 만들기

**빈 창에서 포털** 에 제공 된 옵션을 사용 하 여 환경을 만들 때 다음 단계를 수행 합니다.

1.  **새 환경** 창에서 환경의 이름을 입력 한 다음 드롭다운 목록에서 지역 및 환경 유형을 선택 합니다. 환경을 만든 후에는 지역을 변경할 수 없습니다. 완료 되 면 **환경 만들기**를 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![새 환경 만들기](media/create-new-environment.png "새 환경 만들기")  

2.  환경을 만들면 대화 상자에 확인 메시지가 표시 되 고 데이터베이스를 만들라는 메시지가 표시 됩니다. **데이터베이스 만들기** 를 선택 하 여 Common Data Service에 대 한 액세스를 사용 하도록 설정 합니다.

    > [!NOTE]
    > 데이터베이스를 만드는 메시지가 자동으로 표시 되지 않을 수 있습니다. 이 경우 새 환경으로 이동 하 여 **빈 타일에서 포털** 을 다시 선택 해야 합니다.

    > [!div class=mx-imgBorder]
    > ![새 환경을 만들었습니다.](media/new-environment-created.png "새 환경을 만들었습니다.")  

3.  데이터베이스에 저장된 데이터의 통화 및 언어를 선택합니다. 데이터베이스를 만든 후에는 통화 또는 언어를 변경할 수 없습니다. 완료 되 면 **내 데이터베이스 만들기**를 선택 합니다. 포털이 프로 비전 되 면 샘플 콘텐츠를 신속 하 게 시작할 수 있도록 시작 포털을 사용 하 여 데이터베이스가 만들어집니다.

    > [!NOTE]
    > **시작 포털 포함** 옵션은 **빈 창에서 포털** 에 제공 된 옵션을 사용 하 여 환경을 만드는 경우에만 사용할 수 있습니다. PowerApps 관리 센터에서 환경을 만드는 경우에는이 옵션을 사용할 수 없습니다.

    > [!div class=mx-imgBorder]
    > ![새 데이터베이스 만들기](media/create-new-database.png "새 데이터베이스 만들기") 

    Common Data Service에서 데이터베이스를 만드는 데 몇 분 정도 걸릴 수 있습니다. 데이터베이스가 만들어지면 PowerApps 홈 페이지의 환경 목록에서 새 환경이 선택 되 고 포털 관리 앱이 만들어집니다. 이 앱은 실제 포털이 아니라 고급 구성 작업을 수행할 수 있는 모델 기반 도우미 앱입니다. 이제 외부 연결 웹 사이트를 디자인 하기 위한 포털 만들기를 진행할 수 있습니다.

    > [!div class=mx-imgBorder]
    > ![포털 관리 앱](media/portal-mgmt-app.png "포털 관리 앱")

4. 환경 및 데이터베이스를 만든 후 **고유한 앱 만들기**에서 **포털**을 선택 합니다. 

    > [!NOTE]
    > 데이터베이스가 생성 되 고 데이터베이스 만들기 프롬프트가 계속 표시 되는 경우 **빈 타일에서 포털** 을 선택 하기 전에 PowerApps 홈 페이지를 새로 고쳐야 합니다.


## <a name="portal-provisioning-notifications"></a>포털 프로 비전 알림

**만들기**를 선택 하면 포털에서 프로 비전을 시작 하 고 알림을 통해 프로 비전 상태가 표시 됩니다.

**알림으로 알림**

**만들기** 를 선택 하 여 포털을 프로 비전 하면 다음과 같은 알림이 표시 됩니다.

> [!div class=mx-imgBorder]
> ![알림 메시지](media/toast-notif.png "알림 메시지") 

**알림 창의 알림**

프로 비전 요청이 성공적으로 배치 되 면 **알림** 창에 다음과 같은 알림이 표시 됩니다.

프로 비전 진행 중에 표시 된 알림

> [!div class=mx-imgBorder]
> ![창 알림](media/pane-notif.png "창 알림") 

프로 비전에 대해 표시 된 알림이 성공적으로 완료 됨

> [!div class=mx-imgBorder]
> ![프로 비전 성공 알림](media/provision-complete-notif.png "프로 비전 성공 알림") 

포털 프로 비전에 실패 하는 경우 알림도 비슷하게 표시 됩니다.
  
**전자 메일을 통한 알림**

프로 비전 요청이 성공적으로 배치 되 면 포털을 만드는 사용자에 게 확인 전자 메일 알림이 전송 됩니다. 또한 포털 프로 비전이 완료 된 후 사용자에 게 전자 메일이 전송 됩니다.

## <a name="disable-portal-creation-in-a-tenant"></a>테 넌 트에서 포털 만들기를 사용 하지 않도록 설정

전역 관리자는 관리자가 아닌 사용자가 테 넌 트에서 포털 만들기를 사용 하지 않도록 설정 하려는 경우 PowerShell을 통해 테 넌 트 수준 설정 `disablePortalsCreationByNonAdminUsers` 사용 하도록 설정 하 여 수행할 수 있습니다. PowerShell cmdlet을 실행 하려면 먼저 필요한 모듈을 설치 해야 합니다. 필요한 PowerShell 모듈을 설치 하는 방법에 대 한 자세한 내용은 [설치](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation)를 참조 하세요.

모듈을 설치한 후 PowerShell 창에서 다음 명령을 실행 합니다 (관리자 권한으로 PowerShell 실행).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

관리자는 다음 Azure 역할 중 하나가 있는 사용자입니다.

- 전역 관리자
- Dynamics 365 서비스 관리자
- 전원 플랫폼 서비스 관리자

위에서 언급 한 Azure 역할이 없는 사용자는 관리자가 아닌 사용자로 간주 됩니다.

테 넌 트에서 포털 만들기를 사용 하지 않도록 설정 하면 관리자가 아닌 경우 다음과 같이 오류가 표시 됩니다.

> [!div class=mx-imgBorder]
> ![포털 만들기 차단 오류](media/portal-create-blocked-error.png "포털 만들기 차단 오류")
