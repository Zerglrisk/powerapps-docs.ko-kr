---
title: 포털에 대 한 사이트 설정 구성 | MicrosoftDocs
description: 포털의 사이트 설정과 조직의 모든 포털에 대 한 전역 설정을 추가 하 고 구성 하는 지침을 설명 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 339a8b221474bd9d98ed8e425f730bab1dbb1e0a
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978327"
---
# <a name="configure-site-settings-for-portals"></a>포털에 대 한 사이트 설정 구성

사이트 설정은 웹 사이트 코드에서 포털의 동작 또는 비주얼 스타일을 수정 하는 데 사용 하는 구성 가능한 명명 된 값입니다. 일반적으로 개발자는 웹 사이트 코드를 만들 때 다양 한 구성 요소에 대 한 사이트 설정을 참조 하 여 최종 사용자가 코드를 변경 하거나 다시 컴파일하고 웹 사이트를 다시 배포 하지 않고도 웹 사이트를 변경 하도록 설정 값을 수정할 수 있도록 합니다.

PowerApps 포털 설치와 함께 제공 되는 샘플 포털에는 배경 스타일, 텍스트 색 및 레이아웃 너비와 같이 사이트 내의 여러 시각적 요소를 수정 하는 데 사용 되는 다양 한 스타일에 대 한 몇 가지 구성 가능한 사이트 설정이 포함 되어 있습니다.
다음 유형의 사이트 설정을 관리할 수 있습니다.

- **전역 포털 설정**: 이러한 설정은 추가 중인 Common Data Service 환경과 연결 된 모든 포털에 적용 됩니다.
- **포털 사이트 설정**: 이러한 설정은 추가 중인 Common Data Service 환경과 연결 된 특정 포털 (웹 사이트 레코드)에 적용 됩니다.


## <a name="manage-portal-site-settings"></a>포털 사이트 설정 관리

