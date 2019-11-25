---
title: Dynamics 365 Power BI 콘텐츠 팩 사용자 지정 | MicrosoftDocs
description: Dynamics 365 데이터에 사용할 수 있는 Power BI 콘텐츠 팩을 수정하는 방법에 대해 알아봅니다.
keywords: PBI
ms.date: 09/30/2017
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 424d7f29-de44-4ce0-94f1-be8777ad6485
author: Mattp123
ms.author: matp
manager: amyla
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 16
topic-status: Drafting
tags: ''
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: 929230a38cf0c9ea1dc23b98550c45fa54f18545
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753837"
---
# <a name="customize-dynamics-365-apps-power-bi-content-packs"></a>Dynamics 365 앱 Power BI 콘텐츠 팩 사용자 지정

Power BI는 비즈니스 데이터를 시각화하기 위해 사용하는 광범위한 서비스 도구 모음입니다.  콘텐츠 팩을 사용하면 표준 데이터 모델에 기반하여 Dynamics 365 Sales, Service, Marketing 앱 데이터를 Power BI로 쉽게 시각화하고 분석할 수 있습니다. 콘텐츠 팩은 대부분의 영업, 서비스 또는 마케팅 시나리오에 유용한 엔터티 및 필드 집합으로 빌드됩니다.  
  
 Dynamics 365 앱은 종종 사용자 지정 필드를 사용하여 확장됩니다. 이러한 사용자 지정 필드는 Power BI 모델에서 자동으로 표시 되지 않습니다. 이 항목에서는 Power BI 모델의 사용자 지정 필드를 포함하기 위한 콘텐츠 팩에 포함된 보고서를 편집하거나 확장할 수 있는 다양한 방법에 대해 설명합니다.  
    
<a name="PBI_edit_first"></a>   
## <a name="do-this-before-you-customize-a-content-pack-for-power-bi-reports"></a>Power BI 보고서를 위한 콘텐츠 팩을 사용자 지정하기 전에 이 작업을 수행합니다.  
 
콘텐츠 팩을 사용자 지정하기 전에 정보를 읽고 필요에 따라 각 작업을 수행합니다.  
  
### <a name="meet-the-requirements"></a>요구 사항 충족  
  
