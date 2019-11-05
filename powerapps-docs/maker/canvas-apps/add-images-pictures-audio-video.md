---
title: 캔버스 앱으로 멀티미디어 파일 포함 및 업로드 | Microsoft Docs
description: 캔버스 앱에서 멀티미디어 파일 표시 및 데이터 원본에 업로드
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/12/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 78f091705a01a54b7e6eb008630949796ffac453
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541181"
---
# <a name="using-multimedia-files-in-powerapps"></a>PowerApps에서 멀티미디어 파일 사용

이 항목에서는 캔버스 앱에 멀티미디어 파일을 포함하고, 데이터 원본에 펜 드로잉을 업로드하고, 캔버스 앱에서 데이터 원본의 이미지를 표시하는 방법을 보여 줍니다. 이 토픽에 사용된 데이터 원본은 비즈니스용 OneDrive에서 Excel 파일입니다.

## <a name="prerequisites"></a>필수 조건

PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 사용하여 [로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.

## <a name="add-media-from-a-file-or-the-cloud"></a>파일 또는 클라우드에서 미디어 추가

추가할 미디어 파일의 종류를 선택할 수 있습니다(예: 이미지, 비디오 또는 오디오).

1. **콘텐츠** 탭에서 **미디어**를 선택합니다.

2. **미디어** 아래에서 **이미지**, **비디오** 또는 **오디오**를 선택한 다음 **찾아보기**를 선택합니다.

    ![미디어 찾아보기][1]

3. 추가하려는 파일을 선택한 다음 **열기**를 선택합니다.

    컴퓨터에서 **그림** 폴더가 열리고 여기에서 이미지를 선택하거나 다른 폴더로 이동할 수 있습니다.

4. 파일 추가가 완료되면 Esc 키를 눌러 기본 작업 영역으로 돌아갑니다.

5. **삽입** 탭에서 **미디어**를 선택한 다음 **이미지**, **비디오** 또는 **오디오**를 선택합니다.

    ![미디어 유형 선택][8]

6. 이미지 컨트롤을 추가한 경우 해당 **[Items](controls/properties-visual.md)** 속성을 추가한 파일로 설정합니다.  

    ![이미지 속성 설정](./media/add-images-pictures-audio-video/imageproperty.png)

    > [!NOTE]
   > 작은따옴표 안에 확장명 없이 파일 이름만 지정합니다.

7. 비디오 또는 오디오 컨트롤을 추가한 경우 해당 **Media** 속성을 추가한 파일로 설정합니다.  

    ![미디어 속성 설정](./media/add-images-pictures-audio-video/mediaproperty.png)

    > [!NOTE]
   > 비디오 컨트롤의 **Media** 속성을 큰따옴표로 묶인 적절한 URL로 설정하여 YouTube 비디오를 재생합니다.

## <a name="add-media-from-azure-media-services"></a>Azure Media Services에서 미디어 추가
1. Azure Media Services 계정에서 **AMS > 설정 > 자산**에서 비디오 자산을 업로드하고 게시합니다.

2. 비디오를 게시한 후 해당 URL을 복사합니다.

3. PowerApps의 **삽입 > 미디어**에서 **비디오** 컨트롤을 추가합니다.

4. **미디어** 속성을 복사한 URL로 설정합니다.

    이 그림에서 볼 수 있듯이 Azure Media Services가 지원하는 모든 스트리밍 URL을 선택할 수 있습니다.

    ![미디어 속성 설정](./media/add-images-pictures-audio-video/ams-with-powerapps.png)

## <a name="add-images-from-the-cloud-to-your-app"></a>앱에 클라우드의 이미지 추가
이 시나리오에서는 클라우드 스토리지 계정, 비즈니스용 OneDrive에 이미지를 저장합니다. Excel 테이블을 사용하여 이미지에 대한 경로를 포함하고 앱의 갤러리 컨트롤에서 이미지를 표시합니다.

이 시나리오에서는 일부 .jpeg 파일을 포함하는 [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)을 사용합니다.

> [!NOTE]
> Excel 파일에서 이러한 이미지에 대한 경로는 슬래시를 사용해야 합니다. PowerApps에서 Excel 테이블에 이미지 경로를 저장할 때 경로는 백슬래시를 사용합니다. 이러한 테이블에서 이미지 경로를 사용하는 경우 백슬래시 대신 슬래시를 사용하도록 Excel 테이블에서 경로를 변경합니다. 그렇지 않으면 이미지가 표시되지 않습니다.  

1. [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip)을 다운로드하고 **자산** 폴더를 클라우드 스토리지 계정에 압축 해제합니다.

2. **자산** 폴더의 이름을 **Assets_images**로 바꿉니다.

3. Excel 스프레드시트에서 1열 테이블을 만들고 다음 데이터로 채웁니다.

    ![Jackets 테이블](./media/add-images-pictures-audio-video/jackets.png)

4. 테이블의 이름을 **Jackets**로 지정하고 Excel 파일의 이름을 **Assets.xlsx**로 지정합니다.

5. 앱에서 **Jackets** 테이블을 데이터 원본으로 추가합니다.  

6. **이미지만** 컨트롤을 추가하고(**삽입** 탭 > **갤러리**) 해당 **Items** 속성을 `Jackets`로 설정합니다.  

    ![항목 속성](./media/add-images-pictures-audio-video/items-jackets.png)

    갤러리는 이미지로 자동으로 업데이트됩니다.  

    ![Jacket 이미지](./media/add-images-pictures-audio-video/images.png)

    **Items** 속성을 설정하는 경우 **PowerAppsId**라는 열은 Excel 테이블에 자동으로 추가됩니다.

    Excel 테이블에서 이미지 경로는 이미지에 대한 URL일 수도 있습니다. 예는 [바닥재 견적](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) 샘플 파일입니다. 클라우드 스토리지 계정으로 다운로드하고, 앱에 데이터 원본으로 `FlooringEstimates` 테이블을 추가한 다음, 갤러리 컨트롤을 `FlooringEstimates`로 설정할 수 있습니다. 갤러리가 해당 이미지로 자동으로 업데이트됩니다.

## <a name="upload-pen-drawings-to-the-cloud"></a>클라우드로 펜 드로잉 업로드
이 시나리오에서는 데이터 원본, 비즈니스용 OneDrive에 펜 드로잉을 업로드하는 방법을 알아보고 드로잉이 저장되는 방식을 확인합니다.

1. Excel에서 **Image [image]** 를 셀 A1에 추가합니다.

2. 다음 단계에 따라 테이블를 만듭니다.    

   1. 셀 A1을 선택합니다.

   2. **삽입** 리본에서 **테이블**을 선택합니다.

   3. 대화 상자에서 **내 테이블에 헤더 포함**을 선택한 다음 **확인**을 선택합니다.

       ![테이블 만들기](./media/add-images-pictures-audio-video/create-table.png)

       이제 Excel 파일이 테이블 형식으로 되었습니다. Excel에서 테이블 서식 지정에 대한 자세한 내용은 [데이터를 테이블로 서식 지정](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370)을 참조하세요.

   4. 테이블 이름을 **Drawings**로 지정합니다.

       ![테이블 이름을 Drawings로 바꾸기](./media/add-images-pictures-audio-video/name-media-table.png)

3. Excel 파일을 **SavePen.xlsx**로 비즈니스용 OneDrive에 저장합니다.

4. PowerApps에서 [빈 앱](get-started-create-from-blank.md)을 만듭니다.

5. 앱에서 비즈니스용 OneDrive 계정을 [데이터 원본](add-data-connection.md)으로 추가합니다.

   1. **보기** 탭을 클릭하거나 탭한 다음 **데이터 원본**을 클릭하거나 탭합니다.

       ![](./media/add-images-pictures-audio-video/choose-data-sources.png)

   2. **데이터 원본 추가**를 클릭하거나 탭한 다음 **비즈니스용 OneDrive**를 클릭하거나 탭합니다.

       ![](./media/add-images-pictures-audio-video/select-source.png)

   3. **SavePen.xlsx**를 클릭하거나 탭합니다.

   4. **Drawings** 테이블을 선택한 다음 **연결**을 클릭하거나 탭합니다.

       ![연결할지](./media/add-images-pictures-audio-video/savepen.png)  

       이제 Drawings 테이블은 데이터 원본으로 나열됩니다.

6. **삽입** 탭에서 **텍스트**를 선택한 다음  **펜 입력**을 선택합니다.

7. 새 컨트롤의 이름을 **MyPen**으로 변경합니다.  

    ![바꾸면](./media/add-images-pictures-audio-video/rename-mypen.png)

8. **삽입** 탭에서 **단추** 컨트롤을 추가하고 이 수식에 해당 **OnSelect** 속성을 설정합니다.

    **Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})**

