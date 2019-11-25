---
title: PowerApps의 목록 보기에서 값과 함께 사용자 지정 아이콘 표시 | MicrosoftDocs
description: 보기에 사용자 지정 아이콘 그래픽을 표시하는 방법 알아보기
ms.custom: ''
ms.date: 02/14/2019
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
ms.assetid: af866aed-2586-4b6f-bb1c-3519baae3645
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e1facad3d5d6cb95e0441800f4d743d429f50787
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705498"
---
# <a name="display-custom-icons-alongside-values-in-list-views"></a>목록 보기에서 값과 함께 사용자 지정 아이콘 표시

<a name="GridIcons"></a>   

 PowerApps 환경 관리자 및 사용자는 보기에 그래픽을 추가하고 JavaScript를 사용하여 열 값을 기반으로 그래픽을 선택하는 데 사용되는 논리를 설정할 수 있습니다. 이 기능을 사용하면 텍스트 또는 숫자 값과 함께 아이콘을 표시하는 목록 보기를 사용자 지정할 수 있습니다. 

> [!div class="mx-imgBorder"] 
> ![](media/icon-in-opportunity-view.png "All Opportunities view with Rating column displaying icons and text value")
  
> [!NOTE]
>  표 아이콘은 웹 인터페이스에만 표시됩니다. [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] 또는 모바일 앱에서는 표시되지 않습니다.  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>사용자 지정 그래픽 및 JavaScript를 웹 리소스로 추가  
  
1.  사용자 지정에 필요한 새 그래픽 파일을 만듭니다. 아이콘 크기는 16x16 픽셀을 사용하는 것이 좋습니다(더 큰 이미지는 축소됨).  
  
