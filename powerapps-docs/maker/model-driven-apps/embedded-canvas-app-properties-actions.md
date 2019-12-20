---
title: ModelDrivenFormIntegration 컨트롤의 속성 및 동작 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 674147425097d75b96e14bfbf76b3c937f9fd999
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868450"
---
# <a name="modeldrivenformintegration-control-properties-and-actions"></a>ModelDrivenFormIntegration 컨트롤의 속성 및 동작
모델 기반 양식에 포함된 캔버스 앱에는 **ModelDrivenFormIntegration**이라는 특수 컨트롤이 포함되어 있습니다. 이 컨트롤은 호스트 모델 기반 양식에서 포함된 캔버스 앱으로 컨텍스트 데이터를 가져오는 역할을 합니다.  

이 항목에서는 ModelDrivenFormIntegration 컨트롤에서 사용할 수 있는 속성과 동작에 대해 설명합니다.

| 속성 또는 작업 | 설명 |
|:--------------|:-------------------------|
|**DataSource** | 호스트 모델 기반 양식의 상위 엔터티에 연결된 데이터 소스로 설정해야 합니다. <br />[새 캔버스 앱을 삽입](embedded-canvas-app-add-classic-designer.md)할 때 자동으로 설정됩니다. |
|**항목** | 포함된 캔버스 앱이 호스트 모델 기반 양식의 레코드에 액세스 할 수 있도록 하는 읽기 전용 속성입니다. <br />예를 들어 이름이 accountnumber이고 표시 이름이 거래처 번호인 필드의 값을 가져오려면 ModelDrivenFormIntegration.Item.accountnumber 또는 ModelDrivenFormIntegration.Item.'Account Number'를 사용할 수 있습니다. |
|**OnDataRefresh** | 이 속성의 수식은 호스트 모델 기반 양식이 데이터를 저장할 때 평가됩니다. <br />이를 사용하여 호스트 모델 기반 양식의 상위 엔터티에 연결된 데이터 소스를 새로 고치고 변수 설정 또는 업데이트와 같은 다른 작업을 수행합니다. <br /> 예를 들어 아래 수식으로 설정하면 계정 데이터 소스가 새로 고쳐지고 CurrentAccountNumber라는 변수가 현재 레코드의 거래처 번호 필드 값으로 설정됩니다. <br /> Refresh(Accounts); Set(CurrentAccountNumber, ModelDrivenFormIntegration.Item.'Account Number') |
|**RefreshForm** | 호스트 모델 기반 양식의 데이터를 새로 고칩니다. <br />자세한 내용은 [호스트 양식에서 미리 정의된 작업 수행](embedded-canvas-app-actions.md#refreshformshowprompt)을 참조하십시오. |
|**SaveForm** | 호스트 모델 기반 양식에 데이터를 저장합니다. <br />자세한 내용은 [호스트 양식에서 미리 정의된 작업 수행](embedded-canvas-app-actions.md#saveform)을 참조하십시오.  |
|**NavigateToMainForm** | 호스트 모델 기반 양식을 기본 양식으로 이동하고 지정된 레코드를 표시합니다. <br />자세한 내용은 [호스트 양식에서 미리 정의된 작업 수행](embedded-canvas-app-actions.md#navigatetomainformentityname-mainformname-recordid)을 참조하십시오. |
|**NavigateToView** | 보려는 호스트 모델 기반 양식으로 이동합니다. <br />자세한 내용은 [호스트 양식에서 미리 정의된 작업 수행](embedded-canvas-app-actions.md#navigatetoviewentityname-viewname)을 참조하십시오.  |
|**OpenQuickCreateForm** | 엔터티에 대한 기본 빨리 만들기 양식을 엽니다.  <br />자세한 내용은 [호스트 양식에서 미리 정의된 작업 수행](embedded-canvas-app-actions.md#openquickcreateformentityname)을 참조하십시오.  |
|**데이터** | 프레임워크에서 호스트 모델 기반 양식의 일부 핵심 데이터를 포함된 캔버스 앱에 보내기 위해 사용하는 읽기 전용 속성입니다.  <br /> 이 속성은 사용하지 마십시오. 항목을 사용하여 호스트 모델 기반 양식에서 레코드에 액세스하십시오.  |

## <a name="see-also"></a>참조
[모델 기반 양식에 캔버스 앱 포함](embed-canvas-app-in-form.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 추가](embedded-canvas-app-add-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱 편집](embedded-canvas-app-edit-classic-designer.md) <br />
[모델 기반 양식에 포함된 캔버스 앱의 화면 크기 및 방향 사용자 지정](embedded-canvas-app-customize-screen.md) <br />
[포함된 캔버스 앱 내에서 호스트 양식에 대한 미리 정의된 작업 수행](embedded-canvas-app-actions.md) <br />
[포함된 캔버스 앱 공유](share-embedded-canvas-app.md) <br />
[포함된 캔버스 앱 작업 지침](embedded-canvas-app-guidelines.md) <br />
[공개 미리 보기 릴리스를 사용하여 만든 모델 기반 양식에 포함된 캔버스 엡을 최신 버전으로 마이그레이션](embedded-canvas-app-migrate-from-preview.md) <br />
