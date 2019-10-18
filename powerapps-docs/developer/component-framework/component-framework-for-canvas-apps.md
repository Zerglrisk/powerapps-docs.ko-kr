---
title: Canvas 앱 용 PowerApps 구성 요소 프레임 워크 | Microsoft Docs
description: Canvas 앱에 대 한 코드 구성 요소 만들기
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e1c6b4bad1280bdabf8c27e30396b368276ff10b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347225"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>Canvas 앱 용 PowerApps 구성 요소 프레임 워크

> [!IMPORTANT]
> 이 기능은 아직 실험적 이며 기본적으로 사용 하지 않도록 설정 되어 있습니다. 자세한 내용은 [실험적 및 미리 보기 기능](../../maker/canvas-apps/working-with-experimental.md)을 참조 하세요.

PowerApps 구성 요소 프레임 워크를 사용 하 여 앱 제작자가 앱 또는 앱에서 사용할 코드 구성 요소를 만들 수 있습니다. 추가 정보: [PowerApps 구성 요소 프레임 워크 개요](overview.md) 

이 실험적 미리 보기에서 PowerApps 구성 요소 프레임 워크를 사용 하 여 앱 작성자는 PowerApps CLI 도구를 사용 하 여 코드 구성 요소를 만들고, 디버그 하 고, 가져와 캔버스 앱에 추가할 수 있습니다. 이 실험적 미리 보기에서는 특정 Api만 지원 됩니다. Canvas 앱을 지원 하는지 여부를 확인 하려면 각 API를 확인 하는 것이 좋습니다. 

> [!WARNING]
> 코드 구성 요소에는 Microsoft에서 생성 되지 않을 수 있으며 보안 토큰 및 데이터에 잠재적으로 액세스할 수 있는 코드가 포함 되어 있습니다. 응용 프로그램에 코드 구성 요소를 추가 하는 경우 코드 구성 요소 솔루션이 신뢰할 수 있는 소스에서 온 것인지 확인 합니다.

## <a name="prerequisites"></a>필수 조건

환경에서 PowerApps 구성 요소 기능을 사용 하도록 설정 하려면 시스템 관리자 권한이 필요 합니다.

> [!IMPORTANT]
> 기본적으로 PowerApps 구성 요소 프레임 워크는 모델 기반 앱에 대해 사용 하도록 설정 됩니다.

## <a name="enable-powerapps-component-framework-feature"></a>PowerApps 구성 요소 프레임 워크 기능 사용

응용 프로그램에 코드 구성 요소를 추가 하려면 해당 구성 요소를 사용 하려는 각 환경에서 PowerApps 구성 요소 프레임 워크 기능을 사용 하도록 설정 해야 합니다. 앱 내에서 코드 구성 요소를 사용 하도록 환경을 설정 하려면 다음을 수행 합니다.

