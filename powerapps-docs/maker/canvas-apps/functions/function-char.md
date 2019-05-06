---
title: Char 함수 | Microsoft Docs
description: PowerApps의 Char 함수에 대한 참조 정보이며, 구문과 예제를 포함하고 있습니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1b598cc863ec01bcb2a66a9510cb48ec5203e679
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559710"
---
# <a name="char-function-in-powerapps"></a>PowerApps의 Char 함수

문자 코드를 문자열로 변환합니다.

## <a name="description"></a>설명

**Char** 함수는 숫자를 ASCII 문자에 해당하는 문자열로 변환합니다.

## <a name="syntax"></a>구문

**Char**( *CharacterCode* )

- *CharacterCode* - 필수 항목이며, 변환할 ASCII 문자 코드입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Char( 65 )** |ASCII 코드 65에 해당하는 문자를 반환합니다. |"A" |
| **Char( 105 )** |ASCII 코드 105에 해당하는 문자를 반환합니다. |"i" |
| **Char( 35 )** |ASCII 코드 35에 해당하는 문자를 반환합니다. |"#" |

### <a name="display-a-character-map"></a>문자 매핑 표시

1. 태블릿 앱에서 사용되는 빈 화면에서 **빈 가로** 레이아웃의 [ **갤러리** ](../controls/control-gallery.md) 컨트롤을 추가한 다음, 다음 속성을 설정합니다.

    - **Items**: `[0,1,2,3,4,5,6,7]`
    - **Width**: 800
    - **Height**: 500
    - **TemplateSize**: 100
    - **TemplatePadding**: 0

1. 해당 갤러리 안에, **빈 세로** 레이아웃의 **갤러리** 컨트롤을 추가하고, 다음 속성을 설정합니다.

    - **Items**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **Width**: 100
    - **Height**: 500
    - **TemplateSize**: 30
    - **TemplatePadding**: 0

    **Items** 속성의 값은 첫 번째 갤러리(`ThisItem.Value`의 0-7)의 **Items** 속성에서 제공하는 열 수에 16을 곱합니다. 수식은 그 결과를 두 번째 갤러리([ **ForAll** ](function-forall.md) 함수가 제공하는 레코드 범위의 0 ~ 15)의 행 수의 하나에 더합니다.

1. 두 번째 (세로) 갤러리 안에 **레이블** 컨트롤을 추가하고 다음 속성을 설정합니다.

    - **Text**: `ThisItem.Value`
    - **Width**: 50

1. 두 번째 (세로) 갤러리 안에 또 다른 **레이블** 컨트롤을 추가하고 다음 속성을 설정합니다.

    - **Text**: `Char( ThisItem.Value )`
    - **Width**: 50
    - **X**: 50

처음 128개 ASCII 문자의 차트를 만들었습니다. 작은 사각형으로 표시되는 문자는 인쇄할 수 없는 문자입니다.

![먼저 128 개의 ASCII 문자](media/function-char/chart-lower.png)

확장된 ASCII 문자를 표시하려면, 두 번째 갤러리의 **Items** 속성을 다음 수식으로 설정하여, 각 문자 값에 128을 더합니다.

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![확장 된 ASCII 문자](media/function-char/chart-higher.png)

다른 글꼴로 문자를 표시하려면, 두 번째 레이블의 **Font** 속성을 **Dancing Script**와 같은 값으로 설정합니다.

![스크립트 dancing](media/function-char/chart-higher-dancing-script.png)
