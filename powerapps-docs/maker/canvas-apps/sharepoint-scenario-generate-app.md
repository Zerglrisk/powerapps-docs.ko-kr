---
title: 프로젝트 요청을 처리할 캔버스 앱 생성 | Microsoft Docs
description: 이 작업에서는 SharePoint 목록에서 직접 3개의 화면이 있는 캔버스 앱을 생성합니다.
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
ms.openlocfilehash: 42ca4a12f75c82bb685396a857e5ae825d8d7fa1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674783"
---
# <a name="generate-a-canvas-app-to-handle-project-requests"></a>프로젝트 요청을 처리할 캔버스 앱 생성
> [!NOTE]
> 이 문서는 SharePoint Online에서 Power Apps, 파워 자동화 및 Power BI 사용에 대 한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악하도록 합니다.

SharePoint 목록을 저장했으므로 첫 번째 앱을 빌드하고 사용자 지정할 수 있습니다. Power Apps는 SharePoint와 통합 되므로 목록에서 직접 기본 *3 개 화면 앱* 을 쉽게 생성할 수 있습니다. 이 앱을 사용하면 각 목록 항목에 대한 요약 및 세부 정보를 보고, 기존 목록 항목을 업데이트하고, 새 목록 항목을 만들 수 있습니다. 목록에서 직접 앱을 만드는 경우 앱은 해당 목록에서 *보기*로 나타납니다. 그런 다음 휴대폰뿐만 아니라 브라우저에서 해당 앱을 실행할 수 있습니다.

