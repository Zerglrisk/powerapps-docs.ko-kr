Package Deployer 도구는 [NuGet 패키지](https://go.microsoft.com/fwlink/?linkid=859205)로 사용할 수 있습니다. Package Deployer를 사용하려면 다운로드 후 **nuget.exe**를 사용하여 로컬 컴퓨터에 압축을 풀어야 합니다.<br/><br/>

<https://www.nuget.org/downloads>에서 **nuget.exe**를 다운로드하여 컴퓨터의 예컨대 **d:\\**에 저장합니다. 그런 다음 명령 프롬프트에서 다음 명령을 실행하여 컴퓨터의 폴더, 예컨대 **PD**에 패키지 내용을 추출합니다.<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Package Deployer 도구를 추출한 후에는 `[ExtractedLocation]\tools` 폴더로 이동하여 **PackageDeployer.exe** 파일을 찾습니다. 
