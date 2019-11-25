---
title: Excel에서 엔터티 열기 | Microsoft Docs
description: 대화형 보기 및 편집을 위해 Excel에서 엔터티 데이터를 엽니다.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fa1602b59ed0fdfeec09a8bc7e5f1126249f071f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757495"
---
# <a name="open-entity-data-in-excel"></a>Excel에서 엔터티 데이터 열기
Microsoft Excel에서 엔터티 데이터를 열면 Microsoft PowerApps Excel 추가 기능을 사용하여 쉽고 빠르게 데이터를 보고 편집할 수 있습니다. PowerApps Excel 추가 기능에는 Microsoft Excel 2016이 필요합니다.

![Excel 추가 기능](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps Excel 추가 기능")

## <a name="open-entity-data-in-excel"></a>Excel에서 엔터티 데이터 열기
1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭합니다. 모든 엔터티가 표시됩니다.
2. 원하는 엔터티의 오른쪽에 있는 줄임표(...)를 클릭합니다.
3. **Excel에서 열기**를 클릭한 다음 생성된 통합 문서를 엽니다. 이 통합 문서에는 엔터티에 대한 바인딩 정보, 사용자 환경에 대한 포인터 및 PowerApps Excel 추가 기능에 대한 포인터가 있습니다.  
4. Excel에서 **편집 사용**을 클릭하여 PowerApps Excel 추가 기능을 실행할 수 있도록 설정합니다. Excel 추가 기능을 Excel 창의 오른쪽 창에서 실행됩니다.
5. PowerApps Excel 추가 기능을 처음 실행하는 경우 **이 추가 기능 신뢰**를 클릭하여 Excel 추가 기능을 실행할 수 있도록 합니다.
6. 로그인하라는 메시지가 표시되면 **로그인**을 클릭한 다음 [powerapps.com](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 사용한 것과 동일한 자격 증명을 사용하여 로그인합니다. Excel 추가 기능은 이전 로그인 컨텍스트를 사용하고 가능하면 자동으로 로그인합니다. 따라서 Excel 추가 기능의 오른쪽 위에 있는 사용자 이름을 확인합니다.

Excel 추가 기능은 선택한 엔터티의 데이터를 자동으로 읽습니다. Excel 추가 기능에서 읽을 때까지 통합 문서에 데이터가 없습니다.

## <a name="view-and-refresh-data-in-excel"></a>Excel에서 데이터 보기 및 새로 고침
Excel 추가 기능에서 엔터티 데이터를 통합 문서로 읽은 후에는 Excel 추가 기능에서 **새로 고침**을 클릭하여 언제든지 데이터를 업데이트할 수 있습니다.

## <a name="edit-data-in-excel"></a>Excel에서 데이터 편집
필요에 따라 엔터티 데이터를 변경한 다음 Excel 추가 기능에서 **게시**를 클릭하여 다시 게시할 수 있습니다.

레코드를 편집하려면 워크시트에서 셀을 선택한 다음 셀 값을 변경합니다.

새 레코드를 추가하려면 다음 단계 중 하나를 수행합니다.

* 워크시트의 아무 곳이나 클릭한 다음 Excel 추가 기능에서 **새로 만들기**를 클릭합니다.
* 워크시트의 마지막 행을 클릭한 다음 커서가 해당 행의 마지막 열 밖으로 이동하고 새 행이 만들어질 때까지 Tab 키를 누릅니다.
* 워크시트 바로 아래에 있는 행을 클릭하고 셀에 데이터 입력을 시작합니다. 해당 셀에서 포커스를 이동하면 워크시트는 새 행을 포함하도록 확장됩니다.

레코드를 삭제하려면 다음 단계 중 하나를 수행합니다.

* 삭제할 워크시트 행 옆에 있는 행 번호를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.
* 삭제할 워크시트 행을 마우스 오른쪽 단추로 클릭한 다음 **삭제** > **표 행**을 클릭합니다.

## <a name="add-or-remove-columns"></a>열 추가 또는 제거
디자이너를 사용하여 워크시트에 자동으로 추가되는 열과 엔터티를 조정할 수 있습니다.

1. **옵션** 단추(기어 기호)를 클릭한 다음 **디자인 사용** 확인란을 선택하여 Excel 추가 기능의 데이터 원본 디자이너를 사용하도록 설정합니다.
2. Excel 추가 기능에서 **디자인**을 클릭합니다. 모든 데이터 원본이 나열됩니다.
3. 데이터 원본 옆에 있는 **편집** 단추(연필 기호)를 클릭합니다.
4. 필요한 경우 **선택한 필드** 필드에서 목록을 조정합니다.
   * **사용 가능한 필드** 필드의 필드를 **선택한 필드** 필드에 추가하려면 필드를 클릭한 다음 **추가**를 클릭합니다. 또는 필드를 두 번 클릭합니다.
   * **선택한 필드** 필드에서 필드를 제거하려면 필드를 클릭한 다음 **제거**를 클릭합니다. 또는 필드를 두 번 클릭합니다.
   * 필드 순서를 변경하려면 **선택한 필드** 필드에서 필드를 클릭한 다음 **위로** 또는 **아래로**를 클릭합니다.
5. **업데이트**를 클릭하여 데이터 원본에 변경 내용을 적용한 다음 **완료**를 클릭하여 디자이너를 종료합니다. 필드(열)를 추가한 경우 **새로 고침**을 클릭하여 업데이트된 데이터 집합을 끌어냅니다.

> [!NOTE]
> 게시할 때 오류가 발생할 수 있으므로 통합 문서에 ID 및 필수 필드를 항상 포함해야 합니다.

> [!NOTE]
> 조회 필드를 추가할 때는 ID와 표시 필드를 모두 추가해야 합니다.

## <a name="troubleshooting"></a>문제 해결
몇 가지 간단한 단계를 통해 해결할 수 있는 몇 가지 문제가 있습니다.

* 모든 엔터티가 새 레코드의 편집 및 생성을 지원하는 것은 아니므로 이러한 엔터티는 Excel에서 열리고 데이터를 볼 수 있지만 게시는 사용하지 않도록 설정됩니다.
* 조회 필드는 추가 기능을 사용하여 올바른 레코드가 참조되도록 편집해야 하며, 복사 및 이전을 통해 필드를 업데이트하거나 필드에 직접 입력하는 것은 지원되지 않습니다.


여기에서 설명하지 않은 문제가 발생하는 경우 [지원 페이지](https://powerapps.microsoft.com/support/)를 통해 당사에 문의해 주십시오.

## <a name="next-steps"></a>다음 단계
* [엔터티의 필드 관리](data-platform-manage-fields.md)
* [엔터티 간 관계 정의](data-platform-entity-lookup.md)
* [Common Data Service를 사용하여 앱 생성](../canvas-apps/data-platform-create-app.md)
* [Common Data Service를 사용하여 처음부터 앱 만들기](../canvas-apps/data-platform-create-app-scratch.md)

