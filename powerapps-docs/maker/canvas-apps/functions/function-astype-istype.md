---
title: AsType 및 IsType 함수에서 캔버스 앱 | Microsoft Docs
description: 캔버스 앱 구문과 AsType 및 IsType 함수에 대 한 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dafffcc148329be81f7544bdc2f0730f307ae4eb
ms.sourcegitcommit: f6c9e525130a03b8c76f0a4b4e90419604c5823c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65526057"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>캔버스 앱의 AsType 및 IsType 함수

특정 엔터티 형식에 대 한 레코드 참조를 확인 하 고 참조를 특정 형식으로 처리 합니다.

## <a name="description"></a>설명

읽기 [레코드 참조 및 다형 조회 이해](../working-with-references.md) 광범위 한 소개 및 자세한 정보에 대 한 합니다.

일반적으로 조회 필드를 특정 엔터티의 레코드를 가리킵니다. 엔터티 형식을 잘 확립 된 이기 때문에 간단한 점 표기법을 사용 하 여 조회 필드를 액세스할 수 있습니다. 예를 들어 **첫 번째 (계정).' 기본 연락처 '.' 전체 이름 '** 에서 설명 합니다 **계정** 엔터티를를 **기본 연락처** 레코드를 **연락처** 엔터티와 추출을 **전체 이름**  필드입니다.

Common Data Service에는 또한 다음이 예제와 같이 엔터티 집합에서 레코드를 참조할 수 있는 다형 조회 필드를 지원 합니다.

| 조회 필드 | 참조할 수 있습니다. |
|--------------|--------------|
| **소유자** | **사용자가** 또는 **팀** |
| **고객** | **계정** 또는 **연락처** |
| **관련 항목** | **계정**하십시오 **연락처**, **기술 항목**등. |

캔버스 앱 수식에서 레코드 참조 다형 조회를 사용 하 여 작업을 사용할 수 있습니다. 다른 엔터티 레코드 참조를 참조할 수, 있으므로 모 르 수식을 작성할 때 어떤 필드가 제공 됩니다. *합니다. 필드* 표기법을 사용할 수 없습니다. 수식 실행 될 때 앱에서 발생 하는 레코드에 맞게 조정 해야 합니다.

합니다 **IsType** 함수는 레코드 참조가 특정 엔터티 형식에 있는지 여부를 테스트 합니다. 부울 값을 반환 하는 함수 *true* 하거나 *false*합니다.

합니다 **AsType** 취급 라고도 특정 엔터티 형식으로 레코드 참조 *캐스팅*합니다. 엔터티의 레코드 것 처럼 결과 사용 하 고을 수를 사용 하 여 *입니다. 필드* 표기법의 모든 레코드의 필드에 액세스 합니다. 특정 유형의 참조가 없는 경우 오류가 발생 했습니다.

레코드의 엔터티 형식을 먼저 테스트 하 여 필드를 사용할 수 있도록 해당 형식의 레코드로 처리 이러한 함수를 함께 사용 합니다.

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

레코드 참조의 필드에 액세스 하는 경우에 이러한 함수가 필요 합니다. 예를 들어, 레코드 참조를 사용할 수 있습니다 합니다 [ **필터** ](function-filter-lookup.md) 없이 작동할 **IsType** 하거나 **AsType**:

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

마찬가지로, 레코드 참조를 사용할 수 있습니다 합니다 [ **패치** ](function-patch.md) 함수:

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

