---
title: PickFile | Microsoft Docs
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
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
ms.openlocfilehash: a36731edc7ee5cc8edede499fc791595bc00bc8c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344626"
---
# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>구문

`context.device.pickFile(options)`

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|`options`|`Object`|아니요|파일을 선택 하는 옵션입니다.|

## <a name="return-value"></a>반환 값

형식: `Promise<FileObject[]>`

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 및 [FileObject](../fileobject.md) 참조

## <a name="remarks"></a>설명

@No__t_0 매개 변수 개체에는 다음과 같은 속성이 있습니다.

|이름|유형|설명|
|--|--|--|
|`accept`|`String`|선택할 이미지 파일 형식입니다. 유효한 값은 *오디오*, *비디오*또는 *이미지*입니다.|
|`allowMultipleFiles`|`Boolean`|여러 파일을 선택할 수 있는지 여부를 나타냅니다.|
|`maximumAllowedFileSize`|`Number`|선택할 최대 파일 크기입니다.|


### <a name="related-topics"></a>관련 항목

[장치](../device.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)