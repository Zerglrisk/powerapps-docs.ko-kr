---
title: Office 365 사용자 연결 개요 | Microsoft Docs
description: Office 365 사용자에 연결하는 방법을 알아보고 몇 가지 예제를 진행하고, 모든 함수를 살펴봅니다.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: da6c30cc824f5bb6cf1f661d332831223c37d5b8
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993894"
---
# <a name="connect-to-office-365-users-connection-from-powerapps"></a>PowerApps에서 Office 365 사용자 연결
![Office 365 사용자](./media/connection-office365-users/office365icon.png)

Office 365 사용자를 통해 Office 365 계정을 사용하여 조직의 사용자 프로파일에 액세스할 수 있습니다. 프로필, 사용자 프로필, 사용자의 관리자 또는 직속 부하의 정보 가져오기 등 다양한 작업을 수행할 수 있습니다.

앱의 레이블에 이 정보를 표시할 수 있습니다. 하나의 함수, 여러 함수를 표시할 수 있고 다양한 기능을 조합할 수도 있습니다. 예를 들어, 사용자 이름 및 전화 번호를 결합하는 식을 만들고 앱에서 이 정보를 표시할 수 있습니다.

이 토픽에서는 앱에 Office 365 사용자를 연결 및 데이터 원본으로 추가하는 방법과 갤러리 컨트롤에서 테이블 데이터를 사용하는 방법을 설명합니다.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>연결 추가
1. [데이터 연결을 추가](../add-data-connection.md)하고 **Office 365 사용자**를 선택합니다.  

    ![Office 365에 연결](./media/connection-office365-users/add-office.png)
2. **연결**을 선택하고 로그인하라는 메시지가 표시되면 회사 계정을 입력합니다.

Office 365 사용자 연결이 만들어지고 앱에 추가됩니다. 이제 사용할 수 있습니다.

## <a name="use-the-connection-in-your-app"></a>앱에서 연결 사용
### <a name="show-information-about-the-current-user"></a>현재 사용자에 대한 정보 표시
1. **삽입** 메뉴에서 **레이블**을 선택합니다.
2. 함수 막대에서 다음 수식 중 하나에 **[Text](../controls/properties-core.md)** 속성을 설정합니다.

   `Office365Users.MyProfile().City`  
   `Office365Users.MyProfile().CompanyName`  
   `Office365Users.MyProfile().Country`  
   `Office365Users.MyProfile().Department`  
   `Office365Users.MyProfile().DisplayName`  
   `Office365Users.MyProfile().GivenName`  
   `Office365Users.MyProfile().Id`  
   `Office365Users.MyProfile().JobTitle`  
   `Office365Users.MyProfile().Mail`  
   `Office365Users.MyProfile().MailNickname`  
   `Office365Users.MyProfile().mobilePhone`  
   `Office365Users.MyProfile().OfficeLocation`  
   `Office365Users.MyProfile().PostalCode`  
   `Office365Users.MyProfile().Surname`  
   `Office365Users.MyProfile().TelephoneNumber`  
   `Office365Users.MyProfile().UserPrincipalName`  
   `Office365Users.MyProfile().AccountEnabled`  
   `Office365Users.MyProfile().BusinessPhones`

레이블에 현재 사용자에 대해 입력한 정보가 표시됩니다.

### <a name="show-information-about-another-user"></a>다른 사용자에 대한 정보 표시
1. **삽입** 메뉴에서 **텍스트 상자**를 선택한 다음 **텍스트 입력**을 선택합니다. **InfoAbout**로 이름을 바꿉니다.  

    ![컨트롤 이름 바꾸기](./media/connection-office365-users/renameinfoabout.png)
