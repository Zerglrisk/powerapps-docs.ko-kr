---
title: 클라우드 스토리지 연결 개요 | Microsoft Docs
description: 클라우드 스토리지 계정에 연결하고 앱에서 Excel 데이터를 표시하는 방법 참조
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2da924310d07869972e8d0a9a4b26649d6a56b8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679963"
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>PowerApps에서 클라우드 스토리지에 연결
Power Apps는 여러 클라우드 저장소 연결을 제공 합니다. 이러한 연결을 사용하여 Excel 파일을 저장하고 앱 전체에서 해당 정보를 사용할 수 있습니다. 이러한 연결 항목은 다음과 같습니다.  

| **Azure Blob** | **Box** | **Dropbox** | **Google 드라이브** | **OneDrive** | **비즈니스용 <br>OneDrive** |
| --- | --- | --- | --- | --- | --- |
| ![아이콘](./media/cloud-storage-blob-connections/blobicon.png) |![API 아이콘][boxicon] |![API 아이콘][dropboxicon] |![API 아이콘][googledriveicon] |![API 아이콘][onedriveicon] |![API 아이콘][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* 데이터가 [표로 서식이 지정된](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664) Excel 파일:
  
  1. Excel 파일을 열고 사용하려는 데이터의 모든 셀을 선택합니다.
  2. **삽입** 탭에서 **표**를 선택합니다.
  3. **표 만들기** 대화 상자에서 **머리글 포함** 확인란을 선택한 후 **확인**합니다.
  4. 변경 내용을 저장합니다.

## <a name="connect-to-the-cloud-storage-connection"></a>클라우드 스토리지 연결에 연결합니다.
1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **관리**를 확장하고 **연결**을 선택합니다.  
   
    ![연결 선택](./media/cloud-storage-blob-connections/connections.png)
2. **새 연결**을 선택하고 클라우드 스토리지 연결을 선택합니다. 예를 들어 **OneDrive**를 선택합니다.
3. 클라우드 스토리지 계정의 사용자 이름과 암호를 묻는 메시지가 나타납니다. 입력한 다음 **로그인**을 선택합니다.  
    ![사용자 이름 및 암호를 입력합니다.](./media/cloud-storage-blob-connections/signin.png)
   
    로그인하면 이 연결은 앱 내에서 사용할 준비가 된 것입니다.
4. 앱에서 리본의 **보기** 탭에서 **데이터 원본**을 클릭하거나 탭합니다. 오른쪽 창에서 **데이터 원본 추가**를 클릭하거나 탭하고 클라우드 스토리지 연결을 클릭하거나 누른 다음, Excel 표를 선택합니다.
5. **연결**을 선택합니다.
   
    표는 데이터 원본으로 나열됩니다.
   
    ![Excel 표를 선택합니다.](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > Excel 데이터는 테이블 형식으로 작성되어야 합니다.

## <a name="using-the-excel-data-in-your-app"></a>앱에서 Excel 데이터 사용
1. **삽입** 탭에서 **갤러리**를 선택하고 **텍스트 추가** 갤러리 컨트롤을 선택합니다.
2. 갤러리의 **[항목](../controls/properties-core.md)** 속성을 Excel 표로 설정합니다. 예를 들어, Excel 표의 이름이 **Table1**인 경우 Table1로 설정합니다.  
   
    ![항목 속성](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    갤러리는 Excel 표의 정보로 자동 업데이트됩니다.
3. 갤러리에서 두 번째 또는 세 번째 선택 **레이블** 컨트롤을 선택합니다. 기본적으로 두 번째 및 세 번째 레이블의 **텍스트** 속성이 `ThisItem.something`으로 자동 설정됩니다. 테이블의 모든 열에 이러한 레이블을 설정할 수 있습니다.
   
    다음 예제에서는 두 번째 레이블이 `ThisItem.Name`으로 설정되고 세 번째 레이블이 `ThisItem.Notes`로 설정됩니다.  
   
    ![두 번째 레이블](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![세 번째 레이블](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    샘플 출력:  
    ![두 번째 및 세 번째 레이블](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> 실제로 첫 번째 상자는 이미지 컨트롤입니다. Excel 표에 이미지가 없는 경우 이미지 컨트롤을 삭제하고 그 자리에 레이블을 추가할 수 있습니다. [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 것은 좋은 리소스입니다.

[테이블 및 레코드 이해](../working-with-tables.md)는 자세한 세부 정보와 일부 예제를 제공합니다.  

## <a name="sharing-your-app"></a>앱 공유
[앱](../share-app.md)은 물론, 커넥터와 같은 [리소스](../share-app-resources.md) 및 [데이터](../share-app-data.md)를 조직의 다른 사용자와 공유할 수 있습니다.

Dropbox의 폴더를 공유하려는 경우 공유 폴더를 사용자의 Dropbox 계정에 연결해야 합니다.

Excel 파일과 관련된 커넥터에 [특정 제한 사항](#sharing-excel-tables)이 있습니다.

## <a name="known-limitations"></a>알려진 제한 사항
앱에서 Excel 연결을 사용하려는 경우 **Data type unsupported**(지원되지 않는 데이터 형식) 또는 **Not formatted as a table**(표로 서식 지정 안 됨)이 나타날 경우 [표로 데이터를 서식 지정](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)합니다.

Excel 데이터에 계산 열이 포함된 경우에는 앱을 빌드하는 데 사용할 수 없으며, 해당 데이터를 기존 앱에 추가할 수도 없습니다.

### <a name="sharing-excel-tables"></a>Excel 표 공유
Excel 파일에서 데이터를 공유하려면 다음을 수행합니다.

* 비즈니스용 OneDrive에서는 파일 자체를 공유합니다.
* OneDrive에서는 파일이 있는 폴더를 공유하고 어떠한 미디어에 대해서도 URL이 아닌 파일 경로를 지정합니다.
* Dropbox 또는 Google 드라이브에서 파일 또는 폴더를 공유합니다.

## <a name="helpful-links"></a>유용한 링크
[사용 가능한 연결](../connections-list.md)을 모두 보세요.  
앱에 [연결 추가](../add-manage-connections.md) 및 [데이터 원본 추가](../add-data-connection.md) 방법을 알아보세요.  
테이블 형식의 데이터 원본과 함께 [테이블 및 레코드를 이해](../working-with-tables.md)합니다.  
몇 가지 추가 갤러리 리소스에는 [항목 목록 표시](../add-gallery.md) 및 [갤러리에 이미지 및 텍스트 표시](../show-images-text-gallery-sort-filter.md)가 있습니다.

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
