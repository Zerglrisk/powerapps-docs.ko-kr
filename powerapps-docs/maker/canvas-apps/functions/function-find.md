---
title: Find 함수 | Microsoft Docs
description: Power Apps의 찾기 함수에 대 한 구문과 예제를 포함 한 참조 정보
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
ms.openlocfilehash: 62254bf46836ffc8ed5fa5b7685561b611db49a7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730994"
---
# <a name="find-function-in-power-apps"></a>Power Apps에서 함수 찾기
다른 문자열 내에 텍스트 문자열이 있으면 찾습니다.

## <a name="description"></a>설명
**Find** 함수는 다른 문자열 내에서 문자열을 찾고 대/소문자를 구분합니다. 대/소문자를 무시하려면 먼저 인수에 **[Lower](function-lower-upper-proper.md)** 함수를 사용합니다.

**Find**는 찾은 문자열의 시작 위치를 반환합니다.  위치 1은 문자열의 첫 번째 문자입니다. **Find**는 검색하는 문자열 내에 찾는 문자열이 포함되어 있지 않은 경우 *blank*를 반환합니다.

## <a name="syntax"></a>구문
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString* - 필수 항목입니다.  찾을 문자열입니다.
* *WithinString* - 필수 항목입니다.  검색 범위 문자열입니다.
* *StartingPosition* - 선택 항목입니다.  검색을 시작할 시작 위치입니다.  위치 1이 첫 번째 문자입니다.

