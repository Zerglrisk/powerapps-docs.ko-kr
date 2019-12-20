---
title: Power Apps에서 계산 필드 정의 | MicrosoftDocs
description: 계산 필드를 정의하는 방법 알아보기
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 6d58a297-2ddf-4236-be3a-47249b49d5fa
caps.latest.revision: 67
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 82bf8cad9b64f9866cb1cc856eff94eacf1f23a2
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873909"
---
# <a name="define-calculated-fields-to-automate-manual-calculations"></a>계산 필드를 정의하여 수동 계산 자동화

계산 필드를 사용하여 비즈니스 프로세스에 사용되는 수동 계산을 자동화합니다. 

예를 들어, 영업 직원은 가능성을 곱한 영업 기회에서 예측된 매출을 기반으로 하는 영업 기회에 대한 가중 수익을 알고 싶어할 수 있습니다. 또는 주문이 $500보다 큰 경우 자동으로 할인을 적용하고자 합니다. 계산 필드는 간단한 수학 연산 또는 보다 큼이나 if-else, 등과 같은 조건 연산의 결과 값을 포함할 수 있습니다. Power Apps를 사용하여 모든 작업을 수행할 수 있으며 코드를 작성할 필요가 없습니다.  
  
## <a name="capabilities"></a>기능
  
- 계산 필드는 현재 엔터티 또는 관련된 상위 엔터티의 필드를 사용합니다.  
- 식 지원은 **조건** 섹션과 **작업** 섹션에 있는 현재 엔터티와 관련 상위 엔터티 필드에서 사용할 수 있습니다. 기본 제공 함수는 다음과 같습니다.  
 **ADDHOURS**, **ADDDAYS**, **ADDWEEKS**, **ADDMONTHS**, **ADDYEARS**, **SUBTRACTHOURS**, **SUBTRACTDAYS**, **SUBTRACTWEEKS**, **SUBTRACTMONTHS**, **SUBTRACTYEARS**, **DIFFINDAYS**, **DIFFINHOURS**, **DIFFINMINUTES**, **DIFFINMONTHS**, **DIFFINWEEKS**, **DIFFINYEARS**, **CONCAT**, **TRIMLEFT** 및 **TRIMRIGHT**.  
- 풍부한 조건 지원은 분기와 여러 가지 조건을 제공합니다. 논리 연산에는 **AND** 및– **OR** 연산자가 포함됩니다.  
- 시각적 편집 기능에는 **작업** 섹션에 있는 최신 사용자 인터페이스 및 IntelliSense가 포함됩니다. 
- 계산 필드와 양식, 보기, 차트 및 보고서의 완벽한 통합은 실시간으로 사용할 수 있습니다.  
- 사용자 지정 컨트롤을 사용하도록 계산 필드를 구성할 수 있습니다.  
  
  
## <a name="scenarios"></a>시나리오
  
- **가중치가 적용된 매출**: 가능성을 곱한 예상 매출  
- **순 가치**: 해당 거래처에 대해 책임을 뺀 자산  
- **인건비**: 최대 40시간의 기본 요율과 추가 근무 시간 포함  
- **연락처 번호**: 거래처 또는 연락처를 기반으로 하는 영업 기회에 대한 전화 번호  
- **잠재 고객 점수**: 특정 잠재 고객의 품질에 대한 통찰을 제공하는 단일 필드  
- **추가 작업**: 우선 순위를 기반으로 지정된 일 수만큼 활동에 대한 추가 작업  
  
> [!IMPORTANT]
>  계산 필드를 만들려면 [필드 보안 프로필 엔터티](/powerapps/developer/common-data-service/reference/entities/fieldsecurityprofile)에 대한 쓰기 권한이 있어야 합니다. 계산 필드가 계산에서 예약 필드를 사용하는 경우 충분한 권한이 없는 데이터에 사용자가 액세스하지 못하도록 계산 필드 보호를 고려해야 합니다. 계산 필드 편집기는 계산에서 보호된 필드를 사용하는 계산 필드를 만드는 경우 계산 필드를 보호하도록 제안하는 경고를 제공합니다. 추가 정보:  [액세스 제어를 위한 필드 수준 보안](/dynamics365/customer-engagement/admin/field-level-security)  

