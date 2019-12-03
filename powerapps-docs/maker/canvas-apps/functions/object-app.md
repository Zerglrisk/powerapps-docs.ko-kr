---
title: 앱 개체 | Microsoft Docs
description: PowerApps의 앱 개체에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c2e34a9f466fcb64bcf14ef6a504d5b18b0a596d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74676735"
---
# <a name="app-object-in-powerapps"></a>PowerApps의 App 개체

현재 실행 중인 앱에 대 한 정보와 앱 동작에 대 한 제어를 제공 합니다.

## <a name="description"></a>설명

컨트롤과 마찬가지로 **App** 개체는 표시 되는 화면을 식별 하 고 사용자에 게 변경 내용을 저장 하 라는 메시지를 표시 하는 속성을 제공 하 여 손실 되지 않도록 합니다. 모든 앱에는 **앱** 개체가 있습니다.

**앱** 개체의 일부 속성에 대 한 수식을 작성할 수 있습니다. **트리 뷰** 창 맨 위에서 다른 컨트롤이 나 화면과 같은 방식으로 **앱** 개체를 선택 합니다. 수식 입력줄의 왼쪽에 있는 드롭다운 목록에서 개체 속성을 선택 하 여 해당 속성 중 하나를 보고 편집 합니다.

> [!div class="mx-imgBorder"]
> 트리 뷰 창에서 앱 개체를 ![](media/object-app/appobject.png)

## <a name="activescreen-property"></a>App.activescreen 속성

**App.activescreen** 속성은 표시 되는 화면을 식별 합니다.

이 속성은 화면의 속성을 참조 하거나 다른 화면을 비교 하 여 표시할 화면을 결정 하는 데 사용할 수 있는 화면 개체를 반환 합니다. **App.ActiveScreen.Name** 식을 사용 하 여 표시 되는 화면 이름을 검색할 수도 있습니다.

**[뒤로](function-navigate.md)** 또는 **[탐색](function-navigate.md)** 함수를 사용 하 여 표시 되는 화면을 변경 합니다.

## <a name="onstart-property"></a>OnStart 속성

**OnStart** 속성은 사용자가 앱을 시작할 때 실행 됩니다. 앱 제작자는 일반적으로이 속성을 사용 하 여 다음 작업을 수행 합니다.

- **[Collect](function-clear-collect-clearcollect.md)** 함수를 사용 하 여 데이터를 검색 하 고 컬렉션에 캐시 합니다.
- **[Set](function-set.md)** 함수를 사용 하 여 전역 변수를 설정 합니다.
- **[Navigate](function-navigate.md)** 함수를 사용 하 여 초기 화면으로 이동 합니다.

이 수식은 첫 번째 화면이 표시 되기 전에 평가 됩니다. 화면이 로드 되지 않으므로 **[Updatecontext](function-updatecontext.md)** 함수를 사용 하 여 컨텍스트 변수를 설정할 수 없습니다. 그러나 **Navigate** 함수를 사용 하 여 컨텍스트 변수를 전달할 수 있습니다.

**OnStart** 속성을 변경한 후에는 **트리 뷰** 창에서 **앱** 개체를 마우스로 가리키고, 표시 되는 줄임표 (...)를 선택한 다음, **onstart 실행**을 선택 하 여 테스트 합니다. 앱을 처음 로드 하는 경우와 달리 기존 컬렉션 및 변수는 이미 설정 되어 있습니다. 빈 컬렉션으로 시작 하려면 **collect** 함수 대신 **[clearcollect](function-clear-collect-clearcollect.md)** 함수를 사용 합니다.

