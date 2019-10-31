---
title: Common Data Service에서 OData 데이터 공급자를 사용하는 가상 엔터티 연습 | MicrosoftDocs
description: OData v4 데이터 공급자를 가상 엔터티와 함께 사용하는 방법 알아보기
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: null
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>OData v4 데이터 공급자를 사용 는 가상 엔터티 연습

모델 기반 앱 내에서 외부 데이터 원본의 티켓 정보에 액세스하려는 경우를 가정해 보겠습니다. 이 간단한 연습에서는 런타임에 OData 웹 서비스에서 티켓 데이터를 검색하는 외부 스키마에 매핑된 필드가 있는 가상 엔터티를 모델링합니다.

## <a name="data-source-details"></a>데이터 원본 정보

이 연습에 사용되는 데이터 원본에는 OData v4 웹 서비스가 있으므로 사용자 환경에 포함된 OData v4 데이터 공급자를 사용할 수 있습니다.

웹 서비스 url: `http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> 이 연습에 사용되는 웹 서비스 URL은 작동하는 웹 서비스가 아닙니다.

이 연습에서는 다음 세 개의 필드가 포함된 단일 가상 엔터티가 필요합니다.

|외부 필드 이름 |외부 데이터 유형 |가상 엔터티 데이터 유형 |용도 |
|---------|---------|---------|---------|
|TicketID |`Edm.Guid` |기본 키 |엔터티에 대한 기본 키 |
|제목  |`Edm.String` |한 줄 텍스트 |티켓의 제목 |
|심각도 |`Edm.Int32`| 정수 |티켓의 심각도를 나타내는 0~4의 숫자 값 |

외부 데이터 원본 티켓 엔터티의 OData 메타데이터입니다.

```xml
<EntityType Name="Ticket">
  <Key>
    <PropertyRef Name="TicketID" />
  </Key>
  <Property Name="TicketID" Nullable="false" Type="Edm.Guid" />
  <Property Name="Title" Type="Edm.String" />
  <Property Name="Severity" Nullable="false" Type="Edm.Int32" />
