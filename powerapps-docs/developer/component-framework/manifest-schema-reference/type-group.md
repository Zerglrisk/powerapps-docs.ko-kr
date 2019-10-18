---
title: Type Group 요소 | Microsoft Docs
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
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
ms.openlocfilehash: 7b09fad6097bb837c19116d59bb90afbde4d46b2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345983"
---
# <a name="type-group-element"></a>type-group 요소

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="available-for"></a>사용 가능한

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="attributes"></a>특성

|이름|설명|유형|필수|
|--|--|--|--|
|`name`|데이터 형식의 이름입니다.|`string`|예|

## <a name="parent-elements"></a>부모 요소

|요소|설명|
|--|--|
|[컨트롤](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>자식 요소

|요소|설명|항목과|
|--|--|--|
|[입력할](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1 개 이상|


유형-그룹은이 실험적 미리 보기에서 캔버스 앱에 대해 제한 된 지원을 제공 합니다. 구성 요소를 가져오려고 하면 다음과 같은 문제가 발생 합니다.

1. 형식 그룹에 나열 된 모든 형식이 호환 되는 javascript 형식인 경우 개발자는 나열 된 가장 일반적인 옵션을 선택 하려고 시도 합니다. 호환 되는 것으로 간주 되는 형식은 다음과 같습니다.
   - 문자열: Regexoptions.singleline, Multiple, Regexoptions.singleline, Regexoptions.singleline, Regexoptions.singleline, Regexoptions.singleline, Regexoptions.singleline입니다.
   - 숫자: 10 진수, 부동 소수점, 전체. 없음, 통화.
   - 날짜: dateandtime. DateAndTime, DateAndTime. DateOnly.

2. 그룹에 나열 된 형식이 호환 되지 않는 것으로 간주 되는 경우 매개 변수는 형식 그룹에 나열 된 첫 번째 형식으로 처리 됩니다.

### <a name="example"></a>예

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)