---
title: 팀에서 PowerApps 앱 포함 | Microsoft Docs
description: Microsoft Teams 공유 하려면 PowerApps에서 만든 앱을 포함할 수 있습니다.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/29/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d17b02cc87bb219474aade955a2910f12fcf7f27
ms.sourcegitcommit: 2376c1f1f3431bca52a8deb9b966ce1fe9f88da0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66381389"
---
# <a name="embed-a-powerapps-app-in-teams"></a>팀에서 PowerApps 앱 포함 

Microsoft Teams 직접 포함 하 여 만든 PowerApps를 공유할 수 있습니다. 완료 되 면 사용자가 선택할 수 있습니다 **+** 앱 중 하나에 추가할 **에** team 채널 또는 있는 팀의 대화를 합니다. 앱에서 타일로 나타납니다 **팀에 대 한 탭**합니다. 

관리자 용으로 표시 되도록 앱을 업로드할 수 있습니다 **모든** 팀에서 테 넌 트에는 **모든 탭 섹션**합니다. 참조 [Microsoft Teams 앱 공유](https://review.docs.microsoft.com/en-us/power-platform/admin/embed-app-teams?branch=JimHoltzWorkBranch)합니다.

> [!NOTE]
> 팀 사용자 지정 앱 정책 사용자 지정 앱을 업로드할 수 있도록 설정 되어야 합니다. Teams에서 앱을 포함할 수 없습니다, 경우 관리자의 경우 이러한 설정한 참조 확인 [사용자 지정 앱 설정을](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)합니다. 

## <a name="prerequisites"></a>필수 조건

- [PowerApps 라이선스](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- 캔버스 앱을 만들고

## <a name="locate-your-powerapps-guid"></a>PowerApp의 찾습니다 GUID

찾기 및 PowerApp의 기록해 이후 단계에서 사용할 GUID입니다.

1. 에 로그인 [ https://web.powerapps.com ](https://web.powerapps.com)를 선택한 후 **앱** 메뉴에서.

   > [!div class="mx-imgBorder"] 
   > ![앱 목록 표시](./media/embed-teams-app/file-apps2.png "앱 목록을 표시")

2. 선택 **추가 명령** (...) 팀에서 공유 하 고 클릭 하려는 앱에 대 한 **세부 정보**합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 세부 정보](./media/embed-teams-app/app-details.png "앱 세부 정보")

3. 레코드를 **앱 ID** 나중에 사용할 수 있습니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 세부 정보](./media/embed-teams-app/app-details2.png "앱 세부 정보")

## <a name="install-app-studio"></a>App Studio를 설치 합니다.

App Studio를 이미 설치 되어 있으면 다음이 단계를 건너뛸 수 있습니다. 

1. 팀에서 선택 **앱** 팀 메뉴의 왼쪽 아래에서에서 (![앱 아이콘](./media/embed-teams-app/apps-icon.png "앱 아이콘")).

2. 검색 상자에 "App Studio"를 찾아 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. 선택 **설치**합니다. 

   > [!div class="mx-imgBorder"] 
   > ![App Studio를 설치](./media/embed-teams-app/install-app-studio.png "App Studio를 설치 합니다.")

4. 선택 **열고** 앱 기능에 대 한 합니다.

   > [!div class="mx-imgBorder"] 
   > ![App Studio를 엽니다](./media/embed-teams-app/open-app-studio.png "App Studio를 열고")

## <a name="create-a-teams-app-for-your-powerapp"></a>PowerApp에 대 한 팀 앱 만들기

1. 팀에서 App Studio를 엽니다.

   > [!div class="mx-imgBorder"] 
   > ![App Studio를 엽니다](./media/embed-teams-app/open-app-studio2.png "App Studio를 열고")

2. 선택 합니다 **매니페스트 편집기** 탭을 선택한 후 **새 앱 만들기** 에서 시작 합니다.

   > [!div class="mx-imgBorder"] 
   > ![새 앱 만들기](./media/embed-teams-app/create-new-app.png "새 앱 만들기")

3. 앱에 대 한 정보를 입력 합니다 **앱 정보** 페이지입니다.  앱 ID GUID를 위에서 기록한 PowerApp의 앱 ID GUID를 사용 해야 합니다.  Teams 앱의 특정 PowerApp에 대 한 중복을 피해 야 합니다.
 
   > [!div class="mx-imgBorder"] 
   > ![정보를 입력](./media/embed-teams-app/fill-in-info-about-app.png "정보 입력")

   |필드  |설명  |
   |---------|---------|
   |**앱 이름** |    |
   |짧은 이름     | 필수. 앱에 대 한 짧은 표시 이름입니다. 30 자까지 가능 합니다.        |
   |긴 이름     | 전체 앱 이름이 30 자를 초과 하는 경우 사용 되는 앱의 전체 이름입니다.       | 
   |**식별**     |         |
   |앱 ID     | 필수. 고유한 Microsoft-생성 된 식별자를이 앱에 대 한 합니다.        |
   |패키지 이름     | 필수. 이 앱에 대 한 고유 식별자입니다. 역방향 도메인 표기법;을 사용 하는 것이 좋습니다. 예를 들어 com.example 합니다. <AppName>.       |
   |버전     | 필수. 특정 앱의 버전입니다. 매니페스트에 무언가 업데이트 하는 경우 버전도 증가 해야 합니다.     |
   |**설명**    |     |
   | 간단한 설명    | 필수. 공간이 제한 된 경우 사용 되는 앱 경험을의 짧은 설명입니다. 80 자까지 가능 합니다.   |
   | 자세한 설명    | 필수. 앱의 전체 설명입니다.     |
   | **개발자 정보**    |     |
   | 이름    | 필수. 회사 또는 개발자에 대 한 표시 이름입니다.     |
   | 웹 사이트    | 필수. Powerapps.com 통해 앱에 대 한 웹 사이트는 https:// URL입니다. 사용자가 앱을 설치할 때는 "앱"에 대 한 페이지가 표시 됩니다. Powerapps.com에서 앱의 웹 버전에 연결 해야 합니다.   |
   | **앱 Url**    | 다음이 링크에 표시 되는 **에 대 한** 웹 사이트 URL과 함께 페이지입니다.     |
   | 개인 정보 취급 방침    | 필수. 개발자의 개인 정보 취급 방침 https:// URL입니다. [예제](https://go.microsoft.com/fwlink/p/?LinkID=698505)합니다.   |
   | 사용 약관    | 필수. 개발자의 사용 약관에 https:// URL입니다.  [예제](https://go.microsoft.com/fwlink/p/?LinkID=698507)합니다.  |
   | **브랜딩**    |     |
   | 전체 색    | 전체 색 192 x 192 PNG 아이콘 상대 파일 경로입니다.    |
   | 투명 한 개요    |상대 파일 경로 투명 하 게 하는 32 x 32 PNG 개요 아이콘입니다.     |
   | 강조 색    | 개요 아이콘에 대 한와 배경으로 함께에서 사용 하는 색입니다.     |

자세한 내용은 [매니페스트 편집기](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) 하 고 [매니페스트 스키마](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)합니다.

4. 브랜딩 섹션까지 아래로 스크롤합니다 하 고 로고 및 앱에 대 한 원하는 강조 색을 추가 합니다.  이들은 Teams에서 앱에 대 한 표시 되는 로고입니다. 

   > [!div class="mx-imgBorder"] 
   > ![브랜딩 및 탭](./media/embed-teams-app/branding-tabs.png "브랜딩 및 탭")

5. 아래 **기능**를 선택 **탭**합니다.

6. 아래 **팀 탭** 선택 **추가**합니다.

   > [!div class="mx-imgBorder"] 
   > ![팀 탭 추가](./media/embed-teams-app/team-tab-add.png "팀 탭 추가")

7. 다음 형식을 사용 하 여 "구성 URL" 입력된 필드에 앱의 구성 URL을 추가 합니다. `https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   대체 `<PowerApp ID>` 위에서 기록한 앱 ID GUID를 사용 하 여 합니다.

   선택 된 [범위](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) 에 표시할 앱에 대 한 합니다. 확인 **구성을 업데이트할 수** 선택 되며 선택 **저장**합니다.

   > [!div class="mx-imgBorder"] 
   > ![구성 URL](./media/embed-teams-app/configuration-url.png "구성 URL")

8. 아래 **완료**를 선택 **유효한 도메인**합니다. 추가 **apps.powerapps.com** 하 고 **apps.preview.powerapps.com** 팀 응용 프로그램에 대 한 유효한 도메인으로 합니다.

   > [!div class="mx-imgBorder"] 
   > ![유효한 도메인을 추가할](./media/embed-teams-app/add-valid-domains.png "유효한 도메인을 추가 합니다.")

9. 아래 **완료**를 선택 **테스트 하 고 배포**합니다. 아래 **설치**를 선택 **설치**합니다.

   > [!div class="mx-imgBorder"] 
   > ![설치를 선택할](./media/embed-teams-app/test-distribute-app.png "설치를 선택 합니다.")

10. 앱을 설치 하려는 팀을 선택 하 고 선택한 **설치**합니다.

    > [!div class="mx-imgBorder"] 
    > ![설치를 팀에 추가](./media/embed-teams-app/new-app-add-to-team.png "설치 팀에 추가")

11. 채널에 바로 해당 앱의 인스턴스를 추가 하려는 경우 선택에서 선택한 앱을 사용 하려는 채널 **설정**합니다.

    > [!div class="mx-imgBorder"] 
    > ![설치를 선택 합니다](./media/embed-teams-app/app-now-available.png "설정 선택")

12. **저장**을 선택합니다.

## <a name="add-the-app-as-a-tab"></a>탭으로 앱 추가

탭으로 대화 나 채널 앱을 추가 하려면 **+** 를 선택한 후 **팀에 대 한 탭** 앱을 선택 합니다. 

> [!div class="mx-imgBorder"] 
> ![탭으로 앱 추가](./media/embed-teams-app/add-app-as-tab.png "탭으로 앱 추가")

이제 앱이 탭으로 나타납니다.

> [!div class="mx-imgBorder"] 
> ![탭 앱](./media/embed-teams-app/app-as-tab.png "탭으로는 앱")

### <a name="see-also"></a>참고 항목
[Microsoft Teams 시작](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[관리자: Microsoft Teams 앱을 포함 합니다.](https://docs.microsoft.com/power-platform/admin/share-app-teams)