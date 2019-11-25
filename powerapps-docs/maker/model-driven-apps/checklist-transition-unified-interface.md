---
title: '검사 목록: 통합 인터페이스 전환 | MicrosoftDocs'
description: 통합 인터페이스로 전환할 준비가 되었는지 점검할 검사 목록입니다.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03b3db348ff88b7fd2c5e89e2b94a7d16a1fee17
ms.sourcegitcommit: bcaffcb3135251ea3c2e828f8b59926d19520bec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761823"
---
# <a name="checklist-unified-interface-transition"></a>검사 목록: 통합 인터페이스 전환

이 문서의 단계를 따라 통합 인터페이스로 전환할 준비가 되었는지 점검합니다. 통합 인터페이스로 전환하기 위한 준비는 기본 호환성을 목표로 하는지 또는 새로운 기능을 최대한 활용하도록 재설계할지에 따라 달라집니다. 자세한 내용은 [통합 인터페이스 플레이북](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook)과 [사용자 환경 백서](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface)를 참조하십시오.

지침은 Dynamics 365의 다음 모델 기반 앱에 적용됩니다.

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-powerapps-solution-checker-on-your-solutions"></a>솔루션에서 PowerApps 솔루션 검사기 실행

[PowerApps 솔루션 검사기](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker)는 모범 사례 규칙 세트에 따라 솔루션에 대해 풍부한 정적 분석 검사를 수행하여 이러한 문제 패턴을 신속하게 식별합니다. 확인이 완료되면 식별된 문제, 영향을 받는 구성 요소 및 코드, 각 문제를 해결하는 방법을 설명하는 설명서에 대한 링크가 나열된 자세한 보고서를 받게 됩니다.

솔루션 검사에서 이러한 솔루션 구성 요소를 분석합니다.

-   Common Data Service 플러그 인

-   Common Data Service 사용자 지정 워크플로 활동

-   Common Data Service 웹 리소스(HTML 및 JavaScript)

-   SDK 메시지 단계와 같은 Common Data Service 구성

**고려해야 할 사항** 

-   솔루션 검사기가 감지한 잠재적 문제는 통합 인터페이스에만 적용되지 않을 수 있습니다. 결과를 검토할 때 전환에 영향을 미치는 요소를 염두에 두십시오.

-   자동화된 코드 검토에서와 같이 일부 문제는 잘못된 경보일 수 있으며 애플리케이션이 통합 인터페이스에서 실행되지 않는다는 의미는 아닙니다.

-   플러그 인, 사용자 지정 워크플로 활동 및 SDK 메시지 단계 구성과 같이 서버 측에서 실행되는 논리는 사용자 인터페이스에 영향을 미치지 않아야 하므로 통합 인터페이스로의 전환에 영향을 미치지 않아야 합니다.

-   모든 문제가 통합 인터페이스와 직접 연결되어 있지 않더라도 애플리케이션의 전반적인 상태를 개선하기 위해 문제를 검토하는 데 시간을 할애하는 것이 좋습니다.

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>통합 인터페이스와의 타사 솔루션 호환성 확인


통합 인터페이스로 전환하기 전에 애플리케이션에서 사용하는 타사 솔루션이 통합 인터페이스에서 작동하는지 확인하는 것이 중요합니다.

