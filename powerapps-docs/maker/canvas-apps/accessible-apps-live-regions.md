---
title: 캔버스 앱의 라이브 영역을 사용 하 여 동적 변경 내용을 발표 | Microsoft Docs
description: 캔버스 앱에서 동적 변경 내용을 화면 읽기 프로그램에 알리기 위해 라이브 영역을 사용 하는 방법
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a886b1c585f4fc07efc29bc1166ce4aca5586b5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61549953"
---
# <a name="announce-dynamic-changes-with-live-regions-for-canvas-apps"></a>캔버스 앱에 대 한 라이브 영역을 사용 하 여 동적 변경 내용을 발표합니다

동적 변경 내용을 시각 장애에 문제가 있습니다. 화면 판독기를 통해 앱에 액세스 하는 사용자가 앱의 한 부분에 초점을 두는 합니다. 변경 내용을 다른 곳에서 발생 하는 경우 해당 사용자의 인식 수 없습니다.

라이브 영역을 추적 하는 화면 읽기 프로그램을 추가 하 여이 문제를 해결할 수 있습니다. 라이브 영역의 콘텐츠가 변경 되 면 화면 판독기는 해당 변경 내용을 발표 합니다.

라이브 영역에 대 한 기본 메커니즘은 [aria 라이브 지역](https://www.w3.org/TR/wai-aria-1.1/#dfn-live-region)이므로 동일한 지침이 적용 됩니다.

## <a name="example-uses-of-live-regions"></a>라이브 영역의 예제에서

사용자에 게 알리는 다음과 같은 이벤트가 발생할 때 라이브 영역을 사용할 수 있습니다.

* 폼에서 유효성 검사 오류가 발생합니다.
* 단추를 트리거한 작업은 성공 합니다. 예를 들어 사용자 컬렉션에 항목을 추가 하는 단추를 선택할 수 및 라이브 영역의 "항목이 추가 되었습니다" 메시지를 표시할 수 있습니다.
* 사용자 다른 탭을 선택 합니다.
* 백그라운드 타이머 뉴스를 피드를 새로 고칩니다.

## <a name="create-and-configure-a-live-region"></a>만들고 라이브 영역 구성

만 구성할 수 있습니다는 **[레이블을](controls/control-text-box.md)** 라이브 영역으로 제어 합니다. 해당 **Live** 속성 것 라이브 영역의 유형을 결정 합니다.

* **해제**: 라이브 영역이 없습니다. 화면 읽기 프로그램 변경 내용을 발표 하지 않습니다.
* **처리 완료 후**: 화면 판독기를 마친 후 변경 내용을 알리기 강연 합니다. 즉각적인 주의가 필요 하지 않은 중요 하지 않은 알림에 대 한이 값을 사용 합니다.
* **Assertive**: 화면 판독기 자체 변경 내용을 즉시 발표를 중단 합니다. 즉각적인 주의가 필요한 중요 한 알림에 사용 합니다.

라이브 영역의 텍스트 콘텐츠가 변경 되 면 변경 된 부분을 뿐 아니라 전체 텍스트 콘텐츠를 화면 판독기에 알리기 때문입니다. 경우 값을 **[텍스트](controls/properties-core.md)** 속성을 빈 문자열로 **""** , 화면 판독기는 아무 것도 발표 하지 않습니다.

메시지를 반복 하려면 값을 설정 하 여 텍스트 내용을 지우려면 합니다 **[텍스트](controls/properties-core.md)** 속성을 빈 문자열로 **""** 다음 값을 메시지 다시 설정 합니다.

## <a name="best-practices"></a>모범 사례

* 항상 설정 **[Visible](controls/properties-core.md)** true로 합니다. 화면 판독기 사라졌다가 다시는 라이브 영역은 검색 하지 않습니다.
* 값을 변경 하지 마십시오  **[Live](controls/properties-accessibility.md)** 합니다. 일부 화면 판독기 아닌 라이브 지역 라이브 되 면 검색 하지 않고 그 반대로 합니다.
* 표시 되지 않는 경우에 라이브 영역의 논리 앱에서 위치에 배치 합니다. 이전 및 이후에 내용이 요소를 사용 하 여 컨텍스트에서 합리적인 되는지 확인 합니다. 사용자가 액세스할 수 있습니다 라이브 영역의 언제 든 지 화면 판독기를 사용 하 여 일반 탐색을 통해 변경 내용이 있을 때가 아니라.

## <a name="next-steps"></a>다음 단계

에 대해 알아봅니다 하는 방법 [콘텐츠를 화면 판독기에만 표시](accessible-apps-content-visibility.md) 보면서 사용자의 라이브 영역의 숨겨야 하는 경우.