---
title: 웹 사이트 및 기타 서비스로 캔버스 앱 통합 | Microsoft Docs
description: 웹 사이트 및 기타 서비스로 앱을 포함합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3d67ef4b05b61f59fec49b0bbc0961970d8070bf
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678514"
---
# <a name="integrate-canvas-apps-into-websites-and-other-services"></a>웹 사이트 및 기타 서비스로 캔버스 앱 통합
사용자가 작업을 수행 하는 즉시 사용할 수 있는 경우 사용자가 작성 하는 앱이 가장 유용 합니다. Iframe에 캔버스 앱을 포함 하 여 해당 앱을 웹 사이트 및 Power BI 또는 SharePoint와 같은 다른 서비스에 통합할 수 있습니다.

이 토픽에서는 앱 포함을 위해 매개 변수를 설정하는 방법을 보여 준 다음 웹 사이트에 자산 순서 지정 앱을 포함합니다.

![포함된 앱이 있는 Power BI 대시보드](./media/embed-apps-dev/embed-dashboard.png)

다음과 같은 제한 사항을 염두에 두십시오.

- 동일한 테 넌 트의 Power Apps 사용자만 포함 된 앱에 액세스할 수 있습니다.
- Internet Explorer 11을 사용 하 여 Power Apps에 액세스 하려면 호환성 보기를 해제 해야 합니다.

Iframe을 사용 하지 않고 캔버스 앱을 SharePoint Online에 통합할 수도 있습니다. 추가 정보: [Power Apps 웹 파트를 사용](https://support.office.com/article/use-the-powerapps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c)합니다.

## <a name="set-uri-parameters-for-your-app"></a>앱에 대한 URI 매개 변수 설정
포함하려는 앱이 있는 경우 첫 번째 단계는 iframe이 앱을 찾을 수 있는 위치를 알 수 있도록 URI(Uniform Resource Identifier)에 대한 매개 변수를 설정하는 것입니다. URI는 다음과 같은 형식입니다.

```
https://apps.powerapps.com/play/[AppID]?source=iframe
```

> [!IMPORTANT]
> 8 월 2019부터 URI 형식이 https://web.powerapps.com/webplayer 에서 https://apps.powerapps.com/play 로 변경 되었습니다. 새 URI 형식을 사용 하려면 포함 된 iframe을 업데이트 하세요. 이전 형식에 대 한 참조는 호환성을 보장 하기 위해 새 URI로 리디렉션됩니다.
>
> 이전 형식:
> 
> https\://web.powerapps.com/webplayer/iframeapp? source = iframe & appId =/providers/Microsoft.PowerApps/apps/[AppID]

수행해야 하는 유일한 작업은 URI에서 [AppID]에 대한 앱 ID를 대체하는 것입니다('[' & ']' 포함). 해당 값을 가져오는 방법을 곧 보여 줄 예정이지만 먼저 URI에서 사용할 수 있는 모든 매개 변수는 다음과 같습니다.

* **[appID]** -실행할 응용 프로그램의 ID를 제공 합니다.
* **tenantid** -게스트 액세스를 지원 하 고 앱을 열 테 넌 트를 결정 하는 선택적 매개 변수입니다. 
* **screenColor** - 사용자를 위해 더 나은 앱 로딩 환경을 제공하는 데 사용됩니다. 이 매개 변수는 [RGBA(빨강 값, 녹색 값, 파랑 값, 알파)](../canvas-apps/functions/function-colors.md) 형식이며 앱이 로드하는 동안 화면 색상을 제어합니다. 앱의 아이콘과 동일한 색으로 설정하는 것이 좋습니다.
* **source** - 앱에 영향을 주지 않지만 포함하는 원본을 참조하기 위해 설명이 포함된 이름을 추가하는 것이 좋습니다.
* 마지막으로 [Param() 함수](../canvas-apps/functions/function-param.md)를 사용하여 원하는 사용자 지정 매개 변수를 추가할 수 있으며 해당 값을 앱에서 사용할 수 있습니다. `[AppID]?source=iframe&param1=value1&param2=value2`과 같이 URI의 끝에 추가됩니다. 이러한 매개 변수는 앱을 시작 하는 동안 읽기 전용입니다. 변경 해야 하는 경우 앱을 다시 열어야 합니다. [Appid] 다음의 첫 번째 항목에만 "?";이 있어야 합니다. 그 후에는 여기에 설명 된 대로 "&"을 사용 합니다. 

### <a name="get-the-app-id"></a>앱 ID 가져오기
앱 ID는 powerapps.com에서 제공됩니다. 포함하려는 앱의 경우:

1. [powerapps.com](https://powerapps.microsoft.com)의 **앱** 탭에서 줄임표( **. . .** )를 클릭하거나 탭합니다. 다음 **세부 정보**.
   
    ![앱 세부 정보로 이동](./media/embed-apps-dev/details.png)
1. **앱 ID**를 복사합니다.
   
    ![세부 정보에서 앱 ID 복사](./media/embed-apps-dev/app-id.png)
1. URI에서 `[AppID]` 값을 대체합니다. 자산 순서 지정 앱의 경우 URI는 다음과 같습니다.
   
    ```
    https://apps.powerapps.com/play/76897698-91a8-b2de-756e-fe2774f114f2?source=iframe
    ```

## <a name="embed-your-app-in-a-website"></a>웹 사이트에 앱 포함
앱을 포함하는 것은 이제 사이트(또는 Power BI 또는 SharePoint와 같은 iframe을 지원하는 다른 서비스)에 대한 HTML 코드에 iframe을 포함하는 것만큼 간단합니다.

```html
<iframe width="[W]" height="[H]" src="https://apps.powerapps.com/play/[AppID]?source=website&screenColor=rgba(165,34,55,1)" allow="geolocation; microphone; camera"/>
```

iframe 너비 및 높이에 대한 값을 지정하고 `[AppID]`에 대해 앱의 ID를 대체합니다.

> [!NOTE]
> 앱이 Google Chrome에서 이러한 기능을 사용할 수 있도록 허용하려면 iframe HTML 코드에 `allow="geolocation; microphone; camera"`를 포함하세요.

다음 이미지는 Contoso 샘플 웹 사이트에 포함된 자산 순서 지정 앱을 보여 줍니다.

![포함된 앱이 있는 Contoso 웹 사이트](./media/embed-apps-dev/contoso-website.png)

앱의 사용자를 인증하기 위해 다음 사항을 염두에 두십시오.

- 웹 사이트가 AAD(Azure Active Directory) 기반 인증을 사용하는 경우 추가 로그인이 필요하지 않습니다.
- 웹 사이트가 다른 로그인 메커니즘을 사용하거나 인증되지 않는 경우 사용자에게 iframe에서 로그인 프롬프트를 표시합니다. 로그인한 후에 앱의 작성자가 공유하는 한 앱을 실행할 수 있습니다.

보시다시피 앱 포함은 간단하면서도 강력합니다. 포함을 통해 사용자와 사용자의 고객이 작업하는 위치(웹 사이트, Power BI 대시보드, SharePoint 페이지 등)에 앱을 바로 가져올 수 있습니다.
