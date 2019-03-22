---
title: 캔버스 앱에 대한 경비 보고서 샘플 설치 및 구성 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 대한 경비 보고서 샘플 설치 및 구성하기 위한 단계별 지침입니다.
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/08/2018
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 166fea9e02ebdaa490b400274c971f0c7268ec76
ms.sourcegitcommit: e64344548d607767e495a6b9526900bb5975226a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58330289"
---
# <a name="install-and-configure-the-expense-report-sample-for-canvas-apps-in-powerapps"></a>PowerApps의 캔버스 앱에 대한 경비 보고서 샘플 설치 및 구성 | Microsoft Docs

경비 보고서 샘플 설치 및 구성에 대한 단계별 지침입니다. [여기](https://aka.ms/previewmyexpenses)에서 샘플 앱을 미리 볼 수도 있습니다.

이 단계를 완료하는 데 소요되는 예상 시간: **10-15분**

> [!TIP]
> 경비 보고서 샘플 앱을 사용하는 방법의 데모를 보려면 [이 동영상](https://youtu.be/kJXZPILfbwU)을 시청하세요. 

제출에서 승인까지 경비 보고서를 추적하세요. 품목을 개별 경비로 누적 총계를 내고 준비가 되었으면 승인을 위해 제출하세요. 이 앱을 사용자에게 맞게 설정하려면 약간의 설정 작업이 필요합니다.

![경비 보고서 PowerApps 시작 화면](./media/expense-report-install/expense-report-powerapp.png)

> [!TIP]
> 경비 보고서 PowerApps 샘플을 사용하는 방법을 보려면 [이](https://youtu.be/h6E9cdrOvMU) 동영상을 시청하세요.

## <a name="prerequisites"></a>필수 조건

- PowerApps에 [등록](../signup-for-powerapps.md)합니다.

## <a name="create-the-expenses-sharepoint-list"></a>경비 SharePoint 목록 만들기

이 목록은 경비 보고서를 저장합니다.

1. 웹 브라우저를 열고 https://admin.microsoft.com 으로 이동하세요.
2. 목록을 만들 수 있는 권한을 가진 계정으로 로그인합니다.
3. 경비 목록을 배치할 사이트 컬렉션으로 이동합니다.
4. 웹 페이지의 오른쪽 맨 위 부분에 있는 **기어 아이콘**을 클릭합니다.
5. **앱 추가**를 클릭합니다.
6. **앱 찾기** 텍스트 상자에 **사용자 지정**을 입력합니다.
7. **검색 아이콘**을 클릭합니다.
8. **사용자 지정 목록** 앱을 클릭합니다.
9. **이름** 텍스트 상자에 **경비**를 입력합니다.

    > [!IMPORTANT]
    > 목록에 다른 이름을 선택하는 경우 설치 및 구성 프로세스 중에 경비를 볼 때마다 다른 이름으로 대체해야 하므로 해당 이름을 적어 두세요.

10. **만들기**를 클릭합니다.

### <a name="create-cost-center-column"></a>비용 센터 열 만들기

1. **경비** 목록을 클릭합니다.
2. 웹 페이지의 오른쪽 맨 위 부분에 있는 **기어 아이콘**을 클릭합니다.
3. **목록 설정**을 클릭합니다.
4. **열 만들기**를 클릭합니다.
5. **열 이름** 텍스트 상자에 **비용 센터**를 입력합니다.
6. **이 열의 정보 유형** 라디오 단추 목록에서 **선택**을 선택합니다.
7. **별도의 줄에 각 선택 입력** 텍스트 상자에서 별도의 줄에 각각 다음 값을 입력합니다. 
    - Microsoft
    - Contoso
8. **기본값** 텍스트 상자에 **Microsoft**를 입력합니다.
9. **확인**을 클릭합니다.

### <a name="create-comments-column"></a>주석 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **주석**을 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **여러 줄의 텍스트**를 선택합니다.
4. **확인**을 클릭합니다.

### <a name="create-status-column"></a>상태 열 만들기

1. **경비** 목록을 클릭합니다.
2. 웹 페이지의 오른쪽 맨 위 부분에 있는 **기어 아이콘**을 클릭합니다.
3. **목록 설정**을 클릭합니다.
4. **열 만들기**를 클릭합니다.
5. **열 이름** 텍스트 상자에 **상태**를 입력합니다.
6. **이 열의 정보 유형** 라디오 단추 목록에서 **선택**을 선택합니다.
7. **별도의 줄에 각 선택 입력** 텍스트 상자에서 별도의 줄에 각각 다음 값을 입력합니다. 
    - 개방성
    - 보류 중
    - Approved
8. **기본값** 텍스트 상자에 **열기**를 입력합니다.
9. **확인**을 클릭합니다.

### <a name="create-approvername-column"></a>승인자 이름 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **승인자 이름**을 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **개인 또는 그룹**을 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

### <a name="create-datesubmitted-column"></a>제출된 날짜 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **제출된 날짜**를 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **날짜 및 시간**을 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

### <a name="create-startdate-column"></a>시작 날짜 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **시작 날짜**를 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **날짜 및 시간**을 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

### <a name="create-enddate-column"></a>종료 날짜 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **종료 날짜**를 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **날짜 및 시간**을 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

## <a name="create-the-line-items-sharepoint-list"></a>품목 SharePoint 목록 만들기

이 목록은 경비 보고서와 관련된 품목을 저장합니다.

1. 경비 목록을 만든 사이트 컬렉션으로 이동합니다.
2. 웹 페이지의 오른쪽 맨 위 부분에 있는 **기어 아이콘**을 클릭합니다.
3. **앱 추가**를 클릭합니다.
4. **앱 찾기** 텍스트 상자에 **사용자 지정**을 입력합니다.
5. **검색 아이콘**을 클릭합니다.
6. **사용자 지정 목록** 앱을 클릭합니다.
7. **이름** 텍스트 상자에 **품목**을 입력합니다.

    > [!IMPORTANT] 
    > 목록에 다른 이름을 선택하는 경우 설치 및 구성 프로세스 중에 경비를 볼 때마다 다른 이름으로 대체해야 하므로 해당 이름을 적어 두세요.

8. **만들기**를 클릭합니다.
 
### <a name="create-category-column"></a>범주 열 만들기

1. **품목** 목록을 클릭합니다.
2. 웹 페이지의 오른쪽 맨 위 부분에 있는 **기어 아이콘**을 클릭합니다.
3. **목록 설정**을 클릭합니다.
4. **열 만들기**를 클릭합니다.
5. **열 이름** 텍스트 상자에 **범주**를 입력합니다.
6. **이 열의 정보 유형** 라디오 단추 목록에서 **선택**을 선택합니다.
7. **별도의 줄에 각 선택 입력** 텍스트 상자에서 별도의 줄에 각각 다음 값을 입력합니다. 
    - 식대
    - 교통비
    - 비즈니스 필요성
8. **기본값** 텍스트 상자에 **식대**를 입력합니다.
9. **확인**을 클릭합니다.

### <a name="create-cost-column"></a>비용 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **비용**을 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **숫자(1, 10, 100)** 를 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

### <a name="create-date-column"></a>날짜 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **날짜**를 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **날짜 및 시간**을 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **확인**을 클릭합니다.

### <a name="create-description-column"></a>설명 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **설명**을 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **여러 줄의 텍스트**를 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **허용할 텍스트 유형 지정** 라디오 단추 목록에서 **일반 텍스트**를 선택합니다.
6. **확인**을 클릭합니다.

### <a name="create-reportid-column"></a>보고서 ID 열 만들기

1. **열 만들기**를 클릭합니다.
2. **열 이름** 텍스트 상자에 **보고서 ID**를 입력합니다.
3. **이 열의 정보 유형** 라디오 단추 목록에서 **조회(이 사이트에 이미 있는 정보)** 를 선택합니다.
4. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **예**를 선택합니다.
5. **정보를 가져올 위치** 드롭다운 목록에서 자신이 만든 **경비** 목록을 선택합니다.
6. **이 열** 드롭다운 목록에서 **ID**를 선택합니다.
7. **확인**을 클릭합니다.

### <a name="edit-title-column"></a>제목 열 편집

1. **제목** 열 링크를 클릭합니다.
2. **이 열에 정보가 포함되어야 함** 라디오 단추 목록에서 **아니요**를 선택합니다.
3. **확인**을 클릭합니다.

## <a name="download-the-expense-report-powerapp"></a>경비 보고서 PowerApps 다운로드

1.  웹 브라우저에서 다음 링크로 이동합니다.

    [http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip](http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip).

2.  경비 보고서 PowerApps 샘플 패키지를 다운로드하고 컴퓨터에 저장합니다.

## <a name="create-connections"></a>연결 만들기

1.  웹 브라우저에서 [web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)으로 이동합니다.
2.  등록 시 사용한 동일한 자격 증명을 제공하여 로그인합니다.
3.  왼쪽 메뉴에서 **연결**을 선택합니다.

### <a name="create-approvals-connection"></a>승인 연결 만들기

1.  **+ 새 연결**을 클릭합니다.
2.  **검색** 텍스트 상자에 **승인**을 입력합니다.
3.  목록에서 **승인**을 선택합니다.
4.  **만들기**를 클릭합니다.
    
### <a name="create-office-365-outlook-connection"></a>Office 365 Outlook 연결 만들기

1.  **+ 새 연결**을 클릭합니다.
2.  **검색** 텍스트 상자에 **Office 365 Outlook**을 입력합니다.
3.  목록에서 **Office 365 Outlook**을 선택합니다.
4.  **만들기**를 클릭합니다.
5.  팝업 창에서 로그인하는 데 사용한 계정을 선택합니다.

### <a name="create-sharepoint-connection"></a>SharePoint 연결 만들기

1.  **+ 새 연결**을 클릭합니다.
2.  **검색** 텍스트 상자에 **SharePoint**을 입력합니다.
3.  목록에서 **SharePoint**를 선택합니다.
4.  **만들기**를 클릭합니다.
5.  팝업 창에서 로그인하는 데 사용한 계정을 선택합니다.

## <a name="import-the-expense-report-powerapp"></a>경비 보고서 PowerApps 가져오기

1. 웹 브라우저에서 https://web.powerapps.com 으로 이동합니다.
2. 등록 시 사용한 동일한 자격 증명을 제공하여 로그인합니다.
3. 왼쪽 메뉴에서 **앱**을 선택합니다. 
4. **패키지(미리 보기) 가져오기**를 클릭합니다.
    
   ![패키지 가져오기 화면](./media/expense-report-install/import-package.png)

5. **업로드** 단추를 클릭하고 이전 단계에서 다운로드한 PowerApp 패키지를 선택합니다.
6. **앱** 및 **흐름** 리소스 유형의 **가져오기 설정**을 **새로 만들기**로 설정합니다.
7. **SharePoint** 및 **Outlook** 연결의 **가져오기 설정**을 **가져올 때 선택**으로 설정합니다.
    
   ![설정 가져오기 화면](./media/expense-report-install/import-settings.png)

8. **SharePoint 연결**의 **빨간색 아이콘**을 클릭합니다.
9. 연결 목록에서 사용자 이름이 있는 항목을 클릭합니다.

   ![설정 가져오기 화면](./media/expense-report-install/import-settings-sharepoint.png)

10. **저장**을 클릭합니다.
11. **승인 연결**의 **빨간색 아이콘**을 클릭합니다.
12. 연결 목록에서 사용자 이름이 있는 항목을 클릭합니다.

    ![설정 가져오기 화면](./media/expense-report-install/import-settings-approvals.png)

13. **저장**을 클릭합니다.
14. **Office 365 Outlook 연결**의 **빨간색 아이콘**을 클릭합니다.
15. 연결 목록에서 사용자 이름이 있는 항목을 클릭합니다.

    ![설정 가져오기 화면](./media/expense-report-install/import-settings-office365outlook.png)

16. **저장**을 클릭합니다.

    > [!TIP] 
    > 완료되면 다음과 같은 화면이 표시됩니다.

    ![설정 가져오기 화면](./media/expense-report-install/import-settings-done.png)

17. **가져오기**를 클릭하고 프로세스가 완료될 때까지 기다립니다.

    ![설정 가져오기 화면](./media/expense-report-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-lists"></a>SharePoint 목록을 사용하도록 PowerApp 구성

1. 웹 브라우저에서 **앱**을 클릭합니다.
2. 경비 보고서 PowerApp 옆에 있는 **줄임표**를 클릭합니다.
3. **웹에서 편집**을 클릭합니다.
4. **허용**을 클릭합니다.

### <a name="delete-connections"></a>연결 삭제
1. **보기**를 클릭합니다.
2. **데이터 원본**을 클릭합니다.
3. **데이터** 창에서 **경비** 옆에 있는 **줄임표**를 클릭합니다.
4. **제거**를 클릭합니다.
5. **데이터** 창에서 **품목** 옆에 있는 **줄임표**를 클릭합니다.
6. **제거**를 클릭합니다.

### <a name="expenses-list"></a>경비 목록

1. **보기**를 클릭합니다.
2. **데이터 원본**을 클릭합니다.
3. **데이터** 창에서 **+ 데이터 원본 추가**를 클릭합니다.
4. **+ 새 연결**을 클릭합니다.
5. **SharePoint**를 선택합니다.
6. **만들기**를 클릭합니다.
7. **최근에 사용한 사이트** 목록에서 경비 목록을 만든 SharePoint 사이트를 선택합니다.

    > [!TIP] 
    > 사이트가 목록에 나타나지 않을 경우 텍스트 상자에 SharePoint 사이트 URL을 입력하고 **이동**을 클릭합니다.

8. 목록 맨 위에 있는 **검색** 텍스트 상자에 **경비**를 입력합니다.
9. **경비** 목록 옆에 있는 확인란을 선택합니다.
10. **연결**을 클릭합니다.

### <a name="lineitems-list"></a>품목 목록

1. **보기**를 클릭합니다.
2. **데이터 원본**을 클릭합니다.
3. **데이터** 창에서 **+ 데이터 원본 추가**를 클릭합니다.
4. **+ 새 연결**을 클릭합니다.
5. **SharePoint**를 선택합니다.
6. **만들기**를 클릭합니다.
7. **최근에 사용한 사이트** 목록에서 품목 목록을 만든 SharePoint 사이트를 선택합니다.

    > [!TIP] 
    > 사이트가 목록에 나타나지 않을 경우 텍스트 상자에 SharePoint 사이트 URL을 입력하고 **이동**을 클릭합니다.

8. 목록 맨 위에 있는 **검색** 텍스트 상자에 **품목**을 입력합니다.
9. **품목** 목록 옆에 있는 확인란을 선택합니다.
10. **연결**을 클릭합니다.
11. **파일**을 클릭합니다.
12. **저장**을 클릭합니다.
13. **게시**를 클릭합니다.
14. **이 버전 게시**를 클릭합니다.

## <a name="modify-the-flow"></a>흐름 수정

1.  왼쪽 메뉴에서 **흐름**을 클릭합니다.
2.  로그인하라는 메시지가 표시되면 등록 시 사용한 동일한 자격 증명을 제공하여 로그인합니다.
3.  최상위 메뉴에서 **내 흐름**을 선택합니다.
4.  **ApproveExpense** 흐름 옆에 있는 **연필 아이콘**을 클릭합니다.
 
    ![흐름 편집 화면](./media/expense-report-install/edit-flow.png)

5.  **항목 가져오기** 작업을 확장합니다. 
6.  자신이 만든 경비 SharePoint 목록에 맞게 **사이트 주소** 및 **목록 이름**을 변경합니다.
    
    ![흐름 편집 화면](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > 수동으로 입력할 필요 없이 드롭다운 목록에서 선택할 수 있습니다.

7.  **조건**을 확장합니다.
8.  **부합할 경우** 섹션을 확장합니다.
9.  **항목 상태를 승인됨으로 변경** 작업을 확장합니다.
10. 자신이 만든 경비 SharePoint 목록에 맞게 **사이트 주소** 및 **목록 이름**을 변경합니다.

    ![흐름 편집 화면](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > 수동으로 입력할 필요 없이 드롭다운 목록에서 선택할 수 있습니다.

11. **부합하지 않을 경우** 섹션을 확장합니다.
12. **항목 상태를 미결로 변경** 작업을 확장합니다.
13. 자신이 만든 경비 SharePoint 목록에 맞게 **사이트 주소** 및 **목록 이름**을 변경합니다. 

    ![흐름 편집 화면](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > 수동으로 입력할 필요 없이 드롭다운 목록에서 선택할 수 있습니다.

14. **흐름 업데이트**를 클릭합니다.

## <a name="play-the-powerapp"></a>PowerApp 재생

1. 웹 브라우저에서 **앱**을 클릭합니다.
2. 경비 보고서 PowerApp 옆에 있는 **줄임표**를 클릭합니다.
3. **열기**를 클릭합니다.


## <a name="next-steps"></a>다음 단계
- [SharePoint 목록 양식 사용자 지정](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [컨트롤 추가 및 구성](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [SharePoint 목록 또는 라이브러리에 대한 권한 편집 및 관리](https://support.office.com/en-us/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)



