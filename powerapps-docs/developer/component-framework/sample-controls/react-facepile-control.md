---
title: Facepile 구성 요소에 대응 | Microsoft Docs
description: 응답을 사용 하 여 Facepile 구성 요소 구현
ms.custom: ''
author: ghurlman
manager: kvivek
ms.date: 06/19/2019
ms.service: powerapps
ms.topic: article
ms.author: grhurl
ms.reviewer: nkrb
ms.openlocfilehash: 62a46acf98c8cdd93524f17b8a3a28ac999e325b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340118"
---
# <a name="implementing-the-facepile-component"></a>FacePile 구성 요소 구현

이 샘플에서는 PowerApps 구성 요소 프레임 워크를 사용 하 여 구성 요소를 만들기 위해 반응 하는 방법을 보여 줍니다.  Facepile 샘플 구성 요소는 응답을 기반으로 구현 되 고 Office UI 패브릭은 구성 요소에 반응 합니다. 이 코드는 언급 된 타사 라이브러리에 대 한 모범 사례를 노출 하지 않을 수 있습니다.

> [!div class="mx-imgBorder"]
> ![](../media/react-facepile.png "Facepile") Facepile 대응

## <a name="available-for"></a>사용 가능한 

모델 기반 앱 및 캔버스 앱 (실험적 미리 보기) 


> [!IMPORTANT]
> PowerApps 호스트 응용 프로그램은 반응 하는 순서에 따라 작동 하지만 번들로 인 한 응답 버전은 호스트 버전과 통신 하지 않으며 해당 버전에 종속 되지 않습니다. 반응 (또는 구성 요소와 함께 번들 하는 타사 라이브러리)의 새 복사본은 해당 컨트롤의 모든 인스턴스에 대 한 호스트 페이지에 로드 되므로 구성 요소를 추가할 때 페이지를 얼마나 큰지를 염두에 두는 것이 좋습니다. 이후 릴리스에서이 문제에 대 한 해결 방법을 제공 합니다.

## <a name="manifest"></a>Manifest.xml

```XML
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
  <control namespace="SampleControls" constructor="ReactStandardControl" version="0.0.1" display-name-key="ReactStandardControl_Display_Key" description-key="ReactStandardControl_Desc_Key" control-type="standard">
    <!-- property node identifies a specific, configurable piece of data that the control expects from CDS -->
    <property name="numberOfFaces" display-name-key="numberOfFaces" description-key="numberOfFaces" of-type="Whole.None" usage="bound" required="false" />
    <resources>
      <css path="css/ReactStandardControl.css" order="1" />
      <code path="index.ts" order="2"/>
    </resources>
  </control>
</manifest>
```

## <a name="overview"></a>개요

이 샘플에서는 타사 라이브러리 및 Office UI 패브릭을 위한 종속성을 추가 하는 방법에 대 한 예제를 제공 하 고 UI에 반응 하기 위해 Office UI Fabric 구성 요소를 활용 하 고 PowerApps 구성 요소 프레임 워크 간에 양방향 데이터 바인딩을 수행 하는 방법을 보여주는. 그리고 상태 모델에 반응 합니다.

구성 요소 샘플은 facepile, slider, 확인란 및 드롭다운 목록 이라는 세 가지 Office UI Fabric 구성 요소로 구성 되어 있습니다. 슬라이더를 움직이면 facepile의 얼굴 수가 변경 됩니다. 확인란은 얼굴을 페이드 인/페이드 아웃 하거나 단순히 표시 하거나 사라지게 할지, 드롭다운 목록의 옵션은 면의 크기를 제어 합니다. 값이 설정 되어 있지 않으면 얼굴 수는 기본값 3으로 설정 됩니다.

- 구성 요소가 로드 되 면 슬라이더는 바인딩된 특성 값으로 설정 됩니다. @No__t_0 속성에는 연결 된 메타 데이터가 포함 됩니다.
- 이벤트 처리기는 반응 구성 요소의 props에 전달 됩니다. 이렇게 하면 반응 구성 요소가 호스트 PowerApps 구성 요소 프레임 워크 컨트롤에 값이 변경 되었음을 알릴 수 있습니다. 그런 다음 이벤트 처리기는 **notifyOutputEvents** 메서드에 대 한 호출이 필요한 지 여부를 확인 합니다.
- 슬라이더를 이동 하면 응답 하 여 바인딩된 값을 업데이트 하 고 전달 된 이벤트 처리기를 호출 합니다. 해당 처리기 내에서 **notifyOutputEvents** 메서드를 호출 하면 컨트롤의 [getoutputs](../reference/control/getoutputs.md) 메서드가 비동기적으로 호출 되어 PowerApps 구성 요소 프레임 워크로 전달 됩니다. 
- 프레임 워크 호스트는 바인딩된 특성 값을 업데이트 하 고 업데이트 된 값은 구성 요소로 전달 되어 컨트롤의 [Updateview](../reference/control/updateview.md) 메서드를 트리거합니다. 그러면 컨트롤이 반응 구성 요소를 새 값으로 렌더링.


