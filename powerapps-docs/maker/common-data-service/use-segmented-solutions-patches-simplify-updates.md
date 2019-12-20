---
title: Power Apps에서 세분화된 솔루션과 패치를 사용하여 솔루션 업데이트 간소화 | MicrosoftDocs
description: 솔루션 분할을 사용하여 솔루션을 업데이트하는 방법 알아보기
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c7a757e7c9b8342778ec2d9f12d05c2b9bc49dd4
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869771"
---
# <a name="use-segmented-solutions-and-patches-to-export-selected-entity-assets"></a>세분화된 솔루션 및 패치를 사용하여 선택한 Glossary 자산 내보내기

솔루션 및 솔루션 패치에서 무엇을 배포할지 엄격하게 제어하기 위해 솔루션 세분화를 사용합니다. 분할 솔루션을 사용하여 선택한 엔터티 자산과 엔터티 필드, 양식 및 보기 보다는 전체 엔터티 같은 모든 자산을 사용하여 솔루션을 내보낼 수 있습니다. 세분화된 솔루션과 패치를 만들려면 코드를 작성하지 않고 솔루션 사용자 인터페이스를 사용할 수 있습니다.  
  
 솔루션에 무엇이 있는지 효과적으로 제어하는 것 외에 패치에 무엇이 진행되는지 제어할 수 있습니다. 상위 솔루션에 대한 패치를 만들고 기본 솔루션에 부분 업데이트로 내보낼 수 있습니다. 솔루션을 복제하면 시스템은 모든 관련 패치를 기본 솔루션으로 롤업하고 새 버전을 만듭니다.  
  
 패치와 복제된 솔루션 작업을 수행할 때 다음 정보를 염두에 두십시오.  
  
-   패치는 상위 솔루션에 대한 증분 부분 업데이트를 나타냅니다. 패치는 대상 시스템에 설치했을 때 상위 솔루션에 구성 요소와 자신을 추가 또는 업데이트할 수 있지만 상위 솔루션에서 구성 요소나 자산을 삭제할 수 있습니다.  
  
-   패치는 상위 솔루션을 하나만 가질 수 있지만 상위 솔루션은 하나 이상의 패치를 가질 수 있습니다.  
  
-   패치는 관리되지 않는 솔루션에 대해 만들어집니다. 관리형 솔루션을 위한 패치를 만들 수 없습니다.  
  
-   대상 시스템에 패치를 내보낼 때 관리 패치로 내보내야 합니다. 프로덕션 환경에서 관리되지 않는 패치를 사용하지 마십시오.  
  
-   패치를 설치하려면 상위 솔루션이 대상 시스템에 있어야 합니다.  
  
-   패치를 삭제하거나 업데이트할 수 있습니다.  
  
-   상위 솔루션을 삭제하면 모든 하위 패치도 삭제됩니다. 시스템은 삭제 작업을 실행 취소할 수 없다는 경고 메시지를 제공합니다. 삭제는 단일 트랜잭션으로 수행됩니다. 패치 또는 상위 솔루션 중 하나가 삭제에 실패하면 전체 트랜잭션이 롤백됩니다.  
  
-   상위 솔루션에 대한 첫 번째 패치를 만든 후에는 솔루션이 잠기고 이 솔루션을 변경하거나 내보낼 수 없습니다. 그러나 모든 하위 패치를 삭제하는 경우 상위 솔루션 잠금이 해제됩니다.  
  
-   기본 솔루션을 복제하면 모든 하위 패치를 기본 솔루션으로 롤업되고 새 버전을 만듭니다. 복제된 솔루션에서 구성 요소와 자산을 추가, 편집 또는 삭제할 수 있습니다.  
  
-   복제된 솔루션은 관리형 솔루션으로 대상 시스템에 설치되었을 때 기본 솔루션의 대체를 나타냅니다. 일반적으로 복제된 솔루션을 이전 솔루션으로 주요 업데이트를 처리합니다.  
  
