---
title: Common Data Service의 날짜 및 시간 필드의 동작 및 형식 | MicrosoftDocs
description: 포털에서 사용되는 날짜 및 시간 필드의 동작 및 형식.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760704"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>날짜 및 시간 필드의 동작 및 형식

Common Data Service에서는 많은 시스템 엔터티 필드에 날짜 및 시간 데이터 형식이 사용됩니다. 예를 들어, 마케팅 캠페인에서 계정이 마지막으로 사용된 때 또는 서비스 케이스가 에스컬레이션된 날짜와 시간을 보여줄 수 있습니다. 날짜 및 시간 필드를 포함하는 사용자 지정 엔터티를 만들 수도 있습니다. 필드가 무엇을 나타내느냐에 따라 포털 형식과 그리드를 위해 다음 필드 특성 중 하나를 선택할 수 있습니다. 
- **사용자 로컬**: 필드 값이 사용자의 현지 시간에 표시되는 데 현재의 포털 언어/로케일에 따라 포맷됩니다. 값은 Common Data Service에 UTC 시간대 형식으로 저장됩니다. 다른 시간대의 Common Data Service 사용자(또는 다른 포털 사용자)가 해당 값을 볼 때에는 자신의 시간대로 변환된 값으로 나타납니다.
- **날짜만**: 필드 값에 날짜만 포함되고 시간대 변환 없이 표시됩니다. 값의 시간 부분은 항상 12:00AM입니다. 한 사용자가 입력한 값이 다른 시간대의 다른 사용자에게 동일하게 표시됩니다(예: 생일).
  
  > [!Note]
  > 이 필드의 특성은 저장된 후에는 변경할 수 없습니다.
  
- **표준 시간대 독립**: 필드 값에 날짜와 시간이 포함되고 시간대 변환 없이 표시됩니다. 한 사용자가 입력한 값이 다른 시간대의 다른 사용자에게 동일하게 표시됩니다.
  
  > [!Note]
  > 이 필드의 특성은 저장된 후에는 변경할 수 없습니다.

다음 사이트 설정값을 만들어 포털에서 사용될 기본 날짜/시간 형식을 재정의할 수도 있습니다.
- 날짜 시간/날짜 형식: 포털에서 사용되는 날짜 형식. 
- 날짜 시간/시간 형식: 포털에서 사용되는 시간 형식. 
- 날짜 시간/날짜 시간 형식: 포털에서 사용되는 전체 날짜 및 시간의 형식.

기본적으로 포털은 웹사이트 언어 설정에 의해 지정된 표준 날짜/시간 형식을 사용합니다.
허용되는 날짜/시간 형식이 [여기에](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings) 지정되어 있습니다.
