---
title: Dynamics 365 포털 구성 마이그레이션 | MicrosoftDocs
description: Dynamics 365 포털 구성을 마이그레이션하는 방법을 알아보십시오.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="migrate-dynamics-365-portals-configuration"></a>Dynamics 365 포털 구성 마이그레이션

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

포탈 개발에는 포탈 최종 사용자에게 원하는 환경을 구현하기 위한 몇 가지 구성과 사용자 지정가 포함됩니다.

Dynamics 365 포털 인스턴스의 개발이나 구성을 완료한 후 개발에서 테스트 또는 프로덕션 환경으로 최신 Dynamics 365 포털 구성 데이터를 마이그레이션할 수 있습니다. 마이그레이션은 소스 Dynamics 365 인스턴스에서 기존 구성을 내보낸 다음 대상 Dynamics 365 인스턴스로 가져오는 것을 포함합니다.

구성 데이터를 내보내려면 구성 마이그레이션 도구와 포털별 구성 스키마 파일을 사용해야 합니다. 이 도구에 대한 자세한 내용은 [구성 데이터 관리](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-configuration-data)를 참조하십시오.

> [!NOTE]
> - 최신 버전의 구성 마이그레이션 도구를 사용하는 것이 좋습니다. 구성 마이그레이션 도구는 NuGet에서 다운로드할 수 있습니다. 도구 다운로드에 대한 자세한 내용 : [NuGet에서 도구 다운로드](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/download-tools-nuget).
> - 구성 마이그레이션을 위한 스키마 파일에서 지원하는 Dynamics 365 포털의 최소 솔루션 버전은 8.4.0.275입니다. 그러나 최신 솔루션 버전을 사용하는 것이 좋습니다.

