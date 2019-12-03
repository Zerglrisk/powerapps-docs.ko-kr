---
title: Relate 및 인시던트와 관계 해제 함수 | Microsoft Docs
description: PowerApps의 Relate 및 인시던트와 관계 해제 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 94400c88740ea93b3966db8a62a461b5616eaeef
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678353"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>PowerApps의 Relate 함수 및 인시던트와 관계 해제 함수

일 대 다 또는 다 대 다 관계를 통해 두 엔터티의 레코드를 연결 하 고 인시던트와 관계 해제 합니다.

## <a name="description"></a>설명

**Relate** 함수는 Common Data Service에서 일 대 다 또는 다 대 다 관계를 통해 두 레코드를 연결 합니다. **인시던트와 관계 해제** 함수는 프로세스를 되돌리고 링크를 제거 합니다.

일 대 다 관계의 경우 많은 엔터티에는 하나의 엔터티 레코드를 가리키는 외래 키 필드가 있습니다. **Relate** 는이 필드를 하나의 엔터티에 대 한 특정 레코드를 가리키도록 설정 하 고 **인시던트와 관계 해제** 는이 필드를 *blank*로 설정 합니다. **Relate** 를 호출할 때 필드가 이미 설정 되어 있으면 새 링크를 선호 하는 기존 링크가 손실 됩니다. [**Patch**](function-patch.md) 함수 또는 **[편집 양식](../controls/control-form-detail.md)** 컨트롤을 사용 하 여이 필드를 설정할 수도 있습니다. **Relate** 함수는 사용할 필요가 없습니다.

다대다 관계의 경우 레코드를 연결 하는 시스템은 숨겨진 조인 테이블을 유지 합니다. 이 조인 테이블에 직접 액세스할 수 없습니다. 일대다 프로젝션을 통해 읽을 수 있으며 **Relate** 및 **인시던트와 관계 해제** 함수를 통해 설정할 수 있습니다. 관련 엔터티에 외래 키가 없습니다.

첫 번째 인수에 지정 하는 엔터티에 대 한 데이터가 변경 내용을 반영 하도록 새로 고쳐지고 두 번째 인수에 지정 하는 엔터티의 데이터는 변경 되지 않습니다. 작업 결과를 표시 하려면 **[Refresh](function-refresh.md)** 함수를 사용 하 여 해당 데이터를 수동으로 새로 고쳐야 합니다.

이러한 함수는 레코드를 만들거나 삭제 하지 않습니다. 이미 존재 하는 두 개의 레코드를 관련 또는 인시던트와 관계 해제 합니다.

이러한 함수는 [동작 수식](../working-with-formulas-in-depth.md)에만 사용할 수 있습니다.

> [!NOTE]
> 이러한 함수는 미리 보기 기능의 일부 이며, **관계형 데이터, 옵션 집합 및 cd의 기타 새 기능** 을 사용 하는 경우에만 해당 동작을 사용할 수 있습니다. 새 앱에 대해 기본적으로 사용 하도록 설정 된 앱 수준 설정입니다. 이 기능 스위치를 찾으려면 **파일** 메뉴를 열고 **앱 설정**을 선택한 다음 **고급 설정**을 선택 합니다. 의견은 microsoft에 매우 유용 합니다. [Power Apps 커뮤니티 포럼](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)에서 의견을 알려주세요.

## <a name="syntax"></a>구문

**Relate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* -필수 항목입니다. *Entity1*레코드의 경우 일 대 다 또는 다 대 다 관계를 통해 관련 된 *Entity2* 레코드의 테이블입니다.
* *Entity2Record* -필수 항목입니다. 관계에 추가할 *Entity2* 레코드입니다.

**인시던트와 관계 해제**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* -필수 항목입니다. *Entity1*레코드의 경우 일 대 다 또는 다 대 다 관계를 통해 관련 된 *Entity2* 레코드의 테이블입니다.
* *Entity2Record* -필수 항목입니다. 관계에서 제거할 *Entity2* 레코드입니다.

## <a name="examples"></a>예

[Power Apps 포털의 엔터티 뷰어에](../../common-data-service/create-edit-entities-portal.md)표시 된 것 처럼 다음과 같은 관계가 있는 **Products** 엔터티를 생각해 보세요.

