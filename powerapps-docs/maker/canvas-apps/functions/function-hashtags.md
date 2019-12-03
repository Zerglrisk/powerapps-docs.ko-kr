---
title: HashTags 함수 | Microsoft Docs
description: Power Apps의 해시 태그 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a88371e9c151ed097d2c86bcb64121c68a6d62d0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730809"
---
# <a name="hashtags-function-in-power-apps"></a>Power Apps의 해시 태그 함수
텍스트 문자열에서 해시태그(#strings)를 추출합니다.

## <a name="description"></a>설명
**HashTags** 함수는 문자열에서 해시태그를 검색합니다. 해시태그는 파운드 문자(#)로 시작하며 뒤에는 다음과 같은 항목의 조합이 옵니다.

* 대문자와 소문자
* 숫자
* 밑줄
* 통화 기호(예: $)

**HashTags**는 문자열에 해시태그가 포함된 단일 열 [테이블](../working-with-tables.md)을 반환합니다.  문자열에 해시태그가 없으면 이 함수는 [빈](function-isblank-isempty.md) 단일 열 테이블을 반환합니다.

## <a name="syntax"></a>구문
**HashTags**( *String* )

* *String* - 필수 항목입니다.  해시태그를 검색할 문자열입니다.

## <a name="examples"></a>예
### <a name="step-by-step"></a>단계별 가이드
1. **[Text input](../controls/control-text-input.md)** 컨트롤을 추가하고 **Tweet**이라고 이름을 지정하고 다음 문장을 입력합니다.
   
    **This #app is #AMAZING and can #coUnt123 or #123abc but not #1-23 or #$\*(#\@")**
2. 세로 사용자 지정 갤러리를 추가하고 **[Items](../controls/properties-core.md)** 속성을 다음 함수로 설정합니다.
   
    **HashTags(Tweet.Text)**
3. 갤러리 템플릿에 **[Label](../controls/control-text-box.md)** 컨트롤을 추가합니다.
   
    갤러리에 다음 해시태그가 표시됩니다.
   
   * **\#app**
   * **\#AMAZING**
   * **\#coUnt123**
   * **\#123abc**
   * **\#1**

