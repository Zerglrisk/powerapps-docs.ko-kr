---
title: 포털에서 웹 사이트 바인딩 만들기 및 관리 | MicrosoftDocs
description: 포털에서 웹 사이트 바인딩을 만들고 관리하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/12/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f2cc1c3aad7f8aaf4b9dc1f554d7a7a1d91d62e8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866626"
---
# <a name="create-and-manage-website-bindings"></a>웹 사이트 바인딩 만들기 및 관리

포털의 웹 사이트를 선택하는 기본 방법은 해당 특정 포털의 web.config 파일에 정의된 웹 사이트의 이름과 일치시켜 웹 사이트를 찾는 것입니다. 웹 사이트 바인딩은 적절한 웹 사이트를 선택하는 호스트 이름 또는 요청의 경로를 사용하여 포털을 로드할 때 웹 사이트를 선택하는 대체 방법을 제공합니다. 이렇게 하면 특정 웹 사이트의 각 버전에 대해 별도의 web.config 파일을 수정할 필요가 없습니다. 이를 통해 다양한 개발, 스테이징 및 프로덕션 환경에서 포털의 배포가 간소화됩니다. 또한 이를 통해 공통 포털 코드 베이스로 여러 웹 사이트를 운영할 수 있습니다.

## <a name="manage-website-bindings"></a>웹 사이트 바인딩 관리

Power Apps 포털 내에서 웹 사이트 바인딩을 만들고, 편집하고, 삭제할 수 있습니다. 

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 사이트 바인딩**으로 이동합니다.

3. 새 웹 사이트 바인딩을 만들려면 **새로 만들기**를 선택합니다.

4. 기존 웹 사이트 바인딩을 편집하려면 웹 사이트 바인딩 이름을 선택합니다.

5. 필드에 적절한 값을 입력합니다.

6. **저장 후 닫기**를 선택합니다.

### <a name="website-binding-attributes"></a>웹 사이트 바인딩 특성

모든 바인딩에 공통적인 특성입니다.

|이름|설명|
|-----|----------|
|이름| 레코드를 볼 때 웹 사이트 바인딩을 식별하는 제목입니다.|
|웹 사이트|포털에서 선택해야 하는 [웹 사이트](websites.md)입니다.|
|릴리스 날짜|웹 사이트를 선택할 수 있는 시기를 결정하는 날짜입니다.|
|만료 날짜|웹 사이트 선택이 중지되는 시기를 결정하는 날짜입니다.|
|||

#### <a name="application-settings"></a>응용 프로그램 설정

응용 프로그램 수준 바인딩에 대해 이러한 특성의 값을 지정합니다. 이 바인딩은 IIS 웹 사이트 또는 응용 프로그램을 기반으로 매핑됩니다.

|이름|설명|
|-----|----------|
|사이트 이름|IIS 웹 사이트의 이름입니다.|
|가상 경로|웹 사이트 아래에 있는 IIS 응용 프로그램의 이름입니다.|
|||

Azure 웹 사이트 및 클라우드 서비스의 경우 사이트 이름 및 가상 경로 값은 **ServiceDefinition.csdef** 파일의 <Site> 및 <VirtualApplication> 노드에 의해 결정됩니다.

```
<ServiceDefinition>
  <WebRole>
    <Sites>
      <Site name=Dynamics Portals>
        <VirtualApplication name=customer-portal/>
```

### <a name="see-also"></a>참고 항목
[웹 사이트 만들기 및 관리](websites.md)
