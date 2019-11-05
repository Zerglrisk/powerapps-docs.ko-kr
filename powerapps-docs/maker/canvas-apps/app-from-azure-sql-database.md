---
title: Azure SQL Database |에서 캔버스 앱 만들기 Microsoft Docs
description: Azure SQL Database의 데이터에서 캔버스 앱을 만드는 방법을 설명 합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/29/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 652c8d5c67a9f7245ed40be23cc827354d9b1e42
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540883"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>미리 보기: Azure SQL Database에서 캔버스 앱 만들기

[이 토픽은 시험판 설명서이며 변경될 수 있습니다.]

이 항목에서는 Azure SQL Database의 데이터를 사용 하 여 PowerApps를 사용 하 여 몇 분 안에 앱을 만듭니다. 비즈니스 요구에 맞게 사용자 지정 하 고 모든 장치에서 공유 하는 데 사용할 수 있는 완벽 한 기능의 앱이 제공 됩니다.

> [!IMPORTANT]
> - 미리 보기 기능입니다.
> - 미리 보기 기능을 사용 하면 제한 된 기능 및 제한 된 기능을 사용할 수 있습니다. 고객은 초기 액세스 권한을 얻고 피드백을 제공할 수 있도록 미리 보기 기능을 공식 릴리스 전에 사용할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

