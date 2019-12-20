---
title: Common Data Service로 가상 엔터티 만들기 및 편집 | MicrosoftDocs
description: 가상 엔터티를 만드는 방법 알아보기
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 44834893-0bf6-4a64-8f06-7583fe08330d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07a6d262aeaba818d5a965409ce28a90934536c3
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861302"
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>외부 데이터 원본에서 데이터를 포함하는 가상 엔터티 만들기 및 편집

가상 엔터티는 외부 데이터 원본의 데이터를 포함하는 필드가 있는 Common Data Service의 사용자 지정 엔터티입니다. 가상 엔터티는 앱에서 사용자에게 일반 엔터티 레코드로 표시되지만 Azure SQL 데이터베이스와 같은 외부 데이터베이스에서 발생한 데이터를 포함합니다. 가상 엔터티에 기반한 레코드는 Common Data Service 웹 서비스를 사용하여 개발한 사용자 지정 클라이언트를 비롯한 모든 클라이언트에서 사용할 수 있습니다.  
  
과거에는 서로 다른 데이터 원본을 통합하려면 데이터를 이동하거나 사용자 지정 플러그 인(클라이언트 측 또는 서버 측)을 개발하기 위한 커넥터를 만들어야 했습니다. 그러나 가상 엔터티를 사용하면 런타임에 외부 데이터 원본에 직접 연결할 수 있으므로 데이터 복제 없이 환경에서 외부 데이터 원본의 특정 데이터를 사용할 수 있습니다.  

가상 엔터티는 세 가지 주요 구성 요소, *데이터 공급자*, *데이터 원본* 레코드 및 *가상 엔터티*로 구성됩니다. 데이터 공급자는 플러그 인 및 데이터 원본 엔터티로 구성됩니다. 데이터 원본은 연결 매개 변수의 스키마를 나타내는 메타데이터를 포함하는 Common Data Service의 엔터티 레코드입니다. 각 가상 엔터티는 엔터티 정의의 데이터 원본을 참조합니다.  
  
Common Data Service에는 외부 데이터에 액세스하는 OData v4 웹 서비스와 연결할 때 사용할 수 있는 OData 데이터 공급자가 포함됩니다. 
  
또는 개발자는 자신의 데이터 공급자를 빌드할 수 있습니다. 데이터 공급자는 환경에 솔루션으로 설치됩니다. 추가 정보: [개발자 설명서: 가상 엔터티 시작](../../developer/common-data-service/virtual-entities/get-started-ve.md)
  
 ![가상 엔터티 다이어그램](media/virtual-entity-diagram.png "가상 엔터티 다이어그램")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>가상 엔터티 혜택  
  
- 개발자는 Common Data Service 웹 서비스 및 플러그 인 등록 도구를 사용하여 외부 데이터를 읽기 위한 플러그 인을 구현할 수 있습니다.  
- 시스템 사용자 지정자는 Power Apps 솔루션 탐색기를 사용하여 코드를 작성하지 않고 외부 데이터에 액세스하는 데 사용되는 가상 엔터티를 만들고 데이터 원본 레코드를 구성합니다.  
- 최종 사용자는 가상 엔터티에서 만든 레코드를 사용하여 필드, 표, 검색 결과 및 Fetch XML 기반 보고서와 대시보드의 데이터를 봅니다.  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>가상 엔터티에 사용할 데이터 원본 추가 
 
 개발자는 가상 엔터티에 대해 데이터 공급자로 사용할 사용자 지정 플러그 인을 만들 수 있습니다. 또는 제공된 OData v4 데이터 공급자를 사용할 수 있습니다. 추가 정보: [OData v4 데이터 공급자 구성, 요구 사항 및 모범 사례](virtual-entity-odata-provider-requirements.md)  
  
