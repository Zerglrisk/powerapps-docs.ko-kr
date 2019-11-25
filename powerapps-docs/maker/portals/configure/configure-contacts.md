---
title: 포털에서 사용하기 위한 연락처 구성 | MicrosoftDocs
description: 포털에서 사용할 연락처를 추가 및 구성하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760726"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>포털에서 사용하기 위한 연락처 구성

연락처에 대한 기본 정보를 작성한 후(또는 사용자로 하여금 포털에서 가입 양식을 작성하게 한 후) 포털 연락처 양식의 웹 인증 탭으로 이동하여 로컬 인증을 사용하여 연락처를 구성합니다. 페더레이션 인증 옵션에 대한 자세한 내용은 [포털의 인증 ID 설정](set-authentication-identity.md)을 참조하십시오. 로컬 인증을 사용하여 포털에 대한 연락처를 구성하려면 다음 지침을 따르십시오.  

1.  **사용자 이름**을 입력하십시오.
2.  명령 리본에서 **추가 명령** &gt; **암호 변경**으로 이동합니다.

암호 변경 워크플로가 완료되어 필요한 필드가 자동으로 구성됩니다. 이 작업을 완료하면 포털에 대한 연락처가 구성됩니다.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>포털 관리 앱에서 연락처의 암호 변경

1.  [포털 관리 앱](configure-portal.md)을 엽니다.

2.  **포털** > **연락처**로 이동하고 암호를 변경할 연락처를 엽니다.
    또는 [공유](../manage-existing-portals.md#share) 창에서 **연락처** 페이지를 열 수도 있습니다. 

3.  상단의 도구 모음에서 **작업 흐름**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![작업 흐름 아이콘](../media/task-flow.png "작업 흐름 아이콘")

4.  **포털 연락처의 암호 변경** 작업 흐름을 선택합니다.

5.  **포털 연락처의 암호 변경** 창에서 연락처를 선택하거나 만들어 암호를 변경한 후에 **다음**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![연락처를 선택하여 암호 변경](../media/change-password-select-contact.png "연락처를 선택하여 암호 변경")

6.  **새 암호** 필드에 새 암호를 입력한 후에 **다음**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![연락처의 새 암호 지정](../media/change-password-new-password.png "연락처의 새 암호 지정")

    암호를 입력하지 않고 **다음**을 선택하는 경우 선택한 연락처에 대한 암호를 제거할지 묻는 메시지가 표시됩니다.

    > [!div class="mx-imgBorder"]
    > ![연락처의 암호 제거](../media/change-password-remove-password.png "연락처의 암호 제거")

7.  변경한 후 **완료**를 선택합니다.


### <a name="see-also"></a>참조
[연락처에 포털 초대 보내기](invite-contacts.md)  
[포털의 인증 ID 설정](set-authentication-identity.md)  