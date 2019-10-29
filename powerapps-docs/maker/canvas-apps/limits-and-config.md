---
title: 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값 | Microsoft Docs
description: PowerApps에서 기본 제공되는 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/24/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 68e702156b0a5b820dd23076551cf7970efc65a3
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025097"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
이 항목은 디바이스 플랫폼 및 웹 브라우저 요구 사항뿐만 아니라 PowerApps에 대한 제한 사항 및 구성 값을 포함합니다.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>PowerApps 앱을 사용하여 캔버스 앱을 실행하는 데 지원되는 플랫폼

| **필요한 최소 사항** | **권장** |
| --- | --- |
| iOS 9.3 이상 |최소 2GB의 RAM이 있는 iOS 10 이상 |
| Android 5 이상 |최소 4GB의 RAM이 있는 Android 7 이상 |
| Windows 8.1 이상(PC만 해당) |최소 8GB의 RAM이 있는 Windows 10 Fall Creators Update|

> [!NOTE]
> 현재 PowerApps 앱 용 Windows 플랫폼에서 새로운 기능을 지원 하지 않습니다. 이 플랫폼에서는 향상 된 Common Data Service 옵션 및 게스트 액세스와 같은 기능을 사용할 수 없습니다. Windows에서 웹 플레이어를 사용 하 여 전체 기능 집합을 활용 하는 것이 좋습니다. Windows 플랫폼용 PowerApps 앱에 대 한 업데이트는 나중에 발표 될 예정입니다.

## <a name="supported-browsers-for-running-canvas-apps"></a>캔버스 앱 실행에 지원되는 브라우저

| **브라우저** | **운영 체제** |
| --- | --- |
| Google Chrome(최신 버전)<br>(권장) |Windows 7 SP1, 8.1 및 10 <br>Android 5 이상 <br>iOS 8 이상<br>macOS |
| Microsoft Edge(최신 버전)<br>(권장) |Windows 10 |
| Microsoft Internet Explorer 11(호환성 보기 해제) |Windows 7 SP1, 8.1 및 10 |
| Mozilla Firefox(최신 버전) |Windows 7 SP1, 8.1 및 10 <br> Android 5 이상 <br>iOS 8 이상 <br>macOS |
| Apple Safari(최신 버전) |iOS 8 이상 <br>macOS |

## <a name="supported-browsers-for-powerapps-studio"></a>PowerApps Studio에 대해 지원되는 브라우저

| **브라우저** | **운영 체제** |
| --- | --- |
| Google Chrome(최신 버전)<br>(권장) |Windows 7 SP1, 8.1 및 10 <br>macOS |
| Microsoft Edge(최신 버전)<br>(권장) |Windows 10 |
| Microsoft Internet Explorer 11(호환성 보기 해제) |Windows 7 SP1, 8.1 및 10 |

## <a name="request-limits"></a>요청 제한
이러한 제한은 보내는 단일 요청 각각에 적용됩니다.

| 이름 | 제한 |
| --- | --- |
| 시간 제한 |180초 |
| 재시도 횟수 |4 |

> [!NOTE]
> 재시도 값은 달라질 수 있습니다. 특정 오류 조건의 경우 재시도가 필요하지 않습니다.

## <a name="ip-addresses"></a>IP 주소
PowerApps의 요청은 앱이 위치한 [환경](../../administrator/environments-overview.md)의 지역에 따라 다른 IP 주소를 사용합니다. PowerApps 시나리오에 사용할 수 있는 정규화된 도메인 이름을 게시하지 않습니다.

이 항목의 뒷부분에서 지정된 IP 주소에서 앱(예: SQL API 또는 SharePoint API)을 통해 연결된 API의 호출이 비롯됩니다.

예를 들어, Azure SQL Database에 대한 IP 주소를 허용 목록에 추가해야 하는 경우 이러한 주소를 사용합니다.

