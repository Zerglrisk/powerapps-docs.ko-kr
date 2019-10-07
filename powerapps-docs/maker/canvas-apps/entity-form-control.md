---
title: 엔터티 양식 컨트롤 사용 | Microsoft Docs
description: 엔터티 양식 컨트롤을 사용하여 Common Data Service 엔터티에 대한 서식 있는 양식을 추가하여 앱을 보다 빠르게 만들 수 있습니다.
author: aneesmsft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/11/2017
ms.author: aneesa
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1bffa509f382c2f706c2163d89c5788f8607ec7
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993055"
---
# <a name="use-the-entity-form-control"></a>엔터티 양식 컨트롤 사용
**엔터티 양식** 컨트롤을 사용하여 Common Data Service 엔터티에 대한 서식 있는 양식을 추가하여 앱을 보다 빠르게 만들 수 있습니다.

**엔터티 양식** 컨트롤에 대 한 소개는이 블로그 게시물을 참조 하세요. [Common Data Service에 대 한 새 엔터티 양식 컨트롤 (실험적 기능)](https://powerapps.microsoft.com/blog/new-entity-form-control-experimental-feature-for-common-data-service/)입니다.

> [!IMPORTANT]
> 이 블로그 게시물에 요약된 대로 **엔터티 양식** 컨트롤의 실험적인 기능을 알아두고 적어도 지금은 프로덕션 앱에서 **엔터티 양식** 컨트롤 사용에 대해 주의하세요.

## <a name="key-properties"></a>주요 속성
**엔터티 양식** 컨트롤의 주요 속성을 소개합니다.

**DataSource** – 표시할 레코드가 포함된 데이터 원본을 지정합니다.   
> [!NOTE]
> 현재는 Common Data Service의 엔터티만 **엔터티 양식** 컨트롤에 대한 데이터 원본으로 지원됩니다.  

**Pattern** – **엔터티 양식** 컨트롤에서 표시하려는 양식의 스타일을 지정합니다. **FormPattern** 열거를 사용하여 이 속성을 설정합니다.

* **FormPattern.List** – 레코드의 테이블 형식 목록을 표시합니다.
* **FormPattern.CardList** – 레코드의 카드 목록을 표시합니다.
* **FormPattern.Details** – 단일 레코드의 세부 정보를 보거나 편집할 수 있는 양식을 표시합니다.
* **FormPattern.None** – 명시적으로 지정된 스타일이 없습니다. 태블릿 앱은 **List**, 휴대폰 앱은 **CardList**로 기본 설정됩니다.

**Item** – **엔터티 양식** 컨트롤이 표시해야 하는 데이터 원본의 레코드를 지정합니다. 이 속성은 **Pattern**이 **FormPattern.Details**로 설정되어 있는 경우에만 사용됩니다.

**Selected** – 현재 선택된 레코드를 가져옵니다.  
예 들어 **엔터티 양식** 컨트롤에서 판매 주문 레코드 목록을 표시 하는 경우 **선택한** 속성은 현재 선택 된 레코드를 제공 합니다. 레코드 내의 필드에 액세스할 수도 있습니다. (예를 들어 선택한 레코드의 **Account** 필드의 값을 **Selected.Account**로 지정하세요.)

**SelectableFields** – 링크로 나타나야 하는 필드를 지정합니다. 다음 구문을 사용하여 이 속성의 값을 지정합니다.  
**{Field1Name : true, Field2Name : true}**  
예 들어 **SalesOrderId** 및 **Account** 필드가 폼에서 링크로 표시 되도록 하려면 해당 양식의 **SelectableFields** 속성을이 값으로 설정 합니다.  
**{SalesOrderId : true, Account : true}**

**SelectedField** – 클릭 또는 탭되는 필드를 결정합니다. **SelectableFields**로 지정된 필드에만 적용됩니다.  
예 들어 **SelectableFields** 속성을 **{SalesOrderId: true, account: true}** 로 설정 하 고 사용자가 **계정** 필드인 **Selectedfield** 를 클릭 하거나 탭 합니다. account는 true로 설정 됩니다.

**OnFieldSelect** – 사용자가 필드를 클릭하거나 탭할 때 앱이 응답하는 방식입니다. **SelectableFields**로 지정된 필드에만 적용됩니다.

**Mode** – 양식의 모드를 결정합니다. 모드를 변경하려면 **ViewForm**, **EditForm** 또는 **NewForm** 함수를 사용하세요. 이러한 함수는 **Pattern** 속성이 **FormPattern.Details**로 설정된 경우에만 작동합니다. **Mode** 속성의 값을 **FormMode** 열거의 값으로 설정합니다.

* **FormMode.View** – 사용자가 레코드를 볼 수 있지만 편집 또는 추가할 수 없습니다.
* **FormMode.Edit** – 사용자가 레코드를 편집할 수 있습니다.
* **FormMode.New** – 사용자가 레코드를 추가할 수 있습니다.

**OnSuccess** – 데이터 작업에 성공했을 때 앱이 응답하는 방식입니다.

**OnFailure** – 데이터 작업에 실패했을 때 앱이 응답하는 방식입니다.

**Unsaved** – 사용자가 편집하는 레코드에 저장하지 않은 변경 사항이 있는지 여부를 결정합니다.

## <a name="related-functions"></a>관련된 함수
사용자는 이러한 공유 함수를 **엔터티 양식** 컨트롤 또는 [편집 양식 컨트롤](functions/function-form.md)에 사용할 수 있습니다. 이러한 함수는 **Pattern** 속성이 **FormPattern.Details**로 설정된 경우에만 **엔터티 양식** 컨트롤에 작동합니다.

**ViewForm** – **엔터티 양식** 컨트롤의 **Mode** 속성을 **FormMode.View**로 설정합니다.

**EditForm** – **엔터티 양식** 컨트롤의 **Mode** 속성을 **FormMode.Edit**으로 설정합니다.

**ViewForm** – **엔터티 양식** 컨트롤의 **Mode** 속성을 **FormMode.New**로 설정합니다.

**SubmitForm** - 사용자가 **엔터티 양식** 컨트롤의 레코드를 편집할 때 변경 사항을 저장합니다.

**ResetForm** - 사용자가 **엔터티 양식** 컨트롤의 레코드를 편집할 때 저장되지 않은 변경 사항을 포기합니다.

이제 다양한 속성과 함수의 개요가 있으므로 실제 작동을 확인하세요.

> [!NOTE]
> Common Data Service 데이터베이스에 대한 액세스 권한이 없는 경우 다음 단계를 수행하기 전에 하나를 만듭니다.

## <a name="display-a-list-of-records"></a>레코드 목록 표시
다음 다섯 개의 절차는 **엔터티 양식** 컨트롤 사용 방법에 대한 단일하고 포괄적인 예를 제공합니다. 이 절차에서는 판매 주문 목록을 표시하는 양식을 추가합니다.  

1. 빈 태블릿 앱을 만듭니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-01.png)
2. 첫 번째 화면의 이름을 **SalesOrderListScreen**으로 바꿉니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-02.png)
3. **삽입** 탭에서 **양식**을 클릭하거나 탭한 다음, **엔터티 양식(실험적)** 을 클릭하거나 탭합니다.  
   
    **엔터티 양식** 컨트롤이 화면에 추가됩니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-03.png)