</EntityType>
```

## <a name="create-the-data-source"></a>데이터 원본 만들기

OASIS 개방형 데이터 프로토콜(OData) 샘플 웹 서비스를 사용하는 OData v4 데이터 공급자에 대한 데이터 원본을 만듭니다.

1. **설정** > **관리** > **가상 엔터티 데이터 원본**으로 이동합니다.
1. **새로 만들기**를 선택하고 **OData v4 데이터 공급자**를 선택한 다음 **확인**을 선택합니다.
1. 다음 정보를 입력하거나 선택합니다.

    |필드|값|
    |--|--|
    |**이름**|Contoso 예제 데이터 원본|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**시간 제한**|30|
    |**인라인 개수 반환**|True|

다른 필드를 그대로 두고 **저장 및 닫기**를 선택합니다.

> [!TIP]
> 자체 웹 서비스를 사용하는 경우 URL을 웹 브라우저에 붙여 넣어 유효한지 확인합니다. 

## <a name="open-solution-explorer"></a>솔루션 탐색기를 엽니다.

만든 사용자 지정 엔터티의 이름 일부는 사용자 지정 접두사입니다. 이 값은 작업 중인 솔루션의 솔루션 게시자에 따라 설정됩니다. 사용자 지정 접두사에 대해 관심이 있을 경우 이 엔터티에 사용할 접두사가 사용자 지정 접두사인 비관리형 솔루션에서 작업하고 있는지 확인하십시오. 추가 정보: [솔루션 게시자 접두사 변경](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>가상 엔터티 만들기

1. 솔루션 탐색기의 왼쪽 탐색 창에서 **엔터티**를 선택한 다음 기본 창에서 **새로 만들기**를 선택합니다.
2. **엔터티: 새로 만들기** 양식에서 **가상 엔터티** 옵션을 선택하고 다음 정보를 입력합니다. 

    |필드|값|
    |--|--|
    |**데이터 원본**|Contoso 예제 데이터 원본|
    |**표시 이름**|티켓|
    |**복수 이름**|티켓|
    |**이름**|new_ticket|
    |**외부 이름**|티켓|
    |**외부 컬렉션 이름**|티켓|
    |**메모(첨부 파일 포함)**|선택됨|
    |**활동**|선택됨|

1. **이 엔터티가 표시되는 영역** 옆에서 **서비스**를 선택하고 **저장**을 선택하지만 엔터티 양식을 닫지 않습니다.
    ![티켓 엔터티 정의](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>가상 엔터티에 대한 필드 만들기

**엔터티: 티켓** 페이지의 왼쪽 탐색 창에서 **필드**를 선택합니다. 이 연습의 일부로 두 개의 기존 필드를 편집하고 세 번째 필드를 추가하겠습니다.

> [!IMPORTANT]
> 외부 이름은 대/소문자를 구분합니다. 올바른 이름을 사용 하는지 확인하려면 웹 서비스 메타데이터를 참조하십시오.
> null을 허용하는 false 값은 특성이 필요함을 나타냅니다. 기본 키 필드는 항상 시스템에 필요한 것을 알 수 있습니다.

1. **new_ticketid** 필드를 열고 다음 특성을 **외부 이름**: TicketID  ![TicketID 필드](media/ticketid-field.png)에 표시된 값으로 변경합니다.
1. **저장 후 닫기**를 선택합니다.
1. **new_name** 필드를 열고 다음 특성을 여기에 표시된 값을 가지도록 변경합니다.
    - **표시 이름**: 제목
    - **외부 이름**: 제목 ![제목 필드](media/title-field.png)
1. **저장 후 닫기**를 선택합니다.
1. **새로 만들기**를 선택하고 **필드: 티켓에 대해 새로 만들기** 페이지에서 다음 정보를 입력합니다.

    |필드|값|
    |--|--|
    |**표시 이름**|심각도|
    |**이름**|new_severity|
    |**외부 이름**|심각도|
    |**필드 필요**|업무상 필수|
    |**데이터 형식**|정수|
    |**최소값**|0|
    |**최대값**|4|

  ![심각도 필드](media/severity-field.png)
1. **저장 후 닫기**를 선택합니다.

## <a name="add-the-fields-to-the-main-form"></a>기본 양식에 필드 추가

1. 티켓 엔터티 창에서 **양식**을 선택합니다.
1. 기본 양식을 열고 오른쪽 창에서 **심각도** 필드를 **제목** 필드 아래의 **일반** 섹션에 있는 양식으로 끌어다 놓습니다. 
    ![기본 양식에 추가된 심각도 필드](media/drop-severity-field.png)
1. 티켓 엔터티 창에서 **저장 후 닫기**를 선택합니다.

## <a name="configure-the-default-view"></a>기본 보기 구성

1. 솔루션 탐색기의 왼쪽 창에 있는 **티켓 엔터티** 아래에서 **보기**를 선택합니다.
1. **모든 티켓** 보기를 엽니다.
1. **일반 작업** 창에서 **열 추가**를 선택합니다.
    ![보기에 대한 열 추가](media/addcolumns.png)
1. **심각도**를 선택하고 **확인**을 선택합니다.
1. **보기: 모든 티켓** 창에서 **저장 후 닫기**를 선택합니다.
1. 솔루션 탐색기 창에서 **모든 사용자 지정 항목 게시**를 선택합니다.
    ![모든 사용자 지정 항목 게시](media/publishall.png)
1. 모든 사용자 지정 항목을 게시한 후 솔루션 탐색기 창을 닫습니다.

## <a name="view-the-virtual-entity-in-action-with-dynamics-365"></a>Dynamics 365를 통한 실제 가상 엔터티 보기

1. **서비스** > **확장** > **티켓**으로 이동합니다.
    
    ![티켓 영역](media/ticket-area.png)

    **모든 티켓** 보기가 표시됩니다. **서비스** 영역에서 엔터티를 보려면 브라우저를 새로 고쳐야 할 수 있습니다.

    ![모든 티켓 보기](media/all-tickets-view.png)
1. 지정된 레코드에 대한 **제목** 및 **심각도** 필드를 포함하는 양식을 보려면 **티켓** 레코드를 엽니다.
    ![티켓 레코드](media/ticket-record.png)

### <a name="see-also"></a>참고 항목

[OData v4 데이터 공급자 구성, 요구 사항 및 모범 사례](virtual-entity-odata-provider-requirements.md)<br />
[외부 데이터 원본에서 데이터를 포함하는 가상 엔터티 만들기 및 편집](create-edit-virtual-entities.md)