1. [포털 설정](../manage-existing-portals.md#settings) 으로 이동 하 고 **사이트 설정**을 선택 합니다.

2. 새 설정을 만들려면 **새로**만들기를 선택 합니다.

3. 기존 설정을 편집 하려면 표에 나열 된 **사이트 설정을** 선택 합니다.

4. 제공 된 필드에 대 한 값을 지정 합니다. 

    - **이름**: 해당 설정을 검색 하기 위해 웹 사이트 코드에서 참조 하는 레이블입니다. 이 이름은 연결 된 웹 사이트에 대해 고유 해야 합니다. 설정을 검색 하는 코드는 이름이 일치 하는 첫 번째 레코드를 사용 하기 때문입니다.
    
    - **웹 사이트**: 연결 된 웹 사이트입니다. 
    
    - **값**: 설정
    
    - **설명**: 설정 또는 특수 지침의 목적입니다.

5. **저장 후 닫기**를 선택합니다.

> [!NOTE] 
> Bing 지도 통합은 독일어 소 버린 클라우드에서 지원 되지 않습니다. 이 환경에서 Bingmaps/credentials 설정을 만들려고 하면 오류 메시지가 표시 됩니다.

## <a name="portal-site-settings"></a>포털 사이트 설정

|이름|Value|설명|
|----|-----|-----------|
|인증/등록/RequiresConfirmation|허위 |부울 값 true는 전자 메일 확인을 사용 하 고 열기 등록을 해제 합니다. 기본값: False |
|인증/등록/RequiresInvitation|허위 |부울 값이 true 이면 초대 코드 기능이 활성화 되 고 열기 등록이 사용 하지 않도록 설정 됩니다. 기본값: False |
|회의 이름|포털 회의|지정 된 포털의 회의를 나타내는 adx_conference 레코드의 이름입니다.|
|기술 지원팀/CaseEntitlementEnabled|TRUE|지원 센터 케이스 자격을 사용할 수 있는지 여부를 나타내는 부울 값입니다. 기본값: false|
|기술 지원팀/Deflection/DefaultSelectedProductName| |제품 이름이 100000001 인 제품이 둘 이상 있는 경우 지원 센터 사례 Deflection에 표시 되는 드롭다운 목록에서 선택 된 기본 제품인 제품 레코드 이름입니다.|
|Profile/ForceSignUp|허위|부울 값이 "True"로 설정 되 면 사용자가 웹 사이트 콘텐츠에 대 한 액세스 권한을 부여 하기 전에 프로필 정보를 강제로 업데이트 합니다. 기본값: False|
|Profile/ShowMarketingOptionsPanel|TRUE|프로필에 대 한 마케팅 통신 기본 설정을 지정 하는 필드를 나열 하는 패널을 표시할지 여부를 나타내는 부울 값입니다. 기본값: False|
|검색/사용|TRUE|검색을 사용할 수 있는지 여부를 나타내는 부울 값입니다.|
|검색/필터|콘텐츠: adx_webpage; 이벤트: adx_event, adx_eventschedule;<br>블로그: adx_blog, adx_blogpost, adx_blogpostcomment;<br>포럼: adx_communityforum, adx_communityforumthread, adx_communityforumpost;<br>아이디어: adx_ideaforum, adx_idea, adx_ideacomment;<br>문제: adx_issueforum, adx_issue, adx_issuecomment; 지원 센터: 인시던트|검색 논리 이름 필터 옵션의 컬렉션입니다. 여기에서 값을 정의 하면 드롭다운 필터 옵션이 사이트 전체 검색에 추가 됩니다. 이 값은 이름/값 쌍의 형식 이어야 하며, 이름 및 값은 콜론으로 구분 하 고 쌍은 세미콜론으로 구분 해야 합니다.<br>예: "포럼: adx_communityforum, adx_communityforumthread, adx_communityforumpost; 블로그: adx_blog, adx_blogpost, adx_blogpostcomment ".|
|검색/IndexQueryName|포털 검색|포털 검색 쿼리에서 사용 되는 시스템 뷰의 이름입니다. 기본값: 포털 검색|
|검색/쿼리|\+ (@Query) _title: (@Query) _logicalname: adx_webpage ~ 0.9 ^ 0.2<br> -_logicalname: adx_webfile ~ 0.9 adx_partialurl@Query)<br> _logicalname: adx_blogpost ~ 0.9 ^ 0.1-_logicalname: adx_communityforumthread ~ 0.9|사이트 검색에 대 한 쿼리를 재정의 하 여 추가 가중치 및 필터를 적용 합니다. @Query은 사용자가 입력 한 쿼리 텍스트입니다. Lucene 쿼리 구문 참조: [http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|검색/형태소 분석기|영어|포털 검색의 형태소 분석 알고리즘에서 사용 하는 언어입니다. 기본값: 영어|
|CustomerSupport/Displayalluseractivonetimeline|허위| |
|인증/[프로토콜]/[공급자]/AllowContactMappingWithEmail| |전자 메일을 기반으로 하는 연락처 레코드에 자동 연결을 허용 합니다. 자세한 내용을 보려면 [여기](https://docs.microsoft.com/en-us/dynamics365/portals/azure-ad-b2c#allow-auto-association-to-a-contact-record-based-on-email)를 클릭 하세요.|
|||

다양 한 포털 기능과 관련 된 사이트 설정은 다음을 참조 하세요.

- [인증 id](set-authentication-identity.md)
- [Azure AD B2C 공급자](azure-ad-b2c.md)
- [OAuth 2.0](configure-oauth2-settings.md)
- [Open ID Connect](configure-openid-settings.md)
- [WS-FEDERATION](configure-ws-federation-settings.md)
- [SAML 2.0](configure-saml2-settings.md)
- [Azure AD B2C로 id 공급자 마이그레이션](migrate-identity-providers.md)
- [파일 첨부 콘텐츠 내에서 검색](https://docs.microsoft.com/dynamics365/customer-engagement/portals/search-file-attachment)
- [날짜 및 시간 필드의 동작 및 형식](https://docs.microsoft.com/dynamics365/customer-engagement/portals/behavior-format-date-time-field)
- [지리적 위치 추가](https://docs.microsoft.com/dynamics365/customer-engagement/portals/add-geolocation)
- [필드 서비스 통합](https://docs.microsoft.com/dynamics365/customer-engagement/portals/integrate-field-service)
- [일반 데이터 보호 규정 구현](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [머리글 및 바닥글 출력 캐싱 사용](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>전역 포털 설정 관리

1. [포털 설정](../manage-existing-portals.md#settings) 으로 이동 하 고 **사이트 설정**을 선택 합니다.

2. **설정** &gt; **설정**으로 이동 합니다.

3. 새 설정을 만들려면 **새로**만들기를 선택 합니다.

4. 기존 설정을 편집 하려면 표에 나열 된 **사이트 설정을** 선택 합니다.

5. 제공 된 필드에 대 한 값을 지정 합니다. 

    - **이름**: 적절 한 설정을 검색 하기 위해 코드에서 참조 하는 고유 이름입니다.

    - **값**: 설정

    - **설명**: 설정 또는 특수 지침의 목적입니다.

6. **저장 후 닫기**를 선택합니다.

> [!NOTE] 
> Bing 지도 통합은 독일어 소 버린 클라우드에서 지원 되지 않습니다. 이 환경에서 BinMap/Key 또는 Adxstudio/ProductivityPack/BingMap/Key 설정을 만들려고 하면 오류 메시지가 표시 됩니다.


