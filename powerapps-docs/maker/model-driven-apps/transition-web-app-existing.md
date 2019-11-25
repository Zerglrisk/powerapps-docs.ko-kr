---
title: 기존 환경을 사용하여 통합 인터페이스로 기존 웹 클라이언트 앱의 유효성을 검사하기 위한 빠른 시작 | MicrosoftDocs
description: 기존 웹 클라이언트에서 통합 인터페이스로 전환을 계획하고 실행하는 방법에 대해 알아보십시오.
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
ms.assetid: ''
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e39cb11b9883e93d341232bcdcbb43dc17fa491a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759783"
---
# <a name="quick-start-for-using-an-existing-environment-to-validate-your-legacy-web-client-app-with-the-unified-interface"></a>기존 환경을 사용하여 통합 인터페이스로 기존 웹 클라이언트 앱의 유효성을 검사하기 위한 빠른 시작
이 빠른 시작 항목은 기존 환경을 사용하여 현재 구성 또는 기본 솔루션을 기반으로 통합 인터페이스 응용 프로그램을 만드는 방법을 보여줍니다. 이를 통해 기존 레거시 웹 클라이언트 애플리케이션을 병렬로 실행하면서 통합 인터페이스를 탐색하고 테스트할 수 있습니다. 그런 다음 사용자는 나란히 보기 위해 환경 간에 전환할 수 있습니다. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3JzyI]

테스트를 분리하고 통합 인터페이스 환경만 보는 새로운 샌드박스 환경을 만드는 방법을 보여주는 유사한 지침은 다음을 참조하십시오. [Dynamics 365 레거시 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환하기 위한 빠른 시작](transition-web-app.md)을 참조하십시오.

