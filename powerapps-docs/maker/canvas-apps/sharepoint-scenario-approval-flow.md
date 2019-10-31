---
title: 프로젝트 승인을 관리하는 흐름 만들기 | Microsoft Docs
description: 이 작업에서는 프로젝트 승인 프로세스를 구동하는 흐름을 만듭니다.
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/09/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9dc1fa02737b49261dc76a06e208cea578e80dea
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182597"
---
# <a name="create-a-flow-to-manage-project-approvals"></a>프로젝트 승인을 관리하는 흐름 만들기
> [!NOTE]
> 이 문서는 SharePoint Online에서 PowerApps, Microsoft Flow 및 Power BI를 사용하는 방법에 대한 자습서 시리즈의 일부입니다. [시리즈 소개](sharepoint-scenario-intro.md)를 참고하여 관련된 다운로드뿐만 아니라 전체적인 내용을 파악하도록 합니다.

이 작업에서는 프로젝트 승인 프로세스를 구동하는 흐름을 만듭니다. Microsoft Flow는 SharePoint와 통합되어 있으므로 목록에서 직접 흐름을 쉽게 만들 수 있습니다. **프로젝트 요청** 목록에 항목을 추가할 때 만드는 흐름이 트리거됩니다. 흐름은 프로젝트 승인자에게 전자 메일을 보내고, 프로젝트 승인자는 전자 메일에서 직접 요청을 승인하거나 거부합니다. 그런 다음 승인 요청 또는 거부 전자 메일을 프로젝트 요청자에게 보내고, SharePoint 목록을 적절하게 업데이트합니다.

## <a name="step-1-configure-the-flow-template"></a>1단계: 흐름 템플릿 구성
1. **프로젝트 요청** 목록에서 **흐름**, **흐름 만들기**를 차례로 클릭하거나 탭합니다.
   
    ![흐름 만들기](./media/sharepoint-scenario-approval-flow/03-01-01-create-flow.png)
2. 오른쪽 창에서 **새 항목이 추가되면 승인 시작**을 클릭하거나 탭합니다.
   
    ![승인 흐름 만들기](./media/sharepoint-scenario-approval-flow/03-01-02-approval-flow.png)
3. 아직 로그인하지 않은 경우 SharePoint 및 Outlook에 로그인한 다음 **계속**을 클릭하거나 탭합니다.
   
    ![템플릿을 사용하기 위한 로그인](./media/sharepoint-scenario-approval-flow/03-01-03-continue.png)
   
    이제 이 흐름에 대한 템플릿이 표시되며 작업을 수행할 준비가 되었습니다. 흐름의 상자는 단계를 나타냅니다. 제공하는 입력뿐만 아니라 이전 단계의 입력도 가져옵니다. 그런 다음 각 단계에서 후속 단계로 출력을 제공할 수 있습니다.
   
    ![승인 템플릿](./media/sharepoint-scenario-approval-flow/03-01-04-template.png)
4. **할당 대상** 상자에서 테넌트에 유효한 이름을 입력합니다.
   
    ![승인 전자 메일 연락처](./media/sharepoint-scenario-approval-flow/03-01-05-approval-email.png)
   
    흐름의 다음 상자에서는 프로젝트 승인자의 결정에 응답하고 흐름을 두 개의 '분기'(**예인 경우** 또는 **아니요인 경우**) 중 하나로 라우팅합니다.
   
    ![승인 조건](./media/sharepoint-scenario-approval-flow/03-01-06-condition.png)

## <a name="step-2-create-actions-for-approve--yes"></a>2단계: 승인 = 예 작업 만들기
기본적으로 이 분기에서는 요청자에게 승인 전자 메일을 보냅니다. 또한 프로젝트가 승인되었으므로 **프로젝트 요청** 목록을 업데이트하고 **프로젝트 세부 정보** 목록에 항목을 추가합니다.

