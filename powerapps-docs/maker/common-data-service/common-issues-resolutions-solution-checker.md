---
title: 솔루션 검사기에 대한 일반적인 문제 및 해결 방법 | Microsoft Docs
description: ' 솔루션 검사기 내의 일반적인 문제 및 해결 방법 목록'
keywords: ''
ms.date: 02/11/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>솔루션 검사기에 대한 일반적인 문제 및 해결 방법

이 문서에서는 솔루션 검사기를 사용하는 동안 발생할 수 있는 몇 가지 일반적인 문제를 나열합니다. 해당되는 경우 해결 방법이 제공됩니다.

## <a name="youre-unable-to-use-solution-checker-to-run-analysis-or-download-results"></a>솔루션 검사기를 사용하여 분석 또는 결과 다운로드를 실행할 수 없습니다.

분석 실행 또는 결과 다운로드를 위해 솔루션 검사기 요청을 제출한 직후 작업이 완료되지 않고 다음과 같은 오류 메시지가 표시됩니다.

> *"**[솔루션 이름]** 솔루션에 대한 검사를 실행할 수 없습니다. 다시 실행해 보십시오."*

가능할 때마다 솔루션 검사기는 잠재적 원인 및 해결 단계에 대한 세부 정보 링크가 있는 특정 오류 메시지를 반환하려고 시도합니다. 자세한 내용은 **'자세히 알아보기'** 를 선택하십시오.

![오류 메시지 막대](media/solution-checker-missing-roles-error.png)

분석을 백그라운드에서 처리하는 동안 발생하는 오류는 **'완료할 수 없습니다'** 상태로 실패하고 PowerApps 오류 메시지를 반환하고 요청자에게 전자 메일 알림을 보냅니다. 

![오류 상태](media/solution-checker-exception-status.png)

포털 알림을 선택하면 추가 문제 해결을 위해 일반적인 문제에 대한 이 페이지로 연결됩니다. 제공된 공통 문제점 중 하나가 문제를 해결하지 못하면 참조 번호도 반환됩니다. 추가 조사를 위해 Microsoft 지원부에 이 참조 번호를 제공하십시오.

![실패 알림](media/solution-checker-failure-notification.png)

## <a name="solution-checker-fails-due-to-unsupported-version-of-powerapps-checker"></a>PowerApps 검사기의 지원되지 않는 버전으로 인해 솔루션 검사기가 실패합니다.

솔루션 검사기는 PowerApps 검사기 앱에서 활성화되는 기능입니다.  **1.0.0.47** 이전 버전의 PowerApps 검사기 앱 버전이 설치된 경우 솔루션 검사기 실행이 성공적으로 완료되지 않을 수 있습니다. [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)]에서 PowerApps 검사기 버전을 업그레이드해야 합니다. 

그러나 PowerApps 검사기 버전이 설치된 **1.0.0.45** 버전보다 이전 버전인 경우에는 솔루션을 삭제하고 다시 설치하는 것이 좋습니다. 최근의 스키마 변경으로 인해 **1.0.0.45** 이전 버전의 PowerApps 검사기 업그레이드가 실패할 수 있습니다.

솔루션 검사기의 과거 결과를 유지하려면 이전 실행의 결과를 내보내거나 데이터 [Excel로 데이터 내보내기](../../user/export-data-excel.md)를 사용하여 모든 솔루션 검사기 데이터를 내보내 다음 엔터티에서 데이터를 내보냅니다.

- 분석 구성 요소
- 분석 작업
- 분석 결과
- 분석 결과 세부 정보

### <a name="how-to-uninstall-powerapps-checker"></a>PowerApps 검사기를 제거하는 방법

PowerApps 검사기 솔루션을 제거하려면:

1. 시스템 관리자 또는 시스템 사용자 지정자의 경우 https://web.powerapps.com/environments로 이동하여 PowerApps 포털을 엽니다.
2. **솔루션**을 선택합니다.
3. **PowerApps 검사기**를 선택한 다음 솔루션 도구 모음에서 **삭제**를 선택합니다.

### <a name="how-to-install-powerapps-checker"></a>PowerApps 검사기를 설치하는 방법

Common Data Service 환경에 PowerApps 검사기를 다시 설치하려면:

1. 시스템 관리자 또는 시스템 사용자 지정자의 경우 https://web.powerapps.com/environments로 이동하여 PowerApps 포털을 엽니다.
2. **솔루션**을 선택합니다.
3. 솔루션 도구 모음에서 **솔루션 검사기**를 선택한 다음 **설치**를 선택합니다.

