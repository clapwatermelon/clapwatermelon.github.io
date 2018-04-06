---
layout: post
title: Operating Systems 2 - Microkernel VS Monolithic kernel
tags: [Microkernel, Monolithic, Kernel]
---
## Microkernel?
***
Moves as much from the kernel into "user" space  
Communication takes place between user modules using message passing  

Benefits:  
- Easier to extend a microkernel
- Easier to port the operating system to new architectures
- More **reliable** (less code is running in kernel mode)
- More **secure**

Detriments:  
- Performance overhead of user space to kernel space communication

> 커널의 크기가 작으므로 커널과 일부 서비스만으로 작은 운영체제를 구성하여 임베디드 시스템에 사용가능. 즉, 컴포넌트 기반 운영체제에 더욱 가깝다고 할 수 있다. 커널의 핵심적인 기능 외에 모두 프로세스 형태로 제공되므로 파일시스템이나 입출력 처리가 많을수록 서로간의 메세지를 주고 받아야하므로 속도가 느려질 수 있다.  

## Monolithic kernel?
***
**Modules**

Most modern operating systems implement kernel modules  
- Uses **object-oriented** approach
- Each core **componet is separate**
- Each talks to the others over known interfaces
- Each is **loadable as needed within the kernel**

Overall, similar to layers but with more flexible

> 커널이 많은 일을 한다. 가장 확장성이 떨어지는 방법이지만 성능이 좋아서 리눅스에서도 사용되고 있으며 리눅스는 확장성을 보완하기 위해서 module을 사용한다.

Microkernel과 Monolithic kernel을 예를 들자면     
정부는 작아야한다! 공화당스러운건 **Microkernel** (kernel이 작으므로)     
정부는 커야한다! 민주당스러운건 **Monolithic kernel** (kernel이 많은 일을 해야하므로)

