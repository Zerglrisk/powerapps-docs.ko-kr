---
title: 팀에 PowerApps 앱 포함 | Microsoft Docs
description: Microsoft 팀의 PowerApps에서 만든 앱을 포함 하 여 공유할 수 있습니다.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/09/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba08437dc144fc81aa9748163b1005222735cb69
ms.sourcegitcommit: f296922b8039b573e5adb81423a544f70c56c1ee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2019
ms.locfileid: "70842249"
---
# <a name="embed-a-powerapps-app-in-teams"></a>팀에 PowerApps 앱 포함 

Microsoft 팀에 직접 포함 하 여 만든 PowerApps를 공유할 수 있습니다. 완료 되 면 사용자는 자신이 **+** **있는 팀의 팀 채널이** 나 대화에 앱을 추가 하도록 선택할 수 있습니다. 앱은 **팀의 탭 아래에**타일로 표시 됩니다. 

관리자는 앱을 업로드 하 여 **모든 탭 섹션**아래에 있는 테 넌 트의 **모든** 팀에 표시 되도록 할 수 있습니다. [Microsoft 팀에서 앱 공유](https://docs.microsoft.com/en-us/power-platform/admin/embed-app-teams)를 참조 하세요.

> [!NOTE]
> 사용자 지정 앱 업로드를 허용 하도록 팀 사용자 지정 앱 정책을 설정 해야 합니다. 팀에 앱을 포함할 수 없는 경우 관리자에 게 문의 하 여 [사용자 지정 앱 설정을](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)설정 했는지 확인 합니다. 

## <a name="prerequisites"></a>필수 조건

- [PowerApps 라이선스 보유](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- 캔버스 앱 만들기

## <a name="locate-your-powerapps-guid"></a>PowerApp의 GUID 찾기

이후 단계에서 사용할 PowerApp의 GUID를 찾아 적어 둡니다.

1. 에 [https://web.powerapps.com](https://web.powerapps.com)로그인 한 다음 메뉴에서 **앱** 을 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 목록 표시](./media/embed-teams-app/file-apps2.png "앱 목록 표시")

2. 팀에서 공유 하려는 앱에 대 한 **추가 명령** (...)을 선택한 다음 **세부 정보**를 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 세부 정보](./media/embed-teams-app/app-details.png "앱 세부 정보")


3. 나중에 사용 하기 위해 **앱 ID** 를 기록 합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 세부 정보](./media/embed-teams-app/app-details2.png "앱 세부 정보")

## <a name="install-app-studio"></a>앱 Studio 설치

App Studio가 이미 설치 되어 있는 경우에는 이러한 단계를 건너뛸 수 있습니다. 

1. 팀에서 팀 메뉴 (![앱 아이콘](./media/embed-teams-app/apps-icon.png "앱 아이콘"))의 왼쪽 아래에 있는 **앱** 을 선택 합니다.

2. 검색 상자에서 "앱 스튜디오"를 검색 한 다음 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 스튜디오](./media/embed-teams-app/store-app-studio.png "앱 스튜디오")

3. **설치**를 선택 합니다. 

   > [!div class="mx-imgBorder"] 
   > ![앱 Studio 설치](./media/embed-teams-app/install-app-studio.png "앱 Studio 설치")

4. 앱 기능에 대해 **열기** 를 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 Studio 열기](./media/embed-teams-app/open-app-studio.png "앱 Studio 열기")

## <a name="create-a-teams-app-for-your-powerapp"></a>PowerApp에 대 한 팀 앱 만들기

1. 팀에서 App Studio를 엽니다.

   > [!div class="mx-imgBorder"] 
   > ![앱 Studio 열기](./media/embed-teams-app/open-app-studio2.png "앱 Studio 열기")

2. **매니페스트 편집기** 탭을 선택한 후 시작 아래에서 **새 앱 만들기** 를 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![새 앱 만들기](./media/embed-teams-app/create-new-app.png "새 앱 만들기")

