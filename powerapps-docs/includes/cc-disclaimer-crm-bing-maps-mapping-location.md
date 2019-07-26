---
ms.openlocfilehash: f1c11fd086a91db6dc0d0629549166bbba547dee
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67226499"
---
## <a name="mapping-functions-for-dynamics-365-customer-engagement-plan"></a>Dynamics 365 Customer Engagement 플랜의 함수 매핑 
 Field Service 및 Project Service Automation에는 위치에 의존하는 주요 함수가 있습니다. 예를 들어 서비스 또는 작업이 수행되는 위치를 정의하는 서비스 계정의 위치 또는 리소스(서비스 또는 작업을 수행하는 사람)의 시작/종료 위치가 있습니다.  시스템이 지도에 이를 표시하거나 두 지점 사이의 거리를 계산하려면 매핑 서비스(이 경우 Bing Maps)를 사용해야 합니다.  
  
 다음은 Bing Maps 서비스의 입/출력 워크플로입니다.  
  
|Dynamics 365 입력|Bing Maps 반환값|참고|  
|-----------------------|-----------------------|----------|  
|주소(계정 또는 리소스)|주소(위치)의 위도 및 경도입니다.|이를 주소 "지오 코딩"이라고 합니다.|  
|위치 집합(위도/경도)|위치 사이의 거리|이는 리소스의 최적 경로를 찾거나 이동 시간을 계산하는 데 사용할 수 있습니다.|  
|위치 집합(위도/경도)|위치가 지도에 핀으로 표시된 지도 보기|이는 지도 보기에서 계정 및 리소스를 볼 때 사용됩니다.|  
  
> [!NOTE]
>  위에서 언급된 데이터 외에 다른 데이터는 Bing Maps 서비스로 전송되지 않습니다.
