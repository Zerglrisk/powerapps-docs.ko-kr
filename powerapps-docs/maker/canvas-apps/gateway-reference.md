---
title: 캔버스 앱용 온-프레미스 데이터 게이트웨이 이해 | Microsoft Docs
description: PowerApps의 설치 및 문제 해결을 포함한 온-프레미스 데이터 게이트웨이에 대한 참조 정보
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/20/2017
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 095496aba49f722d439960a25242153b9daea382
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310044"
---
# <a name="understand-on-premises-data-gateways-for-canvas-apps"></a>캔버스 앱용 온-프레미스 데이터 게이트웨이 이해
## <a name="installation-and-configuration"></a>설치 및 구성
**필수 구성 요소**

최소:

* .NET 4.5 Framework
* Windows 7 또는 Windows Server 2008 R2의 64비트 버전(또는 이상)

권장:
* 8코어 CPU
* 8GB 메모리
* Windows 2012 R2의 64비트 버전(또는 이상)

관련 고려 사항:

* 도메인 컨트롤러에 게이트웨이를 설치할 수 없습니다.
* 꺼져 있거나 절전 상태이거나 인터넷에 연결되지 않은 상황에서는 게이트웨이를 실행할 수 없으므로 이러한 상황의 노트북과 같은 컴퓨터에는 게이트웨이를 설치하지 않아야 합니다. 또한 무선 네트워크를 통해 게이트웨이 성능이 저하될 수 있습니다.

**게이트웨이 설치**

