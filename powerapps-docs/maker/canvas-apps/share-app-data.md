---
title: 앱에서 사용하는 Excel 파일 공유 | Microsoft Docs
description: Dropbox, OneDrive 및 Google 드라이브에서 Excel 파일을 공유합니다. 사용자는 파일 및 폴더를 편집하고 볼 수 있습니다.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: jamesol
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3348db5897b0c58d7addef775d2a871809fc491b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995212"
---
# <a name="share-excel-data-used-by-your-app"></a>앱에서 사용하는 Excel 데이터 공유
OneDrive와 같은 [클라우드 계정](connections/cloud-storage-blob-connections.md)에서 앱 사용자와 Excel 데이터를 공유할 수 있습니다.

예를 들어 회사에서 기술 지원 그룹의 이름 및 전화 번호를 보여주는 앱을 만들 수 있습니다. 정보는 Dropbox 폴더에 있는 Excel 스프레드시트에 저장됩니다. 그런 다음 이름 및 전화 번호를 확인할 수 있도록 앱 사용자와 폴더를 공유합니다.

사용자가 앱을 실행하고 수정할 수 있도록 데이터를 공유해야 합니다. 공유 권한이 부여되지 않은 사용자는 Excel 파일의 데이터를 확인하지 못합니다.

이 항목에서는 Dropbox, OneDrive 및 Google 드라이브를 사용하여 Excel 스프레드시트의 데이터를 공유하는 방법을 보여줍니다. Excel 파일에서 데이터를 표시하는 앱을 만들려면 [데이터 집합에서 앱 만들기](get-started-create-from-data.md)를 참조하세요.

## <a name="share-data-in-dropbox"></a>Dropbox에서 데이터 공유
1. PowerApps에서 Dropbox로 연결하는 데 사용한 것과 동일한 계정을 사용하여 Dropbox에 로그인합니다.
2. Excel 파일이 포함된 폴더를 선택한 다음 **공유**를 선택합니다.  
   
    ![공유 명령](./media/share-app-data/dropbox-share.png)
3. 대화 상자에서 앱 사용자가 Dropbox에 로그인하는 데 사용한 전자 메일 주소를 입력합니다.  
   
    ![Dropbox에서 공유](./media/share-app-data/dropbox-perms.png)
4. 앱 사용자는 앱의 데이터를 추가, 수정 또는 삭제하는 경우 **편집 가능**을 선택합니다. 그렇지 않은 경우 **보기 가능**을 선택합니다.
5. **공유**를 선택합니다.

자세한 내용은 [Dropbox에서 폴더 공유](https://www.dropbox.com/en/help/19)를 참조하세요.

## <a name="share-data-in-onedrive"></a>OneDrive에서 데이터 공유
1. PowerApps에서 OneDrive로 연결할 때 사용한 것과 동일한 계정을 사용하여 OneDrive에 로그인합니다.
2. 파일이 포함된 폴더를 선택한 다음 **공유**를 선택합니다.  
   
    ![공유 명령](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > 비즈니스용 OneDrive에서 파일이 포함된 폴더가 아니라 파일 자체를 공유합니다.
3. 대화 상자에서 **전자 메일**을 선택합니다.
   
    ![전자 메일로 공유](./media/share-app-data/onedrive-email.png)
4. 앱 사용자가 OneDrive에 로그인하는 데 사용한 전자 메일 주소를 지정하고 **공유**를 선택합니다.  
   
    ![사용자 지정](./media/share-app-data/onedrive-perms.png)

자세한 내용은 [OneDrive 파일 및 폴더 공유](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07)를 참조하세요.

## <a name="share-data-in-google-drive"></a>Google 드라이브에서 데이터 공유
1. PowerApps에서 Google 드라이브로 연결하는 데 사용한 것과 동일한 계정을 사용하여 Google 드라이브에 로그인합니다.
2. Excel 파일을 저장한 폴더를 마우스 오른쪽 단추로 클릭한 다음 **공유**를 선택합니다.  
   
    ![공유 명령](./media/share-app-data/googledrive-share.png)
3. 대화 상자에서 앱 사용자가 Google 드라이브에 로그인하는 데 사용한 전자 메일 주소를 입력합니다.  
   
    ![사용자 지정](./media/share-app-data/googledrive-perms.png)
4. 앱 사용자는 앱의 데이터를 추가, 수정 또는 삭제하는 경우 사용 권한 목록에서 **편집 가능**을 선택합니다. 그렇지 않은 경우 **보기 가능**을 선택합니다.
5. **완료**를 선택합니다.

자세한 내용은 [Google 드라이브 파일 및 폴더 공유](https://support.google.com/drive/answer/2494822)를 참조하세요.

### <a name="known-limitations"></a>알려진 제한 사항
조직 내에서 Excel 데이터를 공유하는 방법에 대한 자세한 내용은 [이러한 제한 사항을 검토](connections/cloud-storage-blob-connections.md#known-limitations)하세요.

