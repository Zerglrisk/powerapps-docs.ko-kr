---
title: ForAll 함수 | Microsoft Docs
description: PowerApps의 ForAll 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3d53a721e5abba3ce7e844420d9e8415b908cdde
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680216"
---
# <a name="forall-function-in-powerapps"></a>PowerApps의 ForAll 함수
[테이블](../working-with-tables.md)의 모든 [레코드](../working-with-tables.md#records)에 대해 값을 계산하고 작업을 수행합니다.

## <a name="description"></a>설명
**ForAll** 함수는 테이블의 모든 레코드에 대한 수식을 계산합니다.  수식은 값을 계산하고 데이터 수정이나 연결 작업과 같은 작업을 수행할 수 있습니다.  [ **With** 함수](function-with.md) 를 사용 하 여 단일 레코드에 대 한 수식을 계산 합니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

### <a name="return-value"></a>반환 값
각 수식 평가의 결과는 입력 테이블과 동일한 순서로 테이블에 반환됩니다.

수식의 결과가 단일 값이면 결과 테이블은 단일 열 테이블이 됩니다.  수식의 결과가 레코드인 경우, 결과 레코드와 동일한 열이 있는 레코드가 결과 테이블에 포함됩니다.  

수식의 결과가 *공백* 값이면 해당 입력 레코드에 대한 결과 테이블에 레코드가 없습니다.  이런 경우 결과 테이블에는 원본 테이블보다 적은 레코드가 있습니다.

### <a name="taking-action"></a>작업 수행
수식에는 작업(예: **[Patch](function-patch.md)** 및 **[Collect](function-clear-collect-clearcollect.md)** 함수를 사용하여 데이터 원본의 레코드를 수정하는 작업)을 수행하는 함수가 포함될 수 있습니다.  수식은 연결에 관한 메서드를 호출할 수도 있습니다.  [ **;** 연산자](operators.md)를 사용하면 레코드당 여러 작업을 수행할 수 있습니다. **ForAll** 함수의 대상인 테이블은 수정할 수 없습니다.

수식을 작성할 때는 레코드가 임의의 순서로 처리될 수 있고 가능한 경우에는 병렬로 처리될 수 있음에 유의하십시오.  테이블의 첫 번째 레코드는 마지막 레코드 다음에 처리될 수 있습니다.  순서 종속성을 피하도록 주의하십시오.  이러한 이유로 인해, **ForAll** 함수 내에서 **[UpdateContext](function-updatecontext.md)** , **[Clear](function-clear-collect-clearcollect.md)** 및 **[ClearCollect](function-clear-collect-clearcollect.md)** 함수를 사용할 수 업습니다. 해당 함수는 이러한 효과에 영향을 받기 쉬운 변수를 보유하는 데 쉽게 사용될 수 있기 때문입니다.  **[Collect](function-clear-collect-clearcollect.md)** 를 사용할 수 있지만 레코드가 추가되는 순서는 정의되지 않습니다.

데이터 원본을 수정하는 **Collect**, **Remove** 및 **Update**를 비롯한 몇 가지 함수는 변경된 데이터 원본을 반환 값으로 반환합니다.  이러한 반환 값이 **ForAll** 테이블의 모든 레코드에 대해 반환되면 커지고 상당한 리소스를 소비할 수 있습니다.  또한 이러한 반환 값이 필요한 값이 아닐 수도 있습니다. **ForAll**은 병렬 작업이 가능하고 이러한 함수의 파생 작업을 그 결과를 얻는 것으로부터 분리할 수 있기 때문입니다.  다행이 **ForAll**의 반환 값이 실제로 사용되지 않으면(데이터 수정 함수의 경우) 반환 값이 생성되지 않아서 리소스나 순서 관련 문제가 없습니다.  하지만 **ForAll**의 결과를 사용하고 데이터 원본을 반환하는 함수 중 하나를 사용하는 경우, 결과를 구조화하는 방법에 대해 신중히 생각하고, 작은 데이터 집합부터 먼저 시도해보십시오.  

### <a name="alternatives"></a>대안
Power Apps의 많은 함수는 단일 열 테이블을 사용 하 여 한 번에 두 개 이상의 값을 처리할 수 있습니다.  예를 들어, **Len** 함수는 **ForAll** 함수와 같은 방식으로 텍스트 값 테이블을 처리하여 긴 테이블을 반환할 수 있습니다.  이렇게 하면 많은 경우 **ForAll**을 사용할 필요가 없어지고, 효율이 높아지고, 읽기가 쉬워집니다.

또 다른 고려 사항은, **ForAll**은 위임이 불가능한 반면 **Filter**와 같은 다른 함수는 위임이 가능하다는 점입니다.  

### <a name="delegation"></a>위임
[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>구문
**ForAll**( *Table*, *Formula* )

* *Table* - 필수 항목입니다. 작업이 수행될 테이블입니다.
* *Formula* - 필수 항목입니다.  *Table*의 모든 레코드를 평가할 수식입니다.

## <a name="examples"></a>예
### <a name="calculations"></a>계산
다음 예에서는 **Squares**라는 [데이터 원본](../working-with-data-sources.md)을 사용합니다.

![](media/function-forall/squares.png)

이 데이터 원본을 컬렉션으로 만들려면 **Button** 컨트롤의 **OnSelect** 속성을 다음 수식으로 설정하고 미리 보기 모드를 연 다음 단추를 클릭하거나 탭합니다.

`ClearCollect( Squares, [ "1", "4", "9" ] )`

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **ForAll(&nbsp;Squares, Sqrt(&nbsp;Value&nbsp;)&nbsp;)**<br><br>**Sqrt(&nbsp;Squares&nbsp;)** |입력 테이블의 모든 레코드에 대해 **Value** 열의 제곱근을 계산합니다.  **Sqrt** 함수는 단일 열 테이블에도 사용할 수 있으므로 **ForAll**을 사용하지 않고 이 예제를 수행할 수 있습니다. |<style> img { max-width: none } </style> ![](media/function-forall/sqrt.png) |
| **ForAll(&nbsp;Squares, Power(&nbsp;Value,&nbsp;3&nbsp;)&nbsp;)** |입력 테이블의 모든 레코드에 대해 **Value** 열을 세 제곱으로 올립니다.  **Power** 함수는 단일 열 테이블을 지원하지 않습니다. 따라서 이 경우 **ForAll**을 사용해야 합니다. |<style> img { max-width: none } </style> ![](media/function-forall/power3.png) |

### <a name="using-a-connection"></a>연결 사용
다음 예에서는 **Expressions**라는 [데이터 원본](../working-with-data-sources.md)을 사용합니다.

![](media/function-forall/translate.png)

이 데이터 원본을 컬렉션으로 만들려면 **Button** 컨트롤의 **OnSelect** 속성을 다음 수식으로 설정하고 미리 보기 모드를 연 다음 단추를 클릭하거나 탭합니다.

`ClearCollect( Expressions, [ "Hello", "Good morning", "Thank you", "Goodbye" ] )`

이 예제에는 [Microsoft Translator](../connections/connection-microsoft-translator.md) 연결도 사용됩니다.  이 연결을 앱에 추가하려면 [연결 관리](../add-manage-connections.md) 방법에 대한 문서를 참조하세요.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "es" ) )** |Expressions 테이블에 있는 모든 레코드의 **Value** 열 콘텐츠를 스페인어(약어: "es")로 번역합니다. |<style> img { max-width: none } </style> ![](media/function-forall/translate-es.png) |
| **ForAll( Expressions, MicrosoftTranslator.Translate( Value, "fr" ) )** |Expressions 테이블에 있는 모든 레코드의 **Value** 열 콘텐츠를 프랑스어(약어: "fr")로 번역합니다. |<style> img { max-width: none } </style> ![](media/function-forall/translate-fr.png) |