4. **엔터티 양식** 컨트롤의 이름을 **SalesOrderListForm**으로 바꾸고 전체 화면을 포함하도록 크기를 조정합니다.
5. 오른쪽 창에서 **데이터 원본을 선택하지 않음** 텍스트 옆의 데이터베이스 아이콘을 클릭하거나 탭하고 **데이터 원본 추가**를 클릭하거나 탭합니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-04.png)
6. 연결 목록에서 데이터베이스에 대한 연결을 클릭하거나 탭합니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-05.png)
7. 엔터티 목록에서 **Sales order**를 클릭하거나 탭하고 **연결**을 클릭하거나 탭합니다.  
   
    **판매 주문** 엔터티에 대한 데이터 원본이 만들어지고 **SalesOrderListForm**의 **DataSource** 속성이 해당 데이터 원본으로 설정됩니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-06.png)  
   
    **엔터티 양식** 컨트롤은 판매 주문 목록을 보여줍니다. **엔터티 양식** 컨트롤을 사용하여 수동으로 빌드하지 않고도 목록 양식을 빠르게 표시했습니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-07.png)  
   
    **엔터티 양식** 컨트롤에 대한 **Pattern** 속성을 설정하지 않았으므로, **List** 패턴으로 기본 설정됩니다. 또한, **판매 주문** 엔터티의 **DefaultList** 필드 그룹은 목록 양식을 표시하는 데 사용됩니다. 이 양식은 동적이며 필드 그룹의 변경 사항을 자동으로 반영합니다.


## <a name="display-the-details-of-a-record"></a>레코드의 세부 정보 표시
앞부분에서 만든 목록에서 선택된 판매 주문의 세부 정보를 표시하도록 다른 **엔터티 양식** 컨트롤을 추가해 보겠습니다.  

1. **SalesOrderListForm**의 크기를 조정하여 화면의 절반을 포함하고 두 번째 **엔터티 양식** 컨트롤을 추가하여 화면의 다른 절반을 포함합니다.  
   <br>![](media/entity-form-control/entityform-tutorial-01-09.png)
