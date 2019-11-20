---
title: 캔버스 앱 공유 | Microsoft Docs
description: 다른 사용자에게 캔버스 앱을 실행하거나 수정할 수 있는 권한을 부여하여 앱 공유
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/09/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fdf5577f907e2beb7ead5eef3c4d7b06aeaa9c5
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177877"
---
# <a name="share-a-canvas-app-in-powerapps"></a>PowerApps에서 캔버스 앱 공유

비즈니스 요구를 해결하는 캔버스 앱을 빌드한 후에 조직의 어떤 사용자가 앱을 실행하고 수정하며 심지어 다시 공유할 수 있는지 지정합니다. 이름으로 각 사용자를 지정하거나, Azure Active Directory의 보안 그룹을 지정합니다. 모든 사용자가 앱의 이점을 누리는 경우 조직 전체가 실행할 수 있도록 지정합니다.

> [!IMPORTANT]
> For a shared app to function as you expect, you must also manage permissions for the data source or sources on which the app is based, such as [Common Data Service](#common-data-service) or [Excel](share-app-data.md). 또한, 앱이 종속된 [기타 리소스](share-app-resources.md)(예: 흐름, 게이트웨이 또는 연결)도 공유해야 합니다.

## <a name="prerequisites"></a>필수 조건

앱을 공유하려면 로컬이 아닌 클라우드에 저장한 다음, 앱을 게시해야 합니다.

- 사용자가 앱의 기능에 대해 알고 목록에서 쉽게 찾을 수 있도록 앱에 의미 있는 이름을 지정하고 명료한 설명을 제공합니다. PowerApps Studio의 **파일** 메뉴에서 **앱 설정**을 선택하고 이름을 지정한 다음, 설명을 입력하거나 붙여넣습니다.

- 변경 사항을 적용할 때마다 다른 사용자가 해당 변경 사항을 보길 원한다면 저장하고 앱을 다시 게시합니다.

## <a name="share-an-app"></a>앱 공유

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인한 다음, 왼쪽 가장자리 근처에서 **앱**을 선택합니다.

    ![앱 목록 표시](./media/share-app/file-apps.png)

1. Select the app that you want to share by selecting its icon.

    ![Select an app](./media/share-app/select-app.png)

1. In the banner, select **Share**.

    ![공유 화면 열기](./media/share-app/banner-share.png)

1. Specify by name or alias the users or security groups in Azure Active Directory with which you want to share the app.

    - To allow your entire organization to run the app (but not modify or share it), type **Everyone** in the sharing panel.
    - You can share an app with a list of aliases, friendly names, or a combination of those (for example, **Jane Doe &lt;jane.doe@contoso.com** ) if the items are separated by semi-colons. If more than one person has the same name but different aliases, the first person found will be added to the list. A tooltip appears if a name or alias already has permission or can't be resolved. 

    ![Specify users and co-owners](./media/share-app/share-everyone.png)

    > [!NOTE]
    > You can't share an app with a distribution group in your organization or with a group outside your organization.

1. If you want to allow those with whom you're sharing the app to edit and share it (in addition to running it), select the **Co-owner** check box.

    You can't grant **Co-owner** permission to a security group if you [created the app from within a solution](add-app-solution.md).

    > [!NOTE]
    > Regardless of permissions, no two people can edit an app at the same time. If one person opens the app for editing, other people can run it but not edit it.

1. If your app connects to data for which users need access permissions, specify them.

    For example, your app might connect to an entity in a Common Data Service database. When you share such an app, the sharing panel prompts you to manage security for that entity.

    > [!div class="mx-imgBorder"]
    > ![Assign a security role](media/share-app/cds-assign-security-role.png)

    For more information about managing security for an entity, see [Manage entity permissions](share-app.md#manage-entity-permissions) later in this topic.

1. If you want to help people find your app, select the **Send an email invitation to new users** check box.

1. At the bottom of the share panel, select **Share**.

    Everyone with whom you shared the app can run it in PowerApps Mobile on a mobile device or in AppSource on [Dynamics 365](https://home.dynamics.com) in a browser. Co-owners can edit and share the app in [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    If you sent an email invitation, everyone with whom you shared the app can run it by selecting a link in the invitation.

    - If a user selects the link on a mobile device, the app opens in PowerApps Mobile.
    - If a user selects the link on a desktop computer, the app opens in a browser.

    Co-owners who receive an invitation get another link that opens the app for editing in PowerApps Studio.

You can change permissions for a user or a security group by selecting their name and then performing either of these steps:

- To allow co-owners to run the app but no longer edit or share it, clear the **Co-owner** check box.
- To stop sharing the app with that user or group, select the Remove (x) icon.

## <a name="security-group-considerations"></a>보안 그룹 고려 사항

- 보안 그룹과 앱을 공유한 경우 그룹의 기존 회원 및 가입하는 모든 회원이 해당 그룹에 지정된 사용 권한을 받습니다. 그룹을 떠난 사람은 액세스 권한이 있는 다른 그룹에 속하거나, 개인으로 사용 권한이 부여되지 않는 한 해당 사용 권한을 잃게 됩니다.

- 보안 그룹의 모든 구성원은 앱에 대해 전체 그룹과 동일한 권한을 갖습니다. 하지만 해당 그룹의 한 명 또는 그 이상의 회원에게 더 많은 사용 권한을 지정하여 더 많은 액세스를 허용할 수 있습니다. For example, you can give Security Group A permission to run an app, but you can also give User B, who belongs to that group, **Co-owner** permission. 보안 그룹의 모든 구성원은 앱을 실행할 수 있지만 사용자 B만 편집할 수 있습니다. If you give Security Group A **Co-owner** permission and User B permission to run the app, that user can still edit the app.

## <a name="manage-entity-permissions"></a>엔터티 사용 권한 관리

### <a name="common-data-service"></a>Common Data Service

If you create an app based on Common Data Service, you must also ensure that the users with whom you share the app have the appropriate permissions for the entity or entities on which the app relies. Specifically, those users must belong to a security role that can perform tasks such as creating, reading, writing, and deleting relevant records. In many cases, you'll want to create one or more custom security roles with the exact permissions that users need to run the app. You can then assign a role to each user as appropriate.

> [!NOTE]
> As of this writing, you can assign security roles to individual users and security groups in Azure Active Directory but not to Office groups.

#### <a name="prerequisite"></a>필수 조건

To assign a role, you must have **System administrator** permissions for a Common Data Service database.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Assign a security group in Azure AD to a role

1. In the sharing panel, select **Assign a security role** under **Data permissions**.

1. Select the role or roles in Common Data Service that you want to assign to the user or the security group in Azure AD with which you want to share the app.
     > [!div class="mx-imgBorder"] 
     > ![Security role list](media/share-app/cds-assign-security-role-list.png "Security role list")

### <a name="common-data-service-previous-version"></a>Common Data Service(이전 버전)

When you share an app that's based on an older version of Common Data Service, you must share the runtime permission to the service separately. If you don’t have permission to do this, see your environment administrator.

## <a name="share-with-guests"></a>Share with guests
 
PowerApps canvas apps can be shared with guest users of an Azure Active Directory tenant. This enables inviting external business partners, contractors, and third parties to run your company’s canvas apps. 

> [!NOTE]
> Guests may only be assigned the **User** role, and not the **Co-owner** role, for apps shared with them.

### <a name="prerequisites"></a>필수 조건
- In Azure Active Directory (Azure AD), enable B2B external collaboration for the tenant. More information: [Enable B2B external collaboration and manage who can invite guests](/azure/active-directory/b2b/delegate-invitations)
    - Enable B2B external collaboration is on by default. However, the settings can be changed by a tenant admin.  For more information about Azure AD B2B, see [What is guest user access in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)  
- Access to an account that can add guest users to an Azure AD tenant. Admins and users with the Guest Inviter role can add guests to a tenant.   
- The guest user must have a license with Power Apps use rights that matches the capability of the app assigned through one of the following tenants:
    - The tenant hosting the app being shared.
    - The home tenant of the guest user.

### <a name="steps-to-grant-guest-access"></a>Steps to grant guest access
1. Select **New guest user** to add guest users in Azure AD. More information: [Quickstart: Add a new guest user in Azure AD](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal).
    > [!div class="mx-imgBorder"] 
    > ![Add guest in Azure AD](media/share-app/guest_access_doc_1.png "Add guest in Azure AD")
2. If the guest user doesn't already have a license in their home tenant, assign a license to the guest user.
   - To assign guest users from admin.microsoft.com, see [Assign licenses to one user](/office365/admin/subscriptions-and-billing/assign-licenses-to-users).
   - To assign guest users from portal.azure.com, see [Assign or remove licenses](/azure/active-directory/fundamentals/license-users-groups).
 
   > [!IMPORTANT]
   > You may need to disable the Microsoft 365 admin center preview to assign a license to a guest. 

3. Share the canvas app. 
    1. Sign in to https://make.powerapps.com  
    2. Go to **Apps**, select a canvas app, and then on the command bar select **Share**. 
    3. Enter an email address for a guest user from an Azure AD tenant. More information: [What is guest user access in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)
          > [!div class="mx-imgBorder"] 
          > ![Share with guest](media/share-app/guest_access_doc_2.png "Share with guest")
 
After you share an app for guest access, guests can discover and access apps shared with them from the email sent to them as part of sharing.

> [!div class="mx-imgBorder"]  
> ![Guests receive app share email](media/share-app/guest_access_doc_4.png "Guests receive app share email")

### <a name="frequently-asked-questions"></a>Frequently Asked Questions

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-powerapps-portals"></a>What’s the difference between canvas app guest access and PowerApps Portals? 
Canvas apps enable building an app, tailored to digitizing a business processes, without writing code in a traditional programming language such as C#. Guest access for canvas apps enables teams of individuals made up of different organizations participating in a common business process to access the same app resources that may be integrated with a wide variety of Microsoft and third-party sources. More information: [Overview of canvas-app connectors for PowerApps](/powerapps/maker/canvas-apps/connections-list).

[PowerApps Portals](/powerapps/maker/portals/overview) provide the ability to build low-code, responsive websites that allow external users to interact with the data stored in Common Data Service. It allows organizations to create websites that can be shared with users external to their organization either anonymously or through the login provider of their choice, such as LinkedIn, Microsoft Account, or other commercial login providers. 

The following table outlines a few core capability differences between PowerApps Portals and canvas apps.  

| | 인터페이스 | Authentication | Accessible data sources |
|------|--------|----------|-------------------|
| PowerApps Portals | Browser only experience | Allows anonymous and authenticated access | Common Data Service |
| 캔버스 앱 | Browser and mobile apps | Requires authentication via Azure AD | Any ~150 out-of-box connectors and any custom connector  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>Can guests access customized forms in SharePoint?
Yes. Any user that can access a SharePoint list with a customized form can create and edit items in the list, using the form, without any Power Apps license.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>Can guests access apps embedded in SharePoint? 
Yes. Though, access to canvas standalone apps require a license with Power Apps use rights that matches the capability of the app, including apps that are embedded. When embedding a canvas app in SharePoint via the Microsoft PowerApps embed control, enter the app id. To do this, enter the app ID in the **App web link or ID** box. 

> [!div class="mx-imgBorder"]  
> ![Embed canvas app in SharePoint for guests](media/share-app/guest_access_doc_5.PNG "Embed canvas app in SharePoint for guests")

When embedding a canvas app in SharePoint via the iFrame HTML tag, reference the app using the full web URL. To find the URL, go to https://make.powerapps.com, select an app, select the **Details** tab, and the URL is displayed under **Web link**.

> [!div class="mx-imgBorder"]  
> ![Canvas app details](media/share-app/guest_access_doc_6.PNG "Canvas app details")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>How come guests can launch the app shared with them but connections fail to be created?
As with non-guests, the underlying data source(s) accessed by the app must also be made accessible to the guest.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>What license must be assigned to my guest so they can run an app shared with them?
The same license that’s required for non-guests to run an app. For instance, if the app uses premium connecters then a PowerApps Per App Plan or a PowerApps Per User Plan must be assigned to the guest.  

|                                 | SharePoint customized form | Standalone canvas app using non-premium connectors | Standalone canvas app using premium connectors | Model driven app |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint user (no PA license) | x                          |                                                    |                                                |                  |
| Power Apps Included w/ Office    | x                          | x                                                  |                                                |                  |
| Power Apps Per App Plan          | x                          | x                                                  | x                                              | x                |
| Power Apps Per User Plan         | x                          | x                                                  | x                                              | x                |


#### <a name="in-powerapps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>In PowerApps Mobile, how does a guest see apps for their home tenant?
Any user that has accessed an canvas app, on their mobile device, that’s published in an Azure AD tenant that isn’t their home tenant must sign-out of PowerApps and sign back in to PowerApps Mobile.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>Must a guest accept the Azure AD guest invitation prior to sharing an app with the guest?
No. If a guest launches an app shared with them prior to accepting a guest invitation the guest will be prompted to accept the invitation as part of the sign-in experience while launching the app.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>What Azure AD tenant are connections for a guest user created in?
Connections for an app are always made in the context of the Azure AD tenant the app is associated. For instance, if an app is created in the Contoso tenant then connections made for Contoso internal and guest users are made in the context of the Contoso tenant.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>Can guests use Microsoft Graph via Microsoft Security Graph connector or a custom connector using Microsoft Graph APIs?
No, Azure AD guests can't query Microsoft Graph to retrieve information for a tenant in which they’re a guest.

#### <a name="what-intune-policies-apply-to-guests-using-my-powerapps"></a>What InTune policies apply to guests using my PowerApps?
InTune only applies policies of a user’s home tenant. For instance, if Alice@Contoso.com shares an app with Vikram@Fabrikam.com, InTune continues to apply Fabrikam.com policies on Virkam’s device regardless of the PowerApps he runs.

#### <a name="what-connectors-support-guest-access"></a>What connectors support guest access?
All connectors that do not perform Azure AD authentication of any type supports guest access. The following table enumerates all connectors that perform Azure AD authentication and which connectors currently support guest access. Many of these will be updated leading up to general availability.

| **Connector**                                     | **Supports guest access**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 Appointment Scheduling                      | 아니요                                                                     |
| Adobe Creative Cloud                              | 아니요                                                                     |
| Adobe Sign                                        | 아니요                                                                     |
| Asana                                             | 아니요                                                                     |
| AtBot Admin                                       | 아니요                                                                     |
| AtBot Logic                                       | 아니요                                                                     |
| Azure AD                                          | 예                                                                    |
| Azure Automation                                  | 예                                                                    |
| Azure Container Instance                          | 예                                                                    |
| Azure Data Factory                                | 예                                                                    |
| Azure Data Lake                                   | 예                                                                    |
| Azure DevOps                                      | 아니요                                                                     |
| Azure Event Grid                                  | 아니요                                                                     |
| Azure IoT Central                                 | 예                                                                    |
| Azure Key Vault                                   | 아니요                                                                     |
| Azure Kusto                                       | 예                                                                    |
| Azure Log Analytics                               | 예                                                                    |
| Azure Resource Manager                            | 예                                                                    |
| Basecamp 2                                        | 아니요                                                                     |
| Bitbucket                                         | 아니요                                                                     |
| Bitly                                             | 아니요                                                                     |
| bttn                                              | 아니요                                                                     |
| Buffer                                            | 아니요                                                                     |
| Business Central                                  | 아니요                                                                     |
| CandidateZip                                      | 아니요                                                                     |
| Capsule CRM                                       | 아니요                                                                     |
| Cloud PKI Management                              | 아니요                                                                     |
| Cognito Forms                                     | 아니요                                                                     |
| Common Data Service                               | 아니요                                                                     |
| Common Data Service (Legacy)                      | 아니요                                                                     |
| D&B Optimizer                                     | 아니요                                                                     |
| Derdack SIGNL4                                    | 아니요                                                                     |
| Disqus                                            | 아니요                                                                     |
| Document Merge                                    | 아니요                                                                     |
| Dynamics 365                                      | 아니요                                                                     |
| Dynamics 365 AI for Sales                         | 예                                                                    |
| Dynamics 365 for Fin & Ops                        | 아니요                                                                     |
| Enadoc                                            | 아니요                                                                     |
| Eventbrite                                        | 아니요                                                                     |
| Excel Online (Business)                           | 아니요                                                                     |
| Excel Online (OneDrive)                           | 아니요                                                                     |
| Expiration Reminder                               | 아니요                                                                     |
| FreshBooks                                        | 아니요                                                                     |
| GoToMeeting                                       | 아니요                                                                     |
| GoToTraining                                      | 아니요                                                                     |
| GoToWebinar                                       | 아니요                                                                     |
| Harvest                                           | 아니요                                                                     |
| HTTP with Azure AD                                | 아니요                                                                     |
| Infusionsoft                                      | 아니요                                                                     |
| Inoreader                                         | 아니요                                                                     |
| Intercom                                          | 아니요                                                                     |
| JotForm                                           | 아니요                                                                     |
| kintone                                           | 아니요                                                                     |
| LinkedIn                                          | 아니요                                                                     |
| Marketing Content Hub                             | 아니요                                                                     |
| Medium                                            | 아니요                                                                     |
| Metatask                                          | 아니요                                                                     |
| Microsoft Forms                                   | 아니요                                                                     |
| Microsoft Forms Pro                               | 아니요                                                                     |
| Microsoft Graph Security                          | 아니요                                                                     |
| Microsoft Kaizala                                 | 아니요                                                                     |
| Microsoft School Data Sync                        | 아니요                                                                     |
| Microsoft StaffHub                                | 아니요                                                                     |
| Microsoft Teams                                   | 예                                                                    |
| Microsoft To-Do (Business)                        | 아니요                                                                     |
| Muhimbi PDF                                       | 아니요                                                                     |
| NetDocuments                                      | 아니요                                                                     |
| Office 365 그룹                                 | 예                                                                    |
| Office 365 Outlook                                | 아니요                                                                     |
| Office 365 사용자                                  | 예                                                                    |
| Office 365 비디오                                  | 아니요                                                                     |
| OneDrive                                          | 아니요                                                                     |
| 비즈니스용 OneDrive                             | 아니요                                                                     |
| OneNote(비즈니스)                                | 아니요                                                                     |
| Outlook Customer Manager                          | 아니요                                                                     |
| Outlook 작업                                     | 예                                                                    |
| Outlook.com                                       | 아니요                                                                     |
| Paylocity                                         | 아니요                                                                     |
| Planner                                           | 아니요                                                                     |
| Plumsail Forms                                    | 아니요                                                                     |
| Power BI                                          | 예                                                                    |
| Project Online                                    | 아니요                                                                     |
| ProjectWise Design Integration                    | 아니요                                                                     |
| Projectwise Share                                 | 아니요                                                                     |
| SharePoint                                        | 예                                                                    |
| SignNow                                           | 아니요                                                                     |
| Skype for Business Online                         | 아니요                                                                     |
| Soft1                                             | 아니요                                                                     |
| Stormboard                                        | 아니요                                                                     |
| Survey123                                         | 아니요                                                                     |
| SurveyMonkey                                      | 아니요                                                                     |
| Toodledo                                          | 아니요                                                                     |
| Typeform                                          | 아니요                                                                     |
| Vimeo                                             | 아니요                                                                     |
| Webex Teams                                       | 아니요                                                                     |
| Windows Defender Advanced Threat Protection (ATP) | 아니요                                                                     |
| Word Online (Business)                            | 아니요                                                                     |
