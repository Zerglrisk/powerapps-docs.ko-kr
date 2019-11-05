---
title: 포털 구성 마이그레이션 | MicrosoftDocs
description: 포털 구성을 마이그레이션하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0aa057594b500c7019a4d645c70cafcfff183608
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543050"
---
# <a name="migrate-portal-configuration"></a>포털 구성 마이그레이션

포털 개발에는 포털 최종 사용자에 게 원하는 환경을 구현 하기 위한 여러 구성 및 사용자 지정이 포함 됩니다.

포털 인스턴스의 개발 또는 구성을 완료 한 후에는 개발에서 테스트 또는 프로덕션 환경으로 최신 포털 구성을 마이그레이션할 수 있습니다. 마이그레이션은 원본 Common Data Service 환경에서 기존 구성을 내보낸 다음 대상 Common Data Service 환경으로 가져오는 작업을 포함 합니다.

구성 데이터를 내보내려면 구성 마이그레이션 도구 및 포털 관련 구성 스키마 파일을 사용 해야 합니다. 이 도구에 대 한 자세한 내용은 [구성 데이터 관리](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data)를 참조 하세요.

> [!NOTE]
> - 최신 버전의 구성 마이그레이션 도구를 사용 하는 것이 좋습니다. 구성 마이그레이션 도구는 NuGet에서 다운로드할 수 있습니다. 도구 다운로드에 대 한 추가 정보: [NuGet에서 도구 다운로드](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget)
> - 구성 마이그레이션의 스키마 파일에서 지원 되는 포털의 최소 솔루션 버전은 8.4.0.275입니다. 그러나 최신 솔루션 버전을 사용 하는 것이 좋습니다.