2.  해당 값을 표시하는 아이콘을 설정하는 하나 또는 그 이상의 JavaScript 함수를 작성합니다.(일반적으로 사용자 지정하려는 각 열에 대해 하나의 함수가 필요합니다.) 각 함수는 이미지 이름 및 도구 설명 텍스트를 포함하는 배열을 반환하는 행 데이터 개체와 언어(LCID) 코드 입력을 허용해야 합니다. 함수 예제는 이 항목의 뒷부분에 나오는 [샘플 JavaScript 함수](#SampleJavascript)를 참조 하십시오.  
  
3.  관리자로 환경에 로그인하고 솔루션 탐색기를 엽니다.  
  
4.  **기본 솔루션** 팝업 창이 열립니다. 여기에서 **구성 요소** > **웹 리소스**로 이동합니다..  
  
5.  이제 사용자 지정 그래픽이 웹 리소스로 한 번에 하나씩 업로드됩니다. 도구 모음에서 **새로 만들기** 단추를 선택하여 새 웹 리소스를 만듭니다. 리소스를 만들 수 있는 다른 팝업 창이 열립니다. 합니다.  
  
    1.  새 리소스에 알기 쉬운 **이름**을 지정합니다. JavaScript 코드에서 각 그래픽을 참조하는 데 사용할 이름입니다.  
  
    2.  **유형**을 그래픽 파일을 저장하는 데 사용된 그래픽 형식(PNG, JPEG, 또는 GIF)으로 설정합니다.  
  
    3.  **파일 선택**을 선택하여 파일 브라우저 창을 엽니다. 그래픽 파일을 찾고 선택하는 데 사용합니다.  
  
    4.  **표시 이름** 및/또는 원할 경우 **설명**울 추가합니다.  
  
    5.  **저장**을 선택하고 **웹 리소스** 창을 닫습니다.  
  
6.  갖고 있는 각 그래픽 파일에 대해 이전 단계를 반복합니다.  
  
7.  이제 최종 웹 리소스로 해당 JavaScript를 추가합니다. 도구 모음에서 **새로 만들기**를 선택하여 새 웹 리소스를 만듭니다. 리소스를 만들 수 있는 다른 팝업 창이 열립니다. 합니다.  
  
    1.  새 리소스에 알기 쉬운 **이름**을 지정합니다.  
  
    2.  **유형**을 **스크립트(JScript)** 로 설정합니다.  
  
    3.  **유형** 설정 옆에 있는 **텍스트 편집기**를 선택하여 텍스트 편집기 창을 엽니다. 여기에 Javascript 코드를 붙여 넣고 **확인**을 선택하여 저장합니다.  
  
    4.  **표시 이름** 및/또는 원할 경우 **설명**울 추가합니다.  
  
    5.  **저장**을 선택하고 **웹 리소스** 창을 닫습니다.  
  
8.  **기본 솔루션** 팝업 창을 계속 연 채로 **구성 요소** > **엔터티** 트리를 확장하여 사용자 지정할 엔터티를 찾습니다.  
  
9. 엔터티를 확장하고 해당 **보기** 아이콘을 선택합니다.  
  
10. 선택한 엔터티에 대한 보기 목록이 표시됩니다. 목록에서 보기를 선택합니다. 그 다음 도구 모음에서 **기타 작업** 드롭다운 목록을 열고 **편집**을 선택합니다.  
  
11. 선택한 보기를 편집할 수 있도록 컨트롤 팝업 창이 열립니다. 보기의 일부인 각 열이 표시됩니다. 대상 열을 선택한 다음 **일반 작업** 상자의 **속성 변경**을 선택합니다. **열 속성 변경** 대화 상자가 열립니다. 여기에서 다음을 설정하십시오.  
  
    - **웹 리소스**: Javascript 함수를 저장하기 위해 만든 웹 리소스의 이름을 지정합니다(목록에서 **찾아보기** 선택).  
  
    - **함수 이름**: 선택한 열과 보기를 수정하기 위해 작성한 함수의 이름을 입력합니다.  
  
12. **확인**을 선택하여 **열 속성 변경** 대화 상자를 닫습니다.  
  
13. **저장 후 닫기**를 선택하여 보기를 저장합니다.  
  
14. 필요에 따라 각 엔터티, 보기 및 열에 대해 이 단계를 반복합니다.  
  
15. 준비 되면 **모든 사용자 지정 항목 게시**를 선택하여 변경 내용을 게시할 수 있습니다. 그런 다음 **기본 솔루션** 창을 닫습니다.  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>JavaScript 함수 예제  
 사용자 지정 아이콘 및 도구 설명을 표시하기 위한 JavaScript 함수는 layoutxml에서 지정된 전체 행 개체 및 사용자의 로캘 ID(LCID) 호출의 두 개의 인수를 필요로 합니다. LCID 매개 변수를 사용하면 여러 언어의 도구 설명 텍스트를 지정할 수 있습니다. 환경에서 지원되는 언어에 대한 자세한 내용은 [언어 활성화](/dynamics365/customer-engagement/admin/enable-languages) 및 [언어 팩 설치 또는 업그레이드](/dynamics365/customer-engagement/on-premises/install-or-upgrade-language-packs)를 참조하십시오. 코드에서 사용할 수 있는 로캘 ID(LCID) 값 목록은 [Microsoft에서 할당한 로캘 ID](https://go.microsoft.com/fwlink/?linkid=829588)를 참조하십시오.

  
 제한적인 미리 정의된 옵션을 가진 속성의 옵션 집합 유형에 대한 사용자 지정 아이콘을 추가하는 경우 지역화 문제를 방지하려면 레이블 대신 옵션의 정수 값을 사용해야 합니다.  
  
 다음 샘플 코드는 opportunityratingcode(등급) 특성의 다음 세 값(1: 관심 높음, 2: 관심 있음, 3: 관심 낮음) 중 하나를 기준으로 아이콘 및 도구 설명을 표시합니다. 샘플 코드에서 지역화된 도구 설명 텍스트를 표시하는 방법도 보여줍니다. 이 샘플에서 작업하려면 new_Hot, new_Warm 및 new_Cold과 같은 이름의 16x16 이미지를 사용하여 세 개의 이미지 웹 리소스를 만들어야 합니다.  

> [!IMPORTANT]
> 이 샘플에는 Dynamics 365 Sales 앱에서 사용할 수 있는 영업 기회 엔터티가 필요합니다.
  
```javascript
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (parseInt(coldata,10)) { 
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 <!-- This results in displaying icons with tooltips in the **Rating** column that depend on the value in each row. The result could look like this:  
  
 ![Custom column graphics example](../customize/media/custom-column-graphics-example.png "Custom column graphics example")  -->
 
 ### <a name="see-also"></a>참조
[모델 기반 앱 보기 이해](../model-driven-apps/create-edit-views.md)
