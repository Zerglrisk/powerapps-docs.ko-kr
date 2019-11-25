---
title: 포털에서 Azure Storage 사용 | MicrosoftDocs
description: 포털에서 Azure Storage를 사용하여 Azure의 보다 큰 파일 저장소 기능을 활용할 수 있는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759915"
---
# <a name="enable-azure-storage"></a>Azure Storage 활성화

포털에 Azure Storage를 통합하면 Azure의 더 우수한 파일 저장소 기능을 활용할 수 있어 기본 파일 첨부와 같은 인터페이스를 사용하여 동일한 사용자 환경을 제공합니다. 이 기능은 웹 파일, 엔터티 양식 및 웹 양식에서 지원됩니다.

배포 모델로 **리소스 관리자**를 사용하여 저장소 계정을 만들어야 합니다. [!include[More information](../../includes/proc-more-information.md)] [Azure Storage 계정 만들기](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

저장소 계정이 실행되면 포털은 저장소 계정을 찾는 방법을 응용 프로그램에 알려 주는 특정 글로벌 설정을 요구합니다. 포털 관리 앱에서 **설정** > **새로 만들기**로 이동하여 **FileStorage/CloudStorageAccount**라는 새 설정을 추가합니다.

> [!NOTE]
> 최대 파일 업로드 크기는 125MB입니다.

파일 저장소/클라우드 저장소 계정의 값을 찾으려면 [!include[Azure portal](../../includes/pn-azure-portal.md)]에서 연결 문자열을 얻어야 합니다.

1. [!include[Azure portal](../../includes/pn-azure-portal.md)]에 로그인합니다.

2. 본인의 저장소 계정으로 이동합니다.

3. **액세스 키**를 선택합니다.

    ![Azure Portal에서 연결 문자열의 값 찾기](media/key-azure-storage.png "Azure Portal에서 연결 문자열의 값 찾기")

4. 결과 패널에서 **연결 문자열**이라는 필드를 찾습니다. 값을 복사해야 하는 필드 옆에 있는 **복사** 아이콘을 선택한 다음 해당 값을 새 설정에 붙여넣습니다.

    ![기본 연결 문자열 값](media/primary-connection-string-azure-storage.png "기본 연결 문자열 값")

    ![클라우드 저장소 계정의 포털 설정](media/portal-site-setting-cloud-storage-account.png "클라우드 저장소 계정의 포털 설정")

## <a name="specify-the-storage-container"></a>저장소 컨테이너 지정

저장소 계정에 Azure Blob 컨테이너가 없는 경우 [!include[Azure portal](../../includes/pn-azure-portal.md)]을 사용하여 추가해야 합니다.

[포털 관리 앱](configure/configure-portal.md)에서 **설정** > **새로 만들기**로 이동하여 컨테이너 이름을 값으로 사용하여 **FileStorage/CloudStorageContainerName**이라는 새 설정을 추가합니다.

![클라우드 저장소 컨테이너의 포털 설정](media/portal-site-setting-cloud-storage-container.png "클라우드 저장소 컨테이너의 포털 설정")

## <a name="add-cors-rule"></a>CORS 규칙 추가

또한 Azure Storage 계정에서 원본 간 리소스 공유(CORS) 규칙을 추가해야 하며 그렇지 않으면 클라우드 아이콘이 아닌 일반 첨부 아이콘이 표시됩니다.

- **허용되는 원본**: 도메인을 지정합니다. 예를 들면 contoso.crm.dynamics.com입니다.
- **허용되는 동사:** GET, PUT, DELETE, HEAD, POST
- **허용되는 헤더**: 원본 도메인이 CORS 요청에 지정할 수 있는 요청 헤더를 지정합니다. 예를 들어 x-ms-meta-data\*, x-ms-meta-target\*입니다. 
- **노출되는 헤더**: CORS 요청에 응답하여 전송되고 브라우저에서 요청 발급자에게 노출되는 응답 헤더를 지정합니다. 예를 들어 x-ms-meta-\*입니다.
- **최대 기간(초)**: 브라우저에서 사전 OPTIONS 요청을 캐시해야 하는 최대 시간을 지정합니다. 예를 들면 200입니다.
 
[!include[More information:](../../includes/proc-more-information.md)] [Azure 저장소 서비스를 위한 CORS 지원](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

## <a name="add-site-settings"></a>사이트 설정 추가

**포털** > **사이트 설정**에서 다음 사이트 설정을 추가합니다. [!include[More information:](../../includes/proc-more-information.md)] [포털 사이트 설정 관리](configure/configure-site-settings.md#manage-portal-site-settings).

|이름|값|
|-----|-----|
|WebFiles/CloudStorageAccount|FileStorage/CloudStorageAccount 설정에 대해 제공된 것과 동일한 연결 문자열을 제공합니다.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

이제 포털에서 하위 파일을 작성하고 Azure Blob 주소 URL의 정규화된 이름(컨테이너 포함)을 멘션할 수 있습니다. 이렇게 설정하면 포털이 파일을 Azure Storage에 업로드 및 Azure Storage에서 다운로드를 시작할 준비가 됩니다. 그러나, 그것을 사용하기 위해 [Azure Storage에 첨부 파일을 업로드할 수 있도록 웹 리소스를 추가](add-web-resource.md)하고 [엔터티 양식](configure-notes.md#notes-configuration-for-entity-forms) 또는 [웹 양식](configure-notes.md#notes-configuration-for-web-forms)을 구성할 때까지는 이 기능을 완전히 활용할 수 없습니다.

### <a name="see-also"></a>참조

[웹 리소스 추가](add-web-resource.md)

[메모 구성](configure-notes.md)
