---
title: 캔버스 앱에서 종속 드롭 다운 목록 만들기 | Microsoft Docs
description: PowerApps에서 캔버스 앱에서 다른 드롭다운 목록을 필터링 하는 드롭다운 목록을 만듭니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dc1b3b87e2c1fdcd4ab7eb6634db7f9e7c049ec2
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550787"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>캔버스 앱에서 종속 드롭 다운 목록 만들기

종속 (또는 연속) 드롭 다운 목록을 만들면 사용자는 다른 목록의 옵션을 필터하기 위해 목록의 옵션을 선택합니다. 대부분의 조직에서는 사용자들이 더 효율적으로 폼을 작성할 수 있도록 하기 위해 종속 목록을 만듭니다. 예를 들어, 사용자는 도시 목록을 필터링할 국가 또는 지역을 선택할 수 있으며 또는 해당 범주의 코드만 표시하도록 범주를 선택할 수 있습니다.

모범 사례로, 사용자가 앱을 사용하여 업데이트하는 데이터 원본과는 별개의 "부모" 및 "자식" 목록(예: 국가/지역 및 도시) 값에 대한 데이터 원본을 만듭니다. 이 방법을 사용하는 경우 둘 이상의 앱에서 동일한 부모 및 자식 데이터를 사용할 수 있으며, 해당 데이터를 사용하는 앱을 다시 게시하지 않고도 해당 데이터를 업데이트할 수 있습니다. 컬렉션 또는 정적 데이터를 사용하여 동일한 결과를 얻을 수 있지만 이는 엔터프라이즈 시나리오에 권장되지 않습니다.

이 항목의 시나리오의 경우, 매장 직원은 폼을 통해 이슈를 **Incidents** 목록에 제출합니다. 인시던트가 발생한 매장의 위치를 지정하는 것 뿐만 아니라 해당 위치 내의 부서도 지정합니다. 모든 위치에 동일한 부서가 있지는 않으므로, **Locations** 목록은 직원이 부서가 없는 위치에 대해 부서를 지정할 수 없도록 합니다.

이 항목에서는 Microsoft SharePoint 목록을 데이터 원본으로 사용하지만 모든 테이블 형식 데이터 원본은 동일한 방식으로 작동합니다.

## <a name="create-data-sources"></a>데이터 원본 만들기

**Locations** 목록에서는 각 위치의 부서를 보여줍니다.

| Location | Department |
|----------------|------------------|
| Eganville      | 빵집           |
| Eganville      | 배달             |
| Eganville      | 생성          |
| Renfrew        | 빵집           |
| Renfrew        | 배달             |
| Renfrew        | 생성          |
| Renfrew        | 약국         |
| Renfrew        | 꽃           |
| Pembroke       | 빵집           |
| Pembroke       | 배달             |
| Pembroke       | 생성          |
| Pembroke       | 꽃           |

**Incidents** 목록은 연락처 정보 및 각 인시던트에 대한 정보를 보여줍니다. 날짜 열로 **Date** 열을 생성하지만, Microsoft PowerApps에서 [위임](./delegation-overview.md) 경고를 방지하고 구성을 단순화하기 위해 **한 줄 텍스트**로 다른 열을 생성합니다.

| First Name | Last Name | Phone Number     | Location | Department | Description       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555 - 1022 | Eganville      | 생성    | 문제가 있습니다...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555 - 1044 | Renfrew        | 꽃     | 문제를 경험 했습니다... | 2/13/2019 |

기본적으로 사용자 지정 SharePoint 목록에 포함된 **제목** 열 이름을 바꾸거나 제거할 수 없습니다. 그리고 목록에서 항목을 저장하기 전에 데이터가 포함되어야 합니다. 데이터가 필요하지 않도록 열을 구성하려면 다음을 수행합니다.

1. 오른쪽 위 모서리에서 기어 아이콘을 선택하고, **목록 설정**을 선택합니다.
1. **설정** 페이지에서 열 목록 중 **제목** 열을 선택합니다.
1. **필수 열로 지정**에서 **아니요**를 선택합니다.

변경 후, **제목 열**을 무시하거나 기본 보기에 다른 열이 하나 이상 있다면 기본 보기에서 [제거](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8)할 수도 있습니다.

