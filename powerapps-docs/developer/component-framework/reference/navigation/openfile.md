---
title: System.windows.forms.openfiledialog.openfile | Microsoft Docs
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
ms.openlocfilehash: 5de6eefb37450fde50127829f2a922252d08a4fb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342694"
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openFile(file, options)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|파일과|`FileObject`|예|열려는 파일을 설명 하는 개체입니다. FileObject에는 다음과 같은 특성이 있습니다. <br/>- **fileContent**: `String`. 파일의 내용입니다. <br/>- **파일 이름**: `String`. 파일의 이름입니다.<br/>- **fileSize**: `Number`. 파일 크기 (KB)입니다. <br/>- **mimeType**: `String`. 파일 MIME 형식입니다.|
|옵션|`Object`|아니요|파일을 열지 아니면 저장할지를 설명 하는 개체입니다. 개체에는 다음과 같은 특성이 있습니다. <br/>- **openMode**: 열을 1로 지정 합니다. 2-저장 합니다. 
이 매개 변수를 지정 하지 않으면 기본적으로 1 (open)이 전달 됩니다. 이 매개 변수는 통합 인터페이스 에서만 지원 됩니다.|

## <a name="return-value"></a>반환 값

형식: `Promise`

## <a name="remarks"></a>설명

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 및 [FileObject](../fileobject.md) 참조


### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)