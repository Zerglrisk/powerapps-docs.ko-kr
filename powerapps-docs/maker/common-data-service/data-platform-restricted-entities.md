---
title: Dynamics 365 라이선스가 필요한 제한적 엔터티 | Microsoft Docs
description: Dynamics 365 라이선스가 필요한 Common Data Service의 제한된 엔터티 목록입니다.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cd722c29bfc850cb1b55c296b4e377e14678b3ad
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703518"
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Dynamics 365 라이선스가 요구되는 제한적 엔터티

> [!IMPORTANT]
> 이 항목은 최신 버전이 아니며 2019년 10월 1일부터 적용 가능한 최신 라이선스 변경 사항을 반영하여 곧 업데이트될 예정입니다. 엔터티의 라이선스 요구 사항에 대한 최신 정보는 [PowerApps 라이선스 가이드](https://go.microsoft.com/fwlink/?linkid=2085130)를 참조하십시오.

앱 제조업체는 Common Data Service 내에서 사용 가능한 대부분의 엔터티를 사용하여 PowerApps 플랜 1 라이선스만 있는 사용자를 위한 앱과 흐름을 만들 수 있습니다. 그러나 일부 엔터티에는 앱 사용자에게 PowerApps 플랜 2 또는 Microsoft Flow플랜 2 라이선스가 있어야 하는 복잡한 비즈니스 논리가 포함되어 있습니다(자세한 내용은 [엔터티 라이선스 요구 사항](data-platform-entity-licenses.md) 참조). Dynamics 365 제품에 연결된 더 작은 엔터티 집합에는 엔터티 내에서 레코드를 생성, 업데이트 또는 삭제해야 하는 경우 캔버스 및 모델 기반 앱 사용자에 게 해당 Dynamics 365 제품에 대한 라이선스가 있어야 합니다. 이러한 항목은 *제한된* 엔터티로 참조됩니다.

엔터티는 다음과 같은 이유로 Dynamics 365 라이선스로 제한될 수 있습니다.

* 엔터티는 일반적으로 응용 프로그램 외부에서 사용되지 않는 제품별 구성 데이터를 저장하 고 유지 관리하는 데 사용됩니다.
* 이 엔터티에는 Dynamics 365 제품 내에서 사용될 때 특정 방식으로 데이터를 만들고 유지 관리하는 고급 논리가 수반됩니다.

앱 또는 흐름이 엔터티에서 정보를 읽기만 하는 경우 Dynamics 365 라이선스가 필요하지 않으며 적절한 PowerApps 또는 Microsoft Flow 라이선스가 필요합니다. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>읽기, 만들기, 업데이트 및 삭제 작업 제한 엔터티
다음 표에서는 엔터티 내에 저장된 데이터를 만들거나 업데이트하거나 삭제하는 PowerApps 및 Microsoft Flow 앱 사용자에 대한 제한된 엔터티 및 관련 Dynamics 365 라이선스 요구 사항을 보여줍니다. 

|엔터티  |논리적 이름  |라이선스 필수  |
|---------|---------|---------|
실제 |msdyn_actual |Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
계약 비즈니스 프로세스 |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
예약 분개장 | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
예약 설정 메타데이터 | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
예약 타임스탬프 | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
서비스 케이스 | incident | Dynamics 365 for Customer Service, Enterprise Edition <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
서비스 케이스와 작업 주문 간 비즈니스 프로세스 |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
구성 |msdyn_configuration |Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
권리 유형 | 권리 유형 | Dynamics 365 for Customer Service, Enterprise Edition <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
추정 라인|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
예상|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
사실|msdyn_fact |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
Field Service 설정 |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
Field Service 시스템 작업 |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
목표 | goal | Dynamics 365 for Sales Professional, <br>**또는** Dynamics 365 for Sales, Enterprise Edition, <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
재고 분개장 |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
송장 프로세스 |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
여정 | journey | Dynamics 365 for Marketing <br> **또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
참조 문서 | knowledgearticle | Dynamics 365 for Customer Service, Enterprise Edition <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
조직 구성 단위 |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
제품 재고 |msdyn_productinventory |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
프로젝트 한도|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
프로젝트 스테이지| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
프로젝트 작업 종속성|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
프로젝트 작업|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
프로젝트 팀 구성원|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
구매 주문 비즈니스 프로세스 | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
리소스 할당 세부 정보(더 이상 사용되지 않음)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
리소스 할당|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
리소스 제한(더 이상 사용되지 않음) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
회람 규칙 집합 | routingrule | Dynamics 365 for Customer Service, Enterprise Edition <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
일정 게시판 설정 |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
예약 매개 변수 |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
SLA| sla | Dynamics 365 for Customer Service, Enterprise Edition <br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
시스템 사용자 스케줄러 설정 |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **또는** Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
거래 연결|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
거래 확보 경로|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
거래 유형|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
고유 번호|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
작업 주문 비즈니스 프로세스 |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획
작업 주문 세부 정보 생성 큐(더 이상 사용되지 않음)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**또는** Dynamics 365 Customer Engagement 플랜 <br> **또는** Dynamics 365 계획

## <a name="licensing"></a>라이선싱
PowerApps 및 Dynamics 365 라이선스에 대한 자세한 내용은 [라이선스 개요](../../administrator/pricing-billing-skus.md) 페이지를 참조하십시오.