3. 앱 **세부** 정보 페이지에서 앱에 대 한 정보를 입력 합니다.  앱 ID GUID에 대해 위에서 기록한 PowerApp의 앱 ID GUID를 사용 해야 합니다.  이렇게 하면 특정 PowerApp 팀 앱이 중복 되지 않습니다.
 
   > [!div class="mx-imgBorder"] 
   > ![정보 입력](./media/embed-teams-app/fill-in-info-about-app.png "정보 입력")

   |필드  |설명  |
   |---------|---------|
   |**앱 이름** |    |
   |약식 이름     | 필수. 앱에 대 한 짧은 표시 이름입니다. 30 자 제한        |
   |긴 이름     | 전체 앱 이름이 30 자를 초과 하는 경우 사용 되는 앱의 전체 이름입니다.       | 
   |**등록**     |         |
   |앱 ID     | 필수. 이 앱에 대해 Microsoft에서 생성 된 고유한 식별자입니다.        |
   |패키지 이름     | 필수. 이 앱에 대 한 고유 식별자입니다. 역방향 도메인 표기를 사용 하는 것이 좋습니다. 예: com. 예: <AppName>.       |
   |버전     | 필수. 특정 응용 프로그램의 버전입니다. 매니페스트에서 항목을 업데이트 하는 경우 버전도 증가 해야 합니다.     |
   |**기술**    |     |
   | 간단한 설명    | 필수. 공간이 제한 되는 경우 사용 되는 앱 환경에 대 한 간단한 설명입니다. 80 문자 제한   |
   | 자세한 설명    | 필수. 앱에 대 한 전체 설명입니다.     |
   | **개발자 정보**    |     |
   | 이름    | 필수. 회사 또는 개발자에 대 한 표시 이름입니다.     |
   | 사이트나    | 필수. Powerapps.com을 통해 앱의 웹 사이트에 대 한 https://URL입니다. 누군가가 앱을 설치 하면 "앱 정보" 페이지가 표시 됩니다. Powerapps.com에서 앱의 웹 버전에 연결 해야 합니다.   |
   | **앱 Url**    | 이러한 링크는 웹 사이트 URL과 함께 **정보** 페이지에 표시 됩니다.     |
   | 개인정보 처리 방침    | 필수. 개발자의 개인 정보 취급 방침에 대 한 https://URL입니다. [예:](https://go.microsoft.com/fwlink/p/?LinkID=698505)   |
   | 사용 약관    | 필수. 개발자의 사용 약관에 대 한 https://URL입니다.  [예:](https://go.microsoft.com/fwlink/p/?LinkID=698507)  |
   | **브랜딩**    |     |
   | 전체 색    | 전체 색 192x192 PNG 아이콘의 상대 파일 경로입니다.    |
   | 투명 윤곽선    |투명 한 32x32 PNG 윤곽선 아이콘의 상대 파일 경로입니다.     |
   | 강조 색    | 및와 함께 개요 아이콘의 배경으로 사용할 색입니다.     |

자세한 내용은 [매니페스트 편집기](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) 및 [매니페스트 스키마](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)를 참조 하세요.

4. 브랜딩 섹션까지 아래로 스크롤하고 앱에 필요한 로고 및 강조 색을 추가 합니다.  이러한 로고는 팀에서 앱에 대해 표시 됩니다. 

   > [!div class="mx-imgBorder"] 
   > ![브랜딩 및 탭](./media/embed-teams-app/branding-tabs.png "브랜딩 및 탭")

5. **기능**아래에서 **탭**을 선택 합니다.

6. **팀 탭** 에서 **추가**를 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![팀 탭 추가](./media/embed-teams-app/team-tab-add.png "팀 탭 추가")

7. 다음 형식을 사용 하 여 "구성 URL" 입력 필드에 앱의 구성 URL을 추가 합니다.`https://apps.powerapps.com/teams/settings/<PowerApp ID>`

   을 `<PowerApp ID>` 위에서 기록한 앱 ID GUID로 바꿉니다.

   앱이 표시 되는 [범위](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) 를 선택 합니다. **업데이트 구성** 이 선택 되어 있는지 확인 하 고 **저장**을 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![구성 URL](./media/embed-teams-app/configuration-url.png "구성 URL")

8. **마침**에서 **올바른 도메인**을 선택 합니다. 팀 응용 프로그램의 올바른 도메인으로 **apps.powerapps.com** 및 **apps.preview.powerapps.com** 를 추가 합니다.

   > [!div class="mx-imgBorder"] 
   > ![유효한 도메인 추가](./media/embed-teams-app/add-valid-domains.png "유효한 도메인 추가")

9. **마침**에서 **테스트 및 배포**를 선택 합니다. **설치**에서 **설치**를 선택 합니다.

   > [!div class="mx-imgBorder"] 
   > ![설치 선택](./media/embed-teams-app/test-distribute-app.png "설치 선택")

10. 앱을 설치할 팀을 선택 하 고 **설치**를 선택 합니다.

    > [!div class="mx-imgBorder"] 
    > ![팀에 추가 설치](./media/embed-teams-app/new-app-add-to-team.png "팀에 추가 설치")
11. 해당 앱의 인스턴스를 바로 채널에 추가 하려면에서 앱을 사용할 채널을 선택 하 고 **설정**을 선택 합니다.

    > [!div class="mx-imgBorder"] 
    > ![설정 선택](./media/embed-teams-app/app-now-available.png "설정 선택")

12. **저장**을 선택합니다.

## <a name="add-the-app-as-a-tab"></a>탭으로 앱 추가

채널 또는 대화에 탭으로 앱을 추가 하려면를 선택한 **+** 다음 **팀의 탭** 에서 앱을 선택 합니다. 

> [!div class="mx-imgBorder"] 
> ![앱을 탭으로 추가](./media/embed-teams-app/add-app-as-tab.png "앱을 탭으로 추가")

이제 앱이 탭으로 표시 됩니다.

> [!div class="mx-imgBorder"] 
> ![앱을 탭으로](./media/embed-teams-app/app-as-tab.png "앱을 탭으로")

### <a name="see-also"></a>참고 항목
[Microsoft 팀 시작](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[관리자의 경우: Microsoft 팀에 앱 포함](https://docs.microsoft.com/power-platform/admin/share-app-teams)
