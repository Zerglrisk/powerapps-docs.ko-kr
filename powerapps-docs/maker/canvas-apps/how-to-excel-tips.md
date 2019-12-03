---
title: Excel에서 표 서식 지정 | Microsoft Docs
description: Power Apps에서 Excel 데이터를 사용 하려면 데이터를 테이블로 서식 지정 해야 합니다. 열 이름에 '이미지' 키워드 추가
author: yifwang
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7b620205ed3fdeaa61768b62ef2db27a850be374
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732166"
---
# <a name="format-a-table-in-excel-and-naming-tips"></a>Excel에서 표 서식 지정 및 이름 지정 팁
Power Apps에서는 테이블로 형식이 지정 된 경우에만 Excel 데이터를 기반으로 캔버스 앱을 만들 수 있습니다. 이 콘텐츠를 따라가면 Excel 열의 이름을 지정하는 몇 가지 팁 및 Excel에서 표의 서식을 지정하는 방법을 알게 됩니다.

## <a name="how-to-format-a-table-in-excel"></a>Excel에서 표의 서식을 지정하는 방법
Excel의 **홈** 탭에서 **테이블로 형식 지정**을 선택하면 사용자 데이터를 테이블로 변환할 수 있습니다.

![Excel에서 테이블의 형식 지정](./media/how-to-excel-tips/format-table.png)

**삽입** 탭에서 **테이블**을 선택하여 테이블도 만들 수 있습니다.

![Excel에서 테이블 삽입](./media/how-to-excel-tips/insert-table.png)

테이블을 쉽게 찾으려면 **테이블 도구** 아래의 **디자인**으로 이동하고 테이블의 이름을 바꿉니다. 특히 동일한 Excel 파일에 둘 이상의 테이블이 있는 경우 테이블에 의미 있는 이름을 지정하는 것이 유용합니다.

![Excel에서 테이블 이름 바꾸기](./media/how-to-excel-tips/rename-table.png)

## <a name="naming-tips-in-excel"></a>Excel에서 이름 지정 팁
표의 열에 이미지가 포함된 경우 해당 열의 이름에 '이미지'를 포함합니다. 이 키워드는 해당 열을 갤러리의 이미지 컨트롤에 바인딩합니다.

![이미지를 사용하여 Excel 테이블 연결](./media/how-to-excel-tips/connect-gallery.png)

## <a name="next-steps"></a>다음 단계
* 지정한 테이블을 기준으로 [Power Apps의 Excel에서 앱을 생성](get-started-create-from-data.md) 합니다. 해당 앱에는 기본적으로 3개의 화면이 있는데 레코드를 검색하고, 단일 레코드에 대한 세부 정보를 표시하며, 레코드를 생성 또는 업데이트하기 위한 화면들입니다.
* Excel에서 서식을 지정한 표을 사용하여 [처음부터 앱을 만듭니다](get-started-create-from-blank.md). 앱을 수동으로 만들고 사용자 지정하여 표의 데이터를 표시, 탐색 또는 편집할 수 있습니다.
