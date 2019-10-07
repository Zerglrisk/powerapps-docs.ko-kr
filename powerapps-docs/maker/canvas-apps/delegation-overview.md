---
title: 캔버스 앱에서 위임 이해 | Microsoft Docs
description: 위임을 사용하여 캔버스 앱에서 큰 데이터 집합을 효율적으로 처리합니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/05/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b03f60173ea09160677bd02adf8a91aae02c272d
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985656"
---
# <a name="understand-delegation-in-a-canvas-app"></a>캔버스 앱에서 위임 이해
PowerApps에는 캔버스 앱에서 데이터의 테이블을 필터링, 정렬 및 셰이핑 하기 위한 강력한 함수 집합이 포함 되어 있습니다. **[Filter](functions/function-filter-lookup.md)** , **[Sort](functions/function-sort.md)** 및 **[addcolumns](functions/function-table-shaping.md)** 함수는 몇 가지 이름을 갖습니다. 이러한 함수를 사용하여 사용자에게 필요한 정보에 대한 집중된 액세스 권한을 제공할 수 있습니다. 데이터베이스 배경 지식이 있는 사람들에게 이러한 함수를 사용하는 것은 데이터베이스 쿼리를 작성하는 것과 같습니다.

효율적인 앱을 빌드하는 핵심은 디바이스로 가져와야 하는 데이터의 양을 최소화하는 것입니다. 수백 만 개의 레코드 중에서 일부만 필요하거나, 또는 단일 집계 값이 수천 개의 레코드를 나타낼 수 있습니다. 또는 아마도 첫 번째 레코드 집합을 검색할 수 있고 나머지 데이터 집합은 사용자가 더 원한다는 제스처를 취할 때 검색됩니다. 집중하면 앱에서 필요한 처리량, 네트워크 대역폭을 현저하게 줄일 수 있어 셀룰러 네트워크를 통해 연결된 휴대폰에서도 사용자를 위해 더 신속하게 응답할 수 있습니다. 

*위임*은 PowerApps 수식의 표현이 네트워크를 통해 이동하는 데이터를 최소화할 필요성을 충족하는 곳입니다. 즉, PowerApps는 로컬에서 처리하기 위해 앱으로 데이터를 이동하는 것이 아니라 데이터의 처리를 데이터 원본으로 위임합니다.

복잡해지는 상황에서 이 문서가 있는 이유는 PowerApps 수식으로 표현할 수 있는 것 중에 모든 데이터 원본으로 위임할 수 없는 것도 있기 때문입니다. PowerApps 언어는 광범위한 숫자 및 텍스트 조작 기능과 함께 메모리의 전체 통합 문서에 완벽한 즉시 액세스할 수 있도록 설계된 Excel의 수식 언어를 흉내내고 있습니다. 결과적으로, PowerApps 언어는 SQL Server와 같은 강력한 데이터베이스 엔진을 포함해 대부분 데이터 원본이 지원할 수 있는 것보다 훨씬 풍부합니다.

**큰 데이터 집합을 작업하려면 위임할 수 있는 데이터 원본과 수식을 사용해야 합니다.** 앱 성능을 유지하고 사용자가 필요한 모든 정보에 액세스할 수 있게 하는 유일한 방법입니다. 위임이 불가능한 위치를 식별하는 위임 경고에 주의하세요. 작은 데이터 집합(500개 레코드 미만)을 사용하려는 경우 수식을 위임할 수 없다면 앱이 로컬로 처리를 수행할 수 있기 때문에 데이터 원본과 수식도 사용할 수 있습니다. 

> [!NOTE]
> 위임 경고는 이전에 "파란색 점" 제안으로 PowerApps에 플래그가 지정되었지만 위임 제안은 다시 경고로 분류된 이후에 지정되었습니다. 데이터 원본의 데이터가 500개의 레코드를 초과하여 함수가 위임될 수 없는 경우 PowerApps는 데이터를 모두 검색할 수 없으므로 앱에는 잘못된 결과가 포함될 수 있습니다. 위임 경고를 통해 올바른 결과가 포함되도록 앱을 관리할 수 있습니다.