1. **예인 경우** 분기에서 **항목 작성자에게 승인 알림**, **편집**을 차례로 클릭하거나 탭하여 요청자에게 보낸 전자 메일에 대한 기본 옵션을 확인합니다.
   
    ![전자 메일 설정 편집](./media/sharepoint-scenario-approval-flow/03-01-07-yes-email.png)
2. 기본적으로 전자 메일은 목록 항목을 만든 사람에게 제목 줄 및 메시지 본문과 함께 보냅니다. 원하는 경우 이러한 내용을 업데이트할 수 있습니다.
   
    ![기본 전자 메일 설정](./media/sharepoint-scenario-approval-flow/03-01-07a-yes-email-defaults.png)
3. **작업 추가**를 클릭하거나 탭합니다.
   
    ![작업 추가](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. **작업 선택** 아래에서 "SharePoint"를 검색한 다음 **SharePoint - 항목 업데이트**를 클릭합니다.
   
    ![항목 업데이트 작업](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. SharePoint 사이트 URL 및 목록 이름을 입력합니다.
   
    ![항목 매개 변수 업데이트](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. **ID** 상자를 선택한 다음 *동적 콘텐츠* 대화 상자에서 **ID**를 클릭하거나 탭합니다.
   
    ![목록 ID 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
   
    동적 콘텐츠는 이전 단계에 따라 흐름 전체에서 사용할 수 있습니다. 이 경우 SharePoint 목록 정보가 제공되며, 만드는 작업에서 이 정보를 사용할 수 있습니다.
7. **제목** 상자를 선택하고, 동적 콘텐츠 대화 상자에서 "제목"을 검색한 다음, **제목**을 클릭하거나 탭합니다.
   
    ![목록 제목 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. **승인됨** 상자에 "예"를 입력합니다. 흐름의 이 부분은 이제 다음 이미지와 같습니다.
   
    ![목록 업데이트](./media/sharepoint-scenario-approval-flow/03-01-08-yes-update-complete.png)
9. **작업 추가**를 다시 클릭하거나 탭합니다. 이번에는 승인된 프로젝트의 **프로젝트 세부 정보** 목록에 항목을 추가합니다.
   
    ![작업 추가](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
10. **작업 선택**에서 "SharePoint"를 검색한 다음 **SharePoint - 항목 만들기**를 선택합니다.
    
    ![항목 만들기 작업](./media/sharepoint-scenario-approval-flow/03-01-09-create.png)
11. SharePoint 사이트 URL 및 목록 이름을 입력합니다.
    
    ![항목 매개 변수 만들기](./media/sharepoint-scenario-approval-flow/03-01-10-yes-create-list.png)
12. **제목** 상자를 선택하고, 동적 콘텐츠 대화 상자에서 "제목"을 검색한 다음, **제목**을 클릭하거나 탭합니다.
    
    ![목록 제목 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
13. **RequestId** 상자를 선택한 다음 동적 콘텐츠 대화 상자에서 **ID**를 클릭하거나 탭합니다.
    
    ![목록 ID 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
14. **PMAssigned** 상자에서 "할당 해제"를 입력합니다. 흐름의 이 부분은 이제 다음 이미지와 같습니다.
    
    ![항목 만들기 완료](./media/sharepoint-scenario-approval-flow/03-01-11-yes-create-complete.png)

## <a name="step-3-review-action-for-approve--no"></a>3단계: 승인 = 아니요 작업 검토
기본적으로 이 분기에서는 요청자에게 거부 전자 메일을 보냅니다. 또한 **프로젝트 요청** 목록을 업데이트합니다. 프로젝트가 진행되지 않으므로 **프로젝트 세부 정보** 목록에 항목을 추가하지 않습니다.

1. **아니요인 경우** 분기에서 **항목 작성자에게 거부 알림**, **편집**을 차례로 클릭하거나 탭하여 요청자에게 보낸 전자 메일에 대한 기본 옵션을 확인합니다.
   
    ![전자 메일 설정 편집](./media/sharepoint-scenario-approval-flow/03-01-12-no-email.png)
2. 기본적으로 전자 메일은 목록 항목을 만든 사람에게 제목 줄 및 메시지 본문과 함께 보냅니다. 원하는 경우 이러한 내용을 업데이트할 수 있습니다.
   
    ![기본 전자 메일 설정](./media/sharepoint-scenario-approval-flow/03-01-13-no-email-defaults.png)
3. **작업 추가**를 클릭하거나 탭합니다.
   
    ![작업 추가](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. **작업 선택** 아래에서 "SharePoint"를 검색한 다음 **SharePoint - 항목 업데이트**를 클릭합니다.
   
    ![항목 업데이트 작업](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. SharePoint 사이트 URL 및 목록 이름을 입력합니다.
   
    ![항목 매개 변수 업데이트](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. **ID** 상자를 선택한 다음 동적 콘텐츠 대화 상자에서 **ID**를 클릭하거나 탭합니다.
   
    ![목록 ID 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
7. **제목** 상자를 선택하고, 동적 콘텐츠 대화 상자에서 "제목"을 검색한 다음, **제목**을 클릭하거나 탭합니다.
   
    ![목록 제목 동적 콘텐츠](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. **승인됨** 상자에서 "아니요"를 입력합니다. 흐름의 이 부분은 이제 다음 이미지와 같습니다.
   
    ![목록 업데이트](./media/sharepoint-scenario-approval-flow/03-01-08-no-update-complete.png)
9. 화면의 오른쪽 위에서 **흐름 만들기**를 클릭하거나 탭합니다.
   
    이제 흐름이 완성되었으며 상자를 접으면 다음 이미지와 같습니다.
   
    ![완성된 흐름](./media/sharepoint-scenario-approval-flow/03-01-16-flow-complete.png)

10. 화면의 오른쪽 위에서 **완료**를 클릭하거나 탭합니다.
   
    ![완료 단추](./media/sharepoint-scenario-approval-flow/03-01-15a-done-button.png)

## <a name="step-4-run-the-approval-flow"></a>4단계: 승인 흐름 실행
1. **프로젝트 요청** 목록에서 **빠른 편집**을 클릭하고 다음과 같은 항목을 추가합니다.
   
   * **Title** = "Megan을 위한 새 모니터"

   * **Description** = "Megan은 24" 모니터가 필요합니다."

   * **ProjectType** = "New hardware"

   * **RequestDate** = "02/03/2017"

   * **Requestor** = "Megan Bowen"

   * **EstimatedDays** = "1"

   * **Approved** = "Pending"

     ![목록에 추가된 항목](./media/sharepoint-scenario-approval-flow/03-02-01-list-add.png)
2. 완료되면 페이지 위쪽의 **완료**를 클릭합니다.
   
    ![완료 확인 표시](./media/sharepoint-scenario-approval-flow/03-02-02-done.png)
3. 승인자 전자 메일 계정의 받은 편지함을 확인합니다. 다음과 같은 전자 메일이 있습니다.
   
    ![Allan Deyoung에게 전자 메일 보내기](./media/sharepoint-scenario-approval-flow/03-02-03-allan-email.png)
4. **승인** 또는 **거부**를 클릭하면 흐름에서 다른 프로세스를 실행하고 전자 메일을 통해 다음과 같은 피드백을 직접 받습니다.
   
    ![승인 작업 완료](./media/sharepoint-scenario-approval-flow/03-02-04-action-complete.png)
5. 이 흐름에서는 다음 이미지와 같이 Allan의 응답으로 Megan에게 전자 메일을 보냅니다. Megan이 흐름을 소유하고 있으므로 다음 전자 메일은 *Megan으로부터* 온 것입니다.
   
    ![Megan Bowen에게 전자 메일 보내기](./media/sharepoint-scenario-approval-flow/03-02-05-megan-email.png)

## <a name="next-steps"></a>다음 단계
이 자습서 시리즈의 다음 단계에서는 [프로젝트를 관리하는 앱을 만듭니다](sharepoint-scenario-build-app.md).

