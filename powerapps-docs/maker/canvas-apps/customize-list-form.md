---
title: SharePoint 목록 양식 사용자 지정 | Microsoft Docs
description: Power Apps를 사용 하 여 사용자가 SharePoint 목록에서 항목을 만들고 업데이트 하는 양식을 사용자 지정할 수 있습니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/24/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5912723765f99539852884a3fe55738c171c64c3
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678583"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>PowerApps를 사용하여 SharePoint 목록 양식 사용자 지정

브라우저에서 Power Apps를 열어 SharePoint 목록의 양식을 쉽게 사용자 지정할 수 있습니다. C#과 같은 기존 코드를 작성하거나 InfoPath와 같은 다른 앱을 다운로드할 필요가 없습니다. 변경 내용을 게시하는 경우 해당 사용자가 모두 사용하기 위해 SharePoint 목록 내에 양식이 포함됩니다. Power Apps에서 분석 보고서를 검토 하 고, 조건부 서식을 쉽게 만들고, 다른 데이터 원본에 연결할 수도 있습니다.

이 항목의 단계를 수행하기 위해 사용자 지정 작동 방식을 볼 수 있도록 간단한 목록을 만든 다음, 고유한 목록에 동일한 개념을 적용할 수 있습니다.

> [!NOTE]
> - **양식 사용자 지정** 옵션을 사용할 수 없거나 목록에 대해 올바르게 작동 하지 않는 경우 [Power Apps에서 지원 하지](connections/connection-sharepoint-online.md#known-issues)않는 데이터 형식을 포함할 수 있습니다. 다른 목록 또는 [환경](working-with-environments.md)으로 양식을 전환할 수도 없습니다. 
> - 목록의 사용자 지정 양식은 제네릭 목록 에서만 지원 됩니다. 일반 문서 라이브러리에 대 한 지원이 곧 제공 될 예정입니다. 사용자 지정 목록 및 라이브러리 템플릿은 현재 지원 되지 않습니다. 알림, 연락처, 작업 등의 목록에 포함 되지만이에 국한 되지 않습니다.

## <a name="create-a-list"></a>목록 만들기

SharePoint 사이트에서 목록을 만든 다음 이러한 열을 해당 목록에 추가 합니다.

- **세부 정보**(예/아니요)
- **가격**(통화)
- **가용성**(시간 없는 날짜)
- **색**(선택)

> [!div class="mx-imgBorder"]
> 사이트 콘텐츠 > 새 > 목록 ![선택 하 고 목록 이름을 입력 한 다음 만들기를 선택 합니다. 각 열에 대해 열 추가를 선택 하 고 목록 유형 (예/아니요, 통화, 날짜, 선택)을 지정한 다음 목록 이름 (세부 정보, 가격, 사용 가능, 색)을 지정 하 고 저장을 선택 합니다.](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>양식 열기

1. 명령 모음에서 **PowerApps**를 선택 하 고 **양식 사용자 지정**을 선택 합니다.

    Power Apps 스튜디오는 동일한 브라우저 탭에서 열립니다.

1. **Power Apps 스튜디오 시작** 대화 상자가 열리면 **건너뛰기**를 선택 합니다.

> [!div class="mx-imgBorder"]
> 명령 모음에서 ![Power Apps를 선택 하 고 양식 사용자 지정을 선택 합니다. Power Apps 스튜디오는 동일한 브라우저 탭에서 열립니다. Power Apps 스튜디오 시작 대화 상자가 열리면 건너뛰기를 선택 합니다.](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>필드 이동 및 제거

1. **Availability** 필드를 필드 목록의 아래쪽으로 끕니다.

    필드는 지정 된 순서 대로 표시 됩니다.

1. **첨부 파일** 필드를 마우스로 가리키고, 표시 되는 줄임표 (...)를 선택한 다음, **제거**를 선택 합니다.

    지정한 필드가 폼에서 사라집니다.

> [!div class="mx-imgBorder"]
> Availability 필드를 필드 목록의 맨 아래로 끌어 ![합니다. 첨부 파일 필드를 마우스로 가리키고, 표시 되는 줄임표 (...)를 선택한 다음, 제거를 선택 합니다.](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>조건부 서식 지정 설정

**세부 정보**가 예로 설정되는 경우에만 **가격**, **가용성** 및 **색** 필드가 사라지도록 구성할 수 있습니다.

1. 왼쪽 탐색 모음에서 **Details_DataCard1**를 확장 하 고 **DataCardValue**의 끝에 표시 되는 숫자를 확인 합니다.

1. **Color**, **Availability**및 **Price** 카드의 **Visible** 속성을이 수식으로 설정 합니다. 필요한 경우 이전 단계에서 적어둔 숫자로 바꿉니다.

    **If (DataCardValue2 = true, true)**

1. Alt 키를 누른 채 **세부 정보** 설정/해제를 여러 번 클릭하거나 눌러서 선택합니다.

    구성한 세 개의 필드가 표시되고 양식에서 사라집니다.

> [!div class="mx-imgBorder"]
> ![왼쪽 탐색 모음에서 DataCardValue의 끝에 표시 되는 숫자를 확인 합니다. 색, 가용성 및 가격 카드의 Visibility 속성을이 수식으로 설정 합니다. Alt 키를 누른 상태에서 세부 정보 컨트롤을 여러 번 선택 합니다.](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>양식을 저장 하 고 게시 합니다.

1. **파일** 메뉴를 열고 **저장**을 선택한 다음, **SharePoint에 게시**를 두 번 선택합니다.

1. 왼쪽 위 모퉁이에서 뒤로 화살표를 선택한 다음, **SharePoint로 돌아가기**를 선택합니다.

> [!div class="mx-imgBorder"]
> 파일 메뉴를 열고 저장을 선택한 다음 SharePoint에 게시를 두 번 선택 합니다. ![ 왼쪽 위 모서리에서 뒤로 화살표를 선택 하 고 SharePoint로 돌아가기를 선택 합니다.](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>양식 사용자 지정

1. 목록을 열고 명령 모음에서 **새로 만들기** 를 선택한 후 폼의 위쪽 근처에서 **사용자 지정** 을 선택 합니다.

1. 이러한 항목에서 설명 하는 것과 같은 다양 한 방법으로 양식을 사용자 지정 합니다.

    - 크기, 방향 또는 둘 다를 변경합니다(예: [양식 넓히기](set-aspect-ratio-portrait-landscape.md)).
    - [하나 이상의 카드를 사용자 지정](working-with-cards.md) 합니다 (예: 카드의 표시 텍스트 또는 입력 컨트롤 변경).
    - [조회 필드](sharepoint-lookup-fields.md)를 만듭니다.

    추가 정보: [SharePoint 양식 통합 이해](sharepoint-form-integration.md)

## <a name="use-the-default-form"></a>기본 양식 사용

1. SharePoint 목록에서 오른쪽 위 모서리 근처의 기어 아이콘을 선택하여 설정 페이지를 연 다음, **설정 나열**을 선택합니다.

2. **일반 설정** 아래에서 **양식 설정**을 선택합니다.

3. **양식 설정** 페이지에서 이 옵션 중 하나를 선택한 다음, **확인**을 선택합니다.

    - **기본 SharePoint 양식 사용** - 사용자가 목록을 열고 명령 모음에서 **새로 만들기**를 선택할 때 목록에 대한 기본 양식이 표시됩니다.

    - **PowerApps에서 만든 사용자 지정 양식 사용** - 사용자가 목록을 열고 명령 모음에서 **새로 만들기**를 선택할 때 사용자 지정 양식이 표시됩니다. (대안으로 PowerApps에서 양식을 다시 게시할 수 있습니다.)

    필요에 따라 옵션을 앞뒤로 전환할 수 있습니다.

    ![양식 설정 옵션](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>사용자 지정 양식 삭제

1. SharePoint 목록에서 오른쪽 위 모서리 근처의 기어 아이콘을 선택하여 설정 페이지를 연 다음, **설정 나열**을 선택합니다.

1. **일반 설정** 아래에서 **양식 설정**을 선택합니다.

1. **양식 설정** 페이지에서 **기본 SharePoint 양식 사용**을 선택한 다음, **사용자 지정 양식 삭제**를 선택합니다.

    ![사용자 지정 양식 삭제](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>Q & A

### <a name="forms-vs-apps"></a>양식 및 앱

**Q:** 사용자 지정 된 양식은 SharePoint 또는 Power Apps에서 만든 독립 실행형 앱과 어떻게 다릅니까?

**A:** SharePoint 목록에 대해 양식을 사용자 지정 하는 경우 양식은 Power Apps 스튜디오 또는 Power Apps Mobile에서 앱으로 표시 되지 않습니다. 양식을 만든 목록에서만 해당 양식을 열 수 있습니다.

**Q:** 언제 양식을 사용자 지정하여 SharePoint 목록에서 데이터를 관리하고 독립 실행형 앱을 만들어야 하나요?

**A:** 예를 들어 사용자가 데스크톱 브라우저에서 SharePoint를 종료하지 않고 데이터를 관리하는 경우 양식을 사용자 지정합니다. 예를 들어 사용자가 모바일 디바이스에서 SharePoint 외부의 데이터를 관리하려는 경우 앱을 만듭니다.

**Q:** 동일한 목록에 대해 양식을 사용자 지정하고 앱을 만들 수 있나요?

**A:** 예.

**Q:** 동일한 기능을 사용하여 목록을 사용자 지정하고 앱을 만들 수 있나요?

**A:** 예.

**Q:** 내 조직의 기본 환경 이외의 환경에서 양식을 사용자 지정할 수 있나요?

**A:** 아니요.

### <a name="manage-your-custom-form"></a>사용자 지정 양식 관리

**Q:** 다른 사용자와 내 양식을 쉽게 공유하려면 어떻게 할까요?

**A:** 양식을 열고 **링크 복사**를 선택한 다음 양식을 사용 하려는 모든 사용자에 게 링크를 보냅니다.

**Q:** 내 변경 사항을 다른 사용자에게 보여주지 않고 내 양식을 업데이트할 수 있나요?

**A:** 예. 원하는 만큼 양식을 변경하고 저장할 수 있지만 **SharePoint에 게시**를 두 번 선택하지 않으면 변경 내용이 다른 사용자에게 보이지 않습니다.

**Q:** 목록 양식을 사용자 지정하다가 실수를 하면 이전 버전으로 되돌릴 수 있나요?

**A:** 예.

1. 목록을 열고, 명령 모음에서 **PowerApps**를 선택한 다음, **양식 사용자 지정**을 선택합니다.

1. Power Apps Studio에서 **파일**을 선택한 다음 **모든 버전 보기**를 선택 합니다. **버전** 페이지가 새 브라우저 탭에 열립니다.

    > [!NOTE]
    > **모든 버전 보기** 단추가 표시되지 않으면 **저장**을 선택합니다. 그러면 단추가 표시됩니다.

1. **버전** 페이지나 브라우저 탭을 닫지 않고 다른 브라우저 탭의 **저장** 페이지로 돌아가서 왼쪽 탐색 창의 맨 위에 있는 화살표를 클릭 하거나 탭 한 다음, **SharePoint로 돌아가기** 를 클릭 하거나 탭 하 여 양식의 잠금을 해제 하 고 Power Apps Studio를 닫습니다.

1. 다른 브라우저 탭의 **버전** 페이지로 돌아가서 복원할 버전을 찾은 다음, **복원**을 선택합니다.

    > [!NOTE]
    > 다른 사용자가 양식을 잠갔기 때문에 복원이 실패 했다는 오류 메시지가 표시 되 면 사용자가 양식의 잠금을 해제할 때까지 기다린 후 다시 시도 합니다.

**Q:** 내 양식을 한 목록에서 다른 목록으로 이동할 수 있나요?

**A:** 아니요.

### <a name="administer-your-custom-form"></a>사용자 지정 양식 관리

**Q:** 내 양식을 공유하려면 어떻게 할까요?

**A:** 양식을 공유할 필요가 없습니다. 양식은 SharePoint 목록에서 사용 권한을 상속 합니다. 사용자 지정을 완료한 후 [SharePoint에 다시 게시](customize-list-form.md#save-and-publish-the-form)만 하면 다른 사람이 사용할 수 있습니다.

**Q:** 누가 양식을 사용자 지정할 수 있나요?

**A:** 연결된 목록을 관리, 디자인 또는 편집할 수 있는 SharePoint 권한을 가진 사람이면 가능합니다.

**Q:** 사용자 지정 목록 양식을 만들거나 사용 하려면 Power Apps 라이선스가 필요 한가요?

**A:** [PowerApps가 포함된 Office 365 계획](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses)이 필요합니다.

**Q:** 게스트 사용자가 사용자 지정 양식이 있는 목록에 액세스하면 어떻게 되나요?

**A:** PowerApps를 사용하여 사용자 지정된 목록 양식에 게스트 사용자가 액세스하려고 하면 오류 메시지가 표시됩니다.

**Q:** 관리자가 조직의 모든 사용자 지정 양식 목록을 얻으려면 어떻게 해야 하나요?

**A:** Power Apps에 대 한 테 넌 트 관리자 이거나 조직의 기본 Power Apps 환경에서 환경-관리자 권한이 있는 경우 다음을 수행 합니다.

1. [Power Apps 관리 센터](https://admin.powerapps.com)의 환경 목록에서 조직의 기본 환경을 선택 합니다.

1. 기본 환경 페이지의 맨 위에서 **리소스**를 선택합니다.

1. 앱 목록에서 **SharePoint 양식** 앱 유형으로 앱을 찾습니다. 사용자 지정 된 양식입니다.

    ![사용자 지정된 양식 목록](./media/customize-list-form/all-customized-forms.png)