## <a name="delegable-data-sources"></a>위임 가능한 데이터 원본
위임은 특정 테이블 형식 데이터 원본에 대해서만 지원 됩니다. 데이터 원본에서 위임을 지 원하는 경우 해당 [커넥터 설명서](https://docs.microsoft.com/connectors/) 는를 지원 합니다. 예를 들어 이러한 테이블 형식 데이터 원본은 가장 인기 있는 것 이며 위임을 지원 합니다.

- [Common Data Service](https://docs.microsoft.com/connectors/commondataservice/) 
- [SharePoint](https://docs.microsoft.com/connectors/sharepointonline/) 
- [SQL Server](https://docs.microsoft.com/connectors/sql/) 

**응용 프로그램 데이터 원본에 정적 데이터 추가** 를 사용 하 여 가져온 Excel 통합 문서, 컬렉션 및 컨텍스트 변수에 저장 된 테이블은 위임이 필요 하지 않습니다. 이 모든 데이터는 이미 메모리에 있으며, 전체 PowerApps 언어를 적용할 수 있습니다.

## <a name="delegable-functions"></a>위임 가능 함수
다음 단계는 위임할 수 있는 수식만 사용하는 것입니다. 여기에는 위임할 수 있는 수식 요소가 포함됩니다. 그러나 모든 데이터 원본은 서로 다르며 일부는 이러한 요소를 지원하지 않습니다. 특정 수식에서 위임 경고를 확인합니다.

이러한 목록은 시간이 지남에 따라 변경됩니다. 위임에 더 많은 함수와 연산자를 지원하기 위해 노력하고 있습니다.

### <a name="filter-functions"></a>Filter 함수
**[Filter](functions/function-filter-lookup.md)** , **[Search](functions/function-filter-lookup.md)** 및 **[LookUp](functions/function-filter-lookup.md)** 을 위임할 수 있습니다.  

**Filter** 및 **LookUp** 함수 내에서 적합한 레코드를 선택하기 위해 테이블의 열에서 다음을 사용할 수 있습니다.

* **[And](functions/function-logicals.md)** ( **[&&](functions/operators.md)** 포함), **[Or](functions/function-logicals.md)** ( **[||](functions/operators.md)** 포함), **[Not](functions/function-logicals.md)** ( **[!](functions/operators.md)** 포함)
* **[In](functions/operators.md)**
* **[=](functions/operators.md)** , **[<>](functions/operators.md)** , **[>=](functions/operators.md)** , **[<=](functions/operators.md)** , **[>](functions/operators.md)** , **[<](functions/operators.md)**
* **[+](functions/operators.md)** , **[-](functions/operators.md)**
* **[TrimEnds](functions/function-trim.md)**
* **[IsBlank](functions/function-isblank-isempty.md)**
* **[StartsWith](functions/function-startswith.md)** ,  **[EndsWith](functions/function-startswith.md)**
* 컨트롤 속성과 [전역 및 컨텍스트 변수](working-with-variables.md) 등의 모든 레코드 전체에서 동일한 상수 값입니다.

모든 레코드에 대한 상수 값으로 평가하는 수식의 일부를 사용할 수도 있습니다. 예를 들어 **Left (Language (), 2)** , **Date (2019, 3, 31)** 및 **Today ()** 는 레코드의 열에 종속 되지 않으므로 모든 레코드에 대해 동일한 값을 반환 합니다. 이러한 값은 데이터 원본에 상수로 전송 될 수 있으며 위임을 차단 하지 않습니다. 

위의 목록에는 이러한 주목할 만한 항목이 포함되지 않습니다.

* **[If](functions/function-if.md)**
* **[*](functions/operators.md)** , **[/](functions/operators.md)** , **[Mod](functions/function-mod.md)**
* **[Concatenate](functions/function-concatenate.md)** ( **[&](functions/operators.md)** 포함)
* **[ExactIn](functions/operators.md)**
* 문자열 조작 함수: **[Lower](functions/function-lower-upper-proper.md)** , **[Upper](functions/function-lower-upper-proper.md)** , **[Left](functions/function-left-mid-right.md)** , **[Mid](functions/function-left-mid-right.md)** , **[Len](functions/function-left-mid-right.md)** , ...
* 연산 **[위치](functions/signals.md)** , **[가속](functions/signals.md)** , **[나침반](functions/signals.md)** ...
* 일시적 **[Rand](functions/function-rand.md)** , ...
* [컬렉션](working-with-variables.md)

### <a name="sorting-functions"></a>정렬 함수
**[Sort](functions/function-sort.md)** 및 **[SortByColumns](functions/function-sort.md)** 를 위임할 수 있습니다.

**Sort**에서 이 수식은 단일 열의 이름에 불과하며 다른 연산자 또는 함수를 포함할 수 없습니다.

### <a name="aggregate-functions"></a>집계 함수
**[Sum](functions/function-aggregates.md)** , **[Average](functions/function-aggregates.md)** , **[Min](functions/function-aggregates.md)** 및 **[Max](functions/function-aggregates.md)** 를 위임할 수 있습니다. 지금은 제한된 수의 데이터 원본만 이 위임을 지원합니다. 자세한 내용은 [위임 목록](delegation-list.md)을 확인하세요.

**[CountRows](functions/function-table-counts.md)** , **[CountA](functions/function-table-counts.md)** 및 **[Count](functions/function-table-counts.md)** 등의 계산 함수는 위임할 수 없습니다.

**[StdevP](functions/function-aggregates.md)** 및 **[VarP](functions/function-aggregates.md)** 등의 기타 집계 함수는 위임할 수 없습니다.

### <a name="table-shaping-functions"></a>테이블 셰이핑 함수

**[Addcolumns](functions/function-table-shaping.md)** , **[dropcolumns](functions/function-table-shaping.md)** , **[RenameColumns](functions/function-table-shaping.md)** 및 **[showcolumns](functions/function-table-shaping.md)** 는 부분적으로 위임을 지원 합니다.  해당 인수의 수식을 위임할 수 있습니다.  그러나 이러한 함수의 출력에는 위임 되지 않은 레코드 제한이 적용 됩니다.

이 예에서와 같이 결정자는 **Addcolumns** 및 **LookUp** 을 사용 하 여 한 테이블에서 다른 테이블로 정보를 병합 하는 경우가 많습니다. 일반적으로 데이터베이스 용어에서 조인 이라고 합니다.

```powerapps-dot
AddColumns( Products, 
    "Supplier Name", 
    LookUp( Suppliers, Suppliers.ID = Product.SupplierID ).Name 
)
```

**제품** 및 **공급자** 가 데이터 원본에 위임 가능한 수 있지만 **조회가** 위임 가능한 함수 이더라도 **addcolumns** 함수의 출력은 위임 가능한 되지 않습니다. 전체 수식의 결과는 **Products** 데이터 원본의 첫 부분으로 제한 됩니다. **LookUp** 함수와 해당 데이터 원본이 위임 가능하기 때문에 **Suppliers**에 대한 일치 항목은 크더라도 데이터 원본 어디서든 찾을 수 있습니다. 

이러한 방식으로 **Addcolumns** 를 사용 하는 경우 **조회** 는 **제품**의 각 첫 레코드에 대 한 데이터 원본을 개별적으로 호출 해야 하므로 많은 네트워크 chatter 발생 합니다. **공급자** 가 작아서 자주 변경 되지 않는 경우 [**OnStart**](functions/signals.md) 에서 **Collect** 함수를 호출 하 여 앱이 시작 될 때 해당 데이터 원본을 캐시 합니다. 다른 방법으로, 사용자가 관련 레코드를 요청 하는 경우에만 관련 레코드를 가져오도록 응용 프로그램을 재구성할 수 있습니다.  
 
## <a name="non-delegable-functions"></a>위임 불가능 함수
모든 기타 함수는 다음 중요 함수를 포함해 위임을 지원하지 않습니다.

* **[First](functions/function-first-last.md)** , **[FirstN](functions/function-first-last.md)** , **[Last](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)**
* **[Choices](functions/function-choices.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Collect](functions/function-clear-collect-clearcollect.md)** , **[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)** , **[RemoveIf](functions/function-remove-removeif.md)** , **[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)** , **[Ungroup](functions/function-groupby.md)**

## <a name="non-delegable-limits"></a>비-위임 가능한 한계
위임할 수 없는 수식은 로컬에서 처리됩니다. 이를 통해 PowerApps 수식 언어의 전체 범위를 사용할 수 있습니다. 하지만 먼저 네트워크를 통해 많은 양의 데이터를 검색해야 할 수 있으므로, 모든 데이터를 디바이스로 가져와야 하는 수고로움이 있습니다. 시간이 걸려서 앱이 느리거나 충돌한다는 인상을 줄 수 있습니다.

이를 방지 하기 위해 PowerApps는 로컬에서 처리할 수 있는 데이터 양에 제한을 적용 합니다. 기본적으로 500 레코드가 있습니다.  작은 데이터 집합에 대한 전체 액세스 권한을 계속 유지하고 부분 결과를 확인하여 큰 데이터 집합의 사용을 한정할 수 있도록 이 숫자를 선택했습니다.

사용자에게 혼란을 일으킬 수 있기 때문에 이 기능을 사용할 때는 각별하게 주의해야 합니다. 예를 들어 수백만 개의 레코드를 포함하는 데이터 원본에 대해 위임할 수 없는 선택 수식과 함께 **Filter** 함수를 사용합니다. 필터링이 로컬로 수행되기 때문에 처음 500개의 레코드만 스캔됩니다. 원하는 레코드가 레코드 501, 또는 500,001인 경우 **Filter**에 의해 사용되거나 반환되지 않습니다.

집계 함수는 혼란을 일으킬 수도 있습니다. 이 동일한 수백만 개의 레코드 데이터 원본의 열에 대해 **Average**를 사용합니다. **Average**는 아직 위임할 수 없으므로, 처음 500개의 레코드의 평균만을 계산합니다. 주의하지 않으면 부분 답변은 앱 사용자에 의해 전체 답변으로 잘못 해석될 수 있습니다.

## <a name="changing-the-limit"></a>제한 변경
500은 레코드의 기본 숫자이지만 전체 앱에서 이 번호를 변경할 수 있습니다.

1. **파일** 탭에서 **앱 설정**을 선택합니다.
2. **고급 설정**에서 **비 위임 가능한 쿼리 설정의 데이터 행 제한을** 1에서 2000로 변경 합니다.

경우에 따라 2,000(아니면 1,000 또는 1,500)이 시나리오의 필요를 충족하는지 알 수 있습니다. 신중하게, 시나리오에 맞도록 숫자를 늘릴 수 있습니다. 이 숫자를 늘릴수록 앱의 성능은 저하될 수 있습니다. 열이 많이 있는 넓은 테이블의 경우 특히 그렇습니다. 그러나 가장 적합한 답은 가능한 만큼 위임하는 것입니다.

앱이 대규모 데이터 집합으로 확장될 수 있도록 하려면 이 설정을 1로 줄입니다. 위임할 수 없는 항목이 있으면 앱을 테스트할 때 쉽게 감지할 수 있는 단일 레코드를 반환합니다. 이를 통해 개념 증명 앱을 프로덕션 환경에서 사용하려는 경우 예기치 않은 문제를 방지할 수 있습니다.

## <a name="delegation-warnings"></a>위임 경고
위임된 내용 및 위임되지 않은 내용을 쉽게 확인하기 위해 위임될 수 없는 항목이 포함된 수식의 만들 때 PowerApps에서는 경고(노란색 삼각형)를 표시합니다.

위임 경고는 위임 가능한 데이터 원본에서 작동하는 수식에만 표시됩니다. 경고가 표시되지 않고 수식이 제대로 위임되지 않은 경우 이 항목의 앞에서 [위임 가능한 데이터 원본](delegation-overview.md#delegable-data-sources) 목록과 비교하여 데이터 원본 형식을 확인하세요.

## <a name="examples"></a>예
예를 들어 **[dbo].[Fruit]** 라는 SQL Server 테이블을 기반으로 하는 세 개의 화면 앱을 자동으로 생성합니다. 앱을 생성 하는 방법에 대 한 자세한 내용은 SQL Server에 [대 한 Common Data Service 관련 항목](data-platform-create-app.md) 에서 유사한 원칙을 적용할 수 있습니다.

![3개 화면 앱](./media/delegation-overview/products-afd.png)

갤러리의 **Items** 속성은 둘 다 위임할 수 있는 **SortByColumns** 및 **Search** 함수가 포함된 수식으로 설정됩니다.

검색 상자에 **"Apple"** 을 입력합니다.

앱이 검색 요청을 처리하기 위해 SQL Server와 통신하는 경우 행진하는 점이 일시적으로 화면의 위쪽에 표시됩니다. 데이터 원본에 수백만 개의 레코드가 포함되는 경우에도 검색 조건을 충족하는 모든 레코드가 표시됩니다.

![검색 텍스트 입력 컨트롤](./media/delegation-overview/products-apple.png)

**Search** 함수가 텍스트 열 어디에서나 표시되기 때문에 검색 결과에는 **"Apples"** , **"Crab apples"** 및 **"Pineapple"** 이 포함됩니다. 과일 이름의 시작 부분에서 검색 팀이 포함된 레코드만을 찾으려는 경우 더 복잡한 검색 용어를 사용하여 다른 위임 가능한 함수인 **Filter**를 사용할 수 있습니다. (편의상 **SortByColumns** 호출을 제거합니다.)

![SortByColumns 호출 제거](./media/delegation-overview/products-apple-delegationwarning.png)

새 결과에는 **"Apples"** 가 포함되지만 **"Crab apples"** 또는 **"Pineapple"** 은 포함되지 않습니다.  그러나 노란색 삼각형이 갤러리 옆에 표시되고(왼쪽 탐색 모음에 썸네일이 표시되는 경우 화면 썸네일에 표시됨) 파란색 물결선이 수식의 일부 아래에 표시됩니다. 이러한 각 요소는 경고를 나타냅니다. 갤러리 옆에 있는 노란색 삼각형을 마우스로 가리키면 다음과 같은 메시지가 나타납니다.

![위임 경고 마우스로 가리키기](./media/delegation-overview/products-apple-yellowwarning.png)

SQL Server는 위임 가능한 데이터 원본이고 **Filter**는 위임 가능한 함수입니다. 하지만 **Mid** 및 **Len**은 데이터 원본에 위임될 수 없습니다.

하지만 가능했습니다. 가능했다고 봐야죠. 이런 이유로 인해 빨간색 물결선이 아닌 오류가 됩니다.

- 테이블에 500개 미만의 레코드가 포함되는 경우 수식은 완벽하게 작동합니다. 모든 레코드를 디바이스로 불러 왔으며 **Filter**가 로컬에 적용되었습니다.
- 테이블에 500개를 초과하는 레코드가 포함되는 경우 수식은 조건에 일치하는 경우에도 레코드 501 이상을 반환하지 않습니다.
