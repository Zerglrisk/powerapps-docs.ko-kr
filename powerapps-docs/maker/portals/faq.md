---
title: 질문과 대답 | Microsoft Docs
description: Power Apps 포털의 질문과 대답입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/03/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 28df2292d18f38a78e913a9805ac39a33f6aaf54
ms.sourcegitcommit: 5e6d71967902c463f34a9254f988b9c10e431eb4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "2890736"
---
# <a name="power-apps-portals-faq"></a>Power Apps 포털 FAQ

우리는 질문과 대답의 목록을 컴파일하고 귀하의 정보를 신속하게 얻을 수 있도록 간단한 답변을 제공했습니다.

## <a name="general"></a>일반

### <a name="how-do-i-redirect-a-user-to-a-default-page-after-signing-in"></a>로그인 후 사용자를 기본 페이지로 리디렉션하는 방법

로그인한 후 사용자를 기본 페이지로 리디렉션하도록 포털을 구성할 수 있습니다. 이 기능을 구현하려면 홈 웹 템플릿에 JavaScript 코드를 포함시킬 수 있습니다.

예를 들어, 로그인한 후 모든 사용자를 포럼 페이지로 리디렉션하려는 경우 다음과 같이 홈 웹 템플릿에 JavaScript 코드를 포함할 수 있습니다.

```xml
{% if user %}
//if any user logs in
<script>
  window.location.href='./forums/'
</script>
{% else %}
//Home web page code, if you don't want to display the page when the user is being redirected
{% endif %}
//Home web page code, if you want to display the page when the user is being redirected
```

유동 템플릿 작업에 대한 자세한 내용은 [유동 템플릿에 대한 작업](liquid/liquid-overview.md)을 참조하십시오.

### <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>하나의 포털만 만들 수 있다는 오류가 발생합니다.

현재 언어별로 환경에서 각 유형의 포털을 하나만 작성할 수 있습니다. 둘 이상의 포털을 작성하려고 하면 다음과 같은 오류 메시지가 표시됩니다.

> [!div class=mx-imgBorder]
> ![최대 포털 생성 오류](media/portal-max-error.png "최대 포털 생성 오류")

더 많은 포털을 작성하려면 오류 메시지에 **새로운 환경 만들기** 링크를 사용하여 새 환경을 작성해야 합니다. 포털 만들기에 대한 자세한 내용은 [포털 만들기](create-portal.md)를 참조하십시오.

### <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>포털을 삭제할 수 없다는 오류가 발생합니다.

포털을 삭제할 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 삭제 오류](media/portal-delete-error.png "포털 삭제 오류")

포털 삭제 및 필요한 권한에 대한 정보는 [포털 삭제](manage-existing-portals.md#delete)를 참조하십시오.

### <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>포털을 만들 수 없다는 오류가 발생합니다.

환경에서 포털을 만들 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 생성 오류](media/portal-create-error.png "포털 생성 오류")

포털 만들기 및 필요한 권한에 대한 정보는 [포털 만들기](create-portal.md)를 참조하십시오.

### <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>"데이터가 준비되지 않았습니다"라는 메시지가 나타납니다.

때때로 데이터베이스 작성에 시간이 걸리고 올바른 상태가 홈 페이지에 반영되지 않을 수 있습니다. 이 경우 다음과 같은 메시지가 나타납니다.

> [!div class=mx-imgBorder]
> ![데이터 준비 안 됨](media/data-not-ready.png "데이터 준비 안 됨")

데이터베이스 생성 프롬프트 또는 데이터가 준비되지 않았다는 프롬프트가 계속 표시되는 경우 **공백에서 포털** 타일을 선택하기 전에 Power Apps 홈 페이지를 새로 고쳐 봅니다.

### <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory 애플리케이션을 만드는 데 필요한 권한이 없다는 오류가 표시됩니다.

포털을 만들면 포털이 테넌트와 연결된 Azure Active Directory에 새 애플리케이션으로 등록됩니다. Azure Active Directory 테넌트로 애플리케이션을 등록할 충분한 권한이 없으면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![Azure Active Directory 오류](media/azure-ad-error.png "Azure Active Directory 오류")

Azure Active Directory에서 애플리케이션을 만들고 등록하려면 테넌트 관리자에게 문의하여 테넌트에 대한 **앱 등록** 설정을 켭니다. 자세한 내용은 [필요한 권한](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)을 참조하십시오.

### <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>이 테넌트에서 포털 작성이 전역 관리자에 의해 차단되었다는 오류가 발생합니다.

전역 관리자가 테넌트에서 포털 작성을 차단하면 다음과 같은 오류가 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 생성 차단 오류](media/portal-create-blocked-error.png "포털 생성 차단 오류")

관리자가 아닌 사람도 포털을 작성할 수 있도록 하려면 전역 관리자에게 문의해야 합니다.

전역 관리자인 경우 PowerShell을 통해 `disablePortalsCreationByNonAdminUsers` 테넌트 수준 설정을 해제해야 합니다. PowerShell 창에서 다음 명령을 실행합니다(관리자 권한으로 PowerShell 실행).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

