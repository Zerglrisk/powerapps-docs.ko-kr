---
title: 캔버스 앱에 텍스트, 날짜 및 시간 표시 | Microsoft Docs
description: PowerApps에서 캔버스 앱에 텍스트, 날짜 및 시간 표시
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/16/2016
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2e0f365a5b41655188a3adfe02b721e6a5ef9bcd
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71988623"
---
# <a name="show-text-dates-and-times-in-powerapps"></a>PowerApps에서 텍스트, 날짜 및 시간 표시
PowerApps에서 날짜와 시간을 캔버스 앱에 추가하고 형식을 지정하여 적절한 수준의 세부 정보를 표시하거나 로캘을 반영합니다. 두 날짜 사이의 시간을 계산하거나 지정한 날짜 이전 또는 이후의 특정 시간에 해당하는 날짜를 계산합니다. 날짜를 일, 월 및 연도에 대한 별도의 값으로 변환하고 시, 분 및 초에 대한 별도의 값으로 변환합니다.

예를 들어 주식 거래 또는 고객 상담과 관련된 사용자의 데이터, 외부 원본의 데이터 또는 PowerApps에서 만든 다른 앱의 데이터를 추가합니다. 해당 데이터에 밀리초까지의 시간이 포함되어 있는 경우 간단히 하기 위해 가장 가까운 분으로 반올림합니다. 중요 시점까지 남아 있는 일 수를 계산합니다. 5일마다 고객 상담을 예약하려면 해당 날짜를 자동으로 계산합니다. 1985년 5월 10일이 일, 월 및 연도에 대한 별도의 필드에 저장되는 경우 단일 값으로 통합합니다. 반대로 앱에서 별도로 관리하는 경우 각 날짜를 별도의 값으로 구분합니다.

## <a name="prerequisites"></a>필수 조건

* PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 입력하여 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
* PowerApps에서 앱을 만들거나 기존 앱을 엽니다.
* PowerApps에서 [컨트롤 구성](add-configure-controls.md)을 어떻게 하는지 알아봅니다.

## <a name="show-text-in-a-label-control"></a>레이블 컨트롤에 텍스트 표시
**[Text](controls/properties-core.md)** 속성의 값을 설정하여 **[레이블](controls/control-text-box.md)** 컨트롤에 텍스트를 표시합니다. 컨트롤에 직접 입력하거나 수식 입력줄에 식을 입력하여 이 속성을 설정합니다.

* 컨트롤에 직접 입력하면 입력한 내용이 정확하게 표시됩니다.
* 수식 입력줄에 식을 입력하면 컨트롤에 식의 결과가 표시됩니다.

다음은 몇 가지 예제입니다.

1. **ShowText**라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Now()**
   
    컴퓨터가 "en-us" 로캘로 설정되어 있으면 현재 날짜와 시간이 다음 형식으로 나타납니다. <br>*mm/dd/yyyy hh:mm AM/PM*
   
    컴퓨터가 "fr-fr"과 같은 로캘로 설정되어 있으면 현재 날짜와 시간이 다음 형식으로 나타납니다. <br>*dd/mm/yyyy hh:mm AM/PM*
2. **ShowText**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateDiff(Today(), DateValue("01/01/2020"))**
   
    ![현재 날짜와 2020년 1월 1일 사이의 일 수](./media/show-text-dates-times/date-diff-text.png)
   
    컨트롤에서는 다음 함수를 사용하여 현재 날짜와 2020년 1월 1일 사이의 일 수를 표시합니다.
   
   * **DateDiff** - 두 날짜 사이의 일, 분기 또는 년 수를 계산합니다.
   * **Today** - 현재 날짜를 값으로 계산합니다.
   * **DateValue** - 큰따옴표 사이에 표시된 리터럴 문자열을 계산할 수 있는 값으로 변환합니다.
3. **BirthDate**라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하고 **ShowText** 아래로 이동합니다.

4. **BirthDate**에서 생년월일의 월과 일을 입력합니다(예: **05/18**).

5. **ShowText**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateDiff(Today(), DateValue(BirthDate.Text))**
   
    ![현재 날짜와 생일 사이의 일 수](./media/show-text-dates-times/birth-diff.png)
   
    **ShowText**는 현재 날짜와 **BirthDate**에 입력한 날짜 사이의 일수를 표시합니다. 생일이 이미 올해에 발생한 경우 **ShowText**는 음수 값을 표시합니다.

