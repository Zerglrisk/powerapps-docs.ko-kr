---
title: 유형 테이블 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
ms.openlocfilehash: 058580b8f39417ccc5e77e7ac96a51bfc95939a1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338761"
---
|Value|설명|
|--|--|
|`Currency`|-922337203685477과 922337203685477 사이의 통화 값은이 필드에 있을 수 있습니다. 전체 자릿수를 설정 하거나 조직에서 사용 하는 특정 통화 또는 단일 표준 전체 자릿수를 기준으로 전체 자릿수를 선택할 수 있습니다.|
|`DateAndTime.DateAndTime`|날짜 및 시간을 표시 합니다.|
|`DateAndTime.DateOnly`|날짜만 표시 합니다.|
|`Decimal`|-1000억의 값에는 최대 10 개의 소수점 전체 자릿수를 사용할 수 있으며이 필드에는-1000억이 있을 수 있습니다. 전체 자릿수와 최대값과 최 댓 값을 지정할 수 있습니다.|
|`Enum`|열거 된 데이터 형식입니다.|
|`FP`|-1000억에서-1000억 사이의 값에 최대 5 개의 소수점 전체 자릿수를 사용할 수 있습니다. 전체 자릿수와 최대값과 최 댓 값을 지정할 수 있습니다. |
|`Multiple`|이 필드는 최대 1048576 개의 텍스트 문자를 포함할 수 있습니다. 최대 길이를이 보다 작게 설정할 수 있습니다. 폼에이 필드를 추가 하는 경우 필드의 크기를 지정할 수 있습니다.|
|`OptionSet`|이 필드는 일련의 옵션을 제공 합니다. 각 옵션에는 숫자 값 및 레이블이 있습니다. 양식에 추가 하는 경우이 필드에는 사용자가 옵션을 하나만 선택할 수 있는 컨트롤이 표시 됩니다. |
|`SingleLine.Email`|텍스트는 사용자의 전자 메일 응용 프로그램을 열기 위한 mailto 링크를 제공 합니다.|
|`SingleLine.Phone`|웹 응용 프로그램에서 필드는 클릭-사용을 클릭 하 여 Skype 또는 Lync 중 하나를 사용 하 여 컴퓨터에 설치 된 경우이를 사용 하 여 호출을 시작 합니다. 전화 통신 공급자 선택은 시스템 설정의 일반 탭의 맨 아래에 있습니다. 태블릿 용 Dynamics 365의 경우 Skype는 사용할 수 있는 유일한 전화 통신 공급자입니다.|
|`SingleLine.Text`|이 옵션은 단순히 텍스트를 표시 합니다.|
|`SingleLine.TextArea`|이 서식 옵션은 여러 줄의 텍스트를 표시 하는 데 사용할 수 있습니다. 하지만 크기가 4000 자인 경우 여러 줄의 텍스트가 필요한 경우에는 여러 줄의 텍스트 필드를 선택 하는 것이 좋습니다.|
|`SingleLine.Ticker`|대부분의 언어에서 텍스트는 가격 책정 기호로 표시 되는 주식 가격에 대 한 세부 정보를 표시 하는 MSN Money 웹 사이트를 열 수 있는 링크로 활성화 됩니다. 특정 동아시아 언어의 경우 창에서 종목 기호에 대 한 Bing 검색 결과를 엽니다.|
|`SingleLine.URL`|텍스트는 지정 된 페이지를 여는 하이퍼링크를 제공 합니다. 유효한 프로토콜로 시작 하지 않는 텍스트는 "http://" 앞에 붙습니다. 이 필드에는 HTTP, HTTPS, FTP, FTPS, ONENOTE 및 TEL 프로토콜만 사용할 수 있습니다.|
|`TwoOptions`|이 필드는 두 가지 옵션을 제공 합니다. 각 옵션에는 false 또는 true 값에 해당 하는 숫자 값 0 또는 1이 있습니다. 각 옵션에는 또한 true 또는 false 값을 "Yes" 및 "No", "Hot" 및 "콜드", "On" 및 "Off" 또는 표시 하려는 모든 레이블 쌍으로 표현할 수 있도록 레이블이 있습니다.|
|`Whole.None`|이 옵션은 단순히 숫자를 표시 합니다.|

