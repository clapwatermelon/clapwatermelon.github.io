---
layout: post
title: Operating Systems 3 - Process
tags: [multitasking, multiprogramming, multithreading, process, PCB, Process Controll Block, Context Switch, OS, OperatingSystems]
---
## Process?
**프로그램 실행 단위**                
메모리에 올라간 순간부터 프로세스라고 부른다.        
### Multi-programming
***
Run multiple-programs with **timesharing**       
Run each program in turn until **timeout** or **I/O event**    
> 멀티프로그래밍은 프로세서의 자원낭비를 최소화 하기 위해 낭비되는 시간을 다른프로그램 수행에 쓰게 하여 (timesharing) 하나의 프로세서에서 여러 프로그램을 교대로 수행할 수 있게 하는 것

### Multitasking
***
Multiprogramming with frequent job switching       
CPU scheduling     
> 빨리 빨리처리함으로써 동시에 시행되는 것처럼 하는 것. 멀티프로그래밍과 다른 점은 멀티프로그래밍이 낭비되는 자원을 최소화하기 위해 교대로 실행하였다면, 멀티태스킹은 **정해진 시간 동안** 교대로 task 를 수행하는 것.

### Multithreading
***
A process with multiple threads       
> thread는 프로세스 내에서 생성되는 하나의 실행 주체이다. 한 프로세스 내에서 여러개의 thread 가 동시에 생성이 가능하다. 같은 프로세스에 존재하는 다른 thread 들과 OS 의 자원을 공유로 code,file, data 등을 공유한다.

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

## Context Switch
***
![contextSwitch](/assets/post_img/contextSwitch.png)

Context: 어떠한 순간에 CPU Register안에 들어있는 값들의 집합과 기타 정보들.    

> 운영체제는 멀티태스킹을 위해서 여러 프로세스를 번갈아가면서 수행한다. 이때, 현재 수행중인 프로세스를 중단하고 새로운 프로세스로 전환하는 과정을 **context switch** 라고 한다. 이 과정에서 PCB를 활용한다.

예를 들자면 Ready 상태인 A 프로세스와 Running 상태인 B 프로세스가 있고 interrupt 요청에 의해 서로 상태가 전이된다고 가정한다면 이떄, A 프로세스가 Running 상태로 전이되고 B 프로세스가 Ready 상태가 될 때 A 프로세스의 상태 또는 레지스터 값 등등 PCB에 저장이되고 A 프로세스의 정보를 PCB에서 CPU로 적재시킨다.       

여기서 CPU를 다른 프로세스로 교환하려면 이전의 프로세스의 상태를 저장하고 새로운 프로세스와 저장된 상태를 복구하는 작업이 필요한데 이 과정을 **Context switch** 라고 말한다.       

> Context switching 이 일어나는 동안 CPU는 아무런 일을 하지 못하며, CPU에 많은 부하를 가져다 준다. 이는 멀티 프로세스 운영체제의 단점이다. 이러한 Context switching 의 시간은 레지스터의 수나 메모리의 속도 등에 좌우된다.      
현재 컴퓨터는 switching 을 하는데 몇 백 ns 밖에 걸리지 않는다.

## Dispatcher module
***
CPU 의 제어를 스케줄러가 선택한 프로세스에게 넘겨주는 모듈. 실제로 CPU 를 할당하는 역할        

## Five-state Process Model
***
![fivestate](/assets/post_img/fivestate.png)

- **New**: **프로세스가 생성'중'**. 프로세스가 생성되었지만 아직 OS 에 의해 승인받지 못한 상태     
- **Ready**: **프로세스가 처리기에 할당되기를 기다림**. New 상태에서 admit된 상태. CPU 를 제외한 다른 자원이 준비완료. 보조기억장치에 있는 프로그램을 실행시켜 메모리에 로드된 상태. 이상태는 여러개의 프로세스가 존재할 수 있다. (CPU 를 할당받기를 기다림)    
- **Running**: **명령어들이 실행중**. 프로세스가 CPU 를 할당받아 실제로 프로세스가 수행되고 있는 상태    
- **Waiting**: **프로세스가 어떤 event 나 I/O 작업을 기다림**      
- **Terminated**: **프로세스의 실행이 종료**. 프로세스의 실행이 와나료되고 할당된 CPU 를 반납   
