---
title: InfoPath 양식을 캔버스 앱으로 변환 | Microsoft Docs
description: 일반적인 시나리오에 대 한 정보 및 캔버스 앱에서 이러한 항목을 만드는 방법에 대 한 정보를 사용 하 여 InfoPath 양식을 Power Apps로 변환 하기 시작 합니다.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a41c9c121c1b57545376ba16f93d249c36ddeaeb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674560"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>InfoPath 양식을 PowerApps로 변환

보다 강력한 플랫폼에서 이러한 뛰어난 기능을 제공하는 방법을 알아보고자 하는 InfoPath의 뛰어난 기능의 빌더이신가요?

## <a name="key-advantages-of-power-apps-over-infopath"></a>InfoPath를 통한 Power Apps의 주요 이점

대부분의 InfoPath 고급 사용자와 마찬가지로 한동안 뛰어난 양식을 빌드하도록 설정된 고유한 기술을 사용해 왔습니다. 양식에 매우 만족하지만 &quot;클래식&quot; 느낌, 모바일 디바이스에 대해 이상에 못 미치는 환경, 미래의 불확실한 실행 가능성 및 코드를 작성하지 않고 다른 서비스에 연결할 때 항상 궁지에 빠짐 등의 제한 사항도 알고 있습니다.

Power Apps 팀은 이러한 문제 및 기타 많은 문제를 들었습니다. 더 나은 환경을 통합하고 기존 비즈니스 및 기술 능력을 활용하여 캔버스 앱을 만들 수 있도록 열심히 노력했습니다. Power Apps를 사용 하면 코드를 작성 하지 않고도 올바른 비즈니스 솔루션을 빠르게 빌드하고 배포할 수 있습니다.

**Power Apps에서 강력한 미래 사용**  
Power Apps는 추가 작업 없이 웹, SharePoint, Dynamics 365, 팀, Power BI 또는 모바일 장치에 배포할 수 있는 고성능 앱을 신속 하 게 빌드할 수 있도록 설계 된 SaaS (Software as a Service) 플랫폼입니다. 다른 사람에게 게시된 앱에 대한 URL을 제공하기만 하면 배포할 수 있기 때문에 업데이트 역시 쉽습니다.

**앱 공유**  
앱을 빌드한 다음, iOS 또는 Android 디바이스용으로 게시하려고 한 적이 있나요? 이는 복잡합니다. 두 번째 앱을 배포하거나 기존 앱을 업데이트하려면 사용자가 많은 단계를 수행해야 합니다. Power Apps와는 그렇지 않습니다. 사용자가 장치에 Power Apps Mobile을 설치 하 고 로그인 합니다. 그러면 사용자는 여러분이 사용자와 공유한 뛰어난 기능을 갖춘 앱을 전부 갖게 됩니다. 이후에 여러분이 공유한 앱을 업데이트하거나 사용자에게 새 앱을 푸시하는 경우 해당 앱이 사용자의 디바이스에 표시됩니다. 디바이스를 관리할 필요가 없는 모바일 앱은 여러분과 여러분의 비즈니스 성공을 위한 큰 자산입니다.

**모바일에 대해 말하기**  
Power Apps를 사용 하면 사용자의 모바일 장치 기능을 활용할 수 있습니다. 앱 내에서 가속, 카메라, 나침반, 연결 정보 및 위치 신호 모두에 대한 액세스 권한이 있습니다. 이를 통해 앱을 빌드하기 위한 모든 가능성의 세계를 열어 작업을 완수합니다. 물론, 터치 기능은 PowerApps에서 자동이며 앱을 빌드할 때 코드에 별도로 아무것도 추가하지 않습니다.

