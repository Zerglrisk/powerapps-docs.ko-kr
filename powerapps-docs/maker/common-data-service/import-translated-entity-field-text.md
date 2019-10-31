---
title: PowerApps에서 번역된 엔터티 및 필드 텍스트 가져오기 | MicrosoftDocs
description: 번역된 엔터티 및 필드 텍스트를 가져오는 방법 알아보기
ms.custom: ''
ms.date: 06/19/2018
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
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>앱으로 번역된 엔터티 및 필드 텍스트 다시 가져오기

필드 레이블 또는 드롭다운 목록 값과 같은 엔터티 또는 필드 텍스트를 사용자 지정한 경우 사용자 환경의 기본 언어 버전을 사용하지 않는 조직 내 사용자에게 이러한 사용자 지정된 텍스트를 해당 사용자의 고유 언어로 제공해야 할 수 있습니다. 그러기 위해 사용자 지정 항목의 모든 텍스트 문자열을 내보내 조직에서 사용하는 언어로 번역할 수 있습니다.  
  
 번역 후 사용자가 변경 사항을 활용하려면 번역된 텍스트 문자열을 사용자 환경으로 가져와야 합니다.  
  
> [!IMPORTANT]
> - 가져올 파일은 루트에 CrmTranslations.xml 및 [Content_Types].xml 파일이 포함된 압축된 파일이어야 합니다.  
> - 번역된 텍스트가 500자를 초과하면 가져올 수 없습니다. 번역 파일에 500자를 초과하는 항목이 있으면 가져오기 프로세스가 처리되지 않습니다. 가져오기 프로세스가 실패하면 파일에서 오류의 원인이 된 줄을 검토하고 문자 수를 줄인 다음 가져오기를 다시 시도하십시오. 또한 번역된 텍스트를 가져온 후에는 사용자 지정 항목을 다시 게시해야 합니다.  
  
1. [솔루션 탐색기](../model-driven-apps/advanced-navigation.md#solution-explorer)를 엽니다.  
  
2. 솔루션 탐색기의 작업 도구 모음에서 **번역 가져오기**를 선택합니다.  
3.  **번역된 텍스트 가져오기** 대화 상자에서 변환된 텍스트가 들어 있는 파일을 지정하고 **가져오기**를 선택합니다.  
  
4.  가져오기가 완료되면 **닫기**를 선택합니다.  
  
> [!NOTE]
>  사용자 지정 항목을 게시하는 것은 정상적인 시스템 작동을 방해할 수 있습니다. 사용자에게 가장 지장을 덜 줄 때 게시하는 것이 좋습니다.  

## <a name="community-tools"></a>커뮤니티 도구

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/)는 XrmToolBox 커뮤니티가 PowerApps용으로 개발한 도구입니다. Easy Translator를 사용하여 문맥 정보로 번역을 내보내고 가져옵니다. 

> [!NOTE]
> 커뮤니티 도구는 Microsoft에서 지원되지 않습니다. 도구에 대해 질문이 있으면 게시자에게 문의하십시오. 추가 정보: [XrmToolBox](https://www.xrmtoolbox.com)

## <a name="next-steps"></a>다음 단계  
 [번역을 위해 사용자 지정 엔터티 및 필드 텍스트 내보내기](export-customized-entity-field-text-translation.md)
