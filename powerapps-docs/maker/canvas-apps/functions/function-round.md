---
title: Round, RoundDown 및 RoundUp 함수 | Microsoft Docs
description: PowerApps의 Round, RoundDown 및 RoundUp 함수에 대한 참조 정보이며, 구문을 포함하고 있습니다.
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
ms.openlocfilehash: 8480d66949994ba59f5ab84aef7999ab36a20b51
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983973"
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>PowerApps의 Round, RoundDown 및 RoundUp 함수
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

