---
title: 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값 | Microsoft Docs
description: PowerApps에서 기본 제공되는 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/07/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0c972120a70df8471f27a2b6e4e99f7a66182e04
ms.sourcegitcommit: 065b3b210273e5fe9025d41d27a08a62dfa16d03
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64904049"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
이 항목은 디바이스 플랫폼 및 웹 브라우저 요구 사항뿐만 아니라 PowerApps에 대한 제한 사항 및 구성 값을 포함합니다.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>PowerApps 앱을 사용하여 캔버스 앱을 실행하는 데 지원되는 플랫폼

| **필요한 최소 사항** | **권장** |
| --- | --- |
| iOS 9.3 이상 |최소 2GB의 RAM이 있는 iOS 10 이상 |
| Android 5 이상 |최소 4GB의 RAM이 있는 Android 7 이상 |
| Windows 8.1 이상(PC만 해당) |최소 8GB의 RAM이 있는 Windows 10 Fall Creators Update|

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

| 지역 | 아웃바운드 IP |
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

| 도메인 | 프로토콜 | 사용 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |커넥터 런타임/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - 사용자 정보를 가져오는 경우(예: 프로필 사진) |
| gallery.azure.com |https |샘플 및 템플릿 앱 |
| \*.azure-apim.net |https |API 허브 - 각 로캘에 대해 다른 하위 도메인 |
| \*.powerapps.com |https |WebAuth + 포털 |
| \*.azureedge.net |https |WebAuth |
| \*.blob.core.windows.net |https |Blob 저장소 |
| vortex.data.microsoft.com |https |원격 분석 |

> [!NOTE]
> VPN을 사용하는 경우 PowerApps Mobile을 위한 터널링에서 localhost를 제외하도록 구성해야 합니다.
