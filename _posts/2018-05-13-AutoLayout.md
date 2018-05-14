---
layout: post
title: Swift - AutoLayout
tags: [swift, autoLayout]
---

## AutoLayout
***
> 이전에는 하나의 사이즈였던 아이폰 기종이 이제는 iPhone4, iPhoneSE, iPhone8, iPhone8 Plus 그리고 iPhoneX등다양한 사이즈와 화면 비율로 출시 되면서, 사이즈에 구애받지 않고 시각적으로 동일한 화면을 구현해야하는데 이를 위한 가장 편리하고 권장되는 방법이 바로 오토레이아웃입니다.

## AutoLayout
***
> 오토레이아웃은 뷰의 제약 사항을 바탕으로 뷰 체계 내의 모든 뷰의 크기와 위치를 동적으로 계산합니다. 
오토레이아웃은 애플리케이션을 사용할 때 발생하는 외부 변경과 내부 변경에 동적으로 반응하는 사용자 인터페이스를 가능하게 합니다.      

### 외부 변경(External Changes)    
****
> 외부 변경은 슈퍼뷰의 크기나 모양이 변경될 때 발생합니다. 각각의 변화와 함께, 사용 가능한 공간을 가장 잘 사용할 수 있도록 뷰 체계의 레이아웃을 업데이트해주어야 합니다.    

#### 외부 변경이 발생하는 경우
- 사용자가 아이패드의 분할뷰(Split View)를 사용하거나 사용하지 않는 경우(iOS)   
- 장치를 회전하는 경우(iOS)    
- 활성화콜(active call)과 오디오 녹음 바가 보여지거나 사라지는 경우(iOS)     
- 다른 크기의 클래스를 지원하기 원하는 경우    
- 다른 크기의 스크린을 지원하기 원하는 경우    

이러한 변경사항은 대부분은 실행 시간에 발생할 수 있으며 애플리케이션으로부터 동적인 응답을 요구합니다. 다른 스크린 크기를 지원하는 것과 같은 것은 애플리케이션이 다른 환경에 적응하는 것을 나타냅니다. 스크린 크기가 일반적으로 실행 시간에 변경되지 않는다고 하더라도, 적응형 인터페이스를 만들면 애플리케이션이 아이폰 4S, 아이폰 6 플러스, 또는 아이패드에서도 모두 동일하게 잘 작동할 수 있습니다. 오토레이아웃은 아이패드 내부 변경에서 슬라이드와 분할뷰를 지원하는 핵심 요소이기도 합니다.    

### 내부 변경(Internal Changes)
***
> 내부 변경은 사용자 인터페이스의 뷰의 크기 또는 설정이 변경되었을 때 발생합니다.    

#### 내부 변경이 발생하는 경우
- 애플리케이션 변경에 의해 콘텐츠가 보여지는 경우    
- 애플리케이션이 국제화를 지원하는 경우    
- 애플리케이션이 동적 타입을 지원하는 경우    

애플리케이션 콘텐츠가 변경됐을 때, 새로운 콘텐츠는 예전과 다른 레이아웃을 필요 할 수 있습니다. 새로운 애플리케이션이 각각의 신문 기사의 크기에 기반을 둔 레이아웃을 조정할 필요가 있는 경우와 같이, 텍스트 또는 이미지를 보여주는 애플리케이션에서 일반적으로 발생하는 일입니다. 이와 비슷하게, 사진 콜라주는 이미지 크기와 영상의 가로 세로의 비율을 다뤄야만 합니다.    

### 오토레이아웃이 왜 필요할까?
***
> 오토레이아웃은 아래의 경우와 같이 인터페이스의 절대적인 좌표가 아닌 동적으로 상대적인 좌표가 필요한 경우에 유용합니다.    
- 애플리케이션이 실행되는 iOS 기기의 스크린 화면의 크기가 다양한 경우    
- 애플리케이션이 실행되는 iOS 기기의 스크린이 회전할 수 있는 경우    
- 상태표시줄(Status Bar)에 전화 중임을 나타내는 액티브 콜(active call)과 오디오 녹음 중임을 나타내는 오디오 바가 보여지거나 사라지는 경우    
- 애플리케이션의 콘텐츠가 동적으로 보여지는 경우    
- 애플리케이션이 지역화(Localization)를 지원하는 경우    
- 애플리케이션이 동적 타입을 지원하는 경우    

### 오토레이아웃 속성
***
오토레이아웃의 속성은 정렬 사각형을 기반으로 합니다.     

![autolayout](/assets/post_img/autoLayout.png)   

- Width : 정렬 사각형의 너비
- Height : 정렬 사각형의 높이
- Top : 정렬 사각형의 상단
- Bottom : 정렬 사각형의 하단
- Baseline : 텍스트의 하단
- Horizontal : 수평
- Vertical : 수직
- Leading : 리딩, 텍스트를 읽을 때 시작 방향
- Trailing : 트레일링, 텍스트를 읽을 때 끝 방향
- CenterX : 수평 중심
- CenterY : 수직 중심