## <a name="open-the-form"></a>폼 열기

1. **Incidents** 목록을 열고, **PowerApps** > **양식 사용자 지정**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![인시던트 목록 열기를 선택한 다음 PowerApps > 양식 사용자 지정 합니다. ](./media/dependent-drop-down-lists/open-form.png "인시던트 목록 열기를 선택한 다음 PowerApps > 양식 사용자 지정 합니다.")

    PowerApps Studio 기본 양식을 사용 하 여 브라우저 탭이 열립니다.

1. (선택 사항) **필드** 창에서 **제목** 필드 위로 마우스를 가져가고, 줄임표(...)를 선택한 다음 **제거**를 선택합니다.

    **필드** 창을 닫은 경우, 왼쪽 탐색 모음에서 **SharePointForm1**을 선택한 다음, 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택하여 다시 열 수 있습니다.

1. (선택 사항) 이전 단계를 반복하여 폼에서 **첨부 파일** 필드를 제거합니다.

    추가한 필드만 폼에 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![제목 및 첨부 파일 필드가 없는 형성](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>컨트롤 바꾸기

1. **필드** 창에서, **Location** 옆의 화살표를 선택합니다.

    **필드** 창을 닫은 경우, 왼쪽 탐색 모음에서 **SharePointForm1**을 선택한 다음, 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택하여 다시 열 수 있습니다.

1. **컨트롤 형식** 목록을 열어 **허용되는 값**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![허용 되는 값](./media/dependent-drop-down-lists/change-control.png)

    입력 메커니즘이 **드롭다운** 컨트롤로 변경됩니다.

1. **부서** 카드에 이러한 단계를 반복합니다.

## <a name="add-the-locations-list"></a>위치 목록에 추가

1. **보기** > **데이터 원본** > **데이터 원본 추가**를 선택합니다.

1. SharePoint 연결을 만들거나 선택한 다음 **Locations** 목록이 포함된 사이트를 지정합니다.

1. 목록에 대한 확인란을 선택하고 **연결**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![데이터 창](./media/dependent-drop-down-lists/select-list.png)

    연결 목록은 폼의 기반이 되는 **Incidents** 목록과 폼에서 부서와 위치를 식별할 **Locations** 목록을 표시합니다.

    > [!div class="mx-imgBorder"]
    > ![SharePoint 데이터 원본](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>카드 잠금 해제

1. **Location** 카드를 선택합니다. 그리고 오른쪽 창의 **고급** 탭을 선택하고 **속성을 변경하려면 잠금 해제합니다**를 선택합니다.

1. **부서** 카드에 이전 단계를 반복합니다.

## <a name="rename-the-controls"></a>컨트롤 이름 바꾸기

컨트롤의 이름을 바꾸면, 보다 쉽게 식별할 수 있으며 예제를 쉽게 수행할 수 있습니다. 다른 모범 사례를 검색하려면 [코딩 표준 및 지침 백서](https://aka.ms/powerappscanvasguidelines)를 검토합니다.

1. **Location** 카드에서 **드롭다운** 컨트롤을 선택합니다.

1. 오른쪽 창의 위쪽에서, **ddLocation**을 붙여넣거나 입력하여 선택된 컨트롤의 이름을 변경합니다.

    > [!div class="mx-imgBorder"]
    > ![컨트롤 이름 바꾸기](./media/dependent-drop-down-lists/rename-control.png)

1. **드롭다운** 컨트롤의 이름을 **ddDepartment**으로 바꾸기 위해 **부서** 카드의 이전 두 단계를 반복합니다.

## <a name="configure-the-locations"></a>위치 구성

1. **ddlocation**의 **Items** 속성을 다음 수식으로 설정합니다.

    `Distinct(Locations, Location)`

1. (선택 사항) Alt 키를 누른 채 **ddLocation**을 열어서 세 위치가 표시되는지 확인합니다.

## <a name="configure-the-departments"></a>부서 구성

1. **ddDepartment**를 선택한 다음 오른쪽 창 **속성**탭에서 **다음에 종속**을 선택합니다.

1. **부모 컨트롤** 아래, 위쪽 목록에 **ddLocation**이 표시되고 아래 목록에 **결과**가 나타나는지 확인합니다.

    > [!NOTE]
    > 문자열로 매치하는 것을 원하지 않고 데이터 행의 실제 ID와 매치하려는 경우, **결과** 대신 **ID**를 선택합니다.

1. **일치하는 필드** 아래, 위쪽 목록에서 **Locations**를 선택하고 아래 목록에서 **Location**을 선택하고 **적용**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![링크에 따라 달라 집니다.](./media/dependent-drop-down-lists/depends-on.png)

    **ddDepartment**의 **Items** 속성이 다음 수식으로 설정됩니다.

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    이 수식은 사용자가 **ddLocation**을 선택하는 것에 따라 **ddDepartment** 항목을 필터링합니다. 이러한 구성은 "자식" 부서 목록이 SharePoint **Locations** 목록이 지정하는 "부모" 위치에 대한 데이터를 반영하도록 합니다.

1. 오른쪽 창 **속성** 탭에서, **Value** 옆의 목록를 열어 **Department**를 선택합니다.

    이 단계에서는 SharePoint **Locations** 목록의 **Department** 열로부터 옵션에 표시할 텍스트를 설정합니다.

    > [!div class="mx-imgBorder"]
    > ![부서 값](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>폼 테스트

Alt 키를 누른 채로 위치 목록을 열고, 하나를 선택하고 부서 목록을 열고 하나를 선택합니다.

위치와 부서 목록은 SharePoint **Locations** 목록의 정보를 반영합니다.

> [!div class="mx-imgBorder"]
> ![위치 목록, Pembroke,으로 Renfrew에서 선택을 변경를 열고 학부의 목록](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>저장 및 폼 열기(선택 사항)

1. **파일** 메뉴를 열어 **저장** > **SharePoint에 게시** > **SharePoint에 게시**를 선택합니다.

1. 왼쪽 위 모퉁이에서 뒤로 화살표를 선택한 다음, **SharePoint로 돌아가기**를 선택합니다.

1. 명령 모음에서 **새로 만들기**를 선택하여 사용자 지정된 양식을 엽니다.

## <a name="faq"></a>FAQ

**데이터가 보이지 않는 경우: 데이터 원본이 모두 비어있거나 잘못된 데이터입니다.**
아래 방법 중 하나로 컨트롤에 대해 올바른 필드를 표시하는지 여부를 확인합니다.

- 드롭다운 목록을 선택한 다음 오른쪽 창의 **속성** 탭에서 **Value** 속성을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![변경 드롭다운](./media/dependent-drop-down-lists/drop-down-display-field.png)

- 콤보 상자를 선택하고, 기본 텍스트가 표시하려는 필드인지 확인합니다.

    > [!div class="mx-imgBorder"]
    > ![변경 콤보 상자](./media/dependent-drop-down-lists/combo-box-display-field.png)

**자식 드롭다운 목록에서 중복 항목을 포함합니다.**
이 증상은 SharePoint에서 **조회** 열 또는 PowerApps의 **Choices** 함수를 사용하기 때문일 가능성이 큽니다. 중복을 제거하려면, 반환 데이터에 대해 **Distinct** 함수를 래핑합니다. 자세한 정보는 [Distinct 함수](functions/function-distinct.md)를 참조합니다.

## <a name="known-limitations"></a>알려진 제한 사항

이 구성은 **드롭다운** 컨트롤 뿐만 아니라 한 번에 하나의 항목만 선택할 수 있는 **콤보 상자**와 **목록 상자**에도 사용할 수 있습니다. 다중 선택이 허용된다면 이러한 컨트롤에 대해 **다음에 종속** 구성을 사용할 수 없습니다. 이 방법은 Common Data Service의 옵션 집합을 사용하는 작업에는 권장되지 않습니다.

**다음에 종속** 구성은 정적 데이터 또는 컬렉션을 지원하지 않습니다. 종속 드롭다운 목록에서 이러한 소스를 구성하려면 수식 입력줄에서 직접 식을 편집합니다. 또한 PowerApps는 데이터가 일치하는 테이블이 없는 SharePoint의 두 선택 필드를 사용하는 것을 지원하지 않으며 UI에서 **일치하는 필드**를 정의할 수 없습니다.
