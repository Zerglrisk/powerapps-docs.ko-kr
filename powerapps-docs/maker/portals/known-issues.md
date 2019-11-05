---
title: PowerApps 포털의 알려진 문제 | Microsoft 문서
description: PowerApps 포털의 알려진 문제에 대해 알아보기
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="known-issues"></a>알려진 문제

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="general-issues"></a>일반적인 문제

- 이러한 앱은 사전 프로비저닝된 앱이므로 이전에 프로비저닝되었을 수 있기 때문에 앱이 **수정된 날짜**가 잘못되었을 수 있습니다.

- 포털의 담당자가 올바르게 표시되지 않습니다. 이는 시스템으로 표시됩니다.

- 최근에 삭제한 포털의 URL을 재사용하여 새 포털을 작성하는 경우 런타임 설정에 약간의 지연이 있습니다. 이전 리소스 제거가 계속 진행 중이기 때문이며 새 포털이 Azure에 설정되려면 30분에서 1시간이 걸릴 수 있습니다.

- PowerApps에서 환경을 전환할 때 환경 내의 포털이 **앱** 또는 **최근 앱** 목록에 즉시 표시되지 않을 수 있습니다. 이는 테넌트와 다른 지역에서 생성된 환경에서 특히 발생합니다. 해결 방법은 브라우저를 새로 고치거나 포털이 앱 목록에 표시될 때까지 기다리십시오.

- PowerApps 포털 관리 센터에서 포털을 성공적으로 재설정한 경우 다음 오류가 표시됩니다. "액세스하려는 포털은 현재 로그인 한 테넌트에 속하지 않습니다. 로그아웃하고 올바른 테넌트로 로그인하십시오." PowerApps 홈 페이지를 방문하여 새 포털을 만들 수 있습니다. 

## <a name="portal-designer-issues"></a>포털 디자이너 문제

-   텍스트 상자에서 텍스트를 선택하면 선택한 텍스트의 글꼴 크기가 서식 도구 모음에 표시되지 않습니다.

- 섹션의 열 여백은 웹 사이트에서 렌더링되는 것과 다릅니다. 여백은 섹션 내부의 콘텐츠에 따라 조정됩니다.

- 캔버스는 중국어로 콘텐츠를 로드하지 않습니다.

- **측면 탐색이 있는 페이지** 템플릿을 사용하는 웹 페이지는 웹 페이지 생성 중에 존재했던 페이지의 링크만 표시합니다. You can update the links on the left side of the page by changing the 페이지 템플릿을 다른 템플릿으로 변경한 다음 다시 **측면 탐색이 있는 페이지**로 변경하여 페이지 왼쪽의 링크를 업데이트할 수 있습니다.

- 웹 페이지를 삭제하면 캔버스는 다음에 새로 고칠 때까지 업데이트된 메뉴를 반영하지 않습니다.

- 재작성 페이지(포털 디자이너의 지원되지 않는 페이지)에서 하위 페이지를 작성할 때 페이지를 렌더링하려면 속성 창에서 수동으로 템플릿을 선택해야 합니다.

- 페이지 이름이 크고 **페이지** 창에 완전히 표시되지 않은 경우 **줄임표** 버튼(...)이 표시되지 않습니다. 페이지 옵션을 보려면 페이지 이름을 마우스 오른쪽 단추로 클릭해야 합니다.

- 페이지에 비활성화된 콘텐츠 코드 조각을 추가한 경우 포털 디자이너에 표시됩니다. 그러나 비활성화된 콘텐츠 코드 조각은 실제 웹 사이트에서 숨겨집니다.

- 웹 링크, Power BI, 차트와 같은 구성 요소의 자리 표시자는 편집할 수 없습니다. 그러나 구성 요소의 텍스트는 편집할 수 있습니다. 자리 표시자의 변경 내용은 저장되지 않습니다.

- 포털 디자이너의 구성 요소 이름과 같은 캔버스에 대한 정보 및 관련 작업은 영어로만 지원됩니다.

- 색상 선택기와 관련 문자열은 영어로만 지원됩니다.

- 직원 셀프 서비스 포털의 일부 템플릿 페이지는 올바른 이동 경로를 렌더링할 수 없습니다.

- 일부 Dynamics 365 포털 템플릿에는 페이지 계층별로 메뉴 항목이 없습니다. 그러나 새 페이지를 작성하면 그에 따라 메뉴 항목이 작성됩니다.