---
title: " 구성 요소 대칭 이동 | Microsoft Docs"
description: 각도 JS를 사용 하 여 Flip 구성 요소 구현
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 90d74124e21fe74a96ca31830508f3bbb99e17b9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340670"
---
# <a name="implementing-flip-component"></a>플립 구성 요소 구현

이 샘플에서는 PowerApps 구성 요소 프레임 워크에서 타사 라이브러리를 사용 하 여 구성 요소를 만드는 방법을 보여 줍니다.  플립 샘플 구성 요소는 각도의 .js, 각도 ui, 각도 애니메이션, 각도 삭제, 부트스트랩을 기반으로 구현 됩니다. 이 코드는 언급 된 타사 라이브러리에 대 한 모범 사례를 노출 하지 않을 수 있습니다.

> [!div class="mx-imgBorder"]
> ![각도 대칭]이동(../media/angular-flip.png "각도 대칭")

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) 

## <a name="manifest"></a>Manifest.xml

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="JSAngularJSFlipControl" version="1.0.0" display-name-key="JS_AngularJSFlipControl_Display_Key" description-key="JS_AngularJSFlipControl_Desc_Key" control-type="standard">
        <property name="flipModel" display-name-key="flipModel_Display_Key" description-key="flipModel_Desc_Key" of-type="TwoOptions" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="5" />
            <css path="css/bootstrap-associated.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="overview"></a>개요

이 샘플에서는 타사 라이브러리에 대 한 종속성을 추가 하는 방법에 대 한 예제를 제공 합니다. 보여주는는 PowerApps 구성 요소 프레임 워크, 구성 요소 모델 및 타사 내부 데이터 모델 간의 데이터 바인딩을 양방향으로 수행 하는 방법을 제공 합니다.

Flip 구성 요소 예제는 레이블과 단추로 구성 됩니다. 단추를 클릭 하면 레이블의 텍스트가 설정/해제 됩니다.

- 구성 요소가 로드 되 면 레이블은 bind 특성 값을 기반으로 텍스트를 표시 합니다. 연결 된 메타 데이터를 포함 하 `context.parameters.[property_name].attributes`입니다.
- TwoOptions 필드의 `context.parameters.[property_name].Options`에는 true 및 false 값 옵션이 모두 포함 됩니다. 
- 대칭 이동 단추를 클릭 하면 레이블이 **notifyOutputEvents** 메서드를 사용 하 여 값을 업데이트 하 고, [getoutputs](../reference/control/getoutputs.md) 메서드는 비동기적으로 호출 되며 PowerApps 구성 요소 프레임 워크로 전달 됩니다. 
- ClientAPI는 bind 특성 값을 업데이트 하 고 업데이트 된 값은 구성 요소 레이블로 흐릅니다. 또한 `ClientAPI`를 사용 하 여 컨트롤의 [Updateview](../reference/control/updateview.md) 메서드를 트리거하는 특성 값을 업데이트할 수 있습니다. 그런 다음 구성 요소는 타사 모델을 업데이트 하 고 레이블이 업데이트 됩니다.


## <a name="code"></a>Code

