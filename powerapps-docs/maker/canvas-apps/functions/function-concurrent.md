---
title: Concurrent 함수 | Microsoft Docs
description: PowerApps에서 Concurrent 함수에 대한 구문을 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/26/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a0fdddcf906a04914ea9ba9a8572798ea5d55378
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834822"
---
# <a name="concurrent-function-in-powerapps"></a>PowerApps의 Concurrent 함수
동시에 서로 여러 수식을 평가합니다.

## <a name="description"></a>설명
**Concurrent** 함수는 동시에 여러 수식을 평가합니다. 일반적으로 여러 수식은 [**;**](operators.md)(또는 [**;;**](operators.md)) 연산자와 함께 연결하여 평가됩니다. 따라서 순차적으로 각 항목을 평가합니다. 앱이 작업을 동시에 수행하는 경우 사용자가 동일한 결과를 기다리는 시간이 줄어듭니다.

앱의 [**OnStart**](../controls/control-screen.md) 속성에서 **Concurrent**를 사용하여 앱이 데이터를 로드할 때 성능을 향상시킵니다. 이전 호출이 완료될 때까지 데이터 호출이 시작되지 않는 경우 앱은 모든 요청 시간의 합계를 대기해야 합니다. 데이터 호출이 동시에 시작되는 경우 앱은 가장 긴 요청 시간 동안만 대기하면 됩니다. 웹 브라우저는 데이터 작업을 동시에 수행하여 성능을 향상시킵니다.

**Concurrent** 함수 내에서 수식이 평가를 시작하고 종료하는 순서를 예측할 수 없습니다. **Concurrent** 함수 내의 수식은 동일한 **Concurrent** 함수 내의 다른 수식에 대한 종속성을 포함하지 않고 PowerApps에서는 사용하는 경우 오류를 표시합니다. 내부에서 **Concurrent** 함수가 시작하기 전에 완료하기 때문에 **Concurrent** 함수 외부의 수식에 대한 종속성을 안전하게 사용할 수 있습니다. **Concurrent** 함수 내에서 수식은 내부의 수식에 대한 종속성을 안전하게 사용할 수 있습니다. 해당 수식은 **;** 또는 **;;** 연산자를 사용하는 경우 **Concurrent** 함수가 완료되고 체인의 다음 수식으로 이동하기 전에 완료됩니다. 의도하지 않은 결과가 포함된 함수 또는 서비스 메서드를 호출하는 경우 미묘한 순서 종속성에 대해 주의합니다.

**Concurrent**의 인수 내에서 **;**(또는 **;;**) 연산자와 함께 수식을 연결할 수 있습니다. **Concurrent( Set( a, 1 ); Set( b, a+1 ), Set( x, 2 ); Set( y, x+2 ) )** 는 **Set( x, 2 ); Set( y, x+2 )** 와 동시에 **Set( a, 1 ); Set( b, a+1 )** 을 평가합니다. 이 경우에 수식 내에서 종속성에는 문제가 없습니다. **a**는 **b** 전에 설정되고 **x**는 **y** 전에 설정됩니다.

앱이 실행되는 장치 또는 브라우저에 따라 일부 수식만이 실제로 동시에 계산될 수 있습니다. **Concurrent**는 지원되는 기능을 사용하고 모든 수식이 평가될 때까지 완료되지 않습니다.

고급 설정에서 **수식 수준 오류 관리**를 사용하도록 설정하면 인수 순서에서 발생한 첫 번째 오류는 **Concurrent**에서 반환됩니다. 그렇지 않으면 *비어 있음*이 반환됩니다. 모든 수식이 성공하는 경우 *true*가 반환됩니다. 하나의 수식이 실패하면 해당 수식의 나머지는 중지되지만 다른 수식은 계속 평가합니다.

**Concurrent**를 [동작 수식](../working-with-formulas-in-depth.md)에서만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Concurrent**( *Formula1*, *Formula2* [, ...] )

* *Formula(s)* – 필수입니다. 동시에 평가할 수식입니다. 적어도 두 개의 수식을 제공해야 합니다.

## <a name="examples"></a>예

#### <a name="loading-data-faster"></a>신속하게 데이터 로드

1. 앱을 만들고, 앱용 Common Data Service, SQL Server 또는 SharePoint에서 4개의 데이터 원본을 추가합니다. 

    이 예제에서는 [SQL Azure의 샘플 Adventure Works 데이터베이스](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)에서 네 개의 테이블을 사용합니다. 데이터베이스를 만든 후에 정규화된 서버 이름(예: srvname.database.windows.net)을 사용하여 PowerApps에서 연결합니다.

    ![Azure에서 Adventure Works 데이터베이스에 연결](media/function-concurrent/connect-database.png)

2. **[단추](../controls/control-button.md)** 컨트롤을 추가하고 **OnSelect** 속성을 이 수식으로 설정합니다.

    **ClearCollect( Product, '[SalesLT].[Product]' );<br> ClearCollect( Customer, '[SalesLT].[Customer]' );<br> ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );<br> ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )**

3. [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) 또는 [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/)에서 앱이 실행되는 동안 네트워크 트래픽을 모니터링하는 개발자 도구를 사용합니다.

1. (선택 사항) 네트워크 제한을 설정하여 이 비교의 결과를 확장합니다.

