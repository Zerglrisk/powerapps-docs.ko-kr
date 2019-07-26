---
title: Outlook용 Dynamics 365 앱 배포 | MicrosoftDocs
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
ms.openlocfilehash: d75ec08a1d4d594136ca3339daa819cf89ee910a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456792"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Outlook용 Dynamics 365 앱 배포
데스크톱, 웹 또는 태블릿에서 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]을(를) 사용하는 동안 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]을(를) 사용하여 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]의 전원을 탭할 수 있습니다. 예를 들어 이메일 또는 약속 받는 사람에 대한 정보를 보거나 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 이메일 또는 약속을 기회, 계정 또는 사례와 같은 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 레코드에 연결합니다. [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]에서 제공하는 제품에 대해 알아보려면 [Outlook용 Dynamics 365 앱 사용자 가이드](http://go.microsoft.com/fwlink/p/?LinkID=613099)를 참조하세요.  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]은(는) [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]와(과) 동일하지 않습니다. [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]의 경우 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)]와(과) 쌍을 이루는 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]이(가) [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]을(를) [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]와(과) 통합하는 가장 좋은 방법입니다. **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 및 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]이(가) 동일한 사용자에 의해 함께 사용되는 경우 작업 추적은 지원되지 않습니다.** [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 추가 기능에 대한 자세한 내용은 [Outlook용 Dynamics 365 사용자 가이드](http://go.microsoft.com/fwlink/p/?LinkID=524751)를 참조하세요.  
>   
>  [위임된 사용자](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540)는 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용하여 이메일을 추적할 수 없습니다. 위임된 사용자의 경우 [폴더 수준 추적 또는 자동 추적](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx)을 사용하는 것이 좋습니다.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Outlook용 Dynamics 365 앱과 Outlook용 Dynamics 365 비교  
 다음 표에서는 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)](으)로 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 기능을 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]와(과) 비교합니다([!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 클라이언트 또는 추가 기능으로도 알려짐).  
  
||||  
|-|-|-|  
|**기능**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|이메일과 관련된 추적 및 설정|예|예|  
|약속과 관련된 추적 및 설정|예|예|  
|연락처와 관련된 추적 및 설정|예|예|  
|작업과 관련된 추적 및 설정|아니요|예|  
|다음과 관련된 원 클릭 설정|예|아니요|  
|받는 사람의 요약 표시|예|아니요|  
|이메일/약속의 레코드 요약 정보 표시|예|아니요|  
|[!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]에서 작동|예|아니요|  
|[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 데스크톱에서 작동|예|예|  
|Mac용 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]에서 작동|예|아니요|  
|휴대폰에서 작동|예|아니요|  
|[!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 레코드 직접 열고 만들기|예|예|  
|사용자 지정 양식 및 비즈니스 논리 적용|예|예|  
|오프라인으로 작업|아니요|예|  
|이메일 템플릿 적용|예|예|  
|영업 홍보 자료 적용|예|예|  
|기술 문서 적용|예|예|  
|이메일을 보낸 후 모니터링하는 기능|예|아니요|  
|보기 정렬, 필터링, 서식 지정, 그룹화 및 분류|아니요|예|  
|Word 메일 병합 문서 만들기|아니요|예|  
|필드 동기화 제어|아니요|예|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>요구 사항  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용하려면 다음 항목이 필요합니다.  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] 또는 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   서버 쪽 동기화를 통해 들어오는 이메일의 동기화 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][이메일, 약속, 연락처 및 작업의 서버 쪽 동기화 설정](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   아래 설명된 대로 필요한 권한  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] 기능에 대해 지원되는 구성 및 요구 사항은 설명서 전체에서 나열됩니다. 문서화되지 않은 특정 구성은 지원되지 않는 것으로 간주해야 합니다.  
  
### <a name="required-privileges"></a>필요한 권한  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]은(는) **Outlook용 Dynamics 365 앱 사용** 권한을 통해 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]에 대한 액세스를 제공합니다. 사용자가 이 권한이 없으면 다음 오류를 받습니다.  
  