## <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>복제된 솔루션 및 패치의 버전 번호 이해하기  
 솔루션 버전의 형식은 major.minor.build.revision입니다. 패치는 상위 솔루션보다 더 높은 빌드 또는 개정 번호를 가져야 합니다. 더 높은 주 또는 부 버전이 있을 수 있습니다. 예를 들어, 기본 솔루션 버전 3.1.5.7의 경우 패치는 버전 3.1.5.8 또는 버전 3.1.7.0이 될 수 있지만 버전 3.2.0.0는 될 수 없습니다. 복제된 솔루션에는 기본 솔루션의 버전 번호보다 크거나 같은 버전 번호가 있어야 합니다. 예를 들어, 기본 솔루션 버전 3.1.5.7의 경우 복제된 솔루션은 버전 3.2.0.0 또는 버전 3.1.5.7이 될 수 있습니다. UI에서는 복제된 솔루션의 경우 주 버전과 부 버전을, 패치의 경우 빌드 또는 개정 값만 설정할 수 있습니다.  
  
## <a name="create-a-segmented-solution-with-the-entity-assets-you-want"></a>원하는 엔터티 자산을 사용하여 세분화된 솔루션을 만듭니다.  
 세분화된 솔루션을 만들려면 먼저 비관리형 솔루션을 만들고 기존 리소스를 추가합니다. 여러 시스템 또는 사용자 지정 엔터티를 추가하고 각 엔터티에 대해 솔루션에 포함하려는 자산을 선택할 수 있습니다. 마법사 같은 설정은 엔터티 자산을 추가하는 프로세스를 단계별로 안내합니다.  
  
1. **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **솔루션**으로 이동합니다.   
  
2.  **새로 만들기**를 선택하고 솔루션을 만듭니다. 필수 필드에 정보를 입력합니다. **저장 후 닫기**를 선택합니다.  
  
3.  방금 만든 솔루션을 엽니다. **기존 항목 추가** 드롭다운 목록에서 **엔터티**를 선택합니다.  
  
4.  **솔루션 구성 요소 선택** 대화 상자에서 솔루션에 추가하려는 엔터티를 하나 이상 선택합니다. **확인**을 선택합니다.  
  
5.  마법사가 열립니다. 마법사에 따라 각 선택한 엔터티의 자산을 솔루션에 추가합니다.  
  
6.  변경 사항을 발효시키려면 **게시**를 선택합니다.  
  
 다음 그림은 `Account`, `Case` 및 `Contact` 엔터티에서 엔터티 자산을 선택하여 세분화된 솔루션을 만드는 예를 제공합니다.  
  
 먼저 **엔터티** 구성 요소를 선택합니다.  

 > [!div class="mx-imgBorder"] 
 > ![기존 리소스 추가.](media/solution-segmentation-add-existing-resources-admin.png "기존 리소스 추가.")  
  
 그런 다음 솔루션 구성 요소를 선택합니다.  
  
 ![솔루션 구성 요소 선택.](media/solution-segmentation-select-components-admin.png "솔루션 구성 요소 선택.")  
  
 마법사를 따릅니다. 1단계에서 알파벳 순서로 시작하여 첫 번째 엔터티, 그림처럼 `Account` 엔터티의 자산을 선택합니다.  
  
 ![마법사 시작.](media/solution-segmentation-wizard-starts-admin.png "마법사 시작.")  
  
 **필드** 탭을 열고 **계좌 번호** 필드를 선택합니다.  
  
 ![거래처 엔터티 자산 선택.](media/solution-segmentation-select-account-assets-admin.png "거래처 엔터티 자산 선택.")  
  
 2단계에서 **서비스 케이스** 엔터티에 대해 모든 자산을 추가합니다.  
  
 ![서비스 케이스 엔터티 자산 선택.](media/solution-segmentation-select-case-assets-admin.png "서비스 케이스 엔터티 자산 선택.")  
  
 3단계에서 **연락처** 엔터티에 대해 **기념일** 필드를 추가합니다.  
  
 ![연락처 엔터티 자산 선택.](media/solution-segmentation-select-contact-assets-admin.png "연락처 엔터티 자산 선택.")  
  
 결과적으로 만들어지는 세분화된 솔루션은 3개의 엔터티 `Account`, `Case` 및 `Contact`을 포함합니다. 각 엔터티는 선택된 자산만 포함합니다.  
  
 > [!div class="mx-imgBorder"] 
 > ![엔터티가 있는 솔루션.](media/solution-segmentation-solution-entities-admin.png "엔터티가 있는 솔루션.")  
  
