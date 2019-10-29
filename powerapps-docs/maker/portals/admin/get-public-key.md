---
title: 포털의 공개 키 다운로드 | MicrosoftDocs
description: 포털의 공개 키를 다운로드 하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975981"
---
# <a name="download-public-key-of-portal"></a>포털의 공개 키 다운로드

포털의 공개 키를 사용 하 여 인증 된 방문자가 포털에 사용할 수 있도록 Dynamics 365의 모델 기반 앱에 대 한 라이브 지원을 구성 합니다. CafeX의 [라이브 지원](https://www.cafex.com/en/products/live-assist-dynamics-365/)에서는 사용자가 포털에서 라이브 채팅 지원을 포함할 수 있는 채팅 솔루션을 제공 합니다. 공개 키를 사용 하 여 포털에 채팅을 포함 하는 방법에 대 한 자세한 정보: [Dynamics Customer 포털의 인증 된 방문자](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 작업** > **공개 키 가져오기**로 이동 합니다. 키가 표시 됩니다.

    > [!div class=mx-imgBorder]
    > 포털 ![의 공개 키 가져오기](../media/get-public-key.png "포털의 공개 키 가져오기")

3.  텍스트로 **다운로드** 를 선택 하 여 텍스트 파일에 키를 다운로드 합니다.

또는 URL로 이동 하 여 공개 키를 가져올 수도 있습니다. `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> 포털이 현재 프로 비전 되 고 있거나 조직에서 패키지 설치가 완료 되지 않은 경우 공개 키를 다운로드 하려고 하면 오류가 표시 됩니다. 포털 프로 비전이 완료 되 고 포털이 실행 중이 될 때까지 기다려야 합니다.