1. [PowerApps](https://powerapps.microsoft.com/en-us/)에 로그인합니다.

2. **설정** 아이콘을 선택 하 고 **관리 센터**를 선택 합니다.
    
    ![설정 및 관리 센터](media/select-admin-center-from-settings.png "설정 및 관리 센터") 

3. 이 기능을 사용 하도록 설정할 환경을 선택 하 고 줄임표 ( **...** )를 선택한 다음 **설정**을 선택 합니다.

4. **제품** 탭에서 **기능**을 선택 합니다.

   Powerapps ![구성 요소 프레임 워크]사용(media/enable-pcf-feature.png "powerapps 구성 요소 프레임 워크 사용")

5. 사용 가능한 기능 목록에서 **캔버스 앱 용 PowerApps 구성 요소 프레임 워크**의 스위치를 **켜기** 로 설정 합니다.

6. 이제 코드 구성 요소를 추가 하려는 앱을 열고 **파일**  > **앱 설정** 으로 이동 하 여 **고급 설정**을 선택 합니다.

   Powerapps 구성 요소 ![프레임 워크]구성 요소 사용 powerapps 구성 요소(media/enable-components-for-pcf.png "프레임 워크") 구성 요소 사용
   
7. **실험적 기능** 섹션에서 **구성 요소** 스위치를 **켜기로 전환** 합니다.

## <a name="implementing-code-components"></a>코드 구성 요소 구현

사용자 환경에서 PowerApps 구성 요소 프레임 워크 기능을 사용 하도록 설정한 후에는 코드 구성 요소에 대 한 논리 구현을 시작할 수 있습니다. [샘플 구성 요소 구현](implementing-controls-using-typescript.md) 항목에서는 사용자 지정 논리 및 매니페스트 파일을 구현 하 고, 디버깅 프로세스를 실행 하 고, 솔루션 zip 파일을 만들고, 솔루션을 공용으로 가져오는 코드 구성 요소를 만드는 단계별 프로세스를 보여 줍니다. 데이터 서비스.

> [!NOTE]
> 코드 구성 요소 구현은 모델 기반 앱과 캔버스 앱 (실험적 미리 보기) 모두에 대해 동일 합니다. 유일한 차이점은 코드 구성 요소를 추가 하는 것입니다. 

## <a name="add-components-to-a-canvas-app"></a>캔버스 앱에 구성 요소 추가

> [!NOTE]
> 모델 기반 앱의 필드 또는 엔터티에 코드 구성 요소를 추가 하려면 [모델 기반 앱에 코드 구성 요소 추가](add-custom-controls-to-a-field-or-entity.md) 를 참조 하세요.

Canvas 앱에 코드 구성 요소를 추가 하려면 다음을 수행 합니다.

1. PowerApps Studio로 이동 합니다.
2. 새 캔버스 앱을 만들거나 코드 구성 요소를 추가 하려는 기존 앱을 편집 합니다.

   > [!IMPORTANT]
   > 다음 단계로 진행 하기 전에 솔루션 zip 파일을 이미 Common Data Service로 [가져왔는지](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) 확인 합니다.

3. @No__t_1**구성 요소** **삽입**  > **구성 요소 가져오기**로 이동 합니다. 
 
    구성 ![요소]삽입(media/insert-components-import.png "구성 요소") 삽입

4. **코드 (실험적)** 탭을 선택 하 고 목록에서 구성 요소를 추가한 다음 **가져오기**를 선택 합니다. 그러면 **구성 요소** 메뉴에 샘플 구성 요소가 추가 됩니다.

    ![가져오기 샘플 구성 요소](media/import-component-add-sample-component.png "가져오기 샘플 구성 요소")

5. **구성 요소** 로 이동 하 여 구성 요소를 선택 하 여 앱에 추가 합니다.

   ![샘플 구성 요소]추가(media/add-sample-component-from-list.png "샘플 구성 요소") 추가

## <a name="delete-a-code-component"></a>코드 구성 요소 삭제 

Canvas 앱에서 코드 구성 요소를 삭제 하려면 삭제할 코드 구성 요소를 선택 하 고 메뉴에서 **삭제** 단추를 선택 합니다. 앱에서 코드 구성 요소를 삭제 하면 모든 코드 구성 요소 요소가 앱 및 앱 패키지에서 삭제 됩니다. 

## <a name="update-existing-code-components"></a>기존 코드 구성 요소 업데이트

코드 구성 요소를 업데이트할 때 매니페스트 파일에 *version* 특성을 지정 하 여 최신 변경 내용이 런타임에 반영 되도록 합니다. Canvas 응용 프로그램의 경우 기존 코드 구성 요소를 업데이트할 때 *version* 특성을 업데이트 하지 않아도 됩니다. 기본적으로 canvas 앱은 최신 코드 구성 요소를 선택 하 고 런타임에 표시 합니다. Canvas 앱에는 동일한 구성 요소의 단일 버전만 있을 수 있습니다.

> [!NOTE]
> 기존 코드 구성 요소는 PowerApps Studio에서 앱을 닫거나 다시 열 때만 업데이트 됩니다. 앱을 다시 열면 코드 구성 요소를 업데이트 하 라는 메시지가 표시 됩니다. 코드 구성 요소를 삭제 하거나 코드 구성 요소를 다시 앱에 추가 하면 구성 요소가 업데이트 되지 않습니다.

## <a name="see-also"></a>참고 항목

[PowerApps 구성 요소 프레임 워크 개요](overview.md)<br/>
[샘플 구성 요소 구현](implementing-controls-using-typescript.md)

