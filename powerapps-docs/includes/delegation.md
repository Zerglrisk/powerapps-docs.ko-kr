---
ms.openlocfilehash: 7b0f9ce710887c870d22a6362f9cd28245d72519
ms.sourcegitcommit: d87b2068a63e416e2814791328a3a47bbcb5bb48
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "62091150"
---
## <a name="delegation"></a>위임
가능한 경우 PowerApps는 필요에 따라 결과를 통해 필터 및 정렬 작업을 데이터 원본과 페이지에 위임합니다. 예를 들어 데이터가 채워진 **[갤러리](../maker/canvas-apps/controls/control-gallery.md)** 컨트롤을 표시하는 앱을 시작할 때 처음에는 레코드의 처음 집합만 디바이스로 가져옵니다. 사용자가 스크롤하면 다른 데이터를 데이터 원본에서 가져옵니다. 이 덕분에 앱의 시작 시간이 단축되고 앱이 매우 큰 데이터 집합에 액세스할 수 있습니다.

그러나 위임이 늘 가능한 것은 아닙니다. 데이터 원본은 위임을 통해 지원되는 함수 및 연산자에 따라 달라집니다. 전체 수식 위임이 불가능한 경우 제작 환경에서 이 부분에 위임 불가라는 플래그를 추가하고 경고를 표시합니다. 가능하다면 수식을 변경하여 위임 불가능한 함수 및 연산자를 방지하는 것이 좋습니다.  [위임 목록](../maker/canvas-apps/delegation-list.md)은 위임 가능한 데이터 원본과 연산을 상세히 설명합니다.

위임이 불가능한 경우 PowerApps는 로컬에서 작동하도록 소규모 레코드 집합만 끌어옵니다. 필터 및 정렬 함수는 축소된 레코드 집합에서 작동합니다. **[갤러리](../maker/canvas-apps/controls/control-gallery.md)** 에서 사용할 수 있는 항목은 전체 목록이 아닐 수 있고 사용자에게 혼란을 초래할 수 있습니다. 

자세한 내용은 [위임 개요](../maker/canvas-apps/delegation-overview.md)를 참조하세요.