**기본 제공 가져오기**  
InfoPath를 사용하면 일반적으로 단일 소스에서 가져온 데이터로 작업합니다. 그러나 다른 소스(예: 다른 사이트 컬렉션의 SharePoint 목록)를 업데이트하거나 외부 서비스에 연결하려는 경우 일이 복잡해집니다. 숨김 코드와 같은 개념은 문제를 더 어렵게 만듭니다. Power Apps는 한 앱에서 여러 데이터 원본 및 서비스 연결을 사용할 수 있도록 설계 되었습니다. 현재 [200 개 이상의 커넥터](connections-list.md#all-standard-connectors) 는 Microsoft Office 365 및 Azure 서비스 (예: 전원 자동화 및 Dynamics 365)를 비롯 한 온-프레미스 및 클라우드 데이터의 조합을 지원 합니다. 또한 Dropbox, Google, Salesforce, Slack 및 기타 널리 사용되는 서비스 등 여러 타사 서비스에 연결할 수도 있습니다.

이제 원본 데이터가 존재했던 위치가 아니라 사용자가 귀하를 데려가는 위치의 크기를 조정하기 위한 솔루션을 빌드할 수 있습니다.

## <a name="power-apps-and-sharepoint-even-better-together"></a>Power Apps 및 SharePoint: 함께 개선

Power Apps는 두 가지 방법으로 SharePoint 환경을 개선 하는 데 유용한 도구입니다. SharePoint 목록에 대한 양식을 사용자 지정하거나 SharePoint 데이터를 사용해 작업하기 위한 독립 실행형 앱을 만들 수 있는 옵션이 있습니다.

사용자가 목록의 항목을 추가, 보기 또는 편집하는 방식을 사용자 정의하려는 경우 **SharePoint 양식 사용자 지정**이 매우 유용합니다. **형식 사용자 지정**을 클릭하면 컨텍스트에 따라 모드(새로 만들기/편집/보기)가 변경되는 단일 화면 &quot;Forms 앱&quot;을 만듭니다. 이러한 앱은 SharePoint에서 관리하며, 해당 사용 권한은 편집/보기를 위한 목록 사용 권한과 동일합니다.

**SharePoint에서 Power Apps canvas 앱을 만들면** 모바일 장치에서 앱을 실행할 수 있습니다. SharePoint 페이지에 앱을 포함할 수도 있습니다. 이 옵션을 클릭하면 3개 화면 앱(목록 찾아보기, 세부 정보 보기 및 항목 만들기/업데이트)이 생성됩니다. 이러한 앱에 대한 사용 권한/공유 모델은 SharePoint에 연결되지 않고 대신 PowerApps에서 관리됩니다.

두 옵션 간의 차이를 이해했으므로 다음 섹션에서는 각 옵션의 사용에 대한 개요를 제공합니다.

## <a name="sharepoint-forms"></a>SharePoint 양식

Power Apps와 SharePoint 팀은 함께 작업 하 여 SharePoint에서 사용할 사용자 지정 스토리를 만들었습니다. 대부분의 InfoPath 개발자와 비슷하다면 여러분은 InfoPath가 SharePoint와 상호 작용하는 방법을 배웠을 것입니다. SharePoint가 뛰어나긴 하지만 기본 양식이 약간 평범하며 InfoPath가 없으면 사용자 지정 또는 비즈니스 논리를 사용할 수 없습니다. 그것은 이전 방식입니다.

이제 Power Apps를 사용 하 여 목록 양식을 네이티브 기능으로 사용자 지정할 수 있습니다. 이렇게 하면 Power Apps의 모든 기능을 활용할 수 있습니다. 아래 스크린샷에서는 Power BI 보고서가 포함 된 Power Apps 양식의 예를 볼 수 있습니다. 전체 솔루션은 15분 이내에 수행되었습니다.

![SharePoint 통합](./media/transform-infopath/sharepoint-integration.png)

Power Apps의 또 다른 중요 한 기능은 동일한 양식에서 다른 SharePoint 사이트 컬렉션 또는 다른 환경에 쉽게 연결할 수 있는 기능입니다. 예를 들어 SharePoint Online 및 SharePoint 온-프레미스 환경에서 동시에 데이터를 업데이트하고 표시하는 한 가지 양식을 만들기를 원합니까? 문제 없어요. 온 [-프레미스 데이터 게이트웨이](gateway-management.md)를 설치 하는 경우 몇 분 내에 실행 되며, power Apps, Power BI, 파워 자동화 및 Azure Logic Apps를 온-프레미스 데이터와 연결 합니다. 방화벽 규칙을 변경할 필요가 없습니다. 이 앱을 전원 자동화로 연결 하 여 단계를 더 진행할 수 있습니다.

## <a name="a-standalone-sharepoint-app"></a>독립 실행형 SharePoint 앱

목록 양식을 업데이트하지 않고 SharePoint 데이터를 기반으로 한 완전한 독립 실행형 앱을 빌드하려는 경우 이 기술을 사용합니다. 이를 시작 하는 것이 가장 좋은 방법 이기도 하므로, Power Apps canvas가 작동 하는 방식에 대해 알아보고, 데이터 원본의 만들게에서 이후 앱을 빌드하는 것을 시작할 수 있습니다.

시작하려면 다음 단계를 수행하세요.

1. 앱을 빌드할 SharePoint 목록을 엽니다.
1. 메뉴 모음에서 **PowerApps**를 선택한 다음, **앱 만들기**를 선택합니다.
1. 이름을 입력한 다음, **만들기**를 선택합니다.

Power Apps는 사용자 지정할 수 있는 앱을 빌드합니다.

첫 번째 앱에 지정할 수 있는 다른 유형을 나타내는 필드 한 쌍만 포함된 간단한 사용자 지정 목록으로 시작합니다. 그러면 전복되지 않는 견고한 토대를 빌드할 수 있습니다. 걱정하지 마세요. 순식간에 전문가가 되어 복잡한 앱을 만들어 낼 수 있습니다. 첫 번째 앱을 간단히 실행하기 위한 도움말은 이 [설명서](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) 또는 이 커뮤니티 [비디오](https://youtu.be/BnYe_7fpZRM)를 확인하세요. 아래 예제에서는 일반적인 InfoPath 작업 및이 작업을 Power Apps에서 수행 하는 방법을 보여 줍니다. 이들 각각의 예는 간단한 SharePoint 목록 앱에서 수행한 것입니다.

## <a name="how-do-you-do-that-with-power-apps"></a>Power Apps를 사용 하 여 어떻게 해야 하나요?

이제 기본 개념을 이해했으니 더 자세히 들어가 봅시다. 첫 번째 앱을 만들었으면, 이 섹션은 PowerApps에서 일반 InfoPath 개념 중 일부를 적용하는 데 도움이 될 것입니다.

**값에 따라 필드 숨기기/표시/잠그기**  
성공한 양식은 종종 강력한 비즈니스 로직(예: 값 또는 작업을 기반으로 필드의 상태 변경)을 강제로 적용합니다. Power Apps를 사용 하면 컨트롤의 **DisplayMode** 속성을 **편집** 또는 **보기** 로 설정 하 여 사용자가 필드를 변경할 수 있는지 여부를 지정할 수 있습니다. 또한 간단한 **If** 수식을 사용하여 조건부로 지정할 수도 있습니다. 먼저 편집할 카드를 선택한 다음, 잠금 아이콘을 선택합니다. 이 단계에서는 값을 변경할 수 있도록 카드의 잠금을 해제합니다.

![잠금 데이터 카드 표시 숨기기](./media/transform-infopath/hide-show-lock.png)

오른쪽 창에서 편집할 수 있도록 **DisplayMode** 속성으로 스크롤합니다.

![If Else Statement 식](./media/transform-infopath/if-else-statement.png)

이 예에서는 다음과 같이 **If** 수식을 사용합니다.

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

이 수식에 따르면, 현재 항목의 **Color** 필드는 **Blue**이고, **Animal** 필드는 읽기 전용입니다. 읽기 전용이 아니라면 이 필드는 편집 가능합니다.

읽기 전용으로 만드는 대신 카드를 숨기려면 **DisplayMode** 오른쪽 위에 있는 **Visible** 속성에 유사한 함수를 삽입합니다.

또한, 예를 들어 사용자의 메일 주소가 승인자의 메일 주소와 일치하는 경우에만 승인 단추를 표시하도록 할 수도 있습니다. (힌트: **User ()를 사용 합니다. 전자 메일** 을 사용 하 여 현재 사용자의 전자 메일 주소에 액세스 합니다. 따라서 사람의 전자 메일 **주소를 해당 위치에 저장** 한 후 단추의 **표시** 속성을 다음 수식으로 설정할 수 있습니다.

```If( YourDataCard.Text = User().Email, true, false )```

**조건부 서식**  
필드를 숨긴 위의 경우와 비슷한 방식으로 사용자에게 시각적 피드백을 제공할 수도 있습니다. 입력한 값이 허용 가능한 범위를 벗어나는 경우 빨간색으로 텍스트를 강조 표시하거나 사용자가 파일을 업로드한 후에는 업로드 단추의 텍스트 및 색상을 변경하려고 할 수 있습니다. **Color** 또는 **Visible**과 같은 속성에서 **If** 등의 함수를 사용하면 이 두 작업을 모두 수행할 수 있습니다.

예를 들어, [IsMatch](functions/function-ismatch.md) 함수와 짝을 이루는 **If** 함수를 사용하면 사용자가 입력 상자에 올바른 형식의 메일을 입력하지 않은 경우 메일 필드의 텍스트 색을 빨간색으로 변경할 수 있습니다. (사용자가 메일 주소를 입력하는) **TextInput1**의 **Color** 값을 이 수식에 설정해 이러한 기능을 구현할 수 있습니다.

```If( IsMatch(TextInput1.Text, Email), Black, Red )```

**IsMatch**는 메일과 같은 사전 정의된 다양한 패턴을 지원하는데, 고유한 조건부 서식을 만들 수도 있습니다. 조건부 서식에 관한 자세한 내용은 [커뮤니티 비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962)를 확인하세요.

**역할 기반 보안 구현**  
고려해야 할 첫 번째 함수는 [DataSourceInfo](functions/function-datasourceinfo.md)입니다. 데이터 원본에서 얻을 수 있는 정보는 다양하지만 일반적으로 이 수식을 사용하여 사용자에게 데이터를 편집할 액세스 권한이 있는지 여부를 확인할 수 있습니다(*YourDataSource*는 데이터 원본 이름으로 바꾸기).

```DataSourceInfo( YourDataSource, DataSourceInfo.EditPermission )```

이를 통해 사용자에게 편집 권한이 있는 경우에만 양식이나 단추를 표시할 수 있습니다. 함수에서 쿼리할 수 있는 정보의 전체 목록은 [DataSourceInfo](functions/function-datasourceinfo.md) 설명서를 확인하세요.

Active Directory 그룹을 사용하여 앱에 있는 단추 또는 양식에 대한 액세스 권한을 관리하는 것은 좀 더 복잡합니다. 이렇게 하려면 Power Apps의 유연성을 활용 하 고 Microsoft Graph API를 사용 하 여 사용자 고유의 커넥터를 만듭니다. 잘 이해가 안 되는 경우에는 [ 블로그 게시물](https://powerapps.microsoft.com/blog/implementing-role-based-permission/)의 단계별 지침을 따를 수 있습니다.

**앱에서 이메일 보내기**  
여러 가지 방법으로 Power Apps에서 전자 메일 메시지를 보낼 수 있지만 가장 쉬운 방법은 Office 365 Outlook 커넥터를 사용 하는 것입니다. 이 커넥터를 통해 앱에서 직접 메시지를 보낼 수 있습니다. 사서함과 상호 작용하는 이메일 메시지 및 기타 작업을 가져올 수도 있습니다. 메일을 보내는 방법이 나와 있는 [설명서](connections/connection-office365-outlook.md) 또는 커뮤니티 [비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349)도 준비되어 있습니다.

Power 자동화를 사용 하 고 앱을 만든 흐름에 연결 하 여 더 복잡 한 메시지 (예: SharePoint 승인 워크플로의 일부로)를 보낼 수 있습니다. 앱을 전원 자동화에 연결 하면 Power Apps와 같은 워크플로 엔진의 모든 기능을 외부 데이터 및 서비스에 매우 잘 연결 하 여 열었습니다. Power Apps 및 파워 자동화를 연결 하는 방법에 대 한 자세한 내용은이 [설명서](using-logic-flows.md)를 확인 하세요.

원하는 전자 메일 옵션을 아직 찾지 못한 경우 벤치 마크 메일, Gmail, MailChimp, Outlook.com, SendGrid 또는 SMTP에 대 한 Power Apps 커넥터를 활용할 수도 있습니다. PowerApps의 장점은 연결입니다.

**워크플로**  
워크플로 엔진 없이 비즈니스 논리 및 비즈니스 앱에 대해 설명하기는 어렵습니다. 좋은 소식은 Power Apps 팀이 휠을 알기 쉬운 하 고 다른 워크플로 엔진을 제공 하지 않았기 때문입니다. 대신, 강력한 커넥터를 전원 자동화 서비스에 제공 합니다. 사용하기 쉬운 워크플로 엔진을 통해 [200개가 넘는 다양한 서비스](https://flow.microsoft.com/connectors/)에서 프로세스 및 작업을 자동화할 수 있습니다. Power Apps 및 파워 자동화를 연결 하는 방법에 대 한 자세한 내용은이 [설명서](using-logic-flows.md)를 확인 하세요.

**PowerApps를 사용한 변수**  
솔루션을 빌드할 때는 변수 사용을 고려하는 것은 당연합니다. Power Apps는 여러 유형의 변수를 제공 하지만 필요한 경우에만 사용 합니다. 데이터를 가져와 변수에 데이터를 저장하고 해당 변수를 참조하는 것보다는 데이터를 직접 참조하는 방법을 고려해 보세요. Excel과 비교하면 이 모델을 더 잘 이해할 수 있습니다. Excel에서 총계는 변수가 아니라 다른 필드의 합계입니다. 따라서 시트의 다른 곳에 해당 값을 사용하려는 경우 총계를 계산한 셀을 지정합니다. 이 모든 내용에 대한 자세한 설명이 [설명서](working-with-variables.md)에 잘 나와 있습니다. 다른 사고 프로세스에 개방적이어야 합니다.

변수가 필요한 경우(변수가 필요한 경우가 많음) 이 설명서는 다양한 옵션을 이해하는 데 도움이 될 것입니다. Power Apps를 사용 하면 변수를 정의할 필요가 없다는 점에 유의 하세요. 저장할 이름 및 값을 지정하는 함수를 사용하면 변수가 생성됩니다. **보기** 탭에서 **변수** 를 선택 하 여 만든 변수를 볼 수 있습니다. 변수는 메모리에 저장 되며 해당 값은 앱을 닫을 때 손실 됩니다. 다음과 같은 유형의 변수를 만들 수 있습니다.

- 전역 변수는 가장 일반적으로 먼저 떠올리는 것입니다. [Set](functions/function-set.md) 함수를 사용하여 전역 변수 값을 지정하고 앱 전체에서 사용 가능하도록 설정합니다.

    ```Set( YourVariable, YourValue )```

    그러면 앱 전체에서 이름으로*YourVariable*을 참조할 수 있습니다.

- 컨텍스트 변수는 해당 변수가 정의된 화면에서만 사용할 수 있습니다. 화면을 종료하면 컨텍스트 변수는 다시 설정됩니다. 컨텍스트 변수는 예를 들어 이전 화면에서 전달된 정보를 저장하거나 양식을 전송했는지 추적하기 위해 종종 사용됩니다. 컨텍스트 변수를 설정하려면 다음 예제에서처럼 [UpdateContext](functions/function-updatecontext.md) 함수를 사용합니다.

    ```UpdateContext( { Submitted: "true" } )```

    이 예제에서는 **Submitted**라는 변수의 값을 **true**로 설정합니다. 이 수식을 제출 단추의 **OnSelect** 속성에 추가하여 정보가 제출되었음을 추적하고 모든 필드를 읽기 전용으로 변경할 수 있습니다.

- 컬렉션에는 개별적으로 업데이트가 가능한 정보 테이블이 저장됩니다. 사용자가 보내고 싶은 다양한 SharePoint 항목에 태그를 지정할 수 있기 때문에 [Collect](functions/function-clear-collect-clearcollect.md)를 사용해 장바구니를 생성할 수 있습니다. 커뮤니티 [비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180)에는 이러한 개념의 예가 나와 있습니다.

**계단식 드롭다운**  
계단식 드롭다운은 예를 들어, 이전 드롭다운에서 선택한 값에 따라 드롭다운의 선택 항목을 필터링할 수 있기 때문에 매우 유용합니다. Power Apps에서 이러한 응용 프로그램은 종종 응용 프로그램에 두 개의 데이터 원본을 포함 하 여 생성 됩니다. 첫 번째 데이터 원본은 보거나 업데이트하는 데이터이고, 두 번째 데이터 원본은 연쇄적인 효과를 빌드하기 위한 값을 저장합니다. 다음 그림은 선택 옵션이 있는 두 번째 데이터 원본의 예입니다.

![계단식 드롭다운](./media/transform-infopath/cascading-dropdowns.png)

이 예에서는 **ddSelectType**이라는 드롭다운을 추가하고 이 드롭다운의 **Items** 속성을 다음 수식으로 설정할 수 있습니다.

```Distinct( Impacts, Title )```

이 드롭다운에는 Cost, Program Impact 및 Schedule만 표시됩니다. 그런 다음, 두 번째 드롭다운을 추가하고 **Items** 속성을 다음 수식으로 설정할 수 있습니다.

```Filter( Impacts, ddSelectType.Selected.Value in SCategory )```

계단식 드롭다운이 있는 것처럼 설정합니다. 자세한 내용은 Power Apps 팀 SharePoint에서이 게시물을 확인 하세요 [. 4 개의 간단한 단계에서 계단식 드롭다운](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) 또는 이 [커뮤니티 비디오](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)를 참조하세요. 걱정하지 마세요. SharePoint 없이 쉽게 해낼 수 있습니다.

**하나의 슈퍼 앱 빌드하지 않기**  
Power Apps를 사용 하면 다른 앱에서 한 앱을 호출할 수 있습니다. 따라서 대용량 InfoPath 양식을 대충 구성하여 사용하기보다는 서로 호출하고 데이터를 주고받기까지 하는 앱 그룹을 빌드할 수 있으므로 더욱 간단하게 개발할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 항목의 Power Apps 및 정보를 사용 하 여 이제 전 세계로 이동 하 여 한 번에 하나의 앱을 다시 사용 하기 시작할 준비가 되었습니다. 경험을 계속 진행 하면서 Power Apps 커뮤니티 사이트에 대 한 링크와 같은 도움말에 대 한 몇 가지 유용한 링크를 제공 합니다. 오늘 커뮤니티에 참여해 보세요. 혼자 하는 것보다 훨씬 더 빨리 기술이 향상됩니다.

[**수식 참조** ](formula-reference.md) - 기본 함수 중 몇 가지를 탐색하기만 해도 영감을 받는 언제나 좋은 방법입니다.

[**Power apps 커뮤니티**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) -예제를 참조 하 고, 다른 사용자와 협력 하 고, 질문 및 답변 하 고, Power apps 커뮤니티의 성장에 도움을 줍니다.
