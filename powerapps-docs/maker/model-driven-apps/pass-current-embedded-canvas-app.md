---
title: 포함된 캔버스 앱을 사용하여 현재 레코드를 데이터 컨텍스트로 전달 | MicrosoftDocs
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
ms.openlocfilehash: 639b8631f1d953408d30a1fdbba9c9ae8161af4d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755142"
---
# <a name="pass-the-current-record-as-data-context-to-an-embedded-canvas-app"></a>포함된 캔버스 앱을 사용하여 현재 레코드를 데이터 컨텍스트로 전달
> [!IMPORTANT]
> 모델 기반 양식에 포함된 캔버스 앱은 이제 미리 보기가 없이 일반적으로 사용할 수 있습니다. 아래 나열된 단계는 구식이며 모델 기반 양식에 포함된 캔버스 앱의 공개 미리 보기 릴리스에만 적용됩니다.
> 최신 릴리스의 업데이트된 단계 목록은 [모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md)를 참조하십시오.

이 항목에서는 포함된 캔버스 앱을 추가하고 현재(기본 양식) 레코드를 포함된 캔버스 앱에 데이터 컨텍스트로 전달하는 방법에 대해 설명합니다.

거래처 기본 양식의 포함된 캔버스 앱을 추가하고 현재 거래처 레코드를 포함된 캔버스 앱에 전달하려는 경우를 가정해 보겠습니다. 이렇게 하려면 다음 단계를 수행합니다. 

1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인하고 거래처 엔터티와 같은 엔터티의 기본 양식에 대한 양식 편집기를 엽니다. 
2.  양식에서 포함된 캔버스 앱을 표시할 섹션을 선택합니다.
3.  필드 탐색기 창을 사용하여 **거래처 이름**과 같은 필수 필드를 추가합니다.
      > [!IMPORTANT]
      > 항상 값이 있는 필수 필드를 사용하십시오. 필드에 값이 없는 경우 포함된 캔버스 앱은 호스트 모델 기반 양식의 데이터 변경에 대한 응답으로 새로 고쳐지지 않습니다.
4.  필드를 선택한 상태에서 **홈** 탭의 **편집** 그룹에서 **속성 변경**을 선택합니다.
5.  **필드 속성** 대화 상자에서 **컨트롤** 탭을 선택합니다.
6.  **컨트롤** 탭에서 **컨트롤 추가...** 를 선택합니다.
7.  **컨트롤 추가**대화 상자의 사용 가능한 컨트롤 목록에서  **캔버스 앱**을 선택한 다음 **추가**를 선택합니다.
8.  **필드 속성** 대화 상자의 컨트롤 목록에서 **캔버스 앱**을 선택한 다음 **웹** 옵션을 선택합니다.
9.  컨트롤 목록 아래 섹션에 캔버스 앱 컨트롤에 사용할 수 있는 속성 목록이 표시됩니다.
     - **엔터티 이름** 속성은 포함된 캔버스 앱에 데이터를 제공할 엔터티를 지정합니다. 이전 단계에서 추가한 필드가 포함된 엔터티로 설정됩니다.
         - 이 속성이 변경 가능하게 표시되더라도 포함된 캔버스 앱에는 영향을 주지 않습니다. 이는 참조로만 제공되는 것입니다.
     - **앱 ID** 속성은 포함된 캔버스 앱의 ID를 지정합니다. 캔버스 앱을 만들 때 자동으로 생성되어 채워집니다.
         - **앱 ID** 값을 변경하면 모델 기반 양식에서 포함된 캔버스 앱으로의 링크가 끊어집니다.
10. **사용자 지정**을 선택하여 캔버스 앱을 만들거나 편집합니다. 그러면 새 탭에 PowerApps Studio가 열립니다.
       > [!NOTE]
       > 웹 브라우저 팝업 차단기로 인해 PowerApps Studio를 여는 것이 차단된 경우 make.powerapps.com 사이트를 사용하도록 설정하거나 일시적으로 팝업 차단을 해제한 다음 **사용자 지정**을 다시 선택해야 합니다.
