---
layout: post
title: Operating Systems 3 - Process
tags: [multitasking, multiprogramming, multithreading, process, PCB, Process Controll Block, Context Switch, OS, OperatingSystems]
---
## Process?
**프로그램 실행 단위** by [jinjoo choi](https://jinjoochoi.github.io/)       
메모리에 올라간 순간부터 프로세스라고 부른다.        
### Multi-programming
***
Run multiple-programs with **timesharing**       
Run each program in turn until **timeout** or **I/O event**    
> 옛날 컴퓨터라고 볼 수 있다

### Multitasking
***
Multiprogramming with frequent job switching       
CPU scheduling     
> 빨리빨리해서 동시에 시행되는 것처럼 하는 것     

### Multithreading
***
A process with multiple threads     

## Process Control Block(PCB)
***
프로세스 제어 블록(PCB)는 특정한 프로세스를 관리할 필요가 있는 정보를 포함하는 운영체제 커널의 자료구조. **각 프로세스가 생성될 때마다 고유의 PCB**가 생성되고 프로세스가 완료되면 PCB는 제거된다.       
### PCB contains     
- Process state
- Program identifier number (PID)
- [Program counter](https://clapwatermelon.github.io/2018/04/06/Operating-Systems.html) (PC)
- CPU registers 
- CPU scheduling information
- Memory-management information
- Accounting information
- I/O status information

> 프로세스는 CPU가 처리하던 작업의 내용들을 자신의 PCB에 저장하고 다시 CPU를 점유하여 작업을 수행해야 할 때 PCB로부터 해당 정보들을 CPU에서 넘겨와 계속해서 하던 작업을 진행할 수 있다.

### Context Switch
***
![contextSwitch](/assets/post_img/contextSwitch.png)
> 운영체제는 멀티태스킹을 위해서 여러 프로세스를 번갈아가면서 수행한다. 이때, 현재 수행중인 프로세스를 중단하고 새로운 프로세스로 전환하는 과정을 **context switch** 라고 한다. 이 과정에서 PCB를 활용한다.


