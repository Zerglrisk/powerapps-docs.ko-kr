---
title: 연락처 또는 사용자에 대 한 프로필 카드 보기 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67441e506ba2715a9994f6b81cd08426e37e0fc8
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950913"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>연락처 또는 사용자에 대 한 프로필 카드 보기

프로필 카드를 사용 하 여 연락처 또는 사용자에 대 한 빠른 정보를 가져옵니다. Dynamics 365 Sales 및 Dynamics 365 Customer Service와 같이 Dynamics 365의 모델 기반 앱에서 연락처 또는 사용자 필드를 선택 하면 해당 프로필 카드에서 관련 정보를 찾을 수 있습니다. 프로필 카드에 대 한 자세한 내용은 [Office 365의 프로필 카드](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)를 참조 하세요.

> [!NOTE]
>  - **연락처** 및 **사용자** 엔터티에 대해 프로필 카드를 사용할 수 있습니다. 자세한 내용은 [프로필 카드 사용 (관리자 용)](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-profile-card)을 참조 하세요.
>  - Azure Active Directory에서 Office Delve 서비스에 대해 multi-factor authentication이 설정 된 경우 Common Data Service의 프로필 카드가 표시 되지 않습니다.

## <a name="view-a-contacts-profile"></a>연락처의 프로필 보기

1.  **작업**으로 이동합니다.
2.  기존 활동을 선택 하거나 새 활동을 만듭니다.
3.  연락처 레코드가 있을 때 필드 **호출을** 마우스로 가리킵니다. 

연락처 사진, 이름, 제목 및 계정이 포함 된 연락처에 대 한 자세한 정보를 볼 수 있습니다.

4. 자세한 내용을 보려면 자세히 **표시** 를 선택 하 여 연락처의 프로필을 확장 합니다.
 
    > [!div class="mx-imgBorder"] 
    > ![연락처 프로필 카드 세부]정보 확장(media/profile1.png "연락처 프로필 카드 세부 정보") 를 확장 합니다.
   
 ## <a name="view-a-users-profile"></a>사용자의 프로필 보기
 
1.  **계정**으로 이동 합니다.
2.  계정 레코드를 선택 합니다.
3.  사용자 레코드가 있는 경우 소유자 필드를 마우스로 가리킵니다. 사용자의 인라인에 대 한 세부 정보를 볼 수 있습니다.
4.  사용자와의 메일 및 공유 파일 같은 자세한 정보를 보려면 **자세히 표시** 를 선택 하 여 연락처의 프로필을 확장 합니다.
 
    > [!div class="mx-imgBorder"] 
    > ![사용자 프로필 카드 세부]정보 확장(media/profile2.png "사용자 프로필 카드 세부 정보")


 ## <a name="faqs"></a>질문과
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Dynamics 365에서 프로필 카드를 어디에서 볼 수 있나요?
프로필 카드는 연락처 및 사용자 레코드에서 볼 수 있습니다. 조회 하는 경우에만 볼 수 있습니다.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>프로필 카드에 표시 되는 정보는 어디에서 확인할 수 있나요?
연락처 프로필 카드에 표시 되는 정보는 Microsoft Exchange가 아닌 Common Data Service에서 인출 됩니다. 즉, 연락처 세부 정보는 Dynamics 365에서 제공 됩니다.

사용자 프로필 카드에 표시 되는 정보는 Office 365 (Azure Active Directory)에서 인출 됩니다. 자세한 내용은 [Office 365의 프로필 카드 (관리 섹션)](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)를 참조 하세요.

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>프로필 카드에 표시 되는 필드를 사용자 지정 하려면 어떻게 해야 하나요?
현재는 프로필 카드에 표시 되는 필드 목록이 사용자 지정을 위해 열려 있지 않습니다.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>프로필 카드에서 **채팅 시작** 옵션을 사용 하지 않도록 설정 (회색으로 표시) 하는 이유는 무엇 인가요?
프로필 카드의 **채팅 시작** 및 **전자 메일 보내기** 옵션은 기본 인스턴트 메시지와 전자 메일 앱을 엽니다. **채팅 시작** 옵션은 사용자가 사용자와 동일한 Azure Active Directory 환경에서 연결 하려는 사용자 또는 페더레이션된 연락처 인 경우에 사용할 수 있습니다.


  
