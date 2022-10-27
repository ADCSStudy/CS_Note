# PCB와 context switching

__Process Metadata__
* Process ID
* Process State
* Process Priority
* CPU Registers
* Owner
* CPU Usage
* Memeory Usage

프로세스 메타데이터는, 프로세스의 정보들을 뜻한다.

프로세스가 생성되면 이 메타데이터는 PCB에 저장된다.

## PCB : Process Control Block
프로세스의 메타데이터를 저장해 놓는 곳, 한 PCB 안에는 한 프로세스의 정보가 담김.

1. 프로그램 실행
2. 프로세스 생성
3. 프로세스 주소 공간에 (코드, 데이터, 스택) 생성 
4. 이 프로세스의 메타데이터들이 PCB에 저장

## PCB의 필요성
CPU에서는 프로세스의 상태에 따라 교체작업이 이루어진다. (interrupt가 발생해서 할당받은 프로세스가 waiting 상태가 되고 다른 프로세스를 running으로 바꿔 올릴 때)

이때, 앞으로 다시 수행할 대기 중인 프로세스에 관한 저장 값을 PCB에 저장해두는 것이다.

## PCB 구조
Linked List 방식으로 관리된다.

PCB List Head에 PCB들이 생성될 때마다 붙게 된다. 주소값으로 연결이 이루어져 있는 연결리스트이기 때문에 삽입 삭제가 용이하다.

즉, 프로세스가 생성되면 해당 PCB가 생성되고 프로세스 완료시 제거된다.

# Context Switching
CPU가 이전의 프로세스 상태를 PCB에 보관하고, 또 다른 프로세스의 정보를 PCB에 읽어 레지스터에 적재하는 과정

보통 인터럽트가 발생하거나, 실행 중인 CPU 사용 허가시간을 모두 소모하거나, 입출력을 위해 대기해야 하는 경우에 Context Switching이 발생한다.

즉, 프로세스가 Ready → Running, Running → Ready, Running → Waiting처럼 상태 변경 시 발생!

## 오버헤드

오버헤드(overhead)는 어떤 처리를 하기 위해 들어가는 간접적인 처리 시간 · 메모리 등을 말한다.

예를 들어 A라는 처리를 단순하게 실행한다면 10초 걸리는데, 안전성을 고려하고 부가적인 B라는 처리를 추가한 결과 처리시간이 15초 걸렸다면, 오버헤드는 5초가 된다. 또한 이 처리 B를 개선해 B'라는 처리를 한 결과, 처리시간이 12초가 되었다면, 이 경우 오버헤드가 3초 단축되었다고 말한다.

-> 즉 컨텍스트 스위칭 오버헤드는 컨텍스트 스위칭이 걸린 시간과 메모리를 뜻한다.