---
title: '양식 디자이너를 사용하여 양식에 섹션 추가, 이동 또는 삭제 | MicrosoftDocs'
ms.custom: ''
ms.date: 04/21/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="add-move-or-delete-sections-on-a-form"></a>양식에 섹션 추가, 이동 또는 삭제 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

양식 디자이너를 사용하여 양식에 섹션 추가, 이동 또는 삭제 

> [!NOTE]
> 끌어서 놓기를 사용하여 섹션을 추가하거나 이동할 때 양식 미리 보기가 반응적이고 스택된 여러 탭 열을 렌더링할 수 있습니다. 추가 또는 이동 중인 섹션이 올바른 탭 열에 있는지 확인하려면 이미 해당 탭 열에 있는 다른 섹션에 고정 또는 제거합니다.

## <a name="add-sections-to-a-form"></a>양식에 섹션 추가
양식에 섹션을 추가하려면 **레이아웃** 창을 사용합니다. 

> [!div class="mx-imgBorder"] 
> ![](media/layouts-pane.png "레이아웃 창")

  > [!NOTE]
  >   섹션은 기본 양식 및 빠른 보기 양식에만 추가할 수 있습니다. 추가 정보: [양식 유형](types-forms.md)

### <a name="add-sections-to-a-form-using-drag-and-drop"></a>끌어서 놓기를 사용하여 양식에 섹션 추가

