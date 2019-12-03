---
title: Reset 함수 | Microsoft Docs
description: Power Apps의 Reset 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 20109be5e9c77af75409973a32fe46c353d57282
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730326"
---
# <a name="reset-function-in-power-apps"></a>Power Apps에서 함수 다시 설정
사용자 변경 내용을 삭제하면서 해당 기본값에 대한 컨트롤을 다시 설정합니다.  

## <a name="description"></a>설명
**Reset** 함수는 해당 **Default** 속성 값에 대한 컨트롤을 다시 설정합니다.  사용자 변경 내용이 삭제됩니다.

[**갤러리**](../controls/control-gallery.md) 내에 있는 컨트롤 또는 [**편집 양식**](../controls/control-form-detail.md) 컨트롤은 그러한 컨트롤 외부에서 다시 설정할 수 없습니다.  동일한 갤러리 또는 양식 내 컨트롤에 있는 수식에서 컨트롤을 다시 설정할 수 있습니다.  또한 양식 내 모든 컨트롤은 [**ResetForm**](function-form.md) 함수로 다시 설정할 수 있습니다. 

**Reset** 함수 사용은 입력 컨트롤의 **Reset** 속성 전환에 대한 대안으로 일반적으로 선호됩니다.  많은 컨트롤을 여러 수식에서 한꺼번에 다시 설정해야 하는 경우에 **Reset** 속성을 선택하는 것이 좋습니다.  **Reset** 속성 전환은 **Reset = Button.Pressed** 수식을 사용한 [**Button**](../controls/control-button.md) 컨트롤에서 수행하거나 **Reset = MyVar**을 사용한 변수에서 **Button.OnSelect = Set( MyVar, true ); Set( MyVar, false )** 수식을 사용한 **MyVar** 전환으로 수행할 수 있습니다.    

또한 입력 컨트롤은 자신의 **Default** 속성이 변경될 때 다시 설정됩니다.

**Reset**은 반환 값이 없으며 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Reset**( *Control* )

* *Control* – 필수 항목입니다. 다시 설정할 컨트롤입니다.

## <a name="example"></a>예
1. 화면에서 **Text input** 컨트롤을 삽입합니다.  기본적으로의 이름은 **TextInput1**이 되며, 해당 **Default** 속성은 **“Text input”** 으로 설정됩니다.
2. 텍스트 상자에 새 값을 입력합니다.  
3. 화면에서 **Button** 컨트롤을 삽입합니다.
4. 단추의 **OnSelect** 속성을 **Reset( TextInput1 )** 으로 설정합니다.
5. 단추를 선택합니다.  컨트롤의 끝 쪽을 선택하여 작성할 때에도 수행할 수 있습니다.
6. 텍스트 상자의 콘텐츠는 **Default** 속성의 값으로 반환됩니다.

