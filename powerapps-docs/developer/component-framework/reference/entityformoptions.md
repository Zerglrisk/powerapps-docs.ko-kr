---
title: EntityFormOptions | Microsoft Docs
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 0ed2d2b13fa084fe1521e90304b7e3ead4ccac27
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025466"
---
# <a name="entityformoptions"></a>EntityFormOptions

엔터티 형식에 대 한 모든 정보에 대 한 액세스를 제공 합니다.

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="createfromentity"></a>createFromEntity

매핑된 특성 값에 따라 기본값을 제공 하는 레코드를 지정 합니다. 조회 개체의 속성은 엔터티 형식, id 및 이름입니다.

**형식**: [Entityreference](entityreference.md)

### <a name="entityid"></a>entityId

폼을 표시할 엔터티 레코드의 고유 Id입니다. 

**형식**: `string`

### <a name="entityname"></a>entityName

폼을 표시할 엔터티의 논리적 이름입니다. 

**형식**: `string`

### <a name="formid"></a>formId

표시할 폼 인스턴스의 ID입니다.

**형식**: `string`

### <a name="height"></a>height

픽셀 단위로 표시할 폼 창의 높이입니다.

**형식**: `number`

### <a name="openinnewwindow"></a>openInNewWindow

새 창에 폼을 표시할지 여부를 지정 합니다.

**형식**: `boolean`

### <a name="usequickcreateform"></a>useQuickCreateForm

빠른 생성 양식을 열지 여부를 지정 합니다. 이를 지정 하지 않으면 기본적으로 false가 전달 됩니다. 

**형식**: `boolean`

### <a name="width"></a>width

픽셀 단위로 표시할 폼 창의 너비입니다.

**형식**: `boolean`

### <a name="windowposition"></a>windowPosition

화면의 창 위치를 지정 합니다.

**형식**: `number`

WindowPosition 값은 다음과 같은 가능한 값을 가진 숫자입니다.

|Value|위치|
|---|---|
|1|중심과|
|2|Side-by-side|


## <a name="example"></a>예

```TypeScript
private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.simpleTableGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.entityType!,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)