### 안정 영역(Safe Area)
***
- 안전 영역은 콘텐츠가 상태바, 내비게이션바, 툴바, 탭바를 가리는 것을 방지하는 영역입니다. 표준 시스템이 제공하는 뷰들은 자동으로 안전 영역 레이아웃 가이드를 준수하게 되어있습니다.
- 기존의 상/하단 레이아웃 가이드(Top/Bottom Layout Guide)를 대체하며, 하위 버전에도 호환하여 작동합니다.
	* 안전 영역은 iOS 11부터 사용할 수 있습니다.
	* iOS 11 미만의 버전에서는 상/하단 레이아웃 가이드를 사용합니다.

![safeArea](/assets/post_img/safeArea.png)    

안전 영역 레이아웃 가이드는 UIView클래스의 var safeAreaLayoutGuide: UILayoutGuide로 접근할 수 있습니다.     

### 제약(Constraint)    
***
> 제약은 뷰 스스로 또는 뷰 사이의 관계를 속성을 통하여 정의합니다. 제약은 방정식으로 나타낼 수 있습니다.

![constraints](/assets/post_img/constraints.png)    
- Item1 : 방정식에 있는 첫 번째 아이템(B View) 입니다. 첫 번째 아이템은 반드시 뷰 또는 레이아웃 가이드이어야 합니다.
- Attribute1 : 첫번째 아이템에 대한 속성입니다. 이 경우, B View의 리딩입니다.
- Multiplier : 속성 2에 곱해지는 값입니다. 이 경우 1.0 입니다.
- Item2 : 방정식에 있는 두 번째 아이템(A View) 입니다.
- Attribute2 : 두번째 아이템에 대한 속성입니다. 이 경우, A View의 트레일링입니다.
- Constant : 두번째 아이템의 속성에 더해지는 상수 값입니다.

위의 예제 방정식의 제약을 해석하면 'B View의 리딩은 A View의 트레일링의 1.0배에 8.0을 더한 위치'가 됩니다.     

### 고유 콘텐츠 크기(Intrinsic Content Size)    
***
> 뷰의 고유 콘텐츠 크기는 뷰가 갖는 원래의 크기로 생각할 수 있습니다. 예를 들어 레이블의 고유 콘텐츠 크기는 레이블의 텍스트의 크기고, 이미지의 고유 콘텐츠 크기는 이미지 자체의 크기입니다.   

### 제약 우선도(Constraint Priorities)    
***
> 오토레이아웃은 뷰의 고유 콘텐츠 크기를 각 크기에 대한 한 쌍의 제약을 사용하여 나타냅니다. 우선도가 높을수록 다른 제약보다 우선적으로 레이아웃에 적용하며, 같은 속성의 다른 제약과 경합하는 경우, 우선도가 낮은 제약은 무시됩니다.     

1. 콘텐츠 허깅 우선도(Content hugging priority) : 콘텐츠 고유 사이즈보다 뷰가 커지지 않도록 제한합니다. 다른 제약사항보다 우선도가 높으면 뷰가 콘텐츠 사이즈보다 커지지 않습니다.    
2. 콘텐츠 축소 방지 우선도(Content compression resistance priority) : 콘텐츠 고유 사이즈보다 뷰가 작아지지 않도록 제한합니다. 다른 제약사항보다 우선도가 높으면 뷰가 콘텐츠 사이즈보다 작아지지 않습니다.    
![contraintsPriorities](/assets/post_img/constraintsPriority.png)    

### 레이아웃 마진
***
> 뷰에 콘텐츠 내용을 레이아웃할 때 사용하는 기본 간격(default spacing)입니다.    
- 레이아웃 마진 가이드(Layout Margins Guide) : 레이아웃 마진에 따라 형성되는 사각의 프레임 영역
     
### 앵커(Anchor)
***
> 오토레이아웃을 코딩으로 구현하여 제약(Constraint)을 만들기 위해 앵커(Anchor)를 사용할 수 있습니다.    

#### 앵커와 관련된 프로퍼티
```swift
// 뷰에 부여한 제약사항들은 담은 배열
var constraints: [NSLayoutConstraint]

// 뷰 프레임의 하단부 레이아웃 앵커
var bottomAnchor: NSLayoutYAxisAnchor { get }

// 뷰 프레임의 수평 중심부 레이아웃 앵커
var centerXAnchor: NSLayoutXAxisAnchor { get }

// 뷰 프레임의 수직 중심부 레이아웃 앵커
var centerYAnchor: NSLayoutYAxisAnchor { get }

// 뷰 프레임의 높이를 가리키는 레이아웃 앵커
var heightAnchor: NSLayoutDimension { get }

// 뷰 프레임의 리딩을 가리키는 레이아웃 앵커
var leadingAnchor: NSLayoutXAxisAnchor { get }

// 뷰 프레임의 상단부 레이아웃 앵커
var topAnchor: NSLayoutYAxisAnchor { get }

// 뷰 프레임의 트레일링을 가리키는 레이아웃 앵커
var trailingAnchor: NSLayoutXAxisAnchor { get }

// 뷰 프레임의 넓이를 가리키는 레이아웃 앵커
var widthAnchor: NSLayoutDimension { get }
``` 

## 관련 문서
[Auto Layout Guide](https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/AutolayoutPG/index.html#//apple_ref/doc/uid/TP40010853-CH7-SW1)      
[Adaptivity and Layout - iOS H.I.G](https://developer.apple.com/ios/human-interface-guidelines/visual-design/adaptivity-and-layout/)    
