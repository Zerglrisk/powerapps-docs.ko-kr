---
title: 온-프레미스 데이터 게이트웨이 | Microsoft Docs
description: 이 문서는 PowerApps 용 온-프레미스 데이터 게이트웨이에 대 한 개요입니다.
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2019
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 60f8fb3c0c6d28bb30140017c2af07040d5ade7f
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73898208"
---
# <a name="what-is-an-on-premises-data-gateway"></a>온-프레미스 데이터 게이트웨이 란 무엇 인가요?

온-프레미스 데이터 게이트웨이는 온-프레미스 데이터 (클라우드에 없는 데이터)와 여러 Microsoft 클라우드 서비스 간에 빠르고 안전한 데이터 전송을 제공 하는 브리지 역할을 합니다. 이러한 클라우드 서비스에는 Power BI, PowerApps, 파워 자동화, Azure Analysis Services 및 Azure Logic Apps가 포함 됩니다. 조직은 게이트웨이를 사용 하 여 온-프레미스 네트워크에 데이터베이스 및 기타 데이터 원본을 보관할 수 있지만 클라우드 서비스에서 해당 온-프레미스 데이터를 안전 하 게 사용할 수 있습니다.

## <a name="how-the-gateway-works"></a>게이트웨이 작동 방식

![게이트웨이 개요](media/gateway-reference/on-premises-data-gateway.png)

게이트웨이의 작동 방식에 대 한 자세한 내용은 [온-프레미스 데이터 게이트웨이 아키텍처](/data-integration/gateway/service-gateway-onprem-indepth)를 참조 하세요.

## <a name="types-of-gateways"></a>게이트웨이 유형

각각 서로 다른 시나리오에 대 한 두 가지 유형의 게이트웨이가 있습니다.

- **온-프레미스 데이터 게이트웨이** 를 사용 하면 여러 사용자가 여러 온-프레미스 데이터 원본에 연결할 수 있습니다. 단일 게이트웨이 설치를 사용 하 여 지원 되는 모든 서비스와 함께 온-프레미스 데이터 게이트웨이를 사용할 수 있습니다. 이 게이트웨이는 여러 사용자가 여러 데이터 원본에 액세스 하는 복잡 한 시나리오에 적합 합니다.

- **온-프레미스 데이터 게이트웨이 (개인 모드)** 를 사용 하면 한 사용자가 원본에 연결 하 여 다른 사용자와 공유할 수 없습니다. 온-프레미스 데이터 게이트웨이 (개인 모드)는 Power BI 에서만 사용할 수 있습니다. 이 게이트웨이는 사용자가 보고서를 만드는 유일한 사용자 이며 다른 사용자와 데이터 원본을 공유 하지 않아도 되는 시나리오에 적합 합니다.

## <a name="use-a-gateway"></a>게이트웨이 사용

게이트웨이를 사용 하는 네 가지 주요 단계가 있습니다.

1. 로컬 컴퓨터에 [게이트웨이를 다운로드 하 여 설치](/data-integration/gateway/service-gateway-install) 합니다.
2. 방화벽 및 기타 네트워크 요구 사항에 따라 게이트웨이를 [구성](/data-integration/gateway/service-gateway-app) 합니다.
3. 다른 네트워크 요구 사항을 관리 하 고 관리할 수도 있는 [게이트웨이 관리자를 추가](/data-integration/gateway/service-gateway-manage) 합니다.
4. 오류가 발생 한 경우 게이트웨이 [문제를 해결](/data-integration/gateway/service-gateway-tshoot) 합니다.

## <a name="next-steps"></a>다음 단계

- [온-프레미스 데이터 게이트웨이 설치](/data-integration/gateway/service-gateway-install)