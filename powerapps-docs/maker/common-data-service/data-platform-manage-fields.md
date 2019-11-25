---
title: 엔터티의 사용자 지정 필드 관리 | Microsoft Docs
description: Common Data Service에서 엔터티의 사용자 지정 필드를 만들고 읽고 업데이트하고 삭제하는 방법에 대한 연습입니다.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b0c576b8eab2b547c66a90f0693becf516b01207
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758595"
---
# <a name="manage-custom-fields-in-an-entity"></a>엔터티의 사용자 지정 필드 관리
모든 엔터티에서 하나 이상의 사용자 지정 필드를 만들고 업데이트할 수 있습니다. 사용자 지정 필드를 만들 때는 필드 이름, 표시 이름 및 포함될 데이터 형식과 같은 속성 집합을 지정합니다. 자세한 내용은 [엔터티 속성 메타데이터](../../developer/common-data-service/entity-attribute-metadata.md)를 참조하십시오.

> [!NOTE]
> 모든 엔터티에는 레코드를 마지막으로 업데이트한 시간과 업데이트한 사람을 나타내는 필드와 같은 시스템 필드가 있습니다. 또한 표준 엔터티에는 표준(기본) 필드가 있습니다. 시스템 필드 또는 표준 필드를 수정하거나 삭제할 수 없습니다. 사용자 지정 필드를 만드는 경우에는 이러한 기본 제공 필드 외의 기능을 제공해야 합니다.

## <a name="create-a-field"></a>필드 만들기
1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭합니다.

    ![엔터티 세부 정보](./media/data-platform-cds-create-entity/entitylist.png "엔터티 목록")

2. 기존 엔터티 클릭 또는 탭 또는 [새 엔터티 만들기](data-platform-create-entity.md)

3. **필드 추가**를 클릭하여 엔터티에 새 필드를 추가합니다.

4. 새 필드 패널에서 필드의 **표시 이름**을 입력하면 **이름**이 자동으로 채워지고 필드의 고유 이름으로 사용됩니다. **표시 이름**은 사용자에게 이 필드를 표시할 때 사용되며 이 **이름**은 앱을 빌드할 때 식과 수식에서 사용됩니다.

    > [!NOTE]
    > **표시 이름** 필드는 언제든지 업데이트하여 앱에서 다르게 표시할 수 있으며, **엔터티** 를 저장한 후에는 이름 필드를 변경할 수 없으므로 기존 앱이 손상될 수 있습니다.

    > [!div class="mx-imgBorder"] 
    > ![새 필드](./media/data-platform-cds-create-entity/newfieldpanel.png "새 필드 패널")

5. 필드의 **데이터 형식**을 선택하면 정보가 저장되는 방식과 앱에서 정보를 표시하는 방법을 제어합니다. 예를 들어 텍스트는 10진수 또는 URL과 다르게 저장됩니다. 사용 가능한 데이터 형식에 대한 자세한 내용은 [엔터티 특성 메타데이터](../../developer/common-data-service/entity-attribute-metadata.md)를 참조하십시오.

    메시지가 표시되면 지정한 데이터 형식에 대한 추가 정보를 지정합니다. 데이터 형식에 따라 다른 필드가 표시됩니다. 옵션 집합 또는 다중 선택 옵션 집합의 필드를 만드는 경우 **새 옵션 집합**을 선택하고 필드를 생성하는 동안 새 옵션 집합을 만들 수 있습니다. 자세한 내용은 [옵션 집합 만들기](custom-picklists.md)를 참조하십시오.

    > [!div class="mx-imgBorder"] 
    > ![새 필드](./media/data-platform-cds-create-entity/newfieldpanel-2.png "새 필드 패널")


7. 이 필드를 앱에 필요한 대로 권장하려면 **필수**에서 확인란을 선택합니다. 이는 Common Data Service에 대한 모든 연결 전체에서 엄격한 적용을 제공하지 않습니다. 필드가 채워졌는지 확인해야 하는 경우 [비즈니스 규칙](data-platform-create-business-rule.md)을 만드십시오.

8. 보기 ,차트, 대시보드 및 상세하게 찾기에서 이 필드를 사용하려면 **검색 가능**에서 확인란을 선택합니다. 대부분의 경우 이 확인란을 선택해야 합니다.

9. **완료** 를 클릭하거나 탭하여 필드 패널을 닫고 엔터티로 돌아갑니다. 각 추가 필드에 대해 3~9단계를 반복할 수 있습니다.
   
    > [!IMPORTANT]
    > 엔터티에 대한 변경 내용을 저장할 때까지 필드는 아직 저장되고 만들어지지 않습니다.

10. **엔터티 저장**을 클릭하거나 탭하여 변경 내용을 완료하고 Common Data Service에 저장합니다.

    작업이 성공적으로 완료되면 알림이 표시됩니다. 작업이 실패하면 발생한 문제와 문제를 해결하는 방법에 대한 오류 메시지가 표시됩니다.

