---
title: 포털과 Power BI 통합 설정 | MicrosoftDocs
description: 포털과 Power BI 통합을 설정하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="set-up-power-bi-integration"></a>Power BI 통합 설정

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Power BI는 간단한 대화형 시각화로 통찰력을 제공하는 최상의 도구 중 하나입니다. 포털의 웹 페이지에 있는 Power BI에서 대시보드 및 보고서를 보려면 포털 관리 센터에서 Power BI 시각화를 사용하도록 설정해야 합니다. Power BI Embedded 서비스 통합을 활성화하여 Power BI의 새 작업 영역에서 만든 대시보드 및 보고서를 포함할 수도 있습니다.

> [!NOTE]
> - 적절한 Power BI 라이선스가 있어야 합니다.
> - Power BI Embedded 서비스를 사용하려면 적절한 Power BI Embedded 라이선스가 있어야 합니다. 자세한 내용은 [라이선싱](https://docs.microsoft.com/en-us/power-bi/developer/embedded-faq#licensing)을 참조하십시오.

## <a name="enable-power-bi-visualization"></a>Power BI 시각화 사용

Power BI 시각화를 사용하면 powerbi 유동 태그를 통해 포털의 웹 페이지에 대시보드와 보고서를 포함할 수 있습니다.

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI 통합 설정** > **Power BI 시각화 사용**으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 시각화 사용](../media/enable-power-bi-visualization.png "Power BI 시각화 사용")

3.  확인 메시지에서 **사용**을 클릭합니다. Power BI 시각화를 활성화하는 동안 포털을 다시 시작하고 몇 분 동안 사용할 수 없습니다. Power BI 시각화가 활성화되면 메시지가 나타납니다.

사용자 지정자는 [powerbi](../liquid/portals-entity-tags.md#powerbi) 유동 태그를 사용하여 포털의 웹 페이지에 Power BI 대시보드 및 보고서를 포함할 수 있습니다. 사용자 지정자는 Power BI 콘텐츠를 포함하는 동안 [필터 매개 변수](https://docs.microsoft.com/en-us/power-bi/service-url-filters)를 사용하여 개인화된 보기를 만들 수 있습니다. 추가 정보: [powerbi 유동 태그](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Power BI 시각화 사용 안 함

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI 통합 설정** > **Power BI 시각화 사용 안 함**으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 시각화 사용 안 함](../media/disable-power-bi-visualization.png "Power BI 시각화 사용 안 함")

3. 확인 메시지에서 **사용 안 함**을 클릭합니다. Power BI 시각화를 비활성화하는 동안 포털을 다시 시작하고 몇 분 동안 사용할 수 없습니다. Power BI 시각화가 비활성화되면 메시지가 나타납니다.

## <a name="enable-power-bi-embedded-service"></a>Power BI Embedded 서비스 활성화

Power BI Embedded 서비스를 활성화하면 Power BI의 새 작업 영역에서 만든 대시보드 및 보고서를 포함할 수도 있습니다. 대시보드 및 보고서는 powerbi 유동 태그를 사용하여 포털의 웹 페이지에 포함됩니다.

**전제 조건**: Power BI Embedded 서비스를 사용하도록 설정하기 전에 Power BI의 새 작업 영역에서 대시보드 및 보고서를 만들었는지 확인합니다. 작업 영역을 만든 후에는 전역 관리자에게 관리자 액세스 권한을 제공하여 작업 영역이 포털 관리 센터에 표시되도록 합니다. 새 작업 영역을 만들고 액세스 권한을 추가하는 방법에 대한 자세한 내용은 [Power BI에서 새 작업 영역 만들기(미리 보기)](https://docs.microsoft.com/en-us/power-bi/service-create-the-new-workspaces)를 참조하십시오.

**Power BI Embedded 서비스 제한 사항**: 제한 사항에 대한 자세한 내용은 [고려 사항 및 제한 사항](https://docs.microsoft.com/en-us/power-bi/developer/embed-service-principal#considerations-and-limitations)을 참조하십시오.

> [!NOTE]
> Powerbi 유동 태그가 작동하도록 Power BI 시각화가 사용되도록 설정되어 있는지 확인합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **Power BI 통합 설정** > **Power BI Embedded 서비스(미리 보기) 사용**으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 사용](../media/enable-powerbi-embedded-button.png "Power BI Embedded 서비스 사용")

3. **Power BI Embedded 서비스 통합 사용** 창에서 포털에 표시해야 하는 대시보드 및 보고서가 있는 Power BI 작업 영역을 선택하여 **선택한 작업 영역** 목록으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 작업 영역 선택](../media/enable-powerbi-embedded-window.png "Power BI 작업 영역 선택")
    
    > [!NOTE]
    > **선택한 작업 영역** 목록에 작업 영역을 추가한 후 몇 분 후에 데이터베이스와 보고서가 렌더링됩니다.
    

