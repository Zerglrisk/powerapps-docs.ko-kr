---
title: 포털의 웹 페이지에서 평가 또는 투표 | MicrosoftDocs
description: 포털의 블로그 게시물에서 등급을 설정 및 관리하는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e32d2e7969481c3aea4ab3abefb5bfc5c48e8852
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866758"
---
# <a name="rate-or-vote-on-a-webpage-on-a-portal"></a>포털의 웹 페이지에서 평가 또는 투표

등급은 웹 페이지에서 평가하거나 투표할 수 있는 기능을 제공합니다. 페이지에 대한 댓글에 대해서도 등급을 사용할 수 있습니다. 기본적으로 이 기능은 비활성화되어 있으나 페이지 단위로 사용하도록 설정할 수 있습니다.

등급은 사용자 지정 활동이므로 전자 메일, 전화 통화 등과 같은 기타 활동과 동일한 방식으로 사용할 수 있습니다. 등급은 활동이므로 사용자 지정을 사용하면 사용자 지정 엔터티를 포함하여 포털에서 나타나고 렌더링되며 사용자가 선택하는 모든 엔터티의 등급을 나타낼 수 있습니다.

## <a name="enable-ratings-for-pages"></a>페이지에 등급 사용

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 페이지**로 이동합니다.

3. 등급을 사용하도록 설정할 **웹 페이지**를 선택합니다.

4. **일반** 탭의 **페이지 옵션** 아래에서 **등급 사용**을 **예**로 설정합니다.

5. **저장 후 닫기**를 선택합니다.

## <a name="use-ratings"></a>등급 사용

웹 페이지에 페이지 등급을 사용하도록 설정되어 있고 개발자가 템플릿에 컨트롤을 적용한 경우, 사용자는 컨트롤을 페이지 템플릿에 추가할 때 선택된 유형에 따라 등급 척도 또는 투표 중 하나를 사용하여 페이지를 평가할 수 있습니다.

### <a name="rating-type"></a>등급 유형

![등급 유형](../media/rating-type.png "등급 유형")  

### <a name="vote-type"></a>투표 유형

![투표 유형](../media/vote-type.png "투표 유형")  

## <a name="manage-ratings"></a>등급 관리

웹 페이지의 등급을 Power Apps 포털 내에서 보거나 수정 또는 삭제할 수 있습니다.

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. 평가를 보고 싶은 **웹 페이지**로 이동합니다.

3. **관련 항목** 탭에서 **활동**을 선택합니다. 연결된 보기에 선택한 웹 페이지의 평가가 나열됩니다. 이 보기에서 사용자가 기존 등급을 수정하거나 삭제할 수 있습니다.
