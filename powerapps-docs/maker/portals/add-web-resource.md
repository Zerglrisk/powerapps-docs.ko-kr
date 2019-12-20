---
title: 양식에 Azure Storage 웹 리소스 추가 | MicrosoftDocs
description: Azure Storage에 첨부를 업로드할 수 있도록 양식에 Azure Storage 웹 리소스를 추가하는 단계입니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 873f2054856e21b7fbf56247a4234ae2fb2a72c9
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "2816478"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>양식에 Azure 저장소 웹 리소스 추가

바로 Common Data Service에 업로드하지 않고 Azure Storage에 업로드된 첨부 파일은 Common Data Service의 메모를 사용하여 관리할 수 있습니다.

특정 양식의 첨부 파일을 Azure Storage에 업로드하려면, 해당 양식에 웹 리소스를 추가해야 하고 [조직을 위한 Azure Storage를 구성](enable-azure-storage.md)해야 합니다.

> [!Note]
> 이 예에서는 잠재 고객 엔터티의 잠재 고객 양식에 양식이 추가됩니다. 기존 양식을 편집할 때는 주의하는 것이 좋습니다.

포털을 사용하여 파일(예: attachments.zip)을 Azure Storage에 업로드하면, 첨부 파일의 엔터티와 자리 표시자에 대한 메모가 표시됩니다.

![양식의 첨부 파일](media/notes-attachment-lead-form.png "양식의 첨부 파일 자리 표시자")

첨부 파일은 이제 attachment.zip.txt로 명명됨에 유의하십시오. 기본적으로 Common Data Service에는 Azure 파일이라는 개념이 없으므로, 대신 이 자리 표시자 .txt 파일은 Common Data Service에 저장됩니다. 이 자리 표시자 파일의 Azure Storage 컨텍스트는 파일에 대한 세부 정보를 표시합니다.
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Azure에 저장된 파일을 보고 상호 작용하려면, 양식에 웹 리소스 adx.annotations.html을 추가해야 합니다. 필수 조건으로 사용자에게 adx_setting에 대한 읽기 권한이 있는지 확인합니다. 그렇지 않으면 웹 리소스가 제대로 렌더링되지 않습니다.

1. 관련 양식의 양식 편집기에서, **삽입** 탭의 **웹 리소스**를 선택합니다.

2. **웹 리소스** 상자에서 **adx_annotations/adx.annotations.html**을 선택합니다.

3. 리소스의 이름과 레이블을 입력합니다.

4. **맞춤 항목(데이터)** 상자에 **azureEnabled=true**를 입력합니다. <br>Azure 지원을 이 방식으로 활성화하지 않고도 웹 리소스를 사용할 수 있는데, 그 경우에는 기본 컨트롤과 거의 완전히 동일하게 기능합니다.</br>

5. **포맷팅** 탭에서 선호하는 포맷팅 규칙을 선택합니다. **테두리 표시** 확인란의 선택을 취소하는 것이 좋습니다.

6. **확인**을 선택하여 리소스를 저장합니다.

7. 필요에 따라 기존 메모 컨트롤을 제거하거나 기본적으로 표시되지 않는 것으로 표시된 탭 또는 섹션으로 이동할 수도 있습니다.

8. 양식을 저장한 다음, 변경 내용을 게시합니다.

   ![웹 리소스 추가](media/add-web-resource.png "웹 리소스 추가")

이제 페이지에 새 컨트롤이 렌더링되므로 Azure Storage의 첨부 파일을 관리할 수 있습니다.

![양식의 Azure 파일 첨부](media/azure-file-attachment-lead-form.png "양식의 Azure 파일 첨부")

페이퍼클립 아이콘이 클라우드 아이콘으로 대체되어 이 파일이 Azure Storage에 저장되었음을 나타냅니다. 계속해서 Common Data Service에 첨부 파일을 저장할 수 있습니다; 그러한 파일은 페이퍼클립 아이콘으로 표시됩니다.

> [!Note]
> 또한 Azure Storage 계정에서 원본 간 리소스 공유(CORS) 규칙을 추가해야 하며 그렇지 않으면 클라우드 아이콘이 아닌 일반 첨부 아이콘이 표시됩니다.
> - **허용되는 원본**: 도메인을 지정합니다. `http://contoso.crm.dynamics.com`을 예로 들 수 있습니다.
> - **허용되는 동사:** GET, PUT, DELETE, HEAD, POST
> - **허용되는 헤더**: 원본 도메인이 CORS 요청에 지정할 수 있는 요청 헤더를 지정합니다. 예를 들어 x-ms-meta-data\*, x-ms-meta-target\*입니다. 이 시나리오에서는 *를 지정해야 하며 그렇지 않으면 웹 리소스가 제대로 렌더링되지 않습니다.
> - **노출되는 헤더**: CORS 요청에 응답하여 전송되고 브라우저에서 요청 발급자에게 노출되는 응답 헤더를 지정합니다. 예를 들어 x-ms-meta-\*입니다.
> - **최대 기간(초)**: 브라우저에서 사전 OPTIONS 요청을 캐시해야 하는 최대 시간을 지정합니다. 예를 들면 200입니다.
> 
> [!include[More information](../../includes/proc-more-information.md)] [Azure 저장소 서비스를 위한 CORS 지원](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services).

첨부 파일이 이미지인 경우, 이미지가 Common Data Service 또는 Azure Storage에 저장되어 있는지 여부에 따라 컨트롤은 이미지를 미리 보기로 표시합니다.

> [!Note]
> 썸네일 기능은 크기가 1 MB 미만의 이미지로 제한됩니다.

![메모 미리 보기](media/notes-thumbnail.png "메모 미리 보기")

## <a name="cors-protocol-support"></a>CORS 프로토콜 지원

[원본 간 리소스 공유(CORS)](https://www.w3.org/TR/cors/) 프로토콜은 응답을 다른 도메인과 공유할 수 있는지의 여부를 표시하는 머리글 집합으로 구성됩니다.
CORS를 구성하기 위해 다음 사이트 설정값이 사용됩니다.

|                 이름                  |                                                                            설명                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/액세스-제어-허용-자격 증명 | 이 머리글의 유일한 유효 값은 true(대/소문자 구분)입니다. 자격 증명이 필요하지 않은 경우에는 그 값을 false로 설정하는 대신 이 머리글을 완전히 생략합니다. |
|   HTTP/액세스-제어-허용-머리글   |                                                   지원되는 HTTP 요청 머리글의 쉼표로 구분된 목록.                                                   |
|   HTTP/액세스-제어-허용-방법   |                                      GET, POST, OPTIONS 같은 허용되는 HTTP 요청 방법의 쉼표로 구분된 목록.                                       |
|   HTTP/액세스-제어-허용-기원    |                   어떤 리소스든지 귀하의 리소스에 액세스하는 것을 허용하기 위해 \*를 지정할 수 있습니다. 그렇지 않으면 리소스에 액세스할 수 있는 URI를 지정합니다.                   |
|  HTTP/액세스-제어-노출-머리글   |                리소스가 사용할 수 있고 노출할 수 있는 간단한 응답 헤더가 아닌 HTTP 헤더 이름의 쉼표로 구분된 목록.                 |
|      HTTP/액세스-제어-최대-시간      |                                                       결과를 캐싱할 수 있는 최대 시간(초).                                                        |
|                                       |                                                                                                                                                                   |

