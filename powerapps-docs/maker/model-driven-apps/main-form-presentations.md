---
title: PowerApps의 모델 기반 앱 기본 양식 프레젠테이션 | MicrosoftDocs
description: 다른 장치에 표시될 때 기본 양식이 나타나는 방법 알아보기
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9ed031f75235cfb47a2206de0a814fb008a335bd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702550"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>모델 기반 앱 기본 양식이 여러 장치에 표시되는 방식

기본 양식은 모든 모델 기반 앱 클라이언트에서 사용됩니다. 이 양식은 사용자가 웹 브라우저, 휴대폰용 Dynamics 365, 태블릿용 Dynamics 365 또는 Dynamics 365 for Outlook을 사용하는지 여부와 상관없이 일관적인 사용자 환경을 제공합니다.  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>기본 양식  
 엔터티에 존재하는 모든 기본 양식은 다음 표의 요소에 따라 다르게 표시될 수 있습니다. 기본 양식을 디자인할 때 다른 각 프레젠테이션에서 어떻게 작동하는지 고려하십시오.  
  
|프레젠테이션|설명|  
|------------------|-----------------|  
|**업데이트됨**|[업데이트된 엔터티 및 클래식 엔터티](create-design-forms.md#updated-versus-classic-entities) 그리고 사용자 지정 엔터티에 대해 업데이트된 양식은 Dynamics 365 (online) 및 Dynamics 365 On-premises에서 새로운 사용자 환경을 제공합니다. 이러한 양식에는 더욱 새로운 명령 모음 디자인이 있으며 자동 저장 및 비즈니스 프로세스 흐름 같은 추가 기능을 사용할 수 있습니다.|  
|**Dynamics 365 for tablets**| Dynamics 365 for tablets는 태블릿에 최적화된 방식으로 기본 양식의 내용을 제공합니다.|  
|**핸드폰용 Dynamics 365**| Dynamics 365 for phones는 휴대폰에 최적화된 방식으로 기본 양식의 내용을 제공합니다.|  
|**클래식**|이러한 양식은 업데이트되지 않은 엔터티를 위한 것입니다. 이러한 양식은 양식 왼쪽에 있는 명령 모음 및 탐색 창보다 리본을 사용합니다.<br /><br /> 이러한 양식에는 2열 레이아웃이 있습니다.|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>업데이트된 양식  
 이 다이어그램은 업데이트된 엔터티 양식에서 볼 수 있는 일반적인 구성 요소를 나타냅니다.  
  
 ![다이어그램은 Dynamics 365에서 업데이트된 엔터티 양식 구조를 표시함](media/updated-form-diagram.png "다이어그램은 Dynamics 365에서 업데이트된 엔터티 양식 구조를 표시함")  
  
 업데이트된 엔터티의 경우 양식의 레이아웃은 넓은 디스플레이와 창 크기로 작동합니다. 창 너비가 감소하면 압축하거나 오른쪽으로 스크롤하는 대신 아래로 스크롤하여 열을 사용할 수 있도록 열을 탭하여 아래로 이동합니다.  
  
 다음 표는 업데이트된 엔터티에 대한 기본 양식의 사용 가능한 구성 요소를 요약합니다.  
  
|구성 요소|요약|  
|---------------|-------------|  
|**탐색 모음**|사이트 맵의 데이터를 사용하여 응용 프로그램의 다른 영역으로 이동할 수 있는 기능을 제공합니다.<br /><br /> 클래식 양식으로 사용되는 탐색 창은 업데이트된 양식에는 포함되지 않습니다. 레코드 컨텍스트에서 탐색 모음은 관련 레코드의 보기에 대한 액세스를 제공합니다. 탐색 창을 사용하거나 탐색 모음을 사용하여 관련 레코드를 탐색하는 대신 유용한 관련 엔터티를 표시하도록 구성된 하위 표를 추가하면 대부분의 사용자에게 더 나은 환경을 제공합니다.|  
|**명령 모음**|리본에 정의된 데이터를 사용하여 레코드 관련 명령을 제공합니다.<br /><br /> 처음 5개 명령 뒤에 추가 명령을 선택하도록 플라이아웃 메뉴를 제공하는 줄임표(![추가 명령 단추](media/not-available.gif "M추가 명령 단추"))가 표시됩니다|  
|**이미지**|엔터티에 이미지 필드가 있고 엔터티 **기본 이미지** 옵션이 **기본 이미지**로 설정되어 있으면 양식이 이미지를 표시하도록 구성되어 있을 경우 이미지가 머리글에 표시될 수 있습니다.|  
|**머리글**|머리글에 있는 필드는 사용자가 양식의 본문을 통해 아래로 스크롤해도 계속 표시됩니다.<br /><br /> 최대 4개까지 필드를 머리글에 배치할 수 있습니다. 여러 줄 텍스트, 웹 리소스 또는 iFrame은 머리글에 배치할 수 없습니다. 머리글과 바닥글은 섹션과 일부 속성을 공유합니다.|  
|**프로세스 컨트롤**|엔터티에 활성 비즈니스 프로세스 흐름이 있을 경우 프로세스 컨트롤은 머리글 아래에 표시됩니다. 추가 정보: [비즈니스 프로세스 흐름](/flow/business-process-flows-overview)|  
|**본문**|본문은 탭이 포함된 양식의 스크롤 가능한 부분입니다.|  
|**탭**|양식의 본문에서 탭은 가로 분할을 제공합니다. 탭에는 표시할 수 있는 레이블이 있습니다. 레이블이 표시되면, 탭은 레이블을 선택하여 내용을 표시하거나 숨기도록 확장하거나 축소할 수 있습니다.<br /><br /> 탭에는 최대 3개까지 열을 포함하며 각 열의 너비는 전체 너비에 비례하여 설정할 수 있습니다. 새 탭을 만들 때 각 열은 섹션으로 미리 채워집니다.|  
|**섹션**|섹션은 탭 열에서 사용 가능한 공간을 차지합니다. 섹션에는 표시할 수 있는 레이블이 있고 레이블 아래에는 줄이 표시될 수 있습니다.<br /><br /> 섹션에는 최대 4개까지 열을 사용할 수 있으며 섹션에 있는 필드의 레이블이 표시되는 방법을 표시하는 옵션이 포함됩니다.|  
|**필드**|필드는 사용자가 엔터티 레코드의 데이터를 보거나 편집하는 데 사용하는 컨트롤을 표시합니다. 필드는 섹션 내에서 최대 4개까지 열을 차지하도록 서식을 지정할 수 있습니다.|  
|**공백**|공백은 섹션 열에 공백을 추가할 수 있도록 합니다.|  
|**하위 표**|하위 표는 양식 내에 목록을 표시할 수 있습니다. 업데이트된 엔터티의 양식에서는 하위 표를 사용하여 차트를 표시할 수 있는 기능을 사용할 수 없습니다.|  
|**빠른 보기 양식**|빠른 보기 양식은 양식의 조회 필드에서 참조하는 레코드의 데이터를 표시합니다. 조회의 대상이 되는 엔터티에는 양식에 추가할 수 있으려면 빠른 보기 양식이 있어야 합니다. 추가 정보: [빠른 보기 양식 만들기 및 편집](create-edit-quick-view-forms.md)|  
|**웹 리소스**|HTML 및 Microsoft Silverlight 웹 리소스는 기본 양식에 추가할 수 있지만 Dynamics 365 for phones 및 tablets를 사용할 때는 표시할 수 없습니다.|  
|**iFrame**|다른 웹 사이트의 웹 페이지를 표시하도록 구성하는 인라인 프레임입니다. **중요:**  <ul><li>iFrame에 표시된 페이지가 다른 도메인에 있을 경우 브라우저는 더 높은 수준의 보안을 적용합니다. 따라서 양식의 데이터와 상호 작용하는 iFrame의 콘텐츠에 대한 요구 사항을 복잡하게 할 수 있습니다.</li><li>다른 엔터티 양식에 포함된 iFrame 내에는 엔터티 양식을 표시할 수 없습니다. 
|**Bing 지도**|이 컨트롤이 업데이트된 엔터티의 양식에 표시되고 시스템 설정 **Bing 지도 사용**이 유효한 Bing 지도 키와 사용할 수 있을 경우 이 컨트롤은 업데이트된 엔터티의 주소 중 하나의 위치를 표시하는 양식에 한 번 사용할 수 있습니다. 추가 정보: [Bing 맵 구성](configure-bing-maps-legacy.md)|  
|**바닥글**|여러 개의 필드, 웹 리소스 또는 iFrame을 바닥글에 추가할 수 있습니다. 필드는 바닥글에 표시되면 읽기 전용입니다. 머리글과 바닥글은 섹션과 일부 속성을 공유합니다.|  
|**상태 표시줄**|상태 표시줄은 레코드, 알림 영역 및 저장 단추의 상태 필드를 표시합니다.|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>Dynamics 365 for phones 및 tablets 양식  
 대부분의 시스템 엔터티 및 사용자 지정 엔터티는 Dynamics 365 for phones 및 tablets에 사용할 수 있습니다. 이러한 엔터티의 기본 양식은 휴대폰 및 태블릿에 최적화된 프레젠테이션으로 변환됩니다.  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>Dynamics 365 for phones 및 tablets에 사용되는 엔터티  
 Dynamics 365 for phones 및 tablets에서 사용 가능한 엔터티만 기본 양식의 이 프레젠테이션을 사용합니다. 추가 정보: [Dynamics 365 for phones 및 tablets에 표시된 엔터티](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity)를 참조하십시오.  
  
### <a name="form-design"></a>양식 디자인  
 Dynamics 365 for phones 및 tablets는 많은 기본 양식 요소를 사용하고 휴대폰 및 태블릿에 최적화된 방식으로 표시합니다. 다음 다이어그램은 웹 앱에서 태블릿 및 휴대폰 앱까지의 재배치를 보여 줍니다.  
  
 **웹 앱**  
  
 ![웹 응용 프로그램에서 Dynamics 365 양식 리플로](media/custon-reflow-web-app.png "웹 응용 프로그램에서 Dynamics 365 양식 리플로")  
  
 **태블릿 앱**  
  
 ![태블릿 앱으로 Dynamics 365 양식 리플로](media/reflow-tablet-app.png "태블릿 앱으로 Dynamics 365 양식 리플로")  
  
 **휴대폰 앱**  
  
 ![휴대폰 앱으로 Dynamics 365 양식 리플로](media/custon-reflow-phone-app.png "휴대폰 앱으로 Dynamics 365 양식 리플로")  
  
 양식 요소는 Dynamics 365 for tablets에서 사용자가 화면을 살짝 밀어 보기 포트 내에서 요소를 표시하도록 변경하는 넓은 파노라마 레이아웃으로 변환됩니다. Dynamics 365 for phones에서 사용자는 화면을 밀어 다른 열, 요소 창을 보고 모든 열 위에 프로세스 컨트롤이 나타납니다.  
  
### <a name="view-port-element"></a>보기 포트 요소  
 다음 항목은 양식의 컨텍스트에서 보기 포트에서 항상 표시됩니다.  
  
 **탐색 모음**  
 탐색 모음은 터치에 최적화된 사이트 맵의 프레젠테이션입니다. 추가 정보: [탐색 옵션 변경](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions)  
  
 **홈**  
 홈 단추는 Dynamics 365 for phones 및 tablets의 시작 페이지인 대시보드로 이동합니다.  
  
 **프로세스 컨트롤**  
 엔터티에 사용 가능한 비즈니스 프로세스가 있으면 Dynamics 365 for tablets에서 검색 컨트롤 옆의 오른쪽 위와 Dynamics 365 for phones에서 화면 상단에 표시됩니다.  
  
 **검색**  
 사용자는 검색 컨트롤을 탭하여 화면을 열어 레코드를 검색할 수 있습니다.  
  
 **명령 모음**  
 기본적으로 웹 브라우저에서 실행되는 앱에 표시되는 명령의 일부는 Dynamics 365 for phones 및 tablets 앱에 표시되지 않습니다. 웹 응용 프로그램과 마찬가지로 명령 모음은 상황에 맞으며 현재 표시되거나 선택된 항목에 따라 사용 가능한 명령이 변합니다. 추가 정보: [명령 변경](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands)  
  
### <a name="form-elements"></a>양식 요소  
 표시되는 양식 요소는 기본 양식에서 가져오고 보기 포트를 통해 보는 일련의 패널로 나타납니다.  
  
 Dynamics 365 for tablets에서 첫 번째 패널에는 레코드에 있는 관계에 대한 연락처 정보가 표시됩니다. Dynamics 365 for phones에서 첫 번째 패널은 관계 타일 위에 있는 양식의 머리글 필드도 표시합니다.  
  
 ![태블릿용 Dynamics 365 관계 패널](media/mobile-app-form-relationships.png "태블릿용 Dynamics 365 관계 패널")  
  
 연락처 및 사용자 양식의 경우 상위 항목은 레코드의 통신 카드를 표시합니다. 통신 카드는 사용자와 통신을 시작하는 단추를 제공합니다. 다른 엔터티의 경우 통신 카드는 기본 양식에 포함된 연락처 빠른 보기 양식이 있을 경우 표시됩니다.  
  
 엔터티 관계를 기반으로 추가 타일을 표시할 수 있지만 다음 엔터티에 대한 타일은 사용자 지정할 수 없습니다.  
  
|엔터티|타일|  
|------------|-----------|  
|거래처|담당자|  
|연락처|회사 이름, 담당자|  
|잠재 고객|담당자|  
|영업 기회|거래처, 담당자|  
  
 양식 편집기에서 나머지 타일을 사용자 지정할 수 있습니다. 순서는 고정되어 있지만 관계 패널에 어떤 요소를 표시할지 설정할 수 있습니다.  
  
 Dynamics 365 for tablets에서 두 번째 패널은 양식에서 첫 번째 탭의 이름으로 시작합니다. 머리글에 포함된 모든 필드가 포함되고 첫 번째 탭의 내용이 포함됩니다. Dynamics 365 for phones에서 머리글은 첫 번째 열에 나타납니다.  
  
 ![태블릿용 CRM 양식 첫 번째 패널](media/mobile-app-form-first-panel.png "태블릿용 CRM 양식 첫 번째 패널")  
  
 양식에 대해 프로세스 흐름 활성 상태인 경우 Dynamics 365 for tablets에서 세 번째 탭은 프로세스의 현재 스테이지에 대한 작업을 표시합니다. Dynamics 365 for phones에서 프로세스 컨트롤은 패널 위에 있으며 선택되면 사용자의 현재 창 위로 확장되고 항상 표시되고 사용할 수 있습니다.  
  
 양식의 나머지 패널에는 양식의 탭 내용이 포함됩니다. 발견된 하위 표는 별도의 패널로 표시됩니다.  
  
 Dynamics 365 for phones 및 tablets 양식은 항상 탭과 하위 표의 레이블을 표시합니다. **양식에 레이블 표시** 설정이 적용되지 않습니다.  
  
> [!NOTE]
>  모바일 장치의 성능을 최적화하기 위해 개체 수를 5개 탭이나 75개 필드 및 10개 하위 표로 제한됩니다.  
  
 Dynamics 365 for phones 및 tablets 양식은 다음을 지원하지 않습니다.  
   
-   Bing 지도  
  
-   Yammer
  
-   피드 알림  
  
-   테마  
  
 또한 엔터티 이미지는 목록 보기와 연락처 카드에서 표시되지만 실제 양식에서는 표시되지 않습니다.  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>여러 양식  
 Dynamics 365 for phones 및 tablets는 여러 양식을 지원하지만 사용자가 두 번 이상 액세스할 수 있을 경우 양식 간 전환하는 방법은 제공하지 않습니다. 액세스해야 하는 양식 순서에서 첫 번째 양식이 표시됩니다.  
  
 예를 들어 영업 기회 엔터티에 대해 다음 기본 양식이 있고 각 양식에 대해 다음 보안 역할을 할당한 경우 다음 표에 표시된 양식 순서가 표시됩니다.  
  
|양식 순서|양식 이름|보안 역할|  
|----------------|---------------|--------------------|  
|1|**영업 양식 1**|영업 직원|  
|2|**영업 양식 2**|영업 직원 및 영업 관리자|  
|3|**영업 양식 3**|영업 관리자|  
|4|**영업 양식 4**|영업부 부서장|  
  
-   영업 직원 역할을 가진 사용자는 항상 **영업 양식 1**을 봅니다.  
  
-   영업 관리자 역할을 가진 사용자는 항상 **영업 양식 2**를 봅니다.  
  
-   영업부 부서장 역할을 가진 사용자는 항상 **영업 양식 4**를 봅니다.  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>클래식 양식  
 다음 다이어그램은 기본 프레젠테이션에 사용된 기본 양식 구성 요소를 표시합니다.  
  
 ![주 양식 요소](media/elements.png "주 양식 요소")  
  
 업데이트된 엔터티에 대한 양식은 클래식 양식에서 여러 구성 요소를 상속 받지만 중요한 차이가 있습니다.  
  
 기본 프레젠테이션을 사용하는 양식에는 탐색 모음이 포함되지 않고 탐색 모음 대신 리본이 사용됩니다. 이러한 양식은 엔터티 이미지, 프로세스 컨트롤, 빠른 보기 양식, 자동 저장 또는 Bing 지도를 지원하지 않습니다. 머리글의 필드는 편집할 수 없습니다.  
  
 양식 도우미가 `Article`과 같은 특정 엔터티에 대해 노출되었습니다.  
  
## <a name="next-steps"></a>다음 단계  
 [양식 만들기 및 디자인](create-design-forms.md)   

 
