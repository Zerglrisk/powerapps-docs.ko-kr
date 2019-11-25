---
title: 데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결 | MicrosoftDocs
description: 데이터 흐름 저장소에 Azure Data Lake Storage Gen2를 연결하는 방법 알아보기
ms.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d7957f048613045a64af0caf5696e540dbb8f883
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754790"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

조직의 Azure Data Lake Storage Gen2 계정에 데이터를 저장하도록 데이터 흐름을 구성할 수 있습니다. 이 문서에서는 이를 수행하는 데 필요한 일반적인 단계를 설명하고 그 과정에서 지침과 모범 사례를 제공합니다. 

데이터 레이크에 정의 및 데이터 파일을 저장하도록 데이터 흐름을 구성하면 다음과 같은 이점이 있습니다.
- Azure Data Lake Storage Gen2는 데이터를 위한 확장성이 뛰어난 스토리지 기능을 제공합니다.
- Azure 데이터 서비스의 GitHub 샘플에 설명된 대로 IT 부서의 개발자는 데이터 흐름 데이터 및 정의 파일을 활용하여 Azure 데이터 및 AI(인공 지능) 서비스를 활용할 수 있습니다.
- 조직의 개발자는 데이터 흐름 및 Azure에 대한 개발자 리소스를 사용하여 데이터 흐름 데이터를 내부 응용 프로그램 및 기간 업무 솔루션에 통합할 수 있습니다.

## <a name="requirements"></a>요구 사항
데이터 흐름에 Azure Data Lake Storage Gen2를 사용하려면 다음이 필요합니다.
- PowerApps 환경. 모든 PowerApps 플랜을 통해 Azure Data Lake Storage Gen2가 있는 데이터 흐름을 대상으로 만들 수 있습니다. 환경에서 제조업체로서 권한을 부여받아야 합니다. 
- Azure 구독. Azure Data Lake Storage Gen2를 사용하려면 Azure 구독이 필요합니다.
- 리소스 그룹. 이미 보유한 리소스 그룹을 사용하거나 새로 작성하십시오.
- Azure Storage 계정. 저장소 계정에는 Data Lake Storage Gen2 기능이 활성화되어 있어야 합니다.

