---
title: SetFocus 함수 | Microsoft Docs
description: PowerApps의 SetFocus 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cdf34c3c4909697b70a105e5145620ab5bd31ea9
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038145"
---
# <a name="setfocus-function-in-powerapps"></a>PowerApps의 SetFocus 함수
입력 포커스를 특정 컨트롤로 이동 합니다. 

## <a name="description"></a>설명
**SetFocus** 함수는 컨트롤에 입력 포커스를 제공 합니다.  그런 다음 사용자의 키 입력을 해당 컨트롤에서 수신 하 여 텍스트 입력 컨트롤에 입력 하거나 *Enter* 키를 사용 하 여 단추를 선택할 수 있습니다.  사용자는 *Tab* 키, 터치, 마우스 또는 다른 제스처를 사용 하 여 입력 포커스를 직접 이동할 수도 있습니다. *Tab* 키 동작은 [ **TabIndex** 속성](../controls/properties-accessibility.md)에 의해 제어 됩니다.

**SetFocus** 함수를 사용 하 여 (각각 아래 예제가 있는 경우)에 포커스를 설정 합니다.
- 사용자에 게 다음 작업을 안내 하 고 더 빠른 데이터를 제공 하기 위해 새로 노출 되거나 활성화 된 입력 컨트롤입니다.
- 폼의 유효성을 검사 하 고, 문제를 해결 하기 위해 잘못 된 입력 컨트롤을 표시 하 고 표시 합니다.
- 화면의 **Onvisible** 속성을 사용 하 여 첫 번째 입력 컨트롤에 포커스를 주는 화면이 표시 [**됩니다.** ](../controls/control-screen.md)

포커스가 있는 컨트롤은 [**FocusedBorderColor**](../controls/properties-color-border.md) 및 [**FocusedBorderThickness**](../controls/properties-color-border.md) 속성에 따라 시각적으로 달라질 수 있습니다.

## <a name="limitations"></a>제한 사항

**SetFocus** 는 다음에만 사용할 수 있습니다.
- [**Button**](../controls/control-button.md) 컨트롤
- [**아이콘**](../controls/control-shapes-icons.md) 컨트롤
- [**이미지**](../controls/control-image.md) 컨트롤
- [**레이블**](../controls/control-text-box.md) 컨트롤
- [**TextInput**](../controls/control-text-input.md) 컨트롤

[**갤러리**](../controls/control-gallery.md) 컨트롤, [**편집 양식**](../controls/control-form-detail.md) 컨트롤 또는 [구성 요소](../create-component.md)내에 있는 컨트롤에 포커스를 설정할 수 없습니다.  **SetFocus** 는 scrollbale 화면에서 컨트롤과 함께 사용할 수 있습니다.

**SetFocus** 호출을 포함 하는 수식과 동일한 화면에 있는 컨트롤로만 포커스를 설정할 수 있습니다.

[**DisplayMode**](../controls/properties-core.md) 속성이 **Disabled** 로 설정 된 컨트롤에 포커스를 설정 하려고 하면 아무런 효과가 없습니다.  포커스는 이전에 있던 위치에 유지 됩니다.

Apple iOS에서 수동 사용자 작업으로 인해 **SetFocus** 가 시작 된 경우 소프트 키보드만 자동으로 표시 됩니다.  예를 들어 단추의 **Onselect** 속성에서를 호출 하면 화면에 표시 되는 **onselect** 에서 호출 하는 동안 소프트 키보드를 표시 합니다. 

**SetFocus** 는 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**SetFocus** ( *컨트롤* )

* *Control* – 필수 항목입니다.  입력 포커스를 제공 하는 컨트롤입니다.

## <a name="examples"></a>예

### <a name="focus-on-a-newly-exposed-or-enabled-input-control"></a>새로 노출 되거나 활성화 된 입력 컨트롤에 포커스

많은 쇼핑 카트는 고객이 배송 주소를 청구 주소로 사용할 수 있도록 하 여 동일한 정보를 두 번 입력할 필요를 완화 합니다.  다른 청구 주소가 필요한 경우 청구 주소 텍스트 입력 상자를 사용할 수 있으며,이에 따라 사용자가 새로 사용 하도록 설정 된 컨트롤을 사용 하 여 더 빠르게 데이터를 입력할 수 있습니다.  

![사용자 지정 대금 청구 주소를 사용 하도록 선택 하는 애니메이션으로, 포커스를 청구 이름 입력 컨트롤로 이동 하 고 배송 주소 자동 동기화를 해제 합니다.](media/function-setfocus/shipping-billing.gif)

여기에는 다양 한 수식이 있지만 포커스를 이동 하는 수식은 **확인란** 컨트롤의 **onuncheck 취소** 속성에 있습니다.

