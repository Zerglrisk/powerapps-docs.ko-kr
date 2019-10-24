---
title: Canvas 앱에서 종속 드롭다운 목록 만들기 | Microsoft Docs
description: PowerApps에서 캔버스 앱의 다른 드롭다운 목록을 필터링 하는 드롭다운 목록을 만듭니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57abde44541a2a1e40e3a8ffc55a89e37a8c6478
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "71985743"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>캔버스 앱에서 종속 된 드롭다운 목록 만들기

종속 (또는 계단식) 드롭다운 목록을 만들 때 사용자는 목록에서 옵션을 선택 하 여 다른 목록에서 옵션을 필터링 합니다. 많은 조직에서 사용자가 양식을 더 효율적으로 채울 수 있도록 종속 목록을 만듭니다. 예를 들어 사용자가 도시 목록을 필터링 할 국가 또는 지역을 선택 하거나, 사용자가 범주를 선택 하 여 해당 범주의 코드만 표시할 수 있습니다.

사용자가 앱을 사용 하 여 업데이트 하는 데이터 원본과 별개의 "부모" 및 "자식" 목록 (예: 국가/지역 및 도시)의 값에 대 한 데이터 원본을 만드는 것이 가장 좋습니다. 이 방법을 사용 하는 경우 두 개 이상의 앱에서 동일한 부모 및 자식 데이터를 사용할 수 있으며 해당 데이터를 사용 하는 앱 또는 앱을 다시 게시 하지 않고도 해당 데이터를 업데이트할 수 있습니다. 컬렉션 또는 정적 데이터를 사용 하 여 동일한 결과를 얻을 수 있지만 엔터프라이즈 시나리오에는 권장 되지 않습니다.

이 항목의 시나리오에서 직원은 양식을 통해 **인시던트** 목록에 문제를 제출 합니다. 직원은 인시던트가 발생 한 저장소 위치 뿐만 아니라 해당 위치 내의 부서도 지정 합니다. 모든 위치에 동일한 부서가 있는 것은 아니므로 **위치** 목록을 사용 하면 직원이 해당 부서가 없는 위치의 부서를 지정할 수 없습니다.

이 항목에서는 Microsoft SharePoint 목록을 데이터 원본으로 사용 하지만 모든 테이블 형식 데이터 원본은 동일한 방식으로 작동 합니다.

## <a name="create-data-sources"></a>데이터 원본 만들기

**위치** 목록은 각 위치의 부서를 표시 합니다.

| 위치 | Department |
|----------------|------------------|
| Eganville      | 빵집           |
| Eganville      | Deli             |
| Eganville      | 생성할          |
| 가는 frew        | 빵집           |
| 가는 frew        | Deli             |
| 가는 frew        | 생성할          |
| 가는 frew        | Pharmacy         |
| 가는 frew        | 흰꽃잎색           |
| Pembroke       | 빵집           |
| Pembroke       | Deli             |
| Pembroke       | 생성할          |
| Pembroke       | 흰꽃잎색           |

**인시던트** 목록에는 각 인시던트에 대 한 연락처 정보 및 정보가 표시 됩니다. 날짜 열을 **날짜** 열로 만들지만 다른 열을 **한 줄의 텍스트** 열로 만들어 구성을 단순화 하 고 Microsoft PowerApps에서 [위임](./delegation-overview.md) 경고를 방지 합니다.

| 이름 | 성 | 전화 번호     | 위치 | Department | 설명       | 날짜      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555-1022 | Eganville      | 생성할    | 다음에 문제가 있습니다.   | 2/12/2019 |
| 프로그램인 moses     | Laflamme     | (425) 555-1044 | 가는 frew        | 흰꽃잎색     | 문제가 발생 했습니다. | 2/13/2019 |

기본적으로 사용자 지정 SharePoint 목록에는 이름을 바꾸거나 제거할 수 없는 **제목** 열이 포함 되며, 항목을 목록에 저장 하려면 먼저 데이터를 포함 해야 합니다. 데이터를 요구 하지 않도록 열을 구성 하려면 다음을 수행 합니다.

1. 오른쪽 위 모서리 근처에서 기어 아이콘을 선택 하 고 **목록 설정**을 선택 합니다.
1. **설정** 페이지의 열 목록에서 **제목** 을 선택 합니다.
1. **이 열에 정보가 포함 되어 있어야**함에서 **아니요**를 선택 합니다.

