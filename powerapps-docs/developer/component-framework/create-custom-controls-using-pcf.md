---
title: 코드 구성 요소 만들기 및 빌드 | Microsoft Docs
description: PowerApps 구성 요소 프레임 워크 도구를 사용 하 여 구성 요소 만들기 시작
keywords: PowerApps 구성 요소 프레임 워크, 코드 구성 요소, 구성 요소 프레임 워크
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 9a02b64321564b0a09e6b53223f13748358d76cf
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025790"
---
# <a name="create-and-build-a-code-component"></a>코드 구성 요소 만들기 및 빌드

이 항목에서는 PowerApps CLI를 사용 하 여 코드 구성 요소를 만들고 배포 하는 방법을 보여 줍니다. [CLI Microsoft PowerApps](https://aka.ms/PowerAppsCLI)를 설치 했는지 확인 합니다.

## <a name="create-a-new-component"></a>새 구성 요소 만들기

시작 하려면 PowerApps CLI를 설치한 후 **VS 2017에 대 한 개발자 명령 프롬프트** 를 엽니다.

1. VS 2017에 대 한 개발자 명령 프롬프트에서 명령 `mkdir <Specify the folder name>`를 사용 하 여 로컬 컴퓨터에 새 폴더를 만듭니다 (예: *C:\Users\your Atedocumentss\my_code__l)* .
2. `cd <specify your new folder path>`명령을 사용 하 여 새로 만든 폴더로 이동 합니다.
3. 명령을 사용 하 여 몇 가지 기본 매개 변수를 전달 하 여 새 구성 요소 프로젝트를 만듭니다.

    `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>`
 
   > [!NOTE]
   > 현재 PowerApps CLI는 모델 기반 앱에 대 한 **필드** 와 **데이터 집합** 이라는 두 가지 유형의 구성 요소를 지원 합니다.  Canvas 앱의 경우에는이 실험적 미리 보기에 대해 **필드** 형식만 지원 됩니다.

4. 모든 필수 프로젝트 종속성을 검색 하려면 `npm install` 명령을 실행 합니다.
5. 선택한 개발자 환경에서 `C:\Users\<your name>\Documents\<My_code_Component>` 프로젝트 폴더를 열고 코드 구성 요소 개발을 시작 합니다. 시작 하는 가장 빠른 방법은 `C:\Users\<your name>\Documents\<My_code_Component>` 디렉터리에 있는 명령 프롬프트에서 `code .`를 실행 하는 것입니다. 이 명령은 Visual Studio Code 구성 요소 프로젝트를 엽니다.
6. 매니페스트, 구성 요소 논리 및 스타일 지정과 같은 구성 요소에 필요한 아티팩트를 구현한 다음 구성 요소 프로젝트를 빌드합니다. 추가 정보: [샘플 구성 요소 구현](implementing-controls-using-typescript.md)

## <a name="build-your-component"></a>구성 요소 빌드

구성 요소 프로젝트를 빌드하려면 Visual Studio Code에서 `package.json` 들어 있는 프로젝트 폴더를 열고 (Ctrl + Shift-B) 명령을 사용 하 여 빌드 옵션을 선택 합니다. 또는 VS 2017에 대 한 개발자 명령 프롬프트 창에서 `npm run build` 명령을 사용 하 여 구성 요소를 신속 하 게 빌드할 수 있습니다.

> [!TIP]
> 빌드 작업 중 또는 이후에 구성 요소를 디버깅 하려면 [코드 구성 요소 디버그](debugging-custom-controls.md)를 참조 하세요.

TypeScript에서 구성 요소 논리를 구현 하는 작업이 완료 되 면 솔루션을 Common Data Service으로 가져올 수 있도록 모든 코드 구성 요소 요소를 솔루션 파일에 번들 해야 합니다. 추가 정보: [패키지 a 코드 구성 요소](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>알려진 구성 문제 및 해결 방법

**Msbuild 오류 MSB4036:**

1. 프로젝트 파일의 작업 이름은 작업 클래스의 이름과 동일 합니다.
2. 작업 클래스는 public이 고 ITask 인터페이스를 구현 합니다.
3. 작업은 프로젝트 파일이 나 path 디렉터리에 있는 *. tasks 파일의 *\<UsingTask >* 를 사용 하 여 올바르게 선언 됩니다.

**해결책이**

1. Visual Studio 설치 관리자를 엽니다. 
1. Visual Studio 2017의 경우 **수정**을 선택 합니다. 
1. **개별 구성 요소**를 선택 합니다.
1. 코드 도구에서 **NuGet 대상 & 빌드 작업**을 선택 합니다.

**게시자 접두사**

0\.4.3 보다 낮은 PowerApps CLI 도구 버전을 사용 하 여 구성 요소를 만든 경우 솔루션 파일을 Common Data Service으로 다시 가져오는 동안 오류가 발생 합니다. 새로 가져온 구성 요소 이름이 이제 게시자 접두사와 함께 추가 되어 고유성이 보장 되 고 충돌을 방지 하기 때문에 오류가 발생 합니다.

**해결 방법**:

- Common Data Service에서 관련 구성 요소가 포함 된 솔루션을 삭제 합니다. 구성 요소가 폼 이나 표에 이미 구성 되어 있는 경우 구성 요소 솔루션이 구성에 종속 되어 있기 때문에 먼저 해당 구성 요소가 제거 되어야 합니다.  
- 최신 CLI 버전으로 작성 된 구성 요소에 대 한 업데이트로 새 솔루션을 가져옵니다.
- 이제 폼 이나 그리드에서 새로 가져온 구성 요소를 구성할 수 있습니다.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>참고 항목

[디버그 코드 구성 요소](debugging-custom-controls.md)<br/>
[코드 구성 요소 패키지](import-custom-controls.md)<br/>
[필드 또는 엔터티에 코드 구성 요소 추가](add-custom-controls-to-a-field-or-entity.md)<br/>
[기존 코드 구성 요소 업데이트](updating-existing-controls.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
