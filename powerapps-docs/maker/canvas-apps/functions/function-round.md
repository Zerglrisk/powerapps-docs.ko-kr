---
title: Round, RoundDown 및 RoundUp 함수 | Microsoft Docs
description: Power Apps의 Round, RoundDown 및 RoundUp 함수에 대 한 구문을 포함 한 참조 정보
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
ms.openlocfilehash: 3b319f831291b1d0d21f3ed4699a144beb023611
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730304"
---
# <a name="round-rounddown-and-roundup-functions-in-power-apps"></a>Power Apps의 Round, RoundDown 및 RoundUp 함수
숫자를 반올림합니다.

## <a name="description"></a>설명
**Round**, **RoundDown** 및 **RoundUp** 함수는 숫자를 지정된 소수 자릿수로 반올림합니다.

* **Round**는 다음 숫자가 5 이상이면 올림합니다. 그렇지 않으면 이 함수에서 내림합니다.
* **RoundDown**은 항상 이전 낮은 숫자로 내림합니다.
* **RoundUp**은 항상 다음 높은 숫자로 올림합니다.

단일 숫자를 전달하면 반환 값은 해당 숫자를 반올림한 값입니다.  숫자가 포함된 단일 열 [테이블](../working-with-tables.md)을 전달하면 반환 값은 해당 숫자를 반올림한 값이 포함된 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.

## <a name="syntax"></a>구문
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Number* - 필수 항목입니다. 반올림할 숫자입니다.
* *DecimalPlaces* - 필수 항목이며,  반올림할 소수점의 오른쪽에 있는 자릿수입니다.  0을 사용하여 정수로 반올림합니다.  

