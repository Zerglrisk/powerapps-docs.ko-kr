---
title: Power Apps 포털에서 일반 데이터 보호 규정 구현 | MicrosoftDocs
description: Power Apps 포털에서 일반 데이터 보호 규정을 구현하는 방법을 알아봅니다.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6ab1f29eac3835ed1699c2656c39034480bd495d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866890"
---
# <a name="implementing-general-data-protection-regulations-in-your-power-apps-portals"></a>Power Apps 포털에서 일반 데이터 보호 규정 구현

일반 데이터 보호 규정(GDPR)은 EU 내의 모든 개인을 위해 데이터를 보호하는 유럽 연합(EU)의 법적 행위입니다. GDPR과 함께, 사람들은 Common Data Service에서 자신의 개인 데이터의 사용을 제어할 수 있습니다.

관리자는 GDPR 표준을 충족하도록 포털을 구성할 수 있습니다. 예를 들어 미성년자가 포털을 사용하려면 부모의 동의가 있어야 합니다. 포털을 사용하는 사용자에 대한 사용 약관을 설정할 수도 있습니다. 사용자는 포털을 사용하기 위해 사용 약관에 동의해야 합니다.

GDPR은 사용자의 개인 데이터 사용에 대한 포털 사용자들의 동의를 얻고 미성년 사용자를 식별하고 자녀에 대한 부모의 동의를 얻을 수 있도록 합니다.

## <a name="audit-logging"></a>감사 로깅

포털 연락처 레코드에서 **마지막으로 성공한 로그인** 필드는 포털 사용자가 마지막으로 로그인한 시간을 표시합니다. 이 날짜는 연락처 레코드의 감사에 의해 선택되며 해당 정보를 표준 감사 스트림에서 사용할 수 있게 합니다. 이렇게 하면 관리자가 비활성 커뮤니티 구성원을 확인하고 레코드를 삭제할 수 있습니다.

> [!NOTE]
> 로그인 추적 기능은 더 이상 사용되지 않습니다. Azure Application Insights와 같은 분석 기술을 사용하여 이러한 종류의 정보를 캡처하는 것이 좋습니다. 사용되지 않는 기능 목록을 보려면 [여기](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)를 클릭하십시오.

## <a name="identifying-minor-portal-users-and-obtaining-parental-consent"></a>미성년자 포털 사용자 확인 및 부모의 동의 획득

미성년자 식별 규정은 국가/지역별로 다릅니다. 미성년자는 보호자 동의가 있어야만 포털에 액세스할 수 있으므로 포털 연락처 레코드에서 이러한 필드를 사용하여 미성년자를 식별하도록 포털을 구성할 수 있습니다.
- **미성년자임**: 연락처가 해당 관할지에서 미성년자로 간주됨을 나타냅니다. 기본적으로 **아니요**가 선택됩니다.
- **부모 동의가 있는 미성년자임**: 연락처가 해당 관할지에서 미성년자로 간주되고 부모 동의를 얻었음을 나타냅니다. 기본적으로 **아니요**가 선택됩니다.

    ![미성년 포털 사용자 식별 및 부모의 동의 획득](../media/identify-minor-in-portal.png "미성년 포털 사용자 식별 및 부모의 동의 획득")

다음 사이트 설정은 미성년자 및 부모 동의가 없는 미성년자의 포털 사용을 제어합니다.

| 이름  | 설명   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | 미성년자의 포털 사용을 거부합니다. 기본적으로는 거짓으로 설정됩니다.                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | 부모 동의가 없는 미성년자가 이 포털을 사용하는 것을 거부합니다. 기본적으로는 거짓으로 설정됩니다. |
|||

포털 사용자가 미성년자임이 확인되고 포털이 미성년자를 차단하도록 구성된 경우 해당 메시지가 표시되고 콘텐츠가 표시되지 않습니다.

![연령 요구 사항 메시지](../media/gdpr-age-req.png "연령 요구 사항 메시지")