> [!IMPORTANT]
>   PowerApps 앱이 위치한 지역의 경우 이 목록의 IP 주소를 포함하고 일치하도록 기존 구성이 있는 경우 2018년 9월 30일 전에 최대한 신속하게 업데이트하세요.

| 국가별 | 아웃바운드 IP |
| --- | --- |
| 아시아 | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| 오스트레일리아  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| 브라질 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| 캐나다 | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| 유럽 | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| 인도  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| 일본 | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 남아메리카 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| 영국 | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| 미국 | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 미국(초기 액세스)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>필수 서비스
PowerApps Studio에서 통신하고 사용하는 모든 서비스를 식별하는 목록입니다. 네트워크는 이러한 서비스를 차단하지 **않아야** 합니다.

| 도메인 | 인터넷용 | 사용 |
| --- | --- | --- |
| management.azure.com |http |RP |
| msmanaged-na.azure-apim.net |http |커넥터 런타임/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |http |ADAL |
| graph.microsoft.com<br>graph.windows.net |http |Azure Graph-사용자 정보 (예: 프로필 사진)를 가져오는 데 사용 됩니다. |
| gallery.azure.com |http |샘플 및 템플릿 앱 |
| \* azure-apim.net |http |API 허브 - 각 로캘에 대해 다른 하위 도메인 |
| \* powerapps.com |http | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 web.powerapps.com |
| \* azureedge.net |http | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 web.powerapps.com |
| \* blob.core.windows.net |http | Blob 저장소 |
| \* flow.microsoft.com | http | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 web.powerapps.com |
| *. dynamics.com | http | Common Data Service |
| vortex.data.microsoft.com |http |분석이 |
| 호스트 | http | PowerApps Mobile

> [!NOTE]
> VPN을 사용하는 경우 PowerApps Mobile을 위한 터널링에서 localhost를 제외하도록 구성해야 합니다.

## <a name="size-limits"></a>크기 제한

텍스트, 하이퍼링크, 이미지 및 미디어의 [데이터 형식](functions/data-types.md#text-hyperlink-image-and-media)에 대 한 크기 제한에 대 한 정보를 찾을 수 있습니다.

## <a name="powerapps-per-app-plan"></a>앱 요금제 별 PowerApps

앱 요금제 당 PowerApps를 사용 하면 개별 사용자가 PowerApps의 전체 기능을 기반으로 하는 특정 비즈니스 시나리오에 대해 단일 포털에서 2 개의 응용 프로그램을 실행할 수 있습니다. 이 계획은 사용자가 보다 폭넓은 규모 도입 전에 플랫폼을 시작할 수 있는 쉬운 방법을 제공 합니다.

관리자가 앱 계획 당 PowerApps를 환경에 할당 하면 앱을 공유할 때 기본적으로 사용자에 게 할당 됩니다. 관리자가 앱 계획 별로 할당 하는 방법을 볼 [수 있습니다.](https://docs.microsoft.com/power-platform/admin/capacity-add-on)

앱이 공유 될 때 사용자에 대 한 앱 요금제 할당을 해제 하려면 다음 단계를 수행 합니다.

- **앱**을 선택 합니다.
- **설정**을 선택 합니다.
- **Pass** **assign에서 앱 당 자동 할당 통과** 를 전환 합니다.

**앱 당 자동 할당 통과** 는 모든 앱 설정에 표시 됩니다.

> [!NOTE]
> 앱 당 계획을 사용 하지 않도록 설정 하는 것은 현재 캔버스 앱에만 사용할 수 있습니다.  모델 기반 앱 및 포털은 나중에이 기능을 제공 합니다.

### <a name="app-settings"></a>앱 설정

![Canvas 앱 설정](./media/limits-and-config/app_settings.png "Canvas 앱 설정")

### <a name="pass-assignment"></a>통과 할당

![Canvas 앱 설정 패스 할당](./media/limits-and-config/app_settings_pass_assignment.png "Canvas 앱 설정 패스 할당")
