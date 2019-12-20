---
title: 메타데이터 번역 가져오기 | MicrosoftDocs
description: 메타데이터 변환을 가져오는 지침입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6e1f577e5097aead282b6da9338acfd5d1f36364
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862630"
---
# <a name="import-metadata-translation"></a>메타데이터 번역 가져오기

포털을 프로비전하는 경우 포털 관련 솔루션이 조직에 설치됩니다. 솔루션을 설치하는 동안 솔루션 메타데이터 번역(예: 필드 이름, 양식 이름, 보기 이름)은 현재 조직에서 활성화된 언어에 대해서만 설치됩니다. 나중에 새 언어를 활성화하면 새로 활성화된 언어에 대한 메타데이터가 자동으로 설치되지는 않습니다. 새로 활성화된 언어의 메타데이터 번역을 가져오려면 Power Apps 관리 센터에서 메타데이터 번역을 가져와야 합니다.

## <a name="to-import-metadata-translation"></a>메타데이터 번역 가져오기

1.  [Power Apps 포털 관리 센터](admin-overview.md)를 엽니다.

2.  **포털 작업** > **최신 메타데이터 번역 가져오기**로 이동합니다. 포털 솔루션을 업데이트할지의 여부를 묻는 확인 창이 표시됩니다.

3.  **업데이트**를 선택합니다. 포털 솔루션이 최신 메타데이터 번역으로 업데이트됩니다.

> [!Note]
> - 최신 버전의 포털 패키지를 사용할 수 있는 경우에는 업데이트되지 않습니다. 포털 솔루션은 동일한 버전에서 업데이트됩니다. 제공되는 최신 패키지를 기반으로 포털 솔루션을 업그레이드하려면 솔루션 관리 센터에 액세스해야 합니다.
> - 사용자가 Common Data Service에 있는 데이터를 수정한 경우, 업데이트 중에 기존 데이터를 덮어쓰지 않습니다.
> - 포털 솔루션을 설치하고 있는 경우 솔루션 업데이트를 트리거할 수 없습니다.