---
title: 포털에 대한 사용자 지정 JavaScript 사용 | MicrosoftDocs
description: 포털의 양식에 사용자 정의 JavaScript를 추가하는 방법
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760707"
---
# <a name="add-custom-javascript"></a>맞춤 JavaScript 추가

웹 양식 단계 레코드에는 양식의 시각적 표시 또는 함수를 확장하거나 수정할 수 있도록 JavaScript 코드를 저장하는 데 사용할 수 있는 **사용자 지정 JavaScript** 라는 필드가 포함되어 있습니다.

JavaScript의 사용자 지정 블록은 종료 양식 태그 요소 바로 앞 페이지의 하단에 추가됩니다.

## <a name="form-fields"></a>양식 필드

엔터티 필드의 HTML 입력 ID는 특성의 논리 이름으로 설정됩니다. [jQuery](https://jquery.com/)로 필드 선택, 값 설정 또는 기타 클라이언트 쪽 조작을 쉽게 할 수 있습니다.  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>추가 클라이언트 쪽 필드 유효성 검사
때로는 양식 내 필드의 유효성 검사를 사용자 지정해야 할 수 있습니다. 다음 예제에서는 사용자 지정 유효성 검사기를 추가하는 방법을 보여줍니다. 이 예에서는 선호하는 연락 방법의 다른 필드가 전자 메일로 설정되어 있는 경우에만 사용자가 이메일을 지정하게 합니다.

> [!NOTE]
> 클라이언트 쪽 필드 유효성 검사는 하위 표에서 지원되지 않습니다.

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>일반적인 유효성 검사

**다음**/**제출** 단추를 클릭하면 **webFormClientValidate**라는 함수가 실행됩니다. 이 메서드를 확장하여 사용자 지정 유효성 검사 논리를 추가할 수 있습니다.

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>참조

[포털 구성](configure-portal.md)  
[엔터티 양식 정의](entity-forms.md)  
[포털에 대한 웹 양식 단계](web-form-steps.md)  
[포럼 불러오기/탭 단계 유형 불러오기](load-form-step.md)  
[리디렉션 단계 유형](add-redirect-step.md)  
[조건부 단계 유형](add-conditional-step.md)
