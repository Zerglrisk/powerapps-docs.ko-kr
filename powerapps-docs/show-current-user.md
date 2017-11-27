---
title: "현재 사용자에 대한 세부 정보 표시 | Microsoft Docs"
description: "User 함수를 삽입하여 PowerApps에 로그인한 사용자의 이름과 이메일 주소를 표시합니다."
services: 
suite: powerapps
documentationcenter: 
author: lonu
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: lonu
ms.openlocfilehash: c5d4780908ebd20989649df14dec51d70e8eecde
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2017
---
# <a name="show-information-about-a-powerapps-user"></a>PowerApps 사용자에 대한 정보 표시
User 함수는 전체 이름, 이메일 주소 및 로그인한 사용자와 관련된 그림을 표시할 수 있습니다. 이 정보를 사용하여 양식을 자동으로 채울 수 있습니다.

예를 들어 이 기능을 사용하여 다음을 수행할 수 있습니다.

* 사용자가 교육, 이벤트 자원 봉사, 키오스크 체크 인 등에 참여하기 위한 "등록" 시트를 만듭니다.
* 인사 관리 응용 프로그램에 전체 이름을 표시합니다.
* 지원 센터에 문의할 때 이메일 주소를 자동으로 입력합니다.

기본적으로 사용자가 자동으로 채워지는 양식이나 레이블의 이점을 얻을 수 있는 위치이면 어디서든 이와 같이 사용할 수 있습니다.

&nbsp;

[!INCLUDE [app-customization-requirements](includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>사용자 세부 정보 표시
1. **삽입** 탭에서 **미디어**, **이미지**를 차례로 클릭하거나 탭합니다.
   
   ![][2]
2. **[Image](controls/properties-visual.md)** 속성을 다음 수식으로 설정합니다.
   <br>**User().Image**
   
    ![][3]
3. **삽입** 탭에서 **텍스트**, **텍스트 상자**를 차례로 클릭하거나 탭합니다.  
   
    ![][4]
4. **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
   <br>**User().FullName**
   
   ![][6]
   
   이렇게 하면 레이블에 전체 이름이 자동으로 채워집니다. 다음과 비슷하게 레이블을 이동하여 이미지 컨트롤 아래에 있도록 합니다.
   
   ![][5]
5. 다른 레이블을 추가하고, **[Text](controls/properties-core.md)** 속성을 다음 수식으로 설정합니다.
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
