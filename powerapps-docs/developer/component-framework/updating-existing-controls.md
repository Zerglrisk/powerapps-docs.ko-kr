---
title: PowerApps 구성 요소 프레임 워크 도구를 사용 하 여 기존 코드 구성 요소 업데이트 | Microsoft Docs
description: PowerApps 구성 요소 프레임 워크 도구를 사용 하 여 구성 요소 업데이트
keywords: PowerApps 구성 요소 프레임 워크, 코드 구성 요소, 구성 요소 프레임 워크
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 05e32fb7e098dad3aabf36f2efdaf311c1bea327
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340233"
---
# <a name="update-existing-code-components"></a>기존 코드 구성 요소 업데이트 

모델 기반 앱에 대 한 PowerApps 구성 요소 프레임 워크 비공개 미리 보기 참가자이 고 이미 코드 구성 요소를 빌드한 경우에는 몇 가지 사소한 업데이트를 수행 하 여 새 ALM 중심 프로젝트 구조와 호환 되도록 해야 합니다. 

기존 PowerApps 구성 요소 프레임 워크 코드 구성 요소와 함께 새 PowerApps CLI 도구를 사용 하려면 몇 가지 사항을 변경 해야 합니다.

> [!NOTE]
> 이 항목은 모델 기반 앱에 대 한 비공개 미리 보기 시 PowerApps CLI 도구를 사용할 수 없기 때문에 모델 기반 앱에 대 한 코드 구성 요소를 업데이트 하는 경우에만 적용할 수 있습니다.  

## <a name="creating-an-empty-project"></a>빈 프로젝트 만들기

PowerApps CLI를 사용 하 여 코드 구성 요소에 대 한 빈 프로젝트를 새로 만듭니다. 추가 정보: [도구를 사용 하 여 구성 요소 만들기](create-custom-controls-using-pcf.md)

프로젝트가 생성 되 면 코드 구성 요소 원본을 새 프로젝트로 마이그레이션합니다.

1. 이전 원본 파일의 구성 요소 원본 파일을 **인덱스나**로 복사 하거나 바꿉니다.
2. **Controlmanifest** 의 내용을 **Controlmanifest. Input .xml** 파일로 복사 하거나 바꿉니다.
3. CSS, RESX 또는 IMG와 같은 기타 모든 주변 구성 요소 리소스를 이전 프로젝트에서 새 프로젝트로 해당 하위 폴더에 복사 합니다.

## <a name="updating-manifest-file"></a>매니페스트 파일 업데이트 중

코드 구성 요소 속성을 정의 하는 `ControlManifest.xml` 파일이 `ControlManifest.Input.xml` 파일로 바뀝니다. 두 파일 간에 스키마를 변경 하는 경우는 거의 없습니다.

하지만 몇 가지 중요 한 의미 체계가 변경 되었습니다.

1. 이제 `code` 리소스 항목이 코드 구성 요소의 미리 컴파일된 소스 파일을 가리켜야 합니다. 파일 이름은 기본적으로 index로 설정 됩니다 **.**

   예를 들어 구성 요소 소스가 `MyControl.ts` 이라는 파일에 구현 된 경우 `ControlManifest.Input.xml`의 `code` 항목이 해당 파일을 가리켜야 합니다. 또한 `code` 파일은 유효한 TypeScript 파일 이어야 합니다. 이는 `code` 항목에서 컴파일된 JS 출력 파일을 지정 하는 레거시 매니페스트 파일과 대조 됩니다.
2. @No__t_1 또는 `css` 같은 리소스 요소의 `path` 특성은 이제 디스크에 있는 파일의 로컬 경로를 참조 합니다. 예:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

위의 `path` 특성은 `YourControlName.css` 파일이 `ControlManifest.Input.xml` 디스크에 있는 현재 디렉터리를 기준으로 `css` 하위 폴더에 있음을 나타냅니다.

다음과 같이 ControlManifest. Input .xml 파일을 업데이트 합니다.

1. @No__t_1의 `code` 항목을 코드 구성 요소의 미리 컴파일된 소스 파일 (일반적으로 node.js)로 편집 합니다.
2. 디스크에 있는 파일의 상대 경로를 정확 하 게 참조 하도록 리소스의 모든 경로를 편집 합니다.

## <a name="updating-the-project-files"></a>프로젝트 파일 업데이트

이전 버전의 도구를 사용 하 여 구성 요소를 만들고 최신 기능을 활용 하려는 경우 다음과 같이 프로젝트 파일을 업데이트 해야 합니다.

1. 최신 모듈을 사용 하도록 기존 프로젝트를 업데이트 합니다.
 
   - PowerApps 구성 요소 프레임 워크 프로젝트 폴더 내에 있는 `pcfproj`의 버전 태그를 다음과 같이 업데이트 합니다.

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - 다음과 같이 솔루션 프로젝트 폴더 내에 있는 `cdsproj`의 버전 태그를 업데이트 합니다.

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > 위의 변경 내용을 적용 한 후 `msbuild /t:restore` 명령을 실행 하 여 프로젝트를 올바른 버전으로 업데이트 합니다.


   - PowerApps 구성 요소 프레임 워크 프로젝트 폴더 내에 있는 `package.json` 파일의 버전 태그를 업데이트 합니다.

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
     > [!NOTE]
     > 위의 변경 내용을 적용 한 후 `npm update` 명령을 실행 하 여 프로젝트를 올바른 버전으로 업데이트 합니다.