포털 사용자가 부모 동의가 없는 미성년자임이 확인되고 포털이 부모 동의가 없는 미성년자를 차단하도록 구성된 경우 해당 메시지가 표시되고 콘텐츠가 표시되지 않습니다.

![부모 동의 메시지](../media/gdpr-parental-consent.png "부모 동의 메시지")

다음 콘텐츠 조각은 미성년자 및 부모 동의가 없는 미성년자가 포털을 사용할 때 나타나는 메시지를 제어합니다. 요구 사항에 따라 메시지를 변경할 수 있습니다.

| 이름                                                        | 타입 | 값                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | 텍스트 | 연령 요구 사항                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML | 이 포털은 미성년자가 사용하기에 적합하지 않으며 허용되지 않습니다. |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | 텍스트 | 부모 동의                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML | 미성년자가 이 포털을 사용하려면 부모 동의가 필요합니다.              |
|||

사용자가 외부 공급자를 사용하여 등록하고 포털이 미성년자 또는 부모의 동의가 없는 미성년자를 차단하도록 구성된 경우에는 연락처 레코드가 만들어지지 않으며 사용자가 인증되지 않습니다.

## <a name="agreeing-to-terms-and-conditions"></a>사용 약관에 동의

GDPR에 따르면 포털 사용자는 마케팅, 프로파일링 또는 개인 정보에 대한 액세스를 허용하는 사용 약관에 동의해야 합니다. 관리자는 자신의 사용 약관을 게시하여 사이트에 인증되기 전에 포털 사용자의 동의를 받을 수 있습니다.

![포털 사용 약관](../media/gdpr-terms-agreement.png "포털 사용 약관")

다음 콘텐츠 조각은 화면에 표시되는 사용 약관을 제어합니다. 요구 사항에 따라 텍스트를 변경할 수 있습니다.

| 이름                                           | 타입 | 값                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | 텍스트 | 사용 약관                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | 텍스트 | 사용 약관에 동의함 |
| Account/Signin/TermsAndConditionsButtonText    | 텍스트 | 계속                              |
|||

`Account/Signin/TermsAndConditionsCopy` 콘텐츠 조각은 기본적으로 비어 있습니다. 포털 관리자는 이 콘텐츠 조각에 사용 약관을 입력해야 합니다.

다음 사이트 설정은 포털에 약관이 표시될 약관 게시 날짜를 제어합니다.

| 이름  | 설명 |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | 현재 게시된 사용 약관의 유효한 날짜를 나타내는 GMT 형식의 날짜/시간 값입니다. 약관 계약이 활성화된 경우 이 날짜 이후에 약관을 수락하지 않은 포털 사용자는 다음에 로그인할 때 수락하도록 요청 받습니다. 날짜가 제공되지 않고 사용 약관이 활성화된 경우 포털 사용자가 로그인할 때마다 약관이 표시됩니다. <br> **참고**: 포털 사용자가 로그인할 때마다 사용 약관에 동의하도록 하려면 이 사이트 설정에 대한 값을 제공하지 마십시오.|
| Authentication/Registration/TermsAgreementEnabled | True 또는 False 값. true로 설정하면 포털에 사이트의 사용 약관이 표시됩니다. 사용자가 인증된 것으로 간주되기 전에 사용 약관에 동의해야 하며 사이트를 사용할 수 있습니다. 기본적으로는 거짓으로 설정됩니다.        |
|||

포털 사용자가 사용 약관에 동의한 날짜와 시간을 저장하기 위해 포털 연락처 레코드에 다음 필드가 추가됩니다.
- **포털 약관 계약 날짜**: 사용자가 포털 사용 약관에 동의한 날짜와 시간을 나타냅니다.

    ![포털 약관 계약 날짜](../media/portal-terms-agreement.png "포털 사용 약관 계약 날짜")

### <a name="see-also"></a>참조

[ID 공급자를 Azure AD B2C로 마이그레이션](migrate-identity-providers.md)
