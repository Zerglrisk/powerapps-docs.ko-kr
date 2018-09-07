---
title: InfoPath 양식을 캔버스 앱으로 변환 | Microsoft Docs
description: 일반적인 시나리오에 대한 정보와 캔버스 앱에서 이러한 항목을 만드는 방법을 사용하여 InfoPath 양식을 PowerApps로 변환하기 시작합니다.
author: richardriley99
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/05/2018
ms.author: rriley
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1432ad41b62671267c22d521c7a117e89dfc728c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42859449"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>InfoPath 양식을 PowerApps로 변환

보다 강력한 플랫폼에서 이러한 뛰어난 기능을 제공하는 방법을 알아보고자 하는 InfoPath의 뛰어난 기능의 빌더입니까?

## <a name="key-advantages-of-powerapps-over-infopath"></a>InfoPath에 비해 PowerApps의 주요 이점

대부분의 InfoPath 고급 사용자와 마찬가지로 한동안 뛰어난 양식을 빌드하도록 설정된 고유한 기술을 사용해 왔습니다. 양식에 매우 만족하지만 &quot;클래식&quot; 느낌, 모바일 장치에 대해 이상에 못 미치는 환경, 미래의 불확실한 실행 가능성 및 코드를 작성하지 않고 다른 서비스에 연결할 때 항상 궁지에 빠짐 등의 제한 사항도 알고 있습니다.

PowerApps 팀은 이 외에도 많은 문제들을 들었습니다. 더 나은 환경을 통합하고 기존 비즈니스 및 기술 능력을 활용하여 캔버스 앱을 만들 수 있도록 열심히 노력했습니다. PowerApps를 사용하면 코드를 작성하지 않고도 올바른 비즈니스 솔루션을 빠르게 빌드하고 배포할 수 있습니다.

**PowerApps의 강력한 기능 사용하도록 설정**  
PowerApps는 다른 추가 작업 없이 웹, SharePoint, Dynamics 365, Teams, Power BI 또는 모바일 장치에 배포할 수 있는 고기능 앱을 신속하게 빌드하도록 설계된 SaaS(Software as a Service) 플랫폼입니다. 이들은 배포하기(게시된 앱에 URL을 부여하기) 쉽기 때문에 업데이트도 쉽습니다.

**앱 공유**  
앱을 빌드하려 시도한 다음, Google 또는 Apple 앱 스토어에 게시했습니까? 복잡한 문제입니다. 추가 문제는 두 번째 앱을 배포하거나 기존 앱을 업데이트하려는 경우 사용자가 훨씬 더 많은 단계를 수행해야 한다는 것입니다. PowerApps가 아닙니다. 사용자가 앱 스토어에서 Microsoft PowerApps 앱을 설치한 다음, 자신의 Microsoft 계정 사용자 이름 및 암호를 사용하여 로그인하면 마침내 사용자는 공유했던 모든 고기능 앱을 갖게 됩니다. 나중에 해당 앱을 업데이트하거나 새 앱을 해당 앱을 내보내는 경우 해당 앱은 자신의 장치에 표시됩니다. 장치 관리의 번거로움이 없는 모바일 앱은 귀하와 사업에 큰 장점입니다.

**모바일에 대해 말하기**  
PowerApps를 사용하여 사용자의 모바일 장치의 강점을 활용할 수 있습니다. 앱 내에서 가속, 카메라, 나침반, 연결 정보 및 위치 신호 모두에 대한 액세스 권한이 있습니다. 이를 통해 앱을 빌드하기 위한 모든 가능성의 세계를 열어 작업을 완수합니다. 물론, 터치 기능은 PowerApps에서 자동이며 앱을 빌드할 때 코드에 별도로 아무 것도 추가하지 않습니다.

