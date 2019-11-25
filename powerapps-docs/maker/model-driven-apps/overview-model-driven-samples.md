---
title: 모델 기반 샘플 앱
description: 모델 기반 샘플 앱을 가져오고 사용자 지정하고 제거하는 방법을 이해합니다.
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5e579b7054171222819b2d1dd6bb21d9cb7400a9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711570"
---
# <a name="model-driven-sample-apps"></a>모델 기반 샘플 앱

[powerapps.com](https://powerapps.com)에서 샘플 앱을 사용하여 디자인 가능성을 탐색하고 고유한 앱을 개발할 때 적용할 수 있는 개념을 검색합니다. 각 샘플 앱은 가상 데이터를 사용하여 실제 시나리오를 보여주며, 

자세한 내용은 각 샘플 앱 관련 설명서를 참조하십시오. 

![기금 모금 샘플 앱](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>샘플 앱 가져오기

모델 기반 샘플 앱을 재생하거나 편집하려면 먼저 Common Data Service 데이터베이스에 앱을 프로비저닝해야 합니다. 먼저 평가판 환경과 데이터베이스를 만들고 **샘플 앱 및 데이터 포함**을 확인해야 합니다.

![데이터베이스 만들기](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> 이 옵션은 데이터베이스에 사용 가능한 모든 샘플 앱을 설치합니다. 샘플 앱은 교육용 및 데모용이며 프로덕션 데이터베이스에는 설치하지 않는 것이 좋습니다. 

## <a name="customize-a-sample-app"></a>샘플 앱 사용자 지정

1. [powerapps.com](https://powerapps.com)에 로그인  

    

2. **만들기** 페이지에서 샘플 앱을 마우스로 가리키고 **이 앱 만들기** 클릭합니다.

![모델 샘플 앱](media/overview-model-driven-samples/model-driven-create-page-sample.png)

3. 앱 디자이너는 앱을 사용자 지정하기 위한 여러 옵션을 제공하여 열립니다. 
4. 추가 사용자 지정 옵션에 대한 포털의 왼쪽에 있는 탐색에서 **고급**을 클릭합니다.

## <a name="remove-sample-apps-and-data"></a>샘플 앱 및 데이터 제거 
- 샘플 앱을 삭제하려면 해당하는 [관리형 솔루션](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution)을 삭제해야 합니다. 
- 솔루션을 삭제하면 앱에 대한 사용자 지정 엔터티와 관련된 모든 샘플 데이터만 삭제됩니다.
- 샘플 앱에 대한 사용자 지정이 만들어진 경우 [종속성](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components)이 있을 수 있으며 이는 솔루션을 삭제하기 전에 제거해야 합니다.

### <a name="steps"></a>단계
1. [PowerApps 관리 포털](https://admin.powerapps.com)에 로그인합니다.

2. 환경을 선택합니다.

3. **Dynamics 365 Administration Center**를 클릭합니다. 

    ![Dynamics 365 Administration Center](media/overview-model-driven-samples/admin-center.png)

4. 목록에서 데이터베이스를 선택하고 **열기**를 클릭합니다.

    ![데이터베이스 선택](media/overview-model-driven-samples/select-database.png)

5. **설정/솔루션**으로 이동합니다.

6. 삭제할 앱에 대한 솔루션을 선택하고 **삭제**를 클릭합니다.

    ![솔루션 삭제](media/overview-model-driven-samples/delete-solution.png)

*또는 제작자 포털에서 **고급**을 클릭하여 솔루션 목록으로 이동하고 .dynamics.com/ 후 URL의 모든 항목을 삭제합니다*.

> [!IMPORTANT]
> 영향을 알고 있지 않으면 다른 시스템 솔루션을 삭제하지 마십시오.

## <a name="install-or-uninstall-sample-data"></a>샘플 데이터 설치 또는 제거
1. 위의 1~4단계를 수행합니다.
2. **설정/데이터 관리/샘플 데이터**로 이동합니다.
3. 샘플 데이터가 설치된 경우 제거 옵션을 사용할 수 있습니다. 그렇지 않으면 설치 옵션을 사용할 수 있습니다. 

    ![샘플 데이터 제거](media/overview-model-driven-samples/remove-sample-data.png)




