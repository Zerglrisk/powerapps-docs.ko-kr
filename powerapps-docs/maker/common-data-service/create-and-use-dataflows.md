---
title: PowerApps에서 데이터 흐름 생성 및 사용 | MicrosoftDocs
description: PowerApps에서 데이터 흐름을 생성하고 사용하는 방법을 알아봅니다.
ms.custom: ''
ms.date: 08/05/2019
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
ms.openlocfilehash: 5ad261f668c36e623b35e619e4d573401f3b547a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705806"
---
# <a name="create-and-use-dataflows-in-powerapps"></a>PowerApps에서 데이터 흐름 생성 및 사용
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

PowerApps에서 사용 가능한 고급 데이터 준비를 통해 데이터 흐름이라고 하는 데이터 모음을 만들어 다양한 소스의 비즈니스 데이터와 연결하고 데이터를 정리하고 변환한 다음 Common Data Service 또는 조직의 Azure Data Lake Gen2 저장소 계정에 로드할 수 있습니다.

데이터 흐름은 PowerApps 서비스의 환경에서 생성 및 관리되는 엔터티(엔터티는 테이블과 유사)의 모음입니다. 데이터 흐름이 생성된 환경에서 직접 데이터 흐름의 엔터티를 추가 및 편집하고 데이터 새로 고침 일정을 관리할 수 있습니다.

PowerApps 포털에 데이터 흐름을 생성하면 데이터 흐름을 만들 때 선택한 대상에 따라 Common Data Service 커넥터 또는 Power BI Desktop 데이터 흐름 커넥터를 사용하여 이 흐름에서 데이터를 얻을 수 있습니다.

데이터 흐름을 사용하기 위한 세 가지 기본 단계가 있습니다.

1.  PowerApps 포털에서 데이터 흐름을 작성합니다. 작업을 바로 수행할 수 있도록 설계된 Microsoft 도구를 사용하여 출력 데이터를 로드할 대상, 데이터를 가져올 소스, 데이터를 변환하는 Power Query 단계를 선택합니다.

2.  일정 데이터 흐름을 실행합니다. 이는 Power Platform 데이터 흐름에서 이것이 로드 및 변환할 데이터를 새로 고쳐야 하는 빈도입니다.

3.  대상 저장소에 로드한 데이터를 사용하십시오. 앱, 흐름, Power BI 보고서, 대시보드를 빌드하거나 또는 Azure Data Factory, Azure Databricks 같은 Azure 데이터 서비스 또는 Common Data Model 폴더 표준을 지원하는 다른 모든 서비스를 사용하여 조직의 레이크에 있는 데이터 흐름의 Common Data Model 폴더에 직접 연결할 수 있습니다.

다음 섹션에서는 각 단계를 완료하기 위해 제공된 도구에 익숙해질 수 있도록 각 단계를 살펴봅니다. 

## <a name="create-a-dataflow"></a>데이터 흐름 만들기
하나의 환경에서 데이터 흐름이 생성됩니다. 따라서 해당 환경에서만 흐름을 보고 관리할 수 있습니다. 또한 데이터 흐름에서 데이터를 가져오려는 개인은 이를 생성한 환경에 액세스할 수 있어야 합니다.

> [!NOTE]
> 기본 환경의 Azure Data Lake Storage Gen2에 데이터를 로드하는 데이터 흐름 생성은 현재 지원되지 않습니다.

1.  PowerApps에 로그인하고 어떤 환경인지 확인하고, 명령 모음의 오른쪽 근처에서 환경 전환기를 찾으십시오.

    ![환경 전환기](media/environment-switcher.png)

2.  왼쪽 탐색 창에서 **데이터** 옆에 있는 아래쪽 화살표를 선택하십시오.

    ![데이터 선택](media/data-select.png)

3.  **데이터** 목록에서 **데이터 흐름**을 선택한 다음 **새 데이터 흐름**을 선택합니다.

    ![데이터 흐름 만들기](media/create-a-dataflow.png)

