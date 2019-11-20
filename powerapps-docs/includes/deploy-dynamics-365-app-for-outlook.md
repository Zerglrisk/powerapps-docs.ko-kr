---
title: Dynamics 365 App for Outlook 배포 | MicrosoftDocs
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
ms.openlocfilehash: 2df69eb2823726116ca08e893acf384afffdd957
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754130"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Dynamics 365 App for Outlook 배포
데스크톱, 웹, 또는 태블릿에서 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]을 사용할 때 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]을 사용하여 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]를 활용할 수 있습니다. 예를 들어, 전자 메일 또는 약속에 대한 정보를 보거나 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 전자 메일 또는 약속을 영업 기회, 거래처나 서비스 케이스 같은 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 레코드에 대한 링크로 연결할 수 있습니다. [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]이 무엇을 제안하는지 자세히 알아보려면, [Dynamics 365 App for Outlook 사용자 가이드](https://go.microsoft.com/fwlink/p/?LinkID=613099)를 참조하십시오.  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]은 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]과 같지 않습니다. [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 기준으로, [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]과 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]을 통합하기 위해 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]와 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)]를 사용하는 것이 권장되는 방법입니다. **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 및 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]를 동일한 사용자가 함께 사용할 때 활동 추적은 지원되지 않습니다.** [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 추가 기능에 대한 정보는 [Dynamics 365 for Outlook 사용자 가이드](https://go.microsoft.com/fwlink/p/?LinkID=524751)를 참조하십시오.  
>   
>  [위임된 사용자](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540)는 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 사용하여 전자 메일을 추적할 수 없습니다. 위임된 사용자에 대해 [폴더 수준 추적 또는 자동 추적](https://www.microsoft.com/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx)을 사용하는 것이 좋습니다.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Dynamics 365 App for Outlook과 Dynamics 365 for Outlook 비교  
 다음 표에서는 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 기능을 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]에 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] ([!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 클라이언트 또는 추가 기능이라고도 함)와 비교합니다.  
  
||||  
|-|-|-|  
|**기능**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|전자 메일에 대한 관련 항목 추적 및 설정|예|예|  
|약속에 대한 관련 항목 추적 및 설정|예|예|  
|연락처에 대한 관련 항목 추적 및 설정|예|예|  
|작업에 대한 관련 항목 추적 및 설정|아니요|예|  
|관련 원클릭 설정|예|아니요|  
|받는 사람 요약 표시|예|아니요|  
|전자 메일/약속에 관련 레코드 요약 표시|예|아니요|  
|공동 작업 대상: [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|예|아니요|  
|[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 데스크톱에서 작동|예|예|  
|Mac용 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]에서 작동|예|아니요|  
|전화기에서 작동|예|아니요|  
|[!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 레코드를 직접 열기 및 만들기|예|예|  
|사용자 지정 양식 및 비즈니스 논리 적용|예|예|  
|오프라인으로 작업|아니요|예|  
|전자 메일 템플릿 적용|예|예|  
|영업 홍보 자료 적용|예|예|  
|참조 문서 적용|예|예|  
|보낸 후 전자 메일을 감시하는 기능|예|아니요|  
|보기 정렬, 필터링, 서식 지정, 그룹화 및 분류|아니요|예|  
|Word 메일 병합 문서 만들기|아니요|예|  
|필드 동기화 제어|아니요|예|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>요구 사항  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 사용하려면 다음이 필요합니다.  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] 또는 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   서버쪽 동기화를 통해 수신 전자 메일 동기화. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][전자 메일, 약속, 연락처 및 작업의 서버쪽 동기화 설정](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   아래 설명과 같이 필요한 권한  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] 기능에 대해 지원되는 구성 및 요구 사항은 설명서를 통해 나열 됩니다. 문서화되지 않은 특정 구성은 지원되지 않는 것으로 간주해야 합니다.  
  
### <a name="required-privileges"></a>필요한 권한  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]은 **Dynamics 365 App for Outlook** 사용 권한을 통해 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 액세스를 제공합니다. 사용자에게 이 권한이 없을 경우 다음 오류 메시지가 나타납니다.  
  
> "이 앱을 사용할 수 있는 권한이 없습니다. 시스템 관리자에게 설정을 업데이트해 줄 것을 요청하십시오."  
  
 사용자는 다음 엔터티에 대한 읽기/쓰기 권한이 있어야 합니다.  
  
 비즈니스 관리 탭:  
  
-   **사서함**  
  
 사용자 지정 탭:  
  
-   **엔터티**  
  
-   **필드**  
  
-   **관계**  
  
-   **시스템 응용 프로그램 메타데이터**  
  
-   **시스템 양식**  
  
-   **사용자 응용 프로그램 메타데이터**  
  
-   **보기**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>보안 역할에 대한 권한 설정  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  **보안 역할**을 클릭합니다.  
  
3.  보안 역할을 선택한 다음 **비즈니스 관리** 탭을 클릭합니다.  
  
4.  **엔터티** 섹션에서 **사서함** 권한 설정을 검토합니다. 보안 역할은 사용자 또는 더 높은 설정을 가져야 합니다.  
  
5.  **개인 정보 관련 권한** 섹션에서 **Dynamics 365 App for Outlook 사용**이 **조직**으로 설정되었는지 확인합니다. 그렇지 않을 경우, **Dynamics 365 App for Outlook 사용**을 클릭하십시오.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Microsoft Exchange에 지원되는 구성  
 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]로 [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] 또는 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] 및 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] 또는 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (On-premises) 중 하이브리드 구성을 포함하여 모든 조합의 앱을 사용할 수 있습니다. 즉, [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]에서 다음 구성 중 어떤 것도 사용할 수 있습니다.  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]를 사용하는 경우 아래 설명에 따라 IFD 인증으로 인증해야 합니다.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>웹에서 Outlook에 지원되는 브라우저  
 다음 브라우저에서 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]과 함께 사용할 수 있습니다.  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] 또는 [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     다음 구성이 지원됩니다.  
  
    -   보호 모드는 **인터넷** 보안 영역에 대해 활성화되어 있습니다. 보호 모드를 사용하려면 IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **인터넷**으로 이동합니다.  
  
    -   보호 모드는 **로컬 인트라넷** 보안 영역에 대해 활성화되어 있습니다. 보호 모드를 사용하려면 IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **로컬 인터넷**으로 이동합니다.  
  
    -   [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] URL은 신뢰할 수 있는 웹 사이트의 **로컬 인트라넷** 보안 영역 목록에 있습니다. IE 10 또는 11에서 **도구** > **인터넷 옵션** > **보안 탭** > **로컬 인트라넷** > **사이트** > **고급**으로 이동합니다.  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]의 [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)](최신 버전)  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]의 [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)](최신 버전)  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)]Mac 또는 OSX용 [!INCLUDE[tn_Safari](../includes/tn-safari.md)](버전 9 또는 버전 10)  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>데스크톱에서 Outlook에 지원되는 운영 체제  
 데스크톱의 경우 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]의 다음 버전에서 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 사용할 수 있습니다.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 및 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] for Mac*  
  
     *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 버전 15.0.847.32 이상이 필요합니다.  
  
