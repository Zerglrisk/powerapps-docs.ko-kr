---
title: " IFRAME 구성 요소 | Microsoft Docs"
description: IFRAME 구성 요소 구현
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d10b03c478f238df02ee7e1309c0e39e758ce4c9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340463"
---
# <a name="implementing-a-iframe-component"></a>IFRAME 구성 요소 구현

이 샘플에서는 폼의 여러 필드에 코드 구성 요소를 바인딩하고 이러한 필드의 값을 구성 요소에 대 한 입력 속성으로 사용 하는 방법을 설명 합니다.  

> [!div class="mx-imgBorder"]
> ![Iframe 구성 요소](../media/iframe-control.png "iframe 구성 요소")

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) 

## <a name="manifest"></a>Manifest.xml

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSIFrameControl" version="1.0.0" display-name-key="TS_IFrameControl_Display_Key" description-key="TS_IFrameControl_Desc_Key" control-type="standard">
        <property name="stringProperty" display-name-key="stringProperty_Display_Key" description-key="stringProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />
        <property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_IFrameControl.css" order="2" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSIFrameControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to Bing Map IFrame HTMLElement
  private _bingMapIFrame: HTMLElement;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // Flag if control view has been rendered
  private _controlViewRendered: Boolean;
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
    this._container = container;
    this._controlViewRendered = false;
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    if (!this._controlViewRendered) {
      this._controlViewRendered = true;
      this.renderBingMapIFrame();
    }
    let latitude: number = context.parameters.latitudeValue.raw;
    let longitude: number = context.parameters.longitudeValue.raw;
    this.updateBingMapURL(latitude, longitude);
  }
  /**
   * Render IFrame HTML Element that hosts the Bing Map and appends the IFrame to the control container
   */
  private renderBingMapIFrame(): void {
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
  }
  /**
   * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
   * @param latitude : latitude of center point of Bing map
   * @param longitude : longitude of center point of Bing map
   */
  private updateBingMapURL(latitude: number, longitude: number): void {
    // Bing Map API:
    // https://msdn.microsoft.com/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc: string =
      bingMapUrlPrefix + latitude + "~" + longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
  }
  /**
   * Helper method to create an IFrame HTML Element
   */
  private createIFrameElement(): HTMLElement {
    let iFrameElement: HTMLElement = document.createElement("iframe");
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement;
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
  public destroy() {
    // no-op: method not leveraged by this example custom control
  }
}
```

## <a name="resources"></a>리소스

```css
.SampleNamespace\.TSIFrameControl .TS_SampleControl_IFrame
{
    width: 300px;
    height: 400px;
}
```

> [!NOTE]
> PowerApps 구성 요소 프레임 워크는 아직 복합 필드를 지원 하지 않으므로이 구성 요소를 기본 위도 및 경도 주소 필드에 바인딩할 수 없습니다. 다른 부동 소수점 필드에 코드 구성 요소를 바인딩해야 합니다.

이 샘플 구성 요소는 `Bing Maps URL`를 표시 하는 `IFRAME`를 렌더링 합니다. 구성 요소는 구성 요소에 매개 변수로 전달 되 고 Bing 지도를 제공 된 입력의 위도 및 경도로 업데이트 하기 위해 `IFRAME URL`에 삽입 되는 폼의 부동 소수점 필드 두 개에 바인딩됩니다.  

양식에 두 개의 추가 필드에 대 한 바인딩을 포함 하도록 `Manifest` 파일을 업데이트 합니다.  
이러한 변경으로 인해 PowerApps 구성 요소 프레임 워크에는 초기화 하는 동안 및 값 중 하나가 업데이트 될 때마다 이러한 바인딩된 필드가 구성 요소에 전달 되어야 한다는 것을 알 수 있습니다.
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

추가 바인딩된 속성이 필요할 수도 있습니다. 구성 요소가 폼에 바인딩될 때 구성 요소 구성 중에 적용 됩니다. 구성 요소 매니페스트에서 속성 노드의 `required` 특성을 설정 하 여 구성할 수 있습니다. 구성 요소 속성을 필드에 바인딩하지 않으려면 값을 false로 설정 합니다. 
 
`IInputs` 인터페이스에 두 필드를 추가 하려면 `ControlFramework.d.ts`를 업데이트 해야 합니다. PowerApps 구성 요소 프레임 워크에서 필드 값을 전달 하는 형식입니다. 이러한 값을 `IInputs` 인터페이스에 추가 하면 TypeScript 파일에서 값을 참조 하 고 성공적으로 컴파일할 수 있습니다.  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

초기 렌더링은 `IFRAME` 요소를 생성 하 여 컨트롤 컨테이너에 추가 합니다. 이 `IFRAME`는 **Bing 지도**를 표시 하는 데 사용 됩니다. @No__t_0의 url은 `Bing Map URL`으로 설정 되 고 url에 바인딩된 필드 (latitudeValue 및 longitudeValue)를 포함 하 여 제공 된 위치에 지도의 가운데 맞춤 합니다. 

[Updateview](../reference/control/updateview.md) 메서드는 이러한 필드 중 하나가 폼에서 업데이트 될 때마다 호출 됩니다. 이 메서드는 구성 요소에 전달 된 새 위도 및 경도 값을 사용 하도록 **Bing 지도** IFRAME의 url을 업데이트 합니다. 런타임에이 구성 요소를 보려면 다른 코드 구성 요소와 마찬가지로 폼의 필드에 구성 요소를 바인딩합니다.

### <a name="related-topics"></a>관련 항목

[샘플 구성 요소 다운로드](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
