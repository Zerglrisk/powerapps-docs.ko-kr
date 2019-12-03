---
title: ShowError 함수 | Microsoft Docs
description: Power Apps의 ShowError 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02881fdf284a174f5118e7ee0ae185cca61578f8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730172"
---
# <a name="notify-function-in-power-apps"></a>Power Apps에서 함수 알림
사용자에게 배너 메시지를 표시합니다.

## <a name="description"></a>설명
**Notify** 함수는 화면 맨 위에서 사용자에게 배너 메시지를 표시하여 현재 표시되는 것과 겹치게 합니다.  

메시지의 형식에 따라 적절한 색 및 아이콘을 사용합니다.   형식은 함수에 대한 두 번째 인수에서 지정됩니다.

| NotificationType 인수 | 설명 |
| --- | --- |
| **NotificationType.Error** | 메시지를 오류로 표시합니다. |
| **NotificationType.Information**(기본값) | 메시지를 정보 제공으로 표시합니다.  |
| **NotificationType.Success** | 메시지를 성공으로 표시합니다. |
| **NotificationType.Warning** | 메시지를 경고로 표시합니다. |

앱을 제작할 때와 최종 사용자가 앱을 사용할 때 모두 메시지가 표시됩니다.

**Notify**는 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

**Notify**는 [**IfError**](function-iferror.md) 함수와 쌍을 이루어 오류를 감지하고 사용자 지정 오류 메시지를 사용하여 오류를 보고할 수 있습니다.

Power Apps **는 알림과 완전히**다른 메커니즘을 사용 하 여 푸시 알림을 보낼 수도 있습니다.  자세한 내용은 [Power Apps에서 알림 보내기](../add-notifications.md)를 참조 하세요.

**Notify**는 항상 *true*를 반환합니다.

참고: 오류 메시지만 표시할 수 있는 경우 이 함수의 이전 이름은 **ShowError**입니다.

## <a name="syntax"></a>구문
**Notify**( *Message*, [ *NotificationType* ] )

* *메시지* – 필수입니다.  사용자에게 표시할 메시지입니다.
* *NotificationType* – 선택 사항입니다.  위 테이블에서 표시한 메시지의 형식입니다.  기본값은 **NotificationType.Information**입니다.  

## <a name="examples"></a>예

### <a name="step-by-step"></a>단계별 가이드

1. **단추** 컨트롤을 화면에 추가합니다.

2. **단추**의 **OnSelect** 속성을 다음과 같이 설정합니다.

    **Notify( "Hello, World" )**

3. 단추를 클릭하거나 누릅니다.  

    단추를 클릭할 때마다 **Hello, World**라는 메시지가 정보 제공으로 사용자에게 표시됩니다.

    ![제작 환경에 Notify를 호출하는 Button.OnSelect가 표시되고 그에 따른 Hello, World 메시지가 사용자에게 파란색 배너 메시지로 표시됩니다.](media/function-showerror/hello-world.png)

4. 오류를 나타내는 메시지의 형식을 변경합니다.  수식에 두 번째 인수를 추가합니다.

    **Notify( "Hello, World", NotificationType.Error )**

5. 단추를 클릭하거나 누릅니다.

    이제 단추를 클릭할 때마다 **Hello, World**라는 메시지가 오류로 사용자에게 표시됩니다.

    ![제작 환경에 Notify를 호출하는 Button.OnSelect가 표시되고 그에 따른 Hello, World 메시지가 사용자에게 빨간색 배너 메시지로 표시됩니다.](media/function-showerror/hello-world-error.png)

4. 경고를 나타내는 메시지의 형식을 변경합니다.  수식에서 두 번째 인수를 변경합니다.

    **Notify( "Hello, World", NotificationType.Warning )**

5. 단추를 클릭하거나 누릅니다.

    이제 단추를 클릭할 때마다 **Hello, World**라는 메시지가 경고로 사용자에게 표시됩니다.

    ![제작 환경에 Notify를 호출하는 Button.OnSelect가 표시되고 그에 따른 Hello, World 메시지가 사용자에게 주황색 배너 메시지로 표시됩니다.](media/function-showerror/hello-world-warning.png)

4. 성공을 나타내는 메시지의 형식을 변경합니다.  수식에서 두 번째 인수를 변경합니다.

    **Notify( "Hello, World", NotificationType.Success )**

5. 단추를 클릭하거나 누릅니다.

    이제 단추를 클릭할 때마다 **Hello, World**라는 메시지가 성공으로 사용자에게 표시됩니다.

    ![제작 환경에 Notify를 호출하는 Button.OnSelect가 표시되고 그에 따른 Hello, World 메시지가 사용자에게 초록색 배너 메시지로 표시됩니다.](media/function-showerror/hello-world-success.png)
