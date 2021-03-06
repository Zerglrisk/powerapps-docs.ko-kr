---
title: 포털에 대한 엔터티 권한을 사용하여 레코드 기반 보안 추가 | MicrosoftDocs
description: 엔터티 권한을 추가하고 웹 역할을 할당하기 위한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c92b664c2c40c6bb6354e2666d583d5c7ed7aead
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874437"
---
# <a name="add-record-based-security-by-using-entity-permissions-for-portals"></a>포털의 엔터티 권한을 사용하여 레코드 기반 보안 추가

포털에서 개별 레코드에 레코드 기반 보안을 적용하려면 엔터티 권한을 사용합니다. 엔터티 권한을 사용하여 도입된 레코드 소유권 및 액세스의 권한 및 개념에 논리적으로 해당하는 조직에서의 역할을 정의할 수 있도록 웹 역할에 엔터티 권한을 추가합니다. 지정된 연락처는 여러 역할에 속할 수 있고 지정된 역할에는 여러 엔터티 권한이 포함될 수 있습니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [포털의 웹 역할 만들기](create-web-roles.md) 

사이트 관리자는 포털 사이트 맵에서 URL을 변경하고 액세스할 수 있는 권한을 콘텐츠 권한 부여를 통해 부여해주면서도, 동시에 엔터티 양식 및 엔터티 목록으로 빌드된 사용자 지정 웹 응용 프로그램의 보호도 원합니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [엔터티 양식 정의](entity-forms.md) 및 [엔터티 목록 정의](entity-lists.md)  

이러한 기능을 보호하기 위해, 엔터티 권한은 관계 정의를 통해 사용할 수 있는 임의의 엔터티 및 레코드 수준 보안에 세분화된 권한이 부여되도록 허용합니다.

## <a name="add-entity-permissions-to-a-web-role"></a>웹 역할에 엔터티 권한 추가

