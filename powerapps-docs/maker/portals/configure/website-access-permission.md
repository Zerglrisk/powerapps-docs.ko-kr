---
title: Power Apps 포털에서 웹 사이트 액세스 권한 만들기 | MicrosoftDocs
description: 웹 사이트 액세스 권한을 만들고 포털의 요소에 연결하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ab85eb4feca871089366c8675305b4f6c741f0af
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873469"
---
# <a name="create-website-access-permissions"></a>웹 사이트 액세스 권한 만들기

웹 사이트 액세스 권한은 [웹 역할](create-web-roles.md)과 관련된 권한 집합으로, 포털 내에서 단지 웹 페이지가 아닌 여러 콘텐츠 관리 요소에 대한 전면 편집을 허용합니다. 권한 설정은 포털에서 관리할 구성 요소를 결정합니다.

| 이름                         | 설명                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| 콘텐츠 조각 관리      | 조각 컨트롤의 편집을 허용합니다.                                                          |
| 사이트 마커 관리          | 사이트 마커를 사용하는 하이퍼링크 편집 허용                                           |
| 웹 링크 설정 관리         | 웹 링크 집합에서 웹 링크 추가 및 제거를 포함하여 [웹 링크 집합](manage-web-links.md)을 편집할 수 있습니다. |
| 게시되지 않은 엔터티 미리 보기 | 포털에 노출 설정된 게시 상태가 초안인 엔터티를 볼 수 있습니다.             |
|||

웹 사이트 액세스 권한을 만들고 이를 웹 역할에 추가하려면 다음을 수행합니다.

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 사이트 액세스 권한**으로 이동합니다.

3. **새로 만들기**를 선택합니다.

4. **일반**에서 이름, 웹 사이트를 입력하고 필요한 권한을 선택합니다.

    ![웹 사이트 액세스 권한 만들기](../media/website-access-permission.png "웹 사이트 액세스 권한 만들기")

5. **웹 역할**에서 **기존 웹 역할 추가**를 선택하고 권한을 연결할 웹 역할을 추가합니다.

6. 변경 내용을 저장합니다.

    
