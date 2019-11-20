---
title: 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값 | Microsoft Docs
description: PowerApps에서 기본 제공되는 캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
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
ms.openlocfilehash: 1c8591790fe14d184f5d5e4ef5fc79ff0bfe0e2a
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177889"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>캔버스 앱의 시스템 요구 사항, 제한 및 구성 값
이 항목은 디바이스 플랫폼 및 웹 브라우저 요구 사항뿐만 아니라 PowerApps에 대한 제한 사항 및 구성 값을 포함합니다.

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>PowerApps 앱을 사용하여 캔버스 앱을 실행하는 데 지원되는 플랫폼

| **필요한 최소 사항** | **권장** |
| --- | --- |
| iOS 12 or later |iOS 12 or later|
| Android 7 or later |Android 7 or later |
| Windows 8.1 이상(PC만 해당) |최소 8GB의 RAM이 있는 Windows 10 Fall Creators Update|

> [!NOTE]
> We currently don't support new features on Windows platform for PowerApps app. Features such as the Improved Common Data Service option and guest access are not available on this platform. We recommend using a web player on Windows to leverage the full set of capabilities. Updates to the PowerApps app for Windows platform will be announced in future.

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

| 이름 | Limit |
| --- | --- |
| 시간 제한 |180초 |
| 재시도 횟수 |4 |

> [!NOTE]
> 재시도 값은 달라질 수 있습니다. 특정 오류 조건의 경우 재시도가 필요하지 않습니다.

## <a name="ip-addresses"></a>IP addresses
PowerApps의 요청은 앱이 위치한 [환경](../../administrator/environments-overview.md)의 지역에 따라 다른 IP 주소를 사용합니다. PowerApps 시나리오에 사용할 수 있는 정규화된 도메인 이름을 게시하지 않습니다.

이 항목의 뒷부분에서 지정된 IP 주소에서 앱(예: SQL API 또는 SharePoint API)을 통해 연결된 API의 호출이 비롯됩니다.

예를 들어, Azure SQL Database에 대한 IP 주소를 허용 목록에 추가해야 하는 경우 이러한 주소를 사용합니다.

> [!IMPORTANT]
>   PowerApps 앱이 위치한 지역의 경우 이 목록의 IP 주소를 포함하고 일치하도록 기존 구성이 있는 경우 2018년 9월 30일 전에 최대한 신속하게 업데이트하세요.

| Region | 아웃바운드 IP |
| --- | --- |
| Asia | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| Australia  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| Brazil | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| Canada | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| Europe | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| India  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| Japan | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 남아메리카 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| United Kingdom | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| United States | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 미국(초기 액세스)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>필수 서비스
PowerApps Studio에서 통신하고 사용하는 모든 서비스를 식별하는 목록입니다. 네트워크는 이러한 서비스를 차단하지 **않아야** 합니다.

| 도메인 | Protocols | 사용 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |커넥터 런타임/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (e.g., profile photo) |
| gallery.azure.com |https |샘플 및 템플릿 앱 |
| \*.azure-apim.net |https |API 허브 - 각 로캘에 대해 다른 하위 도메인 |
| \*.powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.blob.core.windows.net |https | Blob storage |
| \*.flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| *.dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |Telemetry |
| localhost | https | PowerApps Mobile

> [!NOTE]
> VPN을 사용하는 경우 PowerApps Mobile을 위한 터널링에서 localhost를 제외하도록 구성해야 합니다.

## <a name="size-limits"></a>Size limits

You can find information about size limits on text, hyperlinks, images, and media in [Data types](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="powerapps-per-app-plan"></a>PowerApps per app plan

PowerApps per app plan allows individual users to run 2 applications on a single portal for a specific business scenario based on the full capabilities of PowerApps. This plan provides an easy way for users to get started with the platform before broader scale adoption.

After an admin allocates PowerApps per app plan to an environment, they're assigned to unlicensed users when an app in that environment is shared with them. You can see how an admin allocates per app plans [here](https://docs.microsoft.com/power-platform/admin/capacity-add-on).

Follow these steps to turn off the assigning per app plans for users when an app is shared with them:

- Choose the **App**.
- Select **Settings**.
- Change the **Auto assign per app passes** toggle under **Pass assignment**.

The **Auto assign per app passes** toggle appears in all app setting.

> [!NOTE]
> Disabling the per app plan is currently available for only canvas apps.  Model-driven apps and Portals will have this ability in the future.
>
> The ability to control per app plan assignment for an app is only available for apps that are in an environment that had Per app plans allocated in the [Power Platform Admin center](https://admin.powerplatform.microsoft.com).  

### <a name="app-settings"></a>App Settings

![Canvas app settings](./media/limits-and-config/app_settings.png "Canvas app settings")

### <a name="pass-assignment"></a>Pass assignment

![Canvas app settings pass assignment](./media/limits-and-config/app_settings_pass_assignment.png "Canvas app settings pass assignment")
