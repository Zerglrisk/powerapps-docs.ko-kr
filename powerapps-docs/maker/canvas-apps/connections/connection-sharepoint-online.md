---
title: SharePoint 연결 개요 | Microsoft Docs
description: SharePoint에 대 한 사용 가능한 기능, 응답 및 예제를 참조 하세요.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ae82166b9cc21de1e25f99f7606ce7b95b2152b9
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71993958"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>캔버스 앱에서 SharePoint에 연결

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

SharePoint 사이트에 연결 하 여 사용자 지정 목록에서 자동으로 앱을 생성 하거나, 기존 앱에 데이터를 추가 하거나 처음부터 앱을 빌드하기 전에 연결을 만듭니다.

데이터가 있는 위치에 따라 다음 방법 중 하나 또는 둘 다를 사용할 수 있습니다.

- SharePoint Online 사이트 또는 온-프레미스 사이트에 사용자 지정 목록의 데이터를 표시 합니다.
- 라이브러리에서 이미지를 표시 하 고 비디오 또는 오디오 파일을 재생 합니다 (SharePoint Online에만 해당).

## <a name="generate-an-app"></a>앱 생성

사용자 지정 목록의 데이터를 관리 하려면 PowerApps에서 [3 화면 앱을 자동으로 생성할](../app-from-sharepoint.md)수 있습니다. 사용자는 첫 번째 화면에서 목록을 탐색 하 고, 두 번째 화면에서 항목에 대 한 세부 정보를 표시 하 고, 세 번째 화면에서 항목을 만들거나 업데이트할 수 있습니다.

> [!NOTE]
> SharePoint 목록에 **선택**, **조회**또는 **개인 또는 그룹** 열이 포함 된 경우이 항목의 뒷부분에 나오는 [갤러리에 데이터 표시](connection-sharepoint-online.md#show-list-columns-in-a-gallery) 를 참조 하세요.

## <a name="create-a-connection"></a>연결 만들기

1. [PowerApps에 로그인](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)하 고, 왼쪽 탐색 모음에서 **데이터**  > **연결** 을 선택한 다음, 왼쪽 위 모서리 근처에 있는 **새 연결** 을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 왼쪽 탐색 모음에서 데이터 > 연결을 ![Select 다음 왼쪽 위 모서리 근처에서 새 연결을 선택 합니다. ](./media/connection-sharepoint-online/new-connection.png)

1. 오른쪽 위 모서리 근처의 검색 상자에 **sharepoint**를 입력 하거나 붙여 넣은 다음 **sharepoint**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 오른쪽 위 모서리 근처에 있는 검색 상자 ![In SharePoint를 입력 하거나 붙여 넣은 다음 SharePoint를 선택 합니다. ](./media/connection-sharepoint-online/select-sharepoint.png)

1. 다음 단계 중 하나를 수행 합니다.

    - SharePoint Online에 연결 하려면 **직접 연결 (클라우드 서비스)** 을 선택 하 고 **만들기**를 선택한 다음, 자격 증명을 제공 합니다 (메시지가 표시 되는 경우).

        > [!div class="mx-imgBorder"]
        > SharePoint Online에 연결 ![To 직접 연결 (클라우드 서비스)을 선택 ](./media/connection-sharepoint-online/select-online.png)

        연결이 만들어지고, 기존 앱에 데이터를 추가 하거나 처음부터 앱을 빌드할 수 있습니다.

    - 온-프레미스 사이트에 연결 하려면 **온-프레미스 데이터 게이트웨이를 사용 하 여 연결**을 선택 합니다.

        > [!div class="mx-imgBorder"]
        > 온-프레미스 사이트에 연결 ![To * * 온-프레미스 데이터 게이트웨이를 사용 하 여 연결)을 선택 ](./media/connection-sharepoint-online/select-onprem.png)

        인증 유형으로 **Windows**를 지정한 다음 자격 증명을 지정합니다. 자격 증명에 도메인 이름이 포함된 경우 *도메인\별칭* 형식으로 지정합니다.

        > [!div class="mx-imgBorder"]
        > ![Specify 자격 증명 ](./media/connection-sharepoint-online/specify-creds.png)

        **게이트웨이 선택**아래에서 사용 하려는 게이트웨이를 선택 하 고 **만들기**를 선택 합니다.

        > [!NOTE]
        > 온-프레미스 데이터 게이트웨이를 설치 하지 않은 경우 [하나 설치](../gateway-reference.md)하 고 아이콘을 선택 하 여 게이트웨이 목록을 새로 고칩니다.

        > [!div class="mx-imgBorder"]
        > ![Choose 게이트웨이 ](./media/connection-sharepoint-online/choose-gateway.png)

        연결이 만들어지고, 기존 앱에 데이터를 추가 하거나 처음부터 앱을 빌드할 수 있습니다.

## <a name="add-data-to-an-existing-app"></a>기존 앱에 데이터 추가

