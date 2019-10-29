---
title: Azure storage 웹 리소스를 양식에 추가 | MicrosoftDocs
description: Azure storage 웹 리소스를 양식에 추가 하 여 Azure Storage에 첨부 파일을 업로드할 수 있도록 하는 단계입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ed1053c758f97234ad94a09832683ff00ef17744
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977568"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>양식에 Azure Storage 웹 리소스 추가

Common Data Service에 직접 업로드 하는 대신 Azure Storage에 업로드 된 첨부 파일은 Common Data Service 메모를 사용 하 여 관리할 수 있습니다.

특정 양식의 첨부 파일이 Azure Storage에 업로드 되도록 하려면 해당 양식에 웹 리소스를 추가 하 고 [조직에 대 한 Azure Storage를 구성](enable-azure-storage.md)해야 합니다.

> [!Note]
> 이 예제에서 폼은 잠재 고객 엔터티의 리드 폼에 추가 됩니다. 기존 폼을 편집할 때는 주의 해야 합니다.

파일 (예: 첨부 파일 .zip)이 포털을 사용 하 여 Azure Storage에 업로드 되 면 해당 파일은 엔터티에 대 한 메모 및 첨부 파일에 대 한 자리 표시자로 표시 됩니다.

폼(media/notes-attachment-lead-form.png "의 첨부 파일에 대 한 양식 자리 표시자") ![의 첨부 파일]

첨부 파일의 이름은 이제 첨부 파일 .zip .txt입니다. 기본적으로 Common Data Service에는 Azure 파일의 conception가 없으므로이 자리 표시자 .txt 파일이 Common Data Service에 대신 저장 됩니다. 자리 표시자 파일의 Azure Storage 컨텍스트는 파일에 대 한 세부 정보를 표시 합니다.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Azure에 저장 된 파일을 확인 하 고 상호 작용 하려면 웹 리소스를 폼에 추가 해야 합니다. 필수 구성 요소로 서 사용자에 게 adx_setting에 대 한 읽기 권한이 있는지 확인 합니다. 그렇지 않으면 웹 리소스가 제대로 렌더링 되지 않습니다.

1. 관련 폼의 폼 편집기에서 **삽입** 탭의 **웹 리소스** 를 선택 합니다.

2. **웹 리소스** 상자에서 **adx_annotations/adx.** annotation을 선택 합니다.

3. 리소스의 이름과 레이블을 입력 합니다.

4. **사용자 지정 매개 변수 (데이터)** 상자에 **azureenabled = true**를 입력 합니다. <br>이러한 방식으로 Azure 지원을 사용 하지 않고 웹 리소스를 사용할 수도 있습니다 .이 경우에는 기본 컨트롤과 거의 완전히 동일 하 게 작동 합니다.</br>

5. **서식** 탭에서 선호 하는 모든 서식 지정 규칙을 선택 합니다. **테두리 표시** 확인란의 선택을 취소 하는 것이 좋습니다.

6. **확인** 을 선택 하 여 리소스를 저장 합니다.

7. 필요에 따라 기존 메모 컨트롤을 제거 하거나 기본적으로 표시 되지 않는 탭 또는 섹션으로 이동할 수 있습니다.

8. 폼을 저장 하 고 변경 내용을 게시 합니다.

   웹 ![리소스 추가](media/add-web-resource.png "웹 리소스 추가")

이제 새 컨트롤이 페이지에서 렌더링 되므로 Azure Storage에서 첨부 파일을 관리할 수 있습니다.

![](media/azure-file-attachment-lead-form.png "양식의") azure 파일 첨부 파일 양식의 azure 파일 첨부 파일

용지 클립 아이콘이이 파일이 Azure Storage에 저장 되었음을 나타내는 클라우드 아이콘으로 대체 되었습니다. Common Data Service에 첨부 파일을 계속 저장할 수 있습니다. 이러한 파일에는 용지 클립 아이콘이 표시 됩니다.

> [!Note]
> 다음과 같이 Azure Storage 계정에 CORS (크로스-원본 자원 공유) 규칙을 추가 해야 합니다. 그렇지 않으면 클라우드 아이콘이 아닌 일반 첨부 파일 아이콘이 표시 됩니다.
> - **허용 된 원본**: 도메인을 지정 합니다. 예를 들면 contoso.crm.dynamics.com입니다.
> - **허용 되는 동사**: GET, PUT, DELETE, HEAD, POST
> - **허용 되는 헤더**: 원본 도메인이 CORS 요청에서 지정할 수 있는 요청 헤더를 지정 합니다. 예를 들면, x-m a s-메타 데이터\*, x m a 메타 대상\*입니다. 이 시나리오의 경우 *를 지정 해야 합니다. 그렇지 않으면 웹 리소스가 제대로 렌더링 되지 않습니다.
> - **노출 된 헤더**: CORS 요청에 대 한 응답으로 보낼 수 있고 브라우저에서 요청 발급자에 게 노출 될 수 있는 응답 헤더를 지정 합니다. 예를 들면 x-m a s-meta\*입니다.
> - **최대 기간 (초)**: 브라우저가 실행 전 옵션 요청을 캐시 해야 하는 최대 시간을 지정 합니다. 예를 들면 200입니다.
> 
> [Azure Storage 서비스에 대 한 CORS 지원](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)[!include[More information](../../includes/proc-more-information.md)] 합니다.

첨부 된 파일이 이미지인 경우이 컨트롤은 Common Data Service 또는 Azure Storage에 저장 되어 있는지 여부에 관계 없이 이미지를 미리 보기로 표시 합니다.

> [!Note]
> 축소판 이미지는 크기가 1mb 미만으로 제한 됩니다.

![노트 축소판 그림](media/notes-thumbnail.png "노트 축소판 그림")

## <a name="cors-protocol-support"></a>CORS 프로토콜 지원

[CORS (크로스-원본 자원 공유)](http://www.w3.org/TR/cors/) 프로토콜은 응답을 다른 도메인과 공유할 수 있는지 여부를 나타내는 헤더 집합으로 구성 됩니다.
다음 사이트 설정은 CORS를 구성 하는 데 사용 됩니다.

|                 이름                  |                                                                            설명                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/액세스 제어-허용-자격 증명 | 이 헤더에 대 한 유효한 값은 true (대/소문자 구분)입니다. 자격 증명이 필요 하지 않은 경우 해당 값을 false로 설정 하는 대신이 헤더를 완전히 생략 합니다. |
|   HTTP/액세스 제어-허용 헤더   |                                                   지원 되는 HTTP 요청 헤더의 쉼표로 구분 된 목록입니다.                                                   |
|   HTTP/액세스 제어-허용 메서드   |                                      GET, POST, OPTIONS와 같은 허용 되는 HTTP 요청 메서드를 쉼표로 구분한 목록입니다.                                       |
|   HTTP/액세스 제어-허용-원본    |                   리소스에 액세스 하는 모든 리소스를 허용 하려면 \*지정할 수 있습니다. 그렇지 않으면 리소스에 액세스할 수 있는 URI를 지정 합니다.                   |
|  HTTP/액세스 제어-헤더   |                리소스가 사용할 수 있고 노출 될 수 있는 단순한 응답 헤더를 제외한 쉼표로 구분 된 HTTP 헤더 이름 목록입니다.                 |
|      HTTP/Access 컨트롤-최대 사용 기간      |                                                       결과를 캐시할 수 있는 최대 시간 (초)입니다.                                                        |
|                                       |                                                                                                                                                                   |

