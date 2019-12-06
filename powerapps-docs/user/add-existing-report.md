---
title: 외부 앱에서 보고서 추가 | Microsoft Docs
description: 외부 앱에서 보고서 추가
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
ms.openlocfilehash: e730d498a4d82518d0f908645e26a541c1e8c6af
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725851"
---
# <a name="add-a-report-from-outside-power-apps"></a>외부 앱에서 보고서 추가

시스템 외부에서 사용자 지정 보고서를 만든 경우 Power Apps에 쉽게 추가할 수 있습니다.

사용자 지정 보고서를 만드는 방법에 대 한 자세한 내용은 [보고 및 분석 가이드](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports)를 참조 하세요.

1. 왼쪽 탐색 창에서 보고서 영역을 선택 합니다. 
2. 명령 모음에서 **새로 만들기**를 선택 합니다.
  
   **다른 응용 프로그램에서 만든 파일 추가**  
  
   1. **원본** 섹션의 **보고서 유형** 상자에서 **기존 파일**을 선택 합니다.  
   
     > [!div class="mx-imgBorder"]
     > ![기존 보고서 추가](media/add_existing_report.png "기존 보고서 추가")
  
   2. **파일 위치** 상자에 추가할 파일의 경로 및 파일 이름을 입력 하거나 **찾아보기** 를 선택 하 여 파일을 찾습니다. 
   
      Excel 파일 등의 다른 많은 파일 형식을 업로드할 수 있지만이를 SQL Server Reporting Services 보고서 또는 보고서 마법사에서 만든 보고서와 같이 실행 하려면 파일이 여야 합니다. RDL 파일입니다. 자세한 내용은 [SQL Server Data Tools를 사용 하 여 보고서 작성 환경](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools)을 참조 하세요.
  
      -또는  
  
   **웹 페이지에 링크 추가**  
  
   1.  **원본** 섹션의 **보고서 유형** 상자에서 **웹 페이지에 연결**을 선택 합니다.  
  
   2.  **웹 페이지 url** 상자에 웹 페이지의 url을 입력 합니다.  
  
3. 보고서의 속성을 지정 합니다.
  
   1.  **세부 정보** 섹션에서 보고서의 의미 있는 이름 및 설명을 지정 합니다.  
  
   2.  **부모 보고서** 텍스트 상자에는 현재 보고서에 대 한 부모 보고서 (있는 경우)가 표시 됩니다.  
  
   3. **범주**. **이 필드에 대 한 값 선택 또는 변경** ![줄임표 단추](media/ellipsis-button.png "줄임표 단추") 단추를 선택 하 고이 보고서에 포함할 범주를 지정 합니다.  
  
   4. **관련 레코드 유형**입니다. 특정 레코드 유형에 대 한 페이지의 보고서 목록에 보고서가 표시 되도록 하려면 **이 필드에 대 한 값 선택 또는 변경** ![줄임표 단추](media/ellipsis-button.png "줄임표 단추") 단추를 선택한 다음 레코드 유형을 선택 합니다.  
  
   5. **에를 표시**합니다. 보고서를 표시할 위치를 지정 하려면 **이 필드의 값을 선택 하거나 변경** 하십시오. ![줄임표 단추](media/ellipsis-button.png "줄임표 단추") 단추를 선택 하 고 하나 이상의 옵션을 선택 합니다.  
  
        값을 선택 하지 않으면 보고서가 최종 사용자에 게 표시 되지 않습니다.  
  
4. **저장** 또는 **저장 후 닫기를**선택 합니다.  




### <a name="see-also"></a>참고 항목
[보고서 작업](work-with-reports.md) 

[보고서 마법사를 사용 하 여 보고서 만들기](create-report-with-wizard.md)

[보고서 필터 편집](edit-report-filter.md)

[보고서에 표시 되지 않는 데이터 문제 해결](troubleshoot-reports.md)
