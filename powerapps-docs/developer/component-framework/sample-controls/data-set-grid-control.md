---
title: 데이터 집합 표 구성 요소 | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 356561d0-a36b-4b93-8b76-3e1abf9414e9
ms.openlocfilehash: ca13ef7758bb21853f9c1411c641bd1ae88115b6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340509"
---
# <a name="implementing-data-set-component"></a>데이터 집합 구성 요소 구현

이 샘플 구성 요소는 데이터 집합과 상호 작용 하는 사용자 환경을 변경 하는 방법을 보여 줍니다. 예를 들어 엔터티 홈페이지의 홈 페이지 그리드는 테이블로만 표시 됩니다. 선택한 대로 데이터를 표시할 수 있는 코드 구성 요소를 빌드할 수 있습니다. 이 샘플에서는 일반 표 형태 표 대신 타일로 레코드를 보여 줍니다.

> [!div class="mx-imgBorder"]
> ![데이터 집합 표 구성 요소](../media/data-set-grid.png "데이터 집합 표 구성 요소")

## <a name="available-for"></a>사용 가능한 

모델 기반 앱

## <a name="manifest"></a>Manifest.xml 

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSDataSetGrid" version="1.0.0" display-name-key="TS_DataSetGrid_Display_Key" description-key="TSIncrementControl_Desc_Key" control-type="standard">
        <data-set name="dataSetGrid" display-name-key="DataSetGridProperty_Display_Key">
        </data-set>
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_DataSetGrid.css" order="1" />
            <resx path="strings/TSDataSetGrid.1033.resx" version="1.0.0" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Code 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
import DataSetInterfaces = ComponentFramework.PropertyHelper.DataSetApi;
type DataSet = ComponentFramework.PropertyTypes.DataSet;
// Define const here
const RowRecordId: string = "rowRecId";
// Style name of Load More Button
const DataSetControl_LoadMoreButton_Hidden_Style =
  "DataSetControl_LoadMoreButton_Hidden_Style";
