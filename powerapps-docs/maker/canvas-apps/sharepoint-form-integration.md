---
title: SharePoint 양식 통합 이해 | Microsoft Docs
description: SharePoint와 사용자 지정 양식의 작업 방식 이해
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fbfe1b62091ff7a4fb84b899518fc941f99d7abb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674848"
---
# <a name="understand-sharepoint-forms-integration"></a>SharePoint 양식 통합 이해
이제 Power Apps에서 [SharePoint 목록 양식을 쉽게 사용자 지정할](customize-list-form.md) 수 있습니다. 이 문서에서는 이러한 양식의 작업 방식과 사용자 지정하는 방법을 자세히 설명합니다.

SharePoint 목록의 양식을 사용자 지정한 경험이 있다면 기본 생성 양식에서 항목 생성, 표시 또는 편집과 같은 모든 작업이 가능하다는 것을 알 수 있습니다. 이러한 작업은 이는 생성된 수식과 **SharePointIntegration** 컨트롤의 도움으로 수행됩니다.

## <a name="understand-the-default-generated-form"></a>기본 생성 양식 이해

기본 생성 양식은 다음과 같은 컨트롤 및 그에 해당하는 기본값으로 구성됩니다.

* **FormScreen1** - 양식을 포함하는 [화면](controls/control-screen.md)입니다.

* **SharePointForm1** - 목록 항목을 작성, 표시 또는 편집하는 데 사용되는 [양식](working-with-forms.md)입니다.

    * **데이터 원본** - 양식이 사용자 지정된 목록입니다.

    * **항목** - 목록에서 선택한 항목입니다. Power Apps Studio에서 작업 하는 경우 편의를 위해 목록의 첫 번째 () 항목으로 설정 됩니다.

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected),First('*YourListName*'),SharePointIntegration.Selected)**

    * **OnSuccess** - 항목 만들기나 저장이 완료되면 양식이 다시 설정되고 SharePoint에서 양식이 숨겨집니다.

        **ResetForm(SharePointForm1); RequestHide()**

* **SharePointIntegration** - SharePoint와 PowerApps 사이에서 사용자 작업의 전달을 담당하는 컨트롤입니다.

    * **데이터 원본** - 양식이 사용자 지정된 목록입니다.

        **'*YourListName*'**

    * **OnNew** - **SharePointForm1**을 새 모드로 설정합니다.

        **NewForm(SharePointForm1)**

    * **OnView** - **SharePointForm1**을 보기 모드로 설정합니다.

        **ViewForm(SharePointForm1)**

    * **OnEdit** - **SharePointForm1**을 편집 모드로 설정합니다.

        **EditForm(SharePointForm1)**

    * **OnSave** - 변경 내용을 **SharePointForm1**에 제출합니다. 양식 제출이 완료되면 **SharePointForm1.OnSuccess** 수식이 실행됩니다.

        **SubmitForm(SharePointForm1)**

    * **OnCancel** - **SharePointForm1**에 대한 변경 내용을 다시 설정합니다. SharePoint에서 사용자가 **취소**를 클릭하거나 탭하면 항상 양식을 숨깁니다.

        **ResetForm(SharePointForm1)**

이러한 기본값은 SharePoint 내에서 실행 하는 경우 양식이 작동 하는지 확인 합니다. 사용자가 SharePoint에서 상호 작용할 때 Power Apps 양식 모드를 변경 하 고 변경 내용이 SharePoint에 제출 되도록 합니다.

## <a name="understand-the-sharepointintegration-control"></a>SharePointIntegration 컨트롤 이해
**SharePointIntegration** 컨트롤은 SharePoint와 PowerApps 사이에서 사용자 작업을 전달합니다.

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>Power Apps Studio에서 양식을 사용자 지정 하는 경우를 사용 하는 것이 아니라 양식이 SharePoint에서 실행 되는 경우에만 **SharePointIntegration** 컨트롤에 대 한 속성에 액세스할 수 있습니다. 이러한 속성은 **OnStart** 또는 **OnVisible**에서 확인할 수 있습니다. 

**SharePointIntegration** 컨트롤에는 다음과 같은 속성이 있습니다.

**Selected** - SharePoint 목록에서 선택한 항목입니다.

**OnNew** - 사용자가 SharePoint의 **새로 만들기** 단추를 클릭 또는 탭하거나 **항목 만들기** 양식을 열 때 앱이 응답하는 방식입니다.

**OnView** - 사용자가 SharePoint의 **항목**을 클릭 또는 탭하거나 **항목 세부 정보** 양식을 열 때 앱이 응답하는 방식입니다.

**OnEdit** - 사용자가 SharePoint의 **모두 편집** 단추를 클릭 또는 탭하거나 **항목 편집** 양식을 열 때 앱이 응답하는 방식입니다.

**OnSave** - 사용자가 SharePoint의 **저장** 단추를 클릭하거나 탭할 때 앱이 응답하는 방식입니다.

**OnCancel** - 사용자가 SharePoint의 **취소** 단추를 클릭하거나 탭할 때 앱이 응답하는 방식입니다.

**SelectedListItemID** - SharePoint 목록에서 선택한 항목의 항목 ID입니다.

**데이터 원본** – 양식이 표시, 편집 또는 작성할 레코드가 포함된 목록입니다. 이 속성을 변경하면 **Selected** 및 **SelectedItemID** 속성이 작동을 중지할 수 있습니다.

## <a name="customize-the-default-form"></a>기본 양식 사용자 지정
기본 생성 양식과 **SharePointIntegration** 컨트롤에 대한 이해를 바탕으로 수식을 변경하여 양식을 사용자 지정할 수 있습니다. 다음은 양식을 사용자 지정할 때 유의할 사항입니다.

* 항목을 만들거나 표시하거나 편집하는 별도의 사용자 지정 환경을 만들려면 변수를 설정하거나 다른 화면으로 이동하도록 **SharePointIntegration** 컨트롤의 **OnNew**, **OnView** 또는 **OnEdit** 수식을 설정합니다.

* **SharePointIntegration** 컨트롤의 **OnSave** 수식을 사용하여 사용자가 SharePoint에서 **저장**을 클릭하거나 탭할 때 수행할 작업을 사용자 지정합니다. 양식이 여러 개 있는 경우 현재 사용 중인 양식에 대해서만 변경 내용을 제출해야 합니다.

  > [!TIP]
  >    **OnNew**, **OnView** 및 **OnEdit** 수식의 변수에 다른 값을 설정합니다. **OnSave** 수식에 이 변수를 사용하면 어떤 양식을 사용 중인지 확인할 수 있습니다.

* 모든 양식의 **OnSuccess** 수식에 **RequestHide()** 를 포함해야 합니다. 이 항목을 잊어 버리면 SharePoint에서 양식을 언제 숨길지 알 수 없게 됩니다.

* 사용자가 SharePoint에서 **취소**를 클릭하거나 탭할 때 양식 숨기기를 제어할 수 없으므로, **SharePointIntegration** 컨트롤의 **OnCancel** 수식에서 양식을 다시 설정해야 합니다.

* **SharePointIntegration** 컨트롤의 속성은 **OnStart** 또는 **OnVisible**에서 지원되지 않을 수 있습니다. 또한 해당 이벤트는 목록을 로드할 때 한 번만 실행합니다. **OnNew**, **OnView** 또는 **OnEdit** 수식을 사용하여 양식이 매번 사용자에게 표시되기 전에 논리를 실행할 수 있습니다. 
