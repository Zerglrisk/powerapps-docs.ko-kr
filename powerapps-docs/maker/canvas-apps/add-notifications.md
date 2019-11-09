---
title: 푸시 알림 보내기 | Microsoft Docs
description: PowerApps에서 앱에 네이티브 푸시 알림을 보내는 방법을 알아봅니다.
author: kavishi
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/08/2017
ms.author: kaagar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d55245a6fba0383ce897030e87ccf5c4e7c6749d
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897933"
---
# <a name="send-a-push-notification-in-powerapps"></a>PowerApps에서 푸시 알림 보내기
푸시 알림은 앱 사용자의 관심을 끌고 주요 작업의 우선 순위를 지정하는 데 도움이 되도록 소비자 및 비즈니스 시나리오에 대한 모바일 앱에 주로 사용됩니다. PowerApps에서 PowerApps 알림 커넥터를 사용하여 알림을 보낼 수 있습니다. PowerApps에서 만드는 모든 앱에 네이티브 푸시 알림을 보낼 수 있습니다. 나중에 더 많은 알림 유형을 추가할 예정입니다.

![푸시 알림 모양의 예](./media/add-notifications/pic1-notification-screenshot.png)

다음의 경우에 앱에 푸시 알림 추가

* 사용자가 정보를 즉시 알고 있어야 하는 경우
* 사용자가 미리 로드된 컨텍스트에서 앱을 사용하여 중요한 작업을 완료해야 하는 경우
* 특정 간격으로 사용자의 관심을 끌길 원하거나 사용자가 특정 컨텍스트에서 앱을 입력하도록 해야 하는 경우