## <a name="value-elements-that-are-not-supported"></a>지원 되지 않는 값 요소

다음 `of-type` 특성 값은 현재 지원 되지 않습니다.

|Value|설명|
|-----|------|
|`Whole.Duration`|이 형식 옵션은 기간 옵션 목록을 표시 하는 데 사용할 수 있습니다. 그러나 데이터베이스에 저장 된 데이터는 항상 몇 분이 됩니다. 이 필드는 드롭다운 목록과 같으며 1 분, 15 분, 30 분 등의 권장 옵션을 최대 3 일까지 제공 합니다. 사용자는 이러한 옵션을 선택할 수 있습니다. 그러나 사용자는 시간 (분)을 입력 하 여 해당 기간으로 확인할 수도 있습니다.|
|`Whole.Timezone`|이 옵션은 (GMT-12:00) 국제 날짜/시간 및 (GMT-08:00) 태평양 표준시 (미국 & 캐나다)와 같은 표준 시간대의 선택 목록을 표시 합니다. 이러한 각 영역은 숫자로 저장 됩니다. 예를 들어 표준 시간대 (GMT-08:00) 태평양 표준시 (미국 & 캐나다)의 경우 TimeZoneCode은 4입니다. 추가 정보: [TimeZoneCode 클래스 (Sdk 어셈블리)](https://docs.microsoft.com/en-us/previous-versions/dynamics-crm4/developers-guide/bb959779(v=msdn.10))|
|`Whole.Language`|이 옵션은 조직에 대해 프로 비전 된 언어 목록을 표시 합니다. 값은 언어 이름 드롭다운 목록으로 표시 되지만 데이터는 LCID 코드를 사용 하 여 숫자로 저장 됩니다. 언어 코드는 4자리 또는 5자리 로캘 ID입니다. 유효한 로캘 ID 값은 [LCID(로캘 ID) 차트](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10))에서 찾을 수 있습니다.|
|`Lookup.Simple`|특정 엔터티에 대 한 단일 참조를 허용 합니다. 모든 사용자 지정 조회는이 형식입니다.|
|`Lookup.Customer`|계정 또는 연락처 레코드에 대 한 단일 참조를 허용 합니다. 이러한 조회는 기회, 사례, 견적, 주문 및 송장 엔터티에 사용할 수 있습니다. 또한 이러한 엔터티에는 고객이 항상 한 가지 유형인 경우 사용할 수 있는 별도의 계정 및 연락처 조회가 있습니다. 또는 고객 조회를 사용 하는 대신 둘 다 포함할 수 있습니다.|
|`Lookup.Owner`|팀 또는 사용자 레코드에 대 한 단일 참조를 허용 합니다. 모든 팀 또는 사용자 소유 엔터티에는 다음 중 하나가 있습니다.|
|`Lookup.PartyList`|여러 엔터티를 여러 번 참조할 수 있습니다. 이러한 조회는 전자 메일 엔터티와 **참조** 필드 **에 있습니다** . 또한 전화 및 약속 엔터티에서 사용 됩니다.|
|`Lookup.Regarding`|여러 엔터티에 대 한 단일 참조를 허용 합니다. 이러한 조회는 활동에서 사용 되는 관련 필드에 있습니다.|
|`MultiSelectOptionSet`|다중 선택 필드를 추가 하 여 양식 (주, 빠른 생성 및 빠른 보기) 및 전자 메일 템플릿을 사용자 지정할 수 있습니다. 다중 선택 옵션 집합 필드를 추가할 때 사용자가 선택할 수 있는 값을 여러 개 지정할 수 있습니다. 사용자가 양식을 작성할 때 드롭다운 목록에 표시 되는 값을 하나, 여러 개 또는 모두 선택할 수 있습니다.|