내에서 같은 레코드 컨텍스트에서 사용 하는 경우는 [ **갤러리** ](../controls/control-gallery.md) 하거나 [ **편집 양식** ](../controls/control-form-detail.md) 컨트롤을 사용 하도록 해야 할 수는 [전역 명확성 연산자](operators.md#disambiguation-operator) 엔터티 유형을 참조할 수 있습니다. 예를 들어이 수식을 연락처 목록을 표시 하는 갤러리에 적용 될 위치 **회사 이름** 되는 **고객** 조회 합니다.

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

두 함수 모두 엔터티에 연결 된 데이터 소스의 이름을 통해 형식을 지정 합니다. 작동 하려면 수식에 대 한 앱을 테스트 하거나 캐스팅에 원하는 모든 형식에 데이터 원본의도 추가 해야 합니다. 예를 들어 추가 해야 합니다 **사용자** 사용 하려는 경우 데이터 원본으로 엔터티 **IsType** 및 **AsType** 사용 하 여는 **소유자** 조회 및 레코드 해당 엔터티에서 합니다. 앱에서 실제로 사용 하는 데이터 원본만 추가할 수 있습니다. 조회를 참조할 수 있는 모든 엔터티를 추가할 필요가 없습니다.

레코드 참조 이면 *빈*를 **IsType** 반환 *false*, 및 **AsType** 반환 *빈*합니다. 모든 필드를 *빈* 레코드가 *빈*합니다.

## <a name="syntax"></a>구문

**AsType**( *RecordReference*, *EntityType* )

- *RecordReference* -필수 항목입니다. 레코드 참조 조회 필드의 여러 엔터티 레코드를 참조할 수 있는 경우가 많습니다.
- *EntityType* -필수 항목입니다. 테스트 하려는 특정 엔터티.

**IsType**( *RecordReference*, *EntityType* )

- *RecordReference* -필수 항목입니다. 레코드 참조 조회 필드의 여러 엔터티 레코드를 참조할 수 있는 경우가 많습니다.
- *EntityType* -필수 항목입니다. 캐스트할 특정 엔터티입니다.

## <a name="example"></a>예

[레코드 참조 및 다형 조회 이해](../working-with-references.md) 광범위 한 예제가 포함 되어 있습니다.

1. 태블릿에 대 한 빈 캔버스 앱을 만듭니다.

1. 에 **뷰** 탭을 선택 **데이터 원본**, 추가한 다음 합니다 **연락처** 및 **계정** 데이터 원본으로 엔터티.
    > [!div class="mx-imgBorder"]
    > ![두 데이터 소스를 사용 하 여 비어 있는 앱: 계정 및 연락처](media/function-astype-istype/contacts-add-datasources.png)

1. 삽입 된 **갤러리** 컨트롤을 **빈 세로** 방향:

    > [!div class="mx-imgBorder"]
    > ![빈 세로 레이아웃을 사용 하 여 갤러리 컨트롤 삽입](media/function-astype-istype/contacts-customer-gallery.png)

1. 에 **속성** 오른쪽 탭 창, 갤러리의 설정 **항목** 속성을 **연락처**합니다.

    > [!div class="mx-imgBorder"]
    > ![속성 창에서 연락처 항목을 설정](media/function-astype-istype/contacts-customer-datasource.png)

1. 갤러리의 레이아웃 설정 **제목 및 부제목**합니다.

    > [!div class="mx-imgBorder"]
    > ![속성 창에서 레이아웃 선택기를 엽니다](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![제목 및 부제목을 레이아웃을 설정 합니다.](media/function-astype-istype/contacts-customer-flyout.png)

1. 에 **데이터** 창 열기를 **Title1** 목록에서 선택한 후 **전체 이름**:

    > [!div class="mx-imgBorder"]
    > ![제목 값 설정](media/function-astype-istype/contacts-customer-title.png)

1. 선택 된 **Subtitle1** 레이블 컨트롤:

    > [!div class="mx-imgBorder"]
    > ![부제목 값 설정](media/function-astype-istype/contacts-customer-subtitle.png)

1. 설정 된 **텍스트** 속성을 **Subtitle1** 을 다음이 수식으로:

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![화면은 이제 전체 보여 주는 계정 및 연락처 갤러리에서 혼합](media/function-astype-istype/contacts-customer-complete.png)

    갤러리에서 부제목 이러한 값을 보여 줍니다.
    - "-" 하는 경우는 **' 회사 이름 '** 됩니다 *빈*합니다.
    - "계정:" 차례로 **계정 이름** 필드를 **계정** 엔터티 경우는 **회사 이름** 필드는 계정에 참조 합니다.
    - "에 게 문의:" 차례로 **전체 이름** 필드를 **연락처** 엔터티 경우는 **회사 이름** 필드는 연락처를 참조 합니다.

    결과 다른 유형의 결과 표시 하도록 수정 된 샘플 데이터를 사용 하기 때문에이 항목에서 다 수 있습니다.