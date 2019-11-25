---
title: 포털 인증 구성 | MicrosoftDocs
description: 포털에 대한 인증을 구성하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b285ce6e3a93efb72ed867149ce0740f7ee96579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755318"
---
# <a name="configure-portal-authentication"></a>포털 인증 구성

포털 응용 프로그램에서, 인증된 포털 사용자는 연락처나 시스템 사용자와 연결됩니다. 기본 포털 구성은 연락처를 기반으로 합니다. 로그인하려면 연락처에 적절한 웹 인증 정보가 구성되어 있어야 합니다. 인증되지 않은 사용자 이상의 권한을 얻으려면 포털 사용자가 웹 역할에 할당되어야 합니다. 웹 역할의 권한을 구성하려면 해당 웹 페이지 액세스 및 웹 사이트 액세스 컨트롤 규칙을 구성하십시오.

최신 포털 인증 환경에서는 포털 사용자가 로컬 연락처 구성원 자격 공급자 기반 계정 또는 [ASP.NET ID](https://www.asp.net/identity) 기반 외부 계정 중 선택하여 로그인할 수 있습니다.   

- **로컬 인증**: 로컬 인증은 인증을 위한 Common Data Service 환경의 연락처 레코드를 사용하는 일반적인 양식 기반 인증입니다. 사용자 지정 인증 환경을 만들려는 개발자는 ASP.Net Identity API를 사용하여 사용자 지정 로그인 페이지와 도구를 만들 수 있습니다.
- **외부 인증**: 외부 인증은 ASP.NET Identity API에 의해 제공됩니다. 이 경우 계정 자격 증명 및 암호 관리는 타사 ID 공급자에 의해 처리됩니다. Yahoo! 및 Google과 같은 OpenID 기반 공급자와 Twitter, Facebook 및 [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]와 같은 OAuth 2.0 기반 공급자가 이에 포함됩니다. 사용자는 포털에 등록하기 위해 외부 ID를 선택하여 포털에 등록합니다. 등록되면 외부 ID는 로컬 계정과 동일한 기능에 대한 액세스 권한을 갖습니다. 

로컬 및 외부 계정 등록 모두 이메일 확인 워크플로뿐 아니라 등록 초대 코드를 사용할 수 있습니다. 또한 포털 관리자는 포털 사이트 설정을 통해 인증 옵션의 조합을 사용할지 여부를 선택할 수 있습니다.

> [!NOTE]
> 포털 사용자는 고유한 이메일 주소가 있어야 합니다. 둘 이상의 연락처 레코드(비활성화된 연락처 레코드 포함)에 동일한 전자 메일 주소가 있는 경우 해당 연락처는 포털에서 인증할 수 없습니다.

## <a name="account-sign-up-registration"></a>계정 가입(등록)

포털 관리자에게는 계정 등록 동작을 제어하기 위한 몇 가지 옵션이 있습니다. 열린 등록은 포털에서 단순히 사용자 ID를 제공하여 사용자 계정이 등록되도록 허용하는 최소한의 제한적인 가입 구성입니다. 대체 구성에서는 사용자가 포털에 등록하기 위해 초대 코드나 올바른 이메일 주소를 제공해야 할 수 있습니다. 등록 구성에 관계 없이 로컬 및 외부 계정 모두 등록 워크플로에 동등하게 참여합니다. 즉, 사용자는 등록할 계정 유형을 선택할 수 있습니다.

## <a name="open-registration"></a>열린 등록

등록 과정 중에 사용자가 로컬 계정(사용자 이름 및 암호 제공)을 만들거나 ID 공급자 목록에서 외부 ID를 선택할 수 있습니다. 외부 ID를 선택하면 사용자는 외부 거래처를 소유하고 있음을 증명하기 위해 선택한 ID 공급자를 통해 로그인해야 합니다. 어떤 경우에든, 사용자는 즉시 포털에 등록되고 인증됩니다. 새 연락처 레코드는 가입 시 Common Data Service 환경에서 만들어집니다.

열린 등록이 활성화되면 사용자가 등록 프로세스를 완료하기 위해 초대 코드를 제공할 필요가 없습니다.

### <a name="see-also"></a>참조

[포털의 인증 ID 설정](set-authentication-identity.md)  
