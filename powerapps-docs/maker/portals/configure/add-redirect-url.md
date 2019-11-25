---
title: 포털의 새 URL로 리디렉션 | MicrosoftDocs
description: 사용자를 사이트의 다른 페이지로 리디렉션하는 리디렉션 URL을 만드는 방법에 관한 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63cec47042cee4c29e225f33f1678261da3a01ca
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760708"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>포털의 새 URL로 URL 리디렉션 추가

빈번하게 고객들은 사이트의 더 깊은 페이지로 리디렉션하는 단순 URL을 갖기 원하거나, 사이트와 함께 레거시 URL을 사용하여 사이트의 새 URL로 자동 리디렉션할 수 있기를 원합니다. 페이지 리디렉션으로 작성자는 요청될 때 영구히 또는 일시적으로 특정 웹 페이지 또는 웹 파일로 리디렉션될 URL을 지정할 수 있습니다. 이러한 리디렉션 URL은 페이지 콘텐츠와 별도로 관리되므로 웹 계층 구조에 직접 맞을 필요는 없습니다.

## <a name="create-a-redirect"></a>리디렉션 만들기

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 사이트** > **리디렉션**으로 이동합니다.

3. **새로 만들기**를 선택합니다.

4. 아래에 설명된대로 리디렉션 정보를 입력합니다.

| 이름        | 설명                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 이름        | 친근한 리디렉션 이름. (어떤 것이든 가능합니다. 식별하기 쉽도록 만드십시오.)                                                              |
| 웹 사이트     | 리디렉션이 연계되는 웹 사이트. (사용자가 리디렉션되는 사이트.)                                                         |
| 인바운드 URL | 리디렉션될 부분 URL. (사용자가 리디렉션되는 사이트.)                                                            |
| 상태 코드 | 다음 중 하나: **302(일시적 리디렉션)**: 일시적 리디렉션 상태를 반환합니다. 기본값입니다.                                               -   **301(영구적 리디렉션)**: 리소스가 영구히 이동하였음을 표시하는 영구적 리디렉션 상태를 반환합니다.                          |
| URL         | 리디렉션될 목표 외부 URL. (사용자가 위에 지정된 웹 사이트 외부의 링크로 리디렉션되는 경우 사용합니다.)                            |
| 웹 페이지    | 리디렉션할 대상 내부 웹 페이지. (사용자가 위에 지정된 웹사이트의 내부 페이지로 리디렉션되는 경우 이것을 사용하십시오.) |
| 사이트 마커 | 리디렉션할 대상 내부 사이트 마커.                                                                                           |

4. 필수 필드에 들어가서 URL, 웹 페이지 또는 사이트 마커 필드 중 적어도 하나의 값을 지정한 후 **저장**을 선택합니다.

    ![고객 설문 조사 리디렉션](../media/redirect-customer-survey.png "고객 설문 조사 리디렉션")  

## <a name="use-the-redirect"></a>리디렉션 사용하기

인바운드 URL이 요청되면 브라우저가 일치하는 리디렉션 입력을 위해 대상 웹 페이지의 URL로 리디렉션됩니다.

예를 들면, 대상 웹 페이지가 고객 지원 설문조사 페이지로 설정된 cs-survey의 인바운드 URL 값의 경우, 다음을 요청합니다.

https://customerportal.contoso.com/cs-survey

브라우저가 다음 URL을 요청하게 됩니다.

https://customerportal.contoso.com/surveys/customer-service-survey/

