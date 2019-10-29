---
title: Canvas 앱에서의 유형 및 IsType 함수 | Microsoft Docs
description: Canvas 앱의 정보 및 IsType 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2019
ms.locfileid: "71992992"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>Canvas 앱의 안 면 및 IsType 함수

특정 엔터티 형식 (**istype**)에 대 한 레코드 참조를 확인 하 고 참조를 특정**형식 (예를 들어**)으로 처리 합니다.

## <a name="description"></a>설명

광범위 한 소개 및 자세한 내용은 [레코드 참조 및 다형성 조회 이해](../working-with-references.md) 를 참조 하세요.

조회 필드는 일반적으로 특정 엔터티의 레코드를 나타냅니다. 엔터티 형식이 제대로 설정 되었으므로 간단한 점 표기법을 사용 하 여 조회 필드에 액세스할 수 있습니다. 예를 들어 **첫 번째 (계정). 기본 연락처 '. ' 전체 이름 '** **Accounts** 엔터티에서 **담당자** 엔터티의 **기본 연락처** 레코드에 대해 안내 하 고 **전체 이름** 필드를 추출 합니다.

또한 Common Data Service는 다음 예와 같이 엔터티 집합의 레코드를 참조할 수 있는 다형 조회 필드도 지원 합니다.

| 조회 필드 | 참조할 수 있습니다. |
|--------------|--------------|
| **소유자도** | **사용자** 또는 **팀** |
| **고객** | **계정** 또는 **연락처** |
| **관련** | **계정**, **연락처**, **기술 문서**등 |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

캔버스-앱 수식에서 레코드 참조를 사용 하 여 다형 조회 작업을 수행할 수 있습니다. 레코드 참조는 서로 다른 엔터티를 참조할 수 있으므로 수식을 작성할 때 어떤 필드를 사용할 수 있는지 알 수 없습니다. *입니다. 필드* 표기법을 사용할 수 없습니다. 이러한 수식은 앱이 실행 될 때 발생 하는 레코드에 맞게 조정 되어야 합니다.

**Istype** 함수는 레코드 참조가 특정 엔터티 형식을 참조 하는지 여부를 테스트 합니다. 이 함수는 부울 TRUE 또는 FALSE를 반환 합니다.

고 **유형 함수는** 레코드 참조를 특정 엔터티 형식으로 처리 합니다 .이를 *캐스팅이*라고도 합니다. 엔터티 레코드 였던 것 처럼 결과를 사용 하 고를 다시 사용할 수 있습니다 *.* 해당 레코드의 모든 필드에 액세스 하는 필드 표기법입니다. 참조가 특정 형식이 아닌 경우 오류가 발생 합니다.

이러한 함수를 함께 사용 하 여 레코드의 엔터티 형식을 먼저 테스트 한 다음 필드를 사용할 수 있도록 해당 형식의 레코드로 처리 합니다.

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

레코드 참조의 필드에 액세스 하는 경우에만 이러한 함수가 필요 합니다. 예를 들어 [**필터**](function-filter-lookup.md) 함수에서 레코드 참조를 사용할 수 **있습니다**.

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

마찬가지로 [**Patch**](function-patch.md) 함수를 사용 하 여 레코드 참조를 사용할 수 있습니다.

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