> [!div class="mx-imgBorder"]
> OnStart 실행을 위한 앱 항목 바로 가기 메뉴 ![](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>로 거 종료 속성

저장 하지 않은 변경 내용이 손실 되지 않습니다. 사용자가 **앱을 닫기** 전에 사용자에 게 경고 **하는 데** 사용할 수 있습니다.

> [!NOTE]
> 에 포함 된 앱 (예: Power BI 및 SharePoint)에서는 작업을 수행할 **수 없습니다.**

> [!NOTE]
> 현재는 **지연 된 부하** 미리 보기 기능을 사용 하는 경우 (새 앱에 대해 기본적으로) 이러한 속성은 첫 번째 화면 에서만 컨트롤을 참조할 수 있습니다. 참조를 만들면 Power Apps 스튜디오에서 오류가 표시 되지 않지만, 게시 된 앱이 Power Apps 모바일 또는 브라우저에서 열리지 않습니다. 이 제한을 리프트 하기 위해 적극적으로 노력 하 고 있습니다. 그 동안에는 **파일** > **앱 설정** > **고급 설정** ( **미리 보기 기능**)에서 **지연 된 로드** 를 해제할 수 있습니다.

### <a name="confirmexit"></a>가 나 종료

**이 기능은** *true*인 경우 앱을 닫기 전에 확인 대화 상자를 여는 부울 속성입니다. 기본적으로이 속성은 *false*이며 대화 상자는 표시 되지 않습니다.

사용자가 변경 내용을 적용 했지만 저장 하지 않은 경우에는이 속성을 사용 하 여 확인 대화 상자를 표시 합니다. 변수 및 컨트롤 속성 (예: [**편집 양식**](../controls/control-form-detail.md) 컨트롤의 **저장 되지 않은** 속성)을 확인할 수 있는 수식을 사용 합니다.

다음 예제와 같이 데이터가 손실 될 수 있는 모든 상황에 확인 대화 상자가 나타납니다.

- [**Exit**](function-exit.md) 함수를 실행 하 고 있습니다.
- 앱이 브라우저에서 실행 되는 경우:
  - 앱이 실행 되 고 있는 브라우저 또는 브라우저 탭을 닫습니다.
  - 브라우저의 뒤로 단추를 선택 합니다.
- 앱이 Power Apps Mobile (iOS 또는 Android)에서 실행 되는 경우:
  - [**Launch**](function-param.md) 함수를 실행 하 고 있습니다.<br>**시작** 함수는 데이터가 손실 되지 않도록 다른 탭이 열리므로 브라우저에서 대화 상자를 트리거하지 않습니다.
  - Power Apps Mobile에서 다른 앱으로 전환 하려면 살짝 밀기를 진행 합니다.
  - Android 장치에서 뒤로 단추를 선택 합니다.

확인 대화 상자의 정확한 모양은 PowerApps의 장치 및 버전에 따라 다를 수 있습니다.

확인 대화 상자는 Power Apps Studio에 표시 되지 않습니다.

### <a name="confirmexitmessage"></a>메시지 아웃 메시지

기본적으로 확인 대화 상자에는 **"저장 하지 않은 변경 내용이 있을 수 있습니다."** 와 같은 일반 메시지가 표시 됩니다. 사용자의 언어로.

사용자 지정 메시지 **를 사용 하 여 확인** 대화 상자에 사용자 지정 메시지를 제공 합니다. 이 속성이 *비어*있으면 기본값이 사용 됩니다. 사용자 지정 메시지는 확인 대화 상자에 맞게 필요에 따라 잘리고 메시지를 몇 줄로 유지 합니다.

브라우저에서 확인 대화 상자가 브라우저의 일반 메시지와 함께 나타날 수 있습니다.

### <a name="example"></a>예

1. 두 가지 양식 컨트롤인 **accountform** 과 지 **폼**이 포함 된 앱을 만듭니다.

1. **앱** 개체의 기능 **종료** 속성을 다음 식으로 설정 합니다.

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    이 대화 상자는 사용자가 한 폼에서 데이터를 변경한 다음 해당 변경 내용을 저장 하지 않고 응용 프로그램을 닫으려고 하면 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![일반 확인 대화 상자](media/object-app/confirm-native.png)

1. **앱** 개체의 **개체 속성을** 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    이 대화 상자는 사용자가 계정 양식의 데이터를 변경한 다음 해당 변경 내용을 저장 하지 않고 앱을 닫으려고 하면 나타납니다.

    > [!div class="mx-imgBorder"]
    > ![양식 관련 확인 대화 상자](media/object-app/confirm-native-custom.png)
