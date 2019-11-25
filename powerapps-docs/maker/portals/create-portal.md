---
title: PowerApps에서 포털 만들기 | MicrosoftDocs
description: PowerApps에서 포털을 만드는 방법에 관한 지침입니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756341"
---
# <a name="create-a-common-data-service-starter-portal"></a>Common Data Service 시작 포털 만들기

PowerApps에서 포털을 구축할 수 있는 기능으로 외부 및 내부 사용자를 위한 웹 사이트를 만들어 Common Data Service에 저장된 데이터와 상호 작용할 수 있습니다.

포털을 만들면 다음과 같은 이점이 있습니다.

- 데이터가 Common Data Service에 저장되어 있기 때문에 SharePoint, Dynamics 365의 모델 기반 앱 또는 Salesforce와 같은 데이터와 같이 PowerApps에서 연결을 만들 필요가 없습니다. 포털에서 표시하거나 관리하려는 엔터티만 지정하면 됩니다.

- 웹 페이지에서 구성 요소를 추가하고 구성하여 WYSIWYG PowerApps 포털 스튜디오를 통해 포털을 설계할 수 있습니다.

새 환경이나 기존 환경에서 포털을 작성할 수 있습니다.

**새로운 환경 만들기** 링크를 사용하여 새 환경에서 포털을 작성하도록 선택한 경우, 엔터티, 데이터 및 시작 포털 템플릿과 같은 필수 포털 전제 조건은 환경이 작성될 때 설치됩니다. 이 방법에서는 몇 분 안에 포털이 프로비저닝됩니다.

포털 사전 구성 요소 없이 기존 환경에서 포털을 작성하도록 선택한 경우, 사전 구성 요소가 먼저 설치되고 포털이 작성됩니다. 이 방법에서는 포털 프로비저닝에 시간이 걸릴 수 있으며 포털을 프로비저닝할 때 알림을 받습니다.

PowerApps에서 선택한 환경을 기반으로 Common Data Service 시작 포털 또는 Dynamics 365의 모델 기반 앱이 포함된 환경의 포털을 만들 수 있습니다.

환경 작업에 대한 자세한 내용은 [환경 및 Microsoft PowerApps에서 작업](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)을 참조하십시오.

사용 가능한 포털 템플릿에 대한 추가 정보: [포털 템플릿](portal-templates.md)

포털을 만들려면:

1.  [PowerApps](https://make.powerapps.com)에 로그인합니다.  

2.  **나만의 앱 만들기** 아래에서 **공백에서 포털**을 선택합니다.

3.  선택한 환경에 포털 사전 구성 요소가 없으면 **공백에서 포털** 창에 다른 환경을 선택하거나 새 환경을 생성하도록 제안하는 메시지가 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![새 환경 만들기 메시지](media/create-portal-message.png "새 환경 만들기 메시지")

4.  현재 환경으로 진행하기로 선택한 경우 다음 단계에서 언급된 대로 창에 필요한 정보를 입력하십시오. 새로운 환경을 만들려면 [새로운 환경 만들기](#create-new-environment)를 참조하십시오.

5.  **공백에서 포털** 창에 포털 이름과 웹 사이트 주소를 입력하고 드롭다운 목록에서 언어를 선택하십시오. 완료되면 **만들기**를 선택합니다.

    > [!div class=mx-imgBorder]
    > ![새 포털 만들기](media/create-new-portal.png "새 포털 만들기")  

**만들기**를 선택하면 포털이 프로비저닝을 시작하고 프로비저닝 상태가 [알림](#portal-provisioning-notifications)을 통해 표시됩니다.

포털 사전 구성 요소가 설치되지 않은 환경에서 포털을 작성한 경우 프로비저닝 상태도 그리드에 표시됩니다.

> [!div class=mx-imgBorder]
> ![표 알림](media/provision-progress-notif.png "표 알림")

포털이 성공적으로 프로비저닝되면 상태가 업데이트되고 포털이 그리드에 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 프로비저닝됨](media/recent-apps.png "포털 프로비저닝됨")

PowerApps 포털 스튜디오에서 포털을 편집하려면 [포털 편집](manage-existing-portals.md#edit)을 참조하십시오.

> [!NOTE]
> - 테넌트에서 최대 5개의 포털을 작성할 수 있습니다. 그러나 환경에서 작성된 각 유형의 포털은 하나만 있을 수 있습니다.
> - 포털을 프로비저닝할 권한이 충분하지 않으면 오류가 표시됩니다. 포털을 만들려면 Common Data Service에서 시스템 관리자 역할이 있어야 합니다. 또한 사용자 레코드의 **CAL(클라이언트 액세스 라이선스) 정보**에서 **액세스 모드**를 **읽기-쓰기**로 설정해야 합니다.
> - 이전 포털 추가 기능을 구입했으며 추가 기능을 사용하여 포털을 프로비저닝하려는 경우 **Dynamics 365 관리 센터** 페이지로 이동해야 합니다. 추가 정보: [이전 포털 추가 기능을 사용하여 포털 프로비저닝](provision-portal-add-on.md)
> - 이전 포털 추가 기능을 사용하여 포털을 프로비저닝한 경우 여전히 [make.powerapps.com](https://make.powerapps.com)에서 포털을 사용자 지정하고 관리할 수 있습니다.
> - [make.powerapps.com](https://make.powerapps.com)에서 포털을 프로비저닝하면 이전 포털 추가 기능이 사용되지 않습니다. 또한 이러한 포털은 **Dynamics 365 관리 센터** 페이지의 **애플리케이션** 탭 아래에 표시되지 않습니다.
> - Common Data Service 시작 포털은 **Dynamics 365 관리 센터** 페이지에서 생성할 수 없습니다.
> - 프랑스 지역에서는 PowerApps 포털을 사용할 수 없습니다.

## <a name="create-new-environment"></a>새로운 환경 만들기

환경을 만들 때 **공백에서 포털** 창에 제공된 옵션을 사용하여 다음 단계를 수행하십시오.

1.  **새로운 환경** 창에서 환경 이름을 입력한 다음 드롭다운 목록에서 지역 및 환경 유형을 선택하십시오. 환경을 만든 후에는 지역을 변경할 수 없습니다. 완료되면 **환경 만들기**를 선택합니다.

    > [!div class=mx-imgBorder]
    > ![새 환경 만들기](media/create-new-environment.png "새로운 환경 만들기")  

2.  환경이 만들어지면 대화 상자에 확인 메시지가 표시되고 데이터베이스를 만들라는 메시지가 나타납니다. **데이터베이스 만들기**를 선택하여 Common Data Service에 대한 액세스를 활성화합니다.

    > [!NOTE]
    > 데이터베이스 작성 프롬프트가 자동으로 표시되지 않을 수 있습니다. 이 경우 새 환경으로 이동하여 **공백에서 포털** 타일을 다시 선택해야 합니다.

    > [!div class=mx-imgBorder]
    > ![새 환경 생성됨](media/new-environment-created.png "새 환경 생성됨")  

3.  데이터베이스에 저장된 데이터의 통화 및 언어를 선택하십시오. 데이터베이스가 작성되면 통화 또는 언어를 변경할 수 없습니다. 완료되면 **내 데이터베이스 만들기**를 선택합니다. 포털이 프로비저닝된 후 샘플 콘텐츠를 빠르게 시작할 수 있는 시작 포털로 데이터베이스가 작성됩니다.

    > [!NOTE]
    > **시작 포털 포함** 옵션은 **공백에서 포털** 창에 제공된 옵션을 사용하여 환경을 만들 때만 사용할 수 있습니다. PowerApps 관리 센터에서 환경을 생성할 때는 이 옵션을 사용할 수 없습니다.

    > [!div class=mx-imgBorder]
    > ![새 데이터베이스 만들기](media/create-new-database.png "새 데이터베이스 만들기") 

    Common Data Service에 데이터베이스를 작성하는 데 몇 분이 걸릴 수 있습니다. 데이터베이스가 작성되면 PowerApps 홈 페이지의 환경 목록에서 새 환경이 선택되며 포털 관리 앱이 작성됩니다. 이 앱은 실제 포털이 아니라 고급 구성 활동을 수행할 수 있는 모델 기반 도우미 앱입니다. 이제 외부 대상 웹 사이트 디자인을 위한 포털 작성을 진행할 수 있습니다.

    > [!div class=mx-imgBorder]
    > ![포털 관리 앱](media/portal-mgmt-app.png "포털 관리 앱")

4. 환경 및 데이터베이스를 생성한 후 **나만의 앱 만들기** 아래에서 **공백에서 포털**을 선택합니다. 

    > [!NOTE]
    > 데이터베이스가 작성되었지만 여전히 데이터베이스 작성 프롬프트가 표시되는 경우 **공백에서 포털** 타일을 선택하기 전에 PowerApps 홈 페이지를 새로 고쳐야 합니다.


## <a name="portal-provisioning-notifications"></a>프로비전 프로비저닝 알림

**만들기**를 선택하면 포털이 프로비저닝을 시작하고 프로비저닝 상태가 알림을 통해 표시됩니다.

**토스트 알림**

포털을 프로비저닝하기 위해 **만들기**를 선택하면 다음 알림이 표시됩니다.

> [!div class=mx-imgBorder]
> ![토스트 알림](media/toast-notif.png "토스트 알림") 

**알림 창의 알림**

프로비저닝 요청이 완료되면 다음 알림이 **알림** 창에 표시됩니다.

프로비저닝 진행 중으로 표시되는 알림

> [!div class=mx-imgBorder]
> ![창 알림](media/pane-notif.png "창 알림") 

프로비저닝 완료로 표시되는 알림

> [!div class=mx-imgBorder]
> ![프로비전 성공 알림](media/provision-complete-notif.png "프로비전 성공 알림") 

포털 프로비저닝에 실패하면 알림이 유사하게 표시됩니다.
  
**전자 메일을 통한 알림**

프로비저닝 요청이 완료되면 포털을 작성하는 사용자에게 확인 전자 메일 알림이 전송됩니다. 또한 포털 프로비저닝이 완료된 후 사용자에게 전자 메일이 발송됩니다.

## <a name="disable-portal-creation-in-a-tenant"></a>테넌트에서 포털 작성 사용 안 함

전역 관리자로서 관리자가 아닌 사람이 테넌트에서 포털을 작성하지 못하도록 하려면 PowerShell을 통해 `disablePortalsCreationByNonAdminUsers` 테넌트 수준 설정을 사용하도록 설정하십시오. PowerShell cmdlet을 실행하려면 먼저 필요한 모듈을 설치해야 합니다. 필요한 PowerShell 모듈 설치에 대한 내용은 [설치](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation)를 참조하십시오.

모듈을 설치했으면 PowerShell 창에서 다음 명령을 실행합니다(관리자 권한으로 PowerShell 실행).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

관리자는 다음 Azure 역할 중 하나를 가진 사용자입니다.

- 전역 관리자
- Dynamics 365 서비스 관리자
- Power Platform 서비스 관리자

위에서 언급한 Azure 역할 중 어느 것도 없는 사용자는 관리자가 아닌 것으로 간주됩니다.

테넌트에서 포털 작성이 비활성화되어 있으면 관리자가 아닌 사용자에게 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 생성 차단 오류](media/portal-create-blocked-error.png "포털 생성 차단 오류")