## <a name="create-a-calculated-field"></a>계산 필드 만들기

필드 편집기를 사용하여 계산 필드를 지정합니다. 이 예에서는 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)를 사용하지만 솔루션 탐색기를 사용하는 것과 단계는 비슷합니다. 추가 정보: [필드 만들기 및 편집](create-edit-fields.md)
  
1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 열기
1. **데이터** > **엔터티**를 확장합니다.  
1. 원하는 엔터티를 선택하고 **필드**를 선택합니다. **필드 추가**를 선택합니다.  
1. **표시 이름**, **이름** 및 **데이터 형식**을 포함한 필드에 필요한 정보를 제공합니다. 
1. 데이터 형식이 계산 필드를 지원하는 형식 중 하나인 경우 **추가** > **계산**을 선택하여 필드를 계산 필드로 만들 수 있습니다.

    ![필드를 계산으로 만들기](media/make-field-calculated-maker.png)

    다음은 계산을 지원하는 필드 유형입니다.
    - 텍스트
    - 옵션 집합  
    - 두 개의 옵션  
    - 정수  
    - 10진수  
    - 통화  
    - 날짜/시간

1. **계산**을 선택하려면 변경 내용을 엔터티에 저장해야 합니다. 계속하려면 **보류 중인 변경 내용**에서 **저장**을 클릭합니다.
1. 그러면 새로운 계산 필드를 만들었지만 공식이 설정되지 않은 계산 필드 정의 편집기로 이동합니다. 계산 필드 정의는 **조건** 및 **작업**의 두 섹션으로 구성됩니다.  
  ![새 필드 계산 양식](media/empty-field-calculation.png)
- **조건** 섹션에서 엔터티, 필드, 연산자, 형식 및 값을 지정할 수 있습니다. **엔터티**의 드롭다운 상자에서 현재 엔터티 또는 관련 엔터티를 선택할 수 있습니다. **필드** 드롭다운 상자에서 엔터티에 사용할 수 있는 모든 필드를 선택할 수 있습니다. 선택하는 연산자에 따라 형식과 값을 제공해야 할 수 있습니다. `AND` 또는 `OR` 연산자를 사용하여 여러 조건을 지정할 수 있습니다.  
- **작업** 섹션에서 계산 필드에 대한 공식을 제공합니다.  
  
> [!NOTE]
>  작업 내에 있는 조회 레코드의 데이터를 사용할 수 있습니다. 먼저 조회 필드를 선택한 다음 마침표를 입력해야 합니다. 그 후 관련 엔터티에 사용할 수 있는 필드 중 하나를 선택할 수 있습니다. 예를 들어 *`<LookupFieldName>.<RelatedFieldName>`* 경우 `ParentAccountId.AccountNumber`를 선택할 수 있습니다.  
>   
>  필드 수준 보안은 관련 엔터티를 무시하므로 액세스한 필드에 민감한 데이터가 있는 경우 계산 필드도 보호하는 것이 좋습니다.  


<a name="BusinessScenarios"></a> 
  
## <a name="examples"></a>예제  

계산된 필드 예를 자세히 살펴 보겠습니다. 
  
### <a name="weighted-revenue-of-opportunity"></a>가중치가 적용된 영업 기회 수익

이 예제에서는 영업 기회 엔터티의 필드를 사용하여 영업 기회 가능성을 기반으로 가중치가 적용된 매출을 계산합니다. 영업 기회 엔터티에 대한 필드 편집기에서 **가중치가 적용된 수익**이라는 필드를 만들고 필드 형식을 **계산**으로 입력하고 데이터 형식은 **통화**입니다.

계산 필드 정의 편집기의 **조건** 섹션에서 상태 = 열림인 영업 기회를 지정합니다. **작업**에서 공식은 영업 기회의 가능성을 곱한 영업 기회 예상 수익을 기반으로 가중치가 적용된 수익을 계산합니다.  다음 스크린샷은 **가중치가 적용된 수익** 계산 필드를 정의하는 단계별 방법을 보여줍니다.  
  