export class TSDataSetGrid
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Cached context object for the latest updateView
  private contextObj: ComponentFramework.Context<IInputs>;
  // Div element created as part of this control's main container
  private mainContainer: HTMLDivElement;
  // Table element created as part of this control's table
  private gridContainer: HTMLDivElement;
  // Button element created as part of this control
  private loadPageButton: HTMLButtonElement;
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
    // Need to track container resize so that control could get the available width. The available height won't be provided even this is true
    context.mode.trackContainerResize(true);
    // Create main table container div.
    this.mainContainer = document.createElement("div");
    // Create data table container div.
    this.gridContainer = document.createElement("div");
    this.gridContainer.classList.add("DataSetControl_grid-container");
    // Create data table container div.
    this.loadPageButton = document.createElement("button");
    this.loadPageButton.setAttribute("type", "button");
    this.loadPageButton.innerText = context.resources.getString(
      "PCF_DataSetControl_LoadMore_ButtonLabel"
    );
    this.loadPageButton.classList.add(
      DataSetControl_LoadMoreButton_Hidden_Style
    );
    this.loadPageButton.classList.add("DataSetControl_LoadMoreButton_Style");
    this.loadPageButton.addEventListener(
      "click",
      this.onLoadMoreButtonClick.bind(this)
    );
    // Adding the main table and loadNextPage button created to the container DIV.
    this.mainContainer.appendChild(this.gridContainer);
    this.mainContainer.appendChild(this.loadPageButton);
    this.mainContainer.classList.add("DataSetControl_main-container");
    container.appendChild(this.mainContainer);
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    this.contextObj = context;
    this.toggleLoadMoreButtonWhenNeeded(context.parameters.dataSetGrid);
    if (!context.parameters.dataSetGrid.loading) {
      // Get sorted columns on View
      let columnsOnView = this.getSortedColumnsOnView(context);
      if (!columnsOnView || columnsOnView.length === 0) {
        return;
      }
      while (this.gridContainer.firstChild) {
        this.gridContainer.removeChild(this.gridContainer.firstChild);
      }
      this.gridContainer.appendChild(
        this.createGridBody(columnsOnView, context.parameters.dataSetGrid)
      );
    }
    // this is needed to ensure the scroll bar appears automatically when the grid resize happens and all the tiles are not visible on the screen.
    this.mainContainer.style.maxHeight =
      window.innerHeight - this.gridContainer.offsetTop - 75 + "px";
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. cancelling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {}
  /**
   * Get sorted columns on view
   * @param context
   * @return sorted columns object on View
   */
  private getSortedColumnsOnView(
    context: ComponentFramework.Context<IInputs>
  ): DataSetInterfaces.Column[] {
    if (!context.parameters.dataSetGrid.columns) {
      return [];
    }
    let columns = context.parameters.dataSetGrid.columns.filter(function(
      columnItem: DataSetInterfaces.Column
    ) {
      // some column are supplementary and their order is not > 0
      return columnItem.order >= 0;
    });
    // Sort those columns so that they will be rendered in order
    columns.sort(function(
      a: DataSetInterfaces.Column,
      b: DataSetInterfaces.Column
    ) {
      return a.order - b.order;
    });
    return columns;
  }
  /**
   * funtion that creates the body of the grid and embeds the content onto the tiles.
   * @param columnsOnView columns on the view whose value needs to be shown on the UI
   * @param gridParam data of the Grid
   */
  private createGridBody(
    columnsOnView: DataSetInterfaces.Column[],
    gridParam: DataSet
  ): HTMLDivElement {
    let gridBody: HTMLDivElement = document.createElement("div");
    if (gridParam.sortedRecordIds.length > 0) {
      for (let currentRecordId of gridParam.sortedRecordIds) {
        let gridRecord: HTMLDivElement = document.createElement("div");
        gridRecord.classList.add("DataSetControl_grid-item");
        gridRecord.addEventListener("click", this.onRowClick.bind(this));
        // Set the recordId on the row dom
        gridRecord.setAttribute(
          RowRecordId,
          gridParam.records[currentRecordId].getRecordId()
        );
        columnsOnView.forEach(function(columnItem, index) {
          let labelPara = document.createElement("p");
          labelPara.classList.add("DataSetControl_grid-text-label");
          let valuePara = document.createElement("p");
          valuePara.classList.add("DataSetControl_grid-text-value");
          labelPara.textContent = columnItem.displayName + " : ";
          gridRecord.appendChild(labelPara);
          if (
            gridParam.records[currentRecordId].getFormattedValue(
              columnItem.name
            ) != null &&
            gridParam.records[currentRecordId].getFormattedValue(
              columnItem.name
            ) != ""
          ) {
            valuePara.textContent = gridParam.records[
              currentRecordId
            ].getFormattedValue(columnItem.name);
            gridRecord.appendChild(valuePara);
          } else {
            valuePara.textContent = "-";
            gridRecord.appendChild(valuePara);
          }
        });
        gridBody.appendChild(gridRecord);
      }
    } else {
      let noRecordLabel: HTMLDivElement = document.createElement("div");
      noRecordLabel.classList.add("DataSetControl_grid-norecords");
      noRecordLabel.style.width =
        this.contextObj.mode.allocatedWidth - 25 + "px";
      noRecordLabel.innerHTML = this.contextObj.resources.getString(
        "PCF_DataSetControl_No_Record_Found"
      );
      gridBody.appendChild(noRecordLabel);
    }
    return gridBody;
  }
  /**
   * Row Click Event handler for the associated row when being clicked
   * @param event
   */
  private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.dataSetGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.name,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
  /**
   * Toggle 'LoadMore' button when needed
   */
  private toggleLoadMoreButtonWhenNeeded(gridParam: DataSet): void {
    if (
      gridParam.paging.hasNextPage &&
      this.loadPageButton.classList.contains(
        DataSetControl_LoadMoreButton_Hidden_Style
      )
    ) {
      this.loadPageButton.classList.remove(
        DataSetControl_LoadMoreButton_Hidden_Style
      );
    } else if (
      !gridParam.paging.hasNextPage &&
      !this.loadPageButton.classList.contains(
        DataSetControl_LoadMoreButton_Hidden_Style
      )
    ) {
      this.loadPageButton.classList.add(
        DataSetControl_LoadMoreButton_Hidden_Style
      );
    }
  }
  /**
   * 'LoadMore' Button Event handler when load more button clicks
   * @param event
   */
  private onLoadMoreButtonClick(event: Event): void {
    this.contextObj.parameters.dataSetGrid.paging.loadNextPage();
    this.toggleLoadMoreButtonWhenNeeded(this.contextObj.parameters.dataSetGrid);
  }
}
```

## <a name="resources"></a>리소스

```css
.SampleNamespace\.TSDataSetGrid .DataSetControl_main-container {
  overflow-y: auto;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-container {
  background-color: transparent;
  border: solid thin lightgray;
  padding: 10px;
  display: inline-block;
  overflow: auto;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-item {
  margin: 5px;
  width: 200px;
  height: 200px;
  background-color: rgb(59, 121, 183);
  color: white;
  border: solid thin black;
  padding: 5px;
  text-align: center;
  float: left;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-text-label {
  font-size: 12px;
  white-space: normal;
  margin: 2px;
  display: block;
  color: lightgray;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-text-value {
  font-size: 12px;
  white-space: normal;
  margin: 1px;
  display: block;
  color: white;
  font-weight: bold;
}

.SampleNamespace\.TSDataSetGrid button.DataSetControl_LoadMoreButton_Style {
  background-color: #e5e5e5;
  font-size: 1.5rem;
  font-weight: bold;
  height: 3.5rem;
  text-align: center;
  width: 100%;
  border: none;
}

.SampleNamespace\.TSDataSetGrid
  button.DataSetControl_LoadMoreButton_Hidden_Style {
  display: none;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-norecords {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

```XML
<?xml version="1.0" encoding="utf-8"?>
<root>
<xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
<xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
<xsd:element name="root" msdata:IsDataSet="true">
  <xsd:complexType>
    <xsd:choice maxOccurs="unbounded">
      <xsd:element name="metadata">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" />
          </xsd:sequence>
          <xsd:attribute name="name" use="required" type="xsd:string" />
          <xsd:attribute name="type" type="xsd:string" />
          <xsd:attribute name="mimetype" type="xsd:string" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="assembly">
        <xsd:complexType>
          <xsd:attribute name="alias" type="xsd:string" />
          <xsd:attribute name="name" type="xsd:string" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="data">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
            <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
          <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
          <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="resheader">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" />
        </xsd:complexType>
      </xsd:element>
    </xsd:choice>
  </xsd:complexType>
</xsd:element>
</xsd:schema>
<resheader name="resmimetype">
<value>text/microsoft-resx</value>
</resheader>
<resheader name="version">
<value>2.0</value>
</resheader>
<resheader name="reader">
<value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<resheader name="writer">
<value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<data name="PCF_DataSetControl_LoadMore_ButtonLabel" xml:space="preserve">
<value>Load More</value>
<comment>Label for TSTableGrid's Load More Paging Button</comment>
</data>
<data name="PCF_DataSetControl_No_Record_Found" xml:space="preserve">
<value>No records found.</value>
<comment>No records found if no records</comment>
</data>
</root>
```

이 샘플에서는 데이터 집합 태그를 사용 하 여 구성 요소 매니페스트 파일에 입력 매개 변수를 정의 했습니다. 구성 요소에 바인딩되는 입력 속성입니다.  
 
이 구성 요소에는 구성 요소에 전달 되는 div에 추가 되는 주 div에 추가 되는 두 개의 중요 한 컨테이너가 있습니다.첫 번째 컨테이너는 뷰에서 레코드 데이터를 표시 하는 타일을 포함 하 고 두 번째 컨테이너는 한 페이지에 맞출 수 있는 더 많은 영역이 필요한 레코드가 있을 때 표시 되는 `Load More button`에 대 한 것입니다. 
 
두 컨테이너는 모두 [Updateview](../reference/control/updateview.md) 메서드가 호출 될 때마다 생성 되 고 새로 고쳐집니다. 첫 번째 컨테이너의 경우 열의 정보와 레코드 수를 기준으로 타일을 생성 합니다. 이렇게 하면 각 레코드의 타일이 해당 정보와 함께 표시 됩니다.  
 
레코드에 대해 다음 페이지가 있으면 로드 추가 단추가 표시 됩니다. 즉, 결과 집합에 페이지가 더 이상 없으면 두 번째 컨테이너가 표시 되 고 숨겨집니다.  
 
로드 추가 단추를 클릭 하 여 다음 레코드 페이지를 로드 하 고 기존 결과 집합에 추가 합니다 .이 단추를 숨기 거 나 표시 하는 논리는 코드에 표시 된 것과 동일 하 게 유지 됩니다.이는 단추에 바인딩되는 ***onLoadMoreButtonClick*** 메서드를 통해 처리 됩니다.
 
***ToggleLoadMoreButtonWhenNeeded*** 함수는 입력을 데이터 집합으로 사용 하 고, 데이터 집합에 다음 페이지가 있는지 여부를 확인 하 고, 단추를 숨기 거 나 표시할지 여부를 확인 하 고, 각각 단추를 숨기 거 나 표시 합니다.  
 
***OnRowClick*** 함수는 GUID 값을 사용 하 여 레코드의 컨텍스트를 연결 하 고 `NavigationAPI`의 [openForm](../reference/navigation/openform.md) 메서드를 호출 하 여 해당 레코드를 엽니다. 이 메서드는 ***createGridBody*** 메서드의 일부로 생성 되는 각 타일에 바인딩됩니다.
 
***GetSortedColumnsOnView*** 메서드는 뷰에서 정의 된 순서에 따라 열 목록을 반환 합니다.

### <a name="related-topics"></a>관련 항목

[샘플 구성 요소 다운로드](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[PowerApps 구성 요소 프레임 워크 API 참조](../reference/index.md)<br/>
[PowerApps 구성 요소 프레임 워크 매니페스트 스키마 참조](../manifest-schema-reference/index.md)
