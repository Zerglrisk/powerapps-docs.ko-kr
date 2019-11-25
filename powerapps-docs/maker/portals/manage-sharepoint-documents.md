---
title: 포털에서 SharePoint 문서 관리 | MicrosoftDocs
description: 포털에서 SharePoint 문서를 관리하기 위한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f94dee983d5d2d9cedf417f2843a2c10c46b82c1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757008"
---
# <a name="manage-sharepoint-documents"></a>SharePoint 문서 관리

Common Data Service은 Common Data Service 내에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용할 수 있는 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]와의 통합을 지원합니다. 이제 PowerApps 포털에서는 포털의 엔터티 양식 또는 웹 양식의 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]에서 직접 문서를 업로드하고 표시하는 기능을 지원합니다. 이를 통해 포털 사용자는 포털에서 문서를 보고, 다운로드하고, 추가하고, 삭제할 수 있습니다. 포털 사용자는 문서를 구성하는 하위 폴더를 만들 수도 있습니다.

> [!NOTE]
> - 문서 관리는 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]에서만 작동합니다.
> - 서버 기반 통합을 통해 문서 관리가 지원됩니다.

Common Data Service 내에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용하려면 다음을 수행해야 합니다.

1.  [Dynamics 365의 모델 기반 앱에서 문서 관리 기능 사용](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [PowerApps 포털 관리 센터에서 SharePoint 통합 설정](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [엔터티에 대해 문서 관리 사용](#step-3-enable-document-management-for-entities)

4.  [PowerApps 문서에서 적절한 양식 구성](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [적절한 엔터티 권한을 만들어 적절한 웹 역할에 할당](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>1단계: Dynamics 365의 모델 기반 앱에서 문서 관리 기능 사용

서버 기반 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용하여 Dynamics 365의 모델 기반 앱에서 문서 관리 기능을 활성화해야 합니다. 서버 기반 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 사용하면 Dynamics 365의 모델 기반 앱 및 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]에서 서버 간 연결을 수행할 수 있습니다. 기본 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]사이트 레코드는 포털에서 사용됩니다. Dynamics 365의 모델 기반 앱에서 문서 관리 기능을 활성화하는 방법에 대한 자세한 내용은 [Dynamics 365의 모델 기반 앱에서 SharePoint 온라인을 사용하도록 설정](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online)을 참조하십시오.

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>2단계: PowerApps 포털 관리 센터에서 SharePoint 통합 설정

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 문서 관리 기능을 사용하려면 PowerApps 포털 관리 센터에서 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 활성화해야 합니다.

> [!NOTE]
> 이 작업을 수행하려면 전역 관리자여야 합니다.

1. [PowerApps 포털 관리 센터](admin/admin-overview.md)를 엽니다.

2.  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합 설정** > **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합 활성화**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![SharePoint 통합 활성화](media/enable-sharepoint-integration.png "SharePoint 통합 사용")

3.  확인 창에서 **사용**을 선택합니다. 이렇게 하면 포털이 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]와 통신할 수 있게 됩니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 활성화하는 동안 포털을 다시 시작하고 몇 분 동안 사용할 수 없습니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합이 활성화되면 메시지가 나타납니다.

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합이 활성화되면 다음 작업을 사용할 수 있게 됩니다.

- **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]통합 비활성화**: 포털과의 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 비활성화할 수 있습니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 비활성화하는 동안 포털을 다시 시작하고 몇 분 동안 사용할 수 없습니다. [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합이 비활성화되면 메시지가 나타납니다.

    > [!div class=mx-imgBorder]
    > ![SharePoint 통합 사용 안 함](media/disable-sharepoint-integration.png "SharePoint 통합 사용 안 함")

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합을 활성화하거나 비활성화하면 포털에 대한 [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) 응용 프로그램이 업데이트되고 필요한 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 사용 권한이 각각 추가 또는 제거됩니다. 또한 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 응용 프로그램에서 변경에 대해 동의하도록 리디렉션됩니다. 

> [!div class=mx-imgBorder]
> ![SharePoint 통합 사용 안 함](media/sharepoint-integration-consent.png "SharePoint 통합 사용 안 함")

동의를 제공하지 않는 경우:

- [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합 활성화 또는 비활성화가 완료되지 않고 오류 메시지가 표시됩니다.

- 포털에서 기본 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 로그인이 작동하지 않습니다. 


## <a name="step-3-enable-document-management-for-entities"></a>3단계: 엔터티에 대해 문서 관리 사용
[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]의 엔터티 레코드와 관련된 문서를 저장하려면 엔터티에 대한 문서 관리를 활성화해야 합니다. 엔터티에 대한 문서 관리를 사용하도록 설정하는 방법에 대한 자세한 내용은 [특정 엔터티에 대해 SharePoint 문서 관리 사용](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)을 참조하십시오.

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>4단계: 문서를 표시하도록 적절한 양식 구성

### <a name="powerapps-customization"></a>PowerApps 사용자 지정

문서 관리 기능을 사용할 양식을 식별합니다. 모델 기반 앱 양식 편집기를 사용하여 양식을 편집하고 여기에 하위 표를 추가해야 합니다. 하위 표는 양식에 섹션을 추가하여 포탈 내에서 문서로 작업할 수 있습니다. 이 기능이 작동하려면 하위 표에서 다음 속성을 설정해야 합니다.

- **데이터 원본** 아래의 **엔터티** 목록에서 **문서 위치**를 선택합니다.

- **데이터 원본** 아래의 **기본 보기** 목록에서 **활성 문서 위치**를 선택합니다.

요구 사항에 따라 이름과 레이블을 지정할 수 있습니다. 하위 표가 추가되고 구성되면 양식을 저장하고 게시합니다.

> [!NOTE]
> 양식을 편집하는 엔터티에 대해 문서 관리를 사용하도록 설정해야 합니다. 추가 정보: [엔터티에 대해 문서 관리 사용](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps 포털 구성

엔터티 양식이나 웹 양식에 필요한 표준 구성 외에, 다음 속성을 설정하여 문서 관리를 사용하도록 설정해야 합니다.

- **엔터티 이름** 및 **양식 이름**: 각각 이전 단계에서 사용자 지정된 엔터티 및 양식 이름을 입력합니다.

- 양식에서 **엔터티 권한 사용** 확인란을 선택하여 사용자가 문서를 읽을 수 있도록 합니다.

- 문서 업로드를 허용하려면 **모드**를 **편집**으로 설정합니다.

> [!NOTE]
> 문서를 업로드하려면 상위 엔터티 레코드가 있어야 합니다. 삽입할 모드를 설정하면 양식이 전송될 때까지 상위 엔터티 레코드가 만들어지지 않기 때문에 문서 업로드가 작동하지 않습니다.

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>5단계: 적절한 엔터티 권한을 만들어 적절한 웹 역할에 할당

문서를 보고 업로드하는 데 필요한 액세스 권한을 설정하려면 두 엔터티 권한 레코드가 필요합니다.

- 엔터티 또는 웹 양식의 엔터티에 대한 사용 권한: 
    - 이전에 구성한 엔터티 양식 또는 웹 양식의 엔터티로 **엔터티 이름**을 지정하는 **엔터티 권한** 레코드를 만듭니다. 
    - 원하는 양식의 동작에 적합한 **범위** 및 범위 관계를 선택합니다. 
    - 문서에 대한 읽기 액세스를 허용하고 선택적으로 **쓰기** 권한을 활성화하여 문서 업로드를 허용하려면 **읽기** 및 **다른 레코드에 추가** 권한을 활성화합니다. 다음 단계에서 채워질 것 이므로 지금은 **하위 엔터티 권한** 섹션을 무시합니다.
- **상위 범위**가 있는 **문서 위치**에서 이전 권한 레코드를 참조하는 권한: 
    - **범위**를 **상위**로 설정한 상태에서 **엔터티 범위**를 **문서 위치** 엔터티로 지정하는 **엔터티 권한** 레코드를 만듭니다. 
    - 이전 단계에서 만든 엔터티 권한 레코드에 대한 상위 엔터티 권한을 선택합니다. 
    - 권한  
        - 문서에 대한 읽기 액세스를 허용하는 최소 권한은 **읽기**, **만들기** 및 **추가**입니다. 
        - 문서 업로드 액세스에 대한 **쓰기** 권한을 포함합니다. 
        - 문서 삭제를 허용하려면 **삭제**를 포함합니다.

> [!NOTE]
> **문서 위치** 엔터티에 대한 해당 하위 엔터티 권한은 문서를 표시해야 하는 엔터티 또는 웹 양식의 엔터티에 있는 상위 엔터티 권한 레코드의 각 인스턴스에 대해 만들어야 합니다.

## <a name="configure-file-upload-size"></a>파일 업로드 크기 구성

기본적으로 이 파일 크기는 10MB로 설정됩니다. 그러나 사이트 설정 `SharePoint/MaxUploadSize`을 사용하여 파일 크기를 최대 50MB까지 구성할 수 있습니다.

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>서비스 케이스 엔터티 양식에 문서 관리를 사용하도록 설정하는 샘플 구성

아래 예제는 Dynamics 365 Customer Service 애플리케이션이 필수 구성 요소인 서비스 케이스 엔터티를 사용하는 구성을 보여줍니다. 이 샘플은 서비스 케이스 엔터티를 사용하지만 위에서 언급한 단계를 설명하기 위한 것이며 다른 사용자 지정 엔터티나 SharePoint에서 문서 관리를 지원하는 모든 Common Data Service 엔터티를 뒤에 사용할 수 있습니다. 

1.  [1단계](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)의 지침에 따라 Dynamics 365의 모델 기반 앱 및 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 통합에 대해 서버 기반 구성이 완전한지 확인합니다.

2.  [2단계](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)의 지침에 따라 포털에 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]와 통합할 권한이 있는지 확인합니다. 

3.  [3단계](#step-3-enable-document-management-for-entities)의 지침에 따라 서비스 케이스 엔터티에 대해 문서 관리를 사용하도록 설정되었는지 확인합니다.

4.  [4단계](#step-4-configure-the-appropriate-form-to-display-documents)의 지침에 따라 다음 구성을 수행합니다.

    - Dynamics 365의 모델 중심 앱 사용자 지정

        a. **설정** > **사용자 지정** > **시스템 사용자 지정**으로 이동합니다. 

        b. **기본 솔루션**에서 **서비스 케이스** 엔터티 > **양식**으로 이동합니다. 
    
        c. 양식 편집기에서 **웹 - 서비스 케이스 편집**을 엽니다.

         > [!div class=mx-imgBorder]
         > ![웹 - 서비스 케이스 양식 편집](media/web-edit-case-form.png "웹 - 서비스 케이스 양식 편집")
    
        d. 양식에서 **만든 날짜** 필드를 선택하고 **삽입** 탭에서 **하위 표**를 선택합니다.

         > [!div class=mx-imgBorder]
         > ![웹에 하위 표 추가 - 서비스 케이스 양식 편집](media/add-sub-grid.png "웹에 하위 표 추가 - 서비스 케이스 양식 편집")
    
        e. **속성 설정** 대화 상자에서 다음 속성을 설정하고 **확인**을 선택합니다.

         - **이름** (모든 이름이 될 수 있음): CaseDocuments 
    
         - **레이블** (레이블 이름이 될 수 있음): 서비스 케이스 문서 
      
         - **엔터티**: 문서 위치 
    
         - **기본 보기**: 활성 문서 위치

         > [!div class=mx-imgBorder]
         > ![하위 표 속성](media/sub-grid-properties.png "하위 표 속성")

        f. 양식 편집기에서 **저장**을 선택한 다음 **게시**를 선택합니다.

    - PowerApps 포털 구성

        a. **포털** > **엔터티 양식**으로 이동합니다.
    
        b. **고객 서비스 - 서비스 케이스 편집** 엔터티 양식을 찾아서 엽니다.
    
        c. 다음 속성이 설정되었는지 검토하고 확인합니다.
    
         - **엔터티 이름**: 서비스 케이스(incident)
    
         - **양식 이름**: 웹 - 서비스 케이스 편집
    
         - **모드**: 편집
    
         - **엔터티 권한**: 사용
    
         > [!div class=mx-imgBorder]
         > ![Customer Service - 서비스 케이스 양식 편집](media/customer-service-edit-case-form.png "Customer Service - 서비스 케이스 양식 편집")
    
        d. 양식을 변경한 경우 **저장**을 선택합니다.

5. [5단계](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
)를 수행하여 엔터티 권한이 사용자에게 부여되는지 확인합니다.

   1. 사용자에 연결된 **웹 역할** 레코드로 이동합니다. 이 샘플에서는 사용자에게 관리자 웹 역할이 있다고 가정합니다.

   2. **고객 서비스 - 연락처가 고객인 서비스 케이스**의 이름에 따라 엔터티 권한 레코드가 있는지 확인합니다. 

      > [!NOTE]
      > 웹 역할에 이 엔터티 권한이 추가되어 있는지 확인합니다. 사용자가 이미 관리자인 경우 위의 엔터티 권한을 명시적으로 할당하지 않아도 됩니다.

   3. 새 엔터티 권한을 만들고, 다음 세부 정보를 입력하고, **저장**을 선택합니다.

    - **이름** (모든 이름이 될 수 있음): 고객 서비스 - 관련 문서

    - **엔터티 이름**: 문서 위치
        
    - **범위**: 상위
        
    - **상위 엔터티 권한**: 연락처의 거래처가 고객인 서비스 케이스
        
    - **상위 관계**: incident_SharePointDocumentLocations
        
    - **권한**: 읽기, 만들기, 추가, 쓰기, 삭제

      > [!div class=mx-imgBorder]
      > ![Customer Service 엔터티 권한](media/customer-service-entity-permission.png "Customer Service 엔터티 권한")
  
   4. 포털에 로그인하여 서비스 케이스 엔터티에 대해 문서 관리가 사용하도록 설정되었는지 확인합니다.

      a. **지원** 페이지로 이동합니다.

      > [!div class=mx-imgBorder]
      > ![포털 지원 페이지](media/portal-support-page.png "포털 지원 페이지")

      b. 목록에서 기존 서비스 케이스 레코드를 클릭합니다. 페이지의 **서비스 케이스 문서** 섹션으로 이동하여 추가된 문서 목록을 확인합니다.

      > [!div class=mx-imgBorder]
      > ![서비스 케이스 문서](media/case-document.png "서비스 케이스 문서")