추가 정보: [테넌트에서 포털 작성 사용 안 함](create-portal.md#disable-portal-creation-in-a-tenant)

### <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>이 웹 사이트에 액세스할 수 있는 적절한 라이선스가 없다는 오류가 발생합니다.

인증된 페이지에 액세스하기 위해 포털을 사용하는 조직의 내부 사용자의 라이선스가 포털이 연결된 환경에 할당되어야 합니다. [여기](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users)에서 내부 사용자용 포털의 사용자 권한에 대해 자세히 읽어볼 수 있습니다. 환경에 라이선스가 할당되지 않은 경우 내부 사용자에게 다음과 같은 오류가 발생합니다.

> [!div class=mx-imgBorder]
> ![포털 로그인 오류](media/portal-login-error.png "포털 로그인 오류")

## <a name="licensing-and-provisioning"></a>라이선싱 및 프로비저닝

### <a name="how-do-i-get-a-portal-subscription"></a>포털 구독을 얻는 방법

다음 방법 중 하나를 통해 포털 구독을 얻을 수 있습니다.

- 사용자 라이선스의 특정 유형 및 수량 구매와 함께 포털 추가 기능 하나가 제공됩니다. 자세한 내용은 Dynamics 365 가격 책정 및 라이선싱 가이드에서 확인할 수 있습니다. 유효한 라이선스의 여러 유형이나 수량을 구매한 경우에도 사용자 라이선스가 있는 포털 추가 기능을 하나만 얻을 수 있다는 점에 유의하십시오.

- 포털 추가 기능 구독을 구입하면 추가 포털 구독을 구입할 수 있습니다. 이 구독은 추가 기능 구독이며 적절한 Dynamics 365 라이선스가 있는 경우 구입할 수 있습니다.

### <a name="how-do-i-change-the-audience-and-type-of-a-portal-after-it-is-provisioned"></a>프로비저닝된 후 포털의 대상 그룹과 유형을 변경하는 방법

포털을 프로비저닝한 후에는 포털 대상 그룹을 변경하는 옵션을 사용할 수 없습니다.

그러나 [Dynamics 365 인스턴스, 대상 그룹 또는 포털 유형 변경](admin/change-dynamics-instance.md)의 단계에 따라 포털의 대상 그룹 및 유형을 프로비저닝한 후 변경할 수 있습니다.

> [!NOTE]
> - 대상 그룹, 포털 유형, 조직 등을 변경하려면 포털을 다시 설정하고 프로비저닝하는 것이 좋습니다. 추가 정보: [포털 다시 설정](admin/reset-portal.md)
> - Dynamics 365 인스턴스 변경은 이전 추가 기능을 사용하여 프로비저닝된 포털에만 적용됩니다.

### <a name="how-do-i-change-the-base-url-of-a-portal-after-it-is-provisioned"></a>포털이 프로비저닝된 후에 포털의 기본 URL을 변경하는 방법

[포털의 기본 URL 변경](admin/change-base-url.md)의 단계를 수행하여 포털이 프로비저닝된 후에 포털의 기본 URL을 변경할 수 있습니다.

### <a name="how-do-i-delete-a-portal-completely-after-it-is-provisioned"></a>포털을 프로비저닝한 후 완전히 삭제하는 방법

포털은 다음과 같은 구성 요소로 구성됩니다.

- **포털 웹 사이트 호스트**: 포털 웹사이트 호스트는 실제 웹사이트를 형성하는 포털 코드입니다.

- **포털 솔루션**: Common Data Service 환경에 설치되고 모든 포털에 대한 메타데이터 엔터티가 포함된 솔루션입니다.

포털을 삭제하려면 포털 웹 사이트 호스트를 삭제하고 Common Data Service 환경에서 포털 솔루션을 제거해야 합니다.

포털 호스트를 재설정하려면 [포털 재설정](admin/reset-portal.md)의 단계를 따릅니다. 포털 호스트를 재설정해도 Common Data Service 환경에서 수행된 구성에는 영향을 주지 않는다는 점에 유의해야 합니다.

포털 솔루션을 삭제하려면 Dynamics 365 솔루션 탐색기 UI에서 솔루션을 삭제해야 합니다. 포털 솔루션을 제거해야 하는 순서는 [포털 솔루션 제거](https://community.dynamics.com/365/b/dynamics365portalssupport/archive/2017/02/27/portal-troubleshooting-part-three-uninstalling-portal-solutions)에서 제공됩니다.

## <a name="common-data-service-environment-lifecycle"></a>Common Data Service 환경 수명 주기

### <a name="we-recently-moved-our-common-data-service-environment-from-one-geolocation-or-tenant-to-another-how-do-we-handle-portals-connected-to-our-organization"></a>최근에 우리는 하나의 지리적 위치 또는 테넌트에서 Common Data Service 환경을 다른 위치로 옮겼습니다. 조직에 연결된 포털을 처리하는 방법은 무엇입니까?

하나의 지리적 위치 또는 테넌트에서 Common Data Service 환경을 이동하면 해당 조직에 연결된 포털이 자동으로 이동되지 않습니다. 또한 조직이 이동되었으므로 해당 조직과 연결된 포털이 작동하지 않고 시작 시 오류가 발생합니다.

포털을 관련 조직에 다시 연결하려면 다음을 수행합니다.

1. [포털 재설정](admin/reset-portal.md)의 단계에 따라 기존 지리적 위치 또는 테넌트에서 기존 포털 호스트를 재설정합니다. 그러면 연결된 포털 리소스가 삭제되고 작업이 완료된 후 포털 URL에 액세스할 수 없습니다.

2. 기존 포털이 재설정되면 새 테넌트(또는 기존 테넌트의 새 지리적 위치)로 이동하고 사용할 수 있도록 포털을 프로비저닝합니다.

### <a name="after-restoring-a-common-data-service-environment-from-an-old-backup-the-portal-connected-to-the-organization-is-not-working-how-do-we-fix-it"></a>이전 백업에서 Common Data Service 환경을 복원한 후에는 조직에 연결된 포털이 작동하지 않습니다. 해결 방법

Common Data Service 환경이 백업에서 복원되는 경우 조직에서 포털과의 연결을 끊을 수 있는 다양한 변경 내용이 조직에서 수행됩니다. 이 문제를 해결하려면

- 복원 작업 후 조직 ID가 동일하고 포털 솔루션도 사용할 수 있는 경우:

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 세부 정보** 탭으로 이동합니다.
3. **포털 상태** 드롭다운 목록에서 **끄기**를 선택합니다.
4. **업데이트**를 선택합니다. 
5. 업데이트 작업이 완료되면 **포털 상태** 드롭다운 목록을 **설정**으로 설정한 다음 **업데이트**를 선택합니다.

  포털이 다시 시작되고 조직에 대한 연결이 다시 생성됩니다.

- 복원 작업 또는 포털 솔루션이 조직에서 삭제된 후에 조직 ID가 다른 경우:

  - 이 경우 [포털 재설정](admin/reset-portal.md)의 단계를 수행하여 포털을 다시 설정하고 다시 프로비저닝하는 것이 좋습니다.

### <a name="we-recently-changed-the-url-of-our-common-data-service-environment-and-our-portal-stopped-working-how-do-we-fix-it"></a>최근 Common Data Service 환경의 URL을 변경하고 포털이 작동을 중지했습니다. 해결 방법

Common Data Service 환경의 URL을 변경하면 더 이상 Common Data Service 환경 URL을 식별할 수 없기 때문에 포털이 작동을 중지합니다. 이 문제를 해결하려면

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 작업** > **Dynamics 365 URL 업데이트**로 이동합니다.
3. 마법사 화면에 나타나는 지시에 따라 수행합니다.

포털을 다시 시작하고 작업을 다시 시작합니다.

## <a name="debugging-and-fixing-problems"></a>문제 디버깅 및 수정

### <a name="when-accessing-my-portal-i-see-a-generic-error-page-how-can-i-see-the-actual-error"></a>포털에 액세스할 때 일반 오류 페이지가 표시됩니다. 실제 오류는 어떻게 확인할 수 있습니까?

포털을 렌더링하는 동안 서버 오류가 발생할 때마다 일반 오류 페이지가 오류에 대한 타임 스탬프 및 활동 ID와 함께 최종 사용자에게 표시됩니다. 포털 관리자는 문제 디버깅 및 수정에 도움이 되는 실제 오류 세부 정보를 가져오기 위해 포털을 구성할 수 있습니다. 실제 오류를 보려면 다음과 같이 하십시오.

- **포털에서 사용자 지정 오류 페이지를 사용하지 않도록 설정**: 사용자 지정 오류 페이지를 해제하고 해당 페이지로 이동하는 경우 모든 오류에 대한 전체 스택 추적을 볼 수 있게 됩니다. [사용자 지정 오류 사용 안 함](admin/view-portal-error-log.md#disable-custom-error)의 단계를 수행하여 사용자 지정 오류를 비활성화할 수 있습니다.

포털을 개발할 때만 이 기능을 사용하는 것이 좋습니다. 사용자를 위해 포털이 활성화되면 사용자 지정 오류를 다시 사용하도록 설정해야 합니다. 추가 정보: [포털 액세스 오류 보기](admin/view-portal-error-log.md)

- **진단 로깅 사용**: 이렇게 하면 Azure Blob 저장소 계정에서 모든 포털 오류를 가져올 수 있습니다. [액세스 포털 오류 로그](admin/view-portal-error-log.md#access-portal-error-logs)의 단계를 수행하여 진단 로깅을 사용하도록 설정할 수 있습니다.

진단 로깅을 사용하도록 설정하면 일반 오류 페이지에 표시된 활동 ID를 사용하여 사용자가 보고하는 특정 오류를 검색할 수 있습니다. 활동 ID는 오류 세부 정보와 함께 기록되며 실제 문제를 찾는 데 유용합니다.

## <a name="portal-administration-and-management"></a>포탈 관리

### <a name="how-do-i-use-a-custom-login-provider-on-my-portal"></a>포털에서 사용자 지정 로그인 공급자를 사용하는 방법

포털은 표준 인증 프로토콜에 대한 지원을 제공하는 모든 사용자 지정 로그인 공급자를 지원합니다. 모든 사용자 지정 IDP에 대해 OpenIdConnect, SAML2 및 WS-Federation 프로토콜을 지원합니다. Oauth 2는 고정된 알려진 IDP 집합에 대해서만 지원됩니다. IDP 구성을 설정하는 방법에 대한 자세한 내용은 [포털 인증 구성](configure/configure-portal-authentication.md)을 참조하십시오.

### <a name="how-do-i-get-new-portal-releases-in-my-sandbox-portal-first-before-it-gets-applied-to-production"></a>프로덕션에 적용하기 전에 먼저 샌드박스 포털에서 새 포털 릴리스를 가져오는 방법

모든 포털 릴리즈는 초기 업그레이드와 GA(일반 가용성)의 두 단계로 이루어집니다. 초기 업그레이드 단계에서는 초기 업그레이드를 위해 표시된 포털만 업그레이드합니다. 샌드박스(개발 또는 테스트) 환경에서 새 포털 릴리스를 받으려면 초기 업그레이드를 위해 포털을 활성화할 수 있습니다. 초기 업그레이드를 위해 포털을 사용하도록 설정하는 방법에 대한 자세한 내용은 [포털 업그레이드](https://docs.microsoft.com/dynamics365/customer-engagement/portals/upgrade-portal)를 참조하십시오.

### <a name="how-do-i-use-a-custom-domain-name-for-my-portal"></a>포털에 사용자 지정 도메인 이름을 사용하는 방법

표준 `microsoftcrmportals.com` 도메인 이름 대신 사용자 지정 도메인 이름을 사용하도록 포털을 활성화할 수 있습니다. 추가 정보: [포털을 사용자 지정 도메인에 연결](admin/add-custom-domain.md).

## <a name="portal-checker"></a>포털 검사기

### <a name="portal-does-not-load-and-displays-a-generic-error-page-server-error-in--application"></a>포털이 로드되지 않고 일반 오류 페이지("/" 응용 프로그램의 서버 오류)가 표시됩니다. 

이 문제는 포털이 기본 Common Data Service 환경에 연결할 수 없는 경우, Common Data Service 환경이 존재하지 않거나 URL이 변경된 경우, Common Data Service 환경에 대한 요청이 시간 초과되는 등의 다양한 이유로 인해 발생할 수 있습니다. 포털 검사기 도구를 실행하면 정확한 이유를 확인하려고 시도하고 올바른 완화를 안내할 것입니다. 

다음은 가장 일반적인 원인과 해당하는 완화 단계 목록입니다.

#### <a name="url-of-the-connected-common-data-service-environment-has-changed"></a>연결된 Common Data Service 환경의 URL이 변경되었습니다. 

이 문제는 포털이 프로비전된 후 사용자가 Common Data Service 환경의 URL을 변경할 때 발생합니다. 이 문제를 해결하려면 Dynamics 365 URL을 업데이트하십시오.

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 작업** > **Dynamics 365 URL 업데이트**로 이동합니다. 이 작업이 성공적으로 실행되면 Common Data Service 환경 URL이 업데이트되고 포털이 작동을 시작합니다.

#### <a name="common-data-service-environment-connected-to-your-portal-is-in-administration-mode"></a>사용자 포털에 연결된 Common Data Service 환경이 관리자 모드에 있습니다.

이 문제는 조직이 생산에서 샌드박스 모드로 변경될 때 또는 조직 관리자가 수동으로 Common Data Service 환경을 관리 모드로 전환하는 경우에 발생합니다.

이것이 원인인 경우 [여기](https://docs.microsoft.com/dynamics365/admin/manage-sandbox-instances#administration-mode)에 나열된 작업을 수행하여 관리 모드를 비활성화할 수 있습니다. 관리 모드가 비활성화되면 포털이 정상적으로 작동합니다.

#### <a name="authentication-connection-between-common-data-service-environment-and-portal-is-broken"></a>Common Data Service 환경과 포털 간의 인증 연결이 끊어집니다.

Common Data Service 환경이 백업에서 복원되었거나 삭제되어 백업에서 다시 생성되었기 때문에 Dynamic 365 조직과 포털 간의 인증 연결이 끊어진 경우 이 문제가 발생합니다. 이 문제를 해결하려면

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 세부 정보** 탭의 **포털 상태** 목록에서 **끄기**를 선택합니다.
3. **업데이트**를 선택합니다.
4. **포털 상태** 목록에서 **켜기**를 선택합니다.
5. **업데이트**를 선택합니다. 포털이 다시 시작되고 인증 연결을 만들 수 있게 됩니다.

그러나 특정 상황에서 특히 복원 작업 후 조직 ID가 변경된 경우(또는 조직을 다시 프로비전한 경우에는) 이러한 완화 단계가 작동하지 않습니다. 이러한 상황에서는 동일한 인스턴스에 대해 포털을 다시 설정하고 다시 프로비저닝할 수 있습니다. 포털을 다시 설정하는 방법에 대한 자세한 내용은 [포털 다시 설정](admin/reset-portal.md)을 참조하십시오.

#### <a name="request-to-common-data-service-environment-has-timed-out"></a>Common Data Service 환경에 대한 요청이 시간 초과되었습니다.

이 문제는 일반적으로 Common Data Service 환경에 대한 API 요청이 시간 초과된 경우 발생할 수 있는 일시적인 문제입니다. 이 문제는 API 요청이 작동을 시작하면 자동으로 자체적으로 완화됩니다. 이 문제를 완화하기 위해 포털을 다시 시작해 볼 수도 있습니다.

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 작업** > **다시 설정**으로 이동합니다.

포털 다시 시작이 작동하지 않고 이 문제가 오랜 기간 동안 발생하는 경우에는 Microsoft 기술 지원부에 문의하여 도움을 요청하십시오.

#### <a name="website-binding-not-found"></a>웹 사이트 바인딩을 찾을 수 없음

포털에 대한 웹 사이트 바인딩 레코드가 기본 Common Data Service 환경에서 삭제되고 포털이 자동으로 바인딩을 만들 수 없는 경우 이 문제가 발생합니다. 이 문제를 해결하려면

1. [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2. **포털** > **웹 사이트 바인딩**으로 이동합니다.
3. 포털을 가리키는 모든 웹 사이트 바인딩 레코드를 삭제합니다. **Sitename** 필드는 포털의 웹 사이트 바인딩 레코드를 식별하는 데 도움이 됩니다.
4. 모든 웹 사이트 바인딩 레코드를 삭제한 후 포털을 다시 시작합니다.

위의 단계를 완료하면 포털이 다시 시작되고 웹 사이트 바인딩 레코드가 자동으로 다시 만들어집니다.

그러나 인스턴스에서 사용할 수 있는 웹 사이트 레코드의 GUID가 포털의 기본 설치 중에 만들어진 것과 다른 경우 포털에서 웹 사이트 바인딩 레코드를 자동으로 다시 만들 수 없는 경우가 있습니다. 이 경우 다음 단계를 수행합니다.

1. 포털에 속한 모든 웹 사이트 바인딩 레코드를 삭제합니다.
2. 다음 값을 사용하여 웹 사이트 바인딩 레코드를 수동으로 만듭니다.
  - **이름**: 모든 문자열이 될 수 있습니다.
  - **웹 사이트**: 포털에서 렌더링하려는 웹 사이트 레코드를 선택합니다.
  - **Sitename**: 포털의 호스트 이름을 입력합니다. 즉 시작 부분에 https://가 없는 포털 URL입니다. 포털이 사용자 지정 도메인 이름을 사용하는 경우 여기에서 사용자 지정 도메인 이름을 사용합니다.
  - 다른 모든 필드는 비워둡니다.
3. 웹 사이트 바인딩 레코드가 다시 만들어지면 Power Apps 포털 관리 센터에서 포털을 다시 시작합니다.

#### <a name="an-unexpected-error-has-occurred-while-trying-to-connect-to-your-common-data-service-environment"></a>Common Data Service 환경에 연결하는 동안 예기치 않은 오류가 발생했습니다.

이 상황은 예기치 않은 문제로 인해 발생할 수 있습니다. 이러한 상황을 완화하기 위해 포털을 다시 설정하거나 다시 프로비전할 수 있습니다. 포털을 다시 설정하는 방법에 대한 자세한 내용은 [포털 다시 설정](admin/reset-portal.md)을 참조하십시오.

포털 다시 설정 및 재프로비저닝으로 이 문제가 해결되지 않으면 Microsoft 지원에 문의하여 도움을 요청하십시오.

### <a name="portal-is-not-displaying-updated-data-from-common-data-service-environment"></a>포털이 Common Data Service 환경에서 업데이트된 데이터를 표시하지 않습니다.

포털에 표시되는 모든 데이터는 포털 캐시에서 렌더링됩니다. 이 캐시는 Common Data Service 환경의 데이터가 업데이트될 때마다 업데이트됩니다. 그러나 이 프로세스는 비동기식이며 최대 15분까지 걸릴 수 있습니다. 포털의 메타데이터 엔터티(예: 웹 페이지, 웹 파일, 콘텐츠 조각, 사이트 설정 등)가 변경되면 캐시를 수동으로 지우거나 Power Apps 포털 관리 센터에서 포털을 다시 시작하는 것이 좋습니다. 캐시를 지우는 방법에 대한 자세한 내용은 [포털에 대한 서버 쪽 캐시 지우기](admin/clear-server-side-cache.md)를 참조하십시오. 

그러나 비 포털 메타데이터 엔터티에서 오랜 시간 동안 부실 데이터가 표시되는 경우 다음과 같은 다양한 문제로 인해 발생할 수 있습니다.

#### <a name="entities-not-enabled-for-cache-invalidation"></a>캐시 무효화를 사용하도록 설정하지 않은 엔터티

모든 엔터티에 대해서가 아니라 특정 엔터티에 대해서만 부실 데이터가 표시되는 경우 변경 내용 추적 메타데이터가 해당 특정 엔터티에 대해 사용하도록 설정되지 않았기 때문일 수 있습니다.

포털 검사기(셀프 서비스 진단) 도구를 실행하는 경우 엔터티 목록 또는 엔터티 양식 및 웹 양식에서 포털에서 참조되는 모든 엔터티의 개체 유형 코드를 나열하고 변경 내용 추적을 사용할 수 없습니다. [조직에 대한 메타 데이터 찾아보기](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/browse-your-metadata)에 언급된 단계를 사용하여 메타데이터를 검색합니다.

이러한 엔터티에서 부실 데이터 문제가 발생하는 경우 Power Apps 포털 관리 센터를 사용하여 변경 내용 추적을 사용 하도록 설정할 수 있습니다. UI 또는 Dynamics 365 API. 추가 정보: [엔터티에 대한 변경 내용 추적 기능 사용](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity)

#### <a name="organization-not-enabled-for-change-tracking"></a>조직에서 변경 내용 추적을 사용하도록 설정하지 않았습니다.

변경 내용 추적에 사용할 각 엔터티 외에도 전체 조직에서 변경 내용 추적을 사용하도록 설정해야 합니다. 포털 프로비저닝 요청이 제출되면 조직에서 변경 내용 추적을 사용할 수 있습니다. 그러나 조직이 이전 데이터베이스에서 복원되거나 다시 설정되는 경우 이는 중단될 수 있습니다. 이 문제를 해결하려면

1. [Power Apps 포털 관리 센터](admin/admin-overview.md)를 엽니다.
2. **포털 세부 정보** 탭의 **포털 상태** 목록에서 **끄기**를 선택합니다.
3. **업데이트**를 선택합니다.
4. **포털 상태** 목록에서 **켜기**를 선택합니다.
5. **업데이트**를 선택합니다. 포털이 다시 시작되고 인증 연결을 만들 수 있게 됩니다.

### <a name="performance-best-practices"></a>성능에 유용한 정보

포털의 성능 문제는 다양한 구성 문제로 인해 발생할 수 있습니다. 모든 기본 포털 템플릿은 포털 성능에 영향을 미칠 수 있는 다양한 부하 조건 및 구성에 대해 테스트되며 아래는 포털에서 성능 문제가 발생할 수 있는 일반적인 포털 구성 목록입니다.

포털 검사기(셀프 서비스 진단) 도구는 또한 포털 구성을 확인하여 이러한 문제를 지적합니다.

#### <a name="web-page-tracking-enabled"></a>웹 페이지 추적 활성화됨

포털 웹 페이지에서 페이지 추적을 활성화하면 포털에서 성능 문제가 발생할 수 있습니다. 이 기능은 Dynamics 365 포털의 2018년 1월 릴리스 이후 사용되지 않습니다. 추가 정보: [Dynamics 365 포털: 더 이상 사용되지 않는 기능](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

포털 검사기 도구는 페이지 추적에 사용할 수 있는 모든 웹 페이지(루트 및 콘텐츠 페이지 모두)를 나열합니다. 이러한 페이지는 다음 단계에 따라 비활성화해야 합니다.

1. [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2. 상세하게 찾기로 이동합니다.
3. **추적 사용(더 이상 사용되지 않음)** 필드가 비활성화된(값이 예로 설정됨) 모든 웹 페이지를 검색합니다.
4. 모든 페이지를 대량 편집하고 이 필드를 **아니요**로 설정합니다.

또는 포털 검사기 결과에 나열된 각 페이지로 이동하고 **추적 사용(더 이상 사용되지 않음)** 필드의 값을 **아니요**로 설정할 수도 있습니다. Dynamics 365 포털 솔루션 버전 9.x를 사용 중인 경우 이 필드는 양식에 표시되지 않으며 먼저 양식에 추가해야 할 수도 있다는 점을 이해하는 것이 중요합니다. 

#### <a name="web-file-tracking-enabled"></a>웹 파일 추적 활성화됨

포털 웹 파일에서 페이지 추적을 활성화하면 포털에서 성능 문제가 발생할 수 있습니다. 이 기능은 Dynamics 365 포털의 2018년 1월 릴리스 이후 사용되지 않습니다. 추가 정보: [Dynamics 365 포털: 더 이상 사용되지 않는 기능](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

포털 검사기 도구는 페이지 추적에 사용할 수 있는 모든 웹 파일을 나열합니다. 이러한 파일은 다음 단계에 따라 비활성화해야 합니다.

1. [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2. 상세하게 찾기로 이동합니다.
3. **추적 사용(더 이상 사용되지 않음)** 필드가 비활성화된(값이 예로 설정됨) 모든 웹 파일을 검색합니다.
4. 모든 레코드를 대량 편집하고 이 필드를 **아니요**로 설정합니다.

또는 포털 검사기 결과에 나열된 각 파일로 이동하고 **추적 사용(더 이상 사용되지 않음)** 필드의 값을 **아니요**로 설정할 수도 있습니다. 포털 솔루션 버전 9.x를 사용 중인 경우 이 필드는 양식에 표시되지 않으며 먼저 양식에 추가해야 할 수도 있다는 점을 이해하는 것이 중요합니다. 

#### <a name="login-tracking-enabled"></a>로그인 추적 활성화됨

포털 로그인 추적을 활성화하면 포털에서 성능 문제가 발생할 수 있습니다. 이 기능은 Dynamics 365 포털의 2018년 1월 릴리스 이후 사용되지 않습니다. 추가 정보: [Dynamics 365 포털: 더 이상 사용되지 않는 기능](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

포털 검사기 도구는 포털에 로그인 추적이 활성화되어 있는지 확인하고 활성화된 경우 실패한 확인을 표시합니다. 로그인 추적은 다음 단계에 따라 비활성화해야 합니다.

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  **포털** > **사이트 설정**으로 이동합니다.
3.  `Authentication/LoginTrackingEnabled`라는 사이트 설정을 검색합니다.
4.  이 사이트 설정의 값을 **False**로 변경하거나 사이트 설정을 삭제합니다.
5.  포털을 다시 시작합니다. 

#### <a name="header-output-cache-is-disabled"></a>머리글 출력 캐시가 비활성화됩니다.

포털에서 머리글 출력 캐시를 사용하지 않도록 설정하면 높은 부하가 있는 동안 포털에서 성능 문제가 발생할 수 있습니다. 이 기능에 대한 자세한 내용은 [포털에서 머리글 및 바닥글 출력 캐싱 사용](configure/enable-header-footer-output-caching.md)에서 찾을 수 있습니다.

포털 검사기 도구는 포털에 머리글 출력 캐시가 비활성화되어 있는지 확인하고 비활성화된 경우 실패한 확인을 표시합니다. 활성화하려면:

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  **포털** > **사이트 설정**으로 이동합니다.
3.  `Header/OutputCache/Enabled`라는 사이트 설정을 검색합니다.
4.  이 사이트 설정을 사용할 수 있는 경우 사이트 설정의 값을 **True**로 변경합니다. 사이트 설정을 사용할 수 없는 경우 이 이름으로 새 사이트 설정을 만들고 해당 값을 **True**로 설정합니다.
5.  포털을 다시 시작합니다. 

#### <a name="footer-output-cache-is-disabled"></a>바닥글 출력 캐시가 비활성화됩니다.

포털에서 바닥글 출력 캐시를 사용하지 않도록 설정하면 높은 부하가 있는 동안 포털에서 성능 문제가 발생할 수 있습니다. 이 기능에 대한 자세한 내용은 [포털에서 머리글 및 바닥글 출력 캐싱 사용](configure/enable-header-footer-output-caching.md)에서 찾을 수 있습니다.

포털 검사기 도구는 포털에 바닥글 출력 캐시가 비활성화되어 있는지 확인하고 비활성화된 경우 실패한 확인을 표시합니다. 활성화하려면:

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  **포털** > **사이트 설정**으로 이동합니다.
3.  `Footer/OutputCache/Enabled`라는 사이트 설정을 검색합니다.
4.  이 사이트 설정을 사용할 수 있는 경우 사이트 설정의 값을 **True**로 변경합니다. 사이트 설정을 사용할 수 없는 경우 이 이름으로 새 사이트 설정을 만들고 해당 값을 **True**로 설정합니다.
5.  포털을 다시 시작합니다. 

#### <a name="large-number-of-web-file-records"></a>많은 수의 웹 파일 레코드

웹 파일 엔터티는 포털에서 사용하려는 정적 파일을 포털에서 저장하는 데 사용됩니다. 이 엔터티의 주요 사용 사례는 CSS, JavaScript, 이미지 파일 등과 같은 웹 사이트의 정적 콘텐츠를 저장하는 것입니다. 그러나 이러한 파일이 많으면 포털을 시작하는 동안 속도가 저하될 수 있습니다.

포털 검사기 도구는 이 시나리오를 확인하고 포털에 500개 이상의 활성 웹 파일이 있는 경우 표시를 제공합니다. 이러한 모든 파일이 CSS, JavaScript, 이미지 파일 등과 같은 정적 콘텐츠를 나타내는 경우 다음 작업을 수행하여 이 문제를 완화할 수 있습니다.

- Azure BLOB 저장소 또는 CDN과 같은 외부 파일 서버를 사용하여 이러한 파일을 저장한 다음 페이지 또는 기본 템플릿의 적절한 페이지에서 이러한 파일을 참조합니다.

- 외부에서 파일을 이동할 수 없는 경우 모든 파일이 홈 페이지와 함께 로드되지 않았는지 확인합니다. 해당 파일의 상위 페이지가 홈으로 설정된 경우 웹 파일이 홈 페이지와 함께 로드됩니다. 이 시나리오를 방지하려면 다음 단계를 수행할 수 있습니다.

  1. 내용이 없고 빈 템플릿이 있는 더미 웹 페이지를 만듭니다. 이 페이지는 웹 파일에 대한 직접 경로를 만드는 데 사용됩니다. 
  2. 홈 페이지에 필요하지 않은 모든 웹 파일에 대해 상위 페이지를 이 더미 웹 페이지로 변경합니다. 완료되 면 웹 파일의 전체 경로는 `Portal URL/{dummy_webpage}/{web file}`이 됩니다.
  3. 웹 파일을 사용하려는 페이지의 페이지 템플릿 또는 웹 템플릿의 HTML에서 직접 참조합니다. 그러면 요청 시 해당 페이지에 파일이 로드됩니다. 

#### <a name="loading-static-resources-cssjs-asynchronously"></a>정적 리소스(css/js)를 비동기적으로 로드

포털 구현 작업을 수행하는 경우 웹 페이지의 클라이언트 쪽 성능이 영향을 받지 않도록 하기 위해 표준 웹 개발 사례를 따라야 한다는 의미로 HTML을 완벽하게 관리한다는 것을 이해하는 것이 중요합니다. 

웹 페이지에서 성능 문제의 가장 일반적인 원인 중 하나는 페이지 로드 시 많은 정적 리소스(css/js)를 로드하는 것입니다. 많은 수의 css/js 파일의 동기식 로드는 웹 페이지에 대한 긴 클라이언트 측 처리 시간으로 이어질 수 있습니다. 

포털의 경우 웹 파일을 홈 페이지에 직접 연결할 때마다 생성된 HTML에 종속성이 생성되므로 웹 파일이 항상 홈 페이지와 함께 로드됩니다. 이 웹 파일이 css/js 파일인 경우 동기적으로 로드되며 클라이언트측 처리 시간이 느려질 수 있습니다. 

이를 방지하려면 다음 단계를 수행할 수 있습니다. 

1. 홈 페이지에 웹 파일이 필요하지 않은 경우 상위 페이지가 홈 페이지로 설정되어 있지 않은지 확인하고 위에서 설명한 메커니즘을 다시 사용하여 요청 시 로드해야 합니다.
2. 모든 페이지에서 요청 시 JavaScript 파일을 로드하는 동안 `<async>` 또는 `<defer>` HTML 특성을 사용하여 파일을 비동기적으로 로드합니다.
3. 요청 시 CSS 파일을 로드하는 동안 `<preload>` HTML 특성(https://www.w3.org/TR/preload/) 또는 사전 로드가 아직 모든 브라우저에서 지원되지 않으므로 JavaScript 기반 접근 방식을 사용할 수 있습니다.

#### <a name="entity-form-lookup-configuration"></a>엔터티 양식 조회 구성 

드롭다운에 표시되는 레코드 수가 200을 초과하고 자주 변경되는 경우 조회를 사용하여 엔터티 양식 또는 웹 양식에서 드롭다운 모드로 렌더링하도록 하면 고도의 성능이 필요할 수 있습니다. 이 옵션은 제한된 수의 레코드를 가진 국가 목록 및 주 목록과 같은 정적 조회에만 사용해야 합니다.

이 옵션을 사용하여 많은 수의 레코드를 조회할 수 있는 경우 엔터티 양식을 사용할 수 있는 웹 페이지의 로드 시간이 느려집니다. 이 페이지를 많은 사용자가 사용하고 여러 번 로드하면 전체 웹 사이트 속도가 느려질 수 있으며 웹 사이트 리소스가 이 페이지를 렌더링하는 데 사용됩니다. 이러한 상황에서는 전체 검색 환경을 사용하거나 원하는 모습과 느낌을 위해 AJAX 끝점(웹 템플릿을 사용하여 생성)을 호출하는 사용자 지정 HTML 컨트롤을 구축해야 합니다.

#### <a name="number-of-web-roles"></a>웹 역할의 수

포털에서 웹 역할은 역할 기반 액세스 제어를 가능하게 하는 데 사용됩니다. 일반적으로 포털의 웹 역할 수는 여러 권한 조합의 수가 제한되므로 제한됩니다. 포털에서 웹 역할 수가 100을 초과하면 성능 문제가 발생하여 포털의 모든 페이지에 영향을 줄 수 있습니다.

### <a name="an-active-home-site-marker-is-not-available-for-this-portal"></a>이 포털에 활성 홈 사이트 마커를 사용할 수 없음

이 문제는 포털 구성에서 **홈** 사이트 마커를 사용할 수 없을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  다음 값을 사용하여 새 사이트 마커를 만듭니다. 
  - **이름**: 홈
  - **웹 사이트**: 포털 호스트의 웹 사이트를 선택하십시오.
  - **페이지**: 포털의 홈 페이지로 설정된 웹 페이지 레코드를 선택하십시오.

### <a name="the-home-site-marker-is-not-pointing-to-any-webpage"></a>홈 사이트 마커가 어떤 웹 페이지도 가리키지 않음

이 문제는 **홈** 사이트 마커를 사용할 수 있지만 웹 페이지를 가리키고 있지 않을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **홈** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 홈 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="the-home-site-marker-is-pointing-to-a-deactivated-web-page"></a>홈 사이트 마커가 비활성 웹 페이지를 가리키고 있음

이 문제는 **홈** 사이트 마커를 사용할 수 있지만 비활성화된 웹 페이지를 가리키고 있을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **홈** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 홈 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="the-home-site-marker-is-not-pointing-to-home-page-of-the-portal"></a>홈 사이트 마커가 포털의 홈 페이지를 가리키지 않음

이 문제는 **홈** 사이트 마커를 사용할 수 있지만 포털의 홈 페이지가 아닌 웹 페이지를 가리키고 있을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **홈** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 홈 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="an-active-profile-site-marker-is-not-available-for-this-portal"></a>활성 프로필 사이트 마커를 이 포털에 사용할 수 없음

이 문제는 포털 구성에서 **프로필** 사이트 마커를 사용할 수 없을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  다음 값을 사용하여 새 사이트 마커를 만듭니다. 
  - **이름**: 프로필
  - **웹 사이트**: 포털 호스트의 웹 사이트를 선택하십시오.
  - **페이지**: 포털의 프로필 페이지로 설정된 웹 페이지 레코드를 선택하십시오.

### <a name="the-profile-site-marker-is-not-pointing-to-any-webpage"></a>프로필 사이트 마커가 어떤 웹 페이지도 가리키지 않음

이 문제는 **프로필** 사이트 마커를 사용할 수 있지만 웹 페이지를 가리키고 있지 않을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **프로필** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 프로필 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="the-profile-site-marker-is-pointing-to-a-deactivated-web-page"></a>프로필 사이트 마커가 비활성 웹 페이지를 가리키고 있음

이 문제는 **프로필** 사이트 마커를 사용할 수 있지만 비활성화된 웹 페이지를 가리키고 있을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **프로필** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 프로필 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="an-active-page-not-found-site-marker-is-not-available-for-this-portal"></a>이 포털에 활성 '페이지 없음' 사이트 마커를 사용할 수 없음

이 문제는 포털 구성에서 **페이지 없음** 사이트 마커를 사용할 수 없을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  다음 값을 사용하여 새 사이트 마커를 만듭니다. 
  - **이름**: 페이지 없음
  - **웹 사이트**: 포털 호스트의 웹 사이트를 선택하십시오.
  - **페이지**: 포털의 '페이지 없음' 페이지로 설정된 웹 페이지 레코드를 선택하십시오.

### <a name="the-page-not-found-site-marker-is-not-pointing-to-any-webpage"></a>'페이지 없음' 사이트 마커가 어떤 웹 페이지도 가리키지 않음

이 문제는 **페이지 없음** 사이트 마커를 사용할 수 있지만 웹 페이지를 가리키고 있지 않을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **페이지 없음** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 '페이지 없음' 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="the-page-not-found-site-marker-is-pointing-to-a-deactivated-web-page"></a>'페이지 없음' 사이트 마커가 비활성 웹 페이지를 가리키고 있음

이 문제는 **페이지 없음** 사이트 마커를 사용할 수 있지만 비활성화된 웹 페이지를 가리키고 있을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **페이지 없음** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 '페이지 없음' 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="an-active-access-denied-site-marker-is-not-available-for-this-portal"></a>이 포털에 활성 '액세스 거부' 사이트 마커를 사용할 수 없음

이 문제는 포털 구성에서 **액세스 거부** 사이트 마커를 사용할 수 없을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  다음 값을 사용하여 새 사이트 마커를 만듭니다. 
  - **이름**: 액세스 거부
  - **웹 사이트**: 포털 호스트의 웹 사이트를 선택하십시오.
  - **페이지**: 포털의 '액세스 거부' 페이지로 설정된 웹 페이지 레코드를 선택하십시오.

### <a name="the-access-denied-site-marker-is-not-pointing-to-any-webpage"></a>'액세스 거부' 사이트 마커가 어떤 웹 페이지도 가리키지 않음

이 문제는 **액세스 거부** 사이트 마커를 사용할 수 있지만 웹 페이지를 가리키고 있지 않을 때 발생합니다. 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **액세스 거부** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 '액세스 거부' 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="the-access-denied-site-marker-is-pointing-to-a-deactivated-web-page"></a>'액세스 거부' 사이트 마커가 비활성 웹 페이지를 가리키고 있음

이 문제는 **액세스 거부** 사이트 마커를 사용할 수 있지만 비활성화된 웹 페이지를 가리키고 있을 때 발생합니다(루트 또는 콘텐츠 페이지가 비활성화될 수 있음). 이 문제를 해결하려면

1.  [포털 관리 앱](configure/configure-portal.md)을 엽니다.
2.  왼쪽 창에서 **사이트 마커**를 선택합니다.
3.  **액세스 거부** 사이트 마커 레코드를 찾습니다.
4.  포털의 활성 '액세스 거부' 페이지를 가리도록 **페이지** 필드를 업데이트합니다.

### <a name="profile-web-form-is-not-available-for-contact-entity"></a>연락처 엔터티에 프로필 웹 양식을 사용할 수 없음

프로필 페이지는 포털에서 모든 프로필 관련 문제에 사용되는 일반적인 페이지 중 하나입니다. 이 페이지는 사용자가 자신의 프로필을 업데이트하는 데 사용할 수 있는 양식을 보여줍니다. 이 페이지에 사용된 양식은 연락처 엔터티에서 사용 가능한 **프로필 웹 페이지** 기본 양식에서 가져옵니다. 이 양식은 포털이 프로비저닝될 때 귀하의 Common Data Service 환경에서 생성됩니다. 이 오류는 포털에서 **프로필** 웹 양식이 삭제되거나 비활성화되었을 때 발생합니다. 이 양식은 필수이며 이 양식을 삭제하거나 비활성화하면 포털에서 전체 웹 사이트에 런타임 오류가 발생할 수 있습니다. 이는 복구할 수 없는 상태이며 환경에서 포털을 다시 설치해야 합니다.

### <a name="published-state-is-not-available-for-this-website"></a>이 웹 사이트에 게시된 상태를 사용할 수 없음

이 문제를 해결하려면 게시 상태 엔터티 **게시됨**을 사용할 수 있고 활성 상태인지 확인하십시오.

### <a name="published-state-is-not-visible"></a>게시된 상태가 표시되지 않음

이 문제를 해결하려면 게시 상태 엔터티 **게시됨**에 **isVisible** 확인란이 선택되어 있는지 확인하십시오.

### <a name="list-of-entities-with-search-result-having-invalid-url"></a>검색 결과에 잘못된 URL이 있는 엔터티 목록

이 문제를 해결하려면 엔터티에 적절한 보안 권한이 있는지 확인하십시오.

### <a name="list-of-entities-with-cms-security-check-failed"></a>CMS 보안 검사에 실패한 엔터티 목록

이 문제를 해결하려면 엔터티에 적절한 검색 페이지가 있는지 확인하십시오.

### <a name="web-file-is-not-active"></a>웹 파일이 활성 상태가 아님

이 문제를 해결하려면 웹 파일이 활성 상태인지 확인하십시오.

### <a name="the-partial-url-of-web-file-is-misconfigured"></a>웹 파일의 부분 URL이 잘못 구성됨

이 문제를 해결하려면 부분 URL이 루트 페이지로 홈을 사용하는 파일 이름인지 확인하십시오.

### <a name="web-file-doesnt-have-a-file-attachment"></a>웹 파일에 첨부 파일이 없음

이 문제를 해결하려면 웹 파일의 메모 섹션에 해당 CSS 파일을 추가합니다.

### <a name="file-attachment-doesnt-have-content"></a>첨부 파일에 콘텐츠가 없음

이 문제를 해결하려면 웹 파일의 메모 섹션에 전체 콘텐츠가 있는 CSS 파일을 추가합니다.

### <a name="mime-type-of-file-is-not-textcss"></a>파일의 MIME 형식이 텍스트/css가 아님

이 문제를 해결하려면 CSS 파일의 MIME 형식을 다시 정의하는 플러그 인 또는 흐름이 없는지 확인하십시오.