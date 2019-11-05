---
title: 포털에 대 한 웹 양식 단계 구성 | MicrosoftDocs
description: 포털에서 웹 폼에 대 한 웹 양식 단계를 만드는 지침을 설명 합니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c81cddb771c98ccecf2be206ab45a8271ff3559d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551235"
---
# <a name="define-web-form-steps-for-portals"></a>포털에 대 한 웹 양식 단계 정의

웹 양식 단계는 단계 및 조건부 분기와 같은 폼의 사용자 환경에 대 한 흐름 논리를 제공 합니다. 또한 폼의 렌더링과 추가 동작에 대 한 세부 정보도 제공 합니다.

> [!NOTE]
> Web Forms는 사용자가 Web Form 세션 엔터티의 개체에서 방문한 단계의 기록을 유지 합니다. 웹 양식의 단계가 수정 된 경우 이전에 만든 기록 데이터는 이제 유효 하지 않게 됩니다. 단계가 변경 될 때마다 모든 Web Form 세션 레코드를 삭제 하 여 기록에 기록 된 단계 시퀀스와 현재 시퀀스 사이에 누락 된 일치 항목을 제거 하는 것이 좋습니다.

각 웹 양식은 포털에 하나 이상의 단계가 표시 됩니다. 이러한 단계는 아래에 설명 된 몇 가지 공통 속성을 공유 합니다. 각 단계에는 다음 단계에 대 한 포인터 (조회)가 포함 되어 있습니다. 단, 터미널 단계는 예외입니다. 터미널 단계는 다음에는 없으며, 그에 따라 웹 폼의 마지막 단계 (조건부 분기로 인해 여러 터미널 단계가 있을 수 있음)

![웹 폼을 만드는 단계](../media/web-form-creation-steps.png "웹 폼을 만드는 단계")  

| 이름     | 설명                                    |
|----------|------------------------------------------------|
| 이름     | 참조에 사용 되는 제목입니다.                    |
| 웹 폼 | 현재 단계와 연결 된 웹 폼입니다. |
|유형|다음 중 하나를 사용합니다.<br>[양식 로드/로드 탭 단계 유형](load-form-step.md): 폼의 속성을 표시 합니다. <ul><li>[양식 로드/로드 탭 단계 유형](load-form-step.md): 탭의 속성을 표시 합니다.</li><li>[조건부 단계 유형](add-conditional-step.md): 조건부 분기에 대해 평가할 식을 지정 하는 속성을 표시 합니다. </li><li>[단계 유형 리디렉션](add-redirect-step.md): 웹 사이트 리디렉션을 구성 하는 데 적합 한 설정을 표시 합니다.</li></ul><br>이러한 웹 양식 단계 유형의 설정에 대 한 자세한 내용은 아래 해당 섹션을 참조 하세요.<br>**참고**: 첫 번째 단계는 "Condition" 형식일 수 없습니다.|
| 다음 단계                  | 현재 단계를 수행 하는 단계입니다. 단일 단계 단일 폼의 경우이 값은 비어 있습니다.                                                                                                            |
| 대상 엔터티 논리적 이름 | 폼과 연결 된 엔터티의 논리적 이름입니다.                                                                                                                                               |
| 이전에 허용 된 이전 이동    | 사용자에 게 여러 단계의 웹 폼에서 이전 단계를 탐색 하는 옵션이 제공 되는지 여부를 나타냅니다. 기본값은 true입니다. 사용자가 이전 단계로 이동할 수 없도록 하려면 선택 취소 합니다. |
||

### <a name="see-also"></a>참고 항목

[포털 구성](configure-portal.md)  
[엔터티 정의](entity-forms.md)  
[양식 로드/로드 탭 단계 유형](load-form-step.md)  
[단계 유형 리디렉션](add-redirect-step.md)  
[조건부 단계 유형](add-conditional-step.md)  
[사용자 지정 JavaScript 추가](add-custom-javascript.md)  