4.  **로드 대상 선택** 페이지에서 엔터티를 저장할 대상 저장소를 선택하십시오. 데이터 흐름은 Common Data Service 또는 조직의 Azure Data Lake Storage 계정에 엔터티를 저장할 수 있습니다. 데이터를 로드할 대상을 선택한 후 데이터 흐름의 **이름**을 입력한 다음 **만들기**를 선택합니다.

    ![로드 대상 선택](media/select-load-target.png)

     > [!IMPORTANT]
     > 데이터 흐름의 담당자(데이터를 생성한 사람)는 한 명뿐입니다. 담당자만 데이터 흐름을 편집할 수 있습니다. 데이터 흐름에 의해 생성된 데이터에 대한 권한 및 액세스는 데이터를 로드한 대상에 따라 다릅니다. Common Data Service에 로드된 데이터는 Common Data Service 커넥터를 통해 사용할 수 있으며 데이터에 액세스하는 사람에게 Common Data Service 권한을 부여해야 합니다.
     > 조직의 Azure Data Lake Gen2 저장소 계정에 로드된 데이터는 Power Platform 데이터 흐름 커넥터를 통해 액세스할 수 있으며 이에 액세스하려면 생성된 환경 내에서 구성원 자격이 필요합니다.

5. **데이터 원본 선택** 페이지에서 엔터티가 저장된 데이터 원본을 선택한 다음 **만들기**를 선택합니다. 표시되는 데이터 소스를 선택하면 데이터 흐름 엔터티를 만들 수 있습니다. 

    ![데이터 원본 선택](media/choose-data-source.png)

6. 데이터 원본을 선택하면 데이터 원본에 연결할 때 사용할 계정을 포함하여 연결 설정을 제공하라는 메시지가 표시됩니다.

    ![데이터 원본에 연결](media/data-source-provide-cred.png)

7. 연결되면 엔터티에 사용할 데이터를 선택합니다. 데이터와 원본을 선택하면 Power Platform 데이터 흐름 서비스는 이에 따라 데이터 원본에 다시 연결하여 설정 과정에서 나중에 선택한 빈도로 데이터 흐름의 데이터를 새로 고칩니다.


    ![데이터 선택](media/choose-data.png)

엔터티에서 사용할 데이터를 선택했으므로 데이터 흐름 편집기를 사용하여 해당 데이터를 데이터 흐름에 사용하기 위해 필요한 형식으로 셰이핑하거나 변환할 수 있습니다.

## <a name="use-the-dataflow-editor-to-shape-or-transform-data"></a>데이터 흐름 편집기를 사용하여 데이터 셰이핑 또는 변형
파워 쿼리 편집 환경을 사용하여 Power BI Desktop의 파워 쿼리 편집기와 유사하게 엔터티에 가장 적합한 양식으로 데이터를 셰이핑할 수 있습니다. 파워 쿼리에 대한 자세한 내용은 [Power BI Desktop의 검색어 개요](/power-bi/desktop-query-overview)를 참조하십시오.

각 단계에서 쿼리 편집기가 작성하는 코드를 보거나 고유한 셰이핑 코드를 작성하려는 경우 고급 편집기를 사용할 수 있습니다.

![고급 편집기](media/advanced-editor.png)

## <a name="dataflows-and-the-common-data-model"></a>데이터 흐름 및 Common Data Model 
데이터 흐름 엔터티에는 비즈니스 데이터를 Common Data Model에 쉽게 매핑하고 Microsoft 및 타사 데이터로 풍부하게 하고 기계 학습에 대한 단순한 액세스 권한을 얻는 새로운 도구가 포함되어 있습니다. 이러한 새로운 기능을 활용하여 비즈니스 데이터에 대한 지능적이고 실행 가능한 통찰력을 제공할 수 있습니다. 아래 설명된 쿼리 편집 단계에서 변환을 완료하면 Common Data Model에 정의된 대로 데이터 원본 테이블의 열을 표준 엔터티 필드에 매핑할 수 있습니다. 표준 엔터티에는 Common Data Model로 정의된 알려진 스키마가 있습니다.

이 방법과 Common Data Model에 대한 자세한 내용은 [Common Data Model](/powerapps/common-data-model/overview)을 참조하십시오.

데이터 흐름에 Common Data Model을 활용하려면 **쿼리 편집** 대화의 **표준에 매핑** 변환을 선택합니다. **엔터티 매핑** 화면이 나타나면 매핑할 표준 엔터티를 선택하십시오.

![표준 엔터티에 매핑](media/map-to-standard-entity.png)

원본 열을 표준 필드에 매핑하면 다음이 발생합니다.

1.  원본 열은 표준 필드 이름을 사용합니다(이름이 다른 경우 열 이름이 바뀐 것임). 

2.  원본 열은 표준 필드 데이터 형식을 가집니다. 

Common Data Model 표준 엔터티를 유지하기 위해 매핑되지 않은 모든 표준 필드는 *Null* 값을 가집니다.

매핑되지 않은 모든 원본 열은 매핑 결과가 사용자 지정 필드가 있는 표준 엔터티가 되도록 그대로 유지됩니다.