## <a name="format-dates-and-times-by-using-datetimevalue"></a>DateTimeValue를 사용하여 날짜 및 시간 형식 지정
날짜와 시간을 텍스트 문자열에서 여러 가지 방법으로 형식을 지정하고 계산에 사용할 수 있는 값으로 변환합니다. 기본 제공 옵션 및 사용자 지정 옵션을 사용하여 형식을 지정합니다.

> [!NOTE]
> **[DateTimeValue](functions/function-datevalue-timevalue.md)** 및 **[DateValue](functions/function-datevalue-timevalue.md)** 함수는 다음 형식의 날짜를 값으로 변환할 수 있습니다.  
> 
> * MM/DD/YYYY  
> * DD/MM/YYYY  
> * DD Mon YYYY  
> * Month DD, YYYY  
> 
> 

1. **ArrivalDateTime**이라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하고 날짜와 시간을 다음 형식으로 입력합니다.
   <br>**5/10/85 6:15 AM**
2. **ShowDate**라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateTimeValue(ArrivalDateTime.Text)**
   
    ![날짜/시간을 텍스트에서 값으로 변환](./media/show-text-dates-times/date-value.png)
   
    **ShowDate**는 입력한 것과 동일한 정보를 표시하지만 텍스트에서 값으로 변환되고 다른 형식으로 지정되었습니다. 예를 들어 연도는 두 자리 대신 네 자리 숫자로 표시됩니다.
3. **ShowDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 변경합니다.
   <br>**DateTimeValue(ArrivalDateTime.Text, "fr")**
   
    ![날짜/시간 값을 프랑스어 형식으로 표시합니다.](./media/show-text-dates-times/date-value-fr.png)
   
    **ShowDate**는 프랑스어 사용자가 예상한 대로 해당 월의 이전 일을 표시합니다.
   
   > [!TIP]
   > Intellisense에서 다른 로캘 목록을 표시하려면 수식에서 닫는 따옴표 및 **fr**을 제거하고 여는 따옴표는 그대로 유지합니다.
   > 
   > ![로캘 목록 표시](./media/show-text-dates-times/locale-list.png)
   > 
   > 
4. 여러 기본 제공 형식 중 하나를 사용하려면 **ShowDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 변경합니다.
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), DateTimeFormat.LongDateTime)**
   
    ![날짜/시간 값을 프랑스어 형식으로 표시합니다.](./media/show-text-dates-times/long-date-time.png)
   
    **ShowDate**는 요일, 날짜 및 시간을 표시합니다.
   
   > [!TIP]
   > **DateTimeFormat** 매개 변수는 다른 몇 가지 기본 제공 형식을 지원합니다. 해당 목록을 표시하려면 수식에서 **LongDateTime**을 제거합니다.
   > 
   > 
5. 사용자 지정 형식을 사용하려면 **ShowDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 변경합니다.
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), "mm/dd/yyyy hh:mm:ss.fff AM/PM")**
   
    ![날짜/시간 값을 프랑스어 형식으로 표시합니다.](./media/show-text-dates-times/format-milliseconds.png)
   
    **ShowDate**는 날짜/시간 값을 밀리초를 포함하여 지정한 형식으로 표시합니다.
   
   > [!TIP]
   > 시간을 가장 가까운 1/10초 또는 1/100초 단위로 반올림하려면 수식에 **hh:mm:ss.f** 또는 **hh:mm:ss.ff**를 지정합니다.
   > 
   > 

## <a name="format-a-date-by-using-datevalue"></a>DateValue를 사용하여 날짜 서식 지정

1. **ArrivalDate**라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가한 다음 날짜를 입력합니다(예: **5/10/85**).

2. **FormatDate**라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateValue(ArrivalDate.Text)**
   
    **FormatDate**는 입력한 날짜를 표시합니다. 단, 연도는 4자리 숫자로 표시됩니다.
3. **FormatDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateValue(ArrivalDate.Text, "fr")**
   
    **FormatDate**는 프랑스 사용자가 기대하는 것처럼 그 달 전날을 표시합니다.