## <a name="create-a-solution-patch"></a>솔루션 패치 만들기  
 패치에는 구성 요소와 자산 추가 또는 편집 같은 상위 솔루션에 대한 변경 사항이 포함됩니다. 편집할 계획이 없는 경우 상위 구성 요소를 포함할 필요는 없습니다.  
  
 #### <a name="create-a-patch-for-an-unmanaged-solution"></a>관리되지 않는 솔루션에 대해 패치 만들기  
  
1. **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **솔루션**으로 이동합니다.   
  
2.  목록에서 패치를 만들 비관리형 솔루션을 선택합니다. **패치 복제**를 선택합니다. 열리는 대화 상자는 기본 솔루션 이름과 패치 버전 번호를 포함합니다. **저장**을 선택합니다.  
  
3.  표에서 새로 만든 패치를 찾아서 엽니다. 기본 솔루션과 마찬가지로 마법사에 따라 원하는 구성 요소와 자산을 추가합니다.  
  
4.  변경 사항을 발효시키려면 **게시**를 선택합니다.  
  
 다음 그림은 기존 솔루션에 대한 패치를 만드는 예제를 제공합니다. **패치 복제**를 선택합니다(압축된 보기에서 **패치 복제** 아이콘은 아래 그림처럼 두 개의 작은 사각형으로 표시됩니다).  
  
 > [!div class="mx-imgBorder"] 
 > ![패치 복제 아이콘.](media/solution-segmentation-click-patch-icon-admin.png "패치 복제 아이콘.")  
  
 **패치 복제** 대화 상자에서 패치의 버전 번호가 상위 솔루션 버전 번호를 기준으로 하지만 빌드 번호는 1씩 증가합니다. 각 후속 패치는 이전 패치보다 빌드 또는 개정 번호가 더 높습니다.  
  
 ![패치로 복제 대화 사용.](media/solution-segmentation-clone-patch-dialog-admin.png "패치로 복제 대화 사용.")  
  
 다음 스크린샷은 기본 솔루션 **SegmentedSolutionExample**, 버전 **1.0.1.0** 및 패치 **SegmentedSolutionExample_Patch**, 버전 **1.0.2.0**를 보여줍니다.  
  
 > [!div class="mx-imgBorder"] 
 > ![솔루션 및 패치가 포함된 표.](media/solution-segmentation-solution-patch-grid-admin.png "솔루션 및 패치가 포함된 표.")  
  
 패치에서 `Book`라는 새로운 사용자 지정 엔터티를 추가했고 패치에 `Book` 엔터티의 모든 자산을 포함했습니다.  
  
 ![패치에 사용자 지정 엔터티 추가.](media/solution-segmentation-add-book-patch-admin.png "패치에 사용자 지정 엔터티 추가.")  
  
## <a name="clone-a-solution"></a>솔루션 복제  
 비관리형 솔루션을 복제하면 이 솔루션과 관련된 모든 패치는 원래 솔루션의 새로 만든 버전으로 롤업됩니다.  
  
1. **[설정](../model-driven-apps/advanced-navigation.md#settings)** > **솔루션**으로 이동합니다.   
  
2.  목록에서 복제하려는 비관리형 솔루션을 선택합니다. **복제 솔루션**을 선택합니다. 열리는 대화 상자는 기본 솔루션 이름과 새 버전 번호를 포함합니다. **저장**을 선택합니다.  
  
3.  변경 사항을 발효시키려면 **게시**를 선택합니다.  
  
 예제를 계속하면 새로운 솔루션 버전 번호를 보여주는 **솔루션으로 복제** 대화 상자가 나타납니다.  
  
 ![솔루션으로 복제 대화 사용.](media/solution-segmentation-clone-solution-dialog-admin.png "솔루션으로 복제 대화 사용.")  
  
 복제 후에 새로운 솔루션 버전은 3개의 원래 엔터티(`Account`, `Case` 및 `Contact`)와 패치에 추가된 `Book`라는 사용자 지정 엔터티를 포함합니다. 각 엔터티는 예제에 추가된 자산만 포함합니다.  
  
 > [!div class="mx-imgBorder"] 
 > ![롤업 패치가 있는 복제된 솔루션.](media/solution-segmentation-solution-rolled-up-patch-admin.png "롤업 패치가 있는 복제된 솔루션.")  
  
## <a name="next-steps"></a>다음 단계  
 [솔루션 개요](solutions-overview.md) [패치를 만들어 솔루션 업데이트 간소화]

