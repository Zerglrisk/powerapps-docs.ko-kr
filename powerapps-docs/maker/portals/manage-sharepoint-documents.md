---
title: 포털에서 SharePoint 문서 관리 | MicrosoftDocs
description: 포털에서 SharePoint 문서를 관리 하는 방법에 대 한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ab51a2b1a309921e32949a806adb4a7bf3273ccf
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974693"
---
# <a name="manage-sharepoint-documents"></a>SharePoint 문서 관리

Common Data Service는 Common Data Service 내에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용할 수 있도록 하는 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]와의 통합을 지원 합니다. PowerApps 포털에서 포털의 엔터티 양식 또는 web form에서 직접 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 문서를 업로드 하 고 표시할 수 있습니다. 이를 통해 포털 사용자는 포털에서 문서를 보고, 다운로드 하 고, 추가 하 고, 삭제할 수 있습니다. 포털 사용자는 하위 폴더를 만들어 문서를 구성할 수도 있습니다.

> [!NOTE]
> - 문서 관리는 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]에서만 작동 합니다.
> - 서버 기반 통합에서는 문서 관리가 지원 됩니다.

Common Data Service 내에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용 하려면 다음을 수행 해야 합니다.

1.  [Dynamics 365의 모델 기반 앱에서 문서 관리 기능 사용](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [PowerApps 포털 관리 센터에서 SharePoint 통합 설정](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [엔터티에 대해 문서 관리 사용](#step-3-enable-document-management-for-entities)

4.  [PowerApps 문서에서 적절 한 양식 구성](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [적절 한 엔터티 권한을 만들고 적절 한 웹 역할에 할당 합니다.](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>1 단계: Dynamics 365의 모델 기반 앱에서 문서 관리 기능 사용

서버 기반 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하 여 Dynamics 365의 모델 기반 앱에서 문서 관리 기능을 사용 하도록 설정 해야 합니다. 서버 기반 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하면 Dynamics 365 및 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]에서 모델 기반 앱을 사용 하 여 서버 간 연결을 수행할 수 있습니다. 포털에서 기본 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 사이트 레코드를 사용 합니다. Dynamics 365의 모델 기반 앱에서 문서 관리 기능을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [dynamics 365에서 모델 기반 앱 설정을 참조 하 여 SharePoint Online을 사용](https://docs.microsoft.com/en-us/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online)합니다.

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>2 단계: PowerApps 포털 관리 센터에서 SharePoint 통합 설정

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용 하려면 PowerApps 포털 관리 센터에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하도록 설정 해야 합니다.

> [!NOTE]
> 이 작업을 수행 하려면 전역 관리자 여야 합니다.

1. [PowerApps 포털 관리 센터](admin/admin-overview.md)를 엽니다.

2.  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합 설정** 으로 이동 하 > **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하도록**설정 합니다.

    > [!div class=mx-imgBorder]
    > Sharepoint ![통합]사용(media/enable-sharepoint-integration.png "sharepoint 통합") 사용

3.  확인 창에서 **사용** 을 선택 합니다. 이렇게 하면 포털이 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]와 통신할 수 있습니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없게 됩니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합이 사용 하도록 설정 된 경우 메시지가 표시 됩니다.

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하도록 설정 하면 다음 작업을 사용할 수 있게 됩니다.

- **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합 사용 안 함**: 포털에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하지 않도록 설정할 수 있습니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하지 않도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없게 됩니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하지 않도록 설정 하면 메시지가 표시 됩니다.

    > [!div class=mx-imgBorder]
    > Sharepoint ![통합]사용 안 함(media/disable-sharepoint-integration.png "sharepoint 통합") 사용 안 함

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하거나 사용 하지 않도록 설정 하면 포털에 대 한 [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) 응용 프로그램을 업데이트 하 고 필요한 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 권한을 각각 추가 하거나 제거 합니다. 또한 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 응용 프로그램에서 변경 내용을 적용 하는 데 대 한 동의를 제공 하도록 리디렉션됩니다. 

> [!div class=mx-imgBorder]
> Sharepoint ![통합]사용 안 함(media/sharepoint-integration-consent.png "sharepoint 통합") 사용 안 함

사용자의 동의를 제공 하지 않는 경우:

- [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용 하거나 사용 하지 않도록 설정 하는 것은 완료 되지 않으며 오류 메시지가 표시 됩니다.

- 포털에서 기본 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 로그인이 작동 하지 않습니다. 


## <a name="step-3-enable-document-management-for-entities"></a>3 단계: 엔터티에 문서 관리 사용
엔터티에 대 한 문서 관리를 사용 하도록 설정 하 여 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]에서 엔터티 레코드와 관련 된 문서를 저장 해야 합니다. 엔터티에 대해 문서 관리를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [특정 엔터티에 대해 SharePoint 문서 관리 사용](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)을 참조 하세요.

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>4 단계: 문서를 표시 하는 적절 한 양식 구성

### <a name="powerapps-customization"></a>PowerApps 사용자 지정

문서 관리 기능을 사용 하려는 양식을 식별 합니다. 모델 기반 앱 양식 편집기를 사용 하 여 폼을 편집 하 고 subgrid를 추가 해야 합니다. Subgrid는 포털 내에서 문서를 사용할 수 있도록 하는 섹션을 폼에 추가 합니다. 이 기능이 작동 하려면 subgrid에서 다음 속성을 설정 해야 합니다.

- **데이터 원본**아래의 **엔터티** 목록에서 **문서 위치** 를 선택 합니다.

- **데이터 원본**아래의 **기본 보기** 목록에서 **활성 문서 위치** 를 선택 합니다.

요구 사항에 따라 이름 및 레이블을 지정할 수 있습니다. Subgrid가 추가 되 고 구성 되 면 양식을 저장 하 고 게시 합니다.

> [!NOTE]
> 양식을 편집할 엔터티에 대해 문서 관리를 사용 하도록 설정 해야 합니다. 추가 정보: [엔터티에 문서 관리 사용](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps 포털 구성

엔터티 양식이 나 웹 폼에 필요한 표준 구성과는 별도로 다음 속성을 설정 하 여 문서 관리를 사용 하도록 설정 해야 합니다.

- **엔터티 이름** 및 **폼 이름**: 이전 단계에서 사용자 지정 된 엔터티 및 양식 이름을 각각 입력 합니다.

- 사용자가 문서를 읽을 수 있도록 하려면 폼에서 **엔터티 권한 사용** 확인란을 선택 합니다.

- 문서 업로드를 허용 하도록 **모드** 를 **편집** 으로 설정 합니다.

> [!NOTE]
> 문서를 업로드 하려면 부모 엔터티 레코드가 있어야 합니다. 모드를 삽입으로 설정 하는 경우 양식이 제출 될 때까지 부모 엔터티 레코드가 만들어지지 않으므로 문서 업로드가 작동 하지 않습니다.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>5 단계: 적절 한 엔터티 권한 만들기 및 적절 한 웹 역할에 할당

문서를 보고 업로드 하는 데 필요한 액세스 권한을 설정 하려면 두 개의 엔터티 권한 레코드가 필요 합니다.

- 엔터티 또는 web form의 엔터티에 대 한 사용 권한: 
    - 엔터티 **이름을** 이전에 구성한 엔터티 양식 또는 web form의 엔터티로 지정 하는 **엔터티 권한** 레코드를 만듭니다. 
    - 원하는 폼 동작에 적합 한 **범위** 및 범위 관계를 선택 합니다. 
    - 문서에 대 한 읽기 액세스를 허용 하 고 필요에 따라 **쓰기** 권한을 설정 하 여 문서 업로드를 허용 하려면 **읽기** 및 **추가** 권한을 사용 하도록 설정 합니다. 다음 단계로 채워질 수 있으므로 지금은 **자식 엔터티 권한** 섹션을 무시 합니다.
- 이전 권한 레코드를 참조 하는 **부모 범위가** 있는 **문서 위치** 에 대 한 사용 권한: 
    - **범위가** **Parent**로 설정 된 **문서 위치** 엔터티로 **엔터티 이름을** 지정 하 여 **엔터티 권한** 레코드를 만듭니다. 
    - 이전 단계에서 만든 엔터티 권한 레코드에 대 한 부모 엔터티 권한을 선택 합니다. 
    - 권한 
        - 문서에 대 한 읽기 액세스를 허용 하는 최소 권한은 **읽기**, **만들기**및 **추가**입니다. 
        - 문서 업로드 액세스에 대 한 **쓰기** 권한을 포함 합니다. 
        - 문서 삭제를 허용 하려면 **Delete** 를 포함 합니다.

> [!NOTE]
> 문서를 표시 해야 하는 엔터티 또는 웹 폼의 엔터티에 있는 부모 엔터티 권한 레코드의 각 인스턴스에 대해 **문서 위치** 엔터티에 대 한 해당 자식 엔터티 권한을 만들어야 합니다.

## <a name="configure-file-upload-size"></a>파일 업로드 크기 구성

기본적으로 파일 크기는 10mb로 설정 됩니다. 그러나 `SharePoint/MaxUploadSize`사이트 설정을 사용 하 여 파일 크기를 최대 50 MB로 구성할 수 있습니다.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>사례 엔터티 양식에서 문서 관리를 사용 하도록 설정 하는 샘플 구성

아래 예제에서는 Dynamics 365 고객 서비스 응용 프로그램이 필수 구성 요소인 사례 엔터티를 사용 하는 구성을 보여 줍니다. 이 샘플에서는 Case 엔터티를 사용 하지만 위에서 언급 한 단계를 보여 주지만 SharePoint에서 문서 관리를 지 원하는 다른 사용자 지정 엔터티 또는 Common Data Service 엔터티를 따를 수 있습니다. 

1.  [1 단계의](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) 지침에 따라 Dynamics 365 및 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합에서 모델 기반 앱에 대 한 서버 기반 구성이 완료 되었는지 확인 합니다.

2.  [2 단계의](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center) 지침에 따라 포털에 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]와 통합할 수 있는 권한이 있는지 확인 합니다. 

3.  [3 단계의](#step-3-enable-document-management-for-entities) 지침에 따라 사례 엔터티에 대해 문서 관리가 사용 하도록 설정 되어 있는지 확인 합니다.

4.  다음 구성을 사용 하 여 [4 단계](#step-4-configure-the-appropriate-form-to-display-documents) 의 지침을 따릅니다.

    - Dynamics 365 사용자 지정의 모델 기반 앱

        a. **설정** > **사용자 지정** 으로 이동 하 > **시스템을 사용자 지정**합니다. 

        b. **기본 솔루션**에서 **Case** 엔터티 > **양식**으로 이동 합니다. 
    
        c. 폼 편집기에서 **웹 – 편집 사례** 를 엽니다.

         > [!div class=mx-imgBorder]
         > ![웹 편집 사례 양식](media/web-edit-case-form.png "웹 편집 사례 양식")
    
        d. 폼에서 **만든 설정** 필드를 선택 하 고 **삽입** 탭에서 **하위 그리드**를 선택 합니다.

         > [!div class=mx-imgBorder]
         > ![Subgrid을 웹 편집 사례 폼에 추가]하 여(media/add-sub-grid.png "웹 편집 사례 폼에 subgrid 추가")
    
        e. **설정 속성** 대화 상자에서 다음 속성을 설정 하 고 **확인**을 선택 합니다.

         - **이름** (모든 이름일 수 있음): CaseDocuments 
    
         - **레이블** (레이블 이름일 수 있음): 사례 문서 
      
         - **엔터티**: 문서 위치 
    
         - **기본 보기**: 활성 문서 위치

         > [!div class=mx-imgBorder]
         > ![Subgrid properties](media/sub-grid-properties.png "Subgrid 속성")

        350. 폼 편집기에서 **저장** 을 선택한 다음 **게시**를 선택 합니다.

    - PowerApps 포털 구성

        a. **포털** > **엔터티 양식**으로 이동 합니다.
    
        b. **고객 서비스-사례 엔터티 편집** 을 찾아 엽니다.
    
        c. 다음 속성이 설정 되었는지 확인 하 고 확인 합니다.
    
         - **엔터티 이름**: Case (인시던트)
    
         - **양식 이름**: 웹-대/소문자 편집
    
         - **모드**: 편집
    
         - **엔터티 권한**: 사용
    
         > [!div class=mx-imgBorder]
         > ![고객 서비스-대/소문자 편집 폼](media/customer-service-edit-case-form.png "고객 서비스-편집 사례 양식")
    
        d. 양식을 변경한 경우 **저장**을 선택 합니다.

5. [5 단계](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) 에 따라 사용자에 게 엔터티 사용 권한이 부여 되었는지 확인 합니다.

   1. 사용자와 연결 된 **웹 역할** 레코드로 이동 합니다. 이 샘플에서는 사용자에 게 관리자 웹 역할이 있다고 가정 합니다.

   2. **담당자가 customer 인 고객 서비스 케이스**이름으로 엔터티 권한 레코드가 존재 하는지 확인 합니다. 

      > [!NOTE]
      > 웹 역할에이 엔터티 권한이 추가 되어 있는지 확인 합니다. 사용자가 이미 관리자 인 경우에는 위의 엔터티 권한을 명시적으로 할당할 필요가 없습니다.

   3. 새 엔터티 권한을 만들고, 다음 세부 정보를 입력 하 고, **저장**을 선택 합니다.

    - **이름** (모든 이름일 수 있음): 고객 서비스 관련 문서

    - **엔터티 이름**: 문서 위치
        
    - **범위**: 부모
        
    - **부모 엔터티 권한**: 고객 서비스-연락처가 Customer 인 경우
        
    - **부모 관계**: incident_SharePointDocumentLocations
        
    - **권한**: 읽기, 만들기, 추가, 쓰기, 삭제

      > [!div class=mx-imgBorder]
      > ![고객 서비스 엔터티 권한](media/customer-service-entity-permission.png "고객 서비스 엔터티 권한")
  
   4. 포털에 로그인 하 여 사례 엔터티에 대해 문서 관리를 사용할 수 있도록 합니다.

      a. **지원** 페이지로 이동 합니다.

      > [!div class=mx-imgBorder]
      > ![포털 지원 페이지](media/portal-support-page.png "포털 지원 페이지")

      b. 목록에서 기존 사례 레코드를 클릭 합니다. 페이지의 **사례 문서** 섹션으로 이동 하 여 추가 된 문서 목록을 확인 합니다.

      > [!div class=mx-imgBorder]
      > ![사례 문서](media/case-document.png "사례 문서")

