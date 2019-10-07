---
title: Download, Launch 및 Param 함수 | Microsoft Docs
description: Canvas 앱에서 다운로드, 시작 및 매개 변수 함수에 대 한 구문과 예제를 포함 한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c6fb3c5ef002ed0355cc8061603e4f4b1f438e6e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992487"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>Canvas 앱에서 Download, Launch 및 Param 함수
매개 변수를 사용하여 웹 페이지 또는 앱을 다운로드하거나 시작합니다.  

## <a name="description"></a>설명
**Download** 함수는 파일을 웹에서 로컬 디바이스로 다운로드합니다. 사용자에게 파일을 저장할 위치를 묻는 메시지가 표시됩니다.  **Download**는 파일이 로컬로 저장된 위치를 문자열로 반환합니다.  

**Launch** 함수는 웹 페이지 또는 앱을 시작합니다.  이 함수는 필요에 따라 매개 변수를 앱에 전달할 수 있습니다.

Internet Explorer 및 Microsoft Edge에서 **Launch** 함수는 보안 설정이 함수를 포함 하는 앱과 같거나 높은 경우에만 웹 사이트 또는 앱을 엽니다. 예를 들어 **신뢰할 수 있는 사이트** 보안 영역에서 실행 되는 앱에 **시작** 함수를 추가 하는 경우 함수를 열려는 웹 사이트 또는 앱이 **신뢰할 수 있는 사이트** 또는 **로컬 인트라넷** 영역 **에 있는지 확인 합니다. 제한 된 사이트**). 자세한 정보: [Internet Explorer 11에 대 한 보안 및 개인 정보 설정을 변경](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings)합니다.  

**Param** 함수는 앱이 시작될 때 해당 앱에 전달된 매개 변수를 검색합니다. 명명된 매개 변수가 전달되지 않은 경우 **Param**에서 *공백*을 반환합니다.

## <a name="syntax"></a>구문
**Download**( *Address* )

* *Address* - 필수 항목이며,  다운로드할 웹 리소스의 주소입니다.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address* - 필수 항목이며,  시작할 웹 페이지의 주소 또는 앱의 ID입니다.
* *ParameterName(s)* - 선택 항목이며,  매개 변수 이름입니다.
* *ParameterValue(s)* - 선택 항목이며,  앱 또는 웹 페이지에 전달할 매개 변수 값입니다.

**Param**( *ParameterName* )

* *ParameterName* - 필수 항목이며,  앱에 전달된 매개 변수 이름입니다.