### <a name="copying-a-table"></a>테이블 복사
데이터를 필터링하고, 형성하고, 정렬하고, 조작해야 하는 경우가 있습니다.  Power Apps는 **필터**, **Addcolumns**및 **Sort**와 같이이 작업을 수행 하기 위한 다양 한 기능을 제공 합니다.  Power Apps는 각 테이블을 값으로 처리 하 여 수식을 통해 이동 하 고 쉽게 사용할 수 있도록 합니다.      

나중에 사용하기 위해 이러한 결과의 복사본을 만들어야 하는 경우가 있습니다.  하나의 데이터 원본에서 다른 데이터 원본으로 정보를 이동해야 하는 경우도 있습니다.  Power Apps는 데이터를 복사 하는 **Collect** 함수를 제공 합니다.

단 복사본을 만들기 전에 정말 필요한지 신중히 생각해야 합니다.  수식을 사용하여 필요에 따라 기본 데이터 원본을 필터링하고 형성하면 많은 상황이 해결될 수 있습니다. 복사본을 생성에는 다음과 같은 단점이 있습니다.

* 동일한 정보의 복사본이 두 개이면 그 중 하나가 동기화되지 않을 수 있습니다.  
* 복사본을 만드는 데 컴퓨터 메모리, 네트워크 대역폭 및/또는 시간이 많이 소비될 수 있습니다.  
* 대부분의 데이터 원본은 복사를 위임할 수 없기 때문에 이동할 수 있는 데이터의 양이 제한됩니다.      

다음 예에서는 **Products**라는 [데이터 원본](../working-with-data-sources.md)을 사용합니다.

![](media/function-forall/prod.png)

이 데이터 원본을 컬렉션으로 만들려면 **Button** 컨트롤의 **OnSelect** 속성을 다음 수식으로 설정하고 미리 보기 모드를 연 다음 단추를 클릭하거나 탭합니다.

```powerapps-dot
ClearCollect( Products, 
    Table( 
        { Product: "Widget",    'Quantity Requested': 6,  'Quantity Available': 3 }, 
        { Product: "Gadget",    'Quantity Requested': 10, 'Quantity Available': 20 },
        { Product: "Gizmo",     'Quantity Requested': 4,  'Quantity Available': 11 },
        { Product: "Apparatus", 'Quantity Requested': 7,  'Quantity Available': 6 } 
    )
)
```

