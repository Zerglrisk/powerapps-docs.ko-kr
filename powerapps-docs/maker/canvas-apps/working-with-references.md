---
title: 레코드 참조 및 다형성 조회 이해 | Microsoft Docs
description: Canvas 앱에서 레코드 참조 및 다형성 조회 작업
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: deea21dd97ee71a74973393b7d6714a8c55ba969
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "71989458"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>Canvas 앱에서 레코드 참조 및 다형성 조회 이해

학교에서 리서치 문서를 작성 하는 경우 끝에 참조 목록이 제공 될 것입니다. 사용한 실제 배경 자료의 복사본을 포함 하는 것이 아니라 다른 사람이 원본 소스를 추적할 수 있도록 웹 링크, 책 제목, 저자 또는 기타 정보를 포함 하 고 있습니다. 서로 다른 종류의 소스를 단일 목록으로 혼합 하 고, 각각 적절 한 인용문에 대 한 고유한 세부 정보를 포함 하는 오디오 녹음 옆의 신문 문서를 사용할 수 있습니다. 예를 들어 위키백과 문서는 [긴 참조 목록을](https://en.wikipedia.org/wiki/Microsoft#References)포함 하는 경우가 많습니다.

Canvas 앱에서 데이터 원본에서 다운로드 된 레코드의 복사본으로 작업 하는 경우가 많습니다. [**조회**](functions/function-filter-lookup.md) 및 [**필터**](functions/function-filter-lookup.md) 함수와 [**갤러리**](controls/control-gallery.md) 컨트롤의 **선택** 된 속성을 사용 하 여 원하는 특정 레코드를 식별할 수 있습니다. **필터** 또는 **선택** 된 모든 레코드는 동일한 엔터티 형식이 되므로 간단한로 필드를 사용할 수 있습니다. *필드* 표기법입니다. 이러한 복사본은 종종 참조 정보를 포함 하므로 [**Patch**](functions/function-patch.md) 함수를 사용 하 여 원래 원본을 업데이트할 수 있습니다.

Canvas 앱은 *레코드 참조*도 지원 합니다. 연구 문서와 마찬가지로 레코드 참조는 전체 복사본을 포함 하지 않고 레코드를 참조 합니다. 이러한 참조는 엔터티의 레코드를 참조할 수 있습니다. 또한 연구 용지 참조와 마찬가지로 단일 열에서 여러 엔터티의 레코드를 혼합할 수 있습니다.

레코드 참조에 대 한 많은 작업은 레코드 작업과 동일 합니다. 레코드 참조를 서로 비교 하 고 전체 레코드와 비교할 수 있습니다. 전체 레코드로 조회 하는 것 처럼 **Patch** 함수를 사용 하 여 레코드 참조의 값을 설정할 수 있습니다.

한 가지 중요 한 사용 차이가 있습니다. 즉, 참조 하는 엔터티를 먼저 설정 하지 않고도 레코드 참조의 필드에 직접 액세스할 수 없습니다. 이는 캔버스 앱에서 수식을 작성할 때 모든 형식을 알 수 있어야 하기 때문입니다. 앱이 실행 될 때까지 레코드 참조의 형식을 알 수 없으므로 simple을 사용할 수 없습니다. 직접 *필드* 표기법입니다. 먼저 [**istype**](functions/function-astype-istype.md) 함수를 사용 하 여 엔터티 형식을 동적으로 확인 한 다음를 사용 해야 합니다. 표시 [**유형 함수 결과**](functions/function-astype-istype.md) 의 *필드* 표기법입니다.

*엔터티 형식은* 엔터티의 각 레코드 스키마를 나타냅니다. 각 엔터티에는 이름 및 데이터 형식이 다른 고유한 필드 집합이 있습니다. 엔터티의 각 레코드는 해당 구조를 상속 합니다. 동일한 엔터티에서 가져온 두 레코드는 동일한 엔터티 형식입니다.

## <a name="polymorphic-lookups"></a>다형 조회

Common Data Service 레코드 간의 관계를 지원 합니다. **Accounts** 엔터티의 각 레코드에는 **연락처** 엔터티의 레코드에 대 한 **기본 연락처** 조회 필드가 있습니다. 조회는 **연락처** 의 레코드만 참조할 수 있으며, 예를 들어 **팀** 엔터티 라는 레코드를 참조할 수 없습니다. 마지막 세부 정보는 조회에 사용할 수 있는 필드를 항상 알 수 있기 때문에 중요 합니다.

Common Data Service는 집합에 있는 모든 엔터티의 레코드를 참조할 수 있는 다형 조회도 지원 합니다. 예를 들어, **소유자** 필드는 **사용자** 엔터티 또는 **팀** 엔터티의 레코드를 참조할 수 있습니다. 다른 레코드의 동일한 조회 필드는 다른 엔터티의 레코드를 참조할 수 있습니다. 이 경우 사용할 수 있는 필드를 항상 알 수는 없습니다.

Canvas 레코드 참조는 Common Data Service에서 다형 조회를 사용 하도록 설계 되었습니다. 이 컨텍스트 외부에서 레코드 참조를 사용할 수도 있습니다 .이는 두 개념의 차이입니다.

다음 섹션에서는 **소유자** 조회를 사용 하 여 이러한 개념을 탐색 하기 시작 합니다.

## <a name="show-the-fields-of-a-record-owner"></a>레코드 소유자의 필드를 표시 합니다.

Common Data Service의 모든 엔터티는 **소유자** 필드를 포함 합니다. 이 필드는 제거할 수 없으며 다른 필드를 추가할 수 없으며 항상 값이 필요 합니다.

**계정** 엔터티에 해당 필드를 표시 하려면 다음을 수행 합니다.

1. [이 PowerApps 사이트](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)를 엽니다.
1. 왼쪽 탐색 모음에서 **데이터** > **엔터티**를 선택 합니다.
1. 엔터티 목록에서 **계정**을 선택 합니다.
1. 오른쪽 위 모서리에서 필터 목록을 열고 (기본적으로 **기본값으로** 설정 됨) **모두**를 선택 합니다.
1. **소유자** 필드가 나타날 때까지 아래로 스크롤합니다.

 > [!div class="mx-imgBorder"]
 > 계정 엔터티의 소유자 필드를 ![](media/working-with-references/owner-field.png)

이 조회 필드는 **팀** 엔터티 또는 **사용자** 엔터티의 레코드를 참조할 수 있습니다. 이러한 엔터티의 일부 레코드에는 **소유자**가 될 수 있는 권한이 없습니다. 문제가 발생 하는 경우 지원 되는 역할을 확인 합니다.

이 **그래픽은 계정 엔터티가 앱** 에 데이터 원본으로 추가 된 간단한 **계정**갤러리를 보여줍니다.

> [!div class="mx-imgBorder"]
> 갤러리 컨트롤에 표시 되는 ![계정](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> 이 항목 전체에서 그래픽은 Common Data Service와 함께 제공 되는 샘플 데이터의 일부가 아닌 일부 이름 및 기타 값을 표시 합니다. 단계는 특정 결과에 대 한 컨트롤을 구성 하는 방법을 정확 하 게 보여 주지만 사용자의 환경은 조직의 데이터에 따라 달라 집니다.

갤러리에 각 계정의 소유자를 표시 하려면 **ThisItem.Owner.Name**수식을 사용 하는 것이 좋습니다. 그러나 **팀** 엔터티의 이름 필드는 **팀 이름이**고 **사용자** 엔터티의 이름 필드는 **전체 이름**입니다. 앱은 앱을 실행할 때까지 작업 중인 조회 유형을 알 수 없으며, **계정** 엔터티의 레코드 마다 다를 수 있습니다.

이러한 차이에 맞게 조정할 수 있는 수식이 필요 합니다. 또한 **소유자** 가 될 수 있는 엔터티 형식에 대 한 데이터 소스를 추가 해야 합니다 (이 경우 **사용자** 및 **팀**). 앱에 다음 세 가지 데이터 원본을 추가 합니다.

> [!div class="mx-imgBorder"]
> 데이터 창의 계정, 팀 및 사용자 엔터티를 ![](media/working-with-references/accounts-datasources.png)

이러한 데이터 원본을 배치한 다음이 수식을 사용 하 여 사용자 또는 팀의 이름을 표시 합니다.

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> 소유자 필드가 표시 된 갤러리 컨트롤에 표시 되는 ![계정](media/working-with-references/accounts-displayowner.png)

이 수식에서 **istype** 함수는 **팀** 엔터티를 기준으로 **소유자** 필드를 테스트 합니다. 해당 엔터티 형식인 경우 **에는이 함수를** **팀** 레코드로 캐스팅 합니다. 이제를 사용 하 여 **팀 이름**등 **팀 엔터티의 모든** 필드에 액세스할 수 있습니다 *. 필드* 표기법입니다. **Istype** 수가 **소유자** 가 **팀** 엔터티의 레코드가 아닌 것으로 확인 되는 경우 **소유자** 필드가 필요 하므로 해당 필드는 **사용자** 엔터티의 레코드 여야 합니다 ( *비워*둘 수 없음).

**[@Teams]** 및 **[@Users]** 에 대 한 [전역 명확성 연산자](functions/operators.md#disambiguation-operator) 를 사용 하 여 전역 엔터티 형식을 사용 하 고 있는지 확인 합니다. 이 경우에는 필요 하지 않지만 폼을 작성 하는 것이 좋습니다. 일 대 다 관계가 갤러리의 레코드 범위에서 충돌 하는 경우가 많으며이 경우 혼동을 피할 수 있습니다.

레코드 참조의 필드를 사용 하려면 먼저 형식 지정 함수를 사용 하 여 특정 엔터티 형식으로 캐스팅 **해야 합니다.** 시스템에서 사용 하려는 엔터티 형식을 알 수 없으므로 **소유자** 필드에서 직접 필드에 액세스할 수 없습니다.

**Owner** 필드가 요청 중인 엔터티 형식과 일치 하지 않는 경우 **에는** **IfError** 함수를 사용 하 여이 수식을 간소화할 수 있습니다. 먼저 실험적 기능 **수식 수준 오류 관리**를 설정 합니다.

> [!div class="mx-imgBorder"]
> ![실험적 스위치를 사용 하 여 수식 수준 오류 관리를 켭니다](media/working-with-references/accounts-iferror.png)

그런 다음 이전 수식을 다음과 같이 바꿉니다.

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>소유자를 기준으로 필터링

축 하 합니다. 레코드 참조를 사용 하 여 가장 어려운 부분을 완료 했습니다. 다른 사용 사례는 레코드의 필드에 액세스 하지 않기 때문에 보다 간단 합니다. 해당 하는 경우이 섹션에서 살펴볼 필터링을 수행 합니다.

갤러리 위에 **콤보 상자** 컨트롤을 추가 하 고 새 컨트롤의 다음 속성을 설정 합니다.

- **항목**: `Users`
- **Selectmultiple**: `false`

> [!div class="mx-imgBorder"]
> 항목 속성이 사용자로 설정 된 갤러리 위의 갤러리에서 콤보 상자 컨트롤을 추가 ![](media/working-with-references/filter-insert-combobox.png)

이 콤보 상자에서 선택한 특정 사용자가 갤러리를 필터링 하려면 갤러리의 **Items** 속성을 다음 수식으로 설정 합니다.

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> 콤보 상자 컨트롤에 설정 된 값을 기준으로 필터링 된 갤러리 ![](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> 이 항목의 지침은 단계를 정확 하 게 따르는 경우에 정확 합니다. 그러나 컨트롤에 다른 이름이 있는 경우 해당 이름을 기준으로 컨트롤을 참조 하는 수식이 실패 합니다. 동일한 형식의 컨트롤을 삭제 하 고 추가 하는 경우 컨트롤의 이름 끝에 있는 숫자가 변경 됩니다. 오류를 표시 하는 수식의 경우 모든 컨트롤의 올바른 이름이 포함 되어 있는지 확인 합니다.

다른 레코드 **참조 또는 전체** 레코드에 대 한 레코드 참조를 비교 하 고 있으므로 **istype** 또는 고 지 수를 사용할 필요가 없습니다. 앱은 ComboBox1의 엔터티 형식을 알고 있습니다 .이 엔터티는 **Users** 엔터티에서 파생 되기 때문에 **선택 됩니다.** 소유자가 팀 인 계정이 필터 조건과 일치 하지 않습니다.

사용자 또는 팀에서 필터링을 지원 하 여 약간의 fancier을 얻을 수 있습니다.

1. 갤러리의 크기를 조정 하 고 콤보 상자를 이동 하 여 갤러리 위에 [ **라디오** 컨트롤](controls/control-radio.md) 을 삽입 하 고 새 컨트롤에 대해 이러한 속성을 설정 하 여 화면 위쪽 근처에 몇 가지 공간을 만듭니다.

    - **항목**: `[ "All", "Users", "Teams" ]`
    - **레이아웃**: `Layout.Horizontal`

1. **콤보 상자** 컨트롤의 경우이 속성을 설정 합니다. 콤보 상자가 사라지면 라디오 컨트롤의 **사용자** 를 선택 합니다.

    - **표시**: `Radio1.Selected.Value = "Users"`

1. **콤보 상자** 컨트롤을 복사 하 여 붙여넣고 원본에서 직접 복사본을 이동한 다음 복사본에 대해 이러한 속성을 설정 합니다.

    - **항목**: `Teams`
    - **표시**: `Radio1.Selected.Value = "Teams"`

    앱은 라디오 컨트롤의 상태에 따라 한 번에 하나의 콤보 상자만 표시 합니다. 서로 바로 위에 있기 때문에 콘텐츠를 변경 하는 동일한 컨트롤로 표시 됩니다.

1. 마지막으로 **갤러리** 컨트롤의 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > 모든 레코드나 특정 사용자 또는 팀을 보여 주는 필터링 된 갤러리 ![](media/working-with-references/filter-combobox.png)

이러한 변경으로 모든 레코드를 표시 하거나 사용자 또는 팀을 기준으로 필터링 할 수 있습니다.

> [!div class="mx-imgBorder"]
> 라디오 컨트롤 및 콤보 상자를 기준으로 다양 한 필터링 된 결과를 보여 주는 ![애니메이션](media/working-with-references/filter-allthree.gif)

수식이 완전히 위임 가능한. 라디오 단추 값을 비교 하는 부분은 모든 레코드에서 상수 이며 나머지 필터는 Common Data Service 전송 되기 전에 계산 됩니다.

소유자 유형을 필터링 하려는 경우 **istype** 함수를 사용할 수 있지만 아직 되지 않습니다.

> [!div class="mx-imgBorder"]
> IsType](media/working-with-references/filter-bytype.png)를 사용 하 여 소유자 유형별로 필터링 ![

## <a name="update-the-owner-by-using-patch"></a>패치를 사용 하 여 소유자 업데이트

다른 조회와 동일한 방식으로 **소유자** 필드를 업데이트할 수 있습니다. 현재 선택한 계정의 소유자를 첫 번째 팀으로 설정 하려면 다음을 수행 합니다.

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

앱이 **첫 번째 (팀)** 의 유형을 알고 있으므로이 접근 방식은 일반적인 조회와 다릅니다. 첫 번째 사용자를 대신 사용 하려면 해당 부분을 **첫 번째**사용자로 바꿉니다. **Patch** 함수는 **소유자** 필드를 이러한 두 엔터티 형식 중 하나로 설정할 수 있다는 것을 알고 있습니다.

앱에이 기능을 추가 하려면 다음을 수행 합니다.

1. **트리 뷰** 창에서 **라디오** 컨트롤 및 두 개의 **콤보 상자** 컨트롤을 동시에 선택 합니다.

1. 줄임표 메뉴에서 **다음 항목 복사**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 트리 뷰를 사용 하 여 여러 컨트롤의 복사본을 ![](media/working-with-references/patch-copy.png)

1. 동일한 메뉴에서 **붙여넣기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 트리 뷰를 사용 하 여 여러 컨트롤을 ![붙여 넣을](media/working-with-references/patch-paste.png)

1. 복사한 컨트롤을 갤러리의 오른쪽으로 이동 합니다.

    > [!div class="mx-imgBorder"]
    > 복사 된 컨트롤을 갤러리의 오른쪽으로 이동 ![](media/working-with-references/patch-position.png)

1. 복사한 **라디오** 컨트롤을 선택 하 고 다음 속성을 변경 합니다.

    - 항목: `[ "Users", "Teams" ]`
    - 기본값: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > 라디오 컨트롤에서 모든 선택을 제거 ![](media/working-with-references/patch-noall.png) 

1. **라디오** 컨트롤에서 사용자를 나열 하는 **콤보 상자** 컨트롤이 표시 되도록 **사용자** 를 선택 합니다.

1. 표시 되는 **콤보 상자** 컨트롤을 선택 하 고 **DefaultSelectedItems** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > 사용자 콤보 상자에 설정 된 기본 속성 ![](media/working-with-references/patch-default-users.png)

1. **라디오** 컨트롤 **에서 팀을 선택 하** 여 팀을 나열 하는 **콤보 상자** 컨트롤이 표시 되도록 합니다.

1. 사용자를 위해 현재 보이지 않는 **콤보 상자** 컨트롤에서 선택 항목을 가져올 **라디오** 컨트롤을 선택 합니다.

1. 팀에 표시 되는 **콤보 상자** 컨트롤을 선택 하 고 **DefaultSelectedItems** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > 팀 콤보 상자의 기본 속성 집합을 ![](media/working-with-references/patch-default-teams.png)

1. **Button** 컨트롤을 삽입 하 고, **콤보 상자** 컨트롤 아래로 이동한 다음, 단추의 **Text** 속성을 `"Patch Owner"`로 설정 합니다.

1. 단추의 **Onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > 단추 컨트롤에 설정 ![수식](media/working-with-references/patch-button.png)

복사한 **라디오** 및 **콤보 상자** 컨트롤은 갤러리에서 현재 선택한 계정에 대 한 소유자를 표시 합니다. 동일한 컨트롤을 사용 하 여 다음 단추를 선택 하 여 계정의 소유자를 팀 또는 사용자로 설정할 수 있습니다.

> [!div class="mx-imgBorder"]
> 사용자 또는 팀](media/working-with-references/patch-allthree.gif) 소유자의 패치를 보여 주는 ![애니메이션

## <a name="show-the-owner-by-using-a-form"></a>폼을 사용 하 여 소유자 표시

사용자 지정 카드를 추가 하 여 양식 내에 **소유자** 필드를 표시할 수 있습니다. 이 문서를 작성할 때 양식 컨트롤을 사용 하 여 필드의 값을 변경할 수 없습니다.

1. **편집 양식** 컨트롤을 삽입 하 고 크기를 조정 하 여 오른쪽 아래 모서리로 이동 합니다.

1. 화면 오른쪽의 **속성** 탭에서 **데이터 원본** 목록을 열고 **계정**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 빈 값이 있는 추가 필드를 표시 하 ![폼 컨트롤](media/working-with-references/form-insert.png)  

1. 양식의 **항목** 속성을 `Gallery1.Selected`로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 갤러리에서 선택한 항목으로 채워진 추가 필드를 표시 하는 ![양식 컨트롤](media/working-with-references/form-item.png)

1. 화면 오른쪽의 **속성** 탭에서 **필드 편집**을 선택 합니다.

1. **필드** 창에서 줄임표를 선택 하 고 **사용자 지정 카드 추가**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 사용자 지정 카드를 추가 하는 ![명령](media/working-with-references/form-customcard.png)

    새 카드가 양식 컨트롤의 맨 아래에 나타납니다.

1. 모든 텍스트를 표시 하기 위해 필요에 따라 카드 크기를 조정 합니다.

    > [!div class="mx-imgBorder"]
    > ![삽입 된 사용자 지정 카드, 공백](media/working-with-references/form-inserted-customcard.png)

1. **레이블** 컨트롤을 사용자 지정 카드에 삽입 한 다음 레이블의 **Text** 속성을 갤러리에서 사용한 수식으로 설정 합니다.

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > 레이블 컨트롤의 소유자 필드를 표시 하는 사용자 지정 카드를 ![](media/working-with-references/form-displayowner.png)

갤러리의 각 선택에 대해 레코드 소유자를 포함 하 여 계정에 대 한 추가 필드가 폼에 표시 됩니다. **패치** 단추를 사용 하 여 소유자를 변경 하는 경우 양식 컨트롤에도 해당 변경 내용이 표시 됩니다.

> [!div class="mx-imgBorder"]
> 갤러리의 변경 내용에 응답 하는 양식 컨트롤을 보여 주는 ![애니메이션](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>고객의 필드 표시

Common Data Service에서 **고객** 조회 필드는 **소유자**와 매우 유사한 또 다른 다형 조회입니다.

**Owner** 는 엔터티 당 하나로 제한 되지만 엔터티는 0 개 이상의 **고객** 조회 필드를 포함할 수 있습니다. Contact **system 엔터티는** **고객** 조회 필드인 **회사 이름** 필드를 포함 합니다.

> [!div class="mx-imgBorder"]
> 회사 이름 필드를 표시 하는 연락처 엔터티를 필요 하지 않은 고객 데이터 형식으로 ![](media/working-with-references/customer-companyname.png)

새 필드에 대 한 **customer** 데이터 형식을 선택 하 여 더 많은 **고객** 조회 필드를 엔터티에 추가할 수 있습니다.

![필드를 만들 때 데이터 형식 목록의 고객 데이터 형식](media/working-with-references/customer-datatype.png)

**고객** 조회 필드는 **Accounts** 엔터티 또는 **연락처** 엔터티의 레코드를 참조할 수 있습니다. 이러한 엔터티를 사용 하 여 **istype** **사용 하는** 것이 좋습니다. 이제이를 데이터 원본으로 추가 하는 것이 좋습니다. **팀** 과 **사용자** 를 그대로 둘 수 있습니다.

> [!div class="mx-imgBorder"]
> 데이터 창의 계정, 팀, 사용자 및 연락처 엔터티를 ![](media/working-with-references/customer-datasources.png)

**고객** 및 **소유자** 필드를 처리 하는 것은 응용 프로그램을 복사 하는 것과 유사 합니다 (**파일** > 다른 이름으로 저장을 사용 하 여 다른 이름 **으로 저장**).

| 위치 | **Owner** 샘플 | **Customer** 샘플 |
|----------|-----------|------------------|
| 도중 | **소유자도** | **' 고객 이름 '** |
| 도중 | **못하게** | **계좌** |
| 도중 | **팀** | **문의처** |
| 갤러리의 **Items** 속성 | **계좌** | **문의처** |
| 양식의 **Items** 속성 | **계좌** | **문의처** |
| **패치의** 첫 번째 인수<br>단추의 **Onselect** 속성에서 | **계좌** | **문의처** |
| 라디오 **항목** 필터 속성 | **[&nbsp;"모두",&nbsp;"사용자",&nbsp;"팀"&nbsp;]** | **[&nbsp;"모두",&nbsp;"계정",&nbsp;"연락처"&nbsp;]** |
| Patch radio **Items** 속성 | **["사용자", "팀"]** | **["계정", "연락처"]** |
| 콤보 상자의 **Visible** 속성 | **"사용자"** 및 **"팀"** | " **계정"** 및 **"연락처"** |

예를 들어 새 갤러리에는 다음 **항목** 속성이 있어야 합니다.

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> 간단한 변경 내용을 적용 하 여 소유자 앱에서 파생 된 고객 앱 ![](media/working-with-references/customer-simple-update.png)

**Customer** 와 **Owner** 의 두 가지 중요 한 차이점에는 갤러리와 폼의 수식에 대 한 업데이트가 필요 합니다.

1. **계정** 및 **연락처** 간의 일대다 관계는 이름으로 이러한 엔터티 형식을 참조할 때 우선적으로 적용 됩니다. **계정**대신 **\[\@계정]** 을 사용 합니다. **연락처**대신 **\[\@연락처]** 를 사용 합니다. [전역 명확성 연산자](functions/operators.md#disambiguation-operator)를 사용 하 여 **istype** 및 고 지 수에서 엔터티 형식을 참조 **하 고 있는지**확인 합니다. 이 문제는 갤러리 및 폼 컨트롤의 레코드 컨텍스트에서만 존재 합니다.

1. **Owner** 필드에는 값이 있어야 하지만 **Customer** 필드는 *비워*둘 수 있습니다. 형식 이름이 없는 올바른 결과를 표시 하려면 [ **isblank** 함수](functions/function-isblank-isempty.md)를 사용 하 여이 사례를 테스트 하 고 대신 빈 텍스트 문자열을 표시 합니다.

이러한 변경 내용에는 모두 폼의 사용자 지정 카드와 갤러리 레이블 컨트롤의 **Text** 속성에 표시 되는 동일한 수식이 있습니다.

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> 갤러리에서 자막 레이블 컨트롤의 Text 속성으로 업데이트를 ![](media/working-with-references/customer-update.png)

이러한 변경 내용으로 **연락처** 엔터티에서 **회사 이름** 필드를 보고 변경할 수 있습니다.

> [!div class="mx-imgBorder"]
> 연락처를 선택 하 여 다른 컨트롤과 폼을 변경 하는 방법을 보여 주는 ![애니메이션](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>조회 필드 관련 이해

**관련** 조회 필드는이 항목에서 이미 작업 한 필드와는 약간 다릅니다. 먼저이 항목에서 설명 하는 패턴을 적용 한 다음 다른 트릭을 학습 합니다.

간단히 **팩스** 엔터티를 사용 하 여 시작할 수 있습니다. 이 엔터티에는 **계정**, **연락처**및 기타 엔터티를 참조할 수 있는 조회 필드와 **관련** 된 다형성이 있습니다. 앱을 사용 하 여 **고객** 을 위해 앱을 수정 하 고 **팩스**를 수정할 수 있습니다.

| 위치 | **Customer** 샘플 | **팩스** 샘플 |
|----------|-----------|------------------|
| 도중 | **' 고객 이름 '** | **관련** |
| 갤러리의 **Items** 속성 | **문의처** | **없으며** |
| 양식의 **Items** 속성 | **문의처** | **없으며** |
| **패치의** 첫 번째 인수<br> 단추의 **Onselect** 속성에서 | **문의처** | **없으며** |

이번에는 **팩스**에 대해 이번에는 데이터 원본을 추가 해야 합니다. **보기** 탭에서 **데이터 원본**을 선택 합니다.

> [!div class="mx-imgBorder"]
> 계정, 팀, 사용자, 연락처 및 팩스 엔터티를 보여 주는 데이터 창 ![](media/working-with-references/faxes-datasources.png)

**와 관련** 하 여 중요 한 차이점은 **계정** 및 **연락처**에 국한 되지 않는다는 것입니다. 실제로 엔터티 목록은 사용자 지정 엔터티로 확장할 수 있습니다. 대부분의 앱은 수정 없이이 지점을 수용할 수 있지만 갤러리와 폼의 레이블에 대 한 수식을 업데이트 해야 합니다.

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
> 조회와 관련 하 여 부제목 컨트롤의 업데이트 된 텍스트 속성 ![](media/working-with-references/regarding-label.png)

이러한 변경을 수행한 후에는 **소유자** 와 **고객** 조회를 수행한 것 처럼 **관련** 조회를 사용 합니다.

> [!div class="mx-imgBorder"]
> 갤러리에서 항목을 선택 하 여 다른 컨트롤과 폼을 변경 하는 방법을 보여 주는 ![애니메이션](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>관련 관계 이해

와 **관련** 하 여은 다 대 일 관계를 포함 하기 때문에 **소유자** 와 **고객과** 다릅니다. 정의에 따라 역방향, 일 대 다 관계를 사용 하면 **첫 번째 (계정)을 작성할 수 있습니다. 팩스**.

을 (를) 백업 하 고 엔터티 정의를 살펴보겠습니다. Common Data Service **팩스**, **작업**, **전자 메일**, **메모**, **전화 통화**, **문자**및 **채팅** 등의 엔터티는 [*활동*](../../developer/common-data-service/activity-entities.md)으로 지정 됩니다. [사용자 고유의 사용자 지정 활동 엔터티](../../developer/common-data-service/custom-activities.md)를 만들 수도 있습니다. 활동 엔터티를 보거나 만들 때 해당 설정이 **추가 설정**아래에 나타납니다.

![엔터티를 만들 때 활동 엔터티 설정](media/working-with-references/activity-entitytype.png)

다른 엔터티는 엔터티의 설정에서 *활동 작업* 으로 사용 하도록 설정 된 경우 활동 엔터티와 관련 될 수 있습니다. **계정**, **연락처**및 기타 많은 표준 엔터티는 다시 지정 됩니다 ( **더 많은 설정**에서).

![엔터티를 만들 때의 작업 작업 설정](media/working-with-references/activity-entityuse.png)

모든 활동 엔터티와 활동 태스크 엔터티에는 암시적인 관계가 있습니다. 화면 위쪽에서 필터를 **모두** 로 변경 하는 경우 **팩스** 엔터티를 선택 하 고 **관계** 탭을 선택 하면 **관련** 조회 대상이 될 수 있는 모든 엔터티가 표시 됩니다.

> [!div class="mx-imgBorder"]
> 다 대 일 관계를 표시 하는 팩스 엔터티의 관계를 ![](media/working-with-references/activity-manytoone.png)

**계정** 엔터티에 대 한 관계를 표시 하는 경우 **관련** 조회 필드의 원본으로 사용할 수 있는 모든 엔터티가 표시 됩니다.

> [!div class="mx-imgBorder"]
> 일 대 다 관계에 대 한 관계를 보여 주는 계정 엔터티의 관계를 ![](media/working-with-references/activity-onetomany.png)

무엇을 의미 하나요?

- 수식을 작성 하는 경우 활동 엔터티 목록이 고정 되지 않은 것을 고려해 야 하며, 직접 만들 수도 있습니다. 수식이 예상치 못한 활동 엔터티를 적절 하 게 처리 해야 합니다.
- 활동 태스크와 활동에는 일 대 다 관계가 있습니다. 계정과 관련 된 모든 팩스를 쉽게 요청할 수 있습니다.

앱에서이 개념을 탐색 하려면 다음을 수행 합니다.

1. 다른 화면을 추가 합니다.

    > [!div class="mx-imgBorder"]
    > 빈 화면을 삽입 ![](media/working-with-references/activitypointer-newscreen.png)

1. 갤러리 컨트롤을 삽입 하 고 크기를 조정한 다음 화면의 왼쪽으로 이동 합니다.

1. 화면 오른쪽의 **속성** 탭에서 갤러리의 **항목** 을 **계정**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 속성 창에서 항목을 계정으로 설정 ![](media/working-with-references/activitypointer-accounts.png)

1. 갤러리의 레이아웃을 **제목**으로 설정 하 고 제목 필드를 **계정 이름**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 속성 창에서 레이아웃을 갤러리 컨트롤의 제목으로 설정 ![](media/working-with-references/activitypointer-account-name.png)

1. 두 번째 갤러리를 추가 하 고 크기를 조정한 다음 화면 오른쪽으로 이동 합니다.

1. 새 갤러리의 **Items** 속성을 `Gallery2.Selected.Faxes`로 설정 합니다.

    이 단계에서는 지정 된 계정에 대해 필터링 된 팩스 목록을 반환 합니다.

    > [!div class="mx-imgBorder"]
    > 팩스를 표시 하는 갤러리의 Items 속성을 설정 ![](media/working-with-references/activitypointer-faxes.png)

1. 갤러리의 레이아웃을 **제목 및 부제**로 설정 하 고 제목 필드를 표시 하도록 **제목 필드를** 설정 합니다 (소문자 **제목**).

    > [!div class="mx-imgBorder"]
    > 제목을 제목 필드에 설정 ![](media/working-with-references/activitypointer-subject.png)

계정 목록에서 항목을 선택 하면 팩스 목록에 해당 계정에 대 한 팩스도 표시 됩니다.

> [!div class="mx-imgBorder"]
> 계정 갤러리에서 선택 항목을 보여 주는 ![애니메이션은 팩스 목록을 구동](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>활동 엔터티

이전 섹션에서 설명 하는 것 처럼 계정의 모든 팩스를 표시할 수 있습니다. 그러나 팩스, 전자 메일 메시지, 전화 통화 및 기타 상호 작용을 포함 하 여 계정에 대 한 모든 작업을 표시할 수도 있습니다.

두 번째 시나리오에서는 **활동** 엔터티를 사용 합니다. 오른쪽 위 모서리에서 **모두** 를 설정 하 여이 엔터티를 표시 하 여 엔터티 목록에서 필터를 제거할 수 있습니다.

> [!div class="mx-imgBorder"]
> 활동 엔터티를 표시 하는 엔터티 목록 ![](media/working-with-references/activitypointer-entity.png)

**활동** 엔터티는 특수 합니다. **팩스** 엔터티에 레코드를 추가할 때마다 시스템은 모든 활동 엔터티에 공통 된 필드를 사용 하 여 **활동** 엔터티에 레코드를 만듭니다. 이러한 필드 중 **제목** 은 가장 흥미로운 항목 중 하나입니다.

이전 예제에서 한 줄만 변경 하 여 모든 작업을 표시할 수 있습니다. `Gallery2.Selected.Faxes`를 `Gallery2.Selected.Activities`으로 바꿉니다.

> [!div class="mx-imgBorder"]
> 두 번째 갤러리의 항목 ![변경 속성을 팩스에서 작업으로 변경](media/working-with-references/activitypointer-gallery.png)

레코드는 **활동** 엔터티에서 가져오지만, 그럼에도 불구 하 고 **istype** 함수를 사용 하 여 해당 활동의 종류를 식별할 수 있습니다. 엔터티 형식에서 **istype** 를 사용 하기 전에 데이터 원본을 추가 해야 합니다.

> [!div class="mx-imgBorder"]
> IsType 함수에 필요한 모든 엔터티를 보여 주는 데이터 창 ![](media/working-with-references/activity-datasources.png)

이 수식을 사용 하 여 갤러리 내에서 레이블 컨트롤에 레코드 형식을 표시할 수 있습니다.

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> 텍스트 속성을 수식으로 설정 ![팩스, 전화 통화 및 기타 작업에 대 한 정보를 표시](media/working-with-references/activitypointer-type.png)

또한 형식 지정을 **사용 하 여 특정** 형식의 필드에 액세스할 수 있습니다. 예를 들어이 수식은 각 활동의 유형을 결정 하 고 전화 통화의 **경우 전화 번호 엔터티에서 전화** 번호와 통화 방향을 표시 합니다.

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
> 전화 통화에 대 한 추가 정보를 사용 하 여 확장 된 텍스트 속성을 ![](media/working-with-references/activitypointer-phonecall.png)

따라서 앱은 전체 활동 목록을 표시 합니다. **제목** 필드는 수식에서 해당 활동을 고려 하는지 여부에 관계 없이 모든 유형의 활동에 대해 표시 됩니다. 사용자가 알고 있는 활동 유형에 대해 해당 유형 이름과 각 활동에 대 한 유형별 정보를 표시할 수 있습니다.

> [!div class="mx-imgBorder"]
> 여러 종류의 활동에 대 한 정보를 보여 주는 완료 된 화면 ![](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Notes 엔터티

지금까지 모든 **관련** 예제는 활동을 기반으로 하지만 **Notes** 엔터티는 다른 사례를 나타냅니다.

엔터티를 만들 때 첨부 파일을 사용 하도록 설정할 수 있습니다.

> [!div class="mx-imgBorder"]
> 엔터티](media/working-with-references/notes-entity.png)를 만들 때 첨부 파일 및 메모를 사용 하도록 설정 ![

첨부 파일 사용 확인란을 선택 하는 경우이 그래픽이 **Accounts** 엔터티에 대해 보여 주는 것 처럼 **Notes** 엔터티와 **관련** 된 관계를 만듭니다.

> [!div class="mx-imgBorder"]
> 일 대 다 관계를 통해 메모에 대 한 관계를 보여 주는 ![계정 엔터티](media/working-with-references/notes-relationships.png)

이러한 차이를 제외 하 고 활동을 사용 하는 것과 동일한 방식으로 **관련** 조회를 사용 합니다. 첨부 파일에 대해 사용 하도록 설정 된 엔터티는 다음 예제와 같이 **메모**에 대 한 일 대 다 관계를 가집니다.

`First( Accounts ).Notes`

> [!NOTE]
> 이 문서를 작성할 당시 **Notes** 엔터티에 대 한 **관련** 조회는 사용할 수 없습니다. [ **관련** 항목] 필드를 기준으로 읽거나 필터링 할 수 없으며 **Patch**를 사용 하 여 필드를 설정할 수 없습니다.
>
> 그러나 역방향 **메모** 일 대 다 관계를 사용할 수 있으므로 첨부 파일이 활성화 된 레코드에 대 한 메모 목록을 필터링 할 수 있습니다. 또한 [**Relate**](functions/function-relate-unrelate.md) 함수를 사용 하 여 레코드의 **메모** 테이블에 메모를 추가할 수 있지만 다음 예제와 같이 메모를 먼저 만들어야 합니다.
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>활동 당사자

이 문서를 작성할 당시 캔버스 앱은 활동 당사자를 지원 하지 않습니다.