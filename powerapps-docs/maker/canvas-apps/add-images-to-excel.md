---
title: Excel에 이미지 추가 | Microsoft Docs
description: 클라우드 스토리지 계정에서 Excel로 이미지 파일 및 펜 그림을 추가하기 위한 단계별 지침
author: adrianorth
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/25/2016
ms.author: aorth
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: af4412e2f098d6e7e5996b2de436b674cfa60a40
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724626"
---
# <a name="add-images-to-excel-from-power-apps"></a>Power Apps에서 Excel에 이미지 추가
사용자가 파일의 이미지 또는 **펜** 컨트롤의 그림을 표시, 추가 또는 삭제할 수 있는 앱을 자동으로 만듭니다. 앱은 클라우드 스토리지 계정에 만들고 업로드하는 Excel 파일을 기반으로 합니다.

## <a name="prerequisites"></a>필수 조건

* [컨트롤 추가 및 구성](add-configure-controls.md)에 익숙합니다.
* [Excel 데이터를 테이블로 구성](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370?ui=en-US&rs=en-US&ad=US)하는 것에 익숙합니다.
* Excel 파일을 저장할 수 있는 클라우드 저장소 계정 (예: Dropbox, OneDrive 또는 Google Drive)에 대 한 [파워 앱 연결](add-data-connection.md) 입니다.

## <a name="create-the-data-source-and-the-app"></a>데이터 원본 및 앱 만들기
1. Excel에서 **자막** 및 **이미지 [이미지]** 를 두 개의 빈 셀 바로 위 두 개의 셀에 나란히(예: A1, B1) 추가합니다.
2. 업데이트한 셀 및 바로 밑에 있는 셀의 서식을 테이블로 지정하고 테이블 이름을 지정합니다(예: **Images**).
   
    ![테이블 만들기](./media/add-images-to-excel/create-table.png)
3. 파일을 저장(예: **ImageDemo**로)하고, 클라우드 스토리지 계정에 업로드합니다.
4. Power Apps에서 **파일** 메뉴에서 **새로 만들기** 를 클릭 하거나 탭 하 고 (앱을 아직 열지 않은 경우 왼쪽 가장자리를 따라), 클라우드 저장소 계정에 대 한 타일에서 **휴대폰 레이아웃** 을 클릭 하거나 탭 합니다.
   
    ![클라우드 스토리지 계정 선택](./media/add-images-to-excel/select-account.png)
5. **Excel 파일 선택**에서 만든 파일을 클릭하거나 탭합니다.
   
    ![통합 문서 선택](./media/add-images-to-excel/select-workbook.png)
6. **표 선택**에서 만든 테이블을 클릭하거나 탭한 다음, **연결**을 클릭하거나 탭합니다.
   
    ![테이블 선택](./media/add-images-to-excel/select-table.png)
7. 둘러보기가 표시되면 선택하거나 **건너뛰기**를 클릭하거나 탭합니다.
   
    ![둘러보기의 첫 번째 화면](./media/add-images-to-excel/quick-tour.png)

## <a name="add-an-image-from-a-file"></a>파일에서 이미지 추가
1. F5 키를 눌러(또는 오른쪽 위 모서리 근처의 재생 단추를 클릭하거나 탭하기) 미리 보기를 연 다음, 오른쪽 위 모서리에 있는 더하기 아이콘을 클릭하거나 탭합니다.
   
    ![더하기 아이콘](./media/add-images-to-excel/plus-icon.png)
2. **자막** 상자에서 추가할 이미지 파일에 대한 짧은 설명을 입력하거나 붙여넣은 다음, 아래를 클릭하거나 탭하여 파일을 지정합니다.
3. **열기** 대화 상자에서 추가하려는 파일을 찾아보고, 클릭하거나 탭한 다음, **열기**를 클릭하거나 탭합니다.
   
    ![자막 및 이미지 추가](./media/add-images-to-excel/add-image.png)
4. 변경 내용을 저장하려면 오른쪽 위 모서리에 있는 확인 표시 아이콘을 클릭하거나 탭합니다.
   
    ![변경 내용 저장](./media/add-images-to-excel/checkmark-icon.png)
5. 마지막 세 단계를 반복하여 원하는 만큼 여러 이미지를 추가한 다음, Esc 키를 눌러 기본 작업 영역으로 돌아갑니다.
6. (선택 사항) 각 이미지에 대한 자막을 표시하는 **레이블** 컨트롤을 삭제합니다.

## <a name="add-a-drawing"></a>그림 추가
1. 왼쪽 탐색 표시줄에서 클릭하거나 탭하여 **EditScreen1**을 표시한 다음, 이미지 카드를 클릭하거나 탭하여 선택합니다.
   
    ![이미지 카드 선택](./media/add-images-to-excel/select-card.png)
2. 오른쪽 창에서 이미지 카드에 대해 카드 선택기를 클릭하거나 탭한 다음 **메모 추가**를 클릭하거나 탭합니다.
   
    ![메모 추가](./media/add-images-to-excel/add-notes.png)
3. 왼쪽 탐색 표시줄에서 클릭하거나 탭하여 **BrowseScreen1**을 표시한 다음, 미리 보기 모드를 엽니다.
4. 오른쪽 위 모서리에서 더하기 아이콘을 클릭하거나 탭하고, 자막을 추가하고, **펜** 컨트롤에서 이미지를 그립니다.
   
    ![그림 그리기](./media/add-images-to-excel/draw-picture.png)
5. 변경 내용을 저장하려면 오른쪽 위 모서리에 있는 확인 표시 아이콘을 클릭하거나 탭합니다.
   
    ![변경 내용 저장](./media/add-images-to-excel/checkmark-icon.png)
6. 마지막 두 단계를 반복하여 원하는 만큼 여러 그림을 추가한 다음, Esc 키를 눌러 기본 작업 영역으로 돌아갑니다.

