---
title: '서식 있는 텍스트 편집기 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 포함한 서식 있는 텍스트 편집기 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/24/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 26ba133612e1c69ed470984fabafe6a6cdfddb1c
ms.sourcegitcommit: d03915b4e2583327526b448ec10474cedfd7efe0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74550579"
---
# <a name="rich-text-editor-control-in-powerapps"></a>PowerApps의 서식 있는 텍스트 편집기 컨트롤
최종 사용자가 WYSIWYG 편집 영역 내에서 텍스트의 서식을 지정할 수 있습니다.  출력 형식은 HTML입니다.

## <a name="description"></a>설명
**서식 있는 텍스트 편집기** 컨트롤은 앱 사용자에게 텍스트의 서식을 지정하는 WYSIWYG 편집 영역을 제공합니다.  컨트롤의 입력 및 출력 형식은 HTML입니다.

컨트롤을 사용하면 복사된 서식 있는 텍스트(예: 웹 브라우저 또는 Word에서)를 컨트롤에 붙여넣을 수 있습니다.  

컨트롤의 의도된 용도는 텍스트 서식을 지정하는 것이며 입력 HTML의 무결성을 유지하도록 보장하지 않습니다.  모든 스크립트, 스타일, 개체 및 기타 잠재적으로 손상되는 태그는 편집기에서 제거됩니다.  즉, 서식 있는 텍스트가 PowerApps 외부에서 만들어졌으면 만들어진 제품에서와 동일하게 보일 수 없습니다.

현재 지원되는 기능은 다음과 같습니다.
- 굵게, 기울임꼴, 밑줄
- 텍스트 색, 색 강조
- 텍스트 크기
- 번호 매기기 목록, 글머리 목록
- 하이퍼링크
- 서식 지정 지우기

양식 내에서 컨트롤을 사용하려면 "여러 줄 텍스트 편집" 카드를 선택하고 RTE 컨트롤을 삽입하여 사용자 지정합니다.

## <a name="key-properties"></a>주요 속성
**[Default](properties-core.md)** – 편집기에 표시된 초기 텍스트 값에 대한 입력 속성입니다.

**HtmlText** – HTML 형식인 서식 있는 결과 텍스트에 대한 출력 속성입니다.


## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 첨부 파일의 목적을 설명해야 합니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 파일 추가 및 삭제(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**EnableSpellCheck** – 브라우저 맞춤법 검사기를 사용 하도록 설정할지 여부를 지정 합니다. 이 기능은 브라우저의 기본 언어 에서만 맞춤법 검사를 제공 합니다.  Windows 용 Power Apps는이 속성을 지원 하지 않습니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시할지 또는 숨길지 여부입니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(또는 부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(또는 부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="screen-reader-support"></a>화면 판독기 지원
* **[AccessibleLabel](properties-accessibility.md)** 이 있어야 합니다.

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.

> [!TIP]
> 편집기에는 다른 바로 가기 키에 대 한 자세한 내용을 보려면 **Alt + 0** 을 사용 합니다.
