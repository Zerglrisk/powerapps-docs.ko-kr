---
title: 서로 간에 레코드를 연결 하는 연결 역할 추가 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 8/01/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4552c874ca6be72d37465abd2492a64979aba865
ms.sourcegitcommit: 5ec4cab1dd934446ec57c320a375e577560ac88a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72239569"
---
# <a name="add-a-connection-role-to-link-records-to-each-other"></a>연결 역할을 추가 하 여 레코드를 서로 연결

연결을 사용 하면 사용자, 연락처, 견적, 판매 주문 및 기타 여러 엔터티 레코드를 서로 쉽게 연결할 수 있습니다. 연결의 레코드에는 관계의 용도를 정의 하는 데 도움이 되는 특정 역할이 할당 될 수 있습니다.

특정 레코드에 대 한 여러 연결 및 역할을 만드는 빠른 방법입니다. 예를 들어 연락처에는 다른 연락처, 계정 또는 계약과의 많은 관계가 있을 수 있습니다. 각 관계에서 연락처는 다른 역할을 실행할 수 있습니다.

연결 역할은 연결에 직접 연결 됩니다. 연결 역할을 사용 하려면 먼저 레코드에 대 한 연결을 추가 해야 합니다.

연결 역할을 추가 하려면 먼저 관리자가 사용 하도록 설정 해야 합니다. 자세한 내용은 [연결 역할 구성](https://docs.microsoft.com/powerapps/maker/common-data-service/configure-connection-roles)을 참조 하세요.

1. 연결을 추가 하거나 관리 하려면 기회와 같이 관리 하려는 레코드를 선택 합니다.  
2. **관련** 탭을 선택한 다음 **연결**을 선택 합니다. 그러면 레코드에 대 한 연결 목록이 포함 된 연결 표가 열립니다.

    > [!div class="mx-imgBorder"]
    > 새 연결 ![역할 추가](media/connection1.png "새 연결 역할 추가") 

3. **연결** 을 선택한 다음 **다른** 또는 나 **를**선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![연결 유형]선택(media/connection2.png "연결 유형 선택") 
  
4. **이름** 필드에 연결에 대 한 레코드의 이름을 입력 하거나 찾습니다.

5. **이 역할의 역할** 필드에서 조회 아이콘을 선택한 다음 **새 연결 역할**을 선택 합니다. 또는 검색을 사용 하 여 연결에 연결 하려는 기존 역할을 찾은 다음, **저장**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![새 연결 역할 선택](media/connection3.png "새 연결 역할을 선택") 합니다.  

    > [!NOTE]
    > 새 연결 역할을 만들기 전에 정보를 입력 한 경우 취소 하 고 연결에 대 한 작업을 계속 하 고 진행 중인 현재 레코드를 그대로 둘 지 묻는 경고 대화 상자가 표시 됩니다.

6. 새 연결 역할을 만들려면 **새 연결 역할** 화면에서 이름을 입력 한 다음 **연결 역할 범주**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    >  ![연결 역할 범주]추가(media/connection4.png "연결 역할 범주") 추가 

7. 완료 되 면 **저장 & 닫기**를 선택 합니다.

  
## <a name="manage-connection-roles"></a>연결 역할 관리

연결 역할을 관리 하려면 연결 엔터티에서 연결 역할을 선택 합니다. 이렇게 하면 연결 역할 엔터티 레코드가 열립니다.  이름을 편집 하 고, 연결 역할 범주를 선택 하 고, 설명을 추가할 수 있습니다.


   > [!div class="mx-imgBorder"]
   > ![연결 역할 편집](media/connection7.png "연결 역할") 편집 
  
연결 역할에 연결할 연결 역할 유형을 관리할 수도 있습니다.

1. 연결 역할을 연 다음 명령에서 **레코드 유형 관리** 를 선택 합니다. 

    > [!div class="mx-imgBorder"]
    > ![연결 역할 편집](media/connection5.png "연결 역할") 편집 
  

2. 이렇게 하면이 연결 역할에 대해 추가 하거나 제거할 수 있는 연결 역할 유형 목록이 열립니다.

    > [!div class="mx-imgBorder"]
    > ![레코드 유형]관리(media/connection6.png "레코드 유형 관리") 


