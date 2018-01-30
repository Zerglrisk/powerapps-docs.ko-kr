---
title: "PowerApps의 일반적인 문제 및 해결 방법 | Microsoft Docs"
description: "PowerApps의 문제 및 해결 방법 읽기"
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/08/2017
ms.author: sharik
ms.openlocfilehash: b359a4f5dcc930b344ded68d5ffcd3ae72c007c6
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2018
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>PowerApps의 일반적인 문제 및 해결 방법
## <a name="recently-addedchanged"></a>최근에 추가/변경된 내용
1. **데이터 테이블 컨트롤**

    **Items** 속성이 **Filter** 함수가 포함된 수식으로 설정된 **데이터 테이블** 컨트롤을 복사하여 붙여넣으면, 새 **데이터 테이블** 컨트롤의 **Items** 속성에 대한 수식은 **_1** 접미사가 포함된 필드 이름으로 끝납니다. 그러면 필드 이름이 유효하지 않게 되어 데이터 테이블에 데이터가 표시되지 않습니다. 이 문제를 해결하려면 컨트롤을 복사하기 전에 **Filter** 함수가 **데이터 테이블** 컨트롤의 열과 이름이 동일한 데이터 원본의 필드를 참조하지 않는지 확인합니다. 그런 경우에는 **데이터 테이블** 컨트롤에 포함된 열의 이름을 변경합니다. 아니면, 엔터티의 이름과 일치하도록 잘못된 필드 이름에서 **_1** 접미사를 제거합니다.

1. **Windows용 PowerApps Studio의 카메라 컨트롤**

    카메라 컨트롤을 추가하거나 카메라 컨트롤을 사용하는 앱을 열 경우 Windows용 PowerApps Studio가 충돌할 수 있습니다. 이 문제를 방지하려면 카메라 컨트롤을 추가하거나 사용할 때 [웹용 PowerApps Studio](create-app-browser.md)를 사용하세요.

2. **Android 장치의 릴리스 2.0.700**

    Android 장치에 릴리스 2.0.700을 설치한 후 앱을 열 수 없는 경우(또는 앱이 응답을 멈춘 경우) PowerApps를 제거하고 장치를 다시 시작한 후 PowerApps를 다시 설치하세요.

3. **앱을 열 때 “빈” 갤러리**

    데이터에서 앱을 자동으로 생성하고 앱을 저장한 다음 다시 열면 갤러리 찾아보기에 데이터가 즉시 표시되지 않을 수 있습니다. 이 문제를 해결하려면 검색 상자에 문자를 하나 이상 입력한 다음 입력한 텍스트를 삭제하십시오. 그러면 갤러리에 데이터가 예상대로 표시됩니다.

4. **Windows 8.1에서 PowerApps 업그레이드**

    Windows 8 또는 Windows 8.1을 실행하는 컴퓨터에서 PowerApps를 설치하는 경우 Windows 스토어 앱을 열어 활성 상태로 유지하고 설정 아이콘을 사용하여 업데이트를 확인한 다음 설치합니다.

5. **Common Data Service의 사용자 지정 커넥터**

   PowerApps 2.0.540 이전 버전을 사용하여 만든 앱이 Common Data Service의 데이터베이스 및 다른 환경에서 하나 이상의 사용자 지정 커넥터를 사용하는 경우, 데이터베이스와 동일한 환경에 커넥터를 배포하고 새로운 커넥터를 사용하도록 앱을 업데이트해야 합니다. 그렇지 않으면 API를 찾을 수 없는 사용자에게 대화 상자를 통해 알려 줍니다. 자세한 내용은 [환경 개요](environments-overview.md)를 참조하세요.

