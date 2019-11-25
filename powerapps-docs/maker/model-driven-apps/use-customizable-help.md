---
title: 사용자 지정 가능한 도움말 활성화 및 사용(모델 기반 앱) | MicrosoftDocs
description: ''
keywords: ''
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
- customizer
search.app:
- PowerApps
ms.openlocfilehash: 3e6b593a30044c6a2c8cfc3e4867cb18156208f5
ms.sourcegitcommit: 7411b4cf9e30e71052fe932dfd3276e969854af4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "2768435"
---
# <a name="enable-and-use-customizable-help"></a>사용자 지정 가능한 도움말 활성화 및 사용
사용자 지정 가능한 도움말을 통해 양식을 작성하는 모델 기반 앱 사용자에게 고유한 상황 정보를 제공할 수 있습니다. 

> [!NOTE]
> 자체 도움말 시스템을 만들고 유지 관리하는 대신 통합 인터페이스 애플리케이션에 조직에 맞는 제품 내 사용자 지정 도움말 환경을 제공하는 도움말을 작성하는 데 사용할 수 있는 사용자 지정 도움말 창과 단계별 작업을 사용할 수 있습니다. 추가 정보: [통합 인터페이스 앱의 문제 해결 도우미 만들기](../common-data-service/create-custom-help-pages.md)

모델 기반 앱에서 전역(환경) 수준 또는 엔터티 수준에서 기본 도움말을 원하는 사용자 지정 도움말로 바꿀 수 있습니다. 사용자 지정 도움말은 사용자 지정 또는 사용자 지정 가능한 엔터티에 더욱 관련이 있는 도움말 링크를 통해 콘텐츠를 제공합니다. 단일의 전역 전체 URL을 사용하여 모든 사용자 지정 엔터티에 대한 기본 제공 도움말 링크를 재정의할 수 있습니다. 엔터티당 URL은 특정 사용자 지정 가능한 엔터티에 대한 표와 양식에 있는 기본 제공 도움말 링크를 재정의합니다. URL에 언어 코드와 엔터티 이름 같은 추가 매개 변수를 포함할 수 있습니다. 이러한 매개 변수를 사용하면 개발자가 응용 프로그램 내에서 언어 또는 엔터티 컨텍스트와 관련된 페이지로 리디렉션하는 기능을 추가할 수 있습니다. 엔터티 수준 사용자 지정 도움말 설정은 솔루션에 따라 다르므로 솔루션의 일부로 패키징하고 환경 간에 전송하거나 솔루션에 배포할 수 있습니다. 

## <a name="set-up-customizable-help"></a>사용자 지정할 수 있는 도움말 설정
전역 및 엔터티 수준에서 사용자 지정 가능한 도움말을 설정할 수 있습니다. 

### <a name="set-customizable-help-at-the-global-level"></a>전역 수준에서 사용자 지정 가능한 도움말 설정
시스템 관리자 보안 역할을 가진 사용자는 이 설정을 사용하여 전역 수준에서 기본 도움말을 재정의할 수 있습니다. 
1. 모델 기반 앱을 연 다음 명령 모음에서 **설정** ![설정](../model-driven-apps/media/powerapps-gear.png) > **고급 설정**을 선택합니다.
2. **설정** > **관리**로 이동합니다.
3. **시스템 설정**을 선택한 다음 **일반** 탭을 선택합니다. 
4. **사용자 지정 도움말 URL 설정** 아래에서 다음 사용자 지정 도움말 전역 설정을 선택하고 정의하십시오. 
     - **사용자 지정 가능한 엔터티에 대한 사용자 지정 도움말 사용**. 선택하여 활성화합니다.  
     - **전역 사용자 지정 도움말 URL**. 사용자 지정 도움말의 URL을 입력하십시오. 
     - **URL에 매개 변수 추가**. **예**를 선택하여 언어 코드 또는 엔터티 이름과 같은 매개 변수를 엔터티 정의에서 지정한 **도움말 URL**에 추가할 수 있습니다. 추가 정보: [URL에 매개 변수 추가](#append-parameters-to-url)  

    > [!div class="mx-imgBorder"] 
    > ![사용자 지정 가능한 도움말 전역 설정](media/customizable-help-global-setting.png)

5. **확인**을 선택합니다.

### <a name="set-customizable-help-for-a-specific-entity"></a>특정 엔터티에 대해 사용자 지정 가능한 도움말 설정
전역 수준에서 사용자 지정 도움말을 활성화한 후 시스템 사용자 지정자는 엔터티 정의에서 엔터티의 전역 도움말 URL을 재정의할 수 있습니다. 

1. 솔루션 탐색기를 엽니다.
2. **엔터티**를 확장한 다음 원하는 엔터티를 선택합니다. 
3. 엔터티 정의의 **도움말** 섹션 아래에 있는 **일반** 탭의 **도움말 URL** 상자에 사용자 지정 도움말 페이지의 URL을 입력하십시오. 

    > [!div class="mx-imgBorder"] 
    > ![사용자 지정 가능한 도움말 엔터티 설정](media/customizable-help-entity-setting.png)

#### <a name="append-parameters-to-url"></a>URL에 매개 변수 추가
앞에서 설명한 것처럼 매개 변수를 엔터티 정의의 **도움말 URL**에 추가할 수 있도록 허용하려면 **환경 설정** > **일반** 탭에서 **URL에 매개 변수 추가**를 **예**로 설정합니다. 

URL에 추가할 수 있는 매개 변수의 예:

- 사용자 언어 코드: userlcid
- 엔터티 이름: entity
- 진입점: 계층 구조 차트 또는 양식
- 양식 Id: formid

