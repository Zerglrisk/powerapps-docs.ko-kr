---
title: 팀에 앱 포함 | Microsoft Docs
description: Microsoft 팀의 Power Apps에서 만든 앱을 포함 하 여 공유할 수 있습니다.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0b8750733ac6c97d1669c1063700a3d075fbabbe
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678491"
---
# <a name="embed-an-app-in-teams"></a>Teams에 앱 포함

Microsoft 팀에 직접 포함 하 여 만든 강력한 앱을 공유할 수 있습니다. 완료 되 면 사용자는 **+** 를 선택 하 여 사용자가 **있는 팀의 팀 채널** 또는 대화에 앱을 추가할 수 있습니다. 앱은 **팀의 탭 아래에**타일로 표시 됩니다.

관리자는 앱을 업로드 하 여 **모든 탭 섹션**아래에 있는 테 넌 트의 **모든** 팀에 표시 되도록 할 수 있습니다. [Microsoft 팀에서 앱 공유](https://docs.microsoft.com/power-platform/admin/embed-app-teams)를 참조 하세요.

> [!NOTE]
> 사용자 지정 앱 업로드를 허용 하도록 팀 사용자 지정 앱 정책을 설정 해야 합니다. 팀에 앱을 포함할 수 없는 경우 관리자에 게 문의 하 여 [사용자 지정 앱 설정을](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)설정 했는지 확인 합니다.

## <a name="prerequisites"></a>필수 조건

- 유효한 [Power Apps 라이선스가](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)필요 합니다.
- 팀에 앱을 포함 하려면 [PowerApps를 사용 하 여 만든](data-platform-create-app.md)기존 앱이 필요 합니다.

## <a name="download-the-app"></a>앱 다운로드

1. [Make.powerapps.com](https://make.powerapps.com)에 로그인 한 다음 메뉴에서 **앱** 을 선택 합니다.

    ![앱 목록 표시](./media/embed-teams-app/file-apps2.png "앱 목록 표시")

2. 팀에서 공유 하려는 앱에 대 한 추가 **작업** (...)을 선택한 다음 **팀에 추가**를 선택 합니다.

    ![앱 세부 정보](./media/embed-teams-app/add-to-teams.png "팀에 추가")

3. 팀에 추가 패널에서 **다운로드**를 선택 합니다. 그러면 Power Apps는 앱에 이미 설정한 앱 설명 및 로고를 사용 하 여 팀 매니페스트 파일을 생성 합니다.

    ![앱 세부 정보](./media/embed-teams-app/download-app.png "앱 다운로드")

## <a name="add-the-app-as-a-personal-app"></a>개인 앱으로 앱 추가

1. 앱을 개인 앱으로 추가 하거나 임의의 채널이 나 대화에 탭으로 추가 하려면 왼쪽 탐색 영역에서 **앱** 을 선택 하 고 **사용자 지정 앱 업로드**를 선택 합니다.

    > [!NOTE]
    > 사용자 지정 앱 **업로드** 는 팀 관리자가 [사용자 지정 앱 정책을](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies) 만들고 **사용자 지정 앱의 업로드 허용**이 설정 된 경우에만 표시 됩니다.

    ![앱을 탭으로 추가](./media/embed-teams-app/upload-custom-app.png "사용자 지정 앱 업로드")

2. **추가** 를 선택 하 여 앱을 개인 앱으로 추가 하거나 **팀에 추가** 를 선택 하 여 기존 채널 또는 대화 내에서 앱을 탭으로 추가 합니다.

## <a name="publish-the-app-to-the-teams-catalogue"></a>팀 카탈로그에 앱 게시

관리자 인 경우 Microsoft 팀 카탈로그에 앱을 [게시할](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) 수도 있습니다.

### <a name="see-also"></a>참고 항목

[Microsoft 팀 시작](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
