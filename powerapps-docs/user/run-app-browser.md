---
title: 웹 브라우저에서 앱 실행 | Microsoft Docs
description: 이 항목에서는 웹 브라우저에서 앱을 실행하는 방법 알아보기
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 12/05/2019
ms.author: mkaur
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8ce6cfe213817cd603857bb5ea2735b188f8cb6c
ms.sourcegitcommit: 15c6b26ff085928459ad9b3f52fb607fae4a997d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74956787"
---
# <a name="run-an-app-in-a-web-browser"></a>웹 브라우저에서 앱 실행
앱을 만들거나 다른 사람이 사용자와 앱을 공유 하는 경우 Dynamics 365 모바일 앱 또는 태블릿의 웹 브라우저에서 해당 앱을 실행할 수 있습니다. 이 항목에서는 [Dynamics 365 홈 페이지](https://home.dynamics.com)에서 태블릿의 웹 브라우저에서 캔버스 또는 모델 기반 앱을 실행 하는 방법에 대해 알아봅니다.

모든 기능 및 최적화 된 환경을 위해 휴대폰 및 태블릿 모바일 앱에 대 한 Dynamics 365를 사용 하는 것이 좋습니다. 휴대폰 및 태블릿 앱에 대 한 Dynamics 365가 설치 되어 있지 않은 경우 장치에 화면 해상도가 충분히 높은 경우에도 태블릿에서 웹 브라우저를 사용할 수 있습니다. 자세한 내용은 [지원 되는 항목](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app)을 확인 하세요.

> [!NOTE]
> 휴대폰에서 웹 브라우저를 사용 하 여 모델 기반 앱을 실행 하는 것은 지원 되지 않습니다. 휴대폰 앱에 대 한 Dynamics 365을 사용 해야 합니다.

이 빠른 시작을 수행하려면 다음이 필요합니다.
- Power Apps 라이선스. 이 기능은 power apps 요금제 (예: power apps [요금제 2 평가판](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps)) 또는 power apps를 포함 하는 [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) 또는 [Dynamics 365](https://dynamics.microsoft.com/pricing/) 요금제와 함께 사용할 수 있습니다. 
- 또한, 자신이 빌드하거나 다른 사용자가 빌드하고 공유한 앱에 대한 액세스 권한
- 지원되는 웹 브라우저 및 운영 체제에 대한 액세스 권한
   - 캔버스 앱의 경우 [시스템 요구 사항, 제한 및 구성 값](../maker/canvas-apps/limits-and-config.md)을 참조하세요.
   - 모델 기반 앱의 경우 [지원되는 웹 브라우저 및 모바일 디바이스](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)를 참조하세요.


## <a name="sign-in-to-dynamics-365"></a>Dynamics 365에 로그인
[https://home.dynamics.com](https://home.dynamics.com)에서 Dynamics 365에 로그인합니다.

## <a name="find-an-app-on-the-home-page"></a>홈페이지에서 앱 찾기
홈페이지에서는 여러 형식의 비즈니스 앱을 표시할 수 있지만 검색 상자에 해당 이름의 일부를 입력하여 특정 앱을 찾을 수 있습니다. 목록을 필터링 하 여 Power Apps와 같은 특정 원본에서 만든 앱만 표시할 수도 있습니다. 이렇게 하려면 **필터** 를 선택한 다음 원본을 선택 합니다.

앱을 최근에 설치한 경우 앱 목록에 즉시 표시되지 않을 수 있습니다. **동기화** 를 선택 하 여 모든 앱을 표시 합니다. 이 프로세스는 최대 1분 정도 걸릴 수 있습니다.

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>URL에서 앱 실행
앱의 URL을 태블릿 브라우저에 책갈피로 저장 하 고 책갈피를 선택 하 여 실행 하거나, 전자 메일을 통해 URL을 링크로 보낼 수 있습니다. 다른 사용자가 앱을 만들고 전자 메일을 통해 공유 하는 경우 전자 메일의 링크를 선택 하 여 앱을 실행할 수 있습니다. URL을 사용하여 앱을 실행하는 경우에 Azure Active Directory 자격 증명을 사용하여 로그인하라는 메시지가 표시될 수 있습니다.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>데이터에 연결
앱에서 디바이스의 기능(예: 카메라 또는 위치 서비스)을 사용하기 위해 데이터 원본에 연결하거나 권한이 필요한 경우 이에 동의해야 앱을 사용할 수 있습니다. 일반적으로 처음에만 메시지가 표시됩니다.

![Connection](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>앱 닫기
앱을 닫으려면 Dynamics 365 홈페이지에서 로그아웃하거나 다른 앱을 엽니다.

## <a name="next-steps"></a>다음 단계
이 항목에서는 웹 브라우저에서 캔버스 또는 모델 기반 앱을 실행하는 방법을 알아봅니다. 다음 방법에 대해 알아보세요.
- 모바일 장치에서 캔버스 앱 실행을 참조 하세요. [모바일 장치에서 캔버스 앱 실행](run-app-client.md) 을 참조 하세요.
- 모바일 장치에서 모델 기반 앱 실행은 [모바일 장치에서 모델 기반 앱 실행](run-app-client-model-driven.md) 을 참조 하세요.
- 모델 기반 앱 사용은 [모델 기반 앱 사용](use-model-driven-apps.md) 을 참조 하세요.

