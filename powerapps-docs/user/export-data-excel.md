---
title: PowerApps에서 Excel로 데이터 내보내기 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 2c23b25c062bc5ac4be26132c63f4cc4a79c3fad
ms.sourcegitcommit: b3fd824cf0d540b964b729686b198c7ccf2c2174
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316865"
---
# <a name="export-data-to-excel"></a>Excel로 데이터 내보내기

에서 데이터를 분석 하 고 해당 데이터를 더 많은 판매를 구동 하는 데 도움이 되는 실행 가능한 항목으로 변환 해야 하나요? 이제 데이터를 Excel 또는 Excel Online으로 내보낼 때이 작업을 수행할 수 있습니다. 또한 최대 10만 개의 데이터 행을 내보낼 수 있으므로 많은 데이터 집합을 분석 하는 것은 문제가 되지 않습니다.
  
정적 워크시트 또는 동적 워크시트를 내보내도록 선택할 수 있습니다 .이 워크시트는 앱으로 다시 가져올 수 있습니다. 고급 함수가 필요한 경우 동적 피벗 테이블을 내보내 데이터를 매우 쉽게 구성 하 고 요약할 수 있습니다.  
  
휴대폰, 태블릿 또는 데스크톱 컴퓨터와 같은 장치에서 사용할 수 있는 표준 Excel 파일로 데이터를 내보낼 수 있습니다. 데이터는 앱에 표시 되는 것과 동일한 형식으로 내보내집니다. 텍스트는 텍스트로 유지 되 고 숫자는 숫자로 유지 되며 날짜는 그대로 유지 됩니다. 그러나 앱에서 Excel로 데이터를 내보내는 경우 일부 셀 형식이 변경 될 수 있습니다. 다음 표에서는 데이터를 Excel로 내보낼 때 앱의 데이터와 셀 형식이 어떻게 변경 되는지 요약 하 여 보여 줍니다.  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>모델 기반 앱에서 데이터를 내보낼 때의 셀 형식
  
| 모델 기반 앱의 데이터 형식 |                                            Excel의 셀 서식                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            텍스트, 종목 기호, 전화, 옵션 집합 및 조회            |                                                       텍스트 및 옵션 집합이 드롭다운 목록으로 표시 됩니다.                                                       |
|                                 전자 메일, URL                                 |                                                                        일반으로 표시                                                                         |
|                                   숫자                                   |                                                             그룹 구분 기호 없이 숫자로 표시                                                             |
|                                  통화                                  |                                                         숫자로 표시 하 고 달러 기호 ($)를 포함 하지 않습니다.                                                         |
|                          날짜만, 날짜 및 시간                          |                                                                       날짜만 표시                                                                        |
|                       계산 및 롤업 필드                        | Excel에서 편집할 수 있지만 PowerApps로 다시 가져올 수 없습니다. |
|                               보안 필드                               | Excel에서 편집할 수 있지만 PowerApps로 다시 가져올 수 없습니다. |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>사용자에 게 가장 적합 한 내보내기 유형을 확인 하세요.  
  
|                                                                                                               태스크                                                                                                                |                                              자세한 정보                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   앱 데이터를 수정 하지 않고 *임시* 또는 *가상* 분석을 수행 합니다. 또는 여러 레코드를 신속 하 게 대량 편집할 수 있습니다.   | [Excel Online으로 내보내기](export-to-excel-online.md) |
|                                                                   현재 데이터 및 시간에 데이터의 스냅숏을 가져오거나 다른 사용자와 공유 하려고 합니다.                                                                    |           [Excel 정적 워크시트로 내보내기](export-excel-static-worksheet.md)           |
| 최신 정보를 얻고 Excel에서 새로 고칠 수 있으며 언제 든 지 앱에 표시 되는 정보를 찾을 수 있습니다. |          [Excel 동적 워크시트로 내보내기](export-excel-dynamic-worksheet.md)          |
|                                                                      피벗 테이블에서 응용 프로그램 데이터를 봅니다.                                                                      |                 [Excel 피벗 테이블로 내보내기](export-excel-pivottable.md)                 |



Excel (.xlsx 형식)에서 데이터를 내보낸 다음 열을 추가 하거나 수정 하는 경우 데이터를 Dynamics 365로 다시 가져올 수 없습니다. .Xlsx 파일 형식에는 지원 되지 않습니다.  
  
Excel 2010를 사용 하는 경우 계정 영역에서 데이터를 내보낼 때 다음과 같은 오류 메시지가 나타날 수 있습니다. 
 
`The file is corrupt and cannot be opened.`  
  
Excel의 설정으로 인해 발생 하는 오류 메시지입니다. 이 문제를 해결 하려면 다음을 수행 합니다.  
  
1. Excel 2010를 엽니다.  
  
2. **파일** > **옵션**으로 이동 합니다.  
  
3. **보안 센터** > **보안 센터 설정**으로 이동 합니다.  
  
4. **보호 된 보기** 를 선택 하 고 처음 두 옵션에 대 한 확인란의 선택을 취소 합니다.  
  
5. **확인** 을 선택한 다음 **옵션** 대화 상자를 닫습니다.  
  