9. **이미지 갤러리** 컨트롤을 추가하고(**삽입** 탭 > **갤러리**) 해당 **Items** 속성을 `Drawings`로 설정합니다. 갤러리 컨트롤의 **Image** 속성은 자동으로 `ThisItem.Image`로 설정됩니다.

    화면이 다음과 같이 표시되도록 컨트롤을 정렬합니다.  

    ![샘플 화면](./media/add-images-pictures-audio-video/screen.png)

10. F5 키를 누르거나 미리 보기( ![미리 보기 단추](./media/add-images-pictures-audio-video/preview.png) )를 선택합니다.

11. MyPen에 무언가를 그린 다음 단추를 선택합니다.

    그린 그림이 갤러리 컨트롤의 첫 번째 이미지에 표시됩니다.

12. 이 그림에 다른 것을 추가하고 단추를 선택합니다.

    그린 그림이 갤러리 컨트롤의 두 번째 이미지에 표시됩니다.

13. Esc 키를 눌러 미리 보기 창을 닫습니다.

    클라우드 스토리지 계정에서 **SavePen_images** 폴더가 자동으로 생성되었습니다. 이 폴더에는 파일 이름에 대한 ID로 저장된 이미지가 포함되어 있습니다. 폴더를 표시하려면 예를 들어, F5 키를 눌러 브라우저 창을 새로 고쳐야 합니다.

    **SavePen.xlsx**에서 **Image** 열은 새 이미지에 대한 경로를 지정합니다.