4. Alt 키를 누른 채 단추를 선택한 다음, 네트워크 트래픽을 확인합니다.

    도구에서는이 예제와 비슷한 시리즈에서 수행된 네 개의 요청을 보여줍니다.  실제 시간은 상당히 다르므로 제거되었습니다.  그래프에서는 마지막 항목이 완료된 후에 각 호출이 시작함을 보여줍니다.

    ![마지막 항목이 완료된 후에 시작하고 전체 시간 범위를 다루는 네 가지 네트워크 요청의 시간 그래프입니다.](media/function-concurrent/chained-network.png)

5. 앱을 저장하고, 닫고, 다시 엽니다.

    단추를 다시 선택해도 네 개의 새로운 요청이 발생해야만 하지 있도록 PowerApps는 데이터를 캐시합니다. 성능을 테스트할 때마다 앱을 닫고 다시 엽니다. 네트워크 제한을 설정한 경우 다른 테스트에 대해 준비가 될 때까지 해제하는 것이 좋습니다.

1. 두 번째 **[단추](../controls/control-button.md)** 컨트롤을 추가하고 이 수식에 **OnSelect** 속성을 설정합니다.

    **Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Product, '[SalesLT].[Product]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Customer, '[SalesLT].[Customer]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )<br> )**

    동일한 **ClearCollect** 호출을 첫 번째 단추에 추가했지만 이번에는 **Concurrent** 함수에서 래핑되고 쉼표로 구분됩니다.

2. 브라우저에서 네트워크 모니터를 지웁니다.

1. 이전에 네트워크 제한을 사용한 경우 다시 설정합니다.

3. Alt 키를 누른 채 두 번째 단추를 선택한 다음, 네트워크 트래픽을 확인합니다.

    도구에서는이 예제와 비슷하게 동시에 수행된 네 개의 요청을 보여줍니다.  마찬가지로 실제 시간은 상당히 다르므로 제거되었습니다.  그래프는 모든 호출이 거의 동시에 시작되고 이전 호출이 완료될 때까지 기다리지 않는다는 것을 보여줍니다.

    ![모두 동시에 시작되는 네 개의 네트워크 요청의 시간 그래프는 기간 중 절반을 다룹니다.](media/function-concurrent/concurrent-network.png)

    이러한 그래프는 동일한 규모를 기반으로 합니다. **Concurrent**를 사용하여 이러한 작업이 완료되는 데 걸린 총 시간을 50% 감소시킵니다. 

5. 앱을 저장하고, 닫고, 다시 엽니다.

#### <a name="race-condition"></a>경합 조건

1. [Microsoft Translator](../connections/connection-microsoft-translator.md) 서비스에 대한 연결을 앱에 추가합니다.

2. [**텍스트 입력**](../controls/control-text-input.md) 컨트롤을 추가하고, 다른 이름이 있는 경우 이름을 **TextInput1**로 지정합니다.

3. **단추** 컨트롤을 추가하고 **OnSelect** 속성을 이 수식으로 설정합니다.

    **Set( StartTime, Value(Now()) );<br> Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(FRTrans, MicrosoftTranslator.Translate(TextInput1.Text,"fr")); Set(FRTransTime, Value(Now()) ),<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(DETrans, MicrosoftTranslator.Translate(TextInput1.Text,"de")); Set(DETransTime, Value(Now()) )<br> ); <br> Collect( <br> &nbsp;&nbsp;&nbsp;&nbsp;Results, <br> &nbsp;&nbsp;&nbsp;&nbsp;{<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Input: TextInput1.Text, <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;French: FRTrans, FrenchTime: FRTransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;German: DETrans, GermanTime: DETransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FrenchFaster: FRTransTime < DETransTime <br> &nbsp;&nbsp;&nbsp;&nbsp;}<br> )**

4. [**데이터 테이블**](../controls/control-data-table.md) 컨트롤을 추가하고 **Items** 속성을 **Results**로 설정합니다.

1. 오른쪽 창의 **속성** 탭에서 **결과**를 선택하여 **데이터** 창을 엽니다.

1. 필드 목록에서 각 필드에 대한 확인란을 선택하여 데이터 테이블에서 모두 표시합니다.

1. (선택 사항) **입력** 필드를 목록의 맨 위로 끌어오고 **FrenchFaster** 필드를 목록 맨 아래로 끌어옵니다.

    ![결과 컬렉션의 필드 목록](media/function-concurrent/field-list.png) 

6. **텍스트 입력** 컨트롤에서 변환할 문구를 입력하거나 붙여넣습니다.

7. Alt 키를 누른 채 단추를 여러 번 선택하여 테이블을 채웁니다.

    시간은 밀리초 단위로 표시됩니다.
  
    !["Hello World" 문자열을 프랑스어 및 독일어로 변환하는 결과가 포함된 데이터 테이블을 표시합니다. 경우에 따라 프랑스어 번역이 독일어보다 빠르고 경우에 따라 반대일 수도 있습니다.](media/function-concurrent/race-condition.png) 

    경우에 따라 프랑스어 번역이 독일어 번역보다 빠르고 반대로도 가능합니다. 둘 다 동시에 시작되지만 네트워크 대기 시간 및 서버 쪽 처리를 비롯한 다양한 이유로 한 번역이 다른 번역보다 먼저 반환됩니다.

    앱이 먼저 종료한 한 가지 번역을 사용하는 경우 [경합 조건](https://en.wikipedia.org/wiki/Race_condition)이 발생합니다. 다행스럽게도 PowerApps는 감지할 수 있는 대부분의 타이밍 종속성의 플래그를 지정합니다.
