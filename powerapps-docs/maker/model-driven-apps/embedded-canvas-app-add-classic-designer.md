---
title: 모델 기반 양식에 포함된 캔버스 앱 추가 | MicrosoftDocs
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d229edaec03642c594eb8057927fcf44beadf7c5
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2872788"
---
# <a name="add-an-embedded-canvas-app-on-a-model-driven-form"></a>모델 기반 양식에 포함된 캔버스 앱 추가
이 항목에서는 모델 기반 양식에 새 캔버스 앱을 포함하는 방법에 대해 설명합니다.

새 캔버스 앱을 만들고 거래처 엔터티의 기본 양식에 포함한다고 가정해 보겠습니다. 이렇게 하려면 다음 단계를 수행합니다. 

1.  [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
2.  엔터티의 [기본 양식 만들기 또는 편집](create-and-edit-forms.md), 이 예에서 거래처 엔터티. 
3.  명령 모음에서 **클래식으로 전환**을 선택하여 기본 양식 디자이너의 양식을 엽니 다.
4.  기본 양식 디자이너에서 양식에서 포함된 캔버스 앱을 표시할 섹션을 선택합니다.
5.  필드 창을 사용하여 **거래처 이름**과 같은 필수 필드를 추가합니다.
      > [!IMPORTANT]
      > 항상 값이 있는 필수 필드를 사용하십시오. 필드에 값이 없는 경우 포함된 캔버스 앱은 호스트 모델 기반 양식의 데이터 변경에 대한 응답으로 새로 고쳐지지 않습니다.
6.  필드를 선택한 상태에서 **홈** 탭의 **편집** 그룹에서 **속성 변경**을 선택합니다.
7.  **필드 속성** 대화 상자에서 **컨트롤** 탭을 선택합니다.
8.  **컨트롤** 탭에서 **컨트롤 추가**를 선택합니다.
9.  **컨트롤 추가**대화 상자의 사용 가능한 컨트롤 목록에서  **캔버스 앱**을 선택한 다음 **추가**를 선택합니다.
10. **필드 속성** 대화 상자의 컨트롤 목록에서 **캔버스 앱**을 선택한 다음 **웹** 옵션을 선택합니다.
11. 컨트롤 목록 아래 섹션에 캔버스 앱 컨트롤에 사용할 수 있는 속성 목록이 표시됩니다.
     - **엔터티 이름** 속성은 포함된 캔버스 앱에 데이터를 제공할 엔터티를 지정합니다. 이전 단계에서 추가한 필드가 포함된 엔터티로 설정됩니다.
         - 이 속성이 변경 가능하게 표시되더라도 포함된 캔버스 앱에는 영향을 주지 않습니다. 이는 참조로만 제공되는 것입니다.
     - **앱 ID** 속성은 포함된 캔버스 앱의 ID를 지정합니다. 캔버스 앱을 만들 때 자동으로 생성되어 채워집니다.
         - **앱 ID** 값을 변경하면 모델 기반 양식에서 포함된 캔버스 앱으로의 링크가 끊어집니다.
12. **사용자 지정**을 선택하여 캔버스 앱을 만들거나 편집합니다. 그러면 새 탭에 Power Apps Studio가 열립니다.
       > [!NOTE]
       > 웹 브라우저 팝업 차단기로 인해 Power Apps Studio를 여는 것이 차단된 경우 make.powerapps.com 사이트를 사용하도록 설정하거나 일시적으로 팝업 차단을 해제한 다음 **사용자 지정**을 다시 선택해야 합니다.
13. Power Apps Studio에서 왼쪽 창에 특별한 **ModelDrivenFormIntegration** 컨트롤이 있음을 알 수 있습니다. 이 컨트롤은 호스트 모델 기반 양식에서 포함된 캔버스 앱으로 컨텍스트 데이터를 가져오는 역할을 합니다.
14. [캔버스 앱 양식 컨트롤](../canvas-apps/controls/control-form-detail.md)이 포함된 캔버스 앱에 자동으로 추가되었으며 ModelDrivenFormIntegration 컨트롤을 통해 호스트 모델 기반 양식에서 전달된 데이터를 표시합니다. 
15. **보기** 탭을 선택한 다음, **데이터 원본**을 선택합니다. 호스트 모델 기반 양식의 상위 엔터티(이 경우 거래처)의 데이터 원본이 포함된 캔버스 앱에 자동으로 추가되었음을 알 수 있습니다.
16. **Form1** 컨트롤을 선택하고 **DataSource** 속성이 **Accounts**로 설정되어 있는지 확인합니다.
17. 여전히 **Form1** 컨트롤이 선택된 상태에서 **Items** 속성이 **ModelDrivenFormIntegration.Item**으로 설정되어 있는지 확인합니다.
    > [!NOTE]
    > 포함된 캔버스 앱은 ModelDrivenFormIntegration.Item을 통해 호스트 모델 기반 양식에서 레코드에 대한 완벽한 액세스 권한을 갖습니다. 예를 들어 이름이 **accountnumber**이고 표시 이름이 **거래처 번호**인 필드의 값을 가져오려면 **ModelDrivenFormIntegration.Item.accountnumber** 또는 **ModelDrivenFormIntegration.Item.'Account Number'** 를 사용할 수 있습니다.
18. 오른쪽의 속성 창에서 **필드** 옆에 있는 **필드 편집**을 선택합니다.
19. 캔버스 앱 양식에 다른 필드를 추가하거나 드래그 앤 드롭을 사용하여 기존 필드의 순서를 바꾸려면 **+ 필드 추가**를 선택합니다. 필드 추가 및 순서 변경이 완료되면 데이터 창을 닫습니다.
20. **파일** 탭을 선택한 다음 **저장**을 선택합니다.
21. **클라우드** 탭을 선택합니다. 앱의 고유한 이름을 입력한 다음 오른쪽 아래에 있는 **저장**을 선택합니다. 다음을 참고하십시오. 
    -  앱을 처음으로 저장하면 앱이 자동으로 게시됩니다.
      -  이후 저장에서 **게시**를 선택한 다음**이 버전 게시**를 선택하여 변경 내용을 사용할 수 있도록 합니다.
22. 메뉴에서 **뒤로**를 선택합니다.
23. 기본 양식 디자이너가 열려 있는 브라우저 탭을 선택합니다. 캔버스 앱 컨트롤의 **앱 ID** 속성에 이제 자동으로 채워진 값이 있는지 관찰합니다.
    > [!NOTE]
    > - 양식 디자이너에는 이전 단계의 다른 브라우저 탭에서 열린 Power Apps Studio와의 직접 링크가 있습니다.
    > - 양식 디자이너는 앱 ID 보내기를 수신 대기합니다. 
    > - 앱을 저장하면 앱 ID가 양식 디자이너로 보내집니다.
24. **필드 속성** 대화 상자에서 **표시** 탭을 선택합니다.
25. 양식에서 **레이블 표시**를 지우고 **확인**을 선택합니다.
    -   이 양식에 이미 포함된 캔버스 앱이 있는 경우 "하나의 캔버스 앱만 양식에 사용할 수 있습니다"라는 메시지가 표시됩니다. 새 캔버스 앱을 추가하려면 먼저 [현재 포함 된 캔버스 앱을 비활성화](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app)해야 합니다. 그런 다음 [새 포함된 캔버스 앱을 활성화](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app)합니다.
26. **홈** 탭에서 **저장**을 선택한 다음, **게시**를 선택합니다.

포함된 캔버스 앱을 모델 기반 양식에 추가한 후에는 포함된 캔버스 앱을 다른 사용자와 공유합니다. 자세한 내용: [포함된 캔버스 앱 공유](share-embedded-canvas-app.md).

사용자가 수정한 양식이 포함된 모델 기반 앱(통합 인터페이스만 해당)을 열면 양식에 포함된 캔버스 앱이 표시됩니다. 기본 양식에 표시되는 레코드를 변경하면 양식에 전달되는 데이터 컨텍스트가 변경되고 포함된 앱이 새로 고쳐지면서 관련 데이터가 표시됩니다.

이 항목에서는 모델 기반 양식에 캔버스 앱을 포함하는 작업을 시작하는 방법을 보여 주었습니다. 다양한 데이터 원본의 데이터를 연결하고 가져올 수 있도록 포함된 캔버스 앱을 사용자 지정할 수도 있습니다. 필터, 검색 및 조회 기능과 호스트 모델 기반 양식에서 전달된 컨텍스트를 사용하여 해당 데이터 소스의 특정 레코드를 필터링하거나 찾을 수 있습니다. WYSIWYG 캔버스 앱 편집기를 사용하여 요구 사항에 맞게 인터페이스를 쉽게 디자인할 수 있습니다.

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
[공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
