---
title: 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값 | Microsoft Docs
description: Power Apps에서 빌드된 canvas 앱에 대 한 시스템 요구 사항, 제한 및 구성 값
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed59b379b55a38a1e5a3454d26d07ae93d106e4f
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75204114"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
이 항목에는 canvas 앱에 대 한 제한 및 구성 값 뿐만 아니라 장치 플랫폼 및 웹 브라우저 요구 사항이 포함 되어 있습니다.

## <a name="supported-platforms-for-running-canvas-apps-using-the-power-apps-mobile-app"></a>Power Apps 모바일 앱을 사용 하 여 캔버스 앱을 실행 하는 데 지원 되는 플랫폼

| **필요한 최소 사항** | **권장** |
| --- | --- |
| iOS 12 이상 |iOS 12 이상|
| Android 7 이상 |Android 7 이상 |
| Windows 8.1 이상(PC만 해당) |최소 8GB의 RAM이 있는 Windows 10 Fall Creators Update|

> [!NOTE]
> 현재는 Power Apps 용 Windows 플랫폼 [모바일 앱](/powerapps/user/run-app-client)에서 새 기능을 지원 하지 않습니다. 이 플랫폼에서는 향상 된 Common Data Service 옵션 및 게스트 액세스와 같은 기능을 사용할 수 없습니다. Windows에서 웹 플레이어를 사용 하 여 전체 기능 집합을 활용 하는 것이 좋습니다. Windows 플랫폼용 Power Apps 모바일 앱에 대 한 업데이트는 나중에 발표 될 예정입니다.

## <a name="supported-browsers-for-running-canvas-apps"></a>캔버스 앱 실행에 지원되는 브라우저

| **브라우저** | **운영 체제** |
| --- | --- |
| Google Chrome(최신 버전)<br>(권장) |Windows 7 SP1, 8.1 및 10 <br>Android 5 이상 <br>iOS 8 이상<br>macOS |
| Microsoft Edge(최신 버전)<br>(권장) |Windows 10 |
| Microsoft Internet Explorer 11(호환성 보기 해제) |Windows 7 SP1, 8.1 및 10 |
| Mozilla Firefox(최신 버전) |Windows 7 SP1, 8.1 및 10 <br> Android 5 이상 <br>iOS 8 이상 <br>macOS |
| Apple Safari(최신 버전) |iOS 8 이상 <br>macOS |

## <a name="supported-browsers-for-power-apps-studio"></a>Power Apps Studio에 대해 지원 되는 브라우저

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
Power Apps의 요청은 앱이 있는 [환경의](../../administrator/environments-overview.md) 지역에 의존 하는 IP 주소를 사용 합니다. Power Apps 시나리오에 사용할 수 있는 정규화 된 도메인 이름은 게시 하지 않습니다.

이 항목의 뒷부분에서 지정된 IP 주소에서 앱(예: SQL API 또는 SharePoint API)을 통해 연결된 API의 호출이 비롯됩니다.

예를 들어, Azure SQL Database에 대한 IP 주소를 허용 목록에 추가해야 하는 경우 이러한 주소를 사용합니다.

> [!IMPORTANT]
>   기존 구성이 있는 경우 2018 년 9 월 30 일 이전에 가능한 한 빨리 업데이트 하세요. 그러면 Power Apps 앱이 있는 지역에 대해이 목록의 IP 주소를 포함 하 고 일치 시킵니다.

| Region | 아웃바운드 IP |
| --- | --- |
| 아시아 | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| 오스트레일리아  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| 브라질 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| 캐나다 | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| Europe | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| 인도  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| 일본 | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 남아메리카 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| 영국 | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| 미국 | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 미국(초기 액세스)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>필수 서비스
이 목록은 Power Apps Studio에서 사용 하는 모든 서비스와 해당 용도를 식별 합니다. 네트워크는 이러한 서비스를 차단하지 **않아야** 합니다.

| 도메인 | 프로토콜 | 사용 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |커넥터 런타임/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph-사용자 정보 (예: 프로필 사진)를 가져오는 데 사용 됩니다. |
| gallery.azure.com |https |샘플 및 템플릿 앱 |
| \*azure-apim.net |https |API 허브 - 각 로캘에 대해 다른 하위 도메인 |
| \*powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 make.powerapps.com |
| \*azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 make.powerapps.com |
| \*blob.core.windows.net |https | Blob 저장소 |
| \*flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com 및 make.powerapps.com |
| *. dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |분석이 |
| localhost | https | Power Apps 모바일

> [!NOTE]
> VPN을 사용 하는 경우 Power Apps Mobile에 대해 터널링에서 localhost를 제외 하도록 구성 해야 합니다.

## <a name="size-limits"></a>크기 제한

텍스트, 하이퍼링크, 이미지 및 미디어의 [데이터 형식](functions/data-types.md#text-hyperlink-image-and-media)에 대 한 크기 제한에 대 한 정보를 찾을 수 있습니다.

## <a name="power-apps-per-app-plan"></a>앱 요금제 당 Power Apps

이제이 정보는 Power Platform 관리자 가이드의 [앱 요금제 별 Power Apps](/power-platform/admin/signup-for-powerapps-admin#power-apps-per-app-plan) 섹션에서 사용할 수 있습니다.