#### <a name="set-the-condition-on-the-opportunities"></a>영업 기회에 대한 조건을 설정합니다.
  
![Dynamics 365에서 가중 매출 설정](media/calc-field-open-opportunity.png)  
  
#### <a name="provide-the-formula-for-the-weighted-revenue"></a>가중치가 적용된 매출에 대한 공식을 제공합니다. 
  
![Dynamics 365 가중 매출 예상 가치 설정](media/calc-field-open-opportunities-3.png)  
  
#### <a name="altogether"></a>모두:
  
![Dynamics 365에서 예상 매출 대비 가중 매출](media/calculated-field-open-opportunity.png)  
  
### <a name="follow-up-date-of-opportunity"></a>영업 기회의 후속 작업 날짜 
 
이 예제에서는 영업 기회의 원래 잠재 고객 필드를 사용하여 영업 기회에 대한 후석 작업을 수행할 적절한 날짜를 계산합니다. 

영업 기회 엔터티에 대한 필드 편집기에서 **후속 작업 날짜**라는 필드를 만들고 필드 형식을 **계산**으로 입력하고 데이터 형식은 **날짜 및 시간**입니다.  

계산 필드 정의 편집기의 **조건** 섹션에서 구입 시간대 및 잠재 고객의 예측 값이라는 두 조건을 지정합니다. 

**작업**에서는 두 가지 공식을 제공합니다.
 - 일주일 내에 즉시 발생할 영업 기회를 후속 작업하려면
 - 일주일 내에 즉시 발생할 영업 기회를 후속 작업하는 것은 즉시 이루어질 가능성이 없습니다. 

다음 스크린샷은 **후속 작업 날짜** 계산 필드를 정의하는 단계별 방법을 보여줍니다.  
  
#### <a name="set-the-two-conditions-on-the-originating-lead"></a>원래 잠재 고객에 대해 두 가지 조건을 설정합니다.
  
![Dynamics 365에서 영업 기회 후속 날짜](media/calc-field-follow-update-2.PNG)  
  