## <a name="solution-checker-cant-access-organizations-in-administration-mode"></a>솔루션 검사기가 관리 모드에서 조직에 액세스할 수 없음

[관리 모드](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-sandbox-instances#administration-mode)에 배치된 조직은 시스템 관리자 및 시스템 사용자 지정자 역할을 가진 사용자에게만 액세스를 의도적으로 제한합니다. PowerApps 검사기 응용 프로그램 ID에는 이러한 역할이 기본적으로 할당되어 있지 않으므로 이 모드로 작동하는 조직에 액세스할 수 없습니다.

이 조직에서 솔루션 검사기를 사용하려면 관리 모드를 사용하지 않아야 합니다.

### <a name="how-to-disable-administration-mode"></a>관리 모드를 비활성화하는 방법

조직 인스턴스에 대한 관리 모드를 비활성화하려면:

1. Dynamics 365 인스턴스 선택기를 엽니다. https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx
2. 솔루션 검사기를 실행하는 데 문제가 있는 조직 인스턴스를 선택합니다.
3. **ADMIN**을 선택합니다.<br/>
![인스턴스 관리자](media/solution-checker-instance-admin.png)

4. **관리 모드 사용** 선택을 취소한 다음 **저장**을 선택합니다.<br/>
![관리 모드 사용 안 함](media/solution-checker-instance-disable-admin-mode.png)

5. 솔루션 검사기를 다시 실행합니다.

## <a name="solution-checker-fails-due-to-missing-security-roles"></a>보안 역할이 누락되어 솔루션 검사기가 실패

솔루션 검사기의 응용 프로그램 사용자는 Common Data Service 조직과 통신하는 데 필요한 권한을 제공하기 위해 할당된 두 가지 보안 역할이 필요합니다. 이러한 역할 중 하나가 사용자 **'PowerApps 검사기'** 에 할당되지 않은 경우 분석 실행, 결과 다운로드 및 취소 실행 시도가 실패합니다. 이는 예기치 않은 사용자로부터 보안 역할을 제거하는 자동화 기능을 고객이 가지고 있는 경우에 가장 자주 발생합니다. 다음 보안 역할에는 최소한의 필요한 사용 권한이 포함되어 있습니다.

- 사용자 지정 항목 내보내기
- 솔루션 검사기

### <a name="how-to-assign-missing-security-roles"></a>누락된 보안 역할을 할당하는 방법

누락된 보안 역할을 PowerApps 검사기 사용자에게 할당하려면:

1. Common Data Service 조직을 열고 **설정** > **보안** > **사용자**로 이동합니다.
2. 사용자 목록에서 **'PowerApps 검사기'** 사용자를 선택합니다.
3. 명령 모음에서 **역할 관리**를 선택합니다.
4. **'사용자 지정 내보내기'** 및 **'솔루션 검사기'** 역할 확인란을 선택한 다음 **확인**을 선택합니다.<br/>
![필요한 보안 역할](media/solution-checker-required-roles.png)

5. 솔루션 검사기를 다시 실행합니다.

## <a name="solution-checker-fails-due-to-restricted-access-mode"></a>제한된 액세스 모드로 인해 솔루션 검사기가 실패합니다.

솔루션 검사기의 응용 프로그램 사용자는 Common Data Service 조직과 통신하기 위해 **'비대화형'** 또는 **'읽기-쓰기'**  액세스 모드가 필요합니다. 액세스 모드가 **'관리'** 와 같은 다른 값으로 변경되면 분석 실행, 결과 다운로드 및 취소 실행 시도가 실패합니다.

이 문제를 해결하려면 **'PowerApps 검사기'** 응용 프로그램 사용자에게 '비대화형' 액세스 모드를 제공합니다.

### <a name="how-to-update-user-access-mode"></a>사용자 액세스 모드를 업데이트하는 방법

PowerApps 검사기 사용자의 액세스 모드를 업데이트하려면:

1. Common Data Service 조직을 열고 **설정** > **보안** > **사용자**로 이동합니다.
2. 사용자 목록에서 **'PowerApps 검사기'** 사용자를 선택하고 두 번 클릭하여 사용자 양식을 엽니다.
3. 양식의 **'관리'** > **'클라이언트 액세스 라이선스(CAL) 정보'** 섹션으로 스크롤합니다.
4. **액세스 모드** 드롭다운 컨트롤에서 **'비대화형'** 을 선택합니다.<br/>
![액세스 모드](media/solution-checker-access-mode.png)

5. 사용자 양식을 저장하고 닫습니다.
6. 솔루션 검사기를 다시 실행합니다.

## <a name="solution-checker-fails-due-to-disabled-first-party-application-in-aad"></a>AAD에서 비활성화된 자사 응용 프로그램으로 인해 솔루션 검사기가 실패

솔루션 검사기(PowerApps-Advisor)에서 사용되는 자사 엔터프라이즈 응용 프로그램 ID는 Azure Active Directory(AAD)에서 비활성화되어야 합니다. 비활성화하는 경우 요청하는 사용자를 대신하여 Common Data Service 및 기타 필수 리소스 공급자에 대한 전달자 토큰을 요청할 때 인증할 수 없습니다. 

아래 단계에 따라 응용 프로그램 ID가 AAD에서 비활성화되어 있지 않은지 확인하고 필요한 경우 응용 프로그램을 활성화하십시오.

### <a name="how-to-verify-andor-modify-application-enabled-status"></a>응용 프로그램 활성화 상태를 확인 및/또는 수정하는 방법

PowerApps-Advisor 엔터프라이즈 응용 프로그램 ID의 활성화 상태를 확인 및/또는 수정하려면

1. [Azure Active Directory (AAD) 포털](https://aad.portal.azure.com/)에서 테넌트에 액세스합니다.
2. **엔터프라이즈 응용 프로그램**으로 이동합니다.
3. **모든 응용 프로그램**을 선택하고 **'PowerApps-Advisor'** 를 검색합니다.<br/>
![PowerApps-Advisor 앱 검색](media/solution-checker-search-advisor-app.png)

4. **'PowerApps-Advisor'** 를 선택하여 앱 세부 정보를 봅니다.
5. **속성**을 선택합니다.
6. **사용자가 로그인할 수 있도록 설정** 상태를 확인합니다. **'아니요'** 인 경우 응용 프로그램이 비활성화된 것입니다.<br/>
![비활성화된 엔터프라이즈 앱](media/solution-checker-disabled-app.png)

7. 값을 **'예'** 로 전환할 라디오 컨트롤을 선택합니다. 이렇게 하면 응용 프로그램을 사용할 수 있습니다.<br/>
![PowerApps-Advisor 사용](media/solution-checker-enable-app.png)

8. **저장**을 선택합니다. 응용 프로그램이 이제 활성화됩니다. 변경 사항이 적용되려면 몇 분 정도 기다려야 할 수 있습니다.
9. 솔루션 검사기를 다시 실행합니다.

> [!IMPORTANT]
> 엔터프라이즈 응용 프로그램을 편집하려면 Azure Active Directory(AAD)의 관리자 권한이 있어야 합니다.

## <a name="solution-checker-fails-to-export-solutions-with-draft-business-process-flow-components"></a>솔루션 검사기가 초안 비즈니스 프로세스 흐름 구성 요소를 사용하여 솔루션을 내보낼 수 없습니다.

솔루션에 이전에 활성화된 적이 없는 초안 상태의 비즈니스 프로세스 흐름 구성 요소가 포함되어 있으면 솔루션 검사기가 분석을 위해 솔루션을 내보내는 데 실패합니다. 이 오류는 솔루션 검사기에 고유하지 않으며 비즈니스 프로세스 흐름이 처음 활성화될 때까지 생성되지 않는 백업(사용자 지정) 엔터티 구성 요소에 대한 종속성이 있는 비즈니스 프로세스 흐름으로 인해 발생합니다. 이 문제는 솔루션 탐색기에서 비즈니스 프로세스 흐름을 활성화한 경우에도 발생할 수 있습니다.

문제 및 해결 단계에 대한 자세한 내용은 참조 [참조 자료 문서 #4337537: 잘못된 내보내기 - 비즈니스 프로세스 개체 누락](https://support.microsoft.com/en-hk/help/4337537/invalid-export-business-process-entity-missing)을 참조하십시오.

## <a name="solution-checker-fails-to-export-patched-solutions"></a>솔루션 검사기가 패치된 솔루션을 내보낼 수 없습니다.

솔루션에 [패치](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates)가 적용된 경우 솔루션 검사기에서 분석을 위해 솔루션을 내보내지 못합니다. 솔루션에서 패치를 적용하면 원래 솔루션은 잠기게 되며 솔루션을 상위 솔루션으로 식별하는 종속 패치가 조직에 존재하는 경우 패치를 변경하거나 내보낼 수 없습니다.

이 문제를 해결하려면 솔루션에 관련된 모든 패치가 새로 만든 솔루션으로 롤백되도록 솔루션을 복제합니다. 이렇게 하면 솔루션의 잠금이 해제되고 시스템에서 솔루션을 내보낼 수 있습니다.  자세한 내용은 [솔루션 복제](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)를 참조하십시오.

## <a name="solution-checker-will-not-analyze-empty-solutions"></a>솔루션 검사기가 빈 솔루션을 분석하지 않음

솔루션 검사기가 분석할 구성 요소가 없는 솔루션을 내보내면 추가 처리가 종료되고 실행 실패로 간주됩니다. 솔루션 검사기 분석을 위해 제출된 선택한 솔루션에 하나 이상의 구성 요소가 포함되어 있는지 확인하십시오.

## <a name="solution-checker-fails-to-export-large-solutions"></a>솔루션 검사기가 대규모 솔루션을 내보낼 수 없습니다

Common Data Service 환경에서 대규모 솔루션을 내보낼 수 없는 경우의 기본 시나리오에는 내보내기 요청에 대한 시간 초과 예외가 포함됩니다. 요청이 20분을 초과하는 경우 발생합니다. 기본 솔루션과 같은 대형 솔루션은 이 시간 프레임 내에 내보내지 못할 수 있으며 검사는 성공적으로 완료되지 않습니다. 솔루션 검사기에 내보내는 동안 시간 초과가 발생하는 경우 작업 처리에 실패하기 전에 세 번 재시도하므로 실패 알림을 받기 전에 1시간 이상이 걸릴 수 있습니다.

해결 방법은 분석할 구성 요소가 적을수록 더 작은 솔루션을 만드는 것입니다. 솔루션의 큰 파일 크기가 많은 플러그 인 어셈블리 구성 요소로 인한 경우 [사용자 지정 어셈블리 개발을 최적화](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md)하기 위한 지침을 참조하십시오. 

> [!IMPORTANT]
> 가양성을 최소화하려면 종속 사용자 지정을 추가해야 합니다. 솔루션을 만들고 이러한 구성 요소를 추가하는 경우 다음을 포함합니다.
> - 플러그 인을 추가할 때 플러그 인에 대한 SDK 메시지 처리 단계를 포함합니다.
> - 엔터티 양식을 추가할 때 양식 이벤트에 연결된 JavaScript 웹 리소스를 포함합니다.  
> - JavaScript 웹 리소스를 추가하는 경우 모든 종속 JavaScript 웹 리소스를 포함합니다.
> - HTML 웹 리소스를 추가할 때 HTML 웹 리소스 내에 정의된 모든 종속 스크립트를 포함합니다.
> - 사용자 지정 워크플로를 추가할 때 워크플로 내에서 사용되는 어셈블리를 포함합니다.

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>포함 된 JavaScript가 있는 HTML 리소스의 문제에 대한 줄 번호 참조가 올바르지 않습니다. 

HTML 웹 리소스가 솔루션 검사기 내에서 처리되면 HTML 웹 리소스는 HTML 웹 리소스 내에서 JavaScript와 별도로 처리됩니다. 이로 인해 HTML 웹 리소스의 `<script>` 내에서 발견된 위반의 줄 번호가 올바르지 않습니다.

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>웹 리소스에 대한 웹 지원되지 않는 구문 문제

ECMAScript 6 (2015) 이상 버전은 현재 솔루션 검사기에 지원되지 않습니다. 솔루션 검사기가 ECMAScript 6 이상을 사용하여 JavaScript를 분석하는 경우 웹 리소스에 대한 웹 지원 구문 문제가 보고됩니다.  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>호출 범위를 기반으로 하는 플러그 인 및 워크플로 활동에 대해 여러 가지 위반이 보고됨

문제는 호출 컨텍스트에만 관련된 플러그 인 및 워크플로 작업 규칙의 경우 솔루션 검사기 도구는 IPlugin 인터페이스 구현에서 분석을 시작하고 호출 그래프를 트래버스하여 해당 구현의 범위 내에서 문제를 검색합니다. .  경우에 따라 많은 호출 경로가 문제가 발견되는 동일한 위치에 도착할 수 있습니다.  이 문제는 호출 범위와 관련이 있으므로 이 도구는 해당 범위를 기반으로 보고할 수 있으므로 별개의 위치보다 더 나은 영향을 제공합니다. 결과적으로 여러 문제를 해결해야 하는 단일 위치를 참조할 수 있습니다.

## <a name="see-also"></a>참조
[Common Data Service에 대한 모범 사례 및 지침](../../developer/common-data-service/best-practices/index.md)<br/>
[모델 기반 앱에 대한 모범 사례 및 지침](../../developer/model-driven-apps/best-practices/index.md)<br/>
