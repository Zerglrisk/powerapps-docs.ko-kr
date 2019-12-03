---
title: Shuffle 함수 | Microsoft Docs
description: Power Apps의 순서 섞기 함수에 대 한 구문과 예제를 포함 한 참조 정보
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
ms.openlocfilehash: c67e8095a7c0ed3246bce0401bbe787becd7cea0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730151"
---
# <a name="shuffle-function-in-power-apps"></a>Power Apps의 순서 섞기 함수
[테이블](../working-with-tables.md)의 [레코드](../working-with-tables.md#records)를 무작위로 다시 정렬합니다.

## <a name="description"></a>설명
**Shuffle** 함수는 테이블의 레코드 다시 정렬합니다.

**Shuffle**은 인수와 동일한 [열](../working-with-tables.md#columns) 및 동일한 수의 행을 갖는 테이블을 반환합니다.

## <a name="syntax"></a>구문
**Shuffle**( *Table* )

* *Table* - 필수 항목입니다.  순서를 섞을 테이블입니다.

## <a name="example"></a>예
카드 놀이에 대한 세부 정보를 **Deck**라는 [컬렉션](../working-with-data-sources.md#collections)에 저장한 경우, 아래 수식은 무작위로 섞은 컬렉션의 복사본을 반환합니다.

**Shuffle(Deck)**

