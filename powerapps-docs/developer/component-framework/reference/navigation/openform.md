---
title: openForm | Microsoft Docs
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
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
ms.openlocfilehash: d0754030de4880f0ad693105e96b47d785f1561b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342372"
---
# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="syntax"></a>구문

`context.navigation.openForm(options, parameters)`

## <a name="parameters"></a>변수의

| 매개 변수 이름|유형|필수|설명|
| ------------- |----|--------|-----------|
|옵션|`EntityFormOptions`|예|폼을 열기 위한 엔터티 양식 옵션입니다. EntityFormOptions에는 다음과 같은 특성이 있습니다.<br/>- **Createfromentity**: `Lookup` 합니다. 매핑된 특성 값에 따라 기본값을 제공 하는 레코드를 지정 합니다. Lookup 개체의 문자열 속성은 `entityType`, `id` 및 `name`입니다. <br/>- **entityId**: `String`. 폼을 표시할 엔터티 레코드의 ID입니다.<br/>- **entityName**: `String` 합니다. 폼을 표시할 엔터티의 논리적 이름입니다.<br/>- **Formid**: `String`. 표시할 폼 인스턴스의 ID입니다.<br/>- **height**: `Number` 합니다. 픽셀 단위로 표시할 폼 창의 높이입니다.<br/>- **Openinnewwindow**: `boolean` 합니다. 새 창에 폼을 표시할지 여부를 지정 합니다.<br/>- **useQuickCreateForm**: `Boolean`. 빠른 생성 양식을 열지 여부를 지정 합니다. 이를 지정 하지 않으면 기본적으로 `false`이 전달 됩니다.<br/>- **width**: `Number` 합니다. 픽셀 단위로 표시할 폼 창의 너비입니다.<br/>- **Windowposition**: `Number`. 화면에서 폼의 창 위치에 대해 다음 값 중 하나를 지정 합니다. `1:center` <br/> `2:side`|
|변수의|`Object`|아니요|폼에 추가 매개 변수를 전달 하는 사전 개체입니다. 매개 변수가 잘못 되 면 오류가 발생 합니다. 자세한 내용은 [폼에 전달 된 매개 변수를 사용 하 여 필드 값을 참조](https://docs.microsoft.com/en-us/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form) 하 고 [사용자 지정 쿼리 문자열 매개 변수를 허용 하도록 양식을 구성 합니다](https://docs.microsoft.com/en-us/powerapps/developer/component-framework/sample-controls/navigation-api-control) .|

## <a name="return-value"></a>반환 값

형식: `Promise<OpenFormSuccessResponse>`

## <a name="remarks"></a>설명

[약속](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 참조

### <a name="related-topics"></a>관련 항목

[탐색](../navigation.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)