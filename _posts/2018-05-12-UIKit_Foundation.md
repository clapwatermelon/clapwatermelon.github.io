---
layout: post
title: Swift - UIKit, Foundation
tags: [swift, UIKit, Foundation]
---

## UIKit, Foundation
***
UIKit 과 Foundation은 Cocoa Touch Framework에 포함되어있습니다.

## UIKit
> UIKit은 iOS 애플리케이션의 사용자 인터페이스를 구현하고 이벤트를 관리하는 프레임워크입니다. UIKit은 iOS 애플리케이션 개발시 사용자에게 보여질 화면을 구성하고 사용자 액션에 대응에 관련된 다양한 요소를 포함합니다.    

- UIKit 프레임워크는 제스처 처리, 애니메이션, 그림 그리기, 이미지 처리, 텍스트 처리 등 사용자 이벤트 처리를 위한 클래스를 포함합니다.     
- 또한 테이블뷰, 슬라이더, 버튼, 텍스트 필드, 얼럿 창 등 애플리케이션의 화면을 구성하는 요소를 포함합니다.    
- UIKit은 iOS와 tvOS 플랫폼에서 사용합니다.    

> **Important**    
UIKit 클래스 중 UIResponder에서 파생된 클래스나 사용자 인터페이스에 관련된 클래스는 애플리케이션의 메인 스레드(혹은 메인 디스패치 큐)에서만 사용하세요.   

### UIKit 기능별 요소
#### 사용자 인터페이스    
화면에 내용을 표시하고 사용자 상호작용을 용이하게합니다. 뷰컨트롤러는 뷰와 인터페이스 구조를 관리하는 데 도움이됩니다.

- View and Control : 화면에 콘텐츠 표시
- View Controller : 사용자 인터페이스 관리    
- Animation and Haptics : 애니메이션과 햅틱을 통한 피드백 제공    
- Window and Screen : 뷰 계층을 위한 윈도우 제공    

#### 사용자 액션    
- Touch, Press, Gesture: 제스처 인식기를 통한 이벤트 처리 로직    
- Drag and Drop: 화면 위에서 드래그 앤 드롭 기능    
- Peek and Pop: 3D 터치에 대응한 미리 보기 기능    
- Keyboard and Menu: 키보드 입력을 처리 및 사용자 정의 메뉴 표시    

#### 그래픽, 드로잉 및 프린트
- Images and PDF: 비트맵 및 PDF 형식을 사용하는 이미지를 생성하고 관리
- Drawing: 렌더러를 사용하여 앱의 드로잉 환경을 구성하고 경로, 문자열 및 그림자를 그려냄
- Printing: system print panel을 보여주고 print process를 관리    
#### 텍스트
UIKit에는 텍스트를 응용 프로그램에 쉽게 표시할 수있는 텍스트 뷰 외에도 사용자 정의 텍스트 관리 및 시스템 키보드를 지원하는 렌더링 기능이 있습니다.
- Text Display and Fonts: UIKit view를 사용하여 텍스트를 표시하고 글꼴을 관리하며 철자를 검사
- Text Storage: 텍스트 저장 공간을 관리하고 텍스트 레이아웃을 조정
- Keyboards and Input: 시스템 키보드를 구성하거나 직접 키보드를 만들고 입력을 직접 처리 가능    

#### ViewController를 생성하면 상단에 'import UIKit'가 기본적으로 명시되어있다. 왜 그럴까?
***
ViewController를 사용하여 UIKit 앱의 인터페이스를 관리한다. 즉, UIKit은 사용자 인터페이스에 사용되는 기능들이 포함되어있어 사용자 인터페이스를 관리하는 ViewController를 생성할때 UIKit가 기본으로 import 된다.    

## Foundation     
> Foundation은 iOS 애플리케이션의 운영체제 서비스와 기본 기능을 포함하는 프레임워크입니다. Foundation은 원시 데이터 타입(String, Int, Double), 컬렉션 타입(Array, Dictionary, Set) 및 운영체제 서비스를 사용해 애플리케이션의 기본적인 기능을 관리하는 프레임워크 입니다.    

- Foundation 프레임워크는 데이터 타입, 날짜 및 시간 계산, 필터 및 정렬, 네트워킹 등의 기본 기능을 제공합니다.    
- Foundation 프레임워크에서 정의한 클래스, 프로토콜 및 데이터 타입은 iOS뿐만 아니라 macOS, watchOS, tvOS 등 모든 애플 SDK에서 사용됩니다.     

> Foundation에서 제공하는 데이터 타입 및 컬렉션 타입의 대부분은 Objective-C 언어의 기능에서 지원하지 않는 것이기 때문에 언어기능을 보완하기 위한 구현이며, Swift에서는 이에 해당하는 데이터 타입과 기능 대부분을 [Swift 표준 라이브러리](https://developer.apple.com/documentation/swift)에서 제공합니다.     

### Foundation 기능별 요소
#### 기본    
- Number, Data, String: 원시 데이터 타입 사용    
- Collection: Array, Dictionary, Set 등과 같은 컬렉션 타입 사용    
- Date and Time: 날짜와 시간을 계산하거나 비교하는 작업    
- Unit and Measurement: 물리적 차원을 숫자로 표현 및 관련 단위 간 변환 기능    
- Data Formatting: 숫자, 날짜, 측정값 등을 문자열로 변환 또는 반대 작업    
- Filter and Sorting: 컬렉션의 요소를 검사하거나 정렬하는 작업    

#### 애플리케이션 지원
- Resources: 애플리케이션의 에셋과 번들 데이터에 접근 지원    
- Notification: 정보를 퍼뜨리거나 받아들이기는 기능 지원    
- App Extension: 확장 애플리케이션과의 상호작용 지원    
- Error and Exceptions: API와의 상호작용에서 발생할 수 있는 문제 상황에 대처할 수 있는 기능 지원

#### 파일 및 데이터 관리
- File System: 파일 또는 폴더를 생성하고 읽고 쓰는 기능 관리    
- Archives and Serialization: 속성 목록, JSON, 바이너리 파일들을 객체로 변환 또는 반대 작업 관리    
- iCloud: 사용자의 iCloud 계정을 이용해 데이터를 동기화하는 작업 관리    

#### 네트워킹    
- URL Loading System: 표준 인터넷 프로토콜을 통해 URL과 상호작용하고 서버와 통신하는 작업   
- Bonjour: 로컬 네트워크를 위한 작업   

#### 어떤 파일을 생성하면 import Foundation이 기본적으로 명시되어있을까?
원시 데이터 타입, 컬렉션 타입을 사용하기 위해 기본적인 swift파일을 생성하면 Foundation이 import되는 것을 확인 할 수있다. ViewController에서도 원시 데이터 타입이나 컬렉션 타입을 사용하는데 UIKit만 import되어있다. 이 이유는 UIKit를 import 하게되면 Foundation은 backstage에서 이미 가져오기 때문이다.


## 관련 문서
[UIKit](https://developer.apple.com/documentation/uikit)     
[Foundation](https://developer.apple.com/documentation/foundation)
[Swift Standard Library](https://developer.apple.com/documentation/swift)

