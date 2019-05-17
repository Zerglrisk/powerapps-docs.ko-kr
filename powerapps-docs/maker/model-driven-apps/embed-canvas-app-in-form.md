---
title: 모델 기반 양식에 캔버스 앱 포함 | MicrosoftDocs
ms.custom: ''
ms.date: 12/17/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
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

# <a name="embed-a-canvas-app-on-a-model-driven-form"></a>모델 기반 양식에 캔버스 앱 포함

캔버스 앱을 사용하면 제작자가 하위 코드, WYSIWYG 캔버스 앱 디자이너를 사용하여 사용자 지정 레이아웃을 쉽게 디자인하고 만들 수 있습니다. 또한 캔버스 앱을 통해 제작자는 200개 이상의 데이터 원본의 데이터를 양식에 연결하고 표시할 수 있습니다.

> [!NOTE]
> 이 기능은 현지 미리 보기로 제공됩니다. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)] <br /><br />

포함된 캔버스 앱을 사용하면 제작자는 캔버스 앱의 성능을 모델 기반 양식에 가져올 수 있습니다. 포함된 캔버스 앱을 사용하면 양식에서 다양한 시각적 영역을 쉽게 만들 수 있으며 Common Data Service의 데이터 바로 옆에 여러 원본의 데이터를 표시할 수도 있습니다.

   > [!div class="mx-imgBorder"] 
   > ![모델 기반 앱 양식에서 포함된 캔버스 앱](media/embed-canvas-app-in-form.png "모델 기반 앱 양식에서 포함된 캔버스 앱")

캔버스 앱은 다른 사용자 지정 컨트롤을 추가하는 것과 동일한 방식으로 모델 기반 양식에 포함됩니다. 포함된 캔버스 앱에는 호스트 모델 기반 양식에서 포함된 캔버스 앱으로 상황별 데이터를 가져오는 다양한 데이터 통합 기능이 포함되어 있습니다.

모델 기반 양식에 캔버스 앱을 포함하는 단계는 호스트 모델 기반 양식에서 포함된 canvas 앱에 제공하려는 데이터 컨텍스트에 따라 달라집니다.
-   현재 레코드를 데이터 컨텍스트로 전달합니다. 자세한 내용: [현재 레코드를 포함된 캔버스 앱에 데이터 컨텍스트로 전달](pass-current-embedded-canvas-app.md)
-   현재 레코드와 관련된 레코드 목록을 데이터 컨텍스트로 전달합니다. 자세한 내용: [관련 레코드의 목록을 포함된 캔버스 앱에 데이터 컨텍스트로 전달](pass-related-embedded-canvas-app.md) 

포함된 캔버스 앱을 모델 기반 양식에 추가한 후에는 포함된 캔버스 앱을 다른 사용자와 공유하는 방법을 알아봅니다. 자세한 내용: [포함된 캔버스 앱 공유](share-embedded-canvas-app.md).

포함된 캔버스 앱 작업에 대한 지침과 발생할 수 있는 문제를 해결하는 유용한 팁은 다음을 참조하십시오. [포함된 캔버스 앱 작업에 대한 가이드라인](embedded-canvas-app-guidelines.md).

## <a name="see-also"></a>참조
[PowerApps의 캔버스 앱이란 무엇입니까?](../canvas-apps/getting-started.md) <br />
[PowerApps에서 캔버스 앱 컨트롤 추가 및 구성](../canvas-apps/add-configure-controls.md) <br />
[PowerApps용 캔버스 앱 커넥터 개요](../canvas-apps/connections-list.md) <br />
[포함된 캔버스 앱을 사용하여 현재 레코드를 데이터 컨텍스트로 전달](pass-current-embedded-canvas-app.md) <br />
[포함된 캔버스 앱을 사용하여 관련 레코드의 목록을 데이터 컨텍스트로 전달](pass-related-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md)