1. PowerApps Studio에서 업데이트할 앱을 열고 **보기** 탭을 선택한 다음 **데이터 원본**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 보기 탭을 ![On 한 다음 데이터 소스를 선택 ](./media/connection-sharepoint-online/view-data-sources.png)

1. **데이터** 창에서 **데이터 원본 추가**  > **SharePoint**를 선택 합니다.

1. **SharePoint 사이트에 연결**아래에서 **최근에 사용한** 사이트 목록에서 항목을 선택 하거나 사용 하려는 사이트의 URL을 입력 하거나 붙여 넣은 다음 **연결**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Select 사이트 ](./media/connection-sharepoint-online/select-sp-site.png)

1. **목록 선택**에서 사용 하려는 **문서** 또는 하나 이상의 목록에 대 한 확인란을 선택 하 고 **연결**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 목록을 선택 ![Under 문서 또는 사용 하려는 하나 이상의 목록에 대 한 확인란을 선택 하 고 연결을 선택 ](./media/connection-sharepoint-online/select-sp-tables.png)

    일부 목록 형식은 기본적으로 표시되지 않습니다. PowerApps는 탬플릿 기반 목록이 아닌 사용자 지정 목록을 지원합니다. 사용할 목록의 이름이 표시 되지 않는 경우 아래쪽으로 스크롤한 다음 **사용자 지정 테이블 이름 입력**이 포함 된 상자에 목록 이름을 입력 합니다.

    > [!div class="mx-imgBorder"]
    > 사용자 지정 목록 이름 입력이 포함 된 상자에 목록 이름을 ![Type 합니다. ](./media/connection-sharepoint-online/custom-list.png)

    데이터 원본이 앱에 추가 됩니다.

## <a name="build-your-own-app-from-scratch"></a>처음부터 자신의 앱 빌드

[앱을 처음부터 새로 만들기](../get-started-create-from-blank.md) 의 개념을 Excel이 아닌 SharePoint에 적용 합니다.

## <a name="show-list-columns-in-a-gallery"></a>갤러리에 목록 열 표시

사용자 지정 목록에 이러한 유형의 열이 포함 되어 있는 경우 수식 입력줄을 사용 하 여 **갤러리 컨트롤에** 해당 데이터를 표시 하 고 해당 갤러리에 있는 하나 이상의 **레이블** 컨트롤의 **Text** 속성을 설정 합니다.

- **선택** 또는 **조회** 열에 대해 ThisItem를 지정 **합니다.** _ColumnName_ **.** 해당 열에 데이터를 표시 하는 값입니다.

    예를 들어 이름이 **Location**인 **선택** 열이 있으면 **ThisItem.Location.Value**을, 이름이 **PostalCode**인 **조회** 열이 있으면 **ThisItem.PostalCode.Value**를 지정합니다.

- **개인 또는 그룹** 열에 대해 ThisItem를 지정 **합니다.** _ColumnName_ **. DisplayName** -사용자 또는 그룹의 표시 이름을 표시 합니다.

    예를 들어 이름이 **Manager**인 **개인 또는 그룹**을 표시하려면 **ThisItem.Manager.DisplayName**을 지정합니다.

    이메일 주소나 직함 등과 같은 다른 사용자 정보를 표시할 수도 있습니다. 전체 옵션 목록을 표시 하려면 ThisItem를 지정 **합니다.** _ColumnName_ **.** (후행 마침표 포함).

    > [!NOTE]
    > **CreatedBy** 열에 대해 목록에서 항목을 만든 사용자의 표시 이름을 표시 하려면 **ThisItem** 를 지정 합니다. **ModifiedBy** 열에 대해 목록에서 항목을 변경한 사용자의 표시 이름을 표시하려면 **ThisItem.Editor.DisplayName**을 지정합니다.

- **관리 되는 메타 데이터** 열에 대해 ThisItem를 지정 **합니다.** _ColumnName_ **.** 해당 열에 데이터를 표시 하는 레이블입니다.

    예를 들어 이름이 **Languages**인 **관리되는 메타데이터**가 있으면 **ThisItem.Languages.Label**을 지정합니다.

## <a name="show-data-from-a-library"></a>라이브러리의 데이터 표시

SharePoint 라이브러리에 이미지가 여러 개 있는 경우 사용자가 표시할 이미지를 지정할 수 있도록 앱에 **드롭다운** 컨트롤을 추가할 수 있습니다. **갤러리** 컨트롤과 같은 다른 컨트롤 및 비디오와 같은 다른 데이터 형식에 동일한 원칙을 적용할 수도 있습니다.

