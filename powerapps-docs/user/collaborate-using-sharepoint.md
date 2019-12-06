---
title: SharePoint를 사용 하 여 공동 작업 | Microsoft Docs
description: 모델 기반 앱 내에서 SharePoint를 사용 하 여 공동 작업 하는 방법 알아보기
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 11/20/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 428291712f91e90cea515723a93e1871ec94de2e
ms.sourcegitcommit: 8f32eed48adf4b24b9ca607bbf6db3d19749c46f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418284"
---
# <a name="collaborate-using-sharepoint"></a>SharePoint를 사용하여 공동 작업 

Word, Excel, PowerPoint 등의 일반적인 문서 유형을 관리 하 고 폴더를 만들어 모델 기반 앱 내에서 SharePoint에 원활 하 게 저장 된 문서를 저장 하 고 관리 합니다. 

> [!NOTE]
> 이 기능을 사용 하려면 시스템 관리자가 SharePoint 문서 관리를 사용 하도록 설정 해야 합니다. 추가 정보: [SharePoint를 사용 하 여 문서 관리](/power-platform/admin/manage-documents-using-sharepoint)

계정 및 연락처 레코드의 경우 처음으로 **파일** 탭으로 이동 하 여 SharePoint에서 기본 문서 위치 폴더가 자동으로 생성 됩니다. 다른 표준 또는 사용자 지정 엔터티 레코드의 경우 **관련** > **문서** 탭으로 이동 합니다. 문서 위치의 이름은 < record_name > _ < record_id > 형식입니다.

기본적으로 위치는 기본 사이트 1의 문서로 설정 됩니다.

## <a name="add-a-document"></a>문서 추가
1.  계정 또는 연락처 레코드를 열고 **파일** 탭을 선택 합니다. 문서 관리를 사용 하도록 설정 된 다른 표준 또는 사용자 지정 엔터티의 경우 **관련** 탭을 선택한 다음 **문서**를 선택 합니다.
2.  다음 옵션을 선택 합니다. 
    - 새 문서를 만들려면 **새로**만들기를 선택 하 고 원하는 문서 유형 (예: Word, Excel 또는 OneNote)을 선택한 다음 이름을 입력 합니다. **저장**을 선택합니다. 빈 문서가 새 탭에서 열립니다. 
    - 기존 문서를 추가 하려면 **업로드**, **파일 선택**을 차례로 선택 하 고 원하는 파일을 찾아서 선택한 다음 **열기**를 선택 합니다. **확인**을 선택합니다. 

문서 파일이 **문서 관련 그리드** 보기에 표시 됩니다. 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

이 문서는 SharePoint 사이트 폴더 위치에도 표시 됩니다. 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>SharePoint 위치 관리
모델 기반 앱에서 기존 SharePoint 위치를 새로 만들거나 편집할 수 있습니다.

1. 명령 모음의 **파일** 목록에서 **Open location**을 선택 하 고 위치를 선택 합니다.
2. 위치를 편집 하려면 명령 모음에서 **위치 편집** <location name>를 선택 합니다.
**위치 편집** 대화 상자가 나타납니다.
3. 표시 이름, 부모 사이트 및 폴더 이름이 자동으로 채워집니다. 새 위치에 대 한 세부 정보를 입력 하 고 **저장**을 선택 합니다.
4. 위치를 추가 하려면 명령 모음에서 **위치 추가**를 선택 합니다.
5. **위치 추가** 대화 상자가 나타납니다.

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. 표시 이름, 부모 사이트 및 폴더 이름이 자동으로 채워집니다. 필요한 경우 세부 정보를 변경 하 고 **저장**을 선택 합니다.

## <a name="actions-on-documents"></a>문서에 대 한 작업
문서 목록에서 하나 이상의 문서를 선택 하면 문서에서 다음과 같은 일반적인 SharePoint 작업을 수행할 수 있습니다.
- 編集
- 삭제
- 체크 인
- 혁신적인 프로젝트 팀에서
- 체크 아웃 취소
- プロパティの編集

## <a name="files-tab-faq"></a>파일 탭 FAQ
*문서에 액세스 하는 위치가 이동 된 이유는 무엇 인가요?* 
- 문서를 더 쉽게 찾을 수 있도록 명령을 이동 했습니다.

*문서 탭이 없어진 가요?*
- 아니요, 제거 되지 않습니다. 사용자는 관련 된 메뉴와 문서 링크를 클릭 하기만 하면 이전 방법으로 해당 레코드와 연결 된 문서에 계속 액세스할 수 있습니다.

*변경 내용에도 SharePoint의 하위 폴더가 자동으로 생성 되나요?*
- 可能。 동작은 **관련** 메뉴의 **문서** 링크와 비슷합니다. 사용자가 처음으로 **파일** 탭을 선택 하면 해당 SharePoint 하위 폴더가 시스템에 의해 만들어집니다. 

*다른 엔터티에 파일 탭을 추가 하거나 제거 하는 방법이 있나요?*
- 可能。 파일 탭을 추가 하거나 제거 하려면이 문서의 단계를 수행 합니다. [엔터티에 대 한 기본 폼에 SharePoint 문서 탭 추가](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

*이 변경 내용에 대 한 피드백을 어디에서 보낼 수 있나요?*
- 이 전자 메일 주소에서 Dynamics 365 판매 사무실 및 팀 통합 팀에 피드백을 보낼 수 있습니다. d365_ot_crew@microsoft.com

### <a name="see-also"></a>참고 항목
[Common Data Service와 SharePoint, OneNote 및 OneDrive 통합](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)