**기본 제공 가져오기**  
InfoPath를 사용한 표준은 하나의 데이터 원본에서 데이터로 작업하는 것이었습니다. 그러나 어딘가 다른 곳에서(다른 사이트 컬렉션에서 SharePoint 목록 같은) 업데이트를 하거나 외부 서비스에 연결하려는 경우 문제는 까다로워지고 코드 같은 개념이 밤새 고민하게 만듭니다. PowerApps를 사용하지 않습니다. 하나의 앱에서 여러 데이터 원본 및 서비스 연결을 사용하여 작업할 수 있도록 설계되었습니다. 현재는 Flow 및 Dynamics 365 같은 온-프레미스 및 클라우드 데이터의 조합, Microsoft Office 365 및 Azure 서비스 그리고 Dropbox, Google, Salesforce 및 Slack 같은 유명한 대상을 포함하여 다양한 타사 서비스를 지원하는 [150개 초과 커넥터](https://docs.microsoft.com/powerapps/connections-list#all-connectors)가 있습니다. 이제 원본 데이터가 존재했던 위치가 아니라 사용자가 귀하를 데려가는 위치의 크기를 조정하기 위한 솔루션을 빌드할 수 있습니다.

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps 및 SharePoint: 함께 사용하면 더욱 좋음

PowerApps는 두 가지 방법으로 SharePoint 환경을 더 낫게 만들 수 있는 뛰어난 도구입니다. SharePoint 목록에 대한 양식을 사용자 지정하거나 SharePoint 데이터를 사용해 작업하기 위한 독립 실행형 앱을 만들 수 있는 옵션이 있습니다.

**SharePoint 양식 사용자 지정**은 사용자가 일상 업무에 대한 목록을 사용하고 있지만 SharePoint 목록에서 항목을 추가/보기/편집하는 방법을 사용자 지정하려는 경우 유용합니다. **형식 사용자 정의**를 클릭하면 컨텍스트에 따라 모드(새로 만들기/편집/보기)가 변경되는 단일 화면 &quot;형식 앱&quot;을 만듭니다. 이러한 앱은 SharePoint에서 관리하며 해당 사용 권한은 편집/보기를 위한 목록 사용 권한과 동일합니다.

**SharePoint에서 PowerApps 캔버스 앱 만들기**를 사용하면 모바일 장치에서 앱을 실행할 수 있습니다. 또한 SharePoint 페이지에 포함될 수도 있습니다. 이를 클릭하면 3가지 화면 앱(목록 보기, 양식 새로 만들기/편집, 양식 보기)을 만듭니다.  이러한 앱에 대한 사용 권한/공유 모델은 SharePoint에 연결되지 않고 대신 PowerApps에서 관리됩니다.

두 옵션 간의 차이를 이해했으므로 다음 섹션에서는 각 옵션의 사용에 대한 개요를 제공합니다.

## <a name="sharepoint-forms"></a>SharePoint 양식

PowerApps 팀 및 SharePoint 팀은 협력해 SharePoint와 함께 사용하도록 사용자 지정 스토리를 새로 만들었습니다.  대부분의 InfoPath 개발자와 마찬가지로 InfoPath가 SharePoint와 상호 작용하는 방법을 배웠습니다. SharePoint가 뛰어난 반면 기본 양식은 약간 평범하며 InfoPath 없는 사용자 지정 또는 비즈니스 논리를 허용하지 않습니다. 그것은 이전 방식입니다.

PowerApps를 사용하여 목록 양식을 네이티브 기능으로 사용자 지정할 수 있습니다. 이렇게 하면 PowerApps의 모든 역량을 활용하게 됩니다. 아래 스크린샷에서 Power BI 보고서가 포함된 PowerApps 양식의 예를 확인할 수 있습니다.  전체 솔루션은 15분 이내에 수행되었습니다.

![SharePoint 통합](./media/transform-infopath/sharepoint-integration.png)

PowerApps의 또 다른 중요한 특징은 같은 양식에서 다른 환경 또는 다른 SharePoint 사이트 컬렉션에 쉽게 연결하는 기능입니다. 예를 들어 SharePoint Online 및 SharePoint 온-프레미스 환경에서 동시에 데이터를 업데이트하고 표시하는 한 가지 양식을 만들기를 원합니까? 걱정하실 필요가 없습니다. [온-프레미스 데이터 게이트웨이](https://docs.microsoft.com/powerapps/gateway-management)를 설치하면 몇 분 이내로 온-프레미스 데이터와 PowerApps, Power BI, Microsoft Flow 및 Azure Logic Apps의 연결을 실행합니다. 방화벽 규칙 변경은 필요하지 않습니다. Microsoft Flow와 이 앱을 연결하여 다른 수준의 기능을 활용할 수 있습니다.

## <a name="a-standalone-sharepoint-app"></a>독립 실행형 SharePoint 앱

목록 양식을 업데이트하지 않고 SharePoint 데이터에 기반한 완전한 독립 실행형 앱을 빌드하려는 경우 이 기술을 사용합니다. 이는 시작하기에 가장 좋은 방법이므로 PowerApps 캔버스를 배우고 여러 데이터 원본 중 하나에서 미래 앱을 빌드하기 시작할 수 있습니다.

시작하려면 상호 작용하려는 SharePoint 목록으로 이동합니다.

1. 메뉴 모음에서 PowerApps 클릭
2. 앱 만들기 선택
3. 이름을 제공하세요.
4. 만들기 클릭

PowerApps는 사용자 지정할 수 있는 기본 앱을 빌드하게 됩니다.

간단히 시작합니다. 첫 번째 앱에 대한 다른 형식의 한 쌍의 필드만으로 간단한 사용자 지정 목록을 사용합니다. 그러면 전복되지 않는 견고한 토대를 빌드할 수 있습니다. 걱정 마십시오. 순식간에 전문가가 되어 복잡한 앱을 처리하게 해줍니다.  이 첫 번째 앱을 간단히 실행하기 위한 도움말은 이 [설명서](https://docs.microsoft.com/powerapps/generate-app-from-sharepoint-list-interface) 또는 이 커뮤니티 [비디오](https://youtu.be/BnYe_7fpZRM)를 확인합니다. 아래의 예는 일반 InfoPath 작업 및 PowerApps에서 해당 작업을 수행하는 방법을 설명합니다. 이들 각각의 예는 단순한 SharePoint 목록 앱에 빌드됩니다.

# <a name="how-do-you-do-that-with-powerapps"></a>PowerApps로 빌드하는 방법

이제 기본 개념을 이해했으니 더 자세히 들어가 봅시다. 첫 번째 앱을 완수했으면 다음 섹션은 PowerApps에서 일반 InfoPath 개념 중 일부를 적용하는 데 도움이 됩니다.

**값에 따라 필드 숨기기/표시/잠그기**  
성공적인 양식을 만드는 가장 일반적인 방법 중 하나는 강력한 비즈니스 논리를 갖추고 해당 논리를 적용하는 것입니다. 이를 완수하는 한 가지 방법은 값 또는 작업에 따라 필드의 상태를 변경하는 것입니다. 사용자가 필드를 변경할 수 있는지 여부를 지정하려면 PowerApps를 통해 컨트롤을 선택하고 DisplayMode를 편집 또는 보기로 설정합니다. 사용 가능한 두 번째 방법은 조건에 따라 작업을 수행하는 단순한 IF 수식입니다. 먼저 편집하려는 레이블을 선택하고 잠금 아이콘을 클릭하여 카드의 잠금을 해제해 값을 변경할 수 있습니다.

![잠금 데이터 카드 표시 숨기기](./media/transform-infopath/hide-show-lock.png)

오른쪽의 카드 하단으로 스크롤하여 DefaultMode 속성을 편집합니다.

![If Else Statement 식](./media/transform-infopath/if-else-statement.png)

이 예에서는 If 문을 사용합니다. 이 If(ThisItem.Color = &quot;Blue&quot;, DisplayMode.View, DisplayMode.Edit) 문은 현재 항목 색상 필드가 파란색이고 동물 필드는 읽기 전용인 경우 그렇지 않으면 해당 필드를 편집할 수 있다는 의미입니다.

카드를 전혀 표시하지 않으려는 경우 DisplayMode 바로 위의 표시 필드에 비슷한 함수를 삽입할 수 있습니다.

여기서 보여줄 다른 것은 사용자의 이메일 주소가 승인자의 이메일 주소와 일치하는 경우에만 표시하도록 승인 단추를 숨기는 것입니다. 힌트: User().Email은 현재 사용자의 이메일 주소에 액세스하는 방법입니다. 따라서 YourDataCard가 승인자의 이메일 주소를 저장하고 있는 카드인 경우 단추 표시 값을 If(YourDataCard.Text = User().Email, true, false)가 되게 할 수 있습니다.

**조건부 서식**  
필드를 숨긴 위의 경우와 비슷한 방식으로 사용자에게 시각적 피드백을 제공할 수도 있습니다. 입력한 값이 허용 가능한 범위를 벗어나는 경우 빨간색으로 텍스트를 강조 표시하거나 업로드 후 파일을 삭제하려면 업로드 단추 텍스트 및 색을 변경합니다. 이 모든 작업은 색 또는 표시 같은 속성 필드에서 If 등의 함수를 사용하여 수행됩니다.

예를 들어 사용자가 입력 상자에 올바른 서식의 이메일을 입력하지 않은 경우 [IsMatch](https://docs.microsoft.com/powerapps/functions/function-ismatch) 함수와 짝을 이루는 If 함수를 사용하여 이메일 필드의 텍스트 색을 빨간색으로 변경할 수 있습니다. TextInput1이 사용자가 이메일 주소에 입력하는 필드인 경우 TextInput1의 색상 값을 If(IsMatch(TextInput1.Text, Email), Black, Red)로 설정하여 이 작업을 수행합니다. IsMatch는 자신의 것을 만드는 기능 또는 이메일 같이 수많은 미리 정의된 패턴을 지원합니다. 조건부 서식에 관한 자세한 내용은 [커뮤니티 비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962)를 확인합니다.

**역할 기반 보안 구현**  
고려해야 할 첫 번째 함수는 [DataSourceInfo](https://docs.microsoft.com/powerapps/functions/function-datasourceinfo)입니다. 데이터 원본에서 다시 가져오는 정보는 데이터 원본에 따라 달라지지만 사용자가 데이터를 편집하기 위한 액세스 권한을 가지고 있는지 확인하려면 종종 DataSourceInfo(YourDataSource, DataSourceInfo.EditPermission)을 사용할 수 있습니다. YourDataSource를 데이터 원본의 이름으로 바꿉니다. 이를 통해 사용자에게 편집에 대한 액세스 권한이 있는 경우 양식이나 단추를 표시할 수 있습니다. 함수에서 쿼리할 수 있는 정보의 전체 목록에 대한 DataSourceInfo 설명서를 확인합니다.

대신 앱에서 단추나 양식에 대한 액세스를 관리하기 위해 Active Directory 그룹을 사용하려는 경우 더 자세히 들어가야 합니다. 이를 하려면 PowerApps의 유연성을 이용하고 Microsoft Graph API를 사용하여 사용자 고유의 커넥터를 만듭니다. 이 작업은 어려운 것 같지만 사용자를 안내해주는 단계별 [설명서](https://powerapps.microsoft.com/blog/implementing-role-based-permission/)가 있습니다.

**앱에서 이메일 보내기**  
PowerApps에서 이메일을 보낼 수 있는 여러 방법이 있습니다. 가장 쉬운 방법은 Office 365 Outlook 커넥터를 사용하는 것입니다. 이 커넥터를 통해 앱에서 직접 이메일을 보낼 수 있습니다. 사서함과 상호 작용하는 이메일 메시지 및 기타 작업을 가져올 수도 있습니다. 이메일을 보내는 방법에 대한 [설명서](https://docs.microsoft.com/powerapps/connections/connection-office365-outlook) 또는 커뮤니티 [비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349)가 있습니다.

예를 들어 SharePoint 승인 워크플로 승인 체인을 만들어 더 복잡한 이메일을 보내야 할 경우 Microsoft Flow를 만들고 이에 앱을 연결하는 것이 해결책입니다. 앱을 Microsoft Flow에 연결하면 PowerApps가 외부 데이터 및 서비스에 매끄럽게 연결되는 것처럼 워크플로 엔진의 모든 역량을 활용하는 것입니다. PowerApps 및 Microsoft Flow 연결에 대한 자세한 내용은 [설명서](https://docs.microsoft.com/powerapps/using-logic-flows)를 확인합니다.

원하는 메일 옵션을 아직 찾지 못한 경우 Benchmark Email, Gmail, MailChimp, Outlook.com, SendGrid 또는 SMTP에 대한 PowerApps 커넥터를 활용할 수 있습니다. PowerApps의 장점은 연결입니다.

**워크플로**  
워크플로 엔진 없이 비즈니스 논리 및 비즈니스 앱에 대해 설명하기는 어렵습니다. 좋은 소식은 PowerApps 팀이 휠을 새로 바꾸지 않고 다른 워크플로 엔진을 제공했다는 것입니다. 대신 Microsoft Flow 서비스에 강력한 커넥터를 제공합니다. 이제 사용하기 쉬운 워크플로 엔진을 통해 [200개 초과 다른 서비스](https://flow.microsoft.com/connectors/) 상에서 프로세스 및 작업을 자동화할 수 있습니다. PowerApps 및 Microsoft Flow 연결에 대한 자세한 내용은 [설명서](https://docs.microsoft.com/powerapps/using-logic-flows)를 확인합니다.

**PowerApps를 사용한 변수**  
솔루션을 빌드할 때 변수가 관련돼야 한다는 것은 당연한 생각입니다. PowerApps가 세 가지 유형의 변수를 제공하는 경우 이들 변수를 사용해야 할 때 사용하기를 원합니다. 데이터를 가져오는 방법에 대해 생각하는 대신 변수에 데이터를 저장하고 해당 변수를 참조하는 것은 직접 해당 데이터를 참조하는 방법에 대해 생각하는 것입니다. 이를 같게 하는 가장 좋은 방법은 Excel을 사용하는 것입니다. Excel에서 총계는 변수가 아니라 다른 필드의 합계입니다. 따라서 시트의 다른 곳에 해당 값을 사용하려는 경우 총계를 계산한 필드를 지정합니다. [설명서](https://docs.microsoft.com/powerapps/working-with-variables)는 이 모든 것에 대한 훌륭한 설명입니다. 다른 사고 프로세스에 개방적이어야 합니다.

아직 변수가 필요한(수행할 수 있는 경우가 많은) 경우 이는 다양한 옵션을 이해하는 데 도움이 됩니다. 변수를 정의할 필요가 없는 PowerApps를 유념하십시오. 저장할 이름 및 값을 지정하기 위해 함수 중 하나를 사용하면 변수가 생성됩니다. 메뉴 모음에서 보기를 클릭하고 변수를 선택하여 만든 변수를 볼 수 있습니다. 변수는 메모리에 보관되고 해당 값은 앱을 닫을 때 손실 됩니다. 변수의 세 유형은 다음과 같습니다.

- 전역 변수는 가장 일반적으로 먼저 떠올리는 것입니다. 여기서 [설정](https://docs.microsoft.com/powerapps/functions/function-set) 함수를 사용하여 변수에 대한 값을 지정할 수 있습니다. 그러면 이 값을 앱 전체에서 사용할 수 있습니다. 함수를 사용하는 방법의 예가 설정(YourVariable, YourValue)되었습니다. 그러면 앱 전체에서 이름으로 YourVariable을 참조할 수 있습니다.
- 컨텍스트 변수는 컨텍스트 변수가 정의되어 있는 화면에서만 사용할 수 있는 변수입니다. 화면을 종료하면 컨텍스트 변수가 재설정됩니다. 컨텍스트 변수는 예를 들어 이전 화면에서 전달된 정보를 저장하거나 양식을 전송했는지 추적하기 위해 종종 사용됩니다. [UpdatedContext](https://docs.microsoft.com/powerapps/functions/function-updatecontext)의 일반적인 용도는 UpdateContext( { Submitted: "true" } )로서 제출된 변수를 True로 설정합니다. 정보가 제출됐는지를 추적하고 모든 필드를 읽기 전용으로 변경하는 페이지에서 제출 단추의 해당 부분을 만들 수 있습니다. 참고: 컬렉션이 개별적으로 업데이트될 수 있는 정보의 테이블을 저장하는 데 사용될 경우 ":"을 사용합니다. 시작하려면 [수집](https://docs.microsoft.com/powerapps/functions/function-clear-collect-clearcollect)을 살펴봅니다. 사용자가 보내려는 다양한 SharePoint 항목을 태그하므로 사용 예제로 쇼핑 카트를 만들 수 있습니다. 작동 중인 해당 개념을 보여주는 커뮤니티 [비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180)가 있습니다.

**계단식 드롭다운**  
계단식 드롭다운은 매우 유용합니다. 이전 드롭다운에서 선택한 값에 기반해 한 드롭다운에서 선택을 필터링할 수 있습니다. PowerApps에서 계단식 드롭다운은 종종 앱에 두 개의 데이터 원본을 소유하여 만들어집니다. 첫 번째 데이터 원본은 작업하거나 업데이트하는 데이터이며 두 번째 데이터 원본은 원하는 연계 효과를 빌드하기 위한 값을 저장하는 데 사용됩니다. 아래는 선택 옵션을 사용한 두 번째 데이터 원본의 예입니다.

![계단식 드롭다운](./media/transform-infopath/cascading-dropdowns.png)

이제 첫 번째 드롭다운 컨트롤을 만들고 항목 속성의 경우 고유 수식(영향, 제목)을 사용하여 드롭다운에서 비용, 프로그램 영향 및 일정을 표시합니다. 그런 다음, 두 번째 드롭다운을 추가하고 항목 속성을 ddSelectType이 첫 번째 드롭다운 상자의 이름인 경우 Filter(Impacts,ddSelectType.Selected.Value in SCategory)로 설정합니다. 계단식 드롭다운이 있는 것처럼 설정합니다. 자세한 내용은 PowerApps 팀에서 해당 게시물 [SharePoint: 간단한 4단계의 계단식 드롭다운!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) 또는 [커뮤니티 비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)를 확인합니다. SharePoint 없이도 쉽게 수행할 수 있으니 걱정 마십시오.

**하나의 슈퍼 앱 빌드하지 않기**  
PowerApps를 사용하여 다른 앱에서 하나의 앱을 호출할 수 있습니다. 따라서 풍선껌으로 고정되고 빌드한 대용량 InfoPath 양식 대신 서로를 호출하고 심지어 데이터를 전달하는 앱 그룹을 빌드할 수 있어 개발을 더욱 단순하게 만듭니다.

## <a name="next-steps"></a>다음 단계

위의 정보를 통해 세계로 나아갈 준비가 됐으니 한 번에 하나의 PowerApps 앱으로 세계를 정복하기 시작합시다. 작업을 계속하면서 다음 몇 가지 유용한 도움말 링크를 제공합니다. 그 중 하나는 PowerApps 커뮤니티 사이트로 가는 링크입니다. 오늘 커뮤니티에 참여해 교류하면 혼자 하는 것보다 훨씬 더 빨리 기술이 향상됩니다.

[**수식 참조** ](https://docs.microsoft.com/powerapps/formula-reference) - 기본 함수 중 몇 가지를 탐색하기만 해도 영감을 받는 언제나 좋은 방법입니다.

[**PowerApps 커뮤니티** ](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) - 예를 참조하고 다른 사람들과 교류하고 질문과 답변을 통해 PowerApps 커뮤니티가 성장하도록 도와줍니다.
