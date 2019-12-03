---
title: '열 컨트롤: 참조 | Microsoft Docs'
description: 이 항목에서는 Microsoft Power Apps의 열 컨트롤에 대 한 정보를 제공 합니다.
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6fcf4d94677a21f013734fedc8a4db70955f40b9
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727461"
---
# <a name="column-control-in-power-apps"></a>Power Apps의 열 컨트롤
[**데이터 테이블**](control-data-table.md) 컨트롤에서 단일 필드에 대한 디스플레이 경험을 제공합니다.

## <a name="description"></a>설명
[**데이터 테이블**](control-data-table.md) 컨트롤은 테이블 형식으로 데이터 세트를 보여주며 테이블 형식의 각 열은 **열** 컨트롤로 나타납니다. **열** 컨트롤은 앱 제작자가 열의 모양과 동작을 사용자 지정하기 위해 사용할 수 있는 속성을 제공합니다.

## <a name="capabilities"></a>기능
### <a name="now-available"></a>지금 사용 가능
* **열** 컨트롤의 너비를 변경합니다.
* **열** 컨트롤의 텍스트를 변경합니다.
* **열** 컨트롤의 값을 클릭하거 눌러 탐색합니다.

### <a name="not-yet-available"></a>아직 사용할 수 없음
* **열** 컨트롤의 스타일을 사용자 지정합니다.

### <a name="known-issues"></a>알려진 문제
* **Visible** 속성이 아직 작동하지 않습니다.

## <a name="properties"></a>속성
* **DisplayName** – 열의 머리글에 나타나는 텍스트입니다.
  
  > [!NOTE]
  > 이 속성의 이름은 곧 **HeaderText**로 변경됩니다.
  > 
  > 
* **IsHyperlink** – 하이퍼링크임을 나타내기 위해 열의 데이터를 밑줄로 표시해야 하는지 나타내는 값입니다.
* [**Width**](properties-size-location.md) – **열** 컨트롤의 왼쪽과 오른쪽 가장자리 사이의 간격입니다.

## <a name="examples"></a>예
### <a name="resize-a-column"></a>열 크기 조정
1. 빈 태블릿 앱을 만듭니다.
2. **삽입** 탭에서 **데이터 테이블**을 클릭하거나 탭하고 전체 화면을 포함하도록 **데이터 테이블** 컨트롤의 크기를 조정합니다.
3. 오른쪽 창에서 **데이터 원본이 선택되지 않음** 오른쪽의 아래 화살표를 클릭하거나 탭하고 **데이터 원본 추가**를 클릭하거나 탭합니다.
4. 연결 목록에서 Common Data Service 데이터베이스에 대한 연결을 클릭하거나 탭합니다.
5. 엔터티 목록에서 **거래처**를 클릭하거나 탭하고 **연결**을 클릭하거나 탭합니다.
   
    **데이터 테이블** 컨트롤이 초기화되고 기본 필드 집합을 보여줍니다.
6. **전체 이름** 열을 클릭하거나 탭합니다.
   
    ![열 컨트롤 선택됨](./media/control-column/pre-resize-column.png)
7. 오른쪽의 표시기를 끌어 필드의 크기를 조정합니다.
   
    ![열 컨트롤 크기 조정됨](./media/control-column/post-resize-column.png)


## <a name="accessibility-guidelines"></a>접근성 지침
### <a name="screen-reader-support"></a>화면 판독기 지원
* **DisplayName**이 있어야 합니다.