> [!NOTE]
> 푸시 알림을 받으려면 각 사용자는 PowerApps Mobile에서 앱을 한 번 열거나 [Dynamics 365](https://home.dynamics.com/)의 AppSource에서 앱을 가져와야 합니다.

## <a name="before-you-start"></a>시작하기 전에
**참가자** 권한이 있는 앱에서 PowerApps 알림 연결을 추가합니다. 아직 앱이 없는 경우 [템플릿에서 앱을 신속하게 만들](get-started-test-drive.md) 수 있으며 기본적으로 필요한 사용 권한을 갖습니다. 해당 자습서 및 이 문서는 사례 관리 템플릿을 기반으로 하는 앱을 사용합니다.

## <a name="send-a-notification-from-a-flow"></a>흐름에서 알림 보내기
> [!NOTE]
> 흐름에서 푸시 알림을 트리거하는 경우 현재 한 번에 한 명의 사용자 또는 보안 그룹에만 알림을 보낼 수 있습니다.

1. [전원 자동화](https://flow.microsoft.com)에서 푸시 알림이 전송 되는 시기를 지정 하는 트리거를 만듭니다.

    예를 들어, 레코드가 Common Data Service의 **사례** 엔터티에 추가될 때 알림을 보낼 수 있습니다.

    ![Common Data Service 트리거를 사용하여 흐름 만들기의 스크린샷](./media/add-notifications/pic4-step1-flowupdated.png)
2. **PowerApps 알림** 커넥터를 사용하여 흐름에 대한 작업을 만들고 알림을 보내려는 앱의 **앱 ID**를 입력합니다.

    시나리오를 반영하도록 연결의 이름을 변경할 수도 있습니다.

    ![이러한 푸시 알림을 받을 PowerApps에 대한 연결 만들기의 스크린샷](./media/add-notifications/pic5-step2-create-connection.jpg)
3. (선택 사항) 열릴 때 앱에 매개 변수를 전달합니다(사용자가 푸시 알림을 탭한 후).

    예제에서는 선택한 연락처에 대한 **사례 ID** 및 **초기 소유자** 필드를 전달합니다.

    ![푸시 알림으로 선택적 매개 변수 전달의 스크린샷](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>앱에서 알림 보내기
하나의 앱에서 다른 앱으로 또는 동일한 앱으로 푸시 알림을 보낼 수 있습니다.

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 푸시 알림을 보내려는 앱으로 이동합니다.
2. **세부 정보** 탭에서 해당 앱의 **앱 ID**를 복사합니다.

    ![앱 ID 가져오기](./media/add-notifications/grab-id.png)
3. **연결** 탭에서 PowerApps 알림 커넥터에 대한 연결을 만들고, 이전 단계의 앱 ID에 붙여넣습니다.

    ![연결 만들기](./media/add-notifications/create-connection.png)
4. 트리거 앱에 연결을 추가합니다.

    예제에서는 트리거 앱과 동일한 앱을 사용합니다. 사례를 다시 할당하는 사용자도 새 사례 소유자에게 푸시 알림을 트리거합니다.

    ![연결 추가](./media/add-notifications/add-connection.png)
5. 푸시 알림 연결에서 **SendPushNotification** 메서드를 호출합니다.

    예제에서는 **OnSuccess** 속성의 형태를 사용하여 이 알림을 트리거합니다.

    ![PowerApps 수식](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>사용자가 알림을 탭하는 경우 특정 페이지 및 컨텍스트 로드
### <a name="pass-parameters"></a>매개 변수 전달
푸시 알림은 앱에 특정 매개 변수를 전달할 수 있습니다. 예를 들어, **CaseID** 값을 읽으려면 *Param("CaseID")* 을 사용합니다. 이 매개 변수를 신속하게 식별하려면 앱에 **레이블** 컨트롤을 추가합니다. 해당 컨트롤의 **Text** 속성을 **Param("CaseID")** 으로 설정합니다. 사용자가 **모든 앱** 목록에서 앱을 여는 경우 값은 비어 있습니다. 사용자가 디바이스의 다른 위치에서 앱을 여는 경우 값은 **CaseID** 값으로 채워집니다.

### <a name="set-the-start-page"></a>시작 페이지 설정
앱에서 열도록 설정할 수 있습니다. 예를 들어, 앱이 열리면 **사례 세부 정보** 페이지가 열리도록 설정할 수 있습니다.

1. **Timer** 컨트롤을 추가하고 이 수식에 해당 **OnTimerEnd** 속성을 설정합니다.
   <br>**Navigate(EditCase, ScreenTransition.None)**
2. (선택 사항) 해당 **Visible** 속성을 **false**로 설정하여 **타이머** 컨트롤을 숨깁니다.
3. 화면의 **OnVisible** 속성을 **Timer.Start()** 로 설정합니다.

> [!TIP]
> 알림을 위해 앱에서 고유한 첫 번째 페이지를 만드는 것이 좋습니다.
> 
> 1. 앱이 아직 열리지 않은 빈 페이지를 만들고, **Text Input** 컨트롤을 추가하고, 해당 **timer.Duration** 값을 설정합니다.
> 2. 앱을 만들 때 0이 아닌 값으로 타이머를 설정합니다. 앱을 게시할 준비가 되면 타이머를 즉시 트리거하도록 값을 **0**으로 설정합니다.

## <a name="syntax"></a>구문

| 이름 | 설명 |
| --- | --- |
| SendPushNotification |알림에 대한 연결 설정에 지정된 앱에 푸시 알림을 보냅니다. |

### <a name="parameters"></a>변수의

| 이름 | 유형 | 설명 |
| --- | --- | --- |
| recipients |String array, 필수 항목 |목록: <ul> <li>사용자 또는 보안 그룹에 대한 전자 메일 주소</li> <li>Azure Active Directory에서 사용자 또는 보안 그룹에 대한 개체 ID</li></ul> |
| message |String, 필수 항목 |푸시 알림의 메시지 본문입니다. |
| openApp |부울, 선택 사항 |사용자가 푸시 알림을 탭하면 앱을 열지 여부입니다. |
| params |매개 변수, 선택 사항 |알림에서 전달하는 키-값 매개 변수입니다. 앱에서 특정 페이지를 열고 특정 상태를 로드하도록 추가로 처리될 수 있습니다. |

### <a name="sample-formulas"></a>샘플 수식
기본 알림을 보냅니다.

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["f60ccf6f-7579-4f92-967c-2920473c966b", "72f988bf-86f1-41af-91ab-2d7cd011db47"],
        message: "A new case was assigned to you."
    }
)
```

앱을 열고 특정 매개 변수를 전달하는 알림을 보냅니다.

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["email1@contoso.com", "email2@contoso.com"],
        message: "message in the notif toast",
        params: Table({key:"notificationKey", value:"The value for notificationKey"}),
        openApp: true
    }
)
```

## <a name="known-limitations"></a>알려진 제한 사항
* 현재 알림은 Windows Phone용 PowerApps Mobile에 표시되지 않습니다.
* 현재 웹 브라우저에서만 앱을 실행하는 사용자에게 푸시 알림을 제공하지 않습니다.
* 알림은 특정 앱 아이콘 대신 일반 PowerApps 아이콘을 표시합니다.
* 전원 자동화를 사용 하는 경우 한 번에 한 명의 받는 사람에 게 푸시 알림을 보낼 수 있습니다.

참조 정보는 [PowerApps 알림 참조](https://docs.microsoft.com/connectors/powerappsnotification/)를 참조하세요.

