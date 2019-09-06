---
title: 솔루션 검사기를 사용하여 PowerApps에서 앱의 유효성 검사 | Microsoft Docs
description: 솔루션 검사기를 사용하여 솔루션의 유효성을 검사합니다.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 07/09/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>솔루션 검사기를 사용하여 PowerApps에서 모델 기반 앱의 유효성 검사

복잡한 비즈니스 요구 사항을 제공하기 위해 모델 기반 앱 제작자는 종종 Common Data Service 플랫폼을 사용자 지정하고 확장하는 고도의 솔루션으로 끝날 수 있습니다. 고급 구현에서는 성능, 안정성 및 안정성 문제가 도입되어 사용자 환경에 부정적인 영향을 줄 수 있는 위험이 증가합니다. 이러한 문제를 해결하는 방법을 확인하고 이해하는 것은 복잡하고 시간이 많이 걸릴 수 있습니다. 솔루션 검사 기능을 사용하면 모범 사례 규칙 세트에 따라 솔루션에 대한 풍부한 정적 분석 검사를 수행하고 이러한 문제 패턴을 신속하게 식별할 수 있습니다. 확인이 완료되면 식별된 문제, 영향을 받는 구성 요소 및 코드, 각 문제를 해결하는 방법을 설명하는 설명서에 대한 링크가 나열된 자세한 보고서를 받게 됩니다.

솔루션 검사에서 이러한 솔루션 구성 요소를 분석합니다. 
- Common Data Service 플러그 인
- Common Data Service 사용자 지정 워크플로 활동 
- Common Data Service 웹 리소스(HTML 및 JavaScript)
- SDK 메시지 단계와 같은 Common Data Service 구성 

솔루션 검사기는 환경에서 내보낼 수 있는 비관리형 솔루션에서 작동합니다. 

> [!NOTE]
> - 이 항목에서는 PowerApps 제조업체 포털에서 솔루션 검사기를 실행하는 방법에 대해 설명합니다. PowerShell 모듈을 사용하여 서비스와 직접 상호 작용할 수도 있습니다. Microsoft.PowerApps.Checker.PowerShell 모듈은 지원되는 버전의 온-프레미스 및 온라인 환경에서 관리되는 솔루션과 관리되지 않는 솔루션을 분석하거나 서비스를 빌드 및 릴리스 파이프 라인에 자동화하고 통합하는 데 사용할 수 있습니다. 추가 정보: [Microsoft.PowerApps.Checker.PowerShell Overview]( /powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) 
> - 솔루션 검사기는 ECMAScript 6(2015) 이상 버전을 사용하는 JavaScript를 포함하는 솔루션에서 작동하지 않습니다. 이러한 버전 중 하나를 사용하는 JavaScript가 검색되면 웹 리소스용 JS001 구문 문제가 보고됩니다.

## <a name="enable-the-solution-checker"></a>솔루션 검사 사용
솔루션 검사기는 모든 Common Data Service 환경에서 기본적으로 활성화되어 있습니다. **솔루션 검사기**메뉴 항목은 PowerApps의 **솔루션** 영역에서 관리되지 않는 솔루션을 선택하면 사용할 수 있습니다. **솔루션 검사기** 메뉴에서 **실행** 옵션을 사용할 수 없는 경우 PowerApps 검사기 솔루션을 설치하여 활성화할 수 있습니다. 이를 설치하려면 다음 단계를 수행합니다.   

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인 하고 솔루션 검사를 사용하도록 설정하려는 Common Data Service 환경을 선택합니다. 
2. 왼쪽 탐색 창에서 **솔루션**을 선택합니다.
3. 도구 모음에서 **솔루션 검사기**를 선택하고 **설치**를 선택하여 Microsoft AppSource 페이지를 엽니다. 브라우저에서 페이지가 열리지 않도록 차단하는 경우 팝업 창을 허용해야 합니다. 

   > [!div class="mx-imgBorder"]
   > ![솔루션 검사기 설치](media/solution-checker-install.png "솔루션 검사기 설치")

4. AppSource 페이지에서 **무료 평가판**을 선택합니다. 

