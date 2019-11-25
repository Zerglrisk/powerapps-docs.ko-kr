---
title: 'FAQ: 검사 목록: 통합 인터페이스 전환 | MicrosoftDocs'
description: 레거시 웹 클라이언트에서 통합 인터페이스로 사용자를 이동하기 위한 자동 전환 프로세스와 관련된 FAQ.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 373201de630b46adc80b25eed10686da9112bad6
ms.sourcegitcommit: c094590862142155cbafa91c6ee0ade975c82083
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "2769447"
---
# <a name="faqs-unified-interface-transition"></a>FAQ: 검사 목록: 통합 인터페이스 전환

이 항목은 레거시 웹 클라이언트에서 통합 인터페이스로 사용자를 이동시키는 전환 프로세스에 대한 가장 일반적인 질문에 대한 답변을 제공합니다.

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-assigned-to-my-environments"></a>내 환경에 지정된 전환 날짜를 어디에서 확인할 수 있습니까? 

자동 전환 포털을 사용하여 환경 전환 날짜를 관리하십시오. <https://runone.powerappsportals.com>

### <a name="how-do-i-gain-access-to-the-portal"></a>포털에 액세스하려면 어떻게 해야 합니까?

합니다.
1. <https://runone.powerappsportals.com>을 방문하십시오.
2. 관리하려는 테넌트의 관리자 자격 증명으로 로그인하십시오.
3. **내 환경**을 선택하고 대상 날짜가 지정된 모든 환경을 검토하십시오.

### <a name="i-see-my-environment-has-a-date-for-auto-transition-can-i-change-this-date"></a>내 환경에 자동 전환 날짜가 표시됩니다. 이 날짜를 변경할 수 있습니까?

예, 테넌트에 대한 **전역 관리자** 또는 **서비스 관리자** 역할이 있다면 가능합니다. 날짜를 변경하려면 환경 옆에 있는 드롭다운 아이콘을 선택하여 레코드를 표시하십시오. 그러면 테넌트 관리자 역할이 이전 또는 이후 전환 날짜에 대한 예외 요청을 제출할 수 있습니다.

- 이전 전환 날짜의 경우 목록에서 기존 날짜를 원하는 옵션으로 업데이트하십시오. 승인이 필요하지 않습니다. 날짜가 적합하지 않은 경우 수동으로 전환할 수도 있습니다.

- 이후 전환 날짜의 경우 예외 요청을 제출할 수 있습니다. 제안된 날짜는 드롭다운에서 사용할 수 있습니다. 승인되면 날짜가 포털에서 업데이트됩니다.

환경당 총 2개의 예외를 요청할 수 있습니다. 선택한 제안 날짜와 함께 비즈니스 타당성을 근거로 예외가 부여됩니다. 확인되면 포털 내에서 날짜가 업데이트됩니다.

> [!NOTE]
> 예약된 전환이 48시간 내에 있으면 날짜를 변경할 수 없습니다. 마찬가지로 기존 웹 클라이언트를 더 이상 사용할 수 없으므로 2020년 10월 1일 이후의 날짜를 요청할 수 없습니다.

### <a name="my-auto-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-transition-taking-place"></a>자동 전환 날짜가 48시간 이내이며 포털 내에서 날짜를 변경할 수 없습니다. 전환 발생을 어떻게 막을 수 있습니까?

환경의 전환 날짜를 변경하는 기능은 전환 48시간 전까지만 사용할 수 있습니다. 이 기간 후에 프로세스를 중지하려면 지원 사례를 제기하십시오. 

> [!NOTE]
> 포털에서 날짜가 잠긴 후(48 시간 이내) 요청이 이루어진 경우 전환이 중지될 수 있음을 보장할 수 없습니다.

### <a name="i-have-environments-without-a-target-auto-transition-date-can-i-update-these-to-include-a-date"></a>대상 자동 전환 날짜가 없는 환경이 있습니다. 날짜를 포함하도록 업데이트할 수 있습니까?

예, 테넌트에 대한 **전역 관리자** 또는 **서비스 관리자** 역할이 있다면 환경을 선택하고 예외 요청을 제출한 후 대상 날짜 목록을 사용하여 제안된 시간 프레임으로 업데이트하십시오. 

해당 날짜로 포털을 업데이트하여 확인합니다. 전환 날짜가 가까워지면 알림 전자 메일이 전역 테넌트 관리자에게도 전송됩니다. 이 문서에 설명된 표준 미리 알림 절차를 따릅니다.

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>전환하기 전에 실행해야 하는 권장 점검 목록이 있습니까?

