---
title: Common Data Service에서 가상 엔터티 OData v4 데이터 공급자 사용 | MicrosoftDocs
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
ms.assetid: null
caps.latest.revision: null
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="odata-v4-data-provider-configuration-requirements-and-best-practices"></a>OData v4 데이터 공급자 구성, 요구 사항 및 모범 사례

이 항목에서는 OData v4 데이터 공급자를 설정하는 방법과 OData v4 웹 서비스에 연결하기 위해 OData v4 데이터 공급자를 사용하는 요구 사항 및 권장되는 최선의 방법에 대해 설명합니다. 

## <a name="odata-v4-data-provider-best-practices"></a>OData v4 데이터 공급자 모범 사례

- Common Data Service에서 모든 엔터티는 ID 특성을 지녀야 하며 이 ID는 고유 식별자로 알려져 있으며 값은 guid여야 합니다.  `Edm.Guid` 데이터 형식의 외부 필드에만 ID 필드를 매핑할 수 있습니다.  Common Data Service에서 고유 식별자 데이터 형식 필드에 `Edm.Int32` 데이터 형식을 매핑할 수 없습니다.
-  null이 허용되는 속성의 OData 엔터티는 가상 엔터티의 매핑된 필드와 일치하도록 설정해야 합니다. 예를 들어 Nullable=False인 OData 엔터티 속성은 Common Data Service **필드 요구 사항** 특성에서 **업무상 필수**로 설정된 매핑된 필드가 있어야 합니다. 
- 표에 데이터를 로드할 때와 같이 여러 쿼리를 검색하려면 선택 및 필터 쿼리 매개 변수를 사용하여 외부 데이터 원본에서 반환되는 데이터 집합의 크기를 제어합니다.
- 아직 활성화하지 않았으면 시스템 관리자가 플러그 인 추적을 사용하도록 설정해야 합니다. 활성화되면 OData 끝점의 모든 오류가 플러그 인 추적 로그에 캡처됩니다. 추가 정보:  [관리자 가이드: 시스템 설정 대화 상자 - 사용자 지정 탭](/dynamics365/customer-engagement/admin/system-settings-dialog-box-customization-tab) 

## <a name="data-type-mapping"></a>데이터 형식 매핑

다음 표에는 Common Data Service 데이터 형식이 포함된 OData 엔터티 데이터 모델(EDM) 데이터 형식 매핑을 나열합니다. 

|OData 데이터 형식|Common Data Service 데이터 형식  |
|---------|---------|
|`Edm.Boolean`|두 개의 옵션|
|`Edm.DateTime`|날짜 및 시간|
|`Edm.DateTimeOffset`|날짜 및 시간|
|`Edm.Decimal`|10진수 또는 통화|
|`Edm.Double`|부동 소수점 수|
|`Edm.Guid`|고유 식별자|
|`Edm.Int32`|정수|
|`Edm.Int64`|정수|
|`Edm.String`|한 줄 텍스트 또는 여러 줄 텍스트|


### <a name="odata-edm-data-types-that-are-not-supported-for-mapping-with-virtual-entities"></a>가상 엔터티와의 매핑에 지원되지 않는 OData EDM 데이터 형식 

- `Edm.Binary`
- `Edm.Time` 
- `Edm.Float`
- `Edm.Single` 
- `Edm.Int16` 
- `Edm.Byte` 
- `Edm.SByte`

 
## <a name="add-a-data-source-using-the-odata-v4-data-provider"></a>OData v4 데이터 공급자를 사용하여 데이터 원본 추가

이 절차에서는 가상 엔터티 데이터 원본으로 사용하기 위해 기본 제공 OData 데이터 공급자를 사용하는 방법을 보여 줍니다.   
  
1. **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **관리** > **가상 엔터티 데이터 원본**으로 이동합니다.  
1. 작업에서 **새로 만들기**를 클릭합니다.  
1. **데이터 공급자 선택** 대화 상자에서 다음 데이터 원본에서 선택하고 **확인**을 클릭합니다.  
  
    - **OData v4 데이터 공급자**. Common Data Service은 OData v4 개방형 표준을 지원하는 데이터 원본에 연결하는 데 사용할 수 있는 OData v4 데이터 공급자를 포함합니다.  
    - *사용자 지정 데이터 공급자*. 데이터 공급자 플러그 인을 가져온 경우 데이터 공급자가 여기에 표시됩니다. 추가 정보:  [개발자 설명서: 가상 엔터티 시작](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)  
    
1. **새 데이터 원본** 속성 페이지에서 다음 필드를 입력한 다음 레코드를 저장합니다.  
  
    - **이름**: 데이터 원본을 설명하는 이름을 입력합니다.  
    - **URI**. OData 데이터 공급자를 사용하는 경우 OData 웹 서비스에 대한 URI를 입력합니다. 예를 들어 OData 공급자를 사용하여 Azure에서 호스팅되는 웹 서비스에 연결하는 경우 URI는 *`http://contosodataservice.azurewebsites.net/odata/`* 와 비슷하게 보일 수 있습니다.  
    - **시간 제한(초)**. 데이터 요청 제한 시간 이전에 웹 서비스의 응답을 기다리는 시간(초)을 입력 합니다. 예를 들어, 30을 입력하면 제한 시간이 발생하기 전에 최대 30초를 기다립니다.  
    - **페이지 매김 모드**. 쿼리 결과가 페이징되는 방식을 제어하기 위해 클라이언트 측 또는 서버 측 페이징을 사용할지 여부를 선택합니다. 기본값은 클라이언트 측 페이징입니다. 서버 쪽 페이징과 함께 서버는 쿼리 문자열에 추가되는 $skiptoken 매개 변수를 사용하여 결과를 페이징하는 방법을 제어합니다. 추가 정보:  [토큰 시스템 쿼리 건너뛰기 옵션($skiptoken)](https://msdn.microsoft.com/library/dd942121.aspx)  
        -  **인라인 개수 반환**. 결과 집합의 총 레코드 수를 반환합니다. 이 설정은 표에 데이터를 반환할 때 다음 페이지 기능을 사용하도록 설정하는 데 사용됩니다. OData 끝점이 OData $inclinecount 매개 변수를 지원하지 않으면 false 값을 사용합니다. 기본값은 false입니다.
    - **요청 매개 변수**. 필요에 따라 외부 서비스에 인증 매개 변수와 같이 OData 웹 서비스에 연결하는 데 사용되는 사용자 지정 머리글 또는 쿼리 문자열 매개 변수를 추가할 수 있습니다. **쿼리 문자열**을 클릭하여 머리글 및 쿼리 문자열 매개 변수 및 값을 전환합니다. 최대 10개의 머리글 또는 쿼리 문자열을 추가할 수 있습니다. 
        > [!div class="mx-imgBorder"] 
        > ![가상 엔터티 데이터 원본 레코드](media/virtual-entity-data-source.png) 


## <a name="see-also"></a>참조  

[외부 데이터 원본에서 데이터를 포함하는 가상 엔터티 만들기 및 편집](create-edit-virtual-entities.md) <br/>
[TechNet 블로그: 새 가상 엔터티를 사용하여 외부 시스템의 데이터와 상호 작용](https://blogs.technet.microsoft.com/lystavlen/2017/09/08/virtual-entities/)
