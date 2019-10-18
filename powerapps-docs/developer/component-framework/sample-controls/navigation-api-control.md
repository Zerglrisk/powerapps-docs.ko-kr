---
title: " 탐색 API 구성 요소 | Microsoft Docs"
description: 탐색 api 구성 요소 구현
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 85dd665f7a3dc92b5198cfd8429b59af0896d5cc
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340348"
---
# <a name="implementing-navigation-api-component"></a>탐색 API 구성 요소 구현

이 샘플 구성 요소는 PowerApps 구성 요소 프레임 워크 탐색 API의 일부로 제공 되는 다양 한 방법을 탐색 합니다. 이 샘플에서는 표시 된 값과 일치 하는 탐색 API의 각 메서드를 호출 하는 단추 형식의 일련의 입력 요소를 만듭니다.  

> [!div class="mx-imgBorder"]
> ![탐색 api 구성 요소](../media/navigation-api-control.png "탐색 api 구성 요소")

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="manifest"></a>Manifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSNavigationAPI" version="1.0.0" display-name-key="TS_NavigationAPI_Display_Key" description-key="TS_NavigationAPI_Desc_Key" control-type="standard">
        <type-group name="numbers">
            <type>Whole.None</type>
            <type>Currency</type>
            <type>FP</type>
            <type>Decimal</type>
        </type-group>
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_NavigationAPI.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code

```TypeScript
import {IInputs, IOutputs} from "./generated/ManifestTypes";
export class TSNavigationAPI implements ComponentFramework.StandardControl<IInputs, IOutputs> {
// PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens. 
private _notifyOutputChanged: () => void;
// Reference to the div element that hold together all the HTML elements that we are creating as part of this control
private divElement: HTMLDivElement;
// Reference to the button that invokes the openAlertDialog command
private openAlertDialogButton: HTMLButtonElement;
// Reference to the button that invokes the openConfirmDialog command
private openConfirmDialogButton: HTMLButtonElement;
// Reference to the button that invokes the openFile command
private openFileButton: HTMLButtonElement;
// Reference to the button that invokes the openUrl command
private openUrlButton: HTMLButtonElement;
// Reference to the control container HTMLDivElement
// This element contains all elements of our custom control example
private _container: HTMLDivElement;
// Reference to ComponentFramework Context object
private _context : ComponentFramework.Context<IInputs>;
/**
* Empty constructor.
*/
constructor()
{
}
/**
* Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
* Data-set values are not initialized here, use updateView.
* @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
* @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
* @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
* @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
*/
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
{
this._notifyOutputChanged = notifyOutputChanged;
this._context = context;
this._container = container;
this.divElement = document.createElement("div");
this.divElement.setAttribute("class","TSNavigationAPI");
// Create the HTML button elements for openAlertDialog button
this.openAlertDialogButton = document.createElement("button");
this.openAlertDialogButton.setAttribute("id","openAlertDialogButton");
this.openAlertDialogButton.innerHTML = "openAlertDialogButton";
// Create the HTML button elements for openConfirmDialog button
this.openConfirmDialogButton = document.createElement("button");
this.openConfirmDialogButton.setAttribute("id","openConfirmDialogButton");
this.openConfirmDialogButton.innerHTML = "openConfirmDialogButton";
// Create the HTML button elements for openFile button
this.openFileButton = document.createElement("button");
this.openFileButton.setAttribute("id","openFileButton");
this.openFileButton.innerHTML = "openFileButton";
// Create the HTML button elements for openUrl button
this.openUrlButton = document.createElement("button");
this.openUrlButton.setAttribute("id","openUrlButton");
this.openUrlButton.innerHTML = "openUrlButton";
// bind the function which invokes the respective API's to each of the buttons
this.openAlertDialogButton.addEventListener("click",this.raiseEvent.bind(this));
this.openConfirmDialogButton.addEventListener("click",this.raiseEvent.bind(this));
this.openFileButton.addEventListener("click",this.raiseEvent.bind(this));
this.openUrlButton.addEventListener("click",this.raiseEvent.bind(this));
// append all the button elements to the parent div element for control.
this.divElement.appendChild(this.openAlertDialogButton);
this.divElement.appendChild(this.openConfirmDialogButton);
this.divElement.appendChild(this.openFileButton);
this.divElement.appendChild(this.openUrlButton);
// append the parent div element in the control to the control's container
this._container.appendChild(this.divElement);
}
/**
* Handles the events raised by each of the buttons that are binded according to their id
* @param event : event object that contains all the properties regarding the raised event
*/
public raiseEvent(event: Event,)
{
var inputSource = (event.srcElement! as Element)!.id;
switch(inputSource)
{
    case "openAlertDialogButton": this._context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
    break;
    case "openConfirmDialogButton": this._context.navigation.openConfirmDialog({title:"Confirmation Dialog", text:"This is a confirmation.",},{height:200, width:450}).then(
        function(success)
        {
            if(success.confirmed)
            {
                document.getElementById("openConfirmDialogButton")!.innerHTML = "Ok button clicked.";
            }
            else
            {
                document.getElementById("openConfirmDialogButton")!.innerHTML = "Cancel or X button clicked.";
            }
        }
    );
    break;
    case "openFileButton": 
        var file = {
                    fileContent: "U2FtcGxlIGNvbnRlbnQgZm9yIERlbW8=", //Contents of the file in base64 encoded format. 
                    fileName: "Sample.txt", //Name of the file.
                    fileSize: 29, //Size of the file in KB.
                    mimeType: "text/plain" //MIME type of the file.
                    };
        this._context.navigation.openFile(file,{openMode:2});
    break;
    case "openUrlButton": this._context.navigation.openUrl("https://www.microsoft.com");
    break;
};
//this._notifyOutputChanged();
}
/**
* Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
* @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
*/
public updateView(context: ComponentFramework.Context<IInputs>,): void
{
this._context = context;
}
/** 
* It is called by the framework prior to a control receiving new data. 
* @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
*/
public getOutputs(): IOutputs
{
// no-op: method not leveraged by this example custom control
return { };
}
/** 
* Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
* i.e. canceling any pending remote calls, removing listeners, etc.
*/
public destroy()
{
}
}
```

