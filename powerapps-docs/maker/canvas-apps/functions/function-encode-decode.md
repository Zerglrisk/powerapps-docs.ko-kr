---
title: EncodeUrl 및 PlainText 함수 | Microsoft Docs
description: PowerApps의 EncodeUrl 및 PlainText 함수에 대한 구문과 예제를 포함한 참조 정보
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
ms.openlocfilehash: c21cae9e39e3a9a1461ac3fafe576f40b70c0818
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985009"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>PowerApps의 EncodeUrl 및 PlainText 함수
문자열을 인코딩하고 디코딩합니다.

## <a name="description"></a>설명
**EncodeUrl** 함수는 URL 문자열을 인코딩하고 영숫자가 아닌 특정 문자를% 및 16 진수로 바꿉니다.  

**PlainText** 함수는 HTML 및 XML 태그를 제거 하 여 다음과 같은 특정 태그를 적절 한 기호로 변환 합니다.

* **&amp;nbsp;**
* **&amp;quot;**

이러한 함수의 반환 값은 인코딩되거나 디코딩된 문자열입니다. 이 함수는 모든 HTML 및 XML 태그를 제거 하지 않습니다. 

## <a name="syntax"></a>구문
**EncodeUrl**( *String* )

* *String* - 필수 항목입니다.  인코딩할 URL입니다.

**PlainText**( *String* )

* *String* - 필수 항목이며, HTML 및 XML 태그를 제거할 문자열입니다.

## <a name="examples"></a>예
텍스트 갤러리에 RSS 피드를 표시한 다음, 해당 갤러리의 레이블에 있는 **[Text](../controls/properties-core.md)** 속성을 **ThisItem.description**으로 설정하면 레이블에 다음 예제와 같이 원시 HTML 또는 XML 코드가 표시됩니다.

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

레이블의 **[Text](../controls/properties-core.md)** 속성을 **PlainText(ThisItem.description)** 로 설정하면 텍스트가 다음 예제와 같이 나타납니다.

```
    We have done an unusually "deep" globalization and localization.
```