이렇게 변경한 후에는 **제목** 열을 무시 하거나, 하나 이상의 다른 열이 표시 되는 경우 기본 보기에서 [제거할](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) 수 있습니다.

## <a name="open-the-form"></a>양식 열기

1. **인시던트** 목록을 열고 **PowerApps**  > **양식 사용자 지정**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![인시던트 목록을 열고 PowerApps > 양식 사용자 지정을 선택 합니다.](./media/dependent-drop-down-lists/open-form.png "인시던트 목록을 열고 PowerApps > 양식 사용자 지정을 선택 합니다.")

    PowerApps Studio의 기본 양식이 포함 된 브라우저 탭이 열립니다.

1. 필드 **필드** 창에서 **제목** 필드를 마우스로 가리키고 표시 되는 줄임표 (...)를 선택한 다음 **제거**를 선택 합니다.

    **필드** 창을 닫은 경우 왼쪽 탐색 모음에서 **SharePointForm1** 을 선택 하 고 오른쪽 창의 **속성** 탭에서 **필드 편집** 을 선택 하 여 다시 열 수 있습니다.

1. 필드 이전 단계를 반복 하 여 양식에서 **첨부 파일** 필드를 제거 합니다.

    추가한 필드만 포함 된 양식이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 제목 및 첨부 파일 필드가 없는 ![Form ](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>컨트롤 바꾸기

1. **필드** 창에서 **위치**옆의 화살표를 선택 합니다.

    **필드** 창을 닫은 경우 왼쪽 탐색 모음에서 **SharePointForm1** 을 선택 하 고 오른쪽 창의 **속성** 탭에서 **필드 편집** 을 선택 하 여 다시 열 수 있습니다.

1. **컨트롤 형식** 목록을 열고 **허용 된 값**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Allowed 값 ](./media/dependent-drop-down-lists/change-control.png)

    입력 메커니즘이 **드롭다운** 컨트롤로 변경 됩니다.

1. **부서** 카드에 대해이 단계를 반복 합니다.

## <a name="add-the-locations-list"></a>위치 목록 추가

1. 데이터**원본 추가** >   > **데이터** 원본 **보기** 를 선택 합니다.

1. SharePoint 연결을 선택 하거나 만든 다음 **위치** 목록이 포함 된 사이트를 지정 합니다.