> [!TIP]
> Azure 구독이 없는 경우 시작하기 전에 [무료 평가판 계정을 만드십시오](https://azure.microsoft.com/free/).

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Power Platform 데이터 흐름용 Azure Data Lake Storage Gen2 준비
Azure Data Lake Storage Gen2 계정으로 환경을 구성하기 전에 저장소 계정을 만들고 구성해야 합니다. Power Platform 데이터 흐름의 요구 사항은 다음과 같습니다.
1.  저장소 계정은 PowerApps 테넌트와 동일한 Azure Active Directory 테넌트에서 만들어야 합니다.
2.  저장소 계정은 사용하려는 PowerApps 환경과 동일한 지역에서 생성하는 것이 좋습니다. PowerApps 환경의 위치를 확인하려면 환경 관리자에게 문의하십시오.
3.  저장소 계정에는 계층적 네임스페이스 기능이 활성화되어 있어야 합니다.
4.  저장소 계정에 대한 담당자 역할이 부여되어야 합니다.

다음 섹션에서는 Azure Data Lake Storage Gen2 계정 구성에 필요한 단계를 안내합니다.

## <a name="create-the-storage-account"></a>저장소 계정 만들기
[Azure Data Lake Storage Gen2 저장소 계정 만들기](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)의 단계를 따르십시오.
1.  환경과 동일한 지역을 선택하고 저장소를 StorageV2(범용 v2)로 설정하십시오.
2.  계층적 네임스페이스 기능을 활성화해야 합니다. 
3.  복제 설정을 RA-GRS(읽기 액세스 지역 중복 저장소)로 설정하는 것이 좋습니다.

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>PowerApps에 Azure Data Lake Storage Gen2 연결
Azure Portal에서 Azure Data Lake Storage Gen2 계정을 설정했으면 이를 특정 데이터 흐름 또는 PowerApps 환경에 연결할 수 있습니다. 레이크를 환경에 연결하면 환경의 다른 제조업체와 관리자가 조직의 레이크에 데이터를 저장하는 데이터 흐름을 만들 수 있습니다. 

Azure Data Lake Storage Gen2 계정을 데이터 흐름에 연결하려면 다음 단계를 따르십시오.
1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하여 어떤 환경에 있는지 확인하십시오. 환경 전환기는 헤더의 오른쪽에 있습니다. 
2. 왼쪽 탐색 창에서 **데이터** 옆에 있는 아래쪽 화살표를 선택하십시오.

   ![PowerApps 제조업체 포털 데이터 탭](media/powerapps-portal-data.png)

3. 나타나는 목록에서 **데이터 흐름**을 선택한 다음 명령 모음에서 **새 데이터 흐름**을 선택합니다.

   ![새 데이터 흐름 만들기](media/new-dataflow.png) 

4. 원하는 분석 엔터티를 선택합니다. 이러한 엔터티는 조직의 Azure Data Lake Store Gen2 계정에 저장하려는 데이터를 나타냅니다. 

   ![분석 엔터티 선택](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>데이터 흐름 저장소에 사용할 저장소 계정을 선택하십시오.
저장소 계정이 아직 환경과 연결되지 않은 경우 **데이터 레이크에 연결** 대화 상자가 나타납니다. 로그인하고 이전 단계에서 생성한 데이터 레이크를 찾아야 합니다. 이 예에서는 데이터 레이크가 환경과 연결되어 있지 않으므로 추가하기 위해 프롬프트가 표시됩니다. 


1. 저장소 계정을 선택합니다.

    **저장소 계정 선택** 화면이 나타납니다.
    
    ![저장소 계정 선택](media/select-storage-account.png)
    
2. 저장소 계정의 **구독 ID**를 선택합니다.
3. 저장소 계정이 생성된 **리소스 그룹 이름**을 선택합니다.
4. **저장소 계정 이름**을 입력합니다.
5. **저장**을 선택합니다.

이 단계가 성공적으로 완료되면 Azure Data Lake Storage Gen2 계정이 Power Platform 데이터 흐름에 연결되며 데이터 흐름을 계속 만들 수 있습니다.

## <a name="considerations-and-limitations"></a>고려 사항 및 제한 사항
데이터 흐름 저장소 작업 시 명심해야 할 몇 가지 고려 사항과 제한 사항이 있습니다.
- 기본 환경에서는 데이터 흐름 저장소에 대한 Azure Data Lake Storage Gen2 계정 연결이 지원되지 않습니다.
- 데이터 흐름 저장소 위치가 데이터 흐름에 대해 구성되면 변경할 수 없습니다.
- 기본적으로 환경의 모든 구성원은 Power Platform 데이터 흐름 커넥터를 사용하여 데이터 흐름 데이터에 액세스할 수 있습니다. 그러나 데이터 흐름의 담당자만 Azure Data Lake Storage Gen2에서 파일에 직접 액세스할 수 있습니다. 다른 사람이 레이크에서 직접 데이터 흐름 데이터에 액세스할 수 있도록 권한을 부여하려면 데이터 레이크의 **CDM 폴더** 또는 데이터 레이크 자체에서 데이터 흐름에 대한 권한을 부여해야 합니다.
- 데이터 흐름이 삭제되면 레이크의 **CDM 폴더**도 삭제됩니다. 

> [!IMPORTANT]
> 조직의 레이크에서 데이터 흐름으로 생성된 파일을 변경하거나 데이터 흐름의 **CDM 폴더**에 파일을 추가해서는 안 됩니다. 파일을 변경하면 데이터 흐름이 손상되거나 동작이 변경될 수 있으며 지원되지 않습니다. Power Platform 데이터 흐름은 레이크에서 생성된 파일에 대한 읽기 권한만 부여합니다. 다른 사람이나 서비스에 Power Platform 데이터 흐름에서 사용하는 파일 시스템에 대한 권한을 부여한 경우 해당 파일 시스템의 파일 또는 폴더에 대한 읽기 권한만 부여하게 됩니다.

## <a name="frequently-asked-questions"></a>질문과 대답
*이전에 조직의 Azure Data Lake Storage Gen2에 데이터 흐름을 생성했으며 저장소 위치를 변경하고자 하면 어떻게 됩니까?*

   데이터 흐름이 생성된 후 데이터 흐름의 저장소 위치를 변경할 수 없습니다.

*환경의 데이터 흐름 저장소 위치를 언제 변경할 수 있습니까?*

   현재 환경의 데이터 흐름 저장소 위치 변경은 지원되지 않습니다. 

## <a name="next-steps"></a>다음 단계
이 문서는 데이터 흐름 저장소를 위한 Azure Data Lake Storage Gen2 계정 연결 방법에 대한 지침을 제공했습니다. 

데이터 흐름, Common Data Model 및 Azure Data Lake Storage Gen2에 대한 자세한 내용은 다음 문서를 참조하십시오.
- [데이터 흐름을 통한 셀프 서비스 데이터 준비](https://go.microsoft.com/fwlink/?linkid=2099972)
- [PowerApps에서 데이터 흐름 만들기 및 사용](https://go.microsoft.com/fwlink/?linkid=2100076)
- [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Common Data Service에서 엔터티에 데이터 추가](https://go.microsoft.com/fwlink/?linkid=2100075)

Azure Storage에 대한 자세한 내용은 이 문서를 참조하십시오.
- [Azure Storage 보안 가이드](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

Common Data Model에 대한 자세한 내용은 다음 문서를 참조하십시오.
- [Common Data Model - 개요](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model 폴더](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM 모델 파일 정의](https://go.microsoft.com/fwlink/?linkid=2045521)

[PowerApps 커뮤니티](https://go.microsoft.com/fwlink/?linkid=2099971)에서 질문하고 답변할 수 있습니다.