2. 두 번째 **엔터티 양식** 컨트롤의 이름을 **SalesOrderDetailsForm**으로 바꾸고 앞부분에서 만든 **판매 주문** 데이터 원본에 연결합니다.  
   <br>![](media/entity-form-control/entityform-tutorial-01-10.png)
3. **SalesOrderDetailsForm**의 **Pattern** 속성을 **FormPattern.Details**로 설정합니다.  
   
    **SalesOrderDetailsForm**은 **판매 주문** 엔터티의 **DefaultDetails** 필드 그룹을 사용하여 양식을 표시합니다. **SalesOrderListForm**과 마찬가지로, 양식을 수동으로 빌드하지 않고도 레코드 세부 정보를 빠르게 표시할 수 있습니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-11.png)
4. **SalesOrderDetailsForm**의 **Item** 속성을 **SalesOrderListForm.Selected**로 설정합니다.
   
    **SalesOrderDetailsForm**은 사용자가 **SalesOrderListForm**에서 클릭하거나 탭하는 레코드의 세부 정보를 표시합니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-12.png)
5. F5 키를 눌러 앱을 미리 본 다음, 왼쪽 목록에서 판매 주문을 클릭하거나 탭합니다.  
   
    선택한 주문의 세부 정보가 오른쪽에 나타납니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-13.png)  

## <a name="configure-a-field-to-navigate-to-another-screen"></a>다른 화면으로 이동하도록 필드를 구성합니다.
다음으로, 앱에 추가 화면을 추가한 후 사용자가 필드를 클릭하거나 탭하면 앱에서 다른 화면으로 이동하도록 **엔터티 양식** 컨트롤의 필드를 구성해 보겠습니다.  

1. 두 번째 화면을 앱에 추가하고 화면의 이름을 **SalesOrderDetailsScreen**으로 바꿉니다.
2. **SalesOrderDetailsForm**을 자른 후 **SalesOrderDetailsScreen**에 붙여넣고 양식의 크기를 조정하여 화면의 대부분을 포함하여 상단의 아이콘에 충분한 공간을 둡니다.
3. **SalesOrderDetailsScreen**의 왼쪽 위 모서리 근처에 뒤로 화살표 아이콘을 추가합니다.
4. 뒤로 화살표 아이콘의 **OnSelect** 속성을 [**Back**](functions/function-navigate.md) 함수로 설정합니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-14.png)
5. **SalesOrderListScreen**에서 **SalesOrderListForm**의 크기를 조정하여 전체 화면을 포함합니다.
6. **SalesOrderListForm**을 클릭하거나 탭하여 선택합니다.
7. 오른쪽 창의 **Fields**에서 **SalesOrderId**를 설정하여 **SalesOrderDetailsScreen**으로 이동합니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-15.png)
   
    **엔터티 양식** 컨트롤은 **SalesOrderId** 필드의 값(목록의 첫 번째 열)을 링크로 표시합니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-16.png)  
8. F5 키를 눌러 앱을 미리 본 다음, 판매 주문 목록에서 링크를 클릭하거나 탭합니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-17.png)  
   
    두 번째 화면이 열리고 지정한 판매 주문의 세부 정보가 표시됩니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-18.png)  
   
    다른 판매 주문의 세부 정보를 표시하려면 뒤로 화살표를 클릭하거나 탭하여 목록으로 다시 이동한 다음, 세부 정보를 표시하려는 주문의 링크를 클릭하거나 탭합니다.

## <a name="navigate-with-a-context-variable"></a>컨텍스트 변수를 사용하여 탐색
**SalesOrderDetailsForm**의 **Item** 속성이 **SalesOrderListForm.Selected**로 설정되어 **SalesOrderDetailsForm**은 사용자가 **SalesOrderListForm**에서 선택한 레코드에 대한 세부 정보를 보여줍니다. 또한 양식 사용자 지정 창을 사용하여 탐색할 필드를 구성할 때 자동으로 만들어지는 **NavigationContext** 컨텍스트 변수를 사용하여 선택한 레코드의 컨텍스트를 가져올 수도 있습니다.  

1. **SalesOrderDetailsForm**의 **Item** 속성을 **NavigationContext**로 설정합니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-19.png)
2. F5 키를 눌러 앱을 미리 본 다음, 판매 주문 목록에서 링크를 클릭하거나 탭합니다.
   
    이 앱은 **SalesOrderDetailsScreen**을 열고 사용자가 지정한 판매 주문의 세부 정보를 표시합니다.

양식 사용자 지정 창이 탐색과 컨텍스트를 설정하는 방법에 대해 자세히 살펴 보겠습니다.  

**SalesOrderListForm**의 **SelectableFields** 속성은 **SalesOrderId**를 선택 가능한 필드로 지정합니다.

