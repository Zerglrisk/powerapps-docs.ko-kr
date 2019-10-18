---
title: PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조 | Microsoft Docs
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
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 8f58f10f6a3695615ddc3b58b540c59240af9641
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346374"
---
# <a name="manifest-schema-reference"></a>매니페스트 스키마 참조

이 섹션에는 PowerApps CLI를 사용하여 생성된 매니페스트 스키마에 대한 참조 설명서가 포함되어 있습니다.

> [!IMPORTANT]
> **사용 가능한 대상** 탭에는 모델 기반 앱 및 캔버스 앱에서 지원 되는 요소 (실험적 미리 보기)가 표시 됩니다. 지원 여부에 관계 없이 각 개별 속성에 대해 **사용 가능한** 섹션을 확인 하는 것이 좋습니다. 예를 들어 **코드** 요소는 모델 기반 앱과 캔버스 앱 모두에 대해 지원 되지만 **코드** 요소의 **html** 및 **img** 속성은 canvas 앱을 지원 하지 않습니다. 

|요소|설명|사용 가능한|
|----|-----------|-----|
|[코드](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[컨트롤](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[데이터 세트](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|모델 기반 앱|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|모델 기반 앱|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|모델 기반 앱|
|[매니페스트](manifest.md)|매니페스트는 구성 요소를 정의하는 메타데이터 파일입니다. 이것은 XML 문서로서 구성 요소를 설명합니다.<br/> - 구성 요소의 네임스페이스입니다.<br/> - 필드 또는 데이터 세트 중 하나로 구성할 수 있는 데이터 종류.<br/> - 구성 요소를 추가할 때 애플리케이션에서 구성할 수 있는 모든 속성.<br/> - 구성 요소에 필요한 리소스 파일 목록.<br/> - 그 중 하나는 JavaScript 웹 리소스여야 합니다. 이 JavaScript는 개체를 인스턴스화하는 함수를 포함해야 합니다. 이는 구성 요소가 작동하는 데 필요한 메서드를 노출하는 인터페이스를 구현합니다. 이를 구성 요소 구현 라이브러리라고 합니다.<br/> - 필수 인터페이스를 적용하는 개체를 반환하는 구성 요소 구현 라이브러리의 JavaScript 함수 이름입니다.<br/> 누군가가 애플리케이션에서 구성 요소를 구성하면 매니페스트의 데이터는 해당 컨텍스트에 유효한 구성 요소만 구성할 수 있도록 사용 가능한 구성 요소를 필터링합니다. 구성 요소에 대해 매니페스트에 정의된 속성은 컨트롤을 구성하는 사용자가 값을 지정할 수 있도록 구성 필드로 렌더링됩니다. 그런 다음, 이러한 속성 값은 런타임 시 구성 요소 함수에서 사용할 수 있습니다.|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[속성](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[속성 집합](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|모델 기반 앱|
|[리소스](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[그룹 유형](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|모델 기반 앱 및 캔버스 앱 (실험적 미리 보기)|
|[기능 사용](feature-usage.md)|기능 사용 요소는 개발자가 구성 요소에서 사용 하려는 기능을 선언할 수 있도록 하는 `uses-feature` 요소 주위에 래퍼 역할을 합니다. 정의 된 사용 기능 요소가 없는 경우 기능 사용 요소가 필요 하지 않습니다.|모델 기반 앱|

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](index.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)