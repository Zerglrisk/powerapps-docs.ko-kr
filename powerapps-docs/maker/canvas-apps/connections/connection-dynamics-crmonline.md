---
title: Dynamics 365 연결 개요 | Microsoft Docs
description: Dynamics 365에서 데이터를 관리하기 위한 앱 만들기
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: matp
ms.reviewer: ''
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 37818e3c7cca175218826c1707ab83cd5c193ae7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723918"
---
# <a name="connect-to-dynamics-365-from-power-apps"></a>파워 앱에서 Dynamics 365에 연결
Power Apps를 사용 하면 코드를 거의 또는 전혀 사용 하지 않고 모바일 앱을 신속 하 게 생성, 사용자 지정, 공유 및 실행할 수 있습니다. Dynamics 365 커넥터를 사용하여 몇 분 만에 사용자의 조직과 공유할 수 있는 유용한 모바일 앱을 만들 수 있습니다.

이 토픽의 단계에 따라 사용자가 Dynamics 365에 있는 연락처를 찾아 보고, 추가하며 삭제 및 업데이트할 수 있는 앱을 만듭니다. 사용자는 [브라우저](../../../user/run-app-browser.md) 또는 휴대폰과 같은 [모바일 디바이스](../../../user/run-app-client.md)에서 앱을 실행할 수 있습니다.

## <a name="prerequisite"></a>필수 조건
이 자습서를 따르려면 Dynamics 365 플랜이 포함된 Microsoft Office 365 계정이 필요합니다.

