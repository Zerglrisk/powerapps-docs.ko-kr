---
title: Color 열거 및 ColorFade, ColorValue 및 RGBA 함수 | Microsoft Docs
description: 구문 및 예제를 포함하여 PowerApps에서 Color 열거 및 ColorFade, ColorValue 및 RGBA 함수에 대한 참조 정보
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4af851160ea8a2add22add9f79dcc181a734e715
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994862"
---
# <a name="color-enumeration-and-colorfade-colorvalue-and-rgba-functions-in-powerapps"></a>PowerApps에서 Color 열거 및 ColorFade, ColorValue 및 RGBA 함수

기본 제공 색 값을 사용 하 고, 사용자 지정 색을 정의 하 고, 알파 채널을 사용 합니다.

## <a name="description"></a>설명

**색** 열거를 사용 하 여 HTML CSS (CSS 스타일시트)에 정의 된 색에 쉽게 액세스할 수 있습니다. 예를 들어 **color.red** 는 순수한 red를 반환 합니다. 이 항목의 끝에서 이러한 색의 목록을 찾을 수 있습니다.

**Colorvalue** 함수는 CSS의 색 문자열을 기준으로 색을 반환 합니다. 문자열은 다음 형식을 사용할 수 있습니다.

- **CSS 색 이름:** **"RoxyBrown"** 및 **"Olivedrab"** 는 예입니다. 이러한 이름에는 공백이 포함 되지 않습니다. 지원 되는 색 목록은이 항목의 뒷부분에 나와 있습니다.
- **6 자리 16 진수 값:** 예를 들어 " **#ffd700"** 는 **"금색"** 과 같습니다. 문자열은 "#*rrggbb*" 형식입니다. 여기서 *rr* 은 두 16 진수 숫자의 빨간색 부분이 고, *gg* 는 녹색이 고, *bb* 는 파란색입니다.
- **8 자리 16 진수 값:** 예를 들어 **"#ff7f5080"** 는 50% 알파 채널이 있는 **"산호색"** 와 동일 합니다. 문자열은 "#*rrggbbaa*" 형식입니다. 여기서 *rr*, *gg*및 *bb* 는 6 자리 형태와 동일 합니다. 알파 채널은 *aa*로 표시 됩니다. **00** 은 완전히 투명 하 고 **ff** 는 완전히 불투명 하 게 나타냅니다.

**RGBA** 함수는 빨강, 녹색 및 파랑 구성 요소를 기준으로 색을 반환 합니다. 또한 함수는 서로 앞에 있는 컨트롤의 색을 혼합 하는 알파 채널을 포함 합니다. 알파 채널은 0 또는 0% (완전히 투명 하 고 보이지 않음)에서 1 또는 100% (완전히 불투명 하 고 컨트롤 뒤에 있는 모든 계층을 완전히 차단)에 따라 달라 집니다.

**ColorFade** 함수는 색의 밝거나 짙은 버전을 반환합니다. 페이드의 양은-1 (색을 검정으로 완전히 어둡게 함)에서 0 (색에 영향을 주지 않음)에서 1 (색을 흰색으로 완전히 밝게 함)까지 다릅니다.

## <a name="alpha-channel"></a>알파 채널

Canvas 앱에서 다른 컨트롤 앞에 컨트롤을 계층화 하 고 그 뒤에 있는 모든 컨트롤에 대 한 컨트롤의 투명도를 지정할 수 있습니다. 따라서 색은 계층을 통해 혼합 됩니다. 예를 들어 다음 다이어그램에서는 세 가지 기본 색이 알파 설정인 50%를 혼합 하 여 보여 줍니다.

> [!div class="mx-imgBorder"]
> @no__t 알파 설정이 50% ](media/function-colors/alpha-primary.png) 인 세 가지 기본 색

알파 채널을 지 원하는 파일 형식으로 이미지를 혼합할 수도 있습니다. 예를 들어 .jpeg 파일을 혼합할 수는 없지만 .png 파일을 혼합할 수 있습니다. 다음 그림은 이전 예제와 동일한 빨간색, 녹색 및 파란색을 보여 주지만, 빨강 색은 50% 알파 채널이 있는 .png 파일에 원 대신 물결선으로 표시 됩니다.

