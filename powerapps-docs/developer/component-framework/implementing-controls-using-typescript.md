---
title: TypeScript를 사용 하 여 코드 구성 요소 구현 | MicrosoftDocs
description: TypeScript를 사용 하 여 코드 구성 요소를 구현 하는 방법
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: cd57cce824c4071de12e7dc96407018dde57c2d7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346834"
---
# <a name="implement-components-using-typescript"></a>TypeScript를 사용 하 여 구성 요소 구현

이 자습서에서는 TypeScript에서 새 코드 구성 요소를 만드는 과정을 안내 합니다. 샘플 구성 요소는 사용자가 필드에 값을 입력 하는 대신 시각적 슬라이더를 사용 하 여 숫자 값을 입력할 수 있도록 하는 선형 입력 구성 요소입니다. 

## <a name="creating-a-new-component-project"></a>새 구성 요소 프로젝트 만들기

새 프로젝트를 만들려면 다음을 수행 합니다.

1. **VS 2017 창의 개발자 명령 프롬프트** 을 엽니다.
1. 다음 명령을 사용 하 여 프로젝트에 대 한 새 폴더를 만듭니다. 
    ```CLI
    mkdir LinearComponent
    ```

1. @No__t_0 명령을 사용 하 여 새 디렉터리로 이동 합니다. 
   
1. 다음 명령을 실행 하 여 기본 매개 변수를 전달 하는 새 구성 요소 프로젝트를 만듭니다.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. @No__t_0 명령을 사용 하 여 프로젝트 빌드 도구를 설치 합니다. 
2. 선택한 개발자 환경에서 `C:\Users\<your name>\Documents\<My_PCF_Component>` 프로젝트 폴더를 열고 코드 구성 요소 개발을 시작 합니다. 를 시작 하는 가장 빠른 방법은 `C:\Users\<your name>\Documents\<My_PCF_Component>` 디렉터리에 있는 명령 프롬프트에서 `code .`를 실행 하는 것입니다. 이 명령은 Visual Studio Code 구성 요소 프로젝트를 엽니다.

## <a name="implementing-manifest"></a>매니페스트 구현

매니페스트는 코드 구성 요소의 메타 데이터를 포함 하는 XML 파일입니다. 또한 코드 구성 요소의 동작도 정의 합니다. 이 자습서에서이 매니페스트 파일은 `<Your component Name>` 하위 폴더 아래에 생성 됩니다. Visual Studio Code에서 `ControlManifest.Input.xml` 파일을 열면 매니페스트 파일이 일부 속성으로 미리 정의 된 것을 알 수 있습니다. 다음과 같이 미리 정의 된 매니페스트 파일을 변경 합니다.

