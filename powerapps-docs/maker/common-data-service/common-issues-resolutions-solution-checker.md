---
title: 솔루션 검사기에 대한 일반적인 문제 및 해결 방법 | Microsoft Docs
description: ' 솔루션 검사기 내의 일반적인 문제 및 해결 방법 목록'
keywords: ''
ms.date: 02/11/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>솔루션 검사기에 대한 일반적인 문제 및 해결 방법

이 문서에서는 솔루션 검사기를 사용하는 동안 발생할 수 있는 몇 가지 일반적인 문제를 나열합니다. 해당되는 경우 해결 방법이 제공됩니다.

## <a name="solution-checker-runs-fail-due-to-powerapps-checker-version-installed"></a>PowerApps 검사기 버전 설치로 인해 솔루션 검사기가 실행되지 않음
솔루션 검사기는 PowerApps 검사기 솔루션에 포함된 기능입니다.  1.0.0.47 이전의 PowerApps 검사기 버전이 있는 경우 솔루션 검사기 실행이 성공적으로 완료되지 않습니다. [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)]에서 PowerApps 검사기 버전을 업그레이드해야 합니다. 

그러나 PowerApps 검사기 버전이 설치된 1.0.0.45 보다 이전 버전인 경우에는 솔루션을 삭제하고 다시 설치하는 것이 좋습니다. 최근의 스키마 변경으로 인해 1.0.0.45 이전 버전의 PowerApps 검사기 업그레이드가 실패할 수 있습니다.

솔루션 검사기의 과거 결과를 유지하려면 이전 실행의 결과를 내보내거나 데이터 [Excel로 데이터 내보내기](../../user/export-data-excel.md)를 사용하여 모든 솔루션 검사기 데이터를 내보내 다음 엔터티에서 데이터를 내보냅니다.

- 분석 구성 요소
- 분석 작업
- 분석 결과
- 분석 결과 세부 정보

### <a name="delete-powerapps-checker"></a>PowerApps 검사기 삭제

PowerApps 검사기 솔루션을 삭제하려면 다음을 수행합니다.

1. 시스템 관리자 또는 시스템 사용자 지정자의 경우 https://web.powerapps.com/environments로 이동하여 PowerApps 포털을 엽니다.
2. **솔루션**을 선택합니다.
3. **PowerApps 검사기**를 선택한 다음 솔루션 도구 모음에서 **삭제**를 선택합니다.

### <a name="add-powerapps-checker"></a>PowerApps 검사기 추가

PowerApps 검사기를 Common Data Service 환경에 다시 추가하려면 다음을 수행합니다.

1. 시스템 관리자 또는 시스템 사용자 지정자의 경우 https://web.powerapps.com/environments로 이동하여 PowerApps 포털을 엽니다.
2. **솔루션**을 선택합니다.
3. 솔루션 도구 모음에서 **솔루션 검사기**를 선택한 다음 **설치**를 선택합니다.

## <a name="runs-on-large-solutions-fail"></a>대규모 솔루션에서 실행 실패

솔루션이 너무 큰 경우 발생할 수 있는 몇 가지 시나리오가 있습니다. 이러한 시나리오는 아래에 자세히 설명되어 있습니다. 각 시나리오에 대한 솔루션은 분석할 구성 요소가 적을수록 더 작은 솔루션을 만드는 것입니다. 솔루션의 큰 파일 크기가 플러그 인 어셈블리 구성 요소로 인한 경우 [사용자 지정 어셈블리 개발을 최적화](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md)하기 위한 지침을 참조하십시오.

솔루션 검사기는 다음 시나리오에 따라 솔루션을 확인하지 못할 수 있습니다.
- 30MB의 솔루션 파일 크기 제한의 하드 제한이 있습니다.  
- Common Data Service 환경에서 솔루션을 내보내는 데 10분의 시간 제한이 있습니다. 기본 솔루션과 같은 대형 솔루션은 이 시간 내에 내보내지 못할 수 있으며 검사는 성공적으로 완료되지 않습니다. 솔루션 검사기는 작업 처리에 실패하기 전에 세 번 재시도하므로 실패 알림을 받기 전에 30분 이상이 걸릴 수 있습니다.

이러한 문제를 해결하려면 분석할 더 작은 솔루션을 확인하거나 만드십시오. 가양성을 최소화하려면 종속 사용자 지정을 추가해야 합니다. 솔루션을 만들고 이러한 구성 요소를 추가하는 경우 다음을 포함합니다.

