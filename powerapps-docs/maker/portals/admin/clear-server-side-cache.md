---
title: 포털에 대 한 서버 쪽 캐시 지우기 | MicrosoftDocs
description: 포털에서 즉시 캐시를 새로 고치도록 하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976004"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>포털에 대 한 서버 쪽 캐시 지우기

포털 관리자는 Common Data Service의 업데이트 된 데이터가 포털에 즉시 반영 되도록 전체 포털에 대 한 서버 쪽 캐시를 지울 수 있습니다. Common Data Service의 업데이트는 비동기 모드로 포털에 전달 되므로 Common Data Service에서 데이터가 업데이트 되는 시간과 포털에 업데이트 된 데이터가 표시 되는 시간 사이에 지연이 발생할 수 있습니다. 예를 들어이 지연을 제거 하려면 포털 구성&mdash;방해할 때 포털에서 캐시를 즉시 새로 고치도록 강제할 수&mdash;.

> [!NOTE]
> 캐시 새로 고침 (Common Data Service 및 포털 간 데이터 전송)에 대 한 SLA는 15 분입니다.

서버 쪽 캐시를 지우려면

1.  관리자 권한으로 포털에 로그인 합니다.

2.  다음과 같이 URL로 이동 합니다. `<portal_path>/_services/about`

3.  **캐시 지우기**를 선택 합니다. 

서버 쪽 캐시가 삭제 되 고 Common Data Service에서 데이터가 다시 로드 됩니다. 포털 서버 쪽 캐시를 지우면 Common Data Service에서 데이터를 다시 로드 하는 동안 일시적으로 포털 성능이 저하 될 수 있습니다.

> [!div class=mx-imgBorder]
> 포털 캐시 ![지우기](../media/clear-portal-cache.png "포털 캐시 지우기")