1. 해당 목록에 대 한 확인란을 선택 하 고 **연결**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Data 창 ](./media/dependent-drop-down-lists/select-list.png)

    연결 목록에는 양식의 기반이 되는 **인시던트** 목록과 양식에서 위치 및 부서를 식별 하는 **위치** 목록이 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > 데이터 원본 ![SharePoint ](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>카드 잠금 해제

1. **위치** 카드를 선택 하 고 오른쪽 창에서 **고급** 탭을 선택한 다음 **잠금 해제를 선택 하 여 속성을 변경**합니다.

1. **부서** 카드에 대해 이전 단계를 반복 합니다.

## <a name="rename-the-controls"></a>컨트롤 이름 바꾸기

컨트롤의 이름을 바꾸는 경우 더 쉽게 식별할 수 있으며 예제는 더 쉽게 수행할 수 있습니다. 다른 모범 사례를 검색 하려면 [코딩 표준 및 지침 백서](https://aka.ms/powerappscanvasguidelines)를 검토 합니다.

1. **위치** 카드에서 **드롭다운** 컨트롤을 선택 합니다.

1. 오른쪽 창의 위쪽에서 **Ddlocation**을 입력 하거나 붙여넣어 선택한 컨트롤의 이름을 바꿉니다.

    > [!div class="mx-imgBorder"]
    > 컨트롤 ](./media/dependent-drop-down-lists/rename-control.png) ![Rename

1. **부서** 카드의 이전 두 단계를 반복 하 여 **드롭다운** 컨트롤의 이름을 **dddepartment**로 바꿉니다.

## <a name="configure-the-locations"></a>위치 구성

1. **Ddlocation** 의 **Items** 속성을 다음 수식으로 설정 합니다.

    `Distinct(Locations, Location)`

1. 필드 Alt 키를 누른 상태에서 **Ddlocation**을 열고 목록에 세 위치가 표시 되는지 확인 합니다.

## <a name="configure-the-departments"></a>부서 구성

1. **Dddepartment**를 선택 하 고 오른쪽 창의 **속성** 탭에서 종속을 선택 **합니다.**

1. **부모 컨트롤**에서 **ddlocation** 이 위쪽 목록에 표시 되 고 **결과가** 아래쪽 목록에 표시 되는지 확인 합니다.

    > [!NOTE]
    > 문자열에서 일치 시 키 지 않고 데이터 행의 실제 ID를 일치 시 키 지 않으려면 **결과**대신 **id** 를 선택 합니다.

1. **일치 필드**의 위쪽 목록 **에서 위치를 선택 하** 고, 아래쪽 목록에서 **위치** 를 선택한 다음, **적용**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 링크 ](./media/dependent-drop-down-lists/depends-on.png) ![Depends

    **Dddepartment** 의 **Items** 속성은 다음 수식으로 설정 됩니다.

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    이 수식은 사용자가 **Dddepartment**에서 선택 하는 항목에 따라 **dddepartment** 의 항목을 필터링 합니다. 이러한 구성은 SharePoint의 **위치** 목록에서 지정 하는 대로 "자식" 부서의 데이터를 "부모" 위치의 데이터를 반영 하도록 합니다.

1. 오른쪽 창의 **속성** 탭에서 **값**옆에 있는 목록을 열고 **부서**를 선택 합니다.

    이 단계에서는 표시 텍스트를 SharePoint의 **위치** 목록에 있는 **부서** 열의 옵션으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > ![Department 값 ](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>양식 테스트

Alt 키를 누른 채 위치 목록을 열고, 위치를 하나 선택 하 고, 부서 목록을 연 다음, 하나를 선택 합니다.

위치 및 부서 목록은 SharePoint의 **위치** 목록에 있는 정보를 반영 합니다.

> [!div class="mx-imgBorder"]
> 위치 목록을 ![Open 하 고, 선택 항목을 다시 시도 하는 것에서 Pembroke으로 변경 하 고 부서 목록을 엽니다 ](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>양식을 저장 하 고 엽니다 (선택 사항).

1. **파일** 메뉴를 연 다음 **저장**  > **sharepoint에 게시**  > **sharepoint에**게시를 선택 합니다.

1. 왼쪽 위 모퉁이에서 뒤로 화살표를 선택한 다음, **SharePoint로 돌아가기**를 선택합니다.

1. 명령 모음에서 **새로 만들기**를 선택하여 사용자 지정된 양식을 엽니다.

## <a name="faq"></a>자주 묻는 질문(FAQ)

**데이터를 볼 수 없습니다. 원본이 모두 비어 있거나 잘못 된 데이터를 포함 합니다.**
다음 중 한 가지 방법으로 컨트롤에 대 한 올바른 필드를 표시 하는지 확인 합니다.

- 드롭다운 목록을 선택 하 고 오른쪽 창의 **속성** 탭에서 **값** 속성을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 드롭다운 ](./media/dependent-drop-down-lists/drop-down-display-field.png)

- 콤보 상자를 선택 하 고 기본 텍스트가 표시 하려는 필드 인지 확인 합니다.

    > [!div class="mx-imgBorder"]
    > ![Change 콤보 상자 ](./media/dependent-drop-down-lists/combo-box-display-field.png)

**내 자식 드롭다운 목록에 중복 된 항목이 있습니다.**
이 증상은 SharePoint에서 **조회** 열을 사용 하거나 PowerApps에서 **choice** 함수를 사용 하기 때문에 발생할 수 있습니다. 중복을 제거 하려면 적절 하 게 반환 되는 데이터를 중심으로 **고유한** 함수를 래핑합니다. 추가 정보: [Distinct 함수](functions/function-distinct.md)

## <a name="known-limitations"></a>알려진 제한 사항

이 구성은 **드롭다운** 컨트롤 뿐만 아니라 한 번에 하나의 선택을 허용 하는 **콤보 상자** 및 **목록 상자** 컨트롤에서 사용할 수 있습니다. 여러 항목을 선택할 수 있는 경우는 해당 컨트롤의 구성 **에 따라 달라 집니다** . Common Data Service에서 옵션 집합을 사용 하는 경우에는이 방법을 사용 하지 않는 것이 좋습니다.

구성 **에 종속** 은 정적 데이터 또는 컬렉션을 지원 하지 않습니다. 이러한 원본으로 종속 된 드롭다운 목록을 구성 하려면 수식 입력줄에서 직접 식을 편집 합니다. 또한 PowerApps는 일치 하는 데이터 테이블이 없는 SharePoint의 선택 필드 두 개를 사용 하는 것을 지원 하지 않으며이 UI 내에서 **일치 하는 필드** 를 정의할 수 없습니다.