스키마 파일은 다음 포털 유형에 사용할 수 있습니다.
- [커뮤니티 포털](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [고객 셀프 서비스 포털](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [파트너 포털](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [직원 셀프 서비스 포털](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [사용자 지정 포털](https://go.microsoft.com/fwlink/p/?linkid=2019804)

기본 스키마 파일에는 각 엔터티에 대 한 포털 엔터티, 관계 및 고유성 정의에 대 한 정보가 포함 되어 있습니다. 추가 정보: [포털 구성 데이터 내보내기](#export-portal-configuration-data)

구성 데이터를 내보낸 후 대상 환경으로 가져와야 합니다. 추가 정보: [포털 구성 데이터 가져오기](#import-portal-configuration-data)

> [!NOTE]
> 스키마 파일은 스키마를 처음부터 작성 하는 데 필요한 작업을 줄이기 위해 제공 됩니다. 스키마는 도구에서 제공 하는 표준 방법을 사용 하 여 구현에 맞게 조정할 수 있습니다. 스키마 파일은 구성 마이그레이션 도구에서 로드 하 고 엔터티, 특성 등을 추가, 제거 및 수정 하도록 변경할 수 있습니다.

## <a name="export-portal-configuration-data"></a>포털 구성 데이터 내보내기

포털 관련 구성 스키마 파일을 사용 하 여 원본 시스템에서 포털 구성 데이터를 내보낼 수 있습니다.

1.  구성 마이그레이션 도구를 다운로드 하 고 원하는 폴더로 추출 합니다.

2.  포털 형식에 대해 위에서 제공한 링크를 사용 하 여 포털 구성 스키마 파일을 다운로드 합니다.

3.  `<your_folder>\Tools\ConfigurationMigration` 폴더에서 **DataMigrationUtility** 파일을 두 번 클릭 하 여 구성 마이그레이션 도구를 실행 하 고 주 화면에서 **데이터 내보내기** 를 선택한 다음 **계속**을 선택 합니다.
    
    > [!div class=mx-imgBorder]
    > ![구성 데이터 내보내기](../media/export-config-data.png "구성 데이터 내보내기")

4.  **로그인** 화면에서 데이터를 내보낼 위치에서 Common Data Service 환경에 연결 하는 데 필요한 인증 세부 정보를 제공 합니다. Common Data Service 환경에 여러 조직이 데이터를 내보낼 수 있는 경우 **사용 가능한 조직 목록 표시** 확인란을 선택 하 고 **로그인**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![데이터를 내보낼 위치에서 Common Data Service 환경에 연결 하기 위한 인증 세부 정보를 제공 합니다.](../media/export-config-login.png "데이터를 내보낼 위치에서 Common Data Service 환경에 연결 하기 위한 인증 세부 정보를 제공 합니다.")

5.  조직 수가 여러 개인 경우 이전 단계에서 **사용 가능한 조직 목록 표시** 확인란을 선택 하 고 다음 화면에서 연결 하려는 조직을 선택할 수 있습니다. 연결할 Common Data Service 환경을 선택 합니다. 

    > [!NOTE]
    > 조직이 여러 개인 경우에는이 화면이 표시 되지 않습니다.

6.  **스키마 파일**에서 데이터 내보내기에 사용할 포털 특정 구성 스키마 파일을 찾아 선택 합니다.

7.  **데이터 파일에 저장**에서 내보낼 데이터 파일의 이름과 위치를 지정 합니다.

    > [!div class=mx-imgBorder]
    > ![스키마 및 대상 파일 지정](../media/export-config-file-name.png "스키마 및 대상 파일 지정")

8.  **데이터 내보내기**를 선택 합니다. 내보내기가 완료 되 면 화면 아래쪽에 내보내기 진행률 상태와 내보낸 파일 위치가 표시 됩니다.

    > [!div class=mx-imgBorder]
    > ![구성 데이터 내보내기 진행률](../media/export-config-status.png "구성 데이터 내보내기 진행률")

    > [!IMPORTANT]
    > 구성 마이그레이션 도구는 엔터티의 레코드 필터링을 지원 하지 않습니다. 기본적으로 선택한 엔터티의 모든 레코드를 내보냅니다. 따라서 둘 이상의 웹 사이트 레코드를 만든 경우 모든 웹 사이트 레코드를 내보냅니다.

9.  **끝내기** 를 선택 하 여 도구를 닫습니다.

## <a name="import-portal-configuration-data"></a>포털 구성 데이터 가져오기

1.  구성 마이그레이션 도구를 실행 하 고 주 화면에서 **데이터 가져오기** 를 선택한 다음 **계속**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![구성 데이터 가져오기](../media/import-config-data.png "구성 데이터 가져오기")

2.  **로그인** 화면에서 데이터를 내보낼 위치에서 Common Data Service 환경에 연결 하는 데 필요한 인증 세부 정보를 제공 합니다. Common Data Service 환경에 여러 조직이 데이터를 내보낼 수 있는 경우 **사용 가능한 조직 목록 표시** 확인란을 선택 하 고 **로그인**을 선택 합니다.

3.  조직 수가 여러 개인 경우 이전 단계에서 **사용 가능한 조직 목록 표시** 확인란을 선택 하 고 다음 화면에서 연결 하려는 조직을 선택할 수 있습니다. 연결할 Common Data Service 환경을 선택 합니다. 

    > [!NOTE]
    > - 조직이 여러 개인 경우에는이 화면이 표시 되지 않습니다.
    > - 구성을 가져올 조직에 대해 포털 솔루션이 이미 설치 되어 있는지 확인 합니다.

4.  다음 화면에서는 가져올 데이터 파일 (.zip)을 지정 하 라는 메시지를 표시 합니다. 데이터 파일을 찾아 선택한 다음 **데이터 가져오기**를 선택 합니다. 

    > [!div class=mx-imgBorder]
    > ![구성 데이터 가져오기 진행률](../media/import-config-status.png "구성 데이터 가져오기 진행률")

5.  다음 화면은 레코드의 가져오기 상태를 표시 합니다. 데이터 가져오기는 종속 데이터를 큐에 대기 하는 동안 먼저 기초 데이터를 가져오기 위해 여러 패스에서 수행 된 다음 데이터 종속성 또는 링크를 처리 하기 위해 후속 패스에서 종속 데이터를 가져옵니다. 이렇게 하면 데이터를 정리 하 고 일관 되 게 가져올 있습니다. 

6.  **끝내기** 를 선택 하 여 도구를 닫습니다. 
