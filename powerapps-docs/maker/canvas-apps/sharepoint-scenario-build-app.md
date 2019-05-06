---
title: 프로젝트를 관리하는 캔버스 앱 만들기 | Microsoft Docs
description: 이 작업에서는 캔버스 앱을 처음부터 빌드합니다. 이 앱을 통해 사용자는 관리자를 프로젝트에 할당하고 프로젝트 세부 정보를 업데이트할 수 있습니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5125299c969db635a9e260ea7bac28f6a6e02bc0
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61542313"
---
# <a name="create-a-canvas-app-to-manage-projects"></a>프로젝트를 관리하는 캔버스 앱 만들기
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악해야 합니다.

이 작업에서는 캔버스 앱을 처음부터 빌드합니다. 이 앱을 통해 사용자는 관리자를 프로젝트에 할당하고 프로젝트 세부 정보를 업데이트할 수 있습니다. 첫 번째 앱에서 본 것과 동일한 컨트롤과 수식이 표시되지만 이번에는 더 많은 앱을 직접 빌드합니다. 프로세스가 더 복잡하지만 자세히 설명하겠습니다.

> [!TIP]
> 이 시나리오에 대한 [다운로드 패키지](https://aka.ms/o4ia0f)에는 이 앱의 완성된 버전인 project-details-app.msapp이 포함되어 있습니다.

## <a name="quick-review-of-powerapps-studio"></a>PowerApps Studio에 대한 빠른 검토
PowerPoint에서 슬라이드 모음을 만드는 것처럼 PowerApps Studio에는 앱을 만들 수 있는 3개 창 및 리본 메뉴가 있습니다.

1. 왼쪽 탐색 모음 - 화면의 썸네일뿐만 아니라 앱의 모든 화면과 컨트롤에 대한 계층적 보기를 보여 줍니다.
2. 가운데 창 - 작업 중인 앱 화면이 포함되어 있습니다.
3. 오른쪽 창 - 레이아웃 및 데이터 원본과 같은 옵션을 설정합니다.
4. 속성 드롭다운 목록 - 수식이 적용되는 속성을 선택합니다.
5. 수식 입력줄 - Excel처럼 앱 동작을 정의하는 수식을 추가합니다.
6. 리본 - 컨트롤을 추가하고 디자인 요소를 사용자 지정합니다.

![PowerApps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>1 단계: 화면 만들기
검토를 마쳤으면 앱 빌드를 시작하겠습니다.

### <a name="create-and-save-the-app"></a>앱 만들기 및 저장
1. PowerApps Studio에서 **새로 만들기**를 클릭하거나 탭한 다음, **빈 앱** 아래에서 **전화 레이아웃**을 클릭하거나 탭합니다.
   
    ![빈 앱 - 전화 레이아웃](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. **파일**을 클릭하거나 탭하여 **앱 설정** 탭을 엽니다. "프로젝트 관리 앱"이라는 이름을 입력합니다.
   
    ![앱 이름](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. **다른 이름으로 저장**을 클릭하거나 탭하고, 앱이 클라우드에 저장되는지 확인한 다음, 오른쪽 아래 모서리에서 **저장**을 클릭합니다.
   
    ![클라우드에 저장](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. 우측 상단 모서리의 ![클릭하거나 탭하여](./media/sharepoint-scenario-build-app/icon-back-to-app.png) 앱으로 돌아갑니다.

### <a name="add-four-screens-to-the-app"></a>앱에 4개 화면 추가
이 단계에서는 앱에 대한 4개의 빈 화면을 만듭니다. 화면의 용도에 따라 별개의 화면 레이아웃을 사용합니다. 이후 단계에서 이러한 화면을 추가합니다.

| **화면** | **용도** |
| --- | --- |
| **SelectTask** |시작 화면, 다른 화면으로 이동 |
| **AssignManager** |승인된 프로젝트에 관리자 할당 |
| **ViewProjects** |요약 정보와 함께 프로젝트 목록 표시 |
| **UpdateDetails** |프로젝트 세부 정보 표시 및 업데이트 |

1. **홈** 탭에서 **새 화면**, **스크롤 가능 화면**을 차례로 클릭하거나 탭합니다.
   
    ![스크롤 가능 화면](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. 화면의 이름을 **SelectTask**로 바꿉니다.
   
    ![화면 이름 바꾸기](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. 추가 화면을 만들고 이름을 바꿉니다.
   
   1. **새 화면**, **스크롤 가능 화면**을 차례로 클릭하거나 탭합니다. 화면의 이름을 **AssignManager**로 바꿉니다.
   2. **새 화면**, **목록 화면**을 차례로 클릭하거나 탭합니다. 화면의 이름을 **ViewProjects**로 바꿉니다.
   3. **새 화면**, **양식 화면**을 차례로 클릭하거나 탭합니다. 화면의 이름을 **UpdateDetails**로 바꿉니다.
4. **Screen1** 옆에 있는 줄임표(**. . .**)를 선택한 다음 **삭제**를 클릭하거나 탭합니다.
   
    ![삭제 화면](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

앱은 이제 다음 이미지와 같습니다.

![모든 앱 화면](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>2 단계: SharePoint 목록에 연결
이 단계에서는 **제품 세부 정보** SharePoint 목록에 연결합니다. 이 앱에서는 하나의 목록만 사용하지만, 앱을 확장하려는 경우 둘 다에 쉽게 연결할 수 있습니다.

1. 왼쪽 탐색 모음에서 **SelectTask** 화면을 클릭하거나 탭합니다.
2. 오른쪽 창에서 **데이터 원본 추가**를 클릭하거나 탭합니다.
   
    ![데이터에 연결](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. **새 연결**을 클릭하거나 탭합니다.
   
    ![새 연결](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. **SharePoint**를 클릭하거나 탭합니다.
   
    ![SharePoint 연결](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. **직접 연결(클라우드 서비스)** 을 선택한 다음 **만들기**를 클릭하거나 탭합니다.
   
    ![직접 연결(클라우드 서비스)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. SharePoint URL을 입력한 다음을 클릭하거나 **이동**을 클릭하거나 탭합니다.
   
    ![연결을 위한 SharePoint URL](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. **프로젝트 세부 정보** 목록을 선택한 다음 **연결**을 클릭하거나 탭합니다.
   
    ![프로젝트 세부 정보 목록 선택](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    이제 오른쪽 창의 **데이터 원본** 탭에 사용자가 만든 연결이 표시됩니다.
   
    ![데이터 원본 탭](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>3 단계: SelectTask 화면 빌드
이 단계에서는 PowerApps에서 제공하는 컨트롤, 수식 및 서식 옵션 중 일부를 사용하여 앱의 다른 화면으로 이동하는 방법을 제공합니다.

### <a name="update-the-title-and-insert-introductory-text"></a>제목 업데이트 및 설명 텍스트 삽입
1. 왼쪽 탐색 모음에서 **SelectTask** 화면을 선택합니다.
2. 가운데 창에서 기본 **[제목]** 을 선택한 다음, 수식 입력줄에서 **Text** 속성을 "Contoso 프로젝트 관리"로 업데이트합니다.
   
    ![수식 입력줄의 Text 속성](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. **삽입** 탭에서 **레이블**을 클릭하거나 탭한 다음, 레이블을 위쪽 배너 아래로 끕니다.
   
    ![레이블 추가](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. 수식 입력줄에서 레이블에 대해 다음 속성을 설정합니다.
   
   * **Color** 속성 = **DarkGray**

   * **Size** 속성 = **18**

   * **Text** 속성 = **"계속하려면 작업을 클릭하거나 탭합니다..."**
     
     ![레이블 텍스트 업데이트](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>두 개의 탐색 단추 추가
1. **삽입** 탭에서 **단추**를 클릭하거나 탭한 다음, 단추를 레이블 아래로 끕니다.
   
    ![단추 추가](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. 수식 입력줄에서 단추에 대해 다음 속성을 설정합니다.
   
   * **OnSelect** 속성 = **Navigate(AssignManager, Fade)**. 앱을 실행하고 이 단추를 클릭하면 앱에서 화면 간의 페이드 전환을 통해 두 번째 화면으로 이동합니다.

   * **Text** 속성 = **"관리자 할당"**

3. 텍스트에 맞게 단추의 크기를 조정합니다.
   
    ![업데이트 단추 텍스트](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. 다음 속성이 있는 다른 단추를 삽입합니다.
   
   * **OnSelect** 속성 = **Navigate(ViewProjects, Fade)**.

   * **Text** 속성 = **"세부 정보 업데이트"**
     
     ![업데이트 단추 텍스트](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > 단추에는 **세부 정보 업데이트**라는 레이블이 있지만, 먼저 **ViewProjects** 화면으로 이동하여 업데이트할 프로젝트를 선택합니다.

### <a name="run-the-app"></a>앱 실행
아직은 많은 작업을 수행할 수 없는 앱이지만 원하는 경우 실행할 수 있습니다.

1. **SelectTask** 화면을 클릭하거나 탭합니다(앱은 항상 PowerApps Studio의 미리 보기 모드에서 선택한 화면에서 시작합니다).

2. 우측 상단 모서리의 ![앱 실행 아이콘](./media/sharepoint-scenario-build-app/icon-run-arrow.png) 을 클릭하거나 탭하여 앱을 실행합니다.

3. 단추 중 하나를 클릭하거나 탭하여 다른 화면으로 이동합니다.

4. 을 클릭하거나 탭하여 ![앱 미리 보기 닫기 아이콘](./media/sharepoint-scenario-build-app/icon-close-preview.png) 앱을 닫습니다.

## <a name="step-4-build-the-assignmanager-screen"></a>4단계: AssignManager 화면 빌드
이 단계에서는 갤러리를 사용하여 승인되었지만 아직 관리자가 없는 모든 프로젝트를 표시합니다. 다른 컨트롤을 추가하여 관리자를 지정할 수 있습니다.

> [!NOTE]
>  나중에 앱에서 관리자 필드를 포함하여 프로젝트에 대한 모든 필드를 편집할 수 있는 페이지를 빌드하지만, 다음과 같은 화면을 빌드하는 것도 좋을 것입니다.

1. 지금까지 변경한 내용을 저장합니다.

2. 왼쪽 탐색 모음에서 **AssignManager** 화면을 클릭하거나 탭합니다.

### <a name="update-the-title-and-insert-introductory-text"></a>제목 업데이트 및 설명 텍스트 삽입

1. **[제목]** 을 **관리자 할당**으로 변경합니다.

2. 다음 속성이 있는 레이블을 추가합니다.
   
   * **Color** 속성 = **DarkGray**

   * **Size** 속성 = **18**

   * **Text** 속성 = **"프로젝트를 선택한 다음 관리자를 할당합니다."**
     
     ![관리자 할당 레이아웃](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask 화면으로 돌아가는 뒤로 화살표 추가

1. 화면 위쪽에서 파란색 막대를 클릭하거나 탭합니다.

2. **삽입** 탭에서 **아이콘**을 클릭하거나 탭한 다음, **왼쪽**을 클릭하거나 탭합니다.
   
    ![왼쪽 화살표 삽입](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. 화살표를 파란색 막대의 왼쪽으로 이동하고, 다음 속성을 설정합니다.
   
   * **Color** 속성 = **White**

   * **Height** 속성 = **40**

   * **OnSelect** 속성 = **Navigate(SelectTask, Fade)**

   * **Width** 속성 = **40**
     
     ![뒤로 단추 추가](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>갤러리 추가 및 수정

1. **삽입** 탭에서 **갤러리**를 클릭하거나 탭한 다음, **세로**를 클릭하거나 탭합니다.
   
    ![세로 갤러리 추가](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. 오른쪽 창의 **레이아웃** 메뉴에서 **제목, 부제목, 본문**을 선택합니다. 
   
    ![갤러리 레이아웃 변경](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    이제 갤러리에 올바른 레이아웃이 있지만 여전히 기본 샘플 텍스트가 있습니다. 다음으로 이 문제를 해결하겠습니다.
   
    ![기본 텍스트가 있는 갤러리](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. 갤러리에 대해 다음 속성을 설정합니다.
   
   * **BorderThickness** 속성 = **1**

   * **BorderStyle** 속성 = **Dotted**

   * **Items** 속성 = **Filter('프로젝트 세부 정보', PMAssigned="할당되지 않음")**. 관리자가 할당되지 않은 프로젝트만 갤러리에 포함됩니다.
     
     ![목록에서 텍스트가 있는 갤러리](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. 오른쪽 창에서 다음 목록과 일치하도록 필드를 업데이트합니다.
   
   * **ApprovedDate**

   * **Status**

   * **Title**
     
     ![갤러리 필드](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. 갤러리의 레이블 크기를 적절히 조정하고, 첫 번째 갤러리 항목에서 화살표를 제거합니다(이 갤러리에서 아무 곳도 탐색할 필요가 없음).
   
    ![화살표 아이콘 제거](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    이제 화면은 다음 이미지와 같습니다.
   
    ![서식이 지정된 갤러리](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>선택한 항목의 색 변경

1. 갤러리를 선택한 다음 **TemplateFill** 속성을 **If (ThisItem.IsSelected=true, Orange, White)** 로 설정합니다.

2. 갤러리에서 항목을 선택합니다. 이제 화면은 다음 이미지와 같습니다.
   
    ![선택한 항목이 있는 갤러리](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>레이블, 텍스트 입력 및 확인 단추를 추가하여 관리자 할당 제출

1. 작업하고 있는 갤러리 외부를 클릭하거나 탭합니다.

2. **삽입** 탭에서 **레이블**을 클릭하거나 탭합니다. 갤러리 아래의 레이블을 왼쪽으로 끕니다. 레이블에 대해 다음 속성을 설정합니다.
   
   * **Size** 속성 = **20**

   * **Text** 속성 = **"관리자:"**
   
   ![관리자 레이블 추가](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. **삽입** 탭에서 **텍스트**, **텍스트 입력**을 차례로 클릭하거나 탭합니다. 갤러리 아래의 텍스트 입력을 가운데로 끕니다. 드롭다운에 대해 다음 속성을 설정합니다.
   
   * **Default** 속성 = **""**

   * **Height** 속성 = **60**

   * **Size** 속성 = **20**

   * **Width** 속성 = **250**
   
   ![텍스트 입력 추가](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. **삽입** 탭에서 **단추**를 클릭하거나 탭합니다. 갤러리 아래의 단추를 오른쪽으로 끕니다. 단추에 대해 다음 속성을 설정합니다.
   
   * **Height** 속성 = **60**

   * **OnSelect** 속성 = **Patch (' 프로젝트 세부 정보 ', LookUp (' 프로젝트 세부 정보 ', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})**. 자세한 내용은 [수식 심층 분석](#formula-deep-dive)을 참조하세요.

   * 이 수식은 **프로젝트 세부 정보** 목록을 업데이트하고 PMAssigned 필드에 대한 값을 설정합니다.

   * **Size** 속성 = **20**

   * **Text** 속성 = **"확인"**

   * **Width** 속성 = **80**
   
   ![확인 단추 추가](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

이제 완성된 화면은 다음 이미지와 같습니다.

![완성된 관리자 할당 화면](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>5단계: ViewProjects 화면 빌드
이 단계에서는 **ViewProjects** 화면에서 갤러리에 대한 속성을 변경합니다. 이 갤러리에는 **프로젝트 세부 정보** 목록의 항목이 표시됩니다. 이 화면에서 항목을 선택한 다음, **UpdateDetails** 화면에서 세부 정보를 편집합니다.

1. 왼쪽 탐색 모음에서 **ViewProjects** 화면을 클릭하거나 탭합니다.

2. **[제목]** 을 **"프로젝트 보기"** 로 변경합니다.

3. 왼쪽 탐색 모음에서 **ViewProjects** 아래의 **BrowserGallery1**을 클릭하거나 탭합니다.

4. 오른쪽 창의 **레이아웃** 메뉴에서 **제목, 부제목, 본문**을 선택합니다. 
   
    ![갤러리 레이아웃 변경](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    이제 갤러리에는 기본 샘플 텍스트가 있는 올바른 레이아웃이 있습니다.
   
    ![기본 텍스트가 있는 갤러리](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. 새로 고침 단추 ![새로 고침 아이콘](./media/sharepoint-scenario-build-app/icon-refresh.png)을 선택하고, **OnSelect** 속성을 **Refresh('프로젝트 세부 정보')** 로 설정합니다.

6. 새 항목 단추 ![새 아이콘 추가](./media/sharepoint-scenario-build-app/icon-add-item.png)를 선택하고, **OnSelect** 속성을 **NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)** 으로 설정합니다.

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask 화면으로 돌아가는 뒤로 화살표 추가

1. 왼쪽 탐색 모음에서 **AssignManager** 화면을 클릭하거나 탭합니다.

2. 여기에 추가한 뒤로 화살표를 선택하고 복사합니다.

3. 화살표를 **ViewProjects** 화면에 붙여넣고, 새로 고침 단추의 왼쪽에 배치합니다. 
   
    ![뒤로 단추](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    **Navigate(SelectTask, Fade)** 의 **OnSelect** 속성을 포함하여 모든 속성이 함께 제공됩니다.

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>BrowseGallery1 갤러리에 대한 데이터 원본 변경

1. **BrowseGallery1** 갤러리를 선택하고, 갤러리의 **Items** 속성을 **SortByColumns(Filter('프로젝트 세부 정보', StartsWith(Title, TextSearchBox1.Text)), "제목", If(SortDescending1, Descending, Ascending))** 으로 설정합니다.
   
    이렇게 하면 갤러리의 데이터 원본이 **프로젝트 세부 정보** 목록에 설정되고 **Title** 필드가 검색 및 정렬에 사용됩니다.

2. 첫 번째 갤러리 항목에서 ![세부 정보 화살표 아이콘](./media/sharepoint-scenario-build-app/icon-details-arrow.png)을 선택하고, **OnSelect** 속성을 **Navigate(UpdateDetails, None)** 으로 설정합니다.
   
    ![ 프로젝트 보기 갤러리 - 선택된 첫 번째 항목](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. 오른쪽 창에서 다음 목록과 일치하도록 필드를 업데이트합니다.
   
   * **Status**

   * **PMAssigned**

   * **Title**
     
     ![갤러리 필드](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     이제 완성된 화면은 다음 이미지와 같습니다.
     
     ![완성된 프로젝트 보기 화면](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>6 단계: UpdateDetails 화면 빌드
이 단계에서는 **UpdateDetails** 화면의 편집 양식을 데이터 원본에 연결하고, 일부 속성 및 필드를 변경합니다. 이 화면에서 **프로젝트 보기** 화면에서 선택한 프로젝트에 대한 세부 정보를 편집합니다.

1. 왼쪽 탐색 모음에서 **UpdateDetails** 화면을 클릭하거나 탭합니다.

2. **[제목]** 을 **"세부 정보 업데이트"** 로 변경합니다.

3. 왼쪽 탐색 모음에서 **UpdateDetails** 아래의 **EditForm1**을 클릭하거나 탭합니다.

4. 양식에 대해 다음 속성을 설정합니다.
   
   * **DataSource** 속성 = **'프로젝트 세부 정보'**

   * **Item** 속성 = **BrowseGallery1.Selected**

5. 양식이 선택되어 있는 상태에서 오른쪽 창에 표시된 순서대로 다음 필드의 확인란을 클릭하거나 탭합니다.
   
   * **Title**

   * **PMAssigned**

   * **Status**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![양식 편집 필드](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. 취소 단추 ![취소 아이콘](./media/sharepoint-scenario-build-app/icon-cancel.png)을 선택하고, **OnSelect** 속성을 **ResetForm(EditForm1); Back()** 으로 설정합니다.

7. 저장 단추 ![저장 확인 표시 아이콘](./media/sharepoint-scenario-build-app/icon-check-mark.png)을 선택하고, **OnSelect** 수식 - **SubmitForm(EditForm1)** 을 확인 표시합니다. 편집 양식 컨트롤을 사용하므로 이전처럼 **Patch()** 대신 **Submit()** 을 사용할 수 있습니다.

이제 완성된 화면은 다음 이미지와 같습니다(필드가 비어 있으면 **프로젝트 보기** 화면에서 항목을 선택했는지 확인합니다).

![세부 정보 업데이트 화면이 완성되었습니다.](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>7 단계: 앱 실행
이제 앱이 완성되었으므로 앱을 실행하여 앱이 어떻게 작동하는지 살펴보겠습니다. SharePoint 사이트의 링크를 앱에 추가하겠습니다. 브라우저에서 앱을 실행할 수는 있지만 다른 사람이 앱을 실행하려면 앱을 공유해야 할 수도 있습니다. 자세한 내용은 [앱 공유](https://powerapps.microsoft.com/guided-learning/learning-manage-share-apps)를 참조하세요.

### <a name="add-a-link-to-the-app"></a>앱에 링크 추가
1. Office 365 앱 시작 관리자에서 **PowerApps**를 클릭하거나 탭합니다.
   
    ![Office 365 앱 시작 관리자의 PowerApps](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. PowerApps에서 **프로젝트 관리 앱**에 대한 줄임표(**. . .**), **열기**를 차례로 클릭하거나 탭합니다.
   
    ![프로젝트 관리 앱 선택](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. 브라우저에서 앱에 대한 주소(URL)를 복사합니다.
   
    ![앱 URL 복사](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. SharePoint에서 **링크 편집**을 클릭하거나 탭합니다.
   
    ![SharePoint 사이트 링크 편집](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. **(+) 링크**를 클릭하거나 탭합니다.
   
    ![SharePoint 사이트에 앱 링크 추가](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. "프로젝트 관리 앱"을 입력하고 앱에 대한 주소에 붙여넣습니다.
   
    ![링크 속성 편집](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. **확인**, **저장**을 차례로 클릭하거나 탭합니다.
   
    ![링크 변경 내용 저장](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>프로젝트에 관리자 할당
이제 SharePoint 사이트에 앱을 만들었으므로 프로젝트 승인자 역할을 맡을 것입니다. 관리자가 할당되지 않은 프로젝트를 찾아서 해당 프로젝트 중 하나에 관리자를 할당합니다. 그런 다음 프로젝트 관리자의 역할을 맡고 할당된 프로젝트에 대한 정보를 추가합니다.

1. 먼저 SharePoint에서 **프로젝트 세부 정보** 목록을 살펴보겠습니다. **PMAssigned** 열에 **할당되지 않음** 값이 있는 두 프로젝트가 있습니다. 앱에서 이러한 프로젝트를 확인합니다.
   
    ![SharePoint 목록에 있는 할당되지 않은 프로젝트](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. 앱에 대해 만든 링크를 클릭하거나 탭합니다.

3. 첫 번째 화면에서 **관리자 할당**을 클릭하거나 탭합니다.
   
    ![앱 소개 화면](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. **관리자 할당** 화면의 목록에서 할당되지 않은 두 개의 프로젝트가 표시됩니다. **New BI software** 프로젝트를 선택합니다.
   
    ![선택한 항목이 있는 갤러리](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. **Manager** 텍스트 입력에서 "Joni Sherman"을 입력한 다음 **확인**을 클릭합니다.
   
    변경 내용을 목록에 적용하고 갤러리를 새로 고치므로 할당되지 않은 나머지 프로젝트만 표시됩니다.
   
    ![프로젝트에 관리자 할당](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. SharePoint 목록으로 돌아가서 페이지를 새로 고칩니다. 이제 프로젝트 항목이 프로젝트 관리자 이름으로 업데이트되었음을 알 수 있습니다.
   
    ![SharePoint 목록에 할당된 프로젝트 관리자](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>프로젝트 세부 정보 업데이트

1. ![뒤로 아이콘](./media/sharepoint-scenario-build-app/icon-back.png)을 클릭하거나 탭하여 첫 번째 화면으로 돌아간 다음, **세부 정보 업데이트**를 클릭하거나 탭합니다.
   
   ![앱 소개 화면](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. **프로젝트 보기** 화면에서 검색 상자에 "New"를 입력합니다.
   
   ![앱 갤러리에서 검색](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. **New BI software** 항목에 대한 ![세부 정보 화살표 아이콘](./media/sharepoint-scenario-build-app/icon-details-arrow.png)을 클릭합니다.
   
   ![선택한 갤러리 항목](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. **세부 정보 업데이트** 화면에서 다음 값을 설정합니다.
   
   * **ProjectedStartDate** 필드 = "3/6/2017"

   * **ProjectedEndDate** 필드 = "3/24/2017"

   * **ProjectedDays** 필드 = "15"
   
   ![항목 세부 정보 업데이트](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. 을 클릭하거나 탭하여 ![체크 표시 아이콘](./media/sharepoint-scenario-build-app/icon-check-mark.png) 변경 내용을 SharePoint 목록에 적용합니다.

6. 앱을 닫고 목록으로 돌아갑니다. 이제 프로젝트 항목이 변경된 날짜 및 일 수로 업데이트됩니다.
   
    ![업데이트된 SharePoint 목록](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>수식 심층 분석
PowerApps 수식에 있는 선택적인 두 번째 섹션입니다. 첫 번째 심층 분석에서 PowerApps가 3개 화면 앱의 찾아보기 갤러리에 대해 생성하는 수식 중 하나를 살펴보았습니다. 이 심층 분석에서는 두 번째 앱의 **AssignManager** 화면에 사용할 수식을 살펴보겠습니다. 수식은 다음과 같습니다.

**Patch ('프로젝트 세부 정보', LookUp ('프로젝트 세부 정보', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text} )**

이 수식에서 수행하는 작업은 무엇일까요? 갤러리에서 항목을 선택하고 **확인** 단추를 클릭하면, 수식에서 **프로젝트 세부 정보** 목록을 업데이트하고, **PMAssigned** 열을 텍스트 입력에서 지정한 값으로 설정합니다. 수식은 다음 함수를 사용하여 작업을 수행합니다.

* [**Patch** 함수](functions/function-patch.md)는 데이터 원본의 레코드를 하나 이상 수정합니다.

* [**LookUp** 함수](functions/function-filter-lookup.md)는 수식을 충족하는 테이블의 첫 번째 레코드를 찾습니다.

수식에 함수를 함께 배치하면 다음과 같은 상황이 발생합니다.

1. **확인** 단추를 클릭하면 **Patch** 함수가 호출되어 **프로젝트 세부 정보** 목록을 업데이트합니다.

2. **Patch** 함수 내에서 **LookUp** 함수는 업데이트할 **프로젝트 세부 정보** 목록의 행을 식별합니다. 이는 선택한 갤러리 항목의 ID를 목록의 ID와 비교하여 수행합니다. 예를 들어 12라는 ID는 **New BI software**에 대한 항목을 업데이트해야 함을 의미합니다.

3. **Patch** 함수에 올바른 ID가 있으므로 **PMAssigned** 필드가 **TextInput1.Text**의 값으로 업데이트됩니다.

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [프로젝트를 분석하는 Power BI 보고서를 만듭니다](sharepoint-scenario-build-report.md).