4. **사용**을 선택합니다. Power BI Embedded 서비스를 활성화하는 동안 포털이 다시 시작되고 몇 분 동안 사용할 수 없습니다. Power BI Embedded 서비스가 활성화되면 메시지가 나타납니다.

이제 보안 그룹을 만들고 이를 Power BI 계정에 추가해야 합니다. 자세한 내용은 [보안 그룹 만들기 및 Power BI 계정에 추가](#create-security-group-and-add-to-power-bi-account)를 참조하십시오.

### <a name="create-security-group-and-add-to-power-bi-account"></a>보안 그룹 만들기 및 Power BI 계정에 추가

Power BI Embedded 서비스 통합을 사용하도록 설정한 후에는 Azure Active Directory에 보안 그룹을 만들고 구성원을 추가하고 Power BI 관리 포털을 통해 Power BI에 보안 그룹을 추가해야 합니다. 이렇게 하면 새 Power BI 작업 영역에서 만든 대시보드 및 보고서를 포털에 표시할 수 있습니다.

> [!NOTE]
> Power BI Embedded 서비스를 사용하도록 설정하는 데 사용한 것과 동일한 전역 관리자 계정으로 로그인해야 합니다.

**1단계: 보안 그룹 만들기**

1. 디렉터리에 대 한 전역 관리자 계정을 사용하여 [Azure 포털](https://portal.azure.com)에 로그인합니다.

2. **Azure Active Directory**, **그룹**을 선택한 다음 **새 그룹**을 선택합니다.

3. **그룹** 페이지에서 다음을 정보를 입력합니다.

    - **그룹 유형**: 보안.

    - **그룹 이름**: 포털 Power BI Embedded서비스.

    - **그룹 설명**: 이 보안 그룹은 포털 및 Power BI Embedded 서비스 통합에 사용됩니다.

    - **멤버십 유형**: 할당됨.

      > [!div class=mx-imgBorder]
      > ![Power BI Embedded 서비스에 대한 보안 그룹 만들기](../media/powerbi-embed-security-group.png "Power BI Embedded 서비스에 대한 보안 그룹 만들기")

4. **만들기**를 선택합니다.

**2단계: 그룹 구성원 추가**

**전제 조건**: 보안 그룹에 구성원을 추가하기 전에 포털의 응용 프로그램 ID가 있어야 합니다. 포털의 응용 프로그램 ID는 [PowerApps 포털 관리 센터](admin-overview.md)의 **포털 세부 정보** 탭에서 사용할 수 있습니다.

1. 디렉터리에 대 한 전역 관리자 계정을 사용하여 [Azure 포털](https://portal.azure.com)에 로그인합니다.

2. **Azure Active Directory**을 선택하고 **그룹**을 선택합니다.

3. **그룹 - 모든 그룹** 페이지에서 **포털 Power BI Embedded 서비스** 그룹을 검색하고 선택합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스에 대한 보안 그룹 검색 및 선택](../media/search-security-group.png "Power BI Embedded 서비스에 대한 보안 그룹 검색 및 선택")

4. **포털 Power BI Embedded 서비스 개요** 페이지의 **관리** 영역에서 **구성원**을 선택합니다.

5. **구성원 추가**를 선택하고 텍스트 상자에 포털의 응용 프로그램 ID를 입력합니다.

6. 검색 결과에서 구성원을 선택한 다음 **선택**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스에 대한 보안 그룹에서 구성원 추가](../media/add-member-powerbi-embed.png "Power BI Embedded 서비스에 대한 보안 그룹에서 구성원 추가")

**3단계: Power BI 설정**

1. 디렉터리에 대한 전역 관리자 계정을 사용하여 [Power BI](https://powerbi.microsoft.com)에 로그인합니다.

2. Power BI 서비스의 오른쪽 위에 있는 **설정**을 선택하고 **관리 포털**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 서비스에서 관리 포털 선택](../media/select-admin-portal.png "Power BI 서비스에서 관리 포털 선택")

3. **테넌트 설정**을 선택합니다.

4. **개발자 설정** 섹션에서 **서비스 주체가 Power BI API를 사용하도록 허용**을 선택합니다.

5. **특정 보안 그룹** 필드에서 **포털 Power BI Embedded 서비스** 그룹을 검색하고 선택합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 관리 포털에서 보안 그룹 추가](../media/add-sg-powerbi.png "Power BI 관리 포털에서 보안 그룹 추가")