스키마 파일은 다음 포털 유형에 사용할 수 있습니다.
- [커뮤니티 포털](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [고객 셀프 서비스 포털](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [파트너 포털](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [직원 셀프 서비스 포털](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [사용자 지정 포털](https://go.microsoft.com/fwlink/p/?linkid=2019804)

기본 스키마 파일에는 포털 엔터티, 관계 및 각 엔터티에 대한 고유성 정의에 대한 정보가 포함되어 있습니다. 추가 정보: [포털 구성 데이터 내보내기](#export-portal-configuration-data)

구성 데이터를 내보낸 후에는 대상 환경으로 가져와야 합니다. 추가 정보: [포털 구성 데이터 가져오기](#import-portal-configuration-data)

> [!NOTE]
> 스키마 파일은 처음부터 스키마를 빌드하는 데 필요한 노력을 줄이기 위해 제공됩니다. 도구에서 제공하는 표준 방법을 사용하여 구현에 맞게 스키마를 조정할 수 있습니다. 스키마 파일을 구성 마이그레이션 도구에 로드하고 엔터티, 특성 등을 추가, 제거 및 수정하도록 변경할 수 있습니다.

## <a name="export-portal-configuration-data"></a>포털 구성 데이터 내보내기

포털별 구성 스키마 파일을 사용하여 소스 시스템에서 포털 구성 데이터를 내보낼 수 있습니다.

1.  구성 마이그레이션 도구를 다운로드하고 원하는 폴더로 압축을 풉니다.

2.  포털 유형에 대해 위에 제공된 링크를 사용하여 포털 구성 스키마 파일을 다운로드합니다.

3.  `<your_folder>\Tools\ConfigurationMigration` 폴더에서 **DataMigrationUtility.exe** 파일을 두 번 클릭하여 구성 마이그레이션 도구를 실행하고 주 화면에서 **데이터 내보내기**를 선택한 다음 **계속**을 선택합니다.
    
    > [!div class=mx-imgBorder]
    > ![구성 데이터 내보내기](../media/export-config-data.png "구성 데이터 내보내기")

4.  **로그인** 화면에서 인증 정보를 제공하여 데이터를 내보낼 Dynamics 365 인스턴스에 연결합니다. Dynamics 365 인스턴스에 여러 조직이 있어서 데이터를 가져올 조직을 선택하려면 **사용 가능한 조직 목록 표시** 확인란을 선택한 다음 **로그인**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![인증 정보를 제공하여 데이터를 내보낼 Dynamics 365 인스턴스에 연결](../media/export-config-login.png "인증 정보를 제공하여 데이터를 내보낼 Dynamics 365 인스턴스에 연결")

5.  여러 조직이 있어서 이전 단계에서 **사용 가능한 조직 목록 표시** 확인란을 선택한 경우 다음 화면에서 연결할 조직을 선택할 수 있습니다. 연결할 Dynamics 365 조직을 선택합니다. 

    > [!NOTE]
    > 여러 조직이 없는 경우 이 화면이 표시되지 않습니다.

6.  **스키마 파일**에서 데이터 내보내기에 사용할 포털별 구성 스키마 파일을 찾아 선택합니다.

7.  **데이터 파일에 저장**에서 내보낼 데이터 파일의 이름과 위치를 지정합니다.

    > [!div class=mx-imgBorder]
    > ![스키마 및 대상 파일 지정](../media/export-config-file-name.png "스키마 및 대상 파일 지정")

8.  **데이터 내보내기**를 선택합니다. 내보내기가 완료되면 내보내기 진행 상태와 내보낸 파일의 위치가 화면 아래쪽에 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![구성 데이터 내보내기 진행률](../media/export-config-status.png "구성 데이터 내보내기 진행률")

    > [!IMPORTANT]
    > 구성 마이그레이션 도구는 엔터티의 레코드 필터링을 지원하지 않습니다. 기본적으로 선택한 엔터티의 모든 레코드를 내보냅니다. 따라서 두 개 이상의 웹 사이트 레코드를 만든 경우 모든 웹 사이트 레코드를 내보냅니다.

9.  **끝내기**를 선택하여 도구를 닫습니다.

## <a name="import-portal-configuration-data"></a>포털 구성 데이터 가져오기

1.  구성 마이그레이션 도구를 실행하고 기본 화면에서 **데이터 가져오기**를 선택한 다음 **계속**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![구성 데이터 가져오기](../media/import-config-data.png "구성 데이터 가져오기")

2.  **로그인** 화면에서 인증 정보를 제공하여 데이터를 내보낼 Dynamics 365 인스턴스에 연결합니다. Dynamics 365 인스턴스에 여러 조직이 있어서 데이터를 가져올 조직을 선택하려면 **사용 가능한 조직 목록 표시** 확인란을 선택한 다음 **로그인**을 선택합니다.

3.  여러 조직이 있어서 이전 단계에서 **사용 가능한 조직 목록 표시** 확인란을 선택한 경우 다음 화면에서 연결할 조직을 선택할 수 있습니다. 연결할 Dynamics 365 조직을 선택합니다. 

    > [!NOTE]
    > - 여러 조직이 없는 경우 이 화면이 표시되지 않습니다.
    > - 구성을 가져올 계획인 조직에 대해 포털 솔루션이 이미 설치되어 있는지 확인합니다.

4.  다음 화면을 사용하면 가져올 데이터 파일(.zip)을 제공할 수 있습니다. 데이터 파일을 찾아 선택한 후 **데이터 가져오기**를 선택합니다. 

    > [!div class=mx-imgBorder]
    > ![구성 데이터 가져오기 진행률](../media/import-config-status.png "구성 데이터 가져오기 진행률")

5.  다음 화면에 레코드의 가져오기 상태가 표시됩니다. 데이터 가져오기는 여러 단계로 수행되는데, 종속 데이터가 대기하고 있는 동안 먼저 기초 데이터를 가져온 후 이후 단계에서 종속 데이터를 가져와 데이터 종속성 또는 연결을 처리합니다. 그러면 깔끔하고 일관되게 데이터를 가져올 수 있습니다. 

6.  **끝내기**를 선택하여 도구를 닫습니다. 
