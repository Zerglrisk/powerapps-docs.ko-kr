---
ms.openlocfilehash: 13a55df026f9114506492f62b236ee8e3f1889cc
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "63319250"
---
Microsoft Social Engagement는 테넌트로 구분된 데이터베이스(고객 데이터)에 고객 검색 구성과 데이터 큐레이션을 저장합니다. 그러면 오로지 솔루션 성능 극대화를 목적으로 일반적인 검색 인덱싱이 가능하도록 내부 애플리케이션의 서버 측에 고객 데이터가 캐시됩니다.   
 캐시된 데이터(고객 데이터)를 인덱싱할 수 있는 액세스 권한은 내부 애플리케이션이 단독으로 처리하며, 사용자가 내부 데이터에서 인덱스 캐시 데이터를 대화식으로 액세스하거나 수정할 수는 없습니다. 구독 라이선스 계약이 종료되면 데이터 보존 정책에 따라 180일 후 고객 인덱스 캐시 데이터가 제거됩니다.