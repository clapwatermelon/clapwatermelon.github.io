---
layout: post
title: Swift - Control Events
tags: [swift, control events]
---

## Control Events(컨트롤 이벤트)
***
### Relationship between Control Events and Actions(컨트롤 이벤트와 액션과의 관계)
- UIKit에는 UIButton, UISwitch, UIStepper 등 UIControl을 상속받은 다양한 컨트롤 클래스가 있습니다. 그런 컨트롤 객체에 발생한 다양한 이벤트 종류를 특정 액션 메서드에 연결할 수 있습니다. 즉, 컨트롤 객체에서 특정 이벤트가 발생하면, 미리 지정해 둔 타겟의 액션을 호출하게 됩니다.

### Types of Control Events(컨트롤 이벤트의 종류)
- 컨트롤 이벤트는 'UIControlEvents'라는 타입으로 정의되어 있습니다.

**touchDown**     
컨트롤을 터치했을 때 발생하는 이벤트
<code>UIControlEvents.touchDown</code>      

**touchDownRepeat**     
컨트롤을 연속 터치 할 때 발생하는 이벤트
<code>UIControlEvents.touchDownRepeat</code>

**touchDragInside**     
컨트롤 범위 내에서 터치한 영역을 드래그 할 때 발생하는 이벤트
<code>UIControlEvents.touchDragInside</code>

**touchDragOutside**      
터치 영역이 컨트롤의 바깥쪽에서 드래그 할 때 발생하는 이벤트
<code>UIControlEvents.touchDragOutside</code>

**touchDragEnter**      
터치 영역이 컨트롤의 일정 영역 바깥쪽으로 나갔다가 다시 들어왔을 때 발생하는 이벤트
<code>UIControlEvents.touchDragEnter</code>
 
**touchDragExit**      
터치 영역이 컨트롤의 일정 영역 바깥쪽으로 나갔을 때 발생하는 이벤트
<code>UIControlEvents.touchDragExit</code>

**touchUpInside**      
컨트롤 영역 안쪽에서 터치 후 뗐을때 발생하는 이벤트
<code>UIControlEvents.touchUpInside</code>

**touchUpOutside**      
컨트롤 영역 안쪽에서 터치 후 컨트롤 밖에서 뗐을때 이벤트
<code>UIControlEvents.touchUpOutside</code>

**touchCancel**       
터치를 취소하는 이벤트 (touchUp 이벤트가 발생되지 않음)
<code>UIControlEvents.touchCancel</code>

**valueChanged**      
터치를 드래그 및 다른 방법으로 조작하여 값이 변경되었을때 발생하는 이벤트
<code>UIControlEvents.valueChanged</code>

**primaryActionTriggered**      
버튼이 눌릴때 발생하는 이벤트 (iOS보다는 tvOS에서 사용)
<code>UIControlEvents.primaryActionTriggered</code>

**editingDidBegin**       
UITextField에서 편집이 시작될 때 호출되는 이벤트
<code>UIControlEvents.editingDidBegin</code>

**editingChanged**     
UITextField에서 값이 바뀔 때마다 호출되는 이벤트
<code>UIControlEvents.editingChanged</code>

**editingDidEnd**      
UITextField에서 외부객체와의 상호작용으로 인해 편집이 종료되었을 때 발생하는 이벤트
<code>UIControlEvents.editingDidEnd</code>

**editingDidEndOnExit**      
UITextField의 편집상태에서 키보드의 return 키를 터치했을 때 발생하는 이벤트
<code>UIControlEvents.editingDidEndOnExit</code>

**allTouchEvents**      
모든 터치 이벤트
<code>UIControlEvents.allTouchEvents</code>

**allEditingEvents**      
UITextField에서 편집작업의 이벤트
<code>UIControlEvents.allEditingEvents</code>

**applicationReserved**      
각각의 애플리케이션에서 프로그래머가 임의로 지정할 수 있는 이벤트 값의 범위
<code>UIControlEvents.applicationReserved</code>

**systemReserved**       
프레임워크 내에서 사용하는 예약된 이벤트 값의 범위
<code>UIControlEvents.systemReserved</code>

**allEvents**     
시스템 이벤트를 포함한 모든 이벤트
<code>UIControlEvents.allEvents</code>

## 관련 문서  
[UIControlEvents](https://developer.apple.com/documentation/uikit/uicontrolevents)      
[Target-Action](https://developer.apple.com/library/content/documentation/General/Conceptual/CocoaEncyclopedia/Target-Action/Target-Action.html)
