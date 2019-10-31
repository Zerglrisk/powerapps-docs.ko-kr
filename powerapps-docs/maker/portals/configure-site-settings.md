---
title: 포털에 대한 사이트 설정 구성 | MicrosoftDocs
description: 포털에 대한 사이트 설정 및 조직의 모든 포털에 대한 전역 설정을 추가 및 구성하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="configure-site-settings-for-portals"></a>포털의 사이트 설정 구성

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

사이트 설정은 포털의 동작이나 시각적 스타일을 수정하기 위해 웹 사이트 코드에서 사용되는 구성 가능한 명명된 값입니다. 일반적으로 개발자가 웹 사이트 코드를 작성할 때에는 최종 사용자가 설정 값을 수정하여 코드를 변경하고 웹 사이트를 다시 컴파일하고 다시 배포할 필요 없이 웹 사이트를 변경할 수 있도록 다양한 구성 요소의 사이트 설정을 참조합니다.

[!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 포털의 설치와 함께 제공되는 샘플 포털에는 배경 스타일, 텍스트 색상, 레이아웃 너비 등 사이트 내 많은 시각적 요소를 수정하는 데 사용되는 다양한 스타일을 위해 구성 가능한 여러 사이트 설정이 포함되어 있습니다.
다음 타입의 사이트 설정값을 관리할 수 있습니다.

- **글로벌 포털 설정값**: 이 설정값은 추가되는 [!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 조직에 연계된 모든 포털에 적용됩니다.
- **포털 사이트 설정값**: 이 설정값은 추가되는 [!INCLUDE[pn-dynamics-crm](../../includes/pn-dynamics-crm.md)] 조직에 연계된 특정 포털(웹 사이트 레코드)에 적용됩니다.


## <a name="manage-portal-site-settings"></a>포털 사이트 설정값 관리

1. [포털 설정](manage-existing-portals.md#settings)으로 이동하여 **사이트 설정**을 선택합니다.

2. 새 설정을 만들려면 **+ 새로 만들기**를 선택합니다.

3. 기존 설정을 편집하려면 표에 나열된 **사이트 설정**을 선택합니다.

4. 제공된 필드에 값을 지정합니다. 

    - **이름**: 적절한 설정을 검색하기 위해 웹 사이트 코드에 의해 참조되는 레이블입니다. 설정을 검색하는 코드는 일치하는 이름으로 찾은 첫 번째 레코드를 선택하므로 해당 이름은 관련된 웹 사이트에 대해 고유해야 합니다.
    
    - **웹 사이트**: 요구되는 연계된 웹 사이트. 
    
    - **값**: 설정
    
    - **설명**: 설정 또는 특별한 지침의 목적입니다.

5. **저장 후 닫기**를 선택합니다.

> [!NOTE] 
> 독일 주권 클라우드 환경에서는 Bing 지도가 지원되지 않습니다. 이 환경에서 Bing 지도/자격 증명 설정값을 만들려고 하면 오류 메시지가 표시됩니다.

## <a name="portal-site-settings"></a>포털 사이트 설정

|이름|Value|설명|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSE |True의 부울 값은 전자 메일 확인을 활성화하고 열린 등록을 비활성화합니다. 기본값: False |
|Authentication/Registration/RequiresInvitation|FALSE |True의 부울 값은 초대 코드 기능을 활성화하고 열린 등록을 비활성화합니다. 기본값: False |
|전화 회의-이름|포털 전화 회의|지정된 포털에 대한 전화 회의를 나타내는 adx_conference 레코드의 이름입니다.|
|HelpDesk/CaseEntitlementEnabled|TRUE|지원 센터 서비스 케이스 권리 유형이 활성화되었는지 여부를 나타내는 부울 값입니다. 기본값: false|
|HelpDesk/Deflection/DefaultSelectedProductName| |producttypecode가 100000001과 동일한 제품이 두 개 이상 있는 경우 헬프 데스크 서비스 케이스 편향에 표시되는 드롭다운에서 기본 선택된 제품인 제품 레코드의 이름입니다.|
|Profile/ForceSignUp|FALSE|"True"로 설정하면 사용자가 웹 사이트 콘텐츠에 대한 액세스 권한을 부여하기 전에 프로필 정보를 업데이트하도록 강제하는 부울 값입니다. 기본값: False|
|Profile/ShowMarketingOptionsPanel|TRUE|프로필에서 마케팅 통신 기본 설정을 지정하기 위해 필드를 나열하는 패널을 표시할지 여부를 나타내는 부울 값입니다. 기본값: False|
|Search/Enabled|TRUE|검색이 사용되는지 여부를 나타내는 부울 값입니다.|
|search/filters|내용:adx_webpage;Events:adx_event,adx_eventschedule;<br>블로그:adx_blog,adx_blogpost,adx_blogpostcomment;<br>포럼:adx_communityforum,adx_communityforumthread,adx_communityforumpost;<br>아이디어:adx_ideaforum,adx_idea,adx_ideacomment;<br>문제:adx_issueforum,adx_issue,adx_issuecomment;헬프 데스크:문제|검색 논리 이름 필터 옵션의 컬렉션입니다. 여기에 값을 정의하면 사이트 차원의 검색에 드롭다운 필터 옵션이 추가됩니다. 이 값은 이름 및 값을 콜론으로 구분하고 쌍을 세미콜론으로 구분한 이름/값 쌍의 형식이어야 합니다.<br>예: "Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment".|
|Search/IndexQueryName|포털 검색|포털 검색 쿼리에서 사용하는 시스템 보기의 이름입니다. 기본값: 포털 검색|
|search/query|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|추가 가중치 및 필터를 적용하려면 사이트 검색에 대한 쿼리를 다시 정의합니다. @Query는 사용자가 입력한 쿼리 텍스트입니다. Lucene 쿼리 구문 참조: [http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Search/Stemmer|영어|포털 검색의 형태소 분석 알고리즘에서 사용하는 언어입니다. 기본값: 영어|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSE| |
|||

다양한 포털 기능과 관련된 사이트 설정에 대해서는 다음을 참조하십시오.

- [인증 ID](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/set-authentication-identity)
- [Azure AD B2C 공급자](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/azure-ad-b2c)
- [OAuth 2.0](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-oauth2-settings)
- [ID 연결 열기](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-openid-settings)
- [WS-Federation](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-ws-federation-settings)
- [SAML 2.0](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-saml2-settings)
- [ID 공급자를 Azure AD B2C로 마이그레이션](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/migrate-identity-providers)
- [첨부 파일 콘텐츠 내에서 검색](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/search-file-attachment)
- [날짜 및 시간 필드의 특성 및 형식](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/behavior-format-date-time-field)
- [지리적 위치 추가](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/add-geolocation)
- [Field Service 통합](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/integrate-field-service)
- [일반 데이터 보호 규정 구현](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/implement-gdpr)
- [머리글 및 바닥글 출력 캐싱 활성화](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>글로벌 포털 설정값 관리

1. [포털 설정](manage-existing-portals.md#settings)으로 이동하여 **사이트 설정**을 선택합니다.

2. **설정** &gt; **설정**으로 이동합니다.

3. 새 설정을 만들려면 **+ 새로 만들기**를 선택합니다.

4. 기존 설정을 편집하려면 표에 나열된 **사이트 설정**을 선택합니다.

5. 제공된 필드에 값을 지정합니다. 

    - **이름**: 해당 설정값을 검색하기 위해 코드에 의해 참조되는 고유 이름.

    - **값**: 설정

    - **설명**: 설정 또는 특별한 지침의 목적입니다.

6. **저장 후 닫기**를 선택합니다.

> [!NOTE] 
> 독일 주권 클라우드 환경에서는 Bing 지도가 지원되지 않습니다. 이 환경에서 Bing 지도/키 또는 Adxstudio/생산성 팩/Bing 지도/키 설정값을 생성하려고 하면 오류 메시지가 표시됩니다.


