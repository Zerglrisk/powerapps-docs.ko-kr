---
title: 제거 | MicrosoftDocs
ms.topic: reference
applies_to: ''
ms.assetid: ba66b513-2a7b-4ba6-b2d5-446ea2b42fdb
author: nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.openlocfilehash: 195a6b56ee440cebfdc46c3aa3bb3fc2b5ce3101
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345454"
---
# <a name="destroy"></a>삭제

[!INCLUDE[./includes/destroy-description.md](./includes/destroy-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)

## <a name="syntax"></a>구문

`destroy()`

## <a name="example"></a>예

```javascript
MyControl.prototype.destroy = function () {
 this.button.removeEventListener("click", this.onButtonClick);
};
```

### <a name="related-topics"></a>관련 항목

[컨트롤](../control.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../../overview.md)