11. PowerApps Studio에서 왼쪽 창에 특별한 **ModelDrivenFormIntegration** 컨트롤이 있음을 알 수 있습니다. 이 컨트롤은 호스트 모델 기반 양식에서 포함된 캔버스 앱으로 컨텍스트 데이터를 가져오는 역할을 합니다.
12. **Gallery1** 컨트롤을 선택하고 **Items** 속성이 **ModelDrivenFormIntegration**로 설정되어 있는지 확인합니다.
      > [!NOTE]
      > ModelDrivenFormIntegration.Data는 레코드 목록입니다. 이 예제에서는 하나의 레코드만 있습니다. 레코드를 직접 참조하려면 First 함수를 사용할 수 있습니다. 예를 들어, *First(ModelDrivenFormIntegration.Data).Name*입니다.
13. 오른쪽의 속성 창에서 **필드** 옆에 있는 **편집**을 선택합니다.
14. 데이터 창에서 **Title1** 컨트롤에 매핑된 필드를 **이름** 또는 데이터가 있는 다른 필드로 변경합니다.
15. 갤러리에 ModelDrivenFormIntegration 컨트롤을 통해 호스트 모델 기반 양식에서 전달되는 데이터가 표시되는지 확인합니다. 데이터 창을 닫습니다.
16. **파일** 탭을 선택한 다음 **앱 설정**을 선택합니다.
17. **고급 설정** 탭의 **실험적 기능** 섹션에서 **앱 포함 사용자 환경 사용**을 **켜기**로 설정합니다.
18. **저장**을 선택합니다. 
19. **클라우드** 탭을 선택합니다. 앱의 고유한 이름을 입력한 다음 오른쪽 아래에 있는 **저장**을 선택합니다. 다음을 참고하십시오. 
    -  앱을 처음으로 저장하면 앱이 자동으로 게시됩니다.
      -  이후 저장에서 **게시**를 선택한 다음**이 버전 게시**를 선택하여 변경 내용을 사용할 수 있도록 합니다.
20. 메뉴에서 **뒤로**를 선택한 다음 양식 편집기가 열려 있는 브라우저 탭을 선택합니다. 캔버스 앱 컨트롤의 **앱 ID** 속성에 이제 자동으로 채워진 값이 있는지 관찰합니다. 다음을 참고하십시오. 
    -   양식 편집기에는 이전 단계의 다른 브라우저 탭에서 열린 PowerApps Studio와의 직접 링크가 있습니다.
    -   양식 편집기는 **앱 ID** 보내기를 "수신 대기"합니다.
    -   앱을 저장하면 **앱 ID**가 양식 편집기로 보내집니다.
21. **필드 속성** 대화 상자에서 **표시** 탭을 선택합니다.
22. 양식에서 **레이블 표시**를 지우고 **확인**을 선택합니다.
    -   이 양식에 이미 포함된 캔버스 앱이 있는 경우 "하나의 캔버스 앱만 양식에 사용할 수 있습니다"라는 메시지가 표시됩니다. 새 캔버스 앱을 추가하려면 먼저 [현재 포함 된 캔버스 앱을 비활성화](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app)해야 합니다. 그런 다음 [새 포함된 캔버스 앱을 활성화](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app)합니다.
23. **홈** 탭에서 **저장**을 선택한 다음, **게시**를 선택합니다.

포함된 캔버스 앱을 모델 기반 양식에 추가한 후에는 포함된 캔버스 앱을 다른 사용자와 공유합니다. 자세한 내용: [포함된 캔버스 앱 공유](share-embedded-canvas-app.md).

사용자가 수정한 양식이 포함된 모델 기반 앱(통합 인터페이스만 해당)을 열면 양식에 포함된 캔버스 앱이 표시됩니다. 기본 양식에 표시되는 레코드를 변경하면 양식에 전달되는 데이터 컨텍스트가 변경되고 포함된 앱이 새로 고쳐지면서 관련 데이터가 표시됩니다.

이 항목에서는 모델 기반 양식에 캔버스 앱을 포함하는 작업을 시작하는 방법을 보여 주었습니다. 다양한 데이터 원본의 데이터를 연결하고 가져올 수 있도록 포함된 캔버스 앱을 사용자 지정할 수도 있습니다. 필터, 검색 및 조회 기능과 호스트 모델 기반 양식에서 전달된 컨텍스트를 사용하여 해당 데이터 소스의 특정 레코드를 필터링하거나 찾을 수 있습니다. WYSIWYG 캔버스 앱 편집기를 사용하여 요구 사항에 맞게 인터페이스를 쉽게 디자인할 수 있습니다.

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
[공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
