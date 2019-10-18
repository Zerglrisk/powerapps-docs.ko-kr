---
title: 코드 구성 요소는 무엇 인가요? | MicrosoftDocs
description: PowerApps 구성 요소 프레임 워크를 사용 하 여 사용자가 양식, 보기 및 대시보드에서 데이터를 보고 작업할 수 있는 향상 된 사용자 환경을 제공 하는 코드 구성 요소를 만들 수 있습니다.
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 08a2043dfb92634837c367e664306d9c100632d6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346972"
---
# <a name="what-are-code-components"></a>코드 구성 요소 정의

코드 구성 요소는 솔루션 파일에 포함 되 고 다른 환경에 설치 될 수 있는 솔루션 구성 요소의 한 유형입니다. 추가 정보: [솔루션을 사용 하 여 확장 패키징 및 배포](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)

솔루션에 포함 하 여 코드 구성 요소를 추가한 다음 Common Data Service로 가져옵니다. 구성 요소가 Common Data Service 된 후에는 시스템 관리자 및 시스템에서 기본 구성 요소 대신 사용할 필드, 하위 그리드, 보기 및 대시보드 하위 그리드를 구성할 수 있습니다. Canvas 앱에서 이러한 코드 구성 요소를 추가할 수도 있습니다. 

코드 구성 요소는 다음 세 가지 요소로 구성 됩니다.

