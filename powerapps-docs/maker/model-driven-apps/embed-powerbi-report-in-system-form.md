---
title: 모델 기반 시스템 양식에 Power BI 보고서 포함 | MicrosoftDocs
ms.custom: ''
ms.date: 03/05/2019
ms.reviewer: matp
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 1
author: prsi-msft
ms.author: prsi
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-power-bi-report-in-a-model-driven-system-form"></a>모델 기반 시스템 양식에 Power BI 보고서 포함
PowerApps 모델 기반 앱에서 Power BI 보고서를 사용하여 다양한 보고 및 분석을 시스템 양식으로 가져오고 사용자가 더 많은 것을 수행할 수 있도록 권한을 부여할 수 있습니다. 이를 통해 시스템 전체의 데이터를 집계하고 단일 레코드의 컨텍스트에 맞게 조정할 수 있습니다.
 
## <a name="prerequisites"></a>필수 구성 요소
Power BI 콘텐츠를 포함하는 것은 선택적 기능이며 기본적으로 모든 환경에서 비활성화됩니다. Power BI 콘텐츠를 포함하기 전에 이 기능을 활성화해야 합니다. 추가 정보: [조직에서 Power BI 시각화를 활성화합니다](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi?#enable--visualizations-in-the-organization).

이 기능을 사용하려면 솔루션을 내보내고 xml 조각을 추가하도록 수정한 다음 환경으로 다시 가져오는 방법을 수정해야 합니다. 관리형 솔루션을 통해서만 대상 환경에 대한 변경 사항을 가져와야 합니다. 기존 관리형 솔루션에 대한 업데이트 설치 지침은 [솔루션 가져오기, 업데이트 및 내보내기](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions)를 참조십시오.

## <a name="embed-without-contextual-filtering"></a>컨텍스트 필터링 없이 포함
간단히 Power BI 보고서 및 타일을 포함하여 정확히 동일한 보고서를 얻을 수 있습니다. 이는 현재 모델 기반 양식에 컨텍스트를 포함하지 않으므로 엔터티의 모든 레코드에서 동일한 보고서나 타일을 얻게 됩니다. 예를 들어 다음 보고서는 모든 계정의 지리적 위치를 한 번에 보여주며 요약 정보를 표시하는 데 유용합니다.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-unfiltered.png "Embed-powerbi-report-in-system-form-unfiltered")

XML의 `<sections>` 블록 내에 다음 코드 조각을 추가하여 시스템 양식에 Power BI 보고서 및 타일을 호스팅하는 섹션을 포함할 수 있습니다. 그런 다음 대상 환경에서 솔루션을 가져옵니다. 

```xml
<section id="{d411658c-7450-e1e3-bc80-07021a04bcc2}" locklevel="0" showlabel="true" IsUserDefined="0" name="tab_4_section_1" labelwidth="115" columns="1" layout="varwidth" showbar="false">
    <labels>
        <label languagecode="1033" description="Unfiltered Power BI embedding demo"/>
    </labels>
    <rows>
        <row>
            <cell id="{7d18b61c-c588-136c-aee7-03e5e74a09a1}" showlabel="true" rowspan="20" colspan="1" auto="false">
                <labels>
                    <label languagecode="1033" description="Accounts (Parent Account)"/>
                </labels>
                <control id="unfilteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
                    <parameters>
                        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
                        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
                        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
                    </parameters>
                </control>
            </cell>
        </row>
        <row/>
    </rows>
</section>
```
> [!IMPORTANT]
> XML 샘플에 표시된 대로 `classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}"` 컨트롤을 사용해야 합니다.

 이 표는 앞의 예제에 있는 속성을 설명합니다.

|                                                 속성                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIGroupId**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Power BI 작업 영역 Id입니다. 사용자의 기본 작업 영역은 항상 00000000-0000-0000-0000-000000000000입니다. URL을 보면 모든 작업 영역의 Id를 확인할 수 있습니다. https://xyz.powerbi.com/groups/0ddbe381-256d-44bc-93de-34e47f3d9ab4/을 예로 들 수 있습니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               **PowerBIReportId**                                |                             Power BI 보고서 Id입니다. 포함하려는 보고서로 이를 바꿉니다. URL을 보면 모든 보고서의 Id를 확인할 수 있습니다. https://xyz.powerbi.com/groups/me/reports/544c4162-6773-4944-900c-abfd075f6081을 예로 들 수 있습니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                       **TileUrl**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        포함하려는 Power BI 보고서 또는 타일 URL입니다. 올바른 Power BI 인스턴스 이름(msit.powerbi.com을 자신의 것으로 교체) 및 보고서 Id를 사용해야 합니다(reportId=544c4162-6773-4944-900c-abfd075f6081을 자신의 것으로 교체). https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081을 예로 들 수 있습니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

## <a name="embed-with-contextual-filtering"></a>컨텍스트 필터링 포함
현재 모델 기반 양식에 컨텍스트 필터를 적용하여 Power BI 보고서와 타일을 더 의미 있게 만들 수 있으므로 현재 레코드의 특성에 따라 보고서나 타일이 필터링됩니다. 예를 들어 다음 보고서에서는 계정 이름을 사용하여 Power BI 보고서를 필터링하여 계정의 지리적 위치를 보여줍니다. 이렇게 하면 단일 보고서에서 엔터티의 모든 레코드에 대한 컨텍스트 정보를 표시할 수 있습니다.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-filtered.png "Embed-powerbi-report-in-system-form-filtered")

