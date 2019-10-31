---
title: Dynamics 365 앱과 함께 Power BI 사용 | MicrosoftDocs
ms.custom: null
ms.date: 12/07/2018
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement  (online)
  - Dynamics 365 for Customer Engagement  Version 9.x
ms.assetid: 48997010-a47c-4e16-b7d2-f55d7a52ba19
caps.latest.revision: 36
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - admin
search.app:
  - D365CE
  - Powerplatform
---
# <a name="use-power-bi"></a>Power BI 사용

Power BI 클라우드 서비스는 Common Data Service 앱과 함께 사용되어 셀프 서비스 분석 솔루션을 제공합니다. Power BI는 표시되는 앱의 데이터를 자동으로 새로 고칩니다. Power BI Desktop 또는 Microsoft Excel로, 파워 쿼리를 사용하여 보고서를 작성하고 Power BI를 사용하여 대시보드를 공유하고 모델 기반 앱의 데이터를 새로 고침으로써 귀하의 사용자는 앱의 데이터를 사용하는 강력한 새로운 방법을 갖게 됩니다.  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-dynamics-365-for-customer-engagement-apps-online"></a>Dynamics 365 for Customer Engagement 앱(online)에서 Power BI를 사용하여 시작하기  
 Power BI용 Dynamics 365 앱 콘텐츠 팩은 영업, 서비스 또는 마케팅 데이터에 쉽게 액세스하여 분석할 수 있게 해 줍니다.  
  
 콘텐츠 팩을 사용하여 Power BI 대시보드를 만들려면 다음 지침을 따릅니다.  
  