1. [Manifest.xml](#manifest)
2. [구성 요소 구현 라이브러리](#component-implementation-library)
3. [리소스](#resources)

## <a name="manifest"></a>Manifest.xml

매니페스트는 구성 요소를 정의하는 메타데이터 파일입니다. 다음을 설명 하는 XML 문서입니다.

- 구성 요소의 이름입니다.
- 필드 또는 데이터 집합 중에서 구성할 수 있는 데이터의 종류입니다.
- 구성 요소가 추가 될 때 응용 프로그램에서 구성할 수 있는 모든 속성입니다.
- 구성 요소에 필요한 리소스 파일의 목록입니다. 
- 필수 구성 요소 인터페이스를 적용 하는 개체를 반환 하는 구성 요소 구현 라이브러리의 TypeScript 함수 이름입니다.

사용자가 코드 구성 요소를 구성할 때 매니페스트 파일의 데이터는 사용 가능한 구성 요소를 필터링 하 여 해당 컨텍스트에 대 한 유효한 구성 요소만 구성할 수 있도록 합니다. 구성 요소에 대 한 매니페스트 파일에 정의 된 속성은 구성 요소를 구성 하는 사용자가 값을 지정할 수 있도록 구성 필드로 렌더링 됩니다. 이러한 속성 값은 런타임에 구성 요소에서 사용할 수 있습니다. 추가 정보: [매니페스트 스키마 참조](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>구성 요소 구현 라이브러리

구성 요소 라이브러리 구현은 PowerApps 구성 요소 프레임 워크를 사용 하 여 코드 구성 요소를 개발할 때 주요 단계 중 하나입니다. 개발자는 TypeScript를 사용 하 여 구성 요소 라이브러리를 구현할 수 있습니다. 각 코드 구성 요소에는 코드 구성 요소 인터페이스에 설명 된 메서드를 구현 하는 개체를 반환 하는 함수 정의를 포함 하는 라이브러리가 있어야 합니다. 

개체는 다음 메서드를 구현 합니다.

- [init](reference/control/init.md) (필수)
- [Updateview](reference/control/updateview.md) (필수)
- [Getoutputs](reference/control/getoutputs.md) (선택 사항)
- [제거](reference/control/destroy.md) (필수)

이러한 메서드는 코드 구성 요소의 수명 주기를 제어 합니다.

### <a name="page-load"></a>페이지 로드

페이지가 로드 되 면 응용 프로그램에서 개체를 사용 해야 합니다. 코드는 매니페스트 파일의 데이터를 사용 하 여를 호출 하 여 개체를 가져옵니다.

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

매니페스트의 네임 스페이스 및 생성자 값을 각각 `SampleNameSpace` 하 고 `LinearInputComponent` 하는 경우 개체를 인스턴스화하는 코드는 다음과 같습니다.

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

페이지가 준비 되 면 매개 변수 집합을 사용 하 여 [init](reference/control/init.md) 메서드를 호출 하 여 구성 요소를 초기화 합니다.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|매개 변수|설명|
|---|---|
|측면| 구성 요소를 구성 하는 방법 및 [PowerApps 구성 요소 프레임 워크 api](reference/index.md)와 함께 구성 요소 내에서 사용할 수 있는 모든 매개 변수에 대 한 모든 정보를 포함 합니다. 예를 들어 `context.parameters.<"property name from manifest">`를 사용 하 여 입력 속성에 액세스할 수 있습니다.|
|notifyOutputChanged |코드 구성 요소에 비동기적으로 검색할 준비가 된 새 출력이 있을 때마다 프레임 워크에 알립니다.|
|상태일|구성 요소가 [Setcontrolstate](reference/mode/setcontrolstate.md) 메서드를 사용 하 여 이전에 명시적으로 저장 한 경우 현재 세션에 있는 이전 페이지 로드의 구성 요소 데이터를 포함 합니다.|
|컨테이너|개발자와 앱 제작자가 구성 요소를 정의 하는 UI에 대 한 HTML 요소를 추가할 수 있는 HTML div 요소입니다.|

### <a name="user-changes-data"></a>사용자 변경 데이터

페이지가 로드 되 면 사용자가 구성 요소와 상호 작용 하 여 데이터를 변경할 때까지 구성 요소가 데이터를 표시 합니다. 이 경우 [init](reference/control/init.md) 메서드에서 *notifyOutputChanged* 매개 변수로 전달 된 메서드를 호출 해야 합니다. 이 메서드를 사용 하는 경우 플랫폼은 [Getoutputs](reference/control/getoutputs.md) 메서드를 호출 하 여 응답 합니다. [Getoutputs](reference/control/getoutputs.md) 메서드는 사용자가 변경한 내용을 포함 하는 값을 반환 합니다. 필드 구성 요소의 경우 일반적으로이 값은 구성 요소의 새 값입니다.

### <a name="app-changes-data"></a>앱 변경 데이터

플랫폼에서 데이터를 변경 하는 경우 구성 요소의 [Updateview](reference/control/updateview.md) 메서드를 호출 하 고 새 컨텍스트 개체를 매개 변수로 전달 합니다. 구성 요소에 표시 된 값을 업데이트 하려면이 메서드를 구현 해야 합니다.

### <a name="page-close"></a>페이지 닫기

사용자가 페이지에서 벗어날 때마다 코드 구성 요소는 범위를 상실 하 고 개체의 해당 페이지에 할당 된 모든 메모리가 지워집니다. 그러나 브라우저 구현 메커니즘을 기반으로 하는 일부 메서드는 메모리를 유지 하 고 사용할 수 있습니다. 일반적으로 이러한 이벤트 처리기는 이벤트 처리기입니다. 사용자가이 정보를 저장 하려는 경우에는 동일한 세션 내에서 정보가 다음에 제공 되도록 [Setcontrolstate](reference/mode/setcontrolstate.md) 메서드를 구현 해야 합니다.

개발자는 페이지를 닫을 때 호출 되는 [소멸](reference/control/destroy.md) 메서드를 구현 하 여 이벤트 처리기와 같은 정리 코드를 제거 해야 합니다.

## <a name="resources"></a>리소스

각 코드 구성 요소에는 시각화를 생성 하기 위한 리소스 파일이 있어야 합니다. 매니페스트에서 리소스 파일을 정의할 수 있습니다. 매니페스트 파일의 리소스 노드는 구성 요소가 시각화를 구현 하는 데 필요한 리소스를 나타냅니다. 추가 정보: [resources 요소](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>관련 항목

[코드 구성 요소 만들기 및 빌드](create-custom-controls-using-pcf.md)
