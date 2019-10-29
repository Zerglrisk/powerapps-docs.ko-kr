---
title: Common Data Service 환경에 포털 연결 | MicrosoftDocs
description: 포털을 Common Data Service 환경에 연결 하는 방법 및 인증 키를 갱신 하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31632f4de1834855c696baa1b4b651ed777c8abd
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977499"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>포털을 사용 하 여 Common Data Service 환경에 연결

포털은 Azure Active Directory 응용 프로그램을 사용 하 여 Common Data Service 환경에 연결 합니다. 응용 프로그램은 포털이 프로 비전 되는 동일한 테 넌 트에 생성 됩니다. 응용 프로그램은 포털 프로 비전 프로세스 중에 Common Data Service 환경에 등록 됩니다.

![Common Data Service 환경을 사용 하 여 포털 연결](../media/connect-with-dynamics.png "Common Data Service 환경에서 포털 연결")

각 포털에는 동일한 Common Data Service 환경에 연결 되어 있든 관계 없이 연결 된 별도의 Azure Active Directory 응용 프로그램이 있습니다. 포털에 대해 생성 된 기본 Azure Active Directory 인증 공급자는 동일한 Azure Active Directory 응용 프로그램을 사용 하 여 포털을 인증 합니다. 권한 부여는 포털에 액세스 하는 사용자에 게 할당 된 웹 역할에 의해 적용 됩니다.

Azure Active Directory에서 연결 된 포털 응용 프로그램을 볼 수 있습니다. 이 응용 프로그램의 이름은 Microsoft CRM 포털이 되며 포털 ID는 Azure Active Directory 응용 프로그램의 **앱 ID URI** 필드에 있습니다. 포털을 프로 비전 하는 사용자는이 응용 프로그램을 소유 합니다. 이 응용 프로그램을 삭제 하거나 수정 하면 안 됩니다. 그렇지 않으면 포털 기능이 손상 될 수 있습니다. PowerApps 포털 관리 센터에서 포털을 관리 하려면 응용 프로그램 소유자 여야 합니다.

## <a name="authentication-key"></a>인증 키

포털에서 Azure Active Directory 응용 프로그램을 사용 하 여 Common Data Service에 연결 하려면 Azure Active Directory 응용 프로그램에 연결 된 인증 키가 필요 합니다. 이 키는 포털을 프로 비전 할 때 생성 되며이 키의 공개 부분은 Azure Active Directory 응용 프로그램에 자동으로 업로드 됩니다.

> [!IMPORTANT]
> 인증 키는 2 년 후에 만료 됩니다. 포털에서 Common Data Service 환경에 계속 연결할 수 있도록 2 년 마다 갱신 해야 합니다. 키를 업데이트 하지 않으면 포털 작동이 중지 됩니다.  

### <a name="authentication-key-details"></a>인증 키 세부 정보

인증 키의 세부 정보는 PowerApps 포털 관리 센터 및 포털에 표시 됩니다.

**PowerApps 포털 관리 센터**

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 인증 키 관리**를 선택 합니다. 인증 키가 만료 날짜 및 지문과 함께 표시 됩니다.

   > [!div class=mx-imgBorder]
   > Powerapps ![포털 관리 센터의 인증 키 세부 정보](../media/manage-auth-key.png "powerapps 포털 관리 센터의 세부 정보")

**포탈**

1. 관리자 권한으로 포털에 로그인 합니다.

2. URL < portal_path >/_services/about.로 이동 합니다. 인증 키 만료 날짜가 표시 됩니다. 

   > [!div class=mx-imgBorder]
   > ![포털 서비스 페이지](../media/portal-services-page.png "포털 서비스 페이지")

> [!NOTE]
> 인증 키 정보를 보려면 동일한 브라우저 세션에서 포털에 로그인 해야 하며 모든 웹 사이트 액세스 권한이 있어야 합니다.

### <a name="authentication-key-expiration-notification"></a>인증 키 만료 알림

인증 키가 만료 되기 전에 전자 메일, PowerApps 포털 관리 센터 및 포털에서 알림이 표시 됩니다.

**Email**

포털에 연결 된 조직에 대 한 전자 메일 알림을 등록 한 사용자에 게 전자 메일이 전송 됩니다. 전자 메일 알림에 등록 하는 방법에 대 한 자세한 내용: [관리자에 게 전자 메일 알림 관리](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

전자 메일 알림은 다음 간격으로 전송 됩니다. 
- 90 일 
- 60 일 
- 30 일 
- 15 일 
- 7 일 
- 6 일 
- 5 일 
- 4 일 
- 3 일 
- 2 일 
- 1 일 
- 12 시간 
- 6 시간 
- 3 시간

키가 만료 된 후 1 주 전에 키가 만료 된 후에도 알림이 표시 됩니다.

> [!NOTE]
> - 간격은 키 만료 날짜 로부터 UTC로 계산 됩니다.
> - 전자 메일은 위에 나열 된 간격에 정확히 일치 하지 않을 수 있습니다. 전자 메일 알림을 지연 하거나 누락 시킬 수 있습니다. 온라인으로 키 만료 날짜도 확인 하세요.

**PowerApps 포털 관리 센터**

키 만료에 대 한 메시지가 페이지 맨 위에 표시 됩니다.

> [!div class=mx-imgBorder]
> Powerapps 포털 관리 센터의 ![인증 키 알림]powerapps 포털 관리 센터(../media/portal-admin-center-auth-notif.png "의 인증 키 알림")

**포탈**

URL < portal_path >/_\_stat/정보로 이동 하면 페이지 맨 아래에 키 만료에 대 한 알림이 표시 됩니다.

> [!NOTE]
> 동일한 브라우저 세션에서 포털에 로그인 해야 하며 모든 웹 사이트 액세스 권한이 할당 되어야 합니다.

> [!div class=mx-imgBorder]
> 포털(../media/portal-service-page-auth-notif.png "의 포털 인증 키 알림에") ![대 한 인증 키 알림]

## <a name="renew-portal-authentication-key"></a>포털 인증 키 갱신

포털이 Common Data Service 환경에 연결할 수 있도록 2 년 마다 키를 갱신 해야 합니다.

> [!NOTE]
> 키를 갱신 하려면 포털을 관리할 수 있는 권한이 있어야 합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 인증 키 관리**를 선택 합니다. 인증 키가 만료 날짜 및 지문과 함께 표시 됩니다.

    > [!div class=mx-imgBorder]
    > ![포털 인증 키]관리(../media/manage-portal-auth-key.png "포털 인증 키") 관리

3. **키 업데이트**를 선택 합니다.

4. 메시지에서 **업데이트** 를 선택 합니다. 업데이트 프로세스가 시작 되 고 메시지가 표시 됩니다.

> [!NOTE]
> - 이 프로세스는 백그라운드에서 실행 되지만 포털은 한 번 다시 시작 됩니다.
> - 키를 업데이트 하는 경우 2 년 동안 업데이트 됩니다.
> - 이 프로세스는 5 ~ 7 분 정도 걸립니다.

### <a name="troubleshooting"></a>문제 해결

키 업데이트가 실패 하면 다음 작업과 함께 오류 메시지가 표시 됩니다.

- **인증 키 업데이트를 다시 시도**합니다. 이 작업을 통해 포털 인증 키 업데이트 프로세스를 다시 시작할 수 있습니다. 업데이트가 여러 번 실패 하는 경우 Microsoft 지원에 문의 하세요.

    > [!div class=mx-imgBorder]
    > ![다시 시도 포털 인증 키 업데이트](../media/retry-auth-key-update.png "다시 시도 포털 인증 키 업데이트")