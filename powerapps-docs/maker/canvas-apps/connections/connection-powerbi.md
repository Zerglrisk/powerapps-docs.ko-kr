---
title: Power BI 연결 개요 | Microsoft Docs
description: 사용 가능한 Power BI 연결을 참조하세요.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5efcc877de7a16524c57121a91488189d4058437
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71987149"
---
# <a name="connect-to-power-bi-from-powerapps"></a>PowerApps에서 Power BI에 연결
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI는 데이터를 분석하고 정보 활용을 공유하는 비즈니스 분석 도구 제품군입니다. 비즈니스를 모니터링하고 모든 디바이스에서 사용할 수 있는 다양한 대시보드에 대해 신속하게 답변 받을 수 있습니다. 앱에서 Power BI 서비스에서 설정한 데이터 경고의 상태를 확인할 수 있습니다. Power BI의 데이터 경고에 대한 자세한 내용은 [설명서 페이지](https://docs.microsoft.com/power-bi/service-set-data-alerts)를 참조하세요.

이 토픽에서는 앱에서 Power BI 연결을 사용하는 방법과 사용할 수 있는 함수를 나열합니다.

## <a name="prerequisites"></a>필수 조건
* [등록](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
* Power BI [연결](https://powerapps.microsoft.com/tutorials/add-manage-connections/)을 추가합니다.
* [템플릿](https://powerapps.microsoft.com/tutorials/get-started-test-drive/), [데이터](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/)에서 앱을 만들거나 [처음부터](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/)만듭니다.

## <a name="use-the-power-bi-connection-in-your-app"></a>앱의 Power BI 연결을 사용합니다.
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Power BI 서비스에서 설정한 경고를 나열합니다.
1. **삽입** 메뉴에서 **갤러리**를 선택하고 **텍스트 갤러리** 하나를 추가합니다.
2. 현재 사용자의 경고를 표시하려면 갤러리의 [항목](../controls/properties-core.md) 속성을 다음 수식에 설정합니다.

   `PowerBI.GetAlerts()`

갤러리가 경고 목록으로 업데이트됩니다. 사용자는 각 경고에 대한 경고 이름, 경고 ID 번호, 경고가 구성 된 그룹 작업 영역 ID를 받습니다. 경고 ID는 경고에 대해 자세한 정보를 얻고자 할 때 필요합니다.

### <a name="view-the-status-of-an-alert"></a>경고 상태 보기
경고 상태를 보려면 위의 단계에서 받은 경고 ID로 CheckAlertStatus 함수를 호출합니다.

경고 ID는 GetAlerts() 호출(예: Gallery1.Selected.alertId)을 사용하여 채워진 갤러리 섹션에 리터럴 문자열(예: "1234") 또는 참조로 전달됩니다.

계속 진행하려면 레이블을 추가하고 해당 [텍스트](../controls/properties-core.md) 속성을 이러한 수식 중 하나로 설정합니다.

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

레이블은 경고의 현재 상태로 업데이트됩니다.

## <a name="view-the-available-functions"></a>사용할 수 있는 함수 보기
이 연결에는 다음 함수가 포함됩니다.

| 함수 이름 | 설명 |
| --- | --- |
| GetAlerts |Power BI 서비스에서 설정한 경고를 나열합니다. |
| CheckAlertStatus |특정 경고의 상태를 확인합니다. |

## <a name="getalerts"></a>GetAlerts
Power BI 서비스에서 설정한 경고를 나열합니다.

#### <a name="input-properties"></a>입력 속성
없음

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| 값 |배열 |아니요 |Power BI 서비스에서 설정한 데이터 경고의 배열입니다. 배열의 각 요소에는 다음이 포함됩니다. <ul><li>alertTitle: 경고의 제목</li><li>alertId: 경고의 ID</li><li>groupId: 경고가 만들어진 그룹의 ID</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
경고 상태를 봅니다.

> [!NOTE]
> 너무 자주 호출하는 경우 경고 당 기준에 따라 이 엔드포인트에 대한 요청이 정체됩니다.

#### <a name="input-properties"></a>입력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| alertId |정수 |예 |GetAlerts가 반환한 경고 ID |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| tileValue |숫자 |아니요 |경고가 트리거되는 경우 타일 값 |
| tileUrl |문자열 |아니요 |경고가 있는 타일에 대한 URL |
| alertTitle |문자열 |아니요 |경고의 이름 |
| isAlertTriggered |부울 |아니요 |경고가 현재 트리거되는지 여부 |
| alertThreshold |숫자 |아니요 |경보가 트리거되는 임계값 |

## <a name="helpful-links"></a>유용한 링크
[사용 가능한 연결](../connections-list.md)을 모두 보세요.  
앱에 [연결을 추가](../add-manage-connections.md)하는 방법을 알아보세요.

