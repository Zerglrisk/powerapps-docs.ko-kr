---
title: 포털을 사용 하 여 고객 문제 식별 및 해결 | MicrosoftDocs
description: 포털을 사용 하 여 고객 문제를 식별 하 고 해결 하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976188"
---
# <a name="portal-checker"></a>포털 검사기

포털 검사기는 포털 관리자가 포털에서 일반적인 문제를 식별 하는 데 사용할 수 있는 셀프 서비스 진단 도구입니다. 포털 검사기를 사용 하면 다양 한 구성 매개 변수를 확인 하 여 포털 문제를 식별 하 고 해결 방법에 대 한 제안을 제공할 수 있습니다.

포털 검사기를 실행 하면 결과가 **진단 결과** 섹션에 표 형식으로 표시 됩니다. 결과 표에는 다음과 같은 열이 있습니다.

- **문제**: 고객이 직면 한 최상위 문제를 표시 합니다. 예를 들어 성능 문제입니다.
- **범주**: 문제를 분류할 수 있는 최상위 영역을 표시 합니다. 예를 들어 프로 비전, 솔루션 업그레이드 등이 있습니다.
- **결과**: 문제 상태를 표시 합니다. 예를 들어 오류, 경고 등이 있습니다.

기본적으로 표의 정보는 오류, 경고 및 통과 순서로 **결과** 열을 기준으로 정렬 됩니다.

> [!div class=mx-imgBorder]
> ![진단 결과](../media/diagnostic-results.png "진단 결과")

문제를 확장 하 여 자세한 정보 및 완화 단계를 볼 수 있습니다. 완화 작업이 필요한 경우 작업을 수행 하는 단추가 표시 됩니다. 또한 완화가 유용한 지 여부에 대 한 피드백을 제공할 수 있습니다.

> [!div class=mx-imgBorder]
> 진단 ![결과에서 문제를 확장]하 여(../media/diagnostic-results-issue-expand.png "진단 결과의 문제를 확장 합니다") .

필요한 경우 업데이트 된 데이터로 결과를 새로 고치는 진단 검사를 다시 실행할 수 있습니다.

> [!NOTE]
> 포털이 꺼져 있거나 IP 주소 필터링이 설정 된 경우 포털에서 특정 진단 검사가 실행 되지 않습니다.

포털 검사기 도구에서 진단 하는 일반적인 문제 목록은 [포털 검사기에서 진단 하는 일반적인 포털 문제 및 모범 사례](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq)를 참조 하세요.

포털 검사기를 실행 하려면:

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 검사기 실행**으로 이동 합니다.

    > [!div class=mx-imgBorder]
    > 포털 ![검사기]실행(../media/run-diagnostics.png "포털 검사기 실행")

3.  **포털 검사기 실행**을 선택 합니다. 진단 세션이 시작 되어 고객 문제에 대 한 데이터를 수집 합니다. 결과는 **진단 결과** 섹션에 표시 됩니다.

    > [!div class=mx-imgBorder]
    > ![진단 결과](../media/diagnostic-results.png "진단 결과")

4.  진단 검사를 다시 실행 하려면 **결과 새로 고침**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![진단 결과]새로 고침(../media/diagnostic-results-refresh.png "진단 결과") 새로 고침
