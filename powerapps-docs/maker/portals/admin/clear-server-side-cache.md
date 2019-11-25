---
title: 포털에 대한 서버 쪽 캐시 지우기 | MicrosoftDocs
description: 포털이 즉각 캐시를 새로 고치도록 강제하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2709898"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>포털에 대한 서버측 캐시 지우기

포털 관리자는 전체 포털에 대한 서버 측 캐시를 지워 Common Data Service에서 업데이트된 데이터가 포털에 즉각 반영되도록 할 수 있습니다. Common Data Service의 업데이트는 비동기 모드에서 포털에 전달되므로 Common Data Service에서 데이터가 업데이트되는 시간과 업데이트된 데이터가 포털에 표시되는 시간 사이에 지연이 발생할 수 있습니다. 이 지연을 없애려면&mdash;예컨대, 포털 구성이 방해되는 경우&mdash;포털이 해당 캐시를 즉각 새로 고치도록 강제할 수 있습니다.

> [!NOTE]
> 캐시 새로 고침(Common Data Service 및 포털 간 데이터 전송)에 대한 SLA는 15분입니다.

서버측 캐시 지우기

1.  포털에 관리자로서 로그인합니다.

2.  URL `<portal_path>/_services/about`로 이동합니다.

3.  **캐시 지우기**를 선택합니다. 

서버측 캐시가 삭제되고 Common Data Service에서 데이터를 다시 로드합니다. 포털 서버 측 캐시를 지우면 Common Data Service에서 데이터를 다시 로드하는 동안에 포털 성능이 일시적으로 저하될 수 있습니다.

> [!div class=mx-imgBorder]
> ![포털 캐시 지우기](../media/clear-portal-cache.png "포털 캐시 지우기")
