---
title: 포털 오류 로그 보기 및 Azure Blob 저장소에 저장 | MicrosoftDocs
description: 포털 오류 로그를 보고 Azure Blob 저장소 계정에 저장하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ced53e6b3eb30668d81aca0f385f4ebd841f02fa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862495"
---
# <a name="view-portal-error-logs"></a>포털 오류 로그 보기

포털 관리자나 개발자는 Power Apps 포털을 사용하여 고객을 위한 웹 사이트를 만들 수 있습니다. 개발자의 일반적인 작업 중 하나는 포털을 개발하는 동안 문제를 디버깅하는 것입니다. 디버깅을 돕기 위해 포털의 모든 문제에 대한 자세한 오류 로그에 액세스할 수 있습니다. 포털에 대한 오류 로그를 얻을 수 있는 방법은 여러 가지가 있습니다.

## <a name="custom-error"></a>사용자 지정 오류

포털에서 서버 측 예외가 발생하는 경우 기본적으로 사용자에게 친숙한 오류 메시지가 표시되는 맞춤형 오류 페이지가 나타납니다. 오류 메시지를 구성하려면 [사용자 지정 오류 메시지 표시](#display-a-custom-error-message)를 참조하십시오.

그러나 디버깅 목적을 위해 옐로우 스크린(YSOD)이라고도 하는 ASP.NET 상세 오류 페이지를 참조하는 것이 좋습니다. 자세한 오류 페이지는 서버 오류의 전체 스택을 가져오는 데 도움이 됩니다.

> [!div class=mx-imgBorder]
> ![옐로우 스크린](../media/ysod.png "옐로우 스크린")

YSOD를 활성화하려면 포털에서 [사용자 정의 오류](#disable-custom-error)를 비활성화해야 합니다.

> [!NOTE]
> 개발 단계에 있을 때만 사용자 지정 오류를 사용하지 않도록 설정하고 공개 후에는 사용자 지정 오류를 사용하도록 하는 것이 좋습니다.

사용자 지정 오류에 대한 추가 정보: [사용자 지정 오류 페이지 표시](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>사용자 지정 오류 사용 안 함

포털에서 서버 쪽 예외가 발생 하면 자세한 예외 메시지를 표시하기 위해 포털에서 사용자 지정 오류를 비활성화할 수 있습니다.

1. [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **사용자 지정 오류를 사용 안 함**으로 이동합니다.

   > [!div class=mx-imgBorder]
   > ![사용자 지정 오류 사용 안 함](../media/disable-custom-errors.png "사용자 지정 오류 사용 안 함")

3. 확인 메시지에서 **사용 안 함**을 클릭합니다. 사용자 지정 오류가 비활성화되는 동안 포털은 다시 시작되어 사용할 수 없게 됩니다. 사용자 지정 오류를 사용할 수 없는 경우 메시지가 나타납니다.

### <a name="enable-custom-error"></a>사용자 지정 오류 사용

포털에서 사용자 지정 오류를 사용하여 YSOD 대신 전문가 수준의 페이지를 표시할 수 있습니다. 이 페이지에서는 응용 프로그램에서 예외가 발생하는 경우에 의미있는 정보를 제공합니다.

1. [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **사용자 지정 오류를 사용**으로 이동합니다.

   > [!div class=mx-imgBorder]
   > ![사용자 지정 오류 사용](../media/enable-custom-errors.png "사용자 지정 오류 사용")

3. 확인 메시지에서 **사용**을 클릭합니다. 사용자 지정 오류가 활성화되는 동안 포털은 다시 시작되어 사용할 수 없게 됩니다. 사용자 지정 오류를 사용할 수 있는 경우 메시지가 나타납니다.

> [!NOTE]
> - 포털이 연결된 인스턴스를 변경하는 경우 사용자 지정 오류 설정은 사용으로 설정됩니다. 필요한 경우 사용자 지정 오류를 다시 사용하지 않도록 설정해야 합니다.
> - 포털이 연결된 인스턴스가 변경될 때 사용자 지정 오류를 사용하거나 사용하지 않도록 설정해야 합니다. 그렇지 않으면 오류 메시지가 나타납니다.

### <a name="display-a-custom-error-message"></a>사용자 지정 오류 메시지 표시

일반 오류 대신 전문가 수준의 사용자 지정 오류를 표시하도록 포털을 구성할 수 있습니다.

사용자 지정 오류를 정의하려면 콘텐츠 조각 `Portal Generic Error`를 사용합니다. 이 조각에 정의된 콘텐츠는 오류 페이지에 표시됩니다. 이 콘텐츠 조각은 기본 제공되지 않으므로 만들어야 합니다. 콘텐츠 조각 **형식**은 **텍스트** 또는 **HTML**일 수 있습니다. 콘텐츠 코드 조각을 만들거나 편집하려면 [콘텐츠 코드 조각을 사용하여 콘텐츠 사용자 지정](../configure/customize-content-snippets.md)을 참조하십시오.

> [!NOTE]
> 콘텐츠 조각에 유동 코드가 작성되면 이 코드를 건너뛰고 이를 렌더링하지 않습니다.

사용자 지정 오류를 사용하도록 설정하면 오류 페이지에 다음 구조로 메시지가 나타납니다.

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

다음은 HTML 형식의 콘텐츠 조각을 사용하는 사용자 지정 오류 메시지의 예입니다.

이것은 사용자 정의 오류입니다. 여기를 클릭하여 오류의 스크린샷과 함께 지원 티켓을 제출해 주십시오.

> [!div class=mx-imgBorder]
> ![사용자 지정 오류 메시지](../media/custom-error-message.png "사용자 지정 오류 메시지")

> [!NOTE]
> Common Data Service에 연결할 수 없어서 포털에서 콘텐츠 조각을 검색할 수 없거나 Common Data Service에서 조각을 사용할 수 없는 경우 오류 메시지가 나타납니다.

## <a name="access-portal-error-logs"></a>포털 액세스 오류 로그

포털을 개발하고 게시한 후에도 포털 로그에 액세스하여 고객이 보고한 문제를 디버깅할 수 있어야 합니다. 로그에 액세스하려면 사용자가 소유한 Azure Blob 저장소 계정으로 모든 응용 프로그램 오류를 보내도록 포털을 구성할 수 있습니다. 문제의 세부 사항을 가지고 있기 때문에 포털 오류 로그에 액세스하여 고객 쿼리에 효율적으로 응답할 수 있습니다. 포털 오류 로그를 Azure Blob Storage에 가져오려면 Power Apps 포털 관리 센터에서 진단 로깅을 사용하도록 설정해야 합니다.

> [!NOTE]
> 포털이 연결된 Common Data Service 인스턴스를 변경하면 진단 로깅이 비활성화됩니다. 진단 로깅을 사용하도록 다시 설정해야 합니다.

### <a name="enable-diagnostic-logging"></a>진단 로깅 사용

1. [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 사용**으로 이동합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용](../media/enable-diagnostic-logging.png "진단 로깅 사용")

3. **진단 로깅 사용** 창에서 다음 값을 입력합니다.

   - **Azure Blob 저장소 서비스의 연결 문자열**: 포털 오류 로그를 저장할 Azure Blob 저장소 서비스의 URL입니다. URL의 최대 길이는 2048자입니다. URL이 2048자보다 길면 오류 메시지가 나타납니다. 연결 문자열에 대한 추가 정보: [Azure Storage 연결 문자열 구성](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **보존 기간 선택**: 포털 오류 로그를 Blob 저장소에 보관할 기간입니다. 선택한 기간 후에 오류 로그가 삭제됩니다. 다음 값 중 하나를 선택할 수 있습니다.
     - 하루
     - 7일
     - 30일
     - 60일
     - 90일
     - 180일
     - 항상 표시

   기본적으로 보존 기간은 30일입니다.
  
   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용 창](../media/enable-diagnostic-logging-window.png "진단 로깅 사용 창")

4. **구성**을 클릭합니다.

진단 로깅이 구성되면 새 **원격 분석 로그** Blob 컨테이너가 Azure Storage 계정에 만들어지고 로그는 컨테이너에 저장된 Blob 파일에 기록됩니다. 다음 스크린샷은 Azure Storage 탐색기의 **원격 분석 로그** Blob 컨테이너를 보여 줍니다.

> [!div class=mx-imgBorder]
> ![Azure Blob Storage 계정](../media/azure-blob-storage.png "Azure Blob Storage 계정")

진단 로깅이 성공적으로 활성화되면 다음 작업을 사용할 수 있게 됩니다.
- **진단 로깅 구성 업데이트**: 포털에 대한 진단 로깅 구성을 업데이트하거나 제거할 수 있습니다.
- **진단 로깅 구성 사용 안 함**: 포털에 대한 진단 로깅 구성을 사용하지 않도록 설정할 수 있습니다.
 
### <a name="update-diagnostic-logging"></a>진단 로깅 업데이트

1. [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 구성 업데이트**로 이동합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 구성 업데이트](../media/update-diagnostic-logging.png "진단 로깅 구성 업데이트")

3. 진단 로깅 구성 업데이트 창에서 다음 값을 입력합니다.
   - **Azure Blob 저장소 서비스의 연결 문자열을 업데이트하시겠습니까?**: Azure Blob 저장소 서비스의 연결 문자열을 업데이트할지 여부를 지정할 수 있습니다. 기본적으로 선택됩니다.
   - **Azure Blob 저장소 서비스의 연결 문자열**: 포털 오류 로그를 저장할 Azure Blob 저장소 서비스의 URL입니다. URL의 최대 길이는 2048자입니다. URL이 2048자보다 길면 오류 메시지가 나타납니다. 이 필드는 **Azure Blob 저장소 서비스의 연결 문자열을 업데이트하시겠습니까?** 확인란이 선택된 경우에만 표시됩니다. 연결 문자열에 대한 추가 정보: [Azure Storage 연결 문자열 구성](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **보존 기간 선택**: 포털 오류 로그를 Blob 저장소에 보관할 기간입니다. 선택한 기간 후에 오류 로그가 삭제됩니다. 다음 값 중 하나를 선택할 수 있습니다.
     - 하루
     - 7일
     - 30일
     - 60일
     - 90일
     - 180일
     - 항상 표시

   기본적으로 보존 기간은 30일입니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 구성 업데이트 창](../media/update-diagnostic-logging-window.png "진단 로깅 구성 업데이트 창")

4. **업데이트**를 클릭합니다.

### <a name="disable-diagnostic-logging"></a>진단 로깅 사용 안 함

1. [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2. **포털 작업** > **진단 로깅 사용 안 함**으로 이동합니다.

   > [!div class=mx-imgBorder]
   > ![진단 로깅 사용 안 함](../media/disable-diagnostic-logging.png "진단 로깅 사용 안 함")

3. 확인 메시지에서 **사용 안 함**을 클릭합니다.

## <a name="display-plugin-error"></a>플러그 인 오류 표시

포털을 개발하는 동안 흔히 나타나는 또 다른 시나리오는 사용자 지정 플러그 인과 Common Data Service 환경에서 작성된 비즈니스 논리에 의해 발생한 오류입니다. 이러한 오류는 일반적으로 [사용자 지정 오류를 사용하지 않도록 설정](#disable-custom-error)하거나 [진단 로깅을 사용하도록 설정](#enable-diagnostic-logging)하여 액세스할 수 있습니다. 그러나 경우에 따라서는 빠르게 문제를 진단하려면 이러한 오류를 직접 포털에 표시하는 것이 더 빠릅니다. 이렇게 하려면 포털 화면에서 Common Data Service의 사용자 정의 플러그인 오류를 표시하도록 포털을 구성할 수 있습니다.

사용자 지정 플러그 인 오류를 표시하려면 사이트 설정 `Site/EnableCustomPluginError`를 만들고 해당 값을 True로 설정합니다. 사용자 지정 플러그 인 오류가 일반 오류 대신 화면에 표시됩니다. 오류는 플러그 인 오류의 메시지 부분 표시하며 완전한 스택 추적을 표시하지 않습니다.

다음은 사용자 정의 플러그인 오류가 표시된 화면입니다. 
- 엔터티 목록 
    - 레코드 검색 
- 엔터티 양식 
    - 검색 
    - 문서 만들기/업데이트 등 
- 웹 양식 
    - 검색 
    - 문서 만들기/업데이트 등

사이트 설정이 없는 경우 기본적으로 false로 처리되며 플러그 인 오류가 렌더링되지 않습니다.
