---
title: 기능 사용 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: 21e76a2a17910fe36967364f063ff2fc9b25e153
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "72339635"
---
# <a name="feature-usage-element"></a>기능 사용 요소

기능 사용 요소는 개발자가 구성 요소에서 사용 하려는 기능을 선언할 수 있도록 하는 `uses-feature` 요소 주위에 래퍼 역할을 합니다. 정의 된 사용 기능 요소가 없는 경우 기능 사용 요소가 필요 하지 않습니다.

## <a name="available-for"></a>사용 가능한

모델 기반 앱

## <a name="child-elements"></a>자식 요소

|요소|설명|사용 가능한|
|--|--|-----|
|[사용-기능](uses-feature.md)|구성 요소에서 사용 하려는 기능을 나타냅니다.|모델 기반 앱|


## <a name="example"></a>예

```XML
<feature-usage>
    <uses-feature name="Device.captureAudio" required="true" />
    <uses-feature name="Device.captureImage" required="true" />
    <uses-feature name="Device.captureVideo" required="true" />
    <uses-feature name="Device.getBarcodeValue" required="true" />
    <uses-feature name="Device.getCurrentPosition" required="true" />
    <uses-feature name="Device.pickFile" required="true" />
    <uses-feature name="Utility" required="true" />
    <uses-feature name="WebAPI" required="true" />
 </feature-usage>
```