6. **Windows 8.1에서 앱 실행**

    [이 Windows 8.1용 업데이트](https://technet.microsoft.com/library/security/ms16-118)를 설치하는 경우 해당 운영 체제에서 PowerApps Studio로 여는 앱을 실행할 수 없습니다. 하지만 [powerapps.com](https://web.powerapps.com) 또는 PowerApps Mobile로 여는 앱은 실행할 수 있습니다.

7. **공백이 포함된 열 이**

    열 이름에 공백이 포함된 SharePoint 목록 또는 Excel 테이블을 사용하는 경우 PowerApps에서 공백이 **"\_x0020\_"**으로 바뀝니다. 예를 들어 SharePoint 또는 Excel의 **"Column Name"**은 데이터 레이아웃에 표시되거나 수식에 사용될 때 PowerApps에 **"Column_x0020_Name"**으로 나타납니다.

## <a name="older"></a>이전 버전
1. **공유 앱의 흐름 변경**

    앱에 흐름을 추가하여 공유한 다음 서비스를 추가하거나 흐름에서 연결을 변경하는 경우, 공유 앱에서 흐름을 제거하고 흐름을 다시 추가한 다음 앱을 다시 공유해야 합니다. 그렇지 않으면 흐름을 트리거하는 사용자가 인증에 실패하게 됩니다.

2. **지역화 버전 사용**.

    Windows 8.1에서 릴리스 2.0.531을 실행하는 경우 장치가 IME 창이 필요한 언어로 설정되어 있으면 **텍스트 입력** 컨트롤로 입력할 수 없습니다.

3. **Windows Phone에서 카메라 컨트롤**

    카메라 컨트롤을 포함하는 앱은 빌드 10.0.10586.107이 실행 중인 Windows Phone에서 앱을 열면 중단될 수 있습니다. 이 문제를 방지하려면 최신 빌드로 업그레이드하십시오(예: [Upgrade Advisor](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4)를 실행).

4. **템플릿에 앱을 엽니다**.

    릴리스 2.0.500을 실행 중인 경우 템플릿에서 앱을 만들려고 시도하면 오류 메시지가 나타납니다. 이 기능을 사용하려면 업그레이드해야 합니다.

    릴리스 2.0.510 이상을 실행 중인 경우 템플릿에서 앱을 만들려고 시도하면 경고 메시지가 나타날 수 있습니다. 단, 해당 메시지를 닫고 앱을 만들 수 있습니다.

5. **바코드 스캔**

    **바코드** 컨트롤 사용에 관련하여 제한 사항과 모범 사례에 대한 내용은 [바코드 스캔](scan-barcode.md)을 참조하세요.

6. **브라우저에서 앱 만들고 수정**

    Windows용 PowerApps Studio에서와 마찬가지로 웹용 PowerApps Studio에서도 동일한 작업을 많이 수행할 수 있지만 일부는 사용할 수 없습니다. 자세한 내용은 [브라우저에서 앱 만들기](create-app-browser.md)를 참조하세요.

7. **엔터티의 제목 필드 변경**

    하나 이상의 조회로 다른 엔터티를 참조하는 엔터티에 대한 제목 필드를 변경할 경우 변경 내용을 저장하려고 할 때 오류가 발생합니다. 이 문제를 해결하려면 제목 필드의 변경을 원하는 엔터티에서 모든 조회를 제거하고, 변경한 다음 해당 조회를 다시 만듭니다. 조회에 대한 자세한 내용은 [엔터티 간의 관계 구성](data-platform-entity-lookup.md)을 참조하세요.

8. **온-프레미스 SharePoint에 연결하는 앱**

    자동으로 공유되지 않는 연결에 의존하는 앱을 공유하는 경우(예: 온-프레미스 SharePoint 사이트) 브라우저에서 이 앱을 연 사용자가 **로그인**을 클릭하거나 탭하면 텍스트가 없는 대화 상자가 나타납니다. 대화 상자를 닫으려면 오른쪽 위 모서리에 있는 닫기 (X) 아이콘을 클릭하거나 탭합니다. PowerApps Studio 또는 PowerApps Mobile에서 앱을 열면 대화 상자가 표시되지 않습니다. 공유 연결에 대한 자세한 내용은 [앱 리소스 공유](share-app-resources.md)를 참조하세요.

9. **PowerApps는 데이터에서 앱을 생성할 때 정렬 및 검색에 사용된 필드를 자동으로 구성하지 않습니다**.

   이 필드를 구성하려면 [갤러리 추가](add-gallery.md)의 필터링 및 정렬에 대한 섹션에서 설명하는 대로 해당 갤러리에 대한 **[항목](controls/properties-core.md)** 수식을 편집합니다.

10. **데이터에서 만들어진 앱의 경우 데이터 원본 중 500개의 레코드에만 액세스할 수 있습니다**.

     일반적으로 PowerApps는 해당 데이터 원본에 수행할 작업을 위임하는 방식으로 모든 크기의 데이터 원본을 사용하여 작동합니다. PowerApps는 위임이 불가한 작업의 경우 작성 시 경고 메시지를 표시하고 해당 데이터 원본 중 최초 500개의 레코드에서만 작업을 수행합니다.  위임에 대한 자세한 내용은 [Filter 함수](functions/function-filter-lookup.md) 문서를 참조하세요.

11. **Excel 데이터는 표 형식으로 작성되어야 합니다**.

     Excel을 데이터 원본으로 사용할 때의 제한 사항에 대한 내용은 [클라우드 저장소 연결](connections/cloud-storage-blob-connections.md#known-limitations)을 참조하세요.

12. **SharePoint 사용자 지정 목록은 있지만 라이브러리, 목록 열의 일부 유형, 또는 여러 개의 값이나 선택 영역을 지원하는 열은 지원되지 않습니다**.

     자세한 내용은 [SharePoint Online](connections/connection-sharepoint-online.md#known-issues)을 참조하세요.

13. **공동 작성은 지원되지 않습니다. 한 번에 한 명의 작성자만 작성하세요**.

     여러 명이 동시에 수정하면 앱이 손상되거나 다른 사용자의 변경 내용으로 작성될 수 있습니다. 다른 사용자가 편집하기 전에 앱을 닫습니다.

14. **새로 공유한 앱을 사용하려면 시간이 다소 소요될 수 있습니다**.

     새로 공유한 앱은 경우에 따라서 바로 사용하기 힘들 수 있습니다. 몇 분 정도 기다린 다음 사용해야 합니다.

15. **[양식 컨트롤](controls/control-form-detail.md)의 경우 사용자 지정 카드를 사용하여 데이터를 변경할 수 없습니다**.

     주식형 사용자 지정 카드는 **[업데이트](controls/control-card.md)** 속성이 없어 변경 내용을 다시 작성해야 합니다. 이 문제의 해결 방법:

    * 양식 컨트롤을 선택하고, 카드를 표시하려는 필드의 오른쪽 창을 사용하여 카드를 삽입합니다.  
    * [데이터 카드 이해](working-with-cards.md#unlock-a-card)에서 설명하는 대로 해당 카드를 잠금 해제합니다.
    * 사용자 지정 카드와 마찬가지로 필요에 따라 카드 내의 컨트롤을 제거하거나 다시 정렬합니다.

16. **Android 5.0에서 실행 중인 앱은 웹 보기 버전 v48 또는 v49이 있는 Nexus 6와 충돌할 수 있습니다**.

     사용자는 웹 보기의 낮은 버전(3x)으로 또는 Android 6.0으로 업데이트하여 이 문제를 해결할 수 있습니다.

17. **메모리가 부족하면 카메라의 사용이 일시적으로 비활성화될 수 있습니다**.

     카메라는 모바일 장치에 메모리가 부족하면 해당 장치와의 충돌을 방지하기 위해 일시적으로 비활성화됩니다.

18. **Office 365 비디오 커넥터는 지원되지 않습니다**.

19. **카드 갤러리는 사용되지 않습니다**.

     기존 앱에서 이 기능을 사용하면 당분간은 계속 실행되지만 카드 갤러리는 추가할 수 없습니다. 카드 갤러리를 새로운 **[편집 양식](controls/control-form-detail.md)** 및 **[양식 표시](controls/control-form-detail.md)** 컨트롤로 대체하세요.
