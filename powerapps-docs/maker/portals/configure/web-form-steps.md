---
title: 포털에 대한 웹 양식 단계 구성 | MicrosoftDocs
description: 포털에서 웹 양식에 대한 웹 양식 단계를 만드는 방법에 대해 설명합니다.
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760709"
---
# <a name="define-web-form-steps-for-portals"></a>포털에 대한 웹 양식 단계 정의

웹 양식 단계는 단계 및 조건부 분기 같은 사용자 경험 양식의 흐름 논리를 제공합니다. 양식과 추가 동작을 렌더링하는 것에 대한 세부 정보 또한 제공합니다.

> [!NOTE]
> 웹 양식은 웹 양식 세션 엔터티의 개체에 사용자가 방문한 단계의 기록을 유지합니다. 웹 양식의 단계가 수정된 경우 이전에 만든 기록 데이터는 이제 부실 데이터가 됩니다. 단계가 변경될 때마다 모든 웹 양식 세션 레코드를 삭제하여 로그인 기록 단계의 순서와 현재 순서의 충돌을 방지하는 것이 좋습니다.

각 웹 양식은 하나 또는 그 이상의 단계로 포털에 나타납니다. 이 단계들은 아래에 설명된 몇 가지 일반 속성을 공유합니다. 각 단계는 최종 단계를 제외한 다음 단계로의 포인터(조회)를 포함합니다. 최종 단계에는 다음 단계가 없기 때문에 웹 양식의 마지막 단계입니다.(조건부 분기 때문에 여러 최종 단계가 있을 수 있습니다.)

![웹 양식 만들기 단계](../media/web-form-creation-steps.png "웹 양식 만들기 단계")  

| 이름     | 설명                                    |
|----------|------------------------------------------------|
| 이름     | 참조를 위한 제목입니다.                    |
| 웹 양식 | 현재 단계와 연관된 웹 양식입니다. |
|타입|(다음 버전 중 하나)<br>[양식 로드/탭 단계 유형 로드](load-form-step.md): 양식의 속성을 표시합니다. <ul><li>[양식 로드/탭 단계 유형 로드](load-form-step.md): 탭의 속성을 표시합니다.</li><li>[조건부 단계 유형](add-conditional-step.md): 조건부 분기에 대해 평가할 식을 지정하는 속성을 표시합니다. </li><li>[리디렉션 단계 유형](add-redirect-step.md): 웹 사이트 리디렉션 구성에 적합한 설정을 표시합니다.</li></ul><br>이러한 웹 양식 단계 유형의 설정에 대한 자세한 내용은 아래의 해당 섹션을 참조하십시오.<br>**참고**: 첫 단계는 "조건" 유형에 속할 수 없습니다.|
| 다음 단계                  | 현재 단계의 다음 단계입니다. 단일 단계 단일 양식을 위해 비어 있습니다.                                                                                                            |
| 대상 엔터티 논리 이름 | 양식과 연관된 엔터티의 논리 이름입니다.                                                                                                                                               |
| 이전으로 이동 권한    | 여러 단계 웹 양식에서 이전 단계로 이동하는 옵션이 사용자에게 제공되는지 나타냅니다. 기본값은 true입니다. 사용자가 이전 단계로 이동할 수 없도록 하려면 선택을 취소합니다. |
||

### <a name="see-also"></a>참조

[포털 구성](configure-portal.md)  
[엔터티 정의](entity-forms.md)  
[포럼 불러오기/탭 단계 유형 불러오기](load-form-step.md)  
[리디렉션 단계 유형](add-redirect-step.md)  
[조건부 단계 유형](add-conditional-step.md)  
[맞춤 JavaScript 추가](add-custom-javascript.md)  

