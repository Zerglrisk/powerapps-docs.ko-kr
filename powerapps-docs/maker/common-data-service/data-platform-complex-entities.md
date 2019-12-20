---
title: Power Apps 플랜 2 라이선스가 필요한 복합 엔터티 | Microsoft Docs
description: Power Apps 플랜 2 라이선스가 필요한 Common Data Service의 복합 엔터티 목록입니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 09/26/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a87b41fd2688992b85fb4dde36a2e7119f4e7a9f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861254"
---
# <a name="complex-entities-and-licensing"></a>복합 엔터티 및 라이선스

> [!IMPORTANT]
> 이 항목은 최신 버전이 아니며 2019년 10월 1일부터 적용 가능한 최신 라이선스 변경 사항을 반영하여 곧 업데이트될 예정입니다. 엔터티의 라이선스 요구 사항에 대한 최신 정보는 [Power Apps 라이선스 가이드](https://go.microsoft.com/fwlink/?linkid=2085130)를 참조하십시오.

다음과 같은 복잡한 서버 쪽 논리를 포함하는 엔터티에는 이러한 엔터티를 사용하는 앱 또는 흐름 사용자에게 Power Apps 플랜 2 또는 Power Automate 플랜 2 라이선스가 있어야 합니다.

* 코드 플러그 인. 추가 정보: [플러그 인 개발](/powerapps/developer/common-data-service/plug-ins)
* 실시간 워크플로입니다. 추가 정보: [워크플로 프로세스](/flow/workflow-processes)

    > [!IMPORTANT]
    >  실시간 워크플로로 변환된 워크플로만 실시간 및 동기식으로 간주됩니다. 백그라운드에서 실행되는 워크플로는 적절한 Power Apps 플랜에 계속 사용할 수 있으며 추가 라이선스가 필요하지 않습니다.

엔터티에 복잡한 비즈니스 논리를 추가했는지 여부를 확인 하려면 사용자 환경에서 구성된 플러그 인 어셈블리 및 워크플로 목록을 검토합니다.

## <a name="complex-entities-installed-with-dynamics-365-apps"></a>Dynamics 365 앱을 사용하여 설치된 복합 엔터티
다음 표에는 Dynamics 365 Sales 및 Dynamics 365 Customer Service와 같이 Dynamics 365의 모델 기반 애플리케이션 설치의 일부로 기본 제공되는 복잡한 서버 쪽 논리를 포함하는 엔터티가 나와 있습니다. 이 목록은 가이드로 사용됩니다. 사용자 환경에 설치된 Dynamics 365 앱 및 버전에 따라 복합 엔터티 목록이 달라질 수 있습니다.

> [!NOTE]
>  Common Data Service를 사용 중이고 Dynamics 365 애플리케이션 또는 타사 솔루션을 설치하지 않은 경우 환경에 복합 서버 쪽 논리가 포함된 엔터티가 없습니다.

* 거래처
* 계약
* 계약 예약 날짜
* 계약 예약 문제
* 계약 예약 제품
* 계약 예약 서비스
* 계약 예약 서비스 작업
* 계약 예약 설정
* 계약 송장 날짜
* 계약 송장 기재 제품
* 계약 송장 설정
* 계약 하위 상태
* 예약 가능한 리소스
* 예약 가능한 리소스 예약
* 예약 가능한 리소스 예약 머리글
* 예약 가능한 리소스 범주
* 예약 가능한 리소스 범주 연결
* 예약 가능한 리소스 특징
* 예약 가능한 리소스 그룹
* 예약 알림
* 예약 알림 상태
* 예약 상태
* 특징
* 역량 요구 사항(더 이상 사용되지 않음)
* 경쟁 업체
* 연락처
* 고객 자산
* 위임
* 경비
* 필드 계산
* Field Service 가격표 항목
* 필터
* 팔로우
* 문제 유형
* 문제 유형 제품
* 문제 유형 서비스
* 문제 유형 서비스 작업
* 통합 작업
* 통합 작업 세부 정보
* 재고 조정
* 재고 조정 제품
* 재고 이동
* 송장
* 송장 빈도
* 송장 라인
* 송장 라인 세부 정보
* 업무 일지
* 분개장 항목
* 잠재 고객
* 메모
* OData v4 데이터 원본
* 영업 기회
* 영업 기회 라인
* 영업 기회 라인 세부 정보
* 주문
* 주문 송장 발부 제품
* 주문 송장 발부 설정
* 주문 라인
* 지불
* 지불 정보
* 포스트 구성
* 포스트 규칙 구성
* 우편 번호
* 가격표
* 가격표 항목
* 제품
* 프로젝트
* 프로젝트 승인
* 프로젝트 계약 내용 세부 정보
* 프로젝트 계약 내용 이정표
* 프로젝트 계약 내용 리소스 범주
* 프로젝트 계약 내용 거래 범주
* 프로젝트 한도
* 프로젝트 스테이지
* 프로젝트 작업 사용자 상태
* 프로젝트 팀 구성원 등록
* 구매 주문
* 구매 주문 청구서
* 구매 주문 제품
* 구매 주문 영수증
* 구매 주문 영수증 기재 제품
* 구매 주문 하위 상태
* 큐 항목
* 견적
* 견적 예약 문제
* 견적 예약 제품
* 견적 예약 서비스
* 견적 예약 서비스 작업
* 견적 예약 설정
* 견적 송장 발부 제품
* 견적 송장 발부 설정
* 견적 라인
* 견적 라인 세부 정보
* 견적 라인 이정표
* 견적 라인 리소스 범주
* 견적 라인 거래 범주
* 견적 프로젝트 가격표
* 등급 모델
* 등급 값
* 요구 사항 특징
* 요구 사항 리소스 범주
* 요구 사항 리소스 선호 설정
* 요구 사항 상태
* 리소스 요청
* 리소스 요구 사항
* 리소스 요구 사항 세부 정보
* RMA
* RMA 제품
* RMA 영수증
* RMA 영수증 기재 제품
* RMA 하위 상태
* 역할 역량 요구 사항
* 역할 가격
* RTV
* RTV 제품
* RTV 하위 상태
* 세금 코드
* 세금 코드 정보
* 시간 항목
* 시간 그룹
* 시간 그룹 세부 정보
* 휴가 요청
* 거래 범주 가격
* 사용자
* 보기
* 담벼락 보기
* 창고
* 작업 주문
* 작업 주문 문제
* 작업 주문 제품
* 작업 주문 서비스
* 작업 주문 서비스 작업
* 작업 주문 하위 상태
* 작업 템플릿


## <a name="licensing"></a>라이선싱
Power Apps 및 Dynamics 365 라이선스에 대한 자세한 내용은 [라이선스 개요](../../administrator/pricing-billing-skus.md) 페이지를 참조하십시오.