1. [Control](manifest-schema-reference/control.md) 노드는 코드 구성 요소의 네임 스페이스, 버전 및 표시 이름을 정의 합니다. 이제 다음과 같이 [control](manifest-schema-reference/control.md) 노드의 각 속성을 정의 합니다.

   - **네임 스페이스**: 코드 구성 요소의 네임 스페이스입니다. 
   - **생성자**: 코드 구성 요소의 생성자입니다.
   - **버전**: 구성 요소의 버전입니다. 구성 요소를 업데이트할 때마다 런타임의 변경 내용을 확인 하기 위해 버전을 업데이트 해야 합니다.
   - **표시 이름-키**: UI에 표시 되는 코드 구성 요소의 이름입니다.
   - **description-name-key**: UI에 표시 되는 코드 구성 요소에 대 한 설명입니다.
   - **컨트롤 형식**: 코드 구성 요소 형식입니다. *표준* 형식의 코드 구성 요소만 지원 됩니다.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. [속성](manifest-schema-reference/property.md) 노드는 필드의 데이터 형식을 정의 하는 것과 같은 코드 구성 요소의 속성을 정의 합니다. 속성 노드는 control 요소 아래에 자식 요소로 지정 됩니다. 다음과 같이 [속성](manifest-schema-reference/property.md) 노드를 정의 합니다.

   - **이름**: 속성의 이름입니다.
   - **표시 이름-키**: UI에 표시 되는 속성의 표시 이름입니다.
   - **description-name-key**: UI에 표시 되는 속성에 대 한 설명입니다. 
   - **-형식-그룹**: 데이터 형식 필드를 두 개 이상 포함 하려는 경우 [-형식-그룹의](manifest-schema-reference/type-group.md) 를 사용 합니다. [형식 그룹](manifest-schema-reference/type-group.md) 요소를 매니페스트의 `property` 요소에 형제로 추가 합니다. @No__t_0는 구성 요소 값을 지정 하며 전체, 통화, 부동 소수점 또는 10 진수 값을 포함할 수 있습니다.
   - **사용법**:에는 *바인딩된* 및 *입력*의 두 속성이 있습니다. 바인딩된 속성은 필드의 값에만 바인딩됩니다. 입력 속성은 필드에 바인딩되어 있거나 정적 값을 허용 합니다.
   - **필수**: 속성이 필수 인지 여부를 정의 합니다.

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. [Resources](manifest-schema-reference/resources.md) 노드는 코드 구성 요소의 시각화를 정의 합니다. 여기에는 코드 구성 요소를 구성 하는 모든 리소스가 포함 됩니다. [코드](manifest-schema-reference/code.md) 는 resources 요소 아래에 자식 요소로 지정 됩니다. 다음과 같이 [리소스](manifest-schema-reference/resources.md) 를 정의 합니다.

   - **code**: 모든 리소스 파일이 있는 경로를 참조 합니다.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      전체 매니페스트 파일은 다음과 같습니다. 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. @No__t_0 파일의 변경 내용을 저장 합니다.
5. 이제 `TSLinearInputComponent` 폴더 안에 새 폴더를 만들고 이름을 **css**로 이름을로 합니다.
6. CSS 파일을 만들어 [코드 구성 요소에 스타일을 추가](#adding-style-to-the-code-component)합니다.
7. 명령 `npm run build`를 사용 하 여 구성 요소 프로젝트를 빌드합니다.
8. 빌드는 `TSLinearInputComponent/generated` 폴더 아래에 업데이트 된 TypeScript 형식 선언 파일을 생성 합니다.

## <a name="implementing-component-logic"></a>구성 요소 논리 구현

매니페스트 파일을 구현한 후 다음 단계는 TypeScript를 사용 하 여 구성 요소 논리를 구현 하는 것입니다. 구성 요소 논리는 `index.ts` 파일 내에 구현 해야 합니다. Visual Studio Code에서 `index.ts` 파일을 열면 네 가지 필수 클래스가 미리 정의 되어 있는 것을 알 수 있습니다. 이제 코드 구성 요소에 대 한 논리를 구현 해 보겠습니다. 

1. 선택한 코드 편집기에서 `index.ts` 파일을 엽니다.
2. @No__t_0 클래스를 다음 코드로 업데이트 합니다.

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // PowerApps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to PowerApps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTML elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0"
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : ""
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}

