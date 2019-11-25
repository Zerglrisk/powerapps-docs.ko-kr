---
title: 모델 기반 앱의 지역화 가능한 텍스트 번역 | MicrosoftDocs
description: 여러 언어를 지원하기 위해 지역화 가능한 텍스트를 번역하는 방법 알아보기
ms.custom: ''
ms.date: 06/03/2018
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
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 32e6eb8439cdd5a685f761b1326a0cc891f0e6bb
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754878"
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>모델 기반 앱의 지역화 가능한 텍스트 번역

필드 레이블 또는 드롭다운 목록 값과 같은 엔터티 또는 필드 텍스트를 사용자 지정한 경우 사용자 환경의 기본 언어 버전을 사용하지 않는 환경 내 사용자에게 이러한 사용자 지정된 텍스트를 해당 사용자의 기본 설정 언어로 제공해야 할 수 있습니다. 

프로세스에서 따라야 할 단계는 다음과 같습니다.
1. 사용자 환경에서 다른 언어 활성화
2. 지역화할 텍스트 내보내기
3. 현지화 가능한 텍스트 번역
4. 현지화된 텍스트 가져오기

## <a name="enable-other-languages-for-your-environment"></a>사용자 환경에서 다른 언어 활성화

사용자 환경에 대한 언어를 아직 활성화하지 않은 경우 [언어 활성화](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)에 설명된 단계를 사용하여 활성화합니다.

> [!IMPORTANT]
> 각 언어를 활성화하는 데 몇 분 정도 걸릴 수 있습니다. 이 시간 동안 환경의 다른 사용자가 앱을 사용하지 못할 수 있습니다. 사용자에게 최소한의 지장을 줄 수 있는 시간에 언어를 사용하도록 설정해야 합니다.