1. 아직 수행하지 않은 경우에는 [Power BI를 등록하십시오](http://powerbi.com/).  
  
2. Power BI에 로그인한 후, **데이터 집합** 영역에서 **데이터 받기**를 선택한 다음 **서비스** 아래의 **받기**를 선택하고, 다음 콘텐츠 팩 중에서 선택합니다.  
  
   - **Dynamics 365용 판매 분석**  
  
   - **Dynamics 365용 Customer Service 분석**  
  
   - **Microsoft Dynamics 365 - Social Engagement**  
  
3. 판매 분석 및 서비스 분석 콘텐츠 팩의 경우, *OrganizationName*이 인스턴스의 조직 이름인 *<https://OrganizationName.crm.dynamics.com>* 과 같은 인스턴스의 URL을 입력하고 **다음**을 선택합니다.  
  
   > [!NOTE]
   >  데이터 센터가 북미 이외의 지역에 있는 경우 crm.dynamics.com 도메인 이름이 crm2.dynamics.com, crm3.dynamics.com, crm4.dynamics.com 등과 같이 다를 수 있습니다. 도메인 이름을 찾으려면 앱 웹앱에서 **설정** > **사용자 지정** > **개발자 리소스**로 이동합니다. 나열된 URL에 올바른 도메인 이름이 표시됩니다.  
  
    마케팅 콘텐츠 팩의 경우 URL을 *<https://OrganizationName.marketing.dynamics.com/analytics>* 으로 입력하고(여기서 *OrganizationName*은 Dynamics 365인스턴스의 조직 이름), **다음**을 클릭합니다.  
  
4. **인증 방법**에서 **oAuth2**를 선택합니다.  
  
5. 인스턴스 데이터를 가져오면 몇 가지 시각화를 사용할 수 있습니다.  
  
> [!TIP]
>  웹 브라우저에서 선택한 콘텐츠 팩이 열리지 않으면 Power BI 작업 영역의 왼쪽 창에서 **대시보드** 아래의 콘텐츠 팩을 클릭합니다.  
  
### <a name="content-packs-available-for-download"></a>콘텐츠 팩을 다운로드할 수 있습니다.  
 Dynamics 365 Content Pack은 앱의 기본 엔터티를 지원합니다. 그러나 PBIX 파일을 다운로드하고 Power BI Desktop을 사용하여 Power BI 서비스에 업로드하기 전에 콘텐츠 팩을 맞춤하면 다음 콘텐츠 팩을 맞춤할 수 있습니다.  
  
- [Dynamics CRM Online 영업 관리자 .PBIX 다운로드](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Dynamics 365 for Customer Engagement 앱(online) 서비스 관리자 .PBIX 다운로드](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  Connected Field Service용 Power BI 보고서 템플릿으로 사용자는 연결된 장치의 라이브 하트비트를 표시하는 Power BI 보고서를 게시할 수 있습니다.  
  
- [Power BI Report Template for Connected Field Service for Dynamics 365 for Customer Engagement 다운로드](http://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 콘텐츠 팩을 맞춤화하는 방법에 대한 자세한 내용은 [Dynamics 365 for Customer Engagement앱 Power BI 콘텐츠 팩 맞춤화](customize-power-bi-content-packs.md)를 참조하십시오. 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>개인 대시보드에 Power BI 시각화 포함  
 사용자가 Power BI 시각화를 개인 대시보드에 포함하려면, 조직 전체 설정을 활성화해야 합니다.  
  
> [!NOTE]
>  기본적으로 Power BI 시각화 포함은 비활성화되어 있으며 사용자가 개인 대시보드에 탑재하려면 반드시 활성화해야 합니다.  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>조직에서 Power BI 시각화 사용  
  
1. Dynamics 365에 시스템 관리자 보안 역할이 있는 사용자로 로그인합니다.  
  
2. **설정** > **관리** > **시스템 설정**으로 이동합니다.  
  
3. **Power BI 시각화 포함 허용** 옵션의 **보고** 탭에서 **예**를 선택하여 활성화하거나 **아니요**를 선택하여 비활성화합니다.  
  
4. **확인**을 선택합니다.  
  
개인 대시보드에 Power BI 타일을 추가하는 방법에 대한 자세한 내용을 보려면 [개인 대시보드에 Power BI 타일 포함](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md#embed--power-bi-tiles-on-your-personal-dashboard)을 참조하십시오.  
  
개인 대시보드에  Power BI 대시보드를 추가하는 방법에 대한 자세한 내용을 보려면 [개인 대시보드에 Power BI 대시보드 추가](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md)를 참조하십시오.  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>Power BI Desktop를 사용하여 인스턴스에 직접 연결  
 인스턴스를 Power BI Desktop과 연결하여 맞춤 보고서 및 대시보드를 만들면 Power BI 서비스와 사용할 수 있습니다.  
  
### <a name="requirements"></a>요구 사항  
  
- Power BI 서비스 등록  
  
- Power BI Desktop  
  
- Dynamics 365 인스턴스  
  
### <a name="connect"></a>연결  
  
1. Power BI Desktop을 시작합니다.  
  
2. 홈 탭에서 **데이터 가져오기**를 선택하고 **자세히**를 선택합니다.  
  
3. 데이터 가져오기 목록에서 **Dynamics 365 Online**을 선택합니다.  
  
4. Dynamics 365 OData 끝점 URL을 입력합니다. *OrganizationName*이 조직의 이름인 이 URL과 유사한 형태이며 버전은 **v8.1**입니다. **확인**을 선택합니다.  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v8.1*  
  
> [!IMPORTANT]
> 다른 끝점 버전에 대한 자세한 내용은 [웹 API URL 및 버전]( https://msdn.microsoft.com/library/gg334391.aspx#bkmk_url_and_versions)을 참조하십시오.
 
> [!TIP]
>  OData 끝점 URL을 찾을 수 있습니다. **설정** > **맞춤화** > **개발자 리소스**로 이동하여 **인스턴스 웹 API** 아래에서 URL을 찾습니다.  
  
5. OData 피드 액세스 대화 상자에서 **조직 계정**를 선택한 다음 **연결**을 선택합니다.  
  
   > [!NOTE]
   >  인스턴스에 로그인되지 않은 경우 연결을 선택하기 전에 OData 피드 액세스 대화 상자에서 **로그인**을 선택합니다.  
  
6. 조직 데이터베이스 엔터티 테이블이 Power BI Desktop 탐색기 창에 표시됩니다. 기본 및 맞춤 엔터티를 선택할 수 있습니다. Power BI Desktop에서 보고서를 만드는 방법에 대한 자세한 내용은 [Power BI 지원: Power BI Desktop에서 보고서 보기](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/)를 참조하십시오.  
  
   ![엔터티 표 선택](media/pbi-select-entity-table.PNG "엔터티 표 선택")  
  
   > [!TIP]
   >  비슷한 단계를 따라 Excel에서 **파워 쿼리** 탭의 **기타 원본**을 선택하면 Excel 파워 쿼리를 사용하여 Dynamics 365에 연결할 수 있습니다.  
  

