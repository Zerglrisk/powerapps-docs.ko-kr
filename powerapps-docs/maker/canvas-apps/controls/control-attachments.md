---
title: '첨부 파일 컨트롤: 참조 | Microsoft Docs'
description: 첨부 파일 컨트롤에 대한 속성 및 예제를 포함한 정보
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: abbe0165041aa3fa496bae480fa1235d9c0b159c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727658"
---
# <a name="attachments-control-in-power-apps"></a>Power Apps의 첨부 파일 컨트롤
사용자가 장치에 파일을 다운로드 하 고 SharePoint 목록 또는 Common Data Service 엔터티에서 파일을 업로드 및 삭제할 수 있도록 하는 컨트롤입니다.

## <a name="limitations"></a>제한 사항
첨부 파일 컨트롤에는 이러한 제한 사항이 있습니다.
1. 첨부 파일은 SharePoint 목록 및 Common Data Service 엔터티에서 지원 됩니다.

1. 업로드 및 삭제 기능은 양식 내 에서만 작동 합니다. 첨부 파일 컨트롤은 편집 모드에 있을 때 폼 내에서 사용할 수 없는 상태로 표시 됩니다. 파일 추가 및 삭제를 저장 하려면 앱 사용자가 양식을 저장 해야 합니다. 이러한 제한으로 인해 첨부 파일 컨트롤은 **삽입** 탭에서 사용할 수 없지만 SharePoint 또는 Common Data Service 양식에서 첨부 파일 양식 필드를 사용 하도록 설정 하면 폼에 나타납니다.

1. 10mb 보다 작은 경우에만 파일을 업로드할 수 있습니다.  

## <a name="description"></a>설명
**첨부** 파일 컨트롤을 사용 하면 SharePoint 목록 또는 Common Data Service 엔터티에서 파일을 열고 추가 하 고 삭제할 수 있습니다.

## <a name="key-properties"></a>주요 속성
**[Items](properties-core.md)** – 다운로드할 수 있는 파일을 설명하는 소스입니다.

**MaxAttachments** – 컨트롤에 허용되는 파일의 최대 수입니다.

**MaxAttachmentSize** – 새로운 첨부 파일당 허용되는 최대 파일 크기(MB)입니다.  현재는 10MB의 제한이 있습니다.

**OnAttach** – 사용자가 새 첨부 파일을 추가할 때 앱이 응답하는 방식입니다.

**OnRemove** – 사용자가 기존 첨부 파일을 삭제할 때 앱이 응답하는 방식입니다.

**[OnSelect](properties-core.md)** – 사용자가 첨부 파일을 클릭할 때 앱이 응답하는 방식입니다.

## <a name="additional-properties"></a>추가 속성
**[AccessibleLabel](properties-accessibility.md)** – 화면 읽기 프로그램의 레이블입니다. 첨부 파일의 목적을 설명해야 합니다.

**AddAttachmentText** – 새 첨부 파일을 추가하는 데 사용되는 링크의 레이블 텍스트입니다.

**[BorderColor](properties-color-border.md)** - 컨트롤의 테두리 색입니다.

**[BorderStyle](properties-color-border.md)** - 컨트롤의 테두리는 **Solid**, **Dashed**, **Dotted**, **None**입니다.

**[BorderThickness](properties-color-border.md)** - 컨트롤의 테두리 굵기입니다.

**[DisplayMode](properties-core.md)** – 컨트롤이 파일 추가 및 삭제(**편집**)하거나, 데이터만 표시(**보기**)하거나 사용 안 하도록(**사용 안 함**) 설정할지 선택합니다.

**[FocusedBorderColor](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 색입니다.

**[FocusedBorderThickness](properties-color-border.md)** – 컨트롤에 포커스가 있을 때 컨트롤의 테두리 두께입니다.

**[Height](properties-size-location.md)** – 컨트롤의 위쪽 및 아래쪽 가장자리 사이의 간격입니다.

**MaxAttachmentsText** – 컨트롤이 허용되는 파일의 최대 수를 포함하는 경우 “첨부 파일” 링크를 대체하는 텍스트입니다.

**NoAttachmentsText** – 첨부된 파일이 없는 경우 사용자에게 표시되는 설명 텍스트입니다.

**[TabIndex](properties-accessibility.md)** – 다른 컨트롤에 관련된 키보드 탐색 순서입니다.

**[Visible](properties-core.md)** – 컨트롤을 표시할지 또는 숨길지 여부입니다.

**[Width](properties-size-location.md)** – 컨트롤의 왼쪽 및 오른쪽 가장자리 사이의 간격입니다.

**[X](properties-size-location.md)** – 컨트롤의 왼쪽 가장자리와 해당 부모 컨테이너(또는 부모 컨테이너가 없는 경우 화면)의 왼쪽 가장자리 사이의 거리입니다.

**[Y](properties-size-location.md)** – 컨트롤의 상단 가장자리와 해당 부모 컨테이너(또는 부모 컨테이너가 없는 경우 화면)의 상단 가장자리 사이의 거리입니다.


## <a name="example"></a>예
1. SharePoint 목록을 데이터 원본으로 사용하여 데이터에서 앱을 만듭니다. 대안으로 앱에 양식을 추가하고, SharePoint 목록을 데이터 원본으로 설정합니다.

2. 왼쪽의 트리 뷰에서 **Form** 컨트롤을 선택합니다.

3. 오른쪽의 옵션 패널에 있는 속성 탭에서 **데이터**를 클릭합니다.

4. **필드**에서 **첨부 파일** 필드를 사용하도록 설정합니다.

    SharePoint 목록과 연결된 첨부 파일 필드가 양식에 표시됩니다.

[컨트롤을 추가하고 구성하는 방법을 알아봅니다].(../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="color-contrast"></a>색 대비
다음 사이에 적절한 색 대비가 있어야 합니다.
* **ItemColor** 및 **ItemFill**
* **ItemHoverColor** 및 **ItemHoverFill**
* **ItemPressedColor** 및 **ItemPressedFill**
* **AddedItemColor** 및 **AddedItemFill**
* **RemovedItemColor** 및 **RemovedItemFill**
* **ItemErrorColor** 및 **ItemErrorFill**
* **AddAttachmentColor** 및 **Fill**
* **MaxAttachmentsColor** 및 **Fill**
* **NoAttachmentsColor** 및 **Fill**

이는 [표준 색 대비 요구 사항](../accessible-apps-color.md)에 추가됩니다.

### <a name="screen-reader-support"></a>화면 판독기 지원
다음 속성이 있어야 합니다.
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>키보드 지원
* 키보드 사용자가 탐색할 수 있도록 **[TabIndex](properties-accessibility.md)** 가 0 이상이어야 합니다.
* 포커스 표시기가 명확하게 표시되어야 합니다. **[FocusedBorderColor](properties-color-border.md)** 및 **[FocusedBorderThickness](properties-color-border.md)** 를 사용하여 이를 달성합니다.
