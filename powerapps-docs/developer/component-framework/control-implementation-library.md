---
title: 구성 요소 구현 라이브러리 | Microsoft Docs
description: JavaScript 또는 TypeScript를 사용 하 여 코드 구성 요소 만들기
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 31b7d2b30a1ef83ca4400011d50854713cb260f6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347248"
---
# <a name="component-implementation-library"></a>구성 요소 구현 라이브러리

구성 요소 라이브러리 구현은 PowerApps 구성 요소 프레임 워크를 사용 하 여 코드 구성 요소를 개발할 때 주요 단계 중 하나입니다. 개발자는 TypeScript를 사용 하 여 구성 요소 라이브러리를 구현할 수 있습니다. 각 코드 구성 요소에는 코드 구성 요소 인터페이스에 설명 된 메서드를 구현 하는 개체를 반환 하는 함수 정의가 포함 된 라이브러리가 있어야 합니다. 

개체는 다음 메서드를 구현 합니다.

- [init](reference/control/init.md) (필수)
- [Updateview](reference/control/updateview.md) (필수)
- [Getoutputs](reference/control/getoutputs.md) (선택 사항)
- [제거](reference/control/destroy.md) (필수)

이러한 메서드는 코드 구성 요소의 수명 주기를 제어 합니다.

