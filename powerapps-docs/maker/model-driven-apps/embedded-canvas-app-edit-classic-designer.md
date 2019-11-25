---
title: 모델 기반 양식에 포함된 캔버스 앱 편집 | MicrosoftDocs
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
ms.openlocfilehash: cb265233e0d72e7350603b496f91e6d62e32002d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758507"
---
# <a name="edit-a-canvas-app-embedded-on-a-model-driven-form"></a>모델 기반 양식에 포함된 캔버스 앱 편집.
이 항목에서는 모델 기반 양식에 포함된 캔버스 앱을 편집하는 방법에 대해 설명합니다.

## <a name="edit-the-canvas-app-directly"></a>캔버스 앱을 직접 편집
다른 캔버스 앱과 마찬가지로 모델 기반 양식에 포함된 캔버스 앱을 편집할 수 있습니다. 캔버스 앱을 편집하는 단계는 다음을 참조하십시오. [캔버스 앱 편집](../canvas-apps/edit-app.md)

## <a name="edit-the-canvas-app-via-the-host-model-driven-form"></a>호스트 모델 기반 양식을 통해 캔버스 앱 편집
또 다른 옵션은 호스트 모델 기반 양식을 통해 포함된 캔버스 앱을 편집하는 것입니다.

거래처 엔터티의 거래처 기본 양식이라는 양식에 포함된 캔버스 앱을 편집한다고 가정해 보겠습니다. 이렇게 하려면 다음 단계를 수행합니다. 

1.  [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
2.  거래처 엔터티에 대한 거래처 기본 양식이라는 [양식을 편집](create-and-edit-forms.md)합니다. 
3.  명령 모음에서 **클래식으로 전환**을 선택하여 기본 양식 디자이너의 양식을 엽니 다.
4.  기본 양식 디자이너에서 사용자 지정된 필드를 선택하여 포함된 캔버스 앱을 표시합니다.
5.  필드를 선택한 상태에서 **홈** 탭의 **편집** 그룹에서 **속성 변경**을 선택합니다.
6.  **필드 속성** 대화 상자에서 **컨트롤** 탭을 선택합니다.
7.  **필드 속성** 대화 상자의 컨트롤 목록에서 **캔버스 앱**을 선택합니다.
8.  컨트롤 목록 아래의 섹션에서 **사용자 지정**을 선택하여 캔버스 앱을 편집합니다. 그러면 캔버스 앱이 열리고 PowerApps Studio의 새 탭에서 편집할 수 있습니다.
       > [!NOTE]
       > 웹 브라우저 팝업 차단기로 인해 PowerApps Studio를 여는 것이 차단된 경우 make.powerapps.com 사이트를 사용하도록 설정하거나 일시적으로 팝업 차단을 해제한 다음 **사용자 지정**을 다시 선택해야 합니다.
9. 변경이 완료되면 **파일** 탭을 선택한 다음 **저장**을 선택합니다.
10. 최종 사용자가 사용할 수 있도록 변경하려면 **게시**를 선택한 다음 **이 버전 게시**를 선택합니다.

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 컨트롤의 속성 및 동작](embedded-canvas-app-properties-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
[공개 미리보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
