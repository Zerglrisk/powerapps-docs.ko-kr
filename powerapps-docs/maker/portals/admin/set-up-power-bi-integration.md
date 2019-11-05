---
title: 포털을 사용 하 Power BI 통합 설정 | MicrosoftDocs
description: 포털과 Power BI 통합을 설정 하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6a471dba2f91ca869ad9ba9da46f6e02cb2a643d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543046"
---
# <a name="set-up-power-bi-integration"></a>Power BI 통합 설정

Power BI는 단순 하 고 대화형 시각화를 사용 하 여 통찰력을 제공 하기 위한 최상의 도구 중 하나입니다. 포털에서 웹 페이지의 Power BI에서 대시보드 및 보고서를 보려면 PowerApps 포털 관리 센터에서 Power BI 시각화를 사용 하도록 설정 해야 합니다. Power BI Embedded 서비스 통합을 사용 하도록 설정 하 여 Power BI의 새 작업 영역에서 만든 대시보드 및 보고서를 포함할 수도 있습니다.

> [!NOTE]
> - 적절 한 Power BI 라이선스가 있어야 합니다.
> - Power BI Embedded 서비스를 사용 하려면 적절 한 Power BI Embedded 라이선스가 있어야 합니다. 자세한 내용은 [라이선스](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing)를 참조 하십시오.

## <a name="enable-power-bi-visualization"></a>Power BI 시각화 사용

Power BI 시각화를 사용 하면 powerbi 액체 태그를 사용 하 여 포털의 웹 페이지에 대시보드 및 보고서를 포함할 수 있습니다.

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI 통합 설정** 으로 이동 하 > **Power BI 시각화를 사용 하도록**설정 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 시각화 사용](../media/enable-power-bi-visualization.png "Power BI 시각화 사용")

3.  확인 메시지에서 **사용** 을 선택 합니다. Power BI 시각화를 사용 하도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없게 됩니다. Power BI 시각화를 사용 하는 경우 메시지가 표시 됩니다.

웹 지정자는 [powerbi](../liquid/portals-entity-tags.md#powerbi) 액체 태그를 사용 하 여 포털의 웹 페이지에 Power BI 대시보드 및 보고서를 포함할 수 있습니다. Power BI 콘텐츠를 포함 하는 동안 사용자 지정자는 [필터 매개 변수](https://docs.microsoft.com/power-bi/service-url-filters) 를 사용 하 여 개인화 된 보기를 만들 수 있습니다. 추가 정보: [Powerbi 액체 태그](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Power BI 시각화 사용 안 함

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI 통합 설정** 으로 이동 하 > **Power BI 시각화를 사용 하지 않도록**설정 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 시각화 사용 안 함](../media/disable-power-bi-visualization.png "Power BI 시각화 사용 안 함")

3. 확인 메시지에서 **사용 안 함** 을 선택 합니다. Power BI 시각화를 사용 하지 않도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없게 됩니다. Power BI 시각화를 사용 하지 않도록 설정 하면 메시지가 표시 됩니다.

## <a name="enable-power-bi-embedded-service"></a>Power BI Embedded 서비스 사용

Power BI Embedded 서비스를 사용 하면 Power BI의 새 작업 영역에서 만든 대시보드 및 보고서를 포함할 수 있습니다. 대시보드 및 보고서는 powerbi 액체 태그를 사용 하 여 포털의 웹 페이지에 포함 됩니다.

**필수 조건**: Power BI Embedded 서비스를 사용 하도록 설정 하기 전에 Power BI의 새 작업 영역에서 대시보드 및 보고서를 만들었는지 확인 합니다. 작업 영역을 만든 후에는 작업 영역이 PowerApps 포털 관리 센터에 표시 되도록 전역 관리자에 게 관리자 액세스 권한을 제공 합니다. 새 작업 영역을 만들고 액세스 권한을 추가 하는 방법에 대 한 자세한 내용은 [Power BI에서 새 작업 영역 만들기](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)를 참조 하세요.

**Power BI Embedded 서비스 제한**사항: 제한 사항에 대 한 자세한 내용은 [고려 사항 및 제한](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations)사항을 참조 하세요.

