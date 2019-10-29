---
title: IP 주소를 사용 하 여 포털에 대 한 액세스 제한 | MicrosoftDocs
description: IP 주소로 포털 액세스를 제한 하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ba3315ed9ba6f2a0c89b6710debc55c4be00a427
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975935"
---
# <a name="restrict-portal-access-by-ip-address"></a>IP 주소로 포털 액세스 제한

포털은 컴퓨터의 모든 사용자가 프로 비전 하 고 액세스할 때 공개 됩니다. 이제 IP 주소 목록에서 포털에 대 한 액세스를 제한할 수 있습니다. 예를 들어 정부 조직에서는 회사 네트워크 내 에서만 콘텐츠를 표시할 수 있습니다. 상업적 조직은 게시 된 경우에만 포털을 표시 하 고, 데이터 누출을 방지 하기 위해 개발 중에는 표시 하지 않을 수 있습니다.

사용자가 포털에 대 한 요청을 생성 하는 경우 해당 IP 주소는 허용 목록에 대해 평가 됩니다. IP 주소가 목록에 없는 경우 포털에서 HTTP 403 상태 코드가 포함 된 웹 페이지를 표시 합니다.

IP 주소를 추가 하거나 제거 하려면 다음 역할 중 하나를 할당 해야 합니다.
- Office 365 전역 관리자 
- 서비스 관리자. 추가 정보: [서비스 관리자 역할을 사용 하 여 테 넌 트 관리](https://technet.microsoft.com/en-us/library/mt793847.aspx)  
- 포털에 대해 선택 된 Common Data Service 환경의 시스템 관리자

## <a name="add-an-ip-address"></a>IP 주소 추가

Ip 주소 또는 IP 주소 집합에서 포털에 대 한 액세스를 허용 하려면 목록에 IP 주소를 추가할 수 있습니다. 이렇게 하면 추가 된 IP 주소 목록 에서만 포털에 액세스할 수 있습니다. IP 주소를 추가 하지 않으면 모든 IP 주소에서 포털에 액세스할 수 있습니다.

제한 목록에 IP 주소를 추가 하면 지정 된 IP 주소에 대해서만 포털에 액세스할 수 있습니다. 다른 IP 주소에서 포털에 액세스 하려고 하면 액세스가 거부 되 고 HTTP 403 상태 코드가 포함 된 웹 페이지가 표시 됩니다. 이 웹 페이지의 콘텐츠는 정적 이며 수정할 수 없습니다.

> [!div class=mx-imgBorder]
> ![Html 403 오류](../media/ip-address-page-error.png "html 403 오류")  

> [!NOTE]
> 포털에서 액세스할 수 있는 공용 IP 주소를 지정 해야 합니다. 개인 IP 주소는 포털에서 액세스할 수 없습니다.

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **IP 주소 제한 설정**으로 이동 합니다. IP 주소와 해당 유형 목록이 표시 됩니다.

    > [!div class=mx-imgBorder]
    > Ip ![주소 제한]설정(../media/set-up-ip-address-restrict.png "ip 주소 제한") 설정

3.  IP 주소 제한 설정 페이지에서 **새로 추가**를 선택 합니다.

4.  IP 주소 추가 창에서 다음 값을 입력 합니다.

    - **Ip 주소 유형 선택**: Ip 주소가 IPv4 또는 IPv6 인지 여부를 선택 합니다.

    - Cidr 표기법 **으로 ip 주소 지정**: cidr 표기법으로 ip 주소를 지정 합니다. 추가 정보: [클래스 없는 도메인 간 라우팅](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > Ip ![주소 추가](../media/add-ip-address.png "ip 주소 추가")    

5.  **구성**을 선택 합니다.

## <a name="remove-an-ip-address"></a>IP 주소 제거

이전에 허용 된 IP 주소에서 포털에 대 한 액세스를 제거 하려면 목록에서 IP 주소를 제거 하면 됩니다. 모든 IP 주소를 제거 하면 모든 IP 주소에서 포털에 액세스할 수 있습니다.

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **IP 주소 제한 설정**으로 이동 합니다. IP 주소와 해당 유형 목록이 표시 됩니다.

    > [!div class=mx-imgBorder]
    > Ip ![주소 제한]설정(../media/set-up-ip-address-restrict.png "ip 주소 제한") 설정

3.  제거할 IP 주소 옆에 **있는 ip 주소 제거 (x)** 를 선택 합니다.

4.  확인 메시지에서 **제거** 를 선택 합니다.

