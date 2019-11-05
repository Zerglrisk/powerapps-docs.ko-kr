---
title: 포털에서 새 URL로 리디렉션 | MicrosoftDocs
description: 리디렉션 URL을 만들어 사용자를 사이트의 다른 페이지로 리디렉션하는 지침을 설명 합니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553420"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>포털에서 새 URL에 리디렉션 URL 추가

고객은 사이트에서 더 깊은 페이지로 리디렉션하는 간단한 URL을 사용 하거나, 기존 URL을 사이트에서 사용 하 고 사이트의 새 URL로 자동으로 리디렉션하는 것이 좋습니다. 콘텐츠 작성자는 페이지 리디렉션을 통해 요청 시 특정 웹 페이지나 웹 파일에 영구적으로 또는 임시 방식으로 리디렉션되는 URL을 지정할 수 있습니다. 이러한 리디렉션 Url은 웹 계층 구조에 직접 맞출 필요가 없도록 페이지 콘텐츠와 별도로 관리 됩니다.

## <a name="create-a-redirect"></a>리디렉션 만들기

1. [포털 관리 앱](configure-portal.md)을 엽니다.

2. **포털** > **웹 사이트로** 이동 하 > **리디렉션합니다**.

3. **새로 만들기**를 선택 합니다.

4. 아래에 설명 된 대로 리디렉션 정보를 입력 합니다.

| 이름        | 설명                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 이름        | 리디렉션의 이름입니다. 는 무엇이 든 될 수 있습니다. 쉽게 식별할 수 있도록 합니다.)                                                              |
| 사이트나     | 리디렉션과 연결 된 웹 사이트입니다. 사용자가 리디렉션되는 사이트입니다.                                                         |
| 인바운드 URL | 리디렉션되는 부분 URL입니다. 사용자가 리디렉션되는 페이지입니다.                                                            |
| 상태 코드 | 다음 중 하나: **302 (임시 리디렉션)** : 임시 리디렉션 상태를 반환 합니다. 이것이 기본값입니다.                                               -   **301 (영구 리디렉션)** : 리소스가 영구적으로 이동 되었음을 나타내는 영구 리디렉션 상태를 반환 합니다.                          |
| URL         | 리디렉션할 대상 외부 URL입니다. 사용자가 위에 지정 된 웹 사이트의 외부 링크로 리디렉션되는 경우이를 사용 합니다.                            |
| 웹 페이지    | 리디렉션할 대상 내부 웹 페이지입니다. 사용자가 위에 지정 된 웹 사이트의 내부 페이지로 리디렉션되는 경우이를 사용 합니다. |
| 사이트 표식 | 리디렉션되는 대상 내부 사이트 표식입니다.                                                                                           |

4. 필수 필드를 입력 하 고 URL, 웹 페이지 또는 사이트 표식 필드 중 하나 이상에 대 한 값을 지정 하 고 **저장**을 선택 합니다.

    ![고객 설문 조사 리디렉션](../media/redirect-customer-survey.png "고객 설문 조사 리디렉션")  

## <a name="use-the-redirect"></a>리디렉션 사용

인바운드 URL이 요청 되 면 브라우저가 일치 하는 리디렉션 항목에 대 한 대상 웹 페이지의 URL로 리디렉션됩니다.

예를 들어 대상 웹 페이지가 고객 지원 설문 조사 페이지로 설정 된 cs-설문 조사의 인바운드 URL 값에 대해 다음 요청을 수행 합니다.

https://customerportal.contoso.com/cs-survey

브라우저에서 다음 URL을 요청 합니다.

https://customerportal.contoso.com/surveys/customer-service-survey/