- [Power BI 서비스 등록](https://powerbi.com/).  
  
- Power BI 보고서 보고서 편집을 위한 [Power BI Desktop](https://powerbi.microsoft.com/desktop) 응용 프로그램.  
  
- 사용자 지정하려는 콘텐츠 팩의 PBIX 파일.  
  
  -   [Dynamics CRM Online 영업 관리자 PBIX 다운로드](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
  -   [Dynamics CRM Online 서비스 관리자 PBIX 다운로드](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  -   [Microsoft Dynamics 365 프로세스 분석기 PBIX 다운로드](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Process%20Analyzer%20-1.34b.pbix)  
  
  Dynamics 365 콘텐츠 팩은 현재 미국 영어로만 지원됩니다.  
  
### <a name="prepare-a-content-pack-for-customization"></a>사용자 지정을 위한 콘텐츠 팩 준비  
  
> [!IMPORTANT]
>  인스턴스에 OData 피드를 연결하려면 콘텐츠 팩을 사용자 지정하기 전에 여기에 설명된 단계를 수행해야 합니다.  
> 
> 현재 Power BI 서비스는 Dynamics 365 버전 9.0 OData 끝점과 호환되지 않습니다. Power BI 서비스와 함께 버전 9.0 OData 끝점을 사용하려고 하면 "피드의 메타데이터 문서가 잘못된 것 같습니다." 오류 메시지가 표시됩니다. 이 비 호환성을 해결하려면 Dynamics 365 버전 8.2 OData 끝점을 사용합니다. 다른 끝점 버전에 대한 자세한 내용은 [HTTP 요청 및 처리 오류 작성](../../developer/common-data-service/webapi/compose-http-requests-handle-errors.md)을 참조하십시오.
  
1. Power BI Desktop을 시작합니다.  
  
    **파일** > **열기**를 선택하고 Sales Manager.bpix와 같은 콘텐츠 팩을 연 다음 **열기**를 선택합니다.  
  
    콘텐츠 팩의 여러 보고서 페이지가 로드되며 Power BI Desktop에 표시됩니다.  
  
2. Power BI Desktop 리본의 **쿼리 편집**을 선택합니다.  
  
3. 쿼리 편집 창의 왼쪽 탐색 창의 **쿼리** 아래에서 **CRMServiceUrl** 쿼리를 선택한 다음 리본에서 **고급 편집기**를 선택합니다. 원본 정의에서 **base.crm.dynamics.com**을 앱 인스턴스 URL로 교체합니다. 예를 들어, 조직 이름이 *Contoso*라면, URL은 다음과 같습니다.  
  
    원본 = "https://*contoso*.crm.dynamics.com/api/data/v8.0/"  
  
4. **완료**를 선택한 다음 쿼리 편집기의 **닫기 및 적용**을 선택합니다.  
  
5. OData 피드 액세스 대화 상자가 나타나면 **조직 계정**를 선택한 다음 **로그인**을 선택합니다.  
  
   ![OData 피드 대화 상자에 액세스](media/pbi-odata-signin.PNG "OData 피드 대화 상자에 액세스")  
  
6. 로그인 페이지가 나타나면 자격 증명을 입력하여 인스턴스에 인증합니다.  
  
7. OData 피드 액세스 대화 상자에서 **연결**을 선택합니다.  
  
    콘텐츠 팩 쿼리가 업데이트됩니다. 몇 분 정도 걸릴 수 있습니다.  
  
<a name="PBI_edit_report"></a>   
## <a name="customize-adynamics-365-content-pack"></a>Dynamics 365 콘텐츠 팩 사용자 지정  
 [보고서에 표시되는 날짜 형식 변경](#PBI_edit_date)  
  
 [거래처를 제외한 모든 엔터티에 대한 보고서에 사용자 지정 필드 추가](#PBI_edit_field)  
  
 [거래처 엔터티에 대한 보고서에 사용자 지정 필드 추가](#PBI_field_Account)  
  
 [보고서에 옵션 집합 필드 추가](#PBI_optionset_field)  
  
 [쿼리된 행의 수 늘리기](#BPI_increaserows)  
  
<a name="PBI_edit_date"></a>   
### <a name="convert-a-datetime-field-to-a-date-field-for-reporting"></a>날짜/시간 필드를 보고 날짜 필드로 변환  
 Dynamics 365 앱에서 일부 날짜는 날짜/시간/표준 시간대 형식으로 저장됩니다. 이 형식은 보고서에서 데이터를 집계하는 데 사용하기에는 적합하지 않을 수 있습니다. 엔터티 필드에 대한 보고서에 표시되는 날짜를 변환할 수 있습니다. 예를 들어, 영업 기회 생성 날짜 필드를 영업 기회를 보고할 날짜로 변환할 수 있습니다.  
  
1. Power BI Desktop에서 **쿼리 편집**을 선택합니다.  
  
2. 쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래의 **영업 기회** 엔터티 쿼리의 **예상 종료 날짜**와 같은 변경할 날짜 필드가 있는 쿼리를 선택합니다.  
  
3. *예상 종료 날짜*와 같은 열 머리글을 마우스 오른쪽 단추로 클릭하고, **형식 변경**을 가리킨 다음, **날짜**와 같은 다른 날짜 형식을 선택합니다.  
  
   ![Power BI Desktop에서 데이터 형식 변경](media/pbi-changeformat.PNG "Power BI Desktop에서 데이터 형식 변경")  
  
4. **닫기 및 적용**을 선택하여 쿼리 편집기를 닫습니다.  
  
5. Power BI 메인 페이지에서 **변경 내용 적용**을 선택하여 관련된 보고서를 업데이트합니다.  
  
<a name="PBI_edit_field"></a>   
### <a name="add-a-custom-field-to-a-report"></a>보고서에 사용자 지정 필드 추가  
 다음 절차에서는 거래처 엔터티를 제외한 모든 가능한 엔터티에 대한 보고서에 날짜, 문자열 또는 숫자 사용자 지정 필드를 추가하는 방법을 설명합니다.  
  
> [!NOTE]
>  거래처 엔터티에 필드를 추가하려면 [거래처 엔터티에 대한 보고서에 사용자 지정 필드 추가](#PBI_field_Account)를 참조하십시오. 옵션 집합 형식인 필드를 추가하려면 [보고서에 옵션 집합 필드 추가](#PBI_optionset_field)를 참조하십시오.  
  
1. Power BI Desktop에서 **쿼리 편집**을 선택합니다.  
  
2. 쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래의 **영업 기회** 엔터티 쿼리와 같은 보고서에 사용 가능한 사용자 지정 필드가 있는 쿼리를 선택합니다.  
  
3. 오른쪽 창의 **적용된 단계**에서 **제거된 기타 열** 옆에 있는 설정 단추![설정 단추](media/mp-ua-r16-settings.png "설정 단추")를 선택합니다.  
  
4. **열 선택** 목록에 사용자 지정 필드를 포함하여 엔터티의 모든 필드가 표시됩니다. 원하는 사용자 지정 필드를 선택하고 **확인**을 선택합니다.  
  
    엔터티 쿼리가 업데이트되며 선택한 사용자 지정 필드에 대한 엔터티 테이블에 열이 추가됩니다.  
  
5. 오른쪽 창의 **적용된 단계**에서 **언어 - 바꾼 열 이름**을 선택한 다음 **고급 편집기**를 선택하여 엔터티 쿼리에 필드에 대한 매핑을 추가합니다. 예를 들어, 영업 기회에 대한 사용자 지정 필드 이름이 *int_forecast*인 경우 표시되는 이름은 *예측*이며 나타나는 모습은 다음과 같습니다.  
  
   ```  
   {"int_forecast","Forecast"}  
   ```  
  
   ![보고서에 사용자 지정 필드에 대한 매핑 추가](media/pbi-addfieldmapping.png "보고서에 사용자 지정 필드에 대한 매핑 추가")  
  
6. 필드 매핑을 추가하고 난 후 고급 편집기 맨 아래에 구문 오류가 표시되지 않는지 확인하십시오. 또한 필드 이름이 올바른 대/소문자를 포함하여 열 머리글에 나타나는 대로 정확하게 표시되는지 확인합니다. 구문 오류 또는 테이블 오류가 발견되지 않으면 **완료**를 선택합니다.  
  
7. 쿼리 편집기의 **닫기 및 적용**을 클릭합니다.  
  
    이제 오른쪽 창의 해당 엔터티에 대한 **필드**에서 사용자 지정 필드를 사용할 수 있으며 기존 또는 새 보고서에 사용자 지정 필드를 추가할 수 있습니다.  
  
<a name="PBI_field_Account"></a>   
## <a name="add-a-custom-field-to-a-report-for-the-account-entity"></a>거래처 엔터티에 대한 보고서에 사용자 지정 필드 추가  
 거래처 쿼리는 쿼리를 필터링하는 데 Fetch XML을 사용하기 때문에 필드를 추가하는 단계는 OData를 사용하는 다른 엔터티 쿼리와 다릅니다. OData 쿼리된 엔터티에 사용자 지정 필드를 추가하려면 [보고서에 사용자 지정 필드 추가](#PBI_edit_field)를 참조하십시오.  
  
1. 거래처 엔터티에 대해 인코딩된 Fetch XML 쿼리를 복사합니다. 이렇게 하려면 다음 단계를 수행합니다.  
  
   1.  Power BI Desktop에서 **쿼리 편집**을 선택합니다.  
  
   2.  쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래의 **거래처** 엔터티 쿼리를 선택한 다음 리본에 있는 **고급 편집기**를 선택합니다.  
  
   3.  %3Cfetch로 시작하고 fetch%3E로 끝나는 첫 번째 줄에서 전체 인코딩된 Fetch XML을 복사합니다.  
  
   4.  복사할 인코딩된 Fetch XML은 다음과 같은 모습입니다.  
  
        %3Cfetch%20version%3D%221.0%22%20output-format%3D%22xml-platform%22%20mapping%3D%22logical%22%20distinct%3D%22true%22%3E%3Centity%20name%3D%22account%22%3E%3Cattribute%20name%3D%22territorycode%22%20%2F%3E%3Cattribute%20name%3D%22customersizecode%22%20%2F%3E%3Cattribute%20name%3D%22owningbusinessunit%22%20%2F%3E%3Cattribute%20name%3D%22ownerid%22%20%2F%3E%3Cattribute%20name%3D%22originatingleadid%22%20%2F%3E%3Cattribute%20name%3D%22revenue%22%20%2F%3E%3Cattribute%20name%3D%22sic%22%20%2F%3E%3Cattribute%20name%3D%22marketcap%22%20%2F%3E%20%3Cattribute%20name%3D%22parentaccountid%22%20%2F%3E%3Cattribute%20name%3D%22owninguser%22%20%2F%3E%3Cattribute%20name%3D%22accountcategorycode%22%20%2F%3E%3Cattribute%20name%3D%22marketcap_base%22%20%2F%3E%3Cattribute%20name%3D%22customertypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_postalcode%22%20%2F%3E%3Cattribute%20name%3D%22numberofemployees%22%20%2F%3E%3Cattribute%20name%3D%22accountratingcode%22%20%2F%3E%3Cattribute%20name%3D%22address1_longitude%22%20%2F%3E%3Cattribute%20name%3D%22revenue_base%22%20%2F%3E%3Cattribute%20name%3D%22createdon%22%20%2F%3E%3Cattribute%20name%3D%22name%22%20%2F%3E%3Cattribute%20name%3D%22address1_stateorprovince%22%20%2F%3E%3Cattribute%20name%3D%22territoryid%22%20%2F%3E%3Cattribute%20name%3D%22accountclassificationcode%22%20%2F%3E%3Cattribute%20name%3D%22businesstypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_country%22%20%2F%3E%3Cattribute%20name%3D%22accountid%22%20%2F%3E%3Cattribute%20name%3D%22address1_latitude%22%20%2F%3E%3Cattribute%20name%3D%22modifiedon%22%20%2F%3E%3Cattribute%20name%3D%22industrycode%22%20%2F%3E%3Clink-entity%20name%3D%22opportunity%22%20from%3D%22parentaccountid%22%20to%3D%22accountid%22%20alias%3D%22ab%22%3E%3Cfilter%20type%3D%22and%22%3E%3Ccondition%20attribute%3D%22opportunityid%22%20operator%3D%22not-null%22%20%2F%3E%3Ccondition%20attribute%3D%22modifiedon%22%20operator%3D%22last-x-days%22%20value%3D%22365%22%20%2F%3E%3C%2Ffilter%3E%3C%2Flink-entity%3E%3C%2Fentity%3E%3C%2Ffetch%3E  
  
2. 인코딩된 Fetch XML을 디코딩합니다. 유효한 인코딩된 Fetch XML이어야 하며 인코딩되면 다음과 유사한 모습이어야 합니다.  
  
    \<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true"> \<entity name="account"> \<attribute name="territorycode" /> \<attribute name="customersizecode" /> \<attribute name="owningbusinessunit" /> \<attribute name="ownerid" /> \<attribute name="originatingleadid" /> \<attribute name="revenue" /> \<attribute name="sic" /> \<attribute name="marketcap" />  \<attribute name="parentaccountid" /> \<attribute name="owninguser" /> \<attribute name="accountcategorycode" /> \<attribute name="marketcap_base" /> \<attribute name="customertypecode" /> \<attribute name="address1_postalcode" /> \<attribute name="numberofemployees" /> \<attribute name="accountratingcode" /> \<attribute name="address1_longitude" /> \<attribute name="revenue_base" /> \<attribute name="createdon" /> \<attribute name="name" /> \<attribute name="address1_stateorprovince" /> \<attribute name="territoryid" /> \<attribute name="accountclassificationcode" /> \<attribute name="businesstypecode" /> \<attribute name="address1_country" /> \<attribute name="accountid" /> \<attribute name="address1_latitude" /> \<attribute name="modifiedon" /> \<attribute name="industrycode" /> \<link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab"> \<filter type="and"> \<condition attribute="opportunityid" operator="not-null" /> \<condition attribute="modifiedon" operator="last-x-days" value="365" /> \</filter> \</link-entity> \</entity> \</fetch>  
  
   > [!TIP]
   >  여러 URL 인코더와 디코더 도구가 웹에서 무료로 제공됩니다.  
  
3. Fetch XML에서 \<엔터티> 노드 사이에 사용자 지정 엔터티를 엔터티 노드로 추가합니다. 예를 들어, 이름이 *customclassificationcode*인 사용자 지정 필드를 추가하려면 **industrycode**와 같은 다른 특성 노드 노드를 추가합니다.  
  
   ```  
  
   <attribute name="industrycode" />  
   <attribute name=" customclassificationcode "/>  
   <link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab">  
   ```  
  
4. 업데이트된 Fetch XML을 URL 인코딩합니다. 새 사용자 지정 특성이 포함된 Fetch XML이 인코딩되며 콘텐츠 팩과 함께 제공되는 기존 OData 피드 쿼리 대신 사용됩니다. 이렇게 하려면 업데이트된 FetchXML을 클립보드로 복사한 다음 URL 인코더에 붙여 넣습니다.  
  
5. 인코딩된 Fetch XML URL을 OData 피드에 붙여 넣습니다. 이를 위해 **Query=[fetchXml=** 텍스트 다음의 따옴표 사이에 인코딩된 URL을 붙여 넣어 기존 인코딩된 FetchXML을 대체한 다음 **완료**를 선택합니다.  
  
    다음 스크린샷은 맨 왼쪽 따옴표의 위치를 나타냅니다.  
  
   ![OData 피드에 인코딩된 URL 붙여 넣기](media/pbi-acct-encoded-url.PNG "OData 피드에 인코딩된 URL 붙여 넣기")  
  
6. 오른쪽 창의 **적용된 단계**에서 **제거된 기타 열** 옆에 있는 설정 단추![설정 단추](media/mp-ua-r16-settings.png "설정 단추")를 선택합니다.  
  
7. 열 선택 목록에 사용자 지정 필드를 포함하여 엔터티의 모든 필드가 표시됩니다. 이전에 Fetch XML에 추가한 *customclassificationcode*와 같은 사용자 지정 필드를 선택한 다음 **확인**을 선택합니다.  
  
   > [!NOTE]
   >  열 선택기에서 선택한 필드 이름이 FetchXML 쿼리에 추가한 필드 이름과 일치해야 합니다.  
  
    엔터티 쿼리가 업데이트되며 선택한 사용자 지정 필드에 대한 엔터티 테이블에 열이 추가됩니다.  
  
8. 쿼리 편집기의 **닫기 및 적용**을 선택합니다.  
  
    이제 오른쪽 창의 해당 엔터티에 대한 **필드**에서 사용자 지정 필드를 사용할 수 있으며 기존 또는 새 보고서에 사용자 지정 필드를 추가할 수 있습니다.  
  
<a name="PBI_optionset_field"></a>   
## <a name="add-a-custom-option-set-field-to-a-report"></a>보고서에 사용자 지정 옵션 집합 필드 추가  
 옵션 집합 필드를 사용하여 여러 값을 선택할 수 있습니다. 기본적인 옵션 집합 필드로 영업 기회에 대한 등급 및 영업 스테이지 필드가 있습니다. 다음 값 및 레이블이 있는 기본 영업 기회 양식의 사용자 지정 옵션 집합 필드를 가정해 봅시다.  
  
 ![사용자 지정 옵션 집합 예제](media/pbi-custom-option-set-example.PNG "사용자 지정 옵션 집합 예제")  
  
 사용자 지정 옵션 집합 필드를 보고서에 추가하려면 다음 단계를 수행합니다.  
  
1. 사용자 지정 필드 열을 추가합니다.  
  
   -   쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래의 *영업 기회* 엔터티 같은 연결된 사용자 지정 옵션 집합이 있는 엔터티를 선택합니다.  
  
   -   오른쪽 창의 **적용된 단계**에서 **제거된 기타 열** 옆에 있는 설정 단추![설정 단추](media/mp-ua-r16-settings.png "설정 단추")를 선택합니다.  
  
   -   열 선택 목록에 사용자 지정 필드를 포함하여 엔터티의 모든 필드가 표시됩니다. *new_customoptionset*와 같은 사용자 지정 필드를 선택한 다음 **확인**을 선택합니다.  
  
   -   **저장**을 선택한 다음 메시지가 나타나면 **적용**을 선택합니다.  
  
        사용자 지정 필드의 열은 엔터티 테이블에 나타납니다.  
  
2. 옵션 집합 쿼리를 만듭니다.  
  
   1.  Power BI Desktop에서 **쿼리 편집**을 선택합니다.  
  
   2.  쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래에 보고서에 추가하고자 하는 옵션 집합과 가장 비슷한 옵션 집합 필드가 있는 **테이블 만들기** 그룹 아래의 쿼리를 선택합니다. 이 예에서 **SalesStageOptionSet** 쿼리는 4개의 옵션이 있으므로 좋은 선택입니다.  
  
   3.  **고급 편집기**를 선택합니다.  
  
        옵션 집합 쿼리가 표시됩니다.  
  
   ![옵션 집합 쿼리 만들기](media/pbi-makeoptionsetquery.png "옵션 집합 쿼리 만들기")  
  
   4.  전체 쿼리를 클립보드로 복사합니다. 나중에 참조할 수 있도록 메모장과 같은 텍스트 편집기에 붙여 넣을 수 있습니다.  
  
   5.  쿼리 편집기에서 **테이블 만들기** 그룹을 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**, 그리고 **빈 쿼리**를 차례로 선택합니다.  
  
   6.  오른쪽 창에서 **이름** 아래에 *CustomOptionSet*와 같은 이름을 입력한 다음 Enter 키를 누릅니다.  
  
   7.  **고급 편집기**를 선택합니다.  
  
   8.  고급 편집기에서 이전에 복사한 쿼리를 붙여 넣습니다.  
  
   9. 기존 값과 옵션을 사용자 지정 값 및 옵션으로 교체합니다. 이 예제에서는 다음을 변경합니다.  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"Qualify"},{1,"Develop"},{2,"Propose"},{3,"Close"}})  
       in  
           Source  
  
       ```  
  
        방법:  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"A"},{1,"B"},{2,"C"},{3,"D"},{4,"E"}})  
       in  
           Source  
  
       ```  
  
   10. 구문 오류가 없는지 확인한 다음 **완료**를 선택하여 고급 편집기를 닫습니다. 값과 옵션 테이블이 쿼리 편집기에 나타납니다.  
  
   ![새 옵션 집합 쿼리](media/pbi-optionsetquerycreated.png "새 옵션 집합 쿼리")  
  
   11. **저장**을 선택한 다음 메시지가 나타나면 **적용**을 선택합니다.  
  
3. 엔터티 및 사용자 지정 옵션 집합 테이블에 대한 병합 쿼리를 삽입합니다.  
  
   1.  쿼리 편집기의 왼쪽 창에서 **엔터티** 아래의 사용자 지정 옵션 집합을 포함하는 엔터티를 선택합니다. 이 예에서는 **영업 기회** 엔터티 쿼리를 선택합니다.  
  
   2.  리본에서 **병합 쿼리**를 클릭하고 단계를 삽입하라는 메시지가 나타나면 **삽입**을 선택합니다.  
  
   3.  병합 대화 상자에서 *new_optionset*과 같은 사용자 지정 옵션 집합에 대한 열 머리글을 선택합니다. 드롭다운 목록에서 이전에 만든 해당 옵션 집합 쿼리를 선택합니다.  옵션 집합 테이블이 나타나면 **값** 열 머리글을 선택합니다.  
  
   ![테이블 선택 병합](media/pbi-merge-tables.png "테이블 선택 병합")  
  
   4.  **왼쪽 외부(처음부터 모두, 두 번째부터 일치하는)** 와 같은 조인은 그대로 두고 **확인**을 선택합니다.  
  
       > [!TIP]
       >  병합 쿼리의 이름을 바꿉니다. **적용된 단계**에서 만든 병합 쿼리를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택한 다음 *CustomOptionSet 병합*과 같이 쿼리를 설명하는 이름을 입력합니다.  
  
4. 레이블만 표시되도록 열을 정의합니다.  
  
   1.  쿼리 편집기의 왼쪽 창에서 엔터티 아래의 사용자 지정 옵션 집합을 포함하는 엔터티를 선택합니다. 이 예에서는 **영업 기회** 엔터티 쿼리를 선택합니다.  
  
   2.  오른쪽 창의 **적용된 단계**에서 확장된 쿼리 중 하나를 선택하여 **확장된 SalesStage**와 같은 병합된 열을 표시합니다.  
  
   3.  이전 병합 쿼리 단계의 일부로 생성된 새 열의 열 머리글을 찾아 선택합니다.  
  
   4.  **변환** 탭에서 **확장**을 선택합니다.  
  
   5.  새 열 확장 대화 상자에서 해당 값에 해당하는 열을 지웁니다(열에 레이블만 표시되어야 함). **완료**를 선택합니다.  
  
   ![라벨을 나타내는 열 선택](media/pbi-expand-column.png "라벨을 나타내는 열 선택")  
  
   6.  **저장**을 선택한 다음 메시지가 나타나면 **적용**을 선택합니다.  
  
5. 보고서 빌드에 대한 열 이름을 변경합니다.  
  
   1.  쿼리 편집기의 왼쪽 창에서 **엔터티** 아래의 사용자 지정 옵션 집합을 포함하는 엔터티를 선택합니다. 이 예에서는 **영업 기회** 엔터티 쿼리를 선택합니다.  
  
   2.  **고급 편집기**를 선택합니다.  
  
   3.  이름을 변경한 열 품목을 추가하고 구문 오류가 없는지 확인한 다음 **완료**를 선택합니다. 이 예제에서는 이전에 만든 사용자 지정 옵션 집합 열 이름인 **NewColumn**이 *사용자 지정 옵션 집합*으로 바뀝니다.  
  
   ![보고서에 표시할 열 이름 변경](media/pbi-rename-column.png "보고서에 표시할 열 이름 변경")  
  
   4.  **저장**을 선택한 다음 메시지가 나타나면 **적용**을 선택합니다.  
  
6. **닫기 및 적용**을 선택하여 쿼리 편집기를 닫습니다.  
  
    사용자 지정 옵션 집합을 이제 Power BI 보고서 빌드에 사용할 수 있습니다.  
  
<a name="BPI_increaserows"></a>   
## <a name="increase-the-number-of-rows-queried"></a>쿼리된 행의 수 늘리기  
 기본적으로 콘텐츠 팩의 모든 Power BI 엔터티 쿼리는 10만 행을 초과할 수 없습니다. 쿼리할 수 있는 행의 수를 늘리려면 다음 단계를 수행합니다.  
  
> [!IMPORTANT]
>  행 개수 제한을 늘리면 보고서를 새로 고치는 시간에 크게 영향을 줄 수 있습니다. 또한 해당 Power BI 서비스에서 쿼리를 실행하는 데 30분의 제한이 있습니다. 행 개수 제한을 늘릴 때는 주의가 필요합니다.  
  
1. Power BI Desktop에서 **쿼리 편집**을 선택합니다.  
  
2. 쿼리 편집기의 왼쪽 탐색 창에서 **쿼리** 아래 **잠재 고객** 엔터티와 같은 행 개수 제한을 늘리고자 하는 엔터티 쿼리를 선택합니다.  
  
3. 오른쪽 창의 **적용된 단계**에서 **유지된 첫 행**을 선택합니다.  
  
4. 필터링된 행 개수를 늘립니다. 예를 들어 행 수를 150,000개로 늘리려면 Table.FirstN(#"필터링된 행",100001)을 Table.FirstN(#"필터링된 행",150000)으로 변경합니다.  
  
5. 오른쪽 창의 **적용된 단계**에서 **행 개수 확인**을 선택합니다.  
  
6. 단계의 **>100,000** 부분을 찾습니다.  
  
   ![행 개수 값 늘리기](media/pbi-increaserowcount.png "행 개수 값 늘리기")  
  
7. 값을 *150,000* 등의 더 큰 값으로 늘립니다.  
  
8. 쿼리 편집기의 **닫기 및 적용**을 선택합니다.  
  
<a name="BPI_publish"></a>   
## <a name="publish-your-report-to-the-power-bi-service"></a>Power BI 서비스에 보고서 게시  
 조직에 공유할 내용에 대한 보고서를 게시하고 어디에서든 대부분의 장치에서 액세스할 수 있습니다.  
  
1. Power BI Desktop 기본 페이지의 **홈** 탭 리본에서 **게시**를 선택합니다.  
  
2. Power BI 서비스에 로그인하라는 메시지가 나타나면 **로그인**을 선택합니다.  
  
3. 여러 곳에 로그인할 수 있는 경우 원하는 곳을 선택한 다음 **게시**를 선택합니다.  
  
### <a name="see-also"></a>참조  
 [Dynamics 365 Customer Engagement (on-premises)에서 Power BI 사용](use-power-bi.md)
