---
title: Power Apps에서 모델 기반 앱 공유 | Microsoft Docs
description: 모델 기반 앱을 공유하는 방법 알아보기
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 11/18/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f11eebcb220ff877b0cd750f2d94338cadc5ceea
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884019"
---
# <a name="share-a-model-driven-app-with-power-apps"></a>Power Apps에서 모델 기반 앱 공유

[!INCLUDE [powerapps](../../includes/powerapps.md)] 앱은 역할 기반 보안을 공유에 사용합니다. 역할 기반 보안의 기본 개념은 앱 내에서 수행할 수 있는 작업 집합을 정의하는 권한이 보안 역할에 포함되어 있다는 것입니다. 모든 앱 사용자가 하나 이상의 사용자 지정 또는 미리 정의된 역할에 할당되어야 합니다. 또는 팀에 역할을 할당할 수도 있습니다. 사용자 또는 팀이 이러한 역할 중 하나에 할당되면 사용자 또는 팀 구성원은 해당 역할에 연결된 권한 집합이 부여됩니다. 

## <a name="prerequisites"></a>필수 구성 요소
앱을 공유 하려면 [!INCLUDE [powerapps](../../includes/powerapps.md)]환경 관리자 또는 시스템 관리자 역할이 있어야 합니다. 

## <a name="share-your-app-for-basic-use"></a>기본 사용을 위한 앱 공유
앱 사용자가 환경 내에서 앱을 실행하고 자신이 소유한 레코드에 대한 공통 작업을 수행할 수 있도록 권한을 추가하려면 **Common Data Service 사용자** 보안 역할을 사용합니다.
1.  [Power Apps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 사이트에서 **앱**을 선택하고, 공유하려는 모델 기반 앱 옆에서 **…** 를 선택한 다음 **공유**를 선택합니다. 
    > [!IMPORTANT]
    > 모델 기반 앱을 공유하는 단계는 캔버스 앱과 다릅니다. 캔버스 앱을 공유하는 단계는 [Power Apps에서 캔버스 앱 공유](../canvas-apps/share-app.md)를 참조하세요. 

2.  **보안 역할에 사용자 할당** 아래에서 **보안 사용자**를 선택합니다.
3.  활성화된 사용자 목록에서 앱에 대한 액세스 권한을 부여할 사용자를 선택한 다음 명령 모음에서 **역할 관리**를 선택합니다. 
4.  **사용자 역할 관리** 대화 상자에서 **Common Data Service 사용자** 보안 역할을 선택한 다음 **확인**을 선택합니다. 

    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/select-common-data-service-user.png "Select Common Data Service User")