> [!TIP]
> 언어를 활성화하는 있는 동안 각 언어에 사용되는 LCID 값을 기록해 둡니다. 이 값은 지역화할 수 있는 텍스트에 대한 내보낸 데이터의 언어를 나타냅니다. 언어 코드는 4-5자리 로캘 ID입니다. 유효한 로캘 ID 값은 [로캘 ID(LCID) 차트](https://go.microsoft.com/fwlink/?LinkId=122128)에서 확인할 수 있습니다.

## <a name="export-the-localizable-text"></a>지역화할 텍스트 내보내기

지역화할 수 있는 지역화 가능한 텍스트의 범위는 지역화 가능한 텍스트를 포함하는 비관리형 솔루션입니다. 이 작업은 솔루션 탐색기를 통해서만 수행할 수 있습니다.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

메뉴 모음에서 지역화할 텍스트를 포함 하는 비관리형 솔루션을 열고 **번역** > **내보내기 번역**을 선택합니다. 

![번역 내보내기](media/export-localizable-text.png)

다음과 같은 경고가 표시됩니다.
> 번역을 위해 사용자 정의 라벨을 내보내는 데 몇 분 정도 걸릴 수 있습니다. 첫 번째 내보내기가 완료될 때까지 내보내기 링크를 다시 클릭하지 마십시오. 이제 내보내시겠습니까? 

계속하려면 **확인**을 클릭합니다.

내보내기가 완료되면 다운로드 폴더에서 같은 `CrmTranslations_{0}_{1}.zip` 이름의 파일을 찾을 수 있습니다. 여기서 `{0}` 솔루션의 고유 이름이고 `{1}`이 솔루션의 버전 번호입니다.

## <a name="get-the-localizable-text-translated"></a>현지화 가능한 텍스트 번역

언어 전문가, 번역 대행사 또는 로컬라이제이션 업체에 이 파일을 보낼 수 있습니다.

텍스트를 번역할 수 있는 지식이 있거나 형식을 확인하려는 경우 내보낸 zip 파일을 추출할 수 있으며 두 개의 XML 파일이 포함되어 있다는 것을 알게 됩니다. 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

Microsoft Office Excel로 CrmTranslations.xml 파일을 열 수 있습니다.

> [!TIP]
> 일반적으로 Excel에서 XML 파일을 열지 않는 한 excel을 연 다음 추출된 CrmTranslations 파일의 경로를 붙여넣어 파일을 열도록 선택하는 것이 더 쉬울 수 있습니다.

> [!IMPORTANT]
> 파일 형식을 변경하지 않았는지 확인하십시오. 다른 형식으로 파일을 저장하는 경우에는 다시 가져올 수 없습니다.

Excel에서 데이터를 볼 때 지역화된 **레이블** 탭을 살펴봅니다.

![지역화를 위해 내보낸 텍스트](media/localized-labels-tab-exported-languages.png)

사용자 지정 엔터티 또는 필드에는 지역화할 수 있는 텍스트에 대한 빈 셀이 있습니다. 해당 항목에 대한 지역화된 값을 추가합니다.

> [!NOTE]
> 표준 엔터티 또는 엔터티 필드에 대한 표시 이름 또는 설명을 변경한 경우 지역화된 문자열에는 원래 값에 대한 번역이 계속 반영됩니다. 새 값을 반영하도록 지역화해야 합니다.

**표시 문자열** 탭에는 리본 명령, 오류 메시지 및 양식 레이블과 같은 다른 UI 요소에 대해 표시되는 텍스트가 포함됩니다.

### <a name="updating-localizable-text-in-the-base-language"></a>기본 언어로 지역화 가능한 텍스트 업데이트

특수 메시지에 포함된 표준 엔터티 또는 엔터티 필드의 표시 이름을 변경 하는 경우 **표시 문자열** 탭의 정보를 업데이트하여 사용자 지정된 이름을 사용할 수 있습니다.

> [!TIP]
> 시스템 엔터티 메시지 편집에 노출된 UI에는 엔터티 이름에 대한 참조가 많이 포함되어 있지만 이를 모두 포함하지는 않습니다. 이 기술을 사용하면 더 많이 찾을 수 있습니다. 추가 정보: [시스템 엔터티 메시지 편집](../common-data-service/edit-system-entity-messages.md)

예를 들어 거래처 엔터티의 표시 이름을 *회사*로 변경하는 경우 **표시 문자열**의 기본 언어 열에서 `account`, `accounts`, `Account` 및 `Accounts` 일치 항목을 검색한 다음 각각 `company`, `companies`, `Company` 및 `Companies`으로 적절하게 대체합니다.

> [!IMPORTANT]
> 이 파일에서 일반 찾기/바꾸기를 수행하지 마십시오. 일치하는 텍스트가 실제로 변경된 이름을 참조하는 주의해야 합니다.


## <a name="import-the-localized-text"></a>현지화된 텍스트 가져오기
텍스트를 가져오려면 파일을 압축하고 시스템으로 가져와야 합니다.

### <a name="compress-the-files"></a>파일 압축

파일을 `CrmTranslations.xml`변경한 후에는 `[Content_Types].xml` 파일을 zip 형식으로 함께 압축해야 합니다. *두 파일* 을 선택한 다음 마우스 오른쪽 버튼을 클릭하여 상황에 맞는 메뉴를 열면 됩니다. 상황에 맞는 메뉴에서 **보내기** > **압축(zip) 폴더**를 선택합니다.

### <a name="import-the-files"></a>파일 가져오기

번역을 내보낸 것과 동일한 비관리형 솔루션에서 메뉴의 **번역** > **번역 가져오기**를 선택합니다. 

![번역 가져오기](media/import-translations.png)

압축하고 번역된 텍스트가 들어있는 파일을 선택하고 **가져오기**를 클릭합니다.

![선택된 파일 가져오기](media/import-translated-text-dialog.png)

번역된 텍스트를 가져온 후에는 모든 사용자 지정 항목을 게시하여 앱의 변경 내용을 확인해야 합니다.

## <a name="community-tools"></a>커뮤니티 도구

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/)는 XrmToolBox 커뮤니티가 개발한 도구입니다. Easy Translator를 사용하여 문맥 정보로 번역을 내보내고 가져옵니다. 

> [!NOTE]
> 커뮤니티 도구는 Microsoft에서 지원되지 않습니다.
> 도구에 대해 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com)


## <a name="next-steps"></a>다음 단계
[조직에 대한 국가별 옵션 및 언어 옵션](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[시스템 엔터티 메시지 편집](../common-data-service/edit-system-entity-messages.md)

