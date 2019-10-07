---
title: AppSource에서 고객이 캔버스 앱을 시험 사용할 수 있도록 하기 | Microsoft Docs
description: AppSource를 사용하여 고객과 캔버스 앱을 공유하고 비즈니스를 위해 잠재 고객을 창출합니다.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/08/2017
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 570d9430d7dbcc5e8d41b7128060677fe1ff45a1
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993073"
---
# <a name="let-customers-test-drive-your-canvas-app-on-appsource"></a>AppSource에서 고객이 캔버스 앱을 시험 사용할 수 있도록 하기

PowerApps에서 캔버스 앱을 빌드하는 데 열중하고 있나요? 캔버스 앱을 고객과 공유하시겠습니까? [AppSource.com](https://appsource.microsoft.com)은 고객과 앱을 공유하고 비즈니스 잠재 고객을 창출하도록 PowerApps 시험 사용 솔루션을 지원합니다.

## <a name="what-is-a-test-drive-solution"></a>시험 사용 솔루션이란?

시험 사용 솔루션을 통해 고객은 PowerApps 계획에 등록하거나 애플리케이션을 설치하지 않고 실제 앱을 사용해 볼 수 있습니다. 고객은 자신의 AAD(Azure Active Directory) 계정을 사용하여 AppSource.com에 로그인하고 웹 브라우저에서 앱을 실행하면 됩니다. 시험 사용 없이 고객은 앱에 대해 읽거나 설명하는 비디오를 시청할 수만 있습니다. 시험 사용을 통해 고객은 솔루션이 무엇이며 앱이 가진 기능에 대해 더 잘 파악할 수 있습니다. 또한 앱을 사용하여 실제의 경험을 갖습니다. 고객은 앱이 작성된 방법을 확인하기 위해 내막을 살펴볼 수 없으므로 지적 재산권은 보호됩니다. 비즈니스 성장에 도움을 주기 위해 시험 사용 앱을 시작하는 사용자에 대한 잠재 고객 정보를 수집하고 공유합니다.

다음은 AppSource.com에서 [앱 목록](https://go.microsoft.com/fwlink/?linkid=848867)의 예제입니다.

![샘플 AppSource 목록 ](./media/dev-appsource-test-drive/sample-app-source-listing.png)

위의 앱 목록에서 **무료 평가판** 링크를 선택하면 사용자의 브라우저 내에서 직접 연결된 PowerApps 시험 사용 앱을 시작합니다.

![샘플 앱 웹 플레이어](./media/dev-appsource-test-drive/sample-app-web-player.png)

## <a name="how-do-i-build-a-test-drive-solution"></a>시험 사용 솔루션을 어떻게 빌드하나요?
시험 사용 솔루션에 대한 앱을 빌드하는 것은 PowerApps에서 앱을 빌드하는 것과 같지만 외부 데이터 연결 대신 포함된 데이터를 사용합니다. 포함된 데이터를 사용하면 고객에게 앱을 배포하는 장벽을 낮춰 사용해 보기 위한 마찰을 없앱니다. 고객에게 궁극적으로 배포하는 전체 솔루션은 일반적으로 데이터 연결을 포함하지만 포함된 데이터는 시험 사용 솔루션에 적합합니다.

PowerApps는 기본적으로 포함된 데이터로 앱 빌드를 지원하므로 앱을 사용하기 위해 샘플 데이터만이 필요합니다. 이 데이터는 하나 이상의 테이블로 Excel 파일에서 캡처되어야 합니다. 그러면 PowerApps에서 Excel 테이블의 데이터를 앱으로 가져오고 외부 연결을 통하는 대신 거기에서 작업합니다. 아래 3단계 프로세스는 데이터를 가져오고 앱에서 해당 데이터를 사용하는 방법을 보여 줍니다.

### <a name="step-1-import-data-into-the-app"></a>1 단계: 앱으로 데이터 가져오기
Excel 파일에 다음 두 개의 테이블이 있다고 가정 합니다. **Siteinspector** 및 **Sitephotos**.

![가져올 Excel 테이블](./media/dev-appsource-test-drive/excel-file.png)

**앱에 정적 데이터 추가** 옵션을 사용하여 이러한 두 테이블을 PowerApps로 가져옵니다.

![앱에 정적 데이터 추가](./media/dev-appsource-test-drive/static-data.png)

이제 앱에 데이터 원본으로 테이블을 가집니다.

![가져온 데이터 원본으로 Excel 테이블](./media/dev-appsource-test-drive/data-sources.png)

### <a name="step-2-handling-read-only-and-read-write-scenarios"></a>2 단계: 읽기 전용 및 읽기/쓰기 시나리오 처리
가져온 데이터는 *정적*이므로 읽기 전용입니다. 앱이 읽기 전용인 경우(즉, 사용자에게 데이터를 표시만 함) 앱에서 직접 테이블을 참조합니다. 예를 들어, **SiteInspector** 테이블에서 **Title** 필드에 액세스하려는 경우 수식에서 **SiteInspector.Title**을 사용합니다.

앱이 읽기-쓰기인 경우 먼저 각 테이블에서 PowerApps에서 표 형식 데이터 구조인 *컬렉션*으로 데이터를 가져옵니다. 그런 다음 테이블보다는 컬렉션에서 작업합니다. **SiteInspector** 및 **SitePhotos** 테이블에서 **SiteInspectorCollect** 및 **SitePhotosCollect** 컬렉션으로 데이터를 가져오려면:

```powerapps-dot
ClearCollect( SiteInspectorCollect, SiteInspector ); 
ClearCollect( SitePhotosCollect, SitePhotos )
```

수식은 두 컬렉션을 지운 다음 각 테이블에서 적절한 컬렉션으로 데이터를 수집합니다.

* 앱의 임의 위치에서 이 수식을 호출하여 데이터를 로드합니다.
* **파일** > **컬렉션**으로 이동하여 앱에서 모든 컬렉션을 봅니다.
* 자세한 내용은 [앱에서 컬렉션 만들기 및 업데이트](../canvas-apps/create-update-collection.md)를 참조하세요.

이제 **Title** 필드에 액세스하려는 경우 수식에서 **SiteInspectorCollect.Title**을 사용합니다.

### <a name="step-3-add-update-and-delete-data-in-your-app"></a>3 단계: 앱에서 데이터 추가, 업데이트 및 삭제
지금까지 데이터를 직접 및 컬렉션에서 읽는 방법을 살펴봤습니다. 이제 컬렉션에서 데이터를 추가, 업데이트 및 삭제하는 방법을 보여 줍니다.

**컬렉션에 행을 추가하려면** [Collect( DataSource, Item, ... )](../canvas-apps/functions/function-clear-collect-clearcollect.md)을 사용합니다.

```powerapps-dot
Collect( SiteInspectorCollect,
    {
        ID: Value( Max( SiteInspectorCollect, ID ) + 1 ),
        Title: TitleText.Text,
        SubTitle: SubTitleText.Text,
        Description: DescriptionText.Text
    }
)
```

**컬렉션에서 행을 업데이트하려면** [UpdateIf( DataSource, Condition1, ChangeRecord1 [, Condition2, ChangeRecord2, ...] )](../canvas-apps/functions/function-update-updateif.md)를 사용합니다.

```powerapps-dot
UpdateIf( SiteInspectorCollect,
    ID = record.ID,
    {
        Title: TitleEditText.Text,
        SubTitle: SubTitleEditText.Text,
        Description: DescriptionEditText.Text
    }
)
```

**컬렉션에서 행을 삭제하려면** [RemoveIf( DataSource, Condition [, ...] )](../canvas-apps/functions/function-remove-removeif.md)를 사용합니다.

```powerapps-dot
RemoveIf( SiteInspectorCollect, ID = record.ID )
```

> [!NOTE]
> 컬렉션은 앱이 실행되는 동안만 데이터를 보관합니다. 앱이 닫힐 때 모든 변경 내용은 삭제됩니다.

요약하자면, 외부 데이터에 연결하는 앱의 경험을 시뮬레이션하는 포함된 데이터로 앱의 버전을 만들 수 있습니다. 데이터가 포함된 후 AppSource.com에서 시험 사용으로 이 앱을 게시할 준비가 됩니다.

## <a name="how-do-i-list-my-test-drive-solution-on-appsourcecom"></a>AppSource.com에 내 시험 사용 솔루션을 어떻게 게시하나요?
이제 앱이 준비되었으므로 AppSource.com에 게시할 시간입니다. 이 프로세스를 시작하려면 PowerApps.com의 [신청서](https://powerapps.microsoft.com/partners/get-listed/)를 작성하세요.

신청한 후 AppSource.com에 게시할 앱을 제출하는 방법에 대한 지침이 포함된 전자 메일을 받게 됩니다. 전체 엔드투엔드 프로세스를 캡처하는 온보딩 설명서는 [여기](https://go.microsoft.com/fwlink/?linkid=851031)에서 다운로드할 수도 있습니다.

