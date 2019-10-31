---
title: 엔터티의 기본 양식에 문서 탭 추가 | MicrosoftDocs
description: 엔터티의 기본 양식에 문서 탭을 추가하는 방법 알아보기
s.custom: null
ms.date: 09/05/2019
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
search.audienceType:
  - customizer
search.app:
  - D365CE
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>엔터티의 기본 양식에 SharePoint 문서 탭 추가
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

엔터티 기본 양식에 탭을 추가하여 SharePoint 문서를 표시하면 사용자가 모델 기반 앱에서 사용 가능한 SharePoint 통합 기능을 찾고 사용할 수 있습니다. 

![문서 파일 탭](media/document-files-tab.png)

> [!IMPORTANT]
> 이 기능을 사용하려면 문서 관리를 사용해야 합니다. 추가 정보: [SharePoint를 사용하여 문서 관리](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>FormXML에 문서 탭 추가 
1.  새 솔루션을 만듭니다. PowerApps에 로그인하고 **솔루션**으로 이동하여 **새 솔루션**을 선택하고 필수 및 선택적 정보를 입력하십시오. 추가 정보: [솔루션 만들기](../common-data-service/create-solution.md)
2. 기본 양식의 문서 탭을 추가할 솔루션에 엔터티를 추가하십시오. 모든 표준 및 사용자 지정 엔터티가 지원됩니다. 추가 정보: [솔루션에 기존 구성 요소 추가](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. 거래처 엔터티의 기본 양식과 같이 솔루션에 엔터티의 양식을 포함시킵니다. 엔터티 옆에서 **...** 를 선택한 다음 **편집**을 선택합니다. **양식** 탭을 선택합니다. 원하는 양식이 없으면 추가하십시오.   

4. 기본 양식에 1열 탭을 추가합니다. 이렇게 하려면 양식 디자이너에서 양식 캔버스의 영역을 선택하고 **구성 요소 추가**를 선택한 다음 **1열 탭**을 선택합니다.  
   ![1열 탭 삽입](media/insert-one-column-tab.png)

5. 양식 디자이너에서 양식 디자이너 캔버스의 **새 탭**을 선택하고 **필드 추가**를 선택한 다음 왼쪽 창에서 *주소 1: 도시* 같은 필드를 추가하십시오. 탭에 텍스트 또는 숫자 필드를 사용할 수 있습니다. ![탭에 필드 추가](media/add-field-to-tab.png)
6. 탭 레이블의 이름을 변경합니다. 이렇게 하려면 **새 탭**을 선택하고 오른쪽 속성 창에서 **새 탭**의 이름을 *파일*과 같이 더 잘 설명하는 이름으로 바꿉니다.
7. **저장**을 선택하고 **게시**를 선택한 다음 양식 디자이너를 닫습니다. 
8. PowerApps 제조업체 홈 페이지에서 **솔루션**을 선택하고, 해당 솔루션을 선택하고, **내보내기**를 선택하여 관리되지 않는 솔루션으로 솔루션을 내보냅니다. 추가 정보: [솔루션 내보내기](../common-data-service/import-update-export-solutions.md#export-solutions) 
9. 솔루션을 추출하고 XML 또는 텍스트 편집기로 customization.xml 파일을 여십시오. 
10. customization.xml에서 **label description = "파일"**(또는 이전 단계에서 지정한 탭 레이블의 이름).
11. **control id="address1_city"** 와 같이 control id="*field name*" 요소로 스크롤을 내려 전체 요소를 이 항목의 [XML 샘플](#xml-sample-for-adding-the-documents-tab-to-a-form)로 교체합니다. 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML 샘플 삽입 지점")

12. XML 샘플을 수정하십시오. 
    
     a. **RelationshipName** 요소를 찾아 *entityLogicalName*_SharePointDocument로 표시되는 스키마 이름으로 바꾸십시오. 예를 들어, 거래처 엔터티의 경우 관계에 대한 스키마 이름은 Account_SharePointDocument이며 이 항목의 XML 샘플에 대한 스키마 이름입니다. 다른 엔터티의 이름을 찾으려면 **설정** > **사용자 지정** > **시스템 사용자 지정** > **엔터티**로 이동하여 엔터티를 선택하고 **1:N 관계**를 선택합니다. **SharePointDocument** 유형의 **관련 엔터티**를 찾습니다. 

      ![거래처 관계 SharePoint 문서](media/account-sharepointdocument.png)

     b. GUID(Globally Unique Identifier)를 만들고 기존 **uniqueid** guid를 이전 단계에서 붙여 넣은 **control** 요소를 교체합니다. 단, 중괄호 {}는 유지합니다.  
       ![컨트롤 요소 고유 ID](media/control-unique-id.png). 변경 내용을 customizations.xml에 저장합니다. 
13. solution.xml 파일을 열고 **버전** 요소 값을 늘립니다. 예를 들어 *1.1.0.0*에서 *1.2.0.0*로 늘립니다. 
14. 모든 솔루션 파일을 압축(Zip) 폴더로 패키지하고 환경으로 가져오십시오. 이전 솔루션을 삭제해야 한다는 오류가 발생하면 삭제하십시오. 추가 정보: [솔루션 가져오기, 업데이트 및 업그레이드](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>문서 탭을 양식에 추가하기 위한 XML 샘플
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>참조
[SharePoint를 사용하여 문서 관리](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)