2. **InfoAbout**에 조직의 사용자 전자 메일 주소를 입력하거나 붙여넣습니다. 예를 들어 *yourName*@*yourCompany.com*으로 입력합니다.
3. **레이블**(**삽입** 메뉴)를 추가하고 다음 수식 중 하나에 **[Text](../controls/properties-core.md)** 속성을 설정합니다.

   * 다른 사용자에 대한 정보 표시:  

     `Office365Users.UserProfile(InfoAbout.Text).City`  
     `Office365Users.UserProfile(InfoAbout.Text).CompanyName`  
     `Office365Users.UserProfile(InfoAbout.Text).Country`  
     `Office365Users.UserProfile(InfoAbout.Text).Department`  
     `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
     `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
     `Office365Users.UserProfile(InfoAbout.Text).Id`  
     `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
     `Office365Users.UserProfile(InfoAbout.Text).Mail`  
     `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
     `Office365Users.UserProfile(InfoAbout.Text).mobilePhone`  
     `Office365Users.UserProfile(InfoAbout.Text).OfficeLocation`  
     `Office365Users.UserProfile(InfoAbout.Text).PostalCode`  
     `Office365Users.UserProfile(InfoAbout.Text).Surname`  
     `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
     `Office365Users.UserProfile(InfoAbout.Text).BusinessPhones`

   * 다른 사용자의 관리자에 대한 정보 표시:  

     `Office365Users.Manager(InfoAbout.Text).City`  
     `Office365Users.Manager(InfoAbout.Text).CompanyName`  
     `Office365Users.Manager(InfoAbout.Text).Country`  
     `Office365Users.Manager(InfoAbout.Text).Department`  
     `Office365Users.Manager(InfoAbout.Text).DisplayName`  
     `Office365Users.Manager(InfoAbout.Text).GivenName`  
     `Office365Users.Manager(InfoAbout.Text).Id`  
     `Office365Users.Manager(InfoAbout.Text).JobTitle`  
     `Office365Users.Manager(InfoAbout.Text).Mail`  
     `Office365Users.Manager(InfoAbout.Text).MailNickname`  
     `Office365Users.Manager(InfoAbout.Text).mobilePhone`  
     `Office365Users.Manager(InfoAbout.Text).OfficeLocation`  
     `Office365Users.Manager(InfoAbout.Text).PostalCode`  
     `Office365Users.Manager(InfoAbout.Text).Surname`  
     `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  
     `Office365Users.Manager(InfoAbout.Text).BusinessPhones`

레이블에 지정한 사용자 또는 해당 사용자의 관리자에 대해 입력한 정보가 표시됩니다.

> [!NOTE]
> Common Data Service에서 엔터티를 기반으로 하는 앱을 개발하는 경우 이메일 주소 대신 ID를 기준으로 사용자를 지정할 수 있습니다.

예를 들어, [앱을 자동으로 만들고](../data-platform-create-app.md), **레이블** 컨트롤이 포함된 화면을 추가하고, 이 수식에 컨트롤의 **Text** 속성을 설정할 수 있습니다.
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

연락처를 만들고 앱의 찾아보기 화면에서 해당 연락처를 선택하면 **레이블** 컨트롤에 표시 이름이 나타납니다.

### <a name="show-the-direct-reports-of-another-user"></a>다른 사용자의 직속 부하 표시
1. **텍스트 입력** 컨트롤을 추가하고(**삽입** 메뉴 > **텍스트**), 이름을 **InfoAbout**으로 바꿉니다.
2. **InfoAbout**에 조직의 사용자 전자 메일 주소를 입력합니다. 예를 들어 *yourManagersName*@*yourCompany.com*으로 입력합니다.
3. **텍스트 추가** 갤러리를 추가하고(**삽입** 메뉴 > **갤러리**) 다음 수식에 **[Items](../controls/properties-core.md)** 속성을 설정합니다.

    `Office365Users.DirectReports(InfoAbout.Text)`

    갤러리에 사용자의 직속 부하에 대해 입력한 정보가 표시됩니다.

    선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
4. 두 번째 목록에서 **JobTitle**을 선택합니다. 세 번째 목록에서 **DisplayName**을 선택합니다. 갤러리에서 이러한 값을 표시하도록 업데이트됩니다.  

> [!NOTE]
> 실제로 첫 번째 상자는 이미지 컨트롤입니다. 이미지를 설정하지 않은 경우 이미지 컨트롤을 삭제하고 그 자리에 레이블을 추가할 수 있습니다. [컨트롤을 추가하고 구성](../add-configure-controls.md)하는 것은 좋은 리소스입니다.

