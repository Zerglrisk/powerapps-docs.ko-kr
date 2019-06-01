---
title: 앱 개체 | Microsoft Docs
description: 구문 및 PowerApps에서 앱 개체에 대 한 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 232accd1050fb84816e86ea95069b8c8778f6586
ms.sourcegitcommit: 562c7ed5fbb116be1cbb0f45e3f6e75e3e4cf011
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451613"
---
# <a name="app-object-in-powerapps"></a>PowerApps에서 앱 개체

현재 실행 중인 앱 및 앱의 동작을 제어 하는 방법에 대 한 정보를 제공 합니다.

## <a name="description"></a>설명

컨트롤을 같은 합니다 **앱** 개체를 식별 하는 화면 표시 되 고 손실 되지 않습니다 있도록 변경 내용을 저장 하는 사용자에 게는 속성을 제공 합니다. 모든 앱에는 **앱** 개체입니다.

일부 속성의 수식을 작성할 수는 **앱** 개체입니다. 맨 위에 있는 **트리 보기** 창 합니다 **앱** 와 다른 컨트롤 또는 화면 개체입니다. 보기 및 수식 입력줄의 왼쪽 드롭다운 목록에서 선택 하 여 개체의 속성 중 하나를 편집 합니다.

> [!div class="mx-imgBorder"]
> ![트리 뷰 창에서 앱 개체](media/object-app/appobject.png)

## <a name="activescreen-property"></a>ActiveScreen 속성

합니다 **ActiveScreen** 속성은 표시 되는 화면을 식별 합니다.

이 속성에는 화면의 속성을 참조 하거나 화면 표시를 확인 하려면 다른 화면과 비교 하는 데 사용할 수 있는 화면 개체를 반환 합니다. 식을 사용할 수도 있습니다 **App.ActiveScreen.Name** 표시 되는 화면의 이름을 검색 합니다.

사용 된 **[다시](function-navigate.md)** 또는 **[탐색](function-navigate.md)** 표시 되는 화면을 변경 하는 함수입니다.

## <a name="onstart-property"></a>OnStart 속성

합니다 **OnStart** 속성이 사용자가 앱을 시작할 때 실행 합니다. 앱 작성자는 종종 이러한 작업을 수행할이 속성을 사용 합니다.

- 검색 하 고 사용 하 여 컬렉션으로 데이터를 캐시 합니다 **[수집](function-clear-collect-clearcollect.md)** 함수입니다.
- 사용 하 여 전역 변수를 설정 합니다 **[설정](function-set.md)** 함수입니다.
- 사용 하 여 초기 화면으로 이동 합니다 **[Navigate](function-navigate.md)** 함수.

이 수식은 첫 번째 화면이 나타나기 전에 평가됩니다. 화면이 로드되지 않으므로 **[UpdateContext](function-updatecontext.md)** 함수로 컨텍스트 변수를 설정할 수 없습니다. 그러나 **Navigate** 함수를 사용하여 컨텍스트 변수를 전달할 수 있습니다.

변경한 후 합니다 **OnStart** 속성을 마우스로 테스트 합니다 **앱** 개체를 **트리 보기** 창 나타나는 줄임표 (...)를 선택 하 고 다음을 선택 하 **OnStart 실행**합니다. 앱이 처음 로드될 때와 달리 기존 컬렉션과 변수가 미리 설정됩니다. 빈 컬렉션을 사용 하 여 시작 하는 **[ClearCollect](function-clear-collect-clearcollect.md)** 함수 대신 합니다 **수집** 함수입니다.

