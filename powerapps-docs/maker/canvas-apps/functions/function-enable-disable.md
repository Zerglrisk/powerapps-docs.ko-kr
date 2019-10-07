---
title: Enable 및 Disable 함수 | Microsoft Docs
description: PowerApps의 Enable 및 Disable 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: 1b58b57ae880f54fc7fccb5aa4c49f0e2fcad6d0
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992775"
---
# <a name="enable-and-disable-functions-in-powerapps"></a>PowerApps의 Enable 및 Disable 함수
[신호](signals.md)를 켜거나 끕니다.

## <a name="overview"></a>개요
일부 신호는 자주 변경되어 그 때마다 앱에서 다시 계산해야 합니다.  장기간에 걸쳐 급격한 변화가 발생하면 디바이스의 배터리가 소모될 수 있습니다. 이 함수를 사용하면 수동으로 신호를 켜거나 끌 수 있습니다.

신호를 사용하지 않는 동안은 자동으로 꺼집니다.

## <a name="description"></a>설명
**Enable** 및 **Disable** 함수는 각각 신호를 켜고 끕니다.

이 함수는 현재 **[위치](signals.md)** 신호에서만 작동합니다.

이 함수에는 반환 값이 없습니다. [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

## <a name="syntax"></a>구문
**Enable**( *Signal* )<br>**Disable**( *Signal* )

* *Signal* - 필수 항목입니다.  켜거나 끌 신호입니다.