```

3. 명령 `npm run build`를 사용 하 여 프로젝트를 다시 빌드합니다. 
 
4. 구성 요소가 `out/controls/TSLinearInputComponent` 폴더로 컴파일됩니다. 빌드 아티팩트는 다음과 같습니다.

   - 번들 .js – 번들 구성 요소 소스 코드입니다. 
   - ControlManifest – Common Data Service 조직에 업로드 되는 실제 구성 요소 매니페스트 파일입니다.

## <a name="adding-style-to-the-code-component"></a>코드 구성 요소에 스타일 추가

개발자와 앱 작성자는 CSS를 사용 하 여 코드 구성 요소를 시각적으로 나타내는 스타일을 정의할 수 있습니다. CSS를 사용 하면 개발자가 스타일, 색, 레이아웃 및 글꼴을 비롯 한 코드 구성 요소의 표시를 설명할 수 있습니다. 선형 입력 구성 요소의 [init](reference/control/init.md) 메서드는 input 요소를 만들고 클래스 특성을 `linearslider` 설정 합니다. @No__t_0 클래스에 대 한 스타일은 별도의 `CSS` 파일에 정의 되어 있습니다. 추가 사용자 지정을 지원 하기 위해 `CSS` 파일 등의 추가 구성 요소 리소스를 코드 구성 요소에 포함할 수 있습니다.

1. @No__t_1 폴더 아래에 새 `css` 하위 폴더를 만듭니다. 
2. @No__t_1 하위 폴더 내에 새 `TS_LinearInputComponent.css` 파일을 만듭니다. 
3. @No__t_0 파일에 다음 스타일 콘텐츠를 추가 합니다.

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. @No__t_0 파일을 저장 합니다.
6. @No__t_0 파일을 편집 하 여 resources 요소 내에 `CSS` 리소스 파일을 포함 합니다.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. 다음 명령을 사용 하 여 프로젝트를 다시 빌드합니다. 
   ```CLI
   npm run build
   ```
8. **/Out/controls/TSLinearInputComponent** 아래의 빌드 출력을 검사 하 여 **TS_LinearInputComponent** 파일이 컴파일된 빌드 아티팩트에 포함 되어 있는지 확인 합니다. 

## <a name="debugging-your-code-component"></a>코드 구성 요소 디버깅

코드 구성 요소 논리를 구현 했으면 다음 명령을 실행 하 여 디버깅 프로세스를 시작 합니다. 추가 정보: [디버그 코드 구성 요소](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>코드 구성 요소 패키징

[솔루션](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) 파일을 만들고 가져오려면 다음 단계를 수행 합니다.

1. **LinearComponent** 폴더 내에 새 폴더 **솔루션** 을 만들고 폴더로 이동 합니다. 
2. 다음 명령을 사용 하 여 **LinearComponent** 폴더에 새 솔루션 프로젝트를 만듭니다.
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > [게시자 이름](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) 및 [게시자 접두사](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) 값은 사용자 환경에서 고유 해야 합니다.
 
3. 새 솔루션 프로젝트를 만든 후에는 만들어진 구성 요소가 있는 위치를 참조 해야 합니다. 다음 명령을 사용 하 여 참조를 추가할 수 있습니다.

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. 솔루션 프로젝트에서 zip 파일을 생성 하려면 솔루션 프로젝트 디렉터리에 `cd` 다음 명령을 사용 하 여 프로젝트를 빌드해야 합니다. 

    ```CLI
     msbuild /t:restore
    ```

5. 다음 명령을 실행 하 여 msbuild를 실행 합니다.
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > **빌드 작업 & NuGet 대상** 이 선택 되어 있는지 확인 합니다. 사용 하도록 설정 하려면
    > - **Visual Studio 설치 관리자**를 엽니다.
    > - Visual Studio 2017의 경우 **수정**을 선택 합니다.
    > - **개별 구성 요소**를 선택 합니다.
    > - **코드 도구**에서 **NuGet 대상 & 빌드 작업**을 선택 합니다.

6. 생성 된 솔루션 zip 파일은 `Solution\bin\debug` 폴더에 있습니다.
7. Zip 파일이 준비 되 면 웹 포털을 사용 하 여 [솔루션을 Common Data Service으로](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) 수동으로 가져오거나 PowerApps CLI 명령을 사용 하 여 가져올 조직 및 [배포](import-custom-controls.md#deploying-code-components) 섹션 [에 대 한 인증](import-custom-controls.md#authenticating-to-your-organization) 섹션을 참조 하세요.

## <a name="adding-code-components-in-model-driven-apps"></a>모델 기반 앱에서 코드 구성 요소 추가

선형 입력 구성 요소와 같은 코드 구성 요소를 추가 하려면 [필드와 엔터티에 구성 요소 추가](add-custom-controls-to-a-field-or-entity.md)항목에 설명 된 단계를 따르세요.

## <a name="adding-code-components-to-a-canvas-app"></a>Canvas 앱에 코드 구성 요소 추가

Canvas 앱에 코드 구성 요소를 추가 하려면 [캔버스 앱에 코드 구성 요소 추가](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)항목의 단계를 따르세요.

### <a name="see-also"></a>참고 항목

[샘플 구성 요소 다운로드](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[기존 PowerApps 구성 요소 프레임 워크 구성 요소 업데이트](updating-existing-controls.md)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 개요](overview.md)
