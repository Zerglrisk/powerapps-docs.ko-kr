---
title: Average, Max, Min, StdevP, Sum 및 VarP 함수 | Microsoft Docs
description: 구문 및 예제를 포함 하 여 Power Apps의 Average, Max, Min, StdevP, Sum 및 VarP 함수에 대 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4f25888cebb81b0b18b1dd54faecfa87df4eb1d6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678445"
---
# <a name="average-max-min-stdevp-sum-and-varp-functions-in-powerapps"></a>PowerApps의 Average, Max, Min, StdevP, Sum 및 VarP 함수
일련의 숫자를 요약하는 집계 함수입니다.

## <a name="description"></a>설명
**Average** 함수는 인수의 평균 또는 산술 평균을 계산합니다.

**Max** 함수는 최대값을 찾습니다.

**Min** 함수는 최소값을 찾습니다.

**Sum** 함수는 인수의 합을 계산합니다.

**StdevP** 함수는 인수의 표준 편차를 계산합니다.

**VarP** 함수는 인수의 분산을 계산합니다.

이러한 함수의 값은 다음과 같이 지정할 수 있습니다.

* 별도의 인수. 예를 들어 **Sum( 1, 2, 3 )** 은 6을 반환합니다.
* [테이블](../working-with-tables.md) 및 이 테이블에 연산을 수행할 수식.  집계는 각 [레코드](../working-with-tables.md#records)에 대한 수식의 값에 따라 계산됩니다.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

이러한 함수는 숫자 값에 대해서만 작동합니다. 문자열이나 레코드와 같은 다른 유형의 값은 무시됩니다. 문자열을 숫자로 변환하려면 **[Value](function-value.md)** 함수를 사용합니다.

**Average**, **Max**, **Min** 및 **Sum** 함수는 [이러한 함수에 대한 위임을 지원하는 데이터 원본](../delegation-list.md)과 함께 사용하면 위임이 가능합니다.  하지만 **StdevP** 및 **VarP**는 모든 데이터 원본에 대해 위임할 수 없습니다.  위임이 지원되지 않으면 데이터의 첫 번째 부분만 검색된 다음 함수가 로컬에 적용됩니다.  결과에 전체 스토리가 나타나지 않을 수 있습니다.  해당하는 경우 이러한 제한 사항을 상기시키고 위임 가능한 대안으로 전환하도록 제안하기 위해 수식 작성 시 위임 경고가 표시됩니다. 자세한 내용은 [위임 개요](../delegation-overview.md)를 참조하세요.

## <a name="syntax"></a>구문
**Average**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Max**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Min**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**Sum**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**StdevP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )<br>**VarP**( *NumericalFormula1*, [ *NumericalFormula2*, ... ] )

* *NumericalFormula(s)* - 필수 항목입니다.  연산을 수행할 숫자 값입니다.

**Average**( *Table*, *NumericalFormula* )<br>**Max**( *Table*, *NumericalFormula* )<br>**Min**( *Table*, *NumericalFormula* )<br>**Sum**( *Table*, *NumericalFormula* )<br>**StdevP**( *Table*, *NumericalFormula* )<br>**VarP**( *Table*, *NumericalFormula* )

* *Table* - 필수 항목입니다.  연산을 수행할 테이블입니다.
* *NumericalFormula* - 필수 항목입니다. 각 레코드에 대해 계산할 수식입니다. 이 수식의 결과는 집계에 사용됩니다. 수식에서 표의 열을 사용할 수 있습니다.

## <a name="examples"></a>예
### <a name="step-by-step"></a>단계별 가이드
**CostPerUnit** 열과 **UnitsSold** 열을 포함하는 **Sales**라는 [데이터 원본](../working-with-data-sources.md)이 있고 레이블의 **[Text](../controls/properties-core.md)** 속성을 아래 함수에 설정한다고 가정하겠습니다.<br>
**Sum(Sales, CostPerUnit * UnitsSold)**

레이블은 각 레코드에 대한 해당 열의 값을 곱한 다음, 모든 레코드의 결과를 모두 합하여 총 매출을 표시합니다.<br>![판매 단위 및 단위당 가격으로부터 총 매출 계산](./media/function-aggregates/total-sales.png)

다른 예로, **Slider1**, **Slider2**, **Slider3**이라는 슬라이더와 **[Text](../controls/properties-core.md)** 속성이 다음 수식으로 설정된 레이블이 있다고 가정하겠습니다.<br>
**Sum(Slider1.Value, Slider2.Value, Slider3.Value)**

레이블에는 슬라이더가 설정된 모든 값의 합계가 표시됩니다.

