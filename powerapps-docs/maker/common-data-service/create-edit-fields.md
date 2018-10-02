---
title: 앱용 Common Data Service의 필드를 만들고 편집하는 방법| MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: d88677fa-2caf-47b0-aec6-10a25a7ec9c3
caps.latest.revision: 55
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="how-to-create-and-edit-fields"></a>필드를 만들고 편집하는 방법

앱용 Common Data Service에서 필드는 엔터티에 데이터를 저장하는 데 사용할 수 있는 개별 데이터 항목을 정의합니다. 필드는 개발자에 의해 *특성*이라고도 합니다. 
  
사용자 지정 필드를 만들려면 먼저 기존 필드를 사용하여 요구 사항을 충족하는지 평가합니다. 추가 정보: [새 메타데이터를 만들거나 기존 메타데이터를 사용하시겠습니까?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

필드를 만들거나 편집하는 데 사용할 수 있는 디자이너는 두 가지가 있습니다.

|디자이너| 설명|
|--|--|
|[PowerApps 포털](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|쉽게 간소화된 환경을 제공하지만 일부 특수 설정은 사용할 수 없습니다.<br />추가 정보: [PowerApps 포털을 사용하여 앱용 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-portal.md)|
|솔루션 탐색기|쉽지 않지만 덜 일반적인 요구 사항에 대한 더 많은 유연성을 제공합니다.<br />추가 정보: [PowerApps 솔루션 탐색기를 사용하여 앱용 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md) |

> [!NOTE]
> 다음을 사용하여 환경에서 필드를 만들 수도 있습니다.
> - 모델 기반 앱의 경우 양식 편집기에서 **새 필드**를 선택합니다.
> - 필드의 정의가 포함된 솔루션을 가져옵니다.
> - 파워 쿼리를 사용하여 새 엔터티를 만들고 데이터로 채웁니다.<br />추가 정보: [파워 쿼리를 사용하여 Common Data Service의 엔터티에 데이터 추가](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - 개발자는 [메타데이터 서비스 ](/powerapps/developer/common-data-service/use-web-services#metadata-services)를 사용하여 필드를 만들고 업데이트하는 프로그램을 작성할 수 있습니다.

이 항목의 정보는 사용할 수 있는 디자이너를 선택하는 데 도움이 됩니다. 

다음 요구 사항 중 하나를 해결해야 하는 경우 PowerApps 포털을 사용하여 Common Data Service에 대한 필드를 만들고 편집해야 합니다.

- 고객 조회 필드 만들기
- CDS 기본 솔루션 이외의 솔루션에 필드 만들기
- 상태 설명 전환 정의
- 한 번에 여러 필드 편집
- 감사 사용
- 활성화 필드 수준 보안
- 상호 작용 환경의 전역 필터에 필드가 표시되는지 선택합니다.
- 대화형 환경 대시보드에서 필드를 정렬할 것인지 선택합니다.
- 업무상 권장되는 필드 요구 사항 수준 설정
- 필드를 위한 관리 속성 설정

> [!NOTE]
> 엔터티에 대한 일대다 관계를 만들어 PowerApps 포털 또는 솔루션 탐색기에서 조회 필드를 만들 수 있습니다. 그러나 솔루션 탐색기만 필드를 만드는 동안 관계를 만드는 옵션을 제공합니다.

## <a name="community-tools"></a>커뮤니티 도구

**[특성 번역기](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** 는 XrmToolBox 커뮤니티가 앱용 CDS를 위해 개발한 도구입니다. 커뮤니티 개발 도구에 대한 자세한 내용은 [개발자 도구](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) 항목을 참조하십시오.

> [!NOTE]
> 커뮤니티 도구는 Microsoft의 제품이 아니며 커뮤니티 도구에 대해 지원을 확장하지 않습니다. 도구와 관련된 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com)

### <a name="see-also"></a>참조  
[PowerApps 포털을 사용하여 앱용 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-portal.md)<br />
[PowerApps 솔루션 탐색기를 사용하여 앱용 Common Data Service에 대한 필드 만들기 및 편집](create-edit-field-solution-explorer.md)<br />
[필드 유형 및 필드 데이터 형식](types-of-fields.md)<br />
[개발자 설명서: 속성 메타데이터 작업](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