> [!IMPORTANT]
>  Dynamics 365 Field Service 또는 Dynamics 365 Project Service Automation 앱이 있는 환경의 경우 [Dynamics 365 앱](transition-web-app.md#dynamics-365-apps)을 참조하십시오.

## <a name="prerequisites"></a>필수 구성 요소 
- 기존 Dynamics 365 Sales 또는 서비스 레거시 웹 클라이언트 애플리케이션. 
- 필수는 아니지만 프로덕션 이외의 환경을 사용하여 응용 프로그램을 테스트하는 것이 좋습니다. 추가 정보: [샌드박스 인스턴스 관리](/dynamics365/customer-engagement/admin/manage-sandbox-instances) 

## <a name="overview"></a>개요 
이 항목은 현재 통합 인터페이스로의 전환을 계획하고 실행해야 하는 레거시 웹 클라이언트 애플리케이션을 사용 중인 기존 고객을 위한 것입니다. 병렬 환경을 설정하려면 현재 기본 솔루션을 기반으로 새 응용 프로그램을 만듭니다. 이는 기존 작업에 영향을 주지 않고 현재 개발 샌드박스 환경에서 수행할 수 있습니다.

이 문서의 단계를 완료한 후 적절한 역할을 가진 사용자는 Dynamics 365 드롭다운 앱 목록 또는 Dynamics 365 홈 페이지(https://home.dynamics.com)의 앱 목록에서 새 앱을 볼 수 있습니다.

![앱 목록](media/app-list.png)

솔루션을 사용하여 개발 환경에서 이 항목에 설명된 작업을 완료하면 솔루션을 테스트 환경으로 가져와서 더 많은 비즈니스 사용자 그룹이 익숙한 환경에서 앱을 테스트하고 비교할 수 있습니다. 

ALM(Application Lifecycle Management) 및 개발 운영 프로세스를 따르십시오. 솔루션 컨텍스트 내부에 설명된 모든 단계를 수행하는 것이 좋습니다. 개발 환경에서 앱을 테스트하고 검증한 후에는 프로덕션 환경과 같이 더 많은 사용자에게 파일럿 프로그램으로 앱을 시작하여 앱을 추가로 테스트할 수 있습니다. 솔루션 내에 모델 중심의 앱 및 사이트 맵이 있으면 환경 파이프라인의 기존 프로세스에 따라 이 새 앱을 만든 환경에서 앱을 내보낼 수 있습니다. 

## <a name="process-for-validating-your-legacy-web-client-app-in-an-existing-environment"></a>기존 환경에서 레거시 웹 클라이언트 앱의 유효성을 검사하는 프로세스
 
기존 환경에서 레거시 웹 클라이언트 앱의 유효성을 검사하는 프로세스는 다음 세 단계를 포함합니다.  

1.  기본 솔루션을 기반으로 새 솔루션 만들기
2.  새 모델 기반 앱 만들기 
3.  앱 속성 구성  

최근에 개발 환경에서 **통합 인터페이스만 사용** 모드를 **켜기**로 전환한 경우(예: [Dynamics 365 레거시 웹 클라이언트 애플리케이션을 통합 인터페이스로 전환하기 위한 빠른 시작](transition-web-app.md) 항목의 지침에 따라) 기존 레거시 웹 클라이언트 앱을 실행할 수 있도록 설정을 다시 **끄기**로 설정해야 합니다.

### <a name="create-a-new-solution-thats-based-on-the-default-solution"></a>기본 솔루션을 기반으로 새 솔루션 만들기
1. [PowerApps 제조업체 포털](https://make.powerapps.com)에 로그인합니다.   
2. 환경 목록에서 원하는 환경을 선택합니다.  
3. 왼쪽 탐색 창에서 **솔루션**을 선택합니다. 
4. 메뉴 모음에서 **새 솔루션**을 선택합니다. 
5. **새 솔루션**창에서 다음 속성을 입력합니다. 
   - **이름**: 솔루션의 이름을 입력합니다. 예를 들어, *통합 인터페이스 앱*. 
   - **게시자**. 조직에서 사용하는 게시자를 선택합니다. 기존 사용자 지정에 대한 사용자 지정 거버넌스를 따르십시오. 이를 통해 모델 중심 앱 및 사이트 맵의 스키마 이름이 기존 표준과 일치하게 됩니다. 
   - **버전:** 이는 기존 표준 및 솔루션 거버넌스에 따라 설정해야 합니다. 
6. **만들기**를 선택합니다.  
7. 새 솔루션이 솔루션 목록에 생성됩니다. 솔루션을 열고 다음 섹션으로 이동하려면 선택합니다. 

### <a name="create-a-new-model-driven-app-in-the-new-solution"></a>새로운 솔루션에서 새 모델 중심 앱 만들기
이 단계에서는 통합 인터페이스에서 경험할 수 있도록 기존 사용자 지정을 활용하는 새로운 앱을 만듭니다. 이전 섹션에서 만든 새 솔루션의 컨테이너 내에 앱을 만듭니다.  

1. 메뉴 모음에서 **새로 만들기**를 선택하고 **앱**을 가리킨 다음 **모델 중심 앱**을 선택합니다.
2. **새 앱 만들기** 페이지에서 다음 속성을 입력합니다. 
   - **이름**: 적합하다고 생각되는 응용 프로그램의 이름을 입력합니다. 예를 들어 *사용자 응용 프로그램 이름* + *새로 만들기* 또는 *통합 인터페이스 테스트*. 
   - **고유 이름:** 솔루션 접두사와 사용자가 지정한 앱 이름의 단순화된 버전으로 시작합니다. 표시된 대로 변경하거나 그대로 둘 수 있습니다.  
   - **설명**. 앱에 대한 설명을 추가합니다(예: *솔루션의 새로운 통합 인터페이스 테스트 목적*).  
3. **기존 솔루션을 사용하여 앱 만들기**를 선택한 후 **다음**을 선택합니다. 
4. **솔루션 선택** 목록에서 **기본 솔루션**을 선택하고 **사이트 맵 선택** 목록에서 **사이트 맵**을 선택한 다음 **완료**를 선택합니다.  

   > [!div class="mx-imgBorder"] 
   > ![기존 솔루션 선택](media/select-existing-solution.png "기존 솔루션 선택")

5. 앱 디자이너가 열리고 기본 솔루션에 있던 모든 앱 구성 요소가 표시됩니다. **게시**를 선택합니다.  
6. 게시 프로세스가 완료된 후 **재생**을 선택합니다.  

기본 Dynamics 365 응용 프로그램에 있는 모든 엔터티, 사이트 맵 및 사이트 맵 사용자 지정이 포함된 새 모델 중심 앱이 포함된 새 창이 브라우저에서 열립니다.  

> [!div class="mx-imgBorder"] 
> ![새 통합 인터페이스 앱](media/new-unified-interface-app.png "새 통합 인터페이스 앱")

PowerApps 제조업체 포털 **솔루션** 영역을 사용하여 브라우저 탭으로 돌아가면 새 모델 중심 앱 및 비슷한 이름의 사이트 맵 클라이언트 확장 프로그램은 모두 사용자가 생성한 솔루션의 일부입니다.  

> [!div class="mx-imgBorder"] 
> ![솔루션 자산](media/solution-assets.png "솔루션 자산")

이 단계에서는 솔루션 내부에 새로운 모델 중심 앱을 만들었습니다. 이 앱을 사용하여 테스트 또는 평가 환경으로 가져올 수 있습니다. 지금 새 앱을 경험할 수는 있지만 그렇게 하기 전에 다음 단계에서 새 앱에 대한 몇 가지 설정을 구성합니다. 이렇게 하면 다른 사용자와 공유할 수 있습니다.

### <a name="configure-app-properties"></a>앱 속성 구성
모델 중심 앱 속성을 구성하는 데 필요한 작업은 다음과 같습니다. 

- 관리자가 아닌 사용자가 앱을 사용할 수 있도록 새 역할에 사용자 역할을 할당합니다.  
- 익숙한 URL을 사용자 지정하여 새 앱에 대한 바로 가기를 사용자가 쉽게 공유, 책갈피에 추가 또는 기억할 수 있습니다. 


1. *환경 URL*/**앱**으로 이동합니다. URL은 다음과 유사합니다. https://*사용자 환경*. crm.dynamics.com/apps. 그렇게 하면 환경의 모든 앱 목록이 열립니다. 
2. 생성한 새 모델 중심 앱을 찾습니다.  
3. 앱 타일에서 줄임표를 선택한 다음 **역할 관리**를 선택합니다.   

   > [!div class="mx-imgBorder"] 
   > ![역할 관리](media/select-app-ellipsis.png "역할 관리")

4. 사용 가능한 역할 영역이 오른쪽 창에 표시됩니다. 관리자가 아닌 사용자에게 앱에 대한 액세스 권한을 부여하는 데 필요한 역할을 선택합니다. 

    > [!IMPORTANT]
    > 모든 사용자에게 **모델 중심 앱**에 대한 **읽기** 액세스 권한이 포함된 보안 역할이 하나 이상 부여되어 있는지 확인하십시오. 이 권한은 보안 역할 내의 사용자 지정 탭에서 찾을 수 있습니다. 이 권한이 없는 사용자는 모델 기반 앱을 열 때 오류가 발생합니다.  시스템 관리자 및 시스템 사용자 지정자 보안 역할에는 이 권한이 이미 설정되어 있습니다. 
 
   > [!div class="mx-imgBorder"] 
   > ![모델 기반 앱 권한](media/model-driven-app-privilege.png "모델 기반 앱 권한")

5. 선택적으로 **역할 관리** 창에서 **앱 URL 접미사**를 확장하여 모델 중심 앱의 친숙한 URL을 사용자 지정할 수 있습니다. 대부분의 항목을 지정할 수 있습니다. 예를 들어, 미리 보기에 URL *https://YourEnvironment.crm.dynamics.com/apps/new*이 표시되도록 *새로* 입력합니다.   

   > [!div class="mx-imgBorder"] 
   > ![앱 URL 접미사](media/app-url-suffix.png "앱 URL 접미사")

   이는 사용자가 통합 인터페이스의 경험을 직접 시작할 수 있도록 사용하기 쉽고 공유하기 쉬운 URL이 됩니다. 사용자는 편의를 위해 이 링크를 책갈피에 추가할 수 있습니다. 

6. **저장**을 선택합니다. 

이제 적절한 역할을 가진 사용자는 Dynamics 365 드롭다운 앱 목록 또는 Dynamics 365 홈 페이지(https://home.dynamics.com)의 앱 목록에서 새 앱을 볼 수 있습니다. 
  
   ![앱 목록](media/app-list.png "앱 목록")

**통합 인터페이스만 사용** 모드가 **끄기**로 설정되어 있기 때문에 사용자가 환경의 루트 URL로 이동하면 여전히 전처럼 기본 **Dynamics 365 – 사용자 지정** 응용 프로그램에서 시작됩니다. 통합 인터페이스 앱을 테스트하고 작업하면서 기존 레거시 웹 클라이언트 앱을 계속 지원하려는 경우에 예상됩니다.  

## <a name="compare-your-new-app-to-the-default-dynamics-365-app"></a>새 앱을 기본 Dynamics 365 앱과 비교  
이제 앱을 시작할 준비가 되었습니다. 동일한 환경에 있기 때문에 동일한 데이터, 사용자 역할, 비즈니스 규칙, 워크플로, 플러그 인 등을 사용하여 새 통합 인터페이스 앱을 Dynamics 365 – 사용자 지정 앱과 비교할 수 있습니다. 이를 통해 모든 핵심 기본 요소가 여전히 존재함을 조직에 알리고 동시에 새로운 통합 인터페이스 향상 기능을 탐색할 수 있습니다.  

> [!TIP]
> 하나의 모니터에 앱을 나란히 표시하려면 Windows 및 왼쪽 화살표 키(또는 오른쪽 화살표 키)를 함께 눌러 브라우저 창을 동일한 모니터로 분할할 수 있습니다. 

> [!NOTE]
> 탐색의 변경 또는 단추 및 동작에 대한 더 깊은 리본 사용자 지정과 같은 기본 사이트 맵에서 사용자 지정을 계속 수행하는 경우 다른 모델 기반 앱을 작성하거나 모델 중심 앱과 관련된 새 사이트 맵에서 동일한 사용자 지정을 수행하여 프로세스를 반복해야 합니다.  

## <a name="validate-your-new-app"></a>새 앱 유효성 검사  
응용 프로그램에 통합 인터페이스가 표시되면 응용 프로그램, 프로세스 및 사용자 지정의 유효성 검사를 시작하여 전환될 모습을 확인할 수 있습니다. 모든 사용 사례를 테스트하는 것이 좋지만 가장 중요한 경우부터 시작하거나 논리적 디자인 패턴으로 그룹화할 수 있습니다. 통합 인터페이스는 반응형 디자인을 기반으로 하기 때문에 항상 화면 해상도가 다른 여러 장치에서 테스트를 수행하는 것이 좋습니다. 응용 프로그램을 테스트할 때 사용자 지정 내용이 통합 인터페이스와 호환되는지, 그리고 재설계가 필요하거나 기능이 누락된 기능이 있는지 확인할 수 있습니다.  

> [!IMPORTANT]
> Common Data Service의 현재 버전 및 Dynamics 365의 모델 기반 앱에는 여전히 더 이상 사용되지 않는 기능이 포함되어 있습니다. 더 이상 사용되지 않는 기능이 있는지 응용 프로그램을 검토하고 필요에 따라 새 기능으로 교체해야 합니다. 추가 정보: [중요한 변경 사항(사용 중지)](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

> [!TIP]
> PowerApps 검사기 도구는 솔루션 구성 요소의 품질 검사를 지원합니다.  추가 정보: [솔루션 검사기를 사용하여 PowerApps에서 모델 기반 앱의 유효성 검사](../common-data-service/use-powerapps-checker.md)

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
