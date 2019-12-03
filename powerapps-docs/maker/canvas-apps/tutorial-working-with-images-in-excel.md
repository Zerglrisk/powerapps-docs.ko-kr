---
title: Excel 파일에 이미지 저장 | Microsoft Docs
description: 클라우드 스토리지 계정의 Excel 테이블에 이미지를 저장하는 방법
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/15/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5ee1d56e6144f0c7f4e1b3ca440063f87b7bdc5d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733080"
---
# <a name="how-to-save-images-in-an-excel-file-and-then-add-these-images-to-your-app"></a>이미지를 Excel 파일에 저장한 다음 앱에 추가하는 방법

이 자습서에서는 다음 작업을 수행합니다.

* Excel 파일을 만들고 이를 테이블 형식으로 지정합니다.
* 비즈니스용 OneDrive에 대한 연결을 만듭니다. 모든 클라우드 스토리지 계정이 작동합니다. 이 연습에서는 비즈니스용 OneDrive가 사용됩니다.
* 펜 입력 컨트롤이 있는 앱을 만듭니다.
* 펜 입력 컨트롤에서 만든 이미지를 Excel 파일에 저장합니다.
* 앱에서 Excel 파일의 이미지를 표시합니다.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]
* [데이터 원본을 추가](add-data-connection.md)하는 방법을 알아봅니다.

## <a name="create-the-excel-file-as-a-table"></a>Excel 파일을 테이블로 만들기

1. 빈 Excel 파일에서 열 이름을 **Image [image]** 로 지정합니다.
2. 다음 단계에 따라 테이블를 만듭니다.    
   
   1. 행과 열의 데이터에 대한 모든 부분을 선택합니다. 예를 들어 **Image**를 선택합니다.
   2. **삽입** 리본에서 **테이블**을 선택합니다.
   3. 대화 상자 창에서 **테이블에 머리글 있음**을 선택하고 **확인**을 선택합니다.
      
      이제 Excel 파일이 테이블 형식으로 되었습니다. [데이터를 테이블 형식으로 지정](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370)에서 Excel의 테이블 형식 지정에 대한 추가 세부 정보를 제공합니다.
   4. 테이블 이름을 **Drawings**로 지정합니다.  
      
      ![테이블 이름을 Drawings로 바꾸기](./media/tutorial-working-with-images-in-excel/drawings-table.png)
3. Excel 파일의 이름을 **SavePen.xlsx**로 지정하고, 클라우드 스토리지 계정(비즈니스용 OneDrive, Dropbox 등)에 해당 파일을 저장합니다.

## <a name="create-an-app-with-the-pen-control"></a>펜 컨트롤이 있는 앱 만들기
1. Power Apps에서 [빈 앱](get-started-create-from-blank.md)을 만듭니다.
2. 앱에서 클라우드 스토리지 계정을 [데이터 원본](add-data-connection.md)으로 추가합니다. 데이터 원본으로 추가되면 **SavePen.xlsx**를 연결로 추가한 다음 **Drawings** 테이블을 선택합니다.  
   ![연결](./media/tutorial-working-with-images-in-excel/savepen.png)  
   
   이제 Drawings 테이블이 데이터 원본으로 나열됩니다.
3. **삽입** 메뉴에서 **텍스트**를 선택한 다음, **펜 입력**을 선택합니다. 이름을 **MyPen**으로 바꿉니다.  
   
   ![바꾸면](./media/tutorial-working-with-images-in-excel/rename-mypen.png)
4. **단추** 컨트롤(**삽입** 메뉴)을 추가하고, **OnSelect** 속성을 다음 수식으로 설정합니다.  
   `Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})`
5. **이미지 갤러리** 컨트롤(**삽입** 메뉴 > **갤러리**)을 추가하고 **Items** 속성을 `Drawings`로 설정합니다. 갤러리 컨트롤의 **Image** 속성은 자동으로 `ThisItem.Image`로 설정됩니다.
   
   화면은 다음과 비슷하게 표시됩니다.  
   
   ![샘플 화면](./media/tutorial-working-with-images-in-excel/screen.png)  
