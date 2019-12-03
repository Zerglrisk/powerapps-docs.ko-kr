---
title: Oracle 데이터베이스에 연결 | Microsoft Docs
description: Oracle 데이터베이스에 연결하고 PowerApps에서 앱을 빌드하기 위해 사용하는 방법에 알아봅니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 31bf18342de1191dbd816093186fe33e31755232
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678744"
---
# <a name="connect-to-an-oracle-database-from-powerapps"></a>PowerApps에서 Oracle 데이터베이스에 연결
연결을 만들고 Power Apps에서 앱을 빌드한 후 테이블을 나열 하 고 Oracle 데이터베이스에서 테이블 행을 만들고, 읽고, 업데이트 하 고, 삭제 합니다. Oracle 데이터베이스 연결은 트리거 또는 저장 프로시저를 제외한 필터링, 정렬 및 기타 함수의 전체 위임을 지원합니다.

## <a name="prerequisites"></a>필수 조건
* Oracle 9 이상
* Oracle 클라이언트 소프트웨어 8.1.7 이상
* 온-프레미스 데이터 게이트웨이 설치
* Oracle 클라이언트 SDK 설치

### <a name="install-an-on-premises-data-gateway"></a>온-프레미스 데이터 게이트웨이 설치
게이트웨이를 설치하려면 [이 자습서](../gateway-management.md)의 단계를 따릅니다.

온-프레미스 데이터 게이트웨이는 온-프레미스 데이터 (클라우드에 없는 데이터)와 Power BI, 파워 자동화, Logic Apps 및 Power Apps 서비스 간에 빠르고 안전한 데이터 전송을 제공 하는 브리지 역할을 합니다. 여러 서비스 및 여러 데이터 원본과 동일한 게이트웨이를 사용할 수 있습니다. 자세한 내용은 [게이트웨이 이해](../gateway-reference.md)를 참조하세요.

### <a name="install-oracle-client"></a>Oracle 클라이언트 설치
온-프레미스 데이터 게이트웨이와 동일한 컴퓨터에 [Windows x64용 64비트 ODAC 12c 릴리스 4(12.1.0.2.4)](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)를 설치합니다. 그렇지 않은 경우, 알려진 문제의 목록에 설명된 대로 연결을 만들거나 사용하려고 하면 오류가 나타납니다.

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>Oracle 데이터베이스에서 테이블로 앱 만들기
1. Power Apps 스튜디오에서 **파일** 메뉴 (왼쪽 가장자리 근처)에서 **새로 만들기** 를 클릭 하거나 탭 합니다.
   
   ![새 옵션](./media/connection-oracledb/new-app.png)
2. **데이터를 통해 시작**에서 화살표를 클릭하거나 탭합니다.
   
      이미 있는 연결 목록이 나타납니다.
3. **새 연결**을 클릭하거나 탭합니다.
   
   ![새 연결](./media/connection-oracledb/new-connection.png)
4. 연결 목록에서 **Oracle 데이터베이스**를 클릭하거나 탭합니다.
   
   ![새 데이터베이스](./media/connection-oracledb/oracle-db.png)
5. Oracle 서버의 이름, 사용자 이름과 암호를 지정합니다.
   
    SID가 필요한 경우 이 형식의 서버를 지정합니다.<br>
    *ServerName*/*SID*
   
   ![연결 매개 변수](./media/connection-oracledb/connection-params.png)
6. 사용하려는 게이트웨이를 클릭 또는 탭하거나 하나 설치합니다.
   
    설치한 후에도 게이트웨이가 나타나지 않으면 **게이트웨이 목록새 로 고침**을 클릭합니다.
   
   ![새 게이트웨이](./media/connection-oracledb/choose-gateway.png)
7. **만들기**를 클릭하거나 탭하여 연결을 만듭니다.
   
   ![새로 만들기](./media/connection-oracledb/create-button.png)
8. **기본** 데이터 세트를 클릭하거나 탭합니다.
   
   ![새로 만들기](./media/connection-oracledb/choose-dataset.png)
9. 테이블 목록에서 사용하려는 테이블을 클릭하거나 탭합니다.
   
   ![새로 만들기](./media/connection-oracledb/choose-table.png)
10. **연결**을 클릭하여 앱을 만듭니다.
    
    ![새로 만들기](./media/connection-oracledb/connect-button.png)

Power Apps는 세 개의 화면이 있고 선택한 테이블의 데이터를 표시 하는 앱을 만듭니다.

* **BrowseScreen1** - 테이블의 모든 항목을 나열합니다.
* **DetailScreen1** - 단일 항목에 대한 자세한 정보를 제공합니다.
* **EditScreen1** - 사용자가 항목을 업데이트하거나 항목을 만듭니다.

![새로 만들기](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>다음 단계
* 방금 생성한 앱을 저장하려면 Ctrl-S 키를 누릅니다.
* **BrowseScreen1**(기본으로 나타남)을 사용자 지정하려면 [레이아웃 사용자 지정](../customize-layout-sharepoint.md)을 참조하세요.
* **DetailsScreen1** 또는 **EditScreen1**을 사용자 지정하려면 [양식 사용자 지정](../customize-forms-sharepoint.md)을 참조하세요.

## <a name="known-issues-tips-and-troubleshooting"></a>알려진된 문제, 팁 및 문제 해결
1. 게이트웨이에 연결할 수 없습니다.
   
    이 오류는 온-프레미스 데이터 게이트웨이가 클라우드에 연결할 수 없는 경우에 나타납니다. 게이트웨이의 상태를 확인하려면 powerapps.microsoft.com에 로그인하여 **게이트웨이**를 클릭하거나 탭한 다음, 사용하려는 게이트웨이를 클릭하거나 탭합니다.
   
    게이트웨이가 실행되고 있고 인터넷에 연결할 수 있는지 확인합니다. 꺼져 있거나 절전 상태인 컴퓨터에는 게이트웨이를 설치하지 마세요. 또는 온-프레미스 데이터 게이트웨이 서비스(PBIEgwService)를 다시 시작해 보세요.
2. System.Data.OracleClient는 Oracle 클라이언트 소프트웨어 버전 8.1.7 이상이 필요합니다.
   
    이 오류는 Oracle 클라이언트 SDK가 온-프레미스 데이터 게이트웨이와 동일한 컴퓨터에 설치되어 있지 않은 경우에 나타납니다. 이 문제를 해결하려면 [공식 공급자를 설치](https://go.microsoft.com/fwlink/p/?LinkID=272376)합니다.
3. '[Tablename]' 테이블은 모든 키 열을 정의하지 않습니다.
   
    이 오류는 Oracle 데이터베이스 연결에 필요한 기본 키가 없는 테이블에 연결하려고 하는 경우에 나타납니다.
4. 이 문서를 작성하는 날짜를 기준으로, 저장 프로시저, 복합 키가 있는 테이블, 테이블의 중첩된 개체 형식은 지원되지 않습니다.

