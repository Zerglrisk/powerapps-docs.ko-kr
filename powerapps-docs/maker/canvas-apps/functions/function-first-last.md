---
title: First, FirstN, Last 및 LastN 함수 | Microsoft Docs
description: PowerApps의 First, FirstN, Last 및 LastN 함수에 대한 구문과 예제를 포함한 참조 정보
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 947a6c369c41b1ff67c611fa734f927227dde991
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="first-firstn-last-and-lastn-functions-in-powerapps"></a>PowerApps의 First, FirstN, Last 및 LastN 함수
테이블의 첫 번째 또는 마지막 [레코드](../working-with-tables.md#records) 집합을 반환합니다.

## <a name="description"></a>설명
**First** 함수는 [테이블](../working-with-tables.md)의 첫 번째 레코드를 반환합니다.

**FirstN** 함수는 테이블의 첫 번째 레코드 집합을 반환합니다. 두 번째 인수는 반환할 레코드 수를 지정합니다.

**Last** 함수는 테이블의 마지막 레코드를 반환합니다.

**LastN** 함수는 테이블의 마지막 레코드 집합을 반환합니다. 두 번째 인수는 반환할 레코드 수를 지정합니다.

**First** 및 **Last**는 단일 레코드를 반환합니다.  **FirstN** 및 **LastN**는 단일 레코드만 지정해도 테이블을 반환합니다.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>구문
**First**( *Table* )<br>**Last**( *Table* )

* *Table* - 필수 항목입니다. 연산을 수행할 테이블입니다.

**FirstN**( *Table* [, *NumberOfRecords* ] )<br>**LastN**( *Table* [, *NumberOfRecords* ] )

* *Table* - 필수 항목입니다. 연산을 수행할 테이블입니다.
* *NumberOfRecords* - 선택 항목입니다.  반환할 레코드의 수입니다. 이 인수를 지정하지 않으면 함수는 하나의 레코드를 반환합니다.

## <a name="examples"></a>예
다음 수식은 **Employees**라는 테이블에서 첫 번째 레코드를 반환합니다.<br>
**First(Employees)**

다음 수식은 **Employees**라는 테이블에서 마지막 15개의 레코드를 반환합니다.<br>
**LastN(Employees, 15)**