### <a name="supported-mobile-devices"></a>지원 모바일 장치  
 다음 휴대폰 및 운영 체제의 모바일 브라우저에서 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]으로 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]를 사용할 수 있습니다.  
  
-   iOS 버전 8, 9 또는 10을 실행하는 [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] 장치.  
  
-   [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4(KitKat), 5.0(Lollipop), 6(Marshmallow), 또는 7(Nougat) 버전의 [!INCLUDE[tn_android](../includes/tn-android.md)] 폰.  
  
-   [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] 또는 [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)] 버전의 [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] 장치.  
  
### <a name="supported-clients-per-feature"></a>기능에 지원되는 클라이언트  
 지원되는 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 기능은 실행 중인 클라이언트에 따라 다릅니다. 다음 표에서 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 및 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]의 각 클라이언트/구성에 지원되는 기능에 대해 요약하고 있습니다.  
  
 ![각 Dynamics 365 App for Outlook 기능에 지원되는 클라이언트](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "각 Dynamics 365 App for Outlook 기능에 지원되는 클라이언트")  
  
 (1) [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]은 [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)], 그리고 [!INCLUDE[tn_chrome](../includes/tn-chrome.md)]을 지원합니다.  
  
 (2) 모바일 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]은 [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat(4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow, [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat을 지원합니다.  
  
 (3) 작성 모드에서 전자 메일을 추적하고 약속을 추적하려면 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 또는 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016이 필요합니다.  
  
 (4) 연락처 추적은 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 및 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 이상에서만 지원됩니다.  
  
 (5) 전자 메일 템플릿, 참조 자료 관리 문서 및 영업 홍보 자료는 Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]에서 지원되지 않습니다.  
  
 (6) [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 이상에서만 지원됩니다.  
  
 (7) 16.0.6741.1000 이상에서만 지원됩니다.  
  
> [!NOTE]
>  현재 태블릿은 지원되지 않습니다(역년 2017 예정).  
  
 [이 블로그에서 지원되는 클라이언트에 대한 자세한 내용을 보려면 Dynamics 365 App for Outlook 지원 매트릭스를 확인하십시오.](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>지원되는 서버  
 [Office 추가 기능을 사용하기 위한 서버 요구 사항](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins)은 [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)], 또는 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]입니다.  
  
### <a name="supported-languages"></a>지원되는 언어  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]은 다음 언어를 지원합니다.  
  
||||  
|-|-|-|  
|불가리아어(불가리아) - 1026|힌디어(인도) - 1081|포르투갈어(포르투갈) - 2070|  
|중국어(중국) - 2052|헝가리어 - 1038|루마니아어 - 1048|  
|중국어(대만) - 1028|인도네시아어 - 1057|러시아어 - 1049|  
|크로아티아어(크로아티아) - 1050|이탈리아어 - 1040|세르비아어 - 2074|  
|체코어(체코 공화국) - 1029|일본어 - 1041|슬로바키아어 - 1051|  
|덴마크어 - 1030|카자흐어 - 1087|슬로베니아어 - 1060|  
|네덜란드어 - 1043|한국어 - 1042|스페인어 - 3082|  
|영어 - 1033|라트비아어 - 1062|스웨덴어 - 1053|  
|에스토니아어 - 1061|리투아니아어 - 1063|태국어 - 1054|  
|핀란드어 - 1035|말레이시아어 - 1086|터키어 - 1055|  
|프랑스어 - 1036|노르웨이어 - 1044|우크라이나어 - 1058|  
|독일어 - 1031|폴란드어 - 1045|베트남어 - 1066|  
|그리스어 - 1032|포르투갈어(브라질) - 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Dynamics 365 App for Outlook 배포  
 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)]을 설치하고 필요한 권한을 설정한 후 일부 또는 모든 사용자에게 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 푸시하거나 사용자가 필요하면 직접 설치하도록 할 수 있습니다.  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)]에 있는 경우 아래 섹션을 참조하십시오. [Dynamics 365 온-프레미스 사용자에게 배포하려면](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>앱을 사용자에게 푸시하려면  
  
1.  **설정** >  **Dynamics 365 App for Outlook**으로 이동하십시오.  
  
2.  **Dynamics 365 App for Outlook 시작** 화면의 **적합한 사용자에 대해 추가** 아래에서(두 번째 이후에 이 화면을 여는 경우 **설정**을 클릭해야 할 수 있음), 사용자가 앱을 **자동으로 가져오도록 하려면 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** 에 자동으로 앱을 추가합니다. 확인란을 선택합니다. 사용자에게 필요한 권한이 있고 전자 메일이 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)]을 통해 동기화된 경우 앱을 푸시하기 위해 추가 작업을 수행할 필요가 없습니다. 예를 들어, 영업 직원 역할에 필요한 권한을 추가한 다음 이 역할을 새 사용자에게 할당하는 경우 앱을 자동으로 가져옵니다.  
  
