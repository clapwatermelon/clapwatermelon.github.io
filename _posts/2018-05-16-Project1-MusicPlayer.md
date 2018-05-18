---
layout: post
title: Project 1 - MusicPlayer
published: false
tags: [AVFoundation, AVKit, AVPlayer, AVAudioPlayer]
---

>  BoostCourse iOS 과정을 들으며 공부한 것과 배운 것을 토대로 정리하고 기록하기 위한 포스팅입니다.



<code>AVFoundation</code> 프레임워크의 <code>AVAudioPlayer</code> 라는 클래스를 통해 음원을 재생하는 어플리케이션을 제작합니다. 



## AVFoundation?
***
> AVFoundation은 다양한 Apple 플랫폼에서 사운드 및 영상 미디어의 처리, 제어, 가져오기 및 내보내기 등 광범위한 기능을 제공하는 프레임워크입니다.



![AVFoundation](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/AVFoundationPG/Art/frameworksBlockDiagram_2x.png)

[이 문서](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/Introduction/Introduction.html#//apple_ref/doc/uid/TP40016757-CH1-SW1) 에서 AVFoundation 마지막 단락 부분을 보면

AVFoundation gives you a rich set of features to build robust playback apps. However, because the framework sits below the user interface frameworks, it doesn’t provide a standard user interface for controlling playback. Although it’s possible to build your own custom player interface, doing so often involves a considerable amount of work and requires you to have a deep understanding of the lower-level AVFoundation interfaces. There are certainly cases where having complete control over the user interface is desirable, but often the better solution is to rely on the features provided by the AVKit framework.


AVFoundation은 풍부한 재생 기능을 제공하는 다양한 기능을 제공합니다. 그러나 프레임 워크는 사용자 인터페이스 프레임 워크 아래에 있기 때문에 재생 제어를위한 표준 사용자 인터페이스를 제공하지 않습니다. 자신의 커스텀 플레이어 인터페이스를 구축하는 것이 가능하지만, 그렇게하기 위해서는 상당한 작업량이 필요하며, 더 낮은 레벨의 AVFoundation 인터페이스에 대한 깊은 이해가 필요합니다. 사용자 인터페이스를 완벽하게 제어하는 것이 바람직한 경우가 있지만, 더 좋은 해결책은 AVKit 프레임 워크에서 제공하는 기능에 의존하는 것입니다.


> <code>AVFoundation</code>은 <code>UIKit</code>아래에 있기 때문에(위에 그림 참고) 커스텀 플레이어 인터페이스를 구축하는 것이 가능하다는 것을 알 수 있다. 또한 마지막 줄에서 **더 좋은 해결책은 AVKit 프레임 워크에서 제공하는 기능에 의존하는 것입니다.** 를 볼 수 있는데 그렇다면 AVKit이란?



## AVKit? 
***
AVKit is a companion framework built on top of AVFoundation. AVKit makes it easy for you to provide a player interface for your app that matches the platform’s native playback experience. AVKit uses AVFoundation’s playback infrastructure to provide a player interface that automatically adapts to best match the content being played. Using AVKit, your player automatically displays subtitles and closed captions, presents navigable chapter markers, and provides controls to select alternative media options. Because AVKit is a system framework, your playback apps automatically adopt the new aesthetics and features of future operating system updates without any additional work from you.

The framework is available in iOS, tvOS, and macOS. Although it shares many of its core features across all platforms, it also offers a number of platform-specific features you can use in your apps. These features are described in later sections of this guide.


AVKit은 AVFoundation 위에 구축 된 보조 프레임 워크입니다. AVKit을 사용하면 플랫폼의 기본 재생 환경과 일치하는 앱용 플레이어 인터페이스를 쉽게 제공 할 수 있습니다. AVKit은 AVFoundation의 재생 인프라를 사용하여 재생중인 콘텐츠와 가장 잘 일치하도록 자동으로 조정되는 플레이어 인터페이스를 제공합니다. AVKit을 사용하면 자막과 자막이 자동으로 표시되고 탐색 가능한 챕터 마커가 표시되며 대체 미디어 옵션을 선택할 수있는 컨트롤이 제공됩니다. AVKit은 시스템 프레임 워크이므로 재생 응용 프로그램은 추가 작업없이 향후 운영 체제 업데이트의 새로운 미학과 기능을 자동으로 채택합니다.
      
> <code>AVKit</code>은 <code>AVFoundation</code> 의 **보조 프레임워크** 임을 알 수 있다.



## AVAudioPlayer?
***
> AVAudioPlayer 클래스는 파일 또는 메모리에 있는 사운드 데이터를 재생하는 기능을 제공합니다.

문서에도 아주 간단명료하게 나와 있다. <code>AVAudioPlayer</code>는 네트워크에 있는 사운드 파일재생이 불가하며 이말인 즉, **파일 또는 메모리**에 있는 사운드를 재생기능을 제공한다는 것.

네트워크에 있는 사운드 파일을 재생하고싶다면 [AVPlayer](https://developer.apple.com/documentation/avfoundation/avplayer) 를 참고하자.



## 관련문서
***
- [AVFoundation Programming Guide](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)
- [Media Playback Programming Guide](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/Introduction/Introduction.html#//apple_ref/doc/uid/TP40016757-CH1-SW1)
- [AVPlayer](https://developer.apple.com/documentation/avfoundation/avplayer) 


## Properties, IBOutlets
***
<code>AVAudioPlayer</code>는 파일 또는 메모리에 있는 사운드를 재생한다는 것을 배웠다.       
에셋 카탈로그에 사운드 파일을 넣어주자.

```swift
import UIKit
import AVFoundation

class ViewController: UIViewController, AVAudioPlayerDelegate {
    // MARK: - Properties
    var player: AVAudioPlayer!
    var timer: Timer!
    
    // MARK: IBOutlets
    @IBOutlet weak var playPauseButton: UIButton!
    @IBOutlet weak var timeLabel: UILabel!
    @IBOutlet weak var progressSlider: UISlider!
}

```

<code>AVAudioPlayer</code>를 사용하기 위해 <code>AVFoundation</code>을 import 해주고 프로퍼티로 <code>var player: AVAudioPlayer!</code>와<code>var timer: Timer!</code>를 선언한다.인터페이스 빌더에서 버튼과 레이블, 슬라이더를 추가한 뒤 <code>IBOutlet</code>으로 연결한다.

## Method - initializePlayer
***
```swift
func initializePlayer() {
        guard let soundAsset: NSDataAsset = NSDataAsset(name: "sound") else {
            print("Could not import sound file assets")
            return
        }
        
        do {
            try self.player = AVAudioPlayer(data: soundAsset.data)
            self.player.delegate = self
        } catch let error as NSError {
            print("Player initialization failed")
            print("code : \(error.code), message : \(error.localizedDescription)")
        }
        self.progressSlider.maximumValue = Float(self.player.duration)
        self.progressSlider.minimumValue = 0
        self.progressSlider.value = Float(self.player.currentTime)
}
```

먼저 <code>NSDataAsset</code>를 사용하여 사운드 파일을 가져올 때 unwrapping을 해준 것을 볼 수 있는데 이것은 NSDataAsset이 파일이 존재하지 않을 수도 있기 때문에 옵셔널로 반환되기 때문이다. 따라서 unwrapping이 필요하다. 만약 unwrapping 해주지 않는 다면 아래 처럼 unwrapping되지 않았다고 친절히 알려준다.

![NSDataAssetError](/assets/post_img/NSDataAssetError.png)

다음으로 사운드를 재생할 AudioPlayer 객체를 생성합니다. 여기서도 예외 처리를 해줌으로써 객체 생성의 실패를 처리할 수 있도록 해줍니다. 마찬가지로 예외처리를 하지 않으면 해야한다고 알려준다.

![AudioPlayerErrorHandle](/assets/post_img/AVAudioPlayerErrorHandle.png)

<code>player</code>객체를 <code>delegate</code>해주어 <code>player</code>가 <code>AVAudioPlayer</code>를 사용할 것을 알려준다.



슬라이더를 앞서 생성하였으니 슬라이더가 나타내는 값의 범위를 지정해준다. 최대 값은 <code>player</code>객체의 **사운드의 지속시간**을 나타내는 <code>duration</code>으로 지정해주고 최소 값은 0으로 지정해준다. 또한 슬라이더의 <code>value</code>를 <code>currentTime</code>으로 초기화 해준다. <code>currentTime</code>은 **사운드가 재생중인 경우 <code>currentTime</code>은 현재 재생 위치의 사운드에 대한 오프셋입니다. 사운드가 재생되지 않으면 currentTime은 재생이 시작될 사운드의 오프셋입니다** 라고 나와있다.



> initializePlayer 부분에서 사운드 파일 할당, AVAudioPlayer 객체생성, 슬라이더 값 지정해주었다.



## Method - updateTimeLabelText 
***
```swift
func updateTimeLabelText(time: TimeInterval) {
        let minute: Int = Int(time / 60)
        let second: Int = Int(time.truncatingRemainder(dividingBy: 60))
        let milisecond: Int = Int(time.truncatingRemainder(dividingBy: 1) * 100)
        let timeText: String = String(format: "%02ld:%02ld:%02ld", minute, second, milisecond)
        self.timeLabel.text = timeText
}
```

<code>truncatingRemainder</code>는 **정수형이 아닌 수**를 나누고 나머지를 구하는 것이다(integer면 % 사용 가능). 즉, % 모듈러스 연산을 하는 것!



10 % 7 를 한 값은 3으로 나오지만 10.0 % 7 을 하면 오류가 나는데 이것을 <code>truncatingRemainder</code>를 사용하여 가능하게한다.



위의 코드에서 처음에 무슨 역할을 하는 건지 몰라서 출력을 하나하나 해보면서 어떤 역할을 하는지 알아보았다.

<code>time</code>, <code>seond</code>, <code>millisecond</code>을 출력시 아래와 같다.

```swift
time: 0.0, second: 0, milisecond: 0
time: 0.00242630385487528, second: 0, milisecond: 0
time: 0.00575963718820862, second: 0, milisecond: 0
time: 0.0157369614512472, second: 0, milisecond: 1
time: 0.025827664399093, second: 0, milisecond: 2
time: 0.0357369614512472, second: 0, milisecond: 3
time: 0.0457596371882086, second: 0, milisecond: 4
time: 0.0557369614512472, second: 0, milisecond: 5
```

 전달받은 현재시간 time의 시간을 60으로 나누어 second를 구하고, 1로 나눈 뒤 100을 곱하여 milisecond의 값을 구해 원하는 포맷으로 보여준다.



## Method - makeAndFireTimer, invalidateTimer
***
```swift
func makeAndFireTimer() {
        self.timer = Timer.scheduledTimer(withTimeInterval: 0.01, repeats: true, block: { [unowned self] (timer: Timer) in
            if self.progressSlider.isTracking { return }
            self.updateTimeLabelText(time: self.player.currentTime)
            self.progressSlider.value = Float(self.player.currentTime)
        })
        self.timer.fire()
}
func invalidateTimer() {
        self.timer.invalidate()
        self.timer = nil
}
```



프로젝트의 기준에 따라 0.01단위로 <code>withTimeInterval</code>로 지정하고, 반복적으로 하기위해 <code>repeats</code>를 <code>true</code>로 셋팅한다. <code>true</code>인 경우 타이머는 <code>invalidate</code> 될 때까지 스스로 일정을 반복한다.



<code>block</code>에는 <code>withTimeInterval</code>에 지정한 0.01초 마다 해주어야할 것들을 넣어 준다. [unowned](https://clapwatermelon.github.io/2018/04/24/ARC.html) 는 간단히 말하면 **값이 있음(non-optional type)을 가정**하고 사용하는 것이다.



<code>timer</code>를 시작하기위해 <code>fire</code>, 종료는 <code>invalidate</code>로 종료한다.

## Method - touchUpPlayPauseButton
***
```swift
@IBAction func touchUpPlayPauseButton(_ sender: UIButton) {
        sender.isSelected = !sender.isSelected
        
        if sender.isSelected {
            self.player?.play()
            self.makeAndFireTimer()
        } else {
            self.player?.pause()
            self.invalidateTimer()
        }
}
```

플레이 버튼이 눌렸을 때 <code>player</code>를 <code>play</code>하고 타이머를 실행시킨다. 여기서 중요한 것은 <code>isSelected</code>의 값은 사용자가 버튼을 누를 때마다 값이 적용되는 것이아니라 초기값은 항상 <code>false</code> 이므로 직접 값을 셋팅해주어야한다.



처음 값이 <code>false</code>이므로 버튼이 눌리면 <code>true</code>값을, 다시 눌리면 <code>false</code>값이 들어갈 수 있게 <code>sender.isSelected = !sender.isSelected</code>를 해주고 실행할 작업들을 구현해준다.



## Method - sliderValueChanged
***
``` swift
@IBAction func sliderValueChanged(_ sender: UISlider) {
        self.updateTimeLabelText(time: TimeInterval(sender.value))
        if sender.isTracking { return }
        self.player.currentTime = TimeInterval(sender.value)
}
```

시간을 나타내는 label에 슬라이더의 값을 넣어주고 슬라이더의 움직이는 동안 재생되는 구간이 바뀌지 않게 <code>isTracking</code>을 <code>return</code>해줌으로써 사운드가 끊기는 것을 막는다. 



<code>currentTime</code>값에 슬라이더의 값을 할당해줌으로써 thumb를 이동시켰을 때의 구간을 재생할 수 있게한다. 



참고: 슬라이더는 사용자가 슬라이더의 값을 변경하면 슬라이더에 연결된 메서드가 호출되어 원하는 작업이 실행됩니다. 기본적으로는 사용자가 슬라이더의 **Thumb**를 이동시키면 연속적으로 이벤트를 호출하지만, **isContinous** 프로퍼티값을 false로 설정하면 슬라이더의 Thumb에서 손을 떼는 동시에 이벤트를 호출합니다.



## Method - audioPlayerDidFinishPlaying
***
```swift
func audioPlayerDidFinishPlaying(_ player: AVAudioPlayer, successfully flag: Bool) {
        self.playPauseButton.isSelected = false
        self.progressSlider.value = 0
        self.updateTimeLabelText(time: 0)
        self.invalidateTimer()
}
```

 <code>AVAudioPlayerDelegate</code> 프로토콜이 제공하는 파일의 재생이 끝나면 호출되는<code>audioPlayerDidFinishPlaying(_,successfully:)</code>에 재생이 끝났을 때의 버튼이미지, 슬라이더, 시간을 다시 설정한다.



> 처음 코드를 보지않고 무작정 만들어 놓고 너무 쉽다고 생각했던 나에게 망치 한대를..이렇게 <code>AVAudioPlayer</code>에 새로이 알게되는 내용과 <code>AVAudioPlayer</code>에 대해 공부하면서  <code>AVKit</code>, <code>AVPlayer</code>도 간단하게나마 이해할 수 있었다.