```TypeScript

import { IInputs, IOutputs } from "./generated/ManifestTypes";
import * as angular from "angular";
export class JSAngularJSFlipControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Element id of the ng-app div. Type: string
  private _appDivId: string;
  // ng-app app id. Type: string
  private _appId: string;
  // ng-controller. Type: string
  private _controllerId: string;
  // PCF framework delegate which will be assigned to this object which would be called whenever an update happens. Type: function
  private _notifyOutputChanged: () => void;
  // Model of the bind field. Type: Boolean
  private _currentValue: boolean;
  // Option Label Text when Option is True. The Text is from attribute customization. Type: string
  private _optionTrueLabel: string;
  // Option Label Text when Option is False. The Text is from attribute customization. Type: string
  private _optionFalseLabel: string;
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
    // We need a random integer from 1-100, so that for a form of multiple fields bind to same attribute, we could differentiate
    let randomInt: number = Math.floor(Math.floor(100) * Math.random());
    let _this = this;
    this._appDivId = this.createUniqueId(
      context,
      "angularflip_controlid",
      randomInt
    );
    this._appId = this.createUniqueId(
      context,
      "JSAngularJSFlipControl",
      randomInt
    );
    this._controllerId = this.createUniqueId(
      context,
      "powerApps.angularui.demo",
      randomInt
    );
    this._notifyOutputChanged = notifyOutputChanged;
    // Assign Model the value of the bind attribute
    this._currentValue = context.parameters.flipModel.raw;
    // Initialize the True/False Label texts from the attribute metadata
    this.initializeOptionsLabel(context);
    // Create HTML structure for the control
    let appDiv: HTMLDivElement = document.createElement("div");
    appDiv.setAttribute("id", this._appDivId);
    appDiv.setAttribute("ng-controller", this._appId);
    appDiv.setAttribute("ng-app", this._controllerId);
    // Below sample html are from Angular-UI single toggle sample code
    // https://angular-ui.github.io/bootstrap/
    appDiv.innerHTML =
      "<pre>{{labelModel}}</pre><button type='button' class='btn btn-primary' ng-model='flipButtonModel' uib-btn-checkbox btn-checkbox-true='1' btn-checkbox-false='0'>Flip</button>";
    // Container appends the HTML structure
    container.appendChild(appDiv);
    // Angular code. Angular module/controller initialization.
    angular.module(this._controllerId, [
      "ngAnimate",
      "ngSanitize",
      "ui.bootstrap"
    ]);
    angular.module(this._controllerId).controller(this._appId, $scope => {
      // Intialize 'labelModel'. Assign initial option text to the Angular $scope labelModel. It will be revealed in '<pre>{{labelModel}}</pre>'
      $scope.labelModel = _this._currentValue
        ? _this._optionTrueLabel
        : _this._optionFalseLabel;
      // Intialize 'flipButtonModel'. Assign bind attribute value to Angular $scope flipButtonModel. The Flip button also bind to this 'flipButtonModel', so when we click, it will flip
      $scope.flipButtonModel = _this._currentValue ? 1 : 0;
      // Watch the click of the flip button
      $scope.$watchCollection("flipButtonModel", () => {
        // Update the label text when Flip Button clicks
        if ($scope.flipButtonModel) {
          $scope.labelModel = _this._optionTrueLabel;
        } else {
          $scope.labelModel = _this._optionFalseLabel;
        }
        // Call updateOutputIfNeeded and inform PCF framework that bind attribute value need update
        _this.updateOutputIfNeeded($scope.flipButtonModel);
      });
    });
    // Angular code. Create an App based on the new appDivId
    angular.element(document).ready(() => {
      angular.bootstrap(document.getElementById(_this._appDivId)!, [
        _this._controllerId
      ]);
    });
  }
  /**
   * Get UniqueId so as to avoid id conflict between multiple fields bind to same attribute
   * @param context The "Input Properties" containing the parameters, control metadata and interface functions.
   * @param passInString input string as suffix
   * @param randomInt random integer
   * @returns a string of uniqueId includes attribute logicalname + passIn specialized string + random Integer
   */
  private createUniqueId(
    context: ComponentFramework.Context<IInputs>,
    passInString: string,
    randomInt: number
  ): string {
    return (
      context.parameters!.flipModel.attributes!.LogicalName +
      "-" +
      passInString +
      randomInt
    );
  }
  /**
   * Initialize Options Label to use the attribute label from Metadata
   * @param context The "Input Properties" containing the parameters, control metadata and interface functions.
   */
  private initializeOptionsLabel(
    context: ComponentFramework.Context<IInputs>
  ): void {
    var _this = this;
    // Get option label texts from metadata
    var optionsMetadata = context.parameters.flipModel.attributes!.Options;
    optionsMetadata.forEach((option: any) => {
      if (option.Value) {
        _this._optionTrueLabel = option.Label;
      } else {
        _this._optionFalseLabel = option.Label;
      }
    });
  }
  /**
   * Update Angular 'flipButtonModel' if needed
   * @param newValue new value
   */
  private updateFlipButtonModelIfNeeded(newValue: boolean): void {
    if (
      (newValue && !this._currentValue) ||
      (!newValue && this._currentValue)
    ) {
      this._currentValue = newValue;
      // Angular Code. Update the 'flipButtonModel' value
      var $scope = angular
        .element(document.getElementById(this._appDivId)!)
        .scope();
      $scope.$apply(($scope: any) => {
        // 'flipButtonModel' value is either 1 or 0
        $scope.flipButtonModel = newValue ? 1 : 0;
      });
    }
  }
  /**
   * Update value in PowerApps component framework
   * @param newValue new value
   */
  private updateOutputIfNeeded(newValue: boolean): void {
    if (
      (newValue && !this._currentValue) ||
      (!newValue && this._currentValue)
    ) {
      this._currentValue = newValue ? true : false;
      this._notifyOutputChanged();
    }
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // An attribute value from Control Framework could be updated even after init cycle, clientAPI, post Save response can update the attribute value and the Flip control should reveal the new value.
    this.updateFlipButtonModelIfNeeded(context.parameters.flipModel.raw);
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    var returnValue = this._currentValue;
    return { flipModel: returnValue };
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {
    // Add code to cleanup control if necessary
  }
}
```

### <a name="resources"></a>리소스

```css
.SampleNamespace\.JSAngularJSFlipControl pre {
  display: block;
  padding: 9.5px;
  margin: 0 0 10px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #333;
  word-break: break-all;
  word-wrap: break-word;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.SampleNamespace\.JSAngularJSFlipControl pre {
  font-family: Menlo, Monaco, Consolas, "Courier New", monospace;
}
.SampleNamespace\.JSAngularJSFlipControl pre {
  overflow: auto;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active:hover,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active:hover,
.open > .dropdown-toggle.btn-primary.focus,
.open > .dropdown-toggle.btn-primary:focus,
.open > .dropdown-toggle.btn-primary:hover {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled:hover,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled].focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled]:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled]:hover,
fieldset[disabled].btn-primary.focus,
fieldset[disabled].btn-primary:focus,
fieldset[disabled].btn-primary:hover {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.badge {
  color: #337ab7;
  background-color: #fff;
}
.SampleNamespace\.JSAngularJSFlipControl .btn {
  display: inline-block;
  padding: 6px 12px;
  margin-bottom: 0;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.42857143;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 4px;
}

```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
