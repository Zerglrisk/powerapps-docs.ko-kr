---
title: 포털에 템플릿 태그 사용 | MicrosoftDocs
description: 포털에서 사용할 수 있는 템플릿 태그에 대해 알아보기
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2820c556ab8e469e8f583cc78da0450b66cc84ef
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976418"
---
# <a name="template-tags"></a>템플릿 태그

템플릿 태그는 다양 한 방식으로 템플릿의 출력을 제어 하 고 여러 템플릿을 단일 출력으로 조합할 수 있습니다.

## <a name="include"></a>되어야

한 템플릿의 내용을 이름으로 다른 템플릿에 포함 합니다. PowerApps 포털에서이 다른 템플릿의 원본은 일반적으로 [웹 템플릿이](store-content-web-templates.md)됩니다. 이를 통해 여러 위치에서 공통 템플릿 조각을 재사용할 수 있습니다.  

템플릿이 다른에 포함 된 경우 포함 된 템플릿은 부모 템플릿에 정의 된 변수에 액세스할 수 있습니다.

`{% include 'My Template' %}`

또한 포함 된 매개 변수를 포함 태그에 전달할 수 있습니다. 그런 다음 포함 된 템플릿에서 변수로 정의 됩니다.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>거부

를와 함께 사용 하 여 템플릿 상속을 제공 합니다. 사용량에 대 한 확장을 참조 하세요.

## <a name="extends"></a>제어할

블록 태그와 함께 사용 되어 템플릿 상속을 제공 합니다. 이렇게 하면 여러 템플릿에서 부모 레이아웃의 특정 영역을 재정의 하면서 공유 레이아웃을 사용할 수 있습니다.

PowerApps 포털에서 태그에 제공 되는 부모 템플릿 이름은 일반적으로 [웹 템플릿의](store-content-web-templates.md)이름을 참조 합니다.  

확장을 사용 하는 경우 템플릿의 첫 번째 콘텐츠 여야 하 고 하나 이상의 블록 태그 다음에만 올 수 있습니다.

부모 템플릿에 정의 된 블록이 재정의 되지 않으면 부모 템플릿 (있는 경우)의 내용이 렌더링 됩니다.

## <a name="comment"></a>주석의

렌더링 되지 않은 코드를 액체 템플릿 내에서 벗어날 수 있습니다. 블록 내의 모든 콘텐츠는 렌더링 되지 않으며 내의 모든 액체 코드는 실행 되지 않습니다.

**Code**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**출력**

`Hello. My name is Charles.`

## <a name="raw"></a>미처리

페이지에서 도구를 구문 분석 하 고 실행 하지 않고도 액체 코드를 출력할 수 있습니다.

**출력**

`Hello, {{ user.fullname }}. My name is Charles.`

### <a name="see-also"></a>참고 항목

[제어 흐름 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[PowerApps common data service 엔터티 태그](portals-entity-tags.md)
