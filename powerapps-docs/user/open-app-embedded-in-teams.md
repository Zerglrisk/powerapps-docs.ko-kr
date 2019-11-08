---
title: Microsoft Teams에 앱 추가 | Microsoft Docs
description: 앱을 공유하는 사용자가 해당 채널에서 앱을 열 수 있도록 Microsoft Teams 채널에 앱을 추가하는 방법에 대해 알아봅니다.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: mduelae
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 62a7166f228545f2a200570186ee23c868650b79
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543487"
---
# <a name="add-an-app-to-microsoft-teams"></a>Microsoft Teams에 앱 추가

Microsoft Teams는 Office 365 기술을 기반으로 구축된 채팅 기반 협업 플랫폼입니다. PowerApps 캔버스 앱을 팀의 채널에 추가하여 Teams 환경을 사용자 지정할 수 있습니다. 이 항목에서는 팀 채널에 제품 소개 샘플 앱을 추가한 다음, 해당 채널에서 앱을 여는 방법을 알아봅니다. 

![Microsoft 팀에 포함된 앱](./media/open-app-embedded-in-teams/embedded-app.png)

PowerApps에 등록하지 않은 경우 시작하기 전에 [무료로 등록합니다](https://make.powerapps.com/signup?redirect=marketing&email=).

## <a name="prerequisites"></a>필수 조건

이 절차를 수행하려면 [Office 365 구독](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) 및 [Teams의 채널](https://www.youtube.com/watch?v=he2f1quaR7M)이 필요합니다.

## <a name="sign-in-to-powerapps"></a>PowerApps에 로그인

[https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 PowerApps에 로그인합니다.

## <a name="add-an-app"></a>앱 추가

1. Microsoft Teams에서 팀을 선택하고, 해당 팀 아래에서 채널을 선택합니다. 이 예제에서는 **비즈니스 개발** 팀 아래의 **일반** 채널입니다.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. **+** 를 선택하여 탭을 추가합니다.

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. **탭 추가** 대화 상자에서 **PowerApps**를 선택합니다.

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. **샘플 앱** > **제품 소개** > **저장**을 선택합니다.

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    이제 앱을 채널에서 사용할 수 있습니다.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> 팀에 추가하기 전에 사용자 고유의 앱을 [공유](../maker/canvas-apps/share-app.md)해야 합니다(샘플 앱은 기본적으로 공유됨).

## <a name="open-an-app"></a>앱 열기

1. Microsoft Teams에서 앱을 포함하는 팀 및 채널을 선택합니다.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. **제품 소개** 탭을 선택합니다.

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    채널에서 앱이 열립니다.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>알려진 문제

Microsoft Teams의 데스크톱 앱:

* 앱은 보안(https) 연결을 통해 이미지 및 .pdf 파일과 같은 콘텐츠를 로드해야 합니다.
* **가속**, **나침반** 및 **위치**와 같은 일부 센서가 지원됩니다.
* AAC, H264, OGG Vorbis 및 WAV 오디오 형식만 지원됩니다.

## <a name="clean-up-resources"></a>리소스 정리

채널에서 앱을 제거하려면 **제품 소개** 탭 > **제거**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 항목에서는 팀 채널에 제품 소개 샘플 앱을 추가한 다음, 해당 채널에서 앱을 열었습니다. PowerApps에 대한 자세한 내용은 PowerApps 자습서를 계속합니다.

> [!div class="nextstepaction"]
> [PowerApps 자습서](../maker/canvas-apps/get-started-create-from-blank.md)