[커뮤니티 사이트](https://community.dynamics.com/365/unified-interface/)에서 지원되는 콘텐츠를 확인하십시오. 또한 효과적으로 계획하는 데 도움이 되는 [전환 점검표](https://aka.ms/UIChecklist)도 있습니다. 통합 인터페이스로 쉽게 전환할 수 있도록 신중하게 검토하십시오.

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-wish-to-move-back-to-the-legacy-web-client-is-this-possible"></a>내 환경이 전환되었지만 사용자에 대한 차단 문제가 발견되어 레거시 웹 클라이언트로 돌아가고 싶습니다. 이것이 가능한가요?

예, 전환 후 최대 10일 동안 레거시 웹 클라이언트로 다시 전환할 수 있습니다. 처음 4일 동안 [수동으로 전환](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only)할 수 있습니다. 또는 해당 시점 이후에는 수동 스위치가 비활성화되므로 일반 채널에서 지원 요청을 제기하십시오. 

> [!NOTE]
> 해당 날짜 이후에는 레거시 웹 클라이언트를 더 이상 사용할 수 없으므로 10일 기간은 2020년 10월 1일 이전이어야 합니다.

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>2020년 10월 1일 이후에 전환하고 싶습니다. 이것이 가능한가요?

사용 가능한 레거시 웹 클라이언트는 2020년 10월 1일 이후에는 사용할 수 없습니다. 해당 날짜 이후로 전환을 연기할 수는 없습니다.

차단 항목이 있으면 가능한 빨리 표준 지원 프로세스를 사용하여 기록하십시오.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>이 과정에서 표준 알림 절차는 무엇입니까?

Microsoft는 다음과 같은 커뮤니케이션을 보냅니다.

-   전환 날짜가 지정된 각 환경에 대한 초기 메시지
-   포털 내에서 날짜가 잠기기 2일 전 미리 알림 메시지
-   전환 날짜를 알리는 최종 미리 알림이 잠기고 계속 진행됩니다.
-   성공을 확인하기 위한 종료 메시지(또는 문제가 발생한 경우)

다음 채널을 사용하여 메시지를 볼 수 있습니다.
-   Microsoft 365 테넌트 내의 메시지 센터. 이것은 일반적으로 전역 관리자, 서비스 관리자, 서비스 메시지 독자와 같은 역할에 표시됩니다.
-   다이렉트 전자 메일.  전자 메일은 해당 특정 환경의 시스템 관리자 역할 또는 환경 관리 포털의 "알림" 탭에 추가된 전자 메일 주소로만 전송됩니다.

> [!NOTE]
> 사용자 계정에 시스템 관리자 역할이 있는 각 환경에 대해 전자 메일이 발송됩니다.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>연기할 날짜를 요청했지만 여전히 내 환경이 전환되도록 설정되었다는 전자 메일과 메시지 센터 게시물을 수신하고 있습니다. 걱정해야 합니까?

첫 번째 권장 사항은 이 모든 환경에 대한 단일 사실 소스가 될 전환 포털(<https://runone.powerappsportals.com/>)을 확인하는 것입니다. 날짜가 업데이트되었으면 통신 목록을 업데이트하기 전에 통신 시스템에서 메시지를 보냈을 가능성이 높습니다. 

포털의 날짜가 새 날짜로 업데이트되지 않은 경우 표준 절차에 따라 지원 요청을 제기하십시오.

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>환경이 통합 인터페이스로 이미 전환된 경우에도 다시 수동으로 레거시 웹 클라이언트로 전환할 수 있습니까?

환경이 전환된 지 4일 이상 지닌 경우 기존 웹 클라이언트로 다시 수동 전환을 사용 중지할 것입니다. 

이 기능이 비활성화되어 있고 다시 전환해야 하는 경우 일반 채널에서 평가를 위해 지원 요청을 제기하십시오.

### <a name="is-there-a-specific-day-and-time-when-automatic-transitions-will-take-place"></a>자동 전환이 발생하는 특정 요일과 시간이 있습니까? 

이러한 전환을 수행할 때 다운타임이 발생하는 것을 원하지 않습니다. 그러나 표준 정책 및 커뮤니케이션에 명시된 것과 동일한 유지 보수 일정에 따라 금요일에 자동으로 전환될 것입니다. 추가 정보: [유지 보수 타임라인](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)