### <a name="search-for-users"></a>사용자 검색
1. **텍스트 입력** 컨트롤을 추가하고(**삽입** 메뉴 > **텍스트**), **SearchTerm**으로 이름을 바꿉니다. 검색할 이름을 입력합니다. 예를 들어 성을 제외한 이름을 입력합니다.
2. **텍스트 추가** 갤러리를 추가하고(**삽입** 메뉴 > **갤러리**) 다음 수식에 **[Items](../controls/properties-core.md)** 속성을 설정합니다.

    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`

    갤러리에 입력한 검색 텍스트를 포함한 이름이 표시됩니다.

    선택한 갤러리의 오른쪽 창에는 해당 갤러리 옵션이 나와 있습니다.
3. 두 번째 목록에서 **Mail**을 선택합니다. 세 번째 목록에서 **DisplayName**을 선택합니다.

    갤러리의 두 번째와 세 번째 레이블이 업데이트됩니다.

## <a name="view-the-available-functions"></a>사용할 수 있는 함수 보기
이 연결에는 다음 함수가 포함됩니다.

| 함수 이름 | 설명 |
| --- | --- |
| [DirectReports](connection-office365-users.md#directreports) |지정 된 사용자에 대 한 부하 직원을 반환 합니다. |
| [Manager](connection-office365-users.md#manager) |지정 된 사용자의 관리자에 대 한 사용자 프로필을 검색 합니다. |
| [MyProfile](connection-office365-users.md#myprofile) |현재 사용자의 프로필을 검색 합니다. |
| [SearchUser](connection-office365-users.md#searchuser) |사용자 프로필의 검색 결과를 검색 합니다. |
| [UserProfile](connection-office365-users.md#userprofile) |특정 사용자 프로필을 검색 합니다. |

### <a name="myprofile"></a>MyProfile
내 프로필 가져오기: 현재 사용자의 프로필을 검색 합니다.

#### <a name="input-properties"></a>입력 속성
없음

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 유형 | 설명 |
| --- | --- | --- |
| 대도시 | 문자열 |사용자의 구/군/시입니다. |
| CompanyName | 문자열 |사용자의 회사입니다. |
| 해외 | 문자열 |사용자의 국가입니다. |
| Department |문자열 |사용자의 부서입니다. |
| DisplayName |문자열 |사용자의 표시 이름입니다. |
| GivenName |문자열 |사용자의 지정된 이름입니다. |
| ID입니다. |문자열 |사용자 id입니다. |
| JobTitle |문자열 |사용자의 직함입니다. |
| 메일 |문자열 |사용자의 전자 메일 ID입니다. |
| MailNickname |문자열 |사용자의 애칭입니다. |
| mobilePhone | 문자열 |사용자의 휴대폰입니다. |
| 위치 | 문자열 |사용자의 사무실 위치입니다.|
| PostalCode | 문자열 |사용자의 우편 번호입니다.|
| Surname |문자열 |사용자의 성입니다. |
| TelephoneNumber |문자열 |사용자의 전화 번호입니다. |
| UserPrincipalName |문자열 |사용자 계정 이름입니다. |
| AccountEnabled |부울 |플래그가 활성화된 계정입니다. |
| BusinessPhones | 문자열 |사용자 회사의 전화 번호입니다.|

### <a name="userprofile"></a>UserProfile
사용자 프로필 가져오기: 특정 사용자 프로필을 검색 합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| ID입니다. |문자열 |예 |사용자 계정 이름 또는 전자 메일 id입니다. |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 유형 | 설명 |
| --- | --- | --- |
| 대도시 | 문자열 |사용자의 구/군/시입니다. |
| CompanyName | 문자열 |사용자의 회사입니다. |
| 해외 | 문자열 |사용자의 국가입니다. |
| Department |문자열 |사용자의 부서입니다. |
| DisplayName |문자열 |사용자의 표시 이름입니다. |
| GivenName |문자열 |사용자의 지정된 이름입니다. |
| ID입니다. |문자열 |사용자 id입니다. |
| JobTitle |문자열 |사용자의 직함입니다. |
| 메일 |문자열 |사용자의 전자 메일 ID입니다. |
| MailNickname |문자열 |사용자의 애칭입니다. |
| Surname |문자열 |사용자의 성입니다. |
| TelephoneNumber |문자열 |사용자의 전화 번호입니다. |
| UserPrincipalName |문자열 |사용자 계정 이름입니다. |
| AccountEnabled |부울 |플래그가 활성화된 계정입니다. |
| BusinessPhones | 문자열 |사용자 회사의 전화 번호입니다.|

### <a name="manager"></a>Manager
관리자 가져오기: 지정 된 사용자의 관리자에 대 한 사용자 프로필을 검색 합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| ID입니다. |문자열 |예 |사용자 계정 이름 또는 전자 메일 id입니다. |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 유형 | 설명 |
| --- | --- | --- |
| 대도시 | 문자열 |사용자의 구/군/시입니다. |
| CompanyName | 문자열 |사용자의 회사입니다. |
| 해외 | 문자열 |사용자의 국가입니다. |
| Department |문자열 |사용자의 부서입니다. |
| DisplayName |문자열 |사용자의 표시 이름입니다. |
| GivenName |문자열 |사용자의 지정된 이름입니다. |
| ID입니다. |문자열 |사용자 id입니다. |
| JobTitle |문자열 |사용자의 직함입니다. |
| 메일 |문자열 |사용자의 전자 메일 ID입니다. |
| MailNickname |문자열 |사용자의 애칭입니다. |
| mobilePhone | 문자열 |사용자의 휴대폰입니다. |
| 위치 | 문자열 |사용자의 사무실 위치입니다.|
| PostalCode | 문자열 |사용자의 우편 번호입니다.|
| Surname |문자열 |사용자의 성입니다. |
| TelephoneNumber |문자열 |사용자의 전화 번호입니다. |
| UserPrincipalName |문자열 |사용자 계정 이름입니다. |
| AccountEnabled |부울 |플래그가 활성화된 계정입니다. |
| BusinessPhones | 문자열 |사용자 회사의 전화 번호입니다.|

### <a name="directreports"></a>DirectReports
부하 직원을 가져옵니다. 부하 직원을 가져옵니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| ID입니다. |문자열 |예 |사용자 계정 이름 또는 전자 메일 id입니다. |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 유형 | 설명 |
| --- | --- | --- |
| 대도시 | 문자열 |사용자의 구/군/시입니다. |
| CompanyName | 문자열 |사용자의 회사입니다. |
| 해외 | 문자열 |사용자의 국가입니다. |
| Department |문자열 |사용자의 부서입니다. |
| DisplayName |문자열 |사용자의 표시 이름입니다. |
| GivenName |문자열 |사용자의 지정된 이름입니다. |
| ID입니다. |문자열 |사용자 id입니다. |
| JobTitle |문자열 |사용자의 직함입니다. |
| 메일 |문자열 |사용자의 전자 메일 ID입니다. |
| MailNickname |문자열 |사용자의 애칭입니다. |
| mobilePhone | 문자열 |사용자의 휴대폰입니다. |
| 위치 | 문자열 |사용자의 사무실 위치입니다.|
| PostalCode | 문자열 |사용자의 우편 번호입니다.|
| Surname |문자열 |사용자의 성입니다. |
| TelephoneNumber |문자열 |사용자의 전화 번호입니다. |
| UserPrincipalName |문자열 |사용자 계정 이름입니다. |
| AccountEnabled |부울 |플래그가 활성화된 계정입니다. |
| BusinessPhones | 문자열 |사용자 회사의 전화 번호입니다.|

### <a name="searchuser"></a>SearchUser
사용자 검색: 사용자 프로필의 검색 결과를 검색 합니다.

#### <a name="input-properties"></a>입력 속성

| 이름 | 데이터 형식 | 필수 | 설명 |
| --- | --- | --- | --- |
| searchTerm |문자열 |아니요 |검색 문자열입니다. 적용 대상: 표시 이름, 이름, 성, 메일, 메일 애칭 및 사용자 계정 이름입니다. |

#### <a name="output-properties"></a>출력 속성

| 속성 이름 | 유형 | 설명 |
| --- | --- | --- |
| 대도시 | 문자열 |사용자의 구/군/시입니다. |
| CompanyName | 문자열 |사용자의 회사입니다. |
| 해외 | 문자열 |사용자의 국가입니다. |
| Department |문자열 |사용자의 부서입니다. |
| DisplayName |문자열 |사용자의 표시 이름입니다. |
| GivenName |문자열 |사용자의 지정된 이름입니다. |
| ID입니다. |문자열 |사용자 id입니다. |
| JobTitle |문자열 |사용자의 직함입니다. |
| 메일 |문자열 |사용자의 전자 메일 ID입니다. |
| MailNickname |문자열 |사용자의 애칭입니다. |
| mobilePhone | 문자열 |사용자의 휴대폰입니다. |
| 위치 | 문자열 |사용자의 사무실 위치입니다.|
| PostalCode | 문자열 |사용자의 우편 번호입니다.|
| Surname |문자열 |사용자의 성입니다. |
| TelephoneNumber |문자열 |사용자의 전화 번호입니다. |
| UserPrincipalName |문자열 |사용자 계정 이름입니다. |
| AccountEnabled |부울 |플래그가 활성화된 계정입니다. |
| BusinessPhones | 문자열 |사용자 회사의 전화 번호입니다.|

## <a name="helpful-links"></a>유용한 링크
* [사용 가능한 연결](../connections-list.md)을 모두 보세요.
* 앱에 [연결을 추가](../add-manage-connections.md)하는 방법을 알아보세요.