여기서 목표는 제공되는 것보다 더 많이 요청된 항목만 포함된 파생 테이블을 사용하여 주문을 하는 것입니다.

![](media/function-forall/prod-order.png)  

이러한 작업은 몇 가지 다른 방법으로 수행할 수 있으며 모든 작업은 동일한 결과를 생성하지만 여러 가지 장단점이 있습니다.

#### <a name="table-shaping-on-demand"></a>주문형 테이블 형성
복사본을 만들지 마십시오.  어디서나 필요하면 다음 함수를 사용할 수 있습니다.

```powerapps-dot
// Table shaping on demand, no need for a copy of the result
ShowColumns( 
    AddColumns( 
        Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
        "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
    ), 
    "Product", 
    "Quantity To Order"
)
```

각 레코드의 **'Quantity Requested'** 및 **'Quantity Available'** 필드를 각각 사용하여 비교 및 빼기 연산을 수행하기 위해 **Filter** 및 **AddColumns** 함수를 사용하여 [레코드 범위](../working-with-tables.md#record-scope)가 만들어집니다.

이 예제에서는 **Filter** 함수를 위임할 수 있습니다.  이 작업은 수백만 개의 테이블 중 소수의 레코드만 해당되는 경우라도, 조건을 충족하는 모든 제품을 찾을 수 있기 때문에 중요합니다.  현재 **ShowColumns**와 **AddColumns**는 위임이 불가능하므로 주문해야 하는 실제 제품 수는 제한됩니다.  결과의 크기가 항상 비교적 작다는 것을 아는 경우에는 이런 접근 방식이 좋습니다.

또한 복사본을 만들지 않았기 때문에 정보의 관리가 필요하거나 만료되는 추가 복사본이 없습니다.  

#### <a name="forall-on-demand"></a>주문형 ForAll
또 다른 접근법은**ForAll** 함수를 사용하여 테이블 형성 함수를 대체하는 것입니다.

```powerapps-dot
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        { 
            Product: Product, 
            'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
        } 
    ) 
)
```

이 수식은 일부 사람이 읽고 쓰기에 더 간단할 수 있습니다.

**ForAll**의 모든 부분은 위임이 불가능합니다.  **Products** 테이블의 첫 번째 부분만 평가되기 때문에 테이블이 매우 큰 경우 문제가 될 수 있습니다.  이전 예제의 경우 **Filter**를 위임할 수 있으므로, 대용량 데이터 집합에서 더 효율적으로 작동할 수 있습니다.

#### <a name="collect-the-result"></a>결과 Collect
경우에 따라 데이터 복사본이 필요할 수 있습니다.  하나의 데이터 원본에서 다른 데이터 원본으로 정보를 이동해야 하는 경우도 있습니다.  이 예에서 주문은 공급 업체의 시스템에 있는 **NewOrder** 테이블에 배치됩니다.  고속 사용자 상호 작용을 위해 서버 대기 시간이 없도록 테이블의 로컬 복사본을 캐시할 수 있습니다.

앞의 두 예제와 동일한 테이블 형성을 사용하지만 결과는 컬렉션으로 캡처합니다.

```powerapps-dot
ClearCollect( NewOrder, 
    ShowColumns( 
        AddColumns( 
            Filter( Products, 'Quantity Requested' > 'Quantity Available' ), 
            "Quantity To Order", 'Quantity Requested' - 'Quantity Available' 
        ), 
        "Product", 
        "Quantity To Order"
    )
)
```

```powerapps-dot
ClearCollect( NewOrder, 
    ForAll( Products, 
        If( 'Quantity Requested' > 'Quantity Available', 
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        } 
    )
)
```

**ClearCollect**와 **Collect**는 위임할 수 없습니다.  따라서 이 방식으로 이동할 수 있는 데이터의 양은 제한됩니다.

#### <a name="collect-within-forall"></a>ForAll 내 Collect
마지막으로 **ForAll** 내에서 **Collect**를 직접 수행할 수 있습니다.

```powerapps-dot
Clear( ProductsToOrder ); 
ForAll( Products, 
    If( 'Quantity Requested' > 'Quantity Available', 
        Collect( NewOrder,  
            { 
                Product: Product, 
                'Quantity To Order': 'Quantity Requested' - 'Quantity Available' 
            } 
        )
    )
)
```

이번에도 **ForAll** 함수는 위임할 수 없습니다.  **Products** 테이블이 큰 경우 **ForAll**은 첫 번째 레코드 집합만을 살펴보기 때문에 주문할 제품이 일부 누락될 수 있습니다.  하지만 여기서 사용하는 테이블은 작게 유지되므로 이 방법이 괜찮습니다

**ForAll**의 결과는 캡처하지 않습니다.  그 안에 생성된 **Collect** 함수 호출은 모든 레코드에 대한 **NewOrder** 데이터 원본을 반환하기 때문에 결과를 캡처하는 경우 대량의 데이터가 추가될 수 있습니다.  

