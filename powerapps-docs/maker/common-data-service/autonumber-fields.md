---
title: Common Data Service의 자동 번호 매기기 필드 | MicrosoftDocs
description: 자동 번호 매기기 필드를 만들고 관리하고 사용하는 방법 이해
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: daemelia
ms.assetid: null
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="autonumber-fields"></a>자동 번호 매기기 필드

자동 번호 매기기 필드는 만들 때마다 영숫자 문자열을 자동으로 생성하는 필드입니다. 제작자는 이러한 필드의 형식을 원하는 대로 사용자 지정하고 시스템을 사용하여 런타임에 자동으로 채우는 값을 생성할 수 있습니다.

자동 번호 매기기 필드는 공식적으로 그 위에 추가 기능이 내장된 텍스트 필드이지만, [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)는 단순히 **자동 번호 매기기**를 **텍스트** 범주 아래에 별개의 데이터 형식으로 노출하여 이 개념을 간소화합니다. [클래식 솔루션 탐색기](use-solution-explorer.md#classic-solution-explorer)가 자동 번호 매기기 필드 만들기 또는 관리를 지원하지 않는지 확인하는 것이 중요합니다.

자동 번호 매기기 필드를 만들려면 동일한 단계에 따라 [필드를 만들고](create-edit-field-portal.md#create-a-field) **데이터 형식** 드롭다운 목록 상자에서 **자동 번호 매기기**를 선택하기만 하면 됩니다. 

필드를 열고 **데이터 형식** 드롭다운 목록 상자에서 **자동 번호 매기기**를 선택하여 기존 텍스트 필드에서 자동 번호 매기기 기능을 활성화할 수도 있습니다. 마찬가지로 필드를 열고 **데이터 형식** 드롭다운 목록 상자에서 다른 옵션을 선택하여 언제든지 자동 번호 매기기 기능을 비활성화할 수도 있습니다.

> [!NOTE]
>자동 번호 값은 레코드가 시작될 때 데이터베이스에 의해 미리 선택됩니다. 레코드가 시작되었지만 취소된 경우 지정된 번호가 사용되지 않습니다. 이 시간 동안 다음 순서 번호로 다른 레코드가 완료되면 레코드의 자동 번호 매기기에 공백이 생깁니다.

## <a name="autonumber-types"></a>자동 번호 매기기 유형

자동 번호 매기기 필드를 쉽게 만들기 위해 가장 일반적인 시나리오를 캡처할 수 있도록 미리 정의된 기본 자동 번호 매기기 유형이 몇 가지 있습니다. 

### <a name="string-prefixed-number"></a>문자열 접두사 번호

가장 일반적인 자동 번호 매기기 형식은 간단한 문자열 접두사 번호입니다. 이 유형을 선택하면 자동 번호 매기기는 선택적 문자열 상수 접두사로 자동으로 증가하는 숫자로 구성됩니다. 예를 들어 접두사 *Contoso*를 사용하는 문자열 접두사 번호는 *Contoso-1000*, *Contoso-1001*, *Contoso-1002* 등의 레코드를 생성합니다.

### <a name="date-prefixed-number"></a>날짜 접두사 번호

또 다른 일반적인 자동 번호 매기기 형식은 날짜 접두사 번호입니다. 이 유형을 선택하면 자동 번호 매기기는 날짜 형식의 접두사로 자동으로 증가하는 숫자로 구성됩니다. 레코드의 날짜 부분은 UTC 시간에 레코드를 만든 현재 날짜 및 시간을 반영합니다. 선택할 수 있는 다양한 날짜 형식을 제공했습니다.
예를 들어, 날짜 접두사 번호는 현재 날짜와 선택한 날짜 형식에 따라 *2019-26-02-1000*, *2019-27-02-1000*, *2019-28-02-1000* 등의 레코드를 생성합니다.

### <a name="custom"></a>사용자 지정

구체적인 사용 사례가 있는 고급 제작자의 경우 자동 번호 매기기 필드의 원하는 형식을 완벽하게 사용자 지정하는 옵션을 제공합니다. 형식은 자동으로 증가 숫자, 서식이 지정된 날짜 또는 임의의 영숫자 시퀀스 등 문자열 상수로 구성될 수 있습니다.
사용자 지정 형식을 정의하는 방법에 대한 자세한 내용은 [자동 번호 매기기 형식 옵션](https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options)을 참조하십시오.

## <a name="seed-values"></a>시드 값

자동 번호 매기기 필드의 시드 값은 형식의 숫자 부분에 사용되는 시작 번호입니다. 예를 들어 자동 번호 매기기 필드가 *Contoso-1000*, *Contoso-1001*, *Contoso-1002* 등의 레코드를 생성하도록 하려는 경우 이것은 숫자 시퀀스가 시작하는 값이므로 원하는 시드 값은 1000입니다. 자동 번호 매기기 필드에는 1000의 기본 시드 값이 있지만 원하는 경우 사용자 지정 시드 값을 설정할 수 있습니다. 


> [!IMPORTANT]
> 시드를 설정하면 현재 환경에서 지정된 특성의 현재 숫자 값만 변경됩니다. 시드 값은 다른 환경에서 가져올 때 솔루션에 포함되지 않습니다. 

## <a name="create-an-autonumber-field"></a>자동 번호 매기기 필드 만들기
  
1.  [PowerApps 포털](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)에 로그인합니다.
  
2.  왼쪽 창에서 **데이터**를 확장하고 **엔터티**를 선택합니다.
  
3.  자동 번호 매기기 필드를 추가할 엔터티를 선택한 다음 **필드** 탭을 선택합니다.
  
4.  도구 모음에서 **추가** 필드를 선택합니다.  
  
5.  오른쪽 창에서 **표시 이름**을 입력하고 **데이터 형식**에 대해 **자동 번호 매기기**를 선택합니다.

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "자동 번호 매기기 필드 만들기")
  
6. 필요에 따라 선택적 필드를 설정합니다. 추가 정보: [필드 만들기 및 편집](create-edit-field-portal.md#create-a-field)

7. 자동 번호 매기기 유형을 선택하거나 기본 **문자열 접두사 번호** 옵션을 유지합니다.

8. 시드 값을 사용자 지정하거나 기본값인 **1000**을 유지합니다.

9. **완료**를 선택합니다.

## <a name="see-also"></a>참조
 [PowerApps포털을 사용하여 Common Data Service용 필드 만들기 및 편집](create-edit-field-portal.md)