6. F5 키를 누르거나 미리 보기(![](./media/tutorial-working-with-images-in-excel/preview.png))를 선택합니다. MyPen에 무언가를 그린 다음 단추를 선택합니다. 그린 그림이 갤러리 컨트롤의 첫 번째 이미지에 표시됩니다. 이 그림에 다른 것을 추가하고 단추를 선택합니다. 그린 그림이 갤러리 컨트롤의 두 번째 이미지에 표시됩니다.
   
   미리 보기 창을 닫습니다.
7. 클라우드 스토리지 계정으로 이동합니다. 자동으로 만든 새 **SavePen_images** 폴더가 있습니다. 새 폴더를 보려면 화면을 새로 고쳐야 할 수도 있습니다. 이 폴더에는 파일 이름에 대한 ID로 저장된 이미지가 포함되어 있습니다.
   
    SavePen.xlsx를 엽니다. '이미지' 열에는 이러한 새 이미지의 경로가 포함되어 있습니다.

## <a name="add-the-image-in-an-excel-file-to-your-app"></a>Excel 파일의 이미지를 앱에 추가
또 다른 예로, 클라우드 스토리지 계정에 이미지를 저장한 다음, 앱에서 Excel 테이블을 사용하여 이미지를 표시할 수 있습니다.

이 예제에서는 일부 .jpeg 파일이 포함된 [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)을 사용합니다.

> [!NOTE]
> Excel 파일의 이미지를 표시할 때 이러한 이미지에 대한 경로에는 슬래시를 사용해야 합니다. Power Apps에서 이미지를 Excel 테이블에 저장 하는 경우 (이전 단계와 마찬가지로) 경로는 백슬래시를 사용 합니다. 따라서 이전 예제의 **SavePen_images**를 사용할 수도 있습니다. 이 경우 Excel 테이블의 경로에서 백슬래시 대신 슬래시를 사용하도록 변경합니다. 그렇지 않으면 이미지가 표시되지 않습니다.  

1. [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)을 다운로드하고 **자산** 폴더를 클라우드 스토리지 계정에 압축 해제합니다.
2. Excel 스프레드시트에서 다음과 비슷한 테이블을 만듭니다.
   
    ![Jackets 테이블](./media/tutorial-working-with-images-in-excel/jackets.png)
3. 테이블의 이름을 **Jackets**로 지정합니다. Excel 파일 이름을 **Assets.xlsx**로 지정합니다. **Assets** 폴더의 이름을 **Assets_images**로 바꿀 수도 있습니다.
4. 앱에서 **Jackets** 테이블을 데이터 원본으로 추가합니다.  
5. **이미지만** 컨트롤(**삽입** 메뉴 > **갤러리**)을 추가하고 **Items** 속성을 `Jackets`로 설정합니다.  
   
    ![항목 속성](./media/tutorial-working-with-images-in-excel/items-jackets.png)
   
    갤러리는 이미지로 자동으로 업데이트됩니다.  
   
    ![Jacket 이미지](./media/tutorial-working-with-images-in-excel/images.png)

Items 속성을 설정하면 Excel 테이블이 **PowerAppsId**라는 새 열로 자동으로 업데이트됩니다.

Excel 테이블에서 이미지 경로는 이미지에 대한 URL일 수도 있습니다. 클라우드 스토리지 계정에 [바닥재 견적](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) 샘플 파일을 다운로드하고, 앱에서 `FlooringEstimates` 테이블을 데이터 원본으로 추가한 다음, 갤러리 컨트롤을 `FlooringEstimates`로 설정합니다. 갤러리가 해당 이미지로 자동으로 업데이트됩니다.

## <a name="learn-more"></a>자세한 정보
[이미지, 비디오 또는 사운드 추가](add-images-pictures-audio-video.md)  
[앱에서 꺾은선형, 원형 또는 막대형 차트로 데이터 표시](use-line-pie-bar-chart.md)  
[Power Apps의 테이블 및 레코드 이해](working-with-tables.md)