## <a name="create-a-calculated-or-roll-up-field"></a>계산 또는 롤업 필드 만들기
계산 필드를 사용하면 비즈니스 프로세스에서 사용되는 수동 계산을 자동화할 수 있습니다. 예를 들어, 영업 직원은 가능성을 곱한 영업 기회에서 예측된 매출을 기반으로 하는 영업 기회에 대한 가중 수익을 알고 싶어할 수 있습니다. 또는 주문이 $500보다 큰 경우 자동으로 할인을 적용하고자 합니다. 계산 필드는 간단한 수학 연산 또는 보다 큼이나 if-else, 등과 같은 조건 연산의 결과 값을 포함할 수 있습니다. 다음 데이터 형식을 사용하여 계산 필드를 만들 수 있습니다.

* 한 줄 텍스트
* 옵션 집합
* 두 개의 옵션
* 정수
* 10진수
* 통화
* 날짜 및 시간

지원되는 표현식 유형과 예제에 대한 자세한 내용은 [계산된 필드 정의](/dynamics365/customer-engagement/customize/define-calculated-fields)를 참조하십시오.

## <a name="update-or-delete-a-field"></a>필드 업데이트 또는 삭제
1. [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에서 **데이터** 섹션을 확장하고 왼쪽 탐색 창에서 **엔터티**를 클릭하거나 탭한 다음 엔터티를 클릭하거나 탭합니다.
2. 선택한 엔터티의 필드 목록에서 필드를 클릭하거나 탭한 후 다음 단계 중 하나를 수행합니다.
   
   * 필드의 하나 이상의 속성 변경
   * 필드의 오른쪽 가장자리 근처에 있는 줄임표(...)를 클릭하거나 탭한 다음 **삭제**를 클릭하거나 탭하여 필드를 삭제합니다.

3. **엔터티 저장**을 클릭하거나 탭하여 변경 내용을 제출합니다.
   
    > [!IMPORTANT]
    > 브라우저에서 다른 페이지를 열거나 브라우저를 종료하기 전에 저장하지 않으면 변경 내용이 손실됩니다.

    작업이 성공적으로 완료되면 알림이 표시됩니다. 작업이 실패하면 발생한 문제와 문제를 해결하는 방법에 대한 오류 메시지가 표시됩니다.

## <a name="best-practices-and-restrictions"></a>모범 사례 및 제한 사항
필드를 만들거나 수정할 때 다음 사항을 기억하십시오.

* 시스템 필드 또는 그 값을 수정하거나 삭제할 수 없습니다.
* 표준 엔터티에서 표준(기본값) 필드를 수정 또는 삭제하거나 데이터가 필요한 필드를 추가하거나 해당 엔터티에 의존 하는 앱을 중단할 수 있는 다른 변경을 수행할 수 없습니다.
* 사용자 지정 엔터티에서는 변경 내용이 해당 엔터티에 의존하는 앱을 중단하지 않는지 확인해야 합니다.
* 각 사용자 정의 필드에 엔터티 내에서 고유한 이름을 지정해야 하며 필드를 만든 후에는 이름을 바꿀 수 없습니다.

## <a name="next-steps"></a>다음 단계
* [엔터티 간 관계 정의](data-platform-entity-lookup.md)
* [비즈니스 규칙 만들기](data-platform-create-business-rule.md)
* [엔터티를 사용하여 앱 만들기](../canvas-apps/data-platform-create-app.md)
* [Common Data Service 데이터베이스를 사용하여 처음부터 앱 만들기](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>개인 정보 취급 방침
Microsoft PowerApps Common Data Model을 사용하면 진단 시스템에서 사용자 지정 엔터티 및 필드 이름을 수집하고 저장합니다.  이 점을 파악하여 고객을 위해 일반적인 데이터 모델을 개선합니다. 작성자가 만드는 엔터티 및 필드 이름은 Microsoft PowerApps 커뮤니티에서 공통적인 시나리오를 이해하고 조직과 관련된 스키마와 같은 서비스의 표준 엔터티 적용 범위에서 차이를 확인하는 데 도움이 됩니다. 이러한 엔터티와 연결된 데이터베이스 테이블의 데이터는 Microsoft에서 액세스하거나 사용하거나 데이터베이스가 프로비전되는 지역 외부에서 복제되지 않습니다. 그러나 사용자 지정 엔터티와 필드 이름은 여러 지역에 걸쳐 복제될 수 있으며 데이터 보존 정책에 따라 삭제됩니다. Microsoft는 [보안 센터](https://www.microsoft.com/trustcenter/Privacy/default.aspx)에서 추가로 설명한 대로 사용자의 개인 정보를 보호하기 위해 최선을 다하고 있습니다.

