---
title: PowerApps의 모델 기반 앱 사용자 지정 엔터티 아이콘 변경 | MicrosoftDocs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="change-model-driven-app-custom-entity-icons"></a>모델 기반 앱 사용자 지정 엔터티 아이콘 변경 

사용자 지정 엔터티를 만들면 자동으로 기본 아이콘이 할당됩니다. 모든 사용자 지정 엔터티는 기본적으로 동일한 아이콘을 사용합니다. 사용자 지정 아이콘을 사용하여 사용자 지정 엔터티의 모양을 구분할 수 있습니다. 시스템 엔터티에 할당된 아이콘은 수정할 수 없습니다.  
  
 각 사용자 지정 엔터티에 세 가지 유형의 엔터티 아이콘을 업로드할 수 있습니다. 

|아이콘 유형  |설명  |
|---------|---------|
|**통합 인터페이스 아이콘**|확장 가능한 벡터 그래픽(.svg) 아이콘이어야 합니다. |
|**웹 응용 프로그램의 아이콘**|크기가 16x16 픽셀인 .svg, .gif, .png 또는 .jpg 형식 이미지입니다.|
|**엔터티 양식의 아이콘**|크기가 32x32 픽셀인 .svg, .gif, .png 또는 .jpg 형식 이미지입니다.|

> [!NOTE]
> 모든 이미지 파일의 크기는 10kB 이하여야 합니다.
>
> 확장 가능 벡터 그래픽(.svg) 이미지를 **웹 응용 프로그램 아이콘** 또는 **엔터티 양식에대 한 아이콘**으로 사용하는 경우 기본 크기를 설정해야 합니다. svg는 XML 문서이므로 텍스트 편집기로 [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) 요소 [너비](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) 및 [높이](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) 값을 편집하여 이미지의 기본 크기를 정의할 수 있습니다.

각 아이콘 유형은 웹 리소스로 저장됩니다. 먼저 웹 리소스를 만든 다음 이를 사용 하도록 아이콘을 설정 하거나 값을 설정하는 동안 **새로 만들기**를 선택하여 **조회 레코드** 대화 상자에서 새 웹 리소스를 만들 수 있습니다. 추가 정보: [웹 리소스를 만들거나 편집하여 앱 확장](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>사용자 지정 엔터티의 아이콘을 설정합니다.

엔터티 아이콘을 설정하려면 솔루션 탐색기를 사용해야 합니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>엔터티 아이콘 설정

1. 명령 모음에서 **아이콘 업데이트**를 선택합니다.  
  
2. **새 아이콘 선택** 대화 상자, **웹 클라이언트 탭**의 **웹 응용 프로그램의 아이콘** 또는 **엔터티 양식의 아이콘**에서 **새 아이콘** 오른쪽의 **찾아보기** 단추![조회 단추](media/lookup-button-4.gif)를 선택합니다.
3. 적절한 웹 리소스를 선택하거나 만든 다음 **확인**을 선택합니다. 
4. **통합 인터페이스** 탭에서 **새 아이콘** 필드에 대해 동일한 작업을 수행합니다.
5. **확인**을 클릭하여 **새 아이콘 선택** 대화를 닫습니다.
6. 명령 모음에서 **파일** 메뉴에서 **저장**을 선택합니다.  
7. 변경을 완료했으면 사용자 지정 항목을 게시합니다. 솔루션 탐색기에서 엔터티가 선택된 상태에서 명령 모음에서 **게시**를 선택합니다.
  
## <a name="community-tools"></a>커뮤니티 도구

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** 는 XrmToolbox 커뮤니티가 PowerApps용으로 개발한 도구입니다. 커뮤니티 개발 도구에 대해서는 [Common Data Service용 개발자 도구](/powerapps/developer/common-data-service/developer-tools) 항목을 참조하십시오.

> [!NOTE]
> 커뮤니티 도구는 Microsoft의 제품이 아니며 커뮤니티 도구에 대해 지원을 확장하지 않습니다. 도구와 관련된 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com)

## <a name="next-steps"></a>다음 단계  
[엔터티 만들기](../common-data-service/create-edit-entities.md)<br />
[엔터티 편집](../common-data-service/edit-entities.md)
