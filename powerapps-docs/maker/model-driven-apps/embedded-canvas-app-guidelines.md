---
title: 포함된 캔버스 앱 작업 지침 | MicrosoftDocs
ms.custom: ''
ms.date: 01/07/2019
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
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

이 항목에서는 포함된 캔버스 앱 작업에 대한 지침과 발생할 수 있는 문제를 해결하는 유용한 팁을 제공합니다.

-   포함된 캔버스 앱은 통합 인터페이스 모델 기반 앱에서만 지원됩니다.
-   양식마다 포함된 캔버스 앱을 하나만 사용할 수 있습니다. 
     - 여러 개의 포함된 캔버스 앱을 양식에 추가할 수 있지만 한 번에 하나씩만 활성화할 수 있습니다.
     - 모델 기반 양식에서 둘 이상의 포함된 캔버스 앱을 사용하도록 설정하려고 하면 "한 캔버스 앱만 양식에서 사용할 수 있습니다" 라는 메시지가 표시됩니다.
     - 포함된 캔버스 앱을 사용하거나 사용하지 않도록 설정하려면 [포함된 캔버스 앱 사용](#enable-an-embedded-canvas-app) 및 [포함된 캔버스 앱 사용 안 함](#disable-an-embedded-canvas-app)을 참조하세요.
-   포함된 캔버스 앱은 호스트 모델 기반 양식을 통해서만 생성, 편집 및 재생할 수 있습니다.
     - 포함된 캔버스 앱은 모델 기반 양식의 컨텍스트 외부에서 직접 만들 수 없습니다.
     - 마찬가지로 모델 기반 양식의 컨텍스트 외부에서 편집 또는 재생을 위해 포함된 캔버스 앱을 여는 것은 지원되지 않습니다.

     > [!NOTE]
     > 포함된 캔버스 앱은 모델 기반 앱 외부에서 열 수 있지만 이는 지원되지 않습니다.

-   하위 표 컨트롤을 사용하여 포함된 캔버스 앱을 모델 기반 양식에 추가하는 경우 다음 사항에 유의하십시오.
     - 런타임에 포함된 캔버스 앱으로 전송된 데이터(필드 및 값)는 하위 표 컨트롤의 속성에 있는 **데이터 원본** 섹션의 **기본 보기**로 지정된 보기에 의해 결정됩니다. 포함된 캔버스 앱에서 보기에 포함된 필드만 사용하거나 필요한 경우 보기에 추가할 수 있습니다. 보기에 포함되지 않은 필드는 런타임에 빈 값을 표시합니다. 
     - 보기에 대한 필터 기준은 작성 시에 사용되지 않습니다. 따라서 포함된 캔버스 앱을 작성할 때 표시되는 데이터는 필터링 되지 않으며, 액세스 권한이 있는 상위 몇 개 레코드의 목록일 뿐입니다. 런타임 시 보기에 대한 필터 기준이 예상대로 적용되고 관련 데이터만 표시됩니다.
-   필드 컨트롤을 사용하여 포함된 캔버스 앱을 모델 기반 양식에 추가하는 경우 항상 값이 보장되는 필수 필드를 사용합니다. 필드에 값이 없는 경우 포함된 캔버스 앱은 호스트 모델 기반 양식의 데이터 변경에 대한 응답으로 새로 고쳐지지 않습니다.
-   모델 기반 양식을 게시해도 포함된 캔버스 앱이 게시되지 않습니다.
     - 포함된 캔버스 앱은 호스트 모델 기반 양식과 독립적으로 게시해야 합니다. 자세한 내용: [앱 게시](../canvas-apps/save-publish-app.md#publish-an-app).
-   웹 브라우저 팝업 차단으로 인해 캔버스 앱 컨트롤 속성의 **사용자 지정** 단추를 통해 포함된 캔버스 앱을 만들거나 편집하기 위해 PowerApps Studio를 열 경우 web.powerapps.com 사이트를 사용하도록 설정하거나 일시적으로 팝업 차단을 사용하지 않도록 설정한 다음 **사용자 지정** 을 다시 선택합니다.
-   포함된 캔버스 앱은 레코드 컨텍스트가 전달될 필요가 있기 때문에 새 레코드를 만들때 표시되지 않습니다.
-   ModelDrivenFormIntegration.Data 개체는 읽기 전용입니다. 
     - 데이터를 다시 쓰려면 Common Data Service 커넥터를 사용해야 합니다. 자세한 내용: [Common Data Service](/connectors/commondataservice/)
-   ModelDrivenFormIntegration.Data 개체는 레코드 목록입니다. 
     - 현재 레코드는 ModelDrivenFormIntegration.Data를 통해 포함된 캔버스 앱에 단일 레코드를 포함하는 목록으로 전달됩니다.
     - 레코드를 직접 참조하려면 [첫 번째 함수](../canvas-apps/functions/function-first-last.md)를 사용할 수 있습니다. 예: 첫 번째(ModelDrivenFormIntegration.Data).이름
-   캔버스 앱 컨트롤 속성에서 앱 ID를 수동으로 변경하는 것은 가급적 피해야 합니다.
     - 캔버스 앱의 앱 ID가 자동으로 생성 및 입력됩니다. 
     - 어떤 이유로 수동으로 편집해야 하는 경우 사용하는 모든 앱 ID가 독립 실행형 캔버스 앱 뿐만 아니라 *포함된* 캔버스 앱에 해당하는지 확인해야 합니다. 
     - 또한 포함된 캔버스 앱은 모델 기반 양식에서 보내는 것과 동일한 데이터 컨텍스트를 사용하여 만들어야 합니다.
     - 앱 ID를 업데이트한 후 **사용자 지정**을 선택하여 PowerApps Studio에서 열고 새 앱에 대한 연결을 설정합니다.
     - 응용 프로그램을 약간 변경하여 저장되지 않은 상태로 둔 다음, 저장하고 앱을 게시합니다.
- 포함된 캔버스 앱을 사용하여 모델 기반 양식을 볼 때 "해당 앱을 찾지 못했습니다. 죄송합니다" 라는 오류 메시지가 표시 되면 포함된 캔버스 앱이 모델 기반 양식과 동일한 솔루션에 있는지 확인합니다.
- 포함된 캔버스 앱을 사용하여 모델 기반 양식을 볼 때 "이 응용 프로그램에 대한 액세스 권한이 없는 것 같습니다" 라는 오류 메시지가 표시되는 경우. 담당자에게 공유하도록 요청" 작성자가 포함된 캔버스 앱을 공유했는지 확인합니다. 자세한 내용: [포함된 캔버스 앱 공유](share-embedded-canvas-app.md).

## <a name="enable-an-embedded-canvas-app"></a>포함된 캔버스 앱 사용
1. 포함된 캔버스 앱으로 표시하도록 사용자 지정된 필드 또는 하위 표 컨트롤을 선택합니다.
2. **필드 속성** (또는 하위 표의 **속성 설정**) 대화에서 **컨트롤** 탭을 선택합니다.
3. 컨트롤 목록에서 **캔버스 앱**을 선택한 다음 **웹** 옵션을 선택합니다.
4. **확인**을 선택합니다.

## <a name="disable-an-embedded-canvas-app"></a>포함된 캔버스 앱 사용 안 함
1. 포함된 캔버스 앱으로 표시하도록 사용자 지정된 필드 또는 하위 표 컨트롤을 선택합니다.
2. **필드 속성** (또는 하위 표의 **속성 설정**) 대화에서 **컨트롤** 탭을 선택합니다.
3. 컨트롤 목록에서 기본 컨트롤을 선택한 다음 **웹** 옵션을 선택합니다.
4. **확인**을 선택합니다.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>포함된 캔버스 앱의 알려진 문제 및 제한사항
- Canvas 앱 사용자 지정 컨트롤은 **웹** 클라이언트 유형 사용에만 지원 됩니다. 현재 **전화** 및 **태블릿** 클라이언트 유형은 지원되지 않습니다. 추가 정보: [모델 기반 앱 데이터 시각화를 위한 사용자 지정 컨트롤 사용](use-custom-controls-data-visualizations.md)
- 새 레코드를 만들면 레코드가 저장된 후에도 양식에 포함된 캔버스 앱이 표시되지 않습니다. 
-    ModelDrivenFormIntegration.Data 개체는 현재 표시 양식 및 편집 양식 컨트롤에서 작동하지 않습니다.
- 앱 사용자에게 포함된 또는 독립형 캔버스 앱에 대한 액세스 권한을 부여하기 위해 보안 역할의 **캔버스 앱** 권한을 사용할 수 없습니다. 포함된 캔버스 앱 공유에 대한 자세한 내용은 [포함된 캔버스 앱 공유](share-embedded-canvas-app.md)를 참조하세요.
- 호스트 모델 기반 양식에 표시되는 것과 동일한 데이터를 다시 작성하면 양식이 새로 고쳐질 때까지 이전 데이터를 계속 표시합니다. 이 작업을 수행하는 쉬운 방법은 [RefreshForm](embedded-canvas-app-actions.md) 메서드를 사용하는 것입니다.
- 기능을 사용할 수 있게 되기 전에 만들어진 포함된 캔버스 앱에서 [미리 정의된 작업을 수행하는 메서드](embedded-canvas-app-actions.md)에 대한 IntelliSense가 표시되지 않는 경우 앱을 저장하고 닫은 후 다시 엽니다. 

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[포함된 캔버스 앱을 사용하여 현재 레코드를 데이터 컨텍스트로 전달](pass-current-embedded-canvas-app.md) <br />
[포함된 캔버스 앱을 사용하여 관련 레코드의 목록을 데이터 컨텍스트로 전달](pass-related-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md)