```powerappa-dot
SetFocus( BillingName ) 
```

*Tab* 키를 사용 하 여 한 필드에서 다른 필드로 포커스를 빠르게 이동할 수도 있습니다.  보다 잘 이해할 수 있도록 *Tab* 키가 애니메이션에서 사용 되지 않았습니다.

이 예를 만들려면 다음을 수행 합니다.
1. 새 앱을 만듭니다.
1. "배송 주소", "이름:", "주소:", "청구 주소", "이름:" 및 "주소:" 텍스트를 사용 하 여 [ **레이블** 컨트롤](../controls/control-text-box.md) 을 추가 하 고 애니메이션에 표시 된 대로 위치를 조정 합니다.
1. [ **텍스트 입력** 컨트롤](../controls/control-text-input.md) 을 추가 하 고 이름을 파일 **이름**으로 바꿉니다.
1. [ **텍스트 입력** 컨트롤](../controls/control-text-input.md) 을 **추가 하 고 이름을 파일 이름**으로 바꿉니다.
1. [ **확인란** 컨트롤](../controls/control-check-box.md) 을 추가 하 고 **syncaddresses**의 이름을 바꿉니다.
1. 이 컨트롤의 **Text** 속성을 수식 `"Use Shipping address as Billing address"`으로 설정 합니다.
1. [ **텍스트 입력** 컨트롤](../controls/control-text-input.md) 을 추가 하 고 이름을 **BillingName**로 바꿉니다.
1. 이 컨트롤의 **기본** 속성을 수식 `ShippingName`으로 설정 합니다.
1. 이 컨트롤의 **DisplayMode** 속성을 수식 `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`으로 설정 합니다.  그러면 확인란 컨트롤의 상태에 따라이 컨트롤을 자동으로 사용 하거나 사용 하지 않도록 설정 합니다.
1. [ **텍스트 입력** 컨트롤](../controls/control-text-input.md) 을 추가 하 고 이름을 **BillingAddress**로 바꿉니다.
1. 이 컨트롤의 **기본** 속성을 수식 `ShippingAddress`으로 설정 합니다.
1. 이 컨트롤의 **DisplayMode** 속성을 수식 `If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`으로 설정 합니다.  그러면 확인란 컨트롤의 상태에 따라이 컨트롤을 자동으로 사용 하거나 사용 하지 않도록 설정 합니다.
1. 확인란의 **Default** 속성을 수식 `true`으로 설정 합니다.  이렇게 하면 기본적으로 청구 주소가 배송 주소와 같은 값을 사용 합니다.
1. 확인란의 **Oncheck** 속성을 수식 `Reset( BillingName ); Reset( BillingAddress )`으로 설정 합니다.  사용자가 배송 및 대금 청구 주소를 동기화 하도록 선택 하면 청구 주소 필드의 모든 사용자 입력이 지워집니다. 그러면 각 사용자 입력에서 해당 **하는 배송** 주소 필드의 값을 가져올 수 있습니다.
1. 확인란의 **Onuncheck 취소** 속성을 수식 `SetFocus( BillingName )`으로 설정 합니다.  사용자가 다른 청구 주소를 선택 하는 경우이를 통해 청구 주소의 첫 번째 컨트롤로 포커스가 이동 합니다.  **DisplayMode** 속성으로 인해 컨트롤이 이미 사용 하도록 설정 되었습니다.

### <a name="focus-on-validation-issues"></a>유효성 검사 문제에 집중

> [!NOTE]
> 이 예제는 **편집 양식** 컨트롤 이지만 현재 **SetFocus** 는 해당 컨트롤에서 아직 지원 되지 않습니다.  대신이 예제에서는 스크롤 가능한 화면을 사용 하 여 입력 컨트롤을 호스팅합니다.

폼의 유효성을 검사할 때 문제가 있는 경우에도 메시지를 표시 하는 것이 아니라 사용자가 잘못 된 필드로 이동 하는 것이 유용할 수 있습니다.  문제의 필드가 화면 밖으로 스크롤 되 고 표시 되지 않는 경우에 특히 유용할 수 있습니다.

![데이터 입력 폼의 유효성을 검사 하 고 메시지를 표시 하지 않고 화면 밖으로 스크롤 하는 경우에도 입력 포커스를 잘못 된 입력 컨트롤로 설정 하는 애니메이션입니다.](media/function-setfocus/scrollable-screen.gif)

이 애니메이션에서 유효성 검사 단추는 모든 필드가 제대로 채워질 때까지 반복적으로 눌러져 있습니다.  마우스 포인터는 화면 맨 위에서 아래로 이동 하지 않습니다.   대신에 **SetFocus** 함수는이 수식과 함께 주의가 필요한 컨트롤에 대 한 입력 포커스를 이동 했습니다.

