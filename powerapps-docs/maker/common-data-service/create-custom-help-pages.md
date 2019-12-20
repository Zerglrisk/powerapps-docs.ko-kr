---
title: 사용자 지정 도움말 페이지 만들기 | MicrosoftDocs
description: UCI에서 사용자 지정 도움말 페이지 만들기
ms.custom: ''
ms.date: 09/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: ''
author: matthewbolanos
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 25ad6206fb76c1c26f182c4ff4b67c8815e7e8ba
ms.sourcegitcommit: 94aa6fd38aab1e145e0b9a0189154fb69b0ee223
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "2778952"
---
# <a name="create-guided-help-for-your-unified-interface-app"></a>통합 인터페이스 앱의 문제 해결 도우미 만들기

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

사용자 지정 도움말 창과 단계별 작업을 사용하여 통합 인터페이스 애플리케이션에 조직에 맞는 맞춤형 제품 내 도움말 환경을 제공하십시오. 사용자 지정 도움말 창을 사용하여 서식 있는 텍스트, 콘텐츠 링크, 이미지 및 비디오 링크가 포함된 엔터티, 양식 및 언어별 도움말 및 지침을 제공하십시오. 

> [!IMPORTANT]
> 사용자 지정 도움말 창은 레거시 웹 클라이언트 앱에 사용된 이전의 학습 경로 단계별 학습 기능을 대체합니다.

## <a name="custom-help-panes-and-learning-path"></a>사용자 지정 도움말 창 및 학습 경로
사용자 지정 도움말 창의 새로운 안내식 도움말 구현은 이전의 학습 경로 문제 해결 도우미 기능과 다릅니다. 두 기능 모두 애플리케이션에 대한 사용자 지정 도움말을 만들 수 있습니다. 그러나 사용자 지정 도움말 창은 가장 일반적인 문제 해결 도우미 시나리오에 최적화되어 있습니다.   

사용자 지정 도움말 창은 학습 경로에서 사용할 수 없는 다음과 같은 주요 기능을 제공합니다. 
- 글머리 기호 및 번호 매기기를 포함한 자유 형식의 서식 있는 텍스트.
- 눈에 띄게 연결된 코칭 표시와 도움말 풍선.
- 비공개 소스를 포함한 비디오 소스에 대한 추가 옵션.
- 솔루션의 일부로 Common Data Service에 있는 도움말 콘텐츠의 저장소. 

사용자 지정 도움말 창은 학습 경로에서 사용할 수 있는 다음과 같은 주요 기능을 제공하지 않습니다. 
- 순차적인 도움말 풍선.
- 역할별 도움말 페이지.
- 스마트폰과 같은 기기별 폼 팩터에 대한 도움말 페이지. 

