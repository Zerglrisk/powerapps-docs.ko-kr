---
title: GUID 함수 | Microsoft Docs
description: Power Apps에서 GUID 함수에 대 한 구문을 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88028d2dc4016d294e051ecff66b590996b57966
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730859"
---
# <a name="guid-function-in-power-apps"></a>Power Apps의 GUID 함수
GUID([전역적으로 고유 식별자](https://en.wikipedia.org/wiki/Universally_unique_identifier)) 문자열을 GUID 값으로 변환하거나 새 GUID 값을 만듭니다.

## <a name="description"></a>설명
**GUID** 함수를 사용하여 GUID의 16진수 표현을 포함하는 문자열을 데이터베이스로 전달할 수 있는 GUID 값으로 변환합니다. GUID 값은 Common Data Service 및 SQL Server와 같은 데이터베이스 시스템에서 키로 사용 됩니다.

전달된 문자열에는 대문자 또는 소문자가 포함될 수 있지만, 다음 형식 중 하나에는 32자리 16진수여야 합니다.

- **"123e4567-e89b-12d3-a456-426655440000"** (표준 위치의 하이픈)
- **"123e4567e89b12d3a456426655440000"** (하이픈 없음)

인수를 지정하지 않으면 이 함수는 새 GUID를 만듭니다.

GUID 값을 문자열로 변환하려면 문자열 컨텍스트에서 사용합니다. GUID 값은 하이픈과 소문자로 구성된 16진수 표현 문자열로 변환됩니다. 

새 GUID를 생성 하는 경우이 함수는 의사 (pseudo) 난수를 사용 하 여 버전 4 [IETF RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) GUID를 만듭니다. 문자열을 GUID로 변환 하는 경우이 함수는 32 자리의 16 진수 문자열을 허용 하 여 모든 GUID 버전을 지원 합니다.

## <a name="volatile-functions"></a>일시적 함수
**GUID**는 인수 없이 사용되는 일시적 함수입니다. 이러한 함수는 평가될 때마다 다른 값을 반환합니다.  

데이터 흐름 수식에 사용할 경우 일시적 함수는 표시되는 수식을 다시 계산하는 경우에만 다른 값을 반환합니다. 수식에서 변경되는 내용이 없으면 앱 실행 내내 같은 값을 갖습니다.

예를 들어 **텍스트** 속성이 **GUID()** 로 설정된 레이블 컨트롤은 앱이 활성 상태인 동안에는 변경되지 않습니다. 앱을 닫았다가 다시 여는 것만 다른 값이 발생합니다.

함수가 다른 내용이 변경된 수식의 일부인 경우 다시 평가됩니다. 예를 들어 **레이블** 컨트롤의 **텍스트** 속성을 이 수식으로 설정하면 사용자가 **텍스트 입력** 컨트롤의 값을 변경할 때마다 GUID가 생성됩니다.

**TextInput1.Text & " " & GUID()**

[동작 수식](../working-with-formulas-in-depth.md)에서 사용될 경우 **GUID**는 수식이 계산될 때마다 평가됩니다. 자세한 내용은 이 항목 뒷부분에 있는 예제를 참조하세요.

## <a name="syntax"></a>구문
**GUID**( [ *GUIDString* ] )

* *GUIDString* – 선택 사항입니다.  GUID의 16진수 표현을 포함하는 텍스트 문자열입니다. 문자열이 제공되지 않으면 새 GUID가 생성됩니다.

## <a name="examples"></a>예

#### <a name="basic-usage"></a>기본 사용법

16진수 문자열 표현을 기반으로 하는 GUID 값을 반환하려면:

* **GUID( "0f8fad5b-d9cb-469f-a165-70867728950e" )**

하이픈 없이 GUID 문자열을 제공할 수도 있습니다. 이 수식은 동일한 GUID 값을 반환합니다.

* **GUID( "0f8fad5bd9cb469fa16570867728950e" )**

컨텍스트에서 사용하여 새 데이터베이스 레코드의 **상태** 필드를 잘 설정된 값으로 설정합니다.

* **패치( 제품, 기본값( 제품 ), { Status: GUID( "F9168C5E-CEB2-4faa-B6BF-329BF39FA1E4" ) } )**

사용자에게 GUID를 표시하지 않을 수도 있지만 GUID를 사용하면 응용 프로그램을 디버그하는 데 도움이 될 수 있습니다. 이전 예에서 만든 레코드에서 **상태** 필드 값을 표시하려면 **레이블** 컨트롤의 **텍스트** 속성을 다음 수식으로 설정합니다.

* **첫 번째(제품).상태**

**레이블** 컨트롤에 **f9168c5e-ceb2-4faa-b6bf-329bf39fa1e4**가 표시됩니다.

#### <a name="create-a-table-of-guids"></a>GUID 테이블 만들기

1. **[단추](../controls/control-button.md)** 컨트롤의 **[OnSelect](../controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.

    **ClearCollect( NewGUIDs, ForAll( [ 1, 2, 3, 4, 5 ], GUID() ) )**

    이 수식은 다섯 번 반복하는 데 사용되는 단일 열 테이블을 만들어 5개의 GUID를 생성합니다.

1. **[데이터 테이블](../controls/control-data-table.md)** 컨트롤을 추가하고, 해당 **항목** 속성을 **NewGUIDs**로 설정하고, **값** 필드를 표시합니다.

1. Alt 키를 누른 채 클릭하거나 눌러 단추를 선택합니다.

    데이터 테이블에는 다음과 같은 GUID 목록이 표시됩니다.

    ![다섯 개의 다른 GUID 값이 있는 데이터 테이블을 보여주는 화면](media/function-guid/guid-collection-1.png)

1. 단추를 다시 선택하여 다른 GUID 목록을 표시합니다.

    ![다섯 개의 다른 GUID 값의 새 집합이 있는 데이터 테이블을 보여주는 동일한 화면](media/function-guid/guid-collection-2.png)

테이블 대신 단일 GUID를 생성하려면 이 수식을 사용합니다.

**Set( NewGUID, GUID() )**
