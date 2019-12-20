---
title: Power Apps 포털의 릴리스 업데이트 | MicrosoftDocs
description: Power Apps 포털의 릴리스 업데이트에 대해 알아보기 .
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: bbdc9a775c4bfaacc6f99217f6f24ce32db06bca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884480"
---
# <a name="release-updates"></a>릴리스 업데이트

이 항목은 최근 릴리스된 새로운 기능과 향후 몇 개월 동안 릴리스될 새로운 기능에 대해 알아볼 수 있는 리소스를 제공합니다.

## <a name="power-apps-portals-updates"></a>Power Apps 포털 업데이트

계획에 사용할 수 있는 향후 몇 개월 동안 릴리스되는 새로운 기능에 대한 자세한 내용은 다음을 참조하십시오.

- [2019 릴리스 웨이브 2 계획](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>이전 포털 업데이트

다음은 Dynamics 365 포털에 추가된 기능 목록입니다. Dynamics 365 포털 업데이트에 대한 자세한 내용은 [Microsoft Dynamics 365 릴리스의 포털 기능](https://support.microsoft.com/help/3181191)을 참조하십시오.

> [!NOTE]
> Power Apps 포털은 이전에 Dynamics 365 포털로 알려졌습니다.

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.1.4

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.1.4는 다음과 같은 새로운 업데이트 및 기능을 제공합니다.

- **포털의 유지 관리 모드**: 포털 관리자는 이제 유지 관리 작업이 진행 중일 때(예: 솔루션 패키지를 업그레이드하는 경우) 고객에게 적절한 메시지를 표시하도록 포털을 구성할 수 있습니다. 자세한 내용: [포털의 유지 관리 모드](admin/enable-maintenance-mode.md)

- **Power BI Embedded 서비스 사용**: 포털 사용자 지정자는 이제 Power BI Embedded 서비스를 활성화하여 Power BI의 새 작업 영역에서 만든 대시보드와 보고서를 포함할 수 있습니다. 대시보드 및 보고서는 powerbi 유동 태그를 사용하여 포털의 웹 페이지에 포함됩니다. 추가 정보: [Power BI 통합 설정](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)

- **아이디어에 대한 콘텐츠 조정 활성화**: 포털 관리자는 이제 포털에 제출된 아이디어를 조정하는 콘텐츠 조정 정책을 만들 수 있습니다.

- **OAuth 2.0 암시적 권한 부여 흐름**: 포털 개발자는 이제 외부 API에 대한 클라이언트 쪽 API 호출을 만들고 OAuth 2.0 암시적 권한 부여 흐름을 사용하여 보안을 확보할 수 있습니다. 자세한 내용: [OAuth 2.0 암시적 권한 부여 흐름](oauth-implicit-grant-flow.md)

- **Common Data Service 시작 포털(미리 보기)**: 포털 관리자는 이제 Common Data Service 환경에 연결하고 사용자가 상호 작용할 수 있도록 포털을 구성할 수 있습니다. 이 기능은 사전 설치된 Dynamics 365(Dynamics 365 Sales,Dynamics 365 Service 또는 Dynamics 365 Marketing)이 없는 Common Data Service 환경에 포털을 연결하는 기능을 제공합니다.

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.1.1

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.1.1은 다음과 같은 새로운 업데이트 및 기능을 제공합니다.

- **포털 검사기**: 이제 포털 검사기를 사용하여 다양한 구성 매개 변수를 확인하여 포털과 관련된 문제를 식별하고 이를 해결하는 방법에 대한 제안을 제공할 수 있습니다. 추가 정보: [포털 검사기](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.0.10

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.0.10은 다음과 같은 새로운 업데이트 및 기능을 제공합니다.

- **Dynamics 365 포털 구성**: 이제 개발에서 테스트 또는 프로덕션 환경으로 Dynamics 365 포털 구성을 마이그레이션할 수 있습니다. 마이그레이션은 소스 Dynamics 365 인스턴스에서 기존 구성을 내보낸 다음 대상 Dynamics 365 인스턴스로 가져오는 것을 포함합니다. 구성 데이터를 마이그레이션하려면 구성 마이그레이션 도구와 포털별 구성 스키마 파일을 사용해야 합니다. 추가 정보: [Dynamics 365 포털 구성 마이그레이션](admin/migrate-portal-configuration.md)

- **Power BI 시각화 추가**: 포털 사용자 지정자는 이제 powerbi 유동 태그를 사용하여 포털의 웹 페이지에 Power BI 시각화(대시보드, 보고서 및 타일)를 포함할 수 있습니다. 추가 정보: [Power BI 통합 설정](admin/set-up-power-bi-integration.md)

- **IP 주소로 포털 액세스 제한**: 포털 관리자는 이제 포털에 액세스할 수 있는 IP 주소 목록을 정의할 수 있습니다. 포털에 대한 요청이 사용자로부터 생성되면 해당 IP 주소가 허용 목록과 비교하여 평가됩니다. IP 주소가 목록에 없으면 포털에 HTTP 403 상태 코드가 포함된 웹 페이지가 표시됩니다. 추가 정보: [IP 주소로 포털 액세스 제한](admin/ip-address-restrict.md)

- **SharePoint 문서 관리**: 이제 Dynamics 365 포털에서는 포털의 엔터티 양식 또는 웹 양식의 SharePoint에서 직접 문서를 업로드하고 표시하는 기능을 지원합니다. 이를 통해 포털 사용자는 포털에서 문서를 보고, 다운로드하고, 추가하고, 삭제할 수 있습니다. 포털 사용자는 문서를 구성하는 폴더를 만들 수도 있습니다. 추가 정보: [SharePoint 문서 관리](manage-sharepoint-documents.md)

- **새로운 포털 콘텐츠 편집기(미리 보기)**: 이 미리 보기에서는 Dynamics 365 포털 사용자 지정에 대한 학습 곡선을 줄이고 사용자 지정자의 생산성을 향상시키는 데 도움이 되는 새롭고 간소화된 포털 편집기를 Dynamics 365 포털 사용자 지정자에서 사용할 수 있습니다.

- **상태 설명에 대해 투표 활성화**: 기본적으로 상태 설명이 신규로 설정된 경우에만 아이디어의 투표가 활성화됩니다. 이제 다양한 상태 이유에 대해 아이디어에 대한 투표를 활성화할 수 있습니다. 다양한 상태 설명에 대한 투표를 활성화하려면 Ideas/EnableVotingForStatusReasons 사이트 설정을 만들고 해당 값을 필요한 상태 설명 값으로 설정해야 합니다. 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.0.6

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 9.0.6은 다음과 같은 최신 업데이트 및 기능을 제공합니다.

- **Dynamics 365 포털 앱**: Dynamics 365 포털 앱은 고객과 통신하고 공동 작업하기 위해 온라인 플랫폼을 구성하고 관리하는 새로운 환경을 제공합니다. Dynamics 365 포털 버전 9.0 이상을 설치하면 통합 인터페이스 프레임워크에 구축된 Dynamics 365 포털 앱이 즉시 생성됩니다.

- **포털 다시 설정**: 이제 다른 지리적 위치 또는 다른 테넌트로 이동하려는 경우 및 포털을 더 이상 사용하지 않으려는 경우 포털을 다시 설정할 수 있습니다. 포털을 다시 설정하면 포털의 호스트된 리소스가 삭제되고 포탈 URL에 액세스할 수 없습니다. 추가 정보: [포털 다시 설정](admin/reset-portal.md)

- **포털의 기본 URL 변경**: 이제 포털이 프로비저닝된 후에 포털의 기본 URL을 변경할 수 있습니다. 예를 들어 포털을 프로비저닝하는 동안 기본 URL로 contosocommunity.microsoftcrmportals.com을 선택한 경우 나중에 요구 사항에 따라 contosocommunityportal.microsoftcrmportals.com으로 변경할 수 있습니다. 추가 정보: [기본 URL 변경](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.4.1

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.4.1은 다음과 같은 기능을 비롯하여 많은 버그 수정뿐만 아니라 성능 향상 기능도 제공합니다.

- **참조 자료 및 웹 파일의 첨부 파일 내용 내에서 검색**: 이제 참조 자료 및 웹 파일의 첨부 파일 내용을 검색하여 관련 검색 결과의 가능성을 높일 수 있습니다. 추가 정보: [첨부 파일 콘텐츠 내에서 검색](configure/search-file-attachment.md)
- **접근성**: 기본 제공 포털(커뮤니티 포털, 파트너 포털, 고객 포털, 직원 셀프 서비스 포털)에 액세스할 수 있습니다. 그러나 사용자 지정 프로그램은 사용자 지정 또는 변경 후에도 포털에 계속 액세스할 수 있도록 해야 합니다.


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.4

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.4는 다음과 같은 기능을 비롯하여 많은 버그 수정뿐만 아니라 성능 향상 기능도 제공합니다.

- **포털 액세스 오류 로그**: 포털 개발자는 이제 포털의 모든 문제에 대한 자세한 오류 로그에 액세스할 수 있습니다. 이렇게 하면 포털을 개발하는 동안 문제를 디버깅할 수 있습니다. 포털이 활성화되면 사용자가 소유한 Azure Blob 저장소 계정으로 모든 응용 프로그램 오류를 보내도록 포털을 구성할 수 있습니다. 이렇게 하면 고객이 보고한 문제를 디버깅하는 데 도움이 됩니다. 추가 정보: [포털 액세스 오류 로그](admin/view-portal-error-log.md)
- **포털 인증 키 갱신**: 포털은 Azure Active Directory 응용 프로그램을 사용하여 Common Data Service 환경에 연결합니다. 이를 위해 Azure Active Directory 응용 프로그램에 연결된 인증 키가 필요합니다. 이 키는 포털을 프로비전할 때 추가되며 2년마다 갱신해야 합니다. 이 버전의 포털은 관리자가 키 만료에 대한 알림을 받고 Power Apps 포털 관리 센터에서 이 키를 갱신할 수 있는 기능을 제공합니다. 추가 정보: [포털 인증 키 갱신](admin/manage-auth-key.md)
- **포털에서 일반 데이터 보호 규칙 구현**: 포털 관리자는 이제 GDPR 표준을 충족하도록 포털을 구성할 수 있습니다. 또한 포털 사용자가 포털을 사용하도록 동의 해야 하는 특정 사용 약관을 제공할 수 있습니다. 또한 미성년 사용자가 포털에 액세스하는 경우, 사용자가 포털에 액세스하려면 부모의 동의가 있어야 하는 등 같은 검사를 설정할 수 있습니다. GDPR을 구현하면 사용자의 개인 데이터 사용에 대한 포털 사용자들의 동의를 얻고 미성년자 사용자를 식별하고 자녀에 대한 부모의 동의를 얻을 수 있습니다. 추가 정보: [포털에서 GDPR 구현](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.3

Dynamics 365의 모델 기반 앱용 Dynamics 365 포털 버전 8.3은 다음과 같은 많은 새로운 업데이트 및 기능을 제공합니다.

- **참조 문서에 첨부 파일을 포함할 수 있는 기능**: 포털의 참조 문서와 함께 메모 첨부 파일을 표시할 수 있습니다. 이 기능을 활성화하려면 KnowledgeManagement/DisplayNotes 사이트 설정을 만들어 그 값을 **true**로 설정해야 합니다. 포털 사용자는 이러한 첨부 파일을 검색할 수도 있습니다. 추가 정보: 참조 문서와 함께 첨부 파일 표시

  > [!Note]
  > 첨부 파일을 검색하는 것은 메모 설명 및 첨부 파일 이름에서만 가능합니다. 첨부 파일의 콘텐츠는 검색할 수 없습니다.
  
- **포털에 엔터티를 추가하기 위한 관리 마법사**: 이 기능은 포털의 데이터를 쉽게 노출하는 새 관리 마법사를 도입합니다. 마법사를 통해 만든 엔터티는 사용자가 선택한 보안 및 사용 권한 모델에 근거하여 조직의 데이터를 가져와 포털 고객에게 제공되는 하위 집합을 만듭니다.

- **메타데이터 변환 가져오기**: 이 기능을 사용하면 포털을 설치한 후 새로 활성화된 언어의 메타데이터 변환을 가져올 수 있습니다. 추가 정보: [메타데이터 변환 가져오기](admin/import-metadata-translation.md)

- **포털에 대한 소스 코드 가용성**: 개발자가 다운로드할 수 있도록 MIT 라이선스에 의거 Dynamics 365 포털 코드의 일회성 릴리스가 Microsoft 다운로드 센터에 릴리스됩니다. 이 기능을 사용하면 포털을 Dynamics 365 온-프레미스 또는 온라인 환경에 배포할 수 있으며 개발자는 자신의 특정 비즈니스 니즈에 맞게 코드를 맞춤화할 수 있습니다.

  > [!NOTE]
  > 소스 코드는 작업 샘플로서 필요에 따라 제공됩니다. 코드 수정을 위한 직접 지원은 제공되지 않습니다.

- **Azure Active Directory B2C(Azure AD B2C)를 위한 Single Sign-on(SSO) 구성 개선 및 지원**: 소비자 기반 로그인이 요구되는 포털을 위해 이제 이 기능은 다음 기능을 지원합니다.
  - SSO를 사용하기 위해 포털 인증을 구성합니다. 
  - 고객 인증을 위해 Azure AD B2C를 지원합니다.
  - Azure에서 포털 보안을 관리합니다.

  추가 정보: [포털을 위한 Azure AD B2C 공급자 설정](configure/azure-ad-b2c.md)

- **포털 양식에서 표준 시간대 독립 날짜 형식 지원**: 이 기능은 날짜/시간 필드를 위한 **날짜만** 및 **표준 시간대 독립** 동작에 대한 지원을 추가합니다. 추가 정보: [날짜 및 시간 필드의 동작 및 형식](configure/behavior-format-date-time-field.md)

- **비전역 관리자가 포털을 프로비전하도록 허용**: 귀하가 포털을 위해 선택된 CRM 조직의 시스템 관리자 역할에 지정된 경우 이제 포털을 프로비전할 수 있습니다. 다음 역할 중 하나가 있는 경우에도 기존 포털을 관리할 수 있습니다:
  - Dynamics 365 서비스 관리자
  - 포털을 위해 선택된 CRM 조직의 시스템 관리자

- **포털의 맞춤 도메인 이름을 저장**: 이 기능은 포털의 주 도메인 이름을 웹사이트 레코드에 저장합니다. 나중에 도메인 이름이 변경되는 경우 최신 주 도메인 이름이 저장됩니다.

- **포털에 대한 쿠키 추적**: 사용자가 포털로 이동할 때마다 영구적 쿠키 Dynamics365PortalAnalytics가 설정됩니다. 이 쿠키의 만료 시한은 90일입니다. 이 쿠키는 사용자의 개인 데이터를 저장하지 않으며 Microsoft가 포털 서비스에 대한 분석 자료를 수집하기 위해 사용합니다. Microsoft 온라인 서비스 개인 정보 보호 정책에 대한 자세한 내용은 [여기에서](https://go.microsoft.com/fwlink/p/?linkid=856855) 참조하십시오.

- **포털의 머리글 및 바닥글의 성능 향상**: 두 개의 새 사이트 설정 Header/OutputCache/Enabled 및 Footer/OutputCache/Enabled가 추가되어 이러한 설정이 true로 설정되면 머리글/바닥글 출력 캐싱이 활성화됩니다. 새 사용자의 경우 이러한 사이트 설정은 기본적으로 true로 설정되므로 머리글 및 바닥글 출력 캐싱이 활성화됩니다. 최신 버전의 Dynamics 365 포털로 업그레이드하는 기존 사용자의 경우 기본적으로 출력 캐싱이 비활성화되어 있습니다. 즉, 페이지가 로드될 때마다 머리글 및 바닥글 웹 템플릿이 구문 분석되고 렌더링됩니다. 출력 캐싱을 활성화하려면 해당 웹 템플릿을 업데이트하고 요구되는 사이트 설정을 만들어야 합니다. 추가 정보: [머리글 및 바닥글 출력 캐싱 활성화](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>2016년 12월 업데이트

2016년 12월 업데이트는 Dynamics 365 포털에 많은 새로운 기능을 가져왔습니다. 이러한 업데이트를 통해 회사, 파트너 및 고객 사이의 상호 작용을 더 쉽고 빠르게 탐색하는 환경을 만들 수 있습니다. 주요 업데이트 중 일부는 다음과 같습니다.

- **여러 언어 지원:** 단일 포털을 사용하여 여러 영역에서 고객을 지원합니다. 추가 정보: [다중 언어 지원 사용](configure/enable-multiple-language-support.md)
- **동아시아 언어 지원:** 일본어, 중국어 및 한국어와 같은 멀티바이트 언어가 이제 지원됩니다.
- **패싯 검색:** 새 필터를 통해 고객은 콘텐츠 가시성에 대해 더 많은 제어를 부여하면서 고객이 원하는 내용을 더 빠르게 찾을 수 있습니다. 추가 정보: [패싯 검색](configure/improve-portal-search-faceted-search.md)
- **제품 필터링:** 포털 사용자는 정보 과부하를 방지하기 위해 제품 소유권과 관련된 액세스 참조 문서를 자를 수 있습니다.
- **콘텐츠 액세스 수준:** 포털 연락처, 계정 또는 웹 역할과 연계된 새 수준의 소유권을 사용하여 참조 문서에 대한 액세스를 통제하고, 올바른 기사를 올바른 대상에 제공하고 관련 없는 기사가 표면화되지 않도록 할 수도 있습니다. 추가 정보: [콘텐츠 액세스 수준](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **참조 문서 보고 향상:** 포털에서 참조 문서가 사용된 위치를 추적합니다.
- **Project Service Automation 통합:** 파트너 및 고객에게 프로젝트 수명 주기의 모든 단계에 걸쳐 활성 및 종료된 프로젝트에 대한 액세스 및 가시성을 제공합니다. 팀 구성원, 검토자 및 고객은 이 솔루션을 사용하여 포털의 프로젝트 상태, 견적, 주문 포럼 및 예약 가능한 리소스를 볼 수 있습니다. 추가 정보: [Project Service Automation 통합](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Field Service 통합:** 이 솔루션을 사용 중인 포털의 파트너 및 고객에게 활성 계약, 자산, 작업 주문, 송장 및 지원 사례에 대한 정보를 표시합니다. 추가 정보: [Field Service 통합](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **파트너 합류:** 더 나은 고객 영업 및 서비스 경험을 위한 새로운 파트너를 모집합니다. 잠재적인 파트너는 포털을 통해 파트너 상태를 신청할 수 있습니다.

### <a name="privacy-notice"></a>개인정보취급방침

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

추가 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] 서비스 제품에 대한 자세한 내용은 [[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/)를 참조하십시오.  
