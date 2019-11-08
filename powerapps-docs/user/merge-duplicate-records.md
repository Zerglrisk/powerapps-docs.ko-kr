---
title: 중복 레코드 병합 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c0811645429c9f1e7570ceeaf316a5217e440ae4
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73609880"
---
# <a name="merge-duplicate-records"></a>중복 레코드 병합 

중복 레코드는 사용자 또는 다른 사용자가 데이터를 수동으로 입력 하거나 데이터를 대량으로 가져올 때 데이터를 증가 시킬 수 있습니다. Common Data Service는, 계정 및 연락처와 같은 활성 레코드에 대해 중복 검색 기능을 제공 하 여 잠재적 중복을 해결 하는 데 도움이 됩니다. 레코드를 병합 하는 경우 관련 된 레코드나 자식 레코드도 병합 됩니다. 관리자는 다른 상황에 대 한 중복 검색 규칙도 설정할 수도 있습니다.  
  
예를 들어 연락처 레코드를 휴대 전화 번호와 함께 연락처 레코드를 입력 하는 경우를 가정해 보겠습니다.  중복 검색 규칙은 이미 유사한 레코드가 있음을 검색 하 고이 대화 상자를 표시 합니다.  
  
 > [!div class="mx-imgBorder"] 
 > ![중복 된 연락처 레코드 detectied](media/duplicates-detected.png "중복 된 연락처 레코드 detectied")  
  
 새 레코드 (기존 연락처와 동일한 이름을 가진 레코드) 인지 확실 하지 않으므로 **무시 하 고 저장**을 선택 합니다.  
  
 이제 **모든 연락처** 목록으로 이동 하 여 이름이 같은 두 개의 레코드가 있음을 확인 합니다. 레코드를 검토 한 후 병합 해야 하는 중복 항목이 있는지 확인 합니다.  
 
 > [!div class="mx-imgBorder"] 
 > ![중복 된 연락처 레코드 detectied](media/duplicates-detected_1.png "중복 된 연락처 레코드 detectied")  
 
Common Data Service에는 계정 및 연락처에 대 한 중복 검색 규칙이 포함 되어 있습니다. 이러한 규칙은 자동으로 설정 되므로 이러한 레코드 유형에 대 한 중복 검색을 설정 하기 위해 아무것도 수행할 필요가 없습니다.  
  
> [!NOTE]
>  사용자의 시스템에서 사용할 수 있는 경우 연락처와 계정 외에 다른 레코드 유형의 중복도 확인할 수 있습니다. 시스템 관리자에 게 문의 하십시오. [관리자 또는 지원 담당자 찾기](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>중복 레코드 병합  
  
1. 중복 레코드를 선택한 다음 **병합**을 선택 합니다.  
  
   > [!div class="mx-imgBorder"] 
   > ![중복 된 연락처 레코드 detectied](media/duplicates-detected_2.png "중복 된 연락처 레코드 detectied")  
  
2. **레코드 병합** 대화 상자에서 마스터 레코드 (유지할 항목)를 선택한 다음 마스터 레코드에 병합 하려는 새 레코드의 필드를 선택 합니다. 이러한 필드의 데이터는 마스터 레코드의 기존 데이터를 재정의할 수 있습니다. **확인**을 선택합니다.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![레코드 병합을 위한 대화 상자](media/merge-records-dialog.png "레코드 병합을 위한 대화 상자")  
  
> [!NOTE]
>  중복 항목을 찾을 수 있는 경우는 다음과 같습니다.  
> 
> - 레코드가 만들어지거나 업데이트 되는 경우  
>   - Outlook에 Dynamics 365을 사용 하는 경우 오프 라인에서 온라인으로 전환 합니다.  
>   - 데이터를 가져올 때 데이터 가져오기 마법사를 사용 합니다.  
> 
>   레코드를 병합 하거나, 완료 된 대로 작업을 저장 하거나, 레코드 활성화 또는 다시 활성화와 같은 레코드의 상태를 변경 하는 경우 중복 항목이 검색 되지 않습니다.  