1. 양식 디자이너를 열어 양식을 만들거나 편집합니다. 추가 정보: [양식 만들기](create-and-edit-forms.md#create-a-form) 또는 [양식 편집](create-and-edit-forms.md#edit-a-form)
2. 명령 모음에서 **컨트롤 추가**를 선택하거나 왼쪽 창에서 **레이아웃**을 선택합니다. 
3. **레이아웃** 창에서 섹션 컨트롤을 선택하고 양식 미리 보기로 끌어옵니다. 양식 미리 보기에서 섹션을 끌어오면 섹션을 추가할 수 있는 놓기 대상이 표시됩니다. 
4. 원하는 위치에 섹션을 놓습니다. 다음을 참고하십시오. 
    - 기존 섹션 이전 또는 이후에 섹션을 삭제할 수 있습니다.
    - 섹션은 탭 내의 빈 영역에도 놓을 수 있습니다. 이 경우 탭 열에 섹션을 균등하게 분배할 수 있도록 섹션이 사용 가능한 공간에 추가됩니다.
    - 섹션을 끌 때 탭 머리글 위에 마우스를 올려 놓으면 현재 선택된 탭이 변경되어 섹션을 다른 탭에 추가할 수 있습니다.   
5. 섹션을 더 추가하려면 위의 3~4단계를 반복합니다.
6. 명령 모음에서 **저장**을 선택하여 양식을 저장하거나 저장하고 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다. 

### <a name="add-sections-to-a-form-using-selection"></a>선택 항목을 사용하여 양식에 섹션 추가 

1. 양식 디자이너를 열어 양식을 만들거나 편집합니다. 추가 정보: [양식 만들기](create-and-edit-forms.md#create-a-form) 또는 [양식 편집](create-and-edit-forms.md#edit-a-form)
2. 양식 미리보기에서 다른 기존 섹션이나 탭을 선택합니다. 다음을 참고하십시오.
    - 기존 섹션을 선택하는 경우 새 섹션이 기존 섹션 다음에 추가됩니다. 
    - 탭을 선택하면 탭 열 전체에 섹션을 균등하게 배분하기 위해 사용 가능한 공간에 새 섹션이 추가됩니다. 
3. 명령 모음에서 **컨트롤 추가**를 선택하거나 왼쪽 창에서 **레이아웃**을 선택합니다.  
4. **레이아웃** 창에서 섹션 컨트롤을 선택하여 양식에 추가합니다. 또는 원하는 섹션 컨트롤 옆의 **...** 을 선택한 다음 **선택한 탭에 추가**를 선택합니다. 
5. 섹션을 더 추가하려면 위의 2~4단계를 반복합니다.
6. 명령 모음에서 **저장**을 선택하여 양식을 저장하거나 저장하고 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다. 

## <a name="move-sections-on-a-form"></a>양식의 섹션 이동

### <a name="move-sections-on-a-form-using-drag-and-drop"></a>끌어서 놓기를 사용하여 양식의 섹션 이동

1. 양식 디자이너를 열어 양식을 만들거나 편집합니다. 추가 정보: [양식 만들기](create-and-edit-forms.md#create-a-form) 또는 [양식 편집](create-and-edit-forms.md#edit-a-form)
2. 양식 미리 보기에서 이동하려는 섹션 내의 섹션 레이블 또는 빈 공백을 선택하고 끌어서 놓기 작업을 시작합니다. 양식 미리 보기에서 섹션을 끌어오면 섹션을 이동할 수 있는 놓기 대상이 표시됩니다. 
3. 원하는 위치에 섹션을 놓습니다. 다음을 참고하십시오. 
    - 기존 섹션 이전 또는 이후에 섹션을 삭제할 수 있습니다.
    - 섹션은 탭 내의 빈 영역에도 놓을 수 있습니다. 이 경우 탭 열에 섹션을 균등하게 분배할 수 있도록 섹션이 사용 가능한 공간에 추가됩니다.
    - 섹션을 끌 때 탭 머리글 위에 마우스를 올려 놓으면 현재 선택된 탭이 변경되어 섹션을 다른 탭에 추가할 수 있습니다.   
4. 섹션을 더 이동하려면 위의 2~3단계를 반복합니다.
5. 명령 모음에서 **저장**을 선택하여 양식을 저장하거나 저장하고 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다. 

### <a name="move-sections-on-a-form-using-cut-and-paste"></a>잘라내기 및 붙여넣기를 사용하여 양식에서 섹션 이동

1. 양식 디자이너를 열어 양식을 만들거나 편집합니다. 추가 정보: [양식 만들기](create-and-edit-forms.md#create-a-form) 또는 [양식 편집](create-and-edit-forms.md#edit-a-form)
2. 양식 미리 보기에서 이동할 섹션을 선택합니다.
3. 명령 모음에서 **잘라내기**를 선택합니다.
4. 양식 미리 보기에서 다른 기존 섹션이나 탭을 선택합니다. 필요한 경우 다른 탭으로 전환할 수도 있습니다.
5. 명령 모음에서 **붙여넣기**를 선택하거나 펼침 아이콘을 선택한 다음 **앞에 붙여 넣기**를 선택합니다. 다음을 참고하십시오. 
    - **붙여 넣기**를 선택하면 이동 중인 섹션이 기존 섹션 뒤에 붙여 넣어집니다. 
    - **앞에 붙여 넣기**를 선택하면 이동 중인 섹션이 기존 섹션 앞에 붙여 넣어집니다.
    - 탭을 선택하면 탭 열 전체에 섹션을 균등하게 배분하기 위해 사용 가능한 공간에 이동 중인 섹션이 추가됩니다. **앞에 붙여 넣기** 작업은 적용할 수 없으므로 이 경우 사용할 수 없습니다.
6. 섹션을 더 이동하려면 위의 2~5단계를 반복합니다.
7. 명령 모음에서 **저장**을 선택하여 양식을 저장하거나 저장하고 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다. 

## <a name="delete-sections-on-a-form"></a>양식의 섹션 삭제
1. 양식 디자이너를 열어 양식을 만들거나 편집합니다. 추가 정보: [양식 만들기](create-and-edit-forms.md#create-a-form) 또는 [양식 편집](create-and-edit-forms.md#edit-a-form)
2. 양식 미리보기에서 양식에서 삭제하려는 섹션을 선택합니다. 
3. 명령 모음에서 **삭제**를 선택합니다.
4. 섹션을 더 삭제하려면 위의 2~3단계를 반복합니다.
4. 명령 모음에서 **저장**을 선택하여 양식을 저장하거나 저장하고 사용자에게 변경 사항을 표시하려는 경우 **게시**를 선택합니다. 

    > [!NOTE]
    >   - 섹션은 기본 양식 및 빠른 보기 양식에서만 삭제할 수 있습니다. 추가 정보: [양식 유형](types-forms.md)
    >   - 명령 모음에서 실수로 섹션을 삭제한 경우에는 **실행 취소**를 선택하여 양식을 이전 상태로 되돌립니다. 
    >   - 필수 또는 잠긴 필드가 포함된 섹션은 삭제할 수 없습니다. 
    >   - 잠긴 섹션은 삭제할 수 없습니다. 
    >   - 탭에는 각 탭 열에 하나 이상의 섹션이 있어야 합니다. 탭 열의 마지막 남은 섹션을 삭제하면 새 섹션이 자동으로 추가됩니다. 

### <a name="see-also"></a>참조
[모델 기반 양식 디자이너 개요](form-designer-overview.md)  
[양식 디자이너를 사용하여 양식 만들기 또는 편집](create-and-edit-forms.md)  
[양식 디자이너를 사용하여 양식에 필드 추가, 이동 또는 삭제](add-move-or-delete-fields-on-form.md)  
[양식 디자이너를 사용하여 양식에 탭 추가, 이동 또는 삭제](add-move-or-delete-tabs-on-form.md)  
[양식 디자이너에서 사용 가능한 속성](form-designer-properties.md)  
[양식 디자이너에서 머리글 속성 구성](form-designer-header-properties.md)  
[양식 디자이너에서 트리 보기 사용](using-tree-view-on-form.md)  
[필드 만들기 및 편집](../common-data-service/create-edit-field-portal.md)