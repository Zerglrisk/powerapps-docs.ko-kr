---
title: 캔버스 앱에 대한 데이터 원본 이해 | Microsoft Docs
description: 캔버스 앱의 연결 및 데이터 원본 작업에 대한 참조 정보.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/08/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0bb04f9c3c1fc0d2b330e53dd39b355421af84aa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674289"
---
# <a name="understand-data-sources-for-canvas-apps-in-powerapps"></a>PowerApps에서 캔버스 앱에 대한 데이터 원본 이해

Power Apps에서 대부분의 canvas 앱은 **데이터 원본**이라고 하는 클라우드 서비스에 저장 된 외부 정보를 사용 합니다. 일반적인 예로 비즈니스용 OneDrive에 저장된 Excel 파일의 테이블이 있습니다. 앱에서 **연결**을 사용하여 이러한 데이터 원본에 액세스합니다.

이 문서에서는 다양한 종류의 데이터 원본 및 테이블 데이터 원본을 사용하는 방법에 대해 설명합니다.

데이터 원본에 대한 기본 읽기 및 쓰기를 수행하는 앱을 만드는 것은 쉽습니다. 하지만 때로는 데이터가 앱 내/외부로 흐르는 방식을 더 자세히 제어하려는 경우가 있습니다.  이 문서에서는 **[Patch](functions/function-patch.md)** , **[DataSourceInfo](functions/function-datasourceinfo.md)** , **[Validate](functions/function-validate.md)** 및 **[Errors](functions/function-errors.md)** 함수에서 더 많은 컨트롤을 제공하는 방법에 대해 설명합니다.

## <a name="kinds-of-data-sources"></a>데이터 원본의 종류

데이터 원본은 클라우드 서비스에 연결되거나 앱에 로컬로 연결될 수 있습니다.

### <a name="connected-data-sources"></a>연결된 데이터 원본

가장 일반적인 데이터 원본은 정보를 검색하고 저장하는 데 사용할 수 있는 **테이블**입니다. 데이터 원본에 대한 **연결**을 사용하여 데이터를 비즈니스용 OneDrive, DropBox 및 SQL Server와 같은 클라우드 서비스에 저장할 수 있는 Microsoft Excel 통합 문서, SharePoint 목록, SQL 테이블 및 다른 많은 형식으로 읽고 쓸 수 있습니다.

테이블 이외의 데이터 원본으로 전자 메일, 캘린더, Twitter 및 알림이 포함되지만, 이 문서에서는 이러한 다른 종류의 데이터 원본은 설명하지 않습니다.

### <a name="local-data-sources"></a>로컬 데이터 원본

**[갤러리](controls/control-gallery.md)** , **[폼 표시](controls/control-form-detail.md)** 및 **[폼 편집](controls/control-form-detail.md)** 컨트롤을 사용하면 데이터 원본의 데이터를 읽고 쓸 수 있는 앱을 손쉽게 만들 수 있습니다.  시작하려면 [데이터 폼 이해](working-with-forms.md)를 읽어 보세요.  

Power Apps에 데이터에서 앱을 만들도록 요청 하면 이러한 컨트롤이 사용 됩니다. 내부적으로 앱은 내부 테이블을 사용하여 데이터 원본에서 제공되는 데이터를 저장하고 조작합니다.