- 브라우저에서 팝업을 사용 하도록 설정 해야 합니다.
- Azure 구독이 필요 합니다. </br>Azure 구독이 없는 경우 [무료 계정을 만듭니다](https://azure.microsoft.com/free/).
- 기존 SQL Database에 대 한 액세스 권한이 필요 합니다. </br> 기존 SQL Database 없는 경우 [새 데이터베이스를 만듭니다](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- 방화벽 설정에서 SQL Database 하려면 PowerApps 지역 [IP 주소 또는 Azure 서비스](#app-access-to-sql-database) 액세스를 허용 해야 합니다.
- SQL Database 테이블에는 text 데이터 형식의 열이 하나 이상 있어야 합니다.
- 유효한 PowerApps 라이선스가 필요 하거나 [30 일 평가판 라이선스](../signup-for-powerapps.md)에 등록 하세요.

## <a name="create-an-app"></a>앱 만들기

1. [Azure Portal](https://portal.azure.com)에 로그인 합니다.
2. SQL Database로 이동 합니다.
3. PowerApps를 선택 합니다.

    
    ![SQL Database 옵션의 PowerApps 옵션](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "SQL Database 내 PowerApps 옵션")

    > [!NOTE]
    > PowerApps 라이선스가 없는 경우 평가판을 시작 하기 위한 링크가 포함 된 파란색 정보 표시줄이 표시 됩니다. 평가판을 시작 하도록 선택 하면 라이선스에 등록 되는 새 탭으로 이동 됩니다. 완료 되 면 Azure Portal로 돌아가서 블레이드를 새로 고쳐 계속 합니다.

4. 앱에 대 한 이름 (예: "사이트 검사", "Fundraiser" 또는 "예산 추적 장치")을 입력 합니다.

5. SQL 인증 암호를 입력 하 고 필요한 경우 사용자 이름을 변경 합니다.
6. 드롭다운 목록에서 앱을 만드는 데 사용할 테이블을 선택 합니다.

7. **만들기**를 선택합니다.


    ![앱에 대 한 정보 지정](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "앱에 대 한 정보 지정")

    [PowerApps Studio](https://create.powerapps.com/studio/) 새 탭에서 열립니다. 팝업이 차단 된 경우 팝업을 허용 하도록 브라우저를 업데이트 하 고 다시 시도 합니다. 만든 후에는 SQL Database 데이터를 사용 하는 3 페이지 앱을 갖게 됩니다.

## <a name="accessing-your-app"></a>앱 액세스

만든 앱에 다시 액세스 하려면 [make.powerapps.com](https://make.powerapps.com)로 이동 합니다.

## <a name="app-environment-and-region"></a>앱 환경 및 지역

이 메서드를 사용 하 여 만든 앱은 테 넌 트의 [기본 환경을](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) 사용 하 고이 환경의 지역에 배포 됩니다. [관리 센터](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed)에서 배포 된 앱의 지역 또는 테 넌 트의 기본 환경을 찾을 수 있습니다. 특정 환경에서 모든 앱을 검토 하려면 [make.powerapps.com](https://make.powerapps.com)로 이동 하 여 리본에서 **환경을** 선택한 다음 왼쪽에서 **앱** 을 선택 합니다.

## <a name="app-access-to-sql-database"></a>SQL Database에 대 한 앱 액세스

IP 주소를 사용 하 여 SQL Database에 연결 하거나 Azure 서비스로 PowerApps를 구성할 수 있습니다.

### <a name="app-access-using-ip-address"></a>IP 주소를 사용 하 여 앱 액세스

[Powerapps 시스템 요구 사항은](limits-and-config.md#ip-addresses) 앱의 지역에 따라 powerapps에서 사용 하는 IP 주소를 나열 합니다.

Transact-sql 저장 프로시저 또는 Azure Portal를 사용 하 여이 액세스를 구성할 수 있습니다.

- SQL Database 또는 SQL Server 방화벽 규칙에 대 한 저장 프로시저 [sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current)
- SQL Server 방화벽 규칙에 대 한 [Azure Portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)

### <a name="app-access-as-an-azure-service"></a>Azure 서비스로 앱 액세스

PowerApps는 Azure Portal를 사용 하 여 **Azure 서비스 제어에 대 한 액세스를 허용** SQL Database에 연결할 수 있습니다. 이 액세스를 구성 하려면 [Azure Portal](https://portal.azure.com/) 에 로그인 하 고 포털에서 **SQL Server**로 이동 합니다. **방화벽 및 가상 네트워크** 를 선택 하 고 **이 서버에 액세스할 수 있는 Azure 서비스 및 리소스가** **있는**컨트롤을 설정으로 설정 합니다. **저장** 을 선택 하 여 변경 내용을 제출 합니다.

> [!IMPORTANT]
> 제어를 설정 된 상태로 두면 Azure SQL Database 서버는 azure 경계 내의 모든 서브넷에서 통신을 수락 합니다 .이는 Azure 데이터 센터에 대해 정의 된 범위 내에서 해당 IP 주소 중 하나로 인식 됩니다. 컨트롤 집합을 ON으로 두면 보안 관점에서 과도 하 게 액세스할 수 있습니다.

## <a name="limitations"></a>제한 사항

- 앱 이름에는 문자, 숫자, 하이픈, 괄호 또는 밑줄만 사용할 수 있습니다.
- PowerApps에서 SQL Database에 연결 하려면 SQL 인증이 필요 합니다.
- Azure Portal에서 캔버스 앱을 만드는 동안에는 하나의 테이블만 선택할 수 있습니다. 더 많은 데이터 연결을 추가 하 여 더 많은 테이블 및 기타 데이터 원본을 추가 하려면 앱을 만든 후 앱을 사용자 지정 합니다.
- PowerApps는 VNet 서비스 끝점을 사용 하 여 SQL Database에 연결할 수 없습니다. 자세한 내용은 [VNet 서비스 끝점을 통한 액세스 허용](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview)을 참조 하세요.

## <a name="other-considerations"></a>기타 고려 사항

- SQL Database에 대 한 앱 액세스는 [이 앱을 공유](share-app.md) 하는 모든 사용자에 게 암시적으로 공유 됩니다. SQL 인증 자격 증명에 데이터 읽기 및 쓰기에 대 한 적절 한 액세스 권한이 있는지 확인 합니다. </br> 예를 들어 다른 SQL 인증 자격 증명을 사용 하 여 동일한 SQL Database에 연결 하 여 읽기 및 읽기/쓰기 액세스를 분리 하는 별도의 앱을 만들 수 있습니다.
- 이 기능에서 성능 고려 사항에 대해 사용 하는 [SQL Database](https://docs.microsoft.com/connectors/sql/) 커넥터의 제한 제한, 위임할 기능 및 작업, 알려진 문제 및 제한 사항을 검토 합니다.
- SQL Database의 데이터를 사용 하 여 기본이 아닌 환경 및 테 넌 트의 다른 지역에 대 한 앱을 만들어야 하는 경우 [make.powerapps.com](https://make.powerapps.com) 에서 앱을 만듭니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Azure Portal를 사용 하 여 SQL Database의 데이터를 사용 하 여 앱을 만들었습니다. 다음 단계로 비즈니스 요구 사항에 더 적합 하도록 컨트롤, 이미지 및 논리를 사용 하 여 앱을 사용자 지정 합니다.

> [!div class="nextstepaction"]
> [PowerApps에서 캔버스 앱 인터페이스 디자인](add-configure-controls.md)

## <a name="see-also"></a>참고 항목

- [PowerApps에서 캔버스 앱 공유](share-app.md) </br>
- [PowerApps에서 캔버스 앱에 데이터 연결 추가](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: PowerApps에서 캔버스 앱 사용자 지정](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
