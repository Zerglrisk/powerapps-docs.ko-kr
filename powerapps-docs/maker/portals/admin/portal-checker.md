---
title: 포털을 사용하여 고객 문제를 식별하고 해결 | MicrosoftDocs
description: 포털을 사용하여 고객 문제를 식별하고 해결하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="portal-checker"></a>포털 검사기

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

포털 검사기는 포털 관리자가 포털에서 일반적인 문제를 식별하는 데 사용할 수 있는 셀프 서비스 진단 도구입니다. 포털 검사기는 다양한 구성 매개 변수를 확인하여 포털과 관련된 문제를 식별하는 데 도움이 되며 이를 해결하는 방법에 대한 제안을 제공합니다.

포털 검사기를 실행하면 결과가 표 형식으로 **진단 결과** 섹션에 표시됩니다. 결과 표에는 다음과 같은 열이 있습니다.

- **문제**: 고객이 직면한 최상위 문제를 표시합니다(예: 성능 문제).
- **범주**: 문제를 분류할 수 있는 최상위 영역을 표시합니다(예: 프로비저닝, 솔루션 업그레이드 등).
- **결과**: 문제 상태를 표시합니다(예: 오류, 경고 등).

기본적으로 표의 정보는 오류, 경고 및 전달 순서로 **결과** 열을 기준으로 정렬됩니다.

> [!div class=mx-imgBorder]
> ![진단 결과](../media/diagnostic-results.png "진단 결과")

문제를 확장하여 자세한 정보 및 완화 단계를 볼 수 있습니다. 완화 조치가 필요한 경우 조치를 수행하는 단추가 표시됩니다. 완화가 유용한 지 여부에 대한 피드백을 제공할 수도 있습니다.

> [!div class=mx-imgBorder]
> ![진단 결과에서 문제 확장](../media/diagnostic-results-issue-expand.png "진단 결과에서 문제 확장")

필요한 경우 업데이트된 데이터로 결과를 새로 고치는 진단 검사를 다시 실행할 수 있습니다.

> [!NOTE]
> 포털이 꺼져 있거나 IP 주소 필터링을 사용하는 경우 포털에서 특정 진단 검사가 실행되지 않습니다.

포털 검사기 도구에서 진단되는 일반적인 문제 목록은 [포털 검사기로 진단되는 일반적인 포털 문제 및 모범 사례](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/portal-faq)를 참조하십시오.

포털 검사기를 실행하려면:

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 검사기 실행**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![포털 검사기 실행](../media/run-diagnostics.png "포털 검사기 실행")

3.  **포털 검사기 실행**을 선택합니다. 진단 세션이 시작되고 고객 문제에 대한 데이터를 수집합니다. 결과는 **진단 결과** 섹션에 표시됩니다.

    > [!div class=mx-imgBorder]
    > ![진단 결과](../media/diagnostic-results.png "진단 결과")

4.  진단 검사를 다시 실행하려면 **결과 새로 고침**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![진단 결과 새로 고침](../media/diagnostic-results-refresh.png "진단 결과 새로 고침")