1. **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **관리** > **가상 엔터티 데이터 원본**으로 이동합니다.  
1. 작업 도구 모음에서 **새로 만들기**를 선택합니다.  
1. **데이터 공급자** 선택 대화 상자에서 다음 데이터 원본에서 선택하고 **확인**을 선택합니다.
 
    |데이터 공급자|설명|
    |--|--|
    |*사용자 지정 데이터 공급자*|데이터 공급자 플러그 인을 가져온 경우 데이터 공급자가 여기에 표시됩니다. 추가 정보 [개발자 설명서: 가상 엔터티 시작](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |**OData v4 데이터 공급자**|Common Data Service에는 OData v4 웹 서비스와 함께 사용할 수 있는 OData 데이터 공급자를 포함합니다. 추가 정보 [OData v4 데이터 공급자 구성, 요구 사항 및 모범 사례](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>데이터 원본에 보안 필드 추가

다른 엔터티와 동일한 방식으로 데이터 원본에 대한 필드를 만듭니다. 암호화되거나 중요한 데이터의 경우 데이터 원본의 사용자 지정 필드에서 데이터 원본 비밀 특성을 사용하도록 설정합니다. 예를 들어, 데이터베이스 연결 문자열을 포함하는 필드의 보안을 설정합니다. 

> [!NOTE]
> 데이터 원본 비밀 특성은 데이터 원본 양식에 추가된 필드에서만 사용할 수 있습니다.

> [!div class="mx-imgBorder"] 
> ![데이터 원본 비밀 특성](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>가상 엔터티 만들기
  
여기서 설명하는 몇 가지 추가 특성을 추가하여 Common Data Service의 다른 엔터티와 마찬가지로 가상 엔터티를 만듭니다. 가상 엔터티는 솔루션 탐색기를 사용하여 만들어야 합니다.

> [!NOTE]
>  데이터 원본으로 **없음**을 선택하여 가상 엔터티를 만들 수 있지만 데이터를 가져오려면 가상 엔터티에는 데이터 원본이 필요합니다. 추가 정보 [가상 엔터티에 사용할 데이터 원본 추가](#AddDataSource)

### <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 가상 엔터티의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 가상 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>가상 엔터티 만들기
  
1. 솔루션 탐색기에서 새 엔터티를 만듭니다. 이를 수행하려면 왼쪽 탐색창에 있는 **엔터티**를 선택한 다음 **새로 만들기**를 선택합니다.  
2. **엔터티 정의**의 **일반** 탭에서 **가상 엔터티**를 선택한 다음 **데이터 원본** 드롭다운 목록에서 원하는 데이터 원본을 선택합니다.  

    > [!div class="mx-imgBorder"] 
    > ![엔터티 정의의 가상 엔터티 옵션](media/virtual-entity-click-option.png)  
  
1. 엔터티 정의에서 다음 필수 필드를 완료합니다.
  
    |필드|설명|
    |--|--|
    |**외부 이름**|이 엔터티가 매핑되는 외부 데이터 원본에 테이블 이름을 입력합니다.|
    |**외부 컬렉션 이름**|이 엔터티가 매핑되는 외부 데이터 원본에 테이블 복수 이름을 입력합니다.|
      
    다음은 Azure Cosmos DB 데이터 공급자를 사용하여 문서 파일에 액세스하는 *영화*라는 가상 엔터티의 예입니다.  
      
    > [!div class="mx-imgBorder"] 
    > ![Azure Cosmos DB 데이터 공급자를 사용하여 가상 엔터티 정의](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > 액세스 팀, 큐 및 빨리 만들기와 같은 몇 가지 옵션을 가상 엔터티와 함께 사용할 수 없습니다. 추가 정보 [가상 엔터티를 사용할 때 고려할 사항](#considerations)  
      
    필요에 따라 표시 및 복수 이름 등의 추가 필수 및 선택적 속성을 완료합니다. 이러한 속성에 대한 자세한 내용은 [엔터티 만들기 및 편집](create-edit-entities.md)을 참조하십시오.  
  
1. 가상 엔터티에 대해 하나 이상의 필드를 만들고 추가합니다. 사용자 지정 필드를 만드는 데 필요한 표준 필드 속성 외에도 가상 엔터티에 대해 만든 각 사용자 지정 필드에 이러한 선택적 속성을 사용할 수 있습니다.

    |필드|설명|
    |--|--|
    |**외부 이름**|일반적으로 필드에 표시할 데이터를 식별하는 고유한 이름입니다.|
    |**외부 유형 이름**|만드는 필드 형식이 옵션 집합인 경우: 이 속성은 옵션 집합에 대한 외부 서비스의 값 집합의 외부 이름에 매핑됩니다.  일반적으로 문자열 값 클래스의 열거형 또는 이름일 수 있습니다. 정규화된 이름이 필요한 경우 외부 형식 이름을 사용할 수 있습니다.  예를 들어 [*형식 이름*].[*값*]과 같이 OData의 *형식 이름*에 쿼리의 매개 변수에 정규화된 이름이 필요합니다.|
    |**외부 값**|만드는 필드 형식이 옵션 집합인 경우: 이 속성은 옵션 집합 항목에 대한 외부 데이터 원본의 해당 값에 매핑됩니다.  이 값은 앱에서 표시할 옵션 집합 항목을 결정하는 데 사용됩니다.  |

    필요에 따라 추가 속성을 완료합니다. 이러한 속성에 대한 자세한 내용은 [필드 만들기 및 편집](create-edit-fields.md)을 참조하십시오.  
  
1. **필드** 속성 페이지에서 **저장 후 닫기**를 선택합니다.  
1. 솔루션 탐색기 모음에서 **저장**을 선택합니다.  
1. 솔루션 탐색기 모음에서 **게시**를 선택합니다.  
1. 솔루션 탐색기를 닫습니다.  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>가상 엔터티를 사용할 때 고려할 사항  

가상 엔터티에는 이러한 제한이 있습니다.  
  
- 모든 가상 엔터티는 읽기 전용입니다.  
- 기존 엔터티는 가상 엔터티로 변환할 수 없습니다.  
- 기본적으로 가상 엔터티에는 이름 및 ID 필드만 포함됩니다.  상태 또는 만든 날짜/수정한 날짜와 같은 다른 시스템 관리 필드는 지원되지 않습니다.
- 가상 엔터티는 통화, 이미지 또는 고객 데이터 형식의 사용자 지정 필드를 지원하지 않습니다.
- 가상 엔터티는 감사를 지원하지 않습니다.  
- 가상 엔터티 필드는 롤업 또는 계산 필드에 사용할 수 없습니다.
- 가상 엔터티는 엔터티의 활동 유형이 될 수 없습니다.  
- 엔터티 테이블 행에 영향을 주는 많은 기능은 가상 엔터티에 대해 사용할 수 없습니다.  예를 들어 큐, 참조 자료 관리, SLA, 중복 검색, 변경 내용 추적, Mobile offline 기능, 필드 보안, 관련성 검색, Dynamics 365 웹 포털 솔루션용 포털 및 가상 엔터티 간 N:N 관계 등이 있습니다.  
- 가상 엔터티는 조직 소유이며 행 수준 Common Data Service 보안 개념을 지원하지 않습니다. 외부 데이터 원본에 대한 사용자 고유의 보안 모델을 구현하는 것이 좋습니다.  
- 고급 검색에서 가상 엔터티를 사용할 때 단일 데이터 원본을 대상으로 하는 것이 좋습니다. 예를 들어 Common Data Service 네이티브 데이터와 가상 엔터티 외부 데이터 간에 연결을 만드는 상세하게 찾기를 만드는 것은 지원되지 않습니다.  
- 업데이트 시 유효성을 검사하는 필드 메타데이터 속성은 가상 엔터티에 적용되지 않습니다. 예를 들어 가상 엔터티 필드의 정수 필드의 최소값을 0으로 설정할 수 있습니다. 그러나 값이 외부 데이터 원본에서 가져온 것이므로 가상 엔터티에서 검색할 때 쿼리는 0보다 작은 값을 반환합니다.  최소 값 속성은 쿼리에 포함되지 않습니다.  원하는 경우 값을 0보다 크게 필터링해야 할 수 있습니다.
- 가상 엔터티는 변경 내용 추적을 지원하지 않으며 데이터 내보내기 서비스와 같은 Common Data Service 기능을 사용하여 동기화할 수 없습니다.
  
### <a name="see-also"></a>참조  

[OData v4 데이터 공급자 요구 사항 및 모범 사례](virtual-entity-odata-provider-requirements.md)</br> 
[엔터티 만들기 및 편집](create-edit-entities.md)</br>
[필드 만들기 및 편집](create-edit-fields.md)
