---
title: PowerApps의 솔루션 모범 사례 | MicrosoftDocs
description: 솔루션 작업 시 모범 사례에 대해 알아보십시오.
ms.custom: ''
ms.date: 10/08/2019
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
ms.assetid: ''
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e10b9951ca70e497349620ae96308d6db49403fe
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702154"
---
# <a name="best-practices-when-working-with-solutions"></a>솔루션 작업 시 모범 사례 
이 항목에서는 솔루션 작업 시 모범 사례에 대해 설명합니다. 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>단일 관리형 솔루션을 사용하여 모델 기반 앱 관리 
관리형 솔루션에 포함된 앱을 업데이트하려면 업데이트 또는 패치 솔루션을 사용하십시오. 동일한 모델 기반 앱이 있는 환경에 다른 관리형 솔루션을 설치하지 마십시오. 추가 정보: [솔루션 업데이트](import-update-export-solutions.md#update-solutions) 및 [분할된 솔루션과 패치를 사용하여 선택한 엔터티 자산 내보내기](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>보안 역할을 사용하여 앱 액세스 관리
모델 기반 앱에는 사용자 액세스를 제어하는 보안 역할이 할당되어 있어야 합니다. 추가 정보: [앱에 보안 역할 추가](../model-driven-apps/share-model-driven-app.md#add-security-roles-to-the-app) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>관리형 솔루션을 삭제하여 모델 기반 앱 삭제 
관리형 솔루션의 일부로 기본 솔루션에 설치된 모델 기반 앱을 삭제하려면 관리형 솔루션을 삭제하십시오. 

관리형 솔루션의 일부로 설치된 기본 환경에서 앱 또는 앱의 사이트 맵을 직접 삭제하지 마십시오. 그렇게 하면 앱을 설치하는 데 사용된 솔루션의 솔루션 업그레이드 또는 솔루션 업데이트가 실패할 수 있습니다. 모델 기반 앱을 직접 삭제하는 예는 솔루션 탐색기에서 기본 솔루션을 열고 **모델 기반 앱**으로 이동하여 앱을 선택한 다음 **삭제**를 선택하는 경우가 있습니다.

### <a name="see-also"></a>참조
[솔루션 개요](solutions-overview.md)