2. 이전에 인증 프로필을 만든 경우 다시 만들어야 합니다. 이는 공용이 아닌 클라우드를 지원 하기 위해 새 속성이 프로필에 추가 되었기 때문입니다. 이렇게 하려면 다음을 수행 합니다.
 
    - 명령 `pac auth clear`를 실행 합니다.
    - 명령 `pac auth create --url <your org url>`를 실행 합니다.

## <a name="updating-your-project-with-the-latest-node-modules"></a>최신 노드 모듈을 사용 하 여 프로젝트 업데이트

최신 CLI 기능을 활용 하려면 레거시 프로젝트에 최신 npm 모듈을 검색 해야 합니다. 이전에 다운로드 한 노드 모듈을 업데이트 하려면 개발자 명령 프롬프트에서 프로젝트 디렉터리로 이동 하 여 명령 `npm update`를 실행 합니다. 

## <a name="using-es6-module-syntax"></a>ES6 module 구문 사용

빌드 도구는 표준 ES6 모듈 형식을 사용 하 여 구성 요소 원본을 내보낼 것으로 간주 합니다. 레거시 구성 요소는 일반적으로 내부 모듈 (네임 스페이스 라고도 함)로 내보내집니다. 새 빌드 도구와 맞추려면 구성 요소 원본 파일을 아래와 같이 수정 해야 합니다.

1. 코드 구성 요소 (예: .ts)를 구현 하는 소스 파일을 엽니다.
2. 모듈 선언을 제거 하 여 표준 ES6 export 구문을 사용 합니다.

     하기 전에
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    했으면
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>생성 된 매니페스트 입력 파일 사용

레거시 프로젝트는 일반적으로 `private_typing` 하위 폴더 아래에 있는 `inputsOutputs.d.ts` 입력 파일을 수동으로 만들고 편집 해야 합니다. PowerApps CLI 도구는 이제 빌드할 때이 파일을 자동으로 생성 합니다. 

코드 생성을 사용 하면 구성 요소 소스 코드에서 사용 되는 `type` 정의가 구성 요소 매니페스트 파일에 정의 된 `types`와 동기화 상태를 유지 합니다.

입력 하는 파일의 이름이 `ManifestTypes.d.ts`로 바뀌고 이제 `generated` 라는 하위 폴더로 생성 됩니다. 또한 `InputsOutputs.IInputBag` 및 `InputsOutputs.IOutputBag` 형식은 각각 `IInputs` 및 `IOutputs`로 이름이 변경 됩니다.

새 입력 파일을 사용 하려면 다음을 수행 합니다.

1. 구성 요소 소스 파일의 맨 위에 다음 줄을 추가 하 여 새 `ManifestTypes.d.ts` 파일을 가져옵니다.

    `./generated/ManifestTypes`에서 {IInputs, Iinputs}를 가져옵니다.
2. IInputBag의 모든 참조 이름을 **iinputs**으로 바꿉니다 **.**
3. Inputsoutputs의 모든 참조 이름 바꾸기 **. IOutputBag** 을 **ioutputs**로 바꿉니다.
4. @No__t_1 명령을 사용 하 여 새 **ManifestTypes** 파일을 생성 하는 프로젝트를 빌드합니다.

## <a name="troubleshooting-and-workarounds"></a>문제 해결 및 해결 방법

1. Pcf 스크립트를 사용 하는 방법에 대 한 1ES 알림이 표시 되는 경우 이러한 스크립트는 코드 구성 요소를 작성 하는 데만 사용 되지만 결과 구성 요소에서 번들로 또는 사용 되지 않습니다.  
2. 이전에 0.1.817.1 이전 버전의 도구를 사용 하 여 코드 구성 요소를 만들고 최신 빌드 및 디버그 모듈을 사용 하 고 있는지 확인 하려면 다음과 같이 package. json을 업데이트 합니다.
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. 사용자는 권한 부여 문제에 대 한 빌드가 실패할 때 `Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>` 오류를 가져옵니다. 이에 대 한 해결 방법은 다음과 같습니다.

   - **%Appdata%\nuget**에서 NuGet .config 파일을 엽니다. 사용자가 오류를 가져오는 피드가이 파일에 있어야 합니다. 
   - NuGet 파일에서 피드를 제거 하거나 PAT 토큰을 생성 하 여 Nuget .Config 파일에 추가 합니다. 예:

     ```XML
     <?xml version="1.0" encoding="utf-8"?>  
     <configuration>  
     <packageSources>  
         <add key="CRMSharedFeed" value="https://dynamicscrm.pkgs.visualstudio.com/_packaging/CRMSharedFeed/nuget/v3/index.json" />  
      </packageSources>  
     <packageSourceCredentials>  
      <CRMSharedFeed>  
      <add key="Username" value="anything" />  
      <add key="Password" value="User PAT" />  
    </CRMSharedFeed>  
     </packageSourceCredentials>  
   </configuration>
     ```

### <a name="see-also"></a>참고 항목

[PowerApps 구성 요소 프레임 워크의 제한 사항](limitations.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
