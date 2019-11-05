---
title: Common Data Service에서 날짜 및 시간 필드의 동작 및 형식 MicrosoftDocs
description: 포털에서 사용 되는 날짜 및 시간 필드의 동작 및 형식입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 785b5fa7def4a5b8e4964e888567d64643405708
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553328"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>날짜 및 시간 필드의 동작 및 형식

Common Data Service에서는 날짜 및 시간 데이터 형식이 많은 시스템 엔터티 필드에 사용 됩니다. 예를 들어 마케팅 캠페인에서 계정이 마지막으로 사용 된 시기를 표시 하거나 사례가 에스컬레이션 된 날짜 및 시간을 표시할 수 있습니다. 또한 날짜 및 시간 필드를 포함 하는 사용자 지정 엔터티를 만들 수 있습니다. 필드에 표시 되는 내용에 따라 포털 양식과 모눈에 대해 다음과 같은 필드 동작 중 하나를 선택할 수 있습니다. 
- **사용자 로컬**: 필드 값은 사용자의 현지 시간으로 표시 되 고 현재 포털 언어/로캘에 따라 형식이 지정 됩니다. 값은 Common Data Service에서 UTC 표준 시간대 형식으로 저장 됩니다. 다른 표준 시간대에 있는 Common Data Service (또는 다른 포털 사용자)의 사용자가 해당 값을 볼 경우 해당 사용자의 표준 시간대로 변환 된 것을 볼 수 있습니다.
- **날짜만**: 필드 값에는 날짜만 포함 되 고 표준 시간대 변환은 표시 되지 않습니다. 값의 시간 부분은 항상 오전 12:00입니다. 한 사용자가 입력 한 값은 다른 표준 시간대 (예: 생년월일)의 다른 사용자에 의해 동일 하 게 표시 됩니다.
  
  > [!Note]
  > 저장 한 후에는이 필드의 동작을 변경할 수 없습니다.
  
- **표준 시간대 독립적**: 필드 값은 날짜 및 시간을 포함 하며 표준 시간대 변환이 없는 상태에서 표시 됩니다. 한 사용자가 입력 한 값은 다른 표준 시간대의 다른 사용자와 동일 하 게 표시 됩니다.
  
  > [!Note]
  > 저장 한 후에는이 필드의 동작을 변경할 수 없습니다.

다음 사이트 설정을 만들어 포털에서 사용할 기본 날짜/시간 형식을 재정의할 수도 있습니다.
- DateTime/DateFormat: 포털에서 사용 되는 날짜 형식입니다. 
- DateTime/TimeFormat: 포털에서 사용 되는 시간 형식입니다. 
- DateTime/DateTimeFormat: 포털에서 사용 되는 전체 날짜 및 시간 형식입니다.

기본적으로 포털에는 웹 사이트 언어 설정에 지정 된 표준 날짜/시간 형식이 사용 됩니다.
허용 되는 날짜/시간 형식이 [여기](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)에 지정 됩니다.