> [!NOTE]
> Powerbi 액체 태그가 작동 하려면 Power BI 시각화가 사용 하도록 설정 되어 있는지 확인 합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **Power BI 통합 설정** 으로 이동 하 > **Power BI Embedded 서비스를 사용 하도록**설정 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 사용](../media/enable-powerbi-embedded-button.png "Power BI Embedded 서비스 사용")

3. **Power BI Embedded 서비스 통합 사용** 창에서 포털에서 대시보드 및 보고서를 표시 해야 하는 Power BI 작업 영역을 **선택한 작업 영역** 목록으로 이동 하 고 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 작업 영역 선택](../media/enable-powerbi-embedded-window.png "Power BI 작업 영역 선택")
    
    > [!NOTE]
    > **선택한 작업 영역** 목록에 작업 영역을 추가 하면 몇 분 후에 데이터베이스 및 보고서가 렌더링 됩니다.
    

4. **사용**을 선택 합니다. Power BI Embedded 서비스를 사용 하도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없습니다. Power BI Embedded 서비스를 사용 하는 경우 메시지가 표시 됩니다.

이제 보안 그룹을 만들고 Power BI 계정에 추가 해야 합니다. 자세한 내용은 [보안 그룹 만들기 및 Power BI 계정에 추가](#create-security-group-and-add-to-power-bi-account)를 참조 하세요.

### <a name="create-security-group-and-add-to-power-bi-account"></a>보안 그룹 만들기 및 Power BI 계정에 추가

Power BI Embedded 서비스 통합을 사용 하도록 설정한 후 Azure Active Directory에서 보안 그룹을 만들고 해당 그룹에 구성원을 추가한 다음 Power BI 관리 포털을 통해 Power BI에서 보안 그룹을 추가 해야 합니다. 이렇게 하면 새 Power BI 작업 영역에서 만든 대시보드 및 보고서를 포털에 표시할 수 있습니다.

> [!NOTE]
> Power BI Embedded 서비스를 사용 하도록 설정 하는 데 사용한 것과 동일한 전역 관리자 계정으로 로그인 해야 합니다.

**1 단계: 보안 그룹 만들기**

1. 디렉터리에 대 한 전역 관리자 계정을 사용 하 여 [Azure Portal](https://portal.azure.com) 에 로그인 합니다.

2. **Azure Active Directory**, **그룹**을 선택 하 고 **새 그룹**을 선택 합니다.

3. **그룹** 페이지에서 다음 정보를 입력 합니다.

    - **그룹 유형**: 보안.

    - **그룹 이름**: Portal Power BI Embedded service.

    - **그룹 설명**:이 보안 그룹은 포털 및 Power BI Embedded 서비스 통합에 사용 됩니다.

    - **멤버 자격 유형**: 할당 됨.

      > [!div class=mx-imgBorder]
      > ![Power BI Embedded 서비스에 대 한 보안 그룹 만들기](../media/powerbi-embed-security-group.png "Power BI Embedded 서비스에 대 한 보안 그룹 만들기")

4. **만들기**를 선택합니다.

**2 단계: 그룹 구성원 추가**

**필수 조건**: 보안 그룹에 구성원을 추가 하기 전에 사용자와 포털의 응용 프로그램 ID가 있어야 합니다. 포털의 응용 프로그램 ID는 [PowerApps 포털 관리 센터](admin-overview.md)의 **포털 세부 정보** 탭에서 사용할 수 있습니다.

1. 디렉터리에 대 한 전역 관리자 계정을 사용 하 여 [Azure Portal](https://portal.azure.com) 에 로그인 합니다.

2. **Azure Active Directory**를 선택 하 고 **그룹**을 선택 합니다.

3. **그룹-모든 그룹** 페이지에서 **포털 Power BI Embedded 서비스** 그룹을 검색 하 여 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스에 대 한 보안 그룹을 검색 하 고 선택 합니다.](../media/search-security-group.png "Power BI Embedded 서비스에 대 한 보안 그룹을 검색 하 고 선택 합니다.")

4. **포털 Power BI Embedded 서비스 개요** 페이지의 **관리** 영역에서 **구성원** 을 선택 합니다.

5. **구성원 추가**를 선택 하 고 텍스트 상자에 포털의 응용 프로그램 ID를 입력 합니다.

6. 검색 결과에서 멤버를 선택한 다음 **선택**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스에 대 한 보안 그룹의 구성원 추가](../media/add-member-powerbi-embed.png "Power BI Embedded 서비스에 대 한 보안 그룹의 구성원 추가")

**3 단계: 설치 Power BI**

1. 디렉터리에 대 한 전역 관리자 계정을 사용 하 여 [Power BI](https://powerbi.microsoft.com) 에 로그인 합니다.

2. Power BI 서비스의 맨 위에 있는 **설정** 을 선택 하 고 **관리 포털**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 서비스에서 관리 포털을 선택 합니다.](../media/select-admin-portal.png "Power BI 서비스에서 관리 포털을 선택 합니다.")

3. **테 넌 트 설정**을 선택 합니다.

4. **개발자 설정** 섹션에서 **서비스 사용자가 Power BI Api를 사용할 수 있도록 허용**을 선택 합니다.

5. **특정 보안 그룹** 필드에서 **포털 Power BI Embedded 서비스** 그룹을 검색 하 고 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 관리 포털에서 보안 그룹 추가](../media/add-sg-powerbi.png "Power BI 관리 포털에서 보안 그룹 추가")

