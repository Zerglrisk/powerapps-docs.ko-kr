---
title: " 지도 구성 요소 | Microsoft Docs"
description: 각도 JS를 사용 하 여 맵 구성 요소 구현
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: f4b8702ef39688bdfc5f3ce9a51bf5c8c6e0ff20
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341337"
---
# <a name="implementing-map-component"></a>맵 구성 요소 구현

이 샘플 구성 요소는 폼의 주소 필드와 상호 작용 하는 사용자 환경을 변경 합니다. 이 구성 요소는 주소의 텍스트 값과 함께 다른 탭 또는 화면으로 이동 하지 않고 맵의 특정 주소를 시각적으로 식별 하는 기능을 제공 합니다. 

> [!div class="mx-imgBorder"]
> ![지도 구성 요소](../media/map-control.png "맵 구성 요소")

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) 

## <a name="manifest"></a>Manifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSMapControl" version="1.0.0" display-name-key="TS_MapControl_Display_Key" description-key="TS_MapControl_Desc_Key" control-type="standard">
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_MapControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSMapControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // HTML IFrame element that will be used to render the map
  private _iFrameElement: HTMLIFrameElement;
  // PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // API Key used to activate and embed the maps automatically
  // NOTE: You can follow the documentation at https://developers.google.com/maps/documentation/embed/get-api-key to generate your own API Key
  private MAPS_API_KEY: string = "<Replace your Key here>";
  /**
   * Empty constructor.
   */
  constructor() {}
  /**
   * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
   * Data-set values are not initialized here, use updateView.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
   * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
   * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
   * @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
   */
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._notifyOutputChanged = notifyOutputChanged;
    this._context = context;
    this._iFrameElement = document.createElement("iframe");
    this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
    container.appendChild(this._iFrameElement);
  }
  /**
   * Checks if the url is not null and sets the value to the iFrame source to be loaded inside it and then notifies the ControlFramework that the output has changed
   * @param mapUrl : The url for the map that needs to be loaded inside the iFrame.
   */
  public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
  /**
   * Converts the string that is passed to a valid url that can be used to render the map for the location
   * @param addressString : any string that can be used to search for a location in maps
   * @returns the HTML encoded url that can be used to load the map if the addressString is non empty string
   */
  public buildMapUrl(addressString: string | undefined): string {
    if (addressString) {
      let url: string =
        "https://www.google.com/maps/embed/v1/place?key=" +
        this.MAPS_API_KEY +
        "&q=" +
        encodeURIComponent(addressString);
      return url;
    }
    return "";
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    this._context = context;
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    // no-op: method not leveraged by this example custom control
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy() {}
}
```

## <a name="resources"></a>리소스

```css
.SampleNamespace\.TSMapControl .mapVisibleStyle {
  width: 640px;
  height: 420px;
  visibility: visible;
}
.SampleNamespace\.TSMapControl .mapHiddenStyle {
  visibility: hidden;
}
```

매니페스트 파일에서 `Single line of Text` 형식의 속성을 정의 했습니다. 이를 사용 하 여 폼의 주소 필드에 바인딩합니다.  

> [!NOTE]
> 시장에서 사용할 수 있는 map API를 사용할 수 있습니다.이 예제에서는 Google Map API를 사용 하 여이 작업을 수행 하는 방법을 보여 줍니다. 구성 요소에 대 한 API 키를 만들어 Google Map API에 액세스 해야 합니다.지침을 따릅니다 (https://developers.google.com/maps/documentation/embed/get-api-key 생성).

구성 요소의 컨텍스트에서 액세스할 수 있는 `MAPS_API_KEY` 변수 이름을 만듭니다.
Google 지도 API를 사용 하면 `IFRAME` 내에서 지도를 렌더링할 수 있습니다. 따라서 생성 하는 URL을 사용 하 여 맵을 렌더링 하려는 `IFRAME` 요소를 만들어야 합니다. 기본적으로 맵은 숨겨지도록 지도를 설정 하 고 주소 값이 양식에 있는 경우에만 표시 합니다.

`buildMapUrl` 및 `renderMap` (하나로 병합) 주소 문자열을 받아서 맵 URL에 포함 한 다음 주소 문자열을 인코딩하고 IFRAME 요소의 src 요소를 각각 URL로 설정 합니다. 또한 **notifyOutputChanged** 메서드를 호출 하 여 렌더링이 변경 되었음을 구성 요소에 알립니다. 
 
```TypeScript
 public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
```

뷰가 업데이트 될 때마다 컨트롤이 새로 고쳐지는지 확인 하려면 [Updateview](../reference/control/updateview.md) 함수 내에서 `renderMap` 함수를 호출 해야 합니다. 

### <a name="related-topics"></a>관련 항목

[샘플 구성 요소 다운로드](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)