- 플러그 인을 추가할 때 플러그 인에 대한 SDK 메시지 처리 단계를 포함합니다.
- 엔터티 양식을 추가할 때 양식 이벤트에 연결된 JavaScript 웹 리소스를 포함합니다.  
- JavaScript 웹 리소스를 추가하는 경우 모든 종속 JavaScript 웹 리소스를 포함합니다.
- HTML 웹 리소스를 추가할 때 HTML 웹 리소스 내에 정의된 모든 종속 스크립트를 포함합니다.
- 사용자 지정 워크플로를 추가할 때 워크플로 내에서 사용되는 어셈블리를 포함합니다.

## <a name="solution-checker-run-or-download-results-dont-complete"></a>솔루션 검사기 실행 또는 다운로드 결과가 완료되지 않음 
솔루션 검사기를 실행한 직후 작업이 완료되지 않고 다음 메시지가 표시됩니다.<br />
"*SOLUTIONNAME* 솔루션에 대한 검사를 실행할 수 없습니다. 다시 실행해 보십시오." <br />
![실행할 수 없습니다](media/solution-checker-werent-able-to-run.png)

이 문제는 조직이 **관리 모드** 상태이고 솔루션 검사기가 요청을 실행하는 사용자의 사용 권한을 확인할 수 없기 때문에 발생합니다. 이 문제를 해결하려면 관리 모드를 사용하지 않도록 설정합니다. 

### <a name="disable-administration-mode-for-an-instance"></a>인스턴스에 대한 관리 모드 사용 안 함
1. Dynamics 365 for Customer Engagement 인스턴스 선택기에 액세스합니다. https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx
2. 솔루션 검사기를 실행하는 데 문제가 있는 인스턴스를 선택합니다.
3. **ADMIN**을 선택합니다.<br />
![인스턴스 관리자](media/solution-checker-instance-admin.png)

4. **관리 모드 사용** 선택을 취소합니다. <br />
![관리 모드 사용 안 함](media/solution-checker-instance-disable-admin-mode.png)

5. 솔루션 검사기를 다시 실행합니다.

## <a name="solution-checker-will-not-process-patched-solutions"></a>솔루션 검사기가 패치가 적용된 솔루션을 처리하지 않음

솔루션에 [패치](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates)가 적용된 경우 솔루션 검사기에서 분석을 위해 솔루션을 내보내지 못합니다. 솔루션에서 패치를 적용하면 원래 솔루션은 잠기게 되며 솔루션을 상위 솔루션으로 식별하는 종속 패치가 조직에 존재하는 경우 패치를 변경하거나 내보낼 수 없습니다.

이 문제를 해결하려면 솔루션에 관련된 모든 패치가 새로 만든 솔루션으로 롤백되도록 솔루션을 복제합니다. 이렇게 하면 솔루션의 잠금이 해제되고 시스템에서 솔루션을 내보낼 수 있습니다. 추가 정보: [솔루션 복제](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>포함 된 JavaScript가 있는 HTML 리소스의 문제에 대한 줄 번호 참조가 올바르지 않습니다. 

HTML 웹 리소스가 솔루션 검사기 내에서 처리되면 HTML 웹 리소스는 HTML 웹 리소스 내에서 JavaScript와 별도로 처리됩니다. 이로 인해 HTML 웹 리소스의 `<script>` 내에서 발견된 위반의 줄 번호가 올바르지 않습니다.

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>웹 리소스에 대한 웹 지원되지 않는 구문 문제

ECMAScript 6 (2015) 이상 버전은 현재 솔루션 검사기에 지원되지 않습니다. 솔루션 검사기가 ECMAScript 6 이상을 사용하여 JavaScript를 분석하는 경우 웹 리소스에 대한 웹 지원 구문 문제가 보고됩니다.  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>호출 범위를 기반으로 하는 플러그 인 및 워크플로 활동에 대해 여러 가지 위반이 보고됨

문제는 호출 컨텍스트에만 관련된 플러그 인 및 워크플로 작업 규칙의 경우 솔루션 검사기 도구는 IPlugin 인터페이스 구현에서 분석을 시작하고 호출 그래프를 트래버스하여 해당 구현의 범위 내에서 문제를 검색합니다. .  경우에 따라 많은 호출 경로가 문제가 발견되는 동일한 위치에 도착할 수 있습니다.  이 문제는 호출 범위와 관련이 있으므로 이 도구는 해당 범위를 기반으로 보고할 수 있으므로 별개의 위치보다 더 나은 영향을 제공합니다. 결과적으로 여러 문제를 해결해야 하는 단일 위치를 참조할 수 있습니다.

## <a name="see-also"></a>참조
[Common Data Service에 대한 모범 사례 및 지침](../../developer/common-data-service/best-practices/index.md)<br />
[모델 기반 앱에 대한 모범 사례 및 지침](../../developer/model-driven-apps/best-practices/index.md)<br />