특별한 종류의 데이터 원본으로 [컬렉션](working-with-data-sources.md#collections)이 있습니다. 이는 클라우드의 서비스에 대한 연결로 지원되지 않고 로컬로 앱에 연결되므로, 동일한 사용자 또는 다른 사용자의 디바이스 간에 정보를 공유할 수 없습니다. 컬렉션은 로드하고 로컬에 저장할 수 있습니다.

### <a name="kinds-of-tables"></a>테이블의 종류

Power Apps 앱 내부에 있는 테이블은 숫자 또는 문자열 값과 마찬가지로 고정 값입니다. 내부 테이블은 어디에도 저장되지 않고 앱의 메모리에만 존재합니다. 테이블의 구조와 데이터는 직접 수정할 수 없습니다. 대신 수식을 통해 새 테이블을 만들 수 있습니다. 이 수식을 사용하여 원본 테이블의 수정된 복사본을 만듭니다.

외부 테이블은 나중의 검색 및 공유를 위해 데이터 원본에 저장됩니다.  Power Apps는 저장 된 데이터를 읽고 쓰기 위한 "연결"을 제공 합니다.  연결 내에서 여러 정보 테이블에 액세스할 수 있습니다.  앱에서 사용할 테이블을 선택하고 각 테이블은 별도의 '데이터 원본'이 됩니다.  

자세한 내용은 [테이블 작업](working-with-tables.md)에서 내부 테이블에 대해 자세히 설명하지만, 클라우드 서비스에 상주하는 외부 테이블에도 적용할 수 있습니다.

## <a name="working-with-tables"></a>테이블 작업
내부 파워 앱 표를 사용 하는 것과 동일한 방식으로 테이블 데이터 원본을 사용할 수 있습니다.  내부 테이블과 마찬가지로 각 데이터 원본에는 [레코드](working-with-tables.md#records), [열](working-with-tables.md#columns) 및 수식에 사용할 수 있는 속성이 있습니다. 또한,

* 데이터 원본은 연결의 기본 테이블과 동일한 열 이름 및 데이터 형식을 갖습니다.
  
    > [!NOTE]
  > 공백이 있는 열 이름이 포함 된 SharePoint 및 Excel 데이터 원본의 경우 Power Apps는 공백을 **"\_x0020\_"** 로 바꿉니다. 예를 들어 SharePoint 또는 Excel의 **"열 이름"** 은 데이터 레이아웃에 표시 되거나 수식에 사용 될 때 Power Apps에서 **"Column_x0020_Name"** 로 표시 됩니다.
* 데이터 원본은 앱이 로드될 때 서비스에서 자동으로 로드됩니다.  **[Refresh](functions/function-refresh.md)** 함수를 사용하여 강제로 데이터를 새로 고칠 수 있습니다.
* 사용자가 앱을 실행하면 레코드를 생성, 수정 및 삭제하고, 변경 내용을 서비스의 기본 테이블로 다시 푸시할 수 있습니다.
  * 레코드는 **[Patch](functions/function-patch.md)** 및 **[Collect](functions/function-clear-collect-clearcollect.md)** 함수로 만들 수 있습니다.  
  * 레코드는 **[Patch](functions/function-patch.md)** , **[Update](functions/function-update-updateif.md)** 및 **[UpdateIf](functions/function-update-updateif.md)** 함수로 수정할 수 있습니다.
  * 레코드는 **[Remove](functions/function-remove-removeif.md)** 및 **[RemoveIf](functions/function-remove-removeif.md)** 함수로 제거할 수 있습니다.
  * **[Errors](functions/function-errors.md)** 함수를 통해 데이터 원본으로 작업할 때 발생하는 오류를 사용할 수 있습니다.
* **[DataSourceInfo](functions/function-datasourceinfo.md)** , **[Defaults](functions/function-defaults.md)** 및 **[Validate](functions/function-validate.md)** 함수는 사용자 환경을 최적화하는 데 사용할 수 있는 데이터 원본에 대한 정보를 제공합니다.

### <a name="creating-data-sources"></a>데이터 원본 만들기
Power Apps를 사용 하 여 연결 된 데이터 원본을 만들거나 해당 구조를 수정할 수는 없습니다. 데이터 원본은 다른 위치에 있는 서비스에 이미 있어야 합니다. 예를 들어 OneDrive에 저장된 Excel 통합 문서에 테이블을 만들려면 먼저 OneDrive에서 Excel Online을 사용하여 통합 문서를 만듭니다. 다음으로 앱에서 이 문서에 대한 연결을 만듭니다.  

그러나 컬렉션 데이터 원본은 앱 내에서 "만들고 수정할 수 있지만" 일시적인 것입니다.

### <a name="display-one-or-more-records"></a>하나 이상의 레코드 표시
![](media/working-with-data-sources/reading-from-a-datasource.png) 위의 다이어그램에서는 앱에서 데이터 원본의 정보를 읽을 때 수행되는 정보 흐름을 보여 줍니다.

* 이 정보는 스토리지 서비스(이 경우 Office 365 사이트의 SharePoint 목록)를 통해 저장되고 공유됩니다.
* 연결을 사용하면 앱에서 이 정보를 사용할 수 있습니다.  연결은 사용자의 인증을 통해 정보에 액세스합니다.
* 앱이 시작되거나 **[Refresh](functions/function-refresh.md)** 함수를 누르면 정보가 로컬에서 사용하기 위해 정보를 연결에서 앱의 데이터 원본으로 가져옵니다.
* 수식은 정보를 읽고 사용자에게 표시될 수 있는 컨트롤에 정보를 공개하는 데 사용됩니다. 화면의 갤러리를 사용하고 **[Items](controls/properties-core.md)** 속성을 데이터 원본에 연결하여(**Gallery.Items = DataSource**) 데이터 원본의 레코드를 표시할 수 있습니다.  컨트롤의 **[Default](controls/properties-core.md)** 속성을 사용하여 갤러리 내의 컨트롤을 갤러리에 연결합니다.  
* 데이터 원본도 테이블입니다.  따라서 데이터 원본 전체를 사용하기 전에 **[Filter](functions/function-filter-lookup.md)** , **[Sort](functions/function-sort.md)** , **[AddColumns](functions/function-table-shaping.md)** 및 기타 함수를 사용하여 데이터 원본을 구체화하고 보강합니다.  또한 **[Lookup](functions/function-filter-lookup.md)** , **[First](functions/function-first-last.md)** , **[Last](functions/function-first-last.md)** 및 기타 함수를 사용하여 개별 레코드로 작업할 수 있습니다.

### <a name="modify-a-record"></a>레코드 수정
이전 섹션에서는 데이터 원본을 읽는 방법에 대해 알아보았습니다.  위의 다이어그램에 있는 화살표는 한 가지 방법입니다.  데이터 원본에 대한 변경 내용은 데이터가 검색된 동일한 수식을 통해 다시 푸시되지 않습니다.  대신 새 수식이 사용됩니다.  종종 다른 화면이, 특히 모바일 디바이스에서 레코드 검색보다는 레코드 편집에 사용됩니다.

데이터 원본의 기존 레코드를 수정하려면 원래의 데이터 원본에서 레코드를 가져와야 합니다.  레코드는 갤러리, [컨텍스트 변수](working-with-variables.md#use-a-context-variable) 및 임의 개수의 수식을 통해 이동할 수 있지만 해당 원본은 데이터 원본에서 다시 추적 가능해야 합니다.  이는 추가 정보가 고유하게 식별되는 레코드와 함께 이동함에 따라 레코드를 올바르게 수정해야 하므로 중요합니다.    

![](media/working-with-data-sources/writing-to-a-datasource.png) 위의 다이어그램에서는 데이터 원본을 업데이트하는 정보의 흐름을 보여 줍니다.

* **[편집 양식](controls/control-form-detail.md)** 컨트롤은 텍스트 입력 컨트롤 또는 슬라이더와 같은 사용자 입력 컨트롤로 구성된 입력 카드에 대한 컨테이너를 제공합니다.  **[DataSource](controls/control-form-detail.md)** 및 **[Item](controls/control-form-detail.md)** 속성은 편집할 레코드를 식별하는 데 사용됩니다.
* 각 입력 카드에는 일반적으로 **[Default](controls/properties-core.md)** 속성이 있으며, 이 속성은 대개 양식의 **ThisItem** 레코드 필드로 설정됩니다.  그러면 입력 카드 내의 컨트롤이 **[Default](controls/properties-core.md)** 에서 입력 값을 가져옵니다.  일반적으로 이 속성은 수정할 필요가 없습니다.
* 각 입력 카드는 **[Update](controls/control-card.md)** 속성을 노출합니다.  이 속성은 사용자 입력을 레코드의 특정 필드에 매핑하여 데이터 원본에 다시 씁니다.  일반적으로 이 속성은 수정할 필요가 없습니다.
* 화면의 단추 또는 이미지 컨트롤을 사용하여 레코드 변경 내용을 저장할 수 있습니다.  컨트롤의 **[OnSelect](controls/properties-core.md)** 수식은 **[SubmitForm](functions/function-form.md)** 함수를 호출하여 이 작업을 수행합니다.  **[SubmitForm](functions/function-form.md)** 은 카드의 **[Update](controls/control-card.md)** 속성을 모두 읽고 이를 사용하여 데이터 원본에 쓰기 저장합니다.
* 때로는 문제가 있을 수 있습니다.  네트워크 연결이 중단되거나 앱에서 인식하지 못하는 서비스에서 유효성 검사가 수행될 수 있습니다.  양식 컨트롤의 **Error** 및 **[ErrorKind](controls/control-form-detail.md)** 속성을 통해 이 정보를 사용할 수 있으므로 해당 정보가 사용자에게 표시될 수 있습니다.  

프로세스에 대해 더 자세히 제어하려면 **[Patch](functions/function-patch.md)** 및 **[Errors](functions/function-errors.md)** 함수를 사용할 수도 있습니다.  **[편집 양식](controls/control-form-detail.md)** 컨트롤은 **[Updates](controls/control-form-detail.md)** 속성을 노출하므로 양식의 필드 값을 읽을 수 있습니다.  또한 이 속성을 사용하여 **Patch** 및 **SubmitForm** 함수를 완전히 무시하고 연결에서 사용자 지정 커넥터를 호출할 수도 있습니다.

### <a name="validation"></a>유효성 검사
레코드를 변경하기 전에 앱에서 변경 내용을 적용할 수 있는지 확인해야 합니다.  여기에는 두 가지 이유가 있습니다.

* *사용자에 대한 즉각적인 피드백*.  문제를 해결하기 위한 가장 적합한 시기는 문제가 발생할 때, 즉 사용자의 마음 속에 선명하게 있을 때입니다.  실제로 각 터치 또는 키 입력을 사용하면 해당 항목에 있는 문제를 식별하는 빨간색 텍스트가 표시될 수 있습니다.
* 네트워크 트래픽 감소 및 사용자 대기 시간 감소 -  앱에서 발견된 문제가 많을수록 네트워크를 통한 대화 수가 줄어들어 문제를 검색하고 해결할 수 있습니다.  각 대화에는 사용자가 계속 이동하기 전에 기다려야 하는 시간이 필요합니다.

Power Apps는 유효성 검사를 위한 두 가지 도구를 제공 합니다.

* 데이터 원본은 유효하거나 유효하지 않은 항목에 대한 정보를 제공할 수 있습니다.  예를 들어 숫자에 최소값과 최대값이 있을 수 있으며, 하나 이상의 항목이 필요할 수 있습니다.  **[DataSourceInfo](functions/function-datasourceinfo.md)** 함수를 사용하여 이 정보에 액세스할 수 있습니다.  
* **[Validate](functions/function-validate.md)** 함수는 이 동일한 정보를 사용하여 단일 열 또는 전체 레코드의 값을 확인합니다.

### <a name="error-handling"></a>오류 처리
아주 멋지게 레코드에 대한 유효성을 검사했군요.  이제는 **[Patch](functions/function-patch.md)** 를 사용하여 해당 레코드를 업데이트할 시간입니다!

그러나 슬프게도 아직 문제가 있을 수 있습니다.  네트워크가 중단되었거나, 서비스에서 유효성 검사가 실패했거나, 사용자에게 앱에 발생할 수 있는 몇 가지 오류의 이름을 지정하는 데 있어 적절한 권한이 없습니다.  오류 상황에 적절하게 대응하여 사용자에게 피드백을 제공하고 올바르게 만들 수 있는 수단을 제공해야 합니다.  

데이터 원본에 오류가 발생하면 앱에서 자동으로 오류 정보를 기록하고 **[Errors](functions/function-errors.md)** 함수를 통해 이 오류 정보를 사용할 수 있도록 합니다.  오류는 문제가 있는 레코드와 관련이 있습니다.  사용자가 해결할 수 있는 문제(예: 유효성 검사 문제)이면 레코드를 다시 제출할 수 있으며 오류가 지워집니다.

**[Patch](functions/function-patch.md)** 또는 **[Collect](functions/function-clear-collect-clearcollect.md)** 를 사용하여 레코드를 만들 때 오류가 발생하면 오류와 관련된 레코드가 없습니다.  이 경우 *공백*이 **[Patch](functions/function-patch.md)** 에서 반환되고 **[Errors](functions/function-errors.md)** 에 대한 레코드 인수로 사용될 수 있습니다.  만들기 오류는 다음 작업을 수행하면 지워집니다.

**[Errors](functions/function-errors.md)** 함수는 오류 정보 테이블을 반환합니다.  특정 열로 인해 오류가 발생하면 이 정보에 열 정보가 포함될 수 있습니다.  편집 화면에서 열이 있는 위치에 가까운 레이블 컨트롤에서 열 수준 오류 메시지를 사용합니다.  오류 테이블의 **열**이 *공백*이고 전체 레코드에 대한 **저장** 단추에 가까운 위치에서 레코드 수준 오류 메시지를 사용합니다.  

### <a name="working-with-large-data-sources"></a>큰 데이터 원본 작업
큰 데이터 원본(수백만 개의 레코드)에서 보고서를 만들 때는 네트워크 트래픽을 최소화해야 합니다. 뉴욕시에 StatusCode가 "Platinum"인 모든 고객에 대해 보고하려는 경우를 가정해 보겠습니다. 그리고 Customers 테이블에는 수백만 개의 레코드가 포함되어 있습니다.

이러한 수백만 명의 고객을 앱에 가져와서 원하는 고객을 선택하고 싶지는 **않습니다**. 다시 말하면 테이블을 저장하는 클라우드 서비스 내에서 선택 작업을 수행하고 선택한 레코드만 네트워크를 통해 보내려고 합니다.

레코드를 선택하는 데 사용할 수 있는 함수는 전부는 아니지만 많은 함수가 '위임'될 수 있습니다. 이는 클라우드 서비스 내에서 실행된다는 것입니다. [위임](delegation-overview.md)에 대한 내용을 참조하면 이 작업을 수행하는 방법을 알아볼 수 있습니다.

## <a name="collections"></a>수집이
컬렉션은 특별한 종류의 데이터 원본입니다.  이는 클라우드의 서비스에 대한 연결로 지원되지 않고 로컬로 앱에 연결되므로, 동일한 사용자 또는 다른 사용자의 디바이스 간에 정보를 공유할 수 없습니다.  몇 가지 예외를 제외하고는 다른 데이터 원본처럼 작동합니다.

* 컬렉션은 **[Collect](functions/function-clear-collect-clearcollect.md)** 함수를 사용하여 동적으로 만들 수 있습니다.  연결 기반 데이터 원본에서 수행하는 것처럼 미리 설정할 필요가 없습니다.
* 컬렉션의 열은 **[Collect](functions/function-clear-collect-clearcollect.md)** 함수를 사용하여 언제든지 수정할 수 있습니다.
* 컬렉션에서는 중복 레코드가 허용됩니다.  컬렉션에 동일한 레코드의 복사본이 둘 이상 있을 수 있습니다.  **[Remove](functions/function-remove-removeif.md)** 와 같은 함수는 **All** 인수가 제공되지 않으면 찾은 첫 번째 일치 항목에서 작동합니다.
* **[SaveData](functions/function-savedata-loaddata.md)** 및 **[LoadData](functions/function-savedata-loaddata.md)** 함수를 사용하여 컬렉션의 복사본을 저장하고 다시 로드할 수 있습니다.  정보는 다른 사용자, 앱 또는 디바이스에서 액세스할 수 없는 개인 위치에 저장됩니다.
* **[내보내기](controls/control-export-import.md)** 및 **[가져오기](controls/control-export-import.md)** 컨트롤을 사용하여 컬렉션의 복사본을 사용자가 상호 작용할 수 있는 파일로 저장하고 다시 로드할 수 있습니다.  

컬렉션을 데이터 원본으로 사용하는 방법에 대한 자세한 내용은 [컬렉션 만들기 및 업데이트](create-update-collection.md)를 참조하세요.

컬렉션은 일반적으로 앱에 대한 전역 상태를 유지하는 데 사용됩니다.  상태 관리에 사용할 수 있는 옵션은 [변수 작업](working-with-variables.md)을 참조하세요.