5. 동의하면 이용 약관에 동의하고 환경을 선택하여 PowerApps 검사기 솔루션을 설치합니다. 
6. 설치가 완료되면 PowerApps 사이트에서 **솔루션** 목록을 새로 고쳐 솔루션 검사를 사용할 수 있는지 확인합니다.  
7. 솔루션을 확인 하려면 솔루션 [검사를 실행](#run-the-solution-checker)합니다.


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>솔루션 검사 실행
환경에 PowerApps 검사기를 설치한 후에는 PowerApps의 **솔루션**영역에서 비관리형 솔루션을 선택하면 **솔루션 검사기** 메뉴 항목을 사용할 수 있습니다. 

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다. 
2. 왼쪽 탐색 창에서 **솔루션**을 선택합니다. 
3. 분석하려는 비관리형 솔루션 옆, **...** 을 클릭하고 **솔루션검사기**를 가리킨 다음 **실행**을 선택합니다. 

   > [!div class="mx-imgBorder"]
   > ![솔루션 검사기 명령 실행](media/solution-checker-run.png "솔루션 검사기 명령 실행")

4.  **솔루션** 페이지의 오른쪽 위에 있는 상태 창에는 **솔루션 검사 실행**이 표시 됩니다. 

    > [!div class="mx-imgBorder"]
    > ![솔루션 검사기 상태](media/solution-checker-status.png "솔루션 검사기 상태")
   
    다음을 참고하십시오.
    - 솔루션 검사기에서 분석을 완료하는 데 몇 분 정도 걸릴 수 있습니다. 
    
    - 이 시간 동안 당신은 **실행을 알 수 있습니다...** **솔루션** 목록의 **솔루션 확인** 열에서 상태를 표시합니다. 
    
    - 확인이 완료되면 PowerApps 사이트의 **알림** 영역에 전자 메일 알림 및 알림이 표시 됩니다.  

5.  검사가 완료 되면 [보고서를 봅니다](#review-the-solution-checker-report).

## <a name="cancel-a-check"></a>검사 취소

환경에서 솔루션 검사를 제출한 후에는 **솔루션** 페이지의 오른쪽 상단 영역에 있는 상태 창을 통해 검사를 취소할 수 있습니다. 

검사를 취소 하면 솔루션 검사가 실행을 중지하고 솔루션 확인 상태가 이전 상태로 돌아갑니다. 

## <a name="solution-checker-states"></a>솔루션 검사기 상태
사용자 환경에서 솔루션 검사기를 설치하면 **솔루션 확인** 열이 **솔루션** 목록에 제공됩니다. 이 열에는 솔루션용 솔루션 분석 상태가 표시됩니다. 

|상태  |설명  |
|---------|---------|
|실행 되지 않은    | 솔루션이 분석 된 적이 없습니다.        |
|실행 중     | 솔루션이 분석되고 있습니다.       |
|완료할 수 없습니다.     |  솔루션 분석이 요청되었으나 분석이 성공적으로 완료되지 않았습니다.       |
|*날짜 및 시간*의 결과   | 솔루션 분석을 완료하고 결과를 다운로드할 수 있습니다.      |
|완료할 수 없습니다. *날짜 및 시간*의 결과     | 최신 분석 요청이 성공적으로 완료되지 않았습니다. 마지막으로 성공한 결과를 다운로드할 수 있습니다.         |
|Microsoft에서 확인     | 이것은 Microsoft 관리형 솔루션입니다. 솔루션 분석은 이러한 솔루션에 허용되지 않습니다.         |
|게시자에게 확인     | 타사 관리형 솔루션입니다. 현재 솔루션 분석은 솔루션에 사용할 수 없습니다.        |


## <a name="review-the-solution-checker-report"></a>솔루션 검사 보고서 검토
솔루션 검사가 완료되면 포털에서 분석 보고서를 보거나 웹 브라우저에서 보고서를 다운로드할 수 있습니다. 포털에는 **문제**, **위치** 또는 **심각도**를 기준으로 결과를 필터링하고 그룹화하며 솔루션에서 발견된 문제에 대한 자세한 정보를 보는 옵션이 있습니다. 

1. 왼쪽 탐색 창에서 **솔루션**을 선택합니다.
2. 솔루션 검사기 보고서를 보려는 비관리형 솔루션 옆의 **...** 을 선택합니다. **솔루션 검사기**를 가리킨 다음 **결과 보기**를 선택합니다.  
3. 문제를 선택하여 해결 방법에 대한 세부 사항 및 지침을 봅니다.

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-checker-viewresults.png "솔루션 검사기 보기 결과")

솔루션 검사 결과를 다운로드할 수도 있습니다. 솔루션 검사기 zip 파일은 웹 브라우저에서 지정한 폴더로 다운로드됩니다. 다운로드 보고서는 [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] 형식이며 솔루션에서 감지된 각 문제의 영향, 유형 및 위치를 식별하는 데 도움이 되는 여러 시각화 및 열이 포함되어 있습니다. 이 문제를 해결하는 방법에 대한 자세한 지침에 대한 링크가 제공됩니다. 

1. 왼쪽 탐색 창에서 **솔루션**을 선택합니다.
2. 솔루션 검사기 보고서를 다운로드할 비관리형 솔루션 옆의 **...** 을 선택합니다. **솔루션 검사기**를 가리킨 다음 **결과 다운로드**를 선택합니다.  
3. 솔루션 검사기 zip 파일이 웹 브라우저에서 지정한 폴더로 다운로드 됩니다.

다음은 보고서의 각 열에 대한 요약입니다.

|보고서 필드 |설명  |구성 요소에 적용   |
|---------|---------|---------|
|문제     |   솔루션에서 식별된 문제의 제목입니다.      | 모두        |
|범주     | **성능**, **사용** 또는 **지원 가능성**과 같은 식별된 문제를 분류한 것입니다.      |  모두     |
|심각도     | 식별된 문제의 잠재적 영향을 나타냅니다. 사용 가능한 영향 유형은 **높음**, **보통**, **낮음**, **정보**입니다.         |  모두       |
|지침     |  문제, 영향 및 권장되는 작업을 자세히 설명하는 문서에 연결합니다.       |  모두       |
|구성 요소     |  문제를 해결하는 솔루션 구성 요소입니다.        |   모두      |
|Location     |  어셈블리 또는 JavaScript 파일 이름과 같이 식별된 문제가 발생한 구성 요소의 위치 및/또는 소스 파일입니다.        |  모두       |
|꺾은선형 #     |  영향을 받는 웹 리소스 구성 요소에 있는 문제의 줄 번호 참조입니다.       |  웹 리소스       |
|모듈     | 어셈블리에서 식별된 문제가 발견된 모듈 이름입니다.     |   플러그 인 또는 사용자 지정 워크플로 활동      |
|그런 다음     | 어셈블리에서 식별된 문제의 유형입니다.        | 플러그 인 또는 사용자 지정 워크플로 활동        |
|구성원     |  어셈블리에서 식별된 문제의 구성원입니다.      | 플러그 인 또는 사용자 지정 워크플로 활동        |
|문     | 문제를 일으킨 코드 문 또는 구성입니다.        |  모두       |
|코멘트     | 높은 수준의 해결 단계를 포함하는 문제에 대한 세부 정보입니다.         |  모두       |


## <a name="best-practice-rules-used-by-solution-checker"></a>솔루션 검사기에서 사용하는 모범 사례 규칙

|솔루션 구성 요소  |규칙 이름  |규칙 설명  |
|---------|---------|---------|
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-지정-열](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Customer Engagement 쿼리 APIs용 Dynamics 365을 통해 모든 열을 선택 하지 마십시오.     |
|플러그 인 또는 사용자 지정 워크플로 활동   | [메타 제거 dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | Customer Engagement 플러그인 등록에 대한 중복 Dynamics 365을 피하십시오.     |
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-턴-오프-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Customer Engagement 플러그인에 대한 Dynamics 365에서 외부 호스트와 상호 작용할 때 KeepAlive를 false로 설정합니다.     |
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-방지-unpub-메타 데이터](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | Customer Engagement 메타 데이터에 대해 게시되지 않은 Dynamics 365을 검색하지 마십시오.     |
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-방지-배치 플러그인](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Dynamics 365 Customer Engagement 플러그인 및 워크플로 작업에서 batch 요청 유형을 사용하지 마십시오.    |
|플러그 인 또는 사용자 지정 워크플로 활동   | [메타-방지-reg-no-속성](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Customer Engagement 플러그인 등록에 대한 Dynamics 365와 함께 필터링 특성을 포함합니다.    |
|플러그 인 또는 사용자 지정 워크플로 활동   | [메타-회피-reg-검색](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Customer Engagement 플러그인에 대해 Dynamics 365에 주의하여 검색 및 RetrieveMultiple의 메시지를 등록합니다.    |
|플러그 인 또는 사용자 지정 워크플로 활동   | [메타-제거-비활성](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Customer Engagement를 위해 Dynamics 365에서 비활성 구성을 제거합니다.    |
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-메타-방지-crm2011-depr-메시지](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | Microsoft Dynamics CRM 2011 사용되지 않는 메시지를 사용해서는 안됩니다.     |
|플러그 인 또는 사용자 지정 워크플로 활동   | [메타-방지-crm4-이벤트](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | Microsoft Dynamics CRM 4.0 플러그인 등록 스테이지를 사용하지 마십시오.    |
|플러그 인 또는 사용자 지정 워크플로 활동   | [il-방지-전문화된 업데이트-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | Dynamics 365에서 Customer Engagement를 위해 전문화된 업데이트 작업 요청을 사용하지 마십시오.    | 
| 플러그 인 또는 사용자 지정 워크플로 활동 |  [il-use-autonumber-feature](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-autonumber-feature&client=PAChecker)  |사용자 지정 자동 번호 매기기 솔루션 대신 자동 번호 기능을 사용하십시오. | 
| 플러그 인 또는 사용자 지정 워크플로 활동  | [il-avoid-parallel-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-parallel-plugin&client=PAChecker)  | 병렬 패턴의 사용은 플러그인 내에서 피해야 합니다.  |
| 플러그 인 또는 사용자 지정 워크플로 활동  | [il-avoid-lock-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-lock-plugin&client=PAChecker)  | 플러그 인에서 정적 멤버를 잠그지 마십시오.  |
| 플러그 인 또는 사용자 지정 워크플로 활동  | [meta-avoid-retrievemultiple-annotation](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-retrievemultiple-annotation&client=PAChecker)  | 주석의 RetrieveMultiple에 플러그인을 등록하지 마십시오.  |
|웹 리소스  | [웹-사용-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  비동기적으로 HTTP 및 HTTPS 리소스와 상호작용 합니다.   |
|웹 리소스  | [메타-제거-잘못된 양식-처리기](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | Customer Engagement 양식 이벤트 등록에 대해 잘못된 Dynamics 365을 수정하거나 제거합니다.   |
|웹 리소스  | [메타-분리-고아-양식-요소](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | Customer Engagement 양식 이벤트 등록에 대해 분리된 Dynamics 365을 수정하거나 제거합니다.   |
|웹 리소스  | [웹-방지-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | 모달 대화 상자를 사용하지 마십시오.   |
|웹 리소스  | [웹-방지-crm2011-서비스-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | Microsoft Dynamics CRM 2011 OData 2.0 끝점을 대상으로 지정하지 마십시오.     |
|웹 리소스  | [웹-방지-crm2011-서비스-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | Microsoft Dynamics CRM 2011 SOAP 서비스를 대상으로 지정하지 마십시오.   |
|웹 리소스  | [웹-방지-브라우저-전용-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | Internet Explorer 레거시 API 또는 브라우저 플러그 인을 사용하지 마십시오.   |
|웹 리소스  | [웹-방지-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | 사용되지 않는 Microsoft Dynamics CRM 2011 개체 모델을 사용해서는 안 됩니다.  |
|웹 리소스  | [웹-사용-상대-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | 절대 Common Data Service 끝점 URL을 사용하지 마십시오.    |
|웹 리소스  | [웹-사용-클라이언트-컨텍스트](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | 클라이언트 컨텍스트를 사용하십시오.   |
|웹 리소스  | [웹-사용-대화-api-변수](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | 대화 상자 API 매개 변수를 사용합니다.   |
|웹 리소스  | [웹-사용-조직-설정](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | 조직 설정을 사용하십시오.   |
|웹 리소스  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | grid API를 사용하십시오.    |
|웹 리소스  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Xrm.Utility.isActivityType 매서드를 새로운 Xrm.Utility.getEntityMetadata로 대체하고 리본 규칙에서 사용하지 마십시오.    |
|웹 리소스  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | Silverlight 웹 리소스 사용은 더 이상 사용되지 않습니다.   |
| 웹 리소스  | [web-remove-debug-script](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-remove-debug-script&client=PAChecker)  | 비 개발 환경에서 디버그 스크립트를 포함하지 마십시오.  | 
| 웹 리소스  | [web-use-strict-mode](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-mode&client=PAChecker)  | 가능한 경우 엄격 모드를 사용하십시오.  | 
| 웹 리소스  | [web-use-strict-equality-operators](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-equality-operators&client=PAChecker)  | 완전 항등 연산자를 사용하십시오.  | 
| 웹 리소스  | [web-avoid-eval](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-eval&client=PAChecker)  | 'eval' 함수 또는 해당 기능을 사용하지 마십시오.  | 


### <a name="see-also"></a>참조
[Common Data Service에 대한 모범 사례 및 지침](../../developer/common-data-service/best-practices/index.md)<br />
[모델 기반 앱에 대한 모범 사례 및 지침](../../developer/model-driven-apps/best-practices/index.md)<br />
[솔루션 검사기에 대한 일반적인 문제 및 해결 방법](common-issues-resolutions-solution-checker.md)<br />