> "이 앱을 사용하도록 인증되지 않았습니다. 시스템 관리자에게 확인하여 설정을 업데이트합니다."  
  
 사용자는 다음 엔터티에 대한 읽기/쓰기 권한도 있어야 합니다.  
  
 비즈니스 관리 탭:  
  
-   **사서함**  
  
 사용자 지정 탭:  
  
-   **엔터티**  
  
-   **필드**  
  
-   **관계**  
  
-   **시스템 애플리케이션 메타데이터**  
  
-   **시스템 양식**  
  
-   **사용자 애플리케이션 메타데이터**  
  
-   **보기**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>보안 역할에 대한 권한 설정  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  **보안 역할**을 클릭합니다.  
  
3.  보안 역할을 선택한 다음, **비즈니스 관리** 탭을 클릭합니다.  
  
4.  **엔터티** 섹션에서 **사서함** 권한 설정을 검토합니다. 보안 역할에는 사용자 이상의 설정이 있어야 합니다.  
  
5.  **개인 정보 관련 권한** 섹션에서 **Outlook용 Dynamics 365 앱 사용**이 **조직**으로 설정되어 있는지 확인합니다. 그렇지 않은 경우 **Outlook용 Dynamics 365 앱 사용**을 클릭합니다.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Microsoft Exchange를 사용하여 지원되는 구성  
 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]의 경우 하이브리드 구성을 포함하여 [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] 또는 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] 및 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] 또는 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)](온-프레미스)의 조합으로 앱을 사용할 수 있습니다. 즉, 다음 구성 중에서 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용할 수 있습니다.  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)](온-프레미스)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)](온-프레미스)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]을(를) 사용하는 경우 아래 설명된 대로 IFD 인증으로 인증해야 합니다.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>웹에서 Outlook에 대해 지원되는 브라우저  
 다음 브라우저에서 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)](으)로 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]을(를) 사용할 수 있습니다.  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]또는 [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     다음 구성이 지원됩니다.  
  
    -   보호 모드는 **인터넷** 보안 영역에 대해 활성화됩니다. 보호 모드를 활성화하려면: IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **인터넷**으로 이동합니다.  
  
    -   보호 모드는 **로컬 인트라넷** 보안 영역에 대해 활성화됩니다. 보호 모드를 활성화하려면: IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **로컬 인터넷**으로 이동합니다.  
  
    -   [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] URL은 신뢰할 수 있는 웹 사이트의 **로컬 인트라넷** 보안 영역 목록에 있습니다. IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **로컬 인트라넷** > **사이트** > **고급**으로 이동합니다.  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]의 [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)](최신 버전)  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]의 [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)](최신 버전)  
  
-   Mac 또는 OSX의 [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)](버전 9 또는 버전 10)  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>데스크톱에서 Outlook에 대해 지원되는 운영 체제  
 데스크톱에 대해 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]의 이러한 버전에서 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용할 수 있습니다.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 및 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016  
  
-   Mac*용 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]  
  
     *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 버전 15.0.847.32 이상이 필요합니다.  
  
### <a name="supported-mobile-devices"></a>지원되는 모바일 디바이스  
 다음 휴대폰 및 운영 체제의 모바일 브라우저에서 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)](으)로 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용할 수 있습니다.  
  
-   iOS 버전 8, 9 또는 10을 실행하는 [!INCLUDE[tn_apple](../includes/tn-apple.md)][!INCLUDE[tn_iphone](../includes/tn-iphone.md)] 디바이스  
  
-   [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4(KitKat) 또는 5.0(Lollipop), 6(Marshmallow) 또는 7(Nougat)을 실행하는 [!INCLUDE[tn_android](../includes/tn-android.md)] 휴대폰  
  
-   [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] 또는 [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)]을(를) 실행하는 [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] 디바이스  
  
