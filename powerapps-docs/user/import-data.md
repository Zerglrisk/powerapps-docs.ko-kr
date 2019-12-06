---
title: 모델 기반 앱에서 데이터 가져오기 | Microsoft Docs
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
ms.openlocfilehash: 8f1105fc88fe87aabceaa10160b96e2d7299cbe0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733206"
---
# <a name="import-data"></a>데이터 가져오기

데이터가 스프레드시트, 휴대폰, 메일 프로그램 중 어디에 저장되어 있든, 데이터를 앱으로 가져오는 방법은 다음과 같습니다. 예를 들어 한 곳에서 모든 고객 정보를 관리할 수 있도록 Excel 스프레드시트의 고객 연락처 목록을 앱으로 가져올 수 있습니다.
  
## <a name="step-1-get-your-import-file-ready"></a>1 단계: 가져오기 파일 준비  
먼저 데이터를 Excel 파일로 내보냅니다. 지원되는 파일 형식은 다음과 같습니다.
 - Excel 통합 문서(.xlsx)
 - 쉼표로 구분된 값(.csv)
  
.zip 파일의 허용되는 최대 파일 크기는 32MB입니다. 다른 파일 형식의 경우 허용되는 최대 파일 크기는 8MB입니다.  
  
### <a name="export-data-from-an-email-program"></a>메일 프로그램에서 데이터 내보내기  
  
1.  쉼표로 구분된 값 파일(.csv)로 데이터를 내보냅니다.  
  
     메일 프로그램에서 연락처를 내보내는 특정 단계를 찾으려면 프로그램의 도움말을 열고 “내보내기”를 검색합니다. 제목에 “연락처 내보내기”, “주소록 내보내기” 또는 “내보내기 마법사”가 포함된 항목을 찾습니다.  
  
2.  나중에 쉽게 찾을 수 있는 위치에 파일을 저장합니다.  
  
### <a name="export-data-from-a-spreadsheet"></a>스프레드시트에서 데이터 내보내기  
  
1.  스프레드시트를 엽니다.  
  
2.  필요한 경우 여기에 표시된 해당 이름과 정확하게 일치하도록 스프레드시트의 열 이름을 편집합니다.  
  
    > [!WARNING]
    > 스프레드시트에 나열된 열 이름 중 일부가 포함되어 있지 않은 경우 괜찮습니다. 그러나 열 이름이 없는 경우 목록의 해당 이름과 정확하게 일치해야 합니다. 그렇지 않으면 가져오기가 작동하지 않습니다. 공백이 필요합니다. “Email”이라는 단어에는 하이픈이 포함되어 있지 않습니다.  

    |**스프레드시트의 열 이름(맞춤법이 정확하게 일치해야 함)**|
    |---------|
    |이름|  
    |중간 이름|  
    |성|  
    |회사 전화|  
    |휴대폰|  
    |직위|  
    |회사 주소|  
    |회사 도시|  
    |회사 시/도|  
    |회사 우편 번호|  
    |회사 국가/지역|  
    |이메일 주소|  
  
3.  파일을 저장합니다.  
  
### <a name="export-data-from-your-phone"></a>휴대폰에서 데이터 내보내기  

USB 케이블이나 앱을 사용하여 연락처와 같은 데이터를 휴대폰에서 컴퓨터로 내보냅니다.
  
휴대폰 브랜드의 연락처 내보내기에 대한 특정 단계를 찾으려면 자주 사용하는 검색 엔진(예: Bing)에서 “내 휴대폰에서 연락처 내보내기”를 검색합니다.  
  
앱을 찾으려면 휴대폰의 온라인 스토어를 검색합니다.  
  
## <a name="step-2-import-the-file"></a>2 단계: 파일 가져오기 
  
1. 명령 모음에서 **Excel에서 가져오기** 또는 **CSV에서 가져오기**를 선택합니다.

   > [!div class="mx-imgBorder"]
   > ![Power Apps의 주 메뉴](media/import.png "Power Apps의 주 메뉴")
  
2. 연락처 내보내기가 포함된 파일을 저장한 폴더로 이동합니다. 파일을 선택하고 **열기**를 선택한 후 **다음**을 선택합니다.  
  
   > [!TIP]
   > 파일은 한 번에 하나씩만 가져올 수 있습니다. 파일을 더 가져오려면 나중에 마법사를 다시 실행합니다.
   
3. 파일 이름을 검토하고 **매핑 검토** 옵션을 사용하여 필드 및 데이터 구분 기호가 올바른지 확인합니다. 모든 항목이 올바르면 **가져오기 마침**을 선택합니다.  
 
## <a name="step-3-check-that-the-import-is-successful"></a>3 단계: 가져오기가 성공 했는지 확인

마법사를 마친 후 데이터(예: 연락처 목록)를 확인하여 제대로 가져왔는지 확인합니다.  
  
1. 주 메뉴에서 **연락처**로 이동합니다.
  
2. 연락처 목록을 스크롤합니다. 모든 사람이 나열되어 있는지 확인하고 필드 내용이 정확한지 확인합니다.

## <a name="import-double-byte-characters"></a>더블바이트 문자 가져오기 

동아시아 언어의 경우 더블바이트 문자가 포함된 데이터를 가져오는 경우 파일이 UTF-8 BOM으로 인코딩되었는지 확인합니다. 일반 UTF-8은 충분하지 않을 수 있습니다.

1. Visual Studio Code를 사용하여 CSV 파일을 엽니다.
2. 아래쪽 표시줄에서 **UTF-8** 레이블을 클릭합니다(팝업 열림). 
3. **인코딩하여 저장**을 선택합니다. 

이제 해당 파일에 대해 UTF-8 BOM 인코딩을 선택할 수 있습니다.

