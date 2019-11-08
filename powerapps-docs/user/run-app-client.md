---
title: 모바일 디바이스에서 캔버스 기반 앱 실행 | Microsoft Docs
description: 모바일 디바이스에서 캔버스 앱을 실행하는 방법에 대해 알아봅니다.
author: Mattp123
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: matp
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 729d852227b31a6a162fdf94644d1e08c1a401ee
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543426"
---
# <a name="run-a-canvas-app-on-a-mobile-device"></a>모바일 디바이스에서 캔버스 앱 실행
앱을 만들거나 다른 사용자가 앱을 공유하는 경우 Windows, iOS, Android 또는 웹 브라우저에서 해당 앱을 사용할 수 있습니다. 이 항목에서는 모바일 디바이스에서 캔버스 앱을 실행하는 방법에 대해 알아봅니다. 모바일 디바이스에서 실행되는 앱은 위치 서비스 및 카메라와 같은 디바이스 기능을 활용할 수 있습니다.

이 절차를 수행하려면 PowerApps에 가입되지 않은 경우 시작하기 전에 [체험 등록](https://make.powerapps.com/signup?redirect=marketing&email=)을 수행한 다음, [지원되는 운영 체제](../maker/canvas-apps/limits-and-config.md)에서 실행되는 iPhone, iPad 또는 Android 디바이스의 [App Store](https://itunes.apple.com/app/powerapps/id1047318566?mt=8) 또는 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.msapps)에서 PowerApps를 다운로드합니다. 또한, 자신이 만들거나 다른 사용자가 만들고 공유한 캔버스 앱에 대한 액세스 권한이 있는지 확인합니다.

## <a name="open-powerapps-and-sign-in"></a>PowerApps 열기 및 로그인
모바일 디바이스에서 PowerApps를 열고 Azure Active Directory 자격 증명을 사용하여 로그인합니다.

![로그인 사용자](./media/run-app-client/run-client-login.png)

모바일 디바이스에 Microsoft Authenticator 앱이 설치되어 있는 경우 메시지가 표시되면 사용자 이름을 입력한 다음, 디바이스로 전송된 알림을 승인하기만 하면 됩니다.

## <a name="find-the-app"></a>앱 찾기
쉽게 앱을 찾으려면 **PowerApps** 메뉴를 연 다음, 필터를 선택합니다.

![앱 필터](./media/run-app-client/filter-menu.png)

다음 필터를 사용할 수 있습니다.

* **모든 앱**: 자신이 만든 앱과 다른 사용자가 공유한 앱을 포함한 액세스 권한이 있는 모든 앱을 표시합니다.

* **내 앱**: 최소 1번 이상 실행한 앱을 표시합니다.

* **샘플 앱**: 가상의 데이터로 실제 애플리케이션 시나리오를 소개하여 디자인 가능성을 살펴보도록 Microsoft에서 제공하는 샘플 앱을 표시합니다.

* **즐겨찾기**: 앱 타일에서 줄임표(...)를 탭한 다음, **즐겨 찾기**를 탭한 앱을 표시합니다. 이 목록에서 앱을 제거하려면 앱 타일에서 줄임표(...)를 탭한 다음, **즐겨찾기에서 제거**를 탭합니다.

    ![즐겨찾기로 표시](./media/run-app-client/favorite.png)

앱을 필터링한 후에 가장 최근에 앱을 열거나 수정한 날짜별로 또는 이름을 사전순으로 필터링한 목록을 정렬할 수 있습니다. 이러한 기본 설정은 PowerApps를 닫고 다시 열 때 유지됩니다.

![정렬 메뉴](./media/run-app-client/sort-menu.png)

실행하려는 앱의 이름을 알고 있는 경우, Powerapps 맨 위에 있는 검색 아이콘을 탭한 다음, 검색 상자에 해당 이름의 일부를 입력할 수 있습니다.

![Search](./media/run-app-client/search.png)

앱을 필터링한 경우 필터링한 목록을 검색합니다.

## <a name="run-an-app"></a>앱 실행
모바일 디바이스에서 캔버스 앱을 실행하려면 앱 타일을 탭합니다. 다른 사용자가 캔버스 앱을 만들고 이메일에서 사용자와 공유하는 경우 이메일의 링크를 탭하여 앱을 실행할 수 있습니다.

PowerApps를 처음 사용할 경우 화면에 앱을 종료하기 위한 살짝 밀기 제스처가 표시됩니다.

![앱 시작하기](./media/run-app-client/run-client-app.png)

## <a name="give-consent"></a>동의
앱에서 디바이스의 기능(예: 카메라 또는 위치 서비스)을 사용하기 위해 데이터 원본에 연결하거나 권한이 필요한 경우 이에 동의해야 앱을 사용할 수 있습니다. 일반적으로 처음에만 메시지가 표시됩니다.

![Connection](./media/run-app-client/app-connection.png)

## <a name="pin-an-app-to-the-home-screen"></a>홈 화면에 앱 고정
빠른 액세스를 위해 디바이스의 홈 화면에 앱을 고정할 수 있습니다. 앱 타일의 줄임표(...)를 탭하고 **홈에 고정**을 탭한 다음, 표시되는 지침을 따릅니다.

![앱 고정](./media/run-app-client/run-client-pin.png)

## <a name="close-an-app"></a>앱 닫기
앱을 닫으려면 손가락으로 앱을 왼쪽에서 오른쪽으로 살짝 밉니다. Android 디바이스에서는 뒤로 단추를 누른 다음, 앱의 종료 여부를 확인합니다.

## <a name="next-steps"></a>다음 단계
이 항목에서는 모바일 디바이스에서 캔버스 앱을 실행하는 방법을 배웠습니다. 또한 모바일 디바이스에서 모델 기반 앱을 실행할 수 있습니다.

> [!div class="nextstepaction"]
> [모바일 디바이스에서 모델 기반 앱 실행](run-app-client-model-driven.md)
