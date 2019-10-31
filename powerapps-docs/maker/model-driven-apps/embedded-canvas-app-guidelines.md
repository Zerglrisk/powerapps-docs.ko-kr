---
title: 포함된 캔버스 앱 작업 지침 | MicrosoftDocs
ms.custom: ''
ms.date: 08/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>포함된 캔버스 앱 작업 지침
이 항목에서는 포함된 캔버스 앱 작업에 대한 지침과 발생할 수 있는 문제를 해결하는 유용한 팁을 제공합니다.

-   포함된 캔버스 앱은 통합 인터페이스 모델 기반 앱에서만 지원됩니다.
-   양식마다 포함된 캔버스 앱을 하나만 사용할 수 있습니다. 
     - 여러 개의 포함된 캔버스 앱을 양식에 추가할 수 있지만 한 번에 하나씩만 활성화할 수 있습니다.
     - 모델 기반 양식에서 둘 이상의 포함된 캔버스 앱을 사용하도록 설정하려고 하면 "한 캔버스 앱만 양식에서 사용할 수 있습니다" 라는 메시지가 표시됩니다.
     - 포함된 캔버스 앱을 사용하거나 사용하지 않도록 설정하려면 [포함된 캔버스 앱 사용](#enable-an-embedded-canvas-app) 및 [포함된 캔버스 앱 사용 안 함](#disable-an-embedded-canvas-app)을 참조하세요.
-   포함된 캔버스 앱을 모델 기반 양식에 추가하는 경우 항상 값이 보장되는 필수 필드를 사용합니다. 필드에 값이 없는 경우 포함된 캔버스 앱은 호스트 모델 기반 양식의 데이터 변경에 대한 응답으로 새로 고쳐지지 않습니다.
-   모델 기반 양식을 게시해도 포함된 캔버스 앱이 게시되지 않습니다.
     - 포함된 캔버스 앱은 호스트 모델 기반 양식과 독립적으로 게시해야 합니다. 자세한 내용: [앱 게시](../canvas-apps/save-publish-app.md#publish-an-app).
-   웹 브라우저 팝업 차단으로 인해 캔버스 앱 컨트롤 속성의 **사용자 지정** 단추를 통해 포함된 캔버스 앱을 만들거나 편집하기 위해 PowerApps Studio를 열 경우 web.powerapps.com 사이트를 사용하도록 설정하거나 일시적으로 팝업 차단을 사용하지 않도록 설정한 다음 **사용자 지정**을 다시 선택합니다.
-   포함된 캔버스 앱은 레코드 컨텍스트가 전달될 필요가 있기 때문에 새 레코드를 만들때 표시되지 않습니다.
-   ModelDrivenFormIntegration.Item 개체는 읽기 전용입니다. 
     - 데이터를 다시 쓰려면 Common Data Service 커넥터를 사용해야 합니다. 추가 정보: [Common Data Service](/connectors/commondataservice/)
-   포함된 캔버스 앱은 호스트 모델 기반 양식을 통해서만 생성할 수 있습니다. 
    - 모델 기반 양식에 포함된 기존 캔버스 앱을 추가하는 기능은 현재 지원되지 않습니다.
    - 향후 업데이트에서 앱 ID를 사용하여 모델 기반 양식에 기존 캔버스 앱을 포함시키는 지원이 제공됩니다.
- 포함된 캔버스 앱을 사용하여 모델 기반 양식을 볼 때 "해당 앱을 찾지 못했습니다. 죄송합니다" 라는 오류 메시지가 표시 되면 포함된 캔버스 앱이 모델 기반 양식과 동일한 솔루션에 있는지 확인합니다.
- 포함된 캔버스 앱을 사용하여 모델 기반 양식을 볼 때 "이 응용 프로그램에 대한 액세스 권한이 없는 것 같습니다" 라는 오류 메시지가 표시되는 경우. 담당자에게 공유하도록 요청" 작성자가 포함된 캔버스 앱을 공유했는지 확인합니다. 자세한 내용: [포함된 캔버스 앱 공유](share-embedded-canvas-app.md).
- 더 이상 하위 표 컨트롤에 캔버스 앱을 추가할 수 없습니다.
    - 미리 보기 릴리스에서 제조업체는 하위 표 컨트롤에 캔버스 앱을 추가할 수 있었습니다. 현재 일반적으로 사용 가능한 모델 중심 양식에 캔버스 앱 포함 기능을 사용하면 모델 중심 양식에 포함된 캔버스 앱을 추가하는 것이 필드로 간소화됩니다. 
    - 따라서 제조업체는 현재(기본 양식) 레코드를 데이터 컨텍스트로 전달할지 또는 현재(기본 양식) 레코드와 관련된 레코드 목록을 전달할지 여부를 미리 결정할 필요가 없기 때문에 더 쉽습니다. 
    - 제조업체는 항상 필드로 시작하여 현재(기본 양식) 레코드 또는 현재(기본 양식) 레코드와 관련된 레코드 목록에 모두 액세스할 수 있습니다.
    - 캔버스 앱에서 관련 레코드 목록에 액세스하기 위해 제조업체는 Common Data Service 커넥터 및 [필터](../canvas-apps/functions/function-filter-lookup.md) 기능을 캔버스 앱에서 활성화된 [데이터 원본 경험 및 Common Data Service 보기 개선](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/) 기능과 함께 사용할 수 있습니다.  
    예를 들어 *연락처* 엔터티의 *활성 연락처* 보기에 액세스하기 위해 제조업체는 *Filter(Contacts, 'Contacts (Views)'.'Active Contacts')* 를 사용할 수 있습니다.
    - 하위 표 컨트롤을 사용하는 기존 캔버스 앱은 계속 작동합니다. 그러나 대신 필드를 사용하도록 이러한 앱을 마이그레이션하는 것이 좋습니다. 자세한 내용은 [현재(기본 양식) 레코드와 관련된 레코드 목록을 사용하는 모델 기반 양식에 포함된 캔버스 앱 마이그레이션](embedded-canvas-app-migrate-from-preview.md#migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record)을 참조하십시오.

## <a name="enable-an-embedded-canvas-app"></a>포함된 캔버스 앱 사용
1. 포함된 캔버스 앱으로 표시하도록 사용자 지정된 필드를 선택합니다.
2. **필드 속성** 대화 상자에서 **컨트롤** 탭을 선택합니다.
3. 컨트롤 목록에서 **캔버스 앱**을 선택한 다음 **웹** 옵션을 선택합니다.
4. **확인**을 선택합니다.

## <a name="disable-an-embedded-canvas-app"></a>포함된 캔버스 앱 사용 안 함
1. 포함된 캔버스 앱으로 표시하도록 사용자 지정된 필드를 선택합니다.
2. **필드 속성** 대화 상자에서 **컨트롤** 탭을 선택합니다.
3. 컨트롤 목록에서 기본 컨트롤을 선택한 다음 **웹** 옵션을 선택합니다.
4. **확인**을 선택합니다.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>포함된 캔버스 앱의 알려진 문제 및 제한사항
- Canvas 앱 사용자 지정 컨트롤은 **웹** 클라이언트 유형 사용에만 지원 됩니다. 현재 **전화** 및 **태블릿** 클라이언트 유형은 지원되지 않습니다.
- ModelDrivenFormIntegration 컨트롤은 관련 엔터티의 필드 값을 제공하지 않습니다. 
  - 예를 들어 ModelDrivenFormIntegration 컨트롤이 Accounts 엔터티에 연결되어 있는 경우 *ModelDrivenFormIntegration.Item.’Primary Contact’.’Full Name’* 은 값을 반환하지 않습니다. 
  - 관련 엔터티 제조업체의 필드에 액세스하려면 여기에 나열된 식 중 하나를 사용할 수 있습니다.
    - *LookUp(Accounts, Account = GUID(First(ModelDrivenFormIntegration.Data).ItemId)).'Primary Contact'.'Full Name'*  
      - *ItemId*는 작성 시 비어 있지만 런타임 시 값을 갖습니다.
    - *LookUp(Accounts, Account = ModelDrivenFormIntegration.Item.Account).'Primary Contact'.'Full Name'*(이 식이 읽기 쉽지만 이전 식이 약간 더 잘 작동합니다.)
- 앱 사용자에게 포함된 또는 독립형 캔버스 앱에 대한 액세스 권한을 부여하기 위해 보안 역할의 **캔버스 앱** 권한을 사용할 수 없습니다. 포함된 캔버스 앱 공유에 대한 자세한 내용은 [포함된 캔버스 앱 공유](share-embedded-canvas-app.md)를 참조하세요.
- 호스트 모델 기반 양식에 표시되는 것과 동일한 데이터를 다시 작성하면 양식이 새로 고쳐질 때까지 이전 데이터를 계속 표시합니다. 이 작업을 수행하는 쉬운 방법은 [RefreshForm](embedded-canvas-app-actions.md#refreshformshowprompt) 메서드를 사용하는 것입니다.

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
