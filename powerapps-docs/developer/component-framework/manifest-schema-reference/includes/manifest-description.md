---
title: 매니페스트 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 31af2963-b4ca-4347-98f6-4a3f6277f43a
ms.openlocfilehash: 22750956cea12e1ed17bbc1ee8d4f015cf0ce2c1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338922"
---
매니페스트는 구성 요소를 정의하는 메타데이터 파일입니다. 다음을 설명 하는 `XML` 파일입니다.

- 구성 요소의 네임 스페이스입니다.
- 필드 또는 데이터 집합 중에서 구성할 수 있는 데이터의 종류입니다.
- 구성 요소가 추가 될 때 응용 프로그램에서 구성할 수 있는 모든 속성입니다.
- 구성 요소에 필요한 리소스 파일의 목록입니다. 
  - 그 중 하나는 JavaScript 웹 리소스 여야 합니다. 이 JavaScript는 개체를 인스턴스화하는 함수를 포함해야 합니다. 이는 구성 요소가 작동하는 데 필요한 메서드를 노출하는 인터페이스를 구현합니다. 이를 구성 요소 구현 라이브러리라고 합니다.
- 필수 구성 요소 인터페이스를 적용 하는 개체를 반환 하는 구성 요소 구현 라이브러리의 JavaScript 함수 이름입니다.

사용자가 캔버스 앱 또는 모델 기반 앱에서 사용자 지정 구성 요소를 구성 하는 경우 매니페스트의 데이터는 사용 가능한 구성 요소를 필터링 하 여 해당 컨텍스트에 대 한 유효한 구성 요소만 구성할 수 있도록 합니다. 구성 요소에 대 한 매니페스트에 정의 된 속성은 구성 요소를 구성 하 여 구성 요소를 구성 하는 사용자가 값을 지정할 수 있도록 구성 필드로 렌더링 됩니다. 이러한 속성 값은 런타임에 구성 요소 함수에서 사용할 수 있습니다.
