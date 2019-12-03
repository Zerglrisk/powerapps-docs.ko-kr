---
title: Common Data Service |에서 캔버스 앱 생성 Microsoft Docs
description: Power Apps에서 자동으로 캔버스 앱을 생성 하 여 Common Data Service 데이터를 관리 합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f1737a70a8b9f6be30c73a91116c88df38609966
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678560"
---
# <a name="generate-a-canvas-app-from-common-data-service-in-powerapps"></a>PowerApps의 Common Data Service에서 캔버스 앱 생성

Power Apps에서 [Common Data Service](../common-data-service/data-platform-intro.md)의 샘플 계정 목록에 따라 캔버스 앱을 자동으로 생성 합니다. 이 앱에서는 모든 계정을 찾아보고, 단일 계정의 세부 정보를 표시하며, 계정을 생성, 업데이트 또는 삭제할 수 있습니다.

Power Apps에 등록 하지 않은 경우 시작 하기 전에 [무료로 등록](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 하세요.

## <a name="prerequisites"></a>필수 조건

이 빠른 시작을 수행 하려면 [환경 작성자](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) 보안 역할에 할당 되어야 하며, Common Data Service 데이터베이스를 만들고 데이터를 포함 하며 업데이트를 허용 하는 [환경으로 전환](working-with-environments.md) 해야 합니다. 이러한 환경이 없고 관리자 권한이 있으면 이 요구 사항을 충족하는 [환경을 만들 수 있습니다](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment).

## <a name="generate-an-app"></a>앱 생성

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 필요한 경우 이 항목의 앞부분에 지정된 대로 환경을 전환합니다.

1. **고유한 앱 만들기** 아래에서 **데이터로 시작**을 마우스로 가리킨 다음, **이 앱 만들기**를 선택합니다.

    ![앱 만들기 옵션](./media/data-platform-create-app/start-from-data.png)

1. **Common Data Service** 타일에서 **휴대폰 레이아웃**을 선택합니다.

    ![연결 타일](./media/data-platform-create-app/connection-tile.png)

1. **테이블 선택**에서 **계정**을 선택한 다음, **연결**을 선택합니다.

1. **Power Apps 스튜디오 시작** 대화 상자가 나타나면 **건너뛰기**를 선택 합니다.

앱이 찾아보기 화면에 열리고 계정 목록이 갤러리라는 컨트롤에 표시됩니다. 화면 위쪽에 있는 제목 표시줄에는 갤러리의 데이터 새로 고침, 갤러리의 데이터를 사전순으로 정렬 및 갤러리에 데이터 추가에 대한 아이콘이 표시됩니다. 제목 표시줄 아래의 검색 상자에서 입력하거나 붙여넣을 텍스트를 기준으로 갤러리의 데이터를 필터링하는 옵션을 제공합니다. 

기본적으로 갤러리에는 이메일 주소, 도시 및 계정 이름이 표시됩니다. [다음 단계](data-platform-create-app.md#next-steps)에서 볼 수 있듯이, 데이터의 표시 방법을 변경하거나 다른 데이터 유형을 표시하도록 갤러리를 사용자 지정할 수 있습니다.

![찾아보기 화면](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>앱 저장
이 앱을 사용하거나 다른 사용자와 공유하기 전에 더 많은 변경 작업을 수행하려고 할 것입니다. 가장 좋은 방법은 진행하기 전에 지금까지의 작업을 저장하는 것입니다.

1. 왼쪽 위 모서리 근처에서 **파일** 탭을 선택합니다.

1. **앱 설정** 페이지에서 앱 이름을 **AppGen**으로 설정하고, 배경색을 진한 빨간색으로, 아이콘을 확인 표시로 변경합니다.

    ![앱 설정 페이지](./media/data-platform-create-app/app-settings.png)

1. 왼쪽 가장자리 근처에서 **저장**을 선택한 다음, 왼쪽 아래 모서리에서 **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계
이 빠른 시작에서는 Common Data Service의 계정에 대 한 샘플 데이터를 관리 하는 앱을 만들었습니다. 다음 단계에서는 사용자의 요구 사항에 맞게 기본 찾아보기 화면의 갤러리 및 다른 요소를 사용자 지정합니다.

> [!div class="nextstepaction"]
> [갤러리를 사용자 지정](customize-layout-sharepoint.md)합니다.
