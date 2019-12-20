---
title: Power Apps 및 Common Data Service용 개발자 리소스 보기 또는 다운로드 | MicrosoftDocs
description: Power Apps 및 Common Data Service 개발자 리소스 및 서비스 끝점 URL 찾기
keywords: ''
ms.date: 09/25/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4cb1670334f676af1a6ddcb1e90ba47240ed46a4
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869574"
---
# <a name="view-or-download-developer-resources"></a>개발자 리소스 보기 또는 다운로드

이 페이지에서는 개발자를 위한 리소스와 작업 중인 특정 인스턴스에 대한 정보를 제공합니다. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>사용자 환경에 대한 개발자 리소스 페이지 보기

1. Power Apps 포털에서 ![설정 단추](../../administrator/media/settings-button-nav-bar.png) 설정 단추를 선택하고 **고급 사용자 지정**을 선택합니다.

    ![고급 사용자 지정](media/advanced-customizations-menu.png)

1. **고급 사용자 지정** 패널에서 **개발자 리소스** 링크를 선택합니다.<br />![개발자 리소스 링크](media/developer-resources-link.png)

## <a name="getting-started"></a>시작 

이 섹션에서는 개발자가 리소스를 찾을 수 있는 링크를 제공합니다. 다음과 같은 리소스를 사용할 수 있습니다.


|링크 |설명|
|---------|---------|
|[개발자 센터](https://go.microsoft.com/fwlink/?LinkId=551006).|Power Apps 및 Common Data Service에 대한 개발자 문서를 보려면 여기에서 시작하십시오.|
|[Power Apps 커뮤니티/포럼](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)|Power Apps커뮤니티에서 질문하고 답변하십시오.|
|[NuGetPackages(패키지)](https://www.nuget.org/profiles/crmsdk)|NuGet 패키지를 검색하여 프로젝트에 SDK 어셈블리를 추가합니다.|
|[다운로드 도구](/powerapps/developer/common-data-service/download-tools-nuget)|필요한 도구는 NuGet에서 다운로드할 수 있습니다. 이 페이지에서 PowerShell 스크립트를 사용하여 최신 버전을 가져올 수 있습니다.|
|[샘플 코드](https://go.microsoft.com/fwlink/?LinkId=553007)|Power Apps 샘플이 있는 GitHub 리포지토리.|
|[개발자 개요](https://go.microsoft.com/fwlink/?LinkId=550995)|개발자를 위한 개요를 제공하는 항목에 연결합니다.|

## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Common Data Service의 이 인스턴스에 앱 연결

이 섹션에서는 Common Data Service 인스턴스에 연결하는 데 필요한 정보를 제공합니다.

### <a name="instance-web-api"></a>인스턴스 웹 API

인스턴스에 대한 웹 API의 URL입니다. 웹 API는 OData v4 RESTful API입니다. 인스턴스에서 사용할 수 있는 메타데이터 및 작업을 설명하는 서비스 문서를 다운로드할 수도 있습니다. 추가 정보: 개발자 설명서: [Common Data Service 웹 API 사용](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>조직 서비스

인스턴스에 대한 조직 서비스의 SOAP 끝점에 대한 URL입니다.
여기에서 이 서비스에 대한 WSDL을 다운로드할 수 있지만 일반적으로 CrmSvcUtil 코드 생성 도구를 사용하여 .net 프로젝트에 대한 엔터티 클래스를 빌드합니다. 추가 정보: 
- [개발자 설명서: 코드 생성 도구(CrmSvcUtil.exe)를 사용하여 초기 바인딩 엔터티 클래스 생성](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [개발자 설명서: 조직 서비스를 사용하여 데이터 또는 메타데이터 읽고 쓰기](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>인스턴스 참조 정보

이 정보는 인스턴스를 고유하게 설명합니다. GUID **ID**와 **고유 이름**이 있습니다.
이 정보는 인스턴스와 함께 Azure 확장을 사용할 때 필요합니다.
추가 정보: [개발자 설명서: Dynamics 365용 Azure 확장](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Common Data Service 검색 서비스에 앱 연결

사용자가 여러 Common Data Service 환경에 액세스할 수 있기 때문에 검색 서비스를 사용하여 개인이 자신의 자격 증명을 기반으로 액세스할 수 있는 환경을 검색합니다.

### <a name="discovery-web-api"></a>검색 웹 API

인스턴스에 사용할 검색 서비스의 RESTful OData v4 버전에 대한 끝점 주소입니다. 여기에서 서비스 문서를 다운로드할 수도 있습니다.
추가 정보: [개발자 설명서서: 웹 API를 사용하여 조직의 URL 검색](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>검색 서비스

인스턴스에 사용할 검색 서비스의 SOAP 버전에 대한 끝점 주소입니다. 여기에서 서비스 문서를 다운로드할 수도 있습니다.
추가 정보: [개발자 설명서서: 검색 서비스를 사용하여 조직의 URL 검색](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