1. [설치 관리자를 다운로드](http://go.microsoft.com/fwlink/?LinkID=820931)한 후 실행합니다.

    ![설치 관리자 실행](./media/gateway-reference/run-installer.png)

2. 설치 마법사의 첫 번째 화면에서 **다음**을 클릭하거나 탭하여 노트북에 게이트웨이를 설치하는 것에 대한 미리 알림을 확인합니다.

    ![미리 알림 화면](./media/gateway-reference/laptop-reminder.png)

3. 게이트웨이를 설치할 위치를 지정하고 사용 약관 및 개인정보처리방침에 동의하는 확인란을 선택한 다음 **설치**를 클릭하거나 탭합니다.

4. **사용자 계정 컨트롤** 대화 상자에서 **예**를 클릭하거나 탭하여 계속합니다.

5. 마법사의 다음 화면에서 **로그인**을 클릭하거나 탭한 후 PowerApps에 로그인하는 데 사용하는 것과 동일한 자격 증명을 제공합니다.

    ![서명하세요](./media/gateway-reference/sign-in.png)

6. 새 게이트웨이를 등록하거나 기존 게이트웨이를 마이그레이션, 복원 또는 인수하는 옵션을 클릭하거나 탭한 후 **다음**을 클릭하거나 탭합니다.

    ![새 또는 기존 게이트웨이 선택](./media/gateway-reference/new-existing.png)

   * 게이트웨이를 구성하려면 **이름** 및 **복구 키**를 입력하고 **구성**을 클릭하거나 탭한 후 **닫기**를 클릭하거나 탭합니다.

       ![새 게이트웨이 구성](./media/gateway-reference/configure-new.png)

       8자 이상을 포함하는 복구 키를 지정하고 안전한 곳에 보관합니다. 게이트웨이를 마이그레이션, 복원 또는 인수하려는 경우 이 키가 필요합니다.

   * 기존 게이트웨이를 마이그레이션, 복원 또는 인수하려면 게이트웨이 이름과 복구 키를 입력하고 **구성**을 클릭하거나 탭한 후 추가 프롬프트를 따릅니다.

       ![기존 게이트웨이 복구](./media/gateway-reference/recover-existing.png)

**게이트웨이 다시 시작**

게이트웨이는 Windows 서비스로 실행되므로 여러 가지 방법으로 시작하고 중지할 수 있습니다. 예를 들어 게이트웨이가 실행 중인 컴퓨터에서 높은 권한으로 명령 프롬프트를 열고 다음 명령 중 하나를 실행할 수 있습니다.

* 서비스를 중지하려면 다음 명령을 실행합니다.<br>
  **net stop PBIEgwService**

* 서비스를 시작하려면 다음 명령을 실행합니다.<br>
  **net start PBIEgwService**

**방화벽 또는 프록시 구성**

게이트웨이에 대한 프록시 정보를 제공하는 방법에 대한 자세한 내용은 [프록시 설정 구성](https://docs.microsoft.com/power-bi/service-gateway-proxy)을 참조하세요.

PowerShell 프롬프트에서 다음 명령을 실행하여 방화벽 또는 프록시가 연결을 차단하는지 여부를 확인할 수 있습니다. 이 명령은 Azure Service Bus에 대 한 연결을 테스트합니다. 이는 네트워크 연결을 테스트하는 데만 사용되며 클라우드 서버 서비스 또는 게이트웨이와 관련이 없습니다. 컴퓨터가 실제로 인터넷에 액세스할 수 있는지 여부를 확인하는 데 도움이 됩니다.

**Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350**

결과는 다음 예와 유사해야 합니다. **TcpTestSucceeded**가 **True**가 아니면 방화벽에 의해 차단될 수 있습니다.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

완전하게 보려면 **ComputerName** 및 **Port** 값을 이 항목 뒷부분에 있는 **포트 구성**에 나열된 값으로 대체합니다.

또한 방화벽은 Azure Service Bus가 Azure 데이터 센터에 보내는 연결을 차단할 수도 있습니다. 이 경우, 해당 데이터 센터에 대해 해당 지역의 IP 주소를 허용 목록에 추가(차단 해제)하고 싶을 것입니다. [여기](https://www.microsoft.com/download/details.aspx?id=41653)에서 Azure IP 주소 목록을 가져올 수 있습니다.

**포트 구성**

게이트웨이는 Azure Service Bus에 대한 아웃바운드 연결을 만듭니다. 아웃 바운드 포트에서 통신 합니다. TCP 443 (기본값), 5671, 5672, 9350 ~ 9354. 게이트웨이에는 인바운드 포트가 필요하지 않습니다.

[하이브리드 솔루션](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/)에 대해 자세히 알아보세요.

방화벽에서 데이터 영역에 대한 IP 주소를 허용 목록에 추가하는 것이 좋습니다. 매주 업데이트되는 [Microsoft Azure 데이터 센터 IP 목록](https://www.microsoft.com/download/details.aspx?id=41653)을 다운로드할 수 있습니다.

> [!NOTE]
> Azure 데이터 센터 IP 목록에서 주소는 [CIDR 표기법](http://whatismyipaddress.com/cidr)으로 나열됩니다. 예를 들어 10.0.0.0/24는 10.0.0.0~10.0.0.24를 의미하지 않습니다.

게이트웨이에서 사용되는 정규화된 도메인 이름 목록은 다음과 같습니다.

| 도메인 이름 | 아웃바운드 포트 | Description |
| --- | --- | --- |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |AMQP(고급 메시지 큐 프로토콜) |
| *.servicebus.windows.net |443, 9350-9354 |TCP를 통한 Service Bus Relay의 수신기(Access Control 토큰 획득에는 443 필요) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| \* login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |게이트웨이가 Power BI 서비스에서 연결할 수 없는 경우 인터넷 연결을 테스트하는 데 사용됩니다. |

**로그인 계정**

사용자는 회사 또는 학교 계정 중 하나로 로그인합니다. 조직 계정입니다. Office 365 제품에 로그인하였고 실제 직장 전자 메일을 입력하지 않은 경우 nancy@contoso.onmicrosoft.com처럼 보일 수 있습니다. 클라우드 서비스 내에서 사용자의 계정은 AAD(Azure Active Directory)의 테넌트 내에 저장됩니다. 대부분의 경우 AAD 계정의 UPN은 이메일 주소와 일치합니다.

**Windows 서비스 계정**

온-프레미스 데이터 게이트웨이는 Windows 서비스 로그온 자격 증명에 대해 *NT SERVICE\PBIEgwService*를 사용하도록 구성됩니다. 기본적으로 서비스로 로그온 권한을 포함합니다. 게이트웨이를 설치 중인 컴퓨터의 컨텍스트에 있습니다.

온-프레미스 데이터 원본 또는 클라우드 서비스에 로그인하는 회사 또는 학교 계정에 연결하는 데 사용되는 계정이 아닙니다.

인증으로 인해 프록시 서버에 문제가 발생하면 [프록시 구성](https://docs.microsoft.com/power-bi/service-gateway-proxy#changing-the-gateway-service-account-to-a-domain-user)에서 설명하는대로 Windows 서비스 계정을 도메인 사용자 또는 관리 서비스 계정으로 변경할 수 있습니다.

## <a name="tenant-level-administration"></a>테넌트 수준 관리 

테넌트 관리자가 다른 사용자가 설치 및 구성한 모든 게이트웨이를 관리할 수 있는 단일 장소는 없습니다.  테넌트 관리자인 경우 설치할 모든 게이트웨이에 관리자로 추가하도록 조직의 사용자에게 요청하는 것이 좋습니다. 이렇게 하면 게이트웨이 설정 페이지를 통해 또는 [PowerShell 명령](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters)을 통해 조직의 모든 게이트웨이를 관리할 수 있습니다.

## <a name="frequently-asked-questions"></a>질문과 대답
#### <a name="general"></a>일반
**지원부** 게이트웨이가 지 원하는 데이터 원본은 무엇 인가요?  
**대답할** 이 항목을 작성할 때:

* SQL Server
* SharePoint
* Oracle
* Informix
* Filesystem
* DB2

**지원부** SQL Azure와 같은 클라우드의 데이터 원본에 대 한 게이트웨이가 필요 한가요?  
**대답할** 아니요. 게이트웨이는 온-프레미스 데이터 원본에만 연결됩니다.

**지원부** 실제 Windows 서비스는 무엇 인가요?  
**대답할** 서비스에서는 게이트웨이를 **온-프레미스 데이터 게이트웨이 서비스**라고 합니다.

**지원부** 클라우드의 게이트웨이에 대 한 인바운드 연결이 있나요?  
**대답할** 아니요. 게이트웨이는 Azure Service Bus로 아웃바운드 연결을 사용합니다.

**지원부** 아웃 바운드 연결을 차단 하면 어떻게 되나요? 어떻게 해야 하나요?  
**대답할** 게이트웨이에서 사용 하는 포트 및 호스트 목록을 참조 하세요.

**지원부** 게이트웨이가 데이터 원본과 동일한 컴퓨터에 설치 되어야 하나요?  
**대답할** 아니요. 게이트웨이는 제공된 연결 정보를 사용하여 데이터 원본에 연결합니다. 이 의미에서 게이트웨이를 클라이언트 애플리케이션으로 생각합니다. 제공된 서버 이름에만 연결할 수 있어야 합니다.

**지원부** 게이트웨이에서 데이터 원본에 대 한 쿼리를 실행 하기 위한 대기 시간은 어떻게 되나요? 최상의 아키텍처는 무엇인가요?  
**대답할**  네트워크 대기 시간을 줄이려면 게이트웨이를 데이터 원본에 최대한 가깝게 설치 합니다. 실제 데이터 원본에 게이트웨이를 설치할 수 있는 경우 발생하는 대기 시간이 최소화됩니다. 데이터 센터도 고려해야 합니다. 예를 들어 서비스가 미국 서부 데이터 센터를 사용하고 Azure VM에서 호스팅되는 SQL Server가 있다면 미국 서부에도 Azure VM이 있어야 합니다. 이렇게 하면 대기 시간이 최소화되고 Azure VM에서 송신 요금을 피할 수 있습니다.

**지원부** 네트워크 대역폭에 대 한 요구 사항이 있나요?  
**대답할** 네트워크 연결에 대 한 양호한 처리량을 갖는 것이 좋습니다. 각 환경이 다르며 전송되는 데이터 양은 결과에 영향을 줍니다. ExpressRoute를 사용하면 온-프레미스와 Azure 데이터 센터 간에 처리량 수준을 보장하는 데 도움이 될 수 있습니다.

타사 도구인 [Azure 속도 테스트 앱](http://azurespeedtest.azurewebsites.net/)을 사용하여 처리량을 측정할 수 있습니다.

**지원부** Azure Active Directory 계정으로 게이트웨이 Windows 서비스를 실행할 수 있나요?  
**대답할** 아니요. Windows 서비스에는 유효한 Windows 계정이 있어야 합니다. 기본적으로 서비스 SID, *NT SERVICE\PBIEgwService*로 실행됩니다.

**지원부** 결과는 클라우드로 다시 전송 되는 방법  
**대답할** 이 작업은 Azure Service Bus를 통해 수행 됩니다. 자세한 내용은 [작동 방법](gateway-reference.md#how-the-gateway-works)을 참조하세요.

**지원부** 내 자격 증명은 어디에 저장 되나요?  
**대답할** 데이터 원본에 대해 입력 하는 자격 증명은 게이트웨이 클라우드 서비스에 암호화 되어 저장 됩니다. 자격 증명은 게이트웨이 온-프레미스에서 암호 해독됩니다.

**지원부** 게이트웨이를 경계 네트워크 (DMZ, 완충 영역 및 스크린 된 서브넷이 라고도 함)에 놓을 수 있나요?  
**대답할** 게이트웨이가 데이터 원본에 연결 해야 합니다. 데이터 원본이 경계 네트워크에 없는 경우 게이트웨이가 연결되지 못할 수 있습니다. 예를 들어 SQL Server를 실행하는 컴퓨터가 경계 네트워크에 있지 않을 수 있으며 경계 네트워크에서 해당 컴퓨터에 연결할 수 없습니다. 게이트웨이를 경계 네트워크에 배치한 경우 게이트웨이는 SQL Server를 실행 중인 컴퓨터에 연결할 수 없습니다.

#### <a name="high-availabilitydisaster-recovery"></a>고가용성/재해 복구
**지원부** 게이트웨이와 함께 고가용성 시나리오를 사용 하기 위한 계획이 있나요?  
**대답할** 고가용성은 둘 이상의 게이트웨이를 동일한 클러스터에 조인 하 여 사용 하도록 설정 됩니다.  고가용성 게이트웨이 클러스터를 사용하려면 온-프레미스 데이터 게이트웨이 2017년 11월 업데이트 이상이 필요합니다.  자세한 내용은 [블로그 게시물 알림](https://powerapps.microsoft.com/en-us/blog/gateway-high-availability-for-powerapps-and-flow)을 참조하세요.

**지원부** 재해 복구에 사용할 수 있는 옵션은 무엇 인가요?  
**대답할** 복구 키를 사용 하 여 게이트웨이를 복원 하거나 이동할 수 있습니다. 게이트웨이 설치하는 경우 복구 키를 지정합니다.

**지원부** 복구 키의 혜택은 무엇 인가요?  
**대답할** 재해 후 게이트웨이 설정을 마이그레이션하거나 복구할 수 있는 방법을 제공 합니다.

#### <a name="troubleshooting"></a>문제 해결
**지원부** 게이트웨이 로그는 어디에 있나요?  
**대답할** 이 항목의 뒷부분에 나오는 [도구](gateway-reference.md#tools) 를 참조 하세요.

**지원부** 온-프레미스 데이터 원본으로 어떤 쿼리를 보내고 있는지 어떻게 확인할 수 있나요?  
**대답할** 전송 중인 쿼리를 포함 하는 쿼리 추적을 사용 하도록 설정할 수 있습니다. 문제 해결이 완료되면 원래 값으로 다시 변경해야 합니다. 쿼리 추적을 사용된 상태로 두면 로그가 더 커질 수 있습니다.

데이터 원본에 쿼리 추적을 위해 포함된 도구를 볼 수도 있습니다. 예를 들어 SQL Server 및 Analysis Services용 확장 이벤트 또는 SQL 프로파일러를 사용할 수 있습니다.

## <a name="how-the-gateway-works"></a>게이트웨이 작동 방식
![작동 방법](./media/gateway-reference/gateway-arch.png)

사용자가 온-프레미스 데이터 원본에 연결된 요소와 상호 작용할 때:  

1. 클라우드 서비스는 데이터 원본에 대해 암호화된 자격 증명과 함께 쿼리를 만들고 게이트웨이가 처리할 수 있도록 쿼리를 큐에 보냅니다.

2. 게이트웨이 클라우드 서비스는 쿼리를 분석하고 요청을 [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/)로 푸시합니다.

3. 온-프레미스 데이터 게이트웨이는 대기 중인 요청에 대해 Azure Service Bus를 폴링합니다.

4. 게이트웨이는 쿼리를 가져와서 자격 증명을 암호 해독하고 해당 자격 증명을 사용하여 데이터 원본에 연결합니다.

5. 게이트웨이는 실행을 위해 쿼리를 데이터 원본으로 보냅니다.

6. 결과는 데이터 원본에서 게이트웨이로 다시 전송된 후 클라우드로 전송됩니다. 그런 다음 서비스에서 결과를 사용합니다.

## <a name="troubleshooting"></a>문제 해결
#### <a name="update-to-the-latest-version"></a>최신 버전으로 업데이트
게이트웨이 버전이 만료되면 많은 문제가 발생할 수 있습니다.  최신 버전을 사용 중인지 확인하는 것이 가장 좋습니다.  한 달 이상 게이트웨이를 업데이트하지 않은 경우 최신 버전의 게이트웨이를 설치하고 문제를 재현할 수 있는지 확인하는 것이 좋습니다.

#### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>오류: 사용자를 그룹에 추가 하지 못했습니다.  (-2147463168   PBIEgwService   Performance Log Users   )
지원되지 않는 도메인 컨트롤러에 게이트웨이 설치하려는 경우 이 오류가 발생할 수 있습니다. 도메인 컨트롤러가 아닌 컴퓨터에 게이트웨이를 배포해야 합니다.

## <a name="tools"></a>도구
#### <a name="collecting-logs-from-the-gateway-configurator"></a>게이트웨이 구성기에서 로그 수집
게이트웨이에 대한 여러 로그를 수집할 수 있습니다. 항상 로그로 시작합니다!

**설치 관리자 로그**

%localappdata%\Temp\On-premises_data_gateway_*.log

**구성 로그**

%localappdata%\Microsoft\on-premises data gateway\GatewayConfigurator*.log

**엔터프라이즈 게이트웨이 서비스 로그**

C:\Users\PBIEgwService\AppData\Local\Microsoft\on-premises data gateway\Gateway*.log

**이벤트 로그**

**온-프레미스 데이터 게이트웨이 서비스** 이벤트 로그는 **애플리케이션 및 서비스 로그** 아래에 있습니다.

![이벤트 로그](./media/gateway-reference/event-logs.png)

#### <a name="fiddler-trace"></a>Fiddler 추적
[Fiddler](http://www.telerik.com/fiddler)는 HTTP 트래픽을 모니터링하는 Telerik의 무료 도구입니다.  클라이언트 컴퓨터에서 Power BI 서비스를 사용하여 앞뒤로 볼 수 있습니다. 오류 및 기타 관련된 정보를 표시할 수 있습니다.
