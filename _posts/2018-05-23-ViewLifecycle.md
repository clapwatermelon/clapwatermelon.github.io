---
layout: post
title: View Lifecycle
tags: [view Lifecycle]
---

## View Lifecycle

***

>  뷰의 상태 변화에 따라 호출되는 메서드와 순서에 대해 알아본다.

![viewlifecycle](https://docs-assets.developer.apple.com/published/f06f30fa63/UIViewController_Class_Reference_2x_ddcaa00c-87d8-4c85-961e-ccfb9fa4aac2.png)



![viewlifecylce](https://www.safaribooksonline.com/library/view/learning-xamarin-studio/9781783550814/graphics/0814OT_06_02.jpg)

- `loadView` : 뷰를 만드는 역할. `loadView`가 뷰를 만들고 메모리에 올린 후 viewDidLoad가 호출된다.
- `viewDidLoad` : 뷰 컨트롤러 클래스가 생성될 때, 가장 먼저 실행된다. 메모리에 처음 로딩될 때 1회 호출되는 메서드로(시스템에의해 자동으로 호출) 메모리 경고로 뷰가 사라지지 않는 이상 다시 호출되지 않는다. 초기화 작업을 할 때 사용한다.
- `viewWillAppear` : 뷰가 생성되기 직전에 항상 실행이 되기 때문에 뷰가 나타나기 전에 실행해야 하는 작업들을 한다. 다른 뷰로 이동했다가 되돌아오면 재호출되는 메서드로, 화면이 나타날 때마다 수행해야하는 작업을 하기 좋은 시점이다.
- `viewDidAppear` : 뷰가 생성되고 난 뒤 실행된다(뷰가 뷰 계층에 추가되어 화면이 표시되면 호출되는 메서드). 데이터를 받아서 화면에 뿌려주거나 애니메이션 등의 작업을 하는 로직을 위치시킬 수 있다( `viewWillApear`에 로직을 넣었다가 반영이 안되는 경우가 있기 때문에). 즉, 뷰를 나타내는 것과 관련된 추가적인 작업을 하기 좋은 시점이다.
- `viewWillDisappear` : 뷰가 사라지기 직전에 실행된다. 뷰가 생성된 뒤 발생한 변화를 이전 상태로 되돌리기 좋은 시점이다.
- `viewDidDisappear` : 뷰가 사라지고 난 뒤에 실행한다. 뷰를 숨기는 것과 관련된 추가적인 작업을 하기 좋은 시점이다. 시간이 오래걸리는 작업은 하지 않는 것이 좋다.



> 추가: 내비게이션 컨트롤러의 rootView, 그 다음 view가 서로 왔다갔다 할 시 `viewDidLoad` 는 두번째 뷰에서 계속 호출되지만 첫번째 뷰에서는 한번만 호출된다. 이것은 첫번째 뷰가 rootView로써 메모리에 올라가 있기 때문이다. (stack을 생각하며 첫번째 뷰와달리 두번째뷰는 계속 pop, push된다고 생각하면된다.)

- `viewWillLayoutSubviews` : 뷰가 서브뷰의 레이아웃을 변경하기 직전에 호출되는 메서드이다. 서브뷰의 레이아웃을 변경하기 전에 수행할 작업을 하기 좋은 시점이다.
- `viewDidLayoutSubviews` : 서브뷰의 레이아웃이 변경된 후 호출되는 메서드이다. 서브뷰의 레이아웃을 변경한 후 추가적인 작업을 수행하기 좋은 시점이다.

여기서 중요한 것은 위 메서드들을 사용할 때 override 키워드와 super를 호출해주는 것을 명심하자.



관련 문서: [UIViewController](https://developer.apple.com/documentation/uikit/uiviewcontroller)



