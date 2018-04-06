---
layout: post
title: Operating Systems 1 - Computer Organization
tags: [OperatingSystems, OS]
---
## What is an Operating System?
***
- Help the user use computer easily (Interface)
- Help the software use computer resource
- Help the programmer develop software (API)

> OS : software와 hardware 사이의 소통을 도움

### Von Neumann Machine
***
- Pre-Von-Neumann Machine: 
	- A computer can do only single computation
	- Program = HW, Data in memory
- Von-Neumann Machine
	- General purpose computer
	- **Program in memory**, Data in memory
	- Called stored-program architecture
	- Good: re-program easily

> 이전의 폰 노이만 머신에서는 프로그램은 하드웨어에, 데이터는 메모리에 따로 존재했었다면 폰 노이만 머신에서는 프로그램과 데이터가 메모리 안에 들어감으로써 프로그램을 좀 더 쉽게 할 수 있게 되었다.

![VNA](/assets/post_img/VNA.png "Von Neumann Architecture")

### Registers
***
입출력(I/O)을 위한 저장공간
![Registers](/assets/post_img/Registers.png "Registers")

- Program Counter: 다음 수행할 명령어가 어디인지 주소를 저장
- Instruction Register: 현재 실행하고 있는 명령어
- MBR:가져온 주소로 가서 data를 넣음
- MAR: 가져온 주소를 써 놓는 곳

### Problem 1 of Von-Neumann
***
Problem: Von Neumann Bottleneck = Bus
- Too much to move over bus: slow (좋은 CPU 여도 Bus도 좋아야 빠르다)

Solution: Cache
- Temporary fast memory with recent data/program
- Code optimization

> Bus에 병목현상이 생기는 문제점을 일시적으로 최근 데이터를 Cache에 저장

### Problem 2 of Von-Neumann
***
Problem: Program & Data in same memory
- A program can mess-up instructions in memory

Solution: Harvard Architecture
- Separate data and program memory
- Memory restriction: Prevent accessing memory outside data

> program과 data가 같은 메모리안에 있게되면 data에 접근할 때 program도 접근이 가능하여 안정성이나 보안도 떨어지게 되고 또한 프로그램은 메모리에 엉망인 명령들을 내려 망가뜨릴 수 있는 가능성이 있다. 아래의 이미지를통해 폰노이만과 하버드의 구조적 차이를 보면 이해가 빠르다.

![harvardArchitecture](/assets/post_img/harvardA.png)

### Problem 3 of Von-Neumann
***
Problem: Program & Data over ther same bus
- Different fetch rate, slow bus

Solution: Harvard Architecture
- Seperate data and program bus

> Problem 2 와 Problem 3 은 같은 문제라고 볼 수 있다. 즉, Program과 Data가 같이 들어있기 때문에 발생된 문제이다.

### How a computer can do many things simultaneously?
***
Interrupts!! 
컴퓨터가 동시에 여러가지 일을 할 수 있도록 해주는 기능

### Interrupts
***
Provided to improve processor utilization
- most I/O devices are slower than the processor
- processor must pause to wait for device
- wasterful use of the processor

> CPU가 프로그램을 실행하고 있을 때, 입출력 하드웨어 등의 장치나 또는 예외상황이 발생하여 처리가 필요할 경우 CPU에 알려 처리할 수 있도록 하는 것

## Memory Hierarchy
***
### Memory
Major constraints in memory
- amount
- speed
- expense

Memory must be able to keep up with the processor
Cost of memory must be reasonable in relationship to the other componets

### The Memory Hierarchy
***
![memoryHierarchy](/assets/post_img/memoryHierarchy.png)

> 위로 갈 수록 빠르고 비쌈, 용량은 적고 속도 빨라짐, 사용 빈도 높아짐

Going down the hierarchy:
- decreasing cost per bit
- increasing capacity
- increasing access time
- decreasing frequency of access to the memory by the processor

Inboard memory:
1. Registers
2. Cache
3. Main Memory

Outboard Storage:
4. Magnetic Disk, CD-ROM . .

### Principle of Locality
***
컴퓨터 프로그램의 메모리 접근 패턴이 시 공간적으로 근접한 모습을 보이는 경향이 크다 이것을 근접성의 원칙이라고 한다.
Fact: Memory references by the processor tend to cluster in time and space

How to exploit it:
- Data is organized so that the percentage of accesses to each successively lower level is substantially less than that of the level above
- Can be applied across more than two levels of memory

### Cache memory
***
Invisible to the processors, programmer, OS  
Interacts with other memory management hardware  

Reasons for its existence:
- Processor must access memory at least once per instruction cycle
- Processor execution is limited by memory cycle time
- Exploit the principle of locality with a small, fast memory

![Cache](/assets/post_img/CacheOrganization.png)

> 위 그림에서와 같이 Main memory에서 Block 단위로 가져오는 것을 알 수있다.
동대문에서 옷을 가져와서 팔려할 때 티한장 가져와서 팔고 또 한장 가져와서 팔고 할 수 없으니 통째(Block)로 가져와서 파는 것

### Replacement Algorithm
***
캐시에 새로운 Block을 로드할 때 어떤 Block을 대체할 것인지에 대한 알고리즘

- Choose which block to replace when a new block is to be loaded into the cahe
- Least Recently Used(LRU) Algorithm: 가장 최근에 덜 사용 된 것을 대체시키는 알고리즘