5. [앱에 보안 역할 추가](#add-security-roles-to-the-app)
6. [앱에 대한 링크 공유](#share-the-link-to-your-app)

Common Data Service 사용자 보안 역할이 있는 사용자는 이제 앱에 액세스할 수 있습니다. 

## <a name="share-a-model-driven-app-for-specific-use"></a>특정 용도를 위해 모델 기반 앱 공유
이 섹션에서는 각각 앱 사용자에게 필요한 두 가지 보안 역할을 사용하여 모델 기반 앱을 공유하는 작업을 수행합니다. 다음 방법에 대해 설명합니다.
- 사용자 지정 보안 역할 만들기
- 사용자 지정 보안 역할에 사용자 할당
- 앱에 보안 역할 할당

### <a name="tutorial-overview"></a>자습서 개요 
이 섹션은 개와 고양이를 서비스하는 애완 동물 사업체인 Contoso사의 경우를 중심으로 설명합니다. 애완 동물 미용 사업을 추적하기 위한 사용자 지정 엔터티가 포함된 앱이 이미 만들어져 게시되었습니다. 이제 앱은 애완 동물 미용 직원이 사용할 수 있도록 공유되어야 합니다. 앱을 공유하려면 관리자나 앱 메이커가 사용자와 앱에 하나 이상의 보안 역할을 할당합니다. 

### <a name="create-or-configure-a-security-role"></a>보안 역할 만들기 또는 구성
[!INCLUDE [powerapps](../../includes/powerapps.md)] 환경에는 앱을 사용하는 데 필요한 비즈니스 데이터의 최소량에 대한 액세스를 제공하는 최상의 목표와 일치하도록 정의된 액세스 수준을 가진 공통의 사용자 작업을 반영하는 [미리 정의된 보안 역할](#about-predefined-security-roles)이 포함되어 있습니다. Contoso 애완 동물 미용 앱은 사용자 지정 엔터티를 기반으로 한다는 점을 기억해야 합니다. 엔터티는 사용자 지정이기 때문에 사용자가 작업을 할 수 있으려면 먼저 권한을 명시적으로 지정해야 합니다. 이렇게 하려면 다음 중 하나를 선택할 수 있습니다.
- 기존에 미리 정의된 보안 역할을 확장하여 사용자 지정 엔터티를 기반으로 하는 레코드에 대한 권한을 포함합니다. 
- 앱 사용자의 권한을 관리할 목적으로 사용자 지정 보안 역할을 만듭니다. 

애완 동물 미용 레코드를 유지 관리하는 환경은 Contoso 사업이 운영되는 다른 앱에도 사용되므로 애완 동물 미용 앱에 특정한 사용자 지정 보안 역할이 만들어집니다. 또한 두 가지 다른 액세스 권한 집합이 필요합니다.
- 애완 동물 미용 기술자는 보안 역할에 읽기, 쓰기 및 추가 권한이 있도록 다른 레코드만 읽고 업데이트하고 첨부해야 합니다. 
- 애완 동물 미용 스케줄러에는 애완 동물 미용 기술자가 가지고 있는 모든 권한이 필요하며 이 기능을 통해 생성, 추가, 삭제 및 공유가 가능하므로 보안 역할에는 만들기, 읽기, 쓰기, 추가, 삭제, 할당, 추가 및 공유 권한이 부여됩니다.

액세스 및 범위 권한에 대한 자세한 내용은 [보안 역할](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)을 참조하십시오.

### <a name="create-a-custom-security-role"></a>사용자 지정 보안 역할 만들기
1. [!INCLUDE [powerapps](../../includes/powerapps.md)] 사이트에서 **앱**을 선택하고, 공유하려는 모델 기반 앱 옆에서 **…** 를 선택한 다음 **공유**를 선택합니다.

2. **이 앱 공유** 대화 상자의 **보안 역할 만들기**에서 **보안 설정**을 선택합니다.

3. **모든 역할** 페이지에서 **새로 만들기**를 선택합니다.  

4. 보안 역할 디자이너에서 읽기, 쓰기 또는 삭제와 같은 작업 및 해당 작업을 수행할 범위를 선택합니다. 범위는 사용자가 특정 작업을 수행할 수 있는 환경 계층 구조 내에서의 깊이 또는 높은 정도를 결정합니다. **역할 이름** 상자에 *애완 동물 미용 기술자*를 입력합니다.

5. **사용자 지정 엔터티** 탭을 선택한 다음 원하는 사용자 지정 엔터티를 찾습니다. 이 예에서는 **애완 동물**이라는 사용자 지정 엔터티가 사용됩니다. 

6. **애완 동물** 행에서 조직 범위 전역 ![조직 전역 범위](media/share-model-driven-app/organizational-scope-privilege.png) 를 선택하기 전까지  **읽기, 쓰기, 추가** 권한 각각을 네 번 선택합니다.

   > [!div class="mx-imgBorder"] 
   > ![새 보안 역할.](media/share-model-driven-app/custom-security-role.png)

7. 애완 동물 미용 앱에도 계정 엔터티와의 관계가 있으므로 **핵심 레코드** 탭을 선택하고 **거래처** 행에서 조직 범위 전역까지 ![조직 전역 범위](media/share-model-driven-app/organizational-scope-privilege.png)가 선택될 때까지 네 번 **읽기**를 선택합니다. 

8. **사용자 지정** 탭을 선택한 다음 권한 목록에서 조직 범위 ![조직 전역 범위](media/share-model-driven-app/organizational-scope-privilege.png)가 선택되도록 **모델 기반 앱** 옆에 있는 **읽기** 권한을 선택합니다.

9. **저장 후 닫기**를 선택합니다. 

10. 보안 역할 디자이너에서 **역할 이름** 상자에 *애완 동물 미용 스케줄러*를 입력합니다. 

11. **사용자 지정 엔터티** 탭을 선택한 다음 **애완 동물** 엔터티를 찾습니다. 

12. **애완 동물** 행에서 조직 범위 전역 ![조직 전역 범위](media/share-model-driven-app/organizational-scope-privilege.png) 를 선택하기 전까지  **만들기, 읽기, 쓰기, 삭제, 추가, 다른 레코드에 추가, 할당, 공유** 권한 각각을 네 번 선택합니다.

13. 애완 동물 미용 앱에도 계정 엔터티와의 관계가 있고 스케줄러는 거래처 레코드를 만들고 수정할 수 있어야 하므로 **핵심 레코드** 탭을 선택하고 **거래처** 행에서 조직 범위 전역까지 ![조직 전역 범위](media/share-model-driven-app/organizational-scope-privilege.png)가 선택될 때까지 네 번 다음 각 권한을 선택합니다. 
    **만들기, 읽기, 쓰기, 삭제, 추가, 다른 레코드에 추가, 할당, 공유**

14. **저장 후 닫기**를 선택합니다.

### <a name="assign-security-roles-to-users"></a>사용자에게 보안 역할 할당
보안 역할은 액세스 수준 및 권한 집합을 통해 데이터에 대한 사용자의 액세스를 제어합니다. 특정 보안 역할에 포함된 액세스 수준과 권한의 조합은 사용자의 데이터 보기 및 사용자와 해당 데이터의 상호 작용에 대한 제한을 설정합니다.

#### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>애완 동물 미용 기술자에게 보안 역할 할당
1. **이 앱 공유** 대화 상자의 **보안 역할에 사용자 할당**에서 **보안 사용자**을 선택합니다.
2. 표시되는 목록에서 애완 동물 미용사인 사용자를 선택한 다음 명령 모음에서 **역할 관리**를 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![역할 관리](media/share-model-driven-app/select-users-for-security-roles.png)

3. **사용자 역할 관리** 대화 상자에서 전에 만든 **애완 동물 미용 기술자** 보안 역할을 선택한 다음 **확인**을 선택합니다.

#### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>애완 동물 미용 스케줄러에게 보안 역할 할당
1. **이 앱 공유** 대화 상자의 **보안 역할을 사용자 할당**에서 **보안 사용자**을 선택합니다.
2. 표시되는 목록에서 애완 동물 미용 스케줄러를 선택합니다.
3. **역할 관리**를 선택합니다.
4. **사용자 역할 관리** 대화 상자에서 전에 만든 **애완 동물 미용 스케줄러** 보안 역할을 선택한 다음 **확인**을 선택합니다.


## <a name="add-security-roles-to-the-app"></a>앱에 보안 역할 추가
앱에 하나 이상의 보안 역할을 할당해야 합니다. 사용자는 할당된 보안 역할에 따라 앱에 대한 액세스를 갖게 됩니다.
1. **이 앱 공유** 대화 상자의 **앱에 보안 역할 추가**에서 **내 앱**을 선택합니다.
2. 앱의 앱 타일의 오른쪽 아래에서 **추가 옵션(...)** 을 선택한 다음 **역할 관리**를 선택합니다.

    ![앱에 대한 역할 관리](media/share-model-driven-app/manage-roles.png)

4. **역할** 섹션에서 모든 보안 역할 또는 선택한 역할에 앱에 대해 액세스를 부여할지 여부를 선택할 수 있습니다. 기본 앱 액세스의 경우 **Common Data Service 사용자** 보안 역할을 선택합니다. 보다 구체적인 액세스를 위해 다른 표준, 또는 사용자 지정 또는 사용자 지정된 보안 역할을 선택하십시오. 예를 들어 이 섹션의 앞부분에서 만든 **애완 동물 미용 스케줄러**와 **애완 동물 미용 기술자** 역할을 선택합니다. 

    > [!div class="mx-imgBorder"] 
    > ![앱에 대한 보안 역할 선택](media/share-model-driven-app/app-security-roles.png)

5. **저장**을 선택합니다. 
 

    > [!IMPORTANT]
    > **모델 기반 앱**에 대한 **만들기** 또는 **쓰기** 권한이 부여된 사용자는 앱에 액세스할 수 있는 역할에 속하지 않아도 환경의 모든 앱에 액세스할 수 있습니다.
    > ![모델 기반 앱 만들기 및 쓰기 권한](media/app-access-cds.png)

## <a name="share-the-link-to-your-app"></a>앱에 대한 링크 공유
1. **이 앱 공유** 대화 상자에서 **사용자와 직접 앱에 대한 링크 공유**에서 표시 되는 URL을 복사합니다.
   > [!div class="mx-imgBorder"] 
   > ![링크 공유](media/share-model-driven-app/share-model-driven-url.png)

2. **닫기**를 선택합니다.
3. 사용자가 SharePoint 사이트에 게시하거나 전자 메일을 통해 전송하는 등의 방법으로 액세스할 수 있도록 앱 URL을 위치에 붙여 넣습니다.

앱 디자이너의 **속성** 탭에서 앱 URL을 찾을 수도 있습니다. 

> [!div class="mx-imgBorder"] 
> ![앱 URL 복사](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>미리 정의된 보안 역할 정보
이러한 미리 정의된 역할은 [!INCLUDE [powerapps](../../includes/powerapps.md)] 환경에서 사용할 수 있습니다.


|보안 역할  |*권한  |설명 |
|---------|---------|---------|
|환경 결정자     |  없음       | Power Automate를 사용하여 앱, 연결, 사용자 지정 API, 게이트웨이 및 흐름을 포함한 환경과 관련된 새 리소스를 만들 수 있습니다. 그러나 환경 내에서 데이터에 액세스할 수 있는 권한은 없습니다. 추가 정보: [환경 개요](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|시스템 관리자     |  만들기, 읽기, 쓰기, 삭제, 사용자 지정, 보안 역할       | 보안 역할 만들기, 수정 및 할당을 포함하여 환경을 사용자 지정하거나 관리할 수 있는 모든 권한이 있습니다. 환경의 모든 데이터를 볼 수 있습니다. 추가 정보: [사용자 지정에 필요한 권한](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|시스템 사용자 지정자     | 만들기(자체), 읽기(자체), 쓰기(자체), 삭제(자체), 사용자 지정         | 환경을 사용자 지정하는 전체 권한이 있습니다. 그러나 만든 환경 엔터티의 레코드만 볼 수 있습니다. 추가 정보: [사용자 지정에 필요한 권한](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service 사용자     |  읽기, 만들기(자체), 쓰기(자체), 삭제(자체)       | 환경 내에서 앱을 실행하고 자신이 소유한 레코드에 대해 일반적인 작업을 수행할 수 있습니다.        |
|위임     | 다른 사용자 대신 작업        | 코드를 다른 사용자로 실행하거나 가장할 수 있습니다.  일반적으로 다른 보안 역할과 함께 사용되어 레코드에 대한 액세스를 허용합니다. 추가 정보: [다른 사용자로 가장](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*권한은 달리 지정되지 않는한 전역 범위입니다.

## <a name="next-steps"></a>다음 단계
[모바일 장치에서 모델 기반 앱 실행](../../user/run-app-client-model-driven.md)



