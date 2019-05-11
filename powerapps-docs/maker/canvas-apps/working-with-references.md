---
title: 레코드 참조 및 다형 조회 이해 | Microsoft Docs
description: 레코드 참조 및 캔버스 앱에서 다형 조회 작업
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/05/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99024b447841668bd887571a269c2fb14f5f5289
ms.sourcegitcommit: f6c9e525130a03b8c76f0a4b4e90419604c5823c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527092"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>레코드 참조 및 다형 캔버스 앱 조회를 이해 합니다.

학교에서 연구 논문을 작성 하는 경우 아마도 끝에 있는 참조의 목록을 제공 합니다. 누군가가 원본을 추적할 수 있도록 웹 링크를 대신, 책 제목, 작성자 또는 기타 정보 이지만 사용 하 여 실제 배경 자료의 복사본이 포함 되지 않았으면 합니다. 여러 종류의 소스를 단일 목록에서 적절 한 인용에 대 한 고유한 세부 정보와 함께 각 오디오 녹음 옆에 있는 신문 기사를 혼합 하는 경우. 예를 들어 Wikipedia 문서가 포함 종종를 [긴 참조 목록을](https://en.wikipedia.org/wiki/Microsoft#References)합니다.

종종 캔버스 앱에서 데이터 원본에서 다운로드 하는 레코드의 복사본을 사용 하 여 작동 합니다. 사용 된 [ **조회** ](functions/function-filter-lookup.md) 하 고 [ **필터** ](functions/function-filter-lookup.md) 함수 및 [ **갤러리** ](controls/control-gallery.md) 컨트롤의 **선택한** 하려는 특정 레코드를 식별 하는 속성입니다. 모든 레코드가 **필터** 또는 **선택한** 단순 필드를 사용할 수 있도록 동일한 엔터티 형식의 됩니다. *필드* 표기법입니다. 이러한 복사본은 종종 참조 정보를 포함 시켜 서 사용할 수는 [ **패치** ](functions/function-patch.md) 원본 소스를 업데이트 하는 함수입니다.

캔버스 앱도 지원 *레코드 참조*합니다. 훨씬 연구 논문 참조와 같은 레코드 참조는 전체 복사본을 포함 하지 않고에 레코드를 참조 합니다. 모든 엔터티의 레코드 참조를 참조할 수 있습니다.  또한 연구 논문 참조와 같은 단일 열에 서로 다른 엔터티에서 레코드를 혼합할 수 있습니다.

레코드 참조에서 많은 작업 레코드를 사용 하는 것과 동일 합니다. 레코드 참조 전체 레코드를 서로 비교할 수 있습니다. 레코드 참조의 값을 설정할 수 있습니다 합니다 **패치** 전체 레코드를 사용 하 여 조회 처럼 작동 합니다.

한 가지 차이가 중요 사용: 첫 번째 설정 엔터티를 참조 하지 않고 레코드 참조의 필드를 직접 액세스할 수 없습니다. 캔버스 앱 필요한 수식을 작성 하는 경우 모든 형식을 알 수 때문입니다. 앱이 실행 될 때까지 레코드 참조의 유형을 알 수 없으므로, 간단한을 사용할 수 없습니다. *필드* 직접 표기법입니다. 먼저 동적으로 결정 인 엔터티 형식을 합니다 [ **IsType** ](functions/function-astype-istype.md) 함수를 사용 하 여. *필드* 표기법의 결과에 [ **AsType** ](functions/function-astype-istype.md) 함수입니다.

*엔터티 형식* 엔터티의 각 레코드의 스키마를 가리킵니다. 각 엔터티에 고유 이름 및 데이터 형식이 각기 다른 필드 집합이 있습니다. 각 레코드는 엔터티 상속 구조는 두 레코드는 동일한 엔터티를 동일한 엔터티 형식을 가집니다.

## <a name="polymorphic-lookups"></a>다형 조회

Common Data Service는 레코드 간의 관계를 지원합니다. 각 레코드는 **계정** 엔터티에 **기본 연락처** 에서 레코드를 조회 필드를 **연락처** 엔터티. 조회에서 레코드를 참조할 수 있습니다 **연락처** 예를 들어, 레코드를 참조할 수 없습니다 및 합니다 **팀** 엔터티. 마지막 정보는 항상 알고 있으므로 새로운 필드 조회에 제공 됩니다.

Common Data Service는 또한 레코드 집합 내의 모든 엔터티를 참조할 수 있는 다형 조회를 지원 합니다. 예를 들어 합니다 **소유자** 필드에서 레코드를 참조할 수 있습니다 합니다 **사용자** 엔터티 또는 **팀** 엔터티. 동일한 조회 필드의 다른 레코드는 다른 엔터티의 레코드를 참조할 수 있습니다. 이 경우 항상 모르는 됩니다 필드 사용할 수 있습니다.  

캔버스 레코드 참조 다형 조회를 사용 하 여 공통 데이터 서비스 작업에 대 한 설계 되었습니다. 또한 두 가지 개념이 어떻게 다른 지는이 컨텍스트 외부에서 레코드 참조를 사용할 수 있습니다.

다음 섹션에서는 이러한 개념을 사용 하 여 탐색을 시작 합니다 **소유자** 조회 합니다.

## <a name="show-the-fields-of-a-record-owner"></a>소유자는 레코드의 필드를 표시 합니다.

Common Data Service의 모든 엔터티에 포함 된 **소유자** 필드입니다. 이 필드를 제거할 수 없습니다, 다른 추가할 수 없습니다 및 값이 항상 필요 합니다.

에 있는 해당 필드를 표시 합니다 **계정** 엔터티:

1. 오픈 [이 사이트](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
1. 왼쪽된 탐색 모음에서 선택 **데이터** > **엔터티**합니다.
1. 엔터티 목록에서 선택 **계정**합니다.
1. 오른쪽 위 모퉁이에서 필터 목록을 엽니다 (으로 설정 되는 **기본** 기본적으로)를 선택한 후 **모든**합니다.
1. 될 때까지 아래로 스크롤하여 합니다 **소유자** 필드가 표시 됩니다.

> [!div class="mx-imgBorder"]
> ![계정 엔터티에 대해 소유자 필드](media/working-with-references/owner-field.png)

이 조회 필드 중 하나에서 레코드를 참조할 수는 **팀** 엔터티 또는 **사용자** 엔터티. 되도록 사용 권한이 이러한 엔터티의 모든 레코드는 **소유자**; 문제에 직면 하는 경우 지원 되는 역할을 확인 합니다.

이 그림의 간단한 갤러리 **계정**여기서는 **계정** 엔터티를 데이터 원본으로 앱에 추가 되었습니다.

> [!div class="mx-imgBorder"]
> ![갤러리 컨트롤에 표시 된 계정](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> 이 항목에서는 그래픽 일부 이름 및 Common Data Service를 사용 하 여 제공 되는 샘플 데이터의 일부가 아닌 다른 값을 표시 합니다. 단계에는 정확 하 게 특정 결과 대 한 제어를 구성 하는 방법을 보여 줍니다 하지만 환경을 조직에 대 한 데이터에 따라 달라 집니다.

갤러리에서 각 계정의 소유자를 표시 하려면 수식을 사용 하 고 싶은 생각이 들 수 있습니다 **ThisItem.Owner.Name**합니다. 그러나 이름 필드에는 **Team** 엔터티가 **팀 이름**, 및 이름 필드에는 **사용자** 엔터티가 **전체 이름**합니다. 앱은 어떤 유형의 조회 사용 될 때까지 앱을 실행 하는 및의 레코드 간에 달라질 수 있습니다 알 수 없습니다는 **계정** 엔터티.

이러한 차이에 적용할 수 있는 수식을 해야 합니다. 엔터티 형식에 대 한 데이터 원본을 추가 해야 **소유자** 될 수 있습니다 (이 예제의 경우 **사용자** 하 고 **팀**). 이러한 3 개의 데이터 원본을 앱에 추가 합니다.

> [!div class="mx-imgBorder"]
> ![데이터 창에서 계정, 팀 및 사용자 엔터티](media/working-with-references/accounts-datasources.png)

이러한 데이터를 사용 하 여 원본 배치,이 수식을 사용 하 여 사용자 또는 팀의 이름을 표시 합니다.

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![표시 된 소유자 필드를 사용 하 여 갤러리 컨트롤에 표시 된 계정](media/working-with-references/accounts-displayowner.png)

이 수식에서의 **IsType** 테스트 함수를 **소유자** 에 대 한 필드를 **팀** 엔터티. 해당 엔터티 형식에는 합니다 **AsType** 함수를 캐스팅 하는 **팀** 레코드입니다. 이 시점에서의 모든 필드에 액세스할 수 있습니다 합니다 **팀** 엔터티를 포함 하 여 **팀 이름**를 사용 하 여 *합니다. 필드* 표기법입니다. 경우 **IsType** 확인 되는 **소유자** 에서 레코드 아닙니다를 **팀** 엔터티를 해당 필드의 레코드 여야 합니다를 **사용자** 엔터티 때문에 합니다 **소유자** 필드는 필수입니다 (이 하 여야 *빈*).

사용 하는 합니다 [글로벌 명확성 연산자](functions/operators.md#disambiguation-operator) 에 대 한 **[@Teams]** 및 **[@Users]** 전역 엔터티 형식을 사용 하는 경우를 확인 합니다. 이 경우에 필요 하지 않습니다 이지만 폼에 좋은 습관입니다. 다 관계는 종종 갤러리의 레코드 범위에서 충돌 하 고이 이렇게 혼동을 방지 합니다.

레코드 참조의 모든 필드를 사용 하려면 먼저 사용 해야 합니다 **AsType** 함수는 특정 엔터티 형식으로 캐스팅 해야 합니다. 필드에서 직접 액세스할 수 없습니다는 **소유자** 없으므로 시스템 엔터티 유형을 사용 하려는 필드입니다.

**AsType** 경우 함수는 오류를 반환 합니다 **소유자** 필드 사용할 수 있도록 요청 되는 엔터티 형식 일치 하지 않습니다는 **IfError** 이 수식을 단순화 하는 함수입니다. 첫째, 실험적 기능을 설정 **수식 수준 오류 관리**:

> [!div class="mx-imgBorder"]
> ![수식 수준 오류 관리를 켜려면 실험적 스위치](media/working-with-references/accounts-iferror.png)

그런 다음이 사용 하 여 앞의 수식은 바꿉니다.

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>소유자를 기준으로 필터링

축 하 합니다: 레코드 참조 사용에 대 한 가장 어려운 부분을 완료 했습니다. 다른 사용 사례 더 간단 하 게 되므로 레코드의 필드에 액세스 하지 않습니다. 사례에 점으로, 걸릴 필터링이 단원의 탐색입니다.

추가 **콤보 상자** 갤러리 위에 제어 하 고 새 컨트롤의 이러한 속성을 설정 합니다.

- **Items**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![사용자에 게 설정 하는 항목 속성을 사용 하 여 갤러리 위에 콤보 상자 컨트롤 추가](media/working-with-references/filter-insert-combobox.png)

이 콤보 상자에서 선택한 특정 사용자가 갤러리를 필터링 하려면 갤러리의 설정 **항목** 속성을 다음이 수식입니다.

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![콤보 상자 컨트롤에 설정 된 값에 따라 필터링 된 갤러리](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> 이 항목의 지침에는 정확 하 게 하는 단계를 수행 하는 경우 정확 합니다. 그러나 컨트롤을 이름별으로 참조 되는 수식이 컨트롤 이름이 다른 경우 실패 합니다. 을 삭제 하 고 동일한 유형의 컨트롤을 추가 하는 경우 컨트롤의 이름 끝에 번호는 변경 됩니다. 오류를 표시 하는 모든 수식을 모든 컨트롤의 올바른 이름을 포함 되어 있는지 확인 합니다.

사용할 필요가 **IsType** 하거나 **AsType** 다른 레코드 참조로 또는 전체 레코드를 레코드 참조 비교 하기 때문에 있습니다. 앱의 엔터티 형식을 알고 **ComboBox1.Selected** 에서 파생 되기 때문에 **사용자** 엔터티. 계정 소유자는 팀이를 필터 조건과 일치 하지 않습니다.

사용자 또는 팀으로 필터링을 지원 하 여 좀 더 멋지게을 가져올 수 있습니다.

1. 삽입 콤보 상자를 이동 및 갤러리 크기를 조정 하 여 화면 맨 위 근처 공간을 [ **라디오** 제어](controls/control-radio.md) 갤러리 위에 새 컨트롤에 대 한 이러한 속성을 설정한 후:

    - **Items**: `[ "All", "Users", "Teams" ]`
    - **레이아웃**: `Layout.Horizontal`

1. 에 대 한 합니다 **콤보 상자** 컨트롤을이 속성을 설정 (선택 콤보 상자 사라지면 **사용자** 라디오 컨트롤에서):

    - **표시**: `Radio1.Selected.Value = "Users"`

1. 복사 및 붙여넣기 합니다 **콤보 상자** 제어 복사본을 원래를 통해 직접 이동한 다음 복사본에 대 한이 속성을 설정 합니다.

    - **Items**: `Teams`
    - **표시**: `Radio1.Selected.Value = "Teams"`

    앱에는 종속 라디오 컨트롤의 상태에 대 한 번에 하나의 콤보 상자가 표시 됩니다. 다른 바로 위에 이기 때문에 해당 콘텐츠를 변경 하는 동일한 컨트롤에 나타납니다.

1. 마지막으로 설정 합니다 **항목** 의 속성을 **갤러리** 컨트롤을 다음이 수식으로:

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![모든 레코드 또는 특정 사용자 또는 팀을 보여 주는 필터링 된 갤러리](media/working-with-references/filter-combobox.png)

이러한 변화를 통해 모든 레코드를 표시 하거나 사용자 또는 팀을 기준으로 필터링 합니다.

> [!div class="mx-imgBorder"]
> ![다양 한 필터링 된 결과 보여 주는 애니메이션 기반 라디오 컨트롤 및 콤보 상자](media/working-with-references/filter-allthree.gif)

공식은 완벽 하 게 위임할 수 있습니다. 라디오 단추의 값을 비교 하는 부분에서 모든 레코드는 상수 및 필터의 나머지는 Common Data Service에 전송 되기 전에 평가 됩니다.

소유자의 형식에 따라 필터링 하려는 경우 사용할 수 있습니다는 **IsType** 함수가 있지만 하지 아직 위임할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![IsType를 사용 하 여 소유자 유형으로 필터링](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>패치를 사용 하 여 소유자를 업데이트 합니다.

업데이트할 수 있습니다 합니다 **소유자** 동일한 방식으로 다른 조회 필드입니다. 첫 번째 팀에 현재 선택한 계정 소유자를 설정:

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

앱의 형식을 알고 있기 때문에이 방법은 일반적인 조회에서 다르지 않습니다 **첫 번째 (팀)** 합니다. 첫 번째 사용자를 대신 하려는 경우 해당 부분을 바꿉니다 **첫 번째 (사용자)** 합니다. 합니다 **패치** 한다는 사실을 알고 있으면 함수는 **소유자** 필드는 이러한 두 엔터티 형식 중 하나로 설정할 수 있습니다.

앱에이 기능을 추가 합니다.

1. 에 **트리 보기** 창 합니다 **라디오** 컨트롤과 두 **콤보 상자** 동시에 컨트롤입니다.

1. 줄임표 메뉴에서 선택 **이러한 항목을 복사할**:

    > [!div class="mx-imgBorder"]
    > ![트리 뷰를 사용 하 여 여러 컨트롤의 복사본](media/working-with-references/patch-copy.png)

1. 동일한 메뉴에서 선택 **붙여넣기**:

    > [!div class="mx-imgBorder"]
    > ![트리 뷰를 사용 하 여 여러 컨트롤 붙여넣기](media/working-with-references/patch-paste.png)

1. 복사한 컨트롤 갤러리의 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > ![복사한 컨트롤 갤러리의 오른쪽으로 이동](media/working-with-references/patch-position.png)

1. 복사한 선택 **라디오** 를 제어 하 고 이러한 속성 변경:

    - 항목: `[ "Users", "Teams" ]`
    - 기본값: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![모든 선택 라디오 컨트롤에서 제거](media/working-with-references/patch-noall.png) 

1. 에 **라디오** 컨트롤을 선택 **사용자가** 있도록를 **콤보 상자** 사용자를 나열 하는 컨트롤이 표시 되는지 합니다.

1. 표시 된 선택 **콤보 상자** 컨트롤을 설정한 후 합니다 **DefaultSelectedItems** 속성을 다음이 수식:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![사용자가 콤보 상자에 대 한 기본 속성 설정](media/working-with-references/patch-default-users.png)

1. 에 **라디오** 컨트롤을 선택 **팀** 있도록 합니다 **콤보 상자** 팀을 나열 하는 컨트롤이 표시 되는지 합니다.

1. 선택 된 **라디오** 지금 보이지 않는 있이 되려면 컨트롤 **콤보 상자** 사용자에 대 한 제어 합니다.

1. 표시 된 선택 **콤보 상자** 팀에 대 한 제어로 설정한 다음 해당 **DefaultSelectedItems** 속성을 다음이 수식:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![기본 팀 콤보 상자에 대 한 속성 집합](media/working-with-references/patch-default-teams.png)

1. 삽입을 **단추** 컨트롤을 아래로 이동 합니다 **콤보 상자** 컨트롤을 설정한 다음 단추의 **텍스트** 속성을 `"Patch Owner"`입니다.

1. 설정 된 **OnSelect** 속성을 다음이 수식으로 단추:

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![단추 컨트롤을 설정 하는 수식](media/working-with-references/patch-button.png)

복사한 **라디오** 하 고 **콤보 상자** 컨트롤 갤러리에서 현재 선택한 계정에 대 한 소유자를 표시 합니다. 동일한 컨트롤을 사용 하 여 단추를 선택 하 여 팀 또는 사용자 계정의 소유자를 설정할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![사용자 또는 팀을 사용 하 여 소유자의 애니메이션 보여 주는 패치](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>소유자 폼을 사용 하 여 보여 줍니다.

표시할 수 있습니다는 **소유자** 사용자 지정 카드를 추가 하 여 폼 내부 필드입니다. 이 문서의 작성 시점 현재 양식 컨트롤을 사용 하 여 필드의 값을 변경할 수 없습니다.

1. 삽입을 **편집 양식** 컨트롤 및 다음 크기를 조정 하 고 오른쪽 아래 모서리로 이동 합니다.

1. 에 **속성** 오픈 오른쪽 창의 탭을 **데이터 원본** 목록 및 선택한 **계정**:

    > [!div class="mx-imgBorder"]
    > ![빈 값을 사용 하 여 추가 필드를 표시 하는 양식 컨트롤](media/working-with-references/form-insert.png)  

1. 폼의 설정 **항목** 속성을 `Gallery1.Selected`:

    > [!div class="mx-imgBorder"]
    > ![갤러리에서 선택한 항목에서 채워진 추가 필드가 표시 양식 컨트롤](media/working-with-references/form-item.png)

1. 오른쪽 창의 **속성** 탭에서 **필드 편집**을 선택합니다.

1. 에 **필드** 창에서 줄임표를 선택한 후 **사용자 지정 카드 추가**:

    > [!div class="mx-imgBorder"]
    > ![사용자 지정 카드 추가 명령](media/working-with-references/form-customcard.png)

    새 카드 양식 컨트롤의 맨 아래에 나타납니다.

1. 모든 텍스트를 표시 하는 데 필요한 대로 카드 크기 조정:

    > [!div class="mx-imgBorder"]
    > ![삽입 된 사용자 지정 카드 빈](media/working-with-references/form-inserted-customcard.png)

1. 삽입 된 **레이블을** 사용자 지정 카드를 제어 하 고 설정한 다음 레이블의 **텍스트** 속성을 갤러리에는 수식:

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![소유자 필드는 레이블 컨트롤에 표시 되는 사용자 지정 카드](media/working-with-references/form-displayowner.png)

갤러리에서 선택한 각 항목에 대 한 레코드의 소유자를 포함 하 여 계정의 자세한 필드가 폼에 나타납니다. 사용 하 여 소유자를 변경 합니다 **패치** 단추를 폼 컨트롤에는 또한 해당 변경 내용을 보여 줍니다.

> [!div class="mx-imgBorder"]
> ![갤러리에서 변경 내용에 응답 하는 form 컨트롤을 보여 주는 애니메이션](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>고객의 필드를 표시 합니다.

Common Data Service에는 **고객** 조회 필드는 매우 비슷한 다른 다형 조회 **소유자**합니다.

**소유자** 노드인 0 개 이상의 엔터티를 하지만 엔터티 하나씩 포함 될 수 있습니다 **고객** 조회 필드입니다. 합니다 **연락처** 시스템 엔터티를 포함 합니다 **회사 이름** 필드를 **고객** 조회 필드:

> [!div class="mx-imgBorder"]
> ![연락처 회사 이름 필드는 필요 하지 않습니다 하는 고객 데이터 형식으로 표시 하는 엔터티](media/working-with-references/customer-companyname.png)

더 추가할 수 있습니다 **고객** 를 선택 하 여 엔터티에 조회 필드를 **고객** 새 필드에 대 한 데이터 형식:

![필드를 만들 때 데이터 형식의 목록에서 고객 데이터 입력](media/working-with-references/customer-datatype.png)

A **고객** 조회 필드 중 하나에서 레코드를 참조할 수는 **계정** 엔터티 또는 **연락처** 엔터티. 사용 하 여는 **IsType** 하 고 **AsType** 이러한 엔터티를 사용 하 여 이제 기능은 데이터 원본으로 추가 하는 것이 좋습니다 (두어도 **팀** 및 **사용자**  진행에서).

> [!div class="mx-imgBorder"]
> ![계정, 팀, 사용자 및 연락처 엔터티를 데이터 창에서](media/working-with-references/customer-datasources.png)

처리를 **고객** 하 고 **소유자** 필드는 유사 하므로 앱 문자 그대로 복사할 수 있습니다 (**파일** > **다른이름으로**, 한 다음 다른 이름을 지정) 하 고 이러한 간단한 대체:

| 위치 | **소유자** 샘플 | **고객** 샘플 |
|----------|-----------|------------------|
| 전체 | **소유자** | **' 고객 이름 '** |
| 전체 | **사용자** | **계정** |
| 전체 | **팀** | **연락처** |
| 갤러리의 **항목** 속성 | **계정** | **연락처** |
| 양식의 **항목** 속성 | **계정** | **연락처** |
| 첫 번째 인수 **패치**<br>단추의 **OnSelect** 속성 | **계정** | **연락처** |
| 라디오의 필터링 **항목** 속성 | **[&nbsp;"All",&nbsp;"Users",&nbsp;"Teams"&nbsp;]** | **[&nbsp;"All",&nbsp;"Accounts",&nbsp;"Contacts"&nbsp;]** |
| 라디오의 패치 **항목** 속성 | **["Users", "팀"]** | **[ "Accounts", "Contacts" ]** |
| 콤보 상자 **Visible** 속성 | **"사용자"** 고 **"팀"** | **[계정]** 고 **"Contacts"** |

예를 들어, 새 갤러리가 있어야 합니다 **항목** 속성:

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![간단한 변경 내용 적용을 사용 하 여 소유자 앱에서 파생 하는 고객 앱](media/working-with-references/customer-simple-update.png)

두 가지 중요 한 차이점 **고객** 하 고 **소유자** 갤러리 및 양식 내에서 수식에 대 한 업데이트 필요:

1. 사이 일 대 다 관계 **계정을** 하 고 **연락처** 이러한 엔터티 형식 이름으로 참조 하는 경우 보다 우선적으로 적용 합니다. 대신 **계정을**를 사용 하 여  **\[ \@계정]**; 대신 **연락처**를 사용 하 여  **\[ \@ 연락처]** 합니다. 사용 하 여는 [글로벌 명확성 연산자](functions/operators.md#disambiguation-operator) 에서 엔터티 형식 참조 하는 것이 해야 **IsType** 하 고 **AsType**. 이 문제는 갤러리 및 양식 컨트롤의 레코드 컨텍스트에만 존재 합니다.

1. 합니다 **소유자** 필드 값이 있어야 합니다. 하지만 **고객** 필드 수 *빈*합니다. 형식 이름이 없는 올바른 결과 표시 하려면 사용 하 여이 사례에 대 한 테스트를 [ **IsBlank** 함수](functions/function-isblank-isempty.md), 대신 빈 텍스트 문자열을 표시 합니다.

이러한 변경 내용을 모두 동일한 수식에서 형태로 사용자 지정 카드에 나타나는 뿐만 **텍스트** 갤러리의 레이블 컨트롤의 속성:

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![갤러리에서 부제목 레이블 컨트롤의 Text 속성을 업데이트 합니다.](media/working-with-references/customer-update.png)

이러한 변경으로 확인 하 고 변경할 수는 **Company Name** 필드를 **연락처** 엔터티:

> [!div class="mx-imgBorder"]
> ![연락처에서 선택을 변경 하는 애니메이션 보여 주는 기반 기타 컨트롤 및 폼에 변경 하는 갤러리 컨트롤](media/working-with-references/customer-allthree.gif)

> [!NOTE]
> 이 문서의 작성 시점 현재 **고객** 조회 이러한 제한 사항이 있습니다.
>
> - 특정 레코드를 기준으로 목록을 필터링 할 수 없습니다는 **연락처** 하거나 **계정** 엔터티. 이전 예제에서 필터 라디오 단추 컨트롤 작동 하지 않습니다.
> - 작동 하는 유일한 고객 필드는 시스템 정의 **' 회사 이름 '** 에 **연락처** 이전 예제에서 사용 된 엔터티. 사용자 지정 고객 필드를 추가 합니다. 아직 지원 되지 않습니다.
> - 사용 하 여 고객 필드를 지울 수 없습니다 **패치** 로 설정 하려면 *빈*합니다.

## <a name="understand-regarding-lookup-fields"></a>조회 필드에 대 한 이해

합니다 **와 관련 하 여** 조회 필드에서 이미 작업을 했었다면이 항목에는 약간 다릅니다. 이 항목에서는 앞에서 설명한 패턴을 적용 하 여 먼저 및 다음 다른 유용한 정보를 배웁니다.

시작할 수 있습니다 단순히 합니다 **팩스** 엔터티. 이 엔터티는 다형성에 **에 대 한** 조회 필드를 참조할 수 있는 **계정**를 **연락처**, 및 기타 엔터티. 앱에 대해 수행할 수 있습니다 **고객이** 에 대 한 수정 **팩스**:

| 위치 | **고객** 샘플 | **팩스** 샘플 |
|----------|-----------|------------------|
| 전체 | **' 고객 이름 '** | **관련 항목** |
| 갤러리의 **항목** 속성 | **연락처** | **팩스 수** |
| 양식의 **항목** 속성 | **연락처** | **팩스 수** |
| 첫 번째 인수 **패치**<br> 단추의 **OnSelect** 속성 | **연락처** | **팩스 수** |

데이터 소스를 추가 해야 하는 다시:에 대 한이 이번 **팩스**합니다. 에 **뷰** 탭을 선택 **데이터 원본**:

> [!div class="mx-imgBorder"]
> ![계정, 팀, 사용자, 연락처 및 팩스 엔터티를 보여 주는 데이터 창](media/working-with-references/faxes-datasources.png)

에 대 한 중요 한 차이점이 **에 관한** 제한 아니라는 점 **계정** 하 고 **연락처**합니다. 사실, 엔터티 목록을 사용자 지정 엔터티를 사용 하 여 확장 가능 합니다. 대부분 앱의 수정 없이이 시점에서 수용할 수 있지만 갤러리 및 폼에서 레이블에 대 한 수식을 업데이트 해야 합니다.

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> ![조회에 대 한 자막 컨트롤에 대 한 업데이트 된 텍스트 속성](media/working-with-references/regarding-label.png)

이러한 변경을 수행한 후 작업할 합니다 **에 대 한** 수행한 것 처럼 조회를 **소유자** 및 **고객** 조회:

> [!div class="mx-imgBorder"]
> ![팩스에 변경 내용을 보여 주는 애니메이션 기반 다른 컨트롤과 폼에 업데이트를 구동 하는 갤러리 컨트롤](media/working-with-references/regarding-allthree.gif)

> [!NOTE]
> 이 문서의 작성 시점 현재 **와 관련 하 여** 조회 이러한 제한 사항이 있습니다.
>
> - 특정 레코드를 기준으로 목록을 필터링 할 수 없습니다. 이전 예제에서 필터 라디오 단추 컨트롤 작동 하지 않습니다.
> - 사용 하 여 관련 필드를 지울 수 없습니다 **패치** 로 설정 하려면 *빈*합니다.

## <a name="understand-regarding-relationships"></a>관계에 대 한 이해

**에 대 한** 에서 서로 다릅니다 **소유자** 및 **고객** 전자 다 대 일 관계 반하므로 합니다. 정의상, 역방향, 다 관계를 작성할 수 있습니다 **첫 번째 (계정). 팩스**합니다.

보겠습니다를 백업 하 고 엔터티 정의 살펴봅니다. Common Data Service와 같은 엔터티 **팩스**, **작업**, **전자 메일**, **노트**를 **전화 통화**, **문자**, 및 **채팅** 으로 지정 된 [ *활동*](../../developer/common-data-service/activity-entities.md)합니다. 만들 수도 있습니다 고유한 [사용자 지정 활동 엔터티](../../developer/common-data-service/custom-activities.md)합니다. 작업 엔터티를 만들거나 보려면 아래 해당 설정이 표시 **더 많은 설정을**:

![엔터티를 만들 때 작업 엔터티 설정](media/working-with-references/activity-entitytype.png)

활동 엔터티도 활성화 되어 있는 경우 다른 엔터티에 연결할 수 있습니다는 *활동 작업* 엔터티의 설정 합니다. **계정**, **연락처**, 및 다른 여러 표준 엔터티는 지정 된 (다시 아래 **더 많은 설정을**):

![작업 작업 설정 엔터티를 만들 때](media/working-with-references/activity-entityuse.png)

모든 활동 엔터티 및 작업-작업 엔터티 관계를 암시 된 경우 필터를 변경 하는 경우 **모든** 화면의 맨 위에 있는 선택 된 **팩스** 엔터티를 선택한 후는 **관계** 탭을 대상이될수있는모든엔터티 **와 관련 하 여** 조회 표시:

> [!div class="mx-imgBorder"]
> ![다 대 일 관계에 대 한 표시 팩스 엔터티의 관계](media/working-with-references/activity-manytoone.png)

에 대 한 관계를 표시 하는 경우는 **계정을** 엔터티의 원인이 될 수 있는 모든 엔터티를 **와 관련 하 여** 조회 필드 표시:

> [!div class="mx-imgBorder"]
> ![1 대 다 관계에 대 한 표시: 계정 엔터티 관계](media/working-with-references/activity-onetomany.png)

새로운 모든 평균 하는가?

- 수식에 작성할 때 작업 엔터티 목록을 수정 되지 않습니다 하 고 직접 만들 수 있습니다를 고려해 야 합니다. 수식이 예상 하지 않은 활동 엔터티를 처리 적절 하 게 해야 합니다.
- 작업 활동 및 활동에는-일대다 관계가 있습니다. 계정에 관련 된 모든 팩스에 대 한 쉽게 요청할 수 있습니다.

앱에서이 개념을 탐색:

1. 다른 화면을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > ![빈 화면을 삽입 합니다.](media/working-with-references/activitypointer-newscreen.png)

1. 갤러리 컨트롤을 삽입 하 고 조정한 다음 화면의 왼쪽으로 이동 합니다.

1. 에 **속성** 오른쪽 탭 창, 갤러리의 설정 **항목** 에 **계정**:

    > [!div class="mx-imgBorder"]
    > ![속성 창에서 계정에 항목을 설정 합니다.](media/working-with-references/activitypointer-accounts.png)

1. 갤러리의 레이아웃 설정 **제목**, 다음으로 제목 필드를 설정 하 고 **계정 이름**:

    > [!div class="mx-imgBorder"]
    > ![속성 창에서 갤러리 컨트롤에 대 한 레이아웃을 제목에 설정 합니다.](media/working-with-references/activitypointer-account-name.png)

1. 두 번째 갤러리를 추가 하 고 조정한 다음 화면 왼쪽에서 오른쪽으로 이동 합니다.

1. 새 갤러리의 설정 **항목이** 속성을 `Gallery2.Selected.Faxes`입니다.

    이 단계에는 지정된 된 계정에 대 한 팩스의 필터링 된 목록을 반환합니다.

    > [!div class="mx-imgBorder"]
    > ![팩스에 대 한 항목 속성 설정 기반 갤러리 컨트롤](media/working-with-references/activitypointer-faxes.png)

1. 갤러리의 레이아웃 설정 **제목 및 부제목**, 표시할 제목 필드를 설정한 후를 **주체** 필드 (소문자 수 있음 **주체**):

    > [!div class="mx-imgBorder"]
    > ![제목 필드로 설정 제목](media/working-with-references/activitypointer-subject.png)

계정 목록에서 항목을 선택 하면 해당 계정에만 팩스 팩스의 목록에 나타납니다.

> [!div class="mx-imgBorder"]
> ![팩스 목록을 주행 계정 갤러리에서 선택 영역을 표시 하는 애니메이션](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>작업 엔터티

이전 섹션에서 설명한 대로 계정의 모든 팩스를 표시할 수 있습니다. 그러나 팩스, 전자 메일 메시지, 전화 통화 및 기타 상호 작용을 포함 하는 계정에 대 한 모든 활동을 표시할 수 있습니다.

후자의 시나리오의 경우 사용 합니다 **활동** 엔터티. 설정 하 여이 엔터티를 표시할 수 있습니다 **모든** 엔터티 목록에서 필터를 제거 하려면 오른쪽 위 모퉁이에서.

> [!div class="mx-imgBorder"]
> ![작업 엔터티를 보여 주는 엔터티 목록](media/working-with-references/activitypointer-entity.png)

합니다 **활동** 엔터티는 특별 합니다. 레코드를 추가할 때마다 합니다 **팩스** 엔터티를 시스템도에 레코드를 만듭니다 합니다 **활동** 모든 활동 엔터티 간에 공통 되는 필드를 사용 하 여 엔터티. 이러한 필드 중 **주체** 가장 흥미로운 부분 중 하나입니다.

이전 예제에서 하나의 줄을 변경 하 여 모든 활동을 표시할 수 있습니다. 바꿉니다 `Gallery2.Selected.Faxes` 사용 하 여 `Gallery2.Selected.Activities`:

> [!div class="mx-imgBorder"]
> ![팩스에서 활동을 변경 하 고 두 번째 갤러리 항목 속성 변경](media/working-with-references/activitypointer-gallery.png)

레코드에서 생성 되는 **활동** 엔터티를 사용할 수 있습니다 그럼에도 불구 하 고는 **IsType** 는 어떤 종류의 작업을 식별 하는 함수입니다. 다시 사용 하기 전에 **IsType** 엔터티 형식을 사용 하 여 데이터 소스를 추가 해야 합니다.

> [!div class="mx-imgBorder"]
> ![IsType 함수에 필요한 모든 엔터티를 보여 주는 데이터 창](media/working-with-references/activity-datasources.png)

이 수식은 사용 하 여 레이블 컨트롤을 갤러리 내에서 레코드 종류를 표시할 수 있습니다.

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![팩스, 전화 통화 및 기타 작업에 대 한 정보를 표시 하는 수식에 텍스트 속성을 설정 합니다.](media/working-with-references/activitypointer-type.png)

사용할 수도 있습니다 **AsType** 특정 형식의 필드에 액세스할 수 있습니다. 예를 들어이 수식을 각 작업의 유형을 결정을 전화 통화, 전화 번호 및 호출 방향 표시 합니다 **전화번호** 엔터티:

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![전화 통화에 대 한 자세한 정보를 사용 하 여 확장 된 텍스트 속성](media/working-with-references/activitypointer-phonecall.png)

결과적으로, 앱 활동의 전체 목록을 보여 줍니다. 합니다 **주체** 수식을 고려 하 인지 여부를 모든 종류의 작업에 대 한 필드가 나타납니다. 활동에 대 한 사용자가 알고 있는 유형의 경우 해당 형식 이름 및 각 활동에 대 한 type 별 정보를 표시할 수 있습니다.

> [!div class="mx-imgBorder"]
> ![완료 작업의 종류에 대 한 정보를 보여 주는 화면](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>엔터티 정보

모든 지금 합니다 **에 대 한** 예제 토대로 작업을 하지만 **정보** 엔터티 다른 케이스를 나타냅니다.

엔터티를 만든 경우에 첨부 파일을 사용할 수 있습니다.

![엔터티를 만들 때 첨부 파일 및 메모를 사용 하도록 설정](media/working-with-references/notes-entity.png)

만들어야이 확인란을 선택 하면를 **에 대 한** 와 관계는 **메모** 엔터티를이 그래픽으로 보여 줍니다는 **계정** 엔터티:

> [!div class="mx-imgBorder"]
> ![1 대 다 관계를 통해 정보에 관계를 보여 주는: 계정 엔터티](media/working-with-references/notes-relationships.png)

사용이 차이 외는 **와 관련 하 여** 작업을 사용 하는 동일한 방식으로 조회 합니다. 첨부 파일을에 일 대 다 관계가 사용 되는 엔터티 **노트**이 예제와 같이:

`First( Accounts ).Notes`

> [!NOTE]
> 이 문서의 작성 시점 현재 합니다 **에 대 한** 조회에 사용할 수 없습니다는 **메모** 엔터티. 읽을 수 없습니다 또는 필터를 기반으로 합니다 **에 대 한** 필드를 사용 하 여 필드를 설정할 수 없습니다 **패치**합니다.
>
> 그러나 반대 **노트** 에 일 대 다 관계 이므로 사용할 수 있는, 첨부 파일에 사용 되는 레코드에 대 한 정보 목록을 필터링 할 수 있습니다. 사용할 수도 있습니다는 [ **관련** ](functions/function-relate-unrelate.md) 레코드의 메모를 추가 하려면 함수 **메모** 테이블 이지만 먼저 만들어야,이 예제와 같이:
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>활동 당사자

이 문서의 작성 시점 현재 캔버스 앱 활동 당사자를 지원 하지 않습니다.
