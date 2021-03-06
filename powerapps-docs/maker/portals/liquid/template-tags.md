---
title: 포털에 대한 템플릿 태그 사용 | MicrosoftDocs
description: 포털에서 사용 가능한 템플릿 태그에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 951b4055aa47a6fba31df5473bd517ed67c8f17d
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873228"
---
# <a name="template-tags"></a>템플릿 태그

템플릿 태그는 다양한 방법으로 템플릿 출력을 제어하고 여러 템플릿을 단일 출력으로 결합할 수 있습니다.

## <a name="include"></a>include

이름별로 템플릿 한 개의 콘텐츠를 다른 템플릿에 포함시킵니다. Power Apps 포털에서 이 다른 템플릿의 원본은 일반적으로 [웹 템플릿](store-content-web-templates.md)이 됩니다. 이렇게 하면 공통 템플릿 부분을 여러 곳에 다시 사용할 수 있습니다.  

한 템플릿이 다른 템플릿에 포함되어 있으면, 포함된 템플릿에는 상위 템플릿에 정의된 모든 변수에 대한 액세스 권한이 생깁니다.

`{% include 'My Template' %}`

또한 임의 개수의 명명된 매개 변수를 include 태그에 전달할 수 있습니다. 그런 다음, 포함된 템플릿에서 변수로 정의됩니다.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>block

템플릿 상속을 제공하기 위해 extends와 함께 사용됩니다. 사용법은 extends를 참조하십시오.

## <a name="extends"></a>extends

block 태그와 함께 사용되며 템플릿 상속을 제공합니다. 이렇게 하면 상위 레이아웃의 특정 영역을 다시 정의하는 동안 여러 템플릿이 공유 레이아웃을 사용할 수 있습니다.

Power Apps 포털에서 태그에 제공된 상위 템플릿 이름은 일반적으로 [웹 템플릿](store-content-web-templates.md)의 이름을 참조합니다.  

extends가 사용되면 템플릿의 첫 번째 콘텐츠여야 하며, 그 뒤에 하나 이상의 block 태그만 올 수 있습니다.

상위 템플릿에 정의된 블록을 다시 정의하지 않은 경우, 상위 템플릿(있는 경우)의 해당 콘텐츠가 렌더링됩니다.

## <a name="comment"></a>comment

유동 템플릿 내에 렌더링 되지 않은 코드를 둘 수 있습니다. 블록 내 콘텐츠가 렌더링되지 않으며, 블록 내 유동 코드는 실행되지 않습니다.

**코드**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**출력**

`Hello. My name is Charles.`

## <a name="raw"></a>raw

유동 코드를 구문 분석하거나 실행하지 않고도 페이지에 출력할 수 있습니다.

**출력**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>대체

사용자가 머리글 및 바닥글 캐싱을 활성화하고 특정 섹션 출력의 캐싱을 피하려는 경우 이 태그를 사용할 수 있습니다. 이 태그는 래핑된 콘텐츠 블록의 출력이 캐시되지 않는 머리글 또는 바닥글의 콘텐츠 블록을 제공합니다. 이는 사용자가 요청, 페이지, 언어 및 날짜와 같이 자주 업데이트될 수 있는 개체를 사용하는 시나리오에서 유용합니다. 예를 들어, [머리글 및 바닥글 캐싱이 활성화](../configure/enable-header-footer-output-caching.md)된 경우 머리글 및 바닥글 웹 템플릿 원본 코드 업데이트 시나리오를 참조하십시오.

### <a name="see-also"></a>참조

[흐름 통제 태그](control-flow-tags.md)<br>
[반복 태그](iteration-tags.md)<br>
[변수 태그](variable-tags.md)<br>
[Power Apps Common Data Service 엔터티 태그](portals-entity-tags.md)
