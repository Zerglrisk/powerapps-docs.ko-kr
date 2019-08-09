---
title: 공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
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

# <a name="migrate-embedded-canvas-apps-on-model-driven-forms-created-using-the-public-preview-release"></a>공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션
> [!IMPORTANT]
> 최신 버전에서는 일반적으로 모델 기반 양식에 포함된 캔버스 앱을 사용할 수 있습니다. 공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식의 모든 포함된 캔버스 앱은 최신 버전을 사용하여 만든 새로운 포함된 캔버스 앱으로 마이그레이션해야 합니다.
> 공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 앱에 대한 지원은 곧 더 이상 사용되지 않을 예정입니다. 

공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에서 최신 버전으로 포함된 캔버스 앱을 마이그레이션하려면 제조업체는 먼저 최신 버전을 사용하여 새로운 포함된 캔버스 앱을 만들어야 합니다. 제조업체는 기존의 포함된 캔버스 앱에서 새 캔버스 캔버스 앱으로 컨트롤을 복사하고, 필요한 데이터 소스를 추가하고, 연결이 끊어진 참조가 있는 경우 이를 업데이트할 수 있습니다. 자세한 단계는 아래에 나와 있습니다.

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
2. PowerApps Studio에서 편집을 위해 공개 미리 보기를 사용하여 만든 포함된 캔버스 앱을 엽니다. 캔버스 앱을 편집하는 단계는 [캔버스 앱 편집](../canvas-apps/edit-app.md)을 참조하십시오.
3. 새 브라우저 탭에서 [모델 기반 양식에 새로운 포함된 캔버스 앱을 추가하는 단계](embedded-canvas-app-add-classic-designer.md)를 따르십시오.
4. 공개 미리 보기 릴리스를 사용하여 만든 포함된 캔버스 앱의 컨트롤을 아래의 단계를 사용하여 한 번에 한 화면씩 새로 포함된 캔버스 앱에 복사합니다.
    1. 2단계에서 공개 미리 보기 릴리스를 사용하여 만든 캔버스 앱이 포함된 브라우저 탭을 선택하고 PowerApps Studio에서 엽니다.
    2. 컨트롤을 복사할 화면을 선택합니다.
    3. **Ctrl + A**를 사용하여 화면의 모든 컨트롤을 선택합니다.
    4. **Ctrl + C**를 사용하여 선택한 모든 컨트롤을 복사합니다.
    5. 3단계에서 최신 릴리스를 사용하여 만든 새로운 포함된 캔버스 앱이 있는 브라우저 탭을 선택합니다.
    6. 화면을 선택하거나 새 화면을 추가합니다.
    7. **Ctrl + V**를 사용하여 선택한 화면에 컨트롤을 붙여 넣습니다.
    8. 단계를 반복하여 각 화면을 복사합니다.
5. 모든 화면을 복사했으면 3단계에서 최신 릴리스를 사용하여 만든 새로운 포함된 캔버스 앱이 있는 브라우저 탭을 선택합니다.
6. 호스트 모델 기반 양식의 레코드가 액세스되는 모든 장소를 업데이트합니다. **First(ModelDrivenFormIntegration.Data)** 를 **ModelDrivenFormIntegration.Item**으로 바꿉니다.
7. 누락된 데이터 원본을 새로 포함된 캔버스 앱에 추가합니다.
8. 새 포함된 캔버스 앱에서 연결이 끊어진 참조를 모두 업데이트합니다. 
9. 변경이 완료되면 **파일** 탭을 선택한 다음 **저장**을 선택합니다.
10. 최종 사용자가 사용할 수 있도록 변경하려면 **게시**를 선택한 다음 **이 버전 게시**를 선택합니다.

## <a name="migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record"></a>현재(기본 양식) 레코드와 관련된 레코드 목록을 사용하는 모델 기반 양식에 포함된 캔버스 앱 마이그레이션

미리 보기 릴리스에서 캔버스 앱을 모델 기반 양식에 포함시키기 위해 제조업체는 현재(기본 양식) 레코드를 데이터 컨텍스트로 전달할지 또는 현재(기본 양식)와 관련된 레코드 목록을 전달할 것인지 미리 결정해야 했습니다. 그런 다음 캔버스 앱 컨트롤을 필드 또는 하위 그리드 컨트롤에 추가해야 했습니다.

최신 릴리스를 사용하면 모델 기반 양식에 포함된 캔버스 앱을 추가하는 작업이 간소화되고 필드로만 제한됩니다. 제조업체는 Common Data Service 커넥터를 사용하여 캔버스 앱에서 직접 관련 레코드 목록에 쉽게 액세스할 수 있습니다. 

현재(기본 양식) 레코드와 관련된 레코드 목록을 사용하는 모델 기반 양식에서 포함된 캔버스 앱을 마이그레이션하려면 다음 단계를 따르십시오.

1. 위 섹션의 단계에 따라 공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 앱을 최신 버전으로 마이그레이션할 수 있습니다.
2. Common Data Service 커넥터를 사용하여 관련 엔터티의 데이터 소스를 앱에 추가합니다. 캔버스 앱에서 데이터 원본을 추가하는 방법은 [PowerApps의 캔버스 앱에 데이터 연결 추가](../canvas-apps/add-data-connection.md)를 참조하십시오.
3. [갤러리](../canvas-apps/controls/control-gallery.md) 또는 [데이터 테이블](../canvas-apps/controls/control-data-table.md)과 같은 컨트롤에 관련 엔터티의 데이터 원본을 사용하는 경우 **[필터](../canvas-apps/functions/function-filter-lookup.md)** 함수를 사용하여 현재(기본 양식) 레코드와 관련된 레코드로 레코드를 필터링합니다. 현재(기본 양식) 레코드는 **ModelDrivenFormIntegration.Item**을 통해 사용할 수 있습니다.
    > [!NOTE]
    > 포함된 캔버스 앱은 ModelDrivenFormIntegration.Item을 통해 호스트 모델 기반 양식에서 레코드에 대한 완벽한 액세스 권한을 갖습니다. 예를 들어 이름이 **accountnumber**이고 표시 이름이 **거래처 번호**인 필드의 값을 가져오려면 **ModelDrivenFormIntegration.Item.accountnumber** 또는 **ModelDrivenFormIntegration.Item.'Account Number'** 를 사용할 수 있습니다.
4. 최근 업데이트 Common Data Service에서는 엔터티 보기를 필터로 사용할 수 있도록 지원합니다. 자세한 내용은 [향상된 데이터 소스 선택 및 Common Data Service 보기](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/) 블로그 게시물을 참조하십시오. 

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
