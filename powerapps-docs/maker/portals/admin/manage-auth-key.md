---
title: Dynamics 365 온라인 조직에 포털 연결 | MicrosoftDocs
description: Dynamics 365 온라인 조직에 포털을 연결하는 방법과 인증 키를 갱신하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="connect-to-a-dynamics-365-online-organization-using-a-portal"></a>포털을 사용하여 Dynamics 365 온라인 조직에 연결

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

포털은 Azure Active Directory 애플리케이션을 사용하여 Dynamics 365 온라인 조직에 연결합니다. 응용 프로그램은 포털이 구축된 테넌트에 만들어집니다. 애플리케이션은 포털 프로비저닝 프로세스 중에 Dynamics 365 조직과 함께 등록됩니다.

![Dynamics 365 조직으로 포털 연결](../media/connect-with-dynamics.png "Dynamics 365 조직으로 포털 연결")

각 포털은 동일한 Dynamics 365 조직에 연결되어 있는지 여부와 관계 없이 별도의 Azure Active Directory 애플리케이션에 연결되어 있습니다. 포털에 대해 만들어진 기본 Azure Active Directory 인증 공급자는 동일한 Azure Active Directory 응용 프로그램을 사용하여 포털을 인증합니다. 인증은 포털에 액세스하는 사용자에게 할당된 웹 역할에 의해 적용됩니다.

Azure Active Directory에서 연결된 포털 응용 프로그램을 볼 수 있습니다. 이 응용 프로그램의 이름은 Microsoft CRM 포털이 되며, 포털 ID는 Azure Active Directory 응용 프로그램의 **앱 ID URI** 필드에 있습니다. 포털을 프로비전하는 사람이 이 응용 프로그램을 소유합니다. 포털 기능이 손상될 수 있으므로 이 응용 프로그램을 삭제하거나 수정해서는 안 됩니다. 포털 관리 센터에서 포털을 관리하려면 응용 프로그램 담당자여야 합니다.

## <a name="authentication-key"></a>인증 키

포털이 Azure Active Directory 애플리케이션을 사용하여 Dynamics 365에 연결하려면 Azure Active Directory 애플리케이션에 연결된 인증 키가 필요합니다. 이 키는 포털을 프로비전할 때 생성되며 이 키의 공용 부분은 Azure Active Directory 응용 프로그램에 자동으로 업로드됩니다.

> [!IMPORTANT]
> 인증 키는 2년 후에 만료됩니다. 포털이 Dynamics 365 조직에 계속 연결될 수 있도록 2년마다 갱신해야 합니다. 키를 업데이트하지 않으면 포털이 작동하지 않습니다.  

### <a name="authentication-key-details"></a>인증 키 세부 정보

인증 키의 세부 정보는 포털 관리 센터 및 포털에 표시됩니다.

**포털 관리 센터**

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 인증 키 관리**를 선택합니다. 인증 키가 만료 날짜 및 지문과 함께 표시됩니다.

   > [!div class=mx-imgBorder]
   > ![포털 관리 센터의 인증 키 세부 정보](../media/manage-auth-key.png "포털 관리 센터의 인증 키 세부 정보")

**포털**

1. 포털에 관리자로 로그인합니다.

2. Navigate to the URL <포털_경로>/_services/about으로 이동합니다. 인증 키 만료 날짜가 표시됩니다. 

   > [!div class=mx-imgBorder]
   > ![포털 서비스 페이지](../media/portal-services-page.png "포털 서비스 페이지")

> [!NOTE]
> 인증 키 정보를 보려면 동일한 브라우저 세션에서 포털에 로그인해야 하며 모든 웹 사이트 액세스 권한이 있어야 합니다.

### <a name="authentication-key-expiration-notification"></a>인증 키 만료 알림

인증 키가 만료되기 전에 이메일, 포털 관리 센터 및 포털로 통보됩니다.

**Email**

이메일은 포털에 연결된 조직에 대한 이메일 알림을 등록한 사람에게 보내집니다. 이메일 알림에 가입하는 방법에 대한 추가 정보: [관리자에 대한 이메일 알림 관리](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-email-notifications)

이메일 알림은 다음과 같은 간격으로 보내집니다. 
- 90일 
- 60일 
- 30일 
- 15일 
- 7일 
- 6일 
- 5일 
- 4일 
- 3일 
- 2일 
- 하루 
- 12시간 
- 6시간 
- 3시간

키가 만료되면 그 1주일 후까지 매일 알림이 표시됩니다.

> [!NOTE]
> - 간격은 키 만료 날짜에서 UTC로 계산됩니다.
> - 이메일이 위에 나열된 간격으로 정확하게 보내지지는 않습니다. 이메일 알림은 지연되거나 누락될 수 있습니다. 또한 온라인에서 중요한 만료 날짜를 확인하십시오.

**포털 관리 센터**

키 만료에 대한 메시지가 페이지 맨 위에 표시됩니다.

> [!div class=mx-imgBorder]
> ![포털 관리 센터의 인증 키 알림](../media/portal-admin-center-auth-notif.png "포털 관리 센터의 인증 키 알림")

**포털**

<포털_경로>/_services/about URL로 이동하면 키 만료에 대한 알림이 페이지 아래쪽에 표시됩니다.

> [!NOTE]
> 동일한 브라우저 세션에서 포털에 로그인해야 하며 모든 웹 사이트 액세스 권한을 할당 받아야 합니다.

> [!div class=mx-imgBorder]
> ![포털의 인증 키 알림](../media/portal-service-page-auth-notif.png "포털의 인증 키 알림")

## <a name="renew-portal-authentication-key"></a>포털 인증 키 갱신

포털이 Dynamics 365 조직에 계속 연결될 수 있도록 2년마다 키를 갱신해야 합니다.

> [!NOTE]
> 키를 갱신하려면 포털을 관리할 수 있는 권한이 있어야 합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 인증 키 관리**를 선택합니다. 인증 키가 만료 날짜 및 지문과 함께 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![포털 인증 키 관리](../media/manage-portal-auth-key.png "포털 인증 키 관리")

3. **키 업데이트**를 선택합니다.

4. 메시지에서 **업데이트**를 선택합니다. 업데이트 프로세스가 시작되고 메시지가 표시됩니다.

> [!NOTE]
> - 이 프로세스는 백그라운드에서 실행되지만 포털은 다시 한 번 시작됩니다.
> - 키를 업데이트하면 2년 동안 업데이트됩니다.
> - 이 프로세스는 5~7분 정도 걸립니다.

### <a name="troubleshooting"></a>문제 해결

키 업데이트가 실패하면 다음 동작과 함께 오류 메시지가 표시됩니다.

- **인증 키 업데이트 다시 시도**. 이 동작으로 포털 인증 키 업데이트 프로세스를 다시 시작할 수 있습니다. 업데이트가 여러 번 실패하면 Microsoft 지원에 문의하십시오.

    > [!div class=mx-imgBorder]
    > ![포털 인증 키 업데이트 다시 시도](../media/retry-auth-key-update.png "포털 인증 키 업데이트 다시 시도")