---
title: With 함수 | Microsoft Docs
description: Power Apps에서 함수에 대 한 구문을 포함 한 참조 정보
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
ms.openlocfilehash: 886482e9093fa44c34fb1f72b93d51181d4fbc10
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729859"
---
# <a name="with-function-in-power-apps"></a>Power Apps에서 함수 사용
명명 된 값의 인라인 레코드를 포함 하 여 단일 [레코드](../working-with-tables.md#records)에 대 한 값을 계산 하 고 작업을 수행 합니다.

## <a name="description"></a>설명

**With** 함수는 단일 레코드에 대 한 수식을 계산 합니다.  수식은 값을 계산하고 데이터 수정이나 연결 작업과 같은 작업을 수행할 수 있습니다.  [ **ForAll** 함수](function-forall.md) 를 사용 하 여 레코드 테이블의 모든 레코드에 대 한 수식을 평가할 수 있습니다.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

**를** 사용 하 여 복잡 한 수식을 작은 명명 된 하위 수식으로 나누어 가독성을 향상 시킬 수 있습니다.  이러한 명명 된 값은의 범위에만 적용 **되는 단순한**지역 변수 처럼 작동 합니다.  [ **Updatecontext** 함수](function-updatecontext.md) 에 사용 되는 것과 동일한 인라인 레코드 구문을 **와**함께 사용할 수 있습니다.  는 자체 포함 되 고 이해 하기 쉬우며 선언적 수식 컨텍스트에서 사용할 수 있으므로 컨텍스트 또는 전역 변수 보다를 **사용 하는** 것이 좋습니다.  

**With** 를 사용 하 여 [**Patch**](function-patch.md) 또는 [**Match**](function-ismatch.md)와 같은 함수에서 반환 된 레코드의 필드에 액세스 합니다.  **With** 는 이러한 함수의 값을 추가 계산 또는 작업에 사용할 수 있을 정도로 길게 보유 합니다.  

**에 대 한** *Record* 인수가 오류가 면 해당 오류가 함수에 의해 반환 되 고 *수식이* 계산 되지 않습니다.

## <a name="syntax"></a>구문
**With**( *Record*, *Formula* )

* *Record* – 필수 항목입니다. 작업할 레코드입니다.  이름 값의 경우 인라인 구문을 사용 `{ name1: value1, name2: value2, ... }`
* *수식* – 필수 항목입니다.  *레코드*에 대해 평가할 수식입니다.  수식은 레코드의 모든 필드를 레코드 *범위로 직접 참조할* 수 있습니다.

## <a name="examples"></a>예

### <a name="simple-named-values"></a>단순한 명명 된 값

```powerapps-dot
With( { radius: 10, 
        height: 15 },
    Pi() * (radius*radius) * height
)
// Result: 4712.38898038 (as shown in a label control)
```

이 예제에서는 명명 된 값의 레코드를 사용 하 여 실린더의 볼륨을 계산 합니다.  **를 사용** 하 여 모든 입력 값을 함께 캡처하여 계산 자체와 쉽게 구분할 수 있습니다.  

### <a name="nested-with"></a>중첩 된

![With 함수를 사용 하는 관련 계산기](media/function-with/interest-calculator.gif)

```powerapps-dot
With( { AnnualRate: RateSlider/8/100,        // slider moves in 1/8th increments and convert to decimal
        Amount: AmountSlider*10000,          // slider moves by 10,000 increment
        Years: YearsSlider,                  // slider moves in single year increments, no adjustment required
        AnnualPayments: 12 },                // number of payments per year
      With( { r: AnnualRate/AnnualPayments,  // interest rate
              P: Amount,                     // loan amount
              n: Years*AnnualPayments },     // number of payments
            r*P / (1 - (1+r)^-n)             // standard interest calculation
      )
)  
```

이 예에서는 **함수로 중첩 하 여** [월별 담보 대출 지불](https://en.wikipedia.org/wiki/Mortgage_calculator#Monthly_payment_formula)을 위한 2 계층 계산을 만듭니다.  충돌이 발생 하지 않는 한 내부 내에서 명명 된 값 **을 포함** 하는 모든 외부를 사용할 수 **있습니다.**

슬라이더 컨트롤은 1만 큼 이동 될 수 있으므로 슬라이더를 분할 하거나 곱하여 사용자 지정 증가값을 효과적으로 만들 수 있습니다.  이자율의 경우 **RateSlider** 의 **Max** 속성이 **48**으로 설정 되 100 고 1/8 백분율 포인트 증분의 경우 8로 나누고% ~ 6%의 0.125 범위를 포함 하 여 백분율에서 10 진수로 변환 됩니다.  대출 금액의 경우 **Amountslider** 는 해당 **Max** 속성이 60으로 설정 되 고 1만로 곱하여 범위 1만를 60만로 설정 합니다.

슬라이더가 이동 하 고 새 대출 지불을 표시 하면 **With** 가 자동으로 다시 계산 됩니다.  변수가 사용 되지 않으며 slider 컨트롤의 **OnChange** 속성을 사용할 필요가 없습니다.

이 앱을 만들기 위한 자세한 지침은 다음과 같습니다.
1. 새 앱을 만듭니다.
2. [ **슬라이더** 컨트롤](../controls/control-slider.md) 을 추가 하 고 이름을 **RateSlider**로 다시 만듭니다.  **Max** 속성을 48로 설정 합니다.
3. 슬라이더 컨트롤의 왼쪽에 [ **레이블** 컨트롤](../controls/control-text-box.md) 을 추가 합니다.  **Text** 속성을 **"이율:"** 으로 설정 합니다.
3. 슬라이더 컨트롤의 오른쪽에 **레이블** 컨트롤을 추가 합니다.  **Text** 속성을 **RateSlider/8 & "&nbsp;%"** 수식으로 설정 합니다.
3. 다른 **슬라이더** 컨트롤을 추가 하 고 이름을 **amountslider**로 추가 합니다.  **Max** 속성을 60로 설정 합니다.
3. 이 슬라이더 컨트롤의 왼쪽에 **레이블** 컨트롤을 추가 합니다.  **Text** 속성을 **"Loan Amount:"** 로 설정 합니다. 
3. 이 슬라이더 컨트롤의 오른쪽에 **레이블** 컨트롤을 추가 합니다.  **Text** 속성을 **Amountslider/8 * 1만**수식으로 설정 합니다.
4. 다른 **슬라이더** 컨트롤을 추가 하 고 이름을 **YearsSlider**로 추가 합니다.  **Max** 속성을 40로 설정 합니다.
3. 이 슬라이더 컨트롤의 왼쪽에 **레이블** 컨트롤을 추가 합니다.  **Text** 속성을 **"Number of Years:"** 로 설정 합니다. 
3. 이 슬라이더 컨트롤의 오른쪽에 **레이블** 컨트롤을 추가 합니다.  **Text** 속성을 **YearsSlider**수식으로 설정 합니다.
5. **레이블** 컨트롤을 추가 하 고 **텍스트** 속성을 위에 표시 된 수식으로 설정 합니다.
3. **레이블** 컨트롤을 마지막 레이블 컨트롤의 왼쪽에 추가 합니다.  **Text** 속성을 **"되풀이 되는 월간 결제:"** 로 설정 합니다.  

### <a name="primary-key-returned-from-patch"></a>Patch에서 반환 된 기본 키

```powerapps-dot
With( Patch( Orders, Defaults( Orders ), { OrderStatus: "New" } ),
      ForAll( NewOrderDetails, 
              Patch( OrderDetails, Defaults( OrderDetails ), 
                     { Order: OrderID,          // from With's first argument, primary key of Patch result
                       Quantity: Quantity,      // from ForAll's NewOrderDetails table
                       ProductID: ProductID }   // from ForAll's NewOrderDetails table
              )
      )
)
```

이 예에서는 SQL Server의 **Order** 테이블에 레코드를 추가 합니다.  그런 다음 **OrderID** 필드의 **Patch** 함수에서 반환 된 순서로 반환 된 기본 키를 사용 하 여 **OrderDetails** 테이블에 관련 레코드를 만듭니다.  

### <a name="extracted-values-with-a-regular-expression"></a>정규식을 사용 하 여 추출 된 값

```powerapps-dot
With( 
    Match( "PT2H1M39S", "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
    Time( Value( hours ), Value( minutes ), Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control, use the Text function to see the seconds)
```

이 예에서는 ISO 8601 기간 값에서 시, 분, 초를 추출한 다음 이러한 하위 일치 항목을 사용 하 여 날짜/시간 값을 만듭니다. 

하위 항목 일치는 숫자를 포함 하지만 여전히 텍스트 문자열에 있습니다.  수치 연산을 수행 하기 전에 숫자로 변환 하려면 [**Value**](function-value.md) 함수를 사용 합니다.  