### <a name="supported-clients-per-feature"></a>기능당 지원되는 클라이언트  
 지원되는 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 기능은 실행 중인 클라이언트에 따라 달라집니다. 다음 표에서는 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 및 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]의 각 클라이언트/구성에 대해 지원되는 기능을 요약합니다.  
  
 ![각 Outlook용 Dynamics 365 앱 기능에 대해 지원되는 클라이언트](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "각 Outlook용 Dynamics 365 앱 기능에 대해 지원되는 클라이언트")  
  
 (1)  [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]은(는) [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] 및 [!INCLUDE[tn_chrome](../includes/tn-chrome.md)]을(를) 지원합니다.  
  
 (2)  모바일 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]은(는) [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat(4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow 및 [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat을 지원합니다.  
  
 (3)  작성 모드의 이메일 추적 및 약속 추적에는 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 또는 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016이 필요합니다.  
  
 (4)  연락처 추적은 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 및 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 이상에서만 지원됩니다.  
  
 (5)  이메일 템플릿 추가, 기술 관리 문서 및 영업 홍보 자료는 모바일 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]에서 지원되지 않습니다.  
  
 (6)  [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 이상에서만 지원됩니다.  
  
 (7)  16.0.6741.1000 이상에서만 지원됩니다.  
  
> [!NOTE]
>  태블릿은 현재 지원되지 않습니다(CY2017 출시).  
  
 [이 블로그에서 지원되는 클라이언트에 대한 자세한 세부 정보를 읽어보세요. Outlook용 Dynamics 365 앱 지원 매트릭스](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>지원되는 서버  
 [Office 추가 기능을 사용하기 위한 서버 요구 사항](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins)은 [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] 또는 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]입니다.  
  
### <a name="supported-languages"></a>지원되는 언어  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]은(는) 다음 언어를 지원합니다.  
  
||||  
|-|-|-|  
|불가리아어(불가리아) - 1026|힌디어(인도) - 1081|포르투갈어(포르투갈) - 2070|  
|중국어(중국) - 2052|헝가리어 - 1038|루마니아어 - 1048|  
|중국어(대만) - 1028|인도네시아어 - 1057|러시아어 - 1049|  
|크로아티아어(크로아티아) - 1050|이탈리아어 - 1040|세르비아어 - 2074|  
|체코어(체코) - 1029|일본어 - 1041|슬로바키아어 - 1051|  
|덴마크어 - 1030|카자흐어 - 1087|슬로베니아어 - 1060|  
|네덜란드어 - 1043|한국어 - 1042|스페인어 - 3082|  
|영어 - 1033|라트비아어 - 1062|스웨덴어 - 1053|  
|에스토니아어 - 1061|리투아니아어 - 1063|태국어 - 1054|  
|핀란드어 - 1035|말레이시아어 - 1086|터키어 - 1055|  
|프랑스어 - 1036|노르웨이어 - 1044|우크라이나어 - 1058|  
|독일어 - 1031|폴란드어 - 1045|베트남어 - 1066|  
|그리스어 - 1032|포르투갈어(브라질) - 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Outlook용 Dynamics 365 앱 배포  
 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 설정 및 필요한 권한 설정 후 일부 또는 모든 사용자에게 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 푸시하거나 필요에 따라 사용자가 설치하도록 할 수 있습니다.  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)]를 사용하는 경우 아래 섹션을 참조하세요.  [Dynamics 365 온-프레미스 사용자에게 배포하려면](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>사용자에게 앱을 푸시하려면  
  
1.  **설정** >  **Outlook용 Dynamics 365 앱**으로 이동합니다.  
  
2.  **Outlook용 Dynamics 365 앱 시작** 화면의 **적격 사용자에 대해 추가** 아래에서(두 번째로 또는 그 이후로 이 화면을 여는 경우 **설정**을 클릭해야 할 수 있음) 사용자가 앱을 자동으로 가져올 수 있도록 하려는 경우 **자동으로 앱 추가[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** 확인 상자를 선택합니다. 사용자에게 필요한 권한이 있고 이메일이 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)]을(를) 통해 동기화된 경우 앱을 푸시하기 위해 더 이상 수행해야 할 작업이 없습니다. 예를 들어 판매 직원 역할에 필요한 권한을 추가한 다음, 새 사용자에게 이 역할을 할당하는 경우 앱을 자동으로 가져옵니다.  
  
3.  다음 중 하나를 수행합니다.  
  
    -   모든 적격 사용자에게 앱을 푸시하려면 **모든 적격 사용자에 대해 앱 추가**를 클릭합니다.  
  
    -   특정 사용자에게 앱을 푸시하려면 목록에서 해당 사용자를 선택한 다음, **Outlook에 앱 추가**를 클릭합니다.  
  
    > [!TIP]
    >  목록이 사용자가 보류 중이거나 추가되지 않았음을 표시하는 경우 사용자 옆의 **자세히 알아보기** 링크를 클릭하여 상태에 대한 자세한 정보를 찾을 수 있습니다.  
  
4.  완료되면 **저장**을 클릭합니다.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>사용자가 앱을 직접 설치하도록 하려면  
  
1.  사용자는 **설정** 단추 ![설정 단추](media/mp-ua-r16-settings.png "설정 단추")를 클릭한 다음, **Dynamics 365용 앱**을 클릭합니다.  
  
2.  **Dynamics 365용 앱** 화면의 **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** 아래에서 사용자는 **[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]에 앱 추가**를 클릭합니다.  
  
> [!NOTE]
>  사용자는 필요한 경우 직접 추가 기능을 비활성화하거나 제거할 수도 있습니다. 자세한 내용은 [Outlook용 Dynamics 365 앱 사용자 가이드](http://go.microsoft.com/fwlink/p/?LinkID=613099)를 참조하세요.  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Dynamics 365 온-프레미스 사용자에게 배포하려면  
 Dynamics 365 온-프레미스를 사용하는 경우 다음 단계를 수행합니다.  
  
-   인터넷 연결 배포에 대해 Dynamics 365 서버를 구성합니다. [Microsoft Dynamics 365에 대한 IFD 구성](https://technet.microsoft.com/library/dn609803.aspx)을 참조하세요.  
  
-   Exchange 온-프레미스에 연결하는 경우 OAuth 공급자를 구성하고 클라이언트 앱을 등록합니다. [OAuth를 사용하는 Dynamics 365 애플리케이션에 대한 Windows Server 2012 R2 구성](https://technet.microsoft.com/library/hh699726.aspx)을 참조하세요.  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>설치 문제 해결  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 설치에 문제가 있는 경우 해당 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함이 현재 다른 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 조직에 연결되었기 때문일 수 있습니다. [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함(이메일 주소)은 약속, 연락처 및 작업을 하나의 조직과만 동기화할 수 있으며 해당 조직에 속하는 사용자는 약속, 연락처 및 작업을 하나의 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함과만 동기화할 수 있습니다.  기본 동기화 조직을 변경하려는 경우 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]에 저장된 설정을 덮어쓸 수 있습니다. 자세한 내용은 [이 KB 문서](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook)를 참조하세요.  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>사용자 가이드 탐색 및 사용자 교육  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을(를) 사용하는 방법을 알아보려면 [Outlook용 Dynamics 365 앱 사용자 가이드를 참조하세요](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Outlook용 Dynamics 365 앱 사용자 가이드 페이지](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Outlook용 Dynamics 365 앱 사용자 가이드 페이지")  
  
## <a name="see-also"></a>참고 항목  
 [Outlook용 Dynamics 365 앱 사용자 가이드](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [이 블로그에서 지원되는 클라이언트에 대한 자세한 세부 정보를 읽어보세요. Outlook용 Dynamics 365 앱 지원 매트릭스](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [이메일, 약속, 연락처 및 작업의 서버 쪽 동기화 설정](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [사용자, 라이선스 및 보안 역할 추가](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [Microsoft Dynamics 365(온라인)에 상호 운용성 기능 추가](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)