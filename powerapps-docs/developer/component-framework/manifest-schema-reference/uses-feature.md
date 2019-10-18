---
title: 사용-기능 | Microsoft Docs
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
ms.openlocfilehash: fe4d384c8dd53fc0f9efcf5558252984a4be74a3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345891"
---
# <a name="uses-feature-element"></a>사용-기능 요소

구성 요소에서 사용 하려는 기능을 나타냅니다.

## <a name="available-for"></a>사용 가능한

모델 기반 앱

## <a name="parent-element"></a>부모 요소

|요소|설명|
|--|--|
|기능 사용|기능 사용 요소는 개발자가 구성 요소에서 사용 하려는 기능을 선언할 수 있도록 하는 사용 기능 요소 주변의 래퍼로 사용 됩니다. 정의 된 사용 기능 요소가 없는 경우 기능 사용 요소가 필요 하지 않습니다.|

## <a name="child-elements"></a>자식 요소

|요소|설명|유형|필수|
|--|--|---|----|
|이름의|구성 요소에 선언 된 기능의 이름|`string`|예|
|필수|구성 요소에 해당 기능이 필요한 지 여부를 나타냅니다.|`boolean`|예|

### <a name="example"></a>예 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

다음 표에서는 매니페스트에 정의 된 사용 기능 설정에 따라 기능 함수를 호출할 수 있는지 여부에 따라 런타임에 코드에서 발생 하는 작업과 이러한 설정 간의 관계를 보여 줍니다.

|Manifest.xml|호스트가를 지 원하는 경우|호스트가 지원 하지 않는 경우|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null` 확인할 필요가 없습니다.|디자인 타임에 경고가 발생 했습니다. 런타임에 구성 요소 로드에 실패 합니다.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null` 구성 요소는 런타임에이를 확인할 수 있습니다. |
|없음을|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)