4. 여러 기본 제공 형식 중 하나를 사용하려면 **FormatDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Text(DateValue(ArrivalDate.Text), DateTimeFormat.LongDate)**
   
    **FormatDate**는 요일, 월, 일 및 연도를 표시합니다.
5. 사용자 지정 형식을 사용하려면 **FormatDate**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Text(DateValue(ArrivalDate.Text), "yy/mm/dd")**
   
    **FormatDate**는 사용자가 지정한 형식으로 날짜를 표시합니다.

## <a name="format-a-time-using-datetimevalue"></a>DateTimeValue를 사용하여 시간 형식 지정

1. **ArrivalTime** 이라는 이름의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가한 다음 **6:15 AM**을 입력합니다.

2. **ShowTime**이라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가합니다.

3. 여러 기본 제공 형식 중 하나를 사용하려면 **ShowTime**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Text(DateTimeValue(ArrivalTime.Text), DateTimeFormat.LongTime)**
   
    **ShowTime**은 지정한 시간(초 포함)을 표시합니다.
4. 사용자 지정 형식을 사용하려면 **ShowTime**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Text(DateTimeValue(ArrivalTime.Text), "hh:mm:ss.fff AM/PM")**
   
    **ShowTime**은 초 및 밀리초를 포함하여 지정한 시간을 표시합니다.
   
   > [!TIP]
   > 시간을 가장 가까운 1/10 또는 1/100초 단위로 반올림하려면 수식에서 **hh:mm:ss.f** 또는 **hh:mm:ss.ff**를 입력합니다.
   > 
   > 

## <a name="show-the-time-between-dates"></a>날짜 사이의 시간 표시

1. **Start**와 **End**라는 두 개의 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가합니다.

2. **Start**에서 **4/1/2015**를 입력하고, **End**에서 **1/1/2016**을 입력합니다.

3. **DateDiff**라는 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text))**
   
    ![두 날짜의 비교](./media/show-text-dates-times/date-diff.png)
   
    **DateDiff**는 2015년 4월 1일 및 2016년 1월 1일 사이의 일 수인 **275**를 표시합니다.
4. **DateDiff**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text), Months)**
   
    **DateDiff**는 2015년 4월 1일 및 2016년 1월 1일 사이의 개월 수인 **9**를 표시합니다. 시간을 해당 단위로 표시하려면 **Months**를 **Quarters** 또는 **Years**로 바꿉니다.

## <a name="identify-a-date-before-or-after-another-date"></a>다른 날짜 이전 또는 이후의 날짜 식별

1. **Start**라는 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하고 **5/10/1985**를 입력합니다.

2. **DateAdd**라는 이름의 **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateAdd(DateValue(Start.Text), 3)**
   
    ![3일 더하기](./media/show-text-dates-times/date-add.png)
   
    **DateAdd**는 **Start**에 있는 날짜로부터 3일 후인 **5/13/1985**를 표시합니다.
3. **DateAdd**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**DateAdd(DateValue(Start.Text), -3)**
   
    ![3일 빼기](./media/show-text-dates-times/date-subtract.png)
   
    **DateAdd**는 **Start**에 있는 날짜로부터 3일 전인 **5/7/1985**를 표시합니다.
4. **DateAdd**의 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 변경합니다.
   <br>**DateAdd(DateValue(Start.Text), 3, Months)**
   
    ![3개월 더하기](./media/show-text-dates-times/date-add-months.png)
   
    레이블에서 **Start**에 있는 날짜로부터 3개월 후인 **8/10/1985**를 표시합니다. **Months**를 **Quarters** 또는 **Years**로 바꿔 **Start**에 있는 날짜 전후로부터 지정된 분기 수 또는 년 수에 해당하는 날짜를 식별합니다.

## <a name="calculate-dates-based-on-years-months-and-days"></a>년, 월, 일을 기준으로 날짜 계산

1. **Year**, **Month** 및 **Day**라는 3개의 **[드롭다운](controls/control-drop-down.md)** 컨트롤을 추가합니다.

2. **Year**의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Table({Year:"2014"}, {Year:"2015"}, {Year:"2016"})**

3. **Month**의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Table({Month:"1"}, {Month:"2"}, {Month:"3"}, {Month:"4"}, {Month:"5"}, {Month:"6"}, {Month:"7"}, {Month:"8"}, {Month:"9"}, {Month:"10"}, {Month:"11"}, {Month:"12"})**