3.  다음 중 하나를 수행합니다.  
  
    -   모든 적합한 사용자에게 앱을 푸시하려면 **적합한 모든 사용자에 대해 앱 추가**를 클릭합니다.  
  
    -   특정 사용자에게 앱을 푸시하려면 목록에서 이러한 사용자를 선택하고 **Outlook에 앱 추가**를 클릭합니다.  
  
    > [!TIP]
    >  목록에 사용자가 보류 중이거나 추가되지 않은 것으로 나타나는 경우 사용자 옆의 **자세한 정보** 링크를 클릭하여 상태에 대한 자세한 정보를 찾아볼 수 있습니다.  
  
4.  완료되면 **저장**을 클릭합니다.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>사용자가 앱을 직접 설치하도록 하려면  
  
1.  사용자는 **설정** 단추 ![설정 단추](media/mp-ua-r16-settings.png "설정 단추")를 클릭한 다음 **Dynamics 365용 앱**을 클릭합니다.  
  
2.  **Dynamics 365용 앱** 화면의 **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** 아래에서 **[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]에 앱 추가**를 클릭합니다.  
  
> [!NOTE]
>  필요한 경우 사용자가 추가 기능을 사용하지 않도록 설정하거나 제거할 수도 있습니다. 자세한 내용은 [Dynamics 365 App for Outlook 사용자 가이드](https://go.microsoft.com/fwlink/p/?LinkID=613099)를 참조하십시오.  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Dynamics 365 온-프레미스 사용자에게 배포하려면  
 Dynamics 365 On-premises를 사용하는 경우 다음 단계를 수행합니다.  
  
-   Dynamics 365 Server를 인터넷 연결 배포에 맞게 구성합니다. [Microsoft Dynamics 365에 대한 IFD 구성](https://technet.microsoft.com/library/dn609803.aspx)을 참조하십시오.  
  
-   Exchange On-premises에 연결할 경우 OAuth 제공자를 구성하고 클라이언트 앱을 등록합니다. [OAuth를 사용하는 Dynamics 365 응용 프로그램용 Windows Server 2012 R2 구성을 참조하십시오](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>설치 문제 해결  
 사용자가 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]을 설치하는 데 문제가 있는 경우 자신의 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함이 현재 다른 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 조직에 연결되어 있기 때문일 수도 있습니다. [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함(전자 메일 주소)은 한 조직의 약속, 연락처 및 작업만 동기화할 수 있으므로 해당 조직에 속하는 사용자는 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 사서함 한 개의 약속, 연락처 및 작업만 동기화할 수 있습니다.  기본 동기화 조직을 변경하려는 경우 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]에 저장된 설정을 덮어쓸 수 있습니다. 자세한 내용은 [이 KB 문서](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook)를 참조하십시오.  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>사용자 가이드 탐색 및 사용자 교육  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 사용 방법을 알아보려면, [Dynamics 365 App for Outlook 사용자 가이드](https://go.microsoft.com/fwlink/p/?LinkID=613099)를 참조하십시오.  
  
 ![Dynamics 365 App for Outlook 사용자 가이드 페이지](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Dynamics 365 App for Outlook 사용자 가이드 페이지")  
  
## <a name="see-also"></a>참고 항목  
 [Dynamics 365 App for Outlook 사용자 가이드](https://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [이 블로그에서 지원되는 클라이언트에 대한 자세한 내용을 보려면 Dynamics 365 App for Outlook 지원 매트릭스를 확인하십시오.](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [전자 메일, 약속, 연락처 및 작업의 서버 쪽 동기화 설정](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [사용자, 라이선스 및 보안 역할 추가](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [Microsoft Dynamics 365 (online)에 상호 운용 기능 추가](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)