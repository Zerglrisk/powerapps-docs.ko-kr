---
title: 함수, 신호 및 열거형 | Microsoft Docs
description: PowerApps에서 함수, 신호 및 열거형에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ec035ca959f29832e2ba0bbb2250a24c11f1692e
ms.sourcegitcommit: 562c7ed5fbb116be1cbb0f45e3f6e75e3e4cf011
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451408"
---
# <a name="formula-reference-for-powerapps"></a>PowerApps에 대한 수식 참조
수식은 많은 요소를 결합합니다.  아래 나열되어 있습니다.

* **함수**는 매개 변수를 받아 작업을 수행하고 값을 반환합니다. 예를 들어 **Sqrt(25)** 는 **5**를 반환합니다. 함수는 Microsoft Excel 함수를 본떠 만듭니다.  **SubmitForm**과 같은 일부 함수에는 파생 작업이 있으며 **Button.OnSelect**와 같은 [동작 수식](working-with-formulas-in-depth.md)에서만 적합합니다.
* **신호**는 환경에 대한 정보를 반환합니다. 예를 들어 **[Location](functions/signals.md)** 는 디바이스의 현재 GPS 좌표를 반환합니다. 신호는 매개 변수를 받지 않거나 파생 작업이 있습니다.
* **열거형**은 미리 정의된 상수 값을 반환합니다. 예를 들어 **[Color](functions/function-colors.md)** 는 **Color.Red**, **Color.Blue** 등에 대해 미리 정의된 값을 포함하는 열거형입니다.  공통 열거형은 여기에 포함되며 함수별 열거형이 함수와 함께 설명됩니다.
* **[ThisItem](functions/operators.md#thisitem-operator)** 및 **[Parent](functions/operators.md#parent-operator)** 와 같은 **명명된 연산자**는 컨테이너 내에서 정보에 대한 액세스를 제공합니다.

기타 요소는 다음과 같습니다.

* [모든 연산자](functions/operators.md)
* [컨트롤 및 해당 속성](reference-properties.md)
* [데이터 형식](functions/data-types.md)

## <a name="a"></a>A
**[Abs](functions/function-numericals.md)** – 숫자의 절대 값을 반환합니다.  

**[Acceleration](functions/signals.md)** – 디바이스에서 가속 센서를 읽습니다.

**[Acos](functions/function-trig.md)** – 숫자의 아크코사인을 라디안으로 반환합니다.

**[Acot](functions/function-trig.md)** – 숫자의 아크코탄젠트를 라디안으로 반환합니다.

**[AddColumns](functions/function-table-shaping.md)** – [열](working-with-tables.md#columns)이 추가된 테이블을 반환합니다.

**[And](functions/function-logicals.md)** – 부울 논리 AND입니다.  모든 인수가 **true**이면 **true**를 반환합니다.  [ **&&** 연산자](functions/operators.md)를 사용할 수도 있습니다.

**[앱](functions/object-app.md)**  – 현재 실행 중인 앱 및 앱의 동작을 제어 하는 방법에 대 한 정보를 제공 합니다.

**[Asin](functions/function-trig.md)** – 숫자의 아크사인을 라디안으로 반환합니다.

**[AsType](functions/function-astype-istype.md)**  – 특정 엔터티 형식에 대 한 레코드 참조 취급 합니다.

**[Atan](functions/function-trig.md)** – 숫자의 아크탄젠트를 라디안으로 반환합니다.

**[Atan2](functions/function-trig.md)** – (*x*,*y*) 좌표에 따라 아크탄젠트를 라디안으로 반환합니다.

**[Average](functions/function-aggregates.md)** – 테이블 식의 평균 또는 인수 집합을 계산합니다.

## <a name="b"></a>B
**[Back](functions/function-navigate.md)** – 이전 화면을 표시합니다.  

**[Blank](functions/function-isblank-isempty.md)** – 데이터 원본에 NULL 값을 삽입하는 데 사용할 수 있는 *공백* 값을 반환합니다.

## <a name="c"></a>C
**[Calendar](functions/function-clock-calendar.md)** – 현재 로캘에 대한 달력 정보를 검색합니다.

**[Char](functions/function-char.md)** – 문자 코드를 문자열로 변환합니다.

**[Choices](functions/function-choices.md)** – 조회 열에 대해 가능한 값의 테이블을 반환합니다.

**[Clear](functions/function-clear-collect-clearcollect.md)** – [컬렉션](working-with-data-sources.md#collections)에서 모든 데이터를 삭제합니다.

**[ClearCollect](functions/function-clear-collect-clearcollect.md)** – 컬렉션에서 모든 데이터를 삭제한 후 [레코드](working-with-tables.md#records) 집합을 추가합니다.

**[Clock](functions/function-clock-calendar.md)** – 현재 로캘에 대한 시간 정보를 검색합니다.

**[Coalesce](functions/function-isblank-isempty.md)** – *공백*이 아닌 값을 변경하지 않으면서 *공백* 값을 바꿉니다.

**[Collect](functions/function-clear-collect-clearcollect.md)** – 컬렉션을 만들거나 데이터를 데이터 원본에 추가합니다.

**[Color](functions/function-colors.md)** – 속성을 기본 제공 색 값으로 설정합니다.

**[ColorFade](functions/function-colors.md)** – 색 값이 흐려집니다.

**[ColorValue](functions/function-colors.md)** – CSS 색 이름 또는 16진 코드를 색 값으로 변환합니다.  

**[Compass](functions/signals.md)** – 나침반 방향을 반환합니다.

**[Concat](functions/function-concatenate.md)** – 데이터 원본에서 문자열을 연결합니다.  

**[Concatenate](functions/function-concatenate.md)** – 문자열을 연결합니다.

**[Concurrent](functions/function-concurrent.md)** – 동시에 서로 여러 수식을 평가합니다. 

**[Connection](functions/signals.md)** – 네트워크 연결에 대한 정보를 반환합니다.

**[Count](functions/function-table-counts.md)** – 숫자가 포함된 테이블 레코드 수를 계산합니다.

**[Cos](functions/function-trig.md)** – 라디안으로 지정된 각도의 코사인을 반환합니다.

**[Cot](functions/function-trig.md)** – 라디안으로 지정된 각도의 코탄젠트를 반환합니다.

**[CountA](functions/function-table-counts.md)** – [비어 있지](functions/function-isblank-isempty.md) 않은 테이블 레코드 수를 계산합니다.

**[CountIf](functions/function-table-counts.md)** – 조건에 맞는 테이블 레코드의 수를 계산합니다.  

**[CountRows](functions/function-table-counts.md)** – 테이블 레코드의 수를 계산합니다.   

## <a name="d"></a>D
**[DataSourceInfo](functions/function-datasourceinfo.md)** – 데이터 원본에 대한 정보를 제공합니다.

**[Date](functions/function-date-time.md)** – **연도**, **월**, **일** 값을 기반으로 날짜/시간 값을 반환합니다.  

**[DateAdd](functions/function-dateadd-datediff.md)** – 일, 월, 분기 또는 연도를 날짜/시간 값에 추가합니다.

**[DateDiff](functions/function-dateadd-datediff.md)** – 두 날짜 값을 빼는 결과를 일, 월, 분기 또는 연도로 표시합니다.

**[DateTimeValue](functions/function-datevalue-timevalue.md)** – 날짜 및 시간 문자열을 날짜/시간 값으로 변환합니다.

**[DateValue](functions/function-datevalue-timevalue.md)** – 날짜 전용 문자열을 날짜/시간 값으로 변환합니다.

**[Day](functions/function-datetime-parts.md)** – 날짜/시간 값의 일 부분을 검색합니다.  

**[Defaults](functions/function-defaults.md)** – 데이터 원본의 기본값을 반환합니다.

**[Degrees](functions/function-trig.md)** - 라디안을 각도로 변환합니다.

**[Disable](functions/function-enable-disable.md)** – GPS 판독 중에 **[Location](functions/signals.md)** 과 같은 신호를 사용하지 않습니다.

**[Distinct](functions/function-distinct.md)** – 테이블의 레코드를 요약하여 중복을 제거합니다.  

**[Download](functions/function-param.md)** – 웹에서 로컬 디바이스로 파일을 다운로드합니다.

**[DropColumns](functions/function-table-shaping.md)** – 하나 이상의 열이 제거된 테이블을 반환합니다.

## <a name="e"></a>E
**[EditForm](functions/function-form.md)** – 항목 편집을 위해 Form 컨트롤을 다시 설정합니다.

**[Enable](functions/function-enable-disable.md)** – GPS 판독 중에 **[Location](functions/signals.md)** 과 같은 신호를 사용합니다.

**[EndsWith](functions/function-startswith.md)** – 텍스트 문자열이 다른 텍스트 문자열로 끝나는지 확인합니다.

**[Errors](functions/function-errors.md)** – 데이터 원본의 이전 변경에 대한 오류 정보를 제공합니다.

**[EncodeUrl](functions/function-encode-decode.md)** – URL 인코딩을 사용하여 특수 문자를 인코딩합니다.

**[Exit](functions/function-exit.md)** – 현재 실행 중인 앱을 종료합니다.

**[Exp](functions/function-numericals.md)** - *e*를 거듭제곱한 값을 반환합니다.

## <a name="f"></a>F
**[Filter](functions/function-filter-lookup.md)** – 하나 이상의 조건에 따라 필터링된 테이블을 반환합니다.

**[Find](functions/function-find.md)** – 한 문자열이 다른 문자열 내에 나타나는지 확인하고 위치를 반환합니다.

**[First](functions/function-first-last.md)** – 테이블의 첫 번째 레코드를 반환합니다.

**[FirstN](functions/function-first-last.md)** – 테이블에 있는 레코드(N 레코드)의 첫 번째 집합을 반환합니다.

**[ForAll](functions/function-forall.md)** – 테이블의 모든 레코드에 대해 값을 계산하고 작업을 수행합니다.

## <a name="g"></a>G
**[GroupBy](functions/function-groupby.md)** – 함께 그룹화된 레코드가 있는 테이블을 반환합니다.

**[GUID](functions/function-guid.md)** - GUID 문자열을 GUID 값으로 변환하거나 새 GUID 값을 만듭니다.

## <a name="h"></a>H
**[HashTags](functions/function-hashtags.md)** – 문자열에서 해시태그(#strings)를 추출합니다.

**[Hour](functions/function-datetime-parts.md)** – 날짜/시간 값의 시간 부분을 반환합니다.

## <a name="i"></a>I
**[If](functions/function-if.md)** – 조건이 true이면 한 값을 반환하고 그렇지 않으면 다른 값을 반환합니다. 

**[IfError](functions/function-iferror.md)** - 오류를 감지하고 대체 값을 제공하거나 작업을 수행합니다. 

**[IsBlank](functions/function-isblank-isempty.md)** – [공백](functions/function-isblank-isempty.md) 값을 확인합니다.

**[IsEmpty](functions/function-isblank-isempty.md)** – 비어 있는 테이블을 확인합니다.

**[IsMatch](functions/function-ismatch.md)** – 패턴에 대해 문자열을 확인합니다.  정규식을 사용할 수 있습니다.

**[IsNumeric](functions/function-isnumeric.md)** – 숫자 값을 확인합니다.

**[IsToday](functions/function-now-today-istoday.md)** – 날짜/시간 값이 오늘인지 확인합니다.

**[IsType](functions/function-astype-istype.md)**  – 특정 엔터티 형식에 대 한 레코드 참조를 참조 하는지 여부를 확인 합니다.  

## <a name="l"></a>L
**[Language](functions/function-language.md)** – 현재 사용자의 언어 태그를 반환합니다.

**[Last](functions/function-first-last.md)** – 테이블의 마지막 레코드를 반환합니다.

**[LastN](functions/function-first-last.md)** – 테이블에 있는 레코드(N 레코드)의 마지막 집합을 반환합니다.

**[Launch](functions/function-param.md)** – 웹 주소 또는 앱을 시작합니다.

**[Left](functions/function-left-mid-right.md)** – 문자열의 맨 왼쪽 부분을 반환합니다.

**[Len](functions/function-len.md)** – 문자열의 길이를 반환합니다.

**[Ln](functions/function-numericals.md)** – 자연 로그를 반환합니다.

**[LoadData](functions/function-savedata-loaddata.md)** – PowerApps 사설 스토리지에서 컬렉션을 로드합니다.

**[Location](functions/signals.md)** – GPS(Global Positioning System) 또는 기타 정보를 사용하여 사용자의 위치를 지도 좌표로 반환합니다.

**[LookUp](functions/function-filter-lookup.md)** – 하나 이상의 조건에 따라 테이블의 단일 레코드를 조회합니다.

**[Lower](functions/function-lower-upper-proper.md)** – 텍스트 문자열의 문자를 모두 소문자로 변환합니다.

## <a name="m"></a>M
**[Match](functions/function-ismatch.md)** – 패턴에 따라 하위 문자열을 추출합니다.  정규식을 사용할 수 있습니다.

**[MatchAll](functions/function-ismatch.md)**  – 패턴에 따라 여러 부분 문자열을 추출 합니다.  정규식을 사용할 수 있습니다.

**[Max](functions/function-aggregates.md)** – 테이블 식 또는 인수 집합의 최대값입니다.

**[Mid](functions/function-left-mid-right.md)** – 문자열의 가운데 부분을 반환합니다.

**[Min](functions/function-aggregates.md)** – 테이블 식 또는 인수 집합의 최소값입니다.

**[Minute](functions/function-datetime-parts.md)** – 날짜/시간 값의 분 부분을 검색합니다.  

**[Mod](functions/function-mod.md)** – 피제수를 제수로 나눈 나머지를 반환합니다.

**[Month](functions/function-datetime-parts.md)** – 날짜/시간 값의 월 부분을 검색합니다.

## <a name="n"></a>N
**[Navigate](functions/function-navigate.md)** – 표시되는 화면을 변경합니다.

**[NewForm](functions/function-form.md)** – 항목 생성을 위해 Form 컨트롤을 다시 설정합니다.

**[Not](functions/function-logicals.md)** – 부울 논리 NOT입니다.  인수가 **false**이면 **true**를 반환하고 인수가 **true**이면 **false**를 반환합니다.  [ **!** 연산자](functions/operators.md)를 사용할 수도 있습니다.

**[Notify](functions/function-showerror.md)** – 사용자에게 배너 메시지를 표시합니다.

**[Now](functions/function-now-today-istoday.md)** – 현재 날짜/시간 값을 반환합니다.

## <a name="o"></a>O
**[Or](functions/function-logicals.md)** – 부울 논리 OR입니다.  인수 중 **true**인 항목이 있으면 **true**를 반환합니다.  [ **||** 연산자](functions/operators.md)를 사용할 수도 있습니다.

## <a name="p"></a>P
**[Param](functions/function-param.md)** – 사용자가 열었을 때 앱에 전달된 매개 변수에 대한 액세스를 제공합니다.

**[Parent](functions/operators.md#parent-operator)** – 컨테이너 컨트롤의 속성에 대한 액세스를 제공합니다.

**[Patch](functions/function-patch.md)** – 데이터 원본의 레코드를 수정 또는 생성하거나 데이터 원본 외부의 레코드를 병합합니다.

**[Pi](functions/function-trig.md)** – &pi; 숫자를 반환합니다.

**[PlainText](functions/function-encode-decode.md)** – 문자열에서 HTML 및 XML 태그를 제거합니다.

**[Power](functions/function-numericals.md)** – 숫자를 거듭제곱한 값을 반환합니다.  [ **^** 연산자](functions/operators.md)를 사용할 수도 있습니다.

**[Proper](functions/function-lower-upper-proper.md)** – 문자열에 있는 각 단어의 첫 문자를 대문자로 변환하고 나머지는 소문자로 변환합니다.

## <a name="r"></a>R
**[Radians](functions/function-trig.md)** - 각도를 라디안으로 변환합니다.

**[Rand](functions/function-rand.md)** – 의사 난수를 반환합니다.

**[Refresh](functions/function-refresh.md)** – 데이터 원본의 레코드를 새로 고칩니다.

**[Relate](functions/function-relate-unrelate.md)** – 일대다 또는 다대다 관계를 통해 두 엔터티의 레코드를 연결합니다.

**[Remove](functions/function-remove-removeif.md)** – 데이터 원본에서 하나 이상의 특정 레코드를 제거합니다.

**[RemoveIf](functions/function-remove-removeif.md)** – 조건에 따라 데이터 원본에서 레코드를 제거합니다.

**[RenameColumns](functions/function-table-shaping.md)** – 테이블의 열 이름을 변경합니다.

**[Replace](functions/function-replace-substitute.md)** – 문자열의 시작 위치로 문자열의 부분을 다른 문자열로 바꿉니다.

**[Reset](functions/function-reset.md)** – 사용자 변경 내용을 삭제하면서 입력 컨트롤을 해당 기본값으로 다시 설정합니다.

**[ResetForm](functions/function-form.md)** – 기존 항목 편집을 위해 Form 컨트롤을 다시 설정합니다.

**[Revert](functions/function-revert.md)** – 데이터 원본의 레코드를 다시 로드하고 오류를 지웁니다.

**[RGBA](functions/function-colors.md)** – 빨강, 녹색, 파랑 및 알파 구성 요소 집합에 대한 색 값을 반환합니다.

**[Right](functions/function-left-mid-right.md)** – 문자열의 맨 오른쪽 부분을 반환합니다.

**[Round](functions/function-round.md)** – 가장 가까운 수로 반올림합니다.

**[RoundDown](functions/function-round.md)** – 가장 큰 이전 숫자로 내림합니다.

**[RoundUp](functions/function-round.md)** – 가장 작은 다음 숫자로 올림합니다.

## <a name="s"></a>S
**[SaveData](functions/function-savedata-loaddata.md)** – PowerApps 사설 스토리지에 컬렉션을 저장합니다.

**[Search](functions/function-filter-lookup.md)** – 해당 열 중 하나에 문자열을 포함하는 테이블의 레코드를 찾습니다.  

**[Second](functions/function-datetime-parts.md)** – 날짜/시간 값의 초 부분을 검색합니다.

**[Select](functions/function-select.md)** – 컨트롤에 select 작업을 시뮬레이트하여 **OnSelect** 수식을 계산합니다.

**[Set](functions/function-set.md)** – 전역 변수의 값을 설정합니다.

**[ShowColumns](functions/function-table-shaping.md)** – 선택한 열만 포함하는 테이블을 반환합니다.

**[Shuffle](functions/function-shuffle.md)** – 테이블의 레코드를 무작위로 다시 정렬합니다.

**[Sin](functions/function-trig.md)** – 라디안으로 지정된 각도의 사인을 반환합니다.

**[Sort](functions/function-sort.md)** – 수식에 따라 정렬된 테이블을 반환합니다.

**[SortByColumns](functions/function-sort.md)** – 하나 이상의 열에 따라 정렬된 테이블을 반환합니다.

**[Split](functions/function-split.md)** – 텍스트 문자열을 하위 문자열의 테이블로 분할합니다.

**[Sqrt](functions/function-numericals.md)** – 숫자의 제곱근을 반환합니다.

**[StartsWith](functions/function-startswith.md)** – 텍스트 문자열이 다른 텍스트 문자열로 시작하는지 확인합니다.

**[StdevP](functions/function-aggregates.md)** – 인수의 표준 편차를 계산합니다.  

**[Substitute](functions/function-replace-substitute.md)** – 문자열을 일치시켜 문자열의 일부를 다른 문자열로 바꿉니다.

**[SubmitForm](functions/function-form.md)** – 데이터 원본에 Form 컨트롤의 항목을 저장합니다.

**[Sum](functions/function-aggregates.md)** – 테이블 식의 합계 또는 인수 집합을 계산합니다.  

**[Switch](functions/function-if.md)** – 값 집합과 일치시킨 후 해당 수식을 평가합니다.

## <a name="t"></a>T
**[Table](functions/function-table.md)** – 임시 테이블을 만듭니다.  

**[Tan](functions/function-trig.md)** - 라디안으로 지정된 각도의 탄젠트를 반환합니다.

**[Text](functions/function-text.md)** – 모든 값을 변환하고 숫자 또는 날짜/시간 값을 텍스트 문자열로 형식을 지정합니다.

**[ThisItem](functions/operators.md#thisitem-operator)** – 갤러리 또는 Form에서 컨테이너에서 현재 항목에 대한 데이터를 반환합니다.

**[Time](functions/function-date-time.md)** – **시**, **분**, **초** 값을 기반으로 날짜/시간 값을 반환합니다.  

**[TimeValue](functions/function-datevalue-timevalue.md)** – 시간 전용 문자열을 날짜/시간 값으로 변환합니다.

**[TimeZoneOffset](functions/function-dateadd-datediff.md)** – UTC와 사용자의 로컬 시간 간 차이를 분 단위로 반환합니다.

**[Today](functions/function-now-today-istoday.md)** – 현재 날짜/시간 값을 반환합니다.

**[Trim](functions/function-trim.md)** – 텍스트 문자열의 내부 및 끝에서 추가 공백을 제거합니다.

**[TrimEnds](functions/function-trim.md)** – 텍스트 전용 문자열의 끝에서 추가 공백을 제거합니다.

## <a name="u"></a>U
**[Ungroup](functions/function-groupby.md)** – 그룹화를 제거합니다.

**[Unrelate](functions/function-relate-unrelate.md)** – 일대다 또는 다대다 관계에서 두 엔터티의 레코드의 연결을 해제합니다.

**[Update](functions/function-update-updateif.md)** – 데이터 원본에서 레코드를 바꿉니다.

**[UpdateContext](functions/function-updatecontext.md)** – 현재 화면에 있는 하나 이상의 [컨텍스트 변수](working-with-variables.md#use-a-context-variable) 값을 설정합니다.

**[UpdateIf](functions/function-update-updateif.md)** – 조건에 따라 데이터 원본에 있는 레코드 집합을 수정합니다.

**[Upper](functions/function-lower-upper-proper.md)** – 텍스트 문자열의 문자를 모두 대문자로 변환합니다.

**[User](functions/function-user.md)** – 현재 사용자에 대한 정보를 반환합니다.

## <a name="v"></a>V
**[Validate](functions/function-validate.md)** – 데이터 원본에 대해 단일 열 값 또는 전체 레코드가 유효한지 여부를 확인합니다.

**[Value](functions/function-value.md)** – 문자열을 숫자로 변환합니다.

**[VarP](functions/function-aggregates.md)** – 인수의 분산을 반환합니다.  

**[ViewForm](functions/function-form.md)** – 기존 항목 보기를 위해 Form 컨트롤을 다시 설정합니다.

## <a name="w"></a>W
**[Weekday](functions/function-datetime-parts.md)** – 날짜/시간 값의 요일 부분을 검색합니다.

## <a name="y"></a>Y
**[Year](functions/function-datetime-parts.md)** – 날짜/시간 값의 연도 부분을 검색합니다.  

