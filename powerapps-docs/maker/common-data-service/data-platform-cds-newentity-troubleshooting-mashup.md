---
title: 파워 쿼리 문제 해결 | Microsoft Docs
description: 파워 쿼리를 사용하여 Common Data Service에서 사용자 지정 엔터티를 만드는 방법으로 문제를 해결합니다.
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5679d82d6ec53d579567a778043ac9542099a20e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706686"
---
# <a name="troubleshoot-power-query"></a>파워 쿼리 문제 해결
Excel용 파워 쿼리를 사용하여 외부 원본의 데이터를 포함하는 사용자 지정 엔터티를 만드는 경우 이 오류가 나타날 수 있습니다.

>"Azure Active Directory 관리자가 이 기능을 사용하지 못하도록 하는 정책을 설정했습니다. 사용자를 대신하여 이 기능에 대한 권한을 부여할 수 있는 관리자에게 문의하십시오. "

파워 쿼리가 PowerApps 또는 Common Data Service에서 조직의 데이터에 액세스할 수 없는 경우 오류가 표시됩니다. 이러한 상황은 다음과 같은 두 가지 상황에서 발생합니다.

* Azure Active Directory(Azure AD) 테넌트 관리자가 사용자를 대신하여 회사 데이터에 액세스하는 앱에 대한 동의 권한을 허용하지 않습니다.
* 관리되지 않는 Active Directory 테넌트 사용 관리되지 않는 테넌트는 셀프 서비스 등록 제안을 완료하기 위해 만든 전역 관리자가 없는 디렉터리입니다. 이 시나리오를 해결하려면 먼저 사용자가 관리되는 테넌트로 변환한 다음 이 문제에 대한 두 가지 해결 방법 중 하나를 수행해야 합니다. 솔루션에 대해서는 다음 섹션에서 설명합니다.

이 문제를 해결하려면 Azure Active Directory 관리자가 이 문서의 뒷부분에 나오는 절차 중 하나를 따라야 합니다.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>사용자가 회사 데이터에 액세스하는 앱에 동의할 수 있음
이 방법은 다음보다 더 쉬울 수 있지만 광범위한 사용 권한을 허용합니다.

1. [Azure Portal](https://portal.azure.com)에서 **Azure Active Directory** 창을 열고 **사용자 설정**을 선택합니다.
2. **사용자가 대신하여 회사 데이터에 액세스하는 앱에 동의할 수 있음** 옆에서 **예**를 선택한 다음 **저장**을 선택합니다.

## <a name="allow-power-query-to-access-company-data"></a>파워 쿼리가 회사 데이터에 액세스할 수 있음
또는 테넌트 관리자가 테넌트 수준 권한을 수정하지 않고 파워 쿼리에 동의를 제공할 수 있습니다.

1. [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)을 설치합니다.
2. 다음 PowerShell 명령을 실행합니다.
   * Login-AzureRmAccount(및 테넌트 관리자로 로그인)
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

이 방법의 장점(테넌트 수준 솔루션 대비)은 이 솔루션의 대상이 매우 분명하다는 것입니다. **파워 쿼리** 서비스 사용자만 프로비전하지만 테넌트에는 다른 권한 변경이 수행되지 않습니다.

## <a name="update-personal-data"></a>개인 데이터 업데이트

사용자는 쿼리 편집기를 통해 및 쿼리 편집기에서 액세스할 수 있는 **옵션** 대화 상자를 통해 매시업 및 기타 정보(예: 쿼리 이름 및 매시업 메타데이터)를 업데이트할 수 있습니다.

PowerApps에서 다음을 수행하여 쿼리 편집기에 액세스합니다.
1. **데이터** 창으로 이동하여 확장한 다음 **엔터티**를 선택합니다. 
2. 줄임표(...)를 선택한 다음 **쿼리 편집**을 선택합니다.
3. 리본 메뉴에서 **옵션** 단추를 선택한 다음 **내보내기 진단** 단추를 선택합니다.


## <a name="delete-personal-data"></a>개인 데이터 삭제

대부분의 데이터는 30일 이내에 자동으로 삭제됩니다. 매시업에 대한 데이터 및 메타데이터의 경우 사용자는 PowerApps를 통해 모든 매시업을 제거해야 합니다. 연결된 모든 데이터와 메타데이터는 30일 이내에 삭제됩니다.

PowerApps에서 매시업을 제거하려면
1. 이름이 같은 탭에서 제거할 수 있는 데이터 통합자 프로젝트를 제거합니다.
2. 줄임표(...)를 선택한 다음 **삭제** 옵션을 선택합니다.

"데이터에서 새 엔터티(기술 미리 보기)" 기능을 통해 매시업을 만든 경우 다음을 수행하여 제거할 수 있습니다.
1. 줄임표(...)를 선택한 다음 **쿼리 편집**을 선택합니다.
2. 리본 메뉴에서 **옵션** 단추를 클릭합니다.
3. **모든 쿼리 제거** 단추를 선택합니다.  
    쿼리를 삭제할 것인지 확인한 후에는 삭제됩니다.

## <a name="export-personal-data"></a>개인 데이터 내보내기

개인 데이터를 내보내려면 사용자가 다음을 수행할 수 있습니다.
1. 쿼리 편집기를 엽니다.
2. 리본 메뉴에서 **옵션** 단추를 클릭합니다.
3. **내보내기 진단** 단추를 선택합니다.

PowerApps에서 다음을 수행하여 쿼리 편집기에 액세스할 수 있습니다.
1. **데이터** 창으로 이동하여 확장한 다음 **엔터티**를 선택합니다.
2. 줄임표(...)를 선택한 다음 **쿼리 편집**을 선택합니다. 
3. 리본 메뉴에서 **옵션** 단추를 선택한 다음 **내보내기 진단** 단추를 선택합니다.

사용자 인터페이스(UI)에서 사용자 작업에 대한 시스템 생성 로그는 Azure 포털에서 액세스할 수 있습니다.



