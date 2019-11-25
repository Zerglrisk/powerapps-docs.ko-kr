---
title: Common Data Service에서 데이터 가져오기 또는 내보내기
description: Excel에서 데이터 가져오기 및 데이터 내보내기 기능을 사용하여 Common Data Service의 엔터티로 Excel 또는 CSV 파일의 데이터를 대량으로 가져오고 내보냅니다.
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8aad3e440e93becd4741223f1450dd8e3b34921a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755582"
---
# <a name="import-or-export-data-from-common-data-service"></a>Common Data Service에서 데이터 가져오기 또는 내보내기

Microsoft Excel 또는 CSV 파일에서 대량으로 데이터 가져오고 내보내려면 업데이트된 Common Data Service 환경에 대해 Excel 파일에서 데이터 가져오기 또는 데이터 내보내기 기능을 사용합니다.

Excel 또는 CSV 파일에서 엔터티로 파일을 가져올 수 있는 방법은 두 가지가 있습니다.

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>옵션 1: 파일 템플릿을 만들고 수정하여 가져오기

모든 엔터티에는 입력 파일에 있어야 하는 필수 필드가 있습니다. 템플릿을 만드는 것이 좋습니다. 먼저 엔터티에서 데이터를 내보냅니다. 데이터로 수정된 동일한 파일을 사용하여 엔터티로 데이터를 가져옵니다. 이 템플릿은 시간과 노력을 줄여줍니다. 각 엔터티에 대해 필수 필드를 고려할 필요는 없습니다.

1. 파일 템플릿을 준비합니다.

    a. 엔터티 데이터를 CVS 파일로 내보냅니다. **CSV로 데이터 내보내기**의 단계를 따릅니다.  
    b. 데이터가 고유한지 확인하는 계획을 정의합니다. **기본** 키 또는 **대체 키**를 사용합니다.  
    c. 엔터티로 가져오기 전에 데이터가 고유한지 확인 하는 지침은 다음 섹션을 참조하십시오. 

1. 데이터를 사용하여 파일을 수정합니다.

    - Excel 또는 CSV 파일의 데이터를 방금 만든 템플릿으로 복사합니다.