## <a name="code"></a>Code

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
import * as React from "react";
import * as ReactDOM from "react-dom";
import { FacepileBasicExample, IFacepileBasicExampleProps } from "./Facepile";

export class ReactStandardControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to the notifyOutputChanged method
  private notifyOutputChanged: () => void;
  // reference to the container div
  private theContainer: HTMLDivElement;
  // reference to the React props, prepopulated with a bound event handler
  private props: IFacepileBasicExampleProps = {
    numberFacesChanged: this.numberFacesChanged.bind(this)
  };

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
   * @param container If a control is marked control-type='starndard', it will receive an empty div element within which it can render its content.
   */
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this.notifyOutputChanged = notifyOutputChanged;
    this.props.numberOfFaces = context.parameters.numberOfFaces.raw || 3;
    this.theContainer = container;
  }

  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    if (context.updatedProperties.includes("numberOfFaces"))
      this.props.numberOfFaces = context.parameters.numberOfFaces.raw || 3;

    // Render the React component into the div container
    ReactDOM.render(
      // Create the React component
      React.createElement(
        FacepileBasicExample, // the class type of the React component found in Facepile.tsx
        this.props
      ),
      this.theContainer
    );
  }

  /**
   * Called by the React component when it detects a change in the number of faces shown
   * @param newValue The newly detected number of faces
   */
  private numberFacesChanged(newValue: number) {
    // only update if the number of faces has truly changed
    if (this.props.numberOfFaces !== newValue) {
      this.props.numberOfFaces = newValue;
      this.notifyOutputChanged();
    }
  }

  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {
      numberOfFaces: this.props.numberOfFaces
    };
  }

  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. cancelling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {
    ReactDOM.unmountComponentAtNode(this.theContainer);
  }
}

```

### <a name="facepiletsx"></a>Facepile

```TSX
import * as React from "react";
import { Checkbox } from "office-ui-fabric-react/lib/Checkbox";
import { Dropdown, IDropdownOption } from "office-ui-fabric-react/lib/Dropdown";
import { Facepile, IFacepilePersona, IFacepileProps, OverflowButtonType } from "office-ui-fabric-react/lib/Facepile";
import { PersonaSize } from "office-ui-fabric-react/lib/Persona";
import { Slider } from "office-ui-fabric-react/lib/Slider";
import { facepilePersonas } from "./FacepileExampleData";
import { setIconOptions } from "office-ui-fabric-react/lib/Styling";

// Suppress office UI fabric icon warnings.
setIconOptions({
  disableWarnings: true,
});

export interface IFacepileBasicExampleProps {
  numberOfFaces?: number;
  numberFacesChanged?: (newValue: number) => void;
}

export interface IFacepileBasicExampleState extends React.ComponentState, IFacepileBasicExampleProps {
  personaSize: PersonaSize;
  imagesFadeIn: boolean;
}

export class FacepileBasicExample extends React.Component<IFacepileBasicExampleProps, IFacepileBasicExampleState> {
  constructor(props: IFacepileBasicExampleProps) {
    super(props);

    this.state = {
      numberOfFaces: props.numberOfFaces || 3,
      imagesFadeIn: true,
      personaSize: PersonaSize.size32
    };
  }

  public componentWillReceiveProps(newProps: IFacepileBasicExampleProps): void {
    this.setState(newProps);
  }

  public render(): JSX.Element {
    const { numberOfFaces, personaSize } = this.state;
    const facepileProps: IFacepileProps = {
      personaSize,
      personas: facepilePersonas,
      overflowButtonType: OverflowButtonType.descriptive,
      maxDisplayablePersonas: this.state.numberOfFaces,
      getPersonaProps: (persona: IFacepilePersona) => {
        return {
          imageShouldFadeIn: this.state.imagesFadeIn,
        };
      },
      ariaDescription: "To move through the items use left and right arrow keys.",
    };

    return (
      <div className={"msFacepileExample"}>
        <Facepile {...facepileProps} />
        <div className={"control"}>
          <Slider
            label="Number of Personas:"
            min={1}
            max={5}
            step={1}
            showValue={true}
            value={numberOfFaces}
            onChange={this.onChangePersonaNumber}
          />
          <Dropdown
            label="Persona Size:"
            selectedKey={this.state.personaSize}
            options={[
              { key: PersonaSize.size16, text: "16px" },
              { key: PersonaSize.size24, text: "24px" },
              { key: PersonaSize.size28, text: "28px" },
              { key: PersonaSize.size32, text: "32px" },
              { key: PersonaSize.size40, text: "40px" },
            ]}
            onChange={this.onChangePersonaSize}
          />
          <Checkbox
            className={"exampleCheckbox"}
            label="Fade In"
            checked={this.state.imagesFadeIn}
            onChange={this.onChangeFadeIn}
          />
        </div>
      </div>
    );
  }

