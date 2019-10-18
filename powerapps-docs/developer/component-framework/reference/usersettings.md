---
title: UserSettings | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c237ff96-9268-4068-9d61-aea0bdc79fc2
ms.openlocfilehash: 5325091d8f82ffd98cfc4e5fdab4e0228a5d541e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341038"
---
# <a name="usersettings"></a>UserSettings

[!INCLUDE [usersettings-description](includes/usersettings-description.md)]

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="properties"></a>속성

### <a name="dateformattinginfo"></a>dateFormattingInfo

서버에서 검색 된 날짜 형식 지정 정보입니다.

**유형**: [DateFormattingInfo](dateformattinginfo.md)

### <a name="isrtl"></a>isRTL

언어가 오른쪽에서 왼쪽 인 경우 true를 반환 합니다.

**형식**: `boolean`

### <a name="languageid"></a>languageId

현재 사용자의 언어 id입니다.

**형식**: `number`

### <a name="numberformattinginfo"></a>numberFormattingInfo

서버에서 검색 된 숫자 형식 지정 정보입니다.

**유형**: [NumberFormattingInfo](numberformattinginfo.md)

### <a name="securityroles"></a>securityRoles

현재 사용자 역할.

**형식**: `string[]`

### <a name="userid"></a>Id

현재 사용자의 id입니다.

**형식**: `string`

### <a name="username"></a>userName

현재 사용자의 사용자 이름입니다.

**형식**: `string`

## <a name="methods"></a>메서드

|방법이 | 설명 | 
| ------|-------------|
|[getTimeZoneOffsetMinutes](usersettings/gettimezoneoffsetminutes.md)|[!INCLUDE [gettimezoneoffsetminutes-description](usersettings/includes/gettimezoneoffsetminutes-description.md)]|

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)