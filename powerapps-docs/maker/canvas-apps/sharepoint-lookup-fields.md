---
title: 캔버스 앱의 조회 필드를 통해 SharePoint 목록 간의 관계 만들기 | Microsoft Docs
description: Power Apps에서 캔버스 앱의 조회 필드를 사용 하 여 SharePoint 목록 간의 관계를 만듭니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/20/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f1464c7ca75f4fa811a53d18866ce89037b5e47a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733025"
---
# <a name="how-to-link-sharepoint-lists-using-a-lookup-field-in-power-apps"></a>Power Apps에서 조회 필드를 사용 하 여 SharePoint 목록을 연결 하는 방법

이 자습서에서는 캔버스 앱의 두 개의 SharePoint 목록을 조회 필드와 연결하는 방법을 보여줍니다.

## <a name="overview"></a>개요

SharePoint에서는 두 가지 형식의 조회 필드를 제공합니다.

* **조회**: 다른 목록에 연결합니다. 예를 들어 *주문* 목록에는 *고객* 목록의 고객에 연결되는 조회 필드가 있을 수 있습니다.
* **선택**: 필드를 클릭하거나 누르면 선택한 항목의 작은 메뉴가 표시됩니다.

이 자습서에서는 이러한 종류의 조회 필드를 사용하는 앱을 빌드합니다.

### <a name="why-use-a-lookup-field"></a>조회 필드를 사용하는 이유

엔터프라이즈의 데이터는 크고 복잡합니다. 한 SharePoint 목록의 데이터는 다른 목록의 데이터와 자주 관련됩니다. 조회 필드는 이러한 비즈니스 데이터를 함께 표시하는 기본 방법입니다.

예를 들어 주문한 고객을 표시하기 위해 **고객** 목록에 연결된 조회 필드가 있는 **주문** 목록이 있을 수 있습니다. **Orders** 목록의 조회 필드를 통해 **고객** 목록에서 다른 데이터도 가져올 수 있습니다. 또한 조회 필드를 사용하여 **주문** 목록을 **제품** 목록에 연결하고, 제품 사진, 사양, 제조업체 세부 정보 등 주문한 제품에 대해 필요한 정보를 가져올 수 있습니다.

### <a name="what-are-choice-fields-used-for"></a>선택 필드는 어떤 용도로 사용하나요?
**선택** 필드는 매우 짧은 목록에 사용됩니다. 이 기능을 통해 별도 목록을 실제로 만들지 않고 **선택** 필드를 클릭하거나 누를 때 표시되는 작은 메뉴에 목록 값을 포함하여 해당 값 중 하나를 선택할 수 있습니다.

이러한 예로 고객 상태 코드, 제품 사용 가능성, 상태 코드와 같은 기본적으로 비교적 짧은 모든 고정 목록 데이터가 포함됩니다. 이 데이터는 실제로 별도 목록으로 구현될 수 있습니다. **조회** 필드를 사용하여 연결할 수 있지만 일반적으로 **선택** 필드로 구현하는 것이 더 쉽고 빠릅니다.

## <a name="create-the-lists-in-sharepoint"></a>SharePoint에서 목록 만들기
이 자습서에서는 **자산** 및 **RepairShop**라는 두 개의 SharePoint 사용자 지정 목록을 모두 연결합니다. **자산** 목록은 팀에서 하드웨어 장비를 추적하는 데 사용됩니다. 종종 하드웨어가 중단되므로 **RepairShop** 목록을 사용하여 문제를 해결할 수 있는 지역 매장을 추적합니다.

### <a name="the-lookup-fields-used-in-this-example"></a>이 예에서 사용되는 조회 필드
**RepairShop** 목록은 *ContactEmail* 필드를 사용하여 상점을 식별합니다. **자산** 목록의 각 행이 어떤 항목을 가리키도록 이 목록을 먼저 정의합니다.

**자산** 목록에는 두 개의 조회 필드가 있습니다.

* 그 중 하나는 **조회** 형식의 *RepairShop*이며 전자 메일 주소를 사용하여 **RepairShop** 목록에 있는 항목을 가리킵니다.
* 다른 하나는 **선택** 형식의 *AssetType*이며 이 자산에 가능한 하드웨어의 종류를 나열합니다.

추적하는 데 필요한 정보에 따라 추가 필드를 정의할 가능성이 가장 높습니다.

### <a name="define-the-repairshop-list-and-add-data"></a>RepairShop 목록 정의 및 데이터 추가
이 작업을 먼저 수행하면 데이터를 **자산** 목록에 추가할 때 **RepairShop** 항목을 *Assets.RepairShop* 조회 필드 중에서 선택할 수 있습니다.

1. SharePoint 사이트에서 새 **RepairShop** 목록을 만듭니다.

    ![](./media/sharepoint-lookup-fields/new-list.png)

2. **한 줄 텍스트** 형식의 *ContactEmail* 필드를 추가합니다.

    ![](./media/sharepoint-lookup-fields/add-email-field.png)