## <a name="prerequisites"></a>필수 구성 요소 
사용자 지정 도움말 창을 작성하려면 다음이 필요합니다. 
- 버전 9.1.0.10300 이상.
- **도움말 페이지**에서 전역 만들기, 읽기, 쓰기, 삭제, 추가 및 권한에 추가 권한. 기본적으로 시스템 관리자 및 시스템 사용자 지정자 보안 역할에 모두 이 권한이 있습니다.  
- [사용자 환경에서 사용자 지정 도움말 창이 활성화되어 있어야 합니다.](#enable-custom-help-panes-for-your-environment)

## <a name="enable-custom-help-panes-for-your-environment"></a>환경에서 사용자 지정 도움말 창 사용
1. 모델 기반 앱을 연 다음 명령 모음에서 **설정** ![설정](../model-driven-apps/media/powerapps-gear.png) > **고급 설정**을 선택합니다.
2. **설정** > **시스템** > **관리**로 이동합니다.  
3. **관리** 페이지에서 **시스템 설정**을 선택합니다.
4. **일반** 탭의 **사용자 지정 도움말 URL 설정** 아래에서 **사용자 지정 도움말 창 및 단계별 작업 사용**에 대해 **예**를 선택한 다음 **확인**을 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![사용자 지정 도움말 창 사용](media/enable-custom-help-panes.png "사용자 지정 도움말 창 사용")

> [!IMPORTANT]
> 사용자 지정 도움말 창 또는 사용자 지정 가능한 도움말을 사용할 수 있으며 동시에 둘 다 사용할 수는 없습니다. **사용자 지정 가능한 엔터티에 대한 사용자 지정 도움말 사용** 및 **URL에 매개 변수 추가**가 모두 **아니요**로 설정된 것을 확인합니다.  
 
## <a name="context-sensitive-custom-help"></a>상황에 맞는 사용자 지정 도움말
각 도움말 창은 다음과 같은 상황에서 고유합니다. 
- 응용 프로그램 
- 엔터티
- 양식 
- Language   

## <a name="help-pane-navigation"></a>도움말 창 탐색
기본적으로 도움말 창은 열려 있고 다른 양식으로 이동할 때도 처음으로 연 도움말 콘텐츠에 있습니다. 이를 통해 사용자를 앱의 다른 부분으로 안내할 때도 도움말 콘텐츠가 그대로 유지됩니다. 

### <a name="to-author-help-pane-content"></a>도움말 창 콘텐츠를 작성하려면
1.  도움말 창을 보려면 모델 기반 앱을 연 다음 명령 모음에서 **도움말**을 선택합니다. 

    ![도움말](media/help-command.png)   
2.  도움말 창에서 세로 줄임표를 선택한 다음 **편집**을 선택합니다. 

    ![도움말 편집](media/help-edit-command.png)
    
    도움말 창은 이제 편집 모드에 있으며 커서는 도움말 창 제목에 있습니다.
3.  편집 창에서 다음 작업을 수행할 수 있습니다. 
    - 도움말 창 영역에 직접 텍스트를 입력합니다. 
    - 굵게, 기울임꼴, 취소선과 같은 서식 있는 텍스트 명령을 사용하여 텍스트의 서식을 지정하고 목록을 만듭니다. 
    - **삽입** 탭을 선택하여 섹션, 비디오, 이미지, 링크, 코칭 표시 및 풍선 도움말을 추가합니다. 
<!-- confirm the image is safe for use
    > [!div class="mx-imgBorder"] 
    > ![Custom help pane edit](media/custom-help-pane-edit.png)  -->
4.  변경 내용을 저장하려면 **저장**을 선택합니다.  

### <a name="free-form-text"></a>자유 형식 텍스트
텍스트는 도움말 창의 아무 곳에나 배치할 수 있습니다. 섹션 앞, 안, 또는 뒤에 자유 형식의 텍스트를 입력하십시오. 텍스트는 굵게, 기울임꼴, 밑줄 및 취소선 글꼴 형식을 지원합니다. 다단계 실행 취소뿐만 아니라 잘라내기, 복사 및 붙여넣기를 사용할 수 있습니다. 

### <a name="bullets-and-numbered-lists"></a>글머리 기호 및 번호 매기기 목록
글머리 기호 또는 숫자 아이콘을 선택하면 현재 줄이 글머리 기호 또는 번호 매기기로 전환됩니다. 목록에서 여러 줄을 선택한 경우 각 줄은 글머리 기호 또는 번호가 매겨집니다. Tab 사용과 들여쓰기는 목록 내의 한 줄 아래에 번호를 붙입니다.  

### <a name="sections"></a>섹션
섹션은 축소할 수 있는 텍스트 상자입니다.  링크나 자유 형식의 텍스트를 넣을 수 있습니다. 섹션을 사용하여 유사한 항목을 그룹화하십시오. 섹션은 기본적으로 열거나 축소할 수 있습니다. 

### <a name="video-and-static-images"></a>비디오 및 정적 이미지
도움말 창에 비디오 및 정적 이미지를 삽입할 수 있습니다. 비디오 및 이미지는 인터넷 콘텐츠에 대한 링크입니다. 사용자 지정 도움말 창은 비디오 및 이미지 파일을 도움말 창에 저장하지 않습니다. 도움말 창이 열리면 사용자 지정 도움말 창이 콘텐츠를 링크에서 가져와서 표시합니다. 회사의 비공개 콘텐츠를 참조하려는 경우 Microsoft Stream 비디오에 대한 링크를 사용할 수 있습니다. 

> [!TIP]
> 도움말 창에 붙여 넣을 수 있도록 원하는 비디오 또는 이미지의 링크 URL을 복사하십시오. 

사용자 지정 도움말 창은 다음 비디오 소스를 지원합니다.
- Microsoft Stream(비공개 콘텐츠에 사용) 
- YouTube
- Facebook
- Vimeo


### <a name="links"></a>연결
링크는 웹 사이트로 연결할 수 있으며 동일한 창에서 열거나(기본값) 별도의 창에서 열 수 있습니다. 기존 도움말 페이지에 연결하는 기능은 아직 활성화되어 있지 않습니다.   

### <a name="balloons-and-coach-marks"></a>풍선과 코칭 표시
풍선과 코칭 표시를 사용하여 특정 UI 요소를 가리킬 수 있습니다. 풍선은 텍스트를 포함할 수 있습니다. 코칭 표시는 단순히 코칭 포인터로 요소를 강조 표시합니다. 여러 UI 요소를 순차적으로 나타내는 방법은 사용자가 선택할 수 있는 목록에서 링크를 수집하는 것입니다. 예:

1. 지침이나 설명이 있는 첫 번째 UI 요소에 연결.
2. 지침이나 설명이 있는 두 번째 UI 요소에 연결.
3. 지침이나 설명이 있는 세 번째 UI 요소에 연결.

사용자는 요소를 순서대로 선택하거나 특정 요소로 돌아가 강조 표시할 수 있습니다.

## <a name="solutions-and-custom-help-pane-content"></a>솔루션 및 사용자 지정 도움말 창 콘텐츠
모든 도움말 콘텐츠는 솔루션의 일부로 Common Data Service 도움말 페이지 구성 요소에 저장됩니다. 테스트 환경에서 프로덕션 환경과 같이 솔루션을 한 환경에서 다른 환경으로 이동할 때 도움말 레코드가 솔루션에 포함되도록 이러한 레코드를 내보내도록 정의할 수 있습니다. 이를 통해 도움말 콘텐츠가 다른 환경으로 이동할 때 솔루션의 기능과 이를 동기화할 수 있습니다. 솔루션의 일부로 사용자 지정 도움말 창은 모든 표준 솔루션 애플리케이션 수명 주기 관리(ALM) 기능을 지원합니다.

### <a name="moving-content-via-solutions"></a>솔루션을 통한 콘텐츠 이동
기본적으로 모든 새 도움말 페이지가 기본 솔루션에 나타납니다. 콘텐츠를 다른 환경으로 이동하려면 먼저 기존 도움말 페이지를 비관리형 솔루션에 추가한 후 내보내십시오. 비관리형 솔루션에 도움말 페이지를 추가하려면 다음 단계를 수행하십시오.

1. 비관리형 솔루션으로 이동합니다.
2. 명령 모음의 줄임표에서 **클래식으로 전환**을 선택합니다.
3. **기존 항목 추가**를 선택합니다.
4. **도움말 페이지**를 선택합니다.
5. 추가할 도움말 페이지를 선택한 다음 **확인**을 선택합니다.

> [!NOTE]
> 현재 최신 솔루션 탐색기에서 비관리형 솔루션에 기존 도움말 창을 추가할 수 없습니다. 


## <a name="help-page-documentation-automation"></a>도움말 페이지 문서 자동화
소스 코드 제어 시스템에 콘텐츠를 백업하거나 저장할 수 있습니다. 도움말 창 콘텐츠에 번역 도구나 검사기와 같은 설명서 자동화 도구를 사용할 수도 있습니다. 사용자 지정 도움말 창 데이터는 Common Data Service에 바로 저장되며 이러한 목적으로 내보내고 가져올 수 있습니다.  

사용자 지정 도움말 창은 사용자 지정 XML 형식을 지원합니다. 이 형식은 아래에 설명되어 있습니다. 추가 정보: [사용자 지정 도움말 XML 정의](#custom-help-xml-definition)  

내보낼 때 각 도움말 페이지는 별도의 파일로 내보내집니다.   

## <a name="frequently-asked-questions"></a>질문과 대답
이 섹션에서는 사용자 지정 도움말 페이지에 대한 질문과 대답을 설명합니다. 

### <a name="are-custom-help-pages-the-same-as-customizable-help"></a>사용자 지정 도움말 페이지는 사용자 지정 가능한 도움말과 동일합니까?

사용자 지정 도움말 창 및 단계별 작업은 시스템 설정의 **사용자 지정 도움말 URL 설정** 섹션에 있는 옵션입니다. 사용자 지정 도움말 창 및 단계별 작업을 통해 사용자의 양식 바로 옆에 표시되는 사용자 지정 가능한 도움말 창을 사용할 수 있습니다.  이 시스템 설정 사용자 지정 도움말 섹션의 다른 옵션은 사용자 지정 가능한 도움말 기능으로 구성되어 있습니다. 이는 기본 앱 도움말 값을 다시 정의하고 조직의 사용자가 도움말에 대한 다른 URL을 가리킬 수 있도록 합니다. 또는 워크플로를 더 잘 설명할 수 있도록 고도로 사용자 지정 가능한 엔터티에 대한 도움말을 다시 정의할 수 있습니다.

사용자 지정 도움말에 대한 자세한 내용은 [사용자 지정 가능한 도움말 활성화 및 사용](../model-driven-apps/use-customizable-help.md)을 참조하십시오.


### <a name="how-do-i-migrate-my-data-from-learning-path-to-custom-help-pages"></a>학습 경로에서 사용자 지정 도움말 페이지로 데이터를 어떻게 마이그레이션합니까? 
학습 경로에는 도움말 창과 순차적 도움말 풍선이라는 두 가지 유형의 도움말이 있습니다. 순차적인 도움말 풍선 위치는 레거시 웹 클라이언트 UI와 긴밀하게 통합되어 있으며 새 사용자 지정 도움말 창으로 이전할 수 없습니다.  

문제 해결 도우미에 있는 텍스트의 양에 따라 학습 경로 사용자 인터페이스에서 새로운 사용자 지정 도움말 창 사용자 인터페이스로 정보를 직접 복사하는 것이 가장 쉬울 수 있습니다. 그러나 학습 경로 도움말 콘텐츠를 내보낼 수도 있습니다.  가장 간단한 방법은 **학습 경로** > **콘텐츠 라이브러리** > **지역화** > **내보내기** 기능을 사용하여 콘텐츠를 내보내는 것입니다. 추가할 레코드를 선택하여 내보냅니다. 그러면 각 도움말 창 및 단계별 작업에 대한 XLIFF 파일이 생성됩니다.  그런 다음 공개적으로 사용 가능한 XLIFF 편집기 또는 XLIFF에서 HTML로의 변환기를 사용하여 콘텐츠를 검색하십시오. 

## <a name="custom-help-xml-definition"></a>사용자 지정 도움말 XML 정의
이 섹션에서는 사용자 지정 도움말 XML 정의에 대해 설명합니다. 

### <a name="pphml"></a>PPHML

```
<pphml>
    <h1>FAQ</h1>
    <collapsible title="What is PPHML?">
        <p>PPHML is a domain specific language for help content. It is used to create help content that includes elements such as images, videos, balloons, coach marks, etc.</p>
    </collapsible>
    <collapsible title="What does PPHML stand for?">
        <p>PPHML stands for Power Platform Help Markup Language</p>
    </collapsible>
</pphml>
```

#### <a name="definition-and-usage"></a>정의와 사용법

`<pphml>` 요소는 도움말 브라우저에 이것이 PPHML 문서임을 알려줍니다.

`<pphml>` 요소는 PPHML 문서의 루트를 나타냅니다.

`<pphml>` 요소는 다른 모든 PPHML 요소의 컨테이너입니다.

### <a name="title"></a>제목
도움말 페이지에 제목을 표시합니다.

```
<h1>This will be displayed at the top of the help page</h1>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<h1>`** 요소는 도움말 페이지의 제목을 정의합니다.

`<h1>` 이는 `<pphml>` 내부의 첫 번째 요소여야 합니다.

### <a name="image"></a>이미지
도움말 페이지에 이미지를 표시합니다.

```
<img src="smiley.gif" alt="Smiley face" title="Smiley face"/>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<img>`** 요소는 도움말 페이지에 이미지를 포함합니다.

#### <a name="attributes"></a>특성
- `src`: 이미지의 URL을 지정합니다. 이 특성은 필수입니다.

- `title`: 일반적으로 가리키기 도구 설명으로 이미지와 함께 표시할 제목을 지정합니다.

- `alt`: 이미지의 대체 텍스트를 지정합니다. 이 텍스트는 스크린 리더에서 사용됩니다.

### <a name="video"></a>비디오
도움말 페이지에 비디오를 표시합니다.

```
<video src="https://www.youtube.com/watch?v=WSWmn7WM3i4" />
```

#### <a name="definition-and-usage"></a>정의와 사용법

**`<video>`** 요소는 자습서 또는 학습 동영상과 같은 비디오를 도움말 페이지에 포함합니다.

##### <a name="supported-sources"></a>지원되는 소스

- Microsoft Stream
- YouTube
- Facebook
- Vimeo

#### <a name="attributes"></a>특성
- `src`: 비디오의 URL을 지정합니다. 이 특성은 필수입니다.

- `allowFullScreen`: 사용자가 비디오를 전체 화면으로 전환할 수 있는지 여부를 지정합니다. 가능한 값은 "true" 또는 "false"입니다. 이 특성은 모든 비디오 소스에서 지원되지는 않습니다.

- `autoplay`: 도움말 페이지가 로드되는 즉시 비디오 재생을 시작하도록 지정합니다. 가능한 값은 "true" 또는 "false"입니다. 이 특성은 모든 비디오 소스에서 지원되지는 않습니다.

- `startTime`: 비디오 재생을 시작할 시점을 초 단위로 지정합니다.

### <a name="paragraph"></a>단락
도움말 페이지에 단락을 표시합니다.

```
<p>This is some text in a paragraph.</p>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<p>`** 요소는 단락을 정의합니다.

단락 안의 텍스트는 다음과 같은 방식으로 꾸밀 수 있습니다.
- `<strong>` 요소를 사용하여 굵게
- `<em>` 요소를 사용하여 기울임꼴
- `<del>` 요소를 사용하여 취소선
- `<u>` 요소를 사용하여 밑줄

이 장식들은 결합할 수 있습니다. 예를 들어, 굵고 밑줄이 있는 텍스트 조각을 만들 수 있습니다.

### <a name="bulleted-list"></a>글머리 기호 목록
도움말 페이지에 글머리 기호 목록을 표시합니다.

```
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<ul>`** 요소는 글머리 기호 목록을 정의합니다.

`<ul>` 요소를 `<li>` 요소와 함께 사용하여 글머리 기호 목록을 만듭니다.

### <a name="numbered-list"></a>번호 매기기 목록
도움말 페이지에 번호 매기기 목록을 표시합니다.

```
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<ol>`** 요소는 순서가 지정된(번호 매기기) 목록을 정의합니다.
`<ol>` 태그를 `<li>` 요소와 함께 사용하여 번호 매기기 목록을 만듭니다.

### <a name="collapsible"></a>축소 가능
도움말 페이지에 축소 가능 섹션을 표시합니다.

```
<collapsible title="This is a Section">
    <p>This is a paragraph inside a section</p>
    <img src=smiley.gif" title="This is an image inside a section" />
</collapsible>
```

#### <a name="definition-and-usage"></a>정의와 사용법
**`<collapsible>`** 요소는 사용자가 요청 시 보거나 숨길 수 있는 콘텐츠 섹션을 정의합니다.

#### <a name="attributes"></a>특성
- `collapsed`: 섹션이 처음에 축소 또는 확장되는지 여부를 지정합니다. 가능한 값은 "true"(축소됨) 또는 "false"(확장됨)입니다.

### <a name="link"></a>링크
도움말 페이지에 링크를 표시합니다.

새 브라우저 창에서 열리는 웹 사이트에 연결:

```
<a href="https://www.microsoft.com" target="_blank">Microsoft Home Page</a>
```

다른 도움말 페이지로 연결:

```
<a href="./LearnMore">Learn More</a>
```

#### <a name="definition-and-usage"></a>정의와 사용법
`<a>` 태그는 사용자가 도움말 페이지에서 웹 사이트 또는 다른 도움말 페이지로 이동할 수 있는 링크를 정의합니다.

#### <a name="attributes"></a>특성

- `href`: 탐색할 웹 사이트 또는 도움말 페이지의 URL을 지정합니다. 이 특성은 필수입니다.
- `target`: 링크된 URL을 열 위치를 지정합니다.
   - 존재하지 않거나 `_self`인 경우 링크는 다른 도움말 페이지로 가정되며 도움말 브라우저에서 열립니다.
   - `_blank`인 경우 링크가 새 브라우저 창에서 열립니다.
   - `_top`인 경우 링크가 현재 브라우저 창에서 열립니다.
   - 값이 `iframe`의 이름인 경우 링크가 해당 iframe에서 열립니다.

### <a name="coach-mark"></a>코칭 표시
도움말 페이지에 코칭 표시를 표시합니다.

```
<coachmark target="#my-html-button">Click to highlight the HTML element with id [my-html-button]</coachmark>
```

#### <a name="definition-and-usage"></a>정의와 사용법
코칭 표시는 대화형 요소로, 도움말 브라우저를 호스팅하는 애플리케이션 UI의 특정 지점으로 사용자의 주의를 끌 수 있습니다.

#### <a name="attributes"></a>특성

- `target`: 코칭 표시가 표시될 HTML 요소를 지정하는 [CSS 선택기](https://www.w3schools.com/cssref/css_selectors.asp). 이 특성은 필수입니다.

### <a name="balloon"></a>풍선
도움말 페이지에 풍선을 표시합니다.

```
<balloon target="#my-html-button" title="This button submits the form" details="Please click this button to continue and submit the form">Click to show a balloon over the HTML element with id [my-html-button]</balloon>
```

#### <a name="definition-and-usage"></a>정의와 사용법
풍선은 대화형 요소로, 도움말 브라우저를 호스팅하는 애플리케이션 UI에서 사용자가 특정 작업을 수행하는 것을 돕습니다.

#### <a name="attributes"></a>특성
- `target`: 풍선 링크가 표시될 HTML 요소를 지정하는 CSS 선택기. 이 특성은 필수입니다.
- `title`: 풍선의 제목을 지정합니다.
- `details`: 풍선 안에 표시할 콘텐츠를 지정합니다.


