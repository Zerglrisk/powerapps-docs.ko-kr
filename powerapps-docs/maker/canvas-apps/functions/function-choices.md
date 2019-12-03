---
title: Choices 함수 | Microsoft Docs
description: Power Apps의 선택 기능에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2ebe6b2019652b1f2e59419c718136aced81c62e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731400"
---
# <a name="choices-function-in-power-apps"></a>Power Apps의 선택 기능
조회 열에 대해 가능한 값의 테이블을 반환합니다.

## <a name="description"></a>설명
**Choices** 함수는 조회 열에 대해 가능한 값의 테이블을 반환합니다.  

**Choices** 함수를 사용하여 사용자에게 선택할 목록을 제공합니다. 이 함수는 일반적으로 편집 양식에서 [**콤보 상자**](../controls/control-combo-box.md) 컨트롤과 함께 사용됩니다.

조회의 경우 **Choices**에서 반환한 테이블은 조회와 연결된 외래 테이블과 일치합니다. **Choices**를 사용하여 추가 데이터 원본으로 외래 테이블을 추가할 필요가 없습니다. **Choices**에서는 외래 테이블의 모든 열을 반환합니다.

**Choices**에서 테이블을 반환하기 때문에 [**Filter**](function-filter-lookup.md), [**Sort**](function-sort.md), [**AddColumns**](function-table-shaping.md) 및 모든 다른 테이블 조작 함수를 사용하여 테이블을 필터링하고, 정렬하고, 셰이핑할 수 있습니다. 

이 경우에 **Choices**를 [위임](../delegation-overview.md)할 수 없습니다. 이 제한으로 인해 앱에서 문제가 발생하는 경우 데이터 원본으로 외부 엔터티를 추가하고 직접 사용합니다. 

**Choices**에서는 [**ShowColumns**](function-table-shaping.md), [**Search**](function-filter-lookup.md) 및 기타 테이블 함수와 달리 열 이름이 문자열과 큰따옴표에 포함되지 않아도 됩니다. 해당 열을 직접 참조하는 것처럼 수식을 제공합니다.

열 참조는 데이터 원본에 직접 전송되어야 합니다. 예를 들어 데이터 원본이 **Accounts**이고 조회가 **SLA**인 경우 열 참조는 **Accounts.SLA**입니다. 참조는 함수, 변수 또는 컨트롤을 통해 전달할 수 없습니다. 이 예제에서는 앞으로 **계정**이 **갤러리** 컨트롤에 공급되는 경우 **Gallery.Selected.SLA** 수식을 사용하여 선택한 계정의 SLA를 참조합니다. 그러나 이 참조는 컨트롤을 통해 전달했으므로 **Columns** 함수에 전달될 수 없습니다. **Accounts.SLA**를 반드시 사용해야 합니다.

지금은 SharePoint 및 Common Data Service에만 조회 열을 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Choices**(*column-reference*)

* *column-reference* – 필수입니다.  데이터 원본의 조회 열입니다. 열 이름을 큰따옴표로 묶지 마십시오. 참조는 데이터 원본의 열에 직접 전달되며 함수 또는 컨트롤을 통해 전달되지 않아야 합니다.

## <a name="examples"></a>예

#### <a name="choices-for-a-lookup"></a>조회에 대한 Choices

1. Common Data Service에서 [데이터베이스를 만들고](../../../administrator/create-database.md) **샘플 앱 및 데이터 포함** 상자를 선택 합니다.

    **계정**과 같은 여러 엔터티가 생성됩니다.

    **참고**: 엔터티 이름은 Power Apps 스튜디오에서 make.powerapps.com 및 plural의 단일 항목입니다.

    ![앱에 대 한 Common Data Service 계정 엔터티의 필드 목록 중 일부는 "기본 연락처"가 조회 필드 임을 강조 표시 합니다.](media/function-choices/entity-account.png)

    **계정** 엔터티에는 **기본 연락처** 열이 있고 해당 열은 **연락처** 엔터티에 대한 조회입니다.  

    ![Common Data Service에서 Contact 엔터티의 필드 목록 중 일부입니다.](media/function-choices/entity-contact.png)

    각 계정의 경우 연락처가 기본 연락처로 지정되거나 기본 연락처가 *비어* 있습니다.

1. **계정** 엔터티에서 [앱 생성](../data-platform-create-app.md)

1. 왼쪽 모서리 근처의 화면 및 컨트롤 목록에서 **EditScreen1**이 나타날 때까지 아래로 스크롤한 다음, 바로 아래에서 **EditForm1**을 선택합니다.

    ![왼쪽 탐색 모음에서 EditScreen1의 EditForm1을 선택합니다.](media/function-choices/select-editform.png)

1. 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택 합니다.

    ![데이터 창 열기](media/function-choices/open-data-pane.png)

1. **필드** 창에서 **필드 추가**를 선택 합니다.

1. **기본 연락처** 필드를 검색 하 고 해당 확인란을 선택한 다음 **추가**를 선택 합니다.

    ![계정을 선택하여 데이터 창을 엽니다.](media/function-choices/field-list.png)

    **기본 연락처** 필드가 폼의 아래쪽에 표시 됩니다. 필드에 오류가 표시 되는 경우 **보기** 탭에서 **데이터 원본** 을 선택 하 고 **계정** 데이터 원본에 대 한 줄임표 (...)를 선택한 다음 **새로 고침**을 선택 합니다.

1. (선택 사항) 필드 목록의 맨 아래에서 위로 **기본 연락처** 필드를 끌어옵니다.

1. **기본 연락처**의 카드에서 **콤보 상자** 컨트롤을 선택합니다.

    해당 컨트롤의 **Items** 속성은 첫 번째 예제와 같이 표시 이름 또는 해당 논리적 이름을 기준으로 열을 식별 하는 수식으로 설정 됩니다.

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![양식 컨트롤을 사용하는 캔버스 화면입니다. 기본 연락처 카드 내의 콤보 상자 컨트롤이 선택 되 고 항목 속성 (계정. ' 기본 연락처 ')이 표시 됩니다.](media/function-choices/accounts-primary-contact.png)

1. **홈** 탭에서 **새 화면**을 선택한 다음, **비어 있음**을 선택합니다.

1. **삽입** 탭에서 **데이터 테이블**을 선택합니다.

1. **데이터 테이블** 컨트롤의 **Items** 속성을 다음 수식으로 설정 합니다.

     **Choices( Accounts.'Primary Contact' )**

1. **데이터 테이블** 컨트롤 가운데에서 **필드 ...** 를 선택 하는 링크를 선택 하 고 표시 하려는 필드 (예: **firstname** 및 **lastname**)의 확인란을 선택 합니다.

     ![데이터 테이블 컨트롤을 사용하는 캔버스 화면입니다. Items 속성이 Choices( Accounts.'Primary Contact' ) 수식으로 설정되면 테이블에서는 연락처 엔터티의 첫 번째 집합 레코드에 대한 firstname 및 lastname 열을 보여줍니다.](media/function-choices/full-accounts-pc.png)