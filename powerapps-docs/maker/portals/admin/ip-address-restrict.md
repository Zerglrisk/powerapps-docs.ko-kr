---
title: IP 주소를 사용하여 포털에 대한 액세스 제한 | MicrosoftDocs
description: IP 주소로 포털 액세스를 제한하는 지침.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: efc0ea8449e387d292063f16ee6e38f69863267c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867242"
---
# <a name="restrict-portal-access-by-ip-address"></a>IP 주소로 포털 액세스 제한

포털은 컴퓨터의 모든 사용자가 프로비저닝하고 액세스할 수 있는 경우 공개입니다. 이제 IP 주소 목록에서 포털에 대한 액세스를 제한할 수 있습니다. 예를 들어, 정부 기관은 해당 기업 네트워크 내에서만 콘텐츠를 노출시킬 수 있습니다. 상용 조직에서는 데이터 누출을 방지하기 위해 포털이 개발 중일 때가 아니라 게시된 경우에만 포털을 표시할 수 있습니다.

포털에 대한 요청이 사용자로부터 생성되면 해당 IP 주소가 허용 목록과 비교하여 평가됩니다. IP 주소가 목록에 없으면 포털에 HTTP 403 상태 코드가 포함된 웹 페이지가 표시됩니다.

IP 주소를 추가하거나 제거하려면 다음 역할 중 하나를 할당 받아야 합니다.
- Office 365 전역 관리자 
- 서비스 관리자. 추가 정보: [서비스 관리자 역할을 사용하여 테넌트 관리](https://technet.microsoft.com/library/mt793847.aspx)  
- 포털에 선택된 Common Data Service 환경의 시스템 관리자

## <a name="add-an-ip-address"></a>IP 주소 추가

IP 주소 또는 IP 주소 집합에서 포털에 대한 액세스를 허용하려면 목록에 IP 주소를 추가할 수 있습니다. 이렇게 하면 추가된 IP 주소 목록에서만 포털에 액세스할 수 있습니다. IP 주소를 추가하지 않으면 모든 IP 주소에서 포털에 액세스할 수 있습니다.

제한 목록에 IP 주소를 추가하면 포털에 지정된 IP 주소만 액세스할 수 있습니다. 다른 IP 주소에서 포털에 액세스하려고 하면 액세스가 거부되고 HTTP 403 상태 코드가 포함된 웹 페이지가 표시됩니다. 이 웹 페이지의 내용은 정적이므로 수정할 수 없습니다.

> [!div class=mx-imgBorder]
> ![HTML 403 오류](../media/ip-address-page-error.png "HTML 403 오류")  

> [!NOTE]
> 포털에서 액세스할 수 있는 공용 IP 주소를 지정해야 합니다. 포털에서 개인 IP 주소에 액세스할 수 없습니다.

1.  [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **IP 주소 제한 설정**으로 이동합니다. IP 주소와 해당 종류의 목록이 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![IP 주소 제한 설정](../media/set-up-ip-address-restrict.png "IP 주소 제한 설정")

3.  IP 주소 제한 설정 페이지에서 **새로 추가**를 선택합니다.

4.  IP 주소 추가 창에서 다음 값을 입력합니다.

    - **IP 주소 유형 선택**: IP 주소가 IPv4 인지 IPv6 인지를 선택합니다.

    - **CIDR 표기법으로 IP 주소 지정**: CIDR 표기법으로 IP 주소를 지정합니다. 추가 정보:[ 클래스 없는 도메인 간 라우팅](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![IP 주소 추가](../media/add-ip-address.png "IP 주소 추가")    

5.  **구성**을 선택합니다.

## <a name="remove-an-ip-address"></a>IP 주소 제거

이전에 허용된 IP 주소에서 포털에 대한 액세스 권한을 제거하려면 목록에서 IP 주소를 제거하면 됩니다. 모든 IP 주소를 제거하는 경우 모든 IP 주소에서 포털에 액세스할 수 있습니다.

1.  [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **IP 주소 제한 설정**으로 이동합니다. IP 주소와 해당 종류의 목록이 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![IP 주소 제한 설정](../media/set-up-ip-address-restrict.png "IP 주소 제한 설정")

3.  제거할 IP 주소 옆에 있는 **제거할 IP 주소 (x) 제거**를 선택합니다.

4.  확인 메시지에서 **제거**를 선택합니다.