[**갤러리**](../controls/control-gallery.md) 또는 [**편집 양식**](../controls/control-form-detail.md) 컨트롤에서와 같은 레코드 컨텍스트에서 사용 되는 경우에는 [전역 명확성 연산자](operators.md#disambiguation-operator) 를 사용 하 여 엔터티 형식을 참조 해야 할 수 있습니다. 예를 들어 다음 수식은 **회사 이름이** **고객** 조회 인 연락처 목록을 표시 하는 갤러리에 적용 됩니다.

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

두 함수 모두 엔터티에 연결 된 데이터 소스의 이름을 통해 형식을 지정 합니다. 수식이 작동 하려면 테스트 하거나 캐스팅할 모든 형식의 응용 프로그램에 데이터 소스도 추가 해야 합니다. 예를 들어 **소유자** 조회와 해당 엔터티의 레코드 **를 사용 하 여** **istype** 사용 하려는 경우에는 **사용자** 엔터티를 데이터 원본으로 추가 해야 합니다. 앱에서 실제로 사용 하는 데이터 원본만 추가할 수 있습니다. 조회가 참조할 수 있는 모든 엔터티를 추가할 필요는 없습니다.

레코드 참조가 *비어*있는 경우 **ISTYPE** 는 FALSE **를 반환 하 고,** 는 *빈*값을 반환 합니다. *빈* 레코드의 모든 필드가 *비어*있게 됩니다.

## <a name="syntax"></a>구문

고 유형 ( *recordreference*, *EntityType* )

- *Recordreference* -필수 항목입니다. 레코드 참조, 종종 여러 엔터티의 레코드를 참조할 수 있는 조회 필드입니다.
- *EntityType* -필수 항목입니다. 테스트할 특정 엔터티입니다.

**Istype**( *recordreference*, *EntityType* )

- *Recordreference* -필수 항목입니다. 레코드 참조, 종종 여러 엔터티의 레코드를 참조할 수 있는 조회 필드입니다.
- *EntityType* -필수 항목입니다. 레코드를 캐스팅할 특정 엔터티입니다.

## <a name="example"></a>예

[레코드 참조 및 다형성 조회에 대 한 자세한 예제를 이해](../working-with-references.md) 합니다.

1. 태블릿 용 빈 캔버스 앱을 만듭니다.

1. **보기** 탭에서 **데이터 원본**을 선택 하 고 **연락처** 및 **계정** 엔터티를 데이터 원본으로 추가 합니다.
    > [!div class="mx-imgBorder"]
    > 두 개의 데이터 원본 (계정 및 연락처)이 있는 비어 있는 앱 ![](media/function-astype-istype/contacts-add-datasources.png)

1. **세로** 방향으로 **갤러리** 컨트롤을 삽입 합니다.

    > [!div class="mx-imgBorder"]
    > 빈 세로 레이아웃을 사용 하 여 갤러리 컨트롤을 삽입 ![](media/function-astype-istype/contacts-customer-gallery.png)

1. 화면 오른쪽의 **속성** 탭에서 갤러리의 **Items** 속성을 contact로 설정 **합니다.**

    > [!div class="mx-imgBorder"]
    > 속성 창에서 연락처에 항목을 설정 ![](media/function-astype-istype/contacts-customer-datasource.png)

1. 갤러리의 레이아웃을 **제목 및 부제목**으로 설정 합니다.

    > [!div class="mx-imgBorder"]
    > 속성 창에서 레이아웃 선택 ![엽니다](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > 레이아웃을 제목 및 부제목으로 설정 ![](media/function-astype-istype/contacts-customer-flyout.png)

1. **데이터** 창에서 **Title1** 목록을 열고 **전체 이름**을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > ![제목 값을 설정](media/function-astype-istype/contacts-customer-title.png)

1. **Subtitle1** label 컨트롤을 선택 합니다.

    > [!div class="mx-imgBorder"]
    > 자막 값 ![설정](media/function-astype-istype/contacts-customer-subtitle.png)

1. **Subtitle1** 의 **Text** 속성을 다음 수식으로 설정 합니다.

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > 이제 ![화면은 갤러리에 있는 계정과 연락처를 표시 하는 완료 되었습니다](media/function-astype-istype/contacts-customer-complete.png)

    갤러리의 부제는 다음 값을 표시 합니다.
    - **' 회사 이름 '** 이 *비어*있는 경우 "--"입니다.
    - **회사 이름** 필드가 계정을 참조 **하는 경우 계정 엔터티의** **계정 이름** 필드를 "account:"로 차례로 클릭 합니다.
    - **회사 이름** 필드가 연락처를 참조 하는 경우에는 **연락처** 엔터티의 **전체 이름** 필드와 "contact:"를 차례로 클릭 합니다.

    결과는 추가 결과 유형을 표시 하기 위해 수정 된 샘플 데이터를 사용 하기 때문에이 항목의 결과와 다를 수 있습니다.