1. 아직 연결 하지 않은 경우 [연결을 만든](#create-a-connection)다음 [기존 앱에 데이터를 추가](#add-data-to-an-existing-app)합니다.

1. **드롭다운** 컨트롤을 추가 하 고 이름을 **ImageList**로 만듭니다.

1. **ImageList** 의 **Items** 속성을 **Documents**로 설정 합니다.

1. 오른쪽 창의 **속성** 탭에서 **값** 목록을 연 다음 **이름**을 선택 합니다.

    라이브러리에 있는 이미지의 파일 이름이 **ImageList**에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 이미지의 ![List ](./media/connection-sharepoint-online/dropdown-items.png)

1. **이미지** 컨트롤을 추가 하 고 **image** 속성을 다음 식으로 설정 합니다.

    `ImageList.Selected.'Link to item'`

1. F5 키를 누른 다음 **ImageList**에서 다른 값을 선택 합니다.

    지정한 이미지가 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![Sample 이미지 ](./media/connection-sharepoint-online/golden-honey.png)

SharePoint 라이브러리에서 데이터를 표시 하는 더 복잡 한 방법을 보여 주는 [샘플 앱을 다운로드할](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) 수 있습니다.

1. 앱을 다운로드 한 후 [PowerApps Studio](https://us.create.powerapps.com/studio/#)을 열고 왼쪽 탐색 모음에서 **열기** 를 선택한 다음 **찾아보기**를 선택 합니다.
1. **열기** 대화 상자에서 다운로드 한 파일을 찾아서 연 다음이 항목의 처음 두 가지 절차에 따라 SharePoint 라이브러리를 데이터 원본으로 추가 합니다.

> [!NOTE]
> 기본적으로이 앱은 [위임 경고](../delegation-overview.md)를 표시 하지만 라이브러리에 500 개 미만의 항목이 포함 된 경우 무시 해도 됩니다.

이 단일 화면 앱에서 왼쪽 아래 모퉁이의 목록에는 라이브러리의 모든 파일이 표시 됩니다.

- 위쪽 근처의 검색 상자에 하나 이상의 문자를 입력 하거나 붙여넣어 파일을 검색할 수 있습니다.
- 라이브러리에 폴더가 포함 되어 있는 경우 제목 표시줄 바로 아래의 폴더 목록에서 필터 아이콘을 선택 하 여 파일 목록을 필터링 할 수 있습니다.

원하는 파일을 찾으면 해당 파일을 선택 하 여 오른쪽에 있는 **비디오**, **이미지**또는 **오디오** 컨트롤에 표시 합니다.

> [!div class="mx-imgBorder"]
> ![Sample 이미지 ](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>알려진 문제

### <a name="lists"></a>표시

PowerApps는 공백을 포함 하는 열 이름을 읽을 수 있지만 공백은 16 진수 이스케이프 코드 **"\_x0020 \_"** 로 바뀝니다. 예를 들어 SharePoint의 **"Column Name"** 은 데이터 레이아웃에 표시되거나 수식에 사용될 때 PowerApps에 **"Column_x0020_Name"** 으로 나타납니다.

모든 유형의 열이 지원 되는 것은 아니므로 모든 유형의 열이 모든 유형의 카드를 지 원하는 것은 아닙니다.

| 열 형식 | 지원 | 기본 카드 |
| --- | --- | --- |
| 한 줄 텍스트 |예 |보기 텍스트 |
| 여러 줄 텍스트 |예 |보기 텍스트 |
| 선택 |예 |보기 조회<br>편집 조회<br>다중 선택 보기<br>다중 선택 편집 |
| 번호 |예 |보기 백분율<br>보기 등급<br>보기 텍스트 |
| 통화 |예 |보기 백분율<br>보기 등급<br>보기 텍스트 |
| 날짜 및 시간 |예 |보기 텍스트 |
| 조회 |예 |보기 조회<br>편집 조회<br>다중 선택 보기<br>다중 선택 편집 |
| 부울(Yes/No) |예 |보기 텍스트<br>보기 설정/해제 |
| 개인 또는 그룹 |예 |보기 조회<br>편집 조회<br>다중 선택 보기<br>다중 선택 편집 |
| 하이퍼링크 |예 |보기 URL<br>보기 텍스트 |
| 그림 |예(읽기 전용) |보기 이미지<br>보기 텍스트 |
| 첨부 파일 |예(읽기 전용) |첨부 파일 보기|
| 계산됨 |예(읽기 전용) | |
| 작업 결과 |아니요 | |
| 외부 데이터 |아니요 | |
| 관리되는 메타데이터 |예(읽기 전용) | |
| 등급 |아니요 | |

### <a name="libraries"></a>라이브러리인

- PowerApps에서 라이브러리로 파일을 업로드할 수 없습니다.
- Pdf 뷰어 컨트롤에서 라이브러리의 PDF 파일을 표시할 수 없습니다.
- PowerApps Mobile은 **다운로드** 기능을 지원 하지 않습니다.
- 사용자가 PowerApps Mobile 또는 Windows 10 앱에서 앱을 실행 하는 경우에는 **Launch** 함수를 사용 하 여 갤러리에 라이브러리 콘텐츠를 표시 합니다.

## <a name="next-steps"></a>다음 단계

- [데이터 원본에서 데이터 표시](../add-gallery.md) 방법 알아보기
- [세부 정보 보기 및 레코드 만들기 또는 업데이트](../add-form.md) 방법 알아보기
- 연결할 다른 [데이터 원본](../connections-list.md) 유형 참조
