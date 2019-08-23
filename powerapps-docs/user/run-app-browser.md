---
title: 웹 브라우저에서 앱 실행 | Microsoft Docs
description: 이 항목에서는 웹 브라우저에서 앱을 실행하는 방법 알아보기
author: Mattp123
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 8/21/2019
ms.author: matp
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 00b7d5dc7960429f7cc13215cd118e26e206d7d4
ms.sourcegitcommit: d6b7f98b4ae011a753c1e72d7708f0f8dfbfb1fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896191"
---
# <a name="run-an-app-in-a-web-browser"></a>웹 브라우저에서 앱 실행
앱을 만들거나 다른 사용자가 앱을 공유하는 경우 Windows, iOS, Android 또는 웹 브라우저에서 해당 앱을 사용할 수 있습니다. 이 항목에서는 [Dynamics 365 홈페이지](https://home.dynamics.com)에서 웹 브라우저로 캔버스 또는 모델 기반 앱을 실행하는 방법을 알아봅니다.

이 빠른 시작을 수행하려면 다음이 필요합니다.
- PowerApps 라이선스 [PowerApps Plan 2 평가판](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps)이나 [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) 중 하나 또는 PowerApps가 포함된 [Dynamics 365](https://dynamics.microsoft.com/pricing/) 요금제와 같은 PowerApps 요금제로 제공됩니다. 
- 또한, 자신이 빌드하거나 다른 사용자가 빌드하고 공유한 앱에 대한 액세스 권한
- 지원되는 웹 브라우저 및 운영 체제에 대한 액세스 권한
   - Canvas 앱의 경우 다음을 참조 하세요. [시스템 요구 사항, 제한 및 구성 값](../maker/canvas-apps/limits-and-config.md)
   - 모델 기반 앱의 경우 다음을 참조 하세요. [지원 되는 웹 브라우저 및 모바일 장치](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>Dynamics 365에 로그인
[https://home.dynamics.com](https://home.dynamics.com)에서 Dynamics 365에 로그인합니다.

## <a name="find-an-app-on-the-home-page"></a>홈페이지에서 앱 찾기
홈페이지에서는 여러 형식의 비즈니스 앱을 표시할 수 있지만 검색 상자에 해당 이름의 일부를 입력하여 특정 앱을 찾을 수 있습니다. 또한 PowerApps와 같은 특정 원본에서 만든 앱만 표시되도록 목록을 필터링할 수 있습니다. 이렇게 하려면 **필터** 를 선택한 다음 원본을 선택 합니다.

앱을 최근에 설치한 경우 앱 목록에 즉시 표시되지 않을 수 있습니다. **동기화** 를 선택 하 여 모든 앱을 표시 합니다. 이 프로세스는 최대 1분 정도 걸릴 수 있습니다.

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>URL에서 앱 실행
브라우저에 책갈피로 앱의 URL을 저장하고 책갈피를 선택하여 실행할 수 있습니다. 또는 URL을 이메일을 통해 링크로 보낼 수 있습니다. 다른 사용자가 앱을 만들고 전자 메일을 통해 공유 하는 경우 전자 메일의 링크를 선택 하 여 앱을 실행할 수 있습니다. URL을 사용하여 앱을 실행하는 경우에 Azure Active Directory 자격 증명을 사용하여 로그인하라는 메시지가 표시될 수 있습니다.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>데이터에 연결
앱에서 디바이스의 기능(예: 카메라 또는 위치 서비스)을 사용하기 위해 데이터 원본에 연결하거나 권한이 필요한 경우 이에 동의해야 앱을 사용할 수 있습니다. 일반적으로 처음에만 메시지가 표시됩니다.

![연결](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>앱 닫기
앱을 닫으려면 Dynamics 365 홈페이지에서 로그아웃하거나 다른 앱을 엽니다.

## <a name="next-steps"></a>다음 단계
이 항목에서는 웹 브라우저에서 캔버스 또는 모델 기반 앱을 실행하는 방법을 알아봅니다. 다음 방법에 대해 알아보세요.
- 모바일 장치에서 캔버스 앱 실행을 참조 하세요. [모바일 장치에서 캔버스 앱 실행](run-app-client.md) 을 참조 하세요.
- 모바일 장치에서 모델 기반 앱 실행은 [모바일 장치에서 모델 기반 앱 실행](run-app-client-model-driven.md) 을 참조 하세요.
- 모델 기반 앱 사용은 [모델 기반 앱 사용](use-model-driven-apps.md) 을 참조 하세요.