3. 필요한 다른 필드를 추가합니다.

4. **+ 새로 만들기**를 클릭하거나 눌러서 다른 *ContactEmail* 값을 포함하는 3개 이상의 행의 목록에 샘플 데이터를 입력합니다. 자산을 복구해야 하는 경우 다음 중 하나를 선택합니다.

    ![](./media/sharepoint-lookup-fields/add-repair-shops.png)

### <a name="define-the-assets-list"></a>자산 목록을 정의합니다.
1. SharePoint 사이트에서 새 **자산** 목록을 만듭니다.

2. 더하기 기호를 클릭하거나 누르고 **자세히**를 선택합니다.

    ![](./media/sharepoint-lookup-fields/choose-more-type.png)

3. **선택** 형식의 *AssetType* 필드를 추가하고, **별도 줄에 각 선택 사항 입력** 텍스트 상자의 선택 메뉴에 표시하려는 값을 입력합니다. 그런 다음 **확인**을 클릭하거나 누릅니다.

    ![](./media/sharepoint-lookup-fields/define-choice-column.png)

4. 2단계처럼 다른 필드를 추가하기 시작합니다. 더하기 기호를 클릭하거나 누르고 **자세히**를 선택합니다.

5. **조회** 형식의 *RepairShop* 필드를 추가하고, **정보를 가져오는 위치** 텍스트 상자에서 **RepairShop**을 선택하고, **이 열에서** 텍스트 상자에서 *ContactEmail*을 선택합니다. 그런 다음 **확인**을 클릭하거나 누릅니다.

    ![](./media/sharepoint-lookup-fields/setup-lookup-column.png)

6. 원하는 추가 필드를 추가합니다.

## <a name="create-an-app-from-the-assets-list"></a>자산 목록에서 앱 만들기
이 앱을 사용하여 **자산** 목록에 데이터를 추가합니다.

1. [Power Apps Studio에 로그인](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다. Power Apps를 처음 접하는 경우 조직의 전자 메일 주소를 사용 하 여 [무료로 등록 하세요](https://powerapps.microsoft.com) .

2. **파일** 메뉴(왼쪽 모서리를 따라)에서 **새로 만들기**를 클릭하거나 누른 다음 **SharePoint**를 클릭하거나 누릅니다.

    ![](./media/sharepoint-lookup-fields/create-app.png)

1. **최근에 사용한 사이트** 목록에서 SharePoint 사이트를 선택하거나 텍스트 상자에 직접 해당 사이트의 URL을 입력합니다. **이동**을 클릭하거나 누릅니다.

    ![](./media/sharepoint-lookup-fields/choose-sharepoint-site.png)

1. SharePoint 사이트에서 기본 목록을 선택합니다(이 예제에서는 **자산**). 오른쪽 아래 모퉁이에서 **연결** 단추를 클릭하거나 누릅니다.

    ![](./media/sharepoint-lookup-fields/choose-main-list.png)


## <a name="add-data-to-the-assets-list"></a>자산 목록에 데이터 추가
이제 앱을 실행하고 조회 필드에 대한 세부 정보 보기 화면 모양을 확인할 수 있습니다.

1. F5 키를 누르거나 미리 보기(![](./media/sharepoint-lookup-fields/preview.png))를 선택합니다.

2. 오른쪽 위 모서리에서 **+** 기호를 클릭하거나 눌러서 항목을 추가합니다.

3. 이 자산의 **제목**을 입력합니다.

4. **AssetType** 드롭다운 화살표를 클릭하거나 누릅니다. 표시되는 값은 이 필드를 만들 때 입력한 값입니다. 항목 중 하나를 선택합니다.

    ![](./media/sharepoint-lookup-fields/fill-asset-type-3.png)

5. **RepairShop** 드롭다운 화살표를 클릭하거나 누릅니다. 항목 중 하나를 선택합니다.

    ![](./media/sharepoint-lookup-fields/fill-repair-shop-3.png)

6. 오른쪽 위 모서리에서 확인 표시를 클릭하거나 눌러서 새 항목을 저장합니다.

7. (선택 사항) 목록에 항목을 원하는 만큼 추가하려면 이 절차를 반복합니다.

8. 기본 작업 영역으로 돌아가려면 Esc를 누릅니다.

## <a name="for-more-information"></a>자세한 내용은 다음을 참조하세요.
* [조회 및 새 샘플 앱에 대한 지원 소개](https://powerapps.microsoft.com/blog/support-for-lookups/)
* [성능, 새로 고침 단추, ForAll 및 여러 필드 조회](https://powerapps.microsoft.com/blog/performance-refresh-forall-multiple-field-lookups-531/)
* [Common Data Service 데이터베이스를 사용하여 앱 생성](data-platform-create-app.md)
* [Common Data Service 데이터베이스를 사용하여 앱을 처음부터 만들기](data-platform-create-app-scratch.md)