6. **적용**을 선택 합니다.

이제 웹 작업에서 [powerbi](../liquid/portals-entity-tags.md#powerbi) 액체 태그를 사용 하 여 포털의 웹 페이지에 있는 새 Power BI 작업 영역에서 Power BI 대시보드 및 보고서를 포함할 수 있습니다. Power BI Embedded 서비스를 사용 하려면 인증 유형을 **powerbiembedded**로 지정 해야 합니다. Power BI 콘텐츠를 포함 하는 동안 사용자 지정자는 [필터 매개 변수](https://docs.microsoft.com/power-bi/service-url-filters) 를 사용 하 여 개인화 된 보기를 만들 수 있습니다. 추가 정보: [Powerbi 액체 태그](../liquid/portals-entity-tags.md#powerbi)


### <a name="manage-the-power-bi-embedded-service"></a>Power BI Embedded 서비스 관리

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **Power BI Integration 설정** > **Power BI Embedded 서비스 관리**로 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 관리](../media/manage-powerbi-embedded-button.png "Power BI Embedded 서비스 관리")

3. **Power BI Embedded 서비스 통합 관리** 창에서 대시보드 및 보고서가 포털에서 **선택한 작업 영역** 목록에 표시 되어야 하는 Power BI 작업 영역을 제거 하거나 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI 작업 영역 선택](../media/manage-powerbi-embedded-window.png "Power BI 작업 영역 선택")
    
    > [!NOTE]
    > **선택한 작업 영역** 목록에서 작업 영역을 제거한 후에는 변경 내용을 반영 하는 데 최대 1 시간이 걸릴 수 있습니다. 그때까지 데이터베이스와 보고서는 문제 없이 포털에서 렌더링 됩니다.

4. **저장**을 선택합니다.

### <a name="disable-the-power-bi-embedded-service"></a>Power BI Embedded 서비스를 사용 하지 않도록 설정

1.  [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **Power BI Integration 설정** > **Power BI Embedded 서비스 관리**로 이동 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 관리](../media/manage-powerbi-embedded-button.png "Power BI Embedded 서비스 관리")

3. **Power BI Embedded 서비스 통합 관리** 창에서 **Power BI Embedded 서비스 통합 사용 안 함**을 선택 합니다.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded 서비스 사용 안 함](../media/disable-powerbi-embedded-window.png "Power BI Embedded 서비스 사용 안 함")

4. **저장**을 선택합니다.

5. 확인 메시지에서 **확인을** 선택 합니다. Power BI Embedded 서비스를 사용 하지 않도록 설정 하는 동안 포털이 다시 시작 되 고 몇 분 동안 사용할 수 없습니다. Power BI Embedded 서비스를 사용 하지 않도록 설정 하면 메시지가 표시 됩니다.

## <a name="privacy-notice"></a>개인 정보 취급 방침  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>참고 항목

[powerbi 액체 태그](../liquid/portals-entity-tags.md#powerbi)<br>[포털에서 웹 페이지에 Power BI 보고서 또는 대시보드 추가](add-powerbi-report.md)  