| 관계 표시 이름 | 관련 엔터티 | 관계 유형 |
| --- | --- |
| 제품 예약 | 보유 | 일 대 다 |
| 제품 &harr; 연락처 | 연락처 | 다 대 다 |

**제품** 및 **예약은** 일 대 다 관계를 통해 관련 됩니다.  **예약** 엔터티의 첫 번째 레코드를 **Products** 엔터티의 첫 레코드와 연결 하려면 다음을 수행 합니다.

`Relate( First( Products ).Reservations, First( Reservations ) )`

이러한 레코드 간의 관계를 제거 하려면 다음을 수행 합니다.

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

또는 레코드를 만들거나 제거 했을 때 레코드 간의 관계만 수정 되었습니다.

**제품과** **연락처** 는 다 대 다 관계를 통해 관련 됩니다.  **연락처** 엔터티의 첫 번째 레코드를 **Products** 엔터티의 첫 레코드와 연결 하려면 다음을 수행 합니다.

`Relate( First( Products ).Contacts, First( Contacts ) )`

다 대 다 관계는 대칭 이지만 반대 방향으로이 작업을 수행할 수도 있습니다.

`Relate( First( Contacts ).Products, First( Products ) )`

이러한 레코드 간의 관계를 제거 하려면 다음을 수행 합니다.

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

디스크나

`Unrelate( First( Contacts ).Products, First( Products ) )`

다음 단계에서는 관련 레코드를 선택 하기 위해 **갤러리** 및 **콤보 상자** 컨트롤이 있는 앱을 사용 하 여 이러한 엔터티에 대해 이러한 작업을 정확히 수행 합니다.

이러한 예제는 사용자 환경에 설치 되는 샘플 데이터에 따라 달라 집니다. [샘플 데이터를 포함 하는 평가판 환경을 만들거나](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) [기존 환경에 샘플 데이터를 추가](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data)합니다.

### <a name="one-to-many"></a>일 대 다

#### <a name="relate-function"></a>**Relate** 함수

먼저 제품에 연결 된 예약을 확인 하 고 다시 할당 하는 간단한 앱을 만듭니다.

1. 빈 방법으로 [태블릿 앱](../data-platform-create-app-scratch.md)을 만듭니다.

1. **보기**에서 **데이터 원본**을 선택합니다.

1. **데이터** 창에서 **데이터 원본 추가** 를 선택 하 > **Common Data Service** > **제품** > **연결**을 선택 합니다.  

    Products 엔터티는 위에서 로드 한 샘플 데이터의 일부입니다.

     ![Products 엔터티를 데이터 원본으로 추가](media/function-relate-unrelate/products-connect.png)

1. **삽입** 탭에서 빈 세로 **[갤러리](../controls/control-gallery.md)** 컨트롤을 추가 합니다.

1. 방금 추가한 컨트롤의 이름이 **gallery1.selected**인지 확인 한 다음 이동 하 고 크기를 조정 하 여 화면의 왼쪽을 채웁니다.

1. **속성** 탭에서 **gallery1.selected**의 **Items** 속성을 **Products** 로 설정 하 고 해당 **레이아웃** 을 **이미지 및 제목**으로 설정 합니다.

    ![ProductsGallery 구성](media/function-relate-unrelate/products-gallery.png)

1. **Gallery1.selected**에서 **레이블** 컨트롤의 이름을 **Title1**로 지정 하 고 **Text** 속성을 **ThisItem.Name**로 설정 합니다.

    ![Gallery1.selected에서 레이블 구성](media/function-relate-unrelate/products-title.png)

1. **Gallery1.selected**에 다음 항목을 삽입 하지 않으려면 화면을 선택 합니다.  두 번째 빈 세로 **갤러리** 컨트롤을 추가 하 고 이름이 **프로그램도 있습니다**인지 확인 합니다.

    **프로그램도 있습니다** 은 사용자가 **gallery1.selected**에서 선택한 제품에 대 한 예약을 표시 합니다.

1. **프로그램도 있습니다** 를 이동 하 고 크기를 조정 하 여 화면의 오른쪽 위 사분면을 채웁니다.

