---
title: 가속, 앱, 나침반, 연결 및 위치 신호 | Microsoft Docs
description: PowerApps의 가속, 앱, 나침반, 연결 및 위치 센서 등, 구문 및 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 18bd89549aa330b5da333dccfd723887db38a36e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61553933"
---
# <a name="acceleration-app-compass-connection-and-location-signals-in-powerapps"></a>PowerApps의 가속, 앱, 나침반, 연결 및 위치 신호 
전 세계에서 사용자의 위치, 표시할 화면 등과 같이 앱 환경 관련 정보를 반환합니다.  

## <a name="description-and-syntax"></a>설명 및 구문
모든 신호는 정보의 [레코드](../working-with-tables.md#records)를 반환합니다. 이 정보를 레코드로 사용 및 저장하거나, **.** [연산자](operators.md)를 사용하여 개별 속성을 추출할 수 있습니다.

> [!NOTE]
> **Acceleration**과 **Compass** 함수는 iOS 또는 Android 같은 네이티브 플레이어에서는 정확한 값을 반환하지만, 브라우저에서 앱을 수정하거나 생성하게 되면 해당 함수들은 0 값을 반환합니다.

### <a name="acceleration"></a>Acceleration
**가속** 신호는 디바이스의 화면에 상대적인 디바이스의 가속을 3차원으로 반환합니다. 가속은 9.81m/초<sup>2</sup> 또는 32.2피트/초<sup>2</sup>의 *g* 단위로 측정됩니다(지구 중력이 표면의 물체에 영향을 미치는 가속도).

| 속성 | 설명 |
| --- | --- |
| **Acceleration.X** |오른쪽 및 왼쪽.  오른쪽이 양수입니다. |
| **Acceleration.Y** |앞으로 및 뒤로.  앞으로가 양수입니다. |
| **Acceleration.Z** |위 및 아래.  위가 양수입니다. |

### <a name="app"></a>앱
**앱** 신호는 실행 중인 앱 관련 정보를 반환합니다.

| 속성 | 설명 |
| --- | --- |
| **App.ActiveScreen** | 표시되는 화면입니다. 화면의 속성을 참조하거나, 다른 화면과 비교하여 표시할 화면을 결정하는 데 사용할 수 있는 화면 개체를 반환합니다. 표시 되는 화면을 변경 하려면 사용 합니다 **[다시](function-navigate.md)** 또는 **[탐색](function-navigate.md)** 함수입니다. |
| **App.Width** | 앱 실행 되는 창의 너비를 반환 합니다. 설정한 경우 수식에서이 속성을 사용할 수 있습니다 합니다 **너비** 응답성이 뛰어난 앱을 빌드하는 화면의 속성입니다.  |
| **App.Height** | 앱 실행 되는 창의 높이 반환 합니다. 설정한 경우 수식에서이 속성을 사용할 수 있습니다 합니다 **높이** 응답성이 뛰어난 앱을 빌드하는 화면의 속성입니다. |
| **App.DesignWidth** | PowerApps Studio 앱의 너비를 반환합니다. 설정한 경우 수식에서이 속성을 사용할 수 있습니다 합니다 **너비** 응답성 있는 앱의 최소 너비를 확인 하려면 화면의 속성입니다.  |
| **App.DesignHeight** | PowerApps Studio 앱의 높이 반환합니다. 설정한 경우 수식에서이 속성을 사용할 수 있습니다 합니다 **높이** 응답성 있는 앱의 최소 높이 확인 하려면 화면의 속성입니다.  |
| **App.SizeBreakpoints** | 화면 크기를 구분 하는 숫자의 단일 열 테이블을 하는 범위를 [ **Screen.Size** ](../controls/control-screen.md) 속성 반환 합니다. 이 테이블의 값을 사용 하 여를 화면 앱의 모든 중단점에 맞게 변경할 수 있습니다.

또한 **앱** 개체에는 설정할 수 있는 [동작 수식](../working-with-formulas-in-depth.md)이 있습니다.

| 속성  | 설명 |
| --- | --- |
| **App.OnStart** | 사용자가 앱을 시작할 때 앱의 동작입니다. 결정권자가 검색 하 고 사용 하 여 컬렉션으로 데이터를 캐시의 경우이 속성을 사용 합니다 **[수집](function-clear-collect-clearcollect.md)** 함수를 사용 하 여 변수를 설정 합니다 **[설정](function-set.md)** 함수를 사용 하 여 초기 화면에 이동 합니다 **[Navigate](function-navigate.md)** 함수입니다. 이 수식은 첫 번째 화면이 나타나기 전에 평가됩니다. 화면이 로드되지 않으므로 **[UpdateContext](function-updatecontext.md)** 함수로 컨텍스트 변수를 설정할 수 없습니다. 그러나 **Navigate** 함수를 사용하여 컨텍스트 변수를 전달할 수 있습니다. |

**앱** 개체는 왼쪽 탐색 창에서 컨트롤의 계층적 목록 맨 위에서 표시되고, 화면의 컨트롤처럼 개체를 선택할 수 있습니다. 개체를 선택한 후에 수식 입력줄의 왼쪽 드롭다운 목록에서 해당 속성을 선택하면 해당 속성 중 하나를 편집하고 볼 수 있습니다.  

**OnStart** 속성을 변경한 후, 왼쪽된 탐색 창에서 **앱** 개체를 마우스로 가리키고 나타나는 줄임표(...)를 선택한 다음 **Run OnStart**를 선택하여 테스트할 수 있습니다. 앱이 처음 로드될 때와 달리 기존 컬렉션과 변수가 미리 설정됩니다. 빈 컬렉션으로 시작하기 위해서는 **Collect** 함수 대신 **[ClearCollect](function-clear-collect-clearcollect.md)** 함수를 대신 사용합니다.

 ![OnStart 실행을 사용 하 여 앱 항목 상황에 맞는 메뉴](media/appobject-runonstart.png)

### <a name="compass"></a>Compass
**나침반** 신호는 화면 맨 위의 나침반 방향을 반환합니다. 방향은 자기장의 북쪽을 기준으로 합니다.

| 속성 | 설명 |
| --- | --- |
| **Compass.Heading** |각도 단위의 방향입니다.  숫자 0~360을 반환하고 0이 북쪽입니다. |

### <a name="connection"></a>연결
**연결** 신호는 네트워크 연결 관련 정보를 반환합니다. 측정되는 연결에서 네트워크를 통해 보내거나 받는 데이터 크기를 제한하려 할 수 있습니다.

| 속성 | 설명 |
| --- | --- |
| **Connection.Connected** |디바이스의 네트워크 연결 여부를 표시하는 부울 값 **true** 또는 **false**를 반환합니다. |
| **Connection.Metered** |연결의 측정 여부를 표시하는 부울 값 **true** 또는 **false**를 반환합니다. |

### <a name="location"></a>위치
**위치** 신호는 GPS(Global Positioning System) 기준 디바이스 위치와, 셀 타워 통신 및 IP 주소와 같은 기타 디바이스 정보를 반환합니다.

사용자가 처음으로 위치 정보에 액세스할 때 디바이스는 이 정보에 대한 액세스를 허용하라는 메시지를 사용자에게 표시할 수 있습니다.

위치가 바뀌면 해당 위치에 대한 종속성이 지속적으로 재계산되며 디바이스의 배터리에서 전력을 소비합니다. 배터리를 절약하기 위해 **[Enable](function-enable-disable.md)** 및 **[Disable](function-enable-disable.md)** 함수를 사용하여 위치 업데이트를 끄고 켤 수 있습니다. 표시되는 화면이 위치 정보에 종속되지 않은 경우 위치가 자동으로 꺼집니다.

| 속성 | 설명 |
| --- | --- |
| **Location.Altitude** |피트 단위로 해발 고도를 표시하는 숫자를 반환합니다. |
| **Location.Latitude** |적도로부터 도 단위로 측정되는 경도를 나타내는 숫자 -90~90을 반환합니다.  양수 값이 적도 북쪽의 지역을 나타냅니다. |
| **Location.Longitude** |영국 그리니치로부터 도 단위로 측정되는 경도를 나타내는 숫자 0~180을 반환합니다.  |

## <a name="examples"></a>예
야구장에서, 투수는 마운드에서 홈 플레이트의 포수에게 휴대전화를 던집니다. 휴대전화는 그라운드에 평행하게 있다가 화면 위쪽이 포수를 향하고 투수가 회전을 더하지 않습니다. 이 위치에서 휴대전화에는 측정되는 셀룰러 네트워크 서비스가 있지만 WiFi는 없습니다. **PlayBall** 화면이 표시됩니다.   

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Location.Latitude** |현재 위치의 위도를 반환합니다. 필드는 지도 좌표 47.591 N, 122.333 w입니다. |47.591<br><br>전화가 투수와 포수 사이를 이동하는 동안 위도는 지속적으로 바뀝니다. |
| **Location.Longitude** |현재 위치의 경도를 반환합니다. |122.333<br><br>전화가 투수와 포수 사이를 이동하는 동안 경도는 지속적으로 바뀝니다. |
| **Location** |현재 위치의 위도 및 경도를 레코드로 반환합니다. |{&nbsp;Latitude:&nbsp;47.591, Longitude:&nbsp;122.333&nbsp;} |
| **Compass.Heading** |화면 맨 위의 나침반 방향을 반환합니다. 이 필드를 홈 플레이트는 투 플레이트에서 약 남서쪽입니다. |230.25 |
| **Acceleration.X** |디바이스의 측면 방향 가속도를 반환합니다. 투수가 화면 맨위에 대해 직선 방향으로 휴대전화를 던지므로 디바이스에는 측면 방향 가속도가 없습니다. |0 |
| **Acceleration.Y** |디바이스의 전후 방향 가속도를 반환합니다. 투수가 처음에 디바이스를 던질 때는 디바이스에 높은 가속도가 부여되며 0.5초 안에 시간당 0에서 90마일(초당 132피트)로 가속됩니다. 디바이스가 공중에 오른 뒤 공기 마찰을 무시하고 디바이스는 더 이상 가속되지 않습니다. 포수가 디바이스를 잡을 때 디바이스가 가속이 줄어 멈추게 됩니다. |투수가 디바이스를 던지는 동안 8.2<br><br>디바이스가 공중에 있을 때 0<br><br>포수가 디바이스를 잡을 때 -8.2 |
| **Acceleration.Z** |디바이스의 상하 방향 가속도를 반환합니다. 공중에 있는 동안 디바이스는 중력의 영향을 받습니다. |투수가 디바이스를 던지기 전 0<br><br>디바이스가 공중에 있을 때 1<br><br>포수가 디바이스를 잡은 후 0 |
| **Acceleration** |가속을 레코드로 반환합니다. |{ X: 0, Y: 264, Z: 전화가 투 수로 0}의 장치를 throw합니다. |
| **Connection.Connected** |디바이스의 네트워크 연결 여부를 표시하는 부울 값을 반환합니다. |**true** |
| **Connection.Metered** |연결의 측정 여부를 표시하는 부울 값을 반환합니다. |**true** |
| **App.ActiveScreen = PlayBall** |**PlayBall** 표시 여부를 표시하는 부울 값을 반환합니다. |**true** |
| **App.ActiveScreen.Fill** |표시되는 화면의 배경색을 반환합니다. |**Color.Green** |

