---
title: 캔버스 앱에서 현재 사용자에 대한 세부 정보 표시 | Microsoft Docs
description: PowerApps에서 로그인한 사용자의 이름과 이메일 주소를 캔버스 앱에 표시합니다.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: afd5dffc75dea4186058ba96adbaf0dbde8dc3d8
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71988510"
---
# <a name="show-information-about-a-powerapps-user-in-a-canvas-app"></a>캔버스 앱에서 PowerApps 사용자에 대한 정보 표시

PowerApps에서 전체 이름, 이메일 주소 및 캔버스 앱에 로그인한 사용자와 관련된 그림을 표시합니다. 예를 들어, 이 정보를 사용하여 폼을 자동으로 채울 수 있습니다.

예를 들어 이 기능을 사용하여 다음을 수행할 수 있습니다.

* 사용자가 교육, 이벤트 자원 봉사, 키오스크 체크 인 등에 참여하기 위한 "등록" 시트를 만듭니다.
* 인사 관리 응용 프로그램에 전체 이름을 표시합니다.
* 지원 센터에 문의할 때 이메일 주소를 자동으로 입력합니다.

기본적으로 사용자가 자동으로 채워지는 폼이나 레이블의 이점을 얻을 수 있는 위치이면 어디서든 이와 같이 사용할 수 있습니다.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>사용자 세부 정보 표시

1. **삽입** 탭에서 **미디어**, **이미지**를 차례로 클릭하거나 탭합니다.
   
   ![][2]
2. **[Image](controls/properties-visual.md)** 속성을 다음 수식으로 설정합니다.
   <br>**User().Image**
   
    ![][3]
3. **삽입** 탭에서 **텍스트**, **레이블**을 차례로 클릭하거나 탭합니다.  
   
    ![][4]
4. **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**User().FullName**
   
   ![][6]
   
   이렇게 하면 레이블에 전체 이름이 자동으로 채워집니다. 다음과 비슷하게 레이블을 이동하여 이미지 컨트롤 아래에 있도록 합니다.
   
   ![][5]
5. 다른 레이블을 추가하고 **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**User().Email**  
   
    ![][8]
   
    이렇게 하면 레이블에 이메일 주소가 자동으로 채워집니다. 다음과 비슷하게 레이블을 이동하여 첫 번째 레이블 아래에 있도록 합니다.  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