> [!div class="mx-imgBorder"]
> ![OnStart 실행에 대 한 앱 항목 바로 가기 메뉴](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>ConfirmExit 속성

저장 되지 않은 변경 내용이 손실 되어도 아무도 합니다. 사용 된 **ConfirmExit** 및 **ConfirmExitMessage** 앱을 닫을 때 전에 사용자에 게 경고 하는 속성입니다.

> [!NOTE]
> **ConfirmExit** Power BI 및 SharePoint, 예를 들어 포함 된 앱에서 작동 하지 않습니다.

> [!NOTE]
> 현재 이러한 속성을 참조할 수는 첫 번째 화면의 컨트롤을 **지연 된 로드** 미리 보기 기능을 사용 합니다 (이 새 앱에 대해 기본적으로). 참조 된 경우 PowerApps Studio는 오류가 표시 되지 않습니다 하지만 결과 게시 된 앱은 PowerApps 모바일 또는 브라우저에서 열리지 않으면. 이 제한을 제거 하는 작업이 적극적으로 진행 합니다. 그동안 해제할 수 있습니다 **지연 된 로드** 에 **파일** > **앱 설정** > **고급 설정**(아래 **미리 보기 기능**).

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit** 부울 속성인 하는 경우 *true*, 앱을 닫기 전에 확인 대화 상자를 엽니다. 이 속성은 기본적으로 *false*, 대화 상자가 나타납니다.

사용자 변경에 있지만 저장 하지 경우 확인 대화 상자를 표시 하려면이 속성을 사용 합니다. 변수를 확인 하 고 속성을 제어할 수 있는 수식을 사용 하 여 (예를 들어 합니다 **Unsaved** 의 속성을 [ **편집 양식** ](../controls/control-form-detail.md) 컨트롤).

확인 대화 상자 데이터 이러한 예제와 같이 손실 될 수 있는 상황에서 표시 됩니다.

- 실행 합니다 [ **끝내기** ](function-exit.md) 함수입니다.
- 경우 앱이 브라우저에서 실행 됩니다.
  - 앱 실행 되 고 있는 브라우저 탭 또는 브라우저를 닫는 중입니다.
  - 브라우저의 뒤로 단추를 선택합니다.
- 앱은 PowerApps Mobile (iOS 또는 Android)에서 실행 중이면:
  - 실행 합니다 [ **시작** ](function-param.md) 함수입니다.<br>합니다 **시작** 함수는 데이터가 손실 되지 않도록 다른 탭 열기 때문에 브라우저에서 대화 상자를 트리거하지 않습니다.
  - 살짝 PowerApps Mobile에서 다른 앱으로 전환 합니다.
  - Android 장치에서 뒤로 단추를 선택합니다.

확인 대화 상자의 정확한 모양을 장치 및 PowerApps의 버전 간에 달라질 수 있습니다.

확인 대화 상자는 PowerApps Studio 표시 되지 않습니다.

### <a name="confirmexitmessage"></a>ConfirmExitMessage

확인 대화 상자가 기본적으로 일반 메시지를 같은 표시 **"있습니다 수 하지 않은 변경 내용이 있습니다."** 사용자의 언어입니다.

사용 하 여 **ConfirmExitMessage** 확인 대화 상자에서 사용자 지정 메시지를 제공 합니다. 이 속성이 *빈*, 기본 값이 사용 됩니다. 사용자 지정 메시지 확인 대화 상자 내에 최대 몇 줄으로 메시지를 따라서 보관을 필요에 따라 잘립니다.

브라우저에서 브라우저에서 확인 대화 상자는 일반 메시지와 함께 나타날 수 있습니다.

### <a name="example"></a>예

1. 두 개의 폼 컨트롤을 포함 하는 앱을 만듭니다 **AccountForm** 하 고 **ContactForm**합니다.

1. 설정 된 **앱** 개체의 **ConfirmExit** 속성을이 식:

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    사용자의 형태로 데이터를 변경 하 고 해당 변경 내용을 저장 하지 않고 앱을 닫으려면 시도 하는 경우이 대화 상자에 표시 됩니다.

    > [!div class="mx-imgBorder"]
    > ![제네릭 확인 대화 상자](media/object-app/confirm-native.png)

1. 설정 된 **앱** 개체의 **ConfirmExitMessage** 속성을 다음이 수식:

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    사용자 계정 폼의 데이터를 변경 하 고 해당 변경 내용을 저장 하지 않고 앱을 닫으려면 시도 하는 경우이 대화 상자가 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![양식 관련 확인 대화 상자](media/object-app/confirm-native-custom.png)