## <a name="create-a-connection"></a>연결 만들기
1. [Power Apps에 로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
2. 왼쪽 탐색 창에서 **연결**을 클릭합니다.
   
    ![파일 메뉴의 연결 옵션](./media/connection-dynamics-crmonline/file-connections.png)
3. 오른쪽 위 모서리에서 **새 연결**을 클릭합니다.
   
    ![새 연결](./media/connection-dynamics-crmonline/new-connection.png)
4. 연결 목록에서 **Dynamics 365**를 클릭합니다.
   
    ![파일 메뉴의 연결 옵션](./media/connection-dynamics-crmonline/connection-d365.png)
5. 대화 상자에서 **만들기**를 클릭합니다.
   
    ![연결 만들기](./media/connection-dynamics-crmonline/create-connection.png)
6. **계정에 로그인** 대화 상자에서 Dynamics 365(온라인) 테넌트에 대한 자격 증명을 제공합니다.
   
    연결이 만들어집니다.

## <a name="generate-an-app-automatically"></a>자동으로 앱 생성
1. [Power Apps에 로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)하 고 왼쪽 아래 모서리 근처에서 **새 앱** 을 클릭 합니다.
   
    ![새 앱](./media/connection-dynamics-crmonline/new-app.png)
2. **데이터를 통해 시작**에서 **Dynamics 365** 타일의 **전화 레이아웃**을 클릭합니다.
   
    ![파워 앱 Dynamics 365 커넥터 선택](./media/connection-dynamics-crmonline/phonelayout.png)
3. **연결**에서 원하는 연결을 선택한 다음, 앱에서 관리할 Dynamics 365의 인스턴스에 해당하는 데이터 세트를 선택합니다.
4. **테이블 선택**에서 **연락처**를 클릭한 다음, **연결**합니다.
5. 왼쪽 탐색 모음에서 오른쪽 위 모서리의 아이콘을 클릭하거나 탭하여 미리 보기로 전환합니다.
   
    ![보기 토글](./media/connection-dynamics-crmonline/toggle-view.png)

Power Apps는 연락처 레코드를 기반으로 3 화면 앱을 생성 합니다.

* **BrowseScreen1**. 이 화면은 사용자가 앱을 열 때 기본적으로 나타납니다. 왼쪽 탐색 모음에서 이 화면에 대한 미리 보기가 다른 두 화면 위에 나타납니다.
* **DetailScreen1**. 이 화면은 사용자가 **BrowseScreen1**의 항목을 클릭할 때 나타납니다.  왼쪽 탐색 모음에서 **DetailScreen1**에 대한 미리 보기가 다른 두 화면 사이에 나타납니다.
* **EditScreen1**. 이 화면은 사용자가 **DetailScreen1**에서 항목에 대한 편집 아이콘을 클릭할 때 나타납니다. 왼쪽 탐색 모음에서 **EditScreen1**에 대한 미리 보기가 다른 두 화면 아래에 나타납니다.

이 앱은 초기 상태로 실행할 수 있지만, 각 화면에 대한 정보를 조정하여 좀 더 유용하게 만들 수 있습니다.

## <a name="customize-browsescreen1"></a>BrowseScreen1 사용자 지정
이 절차에서는 각 연락처의 이름과 성을 표시하도록 **BrowseScreen1**을 구성합니다. 데이터는 성을 기준으로 알파벳 순서로 정렬되며 2열 그리드에 이미지를 포함합니다.

1. **BrowseScreen1**에서 첫 번째를 제외한 모든 레코드를 클릭하여 갤러리를 선택합니다.
   
    ![레이아웃 선택](./media/connection-dynamics-crmonline/select-gallery.png)
2. 오른쪽 창에서 **데이터** 탭을 클릭하거나 탭합니다.
3. 레이아웃 목록에서 2열 그리드에 그림과 텍스트를 표시하는 레이아웃을 클릭하거나 탭합니다.
   
    이 옵션을 표시하려면 아래까지 스크롤해야 합니다.
   
    ![레이아웃 선택](./media/connection-dynamics-crmonline/select-layout.png)
4. 갤러리를 선택한 상태로 이 수식을 복사한 다음, 공식 표시줄(**fx** 단추의 오른쪽)에 해당 공식을 붙여 넣습니다.
   
    `SortByColumns(Search(Filter(Contacts,statuscode=1), TextSearchBox1.Text, "lastname"), "lastname", If(SortDescending1, Descending, Ascending))`
5. 오른쪽 창에서 맨 위 드롭다운 목록을 **firstname**, 중간 드롭다운 목록을 **lastname**으로 설정합니다.
   
    ![Body1 선택](./media/connection-dynamics-crmonline/firstname-lastname.png)
6. (선택 사항) **파일** 메뉴에서 **다음 이름으로 저장**을 클릭하고 앱에 사용할 이름을 입력한 다음 **저장**을 클릭합니다.
   
    기본적으로 앱은 클라우드로 저장됩니다. 앱을 로컬에 저장하려면 **이 컴퓨터**를 클릭합니다.

## <a name="customize-detailsscreen1-and-editscreen1"></a>DetailsScreen1 및 EditScreen1 사용자 지정
1. 왼쪽 탐색 모음에서 중간 미리 보기를 클릭하여 **DetailsScreen1**을 선택합니다.
2. **DetailScreen1**에서 왼쪽 창에 사용자 지정 옵션을 표시하려면 제목 표시줄 아래의 아무 곳이나 클릭합니다.
   
    ![양식 사용자 지정 표시](./media/connection-dynamics-crmonline/show-customization.png)
3. 오른쪽 창에서 각 필드의 눈 모양 아이콘을 클릭하여 숨깁니다.
   
    ![필드 숨기기](./media/connection-dynamics-crmonline/hide-field.png)
4. 제목 표시줄의 아무 곳이나 클릭하여 **Form1**을 선택합니다.
   
    ![Form1 선택](./media/connection-dynamics-crmonline/select-form1.png)
5. 오른쪽 창에서 이러한 각 필드의 눈 모양 아이콘을 클릭하면 화면에 각 연락처에 대한 4개의 다른 필드와 이미지(테이블에 하나 포함되어 있는 경우)가 표시됩니다.
   
   * **entityimage**
   * **firstname**
   * **lastname**
   * **mobilephone**
   * **emailaddress1**
     
     오른쪽 창은 다음 그래픽과 유사해야 합니다.
     
     ![Form1 선택](./media/connection-dynamics-crmonline/show-fields.png)
6. 왼쪽 탐색 모음에서 하단 미리 보기를 클릭하여 **EditScreen1**을 선택합니다.
7. 이 절차의 단계를 반복하여 **DetailsScreen1**과 동일한 방식으로 **EditScreen1**을 사용자 지정합니다.
8. (선택 사항) 앱을 저장합니다.

## <a name="next-steps"></a>다음 단계
* 왼쪽 탐색 모음에서 **BrowseScreen1**을 클릭한 다음, F5 키를 누르거나 오른쪽 위 모서리 근처의 ![미리 보기 모드](./media/connection-dynamics-crmonline/runpowerapp.png)를 클릭하여 미리 보기 모드에서 앱을 테스트합니다.
* [앱 공유](../share-app.md)
* [두 번째 데이터 원본 추가](../add-data-connection.md)

