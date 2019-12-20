---
title: 솔루션을 사용하여 모델 기반 앱 배포 | MicrosoftDocs
description: 솔루션을 사용하여 모델 기반 앱을 배포하는 방법 알아보기
keywords: ''
ms.date: 08/06/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2d9c6692f26e16b03872696b094ccd14a649299f
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873184"
---
# <a name="distribute-a-model-driven-app-using-a-solution"></a>솔루션을 사용하여 모델 기반 앱 배포

모델 기반 앱은 솔루션 구성 요소로 배포됩니다. 모델 기반 앱을 만든 후에는 앱을 솔루션에 패키징한 다음 zip 파일로 내보내는 방법으로 다른 환경에서 사용할 수 있습니다. 대상 환경에서 솔루션(.zip 파일)을 성공적으로 가져오면 패키지된 앱을 사용할 수 있습니다. 
  
## <a name="add-an-app-to-a-solution"></a>솔루션에 앱 추가
앱을 배포하려면 내보낼 앱을 패키지로 만들 수 있도록 솔루션을 만듭니다.

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

2. **솔루션**을 선택한 다음 **새 솔루션**을 선택합니다.
3. **새 솔루션** 페이지에서 필드를 완료한 다음 **저장**을 선택합니다. 추가 정보: [솔루션 만들기](../common-data-service/create-solution.md)
4. **솔루션** 페이지가 나타납니다. **기존 추가**를 선택하고 **앱**을 선택하고 솔루션에 추가하려는 앱을 선택한 다음 **확인**을 선택합니다. 

    ![솔루션 구성 요소 선택](media/select-solution-components.png)

5. **필수 구성 요소 누락** 페이지가 나타나면 **예, 필수 구성 요소 포함**을 선택하여 앱의 일부인 엔터티, 보기, 양식, 차트 및 사이트 맵과 같은 필수 구성 요소를 추가하는 것이 좋습니다. **확인**을 선택합니다.
6. **솔루션** 페이지에서 **저장 후 닫기**를 선택합니다.

## <a name="export-a-solution"></a>솔루션 내보내기
다른 환경으로 가져오거나 [Microsoft AppSource](https://appsource.microsoft.com/)에서 사용할 수 있도록 앱을 배포하려면 솔루션을 zip 파일로 내보냅니다. 그런 다음 앱과 구성 요소를 포함하는 zip 파일을 다른 환경으로 가져올 수 있습니다.

1. [솔루션 페이지](advanced-navigation.md#solutions)를 엽니다. 
2. 내보낼 솔루션을 선택하고 도구 모음에서 **내보내기**를 선택합니다. 
3. **사용자 지정 항목 게시** 페이지에서 **다음**을 클릭합니다.
4. **필수 구성 요소 누락** 페이지가 나타나면 **다음**을 선택합니다. 
5. **시스템 설정 내보내기** 페이지에서 포함하려는 선택적 기능을 선택하고 **다음**을 선택합니다. 
6. **패키지 유형** 페이지에서 **비관리형** 또는 **관리형**을 선택하고 **내보내기**를 선택합니다. 솔루션 패키지 유형에 대한 자세한 내용은 [솔루션 개요 ](../common-data-service/solutions-overview.md)를 참조하십시오.
7. 브라우저 및 설정에 따라 .zip 패키지 파일이 빌드되고 기본 다운로드 폴더에 복사됩니다. 패키지의 파일 이름은 밑줄 및 솔루션 버전 번호가 추가된 솔루션의 고유 이름을 기반으로 합니다.

    > [!NOTE]
    > 솔루션을 사용하여 앱을 내보낼 때 앱 URL은 내보내지 않습니다.
  
## <a name="import-a-solution"></a>솔루션 가져오기  
가져오려는 앱이 포함된 솔루션 zip 파일을 받으면 솔루션 구성 요소 페이지를 열고 솔루션을 가져옵니다. 솔루션을 성공적으로 가져오면 환경에서 앱을 사용할 수 있습니다.

1. [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.

2. **솔루션**을 선택한 다음 도구 모음에서 **가져오기**를 선택합니다.
3. 가져오려는 파일을 찾은 다음 **다음**을 선택합니다.
4. **가져오기**를 선택합니다.

## <a name="see-also"></a>참조
[솔루션 게시자 접두사를 변경](../common-data-service/change-solution-publisher-prefix.md)