1.  [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** &gt; **웹 역할**로 이동하여 권한을 추가하려는 웹 역할을 엽니다. 

3. **관련 항목** 아래에서 **엔터티 권한**을 선택합니다.

4. 웹 역할에 기존 엔터티 권한을 추가하려면 **기존 엔터티 권한 추가**를 선택합니다. 

4. 엔터티 권한을 찾거나 **새 엔터티 권한**을 선택하여 새 엔터티 권한 레코드를 만듭니다.

    ![웹 역할에 엔터티 권한 추가](../media/add-entity-permission-web-role.png "웹 역할에 엔터티 권한 추가")  

새 엔터티 권한 레코드를 만들 때, 첫 번째 단계는 보호할 엔터티를 정하는 것입니다. 다음 단계는 아래 설명된 것처럼 범위를 정의하는 것이고 전역 외 범위의 경우, 해당 범위를 정의하는 관계를 지정해야 합니다. 마지막으로, 이 권한을 통해 역할에 부여되는 권한을 결정합니다. 권한은 누적되므로 사용자가 읽기를 허용하는 역할과 읽기 및 업데이트를 허용하는 또 다른 역할을 가진 경우, 해당 사용자는 두 가지 역할 사이에 겹치는 모든 레코드에 대해 읽기 및 업데이트 권한을 갖습니다.

> [!Note]
> 웹 페이지 및 웹 파일과 같은 CMS 엔터티를 선택하는 것은 잘못된 것이며 다른 의도하지 않은 결과가 발생할 수 있습니다. 포털은 엔터티 권한이 아닌 콘텐츠 액세스 제어를 기반으로 CMS 엔터티의 보안을 어설션합니다.

### <a name="global-scope"></a>전역 범위

읽기 권한을 가진 엔터티 권한이 전역 범위의 역할에 부여될 경우, 해당 역할의 연락처는 정의된 엔터티의 모든 레코드에 액세스할 수 있습니다. 예를 들어, 모든 잠재 고객, 모든 거래처 등을 볼 수 있습니다. 모든 엔터티 목록은 이 권한을 자동으로 준수하며 기본적으로 해당 목록에 대해 정의된 모델 기반 앱 보기를 따라 모든 레코드를 표시합니다. 또한 사용자가 액세스 권한이 없는 엔터티 양식을 통해 레코드에 액세스하려는 경우, 권한 오류가 발생합니다.

### <a name="contact-scope"></a>연락처 범위

연락처 범위를 사용하면 권한 레코드가 정의되어 있는 역할의 로그인 사용자에게는 정의된 관계를 통해 해당 사용자의 연락처 레코드와 관련된 레코드에 대해서만 해당 권한으로 부여한 권한이 생깁니다.

엔터티 목록에서 필터는 현재 사용자에게 직접 연결된 레코드만 검색하는 목록에 의해 표시되는 모든 모델 기반 앱 보기에 추가될 것임을 의미합니다. (시나리오에 따라 이 관계는 소유권 또는 관리 권한으로 간주할 수 있습니다.)

레코드를 로드할 때 이 관계가 존재하는 경우 엔터티 양식은 읽기, 만들기, 쓰기 등의 적합한 권한만을 허용합니다. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [엔터티 양식 정의](entity-forms.md).  

### <a name="account-scope"></a>계정 범위

계정 범위를 사용하면 권한 레코드가 정의되어 있는 역할의 로그인 사용자에게는 정의된 관계를 통해 해당 사용자의 상위 계정 레코드와 관련된 레코드에 대해서만 해당 권한으로 부여한 권한이 생깁니다.

### <a name="self-scope"></a>자체 범위

자체 범위를 사용하면 사용자가 고유의 연락처(ID) 레코드에 대해 가지고 있는 권한을 정의할 수 있습니다. 그러면 사용자는 엔터티 양식 또는 웹 양식을 사용하여 프로필과 링크된 자신의 연락처 레코드를 변경할 수 있습니다. 기본 프로필 페이지에는 모든 사용자가 기본 연락처 정보를 변경하고 마케팅 목록을 선택하거나 제외할 수 있는 특별한 기본 제공 양식이 있습니다. 이 양식이 포털에 포함되어 있는 경우(기본값)에는 양식을 사용하기 위해 이 권한이 필요하지 않습니다. 그러나 사용자 연락처 레코드를 대상으로 하는 모든 사용자 지정 엔터티 양식 또는 웹 양식을 사용하기 위해서는 이 권한이 필요합니다.

### <a name="parental-scope"></a>상위/하위 범위

이렇게 복잡한 경우에는 엔터티 권한 레코드가 이미 정의되어 있는 엔터티에서 관계가 먼 엔터티에 대해 권한이 부여됩니다. 이 권한은 실제로는 상위 엔터티 권한의 하위 레코드입니다.

상위 권한 레코드는 엔터티의 권한 및 범위를 정의합니다(상위도 가능하지만, 전역 또는 연락처 범위일 가능성이 높음). 해당 엔터티는 연락처(연락처 범위의 경우)와 관련되거나 전역으로 정의될 수 있습니다. 해당 권한이 준비된 경우, 다른 엔터티에서 상위 관계에 정의된 엔터티까지의 관계를 정의하는 하위 권한이 만들어집니다.

따라서 상위 엔터티 권한이 정의한 레코드에 액세스할 수 있는 웹 역할의 사용자에게는 하위 권한 레코드에 정의된 대로 상위 레코드와 관련된 레코드에 대한 권한이 생깁니다.

### <a name="attributes-and-relationships"></a>특성 및 관계

아래 테이블은 엔터티 권한 특성에 대해 설명합니다.

| 이름                     | 설명                                                                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 이름                     | 레코드를 설명하는 이름입니다. 이 필드는 필수 필드입니다.                                                                                                                                                                                                                                                               |
| 엔터티 이름              | 하위 권한에서 관련된 엔터티를 보호하기 위해 연락처 관계 또는 상위 관계를 정의하거나 보안을 유지해야 할 엔터티의 논리적 이름입니다. 이 필드는 필수 필드입니다.                                                                                                                        |
| 범위(필수)                   | <ul><li>**전역**: 담당자(연락처)에 대한 요구 사항 없이 엔터티 레코드에 권한을 부여합니다.</li><li>**연락처**: 담당자(연락처)에 직접적인 관계가 있는 엔터티 레코드에 권한을 부여합니다.</li><li>**거래처**: 거래처가 연락처의 상위 고객이라고 가정할 경우, 소유자 역할을 하는 거래처와 관계가 있는 엔터티 레코드에 권한을 부여합니다.</li><li>**상위**: 해당 상위 권한 관계 체인을 통해 엔터티 레코드에 권한을 부여합니다.</li></ul>|
| 연락처 관계     | 범위 = 연락처인 경우에만 필요합니다. 엔터티 이름 필드에 의해 지정된 엔터티와 연락처 간 관계의 스키마 이름입니다.|
| 상위 관계      | 상위 엔터티 권한이 할당된 경우에만 필요합니다. 해당 상위 엔터티 권한 레코드에서 엔터티 이름 필드에 지정된 엔터티와 엔터티 이름 필드에 지정된 엔터티 간 관계의 스키마 이름입니다.                                                                                     |
| 상위 엔터티 권한 | 범위 = 상위인 경우에만 필요합니다.                                                                                                                                                                                                                                                            |
| 읽기                     | 사용자가 레코드를 읽을 수 있는지 여부를 제어하는 권한입니다.                                                                                                                                                                                                                                                               |
| 쓰기                    | 사용자가 레코드를 업데이트할 수 있는지 여부를 제어하는 권한입니다.                                                                                                                                                                                                                                                             |
| 만들기                   | 사용자가 새 레코드를 만들 수 있는지 여부를 제어하는 권한입니다. 엔터티 유형의 레코드를 만드는 권한은 개별 레코드에는 적용되지 않지만 대신 엔터티의 클래스에는 적용됩니다.                                                                                                                             |
| Del                   | 사용자가 레코드를 삭제할 수 있는지 여부를 제어하는 권한입니다.                                                                                                                                                                                                                                                             |
| 레코드 추가                   | 사용자가 다른 레코드를 지정된 레코드에 연결할 수 있는지 여부를 제어하는 권한입니다. 레코드 추가 및 다른 레코드에 추가 액세스 권한은 함께 작동합니다. 사용자가 한 레코드를 다른 레코드에 추가할 때마다 사용자는 두 권한이 모두 있어야 합니다. 예를 들어, 서비스 케이스에 메모를 추가할 때 메모에 대한 추가 액세스 권한과 서비스 케이스에 대한 다른 레코드에 추가 액세스 권한이 있어야 작업이 가능합니다.  |
| 다른 레코드에 추가                | 사용자가 해당 레코드를 다른 레코드에 연결할 수 있는지 여부를 제어하는 권한입니다. 레코드 추가 및 다른 레코드에 추가 액세스 권한은 함께 작동합니다. 자세한 내용은 추가에 대한 설명을 참조하십시오.|
| | |

## <a name="global-permissions-for-tasks-related-to-leads"></a>잠재 고객에 관련된 작업에 대한 전역 권한

엔터티 목록 및 엔터티 양식을 사용하여 포털의 모든 잠재 고객을 사용자 지정 잠재 고객 관리자 웹 역할을 가진 사람에게 표시하려는 경우가 있을 수 있습니다. 목록의 잠재 고객 행을 선택할 때마다 실행되는 잠재 고객 편집 양식에서 하위 표에 관련된 작업 레코드가 표시됩니다. 이러한 레코드는 잠재 고객 관리자 역할을 가진 모든 사용자가 액세스할 수 있어야 합니다. 첫 단계로, 잠재 고객 관리자 역할의 모든 사용자에게 잠재 고객에 대한 전역 권한을 제공합니다.

이 역할에는 전역 범위를 갖는 잠재 고객 엔터티의 관련 엔터티 권한이 있습니다.

이 역할의 사용자는 포털에서 엔터티 목록 또는 양식을 통해 모든 잠재 고객에게 액세스할 수 있습니다.

![잠재 고객에 전역 권한 부여](../media/grant-global-permission-leads.png "잠재 고객에 전역 권한 부여")  

이제 전역 잠재 고객 권한에 하위 권한을 추가합니다. 상위 권한 레코드가 열리면 **하위 엔터티 권한** 하위 표로 이동하고 **새로 만들기**를 선택하여 엔터티 권한에 대한 조회를 연 다음, 돋보기를 선택하고 **새로 만들기**를 선택하여 새 레코드를 추가합니다.

![웹 역할에 엔터티 권한 추가](../media/add-entity-permission-web-role.png "웹 역할에 엔터티 권한 추가")  

엔터티를 작업으로 선택하고 범위를 상위로 선택하십시오. 그런 다음 상위 관계를 선택할 수 있습니다(**Lead\_Tasks**). 이 권한은 상위 권한을 가진 웹 역할의 연락처에 잠재 고객과 관련된 모든 작업에 대한 전역 권한이 생긴다는 것을 의미합니다.

사용자 목록이 이러한 권한을 준수하려면 목록에서 엔터티 권한을 사용 지정하고, 실제로 사용자가 권한이 부여된 작업을 수행할 수 있도록 허용할 작업이 있어야 합니다. 또한 이 작업의 경우, 권한은 [엔터티 양식](entity-forms.md) 레코드에서 사용 지정해야 하며 해당 양식은 하위 권한으로 사용 지정하려는 엔터티에 대해 하위 표가 있는 페이지를 나타내야 합니다. 또한 작업에 대한 읽기 또는 만들기 권한을 사용하도록 하려면 해당 엔터티 양식을 구성해야 하고, 관련 조회 필드를 제거하기 위해 양식을 편집해야 합니다.  

![웹 페이지 양식 편집](../media/edit-webpage-form.png "웹 페이지 양식 편집")  

그러면 잠재 고객에 관련된 모든 작업에 대한 권한이 부여됩니다. 엔터티 목록에 작업이 표시될 경우, 필터가 기본적으로 목록에 추가되어 잠재 고객과 관련된 작업만 목록에 나타납니다. 이 예에서는, 엔터티 양식에 하위 표를 사용하여 표시됩니다.

![작업 예](../media/tasks-example.png "작업 예")  

## <a name="contact-scoped-permissions-for-tasks"></a>작업에 대한 연락처 범위 권한

또 다른 예는 연락처가 해당 작업의 상위 잠재 고객과 관련된 작업에 액세스를 허용하려고 하는 경우입니다. 이 시나리오는 상위 권한에 대해 전역 대신 연락처 범위를 가지고 있다는 점을 제외하면 이전 섹션과 거의 동일합니다. 잠재 고객 엔터티 및 연락처 엔터티 사이의 하위 관계에 대해 관계를 지정해야 합니다.

이러한 권한이 준비되면 잠재 고객 관리자 역할의 사용자는 연락처 범위 권한에서 지정한 대로 직접 그들과 관련된 잠재 고객에 액세스하고 하위 권한 레코드에서 지정한 대로 해당 동일 잠재 고객과 관련된 작업에 액세스할 수 있습니다.

### <a name="see-also"></a>참고 항목

[포털의 웹 역할 만들기](create-web-roles.md)  
[포털의 웹 페이지 액세스 제어](webpage-access-control.md)