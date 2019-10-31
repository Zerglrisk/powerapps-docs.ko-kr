---
title: 레거시 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환 빠른 시작 | MicrosoftDocs
description: 기존 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환하는 방법 알아보기
ms.custom: ''
ms.date: 09/11/2019
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
ms.assetid: 14c4c18c-927c-4ea2-ba66-0531285a99a7
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="quick-start-for-transitioning-your-legacy-web-client-application-to-unified-interface"></a>레거시 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환 빠른 시작

통합 인터페이스 프레임워크는 응답성이 뛰어난 웹 디자인 원칙을 사용하여 모든 화면 크기, 장치 또는 방향에 최적화된 보기 및 상호 작용 환경을 제공합니다. 이 빠른 시작 항목은 새로운 프로덕션 이외의 환경을 사용하여 레거시 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환하는 방법을 설명합니다. 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE3JwWU]

기존의 프로덕션 이외의 환경을 사용하여 웹 클라이언트 애플리케이션을 전환하려면 [통합 인터페이스에서 기존 환경을 사용하여 기존 웹 클라이언트 앱의 유효성을 검사하기 위한 빠른 시작](transition-web-app-existing.md)을 참조하십시오. 
## <a name="prerequisites"></a>필수 구성 요소
- 레거시 웹 클라이언트 애플리케이션. 
- 필수는 아니지만 프로덕션 이외의 환경을 사용하여 응용 프로그램을 테스트하고 현재 배포 또는 개발 주기에 영향을 미치지 않는지 확인하십시오. 추가 정보: [샌드박스 인스턴스 관리](/dynamics365/admin/manage-sandbox-instances)

## <a name="prepare-the-environment"></a>환경 준비
먼저 프로덕션 이외의 환경을 선택하고 **통합 인터페이스만 사용** 모드를 활성화하고, 환경의 모든 모델 중심 앱에 통합 인터페이스를 사용합니다. 여기에는 레거시 웹 클라이언트용으로 원래 구성된 Dynamics 365 애플리케이션 모듈도 포함됩니다.

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 **환경**을 선택한 다음, 샌드박스 환경을 선택합니다. 

2. **설정** > **동작**을 선택한 다음, **통합 인터페이스만 사용**을 켭니다.

   > [!div class="mx-imgBorder"] 
   > ![통합 인터페이스만 사용 설정](media/use-unified-interface-only-pac.png)

설정 영역에서 이를 설정할 수도 있습니다. **설정** > **관리** > **시스템 설정**으로 이동한 다음, **일반** 탭에서 **통합 인터페이스만 사용**을 **예**로 설정합니다.

> [!div class="mx-imgBorder"] 
> ![새 통합 인터페이스만 사용](media/use-unified-interface-only.png "새 통합 인터페이스만 사용")


> [!NOTE]
> 환경을 이전 상태로 다시 전환해야 하는 경우 통합 인터페이스 설정을 전환하여 원래 인터페이스로 되돌릴 수 있습니다. 추가 정보: [통합 인터페이스만 사용](/dynamics365/customer-engagement/admin/enable-unified-interface-only)

## <a name="run-and-validate-your-application-in-the-unified-interface"></a>통합 인터페이스에서 응용 프로그램 실행 및 유효성 검사
원래 웹 클라이언트 애플리케이션인 응용 프로그램을 실행합니다. **통합 인터페이스만 사용**을 켠 후 응용 프로그램이 원래 웹 클라이언트용으로 구성되어 있어도 환경에서 사용 가능한 모든 앱은 통합 인터페이스를 사용합니다.

앱을 실행하려면 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 **앱**을 누른 다음 실행할 응용 프로그램을 선택합니다. 또는 바로 *https://contoso.crm.dynamics.com/apps/* 와 같은 **내 앱** 페이지로 이동할 수도 있습니다.

### <a name="validate-your-app-processes-and-customizations"></a>앱, 프로세스 및 사용자 지정 유효성 검사 
모든 사용 사례를 테스트하는 것이 좋습니다. 가장 중요한 사용 사례로 시작하거나 논리적 디자인 패턴으로 그룹화할 수 있습니다. 통합 인터페이스는 반응형 디자인을 기반으로 하기 때문에 화면 해상도가 다른 여러 장치에서 테스트를 수행하는 것이 좋습니다. 응용 프로그램을 테스트할 때 사용자 지정 내용이 통합 인터페이스와 호환되는지, 그리고 재설계가 필요하거나 기능이 누락된 기능이 있는지 확인할 수 있습니다. 이러한 요소를 검토하기 위한 계획을 세우고 커뮤니티 포럼에 질문과 의견을 게시하십시오. 

