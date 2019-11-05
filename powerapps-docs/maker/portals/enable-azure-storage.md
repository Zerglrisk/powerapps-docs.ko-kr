---
title: 포털에 Azure storage 사용 | MicrosoftDocs
description: Azure storage에서 포털을 사용 하도록 설정 하 여 Azure의 더 큰 파일 저장소 기능을 활용 하는 지침을 제공 합니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542552"
---
# <a name="enable-azure-storage"></a>Azure Storage 사용

포털에 대 한 Azure Storage 통합을 사용 하면 동일한 인터페이스를 사용 하 고 기본 파일 첨부 파일과 동일한 사용자 환경을 제공 하는 Azure의 더 큰 파일 저장소 기능을 활용할 수 있습니다. 이 기능은 웹 파일, 엔터티 양식 및 web forms에 대해 지원 됩니다.

**리소스 관리자** 를 사용 하 여 배포 모델로 저장소 계정을 만들어야 합니다. [!include[More information](../../includes/proc-more-information.md)] [Azure storage 계정을 만듭니다](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

저장소 계정이 실행 된 후에는 응용 프로그램에 저장소 계정을 찾는 방법을 알려 주는 특정 전역 설정이 포털에 필요 합니다. 포털 관리 앱에서 **설정** > **새로 만들기**로 이동 하 고 **FileStorage/cloudstorageaccount**라는 새 설정을 추가 합니다.

> [!NOTE]
> 최대 파일 업로드 크기는 125 MB입니다.

FileStorage/CloudStorageAccount에 대 한 값을 찾으려면 [!include[Azure portal](../../includes/pn-azure-portal.md)]에서 연결 문자열을 가져와야 합니다.

1. [!include[Azure portal](../../includes/pn-azure-portal.md)]에 로그인 합니다.

2. 저장소 계정으로 이동 합니다.

3. **액세스 키**를 선택 합니다.

    ![Azure Portal에서 연결 문자열의 값을 찾습니다.](media/key-azure-storage.png "Azure Portal에서 연결 문자열의 값을 찾습니다.")

4. 결과 창에서 **연결 문자열**이라는 레이블이 지정 된 필드를 찾습니다. 값을 복사 해야 하는 필드 옆에 있는 **복사** 아이콘을 선택 하 고 해당 값을 새 설정에 붙여넣습니다.

    ![기본 연결 문자열 값](media/primary-connection-string-azure-storage.png "기본 연결 문자열 값")

    ![클라우드 저장소 계정에 대 한 포털 설정](media/portal-site-setting-cloud-storage-account.png "클라우드 저장소 계정에 대 한 포털 설정")

## <a name="specify-the-storage-container"></a>저장소 컨테이너 지정

저장소 계정에 Azure Blob 컨테이너가 아직 없는 경우 [!include[Azure portal](../../includes/pn-azure-portal.md)]를 사용 하 여 추가 해야 합니다.

[포털 관리 앱](configure/configure-portal.md)에서 **설정** > **새로 만들기**로 이동 하 고 컨테이너의 이름을 값으로 사용 하 여 **FileStorage/CloudStorageContainerName**라는 새 설정을 추가 합니다.

![클라우드 저장소 컨테이너에 대 한 포털 설정](media/portal-site-setting-cloud-storage-container.png "클라우드 저장소 컨테이너에 대 한 포털 설정")

## <a name="add-cors-rule"></a>CORS 규칙 추가

다음과 같이 Azure Storage 계정에 CORS (크로스-원본 자원 공유) 규칙을 추가 해야 합니다. 그렇지 않으면 클라우드 아이콘이 아닌 일반 첨부 파일 아이콘이 표시 됩니다.

- **허용 된 원본**: 도메인을 지정 합니다. 예를 들면 contoso.crm.dynamics.com입니다.
- **허용 되는 동사**: GET, PUT, DELETE, HEAD, POST
- **허용 되는 헤더**: 원본 도메인이 CORS 요청에서 지정할 수 있는 요청 헤더를 지정 합니다. 예를 들면, x-m a s-메타 데이터\*, x m a 메타 대상\*입니다. 
- **노출 된 헤더**: CORS 요청에 대 한 응답으로 보낼 수 있고 브라우저에서 요청 발급자에 게 노출 될 수 있는 응답 헤더를 지정 합니다. 예를 들면 x-m a s-meta\*입니다.
- **최대 기간 (초)** : 브라우저가 실행 전 옵션 요청을 캐시 해야 하는 최대 시간을 지정 합니다. 예를 들면 200입니다.
 
[Azure Storage 서비스에 대 한 CORS 지원](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services) [!include[More information:](../../includes/proc-more-information.md)]

## <a name="add-site-settings"></a>사이트 설정 추가

**포털** > **사이트 설정**에서 다음 사이트 설정을 추가 합니다. [포털 사이트 설정 관리](configure/configure-site-settings.md#manage-portal-site-settings)를 [!include[More information:](../../includes/proc-more-information.md)] 합니다.

|이름|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|FileStorage/CloudStorageAccount 설정에 대해 제공 된 것과 동일한 연결 문자열을 제공 합니다.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

이제 포털에서 자식 파일을 만들고 Azure Blob 주소 URL에서 컨테이너와 함께 정규화 된 이름을 언급할 수 있습니다. 이러한 설정을 사용 하 여 포털에서 파일 업로드 및 Azure Storage에서 파일 다운로드를 시작할 준비가 되었습니다. 그러나 [Azure Storage에 첨부 파일을 업로드할 수 있도록 웹 리소스를 추가](add-web-resource.md)하 고이를 사용 하도록 [엔터티 양식](configure-notes.md#notes-configuration-for-entity-forms) 또는 [web forms](configure-notes.md#notes-configuration-for-web-forms) 를 구성할 때까지이 기능을 완전히 활용할 수 없습니다.

### <a name="see-also"></a>참고 항목

[웹 리소스 추가](add-web-resource.md)

[노트 구성](configure-notes.md)