1. 필드 다음 그림에 표시 된 것 처럼 **프로그램도 있습니다**위에 파란색 **레이블** 컨트롤을 추가 합니다.

1. 수식 입력줄에서 **프로그램도 있습니다** 의 **Items** 속성을 **gallery1.selected**로 설정 합니다.

    ![프로그램도 있습니다 항목 구성](media/function-relate-unrelate/reservations-gallery.png)

1. 속성 창에서 **프로그램도 있습니다**의 **레이아웃** 을 **제목**으로 설정 합니다.

    ![프로그램도 있습니다 레이아웃 구성](media/function-relate-unrelate/reservations-gallery-right.png)

1. **프로그램도 있습니다**에서 **[콤보 상자](../controls/control-combo-box.md)** 컨트롤을 추가 하 고 이름이 **ComboBox1**인지 확인 한 다음 **프로그램도 있습니다**의 다른 컨트롤이 차단 되지 않도록 이동 하 고 크기를 조정 합니다.

1. **속성** 탭에서 **ComboBox1**의 **Items** 속성을 **Products**로 설정 합니다.

    ![항목 속성을 Products로 설정](media/function-relate-unrelate/reservations-combo-right.png)

1. **속성** 탭에서 아래로 스크롤하여 **ComboBox1**의 **다중 선택 허용** 속성을 **Off**로 설정 합니다.

    ![다중 선택 허용을 Off로 설정](media/function-relate-unrelate/reservations-singleselect-right.png)

1. 수식 입력줄에서 **ComboBox1**의 **DefaultSelectedItems** 속성을 **ThisItem. ' 제품 예약 '** 으로 설정 합니다.

    ![ReserveCombo에 대 한 DefaultSelectedItems 설정](media/function-relate-unrelate/reservations-combo.png)

1. **프로그램도 있습니다**에서 **NextArrow2**의 **onselect** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    사용자가이 아이콘을 선택 하면 현재 예약이 **ComboBox1**에서 선택한 제품으로 변경 됩니다.

    ![NextArrow2 구성](media/function-relate-unrelate/reservations-relate.png)

1. F5 키를 눌러 미리 보기 모드에서 앱을 테스트 합니다.

이 앱을 사용 하면 사용자가 한 제품에서 다른 제품으로 예약을 이동할 수 있습니다. 한 제품에 대 한 예약의 경우 사용자는 **ComboBox1** 에서 다른 제품을 선택한 다음 **NextArrow2** 를 선택 하 여 해당 예약을 변경할 수 있습니다.