선택을 완료하고 엔터티 및 해당 데이터 설정이 완료되면 다음 단계를 수행할 수 있습니다. 다음 단계는 데이터 흐름의 새로 고침 빈도를 선택하는 것입니다.

## <a name="set-the-refresh-frequency"></a>새로 고침 빈도 설정
엔터티가 정의되면 연결된 각 데이터 원본의 새로 고침 빈도를 예약해야 합니다.

1. 데이터 흐름은 데이터 새로 고침 프로세스를 사용하여 데이터를 최신 상태로 유지합니다. **Power Platform 데이터 흐름 작성 도구**에서 예정된 간격으로 수동 또는 자동으로 데이터 흐름을 새로 고칠 수 있습니다. 새로 고침을 자동으로 예약하려면 **자동으로 새로 고침**을 선택합니다.

   ![자동으로 새로 고침](media/refresh-automatically.png)

2. 데이터 흐름 새로 고침 빈도, 시작 날짜 및 시간을 UTC 기준으로 입력하십시오.

3. **만들기**를 선택합니다.
<!-- 
## Connect to your dataflow in Power BI Desktop
Once you’ve created your dataflow and you have scheduled the refresh frequency
for each data source that will populate the model, you’re ready for the final task, which is connecting to your dataflow from within Power BI Desktop.

To connect to the dataflow, in Power BI Desktop select **Get Data** > **Power Platform** > **Power Platform dataflows** > **Connect**.

![Connect to the dataflow](media/get-data.png)

Navigate to the environment where you saved your dataflow, select
the dataflow, and then select the entities that you created from the list.

You can also use the search bar, near the top of the window, to quickly find the
name of your dataflow or entities from among many dataflow entities.

When you select the entity and then select the **Load** button, the entities
appear in the **Fields** pane in Power BI Desktop, and appear and behave just
like tables from any other dataset. -->

## <a name="using-dataflows-stored-in-azure-data-lake-storage-gen2"></a>Azure Data Lake Storage Gen2에 저장된 데이터 흐름 사용
일부 조직은 고유한 저장소를 사용하여 데이터 흐름을 만들고 관리할 수 있습니다. 저장소 계정을 올바르게 설정하기 위한 요구 사항을 따르는 경우 Azure Data Lake Storage Gen2와 데이터 흐름을 통합할 수 있습니다. 추가 정보: [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2) 

## <a name="troubleshooting-data-connections"></a>데이터 연결 문제 해결
데이터 흐름을 위해 데이터 소스에 연결할 때 문제가 발생할 수 있습니다. 이 섹션에서는 문제 발생 시 문제 해결 팁을 제공합니다.

-   **Salesforce 커넥터.** 데이터 흐름에 Salesforce용 평가판 계정을 사용하면 정보가 제공되지 않고 연결이 실패합니다. 이 문제를 해결하려면 프로덕션 Salesforce 계정 또는 개발자 계정을 사용하여 테스트하십시오.

-   **SharePoint 커넥터.** 하위 폴더나 문서가 없는 SharePoint 사이트의 루트 주소를 제공해야 합니다. 예를 들어, *https://microsoft.sharepoint.com/teams/ObjectModel*과 비슷한 링크를 사용하십시오.


-   **JSON 파일 커넥터.** 현재 기본 인증만 사용하여 JSON 파일에 연결할 수 있습니다. 예를 들어 *https://XXXXX.blob.core.windows.net/path/file.json?sv=2019-01-01&si=something&sr=c&sig=123456abcdefg*와 같은 URL은 현재 지원되지 않습니다.

-   **Azure SQL Data Warehouse.** 데이터 흐름은 현재 Azure SQL Data Warehouse에 대해 Azure Active Directory 인증을 지원하지 않습니다. 이 시나리오에는 기본 인증을 사용하십시오.

## <a name="next-steps"></a>다음 단계
다음 문서는 데이터 흐름을 사용할 때 추가 정보 및 시나리오에 유용합니다.

-   [Common Data Service에서 엔터티에 데이터 추가](data-platform-cds-newentity-pq.md)

-   [온-프레미스 데이터 원본과 함께 데이터 흐름 사용](using-dataflows-with-on-premises-data.md)

-   [데이터 흐름 저장소에 Azure Data Lake Storage Gen2 연결](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)

Common Data Model에 대한 자세한 내용은 다음을 참조하십시오.

-   [Common Data Model - 개요](/powerapps/common-data-model/overview)

-   [GitHub의 Common Data Model 스키마 및 엔터티에 대해 자세히 알아보십시오.](https://github.com/Microsoft/CDM)
