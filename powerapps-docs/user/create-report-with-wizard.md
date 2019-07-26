---
title: 보고서 마법사를 사용 하 여 보고서 만들기 | Microsoft Docs
description: PowerApps에서 보고서 마법사를 사용 하 여 보고서 만들기
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0f953c44d81742baca39058cd68180ca63833eb6
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420286"
---
# <a name="create-a-report-using-the-report-wizard"></a>보고서 마법사를 사용하여 보고서 만들기


보고서 마법사를 사용 하 여 데이터를 쉽게 분석할 수 있는 차트 및 테이블이 포함 된 보고서를 만들 수 있습니다. 

보고서 마법사를 사용 하 여 만든 모든 보고서는 Fetch 기반 보고서입니다. 보고서 마법사를 사용 하 여 생성 된 모든 보고서는 가로 모드로 인쇄 됩니다.

## <a name="create-a-new-report"></a>새 보고서 만들기

1. 왼쪽 탐색 창에서 보고서 영역을 선택 합니다.  
2. 명령 모음에서 **새로 만들기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![새 보고서 만들기](media/newreport.png "새 보고서 만들기")
  
3. **보고서: 새 보고서** 화면이 표시 됩니다. **보고서 유형** 으로 기본 선택, **보고서 마법사 보고서** 를 그대로 두고 **보고서 마법사** 단추를 선택 합니다. 

    > [!div class="mx-imgBorder"]
    > ![보고서 마법사](media/report_wizard.png "보고서 마법사 화면")
  
4. 다음 화면에서 기본 선택 항목을 그대로 두고 **다음**을 선택 합니다.
 
    > [!div class="mx-imgBorder"]
    > ![보고서 마법사](media/report_wizard_1.png "보고서 마법사 화면")
   
4. **보고서 속성** 화면에서 보고서의 이름을 입력 한 다음 보고서에 포함할 레코드를 선택 하 고 **다음**을 선택 합니다.
 
    > [!div class="mx-imgBorder"]
    > ![보고서 속성 화면](media/report_wizard_2.png "보고서 속성 화면")
  
5.  보고서에 **포함할 레코드 선택** 화면에서 필터를 선택 하 여 보고서에 포함 되는 레코드를 결정 합니다. 예를 들어 최근 60 일 동안 수정 된 레코드에 대 한 결과만 보려는 경우이 화면에서 해당 필터를 설정할 수 있습니다. 데이터를 필터링 하지 않으려면 **지우기**를 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![보고서에 포함할 레코드 선택 *](media/report_wizard_3.png "보고서에 포함할 레코드 선택")
  
6. **필드 레이아웃** 화면에서 보고서 레이아웃을 선택 합니다. **그룹화를 추가 하려면 여기를 클릭** 하세요 .를 선택 하 고 데이터를 그룹화 하려는 방법을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![필드 레이아웃](media/report_wizard_4.png "필드 레이아웃")

7. 보고서에서 그룹화 할 데이터의 **열** 과 **레코드 종류** 를 선택 합니다. 선택이 완료 되 면 **확인**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![dd 그룹화 화면](media/report_wizard_5.png "그룹화 화면 추가")
  
8. 이전 단계에서 선택한 레코드 유형과 관련 된 데이터 열에 **열을 추가 하려면 여기를 클릭** 하십시오 .를 선택 합니다.  

    > [!div class="mx-imgBorder"]
    > ![그룹화 화면 추가](media/report_wizard_6.png "그룹화 화면 추가")

9. **열 추가** 화면에서 열에 대해 표시할 데이터를 선택 하 고 **확인**을 선택 합니다. 

    > [!div class="mx-imgBorder"]
    > ![열 추가 화면](media/report_wizard_7.png "열 추가 화면")
  
10. 추가 하려는 추가 열에 대해 이전 단계를 반복 합니다. 작업이 완료 되 면 **필드 레이아웃** 화면에서 눌러 **Next**를 실행 합니다.
 
    > [!div class="mx-imgBorder"]
    > ![열 추가 화면](media/report_wizard_8.png "열 추가 화면")
  
11. **보고서 서식** 화면에서 보고서의 형식을 지정 하는 방법을 선택한 후 **다음**을 선택 합니다.
 
    > [!div class="mx-imgBorder"]
    > ![보고서 서식 지정](media/report_wizard_9.png "보고서 화면 서식 지정")

12. 보고서의 요약을 검토 하 고 **다음** 을 선택한 다음 **마침**을 선택 합니다. 이제 시스템의 보고서 목록에서이 보고서를 볼 수 있습니다.

    > [!div class="mx-imgBorder"]
    > ![보고서 보기](media/report_wizard_10.png "보고서 보기")

### <a name="see-also"></a>참고 항목
[보고서 작업](work-with-reports.md) 

[기존 보고서 추가](add-existing-report.md)

[보고서 필터 편집](edit-report-filter.md)

[보고서에 표시 되지 않는 데이터 문제 해결](troubleshoot-reports.md)