![Dynamics 365에서 영업 기회 후속 날짜](media/calc-field-follow-update-3.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-week"></a>일주일 내에 후속 작업하는 공식을 제공합니다.
  
![Dynamics 365에서 영업 기회 후속 날짜](media/calc-field-follow-update-4.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-month"></a>한 달 내에 후속 작업하는 공식을 제공합니다.
  
![Dynamics 365에서 후속 작업 날짜 설정](media/calc-field-follow-update-5.PNG)  
  
#### <a name="altogether"></a>모두:
  
 ![Dynamics 365에서 If-Then 및 Else 후속 날짜 설정](media/calc-field-follow-update-6.PNG)  
  
### <a name="days-from-a-record-creation"></a>레코드 만든 후 일 수 
 
이 예제에서는 **DIFFINDAYS** 함수를 사용하여 레코드를 만든 때로부터 현재 날짜까지의 일 수 차이를 계산합니다. 

**계산된 일 수 차이**라는 새 정수 필드를 만듭니다.
  
#### <a name="provide-the-formula-for-computing-the-difference-in-days"></a>일수 차이를 계산하는 공식을 제공합니다.
  
![계산 필드, DIFFINDAYS 함수](media/custom-calc-field-diff-days.png)  
  
#### <a name="altogether"></a>모두:
  
![레코드 생성 이후 날짜의 차이](media/calc-field-diff-days-complete.png)  
  
<a name="Syntax"></a> 
  
## <a name="functions-syntax"></a>함수 구문  

다음 표에는 계산된 필드의 **작업** 섹션에 제공된 함수의 구문에 대한 정보가 들어 있습니다.  
  
> [!TIP]
>  함수 이름은 대문자로 지정됩니다.  
  
|함수 구문|설명|반환 유형|  
|---------------------|-----------------|-----------------|  
|**ADDDAYS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 일수를 더한 값을 반환합니다.|날짜 및 시간|  
|**ADDHOURS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 시간을 더한 값을 반환합니다.|날짜 및 시간|  
|**ADDMONTHS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 월수를 더한 값을 반환합니다.|날짜 및 시간|  
|**ADDWEEKS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 수의 주를 더한 값을 반환합니다.|날짜 및 시간|  
|**ADDYEARS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 햇수를 더한 값을 반환합니다.|날짜 및 시간|  
|**SUBTRACTDAYS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 일수를 뺀 값을 반환합니다.|날짜 및 시간|  
|**SUBTRACTHOURS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 시간을 뺀 값을 반환합니다.|날짜 및 시간|  
|**SUBTRACTMONTHS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 월수를 뺀 값을 반환합니다.|날짜 및 시간|  
|**SUBTRACTWEEKS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 수의 주를 뺀 값을 반환합니다.|날짜 및 시간|  
|**SUBTRACTYEARS**(정수, 날짜 및 시간)|지정된 날짜 및 시간과 동일한 새로운 날짜 및 시간에 지정된 햇수를 뺀 값을 반환합니다.|날짜 및 시간|  
|**DIFFINDAYS** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 일수 차이를 반환합니다. 날짜와 시간이 모두 같은 날인 경우 차이는 0입니다.|정수|  
|**DIFFINHOURS** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 시간 차이를 반환합니다.|정수|  
|**DIFFINMINUTES** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 분 차이를 반환합니다.|정수|  
|**DIFFINMONTHS** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 월 차이를 반환합니다. 날짜와 시간이 모두 같은 월인 경우 차이는 0입니다.|정수|  
|**DIFFINWEEKS** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 주 차이를 반환합니다. 날짜와 시간이 모두 같은 주인 경우 차이는 0입니다.|정수|  
|**DIFFINYEARS** (날짜 및 시간, 날짜 및 시간)|두 **날짜 및 시간** 필드 사이의 연수 차이를 반환합니다. 날짜와 시간이 모두 같은 해인 경우 차이는 0입니다.|정수|  
|**CONCAT**(한 줄 텍스트, 한 줄 텍스트, … 한 줄 텍스트)|둘 이상의 문자열을 연결한 문자열을 반환합니다.|문자열|  
|**TRIMLEFT**(한 줄 텍스트, 정수)|첫 N자가 없는 지정된 문자열의 복사본을 포함하는 문자열을 반환합니다.|문자열|  
|**TRIMRIGHT**(한 줄 텍스트, 정수)|마지막 N자가 없는 지정된 문자열의 복사본을 포함하는 문자열을 반환합니다.|문자열|  
  
> [!NOTE]
>  모든 DIFF 함수는 첫 번째 **날짜 및 시간** 필드와 두 번째 **날짜 및 시간** 필드의 동작이 같은 경우 필요합니다. **사용자 로캘**, **날짜만** 또는 **표준 시간대 독립**. 두 번째 필드의 동작이 첫 번째 필드의 동작과 일치하지 않는 경우 두 번째 필드를 현재 함수에 사용할 수 없다는 오류 메시지가 표시됩니다. 추가 정보: [날짜 및 시간 필드의 동작 및 형식](behavior-format-date-time-field.md)  
  
> [!NOTE]
>  01/01/2015 같은 날짜는 계산된 필드에 날짜 값으로 입력할 수 없습니다. 날짜 및 날짜/시간 값은 다른 날짜/시간 필드만 사용하여 설정하거나 비교할 수 있습니다.  
  
**CONCAT** 함수에서 리터럴 문자열을 한 줄 텍스트, 한 줄 텍스트가 포함된 엔터티 필드 또는 둘의 조합으로 사용할 수 있습니다. 예: **CONCAT** (FirstName, LastName, "is a manager.") 리터럴 문자열에 큰따옴표가 있으면 `This string contains the \"quotation marks.\"`처럼 각 따옴표가 역슬래시(\\) 이스케이프 문자 다음에 나옵니다. 따라서 문자열 안의 따옴표가 문자열을 나누는 특수 문자로 처리되지 않습니다.  
  
다음 예제는 **TRIMLEFT** 및 **TRIMRIGHT** 함수를 사용하는 방법을 보여 줍니다. 여기에는 **TRIMLEFT** 및 **TRIMRIGHT** 함수에서 반환된 초기 문자열과 결과 문자열이 포함됩니다.  
  
**TRIMLEFT**(“RXX10-3456789”, 3)는 `10-3456789`   문자열을 반환합니다.  
**TRIMRIGHT**(“20-3456789RXX”, 3), `20-3456789` 문자열을 반환합니다. 
  
<a name="Considerations"></a> 
  
## <a name="considerations"></a>고려 사항 
 
계산 필드를 사용할 때 특정 조건과 제한을 알고 있어야 합니다.  
  
- 저장된 쿼리, 차트 및 시각화는 최대 10개의 고유 계산 필드를 가질 수 있습니다.  
- 계산 필드 값은 Outlook 클라이언트 오프라인에서 타일 보기 또는 엔터티 기본 양식으로 표시되지 않습니다.  
- 체인으로 연결된 계산 필드의 최대 수는 5입니다.  
- 계산 필드는 자신을 참조하거나 순환 체인을 가질 수 없습니다.  
- 여러 조건 절에서 조건 연산자 중 하나를 변경하는 경우 모든 조건 연산자가 해당 조건으로 업데이트됩니다. 예를 들어 `IF (x > 50) OR (y ==10) OR (z < 5)`절에서 `OR` 연산자를 `AND` 연산자로 바꾸면 모든 절 내의 모든 `OR` 연산자가 `AND` 연산자가 됩니다.  
- *`<LookupFieldName>.<FieldName>`* 같은 상위 엔터티에 대한 조회 필드를 통해 상위 필드에 액세스할 수 있습니다. 이는 거래처 또는 연락처가 될 수 있는 고객 같은 여러 엔터티 조회 필드에서는 가능하지 않습니다. 그러나 일부 엔터티에는 `ParentAccountid.`*`<FieldName>`* 또는 `ParentContactid.`*`<FieldName>`* 같은 특정 엔터티에 대한 개별 조회 필드가 있습니다.  
- 정렬은 다음에서 사용할 수 없습니다.  
  - 상위 레코드의 필드를 포함하는 계산 필드.  
  - 논리 필드를 포함하는 계산 필드(예: 주소 필드)
  - 다른 계산 필드를 포함하는 계산 필드.  
- 계산 필드는 두 엔터티에만 걸쳐 있을 수 있습니다.  
  - 계산 필드는 다른 엔터티의 필드를 포함할 수 있습니다(두 엔터티에 걸쳐 있음 – 현재 엔터티 및 상위 레코드).  
  - 계산 필드에는 다른 엔터티(세 개의 엔터티에서)의 다른 필드 하나를 포함하는 다른 엔터티의 계산 필드를 포함할 수 없습니다.   
    (현재 엔터티) 계산 필드 &larr;(상위 레코드) 계산 필드 &larr;(상위 레코드) 계산 필드 2  
- 계산 필드에서는 워크플로 또는 플러그 인을 트리거할 수 없습니다.  
- 기존의 단순 필드를 계산 필드로 변경할 수 없습니다. 현재 응용 프로그램이 JavaScript 또는 플러그 인을 사용하여 필드를 계산하는 경우 새 필드를 만들지 않고 계산 필드 기능을 사용할 수 없습니다.  
- 중복 검색 규칙은 계산 필드에서 트리거되지 않습니다.  
- 롤업은 다른 계산 필드의 모든 필드가 현재 엔터티인 경우에도 다른 계산 필드를 사용하는 계산 필드를 참조할 수 없습니다.  
  
### <a name="see-also"></a>참조
 
[필드 만들기 및 편집](create-edit-fields.md)<br />
[값을 집계하는 롤업 필드 정의](define-rollup-fields.md)<br />
[비디오: 롤업 및 계산 필드](https://go.microsoft.com/fwlink/p/?LinkId=517727)
