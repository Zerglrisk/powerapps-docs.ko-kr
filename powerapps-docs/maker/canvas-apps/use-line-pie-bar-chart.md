---
title: 캔버스 앱에서 차트 만들기 | Microsoft Docs
description: PowerApps에서 캔버스 응용 프로그램의 꺾은 선형 차트, 원형 차트 또는 가로 막대형 차트로 데이터 범주 표시
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/23/2016
ms.author: lonu
ms.openlocfilehash: 63244a05d81f807609c965892f6a84e30577b490
ms.sourcegitcommit: e3f5a2bef64085d02aec82e62ff94ae8a4d01d24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39471147"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-powerapps"></a>PowerApps에서 꺾은선형, 원형 또는 막대형 차트로 데이터 표시

꺾은선형 차트, 원형 차트 및 가로 막대형 차트를 사용하여 캔버스 앱에 데이터를 표시합니다. 차트를 사용할 때 가져오는 데이터는 다음 기준에 따라 구성되어야 합니다.

* 각 시리즈는 첫 번째 행에 있어야 합니다.
* 맨 왼쪽 열에 레이블이 있어야 합니다.

예를 들어 데이터는 다음과 비슷하게 표시됩니다.

![][9]

PowerApps 내에서 이러한 차트를 만들고 사용할 수 없습니다. 이제 시작하겠습니다.

## <a name="prerequisites"></a>필수 조건

* PowerApps에 [등록](../signup-for-powerapps.md)한 다음, 등록에 사용한 동일한 자격 증명을 사용하여 [로그인](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)합니다.
* [템플릿](get-started-test-drive.md), [데이터](get-started-create-from-data.md)에서 앱을 만들거나 [처음부터](get-started-create-from-blank.md)만듭니다.
* PowerApps에서 [컨트롤 구성](add-configure-controls.md)을 어떻게 하는지 알아봅니다.
* 샘플 데이터가 XML 파일로 포함된 [ChartData.zip](http://pwrappssamples.blob.core.windows.net/samples/ChartData.zip)을 다운로드합니다. 이 항목의 단계를 수행하여 앱에 직접 가져옵니다. 대신 .zip 파일의 압축을 풀고, Excel에서 XML 파일을 열고, [클라우드 저장소 계정](connections/cloud-storage-blob-connections.md)에 저장합니다.

## <a name="import-the-sample-data"></a>샘플 데이터 가져오기
이 단계에서는 **ProductRevenue**라는 컬렉션에 샘플 데이터를 가져옵니다.

1. **삽입** 탭에서 **컨트롤**을 선택한 다음 **가져오기**를 선택합니다.  

    ![][11]  

2. 컨트롤의 **[OnSelect](controls/properties-core.md)** 속성을 다음 함수로 설정합니다.  

   ```Collect(ProductRevenue, Import1.Data)```

3. F5 키를 눌러 미리 보기 모드를 열고 **데이터 가져오기** 단추를 선택합니다.

4. **열기** 대화 상자에서 ChartData.zip을 선택하고 **열기**를 선택한 다음 Esc 키를 누릅니다.

5. **파일** 메뉴에서 **컬렉션**을 선택합니다.

    ProductRevenue 컬렉션은 가져온 차트 데이터와 함께 나열됩니다.

    ![][1]  

   > [!NOTE]
   > Excel과 같은 데이터를 가져오고 컬렉션을 만드는 데 가져오기 컨트롤을 사용합니다. 가져오기 컨트롤은 앱을 만들고 앱을 미리 볼 때 데이터를 가져옵니다. 현재는 앱을 게시할 때 가져오기 컨트롤에서 데이터를 가져오지 않습니다.
   >

6. 기본 작업 영역으로 돌아가려면 Esc 키를 누릅니다.

## <a name="add-a-pie-chart"></a>원형 차트 추가
1. **삽입** 탭에서 **차트**를 선택한 다음 **원형 차트**를 선택합니다.

2. **데이터 가져오기** 단추 아래에서 원형 차트로 이동합니다.

3. 원형 차트 컨트롤에서 원형 차트의 중심을 선택합니다.   

    ![][10]

4. 원형 차트의 **[항목](controls/properties-core.md)** 속성을 `ProductRevenue.Revenue2014` 식으로 설정합니다.

    ![][2]  

    원형 차트에서는 2014년의 수익 데이터를 보여줍니다.

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>데이터를 표시하는 가로 막대형 차트 추가
이제 가로 막대형 차트에서 이 ProductRevenue 컬렉션을 사용하겠습니다.

1. **홈** 탭에서 화면을 추가합니다.]

2. **삽입** 탭에서 **차트**를 선택한 다음 **세로 막대형 차트**를 선택합니다.

3. 세로 막대형 차트의 중심을 선택합니다. 세로 막대형 차트의 **[항목](controls/properties-core.md)** 속성을 ```ProductRevenue```로 설정합니다.

    ![][12]  

    세로 막대형 차트에서는 2012년의 수익 데이터를 보여줍니다.

    ![][4]  

4. 세로 막대형 차트에서 가운데 사각형을 선택합니다.

    ![][5]

5. **차트** 탭에서 **일련 번호**를 선택한 다음 수식 입력줄에서 **3**을 입력합니다.

    ![][6]  

    세로 막대형 차트는 3년 동안 각 제품에 대한 수익 데이터를 표시합니다.

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
