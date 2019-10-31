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
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
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
Azure Data Lake Storage Gen2 계정으로 Power BI를 구성하기 전에 저장소 계정을 만들고 구성해야 합니다. Power Platform 데이터 흐름의 요구 사항은 다음과 같습니다.
1.  저장소 계정은 PowerApps 테넌트와 동일한 Azure Active Directory 테넌트에서 만들어야 합니다.
2.  저장소 계정은 사용하려는 PowerApps 환경과 동일한 지역에서 생성하는 것이 좋습니다. PowerApps 환경의 위치를 확인하려면 환경 관리자에게 문의하십시오.
3.  저장소 계정에는 계층적 네임스페이스 기능이 활성화되어 있어야 합니다.
4.  저장소 계정에 대한 담당자 역할이 부여되어야 합니다.

다음 섹션에서는 Azure Data Lake Storage Gen2 계정 구성에 필요한 단계를 안내합니다.

## <a name="create-the-storage-account"></a>저장소 계정 만들기
[Azure Data Lake Storage Gen2 저장소 계정 만들기](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)의 단계를 따르십시오.
1.  Power BI 테넌트와 동일한 위치를 선택하고 저장소를 StorageV2(범용 v2)로 설정하십시오.
2.  계층적 네임스페이스 기능을 활성화해야 합니다. 
3.  복제 설정을 RA-GRS(읽기 액세스 지역 중복 저장소)로 설정하는 것이 좋습니다.



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>Athena 서비스에 대한 원본 간 리소스 공유(CORS) 규칙 생성

> [!NOTE]
> Power Platform 데이터 흐름은 Athena 서비스를 활용하여 데이터 레이크를 PowerApps 환경에 연결합니다. 이 섹션에서는 데이터 흐름 사용을 위해 구성할 수 있도록 Athena 서비스에 저장소 계정에 대한 역할을 부여해야 합니다.

다음으로, Athena 서비스가 웹 브라우저 및 PowerApps 포털을 통해 저장소 계정에 액세스할 수 있도록 해야 합니다. 웹 브라우저는 웹 페이지가 다른 도메인의 API를 호출하는 것을 방지하는 [동일한 원본 정책](http://www.w3.org/Security/wiki/Same_Origin_Policy)이라는 보안 제한을 구현합니다. CORS는 한 도메인(원본 도메인)이 다른 도메인의 API를 호출할 수 있도록 허용하는 안전한 방법을 제공합니다. CORS에 대한 자세한 내용은 [CORS 사양](http://www.w3.org/TR/cors/)을 참조하십시오.

Azure Portal의 설정 페이지에서 방금 만든 저장소 계정의 단계를 따릅니다. CORS 메뉴 항목에서 Blob 서비스 섹션을 선택하고 다음 세부 사항을 입력하십시오. 

|설정  |Value  |
|---------|---------|
|허용된 원본   | https://athena-ui-prod.trafficmanager.net     |
|허용된 메서드   |  DELETE, GET, HEAD, MERGE, POST, OPTIONS, PUT, PATCH   |
|허용된 헤더   | *    |
|노출된 헤더   | *    |
|최대 연령 |   *  |


다음 이미지는 Athena 서비스에 대해 구성된 CORS 규칙을 보여줍니다.

![CORS 규칙](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>PowerApps에 Azure Data Lake Storage Gen2 연결
Azure Portal에서 Azure Data Lake Storage Gen2 계정을 설정했으면 이를 특정 데이터 흐름 또는 PowerApps 환경에 연결할 수 있습니다. 레이크를 환경에 연결하면 환경의 다른 제조업체와 관리자가 조직의 레이크에 데이터를 저장하는 데이터 흐름을 만들 수 있습니다. 

Azure Data Lake Storage Gen2 계정을 데이터 흐름에 연결하려면 다음 단계를 따르십시오.
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하여 어떤 환경에 있는지 확인하십시오. 환경 전환기는 헤더의 오른쪽에 있습니다. 
2. 왼쪽 탐색 창에서 **데이터** 옆에 있는 아래쪽 화살표를 선택하십시오.

   ![PowerApps 제조업체 포털 데이터 탭](media/powerapps-portal-data.png)

3. 나타나는 목록에서 **데이터 흐름**을 선택한 다음 명령 모음에서 **새 데이터 흐름**을 선택합니다.

   ![새 데이터 흐름 만들기](media/new-dataflow.png) 

4. 원하는 분석 엔터티를 선택합니다. 이러한 엔터티는 조직의 Azure Data Lake Store Gen2 계정에 저장하려는 데이터를 나타냅니다. 

   ![분석 엔터티 선택](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>데이터 흐름 저장소에 사용할 저장소 계정을 선택하십시오.
저장소 계정이 아직 환경과 연결되지 않은 경우 **데이터 레이크에 연결** 대화 상자가 나타납니다. 로그인하고 이전 단계에서 생성한 데이터 레이크를 찾아야 합니다. 이 예에서는 데이터 레이크가 환경과 연결되어 있지 않으므로 추가하기 위해 프롬프트가 표시됩니다. 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
