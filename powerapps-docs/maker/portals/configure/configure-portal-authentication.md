---
title: 포털 인증 구성 | MicrosoftDocs
description: 포털에 대 한 인증을 구성 하는 방법에 대해 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 12e85a0233ca596fa5daf09a05b111564c2a7a24
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72977959"
---
# <a name="configure-portal-authentication"></a>포털 인증 구성

포털 응용 프로그램에서 인증 된 포털 사용자는 연락처 또는 시스템 사용자와 연결 됩니다. 기본 포털 구성은 연락처 기반입니다. 로그인 하려면 연락처에 적절 한 웹 인증 정보가 구성 되어 있어야 합니다. 인증 되지 않은 사용자 이상의 권한을 얻으려면 포털 사용자를 웹 역할에 할당 해야 합니다. 웹 역할에 대 한 사용 권한을 구성 하려면 해당 웹 페이지 액세스 및 웹 사이트 액세스 제어 규칙을 구성 합니다.

최신 포털 인증 환경을 통해 포털 사용자는 로컬 연락처 구성원 자격 공급자 기반 계정 또는 [ASP.NET Identity](http://www.asp.net/identity)기반으로 하는 외부 계정 중에서 선택 하 여 로그인 할 수 있습니다.   

- **로컬 인증**: 로컬 인증은 인증을 위해 Common Data Service 환경의 연락처 레코드를 사용 하는 일반적인 폼 기반 인증입니다. 개발자는 사용자 지정 인증 환경을 빌드하기 위해 ASP.Net Identity API를 사용 하 여 사용자 지정 로그인 페이지 및 도구를 만들 수 있습니다.
- **외부 인증**: 외부 인증은 ASP.NET Identity API를 통해 제공 됩니다. 이 경우, 계정 자격 증명 및 암호 관리는 타사 id 공급자에 의해 처리 됩니다. 여기에는 Yahoo!와 같은 Openid connect 기반 공급자가 포함 됩니다. Twitter, Facebook, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]등의 Google 및 OAuth 2.0 기반 공급자를 제공 합니다. 사용자는 포털에 등록할 외부 id를 선택 하 여 포털에 등록 합니다. 등록 된 외부 id는 로컬 계정과 동일한 기능에 액세스할 수 있습니다. 

로컬 및 외부 계정 등록 모두 등록을 위한 초대 코드와 전자 메일 확인 워크플로를 사용할 수 있습니다. 또한 포털 관리자는 포털 사이트 설정을 통해 인증 옵션의 조합을 사용 하거나 사용 하지 않도록 선택할 수 있습니다.

> [!NOTE]
> 포털 사용자에 게는 고유한 전자 메일 주소가 있어야 합니다. 두 개 이상의 연락처 레코드 (비활성화 된 연락처 레코드 포함)에 동일한 전자 메일 주소가 있는 경우 연락처는 포털에서 인증할 수 없습니다.

## <a name="account-sign-up-registration"></a>계정 등록 (등록)

포털 관리자는 계정 등록 동작을 제어 하기 위한 몇 가지 옵션을 사용할 수 있습니다. 등록 열기는 포털에서 사용자 id를 제공 하 여 사용자 계정을 등록할 수 있는 최소 제한적 등록 구성입니다. 대체 구성에서는 사용자가 포털에 등록할 초대 코드 또는 유효한 전자 메일 주소를 제공 해야 할 수 있습니다. 등록 구성에 관계 없이 로컬 계정과 외부 계정은 모두 등록 워크플로에 동일 하 게 참여 합니다. 즉, 사용자는 등록할 계정 유형을 선택할 수 있습니다.

## <a name="open-registration"></a>등록 열기

등록 하는 동안 사용자에 게는 로컬 계정 (사용자 이름 및 암호 제공)을 만들거나 id 공급자 목록에서 외부 id를 선택 하는 옵션이 있습니다. 외부 id를 선택 하는 경우 사용자는 외부 계정을 소유 하 고 있음을 증명 하기 위해 선택한 id 공급자를 통해 로그인 해야 합니다. 두 경우 모두 사용자를 즉시 등록 하 고 포털에 인증 합니다. 등록할 때 Common Data Service 환경에 새 연락처 레코드가 만들어집니다.

오픈 등록을 사용 하도록 설정 하면 사용자가 등록 프로세스를 완료 하는 초대 코드를 제공할 필요가 없습니다.

### <a name="see-also"></a>참고 항목

[포털에 대 한 인증 id 설정](set-authentication-identity.md)  
