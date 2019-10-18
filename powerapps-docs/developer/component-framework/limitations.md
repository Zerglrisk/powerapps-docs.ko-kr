---
title: PowerApps 구성 요소 프레임 워크의 제한 사항 | MicrosoftDocs
description: PowerApps 구성 요소 프레임 워크를 사용 하는 제한 사항
author: nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
ms.openlocfilehash: aabcf4518e71648797c795a006c2d842f3e5ff01
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346742"
---
# <a name="limitations"></a>제한 사항 

PowerApps 구성 요소 프레임 워크의 릴리스를 통해 사용자 고유의 코드 구성 요소를 만들어 모델 기반 앱 및 캔버스 앱에서 사용자 환경을 향상 시킬 수 있습니다. 사용자 고유의 구성 요소를 만들 수 있지만 코드 구성 요소에서 일부 기능을 구현 하는 개발자를 제한 하는 몇 가지 제한 사항이 있습니다. 몇 가지 제한 사항은 다음과 같습니다.

1. 구성 요소의 *필드* 형식만 *데이터 집합* 형식 구성 요소가 아닌 canvas 용 실험적 미리 보기 앱에서 지원 됩니다. 
2. 다른 몇 가지 Api와 함께 WebAPI를 비롯 한 Common Data Service 종속 Api는이 실험적 미리 보기에서 사용할 수 없습니다. 이 실험적 preview 릴리스에 대 한 개별 API 가용성은 [PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)를 참조 하세요.
3. 코드 구성 요소는 외부 라이브러리 콘텐츠를 비롯 한 모든 코드를 기본 코드 번들로 묶어야 합니다. PowerApps 명령줄 인터페이스를 사용 하 여 외부 라이브러리 콘텐츠를 구성 요소별 번들로 묶는 방법에 대 한 예를 보려면 [각도 대칭 이동 구성 요소](sample-controls/angular-flip-control.md) 예를 참조 하세요.

   > [!NOTE]
   > 구성 요소 매니페스트에서 라이브러리 노드를 사용 하는 구성 요소에서 공유 라이브러리에 대 한 지원은 아직 지원 되지 않습니다. Microsoft는이를 검토 하 고 있으며 향후 릴리스에서이 기능을 추가 합니다.
4. 단일 매니페스트 파일에 여러 구성 요소를 정의 하는 것은 아직 지원 되지 않습니다.
5. 프로세스 및 작업 호출은 아직 지원 되지 않습니다. [탐색](reference/navigation.md) 메서드를 사용 하 여 대화 상자를 호출할 수 있습니다.
6. 다른 코드 구성 요소에서 구성 요소 하나를 호출 하는 것은 아직 지원 되지 않습니다.
7. 현재 글꼴 리소스 (.tff)는 아직 지원 되지 않습니다.

## <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