4. **Day**의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Table({Day:"1"}, {Day:"2"}, {Day:"3"}, {Day:"4"}, {Day:"5"}, {Day:"6"}, {Day:"7"}, {Day:"8"}, {Day:"9"}, {Day:"10"}, {Day:"11"}, {Day:"12"}, {Day:"13"}, {Day:"14"}, {Day:"15"}, {Day:"16"}, {Day:"17"}, {Day:"18"}, {Day:"19"}, {Day:"20"}, {Day:"21"}, {Day:"22"}, {Day:"23"}, {Day:"24"}, {Day:"25"}, {Day:"26"}, {Day:"27"}, {Day:"28"}, {Day:"29"}, {Day:"30"}, {Day:"31"})**

5. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**Text(Date(Value(Year.Selected.Value), Value(Month.Selected.Value), Value(Day.Selected.Value)), DateTimeFormat.LongDate)**
   
    **Wednesday, January 1, 2014**가 기본적으로 나열됩니다. **[드롭다운](controls/control-drop-down.md)** 컨트롤에서 다른 값을 선택하여 **[레이블](controls/control-text-box.md)** 컨트롤의 날짜를 변경합니다.

예상하지 않은 데이터를 변환해야 할 수도 있습니다. **[드롭다운](controls/control-drop-down.md)** 컨트롤 대신 **[텍스트 입력](controls/control-text-input.md)** 컨트롤을 추가하면 사용자가 5월 45일과 같은 잘못된 날짜를 입력할 수 있습니다. **[Date](functions/function-date-time.md)** 함수는 다음과 같은 방법으로 비정형 데이터를 처리합니다.

* 연도 값이 0과 1899(포함) 사이에 있으면 함수에서 1900에 해당 값을 더하여 연도를 계산합니다.
* 연도 값이 1900과 9999(포함) 사이에 있으면 함수에서 해당 값을 연도로 사용합니다.
* 연도 값이 0 미만이거나 10000 이상이면 함수에서 오류 값을 반환합니다.
* 월 값이 12보다 크면 함수에서 지정한 연도의 첫 번째 월에 해당 개월 수를 더합니다.
* 월 값이 1보다 작으면 함수에서 지정한 연도의 첫 번째 월에서 몇 개월+1을 뺍니다.
* 일 값이 지정한 월의 일 수보다 크면 함수에서 해당 월의 첫 번째 일에 며칠을 더하여 다음 월의 해당 날짜를 반환합니다.
* 일 값이 1 미만이면 함수에서 지정한 월의 첫 번째 일에서 며칠+1을 뺍니다.

## <a name="calculate-times-based-on-hours-minutes-and-seconds"></a>시간, 분 및 초를 기준으로 시간 계산

1. **Hour** 및 **Minute**이라는 두 개의 **드롭다운** 목록을 추가합니다.

2. **Hour**의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다:
   <br>**Table({Hour:"9"}, {Hour:"10"}, {Hour:"11"}, {Hour:"12"}, {Hour:"13"}, {Hour:"14"}, {Hour:"15"}, {Hour:"16"}, {Hour:"17"})**

3. **Minute**의 **[Items](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다:
   <br>**Table({Minute:"0"}, {Minute:"15"}, {Minute:"30"}, {Minute:"45"})**

4. **[레이블](controls/control-text-box.md)** 컨트롤을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.  
   <br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), 0), DateTimeFormat.ShortTime)**

5. **Hour**에서 **15**, **Minute**에서 **45**를 선택합니다.
   
    **[레이블](controls/control-text-box.md)** 컨트롤에서 **3:45 PM**을 표시합니다.
   
    사용자가 더 큰 시간 범위와 더 정밀한 분 수에서 선택할 수 있도록 **Hour** 및 **Minute**에 항목을 추가할 수 있습니다. 사용자가 초를 지정할 수 있도록 세 번째 **[드롭다운](controls/control-drop-down.md)** 컨트롤을 추가할 수도 있습니다. 세 번째 목록을 추가하는 경우 **[레이블](controls/control-text-box.md)** 컨트롤의 **[Text](controls/properties-core.md)** 속성을 다음 식으로 설정합니다.<br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), Value(Second.Selected.Value)), DateTimeFormat.LongTime)**

