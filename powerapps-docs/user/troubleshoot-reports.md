---
title: 보고서에 표시 되지 않는 데이터 문제 해결 | Microsoft Docs
description: 보고서에 표시 되지 않는 데이터 문제 해결
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
ms.openlocfilehash: 1156aa8fb5fbc3ae51c21b8aa41606df6dbc2e86
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420769"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>보고서에 표시 되지 않는 데이터 문제 해결

보고서에 있을 것으로 예상 되는 데이터가 표시 되지 않는 이유는 여러 가지가 있습니다.  
  
- **보안 권한이 부족**합니다. Common Data Service에서 레코드를 볼 수 있는 권한이 없는 경우 보고서에 표시 되지 않습니다.  
  
- **데이터를 입력 하지 않았습니다.** 데이터를 입력 하는 사람이 왼쪽 필드를 비워 둘 수 있습니다.  
  
- **데이터가 보고서의 기준과 일치 하지 않습니다.** 많은 보고서에는 활성 레코드만 표시 하는 기본 필터가 포함 되어 있거나 일치 하는 레코드가 없는 조건이 선택 되어 있을 수 있습니다. 보고서 필터를 변경해 보세요. 자세한 내용은 [보고서의 기본 필터 편집](edit-report-filter.md) 을 참조 하세요.  
  
- **보고서의 캐시 된 복사본을 볼 수 있습니다.** 기본적으로 Common Data Service 보고서의 데이터는 보고서를 실행할 때마다 데이터베이스에서 가져옵니다. 그러나 시스템 관리자가 캐시에서 실행 되도록 보고서를 변경 했을 수 있습니다. 최근에 입력 한 데이터가 보고서에 포함 되지 않은 경우 캐시에서 이전 버전의 보고서가 있을 수 있습니다. 보고서를 새로 고치려면 보고서 도구 모음에서 **새로 고침** 단추를 선택 합니다.  
  
- **하위 보고서에서 레코드를 읽을 수 있는 권한이 없는 것일 수 있습니다.** 하위 보고서에 포함 된 레코드 종류를 읽을 수 있는 권한이 없는 경우 하위 보고서를 표시할 수 없다는 오류 메시지가 표시 됩니다.  
  
- **Microsoft Internet Explorer 개인 정보 설정이 필요한 쿠키를 차단할 수 있습니다.** 차트 보고서의 경우 차트를 보는 대신 빨간색 문자 X가 표시 되 면 개인 정보 설정에 따라 차트 컨트롤에 필요한 쿠키가 차단 될 수 있습니다. 이 문제를 해결 하려면 브라우저에서 Reporting Services를 실행 하는 서버의 쿠키를 사용 하도록 설정 합니다.  
  

### <a name="see-also"></a>참고 항목
[보고서 작업](work-with-reports.md) 

[보고서 마법사를 사용 하 여 보고서 만들기](create-report-with-wizard.md)

[기존 보고서 추가](add-existing-report.md)

[보고서 필터 편집](edit-report-filter.md)