1. 파일을 가져옵니다.  
    a. [powerapps.com](https://make.powerapps.com/)에서 **데이터** 섹션을 확장합니다. 왼쪽 탐색 창에서 **엔터티**를 선택합니다.  
    b. 데이터를 가져오려는 엔터티를 선택합니다.  
    c. 맨 위에 있는 줄임표 또는 메뉴를 선택합니다. **데이터 가져오기**를 선택합니다. **Excel에서 데이터 가져오기**를 선택합니다.  

    > [!NOTE]
    > 데이터를 둘 이상의 엔터티로 가져오려면 상단 메뉴에서 **데이터 가져오기**를 선택합니다. **Excel에서 데이터 가져오기**를 선택합니다. 그런 다음 여러 엔터티를 선택하고 **다음**을 선택할 수 있습니다.

    > [!div class="mx-imgBorder"] 
    > ![**계정** 엔터티로 데이터를 가져오는 예](./media/data-platform-import-export/import-data-to-account.png)

    d. **데이터 가져오기** 화면에서 Excel 또는 CSV 파일에서 데이터를 가져올지 여부를 선택합니다.  
    e. **업로드**를 선택합니다.  
    f. 파일을 선택합니다. 메시지에 따라 파일을 업로드합니다.  

    > [!div class="mx-imgBorder"] 
    > ![**계정** 엔터티에 파일을 업로드하는 예](./media/data-platform-import-export/upload-account.png)

    g. 파일이 업로드되고 **매핑 상태**가 녹색이면 오른쪽 위에서 **가져오기**를 선택합니다. 다음 섹션을 참조하여 매핑 오류를 탐색하고 수정합니다.  

    > [!div class="mx-imgBorder"] 
    > ![성공적인 **매핑 상태** 및 **가져오기** 버튼의 예](./media/data-platform-import-export/success-map-imp.png)

    h. 가져오기가 성공적으로 완료되면 총 삽입 및 업데이트 수가 표시됩니다.  

    > [!div class="mx-imgBorder"] 
    > ![삽입 및 업데이트 수를 보여주는 성공적인 가져오기 예](./media/data-platform-import-export/success-imp-insert.png)

    > [!NOTE]
    > Upsert(업데이트 또는 삽입) 논리를 사용하여 레코드가 이미 있는 경우 업데이트하거나 새 레코드를 삽입합니다.

## <a name="option-2-import-by-bringing-your-own-source-file"></a>옵션 2: 원본 파일을 가져와 가져오기

고급 사용자이고 Common Data Service 엔터티에 대해 주어진 엔터티의 대한 필수 필드를 알고 있는 경우 고유한 Excel 또는 CSV 원본 파일을 정의합니다. **파일 가져오기**의 단계를 따릅니다.

## <a name="navigate-mapping-errors"></a>매핑 오류 탐색

파일을 업로드한 후 매핑 오류가 발생하면 **맵 상태**를 선택합니다. 다음 단계를 수행하여 필드 매핑 오류를 검사하고 수정합니다.

1. **표시** 아래의 오른쪽에 있는 드롭다운 메뉴를 사용하여 **매핑되지 않은 필드**, **오류가있는 필드** 또는 **필수 필드**를 단계별로 안내합니다.

    > [!TIP]
    > 경고나 오류가 발생하는지 여부에 따라**필드 매핑**의 드롭다운 메뉴를 통해 **매핑되지 않은 필드**나 **오류가 있는 필드**를 검사합니다.

    > [!div class="mx-imgBorder"] 
    > ![필드 매핑이 있는 경고로 인한 부분 일치 예](./media/data-platform-import-export/partial-match.png)

    > [!div class="mx-imgBorder"] 
    > ![필드 매핑 문제 탐색 예](./media/data-platform-import-export/navigate-mappings.png)

    > [!div class="mx-imgBorder"] 
    > ![필드 매핑을 사용하여 경고 검사 및 조정 예](./media/data-platform-import-export/inspect-warnings.png)

2. 모든 오류 및 경고를 해결한 후 오른쪽 위에서 **변경 내용 저장**을 선택합니다. **데이터 가져오기** 화면으로 돌아갑니다.
3. **매핑 상태** 열에 **완료**가 녹색으로 표시되면 **오른쪽** 위 모서리에서 가져오기를 선택합니다.
4. **가져오기가 성공적으로 완료됨** 메시지가 표시되면 총 삽입 및 업데이트가 표시됩니다.

## <a name="ensure-uniqueness-when-you-import-data-into-an-entity-from-excel-or-csv"></a>Excel 또는 CSV에서 엔터티로 데이터를 가져올 때 고유성 보장

Common Data Service 엔터티는 기본 키를 사용하여 Common Data Service 엔터티 테이블 내의 레코드를 고유하게 식별합니다. Common Data Service 엔터티의 기본 키는 GUID(Globally Unique Identifier)입니다. 레코드 식별에 대한 기본 기반을 형성합니다. Common Data Service 엔터티로 데이터를 가져오는 등의 데이터 작업은 기본값인 기본 키를 노출합니다.

예제:  
**거래처** 엔터티의 기본 키는 **accountid**입니다.

   > [!div class="mx-imgBorder"] 
   > ![**accountid**를 기본 키로 표시하는 **거래처** 엔터티의 샘플 내보내기 파일](./media/data-platform-import-export/export-pk.png)

경우에 따라 외부 원본의 데이터를 통합할 때 기본 키가 작동하지 않을 수 있습니다. Common Data Service를 사용하여 기본 키 대신 레코드를 고유하게 식별하는 대체 키를 정의합니다.

예제:  
**거래처** 엔터티의 경우에는 자연 키 기반 ID를 사용하여 **transiccurcycid**를 대체 키로 설정할 수 있습니다. 예를 들어 이전에 표시된 GUID 값 **88c6c893-5b45-e811-a953-000d3a33bcb9** 대신 **미국 달러**를 사용합니다. 또한 **통화 기호** 또는 **통화 이름**을 키로 선택할 수 있습니다.

   > [!div class="mx-imgBorder"] 
   > ![**통화** 엔터티에 대체 키를 만드는 예](./media/data-platform-import-export/create-ak.png)

   > [!div class="mx-imgBorder"] 
   > ![**통화 이름**를 자연 키로 표시하는 **거래처** 엔터티의 샘플 내보내기 파일](./media/data-platform-import-export/export-nk.png)

사용자는 대체 키를 지정한 후에도 기본 키를 식별자로 사용할 수 있습니다. 이전 샘플에서는 GUID가 유효한 데이터인 경우 첫 번째 파일이 여전히 유효합니다.

## <a name="export-data-to-csv"></a>CSV로 데이터 내보내기

표준 엔터티 또는 사용자 지정 엔터티에서 일회성 데이터 내보내기를 수행할 수 있습니다. 한 번에 둘 이상의 엔터티에서 데이터를 내보낼 수 있습니다. 둘 이상의 엔터티에서 데이터를 내보내는 경우 각 엔터티는 자체 Microsoft CSV 파일로 내보내집니다.

1. [powerapps.com](https://make.powerapps.com/)에서 **데이터** 섹션을 확장합니다. 왼쪽 탐색 창에서 **엔터티**를 선택합니다.
1. 데이터를 내보내려는 엔터티를 선택합니다.
1. 맨 위에 있는 줄임표 또는 메뉴를 선택합니다. **내보내기**를 선택합니다. **데이터**를 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![**계정** 엔터티에서 데이터를 내보내는 예](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > 여러 엔터티에서 데이터를 내보내려면 위쪽 메뉴에서 **내보내기**를 선택합니다. **데이터**를 선택합니다. 여러 엔터티를 선택할 수 있습니다.

1. 내보내기가 성공적으로 완료되면 **내보낸 데이터를 다운로드**할 수 있습니다. 이 다운로드는 다운로드할 수 있는 CSV 파일에 대한 링크를 제공합니다.

    > [!div class="mx-imgBorder"] 
    > ![링크 다운로드 가능 파일과 함께 성공적인 내보내기를 보여주는 샘플 내보내기](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>지원되지 않는 데이터 형식

다음 데이터 형식은 현재 지원되지 않습니다.

- 표준 시간대
- 다중 선택 옵션 집합
- 이미지