6. **적용**을 선택합니다.

사용자 지정자는 이제 [powerbi](../liquid/portals-entity-tags.md#powerbi) 유동 태그를 사용하여 포털의 웹 페이지에 새로운 Power BI 작업 영역의 Power BI 대시보드 및 보고서를 포함할 수 있습니다. Power BI Embedded 서비스를 사용하려면 인증 유형을 **powerbiembedded**로 지정해야 합니다. 사용자 지정자는 Power BI 콘텐츠를 포함하는 동안 [필터 매개 변수](https://docs.microsoft.com/en-us/power-bi/service-url-filters)를 사용하여 개인화된 보기를 만들 수 있습니다. 추가 정보: [powerbi 유동 태그](../liquid/portals-entity-tags.md#powerbi).

### <a name="manage-the-power-bi-embedded-service"></a>Power BI Embedded 서비스 관리

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **Power BI 통합 설정** > **Power BI Embedded 서비스(미리 보기) 관리**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 관리](../media/manage-powerbi-embedded-button.png "Power BI Embedded 서비스 관리")

3. **Power BI Embedded 서비스 통합 관리** 창에서 포털에 표시해야 하는 대시보드 및 보고서가 있는 Power BI 작업 영역을 제거하거나 **선택한 작업 영역** 목록으로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 작업 영역 선택](../media/manage-powerbi-embedded-window.png "Power BI 작업 영역 선택")
    
    > [!NOTE]
    > **선택한 작업 영역** 목록에서 작업 영역을 제거한 후 변경 내용을 반영하는 데 최대 1시간이 걸릴 수 있습니다. 그 때까지 데이터베이스와 보고서는 문제 없이 포털에서 렌더링됩니다.

4. **저장**을 선택합니다.

### <a name="disable-the-power-bi-embedded-service"></a>Power BI Embedded 서비스 사용 안 함

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI 통합 설정** > **Power BI Embedded 서비스(미리 보기) 관리**로 이동합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 관리](../media/manage-powerbi-embedded-button.png "Power BI Embedded 서비스 관리")

3. **Power BI Embedded 서비스 통합 관리** 창에서 **Power BI Embedded 서비스 통합 사용 안 함**을 선택합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 사용 안 함](../media/disable-powerbi-embedded-window.png "Power BI Embedded 서비스 사용 안 함")

4. **저장**을 선택합니다.

5. 확인 메시지에서 **확인**을 선택합니다. Power BI Embedded 서비스를 비활성화하는 동안 포털이 다시 시작되고 몇 분 동안 사용할 수 없습니다. Power BI Embedded 서비스가 비활성화되면 메시지가 나타납니다.

## <a name="privacy-notice"></a>개인 정보 취급 방침  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>참조

[powerbi 유동 태그](../liquid/portals-entity-tags.md#powerbi)<br> 
[포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가](add-powerbi-report.md)
