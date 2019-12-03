---
title: Value 함수 | Microsoft Docs
description: Power Apps의 Value 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ec168ce00fff1abdb624a8decc1c5d44ec7bd61c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729780"
---
# <a name="value-function-in-power-apps"></a>Power Apps의 Value 함수
텍스트의 문자열을 숫자로 변환합니다.

## <a name="description"></a>설명
**Value** 함수는 숫자 값으로 숫자 문자를 포함하는 텍스트의 문자열을 변환합니다. 사용자가 텍스트로 입력한 숫자에 대해 계산을 수행해야 할 경우 이 함수를 사용합니다.

다른 언어는 **,**  및 **로 해석합니다.** 다르게 합니다.  기본적으로 텍스트는 현재 사용자의 언어로 해석됩니다.  **[Language](function-language.md)** 함수로 반환되는 동일한 언어 태그를 사용하는 언어 태그로 사용할 언어를 지정할 수 있습니다.

문자열의 형식에 대한 참고 사항:

* 문자열은 현재 언어에 대한 통화 기호로 접두사일 수 있습니다.  통화 기호는 무시됩니다.  다른 언어에 대한 통화 기호는 무시되지 않습니다.
* 문자열은 백분율임을 나타내는 백분율 기호( **%** )를 끝에 포함할 수 있습니다.  숫자는 반환되기 전에 100으로 나뉩니다.  백분율 및 통화 기호를 혼합할 수 없습니다.
* 문자열은 "12e3"으로 표시된 12 x 10<sup>3</sup>이 있는 과학적 표기법일 수 있습니다.

숫자가 적절한 형식이 아닌 경우 **Value**는 *공백*을 반환합니다.

날짜 및 시간 값을 변환하려면 [**DateValue**](function-datevalue-timevalue.md), [**TimeValue**](function-datevalue-timevalue.md) 또는 [**DateTimeValue**](function-datevalue-timevalue.md) 함수를 사용합니다.

## <a name="syntax"></a>구문
**Value**( *String* [, *LanguageTag* ] )

* *String* - 필수 항목입니다. 숫자 값으로 변환할 문자열입니다.
* *LanguageTag* - 선택 항목입니다.  문자열을 구문 분석하는 언어 태그입니다.  지정되지 않은 경우 현재 사용자의 언어를 사용합니다.

## <a name="examples"></a>예
이러한 수식을 실행하는 사용자는 미국에 있으며 자신의 언어를 영어로 선택했습니다.  **Language** 함수는 "en-US"를 반환하고 있습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Value( "123.456" )** |"en-US"의 기본 언어가 사용되며 소수 구분 기호로 마침표를 사용합니다. |123.456 |
| **Value( "123.456", "es-ES" )** |"es-ES"는 스페인에서 스페인어에 대한 언어 태그입니다.  스페인에서 마침표는 천 단위 구분 기호입니다. |123456 |
| **Value( "123,456" )** |"en-US"의 기본 언어가 사용되며 천 단위 구분 기호로 쉼표를 사용합니다. |123456 |
| **Value( "123,456", "es-ES" )** |"es-ES"는 스페인에서 스페인어에 대한 언어 태그입니다.  스페인에서 쉼표는 소수 구분 기호입니다. |123.456 |
| **Value( "12.34%" )** |문자열의 끝에서 백분율 기호는 백분율임을 나타냅니다. |0.1234 |
| **Value( "$ 12.34" )** |현재 언어에 대한 통화 기호는 무시됩니다. |12.34 |
| **Value( "24e3" )** |12 x 10<sup>3</sup>에 대한 과학적 표기법입니다. |24000 |

