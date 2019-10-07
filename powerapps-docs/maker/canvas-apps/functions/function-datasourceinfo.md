---
title: DataSourceInfo 함수 | Microsoft Docs
description: PowerApps의 DataSourceInfo 함수에 대한 구문과 예제를 포함한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 33a119e1e023ed8a28bdabe9ac5caba0723476df
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985326"
---
# <a name="datasourceinfo-function-in-powerapps"></a>PowerApps의 DataSourceInfo 함수
[데이터 원본](../working-with-data-sources.md)에 대한 정보를 제공합니다.

## <a name="overview"></a>개요
데이터 원본은 사용자 환경을 최적화하도록 풍부한 정보를 제공할 수 있습니다.

[열](../working-with-tables.md#columns) 수준 정보를 사용하여 사용자 입력의 유효성을 검사하고 **[Patch](function-patch.md)** 함수를 사용하기 전에 사용자에게 즉각적인 피드백을 제공할 수 있습니다. **[Validate](function-validate.md)** 함수는 이와 동일한 정보를 사용합니다.

예를 들어 데이터 원본 수준의 정보를 사용하여 [레코드](../working-with-tables.md#records)를 편집하고 생성할 권한이 없는 사용자에 대한 **편집** 및 **새로 만들기** 단추를 비활성화하거나 숨길 수 있습니다.

데이터 원본이 제공하는 정보의 양은 전혀 제공하지 않는 경우를 포함하여 다양합니다.  [컬렉션](../working-with-data-sources.md#collections)은 정보를 제공하지 않습니다. 정보가 제공되지 않으면 기본값이 사용되거나 *공백*이 반환됩니다.

## <a name="description"></a>설명
### <a name="column-information"></a>열 정보
**DataSourceInfo**를 사용하면 데이터 원본의 특정 열에 대한 정보를 얻을 수 있습니다.  

| 정보 인수 | 결과 형식 | 설명 |
| --- | --- | --- |
| **DataSourceInfo.DisplayName** |문자열 |열의 표시 이름입니다. 표시 이름을 정의하지 않으면 열 이름이 반환됩니다. |
| **DataSourceInfo.MaxLength** |번호 |열이 보유할 수 있는 최대 문자 수입니다. 문자열이 포함된 열에만 적용됩니다. 최대값을 설정하지 않으면 *공백*이 반환됩니다. |
| **DataSourceInfo.MaxValue** |번호 |열이 보유할 수 있는 최대 숫자 값입니다. 숫자가 포함된 열에만 적용됩니다. 최대값을 설정하지 않으면 *공백*이 반환됩니다. |
| **DataSourceInfo.MinValue** |번호 |열이 보유할 수 있는 최소 숫자 값입니다. 숫자가 포함된 열에만 적용됩니다. 최소값을 설정하지 않으면 *공백*이 반환됩니다. |
| **DataSourceInfo.Required** |부울 |이 열에 값이 필요한가요? 데이터 원본에 설정하지 않으면 **false**가 반환됩니다. |

세 번째 인수는 문자열 형식의 열 이름입니다.  예를 들어 **People** 컬렉션의 **Phone** 열은 큰따옴표를 포함하여 **"Phone"** 으로 전달됩니다.

### <a name="data-source-information"></a>데이터 원본 정보
**DataSourceInfo**를 사용하여 데이터 원본 전체에 대한 정보를 얻을 수도 있습니다.  

| 정보 인수 | 결과 형식 | 설명 |
| --- | --- | --- |
| **DataSourceInfo.AllowedValues** |부울 |이 데이터 원본에 대해 사용자에게 부여할 수 있는 권한 유형은 무엇인가요? 데이터 원본에 설정하지 않으면 *공백*이 반환됩니다. |
| **DataSourceInfo.CreatePermission** |부울 |현재 사용자에게 이 데이터 원본에 레코드를 만들 권한이 있나요? 데이터 원본에 설정하지 않으면 **true**가 반환됩니다. |
| **DataSourceInfo.DeletePermission** |부울 |현재 사용자에게 이 데이터 원본의 레코드를 삭제할 권한이 있나요? 데이터 원본에 설정하지 않으면 **true**가 반환됩니다. |
| **DataSourceInfo.EditPermission** |부울 |현재 사용자에게 이 데이터 원본의 레코드를 편집할 권한이 있나요? 데이터 원본에 설정하지 않으면 **true**가 반환됩니다. |
| **DataSourceInfo.ReadPermission** |부울 |현재 사용자에게 이 데이터 원본의 레코드를 읽을 권한이 있나요? 데이터 원본에 설정하지 않으면 **true**가 반환됩니다. |

## <a name="syntax"></a>구문
**DataSourceInfo**( *DataSource*, *Information*, *ColumnName* )

* *DataSource* – 필수 항목입니다. 사용할 데이터 원본입니다.
* *Information* – 필수 항목입니다. 검색할 정보 유형입니다.
* *ColumnName* – 선택 항목입니다. 열 수준 정보의 경우 열 이름은 문자열 형식입니다. **Phone** 열은 큰따옴표를 포함하여 **"Phone"** 으로 전달됩니다. 데이터 원본 레벨에 대한 정보는 *ColumnName* 인수를 사용할 수 없습니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함된 SharePoint 및 Excel 데이터 원본의 경우 각 공백을 **"\_x0020\_"** 으로 지정합니다. 예를 들어, **"Column Name"** 은 **"Column_x0020_Name"** 으로 지정합니다.

## <a name="examples"></a>예
이 섹션의 예제에서는 **IceCream**이라는 데이터 원본을 사용합니다.

![](media/function-datasourceinfo/icecream.png)

데이터 원본에는 다음 정보도 제공됩니다.

* **Quantity**의 표시 이름은 "보유 물량"입니다.
* **Flavor**의 최대 길이는 30자입니다.
* **Flavor** 열은 값을 포함해야 합니다. **Quantity** 열은 필요하지 않습니다.
* 최소 **Quantity**는 0입니다.
* 최대 **Quantity**는 100입니다.
* 현재 사용자는 **IceCream** 데이터 원본의 레코드를 읽고 편집할 수 있지만 레코드를 생성하거나 삭제할 수는 없습니다.

| 수식 | 설명 | 결과 |
| --- | --- | --- |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DisplayName,&nbsp;"Quantity"&nbsp;)** |**IceCream** 데이터 원본의 **Quantity** 열에 대한 표시 이름을 반환합니다. |"보유 물량" |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxLength,&nbsp;"Flavor"&nbsp;)** |**IceCream** 데이터 원본의 **Flavor** 열에 대한 문자열의 최대 길이를 반환합니다. |30 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Flavor"&nbsp;)** |**IceCream** 데이터 원본의 **Flavor** 열이 필요한가요? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Quantity"&nbsp;)** |**IceCream** 데이터 원본의 **Quantity** 열이 필요한가요? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxValue,&nbsp;"Quantity"&nbsp;)** |**IceCream** 데이터 원본의 **Quantity** 열에 대한 최대 숫자 값을 반환합니다. |100 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MinValue,&nbsp;"Quantity"&nbsp;)** |**IceCream** 데이터 원본의 **Quantity** 열에 대한 최소 숫자 값을 반환합니다. |0 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.ReadPermission)** |현재 사용자가 **IceCream** 데이터 원본의 레코드를 읽을 수 있나요? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.EditPermission)** |현재 사용자가 **IceCream** 데이터 원본의 레코드를 편집할 수 있나요? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.CreatePermission)** |현재 사용자가 **IceCream** 데이터 원본에 레코드를 생성할 수 있나요? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DeletePermission)** |현재 사용자가 **IceCream** 데이터 원본의 레코드를 삭제할 수 있나요? |**false** |

