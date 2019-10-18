---
title: 구성 요소 가져오기 | Microsoft Docs
description: 이 항목에서는 코드 구성 요소를 가져오는 방법에 대해 설명 합니다.
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 3042202fd1790d117c2a503bd6e69eaaea15c08a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346811"
---
# <a name="package-a-code-component"></a>코드 구성 요소 패키지

이 항목에서는 Common Data Service에 코드 구성 요소를 가져오는 방법에 대해 설명 합니다. PowerApps CLI를 사용 하 여 코드 구성 요소를 구현한 후 다음 단계는 모든 코드 구성 요소 요소를 솔루션 파일에 번들로 묶고 솔루션 파일을 Common Data Service로 가져와 런타임에 코드 구성 요소를 볼 수 있도록 하는 것입니다.

솔루션 파일을 만들고 가져오려면:

1. @No__t_1 명령을 사용 하 여 새 폴더를 만들고 이름을 **솔루션** 또는 원하는 이름을 선택 합니다. @No__t_0 명령을 사용 하 여 디렉터리로 이동 합니다.

2. @No__t_0 명령을 사용 하 여 새 솔루션 프로젝트를 만듭니다. 솔루션 프로젝트는 Common Data Service로 가져오는 데 사용 되는 솔루션 zip 파일에 코드 구성 요소를 묶는 데 사용 됩니다.

   > [!NOTE]
   > @No__t_0 및 `publisher-prefix` 값은 사용자 환경에서 고유 해야 합니다.
 
3. 새 솔루션 프로젝트를 만든 후에는 **솔루션** 폴더에서 만들어진 샘플 구성 요소가 있는 위치를 참조 합니다. 아래에 표시 된 명령을 사용 하 여 참조를 추가할 수 있습니다. 이 참조는 빌드 중에 추가 해야 하는 코드 구성 요소에 대 한 솔루션 프로젝트를 알려 줍니다. 단일 솔루션 프로젝트의 여러 구성 요소에 대 한 참조를 추가할 수 있습니다.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. 솔루션 프로젝트에서 zip 파일을 생성 하려면 솔루션 프로젝트 디렉터리로 이동 하 여 `msbuild /t:build /restore` 명령을 사용 하 여 프로젝트를 빌드합니다. 이 명령은 *MSBuild* 를 사용 하 여 복원의 일부로 *NuGet* 종속성을 풀링 하 여 솔루션 프로젝트를 빌드합니다. 솔루션 프로젝트를 처음 빌드할 때만 `/restore`을 사용 합니다. 그 후의 모든 빌드에 대해 `msbuild` 명령을 실행할 수 있습니다.


    > [!NOTE]
    > - Msbuild 15.9. *가 경로에 없는 경우 VS 2017에 대해 개발자 명령 프롬프트를 열어 `msbuild` 명령을 실행 합니다.
    > - *디버그* 구성에서 솔루션을 빌드하면 관리 되지 않는 솔루션 패키지가 생성 됩니다. 관리 되는 솔루션 패키지는 *릴리스* 구성에서 솔루션을 빌드하여 생성 됩니다. 이러한 설정은 `cdsproj` 파일에 `SolutionPackageType` 속성을 지정 하 여 재정의할 수 있습니다.
    > - Msbuild 구성을 `Release` 설정 하 여 프로덕션 빌드를 실행할 수 있습니다. 예: `msbuild /p:configuration=Release`
    > - 솔루션에서 `msbuild` 명령을 실행할 때 *모호한 프로젝트 이름* 이라는 오류가 발생 하는 경우 솔루션 이름과 프로젝트 이름이 동일 하지 않은지 확인 합니다.

4. 생성 된 솔루션 파일은 빌드에 성공한 후 `\bin\debug\` 폴더 안에 있습니다.
5. 웹 포털을 사용 하 여 [솔루션을 Common Data Service으로](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) 수동으로 가져오거나 PowerApps CLI 명령을 사용 하 여 가져올 조직 및 [배포](#deploying-code-components) 섹션 [에 대 한 인증](#authenticating-to-your-organization) 섹션을 참조 하세요.

## <a name="authenticating-to-your-organization"></a>조직에서 인증

Common Data Service 조직에 인증 한 다음 업데이트 된 구성 요소를 푸시하여 PowerApps CLI에서 직접 코드 구성 요소를 배포할 수 있습니다. 다음 단계를 사용 하 여 인증 프로필을 만들고 Common Data Service에 연결한 후 업데이트 된 구성 요소를 푸시합니다. 
 
1. 다음 명령을 사용 하 여 인증 프로필을 만듭니다. 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. 이전에 인증 프로필을 만든 경우 다음 명령을 사용 하 여 기존 프로필을 모두 볼 수 있습니다. 

   ```CLI
    pac auth list 
   ```
 
3. 이전에 만든 인증 프로필 사이를 전환 하려면 다음 명령을 사용 합니다. 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. 조직에 대 한 기본 정보를 가져오려면 다음 명령을 사용 합니다. 연결은 기본 인증 프로필을 사용 하 여 수행 됩니다. 

    ```CLI
    pac org who 
    ```
 
5. 특정 인증 프로필을 삭제 하려면 `pac auth delete --index < index of the profile >` 명령을 사용 합니다. 
6. 로컬 컴퓨터에서 모든 인증 프로필을 제거 하려면 `pac auth clear` 명령을 사용 합니다. 로컬 컴퓨터에서 `authprofile.json` 파일 및 토큰 캐시 파일을 완전히 삭제 하므로이 작업은 되돌릴 수 없습니다. 

## <a name="deploying-code-components"></a>코드 구성 요소 배포 

인증 프로필을 성공적으로 만든 후에는 모든 최신 변경 내용으로 코드 구성 요소를 Common Data Service 인스턴스로 푸시할 수 있습니다. @No__t_0 기능은 코드 구성 요소 버전 관리 요구 사항을 우회 하 고 코드 구성 요소를 가져오기 위해 솔루션 (cdsproj)을 빌드할 필요가 없기 때문에 내부 개발자 주기 개발 속도를 향상 시킵니다. @No__t_0 기능을 사용 하려면 다음을 수행 합니다.

1. 유효한 인증 프로필을 만들었는지 확인 합니다.
2. 코드 구성 요소 프로젝트가 생성 된 루트 디렉터리로 이동 합니다.
3. @No__t_0 명령을 실행 합니다.

   > [!NOTE]
   > @No__t_0 명령과 함께 사용 하는 게시자 접두사는 구성 요소가 포함 될 솔루션의 게시자 접두사와 일치 해야 합니다.

## <a name="how-to-remove-components-from-a-solution"></a>솔루션에서 구성 요소를 제거 하는 방법

솔루션 파일에서 코드 구성 요소를 제거 하려면 다음을 수행 합니다.

1.  솔루션 프로젝트 디렉터리에서 `cdsproj` 파일을 편집 하 고 해당 구성 요소에 대 한 참조를 제거 합니다. 다음은 구성 요소 참조의 예입니다.

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. 다음 명령을 사용 하 여 다시 빌드 (또는 정리)를 수행 합니다.
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>참고 항목

[모델 기반 앱의 필드 또는 엔터티에 코드 구성 요소 추가](add-custom-controls-to-a-field-or-entity.md)<br/>
[캔버스 앱에 구성 요소 추가](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
