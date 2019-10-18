---
title: Code 요소 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 44d9fcfb-0cd8-48cc-aace-dd589099dd79
ms.openlocfilehash: 2caf89a73dba006240c5bb6e8c874dfdd795d8c2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346650"
---
# <a name="code-element"></a>code 요소

[!INCLUDE [code-description](includes/code-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|사용 가능한|
|--|--|--|--|-----|
|`path`|리소스 파일이 있는 위치|`String`|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|
|`order`|리소스 파일을 로드 하는 순서입니다.|`Positive integer`|예|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) (실험적 미리 보기)|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

### <a name="example"></a>예

```XML
<code path="TS_IncrementControl.js" order="1" />
        <css path="css/TS_IncrementControl.css" order="1" />
      <resx path="strings/TSIncrementControl.1033.resx" version="1.0.0" />
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)