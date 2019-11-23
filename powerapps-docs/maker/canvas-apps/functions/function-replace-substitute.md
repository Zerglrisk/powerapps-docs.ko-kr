---
title: Replace 및 Substitute 함수 | Microsoft Docs
description: PowerApps의 Replace 및 Substitute 함수에 대한 구문을 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff0e016f6ab1ad4f66651ccd3cfa2711f1d85a38
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992381"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>PowerApps의 Replace 및 Substitute 함수
텍스트 문자열의 일부를 다른 문자열로 바꿉니다.

## <a name="description"></a>설명
**Replace** 함수는 시작 위치 및 길이를 통해 바꿀 텍스트를 식별합니다.  

**Substitute** 함수는 문자열을 일치시킴으로써 바꿀 텍스트를 식별합니다. 일치 하는 항목이 두 개 이상 있는 경우 모두 바꾸거나 바꿀 수 있습니다.

단일 문자열을 전달하는 경우 반환 값은 수정된 문자열입니다. 문자열이 포함된 단일 열 [테이블](../working-with-tables.md)을 전달하는 경우 반환 값은 수정된 문자열의 단일 열 테이블입니다. 여러 열 테이블이 있는 경우 [테이블 작업](../working-with-tables.md)에 설명된 대로 단일 열 테이블로 만들 수 있습니다.

## <a name="syntax"></a>구문
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String* - 필수 항목이며, 연산을 수행할 문자열입니다.
* *StartingPosition* - 필수 항목입니다. 교체를 시작할 문자 위치입니다. *String*의 첫 번째 문자는 위치 1입니다.
* *NumberOfCharacters* - 필수 항목입니다. *String*에서 교체할 문자 수입니다.
* *NewString* - 필수 항목입니다. 대체 문자열입니다. 이 인수의 문자 수는 *NumberOfCharacters* 인수와 다를 수 있습니다.

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String* - 필수 항목이며, 연산을 수행할 문자열입니다.
* *OldString* - 필수 항목입니다. 교체할 문자열입니다.
* *NewString* - 필수 항목입니다. 대체 문자열입니다. *OldString* 및 *NewString*은 길이가 다를 수 있습니다.
* *InstanceNumber* -선택 사항입니다. *문자열이* 둘 이상의 인스턴스를 포함 하는 경우 바꿀 *oldstring* 의 인스턴스를 지정 하려면이 인수를 사용 합니다. 이 인수를 지정 하지 않으면 모든 인스턴스가 대체 됩니다.

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 필수 항목입니다. 연산을 수행할 문자열의 단일 열 테이블입니다.
* *StartingPosition* - 필수 항목입니다. 교체를 시작할 문자 위치입니다.  테이블에 있는 각 문자열의 첫 번째 문자는 위치 1에 있습니다.
* *NumberOfCharacters* - 필수 항목입니다. 각 문자열에서 교체할 문자 수입니다.
* *NewString* - 필수 항목입니다.  대체 문자열입니다. 이 인수의 문자 수는 *NumberOfCharacters* 인수와 다를 수 있습니다.

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 필수 항목입니다. 연산을 수행할 문자열의 단일 열 테이블입니다.
* *OldString* - 필수 항목입니다.  교체할 문자열입니다.
* *NewString* - 필수 항목입니다.  대체 문자열입니다. *OldString* 및 *NewString*은 길이가 다를 수 있습니다.
* *InstanceNumber* -선택 사항입니다. *문자열이* 둘 이상의 인스턴스를 포함 하는 경우 바꿀 *oldstring* 의 인스턴스를 지정 하려면이 인수를 사용 합니다. 이 인수를 지정 하지 않으면 모든 인스턴스가 대체 됩니다.

## <a name="examples"></a>예

| 수식 | 설명 | 결과 |
|---------|-------------|--------|
| **Replace ("abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*")** | "Abcdefghijk"에서 5 개 문자를 단일 "*" 문자로 바꿉니다 (6 번째 문자 ("f")로 시작). | "abcde...z * k" |
| **Replace (&nbsp;"2019",&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | "2019"의 마지막 두 문자를 "20"으로 바꿉니다. | "2020" |
| **Replace (&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | "123456"의 처음 세 문자를 단일 "_" 문자로 바꿉니다. | "_456" | 
| **대체 (&nbsp;"Sales&nbsp;Data",&nbsp;"Sales",&nbsp;"Cost"&nbsp;)** | "Cost" 문자열을 "Sales"로 대체 합니다. | "비용 데이터" | 
| **대체 ("Quarter&nbsp;1,&nbsp;2018", "1", "2", 1)** | 네 번째 인수 (*InstanceNumber*)가 1과 함께 제공 되므로 "1"의 첫 번째 인스턴스만 "2"로 대체 합니다. |  "사분기 2, 2018" |
| **대체 ("Quarter&nbsp;1,&nbsp;2011", "1", "2", 3)** | 네 번째 인수 (*InstanceNumber*)가 3과 함께 제공 되므로 "1"의 세 번째 인스턴스만 "2"로 대체 합니다. | "Quarter 1, 2012" |
| **대체 ("Quarter&nbsp;1,&nbsp;2011", "1", "2")** | 네 번째 인수 (*InstanceNumber*)가 제공 되지 않았기 때문에 "1"의 모든 인스턴스를 "2"로 대체 합니다. | "사분기 2, 2022" |
| **Replace (<br>[&nbsp;"Quarter&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;2,&nbsp;2011",<br>"Quarter&nbsp;4,&nbsp;2019"],<br>9, 1, "3")** | 단일 열 테이블의 각 레코드에서 아홉 번째 문자를 "3"으로 바꿉니다. | [&nbsp;"Quarter&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Quarter&nbsp;3,&nbsp;2019"&nbsp;] |
| **대체 (<br>[&nbsp;"분기&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3", 1)** | 네 번째 인수 (*InstanceNumber*)는 값 1과 함께 제공 되므로 단일 열 테이블의 각 레코드에서 "1"의 첫 번째 인스턴스만 "3"으로 대체 합니다. | [&nbsp;"분기&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Q3,&nbsp;2019"&nbsp;] |
| **대체 (<br>[&nbsp;"분기&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3")** | 네 번째 인수 (*InstanceNumber*)가 제공 되지 않으므로는 단일 열 테이블의 각 레코드에서 "1"의 모든 인스턴스를 "3"으로 대체 합니다. | [&nbsp;"분기&nbsp;3,&nbsp;2038",<br>"Quarter&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 


