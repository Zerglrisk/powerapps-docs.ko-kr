---
title: Azure Blob storage에서 포털 오류 로그 보기 및 저장 | MicrosoftDocs
description: 포털 오류 로그를 보고 Azure Blob storage 계정에 저장 하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0b8482108be50c07c229d2c283391d96624e6884
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977269"
---
# <a name="view-portal-error-logs"></a>포털 오류 로그 보기

포털 관리자 또는 개발자는 PowerApps 포털을 사용 하 여 고객을 위한 웹 사이트를 만들 수 있습니다. 개발자를 위한 일반적인 작업 중 하나는 포털을 개발 하는 동안 문제를 디버그 하는 것입니다. 디버그를 지원 하기 위해 포털의 모든 문제에 대 한 자세한 오류 로그에 액세스할 수 있습니다. 여러 가지 방법으로 포털에 대 한 오류 로그를 가져올 수 있습니다.

## <a name="custom-error"></a>사용자 지정 오류

포털에서 서버 쪽 예외가 발생 하면 기본적으로 사용자에 게 친숙 한 오류 메시지와 함께 사용자 지정 오류 페이지가 표시 됩니다. 오류 메시지를 구성 하려면 [사용자 지정 오류 메시지 표시](#display-a-custom-error-message)를 참조 하세요.

그러나 디버깅을 위해 ASP.NET 상세 오류 페이지를 확인 하는 것이 좋습니다 (예를 들어, 노란색의 주황색 화면이 라고도 함). 자세한 오류 페이지를 통해 전체 서버 오류 스택을 가져올 수 있습니다.

> [!div class=mx-imgBorder]
> 죽음(../media/ysod.png "노란색 죽음 화면의") ![노란색 화면]

YSOD를 사용 하도록 설정 하려면 포털에서 [사용자 지정 오류를 사용 하지 않도록 설정](#disable-custom-error) 해야 합니다.

> [!NOTE]
> 개발 단계에서 사용자 지정 오류를 사용 하지 않도록 설정 하 고 라이브 상태가 되 면 사용자 지정 오류를 사용 하도록 설정 하는 것이 좋습니다.

사용자 지정 오류에 대 한 추가 정보: [사용자 지정 오류 페이지 표시](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>사용자 지정 오류 사용 안 함

포털에서 서버 쪽 예외가 발생 하는 경우 포털에서 사용자 지정 오류를 사용 하지 않도록 설정 하 여 자세한 예외 메시지를 표시할 수 있습니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **사용자 지정 오류 비활성화**로 이동 합니다.

   > [!div class=mx-imgBorder]
   > ![사용자 지정 오류 사용 안 함](../media/disable-custom-errors.png "사용자 지정 오류 사용") 안 함

3. 확인 메시지에서 **사용 안 함** 을 선택 합니다. 사용자 지정 오류를 사용 하지 않도록 설정 하는 동안 포털이 다시 시작 되 고 사용할 수 없게 됩니다. 사용자 지정 오류를 사용 하지 않도록 설정 하면 메시지가 표시 됩니다.

### <a name="enable-custom-error"></a>사용자 지정 오류 사용

포털에서 사용자 지정 오류를 사용 하도록 설정 하 여 YSOD 아닌 전문적인 페이지를 표시할 수 있습니다. 응용 프로그램에서 예외가 발생 하는 경우이 페이지에서 의미 있는 정보를 제공 합니다.

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **사용자 지정 오류 사용**으로 이동 합니다.

   > [!div class=mx-imgBorder]
   > ![사용자 지정 오류]사용(../media/enable-custom-errors.png "사용자 지정 오류 사용")

3. 확인 메시지에서 **사용** 을 선택 합니다. 사용자 지정 오류를 사용 하도록 설정 하는 동안 포털이 다시 시작 되 고 사용할 수 없게 됩니다. 사용자 지정 오류를 사용 하도록 설정 하면 메시지가 표시 됩니다.

> [!NOTE]
> - 포털이 연결 된 인스턴스를 변경 하는 경우 사용자 지정 오류 설정은 사용으로 설정 됩니다. 필요한 경우에는 사용자 지정 오류를 다시 사용 하지 않도록 설정 해야 합니다.
> - 포털이 연결 된 인스턴스를 변경 하는 경우에는 사용자 지정 오류를 사용 하거나 사용 하지 않도록 설정 해야 합니다. 그렇지 않으면 오류 메시지가 나타납니다.

### <a name="display-a-custom-error-message"></a>사용자 지정 오류 메시지 표시

일반 오류 대신 전문가가 볼 수 있는 사용자 지정 오류를 표시 하도록 포털을 구성할 수 있습니다.

사용자 지정 오류를 정의 하려면 `Portal Generic Error`콘텐츠 조각을 사용 합니다. 이 코드 조각에 정의 된 콘텐츠는 오류 페이지에 표시 됩니다. 이 콘텐츠 조각은 기본 제공 되지 않으므로 만들어야 합니다. 콘텐츠 조각 **형식은** **텍스트** 또는 **HTML**일 수 있습니다. 콘텐츠 조각을 만들거나 편집 하려면 콘텐츠 [조각을 사용 하 여 콘텐츠 사용자 지정](https://docs.microsoft.com/dynamics365/customer-engagement/portals/customize-content-snippets)을 참조 하세요.

> [!NOTE]
> 콘텐츠 조각에서 액체 코드가 작성 되 면이를 건너뛰고 렌더링 되지 않습니다.

사용자 지정 오류를 사용 하도록 설정 하면 오류 페이지의 다음 구조에 메시지가 표시 됩니다.

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

다음은 HTML 형식의 내용 코드를 사용 하는 사용자 지정 오류 메시지의 예입니다.

사용자 지정 오류입니다. 여기를 클릭 하 여 오류 스크린샷으로 지원 티켓을 제출 하십시오.

> [!div class=mx-imgBorder]
> ![사용자 지정 오류 메시지](../media/custom-error-message.png "사용자 지정 오류 메시지")

> [!NOTE]
> Common Data Service에 연결할 수 없거나 조각이 Common Data Service에서 사용할 수 없는 경우 포털에서 콘텐츠 조각을 검색할 수 없는 경우 오류 메시지가 나타납니다.

## <a name="access-portal-error-logs"></a>포털 오류 로그 액세스

포털을 개발 하 고 게시 한 후에도 포털 로그에 액세스 하 여 고객이 보고 한 문제를 디버그할 수 있도록 해야 합니다. 로그에 액세스 하려면 소유한 Azure Blob storage 계정에 모든 응용 프로그램 오류를 보내도록 포털을 구성할 수 있습니다. 포털 오류 로그에 액세스 하면 문제에 대 한 세부 정보가 있으므로 고객 쿼리에 효율적으로 대응할 수 있습니다. Azure Blob storage에 포털 오류 로그를 가져오려면 PowerApps 포털 관리 센터에서 진단 로깅을 사용 하도록 설정 해야 합니다.

> [!NOTE]
> 포털이 연결 된 Common Data Service 인스턴스를 변경 하는 경우 진단 로깅이 사용 되지 않습니다. 진단 로깅을 다시 사용 하도록 설정 해야 합니다.

### <a name="enable-diagnostic-logging"></a>진단 로깅 사용

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 사용**으로 이동 합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용](../media/enable-diagnostic-logging.png "진단 로깅 사용")

3. **진단 로깅 사용** 창에서 다음 값을 입력 합니다.

   - **Azure Blob Storage 서비스의 연결 문자열**: 포털 오류 로그를 저장할 Azure Blob Storage 서비스의 URL입니다. URL의 최대 길이는 2048 자입니다. URL이 2048 자 보다 길면 오류 메시지가 표시 됩니다. 연결 문자열에 대 한 추가 정보: [연결 문자열 Azure Storage 구성](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **보존 기간**: 기간을 선택 하 여 blob storage에서 포털 오류 로그를 유지 합니다. 선택한 기간 후에 오류 로그가 삭제 됩니다. 다음 값 중 하나를 선택할 수 있습니다.
     - 1 일
     - 7 일
     - 30 일
     - 60 일
     - 90 일
     - 180 일
     - 항상

   기본적으로 보존 기간은 30 일입니다.
  
   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용](../media/enable-diagnostic-logging-window.png "진단 로깅 창 사용")

4. **구성**을 클릭 합니다.

진단 로깅이 구성 되 면 새 **원격 분석 로그** Blob 컨테이너가 Azure storage 계정에 만들어지고 로그는 컨테이너에 저장 된 blob 파일에 기록 됩니다. 다음 스크린샷은 Azure storage 탐색기의 **원격 분석 로그** blob 컨테이너를 보여 줍니다.

> [!div class=mx-imgBorder]
> Azure ![블로그 저장소 계정](../media/azure-blob-storage.png "azure 블로그 저장소 계정")

진단 로깅이 성공적으로 설정 되 면 다음 작업을 사용할 수 있게 됩니다.
- **진단 로깅 구성 업데이트**: 포털에 대 한 진단 로깅 구성을 업데이트 하거나 제거할 수 있습니다.
- **진단 로깅 사용 안 함**: 포털에 대 한 진단 로깅 구성을 사용 하지 않도록 설정할 수 있습니다.
 
### <a name="update-diagnostic-logging"></a>진단 로깅 업데이트

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 구성 업데이트**로 이동 합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 구성]업데이트(../media/update-diagnostic-logging.png "진단 로깅 구성을") 업데이트 합니다.

3. 진단 로깅 구성 업데이트 창에서 다음 값을 입력 합니다.
   - **Azure Blob Storage 서비스의 연결 문자열을 업데이트**하 시겠습니까?: Azure Blob Storage 서비스의 연결 문자열을 업데이트할지 여부를 지정할 수 있습니다. 기본적으로 선택 되어 있습니다.
   - **Azure Blob Storage 서비스의 연결 문자열**: 포털 오류 로그를 저장할 Azure Blob Storage 서비스의 URL입니다. URL의 최대 길이는 2048 자까지 가능 합니다. URL이 2048 자 보다 길면 오류 메시지가 표시 됩니다. 이 필드는 **Azure Blob Storage 서비스의 연결 문자열을 업데이트 하려는** 경우에만 표시 됩니다. 확인란을 선택 합니다. 연결 문자열에 대 한 추가 정보: [연결 문자열 Azure Storage 구성](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **보존 기간**: 기간을 선택 하 여 blob storage에서 포털 오류 로그를 유지 합니다. 선택한 기간 후에 오류 로그가 삭제 됩니다. 다음 값 중 하나를 선택할 수 있습니다.
     - 1 일
     - 7 일
     - 30 일
     - 60 일
     - 90 일
     - 180 일
     - 항상

   기본적으로 보존 기간은 30 일입니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 구성 창]업데이트(../media/update-diagnostic-logging-window.png "진단 로깅 구성 창")

4. **업데이트**를 클릭 합니다.

### <a name="disable-diagnostic-logging"></a>진단 로깅 사용 안 함

1. [PowerApps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 사용 안 함**으로 이동 합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용 안]함(../media/disable-diagnostic-logging.png "진단 로깅") 사용 안 함

3. 확인 메시지에서 **사용 안 함** 을 클릭 합니다.

## <a name="display-plugin-error"></a>플러그 인 오류 표시

포털을 개발 하는 동안 자주 발생 하는 또 다른 시나리오는 사용자 지정 플러그 인 및 Common Data Service 환경에서 작성 된 비즈니스 논리에 의해 생성 되는 오류입니다. 이러한 오류는 일반적으로 [사용자 지정 오류를 비활성화](#disable-custom-error) 하거나 [진단 로깅을 사용](#enable-diagnostic-logging)하 여 액세스할 수 있습니다. 그러나 경우에 따라 이러한 오류를 포털에 직접 표시 하 여 문제를 더 빠르게 진단할 수 있습니다. 이렇게 하려면 포털 화면에서 Common Data Service의 사용자 지정 플러그 인 오류를 표시 하도록 포털을 구성할 수 있습니다.

사용자 지정 플러그 인 오류를 표시 하려면 사이트 설정 `Site/EnableCustomPluginError` 만들고 해당 값을 True로 설정 합니다. 사용자 지정 플러그 인 오류는 일반 오류 대신 화면에 표시 됩니다. 이 오류는 전체 스택 추적이 아니라 플러그 인 오류의 메시지 부분만 표시 합니다.

사용자 지정 플러그 인 오류가 표시 되는 화면은 다음과 같습니다. 
- 엔터티 목록 
    - 레코드 검색 
- 엔터티 양식 
    - 읽어들이고 
    - 만들기/업데이트 등 
- Web forms 
    - 읽어들이고 
    - 만들기/업데이트 등

사이트 설정이 없는 경우 기본적으로 false로 처리 되 고 플러그 인 오류가 렌더링 되지 않습니다.
