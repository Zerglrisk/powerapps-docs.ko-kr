---
title: 앱 디자이너를 사용하여 모델 기반 앱 유효성 검사 및 게시 | MicrosoftDocs
description: 모델 기반 앱을 유효성 검사 및 게시하는 방법 알아보기
keywords: ''
ms.date: 06/08/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5a9ec120-9ddc-4d92-b48c-0fee8c57d3c3
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 10
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e6ae7ac84710e6558adde2949025868e6da6930
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710294"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>앱 디자이너를 사용하여 모델 기반 앱 유효성 검사 및 게시

앱의 유효성을 검사하여 앱이 작동하는 데 필요하지만 아직 앱에 추가되지 않은 자산 종속성을 확인합니다. 유효성 검사가 성공한 후 앱을 게시합니다. 
  
예를 들어, 본인이 추가하지 않은 서비스 케이스 혼합(우선 순위별) 또는 서비스 케이스 해결 추세(일별)와 같은 차트를 사용하는 Customer Service 성과 대시보드를 앱에 추가했습니다. 이 앱의 유효성을 검사하면 모든 누락된 필요한 자산 목록을 얻을 수 있습니다.  
  
앱의 유효성을 검사할 때 앱 디자이너 캔버스에 누락된 자산에 대한 자세한 내용이 표시됩니다.  
  
1.  앱 디자이너에서 **유효성 검사**를 선택합니다.  
  
     알림 표시줄이 나타나고 앱에 오류 또는 경고가 있는지 여부를 표시합니다. 알림 표시줄은 예컨대 엔터티에 양식이나 보기가 없거나 앱에 아무 구성 요소도 포함되지 않은 경우 경고를 표시합니다. 앱에 대해 사이트 맵이 구성되지 않은 경우 오류가 나타날 수 있습니다. 경고를 무시하고 앱을 게시할 수 있지만 게시하기 전에 모든 오류를 수정해야 합니다.  
  
     ![앱에서 경고를 표시하는 알림 표시줄](media/app-designer-warning-notification.png "앱에서 경고를 표시하는 알림 표시줄")  
  
     앱 디자이너는 종속 항목의 수와 함께 필요한 자산이 없는 각 아티팩트 또는 자산 타일에 대한 경고 기호를 보여줍니다.  
  
     ![앱 디자이너 타일의 누락된 구성 요소 경고](media/warning--button-on-app-designer-tile.png "앱 디자이너 타일의 누락된 구성 요소 경고")  
  
2.  필요한 자산을 추가하려면 캔버스 오른쪽에서 **필수** 탭을 클릭합니다. **필수** 탭은 앱에서 하나 이상의 필수 자산이 누락되었을 때 표시됩니다.  
  
     탭에 필수 구성 요소 목록이 표시됩니다.  
  
     ![응용 프로그램에서 누락된 구성 요소 목록이 표시되는 필수 탭](media/app-designer-required-components-tab.png "응용 프로그램에서 누락된 구성 요소 목록이 표시되는 필수 탭")  
  
3.  추가할 자산을 선택하고 **종속성 추가**를 선택합니다. 필요한 자산을 추가하면 자산을 추가한 타일의 수가 감소합니다.  
  
    > [!NOTE]
    >  다양한 앱 구성 요소에 공통 자산이 필요한 경우, 예를 들어 대시보드 및 엔터티에 양식이 필요하고 대시보드 종속성 트리에서 해당 자산을 한 번만 추가하면 종속성 개수는 대시보드 타일에서는 줄어들지만 엔터티 타일에서는 줄지 않습니다. 그러나 종속성은 둘 다를 해결합니다.  
    >   
    >  **최신 종속성 가져오기** ![앱 디자이너의 최신 종속성 가져오기 단추](media/app-designer-get-latest-dependencies.png "앱 디자이너에서 최신 종속성 가져오기 단추")를 선택하거나 **유효성 검사**를 다시 선택하여 최신 종속성 집합을 가져옵니다. 앱을 저장한 후에는 이 단추만 표시됩니다.  
  
     제안된 필수 구성 요소를 추가하고 싶지 않다면 **종속성 숨기기**를 선택합니다. 앱 디자이너에서 앱을 열 때 해결되지 않은 경고가 다시 나타나면 **유효성 검사** 또는 **최신 종속성 가져오기** ![앱 디자이너의 최신 종속성 가져오기 단추](media/app-designer-get-latest-dependencies.png "앱 디자이너에서 최신 종속성 가져오기 단추")를 선택합니다.  
  
    > [!NOTE]
    >  지금 종속성을 숨기면 나중에 이 앱을 내보내고자 할 때 모든 종속성 다시 표시됩니다.  
  
## <a name="publish-an-app-using-the-app-designer"></a>앱 디자이너를 사용하여 앱 게시

사용자가 사용할 수 있도록 앱을 게시합니다.  
  
 구성 요소를 추가하고 유효성을 검사하고 앱을 저장한 다음 명령 모음에서 **게시**를 선택합니다. [내 앱](advanced-navigation.md#apps) 페이지의 앱 타일에서 앱을 게시할 수도 있습니다. 게시하려는 앱 타일의 오른쪽 아래에 있는 **편집 중인 앱** 보기에서 **추가 옵션** 단추(**...**)를 선택한 다음 **게시**를 선택합니다.  
  
 앱 상태가 게시됨으로 변경됩니다. 앱 디자이너의 오른쪽 위 모서리에 표시됩니다. 앱이 **편집 중인 앱** 보기에서 **게시된 앱** 보기로 이동하며 앱 타일에 게시된 날짜가 표시됩니다.  
  
> [!NOTE]
> - 앱에 대한 유효성 검사에서 오류가 있는 경우 오류가 알림 표시줄에 표시됩니다. 이 오류를 해결하기 전까지 앱을 게시할 수 없습니다.  
> - 저장하기 전까지 앱을 게시할 수 없습니다.  

## <a name="next-steps"></a>다음 단계  
[PowerApps에서 모델 기반 앱 공유](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [모바일 장치에서 모델 기반 앱 실행](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
