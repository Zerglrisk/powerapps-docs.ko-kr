---
title: 포털의 공개 키 다운로드 | MicrosoftDocs
description: 포털의 공개 키를 다운로드하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="download-public-key-of-portal"></a>포털의 공개 키 다운로드

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

포털의 공개 키는 Dynamics 365의 모델 기반 앱용 Live Assist를 구성하는 데 사용되어 인증된 포털의 방문자가 사용할 수 있습니다. CafeX에서 제공하는 [라이브 지원](https://www.cafex.com/en/products/live-assist-dynamics-365/)은 사용자가 자신의 포털에 라이브 채팅 지원을 포함할 수 있는 채팅 솔루션을 제공합니다. 공개 키를 사용하여 포털에 채팅을 포함하는 방법에 대한 자세한 내용은 [Dynamics 고객 포털의 인증된 방문자](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)를 참조하십시오.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 작업** > **공개 키 가져오기**로 이동합니다. 키가 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![포털의 공개 키 가져오기](../media/get-public-key.png "포털의 공개 키 가져오기")

3.  **텍스트로 다운로드**를 선택하여 키를 텍스트로 다운로드합니다.

또는 URL `<portal_base_URL>/_ services/auth/publickey`로 이동하여 공개 키를 가져올 수도 있습니다. 

> [!NOTE]
> 포털이 현재 프로비저닝 중이거나 조직에서 패키지 설치가 완료되지 않은 경우 공개 키를 다운로드하려고 하면 오류가 표시됩니다. 포털 프로비저닝이 완료되고 포털이 실행될 때까지 기다려야 합니다.