![일대다 앱에서 관련 함수 시연](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**인시던트와 관계 해제** 함수

이 시점에서 관계를 한 레코드에서 다른 레코드로 이동할 수 있지만 관계를 완전히 제거할 수는 없습니다. **인시던트와 관계 해제** 함수를 사용 하 여 모든 제품에서 예약 레코드의 연결을 끊을 수 있습니다.

1. **보기**에서 **데이터 원본**을 선택합니다.

1. **데이터** 창에서 **데이터 원본 추가** 를 선택 하 > **Common Data Service** > **예약** > **연결**을 선택 합니다.

1. **프로그램도 있습니다**에서 **NextArrow2** 에 대 한 **onselect** 수식을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![오른쪽 구성 아이콘](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. **프로그램도 있습니다** 을 선택한 다음 Ctrl + C를 눌러 클립보드로 복사 합니다.

1. Ctrl + V를 눌러 동일한 화면에 중복 된 **프로그램도 있습니다** 를 붙여넣고 화면의 오른쪽 아래 사분면으로 이동 합니다.

1. 필드 **프로그램도 있습니다**위에 레이블을 추가한 경우 해당 레이블에 대해 앞의 두 단계를 반복 합니다.

1. 중복 **프로그램도 있습니다** 의 이름이 **Gallery2_1**인지 확인 하 고 **Items** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    위임 경고가 표시 되지만이 예에서는 적은 양의 데이터를 사용 하는 것은 중요 하지 않습니다.

    ![Gallery2_1의 Items 속성을 설정 합니다.](media/function-relate-unrelate/reservations-lost.png)

이와 같이 변경 하면 사용자가 제품을 예약 하지 않은 경우 연락처에 대 한 **ComboBox1** 에서 선택을 지울 수 있습니다. 제품을 예약 하지 않은 연락처는 사용자가 제품에 각 연락처를 할당할 수 있는 **Gallery2_1** 표시 됩니다.

   ![일대다 앱에서 Relate 및 인시던트와 관계 해제 함수 시연](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>다 대 다

#### <a name="create-a-many-to-many-relationship"></a>다 대 다 관계 만들기

샘플 데이터는 다 대 다 관계를 포함 하지 않지만 Products 엔터티와 contact 엔터티 사이에 하나를 만듭니다. 사용자는 각 제품을 둘 이상의 연락처에 연결 하 고 각 연락처를 둘 이상의 제품에 연결할 수 있습니다.

1. [이 페이지](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)의 왼쪽 탐색 모음에서 **데이터** 를 선택한 다음 **엔터티**를 선택 합니다.

    ![엔터티 목록 열기](media/function-relate-unrelate/entity-list.png)

1. 모든 엔터티를 포함 하도록 엔터티 필터를 변경 합니다.

    기본적으로 샘플 엔터티는 표시 되지 않습니다.

    ![엔터티 필터 제거](media/function-relate-unrelate/entity-all.png)

1. 아래로 스크롤하여 **Product** 엔터티를 열고 **관계**를 선택 합니다.

    ![Product 엔터티에 대 한 관계 탭](media/function-relate-unrelate/entity-relationships.png)

1. **다 대 다** > **관계 추가** 를 선택 합니다.

    ![다 대 다 관계 추가](media/function-relate-unrelate/entity-manytomany.png)

1. 관계에 대 한 **Contact** 엔터티를 선택 합니다.

    ![연락처 엔터티 선택](media/function-relate-unrelate/entity-contact.png)

1. **완료** > **엔터티 저장**을 선택 합니다.

    ![Products 엔터티의 관계 목록](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>하나 이상의 제품과 관련 된 연락처와 인시던트와 관계 해제 연락처

이 항목의 앞부분에서 만든 것과 유사한 다른 앱을 만들지만 새 앱은 다 대 다 관계를 제공 합니다. 각 연락처는 단일 제품 대신 여러 제품을 예약할 수 있습니다.

1. 태블릿에 대 한 빈 앱에서이 항목의 [첫 번째 절차](#one-to-many) 에 설명 된 대로 **gallery1.selected** 를 만듭니다.

1. 또 다른 빈 세로 **갤러리** 컨트롤을 추가 하 고 이름이 **프로그램도 있습니다**인지 확인 한 다음 화면의 오른쪽 위 모서리로 이동 합니다.

    이 항목의 뒷부분에서는 **프로그램도 있습니다**아래에 **콤보 상자** 컨트롤을 추가 합니다.

1. 수식 입력줄에서 **프로그램도 있습니다**의 **Items** 속성을 **gallery1.selected**로 설정 합니다.

    ![연락처 구성](media/function-relate-unrelate/contacts-gallery.png)

1. **속성** 탭에서 **레이아웃** 을 **이미지 및 제목**으로 설정 합니다.

    ![연락처 구성](media/function-relate-unrelate/contacts-gallery-right.png)

1. **프로그램도 있습니다**에서 **Label** 컨트롤의 이름을 **Title2**로 지정 하 고 **Text** 속성을 **ThisItem. ' Full Name '** 으로 설정 합니다.

    이 절차를 완료 하 고 제품에 연락처를 할당할 때까지 해당 컨트롤에 텍스트가 표시 되지 않습니다.

    ![연락처 이름 표시](media/function-relate-unrelate/contacts-title.png)

1. **NextArrow2**를 삭제 하 고, **취소** 아이콘을 삽입 하 고, 이름이 **icon1**인지 확인 합니다.

1. **취소** 아이콘의 **onselect** 속성을 다음 수식으로 설정 합니다. 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![취소 아이콘 구성](media/function-relate-unrelate/contacts-unrelate.png)

1. **보기**에서 **데이터 원본**을 선택합니다.

1. **데이터** 창에서 **데이터 원본 추가** 를 선택 하 > **Common Data Service** > **연락처** > **연결**을 선택 합니다.

1. **프로그램도 있습니다**아래에서 **콤보 상자** 컨트롤을 추가 하 고 이름이 **ComboBox1**인지 확인 한 다음 **Items** 속성을 contact로 설정 합니다 **.**

    ![콤보 상자 항목 속성 구성](media/function-relate-unrelate/contacts-combo.png)

1. **속성** 탭에서 **다중 선택 허용** 을 **Off**로 설정 합니다.

    ![콤보 상자 레이아웃 속성 구성](media/function-relate-unrelate/contacts-combo-right.png)

1. **추가** 아이콘을 삽입 하 고, **onselect** 속성을 다음 수식으로 설정 합니다. 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![추가 아이콘 구성](media/function-relate-unrelate/contacts-relate.png)

사용자는이 앱을 사용 하 여 각 제품에 대 한 연락처 집합을 자유롭게 연결 하 고 인시던트와 관계 해제 수 있습니다.

- 제품에 연락처를 추가 하려면 화면 아래쪽의 콤보 상자에서 연락처를 선택 하 고 **추가** 아이콘을 선택 합니다.
- 제품에서 연락처를 제거 하려면 해당 연락처에 대 한 **취소** 아이콘을 선택 합니다.

    일 대 다 관계와 달리 다 대 다 관계를 사용 하면 사용자가 동일한 연락처를 여러 제품에 연결할 수 있습니다.

![다대다 앱에서 Relate 및 인시던트와 관계 해제 함수 시연](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>역방향: 여러 연락처와의 관계 및 인시던트와 관계 해제 제품

다대다 관계는 대칭입니다. 예를 확장 하 여 연락처에 제품을 추가한 다음 두 화면 간을 대칭 이동 하 여 어느 방향에서 든 관계를 표시 하는 방법을 표시할 수 있습니다.

1. **Screen1** 의 **Onvisible** 속성을 **Refresh (Products)** 로 설정 합니다.

    일 대 다 또는 다 대 다 관계를 업데이트 하면 **Relate** 또는 **인시던트와 관계 해제** 호출의 첫 번째 인수 엔터티 데이터만 새로 고쳐집니다. 이 앱의 화면 간에 대칭 이동 하려면 두 번째를 수동으로 새로 고쳐야 합니다.

    ![OnVisible 속성을 Refresh 함수로 설정](media/function-relate-unrelate/contacts-refresh.png)

1. 중복 된 **Screen1**입니다.

    중복 된 **Screen1_1** 이름이 지정 되 고 연락처 측의 관계를 확인 하는 기준이 형성 됩니다.

    ![화면 복제](media/function-relate-unrelate/contacts-duplicate.png)

1. 역방향 뷰를 만들려면 **Screen1_1**의 컨트롤에서 이러한 수식을 변경 합니다.

    - Screen1_1. OnVisible = `Refresh( Contacts )`
    - Gallery1_1 = `Contacts`
    - Title1_1 = `ThisItem.'Full Name'`
    - Label1_1 = `"Selected Contact Products"`
    - Gallery2_1 = `Gallery1_1.Selected.Products`
    - Title2_1 = `ThisItem.Name`
    - Icon1_1. OnSelect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1 = `Products`
    - Icon2_1. OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    결과는 이전 화면과 매우 유사 하지만 **연락처** 측의 관계에서 제공 됩니다.

    ![연락처에서 시작 하 여 다 대 다 관계 표시](media/function-relate-unrelate/reverse-screen.png)

1. **화살표** 스핀 아이콘을 삽입 하 고 **Onselect** 속성을 **Navigate (Screen1, None)** 로 설정 합니다.  **Navigate (Screen1_1, None)** 수식을 사용 하 여 **Screen1** 에서 동일한 작업을 수행 합니다.

    ![화면 간 탐색 추가](media/function-relate-unrelate/reverse-navigate.png)

이 새로운 화면에서는 사용자가 제품에 연락처를 추가 하 고 연락처 보기로 전환 하 여 연결 된 제품을 볼 수 있습니다. 관계는 대칭 이며 두 화면 간에 공유 됩니다.

![한쪽에서 다 대 다 관계를 보여 줍니다.](media/function-relate-unrelate/contacts-reverse.gif)