> [!TIP]
> 이 시나리오에 대한 [다운로드 패키지](https://aka.ms/o4ia0f)에는 이 앱의 완성된 버전인 project-requests-app.msapp이 포함되어 있습니다.

## <a name="step-1-generate-an-app-from-a-sharepoint-list"></a>1단계: SharePoint 목록에서 앱 생성

1. 사용자가 만든 **프로젝트 요청** 목록에서 **PowerApps** 및 **앱 만들기**를 클릭하거나 누릅니다.
   
    ![앱 만들기](./media/sharepoint-scenario-generate-app/02-01-01-create-app.png)

2. "프로젝트 요청 앱"과 같은 이름을 앱에 지정한 다음 **만들기**를 클릭하거나 누릅니다. 앱이 준비 되 면 Power Apps 스튜디오에서 열립니다.
   
    ![앱의 이름 지정](./media/sharepoint-scenario-generate-app/02-01-02-create-app-name.png)

## <a name="step-2-review-the-app-in-power-apps-studio"></a>2 단계: Power Apps Studio에서 앱 검토

1. Power Apps 스튜디오에서 왼쪽 탐색 모음은 기본적으로 앱에 있는 화면과 컨트롤의 계층 뷰를 표시 합니다.
   
    ![계층 구조 보기를 사용 하는 Power Apps Studio](./media/sharepoint-scenario-generate-app/02-02-01-studio-screens-hierarchy.png)

2. 썸네일 아이콘을 클릭하거나 눌러서 보기를 전환합니다.
   
    ![Power Apps 스튜디오 뷰 선택기](./media/sharepoint-scenario-generate-app/02-02-02-studio-view-selector.png)

3. 가운데 창에서 보려는 각 화면을 클릭하거나 누릅니다. 화면에는 세 가지가 있습니다.
   
    (a). 목록에서 데이터를 찾아보고, 정렬하고, 필터링하고 추출할 수 있는 **찾아보기** 화면
    
    (b). 항목에 대한 자세한 정보를 볼 수 있는 **세부 정보** 화면
    
    (c). 기존 항목을 편집하거나 새 항목을 만들 수 있는 **편집/만들기** 화면
      
      ![미리 보기를 사용 하는 Power Apps 스튜디오](./media/sharepoint-scenario-generate-app/02-02-03-studio-screens-thumbnails.png)

## <a name="step-3-customize-the-apps-browse-screen"></a>3단계: 앱의 찾아보기 화면 사용자 지정

1. 찾아보기 화면을 클릭하거나 누릅니다.
   
    이 화면에는 *갤러리*를 포함하는 *레이아웃*이 있어서 검색 표시줄 및 정렬 단추와 같은 다른 *컨트롤*뿐만 아니라 목록 항목을 표시합니다.

2. 첫 번째 항목을 제외한 레코드를 클릭하거나 눌러서 **BrowseGallery1** 갤러리를 선택합니다.
   
    ![갤러리 찾아보기](./media/sharepoint-scenario-generate-app/02-03-01-browse-gallery.png)

3. 오른쪽 창의 **속성**에서 **프로젝트 요청**을 클릭하거나 탭합니다. 

4. 다음 목록과 일치하도록 필드를 업데이트합니다.
   
   * **RequestDate**

   * **요청자**

   * **Title**

     ![갤러리 필드](./media/sharepoint-scenario-generate-app/02-03-02-gallery-fields.png)

5. **BrowseGallery1**을 선택한 상태에서 **항목** 속성을 선택합니다.
   
    ![항목 속성](./media/sharepoint-scenario-generate-app/02-03-03-items.png)

6. 수식을 **SortByColumns(Filter('Project Requests', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** 으로 변경합니다.
   
    ![수식 입력줄](./media/sharepoint-scenario-generate-app/02-03-04-formula.png)
   
    이렇게 하면 Power Apps에서 선택한 기본값 대신 **제목** 필드를 기준으로 정렬 하 고 검색할 수 있습니다. 자세한 정보는 [수식 심층 분석](#formula-deep-dive)을 참조하세요.

6. **파일** 및 **저장**을 차례로 클릭하거나 누릅니다. ![앱으로 돌아가기 아이콘](./media/sharepoint-scenario-generate-app/icon-back-to-app.png)을 클릭하거나 눌러서 앱으로 돌아갑니다.

## <a name="step-4-review-the-apps-details-screen-and-edit-screen"></a>4단계: 앱의 세부 정보 화면 검토 및 화면 편집
1. 세부 정보 화면을 클릭하거나 누릅니다.
   
    이 화면에는 갤러리에서 선택한 항목에 대한 정보를 표시한 *표시 양식*을 포함하는 다른 레이아웃이 있습니다. 항목을 편집하거나 삭제하는 컨트롤 및 찾아보기 화면으로 돌아가는 컨트롤이 있습니다.
   
    ![세부 정보 표시 양식](./media/sharepoint-scenario-generate-app/02-04-01-details.png)

4. 편집 화면을 클릭하거나 누릅니다.
   
    이 화면에는 선택한 항목을 편집하거나 (찾아보기 화면에서 직접 이동한 경우) 새로운 항목을 만드는 *편집 양식*이 포함됩니다. 변경 내용을 저장하거나 취소하는 컨트롤이 있습니다.

    ![편집 양식](./media/sharepoint-scenario-generate-app/02-04-03-edit.png)

## <a name="step-5-run-the-app-from-the-list"></a>5단계: 목록에서 앱 실행

1. **프로젝트 요청** 목록에서 **모든 항목** 및 **프로젝트 요청 앱**을 차례로 클릭하거나 누릅니다.
   
    ![프로젝트 요청 보기 앱](./media/sharepoint-scenario-generate-app/02-05-01-view-app.png)
2. **열기**를 클릭하면 새 브라우저 탭에서 앱이 열립니다.
   
    ![프로젝트 요청 열기 앱](./media/sharepoint-scenario-generate-app/02-05-02-open-app.png)

3. 앱의 찾아보기 갤러리에서 첫 번째 항목의 ![세부 정보 아이콘으로 이동](./media/sharepoint-scenario-generate-app/icon-details-arrow.png) 을 클릭하거나 누릅니다.
   
    ![첫 번째 갤러리 항목](./media/sharepoint-scenario-generate-app/02-05-04-first-item.png)

4. 연필 편집 아이콘을 ![클릭하거나 눌러서](./media/sharepoint-scenario-generate-app/icon-pencil.png) 항목을 편집합니다.

5. **설명** 필드를 업데이트합니다. 마지막 단어를 "그룹"에서 "팀"으로 변경한 다음 ![확인 표시 아이콘](./media/sharepoint-scenario-generate-app/icon-check-mark.png)을 클릭하거나 누릅니다.
   
   ![설명 필드 업데이트](./media/sharepoint-scenario-generate-app/02-05-07-edit.png)

6. 브라우저 탭을 닫습니다.

7. **프로젝트 요청** 목록으로 이동하고, **프로젝트 요청 앱** 및 **모든 항목**을 차례로 클릭하거나 누릅니다.
   
   ![모든 항목 보기](./media/sharepoint-scenario-generate-app/02-05-08-view-all.png)
8. 앱에서 수행한 변경 내용을 확인합니다.
   
    ![편집 확인](./media/sharepoint-scenario-generate-app/02-05-09-verify-edit.png)

아주 간단한 앱이며 몇 가지 기본 사용자 지정만 수행했지만 흥미로운 기능을 신속하게 빌드할 수 있습니다. 다음 작업으로 이동하겠습니다. 하지만 원하신다면 앱에 대해 좀 더 살펴보고 컨트롤 및 수식이 함께 작동하여 앱 동작을 구현하는 방법을 확인합니다.

## <a name="formula-deep-dive"></a>수식 심층 분석
이 섹션은 옵션이지만 수식이 작동하는 방법에 대해 자세히 이해할 수 있습니다. 이 작업의 3단계에서 **BrowseGallery1**에 있는 **항목** 속성의 수식을 수정했습니다. 특히 Power Apps에서 선택한 필드 대신 **제목** 필드를 사용 하도록 정렬 및 검색을 변경 했습니다. 수정한 수식은 다음과 같습니다.

**SortByColumns ( Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text ) ), "Title", If ( SortDescending1, Descending, Ascending ) )**

하지만 이 수식에서 수행하는 작업은 무엇인가요? 갤러리에서 나타나는 데이터 원본을 결정하고, 검색 상자에 입력한 텍스트에 따라 데이터를 필터링하고, 앱에 표시되는 정렬 단추에 따라 결과를 정렬합니다. 수식은 *함수*를 사용하여 해당 작업을 수행합니다. 함수는 매개 변수(예: 입력)를 사용하고, 작업(예: 필터링)을 수행하고, 값(예: 출력)을 반환합니다.

* [**SortByColumns** 함수](functions/function-sort.md)는 하나 이상의 열을 기준으로 테이블을 정렬합니다.
* [**Filter** 함수](functions/function-filter-lookup.md)는 지정한 수식을 충족하는 테이블에서 레코드를 찾습니다.
* [**StartsWith** 함수](functions/function-startswith.md)는 텍스트 문자열이 다른 텍스트 문자열로 시작하는지 테스트합니다.
* [**If** 함수](functions/function-if.md)는 조건이 true인 경우 하나의 값을 반환하고 동일한 조건이 false인 경우 다른 값을 반환합니다.

수식에 함수를 함께 배치하면 다음과 같은 상황이 발생합니다.

1. 검색 상자에 텍스트를 입력하는 경우 **StartsWith** 함수는 해당 텍스트를 목록의 **제목** 열에서 각 문자열의 시작 부분과 비교합니다.
   
    **StartsWith ( Title, TextSearchBox1.Text )**
   
    예를 들어 검색 상자에 "de"를 입력하는 경우 "Desktop" 및 "Device"로 시작하는 항목을 비롯한 4개의 결과가 표시됩니다. 모든 "Mobile devices" 항목은 "de"로 *시작*하지 않기 때문에 표시되지 않습니다.

2. **필터** 함수는 **프로젝트 요청** 테이블에서 행을 *반환*합니다. 비교할 검색 상자에 텍스트가 없으면 **필터**는 모든 행을 반환합니다.
   
    **Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text )**

3. **If** 함수는 **SortDescending1** 변수가 true 또는 false로 설정되었는지를 확인합니다(앱에서 정렬 단추로 설정). 그러면 함수는 **내림차순** 또는 **오름차순**의 값을 반환합니다.
   
    **If ( SortDescending1, Descending, Ascending )**

4. 이제 **SortByColumns** 함수는 갤러리를 정렬할 수 있습니다. 이 경우에 **제목** 필드에 따라 정렬하지만 검색 필드가 아닌 다른 필드일 수 있습니다.

이 지점까지 수행한 경우 사용자가 이 수식의 작동 방식 및 함수 및 기타 요소를 결합하여 앱에서 필요한 동작을 실행하는 방법을 이해할 수 있을 것입니다. 자세한 내용은 [PowerApps에 대한 수식 참조](formula-reference.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [프로젝트 승인을 관리하는 흐름을 만듭니다](sharepoint-scenario-approval-flow.md).