  private onChangeFadeIn = (
    ev: React.FormEvent<HTMLElement | HTMLInputElement> | undefined,
    checked?: boolean
  ): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.imagesFadeIn = checked!;
        return prevState;
      }
    );
  };

  private onChangePersonaNumber = (value: number): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.numberOfFaces = value;
        return prevState;
      }
    );
    if (this.props.numberFacesChanged) {
      this.props.numberFacesChanged(value);
    }
  };

  private onChangePersonaSize = (event: React.FormEvent<HTMLDivElement>, value?: IDropdownOption): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.personaSize = value ? (value.key as PersonaSize) : PersonaSize.size32;
        return prevState;
      }
    );
  };
}
```

### <a name="facepileexampledatats"></a>FacepileExampleData

```TypeScript
import * as React from 'react';
import { IFacepilePersona } from 'office-ui-fabric-react/lib/Facepile';
import { PersonaInitialsColor } from 'office-ui-fabric-react/lib/Persona';
import { TestImages } from './TestImages';

export const facepilePersonas: IFacepilePersona[] = [
  {
    imageUrl: TestImages.personaFemale,
    personaName: 'Annie Lindqvist',
    data: '50%'
  },
  {
    imageUrl: TestImages.personaMale,
    personaName: 'Aaron Reid',
    data: '$1,000'
  },
  {
    personaName: 'Alex Lundberg',
    data: '75%',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    personaName: 'Roko Kolar',
    data: '4 hrs'
  },
  {
    imageInitials: 'CB',
    personaName: 'Christian Bergqvist',
    initialsColor: PersonaInitialsColor.green,
    data: '25%'
  },
  {
    imageUrl: TestImages.personaFemale,
    imageInitials: 'VL',
    personaName: 'Valentina Lovric',
    initialsColor: PersonaInitialsColor.lightBlue,
    data: 'Emp1234',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'MS',
    personaName: 'Maor Sharett',
    initialsColor: PersonaInitialsColor.lightGreen
  },
  {
    imageUrl: TestImages.personaFemale,
    imageInitials: 'PV',
    personaName: 'Annie Lindqvist2',
    initialsColor: PersonaInitialsColor.lightPink
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'AR',
    personaName: 'Aaron Reid2',
    initialsColor: PersonaInitialsColor.magenta,
    data: 'Emp1234',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'AL',
    personaName: 'Alex Lundberg2',
    initialsColor: PersonaInitialsColor.orange
  }

  // Trimmed for display; full file in the downloadable sample code
```

### <a name="testimagests"></a>TestImages

```TypeScript
const baseProductionCdnUrl = 'https://static2.sharepointonline.com/files/fabric/office-ui-fabric-react-assets/';

export const TestImages = {
  choiceGroupBarUnselected: baseProductionCdnUrl + 'choicegroup-bar-unselected.png',
  choiceGroupBarSelected: baseProductionCdnUrl + 'choicegroup-bar-selected.png',
  choiceGroupPieUnselected: baseProductionCdnUrl + 'choicegroup-pie-unselected.png',
  choiceGroupPieSelected: baseProductionCdnUrl + 'choicegroup-pie-selected.png',
  documentPreview: baseProductionCdnUrl + 'document-preview.png',
  documentPreviewTwo: baseProductionCdnUrl + 'document-preview2.png',
  documentPreviewThree: baseProductionCdnUrl + 'document-preview3.png',
  iconOne: baseProductionCdnUrl + 'icon-one.png',
  iconPpt: baseProductionCdnUrl + 'icon-ppt.png',
  personaFemale: baseProductionCdnUrl + 'persona-female.png',
  personaMale: baseProductionCdnUrl + 'persona-male.png'
};
```

## <a name="resources"></a>리소스

### <a name="cssreactstandardcontrolcss"></a>css/ReactStandardControl

```css
.msFacepileExample {
  max-width: 300px;
}

.msFacepileExample .control {
  padding-top: 20px;
}

.msFacepileExample .ms-Dropdown-container,
.msFacepileExample .ms-Slider {
  margin: 10px 0 10px 0;
}

.msFacepileExample .ms-Dropdown-container .ms-Label {
  padding-top: 0;
}

.msFacepileExample .ms-Checkbox {
  padding-top: 15px;
}

.exampleCheckbox {
  margin: 10px 0;
}

.exampleLabel {
  margin: 10px 0;
}
```

### <a name="related-topics"></a>관련 항목

[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br />
[PowerApps 구성 요소 프레임 워크 개요](../overview.md)
