---
title: Defaults 함수 | Microsoft Docs
description: Power Apps의 기본값 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ad3d8198d73a698abb771aef7230c12b48ff0f56
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731113"
---
# <a name="defaults-function-in-power-apps"></a>Power Apps의 기본값 함수
[데이터 원본](../working-with-data-sources.md)의 기본값을 반환합니다.  

## <a name="description"></a>설명
**Defaults** 함수를 사용하여 데이터 입력 양식을 미리 채우면 채우기가 쉬워집니다.

이 함수는 데이터 원본의 기본값을 포함하는 [레코드](../working-with-tables.md#records)를 반환합니다.  데이터 원본 내의 [열](../working-with-tables.md#columns)에 기본값이 없으면 해당 속성은 표시되지 않습니다.

데이터 원본이 제공하는 기본 정보의 양은 전혀 제공하지 않는 경우를 포함하여 다양합니다.  [컬렉션](../working-with-data-sources.md#collections)을 사용하거나 기본값을 지원하지 않는 다른 데이터 원본을 사용하는 경우 **Defaults** 함수는 [빈](function-isblank-isempty.md) 레코드를 반환합니다.

**Defaults** 함수를 **[Patch](function-patch.md)** 함수와 결합하여 [레코드를 생성](../working-with-data-sources.md)할 수 있습니다.

## <a name="syntax"></a>구문
**Defaults**( *DataSource* )

* *DataSource* – 필수 항목이며, 기본값이 필요한 데이터 원본입니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |**점수** 데이터 원본의 기본값을 반환합니다. |**{ Score: 0 }** |

