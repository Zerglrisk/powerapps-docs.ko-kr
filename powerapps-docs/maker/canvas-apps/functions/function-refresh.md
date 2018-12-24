---
title: Refresh 함수 | Microsoft Docs
description: PowerApps의 Refresh 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2999665e5882245b594468b6babe67be575c5c1e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843600"
---
# <a name="refresh-function-in-powerapps"></a>PowerApps의 Refresh 함수
[데이터 원본](../working-with-data-sources.md)의 [레코드](../working-with-tables.md#records)를 새로 고칩니다.

## <a name="description"></a>설명
**Refresh** 함수는 데이터 원본의 새 복사본을 검색합니다.  다른 사용자가 변경한 내용을 볼 수 있습니다.

**Refresh**에는 반환 값이 없으며 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Refresh**( *DataSource* )

* *DataSource* – 필수 항목입니다. 새로 고칠 데이터 원본입니다.

## <a name="example"></a>예
아래 예제는 다음 데이터로 시작하는 **IceCream**이라는 데이터 원본을 새로 고칩니다.

![](media/function-refresh/icecream.png)

다른 디바이스의 사용자가 **Strawberry** 레코드의 **Quantity**를 **400**으로 변경합니다.  변경 내용은 수식이 실행될 때까지 볼 수 없습니다.

**Refresh(IceCream)**

수식이 실행된 후 **IceCream** 데이터 원본에 바인딩된 갤러리가 **Strawberry**의 업데이트된 값을 표시합니다.

![](media/function-refresh/icecream-after.png)

