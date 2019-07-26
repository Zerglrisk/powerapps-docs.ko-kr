---
title: 모델 기반 앱에서 Excel Online으로 데이터 내보내기 | MicrosoftDocs
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
ms.openlocfilehash: 6cb8fe650db464f41c63af87c3fcb34bb2203cf2
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544802"
---
# <a name="export-your-data-to-excel-online"></a>데이터를 Excel Online으로 내보내기 

앱에서 Excel Online으로 데이터를 내보내 앱에 있는 데이터에 대 한 임시 분석을 신속 하 게 수행할 수 있습니다.
  
Excel Online에서 데이터를 변경 하는 경우 앱에 업데이트 된 정보를 저장할 수 있습니다. 가져오는 동안 문제를 방지 하려면 Excel 셀의 기존 형식을 유지 해야 합니다. 그래프, 차트, 색 등의 스프레드시트에 추가 된 정보는 저장 되지 않습니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
  
- 이 기능을 사용하려면 SharePoint Online 또는 Exchange Online과 같은 온라인 서비스에 대한 Office 365 구독 또는 구독이 있어야 합니다.
  
- Microsoft 계정 필요 합니다.    
  
## <a name="open-app-data-in-excel-online"></a>Excel Online에서 앱 데이터 열기  

Excel Online에서 데이터를 여는 옵션은 일부 레코드 유형에 서 사용할 수 없습니다. 옵션이 표시 되지 않으면 해당 레코드에 대해 사용할 수 없습니다.  
  
> [!NOTE]
> Excel Online에서 지난 2 분간 동일한 보기가 열려 있으면 앱의 업데이트 된 데이터가 즉시 Excel Online에 반영 되지 않습니다. 해당 시간 프레임 후에 업데이트 된 모든 데이터가 Excel Online에 표시 됩니다.
  
앱에서 레코드 목록을 열려면 명령 모음에서 **excel로 내보내기** 메뉴를 선택 하 고 **Excel Online에서 열기**를 선택 합니다. 

> [!div class="mx-imgBorder"] 
> ![Excel Online으로 내보내기](media/exportexcelonline.png "Excel Online으로 내보내기")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>데이터를 저장 하 고 앱으로 다시 가져오기  
  
1. 변경을 완료 한 후 **저장**을 선택 합니다.  
  
   > [!NOTE]
   > - Excel Online에서 *임시* 분석을 위한 데이터는 임시로 저장 됩니다. 차트, 계산 및 열과 같은 추가 사항은 Excel Online의 임시 분석에서 앱에 다시 저장 되지 않습니다.  
   > 
   > - 많은 변경 작업을 수행 하면 파일 가져오기가 실패할 수 있습니다. 데이터를 변경 하 고 앱으로 다시 가져와야 하는 경우 대신 Excel에서 워크시트를 내보내는 것이 좋습니다.  
   > 
   > - 디자인을 통해 Excel Online에서 **파일** > 을 다른 이름**으로 저장할** 수 없습니다. 이렇게 하면 **통합 문서를 저장할 수 없음** 오류 메시지가 표시 됩니다.   
2. **가져오기를 위해 전송 된 데이터** 대화 상자에서 **닫기**를 선택 합니다.  
  

  

 
