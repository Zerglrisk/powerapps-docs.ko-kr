---
title: PowerApps 구성 요소 프레임 워크에 대 한 도구 받기 | Microsoft Docs
description: PowerApps 구성 요소 프레임 워크를 사용 하 여 코드 구성 요소를 작성, 디버그 및 배포 하는 Microsoft PowerApps CLI를 가져옵니다.
keywords: PowerApps 구성 요소 프레임 워크, 코드 구성 요소, 구성 요소 프레임 워크
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2019
ms.locfileid: "72340026"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>PowerApps 구성 요소 프레임 워크에 대 한 도구 가져오기

**MICROSOFT POWERAPPS CLI** (명령줄 인터페이스)를 사용 하 여 PowerApps 구성 요소 프레임 워크를 사용 하 여 코드 구성 요소를 만들고, 디버그 하 고, 배포할 수 있습니다. 개발자는 PowerApps CLI를 사용 하 여 코드 구성 요소를 신속 하 게 만들 수 있습니다. 향후에는 추가 개발 및 ALM (애플리케이션 수명 주기 관리) 환경에 대 한 지원을 포함 하도록 확장 될 예정입니다. 

## <a name="what-is-microsoft-powerapps-cli"></a>CLI Microsoft PowerApps 

CLI Microsoft PowerApps 개발자와 앱 제작자가 코드 구성 요소를 만들 수 있도록 하는 간단한 단일 중단 개발자 명령줄 인터페이스입니다. PowerApps CLI 도구는 엔터프라이즈 개발자 및 Isv가 확장과 사용자 지정을 빠르고 효율적으로 만들고, 빌드하고, 디버그 하 고, 게시할 수 있는 포괄적인 ALM 스토리를 위한 첫 번째 단계입니다.  

## <a name="install-microsoft-powerapps-cli"></a>CLI Microsoft PowerApps 설치

CLI Microsoft PowerApps을 가져오려면 다음을 수행 합니다.

1. [Npm](https://www.npmjs.com/get-npm) (node.js와 함께 제공) 또는 [node.js](https://nodejs.org/en/) (Npm와 함께 제공)를 설치 합니다. LTS (장기 지원) 버전 10.15.3 LTS는 가장 안정적이 지 않기 때문에 권장 됩니다.

1. [.NET Framework 4.6.2 Developer Pack](https://dotnet.microsoft.com/download/dotnet-framework/net462)을 설치 합니다. 

1. Visual Studio 2017 이상이 아직 없는 경우 다음 옵션 중 하나를 수행 합니다.
   - 옵션 1: [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) 이상 버전을 설치 합니다.
   - 옵션 2: [.Net Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 를 설치한 후 [Visual Studio Code](https://code.visualstudio.com/Download)를 설치 합니다.

1. [CLI Microsoft PowerApps](https://aka.ms/PowerAppsCLI)를 설치 합니다.
1. 모든 최신 기능을 활용 하려면 다음 명령을 사용 하 여 PowerApps CLI 도구를 최신 버전으로 업데이트 합니다.

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - PowerApps CLI를 사용 하 여 코드 구성 요소를 배포 하려면 시스템 관리자 또는 시스템 사용자 지정자 권한이 있는 Common Data Service 환경이 있어야 합니다.
> - 현재 PowerApps CLI는 Windows 10 에서만 지원 됩니다.

## <a name="microsoft-powerapps-cli-telemetry"></a>CLI 원격 분석 Microsoft PowerApps

기능 팀은 PowerApps CLI 도구에서 가장 자주 사용 되는 기능 및 기능 개발자를 이해 하기 위해 원격 분석을 집계 합니다. 집계 된 데이터를 사용 하면 필수 항목에 집중 하 여 고객에 게 최상의 환경을 제공할 수 있습니다.

> [!NOTE]
> 원격 분석 컬렉션을 사용 하지 않도록 설정 하려면 `pac telemetry disable` 명령을 실행 합니다. 원격 분석을 다시 설정 하려면 명령 `pac telemetry enable`를 사용 합니다.


## <a name="uninstall-microsoft-powerapps-cli"></a>CLI Microsoft PowerApps 제거

PowerApps CLI 도구를 제거 하려면 [여기](https://aka.ms/PowerAppsCLI)에서 MSI를 실행 합니다. 

비공개 미리 보기 참가자이 고 이전 버전의 CLI가 있는 경우 다음 단계를 수행 합니다.

1. PowerApps CLI가 설치 된 위치를 확인 하려면 명령 프롬프트를 열고 `where pac`를 입력 합니다.
1. PowerAppsCLI 폴더를 삭제 합니다.
1. 명령 프롬프트에서 명령 `rundll32 sysdm.cpl,EditEnvironmentVariables`를 실행 하 여 환경 변수 도구를 엽니다.
1. @No__t_1 섹션에서 `Path`을 두 번 클릭 합니다.
1. PowerAppsCLI 경로를 포함 하는 행을 선택 하 고 오른쪽에 있는 **삭제** 단추를 선택 합니다.
1. **확인을** 두 번 선택 합니다.

### <a name="see-also"></a>참고 항목

[TypeScript를 사용 하 여 구성 요소 구현](implementing-controls-using-typescript.md)<br/>
