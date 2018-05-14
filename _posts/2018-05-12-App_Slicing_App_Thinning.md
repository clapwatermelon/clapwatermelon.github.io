---
layout: post
title: Swift - App Thinning, App Slicing
tags: [swift, App Thinning, App Slicing]
---

## App Thinning(앱 시닝), App Slicing(앱 슬라이싱)
***
### App Thinning(앱 시닝)이란?
***
앱 시닝이란 애플리케이션이 디바이스에 설치될 때 앱 스토어와 운영체제가 그 디바이스의 특성에 맞게 설치하도록 하는 **설치 최적화 기술**을 의미합니다. 이를 통해 **애플리케이션의 설치용량을 최소화하고 다운로드의 속도를 향상**시킬 수 있습니다. 앱 시닝(app thinning)의 기술 구성요소는 **슬라이싱(slicing), 비트코드(bitcode), 주문형 리소스(on-demand resource)**가 있습니다.

### App Slicing(앱 슬라이싱)이란?
***
슬라이싱(slicing)은 애플리케이션이 지원하는 다양한 디바이스에 대한 여러 조각의 애플리케이션 번들(app bundle)을 생성하고 디바이스에 알맞은 조각을 전달하는 기술입니다. 개발자가 애플리케이션의 전체 버전을 iTunes Connect에 업로드하게 되면, 앱 스토어에는 각 디바이스 특성에 다양한 버전의 조각들이 생성됩니다. **사용자가 애플리케이션을 설치할 때 전체 버전이 아닌 슬라이싱(slicing)된 조각들 중 사용자의 디바이스의 가장 적합한 조각이 다운로드되어 설치됩니다.** 에셋 카탈로그에서 관리하는 이미지들은 자동으로 적용이 됩니다.(슬라이싱(slicing)은 iOS 9.0 이상버전 이상만 지원합니다.)

> iTunes Connect란 개발자가 앱 스토어에 판매할 애플리케이션을 제출하고 관리할 수 있도록 도와주는 웹 기반 도구입니다.

## 관련 문서
[App Thinning](https://help.apple.com/xcode/mac/current/#/devbbdc5ce4f)     
[On-Demand Resource](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/On_Demand_Resources_Guide/index.html)