## <a name="resources"></a>리소스

```css
.SampleNamespace\.TSNavigationAPI button {
  background-color: rgb(59, 121, 183);
  border: 1px solid black;
  color: white;
  padding: 10px 24px;
  cursor: pointer;
  width: 100%;
  display: block;
}
.SampleNamespace\.TSNavigationAPI button:not(:last-child) {
  border-bottom: none;
}
.SampleNamespace\.TSNavigationAPI button:hover {
  background-color: #c2c2c2;
}
```

@No__t_0 메서드는 메시지 및 단추를 포함 하는 경고 대화 상자를 표시 하는 기능을 제공 합니다. 경고 대화 상자가 닫히거나 대화 상자를 로드할 때 오류가 발생 하는 경우에도 콜백 메서드를 구현할 수 있습니다.
  
이 샘플에서는 경고 대화 `openAlertDialogButton`를 클릭 하면 대화 상자를 닫을 때 `OK` 단추나 `X` 단추를 사용 하 여 대화 상자를 닫을 때 해당 값을 `Alert dialog closed`로 설정 합니다.

> [!NOTE]
> 이는 ClientAPI에서 [Xrm](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openalertdialog) 메서드를 호출 하는 것과 유사 합니다.  

@No__t_0 메서드는 메시지 및 두 개의 단추를 포함 하는 경고 대화 상자를 표시 하는 기능을 제공 합니다. 이 메서드를 사용 하 여 클릭 한 단추를 기준으로 다른 논리를 구현할 수 있습니다. 단추 중 하나를 클릭 하 여 대화 상자를 닫을 때 호출 되는 성공 콜백을 구현할 수 있습니다.
  
이 샘플에서는 `openConfirmDialogButton` 클릭 하 고 클릭 한 단추에 따라 값을 `Ok` 또는 `Cancel` 또는 `X`으로 설정 하는 경우 확인 대화 상자를 보여 줍니다.

> [!NOTE]
> 이는 ClientAPI에서 [Xrm](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openconfirmdialog) 메서드를 호출 하는 것과 유사 합니다.
  
@No__t_0 메서드는 파일을 열 수 있는 기능을 제공 합니다. 파일 이름, 콘텐츠, mimetype 및 filesize을 포함 하는 파일 개체를 전달 해야 합니다. 또한 파일을 열 때 사용할 모드의 선택적 매개 변수를 1 또는 2로 전달할 수 있습니다. 기본값 1은 파일을 읽기 또는 열기 모드로 여는 것입니다.
  
이 샘플은 `openFileButton` 클릭 하 여 저장 모드에서 `SampleDemo.txt` 라는 파일을 엽니다.

> [!NOTE]
> 이는 ClientAPI에서 [system.windows.forms.openfiledialog.openfile](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openfile) 메서드를 호출 하는 것과 유사 합니다.

@No__t_0 메서드는 URL을 여는 기능을 제공 합니다. Url을 메서드에 문자열로 전달 하 고, 새 창에서 URL을 열도록 하려면 height, width 및 openInNewWindow의 선택적 매개 변수를 true로 전달 해야 합니다.
  
이 샘플은 새 창을 열고 `openUrlButton`를 클릭 하 여 microsoft.com 홈 페이지를 로드 합니다.

> [!NOTE]
> 이는 ClientAPI에서 [Xrm](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openurl) 메서드를 호출 하는 것과 유사 합니다.

### <a name="related-topics"></a>관련 항목

[샘플 구성 요소 다운로드](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)

