---
title: RDL 샌드박싱 | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2017
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: amyla
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: f936dc4c6b78096b74b650bf8426ba1d78c41d19
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711394"
---
# <a name="rdl-sandboxing"></a>RDL 샌드박싱 

Common Data Service에서 보고서는 샌드박스 모드에서 실행됩니다. SQL Server Reporting Services에서 RDL(Report Definition Language) 샌드박싱을 설정하여 수행됩니다. RDL 샌드박싱을 사용하면 특정 유형의 리소스 사용을 검색하고 제한할 수 있습니다. 결과적으로 PowerApps 모델 기반 앱의 특정 기능을 사용할 수 없습니다. 자세한 내용은 [MSDN: RDL 샌드박스 활성화 및 비활성화](https://msdn.microsoft.com/library/ee210591.aspx)를 참조하십시오.  
  
 Common Data Service의 현재 RDL 샌드박싱 구성 설정은 이 항목의 다음 섹션에서 설명되어 있습니다.  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>배열 결과 길이 및 문자열 결과 길이 제한  
 RDL 식에 대해 배열 반환 값에 허용되는 항목의 최대 수가 250에서 102400으로 증가합니다. RDL 식에 대해 문자열 반환 값에 허용되는 항목의 최대 수 또한 250에서 102400으로 증가합니다. 이로 인해 Base64 인코딩을 사용하여 데이터베이스에 저장될 최대 75KB의 이미지 및 로고를 포함할 수 있습니다.  
  
 MaxResourceSize는 2000으로 설정되어 있습니다. 이렇게 하면 보고서에 최대 1500 KB 크기의 외부 이미지를 포함할 수 있습니다. 추가 정보: [TechNet: 외부 이미지 추가(Report Builder 및 SSRS)](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>허용된 유형 및 거부된 구성원  
 RDL 샌드박싱 기능을 사용하면 승인된 유형 목록과 거부된 구성원 목록을 만들 수 있습니다. 승인된 유형 목록은 허용 목록이라고 합니다. RDL 식에서 허용되지 않는 거부된 구성원 목록은 차단 목록이라고 합니다.  
  
 다음 표에는 Common Data Service의 샌드박스 모드에서 사용할 수 있는 허용된 유형 및 거부된 유형 목록이 포함되어 있습니다.  
  
|허용된 유형|거부된 구성원|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Finalize|  
||GetType|  
||MemberwiseClone|  
||크기 조정|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Finalize|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|시간|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||Zero|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|만들기|  
||Finalize|  
|||  
|`System.TimeZone`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Unescape|  
||구문 분석|  
||Esc|  
||Finalize|  
|||  
|`System.UriBuilder`|Finalize|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|비어 있음|  
||NextMatch|  
||결과|  
||동기화됨|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Unescape|  
||UseOptionC|  
||UseOptionR|  
||capnames|  
||caps|  
||capsize|  
||capslist|  
||roptions|  
||pattern|  
||factory|  
||IsMatch|  
||Matches|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||옵션|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||vbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||vbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||Zero|  
|`Microsoft.VisualBasic.ControlChars`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Fix|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Finalize|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Beep|  
||CallByName|  
||명령|  
||CreateObject|  
||Environ|  
||Finalize|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||선택|  
||전환|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Finalize|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>공통 거부된 구성된  
 다음 표에서는 허용된 유형에 공통 거부된 구성원 목록이 들어 있습니다.  
  
||  
|-|  
|DateString|  
|기간|  
|Equality|  
|같음|  
|Erl|  
|필터|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negate|  
|타이머|  
|TimeString|  
|ToBinary|  
|Finalize|  
|GetType|  
|MemberwiseClone|  
  