![](media/entity-form-control/entityform-tutorial-01-20.png)  

**SalesOrderId** 필드가 **SalesOrderDetailsScreen**으로 이동하도록 양식 사용자 지정 창을 사용했을 때 자동으로 설정되었습니다. 따라서, **SalesOrderId** 필드의 값이 링크로 나타납니다.

**SalesOrderListForm** 의 **onfieldselect** 속성은 [**If**](functions/function-if.md) 함수로 설정 되며,이 함수는 사용자가 **판매 주문 ID** 필드를 클릭 하거나 탭 하는지 여부를 결정 합니다. **SalesOrderListForm SalesOrderId = true**입니다.  

이 함수가 true로 평가되면 **SalesOrderDetailsScreen**은 앞부분에서 사용한 **NavigationContext** 이름의 컨텍스트 변수와 함께 열립니다.  

이 모든 것이 **SalesOrderId** 필드가 **SalesOrderDetailsScreen**으로 이동하도록 양식 사용자 지정 창을 사용했을 때 자동으로 설정되었습니다.  

따라서 사용자가 판매 주문 ID 필드를 클릭하거나 탭하면 [**If**](functions/function-if.md) 함수가 true로 평가되며 [**Navigate**](functions/function-navigate.md) 함수는 해당 컨텍스트로 호출되어 세부 정보 화면이 열립니다.  

![](media/entity-form-control/entityform-tutorial-01-21.png)  

> [!NOTE]
> 양식 사용자 지정 창을 사용하면 **NavigationContext**가 지능적으로 결정됩니다. 사용자가 **SalesOrderId**를 클릭하거나 탭하면 이전 공식에서 보여준 것처럼 **NavigationContext**가 **SalesOrderListForm.Selected**로 설정됩니다. 대신 탐색에 **Account** 필드를 지정했다면 **NavigationContext**는 올바른 컨텍스트가 전달되도록 **SalesOrderListForm.Selected.Account**로 설정되었을 것입니다. 그러나 컨텍스트를 소비하려면 Common Data Service에서 **Account** 엔터티에 연결된 **엔터티 양식** 컨트롤이 필요합니다.

## <a name="edit-and-save-a-record"></a>레코드 편집 및 저장
마지막으로 **엔터티 양식** 컨트롤에서 레코드를 편집하고 저장하는 방법을 살펴 보겠습니다.  

1. **SalesOrderDetailsScreen**에서 편집 아이콘을 추가한 다음 **OnSelect** 속성을 다음 수식으로 설정합니다.  
   **EditForm(SalesOrderDetailsForm)**
   
    ![](media/entity-form-control/entityform-tutorial-01-22.png)
2. 편집 아이콘 옆에 확인 표시 아이콘을 추가한 다음, 확인 표시 아이콘의 **OnSelect** 속성을 다음 수식으로 설정합니다.  
   **SubmitForm(SalesOrderDetailsForm)**  
   
    ![](media/entity-form-control/entityform-tutorial-01-23.png)
3. F5 키를 눌러 앱을 미리 보고 **판매 주문 ID**를 클릭하거나 탭하여 판매 주문의 세부 정보를 본 다음, 편집 아이콘을 클릭하거나 탭합니다.  
   
    **엔터티 양식** 컨트롤의 **Mode**는 사용자가 레코드를 편집할 수 있는 **FormMode.Edit**로 설정됩니다.
4. **주문 상태**를 **송장**으로 업데이트합니다.  
   
    ![](media/entity-form-control/entityform-tutorial-01-24.png)
5. **영업 사원**을 **WRK014**로 업데이트합니다.
   
    **영업 사원**을 선택할 수 있도록 **엔터티 양식** 컨트롤은 세부 정보가 많은 조회를 자동으로 렌더링합니다. 조회를 생성하고 표시하기 위해 컨트롤은 Common Data Service에서 **작업자** 엔터티의 **DefaultLookup** 필드 그룹을 사용합니다. **영업 사원** 필드의 유형은 **작업자**이므로 **작업자** 엔터티가 사용됩니다.
   
    ![](media/entity-form-control/entityform-tutorial-01-25.png)
6. 확인 표시를 클릭하거나 탭하여 변경 사항을 저장합니다.

이 단계는 앱에서 **엔터티 양식** 컨트롤을 사용하는 방법에 대한 이 문서의 결론을 내립니다. 이 문서에서 다룬 정보가 **엔터티 양식** 컨트롤 사용을 시작하는 데 유용하길 바랍니다. **엔터티 양식** 컨트롤에 대한 의견을 알려 주시면 사용자가 앱에 다양한 양식을 빠르게 추가할 수 있도록 반영하겠습니다.

