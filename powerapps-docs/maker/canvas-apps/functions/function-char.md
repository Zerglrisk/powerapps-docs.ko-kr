---
title: Char 함수 | Microsoft Docs
description: 구문 및 예제를 포함 하 여 Power Apps의 Char 함수에 대 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: efd5b1ca4f30a5ab1131765d2bb38d21af7c2d2b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731372"
---
# <a name="char-function-in-power-apps"></a>Power Apps의 Char 함수

문자 코드를 문자열로 변환합니다.

## <a name="description"></a>설명

**Char** 함수는 숫자를 해당 하는 ASCII 문자가 포함 된 문자열로 변환 합니다.

## <a name="syntax"></a>구문

**Char**( *CharacterCode* )

- *CharacterCode* - 필수 항목이며, 변환할 ASCII 문자 코드입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Char( 65 )** |ASCII 코드 65에 해당하는 문자를 반환합니다. |은 |
| **Char( 105 )** |ASCII 코드 105에 해당하는 문자를 반환합니다. |보이지 |
| **Char( 35 )** |ASCII 코드 35에 해당하는 문자를 반환합니다. |"#" |

### <a name="display-a-character-map"></a>문자 맵 표시

1. 태블릿 앱의 빈 화면에서 **빈 가로** 레이아웃을 사용 하 여 [**갤러리**](../controls/control-gallery.md) 컨트롤을 추가 하 고 다음 속성을 설정 합니다.

    - **항목**: `[0,1,2,3,4,5,6,7]`
    - **너비**: 800
    - **높이**: 500
    - **Templatesize**: 100
    - **Templatepadding**: 0

1. 해당 갤러리 내에서 **빈 세로** 레이아웃을 사용 하 여 **갤러리** 컨트롤을 추가 하 고 다음 속성을 설정 합니다.

    - **항목**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **너비**: 100
    - **높이**: 500
    - **Templatesize**: 30
    - **Templatepadding**: 0

    **Items** 속성의 값은 첫 번째 갤러리의 **items** 속성 값 열에서 제공 하는 열 번호를 16으로 곱합니다 (`ThisItem.Value`의 0-7). 그런 다음 수식은 두 번째 갤러리 ( [**ForAll**](function-forall.md) 함수가 제공 하는 레코드 범위에서 0-15)의 행 번호 중 하나에 결과를 추가 합니다.

1. 두 번째 (세로) 갤러리 내에서 **레이블** 컨트롤을 추가 하 고 다음 속성을 설정 합니다.

    - **텍스트**: `ThisItem.Value`
    - **너비**: 50

1. 두 번째 (세로) 갤러리 내에서 다른 **레이블** 컨트롤을 추가 하 고 다음 속성을 설정 합니다.

    - **텍스트**: `Char( ThisItem.Value )`
    - **너비**: 50
    - **X**: 50

처음 128 ASCII 문자에 대 한 차트를 만들었습니다. 작은 사각형으로 나타나는 문자는 인쇄할 수 없습니다.

![처음 128 ASCII 문자](media/function-char/chart-lower.png)

확장 ASCII 문자를 표시 하려면 두 번째 갤러리의 **Items** 속성을이 수식으로 설정 합니다. 그러면 각 문자 값에 128이 추가 됩니다.

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![확장 ASCII 문자](media/function-char/chart-higher.png)

다른 글꼴로 문자를 표시 하려면 두 번째 레이블의 **font** 속성을 **' 춤추기 Script '** 와 같은 값으로 설정 합니다.

![춤추기 스크립트](media/function-char/chart-higher-dancing-script.png)
