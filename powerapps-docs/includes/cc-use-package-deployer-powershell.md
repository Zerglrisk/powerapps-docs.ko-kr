---
ms.openlocfilehash: 215a6d9fb0890bd6d93843b0b649ada4203e5600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224197"
---
Package Deployer 도구에 대한 PowerShell 파일은 [NuGet 패키지](https://go.microsoft.com/fwlink/?linkid=859211)로 사용 가능합니다. 사용하려면 이를 다운로드하고 **nuget.exe**를 사용하여 로컬 컴퓨터에 추출해야 합니다.<br/><br/>

<https://www.nuget.org/downloads>에서 **nuget.exe**를 다운로드하고 컴퓨터의 **d:\\** 에 저장합니다. 그런 다음, 명령 프롬프트에서 다음 명령을 실행하여 패키지 콘텐츠를 컴퓨터의 **PD-PowerShell** 등의 폴더로 추출합니다.<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Package Deployer 도구에 대한 PowerShell 파일을 추출한 후 `[ExtractedLocation]\tools` 폴더로 이동하여 필요한 파일을 찾습니다. 
