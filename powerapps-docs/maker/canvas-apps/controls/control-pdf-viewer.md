---
title: 'PDF 뷰어 컨트롤: 참조 | Microsoft Docs'
description: 속성 및 예제를 비롯한 PDF 뷰어 컨트롤에 관한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f7e1b4ff10a12d454380c394b2f6ae64389bc23e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679733"
---
# <a name="pdf-viewer-control-experimental-in-powerapps"></a>PowerApps의 PDF 뷰어 컨트롤(실험)
PDF 파일의 콘텐츠를 표시하는 실험적 컨트롤입니다.

## <a name="description"></a>설명
이 형식의 컨트롤을 추가하고, **Document** 속성을 표시하려는 파일의 URL(큰따옴표로 묶은)로 설정하여 PDF 파일에 있는 텍스트, 그래픽 및 기타 콘텐츠를 표시합니다.

## <a name="limitations"></a>제한 사항
1. Power Apps의 보안 아키텍처에서 HTTP가 아닌 HTTPS 링크만 지원 하려면 PDF 뷰어가 필요 합니다.  

2. **문서** 속성은 PDF 파일에 직접 연결 해야 합니다. 문서에 대 한 서버 리디렉션 또는 HTML 보기가 지원 되지 않습니다.

3. 문서를 호스트 하는 서버는 인증을 요구 하지 않아야 합니다.

4. 문서를 CORS (원본 간 리소스 공유) 설정이 제한적인 서버에 있는 경우 앱에서 PDF 문서를 볼 수 없습니다. 이 문제를 해결 하려면 PDF 문서를 호스트 하는 서버가 powerapps.com에서 원본 간 요청을 허용 해야 합니다.

앱 사용자는 컨트롤에서 문서를 열 수 없는 경우 메시지가 표시 되 면 외부 브라우저에서 PDF 문서를 열어 이러한 제한을 해결할 수 있습니다. 이 옵션은 모든 외부 문서에 대한 컨트롤 메뉴에서 사용할 수 있습니다.

앱 제작자는 PDF 문서를 앱에 미디어 리소스로 포함 하 여 이러한 제한 사항을 해결할 수 있습니다. 이런 방식으로 PDF 뷰어 컨트롤은 항상 문서를 표시할 수 있습니다.

## <a name="key-properties"></a>주요 속성
**Document** – PDF 파일의 URL(큰따옴표로 묶은)입니다.

## <a name="additional-properties"></a>추가 속성
**ActualZoom** - 컨트롤의 실제 확대/축소이며, **Zoom** 속성으로 요청된 확대/축소와 다를 수 있습니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**CurrentFindText** – 사용 중인 현재 검색어입니다.

**CurrentPage** – 실제로 표시되는 PDF 파일의 페이지 번호입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 사용자 입력을 허용(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[DisabledBorderColor](properties-color-border.md)** – 컨트롤의 **[DisplayMode](properties-core.md)** 속성이 **Disabled**로 설정된 경우 컨트롤의 테두리 색입니다.

**[Fill](properties-color-border.md)** - 컨트롤의 배경색입니다.

**FindNext** – 문서에서 **FindText**의 다른 인스턴스를 찾습니다.

**FindPrevious** – 문서에서 **FindText**의 이전 인스턴스를 찾습니다.

**FindText** – 문서에서 찾을 검색어입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**[HoverBorderColor](properties-color-border.md)** – 사용자가 해당 컨트롤에 마우스 포인터를 올려두는 경우 컨트롤의 테두리 색입니다.

**[OnSelect](properties-core.md)** – 사용자가 앱을 클릭하거나 탭할 때 앱이 응답하는 방법입니다.

**OnStateChange** – 컨트롤의 상태가 변할 때 앱이 응답하는 방식입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 하단 가장자리 사이의 거리입니다.

**[PaddingLeft](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 왼쪽 가장자리 사이의 거리입니다.

**[PaddingRight](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 오른쪽 가장자리 사이의 거리입니다.

**[PaddingBottom](properties-size-location.md)** – 컨트롤의 텍스트와 해당 컨트롤의 상단 가장자리 사이의 거리입니다.

**Page** – 표시하려고 하는 페이지 수입니다.

**PageCount** -문서의 페이지 수입니다.

**[PressedBorderColor](properties-color-border.md)** – 사용자가 컨트롤을 탭하거나 클릭하는 경우 컨트롤의 테두리 색입니다.

**ShowControls** - 오디오 또는 비디오 플레이어에서 재생 단추, 볼륨 슬라이더 등을 표시하는지 및 펜 컨트롤에서 그리기, 삭제 및 지우기 아이콘 등을 표시하는지 여부입니다.

**[Tooltip](properties-core.md)** – 사용자가 마우스로 컨트롤을 가리킬 때 표시되는 설명 텍스트입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시하거나 숨길지 여부를 선택합니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.

**Zoom** – 카메라의 이미지 확대 비율 또는 PDF 뷰어의 파일 보기입니다.

## <a name="example"></a>예

다음 예와 같이 **PDF 뷰어** 컨트롤을 추가하고 **Document** 속성을 PDF 파일의 URL(큰따옴표로 묶인)로 설정합니다.

  **"https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf"**

컨트롤은 PDF 파일을 보여줍니다.

[컨트롤을 추가하고 구성](../add-configure-controls.md)하는 방법을 모르시나요?

## <a name="accessibility-guidelines"></a>접근성 지침

**PDF 뷰어**가 여전히 실험 단계에 있기 때문에 PDF 문서의 일부 접근성 기능이 지원되지 않습니다. 따라서 사용자가 외부 애플리케이션에서 문서를 열 수 있으려면 **ShowControls**를 **true**로 설정해야 합니다.

[WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html) 및 [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/) 표준을 사용하여 접근성 있는 PDF 문서를 만드는 방법을 알아봅니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
* PDF 문서에 제목이 없는 경우 **[레이블](control-text-box.md)** 을 제목을 추가하는 것이 좋습니다. 제목은 **PDF 뷰어** 바로 앞에 배치할 수 있습니다.