> [!div class="mx-imgBorder"]
> ![Red 물결선 (알파 설정 50%)이 파랑 및 녹색 원 앞에 있는 (no__t-1)

**색 열거형 값** 을 지정 하거나 색 이름이 나 6 자리 16 진수 값을 사용 하 여 **colorvalue** 수식을 작성 하는 경우 알파 설정은 완전히 불투명 한 100%입니다.

## <a name="syntax"></a>구문

**Color**.*ColorName*

- *ColorName* - 필수 항목입니다.  CSS(Cascading Style Sheet) 색 이름입니다. 가능한 열거형 값 목록은이 항목의 끝에 표시 됩니다.

**ColorValue**( *CSSColor* )

- *CSSColor* - 필수 항목입니다.  CSS(Cascading Style Sheet) 색 정의입니다. 이름 (예: **Olivedrab**) 또는 16 진수 값 (예: **#6b8e23** 또는 **#7fffd420**) 중 하나를 지정할 수 있습니다. 16 진수 값은 #*rrggbb* 또는 #*rrggbbaa*형식으로 사용할 수 있습니다.

**RGBA**( *Red*, *Green*, *Blue*, *Alpha* )

- *Red*, *Green*, *Blue* - 필수 항목입니다.  0 (채도 없음)에서 255 (전체 채도) 까지의 범위에 해당 하는 색 구성 요소 값입니다.
- *Alpha* - 필수 항목입니다.  알파 구성 요소입니다 .이 구성 요소는 0 (완전히 투명)에서 1 (완전히 불투명) 사이의 범위에 있습니다. 0%에서 100%까지 %를 사용할 수도 있습니다.

**ColorFade**( *Color*, *FadeAmount* )

- *Color* - 필수 항목입니다.  **Color.Red** 또는 **ColorValue** 또는 **RGBA**의 출력과 같은 색 값입니다.
- *FadeAmount* - 필수 항목입니다.  -1에서 1 사이의 숫자입니다. -1은 색을 검정으로 완전히 어둡게 하 고 0은 색에 영향을 주지 않으며 1은 색을 흰색으로 완전히 밝게 합니다. -100% ~ 100%의 백분율을 사용할 수도 있습니다.

## <a name="built-in-colors"></a>기본 제공 색

| 색 열거 | ColorValue | RGBA | 색 견본 |
| --- | --- | --- | --- |
| **Color.AliceBlue** |**ColorValue ("#f0f8ff" &nbsp;)**<br>**ColorValue ("aliceblue" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;248, &nbsp;255, &nbsp;1 @ NO__T)** |![aliceblue](./media/function-colors/color-aliceblue.png) |
| **Color.AntiqueWhite** |**ColorValue ("#faebd7" &nbsp;)**<br>**ColorValue ("AntiqueWhite" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;235, &nbsp;215, &nbsp;1 @ NO__T)** |![antiquewhite](./media/function-colors/color-antiquewhite.png) |
| **Color.Aqua** |**ColorValue ("#00ffff" &nbsp;)**<br>**ColorValue ("바다색" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T)** |![aqua](./media/function-colors/color-aqua.png) |
| **Color.Aquamarine** |**ColorValue ("#7fffd4" &nbsp;)**<br>**ColorValue ("청록" &nbsp;)** |**RGBA (&nbsp;127, &nbsp;255, &nbsp;212, &nbsp;1 @ NO__T)** |![aquamarine](./media/function-colors/color-aquamarine.png) |
| **Color.Azure** |**ColorValue ("#f0ffff" &nbsp;)**<br>**ColorValue ("azure" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T)** |![azure](./media/function-colors/color-azure.png) |
| **Color.Beige** |**ColorValue ("#f5f5dc" &nbsp;)**<br>**ColorValue ("베이 지" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;245, &nbsp;220, &nbsp;1 @ NO__T)** |![beige](./media/function-colors/color-beige.png) |
| **Color.Bisque** |**ColorValue ("#ffe4c4" &nbsp;)**<br>**ColorValue ("황갈색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;196, &nbsp;1 @ NO__T)** |![bisque](./media/function-colors/color-bisque.png) |
| **Color.Black** |**ColorValue ("#000000" &nbsp;)**<br>**ColorValue ("Black" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T)** |![black](./media/function-colors/color-black.png) |
| **Color.BlanchedAlmond** |**ColorValue ("#ffebcd" &nbsp;)**<br>**ColorValue ("blanchedalmond" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;235, &nbsp;205, &nbsp;1 @ NO__T)** |![blanchedalmond](./media/function-colors/color-blanchedalmond.png) |
| **Color.Blue** |**ColorValue ("#0000ff" &nbsp;)**<br>**ColorValue ("Blue" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T)** |![blue](./media/function-colors/color-blue.png) |
| **Color.BlueViolet** |**ColorValue ("#8a2be2" &nbsp;)**<br>**ColorValue ("BLUEVIOLET" &nbsp;)** |**RGBA (&nbsp;138, &nbsp;43, &nbsp;226, &nbsp;1 @ NO__T)** |![blueviolet](./media/function-colors/color-blueviolet.png) |
| **Color.Brown** |**ColorValue ("#a52a2a" &nbsp;)**<br>**ColorValue ("갈색" &nbsp;)** |**RGBA (&nbsp;165, &nbsp;42, &nbsp;42, &nbsp;1 @ NO__T)** |![brown](./media/function-colors/color-brown.png) |
| **Color.Burlywood** |**ColorValue ("#deb887" &nbsp;)**<br>**ColorValue ("burlywood" &nbsp;)** |**RGBA (&nbsp;222, &nbsp;184, &nbsp;135, &nbsp;1 @ NO__T)** |![burlywood](./media/function-colors/color-burlywood.png) |
| **Color.CadetBlue** |**ColorValue ("#5f9ea0" &nbsp;)**<br>**ColorValue ("CadetBlue" &nbsp;)** |**RGBA (&nbsp;95, &nbsp;158, &nbsp;160, &nbsp;1 @ NO__T)** |![cadetblue](./media/function-colors/color-cadetblue.png) |
| **Color.Chartreuse** |**ColorValue ("#7fff00" &nbsp;)**<br>**ColorValue ("CHARTREUSE" &nbsp;)** |**RGBA (&nbsp;127, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T)** |![chartreuse](./media/function-colors/color-chartreuse.png) |
| **Color.Chocolate** |**ColorValue ("#d2691e" &nbsp;)**<br>**ColorValue ("초콜릿" &nbsp;)** |**RGBA (&nbsp;210, &nbsp;105, &nbsp;30, &nbsp;1 @ NO__T)** |![chocolate](./media/function-colors/color-chocolate.png) |
| **Color.Coral** |**ColorValue ("#ff7f50" &nbsp;)**<br>**ColorValue ("산호색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;127, &nbsp;80, &nbsp;1 @ NO__T)** |![coral](./media/function-colors/color-coral.png) |
| **Color.CornflowerBlue** |**ColorValue ("#6495ed" &nbsp;)**<br>**ColorValue ("CornflowerBlue" &nbsp;)** |**RGBA (&nbsp;100, &nbsp;149, &nbsp;237, &nbsp;1 @ NO__T)** |![cornflowerblue](./media/function-colors/color-cornflowerblue.png) |
| **Color.Cornsilk** |**ColorValue ("#fff8dc" &nbsp;)**<br>**ColorValue ("옥수수 수염색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;248, &nbsp;220, &nbsp;1 @ NO__T)** |![cornsilk](./media/function-colors/color-cornsilk.png) |
| **Color.Crimson** |**ColorValue ("#dc143c" &nbsp;)**<br>**ColorValue ("크림슨" &nbsp;)** |**RGBA (&nbsp;220, &nbsp;20, &nbsp;60, &nbsp;1 @ NO__T)** |![crimson](./media/function-colors/color-crimson.png) |
| **Color.Cyan** |**ColorValue ("#00ffff" &nbsp;)**<br>**ColorValue ("녹청" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T)** |![cyan](./media/function-colors/color-cyan.png) |
| **Color.DarkBlue** |**ColorValue ("#00008b" &nbsp;)**<br>**ColorValue ("DarkBlue" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;139, &nbsp;1 @ NO__T)** |![darkblue](./media/function-colors/color-darkblue.png) |
| **Color.DarkCyan** |**ColorValue ("#008b8b" &nbsp;)**<br>**ColorValue ("DARKCYAN" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;139, &nbsp;139, &nbsp;1 @ NO__T)** |![darkcyan](./media/function-colors/color-darkcyan.png) |
| **Color.DarkGoldenRod** |**ColorValue ("#b8860b" &nbsp;)**<br>**ColorValue ("DarkGoldenRod" &nbsp;)** |**RGBA (&nbsp;184, &nbsp;134, &nbsp;11, &nbsp;1 @ NO__T)** |![darkgoldenrod](./media/function-colors/color-darkgoldenrod.png) |
| **Color.DarkGray** |**ColorValue ("#a9a9a9" &nbsp;)**<br>**ColorValue ("진한 회색" &nbsp;)** |**RGBA (&nbsp;169, &nbsp;169, &nbsp;169, &nbsp;1 @ NO__T)** |![darkgray](./media/function-colors/color-darkgray.png) |
| **Color.DarkGreen** |**ColorValue ("#006400" &nbsp;)**<br>**ColorValue ("DarkGreen" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;100, &nbsp;0, &nbsp;1 @ NO__T)** |![darkgreen](./media/function-colors/color-darkgreen.png) |
| **Color.DarkGrey** |**ColorValue ("#a9a9a9" &nbsp;)**<br>**ColorValue ("DARKGREY" &nbsp;)** |**RGBA (&nbsp;169, &nbsp;169, &nbsp;169, &nbsp;1 @ NO__T)** |![darkgrey](./media/function-colors/color-darkgrey.png) |
| **Color.DarkKhaki** |**ColorValue ("#bdb76b" &nbsp;)**<br>**ColorValue ("DarkKhaki" &nbsp;)** |**RGBA (&nbsp;189, &nbsp;183, &nbsp;107, &nbsp;1 @ NO__T)** |![darkkhaki](./media/function-colors/color-darkkhaki.png) |
| **Color.DarkMagenta** |**ColorValue ("#8b008b" &nbsp;)**<br>**ColorValue ("darkmagenta" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;0, &nbsp;139, &nbsp;1 @ NO__T)** |![darkmagenta](./media/function-colors/color-darkmagenta.png) |
| **Color.DarkOliveGreen** |**ColorValue ("#556b2f" &nbsp;)**<br>**ColorValue ("DarkOliveGreen" &nbsp;)** |**RGBA (&nbsp;85, &nbsp;107, &nbsp;47, &nbsp;1 @ NO__T)** |![darkolivegreen](./media/function-colors/color-darkolivegreen.png) |
| **Color.DarkOrange** |**ColorValue ("#ff8c00" &nbsp;)**<br>**ColorValue ("DARKORANGE" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;140, &nbsp;0, &nbsp;1 @ NO__T)** |![darkorange](./media/function-colors/color-darkorange.png) |
| **Color.DarkOrchid** |**ColorValue ("#9932cc" &nbsp;)**<br>**ColorValue ("DarkOrchid" &nbsp;)** |**RGBA (&nbsp;153, &nbsp;50, &nbsp;204, &nbsp;1 @ NO__T)** |![darkorchid](./media/function-colors/color-darkorchid.png) |
| **Color.DarkRed** |**ColorValue ("#8b0000" &nbsp;)**<br>**ColorValue ("darkred" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T)** |![darkred](./media/function-colors/color-darkred.png) |
| **Color.DarkSalmon** |**ColorValue ("#e9967a" &nbsp;)**<br>**ColorValue ("DarkSalmon" &nbsp;)** |**RGBA (&nbsp;233, &nbsp;150, &nbsp;122, &nbsp;1 @ NO__T)** |![darksalmon](./media/function-colors/color-darksalmon.png) |
| **Color.DarkSeaGreen** |**ColorValue ("#8fbc8f" &nbsp;)**<br>**ColorValue ("DARKSEAGREEN" &nbsp;)** |**RGBA (&nbsp;143, &nbsp;188, &nbsp;143, &nbsp;1 @ NO__T)** |![darkseagreen](./media/function-colors/color-darkseagreen.png) |
| **Color.DarkSlateBlue** |**ColorValue ("#483d8b" &nbsp;)**<br>**ColorValue ("DarkSlateBlue" &nbsp;)** |**RGBA (&nbsp;72, &nbsp;61, &nbsp;139, &nbsp;1 @ NO__T)** |![darkslateblue](./media/function-colors/color-darkslateblue.png) |
| **Color.DarkSlateGray** |**ColorValue ("#2f4f4f" &nbsp;)**<br>**ColorValue ("darkslategray" &nbsp;)** |**RGBA (&nbsp;47, &nbsp;79, &nbsp;79, &nbsp;1 @ NO__T)** |![darkslategray](./media/function-colors/color-darkslategray.png) |
| **Color.DarkSlateGrey** |**ColorValue ("#2f4f4f" &nbsp;)**<br>**ColorValue ("DarkSlateGrey" &nbsp;)** |**RGBA (&nbsp;47, &nbsp;79, &nbsp;79, &nbsp;1 @ NO__T)** |![darkslategrey](./media/function-colors/color-darkslategrey.png) |
| **Color.DarkTurquoise** |**ColorValue ("#00ced1" &nbsp;)**<br>**ColorValue ("DARKTURQUOISE" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;206, &nbsp;209, &nbsp;1 @ NO__T)** |![darkturquoise](./media/function-colors/color-darkturquoise.png) |
| **Color.DarkViolet** |**ColorValue ("#9400d3" &nbsp;)**<br>**ColorValue ("DarkViolet" &nbsp;)** |**RGBA (&nbsp;148, &nbsp;0, &nbsp;211, &nbsp;1 @ NO__T)** |![darkviolet](./media/function-colors/color-darkviolet.png) |
| **Color.DeepPink** |**ColorValue ("#ff1493" &nbsp;)**<br>**ColorValue ("deeppink" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;20, &nbsp;147, &nbsp;1 @ NO__T)** |![deeppink](./media/function-colors/color-deeppink.png) |
| **Color.DeepSkyBlue** |**ColorValue ("#00bfff" &nbsp;)**<br>**ColorValue ("DeepSkyBlue" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;191, &nbsp;255, &nbsp;1 @ NO__T)** |![deepskyblue](./media/function-colors/color-deepskyblue.png) |
| **Color.DimGray** |**ColorValue ("#696969" &nbsp;)**<br>**ColorValue ("가 나 회색" &nbsp;)** |**RGBA (&nbsp;105, &nbsp;105, &nbsp;105, &nbsp;1 @ NO__T)** |![dimgray](./media/function-colors/color-dimgray.png) |
| **Color.DimGrey** |**ColorValue ("#696969" &nbsp;)**<br>**ColorValue ("가는 회색" &nbsp;)** |**RGBA (&nbsp;105, &nbsp;105, &nbsp;105, &nbsp;1 @ NO__T)** |![dimgrey](./media/function-colors/color-dimgrey.png) |
| **Color.DodgerBlue** |**ColorValue ("#1e90ff" &nbsp;)**<br>**ColorValue ("dodgerblue" &nbsp;)** |**RGBA (&nbsp;30, &nbsp;144, &nbsp;255, &nbsp;1 @ NO__T)** |![dodgerblue](./media/function-colors/color-dodgerblue.png) |
| **Color.FireBrick** |**ColorValue ("#b22222" &nbsp;)**<br>**ColorValue ("FireBrick" &nbsp;)** |**RGBA (&nbsp;178, &nbsp;34, &nbsp;34, &nbsp;1 @ NO__T)** |![firebrick](./media/function-colors/color-firebrick.png) |
| **Color.FloralWhite** |**ColorValue ("#fffaf0" &nbsp;)**<br>**ColorValue ("FLORALWHITE" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;240, &nbsp;1 @ NO__T)** |![floralwhite](./media/function-colors/color-floralwhite.png) |
| **Color.ForestGreen** |**ColorValue ("#228b22" &nbsp;)**<br>**ColorValue ("ForestGreen" &nbsp;)** |**RGBA (&nbsp;34, &nbsp;139, &nbsp;34, &nbsp;1 @ NO__T)** |![forestgreen](./media/function-colors/color-forestgreen.png) |
| **Color.Fuchsia** |**ColorValue ("#ff00ff" &nbsp;)**<br>**ColorValue ("fuchsia" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T)** |![fuchsia](./media/function-colors/color-fuchsia.png) |
| **Color.Gainsboro** |**ColorValue ("#dcdcdc" &nbsp;)**<br>**ColorValue ("Gainsboro" &nbsp;)** |**RGBA (&nbsp;220, &nbsp;220, &nbsp;220, &nbsp;1 @ NO__T)** |![gainsboro](./media/function-colors/color-gainsboro.png) |
| **Color.GhostWhite** |**ColorValue ("#f8f8ff" &nbsp;)**<br>**ColorValue ("GHOSTWHITE" &nbsp;)** |**RGBA (&nbsp;248, &nbsp;248, &nbsp;255, &nbsp;1 @ NO__T)** |![ghostwhite](./media/function-colors/color-ghostwhite.png) |
| **Color.Gold** |**ColorValue ("#ffd700" &nbsp;)**<br>**ColorValue ("골드" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;215, &nbsp;0, &nbsp;1 @ NO__T)** |![gold](./media/function-colors/color-gold.png) |
| **Color.GoldenRod** |**ColorValue ("#daa520" &nbsp;)**<br>**ColorValue ("갈조색" &nbsp;)** |**RGBA (&nbsp;218, &nbsp;165, &nbsp;32, &nbsp;1 @ NO__T)** |![goldenrod](./media/function-colors/color-goldenrod.png) |
| **Color.Gray** |**ColorValue ("#808080" &nbsp;)**<br>**ColorValue ("회색" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T)** |![gray](./media/function-colors/color-gray.png) |
| **Color.Green** |**ColorValue ("#008000" &nbsp;)**<br>**ColorValue ("GREEN" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;128, &nbsp;0, &nbsp;1 @ NO__T)** |![green](./media/function-colors/color-green.png) |
| **Color.GreenYellow** |**ColorValue ("#adff2f" &nbsp;)**<br>**ColorValue ("GreenYellow" &nbsp;)** |**RGBA (&nbsp;173, &nbsp;255, &nbsp;47, &nbsp;1 @ NO__T)** |![greenyellow](./media/function-colors/color-greenyellow.png) |
| **Color.Grey** |**ColorValue ("#808080" &nbsp;)**<br>**ColorValue ("회색" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T)** |![grey](./media/function-colors/color-grey.png) |
| **Color.Honeydew** |**ColorValue ("#f0fff0" &nbsp;)**<br>**ColorValue ("멜론" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;255, &nbsp;240, &nbsp;1 @ NO__T)** |![honeydew](./media/function-colors/color-honeydew.png) |
| **Color.HotPink** |**ColorValue ("#ff69b4" &nbsp;)**<br>**ColorValue ("HOTPINK" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;105, &nbsp;180, &nbsp;1 @ NO__T)** |![hotpink](./media/function-colors/color-hotpink.png) |
| **Color.IndianRed** |**ColorValue ("#cd5c5c" &nbsp;)**<br>**ColorValue ("IndianRed" &nbsp;)** |**RGBA (&nbsp;205, &nbsp;92, &nbsp;92, &nbsp;1 @ NO__T)** |![indianred](./media/function-colors/color-indianred.png) |
| **Color.Indigo** |**ColorValue ("#4b0082" &nbsp;)**<br>**ColorValue ("indigo" &nbsp;)** |**RGBA (&nbsp;75, &nbsp;0, &nbsp;130, &nbsp;1 @ NO__T)** |![indigo](./media/function-colors/color-indigo.png) |
| **Color.Ivory** |**ColorValue ("#fffff0" &nbsp;)**<br>**ColorValue ("코트디부아르" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;240, &nbsp;1 @ NO__T)** |![ivory](./media/function-colors/color-ivory.png) |
| **Color.Khaki** |**ColorValue ("#f0e68c" &nbsp;)**<br>**ColorValue ("카키색" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;230, &nbsp;140, &nbsp;1 @ NO__T)** |![khaki](./media/function-colors/color-khaki.png) |
| **Color.Lavender** |**ColorValue ("#e6e6fa" &nbsp;)**<br>**ColorValue ("연보라" &nbsp;)** |**RGBA (&nbsp;230, &nbsp;230, &nbsp;250, &nbsp;1 @ NO__T)** |![lavender](./media/function-colors/color-lavender.png) |
| **Color.LavenderBlush** |**ColorValue ("#fff0f5" &nbsp;)**<br>**ColorValue ("lavenderblush" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;240, &nbsp;245, &nbsp;1 @ NO__T)** |![lavenderblush](./media/function-colors/color-lavenderblush.png) |
| **Color.LawnGreen** |**ColorValue ("#7cfc00" &nbsp;)**<br>**ColorValue ("LawnGreen" &nbsp;)** |**RGBA (&nbsp;124, &nbsp;252, &nbsp;0, &nbsp;1 @ NO__T)** |![lawngreen](./media/function-colors/color-lawngreen.png) |
| **Color.LemonChiffon** |**ColorValue ("#fffacd" &nbsp;)**<br>**ColorValue ("LEMONCHIFFON" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;205, &nbsp;1 @ NO__T)** |![lemonchiffon](./media/function-colors/color-lemonchiffon.png) |
| **Color.LightBlue** |**ColorValue ("#add8e6" &nbsp;)**<br>**ColorValue ("LightBlue" &nbsp;)** |**RGBA (&nbsp;173, &nbsp;216, &nbsp;230, &nbsp;1 @ NO__T)** |![lightblue](./media/function-colors/color-lightblue.png) |
| **Color.LightCoral** |**ColorValue ("#f08080" &nbsp;)**<br>**ColorValue ("lightcoral" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T)** |![lightcoral](./media/function-colors/color-lightcoral.png) |
| **Color.LightCyan** |**ColorValue ("#e0ffff" &nbsp;)**<br>**ColorValue ("LightCyan" &nbsp;)** |**RGBA (&nbsp;224, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T)** |![lightcyan](./media/function-colors/color-lightcyan.png) |
| **Color.LightGoldenRodYellow** |**ColorValue ("#fafad2" &nbsp;)**<br>**ColorValue ("lightgoldenrodyellow" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;250, &nbsp;210, &nbsp;1 @ NO__T)** |![lightgoldenrodyellow](./media/function-colors/color-lightgoldenrodyellow.png) |
| **Color.LightGray** |**ColorValue ("#d3d3d3" &nbsp;)**<br>**ColorValue ("LightGray" &nbsp;)** |**RGBA (&nbsp;211, &nbsp;211, &nbsp;211, &nbsp;1 @ NO__T)** |![lightgray](./media/function-colors/color-lightgray.png) |
| **Color.LightGreen** |**ColorValue ("#90ee90" &nbsp;)**<br>**ColorValue ("lightgreen" &nbsp;)** |**RGBA (&nbsp;144, &nbsp;238, &nbsp;144, &nbsp;1 @ NO__T)** |![lightgreen](./media/function-colors/color-lightgreen.png) |
| **Color.LightGrey** |**ColorValue ("#d3d3d3" &nbsp;)**<br>**ColorValue ("LightGrey" &nbsp;)** |**RGBA (&nbsp;211, &nbsp;211, &nbsp;211, &nbsp;1 @ NO__T)** |![lightgrey](./media/function-colors/color-lightgrey.png) |
| **Color.LightPink** |**ColorValue ("#ffb6c1" &nbsp;)**<br>**ColorValue ("LIGHTPINK" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;182, &nbsp;193, &nbsp;1 @ NO__T)** |![lightpink](./media/function-colors/color-lightpink.png) |
| **Color.LightSalmon** |**ColorValue ("#ffa07a" &nbsp;)**<br>**ColorValue ("LightSalmon" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;160, &nbsp;122, &nbsp;1 @ NO__T)** |![lightsalmon](./media/function-colors/color-lightsalmon.png) |
| **Color.LightSeaGreen** |**ColorValue ("#20b2aa" &nbsp;)**<br>**ColorValue ("lightseagreen" &nbsp;)** |**RGBA (&nbsp;32, &nbsp;178, &nbsp;170, &nbsp;1 @ NO__T)** |![lightseagreen](./media/function-colors/color-lightseagreen.png) |
| **Color.LightSkyBlue** |**ColorValue ("#87cefa" &nbsp;)**<br>**ColorValue ("LightSkyBlue" &nbsp;)** |**RGBA (&nbsp;135, &nbsp;206, &nbsp;250, &nbsp;1 @ NO__T)** |![lightskyblue](./media/function-colors/color-lightskyblue.png) |
| **Color.LightSlateGray** |**ColorValue ("#778899" &nbsp;)**<br>**ColorValue ("LIGHTSLATEGRAY" &nbsp;)** |**RGBA (&nbsp;119, &nbsp;136, &nbsp;153, &nbsp;1 @ NO__T)** |![lightslategray](./media/function-colors/color-lightslategray.png) |
| **Color.LightSlateGrey** |**ColorValue ("#778899" &nbsp;)**<br>**ColorValue ("LightSlateGrey" &nbsp;)** |**RGBA (&nbsp;119, &nbsp;136, &nbsp;153, &nbsp;1 @ NO__T)** |![lightslategrey](./media/function-colors/color-lightslategrey.png) |
| **Color.LightSteelBlue** |**ColorValue ("#b0c4de" &nbsp;)**<br>**ColorValue ("lightsteelblue" &nbsp;)** |**RGBA (&nbsp;176, &nbsp;196, &nbsp;222, &nbsp;1 @ NO__T)** |![lightsteelblue](./media/function-colors/color-lightsteelblue.png) |
| **Color.LightYellow** |**ColorValue ("#ffffe0" &nbsp;)**<br>**ColorValue ("LightYellow" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;224, &nbsp;1 @ NO__T)** |![lightyellow](./media/function-colors/color-lightyellow.png) |
| **Color.Lime** |**ColorValue ("#00ff00" &nbsp;)**<br>**ColorValue ("라임" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T)** |![lime](./media/function-colors/color-lime.png) |
| **Color.LimeGreen** |**ColorValue ("#32cd32" &nbsp;)**<br>**ColorValue ("LimeGreen" &nbsp;)** |**RGBA (&nbsp;50, &nbsp;205, &nbsp;50, &nbsp;1 @ NO__T)** |![limegreen](./media/function-colors/color-limegreen.png) |
| **Color.Linen** |**ColorValue ("#faf0e6" &nbsp;)**<br>**ColorValue ("linen" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;240, &nbsp;230, &nbsp;1 @ NO__T)** |![linen](./media/function-colors/color-linen.png) |
| **Color.Magenta** |**ColorValue ("#ff00ff" &nbsp;)**<br>**ColorValue ("자홍" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T)** |![magenta](./media/function-colors/color-magenta.png) |
| **Color.Maroon** |**ColorValue ("#800000" &nbsp;)**<br>**ColorValue ("적갈색" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T)** |![maroon](./media/function-colors/color-maroon.png) |
| **Color.MediumAquamarine** |**ColorValue ("#66cdaa" &nbsp;)**<br>**ColorValue ("MediumAquamarine" &nbsp;)** |**RGBA (&nbsp;102, &nbsp;205, &nbsp;170, &nbsp;1 @ NO__T)** |![mediumaquamarine](./media/function-colors/color-mediumaquamarine.png) |
| **Color.MediumBlue** |**ColorValue ("#0000cd" &nbsp;)**<br>**ColorValue ("mediumblue" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;205, &nbsp;1 @ NO__T)** |![mediumblue](./media/function-colors/color-mediumblue.png) |
| **Color.MediumOrchid** |**ColorValue ("#ba55d3" &nbsp;)**<br>**ColorValue ("MediumOrchid" &nbsp;)** |**RGBA (&nbsp;186, &nbsp;85, &nbsp;211, &nbsp;1 @ NO__T)** |![mediumorchid](./media/function-colors/color-mediumorchid.png) |
| **Color.MediumPurple** |**ColorValue ("#9370db" &nbsp;)**<br>**ColorValue ("MEDIUMPURPLE" &nbsp;)** |**RGBA (&nbsp;147, &nbsp;112, &nbsp;219, &nbsp;1 @ NO__T)** |![mediumpurple](./media/function-colors/color-mediumpurple.png) |
| **Color.MediumSeaGreen** |**ColorValue ("#3cb371" &nbsp;)**<br>**ColorValue ("MediumSeaGreen" &nbsp;)** |**RGBA (&nbsp;60, &nbsp;179, &nbsp;113, &nbsp;1 @ NO__T)** |![mediumseagreen](./media/function-colors/color-mediumseagreen.png) |
| **Color.MediumSlateBlue** |**ColorValue ("#7b68ee" &nbsp;)**<br>**ColorValue ("mediumslateblue" &nbsp;)** |**RGBA (&nbsp;123, &nbsp;104, &nbsp;238, &nbsp;1 @ NO__T)** |![mediumslateblue](./media/function-colors/color-mediumslateblue.png) |
| **Color.MediumSpringGreen** |**ColorValue ("#00fa9a" &nbsp;)**<br>**ColorValue ("MediumSpringGreen" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;250, &nbsp;154, &nbsp;1 @ NO__T)** |![mediumspringgreen](./media/function-colors/color-mediumspringgreen.png) |
| **Color.MediumTurquoise** |**ColorValue ("#48d1cc" &nbsp;)**<br>**ColorValue ("MEDIUMTURQUOISE" &nbsp;)** |**RGBA (&nbsp;72, &nbsp;209, &nbsp;204, &nbsp;1 @ NO__T)** |![mediumturquoise](./media/function-colors/color-mediumturquoise.png) |
| **Color.MediumVioletRed** |**ColorValue ("#c71585" &nbsp;)**<br>**ColorValue ("MediumVioletRed" &nbsp;)** |**RGBA (&nbsp;199, &nbsp;21, &nbsp;133, &nbsp;1 @ NO__T)** |![mediumvioletred](./media/function-colors/color-mediumvioletred.png) |
| **Color.MidnightBlue** |**ColorValue ("#191970" &nbsp;)**<br>**ColorValue ("midnightblue" &nbsp;)** |**RGBA (&nbsp;25, &nbsp;25, &nbsp;112, &nbsp;1 @ NO__T)** |![midnightblue](./media/function-colors/color-midnightblue.png) |
| **Color.MintCream** |**ColorValue ("#f5fffa" &nbsp;)**<br>**ColorValue ("MintCream" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;255, &nbsp;250, &nbsp;1 @ NO__T)** |![mintcream](./media/function-colors/color-mintcream.png) |
| **Color.MistyRose** |**ColorValue ("#ffe4e1" &nbsp;)**<br>**ColorValue ("MISTYROSE" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;225, &nbsp;1 @ NO__T)** |![mistyrose](./media/function-colors/color-mistyrose.png) |
| **Color.Moccasin** |**ColorValue ("#ffe4b5" &nbsp;)**<br>**ColorValue ("Moccasin" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;181, &nbsp;1 @ NO__T)** |![moccasin](./media/function-colors/color-moccasin.png) |
| **Color.NavajoWhite** |**ColorValue ("#ffdead" &nbsp;)**<br>**ColorValue ("navajowhite" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;222, &nbsp;173, &nbsp;1 @ NO__T)** |![navajowhite](./media/function-colors/color-navajowhite.png) |
| **Color.Navy** |**ColorValue ("#000080" &nbsp;)**<br>**ColorValue ("해군" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;128, &nbsp;1 @ NO__T)** |![navy](./media/function-colors/color-navy.png) |
| **Color.OldLace** |**ColorValue ("#fdf5e6" &nbsp;)**<br>**ColorValue ("OLDLACE" &nbsp;)** |**RGBA (&nbsp;253, &nbsp;245, &nbsp;230, &nbsp;1 @ NO__T)** |![oldlace](./media/function-colors/color-oldlace.png) |
| **Color.Olive** |**ColorValue ("#808000" &nbsp;)**<br>**ColorValue ("올리브" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;0, &nbsp;1 @ NO__T)** |![olive](./media/function-colors/color-olive.png) |
| **Color.OliveDrab** |**ColorValue ("#6b8e23" &nbsp;)**<br>**ColorValue ("olivedrab" &nbsp;)** |**RGBA (&nbsp;107, &nbsp;142, &nbsp;35, &nbsp;1 @ NO__T)** |![olivedrab](./media/function-colors/color-olivedrab.png) |
| **Color.Orange** |**ColorValue ("#ffa500" &nbsp;)**<br>**ColorValue ("주황색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;165, &nbsp;0, &nbsp;1 @ NO__T)** |![orange](./media/function-colors/color-orange.png) |
| **Color.OrangeRed** |**ColorValue ("#ff4500" &nbsp;)**<br>**ColorValue ("ORANGERED &nbsp;)** |**RGBA (&nbsp;255, &nbsp;69, &nbsp;0, &nbsp;1 @ NO__T)** |![orangered](./media/function-colors/color-orangered.png) |
| **Color.Orchid** |**ColorValue ("#da70d6" &nbsp;)**<br>**ColorValue ("연자주색" &nbsp;)** |**RGBA (&nbsp;218, &nbsp;112, &nbsp;214, &nbsp;1 @ NO__T)** |![orchid](./media/function-colors/color-orchid.png) |
| **Color.PaleGoldenRod** |**ColorValue ("#eee8aa" &nbsp;)**<br>**ColorValue ("palegoldenrod" &nbsp;)** |**RGBA (&nbsp;238, &nbsp;232, &nbsp;170, &nbsp;1 @ NO__T)** |![palegoldenrod](./media/function-colors/color-palegoldenrod.png) |
| **Color.PaleGreen** |**ColorValue ("#98fb98" &nbsp;)**<br>**ColorValue ("Palegreen 입력" &nbsp;)** |**RGBA (&nbsp;152, &nbsp;251, &nbsp;152, &nbsp;1 @ NO__T)** |![palegreen](./media/function-colors/color-palegreen.png) |
| **Color.PaleTurquoise** |**ColorValue ("#afeeee" &nbsp;)**<br>**ColorValue ("PALETURQUOISE" &nbsp;)** |**RGBA (&nbsp;175, &nbsp;238, &nbsp;238, &nbsp;1 @ NO__T)** |![paleturquoise](./media/function-colors/color-paleturquoise.png) |
| **Color.PaleVioletRed** |**ColorValue ("#db7093" &nbsp;)**<br>**ColorValue ("PaleVioletRed" &nbsp;)** |**RGBA (&nbsp;219, &nbsp;112, &nbsp;147, &nbsp;1 @ NO__T)** |![palevioletred](./media/function-colors/color-palevioletred.png) |
| **Color.PapayaWhip** |**ColorValue ("#ffefd5" &nbsp;)**<br>**ColorValue ("papayawhip" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;239, &nbsp;213, &nbsp;1 @ NO__T)** |![papayawhip](./media/function-colors/color-papayawhip.png) |
| **Color.PeachPuff** |**ColorValue ("#ffdab9" &nbsp;)**<br>**ColorValue ("PeachPuff" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;218, &nbsp;185, &nbsp;1 @ NO__T)** |![peachpuff](./media/function-colors/color-peachpuff.png) |
| **Color.Peru** |**ColorValue ("#cd853f" &nbsp;)**<br>**ColorValue ("페루" &nbsp;)** |**RGBA (&nbsp;205, &nbsp;133, &nbsp;63, &nbsp;1 @ NO__T)** |![peru](./media/function-colors/color-peru.png) |
| **Color.Pink** |**ColorValue ("#ffc0cb" &nbsp;)**<br>**ColorValue ("분홍색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;192, &nbsp;203, &nbsp;1 @ NO__T)** |![pink](./media/function-colors/color-pink.png) |
| **Color.Plum** |**ColorValue ("#dda0dd" &nbsp;)**<br>**ColorValue ("plum" &nbsp;)** |**RGBA (&nbsp;221, &nbsp;160, &nbsp;221, &nbsp;1 @ NO__T)** |![plum](./media/function-colors/color-plum.png) |
| **Color.PowderBlue** |**ColorValue ("#b0e0e6" &nbsp;)**<br>**ColorValue ("PowderBlue" &nbsp;)** |**RGBA (&nbsp;176, &nbsp;224, &nbsp;230, &nbsp;1 @ NO__T)** |![powderblue](./media/function-colors/color-powderblue.png) |
| **Color.Purple** |**ColorValue ("#800080" &nbsp;)**<br>**ColorValue ("자주색" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;0, &nbsp;128, &nbsp;1 @ NO__T)** |![purple](./media/function-colors/color-purple.png) |
| **Color.Red** |**ColorValue ("#ff0000" &nbsp;)**<br>**ColorValue ("Red" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T)** |![red](./media/function-colors/color-red.png) |
| **Color.RosyBrown** |**ColorValue ("#bc8f8f" &nbsp;)**<br>**ColorValue ("rosybrown" &nbsp;)** |**RGBA (&nbsp;188, &nbsp;143, &nbsp;143, &nbsp;1 @ NO__T)** |![rosybrown](./media/function-colors/color-rosybrown.png) |
| **Color.RoyalBlue** |**ColorValue ("#4169e1" &nbsp;)**<br>**ColorValue ("RoyalBlue" &nbsp;)** |**RGBA (&nbsp;65, &nbsp;105, &nbsp;225, &nbsp;1 @ NO__T)** |![royalblue](./media/function-colors/color-royalblue.png) |
| **Color.SaddleBrown** |**ColorValue ("#8b4513" &nbsp;)**<br>**ColorValue ("SADDLEBROWN" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;69, &nbsp;19, &nbsp;1 @ NO__T)** |![saddlebrown](./media/function-colors/color-saddlebrown.png) |
| **Color.Salmon** |**ColorValue ("#fa8072" &nbsp;)**<br>**ColorValue ("연어" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;128, &nbsp;114, &nbsp;1 @ NO__T)** |![salmon](./media/function-colors/color-salmon.png) |
| **Color.SandyBrown** |**ColorValue ("#f4a460" &nbsp;)**<br>**ColorValue ("sandybrown" &nbsp;)** |**RGBA (&nbsp;244, &nbsp;164, &nbsp;96, &nbsp;1 @ NO__T)** |![sandybrown](./media/function-colors/color-sandybrown.png) |
| **Color.SeaGreen** |**ColorValue ("#2e8b57" &nbsp;)**<br>**ColorValue ("SeaGreen" &nbsp;)** |**RGBA (&nbsp;46, &nbsp;139, &nbsp;87, &nbsp;1 @ NO__T)** |![seagreen](./media/function-colors/color-seagreen.png) |
| **Color.SeaShell** |**ColorValue ("#fff5ee" &nbsp;)**<br>**ColorValue ("SEASHELL" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;245, &nbsp;238, &nbsp;1 @ NO__T)** |![seashell](./media/function-colors/color-seashell.png) |
| **Color.Sienna** |**ColorValue ("#a0522d" &nbsp;)**<br>**ColorValue ("Sienna" &nbsp;)** |**RGBA (&nbsp;160, &nbsp;82, &nbsp;45, &nbsp;1 @ NO__T)** |![sienna](./media/function-colors/color-sienna.png) |
| **Color.Silver** |**ColorValue ("#c0c0c0" &nbsp;)**<br>**ColorValue ("은색" &nbsp;)** |**RGBA (&nbsp;192, &nbsp;192, &nbsp;192, &nbsp;1 @ NO__T)** |![silver](./media/function-colors/color-silver.png) |
| **Color.SkyBlue** |**ColorValue ("#87ceeb" &nbsp;)**<br>**ColorValue ("SkyBlue" &nbsp;)** |**RGBA (&nbsp;135, &nbsp;206, &nbsp;235, &nbsp;1 @ NO__T)** |![skyblue](./media/function-colors/color-skyblue.png) |
| **Color.SlateBlue** |**ColorValue ("#6a5acd" &nbsp;)**<br>**ColorValue ("SLATEBLUE" &nbsp;)** |**RGBA (&nbsp;106, &nbsp;90, &nbsp;205, &nbsp;1 @ NO__T)** |![slateblue](./media/function-colors/color-slateblue.png) |
| **Color.SlateGray** |**ColorValue ("#708090" &nbsp;)**<br>**ColorValue ("SlateGray" &nbsp;)** |**RGBA (&nbsp;112, &nbsp;128, &nbsp;144, &nbsp;1 @ NO__T)** |![slategray](./media/function-colors/color-slategray.png) |
| **Color.SlateGrey** |**ColorValue ("#708090" &nbsp;)**<br>**ColorValue ("slategrey" &nbsp;)** |**RGBA (&nbsp;112, &nbsp;128, &nbsp;144, &nbsp;1 @ NO__T)** |![slategrey](./media/function-colors/color-slategrey.png) |
| **Color.Snow** |**ColorValue ("#fffafa" &nbsp;)**<br>**ColorValue ("눈" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;250, &nbsp;1 @ NO__T)** |![snow](./media/function-colors/color-snow.png) |
| **Color.SpringGreen** |**ColorValue ("#00ff7f" &nbsp;)**<br>**ColorValue ("SPRINGGREEN" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;127, &nbsp;1 @ NO__T)** |![springgreen](./media/function-colors/color-springgreen.png) |
| **Color.SteelBlue** |**ColorValue ("#4682b4" &nbsp;)**<br>**ColorValue ("SteelBlue" &nbsp;)** |**RGBA (&nbsp;70, &nbsp;130, &nbsp;180, &nbsp;1 @ NO__T)** |![steelblue](./media/function-colors/color-steelblue.png) |
| **Color.Tan** |**ColorValue ("#d2b48c" &nbsp;)**<br>**ColorValue ("tan" &nbsp;)** |**RGBA (&nbsp;210, &nbsp;180, &nbsp;140, &nbsp;1 @ NO__T)** |![tan](./media/function-colors/color-tan.png) |
| **Color.Teal** |**ColorValue ("#008080" &nbsp;)**<br>**ColorValue ("청록" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T)** |![teal](./media/function-colors/color-teal.png) |
| **Color.Thistle** |**ColorValue ("#d8bfd8" &nbsp;)**<br>**ColorValue ("THISTLE" &nbsp;)** |**RGBA (&nbsp;216, &nbsp;191, &nbsp;216, &nbsp;1 @ NO__T)** |![thistle](./media/function-colors/color-thistle.png) |
| **Color.Tomato** |**ColorValue ("#ff6347" &nbsp;)**<br>**ColorValue ("토마토" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;99, &nbsp;71, &nbsp;1 @ NO__T)** |![tomato](./media/function-colors/color-tomato.png) |
| **Color. 투명** |**ColorValue ("#00000000" &nbsp;)**<br>**ColorValue ("Transparent" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;0, &nbsp;0 @ NO__T)** |![보이지](./media/function-colors/color-transparent.png) |
| **Color.Turquoise** |**ColorValue ("#40e0d0" &nbsp;)**<br>**ColorValue ("옥색" &nbsp;)** |**RGBA (&nbsp;64, &nbsp;224, &nbsp;208, &nbsp;1 @ NO__T)** |![turquoise](./media/function-colors/color-turquoise.png) |
| **Color.Violet** |**ColorValue ("#ee82ee" &nbsp;)**<br>**ColorValue ("보라" &nbsp;)** |**RGBA (&nbsp;238, &nbsp;130, &nbsp;238, &nbsp;1 @ NO__T)** |![violet](./media/function-colors/color-violet.png) |
| **Color.Wheat** |**ColorValue ("#f5deb3" &nbsp;)**<br>**ColorValue ("WHEAT" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;222, &nbsp;179, &nbsp;1 @ NO__T)** |![wheat](./media/function-colors/color-wheat.png) |
| **Color.White** |**ColorValue ("#ffffff" &nbsp;)**<br>**ColorValue ("White" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T)** |![white](./media/function-colors/color-white.png) |
| **Color.WhiteSmoke** |**ColorValue ("#f5f5f5" &nbsp;)**<br>**ColorValue ("회백색" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;245, &nbsp;245, &nbsp;1 @ NO__T)** |![whitesmoke](./media/function-colors/color-whitesmoke.png) |
| **Color.Yellow** |**ColorValue ("#ffff00" &nbsp;)**<br>**ColorValue ("노란색" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T)** |![yellow](./media/function-colors/color-yellow.png) |
| **Color.YellowGreen** |**ColorValue ("#9acd32" &nbsp;)**<br>**ColorValue ("YELLOWGREEN" &nbsp;)** |**RGBA (&nbsp;154, &nbsp;205, &nbsp;50, &nbsp;1 @ NO__T)** |![yellowgreen](./media/function-colors/color-yellowgreen.png) |