-   [AppSource](https://appsource.microsoft.com)를 통해 ISV(독립 소프트웨어 벤더) 추가 기능을 설치한 경우 **환경** > [환경_이름] > **솔루션 관리**를 선택하여 [Power Platform 관리 센터](https://admin.powerplatform.microsoft.com)에서 업그레이드가 가능한지 확인하십시오.

-   AppSource 외부에서 제공되는 타사 솔루션을 사용하는 경우 앱을 통합 인터페이스로 업데이트하는 새 버전을 받으려면 공급업체(파트너 또는 ISV)에 문의하십시오.

> [!NOTE]
> 타사 솔루션을 통합 인터페이스와 호환되는 버전으로 업데이트할 계획이 없는 경우 이러한 기능을 기본 플랫폼 기능 또는 호환되는 대체 솔루션으로 대체할 경로를 파악해야 합니다.

## <a name="identify-replacements-for-deprecated-client-api-code-and-features"></a>더 이상 사용되지 않는 클라이언트 API 코드 및 기능에 대한 대체 경로 파악

**PowerApps 솔루션 검사기**의 출력 및 더 이상 사용되지 않는 클라이언트 API 및 기능에 있는 [중요한 변경 사항(더 이상 사용되지 않음)](https://docs.microsoft.com/power-platform/important-changes-coming)에 포함된 정보를 기반으로 통합 인터페이스 프로젝트에서 수정하거나 교체해야 하는 사용자 지정 및 기능에 대해 잘 이해하고 있어야 합니다.

주의해야 할 가장 일반적인 영역은 다음과 같습니다.

-   **클라이언트 API**: 권장 교체 방법이 [여기](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated)에 문서화되어 있습니다.

-   **프로세스 대화 상자**: 대화 상자의 권장 대체 경로가 [여기](https://docs.microsoft.com/flow/replace-dialogs)에 문서화되어 있습니다.

-   **작업 흐름**: [비즈니스 프로세스 흐름](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences)을 사용하여 작업 흐름을 대체하는 것을 고려하십시오.

-   **서비스 일정**: [Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling)을 사용하여 레거시 서비스 스케줄링을 대체하는 것을 고려하십시오.

> [!NOTE]
> Dynamics 365 for Outlook(COM 추가 기능)을 경량 [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview)으로 교체하는 것을 고려할 수도 있습니다.

## <a name="test-your-application-in-unified-interface"></a>통합 인터페이스에서 애플리케이션 테스트

통합 인터페이스에서 애플리케이션을 테스트하는 가장 쉬운 방법 중 하나는 프로덕션 환경의 사본에서 [**통합 인터페이스만 활성화**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) 옵션만 켜는 것입니다. 통합 인터페이스가 활성화된 후 **Dynamics 365 – 사용자 지정** 앱을 사용하여 애플리케이션에 액세스하고 상황에 맞는 사용 사례를 테스트할 수 있어야 합니다.

### <a name="test-your-business-and-technical-scenarios"></a>비즈니스 및 기술 시나리오 테스트

잠재적으로 영향을 받을 수 있는 사항에 집중하십시오.

-   비즈니스 프로세스 흐름, 비즈니스 규칙 등의 **비즈니스 프로세스**

-   양식, 보기, 명령 모음 단추, 웹 리소스 및 차트와 같은 **사용자 지정**

> [!TIP]
> 이러한 초기 테스트를 수행하는 것과 동시에 사용자 경험에 도전하십시오. 모든 것이 의미가 있고 가치를 추가합니까? 무엇을 제거/개선/추가해야 합니까? 예를 들어, 현재 보기 목록이 관련이 있습니까? 또는 사용자가 자신의 보기를 생성해야 합니까?

### <a name="identify-gaps"></a>격차 파악

-   솔루션 검사기 및 타사 솔루션 업데이트에서 아직 발견하지 못한 잠재적인 회귀.

-   최적화(섹션 및 탭을 재구성하여 새 양식 렌더링) 또는 특정 교육으로 이어질 수 있는 사용자 문제점.

-   경량 Dynamics 365 App for Outlook 대신 기존 Outlook COM 추가 기능을 사용하는 등 기존 웹 클라이언트에 대한 기타 종속성.

## <a name="define-your-app-strategy-and-settings"></a>앱 전략 및 설정 정의

통합 인터페이스에 최적화되어 있지 않아 호환성 모드에서 실행되는 **Dynamics 365 – 사용자 지정** 앱을 사용하는 대신 Microsoft에서 만든 자사 앱을 사용하거나 자체 앱을 만드는 것이 좋습니다.

통합 인터페이스에 대해 이미 최적화된 Dynamics 365 자사 앱은 다음과 같습니다.

-   Dynamics 365 영업 허브

-   Dynamics 365 고객 서비스 허브

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service(버전 8.x 이상)

-   Dynamics 365 Project Service Automation(버전 3.x 이상)

### <a name="what-are-model-driven-apps"></a>모델 기반 앱이란 무엇입니까?

**모델 기반 앱**은 PowerApps를 사용하여 만들 수 있는 앱 유형입니다. 이를 통해 조직에서의 역할에 따라 사용자에게 맞춤형 경험을 제공할 수 있습니다. 예를 들어, 영업 직원은 동일한 환경의 데이터를 사용하더라도 서로 다른 모델 기반 앱을 통해 고객 지원 담당자와는 완전히 다른 경험을 가질 수 있습니다. Common Data Service 환경에서 여러 모델 기반 앱을 만들 수 있습니다. 추가 정보: [모델 기반 앱이란 무엇입니까?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

위에 나열된 Dynamics 365 자사 앱은 모델 기반 앱의 예입니다.

### <a name="how-to-define-your-app-strategy"></a>앱 전략을 정의하는 방법은 무엇입니까?

다음 질문 사항에 대한 답을 준비합니다.

1.  특정 비즈니스 프로세스로 사용자를 여러 그룹으로 나눌 수 있습니까?

2.  이러한 그룹은 표시하고 수행해야 하는 사항에 대해 다른 요구 사항을 가지고 있습니까?

3.  앱을 사용하지 않고 다른 사용자 환경을 보유하기가 어렵습니까?

이 질문에 "예"라고 대답한 경우 여러 앱을 사용하는 것이 좋습니다.

이것은 각 그룹이나 역할에 대한 비즈니스 프로세스의 맥락에서 경험을 다시 생각할 수 있는 기회입니다.

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>기본 제공 앱(예: 영업 허브) 또는 사용자 지정 앱을 사용해야 합니까?

-   그것은 경험을 얼마나 맞춤화할 것인지에 달려 있습니다.

-   사용자 지정이 거의 없거나 자사 앱 업데이트의 이점을 얻으려면 기본 앱 사용을 고려하십시오.

-   표준 앱 및 사용자 지정의 경험과 업데이트를 보다 강력하게 제어하려면 고유한 앱을 만드십시오.

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>앱 전략을 정의한 후 다음 단계는 무엇입니까?

1.  대상 앱을 사용자 지정하고 사용자에게 필요한 항목만 포함하십시오. 적을수록 좋습니다. 사용자가 효율적으로 작업할 수 있도록 불필요한 것들을 줄입니다.

2.  사용하지 않는 앱에서 보안 역할을 분리합니다.

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>앱 설정 및 사용자 환경 기본 사항 검토

### <a name="app-settings"></a>앱 설정

-   사이트 맵에 없는 경우에도 앱에 필요한 모든 엔터티를 포함합니다.  
    
-   **보안 역할** 대화 상자의 **사용자 지정** 탭에서 **모델 기반 앱**에 **읽기** 권한을 제공합니다.

-   사용자가 레거시 웹 클라이언트를 사용할 필요가 없는 경우 **통합 인터페이스만 해당** 모드를 활성화합니다. **설정** > **고급 설정**을 선택하여 관리 기능에 계속 액세스할 수 있습니다.

-   보다 단순한 앱 URL을 만듭니다. 예: https://\*.crm.dynamics.com/apps/MyApp*

-   사용자가 액세스할 수 있는 앱 수를 제한하십시오.  
    
    > [!TIP]
    > **통합 인터페이스만 사용**이 **예**로 설정되고 사용자가 하나의 앱에만 액세스할 수 있는 경우 루트 URL(https://\*.crm.dynamics.com)*에 액세스하면 자동으로 앱으로 리디렉션됩니다.

### <a name="optimize-navigation-sitemap"></a>탐색 최적화(사이트 맵)

-   하나의 기본 **영역**을 **그룹**에서 구성된 가장 많이 사용된 **하위 지역**(대시보드, 엔터티 등)으로 정의

-   덜 사용되는 기능(구성, 설정 등)에 대해 하나 이상의 추가 영역을 만듭니다. 아이디어는 사용자가 업무 수행에서 중요한 것에 집중할 수 있도록 돕는 것입니다.

### <a name="update-icons"></a>아이콘 업데이트

-   통합 인터페이스로 전환하면 아이콘을 새로 고칠 수 있습니다.

-   화면 해상도에 관계없이 잘 렌더링되는 **SVG** 형식이 좋습니다.

    > [!TIP]
    > SVG 아이콘 형식의 예:  
    > 너비와 높이: 16px; 패딩: 0px; 배경: 투명; 아이콘 색상: \#FF000000  
    렌더링 문제를 피하려면 편집기(예: 메모장)로 SVG 파일을 열고 fill"=\#000000"를 제거하십시오.

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>통합 인터페이스 독점 기능으로 앱을 풍부하게

-   사용자가 각 앱에 액세스할 때 보게 될 **시작 페이지**를 만드세요. 이는 첫 단계에서 사용자를 안내할 수 있는 좋은 기회입니다.

-   기존 **사용자 지정 컨트롤**을 사용하여 대부분의 필드 유형, 특히 모바일에서 유용성을 향상시킬 수 있습니다. 예를 들어, 0~5 필드 등급을 별표로 바꾸고, 약속 보기를 일정 보기로 바꾸고, 하위 표 보기를 카드 양식으로 바꿉니다.

-   양식에서 **참조 패널**을 활용하여 여러 보기, 빠른 보기, 참조 자료 검색 기능을 한곳에 묶을 수 있습니다.

-   [PowerApps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview)를 활용하여 더 많은 사용자 지정 컨트롤을 추가합니다. 커뮤니티나 파트너 및 ISV로부터 일부를 얻을 수 있습니다.

-   양식에 [캔버스 앱](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started)을 포함하여 애플리케이션을 쉽게 확장할 수 있습니다. 사용자 지정 HTML/JS 웹 리소스를 개발할 필요 없이 코드 없는 또는 거의 없는 앱 확장이 가능합니다.

-   양식에 **Power BI** 보고서 및 타일을 포함하여 여러 시스템의 데이터를 단일 보기로 통합할 수 있습니다.

-   **대화형 대시보드**를 활용하여 대시보드 구성 요소에 글로벌 필터링을 허용하는 원스톱 작업 환경을 구성하는 것을 고려해 보십시오.

-   사용자가 신속하게 도움과 안내를 받을 수 있도록 **사용자 지정 도움말 창 및 단계별 작업**을 구성합니다.

## <a name="conduct-user-acceptance-testing"></a>사용자 승인 테스트 수행

프로덕션 환경과 유사한 조건에서 통합 인터페이스의 비즈니스 사용자가 애플리케이션, 비즈니스 시나리오 및 기술 시나리오를 테스트하는 것이 매우 중요합니다. 이러한 사용자는 비즈니스 챔피언 역할을 하여 비즈니스 전반에 걸쳐 지식을 확장할 수 있습니다.

테스트는 모든 사용자를 통합 인터페이스로 전환하기 전에 해결해야 할 나머지 항목을 식별하는 데 도움이 됩니다.

## <a name="update-user-training-materials"></a>사용자 학습 자료 업데이트

기존 및 계획된 학습 자료를 검토하여 최신 스크린샷이 있는지 확인하고 사용자 흐름에 대한 변경 사항을 반영하십시오.

## <a name="check-your-transition-date"></a>전환 날짜 확인

2020년 10월 1일자로 [레거시 웹 클라이언트를 더 이상 사용할 수 없습니다](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated).
문제가 해결될 시간을 확보하기 위해 미리 마이그레이션해야 합니다.