### <a name="known-limitations"></a>알려진 제한 사항
조직 내에서 Excel 데이터를 공유하는 방법에 대한 자세한 내용은 [이러한 제한 사항을 검토](connections/cloud-storage-blob-connections.md#known-limitations)하세요.

## <a name="for-more-information"></a>자세한 내용은 다음을 참조하세요.
[브라우저 창](https://home.dynamics.com/) 및 휴대폰을 포함하여 다른 플랫폼에서 앱을 테스트해야 합니다.

다른 데이터 원본으로 멀티미디어 직접 업로드와 관련된 고급 시나리오에 대한 자세한 내용은 [이미지 캡처 pro 팁](https://powerapps.microsoft.com/blog/image-capture-pro-tips/) 및 [이미지 업로드에 대한 사용자 지정 커넥터](https://powerapps.microsoft.com/blog/custom-api-for-image-upload/)를 참조하세요.

데이터 원본에 파일을 업로드하는 다른 방법은 [Patch](functions/function-patch.md) 함수를 사용하는 것입니다.

[1]: ./media/add-images-pictures-audio-video/add-image-video-audio-file.png
[3]: ./media/add-images-pictures-audio-video/add-intro-sound.png
[4]: ./media/add-images-pictures-audio-video/add-picture.png
[5]: ./media/add-images-pictures-audio-video/camera-gallery.png
[6]: ./media/add-images-pictures-audio-video/audio-gallery.png
[7]: ./media/add-images-pictures-audio-video/pen-gallery.png
[8]: ./media/add-images-pictures-audio-video/mediaoptions.png
[9]: ./media/add-images-pictures-audio-video/imageproperty.png
[10]: ./media/add-images-pictures-audio-video/mediaproperty.png
[11]: ./media/add-images-pictures-audio-video/renamecamera.png
