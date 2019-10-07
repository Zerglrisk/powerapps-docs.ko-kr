---
title: Excel에서 캔버스 앱 생성 | Microsoft Docs
description: PowerApps를 사용하여 클라우드 스토리지 계정에 저장된 Excel 파일을 사용하는 캔버스 앱을 자동으로 생성
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/14/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 576e61e6e4ea1aad317fdec8f49f76bfcd1e0b6a
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71990255"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>PowerApps의 Excel에서 캔버스 앱 생성

이 항목에서는 Excel 테이블의 데이터를 사용하여 PowerApps에서 첫 번째 캔버스 앱을 자동으로 생성합니다. Excel 파일을 선택하고, 앱을 생성한 다음, 생성하는 앱을 실행합니다. 생성된 모든 앱은 레코드를 검색하고, 레코드 세부 정보를 표시하고, 레코드를 만들거나 업데이트하는 화면을 포함합니다. 앱을 생성하여 Excel 데이터를 사용하는 작업 중인 앱을 신속하게 가져온 다음, 필요에 맞게 앱을 사용자 지정할 수 있습니다. 

Excel 파일은 OneDrive, Google Drive 또는 Dropbox와 같은 클라우드 스토리지 계정에 있어야 합니다. 이 항목에서는 비즈니스용 OneDrive를 사용합니다.

PowerApps에 대한 라이선스가 없으면 [무료로 등록](../signup-for-powerapps.md)할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

이 항목을 정확히 수행하려면 Excel에서 [바닥재 견적](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) 파일을 다운로드하고, [클라우드 스토리지 계정](connections/cloud-storage-blob-connections.md)에 저장합니다.

> [!IMPORTANT]
> 사용자 고유의 Excel 파일을 사용할 수 있지만 데이터는 테이블로 형식이 지정돼야 합니다. 자세한 내용은 [테이블 형식 지정](how-to-excel-tips.md)을 참조합니다. 

## <a name="generate-the-app"></a>앱 생성

1. [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

1. **고유한 앱 만들기** 아래에서 **데이터로 시작**을 마우스로 가리킨 다음, **이 앱 만들기**를 선택합니다.

    ![앱 만들기 옵션](./media/get-started-create-from-data/start-from-data.png)

1. **데이터와 함께 시작** 아래의 클라우드 스토리지 계정에 대한 타일에서 **휴대폰 레이아웃**을 클릭하거나 탭합니다.

    ![앱 만들기 옵션](./media/get-started-create-from-data/odfb-tile.png)

1. 메시지가 표시되면 **연결**을 클릭하거나 탭하고, 해당 계정에 대한 자격 증명을 제공합니다.

1. **Excel 파일 선택** 아래에서 **FlooringEstimates.xlsx**를 찾아 클릭하거나 탭합니다. 

1. **표 선택** 아래에서 **FlooringEstimates**를 클릭하거나 탭한 후 **연결**을 클릭하거나 탭합니다.

    ![앱 만들기 옵션](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>앱 실행

1. F5 키를 눌러(또는 오른쪽 위 모서리의 재생 아이콘을 클릭하거나 탭하여) 미리 보기를 엽니다.

    ![미리 보기 열기](./media/get-started-create-from-data/open-preview.png)

1. 오른쪽 위 모서리 근처의 정렬 아이콘을 클릭하거나 탭하여 정렬 순서를 전환합니다.

    ![정렬 아이콘](./media/get-started-create-from-data/sort-icon.png)

1. 검색 창에서 하나 이상의 문자를 입력하거나 붙여넣어 목록을 필터링합니다.

    예를 들어 제품 이름, 범주 또는 개요에 해당 문자열이 표시 되는 레코드만 표시 하려면 **허니** 를 입력 하거나 붙여 넣습니다.

    ![필터 예제](./media/get-started-create-from-data/filter-example.png)

1. 레코드 추가:

    1. 더하기 아이콘을 선택 합니다.

        ![더하기 아이콘](./media/get-started-create-from-data/plus-icon.png)

    1. 원하는 모든 데이터를 추가한 다음 확인 표시 아이콘을 선택 하 여 변경 내용을 저장 합니다.

        ![저장 아이콘](./media/get-started-create-from-data/save-icon.png)

1. 레코드 편집:

    1. 편집 하려는 레코드의 화살표를 선택 합니다.

        ![다음 화살표](./media/get-started-create-from-data/next-arrow.png)

    1. 연필 아이콘을 선택 합니다.

        ![연필 아이콘](./media/get-started-create-from-data/pencil-icon.png)

    1. 하나 이상의 필드를 업데이트 한 다음 확인 표시 아이콘을 선택 하 여 변경 내용을 저장 합니다.

        ![저장 아이콘](./media/get-started-create-from-data/save-icon.png)

        또는 취소 아이콘을 선택 하 여 변경 내용을 취소 합니다.

1. 레코드 삭제:

    1. 삭제할 레코드에 대 한 다음 화살표를 선택 합니다.

        ![다음 화살표](./media/get-started-create-from-data/next-arrow.png)

    1. 휴지통 아이콘을 선택 합니다.

        ![휴지통 아이콘](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>다음 단계

사용자의 요구 사항에 맞게 기본 찾아보기 화면을 사용자 지정합니다. 예를 들어 범주 또는 개요가 아닌 제품 이름 으로만 목록을 정렬 하 고 필터링 할 수 있습니다.

> [!div class="nextstepaction"]
> [기본 찾아보기 화면을 사용자 지정합니다](customize-layout-sharepoint.md).