```powerapps-dot
If( IsBlank( Name ), 
        Notify( "Name requires a value", Error ); SetFocus( Name ),
    IsBlank( Street1 ), 
        Notify( "Street Address 1 requires a value", Error ); SetFocus( Street1 ),
    IsBlank( Street2 ), 
        Notify( "Street Address 2 requires a value", Error ); SetFocus( Street2 ),
    IsBlank( City ), 
        Notify( "City requires a value", Error ); SetFocus( City ),
    IsBlank( County ), 
        Notify( "County requires a value", Error ); SetFocus( County ),
    IsBlank( StateProvince ), 
        Notify( "State or Province requires a value", Error ); SetFocus( StateProvince ),
    IsBlank( PostalCode ), 
        Notify( "Postal Code requires a value", Error ); SetFocus( PostalCode ),
    IsBlank( Phone ), 
        Notify( "Contact Phone requires a value", Error ); SetFocus( Phone ),
    Notify( "Form is Complete", Success )
)
```

이 예를 만들려면 다음을 수행 합니다.
1. 비어 있는 새 휴대폰 앱을 만듭니다.
1. **삽입** 메뉴에서 **새로 만들기 화면**을 선택 하 고 **스크롤**가능을 선택 합니다.
1. 화면의 가운데 섹션에서 **텍스트 입력** 컨트롤을 추가 하 고 이름을 **name**, **Street1**, **Street2**, **City**, **관할지**, **StateProvince**, **PostalCode**및 **Phone**으로 입력 합니다. 각 필드 위에 **레이블** 컨트롤을 추가 하 여 필드를 식별 합니다.  모든 컨트롤에 맞게 충분히 길지 않은 경우 섹션의 크기를 조정 해야 할 수 있습니다.
1. 화면 위쪽에서 스크롤 가능 섹션 위에 확인 표시 [ **아이콘** 컨트롤](../controls/control-shapes-icons.md) 을 추가 합니다.  
1. 아이콘 컨트롤의 **onselect** 속성을 위에 지정 된 수식 `If( IsBlank( ...` 으로 설정 합니다.

### <a name="focus-when-displaying-a-screen"></a>화면을 표시할 때 포커스

> [!NOTE]
> 이 예제는 **편집 양식** 컨트롤로 표시 되지만 unforutnatley **SetFocus** 는 해당 컨트롤에서 아직 지원 되지 않습니다.  대신이 예제에서는 스크롤 가능한 화면을 사용 하 여 입력 컨트롤을 호스팅합니다.

입력 컨트롤을 노출 하는 것과 유사 하 게 데이터 입력 화면을 표시 하는 경우에는 데이터 입력을 빠르게 하기 위해 첫 번째 입력 컨트롤에 집중 하는 것이 좋습니다.

![데이터 입력 화면을 표시할 때 사용 하지 않고 SetFocus를 사용 하는 경우의 병렬 비교를 표시 하는 애니메이션](media/function-setfocus/visible-setfocus.gif)

이 애니메이션에서 왼쪽의 데이터 입력 화면은 **SetFocus**를 사용 하지 않습니다.  디스플레이에 포커스가 있는 입력 컨트롤이 없습니다. 사용자가 tab 키를 누르거나 마우스를 이동 하거나 다른 수단을 사용 하 여 **이름** 필드에 값을 입력할 수 있도록 해야 합니다.

오른쪽에는 데이터 입력 화면의 **Onvisible** 속성이 다음 수식으로 설정 된 동일한 앱이 있습니다.

```powerapps-dot
SetFocus( Name )
```

이렇게 하면 포커스가 **이름** 필드에 자동으로 설정 됩니다.  사용자는 이전 작업이 필요 없이 필드를 즉시 입력 하 고 탭을 이동할 수 있습니다.

이 예를 만들려면 다음을 수행 합니다.
1. 위의 "유효성 검사 문제에 초점을 맞춘" 앱을 만듭니다.
1. 이 화면에서 **Onvisible** 속성을 수식 `SetFocus( Name )`으로 설정 합니다.
1. 두 번째 화면을 추가 합니다.
1. [ **단추** 컨트롤](../controls/control-button.md)을 추가 합니다.
1. 이 컨트롤의 **Onselect** 속성을 수식 `Navigate( Screen1 )`으로 설정 합니다.
1. 이 화면에서 앱을 미리 봅니다.  단추를 누릅니다.  **Onvisible** 수식이 평가 되 고 **이름** 필드가 자동으로 포커스를 받습니다.