> [!IMPORTANT]
> Common Data Service 현재 버전 및 Dynamics 365의 모델 기반 앱에는 여전히 더 이상 사용되지 않는 기능이 포함되어 있습니다. 더 이상 사용되지 않는 기능이 있는지 응용 프로그램을 검토하고 필요에 따라 새 기능으로 교체해야 합니다. 추가 정보: [중요한 변경 사항(사용 중지)](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

### <a name="dynamics-365-apps"></a>Dynamics 365 앱
Dynamics 365 Field Service 또는 Dynamics 365 Project Service Automation 앱을 사용하고 통합 인터페이스를 테스트하려는 경우 새 샌드박스 환경을 설정하고 프로덕션 환경의 사본을 작성하여 통합 인터페이스에서 이러한 응용 프로그램의 유효성을 검사하기 전에 최신 Field Service 버전 및 Project Service Automation 버전으로 업그레이드해야 합니다. 이렇게 하려면 다음 단계를 수행합니다.

1. [Power Platform 관리 센터](https://admin.powerplatform.microsoft.com/environments) 또는 [Dynamics 365 관리 센터](https://port.crm.dynamics.com/)에서 새로운 샌드박스 환경을 만듭니다. 추가 정보: [신청에 인스턴스 추가](/dynamics365/customer-engagement/admin/add-instance-subscription)

2. Dynamics 365 Field Service 또는 Dynamics 365 Project Service Automation 앱이 있는 프로덕션 환경을 새 샌드박스 환경으로 복사합니다. 이렇게 하려면 Power Platform 관리 센터에서 프로덕션 환경을 연 다음 **복사**를 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![환경 복사](media/ppac-copy-environment.png "환경 복사")

3. **환경 복사** 페이지에서 **모두**를 선택하고 **덮어쓸 환경 선택** 목록에서 새 샌드박스 환경을 선택한 다음, **복사**를 선택합니다. 

    > [!div class="mx-imgBorder"] 
    > ![환경 덮어쓰기](media/ppac-copy-overwrite.png "환경 덮어쓰기")

4. **환경 덮어쓰기** 대화 상자가 나타납니다. 올바른 환경을 선택했는지와 올바른 옵션을 선택했는지 확인한 다음 **확인**을 선택합니다. 

5. 복사가 성공하면 확인 알림이 나타납니다. 

6. 메뉴 모음에서 **솔루션 관리**를 선택하여 **솔루션** 영역을 엽니다. 

    > [!div class="mx-imgBorder"] 
    > ![솔루션 관리](media/ppac-manage-solutions.png "솔루션 관리")

    > [!IMPORTANT]
    > **관리 모드**가 활성화된 경우 **솔루션** 영역을 볼 수 있도록 비활성화해야 합니다. 추가 정보: [관리 사용](/power-platform/admin/sandbox-environments#administration-mode)

7. Field Service 또는 Project Service Automation 솔루션을 찾아서 선택합니다. **업그레이드** 옵션은 사용할 수 있어야 합니다. 선택하여 솔루션을 업그레이드합니다. 

    > [!div class="mx-imgBorder"] 
    > ![솔루션 업그레이드](media/ppac-upgrade-solution.png "솔루션 업그레이드")
    
> [!NOTE]
> 통합 인터페이스의 최신 버전의 Field Service 및 Project Service Automation은 기본적으로 새로 생성된 인스턴스에 사용할 수 있습니다. 이전 버전이 설치된 기존 환경을 업그레이드하려는 경우 [Microsoft 고객 지원](https://go.microsoft.com/fwlink/?LinkId=853505)에 연락하여 업그레이드를 요청해야 합니다. 

추가 정보: [Dynamics 365 for Field Service 최신 버전](/dynamics365/customer-engagement/field-service/version-history#latest-versions) 및 [Dynamics 365 for Project Service Automation 업그레이드 홈페이지](/dynamics365/customer-engagement/project-service/upgrade-psa-home-page)

## <a name="next-steps"></a>다음 단계
결과를 바탕으로 구현 팀 또는 파트너는 응용 프로그램을 통합 인터페이스로 전환하는 데 필요한 노력의 양을 추정하고 잠재적 유용성 개선을 식별할 수 있습니다. 통합 인터페이스에서 여러 가지 새로운 기능을 사용할 수 있으므로 응용 프로그램 사용자의 가치를 높일 수 있습니다. 

통합 인터페이스로 전환하면 최신 사용자 인터페이스를 만들고 기존 프로세스를 다시 방문하여 여전히 유효하거나 개선이 필요한지 확인할 수 있습니다. 또한 응용 프로그램이 비즈니스 요구 사항을 반영하는지 여부와 기존 응용 프로그램을 다양한 팀과 역할을 위해 여러 응용 프로그램에 분산시킬 수 있는지 여부를 고려해야 합니다.
추가 정보: [앱 디자이너를 사용하여 모델 중심 앱 설계](design-custom-business-apps-using-app-designer.md)  

### <a name="see-also"></a>참조
<!-- Unified Interface transition community (link tbd) <br />  -->
[통합 인터페이스 플레이북](unified-interface-playbook.md) <br />
[사용자 경험 및 통합 인터페이스 전환 접근](approaching-unified-interface.md) <br />
[통합 인터페이스 정보](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[PowerApps의 모델 기반 앱이란 무엇입니까?](model-driven-app-overview.md) <br />
[통합 인터페이스로 앱 업데이트](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[모델 기반 앱 상호 작용 환경 대시보드 구성](configure-interactive-experience-dashboards.md) <br />
[모델 기반 앱 데이터 시각화를 위한 사용자 지정 컨트롤 사용](use-custom-controls-data-visualizations.md) <br />
[PowerApps component framework 개요](/powerapps/developer/component-framework/overview) <br />
[모든 사용자를 위한 통합 인터페이스](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)