필터링은 여기에 표시된 것처럼 `<parameter>` 블록에 `<PowerBIFilter>` 요소를 추가하여 수행됩니다. 양식 엔터티의 모든 특성을 사용하여 필터 식을 생성할 수 있습니다. 추가 정보: [필터 구성](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters)을 통해 자신의 필터를 만드는 방법을 이해합니다.
    
```xml
<control id="filteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
    <parameters>
        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
        <PowerBIFilter>{"Filter": "[{\"$schema\":\"basic\",\"target\":{\"table\":\"My Active Accounts\",\"column\":\"Account Name\"},\"operator\":\"In\",\"values\":[$a],\"filterType\":1}]", "Alias": {"$a": "name"}}</PowerBIFilter>
    </parameters>
</control>
```

이는 필터링되지 않은 보고서 포함과 동일한 컨트롤을 사용하므로 컨트롤 클래스 id는 변경되지 않습니다. 

이 표는 앞의 예제에 사용된 추가 속성을 설명합니다.

|                                                 속성                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIFilter**                          |        양식 특성을 매개 변수로 전달하여 Power BI 보고서를 컨텍스트화하는 필터 식입니다. 읽기 쉽도록 필터는 다음과 같이 구성됩니다.    |

    {
            "Filter": "[{
                    \"$schema\":\"basic\",
                    \"target\":{
                            \"table\":\"My Active Accounts\",
                            \"column\":\"Account Name\"
                    },
                    \"operator\":\"In\",
                    \"values\":[$a, $b],
                    \"filterType\":1
            }]",
            "Alias": {
                    "$a": "firstname",
                    "$b":"lastname"
            }
    }

이전 식의 대상 부분에서는 필터를 적용할 테이블과 열을 식별합니다. 연산자는 논리를 식별하고 값은 PowerApps 모델 기반 앱에서 전달된 데이터를 식별합니다. 일반적인 방식으로 매개 변수화하려면 값은 별칭으로 구성됩니다. 이전 식에서 거래처의 **firstname** 및 **lastname** 값이 전달되고, 그 중 하나가 Power BI 보고서의 **거래처 이름** 열에서 검색됩니다. **firstname** 및 **lastname**은 해당 값이 여기에 전달되는 거래처 엔터티의 고유 특성 이름입니다. 

[필터 구성](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters)에서 예제를 보고 $schema 및 filterType에 대한 적절한 값을 제공하여 보다 복잡한 필터 식을 만들 수 있습니다. JSON이 올바르게 생성되도록 *\"* 를 사용하여 필터 파트의 모든 리터럴을 이스케이프해야 합니다.

## <a name="known-issues-and-limitations"></a>알려진 문제 및 제한 사항
1. 이 통합은 지원되는 웹 브라우저 및 모바일 장치에서 통합 인터페이스 클라이언트에서만 사용할 수 있습니다.
2. PowerApps 양식 디자이너에서 이 양식을 열면 의미 있는 방식으로 컨트롤을 표시하지 않습니다. 이는 컨트롤이 양식 디자이너 외부에서 사용자 지정되었기 때문입니다.
3. 사용자는 PowerApps 사용자 이름 및 암호를 사용하여 Power BI에 자동으로 인증됩니다. 자격 증명이 일치하는 Power BI 계정이 존재하지 않는 경우 여기에 설명된 대로 로그인 프롬프트가 표시됩니다. 

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-1.png "Embed-powerbi-report-in-system-form-auth-1")

4. Power BI에 로그인하는 데 잘못된 계정을 사용하는 경우 데이터가 표시되지 않습니다. 올바른 자격 증명으로 로그인하려면 로그아웃한 다음 다시 로그인합니다.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-2.png "Embed-powerbi-report-in-system-form-auth-2")

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-3.png "Embed-powerbi-report-in-system-form-auth-3")

5. PowerApps 내에 표시되는 보고서 데이터의 보기는 Power BI에서와 동일하며 PowerApps 보안 역할 및 권한은 표시되는 데이터에 영향을 주지 않습니다. 따라서 데이터는 Power BI 데이터 집합의 작성자가 보는 것과 본질적으로 동일합니다. PowerApps 보안 역할 및 팀과 유사한 데이터 액세스 제한을 적용하려면 [RLS(행 수준 보안)를 Power BI와 함께 사용합니다](https://docs.microsoft.com/power-bi/service-admin-rls).
6. 솔루션을 가져오고 사용자 지정 항목을 게시한 후 양식에 Power BI 보고서가 표시되지 않는 경우 모델 기반 양식 편집기에서 보고서를 열고 저장하여 양식 JSON이 다시 생성되도록 합니다.


### <a name="see-also"></a>참조

[PowerApps 모델 기반 개인 대시보드에 Power BI 대시보드 포함](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard)

[Dynamics 365 for Customer Engagement를 Power BI와 통합](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi)

[솔루션 가져오기, 업데이트 및 내보내기](../common-data-service/import-update-export-solutions.md)
