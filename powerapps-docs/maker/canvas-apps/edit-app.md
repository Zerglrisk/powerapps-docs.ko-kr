---
title: 앱 편집 | Microsoft Docs
description: 앱 편집 및 세션 잠금 시나리오에 대한 단계별 지침입니다.
services: ''
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/19/2017
ms.author: sharik
ms.openlocfilehash: a71aa71ec80a60f2aec4ce179abcade3f9eef964
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2018
---
# <a name="edit-an-app-in-powerapps"></a>PowerApps에서 앱 편집
빌드하거나 소유하거나 **편집할 수 있는** 사용 권한이 있는 앱을 편집합니다. 웹용 PowerApps Studio 또는 Windows용 PowerApps Studio에서 앱을 편집할 수 있습니다. 다른 위치에서 편집을 위해 열려 있는 앱을 편집하려고 하면 이미 열려 있거나 다른 사용자가 사용 중인지 여부를 알리는 메시지가 표시됩니다.

## <a name="verify-your-permissions"></a>사용 권한 확인
1. [PowerApps](https://web.powerapps.com)에 로그인한 다음, **파일** 메뉴(왼쪽 모서리)에서 **앱**을 클릭하거나 탭합니다.
   
    ![파일 메뉴의 앱 옵션](./media/edit-app/file-apps.png)
2. 앱 범주 선택기를 연 다음, **소유한 앱** 또는 **기여한 앱** 중 하나를 클릭하거나 탭합니다.
   
    ![앱 범주 선택기](./media/edit-app/app-category.png)
   
    표시되는 목록에서 원하는 앱을 편집할 수 있습니다. 또한 오른쪽 위 모서리 근처에 있는 검색 상자에 하나 이상의 문자를 입력하여 앱을 검색할 수 있습니다.
   
    > [!NOTE]
> 편집하려는 앱이 여전히 표시되지 않으면 오른쪽 위 모서리 근처에서 올바른 환경을 선택했는지 확인합니다.
   
    ![환경 목록](./media/edit-app/environment-list.png)

## <a name="edit-an-app-in-powerapps-studio-for-web"></a>웹용 PowerApps Studio에서 앱 편집
1. 이전 절차의 단계에 따라 편집할 앱을 찾습니다.
2. 오른쪽 가장자리 근처에 있는 앱 정보 아이콘을 클릭하거나 탭합니다.
   
    ![정보 아이콘](./media/edit-app/app-edit.png)
3. 오른쪽 위 모서리 근처에 있는 **편집** 아이콘을 클릭하거나 탭한 다음, **웹에서 편집**을 클릭하거나 탭합니다.
   
    ![편집 아이콘](./media/edit-app/edit-icon.png)

## <a name="edit-an-app-in-powerapps-studio-for-windows"></a>웹용 PowerApps Studio에서 앱 편집
1. Windows용 PowerApps Studio를 엽니다.
2. 기본적으로 표시되는 페이지에서 편집하려는 앱을 찾습니다.
   
    앱을 더 쉽게 찾으려면 오른쪽 위 모서리 근처에서 검색 아이콘을 클릭하거나 탭한 다음, 앱의 이름에 하나 이상의 문자를 입력합니다. 또한 이름, 가장 최근에 수정한 날짜 또는 가장 최근에 연 날짜를 기준으로 목록을 정렬할 수 있습니다. 원하는 앱이 계속 표시되지 않으면 첫 번째 절차에 설명된 대로 현재 있는 오른쪽 PowerApps 환경을 확인합니다.
   
    ![](./media/edit-app/sort-filter.png)
3. 오른쪽 가장자리 근처에서 편집할 앱에 대한 연필 아이콘을 클릭하거나 탭합니다.
   
    연필 아이콘이 회색이 아닌 검정색인 앱을 편집할 수 있습니다.
   
    ![](./media/edit-app/app-editstudio.png)

## <a name="collaborate-on-an-app"></a>앱에 대한 공동 작업
앱에 대해 **편집 가능** 권한이 있는 사용자는 누구든지 앱을 편집할 수 있습니다. 단, 한 명의 사용자가 한 번에 하나의 앱만 편집할 수 있습니다. 다른 사람이 이미 편집 중인 앱을 편집하려고 하는 경우 이 메시지가 표시됩니다. 다른 사람이 앱을 닫을 때까지는(또는 사용자의 세션 제한 시간이 초과) 계속할 수 없습니다.

![](./media/edit-app/applock-otheruser.png)

또한 편집을 위해 앱을 연 다음, 다른 장치나 다른 브라우저 창에서 열려고 하는 경우에도 이 메시지가 나타납니다. 이전 세션을 재정의할 수 있지만 저장하지 않은 변경 내용이 손실될 수 있습니다.

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>다음 단계
[화면](add-screen-context-variables.md), [컨트롤](add-configure-controls.md) 또는 [데이터 연결](add-data-connection.md)을 추가하는 방법에 대해 알아봅니다.

